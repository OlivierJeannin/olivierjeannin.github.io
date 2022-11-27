---
title: Sorting Problem
date: 2022-11-25 21:38:20
top: 10
tags:
categories:
  - Algorithm
  - Sort
---

**Sorting** is to rearrange order of an array of items according to a key and an ordering rule.

<!--more-->

Key is by what you sort. When you sort students, for example, you sort them by score, name, or age. These are keys.

Ordering rule is how you decide one item is prior to another. The most natural ordering rule is the **Total Order**. Let $a$ and $b$ are 2 items, then they follow:

- $a\le b,b\le a\Longrightarrow a=b$
- $a\le b,b\le c\Longrightarrow a\le c$
- either $a<b$ or $b<a$ or $a=b$

Not all orders are total order. For example, in rock-paper-scissors game, $rock<paper$, $paper<scissors$, but $rock>scissors$.

Ideally, your sorting algorithms can sort *any* type of data, no matter it's file, number, string, or whatsoever.

In [this](/categories/Algorithm/Sort) sub-category, I wrote some articles to explain some classic sorting algorithms.
