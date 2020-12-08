---
title: "December_day_5"
date: 2020-12-08T00:14:00-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---
# Leetcode December Challenge Day 5

[Link to the question](https://leetcode.com/explore/challenge/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3555/ "Day 5")

Solution to the question

```py
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        cur=0
        prev=-10
        while cur < len(flowerbed)-1:
            if flowerbed[cur] != 1 and (cur - prev > 1) and (flowerbed[cur+1]) != 1:
                flowerbed[cur] = 1
                prev = cur
                n -= 1
            elif flowerbed[cur] == 1:
                prev = cur
            cur += 1
        if n == 1 and (cur - prev > 1) and flowerbed[cur] != 1:
            return True
        if n > 0:
            return False
        return True
```
