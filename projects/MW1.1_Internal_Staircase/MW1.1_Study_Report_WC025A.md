# MW 1.1 Internal Staircase – Study Report
**基於真實案例：Camel Paint Buildings Block 3 (WC025A)**  
**項目編號：MW 1.1（Erection or Alteration of Internal Staircase）**  
**學習日期：2026-07-30**  
**來源文件：WC025A_Part I & II Rev A + Drawing WC025A-1 / WC025A-2**

---

## 1. 項目資料 / Project Information

| 項目 | 內容 |
|------|------|
| 工程名稱 | Proposed New Internal Staircase at Cockloft to 1/F |
| 地址 | Camel Paint Buildings Block 3, 60 Hoi Yuen Road, Kwun Tong |
| 地段 | K.T.I.L. 53 (Portion) & K.T.I.L. 72 (Portion) |
| 文件編號 | WC025A (Part 1 – Main Text and Detail Analysis) |
| 修訂 | Rev. A, 16/07/2025 |
| 工程內容 | 1. 新增 G/F 至閣樓內部鋼樓梯<br>2. 新增玻璃欄杆（沿樓梯及開口） |
| BD 批則 | 2025-12-04 批准信明確要求：**必須以小型工程監管制度提交**（不可單純以 A&A 進行） |

---

## 2. 設計概要 / Design Synopsis

| 中文 | English |
|------|---------|
| 設計準則 | 符合《鋼結構實務守則 2011》 / Code of Practice for the Structural Use of Steel 2011 |
| 荷載路徑 | 恆載 + 活載 + 玻璃欄杆水平荷載 → 鋼構件 → 預埋件／底板 → 現有 RC 結構 |
| 現有結構檢查 | 現有 RC 結構容量經檢核後足夠承擔新增荷載 |
| 分析軟件 | SAP2000 三維模型（曲線樓梯） |

---

## 3. 設計荷載 / Design Loadings

| 荷載項目 | 數值 | 依據 |
|----------|------|------|
| 樓梯／平台活載 | 3.0 kPa | CoP Dead & Imposed Loads 2011 |
| 防護欄杆水平線荷載 | 0.75 kN/m（於 1.1 m 高度） | Table 3.13（人流不預期聚集地方） |
| 防護欄杆均布荷載 | 1.0 kPa | Table 3.13 |
| 防護欄杆集中荷載 | 0.5 kN | Table 3.13 |
| 荷載組合 | 1.4 DL + 1.6 LL | CoP Steel 2011 |

---

## 4. 主要構件（S355） / Main Members

| 構件代號 | 說明 | 截面 | 利用率 |
|----------|------|------|--------|
| **MB1** | 主梁／弦桿（組裝截面） | UEA 200×100×15 + 15 mm 鋼板 | 局部承載力 ≈ 0.87；整體屈曲 ≈ 0.65 → **OK** |
| **C1** | 柱／立柱 | SHS 80×80×8 | 局部承載力 ≈ 0.61；整體屈曲 ≈ 0.81 → **OK** |
| **SB1** | 次梁／平台梁 | SHS 70×70×6.3 | ≈ 0.09 → **OK** |
| **Steps** | 踏步 | 15 mm 鋼板 + 木面層 | — |
| **Glass** | 玻璃欄杆 | 12 + 1.52 PVB + 12 mm 鋼化夾層玻璃 | 符合《玻璃結構實務守則 2018》，應力及撓度（L/30）合格 |
| **Anchor** | 錨栓 | Hilti HST3-R M12 | PROFIS 最高利用率約 84% → **OK** |

---

## 5. 分析與檢核結果 / Analysis Results Summary

### 5.1 鋼構件
- 所有主要構件利用率 < 1.0，符合 CoP Steel 2011 交互作用公式。
- 撓度控制符合要求。

### 5.2 底板 + 錨栓
- 使用 Hilti PROFIS Engineering 計算。
- 最高利用率約 84%，安全。

### 5.3 玻璃欄杆
- 符合 Code of Practice for Structural Use of Glass 2018。
- 應力及撓度（L/30）合格。

### 5.4 現有 RC 結構
- 經檢核足夠承擔新增荷載。

### 5.5 臨時工程
- 圖則已提供施工期間臨時支撐及橫向拉結詳圖。

---

## 6. 圖則重點（WC025A-1 & WC025A-2） / Drawing Key Points

| 項目 | 內容 |
|------|------|
| 平面圖 | G/F 及閣樓關鍵平面、局部框架平面 |
| 立面／剖面 | 立面、剖面 A-A、X-X |
| 節點詳圖 | 踏步連接、對接焊、角焊、玻璃固定、底板、臨時支撐、RC 修補詳圖 |
| 顏色標示 | 紫色：鋼構件；青色：玻璃（符合 MWTGe Appendix VI 著色要求） |
| 材料表 | 鋼材等級、玻璃規格、錨栓型號、焊縫要求清楚 |

---

## 7. 對 Class I 小型工程學習的啟示 / Learning Points for Pure MW Submission

### 優點（可作為參考範本）
- 荷載路徑清晰
- 使用正確的《鋼結構實務守則 2011》交互作用公式
- 附有完整 Hilti PROFIS 錨栓計算
- 圖則有顏色標示、臨時工程及修補詳圖
- 現有結構檢查齊全
- SAP2000 模型結果與手算互相驗證

### 需注意／改進之處（轉為純小型工程提交時）
1. **標題仍以 A&A 結構報告形式書寫** → 純小型工程應明確寫出「小型工程項目 MW 1.1 – Erection of Internal Staircase」
2. 部分構件採用保守檢核（單角鋼代替組裝截面）→ 可接受，但需在報告中說明
3. 需確認實際高度差及對應的小型工程項目編號（參考 MWTGe.pdf Section 3.x）
4. **必須加入 RSE 簽署結論頁** 及明確符合 B(C)R 第 8 及 17 條的聲明
5. 建議加入 Form MW01 / PR4 相關聲明

---

## 8. 建議報告結構（純 MW 1.1 版本）

1. 封面（項目名稱、地址、MW 項目編號、日期、RSE 姓名及註冊編號）
2. 目錄
3. 項目簡介及範圍
4. 設計準則及引用規範（MWTGe + CoP Steel 2011 + CoP Dead & Imposed Loads 2011 + CoP Glass 2018）
5. 荷載計算（含 Table 3.13）
6. 結構分析（SAP2000 結果摘要 + 手算驗證）
7. 構件設計檢核表（MB1、C1、SB1、底板、錨栓、玻璃）
8. 現有結構檢查
9. 臨時支撐及施工注意事項
10. 圖則（著色）
11. **RSE 簽署結論頁**

---

## 9. 結論 / Conclusion

此份 WC025A 計算報告專業完整，結構安全，可作為準備 **Class I 小型工程結構計算報告**（特別是涉及防護欄杆及內部樓梯）的優質參考範本。

下一步建議：
- 以此案例為藍本，撰寫一份純 MW 1.1 格式的完整 RSE Calculation Report（8–12 頁）
- 加入 RSE 簽署結論頁
- 按 MWTGe Appendix VI 著色圖則

---

**RSE 學習簽署（自學記錄）**  
學習者：Yip Sze  
日期：2026-07-30  
狀態：Study Complete → 準備撰寫正式報告
