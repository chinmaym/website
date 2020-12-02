---
title: "69 sqrt"
slug: "Leetcode"
date: 2020-04-13T02:44:22-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
[Link to the question](https://leetcode.com/problems/sqrtx/ "Sqrt")

```
Implement int sqrt(int x).

Compute and return the square root of x, where x is guaranteed to be a non-negative integer.

Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.

Example 1:

Input: 4
Output: 2

Example 2:

Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since 
             the decimal part is truncated, 2 is returned.

```
I have implemented a approximation algorithm by newton to find the sqrt of a number. Google it.

```go
func getNext(x float64, n float64) float64 {
    return 0.5*(x+(n/(x*1.0)))
}

func mySqrt(n1 int) int {
    x := 1.0
    n := float64(n1)
    for {
        nx := getNext(x, n)
        if math.Abs(x - nx) < 1 {
            x=nx
            break
        }
        x = nx
    }
    return int(x)
}
```