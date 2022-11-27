---
title: Selection Sort
date: 2022-11-27 18:49:04
tags:
categories:
  - Algorithm
  - Sort
---

Selection sort is really simple.

You go all unsorted items over and over, and each time you choose the smallest item and bring it to the front as sorted. Equivalently, you can swap the smallest with the first unsorted item, so that it joins right after with  sorted ones.

<!--more-->

An example is good for understanding. ==example==

As you bring the smallest to the front, the sorted ones are absolutely no bigger than unsorted ones. Because of that, in the subarray of sorted ones, values of item key will grow bigger (or sometimes remain the same).

This algorithm performs $\sim N^2/2$ compares and $\sim N$ swaps.
