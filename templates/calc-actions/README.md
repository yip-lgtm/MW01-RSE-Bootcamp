# CalcAction 系統

> 靈感來自 OpenMAIC Action Engine  
> 把「計算步驟」變成可執行動作，支援 Ledger 記錄與可重現報告

## 目標

| 中文 | English |
|------|---------|
| 每個計算步驟都是具名 Action | Every calculation step is a named Action |
| 可執行、可記錄、可審批 | Executable, recordable, approvable |
| 對應 MW01 Class I RSE 報告章節 | Maps to MW01 Class I RSE report sections |

## 目錄

| 檔案 | 內容 |
|------|------|
| `loading-calc-actions.md` | Loading Analysis（9 個動作） |
| `member-design-calc-actions.md` | 鋼構件設計（MB1/C1/SB1） |
| `glass-anchor-calc-actions.md` | 玻璃欄杆 + 錨栓 |

引擎與序列：

- `../engine/calculation-engine.md` — CalculationEngine + Ledger
- `../engine/loading-sequence-wc025a.md` — WC025A 第 7 頁完整序列

## 對應關係（OpenMAIC → RSE）

| OpenMAIC | RSE Bootcamp |
|----------|--------------|
| Action | CalcAction |
| ActionEngine | CalculationEngine |
| Whiteboard Ledger | Calc Ledger |
| speech / wb_draw_* | explain_formula / write_equation / fill_load_table |
| SYNC_ACTIONS | 必須等待計算完成的動作 |

## 建議使用順序

1. Loading Analysis 序列  
2. Member Design 序列  
3. Glass + Anchor 序列  
4. 結論與 RSE 簽署（後續擴充）  
