---
title: "1408_string_matching_in_an_array"
date: 2020-04-15T02:03:50-07:00
draft: false
tags: ['Leetcode']
categories: ['Leetcode']
---
# Leetcode 1408
[Link to the question] (https://leetcode.com/problems/string-matching-in-an-array/ "String Matching in an Array")
```
Given an array of string words. Return all strings in words which is substring of another word in any order. 

String words[i] is substring of words[j], if can be obtained removing some characters to left and/or right side of words[j].

 

Example 1:

Input: words = ["mass","as","hero","superhero"]
Output: ["as","hero"]
Explanation: "as" is substring of "mass" and "hero" is substring of "superhero".
["hero","as"] is also a valid answer.

Example 2:

Input: words = ["leetcode","et","code"]
Output: ["et","code"]
Explanation: "et", "code" are substring of "leetcode".

Example 3:

Input: words = ["blue","green","bu"]
Output: []

```
My solution is not a good one. It's just that this solution stuck in my head and i wanted to also learn how to implement trie in GO. But there are solutions better than this.
```go
const (
	ALPHABET_SIZE = 26
)

type trieNode struct {
	children  [ALPHABET_SIZE]*trieNode
	isWordEnd bool
}

type trie struct {
	root *trieNode
}

func initTrie() *trie {
	return &trie{
		root: &trieNode{},
	}
}

func (t *trie) insert(word string) {
	wordLength := len(word)
	current := t.root
	for i := 0; i < wordLength; i++ {
		index := word[i] - 'a'
		if current.children[index] == nil {
			current.children[index] = &trieNode{}
		}
		current = current.children[index]
	}
	current.isWordEnd = true
}

func (t *trie) findSub(word string) bool {
	wordLength := len(word)
	current := t.root
	for i := 0; i < wordLength; i++ {
		index := word[i] - 'a'
		if current.children[index] == nil {
			return false
		}
		current = current.children[index]
	}
	return true
}

type byLength []string

func (s byLength) Len() int {
	return len(s)
}
func (s byLength) Swap(i, j int) {
	s[i], s[j] = s[j], s[i]
}

func (s byLength) Less(i, j int) bool {
	return len(s[i]) < len(s[j])
}

func stringMatching(words []string) []string {
    ret := make([]string, 0)
	sort.Sort(byLength(words))
	for i := len(words) - 1; i >= 0; i-- {
		trie := initTrie()
		for j := len(words) - 1; j >= 0; j-- {
			if j != i {
				fmt.Print(words[j], " ")
				word := words[j]
				for len(word) > 0 {
					trie.insert(word)
					word = word[1:]
				}
			}
		}
		fmt.Println()
		if trie.findSub(words[i]) {
			ret = append(ret, words[i])
		}
	}
	return ret
}
```