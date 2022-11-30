---
title: Shuffling
date: 2022-11-30 15:50
categories:
  - Algorithm
  - Sort
---

**Shuffling** is to rearrange items to random order.

A simple way of shuffling is to attribute to each item a random number as the key, and sort items by this key.

There is another shuffling algorithm created by Knuth. The array is considered to consist of a shuffled subarray and an unshuffled array. For each unshuffled item `a[i]`, generate a random integer $r$ ($r\in[0,i]$), then swap `a[i]` and `a[r]`. After this, `a[i]` (now the new `a[r]`) is part of the shuffled subarray, and you move on to next unshuffled item.

```
		a d b g f c e
i=0, r=0
		a  d b g f c e
i=1, r=0
		d a  b g f c e
i=2, r=2
		d a b  g f c e
i=3, r=1
		d g b a  f c e
i=4, r=3
		d g b f a  c e
i=5, r=0
		c g b f a d  e
i=6, r=4
		c g b f e d a
```
