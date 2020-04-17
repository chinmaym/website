---
title: "1342_number_of_steps_to_reduce_to_zero"
date: 2020-04-16T01:59:14-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1342
[Link to the question] (https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/ "Number of Steps to Reduce a Number to Zero")
```
Given a non-negative integer num, return the number of steps to reduce it to zero. If the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

 

Example 1:

Input: num = 14
Output: 6
Explanation: 
Step 1) 14 is even; divide by 2 and obtain 7. 
Step 2) 7 is odd; subtract 1 and obtain 6.
Step 3) 6 is even; divide by 2 and obtain 3. 
Step 4) 3 is odd; subtract 1 and obtain 2. 
Step 5) 2 is even; divide by 2 and obtain 1. 
Step 6) 1 is odd; subtract 1 and obtain 0.
```

My solution -
```go
func numberOfSteps (num int) int {
    if num == 0 {
        return 0
    }
    if num % 2 == 0 {
        return numberOfSteps(num/2) + 1
    } else {
        return numberOfSteps(num-1) + 1
    }
}
```