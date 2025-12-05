---
title: "Konigsiberg_problem"
date: 2025-12-05T16:54:54+08:00
lastmod: 2025-12-05T16:54:54+08:00
draft: flase
description: "" 
author: "Jinghao Li" 
# 默认开启数学公式支持（FixIt 主题配置）
math: true
# 默认开启目录
toc: true
tags: []
categories: []
---
![konisberg bridge abstract pricture](data\pictures\konisberg_bridge.png)
🌉 What is the Königsberg Bridge Problem?
The Königsberg Bridge Problem is a famous historical problem in mathematics that laid the foundation for graph theory and topology.

The Problem: The city of Königsberg (now Kaliningrad, Russia) was situated on the Pregel River and included two large islands connected to each other and to the two mainland banks by seven bridges. The citizens wondered if it was possible to find a walk through the city that would cross every one of these seven bridges exactly once and return to the starting point.

The Key Question: Can a Eulerian circuit (or a single continuous path) be found in the physical layout?

The Solution: In 1736, the Swiss mathematician Leonhard Euler proved that the task was impossible. He demonstrated this not by physically trying all possibilities, but by simplifying the city's map into an abstract diagram.

## proof: you can't across the all bridge by only across it once.

📜 欧拉路径与欧拉回路定理的证明

🎯 定理陈述 (Theorem Statement)

对于一个连通图 G：

1. 欧拉回路（Eulerian Circuit）存在，当且仅当图中所有节点（Vertices）的度（Degree）都是偶数。
2. 欧拉路径（Eulerian Path）存在，当且仅当图中有零个或恰好两个度为奇数的节点。

---

Ⅰ. 必要性证明 (Necessity: If Path/Circuit Exists => Degree Condition Holds)

假设存在一条欧拉路径 P 或欧拉回路 C，它遍历了图 G 中的所有边且每条边恰好一次。

1. 欧拉回路的度数分析 (Circuit C)

* 起点和终点重合 (s=t)。
* 对于任一节点 v：每当回路 C 进入 v 时，它必定会使用一条不同的边 离开 v。
* 由于 C 遍历了所有边，所有连接到 v 的边都可以成对配对（进入-离开）。
* 因此，所有节点的度 deg(v) 都必须是偶数。

2. 欧拉路径的度数分析 (Path P)

* 起点 s 和终点 t (s ≠ t)。
* 对于中间节点 v (v ≠ s, v ≠ t)：
    * 与回路证明相同，它们仍然需要成对的进入和离开边。因此，这些节点的度 deg(v) 必须是偶数。
* 对于起点 s：
    * 路径 P 从 s 开始（离开），并在过程中可以多次进出。但它不会最终回到 s。
    * 因此，离开 s 的边数比进入 s 的边数多 1。 deg(s) 必须是奇数。
* 对于终点 t：
    * 路径 P 在 t 结束（进入），并在过程中可以多次进出。
    * 因此，进入 t 的边数比离开 t 的边数多 1。 deg(t) 必须是奇数。

结论：存在欧拉路径时，奇度节点只能是起点和终点，恰好两个。

---

Ⅱ. 充分性证明 (Sufficiency: If Degree Condition Holds => Path/Circuit Exists)

我们使用构造性证明（基于 Hierholzer's Algorithm 的思想）来证明条件成立时，欧拉路径或回路一定存在。

1. 证明所有度数为偶数 => 存在欧拉回路

假设 G 是连通图，且所有 deg(v) 均为偶数。

1.  构造第一个子回路 (C1)：从任一节点 v0 开始，沿着未使用的边随意行走，每进入一个节点，必有未使用的边离开（因为度数是偶数）。因此，行走一定会回到起点 v0，形成一个回路 C1。
2.  检查剩余边 (G'):
    * 如果 C1 包含了 G 的所有边，则 C1 即为欧拉回路，证明结束。
    * 否则，删除 C1 中的边，形成子图 G'。由于 C1 移除了偶数条边，在 G' 中，所有剩余边的度数仍然是偶数。
3.  构造第二个子回路 (C2): 由于 G 是连通的， G' 中必存在一个节点 v1 仍在 C1 上。从 v1 开始，在 G' 中构造第二个回路 C2。
4.  拼接回路：将 C2 插入到 C1 中 v1 的位置。这形成了一条更长的回路 C_new。
5.  迭代：不断重复步骤 2-4，直到所有边都被包含进一个单一的回路中。由于边是有限的，最终得到的回路即为 G 的欧拉回路。

2. 证明恰好两个奇度节点 (s, t) => 存在欧拉路径

假设 G 是连通图，且恰好有两个奇度节点 s 和 t。

1.  引入辅助边 (e_st): 在节点 s 和 t 之间添加一条新的边 e_st。
2.  形成新图 (G'): 在新图 G' 中， deg(s) 和 deg(t) 各增加了 1，因此都变为了偶数。G' 中所有节点的度现在都是偶数。
3.  应用回路定理：根据步骤 1 的充分性证明， G' 必然存在一条欧拉回路 C'。
4.  移除辅助边：欧拉回路 C' 必然经过边 e_st。将 e_st 从 C' 中移除：
    $$P = C' - \{e_{st}\}$$
5.  形成欧拉路径：移除 e_st 后，回路 C' 被打破，形成了一条路径 P。这条路径包含了 G 中的所有原始边，并且必然从 s 或 t 开始，在另一个节点结束。

最终结论：P 即为 G 中的欧拉路径，证明完毕。