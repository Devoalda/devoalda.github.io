---
layout: post
title: HackerRank - Minimum Height Triangle
date: '2022-11-21 17:19:32 +0800'
categories: [Code, C]
tags: [c, hackerrank,math]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
Given integers `b` and `a`, find the smallest integer `h`, such that there exists a triangle of height `h`, base `b`, having an area of at least `a`.

## Example Input Output
```shell
# Input:
2 2
# Output:
2
```
{: file="Input and Output" }

Explanation: 
The task is to find the height of the triangle having base `b = 2` and area `a = 2`. It turns out that the height is `h = 2`.

```shell
# Input:
17 100
# Output:
12
```
{: file="Input and Output" }

Explanation:
The task is to find the height of the triangle having base `b = 17` and area `a = 100`. It turns out that the height is `h = 12` and the triangle has an area of `102`.

# Process
The area of a triangle is given by the formula:

$$
A = \frac{1}{2}bh
$$

where `b` is the base and `h` is the height of the triangle. Manupulating the formula, we get:


$$
h = \frac{2A}{b}
$$

I knew I needed to use the ceiling function to get the smallest integer `h` that satisfies the condition. So I used the `ceil()` function from the `math.h` library to round the calculated value of the height up to the next integer. The formula can be changed to:

$$
h = \lceil\frac{2A}{b} \rceil
$$

We are able to use this formula to calculate the height of the triangle given the base and area.

# Code
```c
int lowestTriangle(int trianglebase, int area) {
    double height = ceil(2 * (double)area / (double)trianglebase);
    return (int)height;
}
``` 
{: file="Minimum Height Triangle.c" }

# Afterthoughts
Upon applying the manipulated formula, I was able to return the minimum height of the triangle, given the base and the area. 

However, All challenges come with their hurdles and I was met with some when I did this.
1. I initially used `int` for the height, but using a calculator to check the results, some results return a decimal value and `int` will truncate the decimal value. So, I changed the type to `double` and used `ceil()` to round up the value.
2. I needed to typecast the `area` and `trianglebase` to `double` to avoid integer division as the result of the division will be an integer.
3. The return value of the function is an `int`, so I had to typecast the `height` to `int`.

This solution passed all testcases.
