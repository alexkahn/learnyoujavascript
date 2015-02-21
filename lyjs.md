# Learn you JavaScript for fun and profit

JavaScript is an implementation of ECMAScript, a standardized browser scripting language that powers all aspects of the WWW. What exactly does JavaScript do? It adds behavior to web pages, it allows you to do things asyncronously, it allows you to store things on the client, in short: JavaScript allows you to program the web.

What are all these words that people use?
- Node: a stand-alone (no browser) JavaScript interpreter (thing that runs your code) built out of Chrome. It's wicked fast and built to do things asyncronously.

- jQuery: jQuery is a library (a bunch of files with code in them like yours) that turns ugly, annoying JavaScript into nice, elegant JavaScript.

```js
// for example:
 $('#my-id').hide();
//is the equivalent of:
var myId = document.getElementById('my-id');
myId.style.display = "none";
```

- Angular JS, Ember JS, Backbone JS: These are front-end MVC JavaScript frameworks. The point is to make the piles and piles of JavaScript you write into fewer piles. 

## Programming Principles

Are you an engineer or an artist? Is there a difference at a certain point? Almost any field of study you can imagine has a subfield called "Computational [field]." So there are all these people out there who are Neuroscientists, Astronomers, Economists, Finance professionals etc. that program for fun and profit. So can you! There are many, many people out there that would love to tell you their opinions on how to code 'properly' and the like. Hey, I guess that's what I'm doing but really I'm just relaying the stuff I've seen so far that I've found useful. So here are some acronymns.

- KISS: Keep it simple, stupid. Your goal as a programmer is to translate your idea into code simple. If the code you are writing is growing and growing but not making much progress in accomplishing your goal, you should consider using your delete key liberally. There are an infinite number of ways to code any one thing but only a few of them are any good. 

- DRY: Don't Repeat Yourself. If you find yourself typing essentially the same things over and over (or just more than once) then it would be a good opportunity to make a function or a method that encapsulates that procedure.

- Convention over Configuration: A lot of people have been coding for a long time and a few good 'patterns' have emerged. This term is generally reserved for web development (at least to my knowledge) but essentially the idea is to not fight the current on how to name things, where to put files, etc.. That is, just use the defaults: it will seem like magic at first but the first time you encounter an error that occurs from your departure you'll learn the secrets behind the magic pretty quickly. But, like any programming paradigm or idea, there is a counter: in this case, Configuration over Convention. That is, do whatever you want your framework should be agnostic to your naming, organizing etc.. Both of these principles have their place much like the rest of the ideas we're discussing here so just keep them in mind as your journey continues.

- YAGNI: You Ain't Gonna Need It. Here's a good one that throws a bit of a wrench in writing 'elegant' code: with all these modern computers, cloud technology and the like, making small savings/ pouring over code for optimizations will generally not matter. You might think that denormalizing your database will make your application run faster but there are probably some more glaringly obvious changes/ refactoring you could do for a comparable gain in application efficiency. That is, don't worry about it, having so much traffic that your site breaks is a good problem that you can solve later provided you have some data to inform you.

- Horses for Courses (HFC): In truth, this isn't something I learned in the course of programming, I learned it in International Finance at Florida State from a professor by the name of James Cobbe. This lesson had little to do with International Finance (like most good lessons in economics courses) but instead for horse racing. The idea here is that the performance of a horse is correlated with the track on which the horse is running. Mud, clay, grass, turf - each of these scenarios (I have no clue on which courses horse racing occurs) will have a significant impact on which horse will do the best. So, the tools you use (for fun and profit) should be suited for the application. For example, you need to make an application that displays blog posts. Would you write it in Enterprise Java Server Pages, use an Oracle Database, and put it on a cluster of extra large AWS machines? Probably not, that's overkill unless you are managing millions of visitors, millions of blog posts, etc.; just use WordPress or Jekyll. Point is, selecting the right tools for the job isn't always so obvious but it's totally worth some thinking and searching.

- Typing is BAD. This isn't really a subtle philosophical lesson, it's just practical. Every key stroke you make is a step towards carple tunnel, wrist issues, elbow issues, you name it. If this is something you want to do for a living, you'll probably be typing a lot so every little saving in typing is worth it's weight in gold for your longevity as a programmer. It is absolutely worth learning as many shortcuts with the keyboard as possible, not just for a text editor but for your operating system. Learning the command line is super valueable but it's also worth your time to write configurations to make your own shortcuts. Many people are proud of their .vimrc, .bashrc, and .gitconfig files and many of them are available on the internet for you copy and paste. Do it.

