# 4. Loading Analysis / 荷載分析

**項目**：Internal Staircase at Cockloft to 1/F, Camel Paint Buildings Block 3  
**文件**：WC025A  
**章節草稿**：依 CalcAction 序列 `la-01` → `la-10` 重寫  
**日期**：2026-08-06  
**狀態**：Draft（可重現、可審批）

---

## 4.1 Design Data / 設計數據

> Action: `define_design_data` (la-01)

| 項目 Item | 數值 Value | 單位 Unit | 來源 Source |
|-----------|------------|-----------|-------------|
| 鋼材等級 Steel grade | S355 | — | CoP Steel 2011 |
| 鋼材密度 Density | 7850 | kg/m³ | CoP Steel 2011 |
| 彈性模量 E | 205000 | N/mm² | CoP Steel 2011 |
| 設計強度 py | 355 | N/mm² | CoP Steel 2011 |
| 焊縫設計強度 Weld strength | 250 | N/mm² | CoP Steel 2011 |
| 鋼化玻璃允許應力 Tempered glass permissible stress | 80 | N/mm² | CoP Glass 2018 |

**Ledger**

```
[la-01] define_design_data → OK
outputs: { steelGrade: "S355", steelDensity: 7850, steelE: 205000, steelPy: 355, weldStrength: 250, glassPermissibleStress: 80 }
```

---

## 4.2 Geometry / 幾何尺寸

> Action: `define_geometry` (la-02)

| 項目 Item | 符號 | 數值 Value | 單位 |
|-----------|------|------------|------|
| 踏步長度 Tread length | L | 1400 | mm |
| 踢腳高度 Riser | a | 175 | mm |
| 內側踏面寬 Inner tread | b | 230 | mm |
| 外側踏面寬 Outer tread | c | 420 | mm |
| 中間平台內側寬 Intermediate landing (inner) | — | 900 | mm |
| 中間平台外側寬 Intermediate landing (outer) | — | 1685 | mm |
| 頂部平台內側寬 Top landing (inner) | — | 1200 | mm |
| 頂部平台外側寬 Top landing (outer) | — | 2000 | mm |

**假設 Assumptions**

- 踏步有效面積按平均踏面寬估算：\((b+c)/2 = 325\) mm  
- 單一踏步平面面積約：\(1.400 \times 0.325 = 0.455\,\mathrm{m}^2\)（後續可依實際弧形微調）

**Ledger**

```
[la-02] define_geometry → OK
outputs: { L: 1400, a: 175, b: 230, c: 420, landings: { intermediate: [900,1685], top: [1200,2000] } }
```

---

## 4.3 Imposed Loads / 活荷載定義

> Action: `define_imposed_loads` (la-03) + `ref_cop` (la-04)

| 荷載項目 Load Item | 數值 Value | 單位 | 規範依據 Reference |
|--------------------|------------|------|---------------------|
| 樓梯／平台活荷載 Staircase / Landing LL | 3.0 | kPa | CoP Dead & Imposed Loads 2011 |
| 防護欄杆水平線荷載 Line load @ 1.1 m | 0.75 | kN/m | Table 3.13 |
| 防護欄杆均布荷載 UDL (floor to top rail) | 1.0 | kPa | Table 3.13 |
| 防護欄杆集中荷載 Concentrated load | 0.5 | kN | Table 3.13 |

**規範引用 Code Reference**

- Code of Practice for Dead and Imposed Loads 2011, **Table 3.13** – Protective barriers  
- 適用於「人流不預期大量聚集」之位置（內部樓梯／平台）

**Ledger**

```
[la-03] define_imposed_loads → OK
[la-04] ref_cop → OK (Dead & Imposed Loads 2011, Table 3.13)
```

---

## 4.4 Dead Loads – Steps / 踏步自重

> Action: `calc_step_self_weight` (la-05)

**計算 Calculation**

| 項目 | 公式 / 數值 | 結果 |
|------|-------------|------|
| 鋼踏板厚度 | 15 mm | — |
| 鋼密度 | 7850 kg/m³ ≈ 77 kN/m³ | — |
| 鋼踏板自重 | \(0.015 \times 77 = 1.155\) kPa | 1.16 kPa |
| 木面層（假設） | 0.50 kPa | 0.50 kPa |
| **踏步總面荷載** | — | **1.66 kPa** |
| 單一踏步面積（估） | 0.455 m² | — |
| **單一踏步恆載** | \(1.66 \times 0.455\) | **≈ 0.76 kN** |

> 註：弧形樓梯實際面積以 SAP2000 模型為準；本節為可審批手算對照。

**Ledger**

```
[la-05] calc_step_self_weight → OK
outputs: { deadLoadPerStep_kN: 0.76, udl_kPa: 1.66 }
```

---

## 4.5 Dead Loads – Landings / 平台自重

> Action: `calc_landing_self_weight` (la-06, la-07)

### 中間平台 Intermediate Landing

| 項目 | 數值 |
|------|------|
| 估算面積 | 約 \(1.3\) m²（依 900–1685 mm 寬度與深度） |
| 鋼平台 + 面層 | 取 1.66 kPa（同踏步邏輯） |
| **中間平台恆載** | \(1.66 \times 1.3 \approx 2.2\) kN |

