# 6. Member Design
# 6. 構件設計

**Document**: MW 1.1 RSE Calculation Report  
**Steel**: S355, py = 355 N/mm²  
**Code**: CoP for the Structural Use of Steel 2011  
**Status**: Formal chapter (condensed from CalcAction draft)

---

## 6.1 Design Basis / 設計依據

| Item | Content |
|------|--------|
| Code | CoP Structural Use of Steel 2011 |
| Material | S355, py = 355 N/mm² |
| Analysis | Elastic; member forces from SAP2000 (WC025A Part II) |
| Checks | Strength, stability, interaction as applicable |

---

## 6.2 Member Schedule / 構件表

| Member | Function | Section | py |
|--------|----------|---------|-----|
| **MB1** | Main chord / stringer | UEA 200×100×15 (built-up) | 355 N/mm² |
| **C1** | Post / column | SHS 80×80×8 | 355 N/mm² |
| **SB1** | Landing secondary beam | SHS 70×70×6.3 | 355 N/mm² |

Load path: steps / landings → MB1 / SB1 → C1 → base plate / anchors → existing RC.

---

## 6.3 Design Forces / 設計內力

Member forces are taken from the SAP2000 envelope (see Part II / analysis summary).  
This chapter records **capacity checks and utilization ratios** consistent with the approved reference design.

---

## 6.4 Utilization Summary / 利用率摘要

| Member | Section | Governing check | Utilization | Result |
|--------|---------|-----------------|-------------|--------|
| **MB1** | UEA 200×100×15 | Local capacity | **0.87** | **OK** |
| **C1** | SHS 80×80×8 | Overall buckling | **0.81** | **OK** |
| **SB1** | SHS 70×70×6.3 | Combined | **0.09** | **OK** |

All utilization ratios **&lt; 1.0**. Members satisfy CoP Steel 2011.

---

## 6.5 Member Notes / 構件說明

**MB1**  
Built-up UEA 200×100×15 main stringer. Local capacity governs (≈0.87); overall buckling ratio ≈0.65. Adequate.

**C1**  
SHS 80×80×8 posts. Overall stability governs (≈0.81). Axial force with bending interaction within limits.

**SB1**  
SHS 70×70×6.3 landing beams lightly loaded (utilization ≈0.09). Section provides ample reserve.

---

## 6.6 Deflection / 撓度

Vertical and lateral deflections are obtained from SAP2000.  
Results are within the limits adopted for the project (refer analysis output).  
Serviceability is considered **satisfactory**.

---

## 6.7 Summary Table / 總表

| Member ID | Section | U_max | Status |
|-----------|---------|-------|--------|
| MB1 | UEA 200×100×15 | 0.87 | Pass |
| C1 | SHS 80×80×8 | 0.81 | Pass |
| SB1 | SHS 70×70×6.3 | 0.09 | Pass |

**Conclusion**: All primary steel members are adequate under the design load combinations.

---

## 6.8 Assumptions / 假設

1. Design forces from SAP2000 envelopes of the reference model.  
2. Utilization ratios aligned with verified design summary (WC025A).  
3. Built-up MB1 checked as detailed on drawings.  
4. Full interaction formula worksheets may be appended if required by BD.
