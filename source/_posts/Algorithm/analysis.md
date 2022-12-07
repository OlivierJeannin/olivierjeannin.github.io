---
title: Analysis of Algorithms
date: 2021-09-17 18:35:30
categories:
  - Algorithm
---

This is a brief introduction on cost of algorithms, order of growth, Tilde and Big-Oh notations, and optimal algorithm.

<!--more-->

# Analysis of Algorithms

Analysing an algorithm is mainly to develop a mathematical model on its cost. This mathematical model will help us to have some insights into the algorithm we are studying, as well as to predict how much the algorithm will cost given a set of input.

## Step1 - Define *Input* Model

What does the input look like? How big it is (the *problem size*)?

## Step2 - Define *Cost* Model

### Considering Everything

The most accurate way to calculate algorithm cost is to check *every* instruction and see its cost and how frequently it is executed.

But this can be too complex and overwhelming. It doesn't make much difference if we miss some insignificant operations.

So, we use a simpler approach:

### Ignoring Something

We only count the operations that are:

- most costly
- executed most frequently

In other words, operations that contribute most to the total cost.

## Step3 - Mathematical *Analysis*

Now we represent the cost in math.

Mathematical model of algorithm cost is based on probability:

$$
C=\sum p_ic_i
$$

where $C$ is overall cost of algorithm; $p_i$ is probability of case $i$; $c_i$ is cost of algorithm when case $i$ happens.

But even if we're looking at an already smaller set of operations, the cost of them can lead to complex mathematical results, which might be:
$$
T(N)=N^3/6+N^2/2+N/3+10 \label{a}\tag{1}
$$
Also, we don't always need such a precise result. More often, an *approximation* works fine.

So, in order to:

1. simplify the formulas we work with
2. provide an *approximation* of values of interest (algorithm cost, in this case)

We use **tilde notation ($\sim$)**:
$$
T(N)\sim f(N)\iff \lim_{N\to\infty}{T(N)\over f(N)}=1
$$

Then we can turn formula $\eqref{a}$ to $\sim 1/6N^3$, because $\lim_{N\to\infty}{N^3/6+N^2/2+N/3+10\over 1/6N^3}=1$. Way simpler, right?

Here are more examples of tilde notation:

- ${1\over 2}N^3+12N^2-4N-5 \sim {1\over 2}N^3$

- $6N+10 \sim 6N$

- $2^N-N^3+2N \sim 2^N$

{% note warning %}

Sometimes, however, tilde notation may be **misleading**.

When you have a cost of $2N^2+10^6N$, you can not approximate it to $\sim 2N^2$, because $10^6$ is too large to be negligible.

{% endnote %}

## Example

1. *Input* model is an array `a[]` of size N
2. *Cost* model is compare operation (thus the total cost is the time spent on executing compare operation)
3. *Analysis* shows the cost is  $\sim 1/6N^3$

## Order of Growth

$f(N)$ is the **order of growth** of $T(N)$ when:
$$
T(N)\sim af(N)
$$

where $f(N)=N^b\log^cN$, and $a$, $b$, $c$ are constants.

When an algorithm has cost of $N^3/6+N^2/2+N/3+10$, for example, its order of growth is $N^3$.

Some common examples are: 

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

Generally, algorithms whose running time has order of growth of $N^2$ or larger are incapable of solving many problems with large input in an acceptable amount of time.

{% note warning %}

Order of growth discards leading coefficient.

If $T(N)\sim 2N$, then the order of growth is $N$, not $2N$.

{% endnote %}

# Theory of Algorithms

Goal of this theory:

- Identify *difficulty* of a problem
- Develop *optimal* algorithms

## Difficulty of problem

Notations used to identify how "difficult" a problem is:

|      Notation       |                     Definition                      |                Meaning                |
| :-----------------: | :-------------------------------------------------: | :-----------------------------------: |
|   $T(N)=O(f(N))$    | $\exists c,n_0:N\geq n_0\Rightarrow T(N)\leq cf(N)$ |   $f(N)$ is *upper bound* of $T(N)$   |
| $T(N)=\Omega(g(N))$ | $\exists c,n_1:N\geq n_1\Rightarrow T(N)\geq cg(N)$ |   $g(N)$ is *lower bound* of $T(N)$   |
| $T(N)=\Theta(h(N))$ |       $T(N)=O(h(N))$ and $T(N)=\Omega(h(N))$        | $h(N)$ is *order of growth* of $T(N)$ |

## Optimal Algorithm

An optimal algorithm is an algorithm whose **upper bound** is as close as possible with its **lower bound**.

- Upper Bound

  Cost of the best existing algorithm. Cost of the optimal one must be no larger than this.

- Lower Bound

  Essential cost that any algorithm trying to address current problem must have. The bottom line.


Your mission is to find a new algorithm to diminish the gap between upper and lower bounds.
