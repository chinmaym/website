---
title: "December_day_7"
date: 2020-12-08T00:24:52-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---

# Leetcode December Challenge Day 7
[Link to the question](https://leetcode.com/problems/spiral-matrix-ii/ "Day 7")

Solution -
```py
class Solution(object):
    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        ret = [[0 for i in range(n)] for i in range(n)]
        a = 1
        for i in range(n/2+1):
            for j in range(i, n-i):
                ret[i][j] = a
                a +=1
            for k in range(i+1, n-i):
                ret[k][j] = a
                a += 1
            for l in range(j-1, i-1, -1):
                ret[j][l] = a
                a += 1
            for m in range(j-1, i, -1):
                ret[m][i] = a
                a += 1
        return ret
```