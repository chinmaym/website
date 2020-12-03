---
title: "1021_remove_outermost_parentheses"
date: 2020-12-02T23:16:16-08:00
draft: false
tags: ['Leetcode', 'Google']
categories: ['Leetcode']
---
# Leetcode 1021
[Link to the question](https://leetcode.com/problems/remove-outermost-parentheses/ "Remove outermost parentheses")
```
A valid parentheses string is either empty (""), "(" + A + ")", or A + B, where A and B are valid parentheses strings, and + represents string concatenation.  For example, "", "()", "(())()", and "(()(()))" are all valid parentheses strings.

A valid parentheses string S is primitive if it is nonempty, and there does not exist a way to split it into S = A+B, with A and B nonempty valid parentheses strings.

Given a valid parentheses string S, consider its primitive decomposition: S = P_1 + P_2 + ... + P_k, where P_i are primitive valid parentheses strings.

Return S after removing the outermost parentheses of every primitive string in the primitive decomposition of S.

Example 1:
Input: "(()())(())"
Output: "()()()"
Explanation: 
The input string is "(()())(())", with primitive decomposition "(()())" + "(())".
After removing outer parentheses of each part, this is "()()" + "()" = "()()()".

Example 2:
Input: "(()())(())(()(()))"
Output: "()()()()(())"
Explanation: 
The input string is "(()())(())(()(()))", with primitive decomposition "(()())" + "(())" + "(()(()))".
After removing outer parentheses of each part, this is "()()" + "()" + "()(())" = "()()()()(())".

Example 3:
Input: "()()"
Output: ""
Explanation: 
The input string is "()()", with primitive decomposition "()" + "()".
After removing outer parentheses of each part, this is "" + "" = "".
 ```
 My solution - 
 ```py
 class Solution:
    def removeOuterParentheses(self, s: str) -> str:
        ret = ''
        count = 0
        begin = 0
        for i in range(len(s)):
            if s[i] == '(':
                count += 1
            if s[i] == ')':
                count -= 1
            if count == 0:
                ret += s[begin+1: i]
                begin = i + 1
        return ret
 ```