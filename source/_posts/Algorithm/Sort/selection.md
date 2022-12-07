---
title: Selection Sort
date: 2022-11-27 18:49:04
categories:
  - Algorithm
  - Sort
---

Selection sort is really simple.

You go all unsorted items over and over, and each time you choose the smallest item and bring it to the front as sorted. Equivalently, you can swap the smallest with the first unsorted item, so that it joins right after with  sorted ones.

<!--more-->

An example is good for understanding. For array `5 4 2 3 1`, first, we go over all elements to see which one is the smallest. We see `1` is smallest, so we swap `5` and `1`, thus the array becomes `1 4 2 3 5`. Now that `1` is already sorted, we no longer check it in the later rounds. The smallest item in the remaining ones is `2`, so we swap it with `4`, the one that takes the 1st place in the unsorted subarray. The array now is `1 2 4 3 5`. Now `3` is the smallest, and `4` is the 1st one in the unsorted array, so swap, resulting in `1 2 3 4 5`. Now the array is totally sorted, but the algorithm must continue. It runs the same procedure until `4` and `5` are checked and recognised as sorted.

```
5 4 2 3 1
1  4 2 3 5
1 2  4 3 5
1 2 3  4 5
1 2 3 4  5
1 2 3 4 5
```

As you bring the smallest to the front, the sorted ones are absolutely no bigger than unsorted ones. Because of that, in the subarray of sorted ones, values of item key will grow bigger (or sometimes remain the same).

This algorithm performs $\sim N^2/2$ compares and $\sim N$ swaps.
