---
title: "December_day_2"
date: 2020-12-02T23:10:08-08:00
draft: false
tags: ['Leetcode', 'December Challenge']
categories: ['Leetcode']
---

# Leetcode December Challenge Day 2
[Link to the question](https://leetcode.com/explore/featured/card/december-leetcoding-challenge/569/week-1-december-1st-december-7th/3552/ "Day 2")

Solution to the question

```py
import random
class Solution:

    def __init__(self, head: ListNode):
        """
        @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node.
        """
        self.head = head
        self.length = None

    def getRandom(self) -> int:
        """
        Returns a random node's value.
        """
        head = self.head
        if self.length == None:
            self.length = 0
            while head != None:
                self.length += 1
                head = head.next
        ind = random.randint(1, self.length)
        head = self.head
        while ind > 0:
            ind -= 1
            if ind == 0:
                return head.val
            head = head.next
```