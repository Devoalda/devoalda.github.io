---
layout: post
title: HackerRank - Handshake
date: '2022-11-20 15:35:37 +0800'
categories: [Code, C]
tags: [c, hackerrank,math]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
At the annual meeting of Board of Directors of Acme Inc. If everyone attending shakes hands exactly one time with every other attendee, how many handshakes are there?

## Input and Output Format

```shell
# Input:
2
1
2
# Output:
0
1
```
{: file="Input and Output" }

## Process

This is a math challenge. So using the primitive way of counting, I counted the number of handshakes for each number of attendees, I came up with this:

```
n  = 1 2 3 4 5
HS = 0 1 3 6 10
```
where `HS` is the number of handshakes.

So, the interval between each number of handshake is `1, 2, 3, 4, 5`. With this, I was able to come up with a simple formula to calculate the number of handshakes with respect to the number of attendees `n`: 

$$
HS_n = \frac{n(n-1)}{2}
$$

# Code
This formula could be use as the return value of the function `int numberOfHandshakes(int n)`, shown below.

```c
int handshake(int n) {
    return n*(n-1)/2;
}
```
{: file="Handshake.c" }

# Afterthoughts
This is a pretty simple challenge that allows me to practice sequence counting, I was able to apply what I've learnt in this challenge.