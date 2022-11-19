---
layout: post
title: HackerRank - Sherlock and Divisors
date: '2022-11-19 11:33:55 +0800'
categories: [Code, C]
tags: [c, hackerrank]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
Watson gives an integer `N` to Sherlock and asks him: What is the number of divisors of `N` that are divisible by `2`?

## Input and Output Format

```shell
# Input:
2
9
8

# Output:
0
3
```
{: file="Input and Output" }

### Explanation
9 has three divisors 1, 3 and 9 none of which is divisible by 2.
8 has four divisors 1,2,4 and 8, out of which three are divisible by 2.


# Process
I thought that this is one of the easier ones to do, I first did a while loop to loop through all the numbers from 1 to `N` and check if it is divisible by 2. If it is, I increment a counter. I then print the counter. This only worked for the first test case. I then did a for loop to loop through all the numbers from 1 to `N` and check if it is divisible by 2. But this was a code that was not optimized for HackerRank's tests and failed some test cases.

I then loop through numbers from 1 to square root of `n` as the divisors of `n` are always less than or equal to the square root of `n`. 
1. I first checked that `i` is divisible by `n`. 
2. I then check if the number `i` is divisible by 2 and increment the counter if it is. 
3. Next, I checked if `n/i` is divisible by 2 and increment the counter if it is.
4. THe last statement is to remove the number `n` if it is divisible by 2 as it is a duplicate.

This code was after some trial and error and multiple references.

# Code

```c
int divisors(int n) {
    int count = 0;
    for (int i=1;i<=sqrt(n);i++)
    {
        if (n%i==0)
        {
            count = (i%2==0) ? count + 1 : count;  
            count = ((n/i)%2==0) ? count + 1 : count;
        }
    }
    if ((n%2==0) && (pow((int)sqrt(n), 2) == n))  
    count--;
    return count;
}
```
{: file="divisors.c" }

# Afterthoughts
Math theory was very important and applicable to this challlenge, the fact that the divisors of `n` are always less than or equal to the square root of `n` was very important. This is also one of the ways to check if the number is a prime doing a prime factorization from 1 to the square root of the number.

This is an interesting challenge that made me apply my math knowledge learnt. 