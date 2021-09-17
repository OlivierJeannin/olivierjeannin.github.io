---
title: Analysis of Algorithms
date: 2021-09-17 18:35:30
tags:
categories:
  - [Algorithms]
description: A brief introduction on cost of algorithms, order of growth, Tilde and Big-Oh notations, and optimal algorithm.
---

# Cost of an Algorithm

## Total Cost

The total cost of an algorithm $C$ is based on probability:
$$
C = \sum p_i c_i
$$

$p_i$: probability for case $i$ to happen

$c_i$: cost of algorithm when case $i$ happens

## Simplification

In practise, when analysize algorithms, we will basically only consider:

1. the **`most consumable steps`** in an algorithm

   e.g. we focus on conditions, loops, etc. and neglect time initializing variables.

2. the **`most significant partitions`** of total cost

   e.g. when we get a total cost of $N^2+2N+3$, we focus on the $N^2$ part and drop those behind it.

In this way, we get *simpler* version of cost, without ignoring too much important things.

## Order of Growth

**Order of Growth**: how fast the `cost` grows as `problem size` $N$ grows

If we classify algorithms by that, we will get these categories:

|  Description   | Order of Growth |
| :------------: | :-------------: |
|   *Constant*   |       $1$       |
| *Logarithmic*  |    $\log N$     |
|    *Linear*    |       $N$       |
| *Linearithmic* |    $N\log N$    |
|  *Quadratic*   |      $N^2$      |
|    *Cubic*     |      $N^3$      |
| *Exponential*  |      $2^N$      |

{% asset_img order-of-growth.png 600 "order-of-growth" %}

{% note warning %}
Order of growth discards leading coefficient. \
$2N$ is not order of growth.
{% endnote %}

# Tilde Notation

We use $f(N)\sim g(N)$ when there stands:
$$
\lim_{N\to\infty}{f(N)\over g(N)} = 1
$$

Example: $f(N)=2N^2+\log N+1$, then $f(N)\sim 2N^2$

# Big-Oh Notation

|        Notation        |                  Definition                   |            Meaning            |
| :--------------------: | :-------------------------------------------: | :---------------------------: |
|   $T(N)\sim O(f(N))$   |  $\exists n_0:\ N\geq n_0,\ T(N)\leq cf(N)$   |   $f(N)$ is **upper bound**   |
| $T(N)\sim\Omega(g(N))$ |  $\exists n_1:\ N\geq n_1,\ T(N)\geq cg(N)$   |   $g(N)$ is **lower bound**   |
| $T(N)\sim\Theta(h(N))$ | $T(N)\sim O(h(N))$ and $T(N)\sim\Omega(h(N))$ | $h(N)$ is **order of growth** |

# Optimal Algorithm

The **`upper bound`** should be as close as possible with **`lower bound`**.

- Upper Bound

  1. Find a *known* algorithm whose cost is $t(N)$,

  2. then we know the cost of *optimal algorithm* is bound to be $T(N)\sim O(t(N))$,

  Why is that? Because the *optimal algorithm* is `optimal`. Its cost should be lower than $t(N)$.

- Lower Bound

  Think of it as the `necessary` cost.

  That is, whatever algorithm you might use, however simple it is, it will cost you *at least* this much. Less cost? Not possible! Or you won't be able to finish your job!

Your mission is to find a lower *upper bound* and a possibly higher *lower bound*, by changing the algorithm.

When you get the narrowest range, look at the algorithm you're using, it's optimal.
