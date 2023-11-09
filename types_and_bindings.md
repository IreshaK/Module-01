# Types and Bindings #

Types and bindings are some of the most fundamental building blocks of JS; in this topic you will learn how to bind data to identifiers, as well as what different types of data you may encounter working in JS. 

## Required Preparation ##

  * A working Node.js installation


## Resources ##

  *   [Chapter 1 of Eloquent Javascript](https://eloquentjavascript.net/01_values.html)
  *   [Types and Declarations Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_Types)
  *   [Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)

## Practice Exercises ##

 * 
  
## Knowledge and Skills Checklist ##

  * Understand the types used in JS
  * Bind idenitifers to values in JS
  * Perform foundational arithmetic in JS
  * Use the Node REPL

## Types ##

Types are used to lump similarly structured values together so programs become easier to predict and reason about. Some examples of different values are keeping a count of something (how many seats are there in a stadium), recording the truth of a statement (15 is divisible by 5), a piece of text ("Do not ask for whom the tollway belle's, the tollway belle's for thee" - maybe the best pun in history, by Peter Applebome), or perhaps a number with a decimal (Feigenbaum's first constant 4.669). 

Types help us because we know we could double a number, or convert a chunk of text to upper-case, but we couldn't convert a number to upper-case, and we couldn't divide a chunk of text by pi. 

### Booleans  ###

> "It from bit" - Prof. John Wheeler

A boolean value is either true ('on', 1) or false ('off', 0), it is the most simple of the data types, and also forms the fundamental machinery of the hardware of computers. Every value you've ever seen on a computer, the graphics in a game, a video on your phone, text file, anything; ultimately came down to a series of 1s and 0s, also known as 'bits' configured in the right arrangements.

### Numbers ###

Numbers in JS don't have the same complexity of some other programming languages, which differentiate between whole numbers (integers) and decimal numbers (floating points); all numbers in JS are very precise floating point numbers that are capable of being exact whole numbers. 

It's unnecessa to explain the benefit of the design in JS, but suffice to say that any number can perform all of the expected arithemetic functions with any other number, and you don't need to worry about the implementation details of how JS accomplishes this so well. This means you can count the number of seats in a stadium (let's say 1750) and then divide this by pi (let's approximate 3.14159) and JS would seamlessly return the result (~557.043); this is not the case with other programming languages which would object to the comparison of whole numbers and floating point numbers. 

### Strings ###

Strings are the data type that is used to hold text, but it's more than just the alphabet, a string can hold punctuation, it can encode emojis, or include special text-like instructions such as tab or carriage returns (starting a new line). 

### Experimenting in the REPL ###

Node.js can be used to run a JS program, but it can also be used to interact with one as you write it; to do this, call the 'node' program from the command line without any other arguments. This opens a REPL session, REPL stands for read-evaluate-print-loop. When you type JS code and hit enter in a REPL session it will read your code, evaluate your code, and print the result to your screen; this happens repeatedly in a loop. 

Below are some expressions you could evaluate to get started working in the REPL, don't limit yourself to these, they are just a starting point. Get used to experimenting with new tools and concepts by opening up a REPL or running some code; there's no better way to learn programming. It will always make more sense once you've experienced and seen it for yourself, and don't forget; repetition is the key to success.

```
1 + 1
5 / 2
(3 + 2) * (1 + (6 / 2))
"Hello" + ", world!"
```

## Binding values to identifiers ##

Programming would be very difficult if we had to constantly rebuild expressions and values in our source code every time we want to use them; that's why we use identifiers, to attach meaningful name-tags (in JS, these are called identifiers) to information so that our code can be reasoned about. 

There are different ways of defining the relationship between an identifier and the value or expression it identifies. Assigning values to identifiers uses the same structure of `relationship identifier = value`, this syntax will become second nature to you quickly, the below examples will help demonstrate uses, and with a bit of experimentation in the REPL, you will become comfortable with this. 

### Const ###

The simplest relationship to understand is const(ant), which is used to declare that an identifier for some value will not change. Pi is a great example of this, you may be writing code that needs to work with circles to a certain level of precision, consider which of the following two examples is easier to reason about.

```javascript
const pi = 3.14159
const radius = 5
const circumference = 2 * pi * radius
circumference
```

```javascript
3.14159 * 2 * 5
```

By providing meaningful names to our data, we have better stated our intent to all future users of this code base, and made it easier for a human to understand; the computer will return the same results in either case. Programming is about more than just getting the correct value from a program, it's also about crafting source code that makes your intent as clear as possible to future maintainers and users of the code. 

The fact you used const also further encodes intent, it lets future developers know these are not variable values, they are constants. To see how JS protects us from making mistakes, see what happens when you try to change the value of a constant. Open your REPL and enter the below. 

```javascript
const eulersNumber = 2.72 // Low precision
const eulersNumber = 2.71828 // Updated to have better precision
eulersNumber
```

Those // indicate comments in the code, this means it will not be read by the REPL, it will simply ignore whatever comes after //; comments are extremely useful for explaining your intent in source code to future users and maintainers. Learning to comment your code meaningfully is a subtle but powerful differentiating factor between producing usable code, and producing fantastic code. 

### Let ###

Let is used to declare a relationship between a value and an identifier that can be altered. Consider the previous example modified slightly.

```javascript
let feigenbaumsAlpha = 2.5 // Low precision instance of Feigenbaum's alpha constant
feigenbaumsAlpha = 2.50291 // Updated to have higher precision
feigenbaumsAlpha
```

Unlike const, let allows the value identified change; you don't declare the identifier a second time by reusing 'let' as this would generate an error - the identifier feigenbaumsAlpha already exists. You are not declaring the identifier to the program again when you reassign the value, you are informing the program the value that identifier points to has changed. 

Changing the value an identifier points to is also known as mutating state, so if you see something refered to as 'immutable' that means it is like a constant in that it cannot be changed, and if something is 'mutable' then the value it identifies is able to be changed. 

### Var ###

var(iable) has a similar relationship to let, in that it allows the value to be altered after declaration; there is a more subtle difference regarding scope, which you will learn about in future lessons. For now, it is sufficient to know that var exists, it creates identifiers which are mutable; and you will not have to use it except when reading legacy code. If you need a mutable identifier, use 'let'. 
