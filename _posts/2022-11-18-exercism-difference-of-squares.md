---
layout: post
title: Exercism - Difference of Squares
date: '2022-11-18 18:35:51 +0800'
categories: [Code, C]
tags: [c, exercism]     # tag names should always be lowercase
author: <dev1>
math: true
---

# Introduction
Find the difference between the square of the sum and the sum of the squares of the first n natural numbers.

The square of the sum of the first ten natural numbers is $(1 + 2 + ... + 10)^2 = 55^2 = 3025$.

The sum of the squares of the first ten natural numbers is $1^2 + 2^2 + ... + 10^2 = 385$.

Hence the difference between the square of the sum of the first ten natural numbers and the sum of the squares of the first ten natural numbers is $3025 - 385 = 2640$.

You are not expected to discover an efficient solution to this yourself from first principles; research is allowed, indeed, encouraged. finding the best algorithm for the problem is a key skill in software engineering.

> As referenced from [Exercism](https://exercism.org/tracks/c/exercises/difference-of-squares)
{: .prompt-info }

# Process
This was a "fill in the blank" sort of question or "complete the function".

I first found the **sum of the squares of the numbers** from 1 to N.
Then I found the **square of the sum of the numbers** from 1 to N.
The function `difference_of_squares()` returns the **difference between the two numbers**.

Both sum functions are similar in that they use a while loop to loop through the numbers from 1 to number (N), decreasing N by 1 each iteration instead of using a for loop, which I was more comfortable. This is more 


# Code


```c
#include "difference_of_squares.h"
#include <math.h>
unsigned int sum_of_squares(unsigned int number){
    int sum = 0;
    while (number > 0){
        sum += pow(number,2);
        number--;
    }
return sum;
}
unsigned int square_of_sum(unsigned int number){
    int sum = 0;
    while (number > 0){
        sum +=number;
        number--;
    }
return pow(sum, 2);
}
unsigned int difference_of_squares(unsigned int number){
    int sumOfSquares = sum_of_squares(number);
    int squareOfSum = square_of_sum(number);
    return squareOfSum - sumOfSquares;
}
```
{: file="difference_of_squares.c" }


```c
#ifndef DIFFERENCE_OF_SQUARES_H
#define DIFFERENCE_OF_SQUARES_H
unsigned int sum_of_squares(unsigned int number);
unsigned int square_of_sum(unsigned int number);
unsigned int difference_of_squares(unsigned int number);
#endif
```
{: file="difference_of_squares.h" }

# Conclusion
This was a good practice for while loops and function calls in C. I was able to use the `pow()` function to find the square of a number.