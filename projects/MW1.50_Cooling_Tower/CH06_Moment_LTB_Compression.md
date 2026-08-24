# SP1/SB1/SB2 — Moment, LTB, Compression, Interaction
# D+L+Wz (governing) · UC 152×152×23 S275

**案例**：W21027  
**日期**：2026-08-24

---

## Design forces (ULS D+L+Wz)

| Item | Value |
|------|-------|
| Fc | 39.1 kN |
| Mxx | 16.1 kNm |
| Myy | 0.1 kNm |
| Vy | 38.4 kN (ref) |

---

## Rule 1 — Low shear + Class 3 → Mc = py Z

\[
\frac{V}{V_c} \le 0.6 \Rightarrow \text{no moment reduction}
\]

Class 3:

\[
M_c = p_y Z
\]

| Axis | V/Vc | Z | Mc | Applied | Result |
|------|------|---|-----|---------|--------|
| Major (x) | 0.274 | 164 cm³ | 45.1 kNm | 16.1 | OK |
| Minor (y) | 0 | 52.6 cm³ | 14.46 kNm | 0.1 | OK |

\[
p_y Z_x = 275 \times 164 \times 10^{-3} = 45.1\ \mathrm{kNm}
\]

---

## Rule 2 — LTB uses pb Z, not py Z

\[
\lambda_{LT} = u\, v\, \lambda \sqrt{\beta_w}
\]

| Symbol | Value |
|--------|-------|
| Le/ry | 81.08 |
| u | 0.84 |
| v | 0.87 |
| βw | 0.9 |
| λLT | 56 |
| pb | 222 MPa |
| mLT | 1 |

\[
M_b = p_b Z_x = 222 \times 164 \times 10^{-3} = 36.41\ \mathrm{kNm}
\]

\[
36.41 > 16.1\ \mathrm{kNm} \quad \mathbf{OK}
\]

Note: Mb < Mcx (36.41 < 45.1) because pb < py.

---

## Rule 3 — Compression uses weak-axis λ → pc

| Item | Value |
|------|-------|
| Le/rx | 46 |
| Le/ry | 81 |
| λ governing | 81 |
| Curve | b |
| pc | 178 MPa |

\[
P_c = p_c A = 178 \times 29.2 \times 0.1 = 519.8\ \mathrm{kN}
\]

\[
519.8 > 39.1\ \mathrm{kN} \quad \mathbf{OK}
\]

---

## Rule 4 — Interaction sum ≤ 1

\[
\frac{F_c}{P_c} + \frac{M_x}{M_{cx}} + \frac{M_y}{M_{cy}} \le 1.0
\]

\[
\frac{39.1}{519.8} + \frac{16.1}{45.1} + \frac{0.1}{14.46} = 0.08 + 0.36 + 0.01 = 0.45
\]

\[
0.45 \le 1.0 \quad \mathbf{OK}
\]

---

## Path

```
V/Vc ≤ 0.6?
  → Class 3 → Mc = py Z
  → λLT → pb → Mb = pb Z
  → weak-axis λ → pc → Pc = pc A
  → Fc/Pc + Mx/Mcx + My/Mcy ≤ 1
  → Pass
```

## Summary

| Check | Capacity | Design | Result |
|-------|----------|--------|--------|
| Mcx | 45.1 kNm | 16.1 | OK |
| Mcy | 14.46 kNm | 0.1 | OK |
| Mb | 36.41 kNm | 16.1 | OK |
| Pc | 519.8 kN | 39.1 | OK |
| Interaction | — | 0.45 | OK |
