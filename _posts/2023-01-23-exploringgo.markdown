---
layout: post
title:  "Book: Learning Go"
date:   2023-01-23 09:47:57 +0100
permalink: /learning-go/
---

'Learning Go' by Jon Bodner is a comprehensive guide to learning the Go programming language.
It was first published on March 2021.
You can find all the information on their [site]

![Book Cover](/images/learninggo.jpeg)

# My personal opinion
The book should be designed for beginners and assumes no prior knowledge of programming.
I however find it quite advanced and dry, so I would not recommend you start reading it without prior programming experience. 
It covers the basics of Go, including syntax, data types, functions, and control structures, but also more advanced topics such as concurrency, networking, and error handling.

I kept with the basics and used Go to implement [advent-of-code 2015].
It seems that Go is especially useful for writing microservices and some fast basic scripts.
I don't know how it is to use the language in big software teams or how much support you can find. 

# Interesting facts about Golang

* Go is very recent with its first release in 2009.
* Go was designed to be platform-independent, with support for multiple operating systems and architectures.
* This language learned a lot from previous languages:
  * No more discussions about style: it's defined in the language tools itself, which is surprisingly liberating.
  * No unnecessary semi-colons, braces,.. It's a clean minimalistic language.
  * It allows functions to return multiple returns, which is a blessing compared to Java and can be very useful for exception handling
  * Built-in support for concurrency. 
  * Defer-code will be executed when a function ends, regardless of outcome.
* Go uses pointers! This is surprising because it is not that popular. It however gives a lot of help with immutability by default.
* Go outperforms Java. It has no virtual machine, but just focuses on building binaries that work on specific platforms.
* Go is not Object-Oriented (no inheritance, overloading,..) but it has the concept op implicit interfaces. It makes decoupling much better, because the client does not even need to know of the interface it is implementing.
* The test code is written next to your production code. Go also has an own test framework.

[site]: https://www.oreilly.com/library/view/learning-go/9781492077206/
[advent-of-code 2015]: https://github.com/BeBitbox/advent-of-code/tree/main/src/main/go/2015