---
title: Insertion Sort
date: 2022-11-27 21:38:07
categories:
  - Algorithm
  - Sort
---

Different from selection sort, you go over the whole array just once.

For each unsorted item (let's call it $a$), you check whether $a$ is smaller than the one on its left side. If so, these two items are not in order, it is time you swap them. Keep on swapping until $a$ is bigger than the item on the left. After this, move on to the next unsorted item. 

<!--more-->

# Example

An example should help you better understand it. Let the array be `2 1 5 4 3`. First item is `2`. There's nothing before it, so we skip. Then check `1`, which is smaller than `2`, not in order, so we swap. The array becomes `1 2 5 4 3`. Note that we have already checked `2`, so we don't mind it and go to `5` directly. `5` is bigger than `2`, move on. Then `4`, smaller than `5`, not in order, swap. Now the array is `1 2 4 5 3`. Check `4` again, bigger than `2`, correct order, move on. Next is `3`, less than `5`, swap, giving us `1 2 4 3 5`. Check `3` again, swap. `1 2 3 4 5`. Check `3` again, move on, nothing behind `5`, and end. The changes of the array would be like this:

```
2 1 5 4 3
2  1 5 4 3
1 2  5 4 3
1 2 5  4 3
1 2 4 5  3
1 2 4 3 5
1 2 3 4 5
```

# Analysis

In the average case, insertion sort operates both compare and exchange for $\sim N^2/4$ times ($N$ being number of items in the array). As for the best case (sorted, ascending array) and the worst (descending array), it is easy to get the numbers.

Besides those, there is one more interesting case, that is, when the array is **partially sorted**. To understand what's a "partially sorted" array, first consider another concept: **inversion**. An inversion is a pair of items that are not in order. For example, in array `1 2 5 4 3`, there are three inversions (pairs), namely, `5-4`, `5-3`, and `4-3`. When the number of inversions (pairs) in an array is $\le cN$ ($c$ being any constant number), this array is **partially sorted**. Using insertion sort on partially sorted arrays, $\#exchange=\#inversion,\#compare=\#exchange+N$, so the time cost will be *linear*.
