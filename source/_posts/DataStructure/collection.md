---
title: Collections
date: 2021-09-17 18:35:45
categories:
 - Data Structure
---

In this article we consider 3 types of collections: stack, queue, and bag. They can all be implemented by the same underlying data structures -- either resizing array or linked-list.

<!--more-->

# Stack

FILO (First In, Last Out) / LIFO (Last In, First Out).

{% asset_img stack.png 200 280 "Stack" %}

## API

- Create a stack
- Push (add an element)
- Pop (remove an element)

## Implementation

### Linked List

{% asset_img stack-linked-list.png 200 400 "Stack by Linked List" %}

Each node in linked list:

```pseudocode
Node {
	DataType data;
	Node next;
}
```

Advantage:

- Quick to add & delete

Drawback:

- Not so easy to access the element you want (may need linear time)

Cost:

$$
\begin{gather*}
T(N)=O(1)\\
S(N)=\Theta (N)
\end{gather*}
$$

### Resizing Array

{% asset_img stack-resizing-array.png 364 150 "Stack by Resizing Array" %}

Resizing:

- `Double` the length when array is ***full***
- `Halve` the length when array is ***1/4 full***

Advantage:

- Quick to access every element (constant time)

Drawback:

- Resizing is expensive when $N$ is large, because you must copy all existing elements to the new array
- To save space, you have to rewind `tail` pointer when `head` is not at position 0

Cost:

$$
T(N)=
\begin{cases}
\Theta (1),&\text{best},\\
\Theta (N),&\text{worst},\\
\Theta (1),&\text{amortized},
\end{cases}
$$

# Queue

FIFO (First In, First Out).

{% asset_img queue.png 400 100 "Queue" %}

## API

- Create a queue
- Enqueue / add
- Dequeue / remove

## Implementation

### Linked List

{% asset_img queue-linked-list.png 640 160 "Queue by Linked List" %}

### Resizing Array

{% asset_img queue-resizing-array.png 418 160 "Queue by Resizing Array" %}

# Bag

No order, no out.

{% asset_img bag.png 200 280 "Bag" %}

## API

- Create a bag
- Add an element

## Implementation

A bag is just a stack without pop, or a queue without dequeue. I'm sure you can figure it out easily. : )