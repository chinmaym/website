---
title: "1_two_sum"
slug: "Leetcode"
date: 2020-10-24T13:00:07-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1
[Link to the question](https://leetcode.com/problems/two-sum/ "2 Sum")
```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].

Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]

Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
```
My solution - 
```go
func twoSum(nums []int, target int) []int {
    diffMap := make(map[int]int)
    for i:=0; i < len(nums); i++ {
        if val, ok:= diffMap[nums[i]]; ok {
            return []int{val, i}
        }
        diffMap[target - nums[i]] = i
    }
    return []int{-1, -1}
}
```