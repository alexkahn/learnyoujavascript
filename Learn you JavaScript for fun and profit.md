# Learn you JavaScript for fun and profit
JavaScript is an implementation of ECMAScript, a standardized browser scripting language that powers all aspects of the WWW. What exactly does JavaScript do? It adds behavior to web pages, it allows you to do things asyncronously, it allows you to store things on the client, in short: JavaScript allows you to program the web.

What are all these JavaScript buzz words?
- Node: a stand-alone (no browser) JavaScript interpreter (thing that runs your code) built out of Chrome. It's wicked fast and built to do things asyncronously.

- jQuery: jQuery is a library (a bunch of files with code in them like yours) that turns ugly, annoying JavaScript into nice, elegant JavaScript.
```
//ex:
 $('#my-id').hide();
//is the equivalent of:
var myId = document.getElementById('my-id');
myId.style.display = "none";
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

```
if ( today == "Monday" ) {
	console.log("go home early!");
}
```

Notice we left it up to whether we can determine if today is in fact Monday: if it is, we have some very high hopes for getting home at a decent hour. But what if it isn't Monday? Shan't we have no alternative? Of course not! That's what we want to be able to deal with: multiple scenarios. So it might be natural to say, well, if it isn't Monday then we'll assume we're here for the long haul.

```
if ( today != "Monday" ) {
	console.log("We'll be here forever.");
}
```

But wait, that seems like a lot of code: and we seem to really be only dealing with a case where we want everything that doesn't meet our initial condition (the if today __is__ Monday bit) to be handled in the same way. Here comes the magnificent ```else```.

```
if ( today == "Monday" ) {
	console.log("go home early!");
} else {
	console.log("We'll be here forever.");
}
```

Notice we've captured the idea of what to do in a specific scenario and what to do if that specific scenario isn't what happens. This particular case of: ```if```-```else``` is very simple and indeed would be pretty hefty to type so of course this kind of thing happens all the time. That's where out friend ```?``` comes in.

```
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

```
if ( conditionalExpression ) {
	statement(s);                     // must be true for me to run
} else { 
	possiblyDifferentStatement(s);    // if not, I'm here to help!
}
```

Notice the semi-colons don't need to be sprinkled everywhere in these things. That's super nice. The other fun thing is that we can really do as many things as we need to within these blocks (stuff between brackets is sometimes referred to as a block of code). That is, we can have more than one thing to do if something is true or otherwise. One other cool caveat is that in here we said that a ```conditionalExpression``` is expected between the parenthesis which means we can make even more complex logic as long as we get something true (or truthy) back otherwise our else code block will run.

##### Logical Or

Since we can decide two routes, what if we have more than one condition? What if we want to go home early on Monday or Friday? In logic, mathematics and computer science, when we say 'or' we are **not** saying "this or that" what we are saying is "this or that or both." The so-called 'inclusive' or. That means when we use the ```||``` operator to say "this or that" we'll need to consider the possibility of both this and that being true.

```
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

```
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

```
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

```
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
