---
layout: post
title: Leetcode - Ugly Number(263)
date: '2022-11-18 21:23:39 +0800'
categories: [Code, C]
tags: [c, leetcode]     # TAG names should always be lowercase
author: <dev1>
math: true
---

# Introduction
Write a program to check whether a given number is an ugly number. Ugly numbers are positive numbers whose prime factors only include 2, 3, 5.

Given an integer n, return true if n is an ugly number.

## Input and Output Format

```shell
Input: n = 6
Output: true
Explanation: 6 = 2 × 3
```

# Process
This was my thought process while attempting this challenge.
First, to return false if the number is less than 1. Next is to check if the number `n` is divisible by 2, 3 or 5, so, following the algorithm as I've done this in Python before, I created the function `keepDividingWhenDiviible()` to reduce the number based on its prime factors. I assigned `n` to the return value of the function that divides the number by 2, 3 or 5 and returned the condition that checks if the number is 1.

# Code

```c
bool isUgly(int n){
    if (n<=0)
        return false;
    
    n = keepDividingWhenDivisible(n,2);
    n = keepDividingWhenDivisible(n,3);    
    n = keepDividingWhenDivisible(n,5);
    
    return (n==1) ; 

}

int keepDividingWhenDivisible(int dividend, int divisor){
    while (dividend % divisor == 0){
        dividend /= divisor;
    }
    return dividend;
}
```
{: file="Ugly Number.c" }

Honestly, I realized that I was reading through the algorithm explanation on leetcode but didn't realize that I wasn't reading the description, I've created the function accordingly as I've done this using python in the past.

# Afterthoughts
1. The function that assigned `n` could be reduced to a loop, this is one way to improve the code.
2. I initially thought that the algorithm wanted to create a recursive function to check if the number is divisible by 2, 3 or 5. But instead, the easier and more efficient way is to constantly check the remainder of the arithmetic operation and divide the number by the divisor until the remainder is not 0.
3. I wanted to use a ternary operator to return the condition that checks if the number is 1, but I realized that it would just not be useful as the check will just return its corrosponding boolean value and there was no point in using a ternary operator.