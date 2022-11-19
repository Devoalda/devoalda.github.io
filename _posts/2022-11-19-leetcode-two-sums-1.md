---
layout: post
title: Leetcode - Two Sums(1)
date: '2022-11-19 15:01:45 +0800'
categories: [Code, C]
tags: [c, leetcode]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

# Input and Output

```shell
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

# Process
Saw guy doing it in [Assembly](https://www.youtube.com/watch?v=lALPErFlfNQ) but wanted to do it myself before watching the video so that I can understand it better.

Since the assumption is that there is only one solution, I can just brute force it by using two for loops. The first loop will be the first number and the second loop will be the second number. If the sum of the two numbers is equal to the target, then I can return the indices of the two numbers.

# Code
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target, int* returnSize){
    int *sums = (int *)malloc(numsSize * sizeof(int));
    int i, j, firstNum;
    *returnSize = 2;
    
    for(i = 0; i< numsSize; i++){
        firstNum = nums[i];
        int x = target - firstNum;
        for (j = i + 1; j<numsSize ; j++){
            if (nums[j] == x){
                sums[0] = i;
                sums[1] = j;
                return sums;
            }
        }
    }
return 0;
}
```
{: file="Two Sums.c" }

# Afterthoughts
1. Using a nested for loop, I first get the first number and assume that the second number is the difference between the target and the first number.
2. I subtracted the first number from the target and used a second for loop to find the position of the second number in the array.
3. I then assign the indexes to the sums array and return the array.

This is an "easy" challenge but I think the solution could be more elegant than just plain brute force. I'll try to think of a better solution later. This solution took $99 ms$ and $6.2MB$ of memory, which was still pretty fast and memory efficient.