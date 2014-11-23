# Learn you JavaScript for fun and profit
JavaScript is an implementation of ECMAScript, a standardized browser scripting language that powers all aspects of the WWW. What exactly does JavaScript do? It adds behavior to web pages, it allows you to do things asyncronously, it allows you to store things on the client, in short: JavaScript allows you to program the web.

What are all these JavaScript buzz words?
- Node: a stand-alone (no browser) JavaScript interpreter (things that runs your code) built out of Chrome. It's wicked fast and built to do things asyncronously.

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
Here we want to start off with things that describe data. The world is all information and we can represent it in many ways but some ways are more sensible then others **but** HFC. To go a bit more in depth (use fancy words for ideas) we have two main types: Primative and Reference. Primative to type is atom to molecule. These are the simplest building blocks of the ways to translate real world things into code. Reference is a little more complicated. References are ways to "point" to something: not making a copy of it for yourself. To understand what we mean, let's look at some code.
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

The trick here is that we can't have an odd number of quotes that are supposed to surround our string. If we don't surround the string with one and only one type of quote character we will be told there is an error in our code by the all powerful interpreter: teller of your wrong. We did, however, illustrate the way you can still use them in a combination with each other as long as you are careful. There are some situation where we will need to get a bit fancier.

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

Here, the plus sign means to take two numbers and make them into one number. It is a __binary__ operator because it operates on two things at once. There are unary operators like the ```typeof``` operator that operates on one thing and tells you what type it is (like string or number). The most often used binary operator is by far the assignment operator, our old pal ```=```.

**End Aside**

- '' vs ""
- Methods and Operators for Strings

### Numbers
- NaN
- Integers
- Floats

### Arrays
- Ordered list of arbitrary data
### Objects
### Boolean
### Dates
### Undefined
### Null

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