### 頂部平台 Top Landing

| 項目 | 數值 |
|------|------|
| 估算面積 | 約 \(2.0\) m²（依 1200–2000 mm） |
| **頂部平台恆載** | \(1.66 \times 2.0 \approx 3.3\) kN |

**Ledger**

```
[la-06] calc_landing_self_weight (intermediate) → OK  { deadLoad_kN: 2.2 }
[la-07] calc_landing_self_weight (top) → OK           { deadLoad_kN: 3.3 }
```

---

## 4.6 Glass Balustrade Loads / 玻璃欄杆荷載

> Action: `calc_glass_loads` (la-08)

**假設**：欄杆總長（沿樓梯外側 + 平台）取約 **4.5 m**（可依圖則精調）。

| 荷載類型 | 計算 | 結果 |
|----------|------|------|
| 水平線荷載 @ 1.1 m | \(0.75 \,\mathrm{kN/m} \times 4.5\,\mathrm{m}\) | **3.38 kN**（總水平力） |
| 均布荷載 1.0 kPa | 作用於欄杆高度範圍（設計時作面荷載／等效） | 1.0 kPa |
| 集中荷載 0.5 kN | 最不利位置 | 0.5 kN |

**設計採用**

- 線荷載 0.75 kN/m 與 UDL 1.0 kPa、集中 0.5 kN 分別檢核，取包絡。  
- 水平荷載傳至立柱 C1 及主弦 MB1。

**Ledger**

```
[la-08] calc_glass_loads → OK
outputs: { lineLoad_kN_per_m: 0.75, totalLine_kN: 3.38, udl_kPa: 1.0, point_kN: 0.5 }
```

---

## 4.7 Load Combination / 荷載組合

> Action: `combine_loads` (la-09)

**基本組合（垂直荷載）**

\[
W_d = 1.4\,G_k + 1.6\,Q_k
\]

| 區域 | Gk（恆載） | Qk（活載） | 設計荷載 Wd |
|------|------------|------------|-------------|
| 踏步面 | 1.66 kPa | 3.0 kPa | \(1.4\times1.66 + 1.6\times3.0 = 7.12\) kPa |
| 平台面 | 1.66 kPa | 3.0 kPa | **7.12 kPa** |

**水平（欄杆）**

- 線荷載設計值：\(1.6 \times 0.75 = 1.20\) kN/m（若僅活載主導；實際依 CoP 組合規則與工程判斷）  
- 本報告垂直組合採 **1.4 DL + 1.6 LL**；水平欄杆荷載按 Table 3.13 特徵值再組合。

**Ledger**

```
[la-09] combine_loads → OK
outputs: { combination: "1.4DL+1.6LL", designUDL_kPa: 7.12 }
```

---

## 4.8 Load Summary Table / 荷載總表

> Action: `write_load_summary` (la-10)

| 項目 Item | 恆載 DL | 活載 LL | 單位 | 備註 Remark |
|-----------|---------|---------|------|-------------|
| 踏步面荷載 Step surface | 1.66 | 3.0 | kPa | 鋼板 15 mm + 面層 |
| 平台面荷載 Landing surface | 1.66 | 3.0 | kPa | 同上 |
| 設計面荷載 Design UDL | — | — | **7.12 kPa** | 1.4DL+1.6LL |
| 欄杆線荷載 Line load @ 1.1 m | — | 0.75 | kN/m | Table 3.13 |
| 欄杆 UDL | — | 1.0 | kPa | Table 3.13 |
| 欄杆集中荷載 | — | 0.5 | kN | Table 3.13 |
| 單一踏步恆載（估） | 0.76 | — | kN | 手算對照 |
| 中間平台恆載（估） | 2.2 | — | kN | 手算對照 |
| 頂部平台恆載（估） | 3.3 | — | kN | 手算對照 |

**Ledger**

```
[la-10] write_load_summary → OK
All loading actions la-01 … la-10 completed.
```

---

## 4.9 假設與限制 Assumptions & Limitations

| 中文 | English |
|------|---------|
| 踏步／平台面積為手算估算，精確值以 SAP2000 幾何為準 | Step/landing areas are hand estimates; SAP2000 geometry governs |
| 面層取 0.5 kPa，實際按裝修圖調整 | Finish load 0.5 kPa; adjust per finishes |
| 欄杆長度 4.5 m 為示例，須對圖則量度 | Balustrade length 4.5 m illustrative; measure from drawings |
| 垂直組合固定為 1.4DL+1.6LL | Vertical combination fixed as 1.4DL+1.6LL |
| 本節不包含風荷載（內部樓梯） | No wind load (internal staircase) |

---

## 4.10 下一步 Next Section

- **5. Structural Analysis** — SAP2000 結果摘要 + 手算對照  
- **6. Member Design** — 依 `member-design-calc-actions.md` 序列（MB1 / C1 / SB1）

---

**章節狀態**：Draft v1 — 可重現、公式與表格齊全、已對應 CalcAction Ledger  
**對應模板**：`templates/engine/loading-sequence-wc025a.md`  
**學習者**：Yip Sze  
**日期**：2026-08-06
