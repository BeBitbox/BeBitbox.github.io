---
layout: post
title:  "Building a Second Brain"
date:   2023-02-25 10:28:57 +0100
permalink: /building-a-second-brain/
---

'Building a Second Brain' by Tiago Forte is a self-help book based on a series of blogs that have been bundled into a book and supplemented by some self-help courses.
While I wouldn't recommend the book or any of the author's work, I do find some of his ideas interesting.

![Book Cover](/images/building-a-second-brain.jpg)

## The ideas behind the book
The author begins with the idea of prosthetics, something that is unique to the human species.
We use clothing to keep us warm or cool, shoes to protect our feet, glasses to improve our sight. 
There are even internal prosthetics (implants) like tooth fillings, pacemakers that significantly improve our well-being.
You could even say that prosthetics differentiate us from animals.
So why don't we have a prosthetic that can improves our brains?

The solution to this problem, according to Forte, is note-taking: "Take notes everywhere, all the time, and organize them digitally".
Whenever you hear something interesting, learn something new, have a random thought or meet someone interesting: take a fast note.
Afterwards you can organize your notes in a structured way, using a tool like OneNote, Google Keep, Evernote, or similar.
By doing this consistently, you will have a custom knowledge base available to you at all the time, helping you find information quickly.

## My feedback
1. The idea of organized note-taking is nothing new, long before the digital era. I remember my grandmother having a folder with recipes, lists with distant family members and addresses, and so on.
2. Having a comprehensive note collection is not the same as having a second brain. The brain is much more than memory.
3. I would caution against storing your notes in a Big Tech tool! Consider the issues of privacy, vendor locking, shortcomings to export your data to other tools? Will the current note application you use still be available in 30 years?
4. As for Tiago Forte: he is self-help coach, who claims to have a technical background, but his only experience is working in an Apple store. He is monetizing a basic idea with courses and books.

## My "Second brain"
I've always loved the idea of having a solid knowledge base. 
My first attempt was to run my own local Wikipedia server on my NAS.
It was easy to add, search, and manage it, but it has some downsides: no mobile app, no easy export to other formats, written in PHP, the cost of running the server.

My current approach is to use a Git repository for all my notes.
Each note is written as a [Markdown]-file, which is essentially a text file with some formatting syntax.
For example, this entire website is written using only Markdown-files on [GitHub Pages].
The big benefit of this approach, is that I can easily search/modify/add these text files and organize them into folders.
Moreover, this technology will never become outdated or lost in the future, making it a future-proof option.
I check my files into a major Git provider like GitHub, which comes with its own apps.

## Examples of notes

### Purchases
Keeping track of when, where, and what I bought, helped me a lot in the past.
It took only one minute to find if something was still in warranty, or what brand something is in case I want to purchase again. 
I don't add too much details, since I can still refer back to the original invoices if needed. 
{% highlight markdown %}
| Purchase                  | Date       | Extra info                           |
|---------------------------|------------|--------------------------------------|
| Solar panel               | 28-06-2012 | Power:  4,51 kilowattpiek            |
| Wardrobe sleeping room    | 23-03-2021 | Brimnes 3 door black - Ikea - 149€   |
{% endhighlight %}

### People
My notes also contain details of people I have met before.
This is really useful for people who you don't see often and tend to forget the last thing they have mentioned to you.
{% highlight markdown %}
* Mark & Lisa (married 22 oct 2018, Churchstr. 7 in Kortrijk)
  * Dennie (01/01/2023)  
{% endhighlight %}

### Lists
I even started to add my TODO-lists or shopping lists into Git.
{% highlight markdown %}
[X] Write blog post
[ ] Complete the Advent-of-Code of 2022
{% endhighlight %}

### Other knowledge
Whenever I come across an interesting topic or suggestion, I make sure to add it to my list of information to process.
A few times each week, I set aside some time to review my notes and decide how to proceed.
I'll keep anything that I found particularly useful, organize it or create tasks for myself if more work is needed. 
By consistently processing and organizing the information I come across, I'm able to build a comprehensive knowledge base that helps me in all aspects of my life.

[Markdown]: https://www.markdownguide.org/
[GitHub Pages]: https://pages.github.com/