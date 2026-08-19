# 2.1 Loading on the Steel Frame + 2.2 Check Deflection

**案例**：W21027  
**日期**：2026-08-19

---

## DL

Frame self-weight assessed by STAAD.

## LL

\[
15\ \mathrm{kN}/4 = 3.75\ \mathrm{kN}
\]

## Wx

\[
A_x = 1.74 \times 3.225 = 5.61\ \mathrm{m^2}
\]
\[
V_x = 5.52 \times 5.61 / 4 = 7.74\ \mathrm{kN}
\]
\[
F_{V,x} = 5.52 \times 5.61 \times 3.225 / 2 / 2.848 / 2 = 8.77\ \mathrm{kN}
\]
\[
w = 5.52 \times 0.152 = 0.84\ \mathrm{kN/m}
\]

## Wz (governing)

\[
A_z = 3.25 \times 3.225 = 10.48\ \mathrm{m^2}
\]
\[
V_z = 5.52 \times 10.48 / 4 = 14.46\ \mathrm{kN}
\]
\[
F_{V,z} = 5.52 \times 10.48 \times 3.225 / 2 / 1.74 / 2 = 26.81\ \mathrm{kN}
\]

Same member line load 0.84 kN/m.

## Wup / Wdn

\[
A_{\mathrm{plan}} = 1.74 \times 3.25 = 5.655\ \mathrm{m^2}
\]
\[
F_{\mathrm{up}} = 6.07 \times 5.655 / 4 = 8.58\ \mathrm{kN}
\]
\[
F_{\mathrm{dn}} = 0.83 \times 5.655 / 4 = 1.17\ \mathrm{kN}
\]

## Per-support summary

| Case | Horizontal | Vertical |
|------|------------|----------|
| LL | — | 3.75 kN |
| Wx | 7.74 kN | ±8.77 kN |
| Wz | 14.46 kN | ±26.81 kN |
| Wup | — | 8.58 kN up |
| Wdn | — | 1.17 kN down |

## Deflection

Limit = L/200.

| Direction | Calculated | Allowable | Result |
|-----------|------------|-----------|--------|
| Horizontal X | 3.42 mm | 4.25 mm | OK |
| Horizontal Z | 2.34 mm | 4.25 mm | OK |
| Vertical | 0.28 mm | 12.74 mm | OK |

Horizontal L = 4.25×200 = 850 mm.  
Vertical L = 12.74×200 = 2548 mm.
