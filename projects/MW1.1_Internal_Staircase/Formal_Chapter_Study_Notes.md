# Step-by-Step Study: Draft → Formal Chapter
# 逐步學習：草稿變成正式章節

**目的**：把 Loading_Analysis_Draft / Member_Design_Draft 收成可放入 8–12 頁報告的正式章

---

## Step 1 — 分清「草稿」與「正式章」

| 草稿 Draft | 正式章 Formal |
|------------|---------------|
| 含 Ledger、Action ID | 不出現 la-01、md-07 |
| 教學說明較多 | 只留設計需要的句子 |
| 可寫「示例長度 4.5 m」 | 改為「以圖則為準」或給定值 |
| 長表格 + 重複 | 合併成少而精的表 |
| 中英對照教學語氣 | 報告語氣（中英可並列表格，正文精簡） |

---

## Step 2 — 刪減清單（必做）

| 刪除 | 原因 |
|------|------|
| 所有 `Ledger` 區塊 | 內部追蹤用，不進報告 |
| `Action: define_xxx` 標題 | 讀者是 BD／RSE，不是引擎 |
| 「下一步 Next Section」 | 目錄已有 |
| 重複的「對應模板」連結 | 放倉庫 README 即可 |
| 過長假設列表 | 收成 4–5 點 |

---

## Step 3 — 保留清單（必留）

| 必須保留 | 說明 |
|----------|------|
| 規範引用一句 | CoP 名稱 + 表號 |
| 材料／幾何／荷載表 | 可審批核心 |
| 組合公式與 7.12 kPa | 可重現 |
| 構件表 + 利用率 + OK | 結論依據 |
| 簡短假設 | 邊界清楚 |
| 荷載路徑一句 | 邏輯完整 |

---

## Step 4 — 頁數目標

| 章 | 草稿篇幅 | 正式章目標 |
|----|----------|------------|
| Loading (Ch.4) | 偏長 | **1.0–1.5 頁** |
| Member (Ch.6) | 偏長 | **1.0–1.5 頁** |

做法：表為主、句為輔；同一數據不出現三次。

---

## Step 5 — 語氣轉換示例

**草稿**  
> Action: `calc_step_self_weight` (la-05) … Ledger [la-05] → OK

**正式**  
> 15 mm steel plate self-weight = 0.015 × 77 = 1.16 kPa. With 0.5 kPa finish, surface DL = 1.66 kPa.

**草稿**  
> 控制情況 Governing | 局部強度 | 0.87 | Pass

**正式**  
> MB1 (UEA 200×100×15): governing utilization 0.87 (local capacity) → OK.

---

## Step 6 — 與全報告銜接

| 正式章檔案 | 放入大綱位置 |
|------------|--------------|
| `CH04_Loading_Analysis_Formal.md` | 第 4 章（約 p.4–5） |
| `CH06_Member_Design_Formal.md` | 第 6 章（約 p.6–8） |

上游：第 2 章引用規範；下游：第 5 章 SAP 摘要、第 7 章玻璃。

---

## Step 7 — 完成檢查（正式章）

| 檢查 | Loading | Member |
|------|---------|--------|
| 無 Ledger / Action ID | ☐ | ☐ |
| 有規範出處 | ☐ | ☐ |
| 有總表 | ☐ | ☐ |
| 有明確 OK／數值 | ☐ | ☐ |
| 假設 ≤ 5 點 | ☐ | ☐ |
| 篇幅約 1–1.5 頁 | ☐ | ☐ |

---

## 產出檔案

- `CH04_Loading_Analysis_Formal.md` — 正式荷載章  
- `CH06_Member_Design_Formal.md` — 正式構件章  
- 本筆記 — 轉換方法（可重複用於 Glass／Anchor）
