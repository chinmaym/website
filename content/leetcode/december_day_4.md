---
title: "December_day_4"
date: 2020-12-08T00:12:05-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---
# Leetcode December Challenge Day 4
[Link to the question](https://leetcode.com/explore/challenge/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3554/ "Day 4")

Solution to the question

```py
class Solution(object):
    def kthFactor(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: int
        """
        i = 1
        while i<=n:
            if n%i == 0:
                k -= 1
            if k == 0:
                return i
            i += 1
        return -1
```