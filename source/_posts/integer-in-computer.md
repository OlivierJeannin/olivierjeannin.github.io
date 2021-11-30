---
title: Integer
date: 2021-10-10 13:47:54
tags:
categories:
  - [Computer System]
description: Representations and operations of integers in computer system.
---

# Unsigned

## Representation

$$
\begin{align*}
x&=x_{w-1}*2^{w-1}+\sum_{i=0}^{w-2}x_i*2^{i} \\
 &=\sum_{i=0}^{w-1}x_i*2^{i}
\end{align*}
$$

| Binary |    ->    | Decimal |      |
| :----: | :------: | :-----: | :--: |
|  0000  | +0+0+0+0 |   +0    |      |
|  ...   |   ...    |   ...   |      |
|  0111  | +0+4+2+1 |   +7    |      |
|  1000  | +8+0+0+0 |   +8    |      |
|  ...   |   ...    |   ...   |      |
|  1111  | +8+4+2+1 |   +15   | UMax |

## Arithmetic

# Signed

## Representation

### Two's Complement（补码）

$$
x=-x_{w-1}*2^{w-1}+\sum_{i=0}^{w-2}x_i*2^{i}
$$

| Binary |    ->    | Decimal |      |
| :----: | :------: | :-----: | :--: |
|  0000  | +0+0+0+0 |   +0    |      |
|  ...   |   ...    |   ...   |      |
|  0111  | +0+4+2+1 |   +7    | TMax |
|  1000  | -8+0+0+0 |   -8    | TMin |
|  ...   |   ...    |   ...   |      |
|  1111  | -8+4+2+1 |   -1    |      |

### Singn-Magnitude（原码）

$$
x=(-1)^{x_{w-1}}*\sum_{i=0}^{w-2}x_i*2^{i}
$$

| Binary |    ->    | Decimal |
| :----: | :------: | :-----: |
|  0000  | +(0+0+0) |   +0    |
|  ...   |   ...    |   ...   |
|  0111  | +(4+2+1) |   +7    |
|  1000  | -(0+0+0) |   -0    |
|  ...   |   ...    |   ...   |
|  1111  | -(4+2+1) |   -7    |

### Ones' Complement（反码）

$$
x=-x_{w-1}*(2^{w-1}-1)+\sum_{i=0}^{w-2}x_i*2^{i}
$$

| Binary |    ->    | Decimal |
| :----: | :------: | :-----: |
|  0000  | +0+0+0+0 |   +0    |
|  ...   |   ...    |   ...   |
|  0111  | +0+4+2+1 |   +7    |
|  1000  | -7+0+0+0 |   -7    |
|  ...   |   ...    |   ...   |
|  1111  | -7+4+2+1 |   -0    |

## Arithmetic

