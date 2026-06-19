# Reinforcement Learning Projects

## Project 3. Frozen Lake

### Goal

學習在 **隨機環境（Stochastic Environment）** 中做決策。

Frozen Lake 和一般 Grid World 最大的差異在於：

> 你選擇某個行動，不代表環境一定會照你的預期執行。

---

## 1. Environment

Frozen Lake 通常是一個格子世界，例如：

```text
S F F F
F H F H
F F F H
H F F G
```

| 符號 | 意義 |
|---|---|
| S | Start，起點 |
| F | Frozen，安全冰面 |
| H | Hole，洞，掉進去失敗 |
| G | Goal，終點 |

---

## 2. Challenge

Frozen Lake 的主要挑戰是：

### 地板很滑

也就是：

```text
行動結果不確定
```

例如你選擇：

```text
Right
```

但實際結果可能是：

```text
80% 往右
10% 往上
10% 往下
```

所以 Agent 不能只學「我要往哪裡走」，還要學會：

```text
在不確定環境中，哪一種策略最安全、最有機會成功？
```

---

## 3. Actions

Frozen Lake 常見行動有四種：

```text
Up
Down
Left
Right
```

但因為環境是 slippery，所以動作結果可能偏離原本方向。

---

## 4. Core Concept 1：Transition Probability

### Transition Probability

中文可以理解成：

```text
狀態轉移機率
```

數學表示：

```text
P(s' | s, a)
```

意思是：

```text
目前在狀態 s
執行動作 a
轉移到下一個狀態 s' 的機率
```

例如：

```text
P(Right Cell | Current Cell, Right) = 0.8
```

代表：

```text
目前在某一格
選擇往右
最後真的到右邊那格的機率是 80%
```

---

## 5. Core Concept 2：Markov Decision Process

### MDP

MDP 全名是：

```text
Markov Decision Process
```

中文常翻成：

```text
馬可夫決策過程
```

MDP 是強化學習最重要的數學模型之一。

---

## 6. MDP 的組成

MDP 通常可以表示成：

```text
MDP = (S, A, P, R, γ)
```

| 符號 | 意義 |
|---|---|
| S | States，所有狀態 |
| A | Actions，所有動作 |
| P | Transition Probability，狀態轉移機率 |
| R | Reward，獎勵 |
| γ | Discount Factor，折扣因子 |

---

## 7. Frozen Lake 可以學到的演算法

### 7.1 Value Iteration

學習每個狀態的價值：

```text
V(s)
```

意思是：

```text
在狀態 s 開始，未來可以得到多少期望回報？
```

---

### 7.2 Policy Iteration

學習每個狀態應該採取什麼行動：

```text
π(s)
```

意思是：

```text
在狀態 s，最佳行動是什麼？
```

---

### 7.3 Q-Learning

學習每個狀態與動作組合的價值：

```text
Q(s, a)
```

意思是：

```text
在狀態 s 採取動作 a，未來可以得到多少期望回報？
```

---

## 8. Bellman Equation

Frozen Lake 會接觸到 Bellman Equation：

```text
V(s) = max_a Σ P(s' | s, a) [R + γV(s')]
```

這個公式的重點是：

```text
目前狀態的價值
=
考慮所有可能下一步結果後
選擇期望價值最高的行動
```

---

## 9. Frozen Lake 的學習重點

Frozen Lake 是第一次真正接觸：

```text
Stochastic Environment
MDP
Transition Probability
Value Function
Policy
Bellman Equation
```

它讓你理解：

> 強化學習不是只處理「確定性問題」，而是要能在「不確定環境」中做出好決策。

---

# Project 4. Blackjack

## Goal

Blackjack 是強化學習中的經典案例，特別適合用來學習：

```text
Monte Carlo Methods
Policy Learning
Expected Return
```

Blackjack 也是 Sutton & Barto《Reinforcement Learning: An Introduction》中的經典範例。

---

## 1. Game Idea

Blackjack 的目標是：

```text
讓玩家點數盡量接近 21
但不能超過 21
```

如果超過 21，稱為 bust，直接輸掉。

---

## 2. State

Blackjack 的狀態通常由三個資訊組成：

```python
(player_sum, dealer_showing, usable_ace)
```

| 狀態項目 | 意義 |
|---|---|
| player_sum | 玩家目前點數 |
| dealer_showing | Dealer 顯示的牌 |
| usable_ace | 是否有可用 Ace |

---

## 3. State Example

例如：

```python
(18, 7, True)
```

意思是：

