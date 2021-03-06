---
layout: post
title:  "JavaScript for Java developers"
date:   2020-04-24 20:47:57 +0100
permalink: /javascript-for-java-developers/
---

# Why ?
JavaScript is one of the most popular programming languages according to [StackOverflow](https://insights.stackoverflow.com/survey/2019#technology) and its possibilities are only growing. 
You might think of JavaScript as just running inside a browser to support websites, but with Node.js it also became a popular language for backend systems and automation tools. 
This article will show you some major improvements and features that might even be considered to implement in Java.

# Releases and Backwards compatibility
Java has now made the switch to a release train that publishes every 6 months a new major release, while still trying to maintain backwards compatibility. 
It’s a difficult process that leads to a lot of deprecation in the API and a difficult maintainable code base.

JavaScript on the other hand has a specification of the language which is being updated every year, called ECMAScript (or ES), where ES6 (specification of 2015) is now the industry standard. 
It introduces some nice features you will find further down in the article. 
Now the interesting part is that you can use the newest features of JavaScript that will even run on old browsers like Internet Explorer. 
There are projects like Babel that will compile your JavaScript code to plain old JavaScript code. 
This is something that should be possible in Java with the target-option:

> javac -source 11 -target 1.8 App.java

It however fails because of bytecode changes in the JVM’s. 
For example: writing Java 8 code for JVM 7 doesn’t work, like writing Java 11 code for JVM 10,…

# Dynamic typing
Java is a static-typed language, so the compiler decides the type of your variables. 
In a dynamically-typed language as JavaScript however the interpreter assigns variables a type at runtime. 
This means that code like here below is allowed, but this is the definition of bad programming:

{% highlight javascript %}
let a = 42;
a = ['now an array'];
{% endhighlight %}

So in general it is better to use static-typing and in JavaScript this is possible with an extension called TypeScript. 
Dynamically typing however offers a lot of flexibility and power, certainly with Objects in mind. 
Imagine you have a class with a teacher and a variable number of students. 
In Java we need to represent it as a collection, so an Object inside our Object.

{% highlight java %}
public class Classroom {
    public String teacher = "Johny";
    public List<String> students = List.of("Lisa", "Mark", "Dennie");
}
{% endhighlight %}

In JavaScript your Objects can be dynamically defined, basically like a Map. 
This works amazingly well with document storage databases like Mongo:

{% highlight javascript %}
const classroom = { teacher: 'Johnny' };  //Creating the Object
const studentNames = ['Mark', 'Lisa', 'Dennie'];
for (let i = 0; i < studentnames.length; i++) {
    classroom[`student${i}`] = studentnames[i]
}

/**  The object classroom is now this:
{
    teacher: 'Johnny',
    student0: 'Mark',
    student1: 'Lisa',
    student2: 'Dennie'    
}
*/
{% endhighlight %}

# Asynchronous calls
One of the biggest advantages of JavaScript is the easy way to do asynchronous calls or concurrent calls. 
Where you would use Future, ExecutorService and Runnables, Javascript uses only Promises. 
A Promise is either still running or is resolved and has a result or exception. 
A small demonstration of the possibilities:

{% highlight javascript %}
async foo() {  
    promiseA();  // promiseA() will run asynchronously and blocks nothing
    promiseB()   // async, but when promiseB fullfilled, run promiseC(),..
        .then(result -> promiseC(result))
        .then(result -> doSomething(result));
    await promiseD();  // block the thread till promiseD is resolved
    Promise.all(promiseE(), promiseF()); // block thread till both promises done
}
{% endhighlight %}

# Special JavaScript operators
JavaScript offers some extremely handy operators that makes writing code much easier and avoids boilerplate code.

#### Thruthy
Instead of always doing null-checks or size checks, JavaScript allows the possibility to just put an Object inside a conditional, where in Java we only accept Booleans

{% highlight javascript %}
// following is all true using thruty evaluation
if (true)
if ({})
if ([])
if (42)
if ("foo")

// following is all false
if (false)
if (null)
if (undefined)
if (0)
if ("")
{% endhighlight %}

#### Template literals
When you want to write a String with some variable parameters inside you will have to use concatenation. 
JavaScript introduced the template literals what works with dynamic placeholders between brackets and backticks instead of standard quotes like this:

{% highlight javascript %}
const name = 'Mark';
const text1 = 'Oww hi ' + name + '.';
const text2 = `Oww hi ${name}.`
{% endhighlight %}

#### Spread operator
The spread operator allows an iterable to expand in places where 0+ arguments are expected.

{% highlight javascript %}
// spread operator doing the concat job
let arr = [1];
let arr2 = [4, 5];

arr = [...arr,...arr2]; // [1, 4, 5]
{% endhighlight %}

#### Destructuring
In a lot of languages the code of just the variable assignments is typically very long: mapping attributes from one object to another. 
JavaScript however introduced destructuring-notation that will reduce the amount of code and logic.

{% highlight javascript %}
function printName(user) {
    const id = user.id;
    const name = user.name;
    console.log(`id ${id} with name ${name}`};
}

function printNameWithDestructuring({id, name}) {
    console.log(`id ${id} with name ${name}`};
}

const user = {
    id: 42,
    name: 'Tommy'
};

printName(user);
printNameWithDestructuring(user); // Same result
{% endhighlight %}

# Conclusion
JavaScript is no longer a language that should be mocked, but instead one that can be admired for the way how they make the life of developers easy. 
Some concepts are definitely worth looking into as Java continues evolving.