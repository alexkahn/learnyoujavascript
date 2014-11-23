# Learn you JavaScript for fun and profit
JavaScript is an implementation of ECMAScript, a standardized browser scripting language that powers all aspects of the WWW. What exactly does JavaScript do? It adds behavior to web pages, it allows you to do things asyncronously, it allows you to store things on the client, in short: JavaScript allows you to program the web.

What are all these JavaScript buzz words?
- Node: a stand-alone (no browser) JavaScript interpreter (thing that runs your code) built out of Chrome. It's wicked fast and built to do things asyncronously.

- jQuery: jQuery is a library (a bunch of files with code in them like yours) that turns ugly, annoying JavaScript into nice, elegant JavaScript.
```
//ex:
 $('.my-class').hide();
//is the equivalent of:
var myClass = document.getElementById('my-class');
myClass.style.display = "none";
```
- Angular JS, Ember JS, Backbone JS: These are front-end MVC JavaScript
  frameworks. The point is to make the piles and piles of JavaScript you
write into fewer piles. 

## Programming Principles
- KISS
- DRY
- Convention over Configuration
- YouAintGonnaNeedIt
- Horses for Courses (HFC)
- Typing is BAD -> Keyboard Shortcuts
- Mouses are BAD

## Data
Here we want to start off with things that describe data. The world is all information and we can represent it in many ways but some ways are more sensible then others **but** HFC. To go a bit more in depth (use fancy words for ideas) we have two main types: Primative and Reference. Primative is to type as atom is to molecule. These are the simplest building blocks of the ways to translate real world things into code. Reference is a little more complicated. References are ways to "point" to something: not making a copy of it for yourself. To understand what we mean, let's look at some code.
```
var myFavoriteNumber = 42;
```
Here we just made a variable (yes, just like Algebra) and it represents a little slot in our memory, this is what RAM (Random Access Memory) is, that **actually** holds on to the number 42 (10101 in binary for you machines out there). A reference type holds on to a copy of the **address** of that memory slot ```myFavoriteNumber``` represents. The coolest way of showing you what this means is with code:

```
var myFavoriteNumber = 42;
var copy = myFavoriteNumber;

console.log(myFavoriteNumber);
// 42
console.log(copy);
// 42

copy = "something completely different";

console.log(myFavoriteNumber);
// 42

console.log(copy);
// "something completely different"
```

Did you think we were going to change what was in myFavoriteNumber by changing what was in copy? Probably not but then there's this:

```
var somethingSuperImportant = {password: "secret-agent-man!"};
var foo = somethingSuperImportant;
console.log(somethingSuperImportant);
console.log(foo)
foo = "HACKERS!!";
console.log(foo);
console.log(somethingSuperImportant);
```

How's that for intense? Lucky for you that only happens with reference types! We'll go in to reference types later but just so you can feel at ease there are only a few reference types and they are:
* Object
* Array
* Date
* Function
* Error
* RegExp

Now we're going to talk about the Primitive types one by one.

### Strings
A string is just some stuff between quotes (single or double).

```
// String examples
"a"
"I am a string"
"298()*7230985y98y98Yv48932hq894y0g8437q2-0957"
"124"
```

As you can see, there is pretty much anything we can shove between some quotes and call it a string. These strings we just made don't stay anywhere (we didn't make variables for them to live in) and they are called "String Literals" because they are literally strings - literally. Here's the first gotcha: what happens when you mix up the quotes?

```
'This won't work';                              // ERROR!!
"This will work or I ain't a good programmer";
'She said and I quote "This is literally amazing"';
```

The trick here is that we can't have an odd number of quotes that are supposed to surround our string. If we don't surround the string with one and only one type of quote character we will be told there is an error in our code by the all powerful interpreter: teller of your wrong. We did, however, illustrate the way you can still use them in a combination with each other as long as you are careful. There are some situations where we will need to get a bit fancier.