- Mice are BAD. The mouse was made to make Graphical User Interfaces (GUIs) easier to navigate. Mice are great, very fancy but entirely unnecessary. You can do everything with a keyboard you can do with a mouse plus more. Every time you take a hand off of the keyboard and on to the mouse, you lose precious time. You may be saying: "psh, come on - how much time could I possibly save?" Whoa there, why so argumentative? Time to math: if you use a mouse every time you are done typing something, say that happens 50 times a day. The motion of moving your hand from the keyboard, placing it on the mouse, moving the mouse, taking your hand back off of it and placing it back on the keyboard takes probably around 2 seconds on average. That's about 100 seconds per day, 500 seconds in a 5 day work week. So you lose 20 minutes a week which is time you will never get back. Feel free to take some measurements and figure it out on your own, hopefully you'll realize that your mouse is almost completely useless.

## Data

Here we want to start off with things that describe data. The world is all information and we can represent it in many ways but some ways are more sensible then others **but** HFC. To go a bit more in depth (use fancy words for ideas) we have two main types: Primative and Reference. Primative is to type as atom is to molecule. These are the simplest building blocks of the ways to translate real world things into code. Reference is a little more complicated. References are ways to "point" to something: not making a copy of it for yourself. To understand what we mean, let's look at some code.

```js
var myFavoriteNumber = 42;
```

Here we just made a variable (yes, just like Algebra) and it represents a little slot in our memory, this is what RAM (Random Access Memory) is, that **actually** holds on to the number 42 (10101 in binary for you machines out there). A reference type holds on to a copy of the **address** of that memory slot ```myFavoriteNumber``` represents. The coolest way of showing you what this means is with code:

```js
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

```js
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

```js
// String examples
"a"
"I am a string"
"298()*7230985y98y98Yv48932hq894y0g8437q2-0957"
"124"
```

As you can see, there is pretty much anything we can shove between some quotes and call it a string. These strings we just made don't stay anywhere (we didn't make variables for them to live in) and they are called "String Literals" because they are literally strings - literally. Here's the first gotcha: what happens when you mix up the quotes?

```js
'This won't work';                              // ERROR!!
"This will work or I ain't a good programmer";
'She said and I quote "This is literally amazing"';
```

The trick here is that we can't have an odd number of quotes that are supposed to surround our string. If we don't surround the string with one and only one type of quote character we will be told there is an error in our code by the all powerful interpreter: teller of your wrong. We did, however, illustrate the way you can still use them in a combination with each other as long as you are careful. There are some situations where we will need to get a bit fancier.

```js
// Challenge: Make a sentence into a string
// I'm sure the most important thing to remember is to "keep calm."
// Solution 1:
"I'm sure the most important thing to remember is to " + '"keep calm."'
// Solution 2:
'I\'m sure the most important thing to remember is to "keep calm."'
// Solution 3:
"I'm sure the most important thing to remember is to \"keep calm.\""
```

First, let's note that we can use what are called _escaping_ to tell JavaScript we would like it to treat specific characters as part of the string, not things that tell it when it should stop regarding characters as part of a string (there's a common one called the new-line character: '\n' that makes it print a new line). Another fun thing in here is the idea that we can 'add' strings to each other; that leads us into a quick, fun aside.

**Aside**

There are some really fancy words for things like `+`, `=`, `<=`, and `typeof`. They are known as operators. Operators have even more specific names depending on how many things they work on. You know about binary operators, you've been using them since grade school. Here's a binary operator:

```
2 + 2
  |
There!
```

Here, the plus sign means to take two numbers and make them into one number. It is a __binary__ operator because it operates on two things at once. There are unary operators like the ```typeof``` operator that operates on one thing and tells you what type it is (like string or number). The most often used binary operator is by far the assignment operator, our old pal ```=```. In math, ```=``` means 'is equal or equivalent,' it is a relation between things like numbers and sets.

In computer science and programming we often use the equal symbol to represent assignments and it means "hey, put the thing on the right hand side (usually some data) into memory and I will call it by the name on the left hand side."

The take away here is that we will not use ```=``` in the normal, mathy
way.

**End Aside**

