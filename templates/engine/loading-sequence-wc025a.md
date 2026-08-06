# WC025A Loading Analysis → Action 序列

> 對應 Structural Design Report WC025A Part I 第 7 頁
> Internal Staircase at Cockloft to 1/F, Camel Paint Buildings Block 3

## 序列總覽

| 順序 | Action type | 主要參數 | 預期輸出 |
|------|-------------|---------|----------|
| 1 | `define_design_data` | steelDensity=7850, py=355, E=205000, weld=250, glass=80 | 材料參數表 |
| 2 | `define_geometry` | L=1400, a=175, b=230, c=420, 中間平台 900/1685, 頂部 1200/2000 | 幾何參數表 |
| 3 | `define_imposed_loads` | staircase=3.0 kPa, line=0.75 kN/m, udl=1.0 kPa, point=0.5 kN | 活荷載定義 |
| 4 | `ref_cop` | code="Dead & Imposed Loads 2011", table="Table 3.13" | 規範引用 |
| 5 | `calc_step_self_weight` | 依踏步面積與面層 | 每級踏步恆載 |
| 6 | `calc_landing_self_weight` | landingId="intermediate" | 中間平台恆載 |
| 7 | `calc_landing_self_weight` | landingId="top" | 頂部平台恆載 |
| 8 | `calc_glass_loads` | length=欄杆長度, height=1.1 | 線荷載 / UDL / 集中荷載 |
| 9 | `combine_loads` | combination="1.4DL+1.6LL" | 設計荷載 |
| 10 | `write_load_summary` | 彙整所有結果成總表 | Loading Summary 表 |

## 完整序列（可直接餵給 CalculationEngine）

```ts
const loadingSequence: LoadingCalcAction[] = [
  {
    id: 'la-01',
    type: 'define_design_data',
    params: {
      steelGrade: 'S355',
      steelDensity: 7850,
      steelE: 205000,
      steelPy: 355,
      weldStrength: 250,
      glassPermissibleStress: 80,
    },
  },
  {
    id: 'la-02',
    type: 'define_geometry',
    params: {
      stepLengthL: 1400,
      riserHeightA: 175,
      innerTreadB: 230,
      outerTreadC: 420,
      intermediateLandingInner: 900,
      intermediateLandingOuter: 1685,
      topLandingInner: 1200,
      topLandingOuter: 2000,
    },
  },
  {
    id: 'la-03',
    type: 'define_imposed_loads',
    params: {
      staircaseLiveLoad: 3.0,
      glassLineLoad: 0.75,
      glassUDL: 1.0,
      glassConcentrated: 0.5,
      loadCodeRef: 'CoP Dead & Imposed Loads 2011 Table 3.13',
    },
  },
  {
    id: 'la-04',
    type: 'ref_cop',
    params: {
      code: 'Dead & Imposed Loads 2011',
      table: 'Table 3.13',
      remark: 'Protective barriers – horizontal loads',
    },
  },
  {
    id: 'la-05',
    type: 'calc_step_self_weight',
    params: {
      stepArea: 0.35,        // 示例，實際由幾何計算
      finishLoad: 0.5,
    },
  },
  {
    id: 'la-06',
    type: 'calc_landing_self_weight',
    params: {
      landingId: 'intermediate',
      area: 1.35,
      finishLoad: 0.5,
    },
  },
  {
    id: 'la-07',
    type: 'calc_landing_self_weight',
    params: {
      landingId: 'top',
      area: 2.0,
      finishLoad: 0.5,
    },
  },
  {
    id: 'la-08',
    type: 'calc_glass_loads',
    params: {
      length: 4.5,
      height: 1.1,
      applyLineLoad: true,
      applyUDL: true,
      applyConcentrated: true,
    },
  },
  {
    id: 'la-09',
    type: 'combine_loads',
    params: {
      combination: '1.4DL+1.6LL',
      deadLoad: 0,           // 由前一步結果填入
      liveLoad: 0,
    },
  },
  {
    id: 'la-10',
    type: 'write_load_summary',
    params: {
      rows: [],              // 由引擎根據 state 自動組裝
    },
  },
];
```

## 使用方式

```ts
const engine = new CalculationEngine(initialState);
const results = await engine.executeSequence(loadingSequence);
const ledger = engine.getLedger();
// ledger 可直接轉成報告附錄或 Markdown 表格
```

## 規範來源（必須引用）

| 項目 | 來源 |
|------|------|
| 樓梯活荷載 3.0 kPa | CoP Dead & Imposed Loads 2011 |
| 玻璃欄杆 0.75 kN/m、1.0 kPa、0.5 kN | Table 3.13 Protective barriers |
| 荷載組合 1.4DL+1.6LL | 常用設計組合 |
| 鋼材 S355、py=355 | CoP Structural Use of Steel 2011 |
| 玻璃允許應力 80 N/mm² | CoP Structural Use of Glass 2018 |
