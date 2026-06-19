# Chapter 4. Bellman Equations

## Learning Objectives

完成本章後，你將能夠理解：

- 為什麼 Bellman Equation 是 Reinforcement Learning 的核心
- State Value Function 的意義
- Bellman Expectation Equation
- Bellman Optimality Equation
- Dynamic Programming 的基本思想
- Value Iteration 如何運作
- Q-Learning 為何源自 Bellman Equation
- DQN、SAC、PPO 與 Bellman 的關係

---

# 1. Why Bellman Equation Matters

假設你正在玩迷宮：

```text
Start
 ↓
A
 ↓
B
 ↓
Goal (+100)
```

當你站在：

```text
State A
```

時，你想知道：

```text
這個位置值多少分？
```

Bellman 的核心想法：

> 一個 State 的價值，取決於未來 State 的價值。

---

# 2. State Value Function

定義：

```math
V(s)
```

表示：

```text
當前 State s
未來可以得到多少期望回報
```

例如：

```text
Goal
Reward = 100
```

則：

```math
V(Goal)=100
```

---

# 3. Bellman Expectation Equation

## 核心概念

如果 Agent 已經有固定策略：

```math
\pi(a|s)
```

則 Bellman Expectation Equation 用來計算：

```text
目前 State 的期望價值
```

## Formula

```math
V(s)
=
\sum_a \pi(a|s)
\sum_{s'}
P(s'|s,a)
[
R+\gamma V(s')
]
```

---

## Components

### Policy

```math
\pi(a|s)
```

表示：

```text
在 State s
選擇 Action a 的機率
```

### Transition Probability

```math
P(s'|s,a)
```

表示：

```text
執行 Action a

到達 State s'

的機率
```

### Reward

```math
R
```

立即獎勵

### Discount Factor

```math
\gamma
```

未來回報折扣係數

常見值：

```text
0.9
0.95
0.99
```

---

# 4. Bellman Expectation Example

假設：

```text
State A
```

有兩種可能結果：

### Outcome 1

```text
80%
到 Goal

Reward = 100
```

### Outcome 2

```text
20%
掉進洞

Reward = 0
```

則：

```math
V(A)
=
0.8(100)
+
0.2(0)
```

得到：

```math
V(A)=80
```

這就是：

```text
Expected Value
```

---

# 5. Bellman Optimality Equation

Bellman Expectation 是：

```text
固定 Policy
```

Bellman Optimality 則是：

```text
尋找最佳 Policy
```

核心思想：

```text
不要平均

直接選最好的 Action
```

## Formula

```math
V^*(s)
=
\max_a
\sum_{s'}
P(s'|s,a)
[
R+\gamma V^*(s')
]
```

---

## 簡化理解

```text
最佳價值

=

所有可能動作中

最好的那個
```

---

# 6. Bellman Optimality Example

假設：

```text
State A
```

可以做兩個動作：

### Action Left

```text
Value = 30
```

### Action Right

```text
Value = 80
```

則：

```math
V^*(A)
=
\max(30,80)
```

得到：

```math
V^*(A)=80
```

---

# 7. Bellman Backup

Bellman 更新過程稱為：

```text
Bellman Backup
```

概念：

```text
利用下一個 State

更新目前 State
```

例如：

```text
Goal = 100
```

則：

```text
B = 90
```

再得到：

```text
A = 81
```

像漣漪一樣向前傳播：

```text
Goal
 ↑
 B
 ↑
 A
 ↑
 Start
```

---

# 8. Value Iteration

Bellman Optimality 最著名應用：

```text
Value Iteration
```

更新公式：

```math
V(s)
\leftarrow
\max_a
\sum_{s'}
P(s'|s,a)
[
R+\gamma V(s')
]
```

流程：

```text
Initialize V(s)=0

Repeat

Update V(s)

Until Convergence
```

---

# 9. Bellman → Q Function

實務上更常使用：

```math
Q(s,a)
```

表示：

```text
在 State s

執行 Action a

未來總回報
```

---

## Bellman Optimality for Q

```math
Q^*(s,a)
=
R
+
\gamma
\max_{a'}
Q^*(s',a')
```

這個公式是 Q-Learning 的基礎。

---

# 10. Q-Learning

Q-Learning 更新公式：

```math
Q(s,a)
\leftarrow
Q(s,a)
+
\alpha
[
R
+
\gamma
\max_{a'}
Q(s',a')
-
Q(s,a)
]
```

本質上就是：

```text
Bellman Equation

+

Learning Rate
```

---

# 11. Bellman and Deep RL

很多 Deep RL 演算法都建立在 Bellman 思想上。

---

## DQN

利用 Neural Network 近似：

```math
Q(s,a)
```

核心仍然是：

```text
Bellman Target
```

---

## SAC

使用：

```text
Soft Bellman Equation
```

額外加入：

```text
Entropy
```

---

## TD3

核心：

```text
Bellman Backup

+

Double Q Learning
```

---

## PPO

雖然屬於 Policy Gradient 方法，

但 Critic Network 仍然學習：

```text
Value Function
```

也就是 Bellman Value。

---

# 12. RL Family Tree

```text
Bellman Equation
│
├── Dynamic Programming
│
├── Value Iteration
│
├── Policy Iteration
│
├── Monte Carlo
│
├── TD Learning
│
├── SARSA
│
├── Q Learning
│
├── DQN
│
├── Double DQN
│
├── Dueling DQN
│
├── TD3
│
├── SAC
│
└── PPO
```

---

# Chapter Summary

## Bellman Expectation Equation

```math
V(s)
=
\sum_a \pi(a|s)
\sum_{s'}
P(s'|s,a)
[
R+\gamma V(s')
]
```

用途：

```text
Policy Evaluation
```

---

## Bellman Optimality Equation

```math
V^*(s)
=
\max_a
\sum_{s'}
P(s'|s,a)
[
R+\gamma V^*(s')
]
```

用途：

```text
Finding Optimal Policy
```

---

# 本章最重要一句話

> Bellman Equation 不是 RL 的一部分，而是整個 Reinforcement Learning 的數學基礎。

---

# English Keywords

```text
Bellman Equation
Bellman Expectation Equation
Bellman Optimality Equation
State Value Function
Action Value Function
Q Function
Expected Return
Policy
Policy Evaluation
Policy Improvement
Transition Probability
Markov Decision Process
MDP
Discount Factor
Bellman Backup
Value Iteration
Policy Iteration
Dynamic Programming
Temporal Difference Learning
SARSA
Q Learning
Deep Q Network
Double DQN
Dueling DQN
TD3
SAC
PPO
Actor-Critic
Value Function Approximation
```