Life wouldn't be complete without methods (functions) on strings that tell us more about them.

The first thing we'll do is as a string how many characters it has.

```js
"my first string".length
"myfirststring".length
```

I kind of lied, ```length``` isn't a method. Technically it's a property which means no parenthesis when we ask for it. Properties aren't a behavior, it's like asking how tall a tree is or what the capacity of a barrel might be. Properties don't *change* anything. We could go through all the string methods one by one but that would certainly deserve a large amount of typing and someone (actually, a lot of people) have done this for us but I will show you how to use them.

```js
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

One last thing before we move on. Let's make a string:

```js
var state = "Mississippi";
```

It is a very nice string, nothing crazy. Let's play Horror Movie and slice it up.

```js
state[0];
// 'M'
```

Think of a string as a list of individual characters that are strung (please forgive the pun) together. When we have a construct like this (a list of things that is) we can use square brackets to get stuff out of it like so:

```js
state[8]
// 'p'
```

This is something important how many languages choose to do things. They will start counting at 0. This is called Zero Indexing and just means that when we want to loop through something (we'll go over that in detail later) we'll probably have to add or subtract a one as the case may be. Since we're on the topic of indicies, let's learn another useful method.

```js
state.indexOf('p');
// 8
```

The `indexOf()` method takes in a character and outputs where that element is in the string. There is also an analogous method for arrays (we'll talk about those later). For completeness, let's make more strings from stirings:

```js
state.substr(0,5);
// Missi
```


### Numbers

We've seen numbers assigned to variables already but we haven't discussed what kinds of numbers we can make. First let's take a second to review some of the common types of numbers:
* Natural numbers [1, 2, 3, 4, 5]
* Integers [... -3, -2, -1, 0, 1, 2, 3]
* Rational Numbers (they can be represented by dividing one integer by another so long as the denominator isn't zero)
* Real Numbers (The rationals plus all the numbers that can't be represented by fractions like the square root of two or pi)
* Complex numbers (the reals plus the imaginary numbers - here for completeness, not because we'll use them)

To JavaScript, there are only two real (see what I did there?) types of numbers: integers and floats. Integers are exactly like I mentioned above: whole numbers that are or positive negative but floats are a little but different. A float is an approximation to a number that doesn't always work out the way you expect.

```js
1.2347 - 1.2344 // should be: 0.0003
// > 0.00029999999999996696
```

Thus we have illustrated the struggle of programming with math happening. Luckily, many of these problems are well documented but it is worth noting that not every number is computable, in fact a great deal of them are not. It has been shown (proved mathematically) that not all real numbers are computable by machines (they can't be represented internally) so that's just something to keep in mind. There are plenty of resources out there for doing math with JavaScript (like the Math javascript library) but we still have some number types to talk about.

#### Integers

Integers are just like their mathematical counterparts: positive and
negative whole numbers. We can make a other primative types into
integers with the ```parseInt()``` method like so:

```js
var fortyTwo = "42";
var int = parseInt(fortyTwo);
console.log(typeof int);
// 'number'
```

JavaScript will attempt to make conversions for you based on what you
give ```parseInt()``` but make sure you try it to see what happens.

#### Floats

Floating point numbers are representations of non-whole numbers. That is to say, we can use floats to represent values like `1/2` as `0.5`, similarly for every terminating rational number (unlike `1/3`). For numbers that don't terminate, we get things like this:

```
node> 1/3
0.3333333333333333
```

Then there are the irrational numbers. This is where we have a talk about the representation of numbers and such. Honestly, this probably won't ever keep you awake at night so I'll just say that doing a bit of searching for `floating point numbers` will give you all the info you need to make sure you're doing things as correctly as possible. You can get famous math numbers like `π` like so:

```js
var pi = Math.PI
console.log(pi);
```

Yay! Another oppotunity to talk programming style! One of the things that is popular for programmers to do is play around with the case of a variable to tell you what it is:

```
var DISCOUNT_RATE = 0.25;
var someVariable = 'some string';
var Class = function() {};
```

In JavaScript, if we make some variables that won't ever change in the program, we put them in all caps (you can finally use that caps lock key for something!). For most every other variable, we use camelCase. If we are doing some more advanced JavaScript, we might want to create a class so we'll give it a titlized name. If, for example, we have a class with more than one word in it's name, we'd do something like this:

```js
function MyClass () {}
```

Notice I've trickily been introducing functions and how you can define them, more on that later.

#### NaN

Programming languages need things to represent certain concepts. In a
moment we'll look at some other primitives that fill similar voids (you
C++ folks know the pun at play here). There are times when we want to do
operations on numbers but we can't be too confident that what we have
is, in fact, a number. Instead of going through a lot of exposition,
let's write a little code.

```js
1 - 'hello';
// NaN
```

That's all we're saying here. When we ask JavaScript to evaluate an expression that involves numbers and it can't very well turn one of the operands (stuff on either side of the binary operator) into a number, JavaScript very politely returns `NaN`. Primarily, well will not deal much with this character but there is a very useful method for checking values.

```
node> isNaN([])
false
node> isNaN({})
true
node> isNaN(0)
false
node> isNaN(true)
false
node> isNaN(false)
false
node> isNaN('happy')
true
node> isNaN('127')
false
```

Notice `isNaN()` returns `true` or `false`, it is a Boolean (more on this in a moment) function that only decides whether whatever is passed to it is a number. Notice also that what seems to not be a number can sometimes make `isNaN()` return false. These are well known 'quirks' in JavaScript so you may need to get a little creative if you have to check the type of something. One last remark is that you may notice that there is also some funny business with `true`, `false` and the string `'127'`. Another fun part of dynamically-typed languages (languages where variables don't explicitly take one and only one type) is that sometimes the language will attempt to keep us safe by coercing a value from one type to another. Some examples:

```
> Number(true)
1
> Number(false)
0
> Number('127')
127
> Number('127.0')
127
> Number('127.5')
127.5
> Number([])
0
> Number({})
NaN
```

Well, the cat's out of the bag: JavaScript can be an immensly
frustrating language to work with at first, even though it is in many
respects an 'easy' language. Thus we have illustrated the need for you
to be creative with these imperfect tools. If you like, you can write
your own language or try another one but if you want to work on the web,
you'll start to appreciate the flaws and embrace the silliness of some
parts. Now, on to next!

### Boolean
The humble Boolean owes it's namesake to George Bool, a mathematician
and inventer of (you'll never guess) Boolean algebra. What's that you
say? This isn't a math tutorial, nice try though. Boolean values are our
friends `true` and `false`. That's it. Every boolean ever made
(correctly) has had one of those two values (but not both). Remember
when we talked about truthiness and falsiness? None of that here, these
values are the absolute truth and absolute false. They are great for
answering yes/no questions so let's have an example:

```js
while(true) {
 console.log("Infinite loop? Yeah, we got that");
}
```

This is a simple example of folly: we made a loop that never ends by never telling it how or when to stop. Hey, maybe that's not such a bad idea, it's the central building block of
event-driven programming and, spoiler alert, that's what JavaScript is really all about. The central theme of JavaScript in the browser and running in Node.js: the event loop. So anyway, back to Booleans. Another example:

```js
function isFortyTwo (number) {
  if (!isNaN(Number(number)) && +number === 42) {
    return true;
  } else {
    return false;
  }
}
```

Here we've defined a function that indicates whether or not it's
argument is the number forty-two. So we can call it like this:

```js
isFortyTwo(42);
// true
isFortyTwo(6*7);
// true
isFortyTwo('42');
// true
isFortyTwo('obviously we want something false');
// false
```

Let's check out the secret to this sauce. First, we ask the question if
`number`, after being converted to a number by `Number()`, isn't NaN,
AND `number`, after being explicitly converted to a number using a `+` is `===` to
the number 42, we'll send back the value `true`. In any other case,
we'll send back false. This is really where booleans come in handy:

```js
if (isFortyTwo(someVariable)) {
  // do something here
} else {
  // do something else here
}
```

Instead of all that nasty logic (which we might have to repeat in an
application) we've made a function that does the work for us so we don't
have to abuse the copy-paste feature or potentially make a mistake in
one place but not be able to find it as easily.

### Undefined
Trying to define `undefined` is likely the greatest of all ironies. So,
let's do just that. Undefined is the primitive value that has no value,
it is simply undefined. For instance, if we were to do something like
this:

```js
var something;
console.log(something);
// undefined

