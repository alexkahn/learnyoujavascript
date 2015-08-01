Chapter the fourth
===================
Do it again!
-------------

## The `for` statement

The `for` statement encapsulates the process of how we iterate through
some collection of things. In this chapter, we will discuss the how and
the what of iterating through the data that we are about.

Let's start out with a canonical example. This is how to print the
numbers from 0 through 10 to the console (which can be done other ways).

```js
for (var i = 0; i < 11; i++) {
  console.log(i);
}
```

The for statement has three main parts. The first, `var i = 0` part, is
the initialization step: we initialize the variable i to zero. It is
worth noting here that arrays being counting at zero. This is a common
construct amongst all programming languages (except R for statistical
computations where indexing begins at 1). The rational behind it is meaningless at this point, we
must accept that indexes begin at zero.

The second piece `i < 11` is the breaking condition. Once that boolean expression evaluates to `false` the loop will exit.

The third and final piece is the thing to do when a cycle completes, usually it is used to increment or decrement the variable of we are iterating (`i`). Just for posterity, incrementing means increasing a value while decrementing means the opposite.

Let's look at a series of examples to illustrate these pieces.

```js
for (var i = 0; i < 13; i+=2) {
    console.log(i);
}
```

The previous example's output is similar to the first, only we print the even numbers from 0 to 12. So, in general, we can say that we can move the iterator by any increment or decrement as long as we don't run into a conflict of logic, that is, we will be able to exit the loop with certainty. Before we move on, let's make another very common example:

```js
for (var j = 10; j >= 0; j-- ) {
    console.log(j);
}
```

It's a countdown (hopefully not the final)!

Okay, I mentioned a couple sentences ago that we always want to exit the loop with certainty. What does that mean? Loops are part control structure, part wild animal that we must respect. The worst thing in the world is making software that doesn't work (well, there are obviously better candidates for that but we're trying to make software for a living) and one of the simplest mistakes is implementing some kind of loop that never ends. For example:

```js
for (var oops = 0; oops >= 0; oops++) {
    console.log(oops);
}
```

I wouldn't suggest running that example (sorry if you did, but now you know why it's bad). The thing that's of significance here is the fact that we cannot logically ever make the check condition false and thus never exit the loop, ever. There are a lot of ways to make something like this happen but luckily, many of the iterations we deal with will be deterministic and therefore won't just unleash the loop. There are many cases (like numerical algorithms) where we will want to have a variable that represents the maximum number of iterations we want to go through before we exit. To illustrate a more complicated example (that won't be on the final) let's see what something like that would look like:

```js
var MAX_ITER = 200;

for (var i = 0; Math.abs(current - previous) <= 0.00001 || i < MAX_ITER; i++) {
    // some more complicated stuff
}
```

So we have a really cool algorithm that is estimating some kind of value that we basically give two options: get within our tolerance level for accuracy of the estimation or we reach the maximum number of iterations before we just call it quits. Notice that we don't have to limit our loops to just exiting based on the value of the iterator, we can use other information to inform how we decide to stop looping. 

### Indexing

The idea of indexing is to pick a standard (arbitrarily) at some
starting point. For our purposes that will be zero, it is simply a
marker for the first position.

Let's look at an example:

```js
var arr = ['foo', 'bar', 'baz'];
arr[0];
// foo
arr[1];
// bar
arr[2];
// baz
```

As we can see, the first element is indexed by zero, the second is
indexed by 1, the third by 2 and so forth ad infinitum. The trick here
is to start learning to count the way computers count. The coolest thing
is that we can map (that is, create a relation between) all of the
integers starting at `n` (some integer) to any other and retain the
property of bijection. That just means that I can find my way back from
my map (function in a mathematical sense) to once place back to another.
Imagine some set of directions between two places. If I can find a path
back to where I started from where I ended, the directions (to some
degree but aren't necessarily) are bijective.
- for
    - (var i = 0; i < something; i++)
    - (banana in bunch)
- while
    - INFINITE LOOPS!!
