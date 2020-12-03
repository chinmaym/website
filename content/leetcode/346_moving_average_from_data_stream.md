---
title: "346_moving_average_from_data_stream"
date: 2020-12-02T23:19:39-08:00
draft: false
tags: ['Leetcode', 'Google']
categories: ['Leetcode']
---
# Leetcode 346

```
Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

Example:
MovingAverage m = new MovingAverage(3);
m.next(1) = 1
m.next(10) = (1 + 10) / 2
m.next(3) = (1 + 10 + 3) / 3
m.next(5) = (10 + 3 + 5) / 3

```
My solution - 
```py
class MovingAverage:

    def __init__(self, size: int):
        """
        Initialize your data structure here.
        """
        self.size = size
        self.window = []
        self.sum = 0

    def next(self, val: int) -> float:
        if len(self.window) == self.size:
            pop_val = self.window.pop(0)
            self.sum -= pop_val
        self.window.append(val)
        self.sum += val
        return self.sum/len(self.window)
```
