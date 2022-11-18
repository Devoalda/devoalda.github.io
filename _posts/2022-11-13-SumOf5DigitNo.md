---
title: HackerRank - Sum of Digits of a Five Digit Number
date: 2022-11-13 08:00:00 
categories: [Code, HackerRank]
tags: [c]     # TAG names should always be lowercase
author: <dev1>
math: true
---

# Introduction
Given a five digit integer, print the sum of its digit
**Input**: 5 digit number, n
**Output**: sum of 5 digit number

## Input and Output Format

```
# Input
10564

# Output
16
```
{: file="Sum Of Digits of a Five Digit Number.c" }

$1+0+5+6+4=16$

> This is a watered-down version of the question
{: .prompt-info }


## Process
This was my thought process while attempting this challenge. 

1. Calculate the number of digits
	1. By dividing the number by 10 and incrementing a counter in a while loop
	2. The number of digits can be found
2. In a for loop to loop through the total number of digits (5)
	1. `sum += number % 10`
	2. `number /= 10 `
		1. This is to remove the LSB of the number for each iteration of the loop
3. Print out the sum


# Code

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
	
    int n;
    scanf("%d", &n);
    //Complete the code to calculate the sum of the five digits on n.
    int sum = 0, divisor=10, x = n;
    if (n>=10000 && n <= 99999){
        int noOfDigits = 0;
        while (n!= 0){
            n /= 10;
            noOfDigits++;
        }
        
        for (int i = 0; i<= noOfDigits; i++){
            sum += x % divisor;
            x /= divisor;
        }
        printf("%d",sum);
    }
    return 0;
}
```
{: file="Sum Of Digits of a Five Digit Number.c" }

# Afterthoughts
I initially thought that I have to increment the mod divisor by 10 everytime (i.e. $10 \times 10 \times 10$) but soon realize that it is only going to make the number bigger.

I use the variable `n` to calculate the number of digits and used the same variable to calculate the sum, this gave me a result of 0 cuz `n` started from 0 in the loop!

I then realize I should probably initialize `sum` to 0 cuz any uninitialized number will be given garbage, this would screw up the sum of numbers.
