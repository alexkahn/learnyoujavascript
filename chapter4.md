Chapter the fourth
===================
Do it again!
-------------

## `for`

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
computations). The rational behind it is meaningless at this point, we
must accept that indexes begin at zero.

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
