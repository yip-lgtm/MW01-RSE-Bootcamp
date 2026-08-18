# MW 1.50 完整 RSE 計算報告大綱
# Complete RSE Calculation Report Outline (8–12 Pages)

**項目 Item**：MW 1.50 – Erection of Supporting Structure for BSI on Roof  
**參考案例**：W21027 Cooling Tower Supporting Frame, R/F 18 Kwai Hei Street  
**目標頁數**：8–12 頁  
**原則**：可重現、可審批；公式／表格／假設清楚；引用 MWTGe + CoP；RSE 親簽結論頁  
**日期**：2026-08-18

---

## Step 0 — 先鎖定 1.50 合規

| 中文 | English |
|------|---------|
| Class I 站設／改動 | Class I erection / alteration |
| 位置：地面／簷篷／天台 | On-grade / canopy / roof |
| 禁止懸臂板 | Other than a cantilevered slab |
| 一般 BSI 架高 ≤ 1.5 m | Height ≤ 1.5 m for typical BSI |
| 天線／收發器 ≤ 2.5 m | Height ≤ 2.5 m for antenna / transceiver |
| 不改動其他結構構件 | No alteration of other structural elements |
| 不涉及 3.50 | Not involve item 3.50 |

**建議文件名**

`MW1.50_Cooling_Tower_RSE_Report_RevA.pdf`

---

## Step 1 — 頁數總表（配置）

| 頁碼 | 章節 | 建議頁數 | W21027 依據 |
|------|------|----------|----------------|
| 1 | 封面 Cover | 1 | 封面 + RSE 欄 |
| 2 | 目錄 + 項目簡介 | 1 | 第 1 節 |
| 3 | 設計準則與 1.50 符合性 | 0.5–1 | 第 2 節 |
| 3–4 | 設計數據（材料／設備） | 0.5 | 第 2.2–2.3 節 |
| 4 | 現有結構檢核 | 0.5 | 第 3 節 |
| 4–6 | 荷載分析（恒載／活載／風） | 1.5–2 | p.2–4 |
| 6–8 | 構件設計 + 擻度 | 1.5–2 | p.5–7 |
| 8 | 焊縫與底板 | 0.5 | p.8 |
| 8–9 | 錨栓 | 0.5–1 | PROFIS |
| 9 | 穩定性 λcr | 0.5 | p.12 |
| 10 | 水泵座（若納入） | 0.5 | 圖則 plinth |
| 10–11 | 圖則清單 | 0.5–1 | Fr1 + Fr |
| **11–12** | **RSE 簽署結論頁** | **1** | **必備** |

**合計**：約 10–12 頁（精簡可壓到 8–9 頁）

---

## Step 2 — 逐章寫什麼

### 封面（Page 1）

| 必含 | 說明 |
|----------|------|
| 標題 | MW 1.50 RSE Calculation Report – Supporting Frame for Cooling Towers |
| 地址 | R/F, 18 Kwai Hei Street, Kwai Chung（或自己項目地址） |
| 文件編號 | e.g. MW1.50-RSE-001 |
| 修訂 | Rev. A / 日期 |
| RSE 姓名、註冊編號 | 預留簽署 |
| Class I 字樣 | 明確標示小型工程監管制度 |

### 1. 項目簡介與範圍（Page 2）

| 中文 | English |
|------|---------|
| 工程內容 | 9 座冷卻塔鋼支撐架 + 9 個水泵混凝土座 |
| MW 項目 | Item 1.50 |
| 位置 | 天台，非懸臂板 |
| 不包含 | 不改動母體結構；不涉及外牆挑架（1.28） |

### 2. 設計準則與引用規範（Page 3）

| 規範 | 用途 |
|------|------|
| MWTGe | 小型工程總則、著色 |
| CoP Steel 2011 | 鋼構件 |
| CoP Wind Effects 2019 | 風荷載 |
| CoP Dead & Imposed Loads 2011 | 活載（維修） |
| B(MW)R Schedule 1 | Item 1.50 定義 |

### 3. 設計數據（Page 3–4）

| 項目 | 數值（本案例） |
|------|----------------------|
| 鋼材 | S275；ρ=78 kN/m³；E=205000 N/mm²；py=275 MPa |
| 焊縫 | 220 MPa |
| 冷卻塔 | 1740×3250×3225(H) mm；1500 kg |
| 水泵 | 100 kg |
| 設計淨風壓 | 5.52 kPa |
| 主截面 | UC 152×152×23 |

