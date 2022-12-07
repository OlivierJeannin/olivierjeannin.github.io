---
title: Shellsort
date: 2022-11-27 21:44:58
categories:
  - Algorithm
  - Sort
---

This algorithm is tricky.

In insertion sort, when you swap, an item is compared with another that is right before it, so you can only move it *one* step forward. Shellsort lets you move an item several steps forward when each compare is done. The intuition is simple, but it is a bit difficult to express in words.

<!--more-->

# 1st Round

First, choose a number called $h$. Split the array into subarrays, each of which contains $h$ items. (If there aren't enough number of items at the end of the array, it doesn't matter.) Using the insertion-sort method, you *compare and swap* the 1st items in every subarray, then 2nd items, then 3rd, and so on, until every item in the array is checked.

Let me give you an example here. Let $h$ be 7, and array be `5 2 3 8 9 6 7 1 4 0`, with 10 items in total. So the array is split up as `5 2 3 8 9 6 7 | 1 4 0`. The ones you want to compare and swap will be `5` and `1`. Having swapped with insertion-sort method, the resulting array will be like `1 2 3 8 9 6 7 | 5 4 0`.  Then compare and swap the 2nd items, `2`, and `4`. Array remains the same. Then do 3rd items, `3`, and `0`. Now array becomes `1 2 0 8 9 6 7 | 5 4 3`. Then 4th items, 5th items, and so on. We are lucky here, the array isn't changed.

Now you can see how shellsort moves items several steps forward. This kind way of sorting is called **h-sort**ing, meaning sorting with an interval $h$. 

# Later Rounds

However, this is not the end, because the array is still not completely sorted. The above is just one round of shellsort. We need to polish our result. In the 2nd round, we set $h$ to a smaller number. Say we set $h$ to 3. Array is split as `1 2 0 | 8 9 6 | 7 5 4 | 3`. Now we 3-sort the array. First do `1`, `8`, `7`, and `3`. Array becomes `1 2 0 | 3 9 6 | 7 5 4 | 8`. Then `2`, `9`, and `5`. Array changes to `1 2 0 | 3 5 6 | 7 9 4 | 8`. You might already get it, and this is getting boring, so I'll type no more. The result of this round is `1 2 0 | 3 5 4 | 7 9 6 | 8`.

This array is so stubborn! Still not in order! Smaller $h$! I call 1! Wait, isn't that the same as insertion sort? Yes, but not quite. This is insertion sort on a *partially sorted* array. (Remember?) It's quicker than normal, plain insertion sort (middle finger up). Anyways, this round we polish our array really hard, and it finally becomes what we want, `0 1 2 3 4 5 6 7 8 9`.

Below is all changes we make on this tough array:

```
5 2 3 8 9 6 7 1 4 0
h=7
5 2 3 8 9 6 7  1 4 0
1 2 3 8 9 6 7  5 4 0
1 2 0 8 9 6 7  5 4 3
h=3
1 2 0  8 9 6  7 5 4  3
1 2 0  7 9 6  8 5 4  3
1 2 0  7 9 6  3 5 4  8
1 2 0  3 9 6  7 5 4  8
1 2 0  3 5 6  7 9 4  8
1 2 0  3 5 4  7 9 6  8
h=1
1 2 0 3 5 4 7 9 6 8
1 0 2 3 5 4 7 9 6 8
0 1 2 3 5 4 7 9 6 8
0 1 2 3 4 5 7 9 6 8
0 1 2 3 4 5 7 6 9 8
0 1 2 3 4 5 6 7 9 8
0 1 2 3 4 5 6 7 8 9
```

# $h$ Value

In one word, shellsort is an algorithm where we *h-sort* an array multiple rounds, with value of $h$ decreasing in each round.

Now, the question is, how to decide what number $h$ should be in each round? Is it randomly chosen? Well, fundamentally, I would say, yes. But there are some sequences of $h$ value that have been verified to work better than other sequences. One such sequence is Knuth's $(3^x-1)/2$ , generating numbers `1,4,13,40,121,...`. Another is $2^x-1$, generating `1,3,7,15,31,...`. We used the latter one in the above example. Other than these, there are other sequences widely used, and new sequences are not yet found by researchers.

# Analysis

There is no accurate mathematical expression to how much shellsort costs.

Nonetheless, generally speaking, shellsort is much quicker than selection and insertion sorts. So it is widely used, and you can definitely trust people using it.
