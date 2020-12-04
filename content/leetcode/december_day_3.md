---
title: "December_day_3"
date: 2020-12-03T23:43:57-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---

# Leetcode December Challege Day 3
[Link to the question](https://leetcode.com/explore/featured/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3553/ "Day 3")

Solution to the question

```py
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def increasingBST(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root == None:
            return None
        left = self.increasingBST(root.left)
        if left == None:
            head = root
        else:
            head = left
            while left and left.right != None:
                left = left.right
            left.right = root
        root.left = None
        right = self.increasingBST(root.right)
        root.right = right
        return head
```