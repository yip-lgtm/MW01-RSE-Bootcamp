# MEB Bootcamp learning-notes.md

## Sem 1 – 2026-04-20 (星期一)

### 今日完成任務
- 職業安全及環保意識：搜 ISO 45001 robot safety（機械人安全標準重點：風險評估、緊急停止、碰撞檢測）
- 工程繪圖及電腦輔助繪圖：用 FreeCAD/Tinkercad 畫機械爪底座（待 push 圖檔）
- 編程技術基礎 + 基礎數學 + 機械工程數學（一）：numpy 向量力學練習（F1 + F2 合力計算成功）
- 微控制器原理與應用 + 工程實踐（一）：Webots panda_gripper_live 練習 open/close gripper
- OpenClaw Skill：新建 safety check skill（已 save）

### 今日筆記 / 心得
- 向量力學同機械工程數學（一）超有用，將來機械人控制一定用到
- Webots 模擬比想像中易上手，之後買 Pi 5 會更快
- 職業安全意識：以後做 hardware project 一定要記住緊急停止機制

### 下次目標
- 繼續 Sem 1 剩低內容（工程繪圖完整圖檔 + 微控制器 Python code）
- 準備 push 晒所有檔案去 GitHub

---

## Sem 1 - Week 1
Date: 2026-05-02

### 今日計劃內容

#### 1. 理論複習（1 小時）
- 職業安全及環保意識：ISO 45001 機械人安全
- 工程繪圖及電腦輔助繪圖：FreeCAD/Tinkercad 機械爪底座
- 基礎數學 + 機械工程數學（一）：向量運算 + 力矩平衡

#### 2. Python + Webots 練習（1.5 小時）
- numpy 向量力學例子
- Webots gripper open/close 練習

#### 3. OpenClaw Skill 實作（1 小時）
- telegram 指令檢查安全隱患

#### 4. 總結 + GitHub push（30 分鐘）

### Python 向量例子
```python
import numpy as np
F1 = np.array([100, 50, 0])
F2 = np.array([-30, 80, 0])
合力 = F1 + F2
print("合力:", 合力, "大小:", np.linalg.norm(合力), "N")
```

### VTC 課程對應（Sem 1）
- 職業安全及環保意識
- 工程繪圖及電腦輔助繪圖
- 編程技術基礎
- 基礎數學
- 機械工程數學（一）
- 微控制器原理與應用
- 工程實踐（一）

---

MEB Bootcamp Day 1 Done! 🚀