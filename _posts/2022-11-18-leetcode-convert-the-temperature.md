---
layout: post
title: Leetcode - Convert the temperature (2469)
date: '2022-11-18 20:51:00 +0800'
categories: [Code, C]
tags: [c, leetcode]     # TAG names should always be lowercase
author: <dev1>
math: true
---

# Description
You are given a non-negative floating point number rounded to two decimal places celsius, that denotes the temperature in Celsius.

You should convert Celsius into Kelvin and Fahrenheit and return it as an array ans = [kelvin, fahrenheit].

Return the array ans. Answers within $10^{-5}$ of the actual answer will be accepted.

Note that:

Kelvin = Celsius + 273.15

Fahrenheit = Celsius * 1.80 + 32.00

## Example

```shell
Input: celsius = 36.50
Output: [309.65000,97.70000]
Explanation: Temperature at 36.50 Celsius converted in Kelvin is 309.65 and converted in Fahrenheit is 97.70.
```

# My thought process
I have no experience in creating arrays dynamically using `malloc` and had to look up how to do it.

This is one of the examples from the book I was reading - "The C Programming Language" by Brian Kernighan and Dennis Ritchie.

Here is what I've done:
1. I first created 2 variables of `double` data type to store the values of Kelvin and Fahrenheit.
2. Then I created a pointer to a double data type and allocated memory for it using `malloc`.
3. Using the Formula given, I calculated the values of Kelvin and Fahrenheit.
4. I assigned the value of 2 to the returnSize pointer
5. I then assigned the values of Kelvin and Fahrenheit to the array using the ans pointer.
6. Lastly, I returned the ans pointer.

# Code
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
double* convertTemperature(double celsius, int* returnSize){
    double fah, kel;
    double *ans = (double *) malloc(2 * sizeof(double));
    
    kel = celsius + 273.15;
    fah = celsius * 1.80 + 32.00;
    
    
    *returnSize = 2;
    
    ans[0] = kel;
    ans[1] = fah;
    
    return ans;
}
```
{: file="Convert the temperature.c" }

The malloc function creates a size of $2\times$ the size of a `double` data type to store both the values of Kelvin and Fahrenheit, this allows for dynamic allocation of memory.

# Afterthoughts
This program could probably be improved by directly assigning the ans pointer to the values of Kelvin and Fahrenheit during the calculation. This would reduce the number of lines of code and reduce the memory usage as lesser variables are created.

I need to have a better understanding of `malloc` and its usage.
