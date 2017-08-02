## Chapter 1 - Overview

Type-driven development is a style of programming in which we write types first first and use those types to guide definition of functions. This introduces the concept of _dependent types_.

**Dependent types example**
- Matrix arithmatic - encoding matrices dimension in types
- ATM - encoding the state (like FSM) into types
- Concurrent programming - model how processes should interact

Process of type-driven development includes,
- _Type_, Write _Matrix_ data type and use it as input and output for an addition function
- _Define_, Write an addition function that satisfies its input and output types
- _Refine_, Refine the the types to be more precise by encoding its dimension

#### Pure functions and referential transparency
The same input always produce the same output. An expression (such as a function call) in a function is referentially transparent if it can be replaced with its result without changing the behavior of the function.

Of course, in real world we have side effects and a programming language that can only do pure functions are useless. In Idris, pure functions may not be able to perform side effects, but they can _describe_ it.

#### Partial and total functions
*Total function* is guaranteed to produce a result, it will return a value in finite time for every possible well-typed input and it's guaranteed not to throw any exceptions. Idris checks for total function by checking if a function terminates for _all_ inputs (halting problem).

#### First-class types
A _first-class_ language construct is one that's treated as a value, with no syntatic restrictions on where it can be used. In other words, a first-class construct can be passed to functions, returned from functions, stored in variables and so on.

For example, you can't do this in Java, `x = int`. In Idris you can (syntax is obviously different, but you get the idea). 

You can even write functions that compute types, and the return type of a function can differ depending on the input _value_ to a function.

```Idris
-- This is a type!
StringOrInt : Bool -> Type
StringOrInt x = case x of
                  True  => Int
                  False => String
```