```
// Challenge: Make a sentence into a string
// I'm sure the most important thing to remember is to "keep calm."
// Solution:
"I'm sure the most important thing to remember is to " + '"keep calm."'
```

Well it's nice we can break strings up and add them together. That leads us into a quick, fun aside.

**Aside**
There are some really fancy words for things like ```+```, ```=```, ```<=```, and ```typeof```. They are known as operators. Operators have even more specific names depending on how many things they work on. You know about binary operators, you've been using them since grade school. Here's a binary operator:

```
2 + 2
  |
There!
```

Here, the plus sign means to take two numbers and make them into one number. It is a __binary__ operator because it operates on two things at once. There are unary operators like the ```typeof``` operator that operates on one thing and tells you what type it is (like string or number). The most often used binary operator is by far the assignment operator, our old pal ```=```. In math, ```=``` means 'is equal or equivalent,' it is a relation between things like numbers and sets.

In computer science and programming we often use the equal symbol to represent assignments and it means "hey, put the thing on the left hand side into the thing on the right hand side."

The take away here is that we will not use ```=``` for comparing variables or collections of variables.

**End Aside**

Life wouldn't be complete without methods (functions) on strings that tell us more about them.

The first thing we'll do is as a string how many characters it has.

```
"my first string".length
"myfirststring".length
```

I kind of lied, ```length``` isn't a method, technically it's a property which means no parenthesis when we ask for it. We could go through all the string methods one by one but that would certainly deserve a large amount of typing and someone (actually, a lot of people) have done this for us but I will show you how to use them.

```
// Using a method, this one's for strings.
var sparseString = '    I'm data surrounded by spaces!       ';
var result = sparseString.trim();
console.log(result)

// the same thing with less typing.
var sparseString = '    I'm data surrounded by spaces!       ';
console.log(sparseString.trim());

// one more
console.log('    I'm data surrounded by spaces!       '.trim());
```

To learn more string methods, check out the very well done [String reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) made my the Mozilla Developers Network.

### Numbers

We've seen numbers assigned to variables already but we haven't discussed what kinds of numbers we can make. First let's take a second to review some of the common types of numbers:
* Natural numbers [1, 2, 3, 4, 5]
* Integers [... -3, -2, -1, 0, 1, 2, 3]
* Rational Numbers (they can be represented by dividing one integer by another so long as the denominator isn't zero)
* Real Numbers (The rationals plus all the numbers that can't be represented by fractions like the square root of two or pi)
* Complex numbers (the reals plus the imaginary numbers - here for completeness, not because we'll use them)

To JavaScript, there are only two real (see what I did there?) types of numbers: integers and floats. Integers are exactly like I mentioned above: whole numbers that are or positive negative but floats are a little but different. A float is an approximation to a number that doesn't always work out the way you expect.

```
1.2347 - 1.2344 // should be: 0.0003
// > 0.00029999999999996696
```

Thus we have illustrated the struggle of programming with math happening. Luckily, many of these problems are well documented but it is worth noting that not every number is computable, in fact a great deal of them are not. It has been shown (proved mathematically) that not all real numbers are computable by machines (they can't be represented internally) so that's just something to keep in mind. There are plenty of resources out there for doing math with JavaScript (like the Math javascript library) 


- Integers
- Floats
- NaN

### Boolean
### Undefined
### Null

### Arrays
- Ordered list of arbitrary data
### Objects
### Dates

typeof
instanceof

isNaN

Constructs
- Statements
	- Control Flow
		- if
		- if else
		- ?
		- if elseif else
		- switch
	- Loops
		- for
			- (var i = 0; i < something; i++)
			- (banana in bunch)
		- while
			- INFINITE LOOPS!!
- Expressions
- Functions

Higher Level Ideas
- OOP
- Event driven programming
- Designing Code


Demo:
putting it all together:
A Practical Example with a Real-World problem (that you can SOLVE!)
- Simple website for collecting email addresses
- Stores them in a spreadsheet?
- Displays a landing page and sends a pop-up based on cookies
