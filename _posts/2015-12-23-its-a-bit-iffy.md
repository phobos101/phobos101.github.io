---
layout: post
section-type: post
title: It's a bit iffy
excerpt: A huge topic for a beginner coder is the topic of functions. This blog post will go over what a function is, how to call them and how to create an IIFE.
---

### It's a bit iffy...

A huge topic for a beginner coders is the topic of functions. Some common questions I have seen regarding functions include:

* Why are they needed?
* I've written a function but nothing is happening!
* What is the difference between a function and a method?

I will aim to cover all these and more as we talk though what a function is and why they are so useful.

#### Jump around!

Every time I think of the movie Ms.Doubtfire, I (for some reason) think of the hit 'Jump Around' by 'House of Pain'.

This is what functions allow us to do, jump around! If you a re a new coder, then you have most likely written programs that start at the top, execute a line, and then go down to the next line until then end. Functions allow you to write code that won't be executed until you specifically want it to giving you extra power over how the program runs. Let's take a look at the example below.

In this first program, we add two numbers, and then we subtract the same two numbers.
<pre><code data-trim class="javascript">
var a = 10;
var b = 5;
var addResult = a + b;
var subtractResult = a - b;

console.log(result);
console.log(subtractResult);
</code></pre>

This will result in two numbers being printed to our console log, 15 and 5. Pretty simple, but what if you wanted to add the numbers multiple times, maybe when something specific happens? Okay, we can do this:

<pre><code data-trim class="javascript">
var a = 10;
var b = 5;

if (something_happens) {
  var addResult = a + b;
};

if (something_happens_again) {
  var addResult = a + b;
};
</code></pre>

Hmmm, okay this will work, but it's sloppy and you have no write the same code every time some condition occurs. Another thing, maybe you want to perform a calculation on different numbers depending on the condition. Let's remake this into a function and explain the benefits.

<pre><code data-trim class="javascript">
function calculate(a, b, operator) {
  if (operator == 'add') var result = a + b;
  if (operator == 'subtract') var result = a - b;
  console.log(result);
};

calculate(10, 20, 'add');
</code></pre>

The above function has the following benefits:

* We can call this function anytime we want or when some condition is met.
* If we need to alter the code, we only alter it in ONE place (the function) as opposed to finding multiple lines dotted around our program to alter.
* We can now use a single line to calculate either adding or subtracting any two numbers.

### Call story bro

It's also really important to understand that just because we have **written** the function, it does not mean that it will run. You must **call** the function in order to run it. To call the function, you simply write the name of the function and pass in any arguments or parameters. If the function takes no arguments then just don't pass any in. :smile:

<pre><code data-trim class="javascript">
calculate(10, 20, 'add');
</code></pre>

In this case, we are passing in three arguments: 10, 20 and 'add'. The first two are numbers, and the third is a string. If the calculate function took no arguments, we would call it with:
<pre><code data-trim class="javascript">
calculate();
</code></pre>

In many programs (including the example in the previous section) you will see functions that are immediately followed by a call for that function. This is not a bad thing, as it means the function is defined and run, and can be called again in the future at any time.

### Methods vs Functions

A method is simply a function that is written inside an **object**. You can therefore call an objects function (method) using something called dot notation, and chances are you have done this before! Check the below example:

<pre><code data-trim class="javascript">
var person = {
  // New person object
  firstName: 'Robert',
  lastName: 'Wilson',
  fullName: function() {
    return this.firstName + ' ' + this.lastName;
  };
};

var name = person.fullName()
</code></pre>

As you can see, the 'fullName' property is just a normal function! But becuase it is written in an object it is known as a method. When we get the value of 'name' it calls the function using dot notation and will get the value 'Robert Wilson'.

### What an IIFE is and is not

There is an elegant way to invoke a function immediately after creation, and we refer to these as IIFEs or Immediately Invoked Function Expressions. The way to write an IIFE is to pre-pend the function with an open parenthesis, and at the end of the function, close the parenthesis, followed by calling the function on the same line.

<pre><code data-trim class="javascript">
(function(a, b) {
  console.log(a + b);
})(10, 20);
</code></pre>

This IIFE will print 30 to the console log. Just like a normal function it takes 0 or more arguments, in this case two. It performs our calculation and the function ends. Directly after the end of the function we call it by opening our parentheses and passing in the values for a and b respectively.

You may hear these referred to as self-executing or self-invoking but this is not the case as we, the programmer, are calling it after creation. Self-executing is a now deprecated term and we use IIFE as this more accurately describes it.
