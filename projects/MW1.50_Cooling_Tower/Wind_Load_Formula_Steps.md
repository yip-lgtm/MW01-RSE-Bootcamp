# 風荷載公式逐步
# Design Wind Load — How to Get 5.52 / 0.83 / 6.07 kPa

**案例**：W21027 Cooling Tower Supporting Frame  
**規範**：CoP Wind Effects in Hong Kong 2019  
**日期**：2026-08-18

---

## 1. 總公式

\[
p = q_{\mathrm{ref}} \times S_t \times S_\theta \times S_s \times C_p
\]

| 符號 | 中文 | English | 本圖取值 |
|------|------|---------|----------|
| \(q_{\mathrm{ref}}\) | 參考風壓 | Wind reference pressure | 2.70 kPa |
| \(S_t\) | 地形係數 | Topographic effect | 1.0 |
| \(S_\theta\) | 方向係數 | Directionality factor | 0.85 |
| \(S_s\) | 尺寸係數 | Size factor | 1.2 |
| \(C_p\) | 風荷載係數 | Pressure coefficient | 2.0 / 0.3 / −2.2 |

---

## 2. 各係數怎樣取

### Step 1 — \(q_{\mathrm{ref}} = 2.70\) kPa

- 圖註：UP TO 70 m FROM SITE GROUND LEVEL
- 查 CoP Wind 2019 **Table 3-1**（平坦開敞地形）
- 有效高度 ≤ 70 m → **2.70 kPa**

### Step 2 — \(S_t = 1.0\)

- 圖註：TOPOGRAPHIC EFFECT St = 1.0
- 查 Appendix A3
- 無山脊／斜坡加速 → **1.0**

### Step 3 — \(S_\theta = 0.85\)

- 圖註：DIRECTIONALITY FACTOR Sθ = 0.85
- 查 Table A1-1
- 本例取 **0.85**

### Step 4 — \(S_s = 1.2\)

- 圖註：SIZE FACTOR Ss = 1.2 (CORNER ZONE)
- 查 Section 5 / Appendix C1
- 小構件 + 角區 → **1.2**

### Step 5 — \(C_p\)

| 工況 | \(C_p\) |
|------|---------|
| Horizontal | 2.0 |
| Downward | 0.3 |
| Uplift | −2.2（公式用 2.2） |

來源：Section 4（独立設備／角區係數）

---

## 3. 代入得三個設計風壓

**Horizontal**

\[
p_H = 2.70 \times 1.0 \times 0.85 \times 1.2 \times 2.0 = 5.52\ \mathrm{kPa}
\]

**Downward**

\[
p_{\mathrm{dn}} = 2.70 \times 1.0 \times 0.85 \times 1.2 \times 0.3 = 0.83\ \mathrm{kPa}
\]

**Uplift**

\[
p_{\mathrm{up}} = 2.70 \times 1.0 \times 0.85 \times 1.2 \times 2.2 = 6.07\ \mathrm{kPa}
\]

---

## 4. 用到架體上（每支承）

冷卻塔：1.74 × 3.25 × 3.225(H) m；4 個支承

| 工況 | 面積 | 每點力 |
|------|------|--------|
| Wx | 1.74×3.225 = 5.61 m² | 水平 7.74 kN；傾覆竪向 8.77 kN |
| Wz | 3.25×3.225 = 10.48 m² | 水平 14.46 kN；傾覆竪向 26.81 kN |
| Wup | 1.74×3.25 = 5.655 m² | 8.58 kN |
| Wdn | 5.655 m² | 1.17 kN |
| 構件線載載 | 寬 0.152 m | 5.52×0.152 = 0.84 kN/m |

**Wx 水平**

\[
V_{x,i} = 5.52 \times 5.61 / 4 = 7.74\ \mathrm{kN}
\]

**Wz 水平（控制）**

\[
V_{z,i} = 5.52 \times 10.48 / 4 = 14.46\ \mathrm{kN}
\]

**Wz 傾覆竪向**

\[
F_{V,z} = 5.52 \times 10.48 \times 3.225 / 2 / 1.74 / 2 = 26.81\ \mathrm{kN}
\]

**上拔**

\[
F_{\mathrm{up},i} = 6.07 \times 5.655 / 4 = 8.58\ \mathrm{kN}
\]

**下壓**

\[
F_{\mathrm{dn},i} = 0.83 \times 5.655 / 4 = 1.17\ \mathrm{kN}
\]

---

## 5. 組合

| 編號 | 公式 |
|------|------|
| 13 | 1.2 DL + 1.2 LL + 1.2 Wx |
| 14 | 1.2 DL + 1.2 LL + 1.2 Wz（控制） |
| 15 | 1.0 DL + 1.0 LL + 1.4 Wup |
| 16 | 1.2 DL + 1.2 LL + 1.2 Wdn |

---

## 6. 寫報告要核

| 檢查 | 說明 |
|------|------|
| 高度 | Table 3-1 所用有效高度是否 ≤ 70 m |
| 角區 | Ss = 1.2 是否真為 corner zone |
| Cp | 是否適用独立設備 |

---

**對應**：`MW1.50_Full_Report_Outline.md` 第 5 章荷載  
**學習者**：Yip Sze  
**日期**：2026-08-18
