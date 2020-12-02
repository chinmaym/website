---
title: "1281_subtract the Product and Sum of Digits of an Integer"
date: 2020-04-13T02:12:28-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1281
[Link to the question](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/ "Subtract the Product and Sum of Digits of an Integer")
```
Given an integer number n, return the difference between the product of its digits and the sum of its digits.

Example 1:

Input: n = 234
Output: 15 
Explanation: 
Product of digits = 2 * 3 * 4 = 24 
Sum of digits = 2 + 3 + 4 = 9 
Result = 24 - 9 = 15
```

My solution - 
```go
func subtractProductAndSum(n int) int {
    prod := 1;
    sum := 0;
    for n >0 {
        rem := n % 10;
        sum += rem;
        prod *= rem;
        n /= 10;
    }
    return prod - sum;
}
```