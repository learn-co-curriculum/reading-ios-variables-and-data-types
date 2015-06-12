# Variables: Primitives & Objects
----

## Objectives

1. Understand the basic nature of variables.
2. Learn how to declare and define a variable.
3. Understand the basic distinction between objects and primitives, and the role of `*` ("star") in variable declarations.


## What is a Variable?

In the most general sense, a **variable** is a quantity which can change in value. For those who can think back to school math class, the comparison to algebra and geometry is helpful here. Let's take a look at the equation for the Pythagorean Theorum:

*a*<sup>2</sup> + *b*<sup>2</sup> = *c*<sup>2</sup>

OR

*c* = √(*a*<sup>2</sup> + *b*<sup>2</sup>)

The equation itself is unintelligible without understanding what it represents: *The sum of the squares of the lengths of the two shorter sides of any right triangle is equal to the square of the length of the hypotenuese (the longest side of the triangle).*

The letters *a*, *b*, and *c* are variables which represent the values of the lengths of the sides of the right triangle. Understanding the context of this equation, we can set the known variables so we can calculate the value of the unknown one.

## Creating a Variable

In programming, a **variable** is any value or set of values that a programmer assigns which can later be recalled through the variable's name. Let's start with Objective-C's integer class `NSInteger`. Creating a variable is done in two steps:

* **Declaring** the variable means establishing the variable's class and name, which should be unique and descriptive:

```objc
NSInteger sideA;
```

* **Defining** the variable means **setting** its value, the syntax of which usually involves an `=` ("equal sign"):

```objc
sideA = 3;
```

These two steps can be combined into a single statement which can look like this:

```objc
NSInteger sideB = 4;
```
You can also define a variable based upon the values of other variables in your program. So to find the result of Pythagorus' Theorum, we can define the hypotenuese like this:

```objc
NSInteger sideC = sqrt( pow(sideA, 2) + pow(sideB, 2) );
```
In our case here, if `sideA` has the value `3` and `sideB` has the value `4`, then `sideC` will result to the value `5`. We can verify this through the [special trigonometry](http://en.wikipedia.org/wiki/Special_right_triangles) of the 3:4:5 Right Triangle.

**Note:** *You will occasionally encounter situations in which you'll need to declare a variable and wait to define it until later, but usually you'll be declaring and setting variables on the same line.*

## Varying a Variable
Just as easily as we can assign a value to a variable name, we can *re-assign* a different value to that variable name. In Objective-C **it has to be a value of the same type**. In our case, this means keeping with `NSInteger`.

```objc
sideA = 5;
sideB = 12;
```

Because we set `sideC` to the equation by referencing `sideA` and `sideB`, and because 5:12:13 is another Pythagorean Triple, `sideC` will now result to the value `13`.

## Primitives vs. Objects

Variables can be of many types: strings, arrays, numbers, dictionaries, and many more. The types of variables which refer only to a value are referred to as "**primitives**". This is because, unlike objects, primitives are unable to perform behaviors on the values that they reference. Subsequently, an object is a variable which can refer to one or many values that it can itself perform actions upon (these actions are called "**methods**").

A string is a type of object which is used to store and manipulate text. In Objective-C, the base string class is `NSString`. We can create a string variable in much the same way as creating an integer variable.

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
```
You will notice, however, that unlike declaring our `NSInteger` variables earlier, declaring our `welcome` string requires a `*` ("star") between the class name and the variable name. This is Objective-C's syntax for creating a pointer reference.

**Advanced:** *Instead of pointing to a memory location which holds a value, a pointer reference is a location in memory which holds the memory  address of another variable's value, or the addresses of a set of other variable's values. [Further Reading](http://www.drdobbs.com/mobile/pointers-in-objective-c/225700236)*

We'll cover in detail the distinction between objects and primitives in a later topic on Object-Oriented-Programming. For now, just recognize that objects hold values and can change them through behaviors called "methods", while primitives just hold a value.

This is because `NSString` is an object type (we'll cover in depth what this means in the next topic). Objects require a pointer reference (the `*`) in their declaration because, well, they point to a set of values at a specific memory address in the computer's RAM. However, `NSInteger` is a primitive, or "data type", and is itself a value, rather than a pointer to a value or set of values.

**Note:** *Entering* `NSInteger *` *will cause the compiler to generate an* `invalid integer to pointer conversion` *warning. The same goes for declaring any of the data types. This syntax does serve a purpose so the language permits it, but your application won't do what you expect.*

While you can reference the complete list of [Foundation Data Types](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Miscellaneous/Foundation_DataTypes/index.html#//apple_ref/doc/c_ref/NSTimeInterval) here, the primitives with which you'll interact the most are:

```objc
NSInteger
NSUInteger
CGFloat
BOOL
```
Most other variables you create will be objects. The next reading will discuss string objects and string formatting in more detail.
