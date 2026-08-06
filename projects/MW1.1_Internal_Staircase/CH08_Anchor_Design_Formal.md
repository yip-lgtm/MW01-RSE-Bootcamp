# 8. Base Plate and Anchor Design
# 8. 底板與錨栓設計

**Document**: MW 1.1 RSE Calculation Report  
**Anchor**: Hilti HST3-R M12  
**Software**: Hilti PROFIS Engineering  
**Status**: Formal chapter (report-ready)

---

## 8.1 Design Basis / 設計依據

| Item 項目 | Content 內容 |
|-----------|--------------|
| Purpose | Transfer forces from posts / base plates to existing RC |
| Anchor product | **Hilti HST3-R M12** |
| Design tool | Hilti PROFIS Engineering |
| Substrate | Existing reinforced concrete (verified capacity) |

Load path: glass / steps → steel members → base plate → anchors → existing RC.

---

## 8.2 Anchor Specification / 錨栓規格

| Item 項目 | Value 數值 |
|-----------|------------|
| Brand / model | Hilti HST3-R M12 |
| Diameter | M12 |
| Typical use | Base of posts (C1) and main supports |
| Quantity / layout | As per base plate details on drawings |

Embedment, edge distances and spacing shall comply with Hilti data and drawing details.

---

## 8.3 Design Actions / 設計作用力

| Source 來源 | Description 說明 |
|-------------|------------------|
| Steel analysis | Reactions at base of C1 / MB1 supports from SAP2000 |
| Barrier loads | Horizontal line / UDL / point loads on posts |
| Combination | Consistent with Chapter 4 load combinations |

Exact tension and shear per anchor group are taken from the PROFIS model input matching the structural analysis reactions.

---

## 8.4 Capacity Check / 承載力檢核

| Item 項目 | Value 數值 | Limit |
|-----------|------------|-------|
| Governing utilization (PROFIS) | **≈ 84%** | 100% |
| Tension / shear / combined | Per PROFIS output | ≤ 1.0 |
| Result | **OK** | — |

The highest utilization ratio reported by Hilti PROFIS Engineering is approximately **84%**, which is less than 1.0. Anchors are adequate.

---

## 8.5 Base Plate / 底板

| Item 項目 | Content 內容 |
|-----------|--------------|
| Plate | As detailed on drawings (thickness, size, holes) |
| Welds | Post / member to plate per CoP Steel 2011 |
| Contact | Bearing on existing RC; packing / grout as specified |

Base plates are designed to distribute anchor forces and member end forces into the concrete without exceeding local bearing limits (see drawing details).

---

## 8.6 Summary / 摘要

| Check 檢核 | Status 狀態 |
|------------|-------------|
| Anchor type | Hilti HST3-R M12 |
| PROFIS utilization | **≈ 84%** |
| Capacity | **Pass** |
| Base plate & detailing | Per drawings |

**Conclusion**: Base plates and anchors are adequate to transfer design forces into the existing RC structure.

---

## 8.7 Assumptions / 假設

1. Anchor design verified by Hilti PROFIS Engineering with reactions from the structural model.  
2. Concrete strength and condition of existing structure are suitable for the selected anchors (see existing structure check).  
3. Installation shall follow Hilti published procedures and drawing notes.  
4. Full PROFIS report may be appended as calculation attachment if required.
