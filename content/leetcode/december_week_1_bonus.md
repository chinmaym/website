---
title: "December_week_1_bonus"
date: 2020-12-02T01:21:46-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---

# Leetcode December Challenge Day 1

[Link to the question](https://leetcode.com/explore/challenge/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3550/ "Shortest Word Distance")

Solution
```py
class Solution(object):
    def shortestDistance(self, words, word1, word2):
        """
        :type words: List[str]
        :type word1: str
        :type word2: str
        :rtype: int
        """
        val1 = val2 = None
        dist = len(words)
        for i in range(len(words)):
            if words[i] == word1:
                val1 = i
            if words[i] == word2:
                val2 = i
            if val1 != None and val2 != None:
                dist = min(dist,abs(val1-val2)) 
        return dist
```