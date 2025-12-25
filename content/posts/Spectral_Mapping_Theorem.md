---
title: "Spectral_Mapping_Theorem"
date: 2025-12-25T16:20:35+08:00
lastmod: 2025-12-25T16:20:35+08:00
draft: false
description: "" 
author: "Jinghao Li" 
# 默认开启数学公式支持（FixIt 主题配置）
math: true
# 默认开启目录
toc: true
tags: [普映射,矩阵论]
categories: [矩阵论]
---

# 谱映射定理 (Spectral Mapping Theorem)

## 1. 定理核心陈述

谱映射定理描述了**矩阵变换**与**特征值变换**之间的同步关系。简单来说：如果你对矩阵 $A$ 施加某种函数变换（如多项式运算），那么新矩阵的特征值，就是原特征值经过同种函数运算后的结果。

### 数学表达
设 $A$ 是一个 $n \times n$ 矩阵，$\lambda$ 是 $A$ 的一个特征值。如果 $P(x)$ 是一个多项式，那么：
$$P(\lambda) \text{ 是矩阵 } P(A) \text{ 的特征值}$$

更形式化地，如果记 $\sigma(A)$ 为矩阵 $A$ 的**谱**（所有特征值的集合），则有：
$$
\sigma(P(A)) = P(\sigma(A)) = \{ P(\lambda) \mid \lambda \in \sigma(A) \}
$$

---

## 2. 推导证明 (多项式情况)

利用特征值的定义，可以轻松证明这一点。

1.  **定义**：设 $\lambda$ 是 $A$ 的特征值，$x$ 是对应的非零特征向量。
    $$Ax = \lambda x$$
2.  **幂运算**：矩阵的幂次对应特征值的幂次。
    $$A^k x = \lambda^k x$$
3.  **多项式运算**：设 $P(t) = a_n t^n + \dots + a_1 t + a_0$。
    $$
    \begin{aligned}
    P(A)x &= (a_n A^n + \dots + a_1 A + a_0 I)x \\
          &= a_n(A^n x) + \dots + a_1(Ax) + a_0(Ix) \\
          &= a_n(\lambda^n x) + \dots + a_1(\lambda x) + a_0 x \\
          &= (a_n \lambda^n + \dots + a_1 \lambda + a_0) x \\
          &= P(\lambda) x
    \end{aligned}
    $$
4.  **结论**：
    由于 $P(A)x = P(\lambda)x$ 且 $x \neq 0$，根据特征值定义，$P(\lambda)$ 即为 $P(A)$ 的特征值，且对应的特征向量依然是 $x$。

---

## 3. 与“零化多项式”的关系

这是理解“为什么零化多项式能推出特征值为根”的关键，它是谱映射定理的一个**特例**。

* **场景**：假设 $P(x)$ 是 $A$ 的**零化多项式**。
* **条件**：这意味着 $P(A) = \mathbf{0}$（零矩阵）。
* **应用定理**：根据谱映射定理，$P(A)$ 的特征值应该是 $P(\lambda)$。
* **推导**：
    零矩阵 $\mathbf{0}$ 的特征值全都是 $0$。
    $$\therefore P(\lambda) = 0$$
* **结论**：**矩阵 $A$ 的特征值 $\lambda$ 必定是方程 $P(x)=0$ 的根。**

---

## 4. 推广：矩阵函数

该定理不仅适用于多项式，还适用于收敛的级数定义的**矩阵函数**（Matrix Functions）。

如果 $f(t)$ 是在 $A$ 的谱上定义的解析函数（例如 $e^t, \sin t, \cos t$ 等），那么：
$$\text{若 } \lambda \in \sigma(A) \implies f(\lambda) \in \sigma(f(A))$$

### 常见例子
* **矩阵指数**：$e^A$ 的特征值是 $e^\lambda$。
* **逆矩阵**：如果 $A$ 可逆（$\lambda \neq 0$），则 $A^{-1}$ 的特征值是 $\lambda^{-1}$（此时函数为 $f(t) = 1/t$）。
* **平移**：矩阵 $A - 3I$ 的特征值是 $\lambda - 3$。

---

## 5. 总结图示

| 原空间 | 操作 (Mapping) | 目标空间 |
| :--- | :---: | :--- |
| **矩阵** $A$ | 代入多项式 $\xrightarrow{P(\cdot)}$ | **新矩阵** $P(A)$ |
| $\updownarrow$ (特征对应) | | $\updownarrow$ (特征对应) |
| **特征值** $\lambda$ | 代入多项式 $\xrightarrow{P(\cdot)}$ | **新特征值** $P(\lambda)$ |

> **一句话记忆**：矩阵怎么变，特征值就跟着怎么变；如果矩阵变成了 0，特征值算出来也得是 0。