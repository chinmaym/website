+++ 
draft = false
date = 2020-04-16T10:06:30-07:00
title = "Trie Implementation in GoLang"
description = "Trie Implementation in GoLang"
slug = "" 
tags = ['Trie', 'Golang', 'GO']
categories = ['Data Structure']
externalLink = ""
series = ['Data Structure', 'GO']
+++
# Trie Implementation in GO


```GO
package main

import "fmt"

const (
	// ChildrenLength Length of the alphabets
	ChildrenLength = 26
)

type trieNode struct {
	children [ChildrenLength]*trieNode
	isEnd    bool
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
	current := t.root
	for _, val := range word {
		index := val - 'a'
		if current.children[index] == nil {
			current.children[index] = &trieNode{}
		}
		current = current.children[index]
	}
	current.isEnd = true
}

func (t *trie) find(word string) bool {
	current := t.root
	for _, val := range word {
		index := val - 'a'
		if current.children[index] == nil {
			return false
		}
		current = current.children[index]
	}
	if current.isEnd == true {
		return true
	}
	return false
}

func main() {
	trie := initTrie()
	trie.insert("test")
	trie.insert("trie")
	trie.insert("go")
	trie.insert("testing")
	fmt.Println("searching for word testing - ", trie.find("testing"))
	fmt.Println("searching for word test - ", trie.find("test"))
	fmt.Println("searching for word testi - ", trie.find("testi"))
	fmt.Println("searching for word go - ", trie.find("go"))
}
```
Output for the program - 
```
searching for word testing -  true
searching for word test -  true
searching for word testi -  false
searching for word go -  true
```