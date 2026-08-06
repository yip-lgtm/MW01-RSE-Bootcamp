# OpenMAIC 架構研究筆記

> 供 MW01 Class I RSE 自學 Bootcamp 使用
> 研究日期：2026-08-06
> 來源：https://github.com/THU-MAIC/OpenMAIC

## 一、整體定位

| 中文 | English |
|------|---------|
| Open Multi-Agent Interactive Classroom | 開源 AI 多代理互動課堂 |
| 一鍵把主題／文件變成沉浸式課堂 | One-click topic/document → immersive classroom |
| 多代理協作（老師 + 同學 + 導演） | Multi-agent collaboration |
| 技術基礎：LangGraph + 兩階段生成 | LangGraph + two-stage generation |

## 二、核心架構分層

```
輸入層 → 生成層 → 編排層 → 執行層 → 回放層 → 輸出層
```

| 層級 | 中文 | 目錄 |
|------|------|------|
| 生成層 | 兩階段流水線 | `lib/generation/` |
| 編排層 | LangGraph 導演圖 | `lib/orchestration/` |
| 執行層 | Action Engine | `lib/action/` |
| 契約層 | DSL（純型別） | `@openmaic/dsl` |
| Skill | OpenClaw 整合 | `skills/openmaic/` |

## 三、兩階段生成流水線（lib/generation/）

| 階段 | 函數 | 輸入 → 輸出 |
|------|------|-------------|
| Stage 1 | `generateSceneOutlinesFromRequirements` | 需求/PDF → SceneOutline[] |
| Stage 2 | `generateSceneContent` + `generateSceneActions` | Outline → 完整 Scene |

**關鍵檔案**

- `outline-generator.ts` — 大綱
- `scene-generator.ts` — 場景內容
- `scene-builder.ts` — 組裝
- `json-repair.ts` — 修復 LLM JSON
- `prompt-formatters.ts` — Prompt 模板

**可借鑑模式**

| 模式 | 對 Bootcamp 啟發 |
|------|------------------|
| 先結構後細節 | 先報告大綱，再填計算 |
| Prompt Template | 荷載／構件專用模板 |
| JSON Schema + Repair | 強制表格與公式格式 |
| Fallback | 計算失敗降級為簡化手算 |

## 四、多智能體編排（lib/orchestration/）

### 狀態機拓撲

```
START → director ──(end)──→ END
           │
           └─(next)→ agent_generate ──→ END
```

| 特點 | 說明 |
|------|------|
| 單輪圖 | 每次請求最多一個 director→agent 循環 |
| 多輪由客戶端串行 | 無內部 maxTurns 迴圈 |
| 單一代理 | 純程式邏輯，不呼叫 LLM |
| 多代理 | LLM 決策 + turn 0 快速路徑 |

### 角色

| 角色 | 職責 |
|------|------|
| Director | 決定誰下一個說話 |
| Teacher / Peer | 註冊於 Registry，各有 persona |

### 對 RSE 的映射

| OpenMAIC | RSE Bootcamp |
|----------|--------------|
| Director | Report Director |
| Teacher | Calculation Engineer |
| Peer | Code Checker / RSE Reviewer |
| whiteboardLedger | 計算步驟 Ledger |

## 五、Action Engine（lib/action/）

| 模式 | 範例 |
|------|------|
| Fire-and-forget | spotlight, laser |
| Synchronous | speech, wb_draw_*, play_video |

**設計重點**

- Switch 分派（type → handler）
- 與 Zustand Store 整合
- 自動開啟白板、動畫延遲、AbortSignal
- 28+ 動作類型

**對計算的映射**

| OpenMAIC Action | CalcAction |
|-----------------|------------|
| speech | explain_formula |
| wb_draw_latex | write_equation |
| wb_draw_table | fill_load_table |
| spotlight | highlight_result |
| discussion | request_review |

## 六、@openmaic/dsl

| 概念 | 說明 |
|------|------|
| 純契約 | 零運行時依賴，只有型別 + 驗證 + 遷移 |
| Stage → Scene → Content → Action | 四層結構 |
| PPTElement | 投影片元素聯合型別 |
| JSON Schema + migrate() | 版本升級 |

**對 RSE DSL 建議**

```ts
interface Report {
  meta: ProjectMeta;
  sections: Section[];
  conclusion: RSEConclusion;
}

interface Section {
  id: string;
  type: 'loading' | 'member' | 'glass' | 'anchor' | 'drawing';
  content: CalculationContent;
  actions: CalcAction[];
}
```

## 七、OpenClaw Skill（skills/openmaic/）

| 原則 | 說明 |
|------|------|
| 一次只走一個階段 | Move one phase at a time |
| 狀態改變前必須確認 | Confirm before state-changing actions |
| 不寫入 API Key | 指導用戶自行編輯設定檔 |
| references/ 拆分 | 各階段載入獨立 md |

**RSE Skill 建議階段**

0. 確認項目類型（MW 1.6 / 1.17…）  
1. 讀取項目資料與圖則（需確認）  
2. 生成報告大綱  
3. 逐章生成計算（Loading → Members → Glass…）  
4. 三角色審核  
5. 匯出完整報告  

## 八、改造為報告生成系統的總結

| OpenMAIC | RSE Bootcamp |
|----------|--------------|
| SceneOutline | Report Section Outline |
| generateSceneContent | generateSectionCalculation |
| ActionEngine | CalculationEngine |
| Multi-agent Director | Report Director + 三角色 |
| DSL Stage/Scene | Report / Section |
| OpenClaw Skill | rse-report Skill |

詳見：`templates/calc-actions/` 與 `templates/engine/`