function foo(x) { return x }
foo();
// undefined
```

The pattern here is that undefined denotes a type of 'missing' value. We
can use `undefined` to make sure we aren't doing anything crazy like:

```js
if ( something === undefined) {
  // STOP NOW!
}
```

### Null
Much like `undefined` we have another 'non-value' value, `null`. We
use null to act as a way of indicating that nothing is there,
specifically, no object is there. To illustrate, let's look at some
testing code:

```js
describe('Requesting the GitHub home page', function() {
  it("doesn't complain when everything is normal", function (done) {
    request.get('http://www.github.com', function(err, response, body) {
      expect(err).to.equal(null);
    });
  });
});
```

Whoa! That's some super advanced looking stuff! This is an example of
how one might test some JavaScript code using the concepts behind Test
Driven Development or Behavior Driven Development. These techniques
allow you to develop software based on things called 'specs' which are
specific scenarios you want to test your software against. Tucked away
in here is an important lesson about using null to test things. Say, for
example, we got some data from our server in an AJAX request and we want
to make sure we got our data and not an error. Note that this is a naive
test but it will illustrate an important concept. To ask JavaScript what
type of thing we are dealing with is, we use the (unary) typeof
operator like so:

```js
var myString = 'learn you javascript';
typeof myString;
// 'string'
```

All of the data types we've looked at so far have an answer to the
`typeof` question but `null` is special.

```js
var myVar = null;
typeof myVar;
// 'object'
```

Uh oh. That's not something we'd expect. Why doesn't it say `null`?
Well, that's just how JavaScript is. This is a well known 'quirk' of
JavaScript so if we need to know if something is `null` we should do it
like this:

```js
var myObject = null;
myObject === null;
// true
```

Notice we use the triple equals instead of the double here.

So we've covered all of the Primitive JavaScript types. For review, they
are:

* Strings
* Numbers
* Booleans
* Undefined
* Null

Now we are going to venture into the second set of 'types' in JavaScript
known as Reference Types that will expand our toolbox for representing
real-world things.

## Reference Types

Alright, here we are at the beginning of the reference types. To work
with these we need to look at what happens under the covers a bit. Let's
look at the memory slots where we store variables.

```
------------------------------
|        |          |        |
| favNum | myString | myBool |
|  (42)  | ('yes')  | (true) |
------------------------------
```

Here you can imagine we are storing each of our values in a slot in the
computer's memory. For Primitive Types, we store them directly in the
slots but for Reference Types we will only hold a reference to the
variable. A reference here means a pointer, a special thing whose value
is an address to another place in memory. Note, you will not have to
worry about this, JavaScript keeps track of this stuff for you, all you
need to know is that the memory picture looks like this:

```
          variables               where our reference types live
