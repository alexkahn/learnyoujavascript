Chapter the Third
==================
Making Decisions
-----------------

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

##### All these equals

So there's this thing about JavaScript that is a little quirky. There are two different ways to ask if two things are equal. In some ways, this is a little intuitive: to us, this -> 1 looks an aweful lot like this -> '1'. To us, this is just one but to the machine these are completely different things but in JavaScript we can mimic this (but really, we shouldn't in most cases).

Here's something simple:

```js
1 == '1'
// true
```

That's not entirely unreasonable, but here's the other way:

```js
1 === '1'
// false
1 === 1
// true
```

This is more correct as strings and numbers are in no way equal. In general, if you are comparing two things you will want to do this second option because it ensures you're looking at things that are the same primitive type as well as the same value. This is good because say we have something like the following:

```js
var creditCardNumber;
if ( creditCardNumber == 7234567248932) {
    refundCard(100000);
}
```

This is a little crazy but you can see what might happen here. Suppose someone puts some kind of malicious code 
Establishing the equality of other things like objects and arrays is a bit more complicated.

##### If - else if - else

##### Conditional Operator Summary Table
```
|----------|--------------------------|
| Operator | Meaning                  |
|----------|--------------------------|
|    >     | Greater than             |
|    <     | Less than                |
|   >=     | Greater than or equal to |
|   <=     | Less than or equal to    |
|   ==     | Logically equal          |
|   ===    | Strict logical equal     |
|   &&     | Logical 'and'            |
|   ||     | Logical 'or'             |
|    !     | Logical 'not'            |
|__________|__________________________|
```

##### Switch

The switch statement is used to choose between scenarios where the
expression being evaluated is always the same data type.

For example:

```js
switch(direction) {
  case 'north':
    return 'You found some mountains!';
    break;
  case 'south':
    return 'Be careful, there are swaps here';
    break;
  case 'east':
    return 'You fell into the ocean, go back 3 turns';
    break;
  case 'west':
    return 'Gold rush!';
    break;
  default:
    return new Error('No direction selected');
}
```

The equivalent `if`-statement would be:

```js
if (direction === 'north') {
  return 'You found some mountains!';
} else if (direction === 'south') {
  return 'Be careful, there are swaps here';
} else if (direction === 'east') {
  return 'You fell into the ocean, go back 3 turns';
} else if (direction === 'west') {
  return 'Gold rush!';
} else {
  return new Error('No direction selected');
}
```

The switch statement makes it easier to write out the conditional logic
you need when deciding between something like direction. In general the
expression in the parenthesis of the switch statement must be of the
same type as each of the case statements. You will also want to know
what the `break` statement means. All it means is that the interpreter
should exit the decision construct and return to the calling context or
parent environment.

The switch can also be used without the break if you want to do
something that cascades down the case statements like so:

```js
switch (arr.length) {
  case 1:
    out += 'one';
  case 2:
    out += 'two';
  case 3:
    out += 'three';
  default:
    out += 'Done!';
}
```

If we put that into a function called `useSwitch`:
```js
function useSwitch(arr) {
  var out = '';
  switch(arr.length) {
    case 1:
      out += 'one';
    case 2:
      out += 'two';
    case 3:
      out += 'three';
    default:
      out += 'all done';
  }
  return out;
}
```

Then we can see what happens when we give it an array of different
lengths:

```js
> useSwitch([4]);
'onetwothreeall done'
> useSwitch(['hello', 'world']);
'twothreeall done'
> useSwitch([{},{},{}]);
'threeall done'
> useSwitch([[],[],[],[]]);
'all done'
```

Making decisions can be difficult but using the tools available can make that
a much simpler process.
