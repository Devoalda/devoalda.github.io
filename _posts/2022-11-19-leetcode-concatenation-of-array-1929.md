---
layout: post
title: Leetcode - Concatenation of array(1929)
date: '2022-11-19 08:43:07 +0800'
categories: [Code, C]
tags: [c, leetcode]     # TAG names should always be lowercase
author: dev1
math: true
---

# Introduction
Given an integer array nums of length n, you want to create an array ans of length 2n where ans[i] == nums[i] and ans[i + n] == nums[i] for 0 <= i < n (0-indexed).

Specifically, ans is the concatenation of two nums arrays.

Return the array ans.

 ## Example
```shell
Input: nums = [1,2,1]
Output: [1,2,1,1,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

# Process
This was a pretty simple one other that figuring out how to use `malloc` again. This would be much simpler to do in python.

After creating an array with size dynamically allocated to `2n` where `n` is the size of the input array, I've managd to follow the description and concatenate the array using a for loop.

There should probably be a more elegant and efficient way to do this, but I'll still need to learn more about pointers and arrays.


# Code

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getConcatenation(int* nums, int numsSize, int* returnSize){
    //int n = (sizeof(nums)/sizeof(int));
    int *ans = (int *)malloc(2 * numsSize * sizeof(int));
    int i;
    
    for (i = 0; i<numsSize; i++){
        ans[i] = nums[i];
        ans[i+numsSize] = nums[i];
        
    }
    *returnSize = 2 * numsSize;
    return ans;

}
``` 
{: file="Concatenation of array.c" }

# Afterthoughts
1. I initially thought of getting the size "dynamically" by using `sizeof(nums)/sizeof(int)` but I instead realize that I should just use the input parameter `numsSize` instead. However, I'm leaving it in the code as a comment for future reference.

2. I also had trouble with the second perimeter of the for loop, I used `i+2*numsSize` but I realized that I should just use `numsSize` instead as I didn't really have to loop through an empty array towards the end. So, looping through the array once with `i<numsSize` is enough to insert the values in position `i` and `i+numsSize`.

3. I didn't know that I should use all the input parameters and had a *heap buffer overflow error* until I added the `*returnSize = 2 * numsSize;` line as it is used to return the size of the array.

I'm still pretty new to the leetcode ecosystem and have to do more practices to truly understand the proper way of attempting the questions.