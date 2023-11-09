# Collections #

Collections are how related data can be kept together in a way that is efficient for access, mutation, and insertion. The study of differently structured collections of data as data structures is an area of significant investigation in computer science; thankfully, JS comes with simple and general collections that are suitable for a wide range of solutions. 

## Required Preparation ##

  * A working Node.js installation
  * An Edabit account

## Resources ##

  * [Chapter 4 of Eloquent JavaScript](https://eloquentjavascript.net/04_data.html)
  * [Types and Structures Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
  * [Arrays Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
  * [Object Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)

## Practice Exercises ##

  * 

## Knowledge and Skills Checklist ##

  * Create, access, and modify collections in JS
  * Understand the properties of collections in JS
  * Select context appropriate collections based on properties

## Purpose of collections ##

A single identifier can be used to represent multiple data that is somehow related; perhaps the data describe different attributes of a single object (a real estate listing for a house has the land size in hectares, the home size in square meters, and the price in dollars) or a collection of related values (the account balances of our users). You will use collections to make interacting with all these related data easier to reason about, and to improve how well your code displays your intent. 

## Properties of different collections ##

The above examples of a real estate listing, and a child's height over time suit different collections; you will learn to evaluate the suitability of a collection's properties to the nature of the things the collection is representing. It is possible to achieve the same output from a program using a variety of collections, so the right choice is often the one that most clearly indicates your intent; it is a subtle skill you will develop over time and practice. 

### Access ###

The way you access the information in a collection is crucial to writing code that expresses your intent as clearly as possible. It makes sense to think of certain information as being a property of something, for example boxer's attributes such as height, weight, age, and reach are read out before a match; these attributes are a collection of data for each athlete. Other information is more easily thought of as a sequence of numbers, for example, a stock price during a day of trading. You would want to access these collections differently according to the nature of the data. 

#### Membership ####

The simplest collection access is membership; this means the collection is only able to answer true or false when you ask it the question 'do you hold the value x?'. For example, if you have a collection of all the even numbers from 0 to 100, and you ask 'is 51 a member of you?' the answer is false, because it is an odd number and therefore not in the set of even numbers.

#### Index ####

In 'place oriented' collections, you access values by where they sit in the collection; this is called the 'index'. Imagine you have 5 empty boxes `[ ] [ ] [ ] [ ] [ ]` and you fill it with random values between 1 and 10, so now you have `[2] [5] [3] [8] [9]`, you could ask 'what value is in the fourth box?' and the collection would return 8. An interesting point to note is that most collections in programming are 0-indexed, which means in the previous examples of 5 boxes, the keys would be 0 to 4. So the fourth box, would have an index of 3. 

```
index: [0] [1] [2] [3] [4]
value: [2] [5] [3] [8] [9]
```

#### Keys ####

The next collection access style has several names, including maps (a word that has several meanings in programming), associative arrays, key-value pairs, and dictionaries. These all express the core idea that you access a value by some kind of name (a key). This data structure would suit the example of a real estate listing, where you may wish to retrieve the listing's value for the 'houseSize' key, or the 'landSize' key. The advantage of using associative arrays is that instead of accessing things by a more abstract concept like index, you can use strings and encode even more specific information into the collection. 

```
key:   ['houseSize'] ['landSize'] [     'price'    ]
value: [ '250sqm'  ] [  '0.9ha' ] ['$1,5000,000AUD']
```

This way of accessing data makes far more sense than trying to remember the order of properties and accessing them by index, especially as your collections grow in size and complexity.

```
index: [    0   ] [   1   ] [       2      ]
value: ['250sqm'] ['0.9ha'] ['$1,500,00AUD']
```

### Order ###

Collections of data can be sequential or they can be unordered. A collection accessed by keys or by membership does not need to be ordered; however, a collection accessed by indices has a natural sequence in the access that may reflect an underlying order to the data. 

```
index:          [ 0 ] [ 1 ] [ 2 ] [ 3 ]
heightOverTIme: [155] [157] [159] [160]
```

In this example, it is useful to use the sequence of the access indices to encode the order of the observed height over time. 

### Uniqueness ###

Uniqueness is an important property to understand for collections accessed by membership and by key; it is a matter of business logic if the values in an indexed collection are unique. 

Membership does not allow for repetition, if I have a collection that answers 'true' to containing the number 8, and I add the number 8 to it, the answer still remains true; there is no change.

Uniqueness is an important consideration for collections accessed by key, because keys must be unique; if you had two keys with identical values, you would need some way of resolving which was the one you were asking for. 

## Collections in JS ##

Now you've been introduced to the basic properties of collections that will help you select which ones are most appropriate to use on a case by case basis, it's time to learn what specific tools JS offers you to collect your data. 

### Array ###

Arrays are accessed ordered, accessed by index, and have no uniqueness requirements. They are created by using the square brackets notation, and are accessed by indices in square brackets.

```javascript
let myArray = [1, 2, 3.14, 'fourish', 3 + 2]
myArray[0]
myArray[1]
myArray[2]
myArray[3]
myArray[4]
```

Observe the array's elements are of different types, it is accessed by index, and each element is evaluated when we create the array, that is why the 5th element at index 4 has the value 5, JS has evaluated the expression `3 + 2`. 
There is a lot more that can be done with arrays in JS, check the links in resources, open up Node.js, and experiment with them to begin developing a sense of their utility.

### Object ###

Objects make up basically everything in JS, you will learn over the coming lessons just how powerful they are; for now it is sufficient to know they are accessed by keys, the keys must be unique, and they are unordered. 

```javascript
let listing = {'homeSize': '250sqm', 'landSize': '0.9ha', 'price': '$1,500,00AUD'}
listing['homeSize']
listing.homeSize
```

Observe the two ways of retrieving a value by key, using square brackets or using the dot-notation; there is a lot more that can be done with objects in JS, in fact they form the fundamental building blocks of everything; for now focus on ensuring that you know how to set a key-value pair, modify values, and retrieve values. To make your understanding stick, open up Node.js and begin to experiment by creating and interacting with objects. The full suite of their capabilities will be made apparent over the coming lessons.


### Set ###

JS has a Set, which is used as a unique membership accessed collection; however, the way it is implemented requires some experience using classes. In future lessons as you build your skills in using classes and objects in JS, you will be able to fully explore the capabilities of the Set object; for now, it is enough to know it exists and is available. 

