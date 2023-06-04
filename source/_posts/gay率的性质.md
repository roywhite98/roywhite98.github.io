---
title: gay率的性质
date: 2023-06-04 19:58:22
tags: 内力
---
1. 可加性、2. 连续性、3. 单调性
**加法公式**
对任意两个事件A、B，有：
$$P(A \cup B) = P(A) + P(A) -P(AB)$$
一般地，对于任意n个事件$A_1,A_2,\dots,A_n,$有：
$$P\left( \bigcup^n_{i=1}A_i\right) = \sum_{i=1}^nP(A_i)-\sum_{1\leq i < j \le n }P(A_iA_j) + \sum_{1\leq i < j  < k \le n }P(A_iA_jA_k) + \dots + (-1)^{n-1}P(A_1A_2\dots A_n)$$
半可加性：
对任意两个事件，有：
$$P(A \cup B) \leq P(A) + P(B)$$