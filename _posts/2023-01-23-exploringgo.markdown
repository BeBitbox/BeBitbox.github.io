---
layout: post
title:  "Book: Learning Go"
date:   2023-01-23 09:47:57 +0100
permalink: /learning-go/
---

Learning Go is a guide on how to start programming Go with a lot of practical examples.
The book pays a lot of attention to other programming languages like Java or C, so it helps if you already have that experience. 
You can find all the information on their [site]

![Book Cover](/images/learninggo.jpeg)

# Interesting facts about Golang

* This language learned a lot from previous languages:
  * No more discussions about style: it's written in the language tools itself, which is surprisingly liberating
  * No unnecessary semi-colons, braces,.. It's a clean minimalistic language
  * Go uses pointers! This is surprising because it is not that popular. It however gives a lot of help with immutability by default.
* Go outperforms Java. It has no virtual machine, but just focuses on building binaries that work on specific platforms.
* Go is not Object-Oriented (no inheritance, overloading,..) but it has the concept op implicit interfaces. It makes decoupling much better, because the client does not even need to know of the interface it is implementing.

[site]: https://www.oreilly.com/library/view/learning-go/9781492077206/
