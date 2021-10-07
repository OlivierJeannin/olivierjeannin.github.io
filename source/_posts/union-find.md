---
title: Union-Find
date: 2021-09-09 13:50:49
tags:
categories:
  - [Algorithms]
description: Union-Find problem and its algorithms, including Quick-Find, Quick-Union, and improvements on QU.
---

# What is Union-Find Problem

## Connectivity

$a-b$: $a$ is connected with $b$

Properties:

- $a-a$

- $a-b \Longrightarrow b-a$

- $a-b,b-c \Longrightarrow a-c$

## Connected Component

A is a `connected component`: $a\in{A},b\in{A} \iff a-b$

{% asset_img connected-component.png "3 Connected Components" %}

## Union-Find

$union(a,b)$: `connect` $a$ and $b$

$find(a,b)$: `check` if $a$ and $b$ are connected *(True/False)*

***Problem***:

1. $union()$ any $N$ objects $(N\to\infty)$, at any time

2. ${\forall}a,b,find(a,b)$ at any time

{% asset_img union-find-problem.png 250 462 "Example" %}

# Algorithms

## Quick Find

> connected $\Longleftrightarrow$ same **status**
>
> {% asset_img quick-find.png 584 300 "Quick Find" %}

{% tabs Quick-Find %}
<!-- tab Data Structure -->
```pseudocode
arr[N];  // status of objects
```
<!-- endtab -->

<!-- tab union(a,b) -->

与 $a$ 状态相同的，都要改为 $b$ 的状态。

```pseudocode
sa = arr[a];  // sataus of a
sb = arr[b];
foreach i in arr[]:
	if (arr[i] == sa):  // every i connected with a
		arr[i] = sb;  // connect i to b
```
<!-- endtab -->

<!-- tab find(a,b) -->

```pseudocode
return arr[a] == arr[b];  // same status
```
<!-- endtab -->
{%  endtabs%}

## Quick Union

> A `connected component` is a `tree`
>
> connected $\Longleftrightarrow$ same **root**
>
> {% asset_img quick-union.png 600 400 "Quick Union" %}

{% tabs Quick-Union %}
<!-- tab Data Structure -->
```pseudocode
arr[N];  // parents of objects
```
<!-- endtab -->

<!-- tab root(i) -->

```pseudocode
while (i != arr[i]):  // not root
	i = arr[i];  // go check parent
```
<!-- endtab -->

<!-- tab union(a,b) -->
```pseudocode
ra = root(a);
rb = root(b);
arr[ra] = rb;  // set rb as ra's parent
```
<!-- endtab -->

<!-- tab find(a,b) -->
```pseudocode
return root(a) == root(b);
```
<!-- endtab -->
{% endtabs %}

### Improvements to QU

> Avoid **`Tall`** trees

#### Weighted QU

> smaller tree goes to bigger tree
>
> {% asset_img weighted-qu.png "Weighted Quick-Union" %}

{% tabs Weighted-QU %}
<!-- tab Data Structure -->
```pseudocode
arr[N];  // parents
size[N];  // size of each tree whose root is i
```

{% asset_img path-compression-1.png 300 375 "size[9] = 3, size[3] = 8" %}
<!-- endtab -->

<!-- tab union(a,b) -->
```pseudocode
ra = root(a);
rb = root(b);
if (ra == rb): return;  // same root -> connected -> do nothing
if (size[ra] >= size[rb]):  // a's tree is bigger
	arr[rb] = ra;
	size[ra] += size[rb];
else:  // b's tree is bigger
	arr[ra] = rb;
	size[rb] += size[ra];
```
<!-- endtab -->
{% endtabs %}

{% asset_img weighted-is-flat.png 750 434 "Weighted QU tree is flat" %}

#### Path Compression

> 1. $root(a)$
>
> 2. $\forall p\ (on\ a's\ path\ to\ root): reconnect\ to\ root$

{% tabs Path-Compression %}
<!-- tab Before -->
{% asset_img path-compression-1.png 350 430 "before" %}
<!-- endtab -->

<!-- tab After -->
{% asset_img path-compression-2.png 600 300 "after" %}
<!-- endtab -->
{% endtabs %}

Weighted Quick-Union + Pass Compression: nearly `Linear-time`

> Union-Find: No Linear-time algorithm
