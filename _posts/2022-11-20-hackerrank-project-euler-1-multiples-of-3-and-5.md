---
layout: post
title: 'HackerRank - Project Euler #1: Multiples of 3 and 5'
date: '2022-11-20 16:15:33 +0800'
categories: [Code, C]
tags: [c, hackerrank,math,projecteuler]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
Find the sum of all the multiples of 3 or 5 below N.

## Input and Output Format

```shell
# Input:
2
10
100
# Output:
23
2318
```
{: file="Input and Output" }

### Explanation
For N = 10, if we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
Similarly for N = 100, we get 2318.

# Process
Using a for loop to loop through all the numbers below N, and check if the number is a multiple of 3 or 5, if it is, add it to the sum, and print out the sum at the end of the loop.

# Code
```c
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

void sumMultiple(int n);

int main(){
    int t; 
    scanf("%d",&t);
    for(int a0 = 0; a0 < t; a0++){
        int n; 
        scanf("%d",&n);
        sumMultiple(n);
        printf("\n");
    }
    return 0;
}

void sumMultiple(int n){
    int sum = 0;
    for(int i = 1; i< n; i++){
        if(i%3 == 0 || i% 5 == 0){
            sum += i;
        }
        
    }
    printf("%d", sum);
}
```
{: file="Multiples of 3 and 5.c" }

# Afterthoughts
This solution was a bit of a brute force solution, but it worked. It passed `4/6` test cases and needed to be optimized. I'm sure there's a more efficient way to do this, but I'll take a second look at this later.

# References
- [HackerRank - Project Euler #1: Multiples of 3 and 5](https://www.hackerrank.com/contests/projecteuler/challenges/euler001/problem)