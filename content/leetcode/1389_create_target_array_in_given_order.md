---
title: "1389_create_target_array_in_given_order"
date: 2020-04-17T01:44:26-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1389
[Link to the question] (https://leetcode.com/problems/create-target-array-in-the-given-order/ "create target array in the given order")

```
Given two arrays of integers nums and index. Your task is to create target array under the following rules:

    Initially target array is empty.
    From left to right read nums[i] and index[i], insert at index index[i] the value nums[i] in target array.
    Repeat the previous step until there are no elements to read in nums and index.

Return the target array.

It is guaranteed that the insertion operations will be valid.
Example 1:
Input: nums = [0,1,2,3,4], index = [0,1,2,2,1]
Output: [0,4,1,3,2]
Explanation:
nums       index     target
0            0        [0]
1            1        [0,1]
2            2        [0,1,2]
3            2        [0,1,3,2]
4            1        [0,4,1,3,2]

Example 2:
Input: nums = [4,2,4,3,2], index = [0,0,1,3,1]
Output: [2,2,4,4,3]
Explanation:
nums       index     target
0            0        [4]
1            1        [2,4]
2            2        [2,4,4]
3            2        [2,2,4,4]
4            1        [2,2,4,4,3]
```
This is my solution for printing the target array in the given order.
```go
package main

import (
	"fmt"
)

func createTargetArray(nums []int, index []int) []int {
	ret := make([]int, len(index))
	for i := 0; i < len(ret)-1; i++ {
		k := index[i]
		for j := i + 1; j < len(ret); j++ {
			if index[j] <= k {
				k++
			}
		}
		ret[k] = nums[i]
	}
	ret[index[len(ret)-1]] = nums[len(ret)-1]
	return ret
}

func main() {
	nums := []int{4, 2, 4, 3, 2}
	index := []int{0, 1, 0, 3, 1}
	fmt.Println(createTargetArray(nums, index))
}
```