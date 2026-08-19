# 2.2 設計荷載 + 2.3 設計材料
# Design Loading and Design Material

**案例**：W21027 Cooling Tower Supporting Frame  
**日期**：2026-08-18

---

## 2.2 Design Loading

### i. Dead Load

| Item | Value | Unit | Source |
|------|-------|------|--------|
| Density of steelworks | 78 | kN/m³ | CoP Steel 2011 |
| Density of RC works | 24.5 | kN/m³ | CoP |
| Cooling tower size | 1740×3250×3225(H) | mm | Equipment |
| Cooling tower weight | 1500 | kg each | Equipment |
| Pump weight | 100 | kg each | Equipment |

\[
G_{\mathrm{CT}} \approx 1500 \times 9.81 / 1000 \approx 14.7\ \mathrm{kN}
\]

Report uses LL = 15 kN per tower → 15/4 = 3.75 kN per support.

### ii. Design Wind Load

Design net pressure = **5.52 kPa** (HK Wind Code 2019).

\[
p_H = 2.70 \times 1.0 \times 0.85 \times 1.2 \times 2.0 = 5.52\ \mathrm{kPa}
\]

Uplift 6.07 kPa and downward 0.83 kPa are on drawing notes. See `Wind_Load_Formula_Steps.md`.

---

## 2.3 Design Material

Original print alignment is misleading. Correct mapping:

| Item | Value | Unit |
|------|-------|------|
| Steel grade | S275 (Class 1, BS EN 10025) | — |
| Density | 78 | kN/m³ |
| Modulus of elasticity E | 205000 | N/mm² |
| Yield stress | 275 | MPa |
| Design weld strength | 220 | MPa |

Compared with MW 1.1: S355 / py=355 / weld=250 vs this case S275 / 275 / 220.
