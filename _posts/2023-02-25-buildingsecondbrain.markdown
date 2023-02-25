---
layout: post
title:  "Building a Second Brain"
date:   2023-02-25 10:28:57 +0100
permalink: /building-a-second-brain/
---

'Building a Second Brain' by Tiago Forte is a self-help book. 
It is based on a serie of blogs, bundled into a book, followed up by some self-help courses.
I don't recommend the book or the work of the author, but some of his ideas are interesting.

![Book Cover](/images/building-a-second-brain.jpg)

# The ideas behind the book
The author starts with the idea of prosthetics, which is something unique for the human species.
We use cloths to keep us warm or cold, shoes to protect our feet and give us more balance, glasses to improve our sight,.. 
There are even internal prosthetics (implants) like tooth fillings, pace makers,.. that improve our well-being significantly.
You can even say it differents us from animals.
So why don't we have a prosthetic that improves our brain?

The solution for the problem is note-taking: "Take notes everywhere, all the time and organize them digitally"
When you hear something interesting, learn something, have a random idea or meet something interesting: take a fast note.
Afterwards organize your notes in a structured way, in a tool like OneNote, Google Keep, Evernote,..
If you keep doing this, you will have a custom ledge at all the time available.
It will help you find information fast and help you with all daily tasks.

# My feedback
1. The idea of organized note-taking is nothing new. My grandmother had a folder with recipes, lists with distant family names and addresses,… Before the digital era there were ways to do this too.
2. Having a comprehensive note-collection is not having a second brain. A brain is much more than memory.
3. Don't put the note-collection in a BigTech tool! First of all privacy, vendor locking, possibilities to export your data? Will OneNote still exist in 30 years? Will Microsoft still exist? What is Microsoft suddenly asks money for the tool?
4. The persona Tiago Forte: self-help guru, claims to be technical, but has only experience of working in an Apple store,... He is monetizing a basic idea with courses and books.

# My "Second brain"
I always loved the idea of having a solid knowledge base. 
My first attempt was my own local Wikipedia-server that I ran locally on my NAS.
It is easy to add, search and manage it, however it has some downsides: no mobile app, no easy export to other formats, PHP, the cost,..

My current attempt is a GIT-repository with all my notes.
A note is written as a [Markdown]-file, so it is basically a text file with some syntax.
For example: this entire website is written as Markdown-files.
The big benefit of it, is that I can search easily in those files and I can organize them in folders.
This technology will never be deprecated or lost in the future, so for me it is the most future-proof option.
I check my files into a major Git-provider like GitHub, that comes with his own apps.

I add everything in my notes

## Purchases
Handy to know when/what/where you bought something. 
Helped me a lot to know if something still has guarantee, what brand something is, and so one. 
I don't add too much details, I can still fallback on the original invoices if needed. 
{% highlight markdown %}
| Purchase                  | Date       | Extra info                           |
|---------------------------|------------|--------------------------------------|
| Solar panel               | 28-06-2012 | Power:  4,51 kilowattpiek            |
| Wardrobe sleeping room    | 23-03-2021 | Brimnes 3 door black - Ikea - 149€   |
{% endhighlight %}

## People
You might forget some details of all your friends, family,...
I don't want to appear rude, so it's good to fallback on their basics
{% highlight markdown %}
* Mark & Lisa (married 22 oct 2018, Churchstr. 7 in Kortrijk)
  * Dennie (01/01/2023)  
{% endhighlight %}

## Lists
I even started to add my TODO-lists or shopping lists into GIT.
{% highlight markdown %}
[X] Write blog post
[ ] Send Christmas cards
{% endhighlight %}

## Things I learned: all else
Everytime I hear an interesting topic or suggestion, I add it on my information to process. 
A couple of times in the week, I will go through it.
Keep the things I found useful, make tasks if needed or simply add them to my previous note.

[Markdown]: https://www.markdownguide.org/
