# SP1/SB1/SB2 — Design Data, Classification, Shear (P.1)
# D+L+Wx · UC 152×152×23 S275

**日期**：2026-08-20

---

## 1.1 Design forces (factored, STAAD combo 13)

| Symbol | Meaning | Value |
|--------|---------|-------|
| Fc | Axial (tension −ve) | 22.2 kN |
| Mxx | Moment about x | 8.8 kNm |
| Myy | Moment about y | 8.8 kNm |
| Vx | Shear x | 10.6 kN |
| Vy | Shear y | 15.4 kN |

## 1.2 Effective length

\(L_x = L_y = 3\) m

## 1.3 Stiffener spacing

\(a = 0\) mm

## 2.0 Section — UC 152×152×23

D=152.4 mm, B=152.2 mm, t=5.8 mm, T=6.8 mm, d=123.6 mm  
A=29.2 cm², Ix=1250 cm⁴, Iy=400 cm⁴, Zx=164 cm³, Zy=52.6 cm³

## 3.0 Classification

\(p_y = 275\) MPa, \(\varepsilon = 1\)

\(b/T = 11.19\) → Class 3 flange  
\(d/t = 21.31 < 80\varepsilon\) → Class 1 web  
**Section Class 3**

## 4.0 Shear

\[
V_c = p_y A_v / \sqrt{3}
\]

\(V_{cx} = 328.6\) kN > 10.6 kN OK  
\(V_{cy} = 140.3\) kN > 15.4 kN OK

## 5.0 Web shear buckling

\(d/t = 21.31 < 70\varepsilon\) → check not required

Note: D+L+Wz is more onerous (Fc=39.1 kN, M=16.1 kNm, V=38.4 kN).