--------------------------------    -------------------------
|         |         |          |    |        |       |      |
|  myObj  | array1  | Date.now |    | object | array | date |
| (Addr1) | (Addr2) | (Addr3)  |    |        |       |      |
--------------------------------    -------------------------
   |        |        |                  ^        ^      ^
   ---------|--------|------------------|        |      |
            |--------|---------------------------|      |
                     |----------------------------------|
```

The reason I bring this up is to explain an important part of working with these things. At the beginning of the data section, we explored this idea a bit.Consider the following:

```js
var num = 42;
var fortyTwo = 42;
console.log(num)
console.log(fortyTwo)

num = 'string'
console.log(num);
console.log(fortyTwo);

var myArray = [1,2,3];
var copy = myArray;
console.log(myArray);
console.log(copy);

myArray = ['a', 'b', 'c'];
console.log(myArray);
console.log(copy); // not quite what we think of a copy.
```

Once again we've shown that making 'copies' of reference types isn't exactly straight forward. I bring this up again to talk a little bit more about what a reference type is.

```js
typeof new Array();
// 'object'
typeof new Object();
// 'object'
typeof new RegExp();
// 'object'
typeof new Date();
// 'object'
typeof new Function();
// 'function'
typeof new Error();
// 'object'
```

It has been natural up to this point to talk about two classes of types but what we really have is a set of Primitive data types that can be combined to form new structures in the form of objects. All of our reference types are distinct objects that cannot equal anything but themselves. For example:

```js
var myArray = [1,2,3];
var yourArray = [1,2,3];

