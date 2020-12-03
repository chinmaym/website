---
title: "December_day_1"
date: 2020-12-02T01:10:00-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---

# Leetcode December Challenge Day 1

[Link to the question](https://leetcode.com/explore/challenge/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3551/ "Day 1")

Solution to the question

```py
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if root is None:
            return 0
        return 1+ max(self.maxDepth(root.left), self.maxDepth(root.right))
```