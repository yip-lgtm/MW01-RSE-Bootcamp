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

- `loading-calc-actions.md` — Loading Analysis 相關動作定義
- `../engine/calculation-engine.md` — 簡化版 CalculationEngine 設計
- `../engine/loading-sequence-wc025a.md` — WC025A 第 7 頁 Action 序列範例

## 對應關係（OpenMAIC → RSE）

| OpenMAIC | RSE Bootcamp |
|----------|--------------|
| Action | CalcAction |
| ActionEngine | CalculationEngine |
| Whiteboard Ledger | Calc Ledger |
| speech / wb_draw_* | explain_formula / write_equation / fill_load_table |
| SYNC_ACTIONS | 必須等待計算完成的動作 |
