# 4. Loading Analysis
# 4. 荷載分析

**Document**: MW 1.1 RSE Calculation Report  
**Project**: Internal Staircase, Camel Paint Buildings Block 3  
**Status**: Formal chapter (condensed from CalcAction draft)

---

## 4.1 Design Data / 設計數據

| Item 項目 | Value 數值 | Unit | Source 來源 |
|-----------|------------|------|-------------|
| Steel grade 鋼材等級 | S355 | — | CoP Steel 2011 |
| Density 密度 | 7850 | kg/m³ | CoP Steel 2011 |
| Modulus of elasticity E | 205000 | N/mm² | CoP Steel 2011 |
| Design strength py | 355 | N/mm² | CoP Steel 2011 |
| Weld design strength | 250 | N/mm² | CoP Steel 2011 |
| Glass permissible stress | 80 | N/mm² | CoP Glass 2018 |

---

## 4.2 Geometry / 幾何

| Item 項目 | Symbol | Value | Unit |
|-----------|--------|-------|------|
| Tread length 踏步長度 | L | 1400 | mm |
| Riser height 踢腳高度 | a | 175 | mm |
| Inner tread 內側踏面 | b | 230 | mm |
| Outer tread 外側踏面 | c | 420 | mm |
| Intermediate landing (inner/outer) | — | 900 / 1685 | mm |
| Top landing (inner/outer) | — | 1200 / 2000 | mm |

Average tread width = (b + c) / 2 = 325 mm.  
Approx. plan area per step ≈ 1.40 × 0.325 = **0.455 m²**.

---

## 4.3 Imposed Loads / 活荷載

| Load Item 荷載項目 | Value | Unit | Reference |
|--------------------|-------|------|-----------|
| Staircase / landing live load | 3.0 | kPa | CoP Dead & Imposed Loads 2011 |
| Barrier line load @ 1.1 m | 0.75 | kN/m | Table 3.13 |
| Barrier UDL | 1.0 | kPa | Table 3.13 |
| Barrier concentrated load | 0.5 | kN | Table 3.13 |

**Code reference**: CoP for Dead and Imposed Loads 2011, Table 3.13 – Protective barriers (areas not susceptible to overcrowding).

---

## 4.4 Dead Loads / 恆載

**Step / landing surface**

| Component | Calculation | Result |
|-----------|-------------|--------|
| 15 mm steel plate | 0.015 × 77 kN/m³ | 1.16 kPa |
| Timber finish (assumed) | — | 0.50 kPa |
| **Total surface DL** | — | **1.66 kPa** |
| DL per step (approx.) | 1.66 × 0.455 | **0.76 kN** |

**Landings (approx.)**

| Landing | Area (approx.) | DL |
|---------|----------------|-----|
| Intermediate | 1.3 m² | ≈ 2.2 kN |
| Top | 2.0 m² | ≈ 3.3 kN |

> Precise areas governed by SAP2000 geometry / drawings.

---

## 4.5 Glass Balustrade Loads / 玻璃欄杆荷載

Assumed balustrade length ≈ 4.5 m (to be confirmed on drawing).

| Type | Characteristic value | Application |
|------|----------------------|-------------|
| Line load @ 1.1 m | 0.75 kN/m | Horizontal on posts / stringers |
| UDL | 1.0 kPa | Height of barrier |
| Concentrated | 0.5 kN | Most unfavourable position |

Design checks use the envelope of the three cases.

---

## 4.6 Load Combination / 荷載組合

Vertical design load:

\[
W_d = 1.4 G_k + 1.6 Q_k = 1.4 \times 1.66 + 1.6 \times 3.0 = \mathbf{7.12\ kPa}
\]

| Surface | Gk (kPa) | Qk (kPa) | Wd (kPa) |
|---------|----------|----------|----------|
| Step / landing | 1.66 | 3.0 | **7.12** |

---

## 4.7 Load Summary / 荷載總表

| Item | DL | LL | Unit | Remark |
|------|----|----|------|--------|
| Step / landing surface | 1.66 | 3.0 | kPa | — |
| **Design UDL** | — | — | **7.12 kPa** | 1.4DL+1.6LL |
| Barrier line load | — | 0.75 | kN/m | Table 3.13 |
| Barrier UDL | — | 1.0 | kPa | Table 3.13 |
| Barrier point load | — | 0.5 | kN | Table 3.13 |

---

## 4.8 Assumptions / 假設

1. Finish load taken as 0.5 kPa; adjust if finishes differ.  
2. Step and landing areas are hand estimates; SAP2000 / drawings govern.  
3. Balustrade length 4.5 m illustrative; measure from drawings for final.  
4. Internal staircase: wind load not applied.  
5. Vertical combination: 1.4DL + 1.6LL throughout.
