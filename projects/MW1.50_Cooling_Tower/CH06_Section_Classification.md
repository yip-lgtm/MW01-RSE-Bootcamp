# Section Classification Class 1 / 2 / 3 / 4
# 截面分類（CoP Steel 2011）

**案例**：W21027 UC 152×152×23 S275  
**日期**：2026-08-20

---

## 1. 四等級

| Class | 中文 | English | 能做到 | 抗彎 |
|-------|------|---------|----------|------|
| 1 | 塑性 | Plastic | 全塑性銳 + 塑性鉸 | \(p_y S\) |
| 2 | 密實 | Compact | 到 \(M_p\)，轉角不足 | \(p_y S\) |
| 3 | 半密實 | Semi-compact | 只到屈服 \(M_y\) | \(p_y Z\) |
| 4 | 細長 | Slender | 屈服前局部屈曲 | \(p_y Z_{\mathrm{eff}}\) |

\[
\varepsilon = \sqrt{275 / p_y}
\]

S275 → \(\varepsilon = 1\). S355 → \(\varepsilon \approx 0.88\).

---

## 2. 熱軋工字 / UC 翼緣限值 \(b/T\)

| Class | Limit |
|-------|-------|
| 1 | \(\le 9\varepsilon\) |
| 2 | \(\le 10\varepsilon\) |
| 3 | \(\le 15\varepsilon\) |
| 4 | \(> 15\varepsilon\) |

Welded outstand: 8ε / 9ε / **13ε**.

This sheet printed 9ε and 13ε (welded Class 3). UC is rolled; rolled Class 3 is 15ε. Result unchanged.

---

## 3. 腹板限值 \(d/t\)（中性軸居中）

| Class | Limit |
|-------|-------|
| 1 | \(\le 80\varepsilon\) |
| 2 | \(\le 100\varepsilon\) |
| 3 | \(\le 120\varepsilon\) |
| 4 | \(> 120\varepsilon\) |

70ε is **shear buckling exemption**, not classification.

---

## 4. This case — SP1/SB1/SB2

\[
b/T = 11.19,\quad d/t = 21.31,\quad \varepsilon = 1
\]

| Part | Ratio | Class |
|------|-------|-------|
| Flange | 10 < 11.19 < 15 | Class 3 |
| Web | 21.31 < 80 | Class 1 |
| **Section** | worst part | **Class 3** |

Use \(M_c = p_y Z\), not \(p_y S\).

Web \(d/t = 21.31 < 70\) → shear buckling need not be checked.
