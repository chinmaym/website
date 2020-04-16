+++ 
draft = false
date = 2020-04-16T14:51:36-07:00
title = "Leetcode 904"
description = "Leetcode 904 Intuitive solution"
slug = "" 
tags = ['Leetcode', 'Python']
categories = ['Leetcode']
externalLink = ""
series = ['Leetcode']
+++
# Leetcode 904 Solution

[Link to the question] (https://leetcode.com/problems/fruit-into-baskets "Leetcode 904")

```
In a row of trees, the i-th tree produces fruit with type tree[i].

You start at any tree of your choice, then repeatedly perform the following steps:

Add one piece of fruit from this tree to your baskets.  If you cannot, stop.
Move to the next tree to the right of the current tree.  If there is no tree to the right, stop.
Note that you do not have any choice after the initial choice of starting tree: you must perform step 1, then step 2, then back to step 1, then step 2, and so on until you stop.

You have two baskets, and each basket can carry any quantity of fruit, but you want each basket to only carry one type of fruit each.

What is the total amount of fruit you can collect with this procedure?

Example 1:

Input: [1,2,1]
Output: 3
Explanation: We can collect [1,2,1].
```
This is my solution to the Fruits in a basket question. I have tried to keep the solution as intuitive as possible.

```py
def getMaxFruits(treeList):
    baskets = [0, 0]
    maxSum = 0
    type = [-1, -1]
    lastPos = 0
    for ind,i in enumerate(treeList):
        if type[0] == i or type[0] == -1:
            baskets[0] += 1
            type[0] = i
        elif type[1] == i or type[1] == -1:
            baskets[1] += 1
            type[1] = i
            type[0], type[1] = type[1], type[0]
            baskets[0], baskets[1] = baskets[1], baskets[0]
            lastPos = ind
        else:
            if baskets[0] + baskets[1] > maxSum:
                maxSum = baskets[0] + baskets[1]
            type = [i, type[0]]
            baskets = [1, ind - lastPos]
            lastPos = ind
    if baskets[0] + baskets[1] > maxSum:
        maxSum = baskets[0] + baskets[1]
    return maxSum
```