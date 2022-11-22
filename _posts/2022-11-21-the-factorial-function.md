---
layout: post
title: The Factorial Function
date: '2022-11-21 16:03:48 +0800'
categories: [Code]
tags: [c,python,math]     # TAG names should always be lowercase
author: dev1
math: true
---

# The Factorial Function

The factorial function is a mathematical function that takes a non-negative integer `n` and returns the product of all positive integers less than or equal to `n`. The factorial function is denoted by `n!`.

This is a reference page for the factorial function, written in C and Python.

## Background
The first 10 factorials are:

| n | n! |
|---|----|
| 0 | 1 |
| 1 | 1 |
| 2 | 2 |
| 3 | 6 |
| 4 | 24 |
| 5 | 120 |
| 6 | 720 |
| 7 | 5040 |
| 8 | 40320 |
| 9 | 362880 |
| 10 | 3628800 |

Where $n!=n\times(n-1)\times(n-2)\times\cdots\times2\times1$ and $n! = n\times(n-1)!$.


The [Wikipedia page](https://en.wikipedia.org/wiki/Factorial) has a more detailed explanation of the factorial function.

# Code
## Psuedocode
This is the psuedocode for the factorial function:
```
BEGIN
    FUNCTION factorial(n)
        IF n = 0
            RETURN 1
        ELSE
            RETURN n * factorial(n-1)
        END IF
    END FUNCTION
END
```
{: file="Factorial Function Psuedocode" }

## Factorial in C
This is a sample factorial function that gets the user's input and returns the factorial of the input, written in C.

```c
#include <stdio.h>

int main();
int factorial(int n);

int main(){
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    int fac = factorial(n);
    printf("\nThe factorial of %d is %d.", n, fac);
}

int factorial(int n){
    if(n == 0 || n == 1){
        return 1;
    }
    else{
        return(n* factorial(n-1));
    }
    //return (n == 0) ? 1 : (n * factorial(n-1));
}
```
{: file="Factorial.c" }

```shell
Enter a number: 9

The factorial of 9 is 362880.
```
{: file="Factorial.c Input and Output" }

The recursive factorial function could be simplified to a single line of code:

```c
return (n == 0) ? 1 : (n * factorial(n-1));
```
{: file="Factorial With Ternary Operator" }

This returns 1 if `n` is 0, otherwise it recursively returns `n` multiplied by the factorial of `n-1`.

I really like the use and elegance of Ternary Operators in C.

## Factorial in Python
This is the same factorial function written in Python.

```python
def factorial(x):
    if (x == 0):
        return (1)

    else:
        return (x * factorial(x - 1))

#    return (1 if x == 0 else x * factorial(x - 1))
        
num = int(input("Please Enter a number: "))
print("Factorial: ",str(factorial(num)))
```
{: file="Factorial.py" }


```shell
Please Enter a number: 9
Factorial:  362880
```
{: file="Factorial.py Input and Output" }


```python
def factorial(x):
    return (1 if x == 0 else x * factorial(x - 1))
```
{: file="Factorial.py" }

Similar to the [C Version](#factorial-in-c), the Python version could be simplified to a single line of code.