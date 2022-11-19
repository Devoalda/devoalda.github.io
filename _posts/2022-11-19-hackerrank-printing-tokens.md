---
layout: post
title: HackerRank - Printing Tokens
date: '2022-11-19 10:15:33 +0800'
categories: [Code, C]
tags: [c, hackerrank]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
Given a sentence, `s`, print each word of the sentence in a new line.

## Input and Output Format

```shell
# Input:
This is C

# Output:
This
is
C
```
{: file="Input and Output" }

# Process
This was a pretty simple challenge. Completing the code, I've added a for loop to print each character at a time, scanning for any blank spaces and "replacing" that with a newline escape character `\n`.

# Code

```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {

    char *s;
    s = malloc(1024 * sizeof(char));
    scanf("%[^\n]", s);
    s = realloc(s, strlen(s) + 1);
    //Write your logic to print the tokens of the sentence here.
    for (int i = 0;i <strlen(s); i++){
        //if(s[i] != ' '){
        //    printf("%c", s[i]);
        //}
        //else{
        //    printf("\n");
        //}
        (s[i] != ' ') ? printf("%c", s[i]) : printf("\n");
    }
    return 0;

```
{: file="Printing Tokens.c" }

# Afterthoughts
Looping through each character in the string, a check is done to check for blankspaces and replacing them with a newline character. 

I did it using an ordinary for loop but translated that same loop to a ternery operator for elegance. I really like the use of ternery operators in C.

This challenge earned me 20 points!