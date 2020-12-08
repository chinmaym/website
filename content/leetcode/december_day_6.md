---
title: "December_day_6"
date: 2020-12-08T00:16:11-08:00
draft: false
tags: ['Leetcode', 'December Challenge', 'Trees']
categories: ['Leetcode']
---

# Leetcode December Challenge Day 6
[Link to the question](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/ "Day 6")

Solution to the question

```py
"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if root == None:
            return None        
        self.connect(root.left)
        self.connect(root.right)
        self.connectInner(root.left, root.right)
        return root
        
        
    def connectInner(self, leftChild, rightChild):
        if leftChild != None and rightChild != None:
            if leftChild.next == None:
                leftChild.next = rightChild
            self.connectInner(leftChild.right, rightChild.left)
            self.connectInner(leftChild.right, rightChild.right)
            self.connectInner(leftChild.left, rightChild.left)
            self.connectInner(leftChild.left, rightChild.right)
```

Best solution to the question 
```py
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        temp = root
        while root:
            cur = dummy = Node(0)
            while root:
                if root.left:
                    cur.next = root.left
                    cur = cur.next
                if root.right:
                    cur.next = root.right
                    cur = cur.next
                root = root.next
            root = dummy.next
        return temp
```