# Loading Analysis CalcAction 型別定義

> 第一批動作：對應 WC025A Loading Analysis（第 7 頁）

## 基礎型別

```ts
/** 所有計算動作的共同基底 */
interface CalcActionBase {
  id: string;                    // 唯一識別
  type: string;                  // 動作類型
  sectionId?: string;            // 所屬報告章節
  timestamp?: string;            // 執行時間
  notes?: string;                // 備註
}

/** 執行結果 */
interface CalcActionResult {
  success: boolean;
  outputs?: Record<string, number | string | object>;
  error?: string;
  ledgerEntry?: string;          // 寫入計算 Ledger 的文字
}
```

## Loading Analysis 專用動作

### 1. define_design_data

```ts
interface DefineDesignDataAction extends CalcActionBase {
  type: 'define_design_data';
  params: {
    steelGrade: string;              // e.g. "S355"
    steelDensity: number;            // 7850 kg/m³
    steelE: number;                  // 205000 N/mm²
    steelPy: number;                 // 355 N/mm²
    weldStrength: number;            // 250 N/mm²
    glassPermissibleStress: number;  // 80 N/mm²
    glassDensity?: number;
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 寫入第 3.2 節設計數據 |
| 輸出 | 材料參數表 |

### 2. define_geometry

```ts
interface DefineGeometryAction extends CalcActionBase {
  type: 'define_geometry';
  params: {
    stepLengthL: number;             // 1400 mm
    riserHeightA: number;            // 175 mm
    innerTreadB: number;             // 230 mm
    outerTreadC: number;             // 420 mm
    intermediateLandingInner: number; // 900 mm
    intermediateLandingOuter: number; // 1685 mm
    topLandingInner: number;         // 1200 mm
    topLandingOuter: number;         // 2000 mm
  };
}
```

### 3. define_imposed_loads

```ts
interface DefineImposedLoadsAction extends CalcActionBase {
  type: 'define_imposed_loads';
  params: {
    staircaseLiveLoad: number;       // 3.0 kPa
    glassLineLoad: number;           // 0.75 kN/m @ 1.1m
    glassUDL: number;                // 1.0 kPa
    glassConcentrated: number;       // 0.5 kN
    loadCodeRef: string;             // "CoP Dead & Imposed Loads 2011 Table 3.13"
  };
}
```

### 4. calc_step_self_weight

```ts
interface CalcStepSelfWeightAction extends CalcActionBase {
  type: 'calc_step_self_weight';
  params: {
    stepArea: number;                // m²
    finishThickness?: number;        // mm
    finishDensity?: number;          // kN/m³
    steelTreadWeight?: number;       // kN per step
  };
}
```

### 5. calc_landing_self_weight

```ts
interface CalcLandingSelfWeightAction extends CalcActionBase {
  type: 'calc_landing_self_weight';
  params: {
    landingId: 'intermediate' | 'top';
    area: number;                    // m²
    slabThickness?: number;          // mm
    finishLoad?: number;             // kPa
  };
}
```

### 6. calc_glass_loads

```ts
interface CalcGlassLoadsAction extends CalcActionBase {
  type: 'calc_glass_loads';
  params: {
    length: number;                  // m（欄杆長度）
    height: number;                  // m（通常 1.1）
    applyLineLoad: boolean;
    applyUDL: boolean;
    applyConcentrated: boolean;
  };
}
```

### 7. combine_loads

```ts
interface CombineLoadsAction extends CalcActionBase {
  type: 'combine_loads';
  params: {
    combination: '1.4DL+1.6LL' | '1.2DL+1.6LL' | string;
    deadLoad: number;
    liveLoad: number;
    memberId?: string;
  };
}
```

### 8. ref_cop

```ts
interface RefCodeAction extends CalcActionBase {
  type: 'ref_cop';
  params: {
    code: 'Dead & Imposed Loads 2011' | 'Steel 2011' | 'Glass 2018' | string;
    clause?: string;
    table?: string;                  // e.g. "Table 3.13"
    remark?: string;
  };
}
```

### 9. write_load_summary

```ts
interface WriteLoadSummaryAction extends CalcActionBase {
  type: 'write_load_summary';
  params: {
    rows: Array<{
      item: string;
      deadLoad: number;
      liveLoad: number;
      unit: string;
      remark?: string;
    }>;
  };
}
```

## 聯合型別

```ts
type LoadingCalcAction =
  | DefineDesignDataAction
  | DefineGeometryAction
  | DefineImposedLoadsAction
  | CalcStepSelfWeightAction
  | CalcLandingSelfWeightAction
  | CalcGlassLoadsAction
  | CombineLoadsAction
  | RefCodeAction
  | WriteLoadSummaryAction;
```
