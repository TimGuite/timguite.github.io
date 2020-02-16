---
layout: post
title: "Maybe Python? Strong Typing and Single Dispatch"
date: 2020-01-26 19:25
categories: jekyll update
---

I've created a module which acts like Haskell's [Data.Maybe](https://hackage.haskell.org/package/base-4.12.0.0/docs/Data-Maybe.html) but for Python.
You can find that [here](https://github.com/TimGuite/python_maybe).
It was an investigation of the [singledispatch] decorator and strong typing in Python.

The first section of this post discusses the type system in Python and how it can be used.
Then I explain the implementation of the Maybe type and difficulties I found.

Please feel free to give any feedback on my code or examples!

# Types in Python

If you've spend much time working on Python, you might have got used to the idea that variables don't really have a type.
In some languages, you have to _constantly_ tell the program what kind of variable you would like.:

- `int x` => I'd like an `integer` called `x` please
- `string y` => I'd like a `string` called `y` please

and so on.

Python is a [dynamically typed](https://en.wikipedia.org/wiki/Type_system#DYNAMIC) programming langauge, which means it doesn't need this information until the program is run, and then it figures out what type you want based on what you gave it.
But sometimes, it is quite helpful to know what types you want.
For instance, knowing what type of information a function will return will help you plan how to handle that information in the rest of your program.

[Type hinting](https://www.python.org/dev/peps/pep-0484/) is the way to do this in Python.
It allows you to quite naturally specify what type of information you might want as a parameter to your functions and what type of information you will return.
Here is a brief example:

```python
x: int = 5 # specify and int
y: str = "This is a string" # specify a string
# specify a function which takes an int and returns a True/False value
def bigger_than_ten(x: int) -> bool:
    return x > 10
```

This information will often be used by your editor to help you spot mistakes, such as proividing a list of values to a function, rather than the value itself.
As the name suggests, type _hinting_ is not enforced.
The closest you can get is using [mypy](http://mypy-lang.org/) (from which type hinting was developed) to check over your code before you run it.
Someone else could still take your code, change it or use it, and receive unexpected failures because they made a mistake with their types.

Similarly, you might want to create a function which acts differently depending on what type of information you give it.
A simple example would be adding 1 to something.
Here are some examples of how that might look once we've written it:

```python
add_one(2) = 3
add_one("two") = "two1"
add_one([1, 2, 3]) = [1, 2, 3, 1]
```

This is merely an example of the same function handling different inputs differently, and not necessarily in an obvious way.
I'm sure you can think of many different ways this function could work.

The point is, how do you do this in Python?

For a long time, the answer was a bit awkward and didn't make you feel good about what you had written.
It would look something like this:

```python
def add_one(x):
    if type(x).__name__) == "int":
        # handle ints
    elif type(x).__name__) == "str":
        # ...
```

Matching strings directly to class names of types is not great.
You might get errors from misspelling them, or the names might changes in a later version.
This is before we even start looking at custom classes and inheritance.

# Singledispatch

Then came Python 3.4 and [`singledispatch`](https://www.python.org/dev/peps/pep-0443/), a [decorator](https://realpython.com/primer-on-python-decorators/) which allows you to create multiple versions of a function which expect different types.
This is often referred to as [function overloading](https://en.wikibooks.org/wiki/Computer_Programming/Function_overloading).

## Example

To carry on with our `add_one` example, here is how we can use `singledispatch` to help us.

Firstly, import `singledispatch` from the [`functools`](https://docs.python.org/3/library/functools.html) package and create a default implementation of our function, decorated with `singledispatch`:

```python
from functools import singledispatch

@singledispatch
def add_one(x: any) -> any:
    return x + 1
```

This registers the `add_one` name to a register kept by `singledispatch`.
It will be our default implementation and to make this clear, we have type hinted that it will accept any and could return any.

Next, we can start implementing some more specific versions of the function. We do this by registering them to the function name we have previously registered, and using type hints to specify the input type:

```python
@add_one.register
def _(x: int) -> int:
    return x + 1

@add_one.register
def _(x: str) -> str:
    return x + "1"

@add_one.register
def _(x: list) -> list:
    return x + [1]
```

Note that because we are registering these functions to a specific function name, the name they are given next to `def` will not be used by us at runtime.
It is common in Python to [use the underscore](https://stackoverflow.com/questions/5893163/what-is-the-purpose-of-the-single-underscore-variable-in-python) to note variable names you are not interested in and that is exactly what we are doing here, just for functions.

This gives us the output we were looking for:

```bash
>>> from singledispatch_examples import *
>>> add_one(2)
3
>>> add_one("two")
'two1'
>>> add_one([1, 2, 3])
[1, 2, 3, 1]
```

Importantly, our code is now very clear about what it is doing, and uses Python classes to perform the evaluation, rather than the string name of the class.
Under the surface, the implementation of `singledispatch` does still look at the class names, but it does it in a much more controlled manner.

## Dispatching Custom Classes

To investigate this more closely, lets consider some new classes which we create:

- A - has a value
- B - inherits from A, has a value and a name

It would be tiresome to implement our `add_one` function for all of our classes and subclasses, especially when we want them to do the same thing.
So, `singledispatch` allows us to define it just for the base class, and when we call with subclasses, it will move up the class hierarchy to find the most specific function call.

Let's define our classes and an implementation of `add_one` for A:

```python
class A:
    def __init__(self, value):
        self.value = value

class B(A): # Inherits from A
    def __init__(self, value, name: str):
        self.value = value
        self.name = name

@add_one.register
def _(x: A) -> A:
    return A(x.value + 1)
```

This seems like it worked well:

```bash
>>> a = A(9)
>>> a1 = add_one(a)
>>> a1.value
10
>>> b = B(4, "B4")
>>> b1 = add_one(b)
>>> b1.value
5
```

However, we need to remember that `b1` is an instance of A, not an instance of B.

We could also provide this functionality as a method of A, which uses the `singledispatch` function we have already defined:

```python
class A:
    def __init__(self, value):
        self.value = value

    def add_one(self):
        self.value = add_one(self.value)
```

## singledispatchmethod

Having looked at `singledispatch` and custom classes, it is natural to wonder how we could combine them, to define methods on classes which act differently depending on the input.

This functionality has been provided in the very latest [release of Python](https://docs.python.org/3/whatsnew/3.8.html), as of this blog post.
The [`singledispatchmethod`](https://docs.python.org/3/library/functools.html#functools.singledispatchmethod) allows overloading of methods within a class, using the same method we have shown before.
Just import `singledispatchmethod` and it will check the second parameters of your method - the second one should be `self`.

Let's provide a new class, C, which has a value and an `add` method which behaves differently depending on what input you call it with:

```python
class C:
    def __init__(self: int, value):
        self.value = value

    @singledispatchmethod
    def add(self, x):
        raise TypeError("Please use an input of int, str or list")

    @add.register
    def _(self, x: int) -> int:
        return x + self.value

    @add.register
    def _(self, x: str) -> str:
        return x + str(self.value)

    @add.register
    def _(self, x: list) -> list:
        return x + [self.value]
```

Using it gives this output:

```bash
>>> c1 = C(5)
>>> c1.add(6)
11
>>> c1.add("6")
'65'
>>> c1.add([6])
[6, 5]
```

and raises a `TypeError` when one of the types which is implemented has not been called.

This gives us a lot of control over using input types to trigger certain function calls, even combining them with our own custom classes.

Let's look at a more complex example.

# Maybe

Maybe is a big thing in Haskell.
It certainly is a big thing when you are _learning_ Haskell.
Maybe lets you tell the program that you are going to have a value, you just aren't sure until you run it whether it will be _Just a value_ or _Nothing_.

If this doesn't sound tremendously useful to you, think about whenever you have written a Python function which sometimes returns a value, and sometimes doesn't.
This is all well and good while you are writing the function, but when you integrate it into a more complex series of functions, suddenly the program is trying to read from a value which doesn't exist. Because you never returned it.

So you start checking for whether the value is `None` or not before using it in function calls. This is fine, but the people who made Haskell wanted something cleaner, so they made Maybe.

I like Maybe. So I recreated it, to a certain degree, in Python, using `singledispatch`.

## Simple Example

All examples can be found in [maybe_examples.py](https://github.com/TimGuite/python_maybe/blob/master/maybe_examples.py)

Here we have a simple function which returns _Just x_ when x is greater than 5 and _Nothing_ otherwise:

```python
def f1(x: int) -> Maybe:
    if x > 5:
        return Just(5)
    else:
        return Nothing
>>> f1(3)
Nothing
>>> f1(3) == Nothing
True
>>> f1(8)
Just 8
>>> f1(8) == Just(8)
True
```

## Implementation

To implement this, there is a base class called Maybe. It does nothing except exist.

It has two subclasses, Just and \_Nothing. \_Nothing has a private name because in general use I wanted to be able to use the Haskell style `Nothing` rather than having to create an instance every time, `Nothing()`. I will use Nothing in place for the remainder of the post.

Both of these subclasses override the `__eq__` method and allow this to be registered with `singledispatchmethod`.
Unfortunately, at the moment, you cannot use a class as a type hint within its own definition.
I think there is a plan to change this in the future but meant a work around was needed for the equality check, which should only allow Just and Nothing objects to be compared, not any other types.

It turns out that you can access this function from outside the class definition, the same way you would when mocking a function. This isn't particularly pretty, but it does work:

```python
@Just.__eq__.register
def _(self, other: Just) -> bool:
    return fromJust(self) == fromJust(other)


@Just.__eq__.register
def _(self, other: _Nothing) -> bool:
    return False
```

As the default definition in the class raises an error, we have narrowed the possibility for calling this function down to Just and Nothing, as desired.

## Parameters Order

The Maybe package in Haskell defines some helper functions which work well with the Maybe type.
It would be nice to be able to fully replicate these functions, but many of them have the Maybe value appearing as the second parameter, not the first.

As it stands, the `singledispatch` decorator only allows you to check type on the _first_ parameter to the function.
So, to perform a check on the _second_ parameter, I applied a wrapper function, which serves only to swap the parameter order, and hid the inner function with a leading underscore:

```python
@singledispatch
def _maybe(m, f, default_value):
    raise TypeError("Call with Maybe value")


@_maybe.register
def _(m: Just, f: callable, default_value: any) -> any:
    return f(fromJust(m))


@_maybe.register
def _(m: _Nothing, f: callable, default_value: any) -> any:
    return default_value


# Move parameters around
def maybe(default_value, f, m):
    return _maybe(m, f, default_value)
```

Again, this is not ideal but it is an implementation detail which an external user would be unlikely to see, and it works as they would expect.

## Dispatching Lists

It is not clear how to use type hinting with `singledispatch` for lists of values.
[The Typing package provides List](https://docs.python.org/3/library/typing.html#typing.List), but this does not seem to work well yet with `singledispatch`. Perhaps this will be figured out in the future.

In the meantime, some functions which should only accept lists of a certain value, will actually just accept a list:

```python
@singledispatch
def catMaybes(_):
    raise TypeError("Use on a list of Maybe values")


@catMaybes.register
def _(m: list) -> List[any]:
    """Not ideal but cannot specify a list of Maybes"""
    try:
        return [fromJust(x) for x in m if isJust(x)]
    except TypeError:
        raise TypeError("Please run on a list of Maybes")
```

# Summary

I was quite surprised when I found out about `singledispatch` because I hadn't expected to find something so centred on types hanging out in a core Python package.

This was an interesting project to learn a bit more about how to use it and what it's limitations are. When writing a library which you expect to be used by many other people, or even yourself, it could be a useful tool to validate inputs, or to clearly overload functions based on input type.

Using the Zen of Python approach, the default implementation should probably do something useful, rather than just raise an error, and then more specific implementations can make more accurate judgements about the class of the input type.

There are several packages available for dispatching on more than one parameter, such as [multimethod](https://pypi.org/project/multimethod/), but I'm not sure how close or far they are from being accepted in the core packages like `singledispatch` is.
Doing so would provide Python with a type system of sorts, living alongside the dynamic typing which is usually used when first teaching.
This might make things more complicated and I don't know how well it would all work.
If you're going to add types and extra packages to provide that functionality, would you be better served by using another language?
Will mypy be able to keep up with these changes well enough to provide you with meaningful output **before** your program crashes at runtime?
Questions for another day!

Once again, all of the working code discussed and the main _maybe.py_ module can be found on my Github: https://github.com/TimGuite/python_maybe

## Thanks for reading!
