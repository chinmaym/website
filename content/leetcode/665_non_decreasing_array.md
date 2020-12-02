---
title: "665_non_decreasing_array"
date: 2020-04-12T03:05:53-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 665
[Link to the question](https://leetcode.com/problems/non-decreasing-array/ "Non-decreasing Array")
```
Given an array nums with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.

We define an array is non-decreasing if nums[i] <= nums[i + 1] holds for every i (0-based) such that (0 <= i <= n - 2).

Example 1:

Input: nums = [4,2,3]
Output: true
Explanation: You could modify the first 4 to 1 to get a non-decreasing array.

Example 2:

Input: nums = [4,2,1]
Output: false
Explanation: You can't get a non-decreasing array by modify at most one element.
```
My solution -
```py
class Solution(object):
    def checkPossibility(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if len(nums) < 2:
            return True
        i = 0
        j = len(nums)-1
        minVal = -1*(99**99)
        maxVal = 99**99
        while i < len(nums)-1:
            if nums[i] <= nums[i+1]:
                minVal = nums[i]
                i += 1
            else:
                break
        while j> 0:
            if nums[j] >= nums[j-1]:
                maxVal = nums[j]
                j-=1
            else:
                break
        
        if i==j-1 and (nums[j] > minVal or nums[i] < maxVal):
            return True
        if i > j:
            return True
        return False
```