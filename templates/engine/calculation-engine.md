# CalculationEngine 設計

> 簡化版計算引擎 — 靈感來自 OpenMAIC ActionEngine

## 核心概念

| 中文 | English |
|------|---------|
| 統一執行所有 CalcAction | Unified execution of all CalcActions |
| 每步寫入 Ledger | Every step written to Ledger |
| 支援單步與批次序列 | Supports single step and batch sequence |
| 失敗可追溯 | Failures are traceable |

## Ledger 結構

```ts
interface CalcLedgerEntry {
  actionId: string;
  type: string;
  success: boolean;
  inputs: Record<string, unknown>;
  outputs?: Record<string, unknown>;
  error?: string;
  durationMs: number;
  timestamp: string;
  remark?: string;
}
```

## 引擎骨架

```ts
class CalculationEngine {
  private ledger: CalcLedgerEntry[] = [];
  private state: ReportState;

  constructor(initialState: ReportState) {
    this.state = initialState;
  }

  /** 執行單一動作 */
  async execute(action: LoadingCalcAction): Promise<CalcActionResult> {
    const start = Date.now();
    let result: CalcActionResult;

    try {
      switch (action.type) {
        case 'define_design_data':
          result = this.execDefineDesignData(action);
          break;
        case 'define_geometry':
          result = this.execDefineGeometry(action);
          break;
        case 'define_imposed_loads':
          result = this.execDefineImposedLoads(action);
          break;
        case 'calc_step_self_weight':
          result = this.execCalcStepSelfWeight(action);
          break;
        case 'calc_landing_self_weight':
          result = this.execCalcLandingSelfWeight(action);
          break;
        case 'calc_glass_loads':
          result = this.execCalcGlassLoads(action);
          break;
        case 'combine_loads':
          result = this.execCombineLoads(action);
          break;
        case 'ref_cop':
          result = this.execRefCop(action);
          break;
        case 'write_load_summary':
          result = this.execWriteLoadSummary(action);
          break;
        default:
          result = { success: false, error: `Unknown action: ${(action as any).type}` };
      }
    } catch (err) {
      result = { success: false, error: String(err) };
    }

    // 無論成功失敗都寫入 Ledger
    this.appendLedger({
      actionId: action.id,
      type: action.type,
      success: result.success,
      inputs: (action as any).params,
      outputs: result.outputs,
      error: result.error,
      durationMs: Date.now() - start,
      timestamp: new Date().toISOString(),
    });

    return result;
  }

  /** 批次執行一序列動作 */
  async executeSequence(actions: LoadingCalcAction[]): Promise<CalcActionResult[]> {
    const results: CalcActionResult[] = [];
    for (const action of actions) {
      const r = await this.execute(action);
      results.push(r);
      if (!r.success) break;  // 失敗即停（可改為繼續）
    }
    return results;
  }

  getLedger(): CalcLedgerEntry[] {
    return [...this.ledger];
  }

  private appendLedger(entry: CalcLedgerEntry) {
    this.ledger.push(entry);
  }

  // ……各 execXXX 私有方法（依 params 計算並更新 this.state）
}
```

## 執行模式（對應 OpenMAIC）

| 模式 | 中文 | 範例 |
|------|------|------|
| Fire-and-forget | 觸發後立即返回 | `ref_cop`（只寫引用） |
| Synchronous | 必須等待完成 | `calc_*`、`combine_loads`、`write_load_summary` |

## 與報告的銜接

| 中文 | English |
|------|---------|
| Ledger 可直接轉成報告「計算過程」附錄 | Ledger can become the calculation process appendix |
| 每個 Action 的 outputs 寫入對應表格 | Each Action’s outputs feed the corresponding tables |
| 全部成功後才進入下一章節 | Only after all succeed proceed to next section |
