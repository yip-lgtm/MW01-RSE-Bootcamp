# Member Design CalcAction 型別定義

> 第二批動作：鋼構件設計（MB1 / C1 / SB1）
> 對應 WC025A Steel Member Design 章節

## 與 Loading 的銜接

| 中文 | English |
|------|---------|
| Loading 完成後進入 Member Design | After Loading, proceed to Member Design |
| 使用 combine_loads 的 designLoad | Use designLoad from combine_loads |
| 截面來自圖則（UEA / SHS） | Sections from drawings (UEA / SHS) |

## 動作定義

### 1. define_member_section

```ts
interface DefineMemberSectionAction extends CalcActionBase {
  type: 'define_member_section';
  params: {
    memberId: string;              // e.g. "MB1", "C1", "SB1"
    sectionType: 'UEA' | 'SHS' | 'RHS' | 'UB' | 'UC' | string;
    designation: string;           // e.g. "200x100x15", "80x80x8"
    area?: number;                 // mm²
    Ixx?: number;                  // mm⁴
    Iyy?: number;
    Zxx?: number;                  // mm³
    Zyy?: number;
    py: number;                    // N/mm² (design strength)
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 定義構件截面與材料強度 |
| 對應 | WC025A：MB1=UEA 200×100×15, C1=SHS 80×80×8, SB1=SHS 70×70×6.3 |

### 2. assign_member_forces

```ts
interface AssignMemberForcesAction extends CalcActionBase {
  type: 'assign_member_forces';
  params: {
    memberId: string;
    axialN?: number;               // kN（壓力為負或依約定）
    momentMy?: number;             // kNm
    momentMz?: number;             // kNm
    shearVy?: number;              // kN
    shearVz?: number;              // kN
    source: 'SAP2000' | 'hand_calc' | 'approx';
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 寫入構件設計內力（來自 SAP2000 或手算） |

### 3. check_section_capacity

```ts
interface CheckSectionCapacityAction extends CalcActionBase {
  type: 'check_section_capacity';
  params: {
    memberId: string;
    checkType: 'compression' | 'bending' | 'shear' | 'combined';
    NcRd?: number;                 // 抗壓承載力 kN
    McRd?: number;                 // 抗彎承載力 kNm
    VcRd?: number;                 // 抗剪承載力 kN
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 計算截面承載力（可先給值，後接公式） |

### 4. check_utilization

```ts
interface CheckUtilizationAction extends CalcActionBase {
  type: 'check_utilization';
  params: {
    memberId: string;
    utilizationRatio: number;      // 0~1+，例如 0.72
    limit?: number;                // 預設 1.0
    governingCheck: string;        // e.g. "combined axial+bending"
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 記錄利用率並判斷是否通過 |
| 輸出 | `{ pass: boolean, ratio: number }` |

### 5. check_deflection

```ts
interface CheckDeflectionAction extends CalcActionBase {
  type: 'check_deflection';
  params: {
    memberId: string;
    delta: number;                 // mm
    span: number;                  // mm
    limitRatio: number;            // e.g. 250 → L/250
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 撓度驗算 |

### 6. ref_steel_code

```ts
interface RefSteelCodeAction extends CalcActionBase {
  type: 'ref_steel_code';
  params: {
    code: 'Steel 2011';
    clause?: string;
    table?: string;
    remark?: string;
  };
}
```

### 7. write_member_summary

```ts
interface WriteMemberSummaryAction extends CalcActionBase {
  type: 'write_member_summary';
  params: {
    rows: Array<{
      memberId: string;
      section: string;
      utilization: number;
      pass: boolean;
      remark?: string;
    }>;
  };
}
```

| 中文 | English |
|------|---------|
| 用途 | 產出構件設計總表 |

## 聯合型別

```ts
type MemberDesignCalcAction =
  | DefineMemberSectionAction
  | AssignMemberForcesAction
  | CheckSectionCapacityAction
  | CheckUtilizationAction
  | CheckDeflectionAction
  | RefSteelCodeAction
  | WriteMemberSummaryAction;
```

## WC025A 建議序列（簡版）

| 順序 | Action | 說明 |
|------|--------|------|
| 1 | `ref_steel_code` | 引用 CoP Steel 2011 |
| 2 | `define_member_section` ×3 | MB1 / C1 / SB1 |
| 3 | `assign_member_forces` ×3 | 從 SAP2000 結果寫入 |
| 4 | `check_utilization` ×3 | 記錄利用率 |
| 5 | `check_deflection`（如需要） | 平台梁等 |
| 6 | `write_member_summary` | 總表 |

## 截面對照（WC025A）

| 構件 | 截面 | 顏色（圖則） |
|------|------|--------------|
| MB1 | UEA 200×100×15 | 紅 |
| C1 | SHS 80×80×8 | 青 |
| SB1 | SHS 70×70×6.3 | 藍 |
