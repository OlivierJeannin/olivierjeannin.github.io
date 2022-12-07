---
title: Union-Find
date: 2021-09-09 13:50:49
categories:
  - Algorithm
---

# What is Union-Find Problem

## Connectivity

$a-b$: $a$ is connected with $b$

Properties:

- $a-a$

- $a-b \Longrightarrow b-a$

- $a-b,b-c \Longrightarrow a-c$

$A$ is a **connected component**: $a\in{A},b\in{A} \iff a-b$

{% asset_img connected-component.jpg 400 333 "3 connected components" %}

<!--more-->

## Union-Find

$union(a,b)$: *connect* $a$ and $b$

$find(a,b)$: *check* if $a$ and $b$ are connected *(True/False)*

Example here:

{% asset_img union-find-eg.png 350 220 %}

***Problem***:

$union()$ any $N$ objects randomly, at random time, then: ${\forall}a,b$, do $find(a,b)$ at any time.

```pseudocode
union(4, 0)
union(3, 2)
union(6, 5)
union(4, 9)
union(2, 1)
find(0, 7)  // false
find(8, 9)  // false
union(5, 0)
union(8, 6)
find(8, 9)  // true
```

# Algorithms

## Quick Find

connected $\iff$ same **status**

In this picture, 1, 2 and 4 have the same status 4; they are connected.

{% asset_img quick-find.jpg 350 270 %}

```pseudocode
arr[N];  // status of objects

union(a,b) {
	sa = arr[a];  // arr[a] will be updated soon!
	sb = arr[b];
	// 与 a 状态相同的，全改成 b 的状态。
	for all i in N:
		if (arr[i] == sa):
			arr[i] = sb;
}

find(a,b) {
	return arr[a] == arr[b];
}
```
## Quick Union

A connected component is now represented with a tree.

connected $\iff$ same **root**

Entries in array represent *parents* of indices:

{% asset_img quick-union.jpg 350 270 %}

2's parent is 6, 6's parent is 4, 4's parent is 4, 4 is the root.

```pseudocode
arr[N];  // parents of objects

root(i) {
	while (arr[i] != i)
		i = arr[i];  // go to parent
}

union(a, b) {
	ra = root(a);
	rb = root(b);
	arr[ra] = rb;  // set rb as ra's parent
}

find(a, b) {
	return root(a) == root(b);
}
```
It can be very *slow* when the tree is too tall or high.

## Improvements on QU

Avoid *tall* trees. Reduce their height.

### Weighted QU

Smaller tree goes to bigger tree.

{% asset_img weighted-qu.png 400 300 %}

By "big" and "small", there are 2 kinds of explanations:

1. **size**: number of nodes
2. **height**

{% asset_img size-height.jpg 400 285 %}

Either way, the algorithm has guaranteed performance of $\lg{N}$ at worst case.

```pseudocode
arr[N];  // parents
size[N];  // size of subtrees
// height[N];  // height of subtrees

union(a,b) {
	ra = root(a);
	rb = root(b);
	if (ra == rb):  // same root -> connected
		return;
	if (size[ra] >= size[rb]):  // a's tree bigger
		arr[rb] = ra;
		size[ra] += size[rb];  // update size
	else:  // b's tree is bigger
		arr[ra] = rb;
		size[rb] += size[ra];
}
```
Result is as below, weighted QU tree is flat:

{% asset_img weighted-is-flat.png 750 434 %}

### Path Compression

When searching for root of $i$, for each node in the path from $i$ to root, reconnect that node to root.

````pseudocode
root(i) {
    while (parent[i] != i) {
        parent[i] = root(parent[i]);  // set i's parent to root
        i = parent[i];
    }
    return parent[i];  // parent[i] and i are equal if i is root
}
````

{% tabs Path-Compression %}

<!-- tab Before -->

9 is newly added to this tree.

x goes up along path 9 -> 6 -> 3 -> 1 -> 0.

{% asset_img path-compression-1.png 300 375 %}

<!-- endtab -->

<!-- tab After -->

9 , 6 and 3 are reconnected to root 0.

{% asset_img path-compression-2.png 560 280 %}

<!-- endtab -->

{% endtabs %}

Think of where there are $M$ union-find oprations and $N$ elements. Total time spent is dependent on $M$, $N$, and algorithm itself.

Weighted Quick-Union + Pass Compression $\Rightarrow$ near *Linear-time* (but still not).

{% note warning %}

Union-Find: ***No** Linear-time algorithm.*

That is, $union()$ and $find()$ cannot both be Constant-time.

{% endnote %}
