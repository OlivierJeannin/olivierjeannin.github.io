---
title: Sort
date: 2022-11-25 21:38:20
tags:
categories:
  - [Algorithms]
description: Classic sorting algorithms.
---

# Sorting

**Sorting** is to rearrange order of an array of items according to a key and an ordering rule.

Key is by what you sort. When you sort students, for example, you sort them by score, name, or age. These are keys.

Ordering rule is how you decide one item is prior to another. The most natural ordering rule is the **Total Order**. Let $a$ and $b$ are 2 items, then they follow:

- $a\le b,b\le a\Longrightarrow a=b$
- $a\le b,b\le c\Longrightarrow a\le c$
- either $a<b$ or $b<a$ or $a=b$

Not all orders are total order. For example, in rock-paper-scissors game, $rock<paper$, $paper<scissors$, but $rock>scissors$.

Ideally, your sorting algorithms can sort *any* type of data, no matter it's file, number, string, or whatsoever.

Following I'm going to talk about some classic sorting algorithms.

# Select Sort

This one is really simple. You go all unsorted items over and over, and each time you choose the smallest item and bring it to the front as sorted. Equivalently, you can swap the smallest with the first unsorted item, so that it joins right after with  sorted ones.

As you bring the smallest to the front, the sorted ones are absolutely no bigger than unsorted ones. Because of that, in the subarray of sorted ones, item key will grow bigger (or sometimes remain the same).

This algorithm performs $\sim N^2/2$ compares and $\sim N$ swaps.