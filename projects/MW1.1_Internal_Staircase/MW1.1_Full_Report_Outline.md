# MW 1.1 完整 RSE 計算報告大綱
# Complete RSE Calculation Report Outline (8–12 Pages)

**項目 Item**：MW 1.1 – Erection or Alteration of Internal Staircase  
**參考案例**：WC025A Camel Paint Buildings Block 3  
**目標頁數**：8–12 頁（含封面、目錄、計算、圖則、結論）  
**原則**：可重現、可審批；公式／表格／假設清楚；引用 MWTGe + CoP；RSE 親簽結論頁  
**日期**：2026-08-06

---

## Step 0 — 報告定位（寫之前先鎖定）

| 中文 | English |
|------|---------|
| 純小型工程 Class I 提交 | Pure Class I Minor Works submission |
| 不是 A&A 結構報告標題 | Not titled as A&A structural report |
| 必須有 RSE 簽署結論頁 | Must have RSE signed conclusion page |
| 圖則按 MWTGe Appendix VI 著色 | Drawings coloured per Appendix VI |

**建議文件名**

`MW1.1_Internal_Staircase_RSE_Report_RevA.pdf`

---

## Step 1 — 頁數總表（8–12 頁配置）

| 頁碼 | 章節 | 建議頁數 | 狀態／來源 |
|------|------|----------|------------|
| 1 | 封面 Cover | 1 | 待寫 |
| 2 | 目錄 Contents | 0.5–1 | 待寫 |
| 2–3 | 1. 項目簡介與範圍 | 1 | 待寫 |
| 3 | 2. 設計準則與引用規範 | 0.5–1 | 待寫 |
| 4–5 | 3–4. 設計數據 + 荷載分析 | 1.5–2 | ✅ Loading_Analysis_Draft |
| 5–6 | 5. 結構分析摘要 | 1 | 待寫（SAP 摘要） |
| 6–8 | 6. 構件設計 | 1.5–2 | ✅ Member_Design_Draft |
| 8–9 | 7. 玻璃欄杆設計 | 0.5–1 | 待寫 |
| 9 | 8. 底板與錨栓 | 0.5–1 | 待寫 |
| 9–10 | 9. 現有結構檢核 | 0.5 | 待寫 |
| 10 | 10. 臨時支撐 | 0.5 | 待寫 |
| 10–11 | 11. 圖則清單與說明 | 0.5–1 | 待寫 |
| **11–12** | **12. RSE 簽署結論頁** | **1** | **必備** |

**合計**：約 10–12 頁（精簡可壓到 8–9 頁）

---

## Step 2 — 逐章內容清單（寫什麼）

### 封面（Page 1）

| 必含項目 | 說明 |
|----------|------|
| 標題 | MW 1.1 RSE Calculation Report – Erection of Internal Staircase |
| 地址 | Camel Paint Buildings Block 3, K.T.I.L. 53 & 72 (Portion) |
| 文件編號 | 自訂 e.g. MW1.1-RSE-001 |
| 修訂 | Rev. A / 日期 |
| RSE 姓名、註冊編號 | 預留簽署位 |
| 「小型工程監管制度」字樣 | 明確標示 Class I |

### 目錄（Page 2）

列出第 1–12 章 + 附錄（若有 SAP 摘要表）。

### 1. 項目簡介與範圍（Page 2–3）

| 中文 | English |
|------|---------|
| 工程位置與地段 | Location and lot |
| 工程內容（新建鋼樓梯 + 玻璃欄杆） | Scope: new steel stair + glass barrier |
| MW 項目編號 1.1 | MW Item 1.1 |
| 不涉及／涉及事項（逃生、改動主結構等） | What is / is not included |

### 2. 設計準則與引用規範（Page 3）

| 規範 | 用途 |
|------|------|
| MWTGe（技術指引） | 小型工程總則、著色、推薦細節 |
| CoP Dead & Imposed Loads 2011 | 活載、Table 3.13 |
| CoP Structural Use of Steel 2011 | 鋼構件 |
| CoP Structural Use of Glass 2018 | 玻璃欄杆 |
| Buildings Ordinance / B(C)R | 法定框架（簡述） |

### 3–4. 設計數據 + 荷載分析（Page 4–5）

**直接採用** `Loading_Analysis_Draft.md` 精簡版：

- 材料表（S355、玻璃 80 N/mm²）
- 幾何表（L/a/b/c、平台寬）
- 活載表（3.0 kPa、0.75 kN/m、1.0 kPa、0.5 kN）
- 組合 1.4DL+1.6LL → 設計面荷載 7.12 kPa
- 荷載總表 + 簡短假設

