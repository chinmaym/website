---
title: "771_jewels_and_stone"
date: 2020-04-13T03:02:11-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 771
[Link to the question](https://leetcode.com/problems/jewels-and-stones/ "Jewels and Stones")
```
You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:

Input: J = "aA", S = "aAAbbbb"
Output: 3

Example 2:

Input: J = "z", S = "ZZ"
Output: 0
```
My solution - 
```go
func numJewelsInStones(J string, S string) int {
    stoneMap := make(map[string]int)
    for _,i := range(S) {
        stoneMap[string(i)] += 1
    }
    ret := 0
    for _,i:= range(J) {
        ret += stoneMap[string(i)]
    }
    return ret
}
```