myArray === yourArray;
// false
```

So now we have two problems with Reference Types: it isn't always straight forward how to copy them and it isn't easy to figure out if one is equal to another.

### Arrays

Arrays are a simple way to combine our data into 'lists.' Arrays are created like so:

```js
var a = [1,2,3,4];
var b = new Array();
var c = new Array(20);
```

The first example is creating an array literal, the second using what's called a constructor (a way to make a new thing), the third is the constuctor with an argument with an integer literal to let the Array constructor know how long the array will be.

Arrays can hold all of the primitive types, and any reference types. This means we can construct arrays of arrays, a concept that allows us to build mathematical objects like matrices which can represent things like the pixels on a screen (think about what a screen really is: a bunch of x,y pairs). We can make a mix of types like this:

```js
node> var myArray = [1, true, 'maybe', null, undefined, Date.now(), [0,1,1,0], {}, /^[0-9]+/g];
undefined
node> myArray
[ 1,
  true,
  'maybe',
  null,
  undefined,
  [ 0, 1, 1, 0 ],
  {},
  /^[0-9]+/g ]
```

While it is nice to know that you can put anything into an array (this one holds all of the primitive and reference types), you'll have to keep track of where something is in the array. This we can do with some handy brackets:

```js
myArray[0];
// 1
myArray[1];
// true
```

This is a concept called indexing: we will use integers (or natural
numbers if you're one of those people) to count the places that all of
our elements live in with one _very_ important piece: INDEXING STARTS AT
ZERO. Why all the caps? It's a big mistake that all beginners will make,
even some pros. Let's take a look:

```
myArray
-----------
 0 | 1
 1 | true
 2 | 'maybe'
 3 | null
 4 | undefined
 5 | [0,1,1,0]
 6 | {}
 7 | /^[0-9]+/g
```

As we can see, there isn't much to this but when we get to looping and
iteration we'll see where this will trip us up (but hopefully we'll be
diligent and it won't)

### Objects

### Dates

instanceof

## Constructs
Now that we have all the main data stuff out of the way, let's do something with it!

Doing something in programming means manipulating data and acting on the information. We'll evaluate __expressions__, make decisions and do things repeatedly with __statements__, and put pretty much all if that stuff in functions. Each of these topics is the core of what programming **does**, so far we've only really talked about the information that powers the fun stuff.

### Statements

#### Control Flow
When we make decisions we use logic. Hopefully. The point of logic is to help us ensure what we are going makes sense and will behave like we want/expect so it's worth going through some logic.

##### Logic and you
Truth and falsehood are not always easy to determine in life but luckily computers are much more simple. In logic terms, statements are true or false. That's it. Period. It's convenient that we have two special values (remember Booleans?) ```true``` and ```false```. These are pretty handy but we'll need to deal with things whose truthiness or falsiness will need to be determined instead of made explicit with those two values. **Side Note**: I used **truthiness** and **falsiness** on purpose, some things are considered falsy but not the exact value of false; examples: the empty string ("") and the ```null``` object.

Now let's start asking questions.

##### The ```if``` statement

The simplest question we can ask is if something is true or false. Then what? Well, ```if``` today is Monday, then we want to go home as early as possible.

In code:

```js
if ( today == "Monday" ) {
    console.log("go home early!");
}
```

Notice we left it up to whether we can determine if today is in fact Monday: if it is, we have some very high hopes for getting home at a decent hour. But what if it isn't Monday? Shan't we have no alternative? Of course not! That's what we want to be able to deal with: multiple scenarios. So it might be natural to say, well, if it isn't Monday then we'll assume we're here for the long haul.

```js
if ( today != "Monday" ) {
    console.log("We'll be here forever.");
}
```

But wait, that seems like a lot of code: and we seem to really be only dealing with a case where we want everything that doesn't meet our initial condition (the if today __is__ Monday bit) to be handled in the same way. Here comes the magnificent ```else```.

```js
if ( today == "Monday" ) {
    console.log("go home early!");
} else {
    console.log("We'll be here forever.");
}
```

Notice we've captured the idea of what to do in a specific scenario and what to do if that specific scenario isn't what happens. This particular case of: ```if```-```else``` is very simple and indeed would be pretty hefty to type so of course this kind of thing happens all the time. That's where out friend ```?``` comes in.

```js
if ( today == "Monday" ) {
    console.log("go home early!");
} else {
    console.log("We'll be here forever.");
}

// is the same as:

