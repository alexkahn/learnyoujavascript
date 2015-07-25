# Chapter the Second
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
let's do just that. Undefined is the value that has no value,
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

To be clear, `undefined` is neither primitive nor reference (object), it
is in a category of it's own.

### Null
Much like `undefined` we have another 'non-value' value, `null`. We
use null to act as a way of indicating that nothing is there,
specifically, no object is there. To illustrate, let's look at some
testing code:

```js
var request = require('request');

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

Special object:
* Null

None of the above:
* Undefined

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

### instanceof