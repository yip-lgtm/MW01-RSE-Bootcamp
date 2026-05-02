# MEB Bootcamp 學習筆記

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