today == "Monday" ? console.log("go home early!") : console.log("We'll be here forever.")
```

All we did was put our conditional expression in front of a question mark, then said what to do if it is true or false. Compare what you see here to the if statement above it.

Just for posterity, here's the syntax of the if:

```js
if ( conditionalExpression ) {
    statement(s);                     // must be true for me to run
} else {
    possiblyDifferentStatement(s);    // if not, I'm here to help!
}
```

Notice the semi-colons don't need to be sprinkled everywhere in these things. That's super nice. The other fun thing is that we can really do as many things as we need to within these blocks (stuff between brackets is sometimes referred to as a block of code). That is, we can have more than one thing to do if something is true or otherwise. One other cool caveat is that in here we said that a ```conditionalExpression``` is expected between the parenthesis which means we can make even more complex logic as long as we get something true (or truthy) back otherwise our else code block will run.

##### Logical Or

Since we can decide two routes, what if we have more than one condition? What if we want to go home early on Monday or Friday? In logic, mathematics and computer science, when we say 'or' we are **not** saying "this or that" what we are saying is "this or that or both." The so-called 'inclusive' or. That means when we use the ```||``` operator to say "this or that" we'll need to consider the possibility of both this and that being true.

```js
if ( today == "Monday" || today == "Friday" ) {
    console.log('get home early!');
} else {
    console.log("sigh, we'll never leave...");
}
```

What happens here is the JavaScript interpreter will first evaluate ```today == "Monday"```, if it is true, it won't bother checking the second condition because it doesn't change the fact that the logical or statement is true if and only if at least one of it's conditional statements is true, which one it doesn't matter but the computer will only check one if it can get away with it.

In this case, we'd have some kind of strange error if today was both Monday and Friday, which leads us to...

##### Logical And

Ah yes, ```and``` or ```&&``` as JavaScript expects it. Logical and means essentially the same thing it does in English, following the previous example we would write:

```js
if ( today == "Monday" && weather == "rain" ) {
    console.log("Boo! I don't want to work");
} else {
    console.log("At least it isn't Monday or Raining...");
}
```

There are a couple subtle points in here, one is the use of the single-quote in the string (remember that?) the other, more pertinent, point is what that else statement says. In that sentence I just illustrated what information we have determined from the ```today``` and ```weather``` variables. Also, it is a demonstration of De Morgan's law (just put that into a search bar). We know that if an ```&&``` breaks (doesn't evaluate to true) then we can only say that at least one of the conditions is false, but it is also possible that both are false. If we wanted to show that symbolically, we might say:

```
If today == Monday && weather == raining  --> False
  Then today != Monday or weather != raining // (or both)
```

If the two conditions being compared both evaluate to ```true``` then our script will execute the code in the succeeding block. The coolest part of the ```&&``` operator is that we can use 'short-circuit' logic to save ourselves. We know that if all of the statements connected by ```&&```s are true, then the entire statement is true but if at least one expression evaluates to false, we have a false conditional. Short-circuiting an ```&&``` will mean placing something in the first position of the execution of purpose. Consider the following:

```js
var user = {
    authenticated: function() {
        return false;
    },
    complexOperation: function() {
        return false;
    }
};
```

We have a JavaScript object called ```user``` that has two defined attributes (authenticated and complexOperation) that are functions. None of that should make too much sense yet but just tag along for a moment. We will often run in to situations where we need to make decisions on what to do when a user interacts with our application so we use conditionals and logic to make it happen. In the real world, the computations we execute will take time, energy and memory all of which means money. Our job is to cost as little as possible (reasonably) while doing everything we NEED to do. Back to our user object. Suppose we find ourselves in this situation:

```js
if (user.authenticated() && user.complexOperation()) {
    something.do();
}
```

Intuitively, we want to know if the user is authenticated (is who they say they are) before we do anything. That makes total sense but there's a clever bit here: if the user isn't authenticated (the authenticated method returns false) then the JavaScript interpreter won't bother doing the complexOperation because it isn't possible for the ```&&``` to evaluate to true overall. Neat!

##### If - else if - else

##### Conditional Operator Summary Table
##### Switch

#### Iterating
- for
    - (var i = 0; i < something; i++)
    - (banana in bunch)
- while
    - INFINITE LOOPS!!


- Expressions
- Functions

### Higher Level Ideas
- OOP
- Event driven programming
- Designing Code


Demo:
putting it all together:
A Practical Example with a Real-World problem (that you can SOLVE!)
- Simple website for collecting email addresses
- Stores them in a spreadsheet?
- Displays a landing page and sends a pop-up based on cookies