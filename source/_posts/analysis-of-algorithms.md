---
title: Analysis of Algorithms
date: 2021-09-17 18:35:30
tags:
categories:
  - [Algorithms]
description: A brief introduction on cost of algorithms, order of growth, Tilde and Big-Oh notations, and optimal algorithm.
---

# Mathematical Model of Cost

## Scientific Method

Conduct experiments (by executing the program) and collect actual data to see how much the algorithm costs. Check every detail to see what it does and figure out how to improve it.

{% mermaid graph LR%}

s((start)) --> o[observe]

o -.-> h[hypothesis]

h --> p[predict]

p --> o

o --> vr[verify]

vr --> vl{validated?}

vl -->|y| e((end))

vl -->|n| h

{% endmermaid %}

The *overall* cost  $C$ is based on probability:
$$
C=\sum p_i c_i
$$

- $C$: overall cost of algorithm

- $p_i$: probability of case $i$

- $c_i$: cost of algorithm when case $i$ happens

## Simplifications

Though doable, looking into details of algorithms can be too complex. So we need a simplified model to briefly estimate algorithm cost.

1. Ignore less costly operations

   We only consider operations that cost most or get invoked most frequently.

2. Ignore lower order terms

   Cost of $\frac{1}{2}{(N+1)(N+2)}$ becomes $\frac{1}{2}N^2$.

Finally, we decided to use **Tilde notation** for our approximate model of algorithm cost:
$$
f(N)\sim g(N)\iff \lim_{N\to\infty}{f(N)\over g(N)}=1
$$

Examples:

- ${1\over 2}N^3+12N^2-4N-5 \sim {1\over 2}N^3$
- $6N+10 \sim 6N$
- $2^N-N^3+2N \sim 2^N$

# Order of Growth

Classifies algorithms by how fast the cost grows when input size $N$ gets larger.

| Description  | Order of Growth |
| :----------: | :-------------: |
|   Constant   |       $1$       |
| Logarithmic  |    $\log N$     |
|    Linear    |       $N$       |
| Linearithmic |    $N\log N$    |
|  Quadratic   |      $N^2$      |
|    Cubic     |      $N^3$      |
| Exponential  |      $2^N$      |

{% asset_img order-of-growth.png 450 "order-of-growth" %}

{% note warning %}

Order of growth discards leading coefficient.

$2N$ is not an order of growth.

{% endnote %}

# Theory of Algorithms

Goal of this theory:

- Identify *difficulty* of a problem
- Develop *optimal* algorithms

## Difficulty of problem

Notations used to identify how "difficult" a problem is:

|      Notation       |                      Definition                      |           Meaning           |
| :-----------------: | :--------------------------------------------------: | :-------------------------: |
|   $T(N)=O(f(N))$    | $\exists c,n_0:N\geq n_0,\Rightarrow T(N)\leq cf(N)$ |   $f(N)$ is *upper bound*   |
| $T(N)=\Omega(g(N))$ | $\exists c,n_1:N\geq n_1\Rightarrow T(N)\geq cg(N)$  |   $g(N)$ is *lower bound*   |
| $T(N)=\Theta(h(N))$ |        $T(N)=O(h(N))$ and $T(N)=\Omega(h(N))$        | $h(N)$ is *order of growth* |

## Optimal Algorithm

An optimal algorithm is one whose **upper bound** is as close as possible with its **lower bound**.

- Upper Bound

  Cost of the best algorithm that we know. Cost of the optimal one must be lower than this.

- Lower Bound

  Necessary cost that any algorithm trying to address current problem must have. The bottom line.


Your mission is to find another algorithm to diminish the gap between upper and lower bounds.