### 4. 現有結構（Page 4）

- 新增荷載傳至現有天台梁／板  
- 結論：容量足夠；**無須加固母體**

### 5. 荷載分析（Page 4–6）

**必寫**

- DL：架自重（STAAD）+ 設備重  
- LL：15 kN / 台 → 3.75 kN / 支承  
- Wx：面積 5.61 m²；水平 7.74 kN；傾覆竪向 8.77 kN  
- Wz：面積 10.48 m²；水平 14.46 kN；傾覆竪向 26.81 kN  
- Wup / Wdn：8.58 / 1.17 kN  
- 組合 12–16（含風 ULS）

### 6. 構件設計（Page 6–8）

| 構件 | 截面 | 控制組合 | 結果 |
|------|------|----------|------|
| SP1/SB1/SB2 | UC 152×152×23 | D+L+Wz | OK |
| 軸力（ULS） | 39.1 kN | — | — |
| 彎矩 | 16.1 kNm | — | — |
| 剪力 | 38.4 kN | — | — |
| 擻度 | 水平 3.42 / 2.34 mm < L/200 | — | OK |

### 7. 焊縫與底板（Page 8）

| 項目 | 結果 |
|------|------|
| 5 mm FWAR 構件焊 | 174.3 < 220 MPa → OK |
| 5 mm FWAR 底板焊 | 84 < 220 MPa → OK |

### 8. 錨栓（Page 8–9）

| 項目 | 結果 |
|------|------|
| 型號 | Hilti HST3-R M12 × 4 |
| PROFIS | 綜合利用率約 88% → OK |

### 9. 穩定性（Page 9）

- λcr = 350 ≥ 10 → 非側移框架

### 10. 水泵座（Page 10）

- 9 個 RC plinth；荷載 100 kg；現有板承載

### 11. 圖則清單（Page 10–11）

| 圖號 | 內容 | 著色 |
|------|------|------|
| Fr1 | First Roof Framing Plan 1:100 | Appendix VI |
| Fr | Supporting Framing + Details | 新鋼構著色 |

### 12. RSE 簽署結論頁（Page 11–12）

| 必含 | 說明 |
|------|------|
| 符合 MW 1.50 | 位置、高度、不改動母體 |
| 符合 CoP Steel + Wind | 構件、風、錨栓足夠 |
| 結論 Adequate | 可施工 |
| RSE 簽名、全名、註冊編號、日期 | 親簽 |

---

## Step 3 — 組裝順序

```
1. 定封面與文件編號
2. 寫第 1–2 章（簡介 + 1.50 符合性 + 規範）
3. 貼材料表 + 設備表
4. 寫荷載章（必有風公式）
5. 貼構件總表 + 擻度
6. 焊縫 + 錨栓 + λcr
7. 圖則清單
8. 寫死 RSE 結論頁
9. 目錄回填頁碼 → 總頁 8–12
```

---

## Step 4 — 完成檢查表

| 檢查項 | 是/否 |
|--------|-------|
| 標題含 MW 1.50 | ☐ |
| 證明非懸臂天台 | ☐ |
| 架高 ≤ 1.5 m | ☐ |
| 引用 Steel + Wind + MWTGe | ☐ |
| 風壓與投影面積公式 | ☐ |
| 構件 OK 表 | ☐ |
| 錨栓 PROFIS | ☐ |
| 現有結構聲明 | ☐ |
| 圖則著色說明 | ☐ |
| **RSE 親簽結論頁** | ☐ |
| 總頁數 8–12 | ☐ |

---

## Step 5 — 與已有檔案

| 內容 | 位置 |
|------|------|
| 本大綱 | `projects/MW1.50_Cooling_Tower/MW1.50_Full_Report_Outline.md` |
| 舊簡報 | `projects/MW1.50_Supporting_Structure_AC/MW1.50_Report.md` |
| 參考 PDF | `REFERENCES/MW1.50_W21027_Cooling_Tower_...` |

---

**大綱狀態**：Ready for section drafting  
**學習者**：Yip Sze  
**日期**：2026-08-18
