---
title: "1295_find Numbers With Even Number of Digits"
date: 2020-04-14T02:07:26-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1295
[Link to the question] (https://leetcode.com/problems/find-numbers-with-even-number-of-digits/ "Find Numbers with Even Number of Digits")
```
Given an array nums of integers, return how many of them contain an even number of digits.

 

Example 1:

Input: nums = [12,345,2,6,7896]
Output: 2
Explanation: 
12 contains 2 digits (even number of digits). 
345 contains 3 digits (odd number of digits). 
2 contains 1 digit (odd number of digits). 
6 contains 1 digit (odd number of digits). 
7896 contains 4 digits (even number of digits). 
Therefore only 12 and 7896 contain an even number of digits.

Example 2:

Input: nums = [555,901,482,1771]
Output: 1 
Explanation: 
Only 1771 contains an even number of digits.

 

Constraints:

    1 <= nums.length <= 500
    1 <= nums[i] <= 10^5
```
After a little research on the internet, i came up with this solution. It is faster than recursive counting and also the logarithmic method. Also keep in mind this solution is only for the given constraints.
```go
func findNumbers(nums []int) int {
    ret := 0
    for _, val := range(nums) {
        if val == 100000 ||  (999 < val && val <= 9999) || (9 < val && val <= 99) {
            ret += 1
        }
    }
    return ret
}
```