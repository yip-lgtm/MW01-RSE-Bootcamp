# Glass & Anchor CalcAction 型別定義

> 第三批動作：玻璃欄杆 + 錨栓／底板
> 對應 WC025A Design of Glass / Base Plate & Anchor

## Glass 相關

### 1. define_glass_panel

```ts
interface DefineGlassPanelAction extends CalcActionBase {
  type: 'define_glass_panel';
  params: {
    thickness: string;             // e.g. "12+1.52+12" laminated tempered
    height: number;                // m
    width?: number;                // m
    permissibleStress: number;     // 80 N/mm²
    codeRef: string;               // "CoP Structural Use of Glass 2018"
  };
}
```

### 2. calc_glass_stress

```ts
interface CalcGlassStressAction extends CalcActionBase {
  type: 'calc_glass_stress';
  params: {
    loadCase: 'line' | 'udl' | 'point';
    stress: number;                // N/mm²
    limit: number;                 // 80 N/mm²
  };
}
```

### 3. check_glass_deflection

```ts
interface CheckGlassDeflectionAction extends CalcActionBase {
  type: 'check_glass_deflection';
  params: {
    delta: number;                 // mm
    limit: number;                 // mm or span ratio
  };
}
```

## Anchor / Base Plate 相關

### 4. define_anchor

```ts
interface DefineAnchorAction extends CalcActionBase {
  type: 'define_anchor';
  params: {
    brand: string;                 // e.g. "Hilti"
    model: string;
    embedment: number;             // mm
    diameter?: number;             // mm
    quantity: number;
  };
}
```

### 5. check_anchor_capacity

```ts
interface CheckAnchorCapacityAction extends CalcActionBase {
  type: 'check_anchor_capacity';
  params: {
    tensionDemand?: number;        // kN
    shearDemand?: number;          // kN
    tensionCapacity?: number;
    shearCapacity?: number;
    utilization: number;
  };
}
```

### 6. write_glass_anchor_summary

```ts
interface WriteGlassAnchorSummaryAction extends CalcActionBase {
  type: 'write_glass_anchor_summary';
  params: {
    glassPass: boolean;
    anchorPass: boolean;
    remarks?: string;
  };
}
```

## 聯合型別

```ts
type GlassAnchorCalcAction =
  | DefineGlassPanelAction
  | CalcGlassStressAction
  | CheckGlassDeflectionAction
  | DefineAnchorAction
  | CheckAnchorCapacityAction
  | WriteGlassAnchorSummaryAction;
```
