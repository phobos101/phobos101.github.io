---
layout: post
section-type: post
title: Can you handle the truth?
excerpt: Boolean logic is used to determine if something is true or false. This is a core concept and can be used to make some really cool code!
---

### Truthy and Falsey
In computer science things tend to follow binary patterns. 1 or 0, on or off, true or false.
Pretty much every variable, function or value is going to be either true or false. When we evaluate
these expressions, we say they are either truthy or falsey. Truthy things are **true** and falsey things are **false**.

In JavaScript the following are examples of **some** truthy values:

* 1
* A string
* An empty object
* true

An here are **all** the things that are falsey:

* 0
* false
* null
* undefined
* An empty string
* NaN (not a number)

As you may have gathered, everything is truthy unless it is one of the falsey things listed above.

#### Conditional Statements
Knowing what evaluates to true, and what evaluates to false is all well and good, but what good does it serve? Well, it allows us to control the flow of the program execution by writing **conditional** statements. This means that if something is truthy, we do one thing, and if it is falsey we do another.

<pre><code data-trim class="javascript">
var a = true;

if (a === true) {
  doThis();
} else {
  doThat();
}
</code></pre>

In this block of code, we only execute the doThis function **if** the variable a is equal to true. In this situation it is easy to see that a does indeed evaluate to truthy, and so it is executed. If a was set to false, then the else part would have been executed instead, and the doThat function would have been called instead.

Let's look at something a bit more complex:
<pre><code data-trim class="javascript">
var number = prompt('Please enter a number');

if (number !== typeof(number)) {
  alert('You did not enter a number!');
} else if (number > 0) {
  alert('You entered a positive number');
} else if (number < 0) {
  alert('You entered a negative number');
} else {
  alert('You entered 0');
}
</code></pre>

Now what happens, is that the user types in something. If they do not (!==) enter a number, then we tell them they did not enter a number and the program ends. The conditions are read top down and will stop when the first condition is truthy. Therefore if we enter the number <i>-10</i> then it will be falsey for the first condition, falsey for the second condition but truth for the third condition (-10 < 0). This says, <i>is -10 less than 0?</i> if it **is** less than 0 then it is true. Therefore that third condition basically becomes else if (true). Because of this we alert them it is a negative number and the program ends. In other words, once a condition matches, the program does **not** continue to evaluate subsequent conditions.

That final else, is only executed if all previous conditions are falsey, and it always evaluates to true when read.

#### Logic Gates
Logic gates are a fancy way of telling us if an expression is truthy or falsey when there is more than one condition in that expression. If I said, 'Is five higher than ten?' this is **falsey**, but if I said, 'Is five higher than ten, *or* one' then this is **truthy**.

##### AND
The table below shows the AND logic gate. 1 = **true**, 0 = **false**:
| A | B | C |
|:-:|---|---|
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 0 | 0 | 0 |

true AND true = true
true AND false = false
false AND true = false
false AND false = false

Both sides must be true to evaluate to truthy.

<pre><code data-trim class="javascript">
if (1 < 2 && 2 < 3) {
  // this is true and will be executed
}

if (1 < 2 && 2 > 3) {
  // this is false because only one side is true
  // this code block will be ignored
}
</code></pre>

##### OR
The table below shows the OR logic gate. 1 = **true**, 0 = **false**:
| A | B | C |
|:-:|---|---|
| 1 | 1 | 1 |
| 1 | 0 | 1 |
| 0 | 1 | 1 |
| 0 | 0 | 0 |

true AND true = true
true AND false = true
false AND true = true
false AND false = false

Either side can be true to evaluate to truthy.

##### NOT
The not logic gate simply converts a truthy value to falsey and vise versa. E.g not true is equal to false.
Similarly *not 10 > 5* is equal to false, because 10 > 5 is true, but then put through the not logic to make it false.

#### Advanced code using boolean logic
As we saw earlier, we can use conditional *if* statements to direct the flow of our program. There is also a special bit of code called a **ternary** we can use to act upon if something is either truthy or falsey. As such, this code is not useful if there are many conditions that require *else if* statements.

Another cool thing that you can do is evaluate whether anything is true or false using the **double bang**.

##### Ternary Statements
A ternary is, as the name implies, made up of three parts. The condition, what to do if true and what to do if false. Let's take a look:

<pre><code data-trim class="javascript">
// How a ternary is structured
condition ? true : false

// If statement
if (condition === true) {
  doThis();
} else {
  doThat();
};

// The same as above in a ternary
condition === true ? doThis() : doThat();
</code></pre>

The ternary starts with the expression and is followed by a question mark (?), if true the first thing is executed, if it's not true then it skips to the colon (:) and executes that code instead!

###### Double bang
You can see if a variable is true or false by using the double bang (!!). For instance if we wrote *!!something* it would return true or false after evaluating the something variable:

<pre><code data-trim class="javascript">
var somethingTrue = true;

console.log(!!somethingTrue);
</code></pre>

The above code will print *true* to the console! You can use this in your code to direct the flow of your program also.
