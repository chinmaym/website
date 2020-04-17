---
title: "1403_minimum_subsequence_in_non_increasing_array"
date: 2020-04-16T01:55:48-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1403
[Link to the question] (https://leetcode.com/problems/minimum-subsequence-in-non-increasing-order/ "Minimum Subsequence in Non-Increasing Order")
```
Given the array nums, obtain a subsequence of the array whose sum of elements is strictly greater than the sum of the non included elements in such subsequence. 

If there are multiple solutions, return the subsequence with minimum size and if there still exist multiple solutions, return the subsequence with the maximum total sum of all its elements. A subsequence of an array can be obtained by erasing some (possibly zero) elements from the array. 

Note that the solution with the given constraints is guaranteed to be unique. Also return the answer sorted in non-increasing order.

 

Example 1:

Input: nums = [4,3,10,9,8]
Output: [10,9] 
Explanation: The subsequences [10,9] and [10,8] are minimal such that the sum of their elements is strictly greater than the sum of elements not included, however, the subsequence [10,9] has the maximum total sum of its elements. 

Example 2:

Input: nums = [4,4,7,6,7]
Output: [7,7,6] 
Explanation: The subsequence [7,7] has the sum of its elements equal to 14 which is not strictly greater than the sum of elements not included (14 = 4 + 4 + 6). Therefore, the subsequence [7,6,7] is the minimal satisfying the conditions. Note the subsequence has to returned in non-decreasing order.  

Example 3:

Input: nums = [6]
Output: [6]
```

This is my solution to the `minimum subsequence in non-increasing order`.

```go
func minSubsequence(nums []int) []int {
    sort.Sort(sort.Reverse(sort.IntSlice(nums)))
    sum := 0
    for _, val := range(nums) {
        sum += val
    }
    ret := make([]int, 0)
    newSum := 0
    for _, val := range(nums) {
        newSum += val
        ret = append(ret, val)
        if newSum > (sum - newSum) {
            break
        }
    }
    return ret
}
```