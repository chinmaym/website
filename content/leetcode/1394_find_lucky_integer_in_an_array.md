---
title: "1394_find_lucky_integer_in_an_array"
date: 2020-04-16T01:51:56-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1394
[Link to the question](https://leetcode.com/problems/find-lucky-integer-in-an-array/ "find lucky integer in an array")
```
Given an array of integers arr, a lucky integer is an integer which has a frequency in the array equal to its value.

Return a lucky integer in the array. If there are multiple lucky integers return the largest of them. If there is no lucky integer return -1.

 

Example 1:

Input: arr = [2,2,3,4]
Output: 2
Explanation: The only lucky number in the array is 2 because frequency[2] == 2.

Example 2:

Input: arr = [1,2,2,3,3,3]
Output: 3
Explanation: 1, 2 and 3 are all lucky numbers, return the largest of them.
```
This is my solution to the `find lucky integer in an array` problem.

```go
func findLucky(arr []int) int {
    numberMap := make(map[int]int)
    for _, val := range(arr) {
        numberMap[val] += 1
    }
    ret := -1
    for key, val := range(numberMap) {
        if key == val && key > ret {
            ret = key
        }
    }
    return ret
}
```