### 5. 結構分析摘要（Page 5–6）

| 內容 | 說明 |
|------|------|
| 模型 | SAP2000 三維弧形樓梯 |
| 邊界條件 | 簡述支承／錨固 |
| 結果 | 最大 N/M/V 摘要表（或「見構件設計表」） |
| 手算對照 | 與第 6 章利用率一致 |

### 6. 構件設計（Page 6–8）

**直接採用** `Member_Design_Draft.md` 精簡版：

| 構件 | 截面 | 利用率 | 結果 |
|------|------|--------|------|
| MB1 | UEA 200×100×15 | 0.87 | OK |
| C1 | SHS 80×80×8 | 0.81 | OK |
| SB1 | SHS 70×70×6.3 | 0.09 | OK |

### 7. 玻璃欄杆（Page 8–9）

| 內容 | 要點 |
|------|------|
| 規格 | 12+1.52+12 mm 鋼化夾層 |
| 荷載 | Table 3.13 三類 |
| 檢核 | 應力 ≤ 80 N/mm²；撓度 L/30 |
| 結論 | OK（對應 glass CalcActions） |

### 8. 底板與錨栓（Page 9）

| 內容 | 要點 |
|------|------|
| 錨栓 | Hilti HST3-R M12 |
| 工具 | PROFIS Engineering |
| 利用率 | 約 84% → OK |

### 9. 現有結構檢核（Page 9–10）

- 新增荷載傳至現有 RC
- 結論：容量足夠（簡表或一句 + 依據）

### 10. 臨時支撐（Page 10）

- 施工期支撐／拉結要點
- 指向圖則詳圖

### 11. 圖則清單（Page 10–11）

| 圖號 | 內容 | 著色 |
|------|------|------|
| 如 S-01 | 平面／框架 | Appendix VI |
| 如 S-02 | 剖面／節點 | 鋼構件／玻璃分色 |

### 12. RSE 簽署結論頁（Page 11–12）**【必備】**

| 必含 | 說明 |
|------|------|
| 結構安全聲明 | 設計符合相關 CoP 與 BO |
| 小型工程項目確認 | MW 1.1 |
| 結論 | Adequate / 可施工 |
| RSE 簽名、全名、註冊編號、日期 | 親簽 |
| 公司蓋章（如適用） | — |

---

## Step 3 — 與 CalcAction／已寫草稿的對照

| 報告章節 | 倉庫檔案 / Action |
|----------|-------------------|
| 荷載 | `Loading_Analysis_Draft.md` ← la-01…la-10 |
| 構件 | `Member_Design_Draft.md` ← md-00…md-11 |
| 玻璃+錨栓 | `templates/calc-actions/glass-anchor-calc-actions.md` |
| 引擎邏輯 | `templates/engine/calculation-engine.md` |
| 架構 | `docs/architecture/openmaic-study.md` |

---

## Step 4 — 組裝順序（實操）

```
1. 定封面與文件編號
2. 寫第 1–2 章（簡介 + 規範）—— 半頁～1 頁
3. 貼入精簡版 Loading（第 3–4 章）
4. 寫第 5 章 SAP 摘要表（半頁）
5. 貼入精簡版 Member Design（第 6 章）
6. 補 Glass + Anchor（第 7–8 章）
7. 現有結構 + 臨時支撐（第 9–10 章）
8. 圖則清單（第 11 章）
9. 寫死 RSE 結論頁（第 12 章）
10. 目錄回填頁碼 → 總頁數控制在 8–12
```

---

## Step 5 — 完成標準檢查表（Bootcamp）

| 檢查項 | 是/否 |
|--------|-------|
| 標題含 MW 1.1 | ☐ |
| 引用 MWTGe + 三本 CoP | ☐ |
| 荷載表含 Table 3.13 | ☐ |
| 構件利用率表齊全 | ☐ |
| 假設寫明 | ☐ |
| 圖則著色說明 | ☐ |
| **RSE 親簽結論頁** | ☐ |
| 總頁數 8–12 | ☐ |
| 可重現（公式/來源清楚） | ☐ |

---

## Step 6 — 建議下一步寫作優先序

| 優先 | 任務 |
|------|------|
| 1 | 寫封面 + 第 1–2 章 + RSE 結論頁模板（定框架） |
| 2 | 精簡 Loading / Member 草稿進正式章節字數 |
| 3 | 補 Glass + Anchor 各半頁 |
| 4 | SAP 摘要表 + 現有結構 + 臨時支撐 |
| 5 | 圖則清單與總頁數微調 |

---

**大綱狀態**：Ready for section drafting  
**學習者**：Yip Sze  
**日期**：2026-08-06