```text
玩家目前 18 點
Dealer 顯示牌是 7
玩家手上有可用 Ace
```

---

## 4. Actions

Blackjack 主要有兩個動作：

| Action | 意義 |
|---|---|
| Hit | 再拿一張牌 |
| Stand | 停止拿牌 |

---

## 5. Reward

Blackjack 的 Reward 通常設計成：

```text
Win  = +1
Draw =  0
Lose = -1
```

也就是：

```text
贏了得到正回報
平手沒有回報
輸了得到負回報
```

---

## 6. 為什麼 Blackjack 適合 Monte Carlo？

因為 Blackjack 通常要等到整局結束後，才知道最後輸贏。

例如：

```text
Hit
Hit
Stand
```

中間過程不一定馬上有 reward。

最後才知道結果：

```text
Win  = +1
Lose = -1
Draw = 0
```

這種問題很適合 Monte Carlo Learning。

---

## 7. Monte Carlo Methods

Monte Carlo 的核心想法是：

```text
不用事先知道環境模型
直接透過大量遊戲經驗來估計價值
```

也就是讓 Agent 玩很多局：

```text
Episode 1
Episode 2
Episode 3
...
Episode N
```

然後統計每個 state 或 state-action 的平均回報。

---

## 8. Example

假設 Agent 玩了很多局後發現：

```text
State = (18, Dealer = 6)
Average Return = +0.42
```

代表：

```text
當玩家 18 點、Dealer 顯示 6 時
這是一個相對有利的狀態
```

---

## 9. Core Concept 1：Expected Return

Expected Return 中文可以理解成：

```text
期望回報
```

公式：

```text
G_t = R_{t+1} + γR_{t+2} + γ²R_{t+3} + ...
```

意思是：

```text
從現在開始
未來所有 reward 的折扣總和
```

---

## 10. Core Concept 2：Policy Learning

Policy Learning 的目標是學到最佳策略：

```text
π*(s)
```

也就是：

```text
在每一個 state 下
Agent 應該選擇哪一個 action
```

例如：

```text
玩家 18 點
Dealer 顯示 6

→ Stand
```

或：

```text
玩家 11 點
Dealer 顯示 10

→ Hit
```

---

## 11. Blackjack 的學習重點

Blackjack 可以幫助理解：

```text
Monte Carlo Methods
Episode
Return
Expected Return
Policy Evaluation
Policy Improvement
Policy Learning
```

它讓你理解：

> Agent 可以不需要知道完整環境規則，只靠大量經驗學出好的策略。

---

# Frozen Lake vs Blackjack

| 比較項目 | Frozen Lake | Blackjack |
|---|---|---|
| 問題類型 | Stochastic Grid World | Card Game |
| 核心環境 | 滑冰地圖 | 撲克牌局 |
| 主要挑戰 | 行動結果不確定 | 最後才知道輸贏 |
| 核心概念 | MDP、Transition Probability | Monte Carlo、Expected Return |
| State | 目前格子位置 | 玩家點數、Dealer 明牌、Ace |
| Action | Up、Down、Left、Right | Hit、Stand |
| Reward | 到達終點或掉入洞 | Win、Draw、Lose |
| 代表方法 | Value Iteration、Policy Iteration、Q-Learning | Monte Carlo Prediction、Monte Carlo Control |
| 難度 | ★★★ | ★★★ |
| 重要度 | ★★★★★ | ★★★★★ |

---

# 學習路線位置

這兩個專案在強化學習學習路線中的位置大約是：

```text
Project 1. Grid World
        ↓
Project 2. Multi-Armed Bandit
        ↓
Project 3. Frozen Lake
        ↓
Project 4. Blackjack
        ↓
Project 5. Taxi
        ↓
Project 6. CartPole
        ↓
Project 7. MountainCar
        ↓
Project 8. LunarLander
```

概念進展：

```text
Deterministic Environment
        ↓
Stochastic Environment
        ↓
MDP
        ↓
Monte Carlo Methods
        ↓
Temporal Difference Learning
        ↓
Q-Learning
        ↓
Deep Q Network
```

---

# English Keywords

```text
Stochastic Environment
Frozen Lake
Slippery Grid World
Transition Probability
Markov Decision Process
MDP
State
Action
Reward
Discount Factor
Value Function
Policy
Bellman Equation
Value Iteration
Policy Iteration
Q-Learning
Blackjack
Monte Carlo Methods
Episode
Expected Return
Policy Learning
Policy Evaluation
Policy Improvement
Monte Carlo Control
```
