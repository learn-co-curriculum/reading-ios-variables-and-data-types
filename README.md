# Variables: Primitives & Objects
----

## Objectives

1. Understand the basic nature of variables.
2. Learn how to declare and define a variable.
3. Understand the basic distinction between objects and primitives, and the role of `*` ("star") in variable declarations.


## What is a Variable?

In the most general sense, a **variable** is a quantity which can change in value. For those who can think back to school math class, the comparison to algebra is helpful here. Let's take a look at an equation representing simple arithmetic:

*a* + *b* = *c*

The letters *a*, *b*, and *c* are variables—placeholders for some associated value. If we know the values of *a* and *b*, we can calculate the value of *c*.

## Creating a Variable

In programming, a **variable** is any value or set of values that a programmer assigns which can later be recalled through the variable's name. Let's start with Objective-C's integer class `NSInteger`. Creating a variable is done in two steps:

* **Declaring** the variable means establishing the variable's class and name, which should be unique and descriptive:

```objc
NSInteger a;
```

* **Defining** the variable means **setting** its value, the syntax of which usually involves an `=` ("equal sign"):

```objc
a = 1;
```

These two steps are almost always combined into a single statement which can look like this:

```objc
NSInteger b = 2;
```
**Note:** *You will occasionally encounter situations in which you'll need to declare a variable and wait to define it until later, but usually you'll be declaring and setting variables on the same line.*

You can also define a variable based upon the values of other variables in your program. So to find the value of *c* having already defined `a` and `b`, we can create another variable called `c` and define it as the result of adding `a` and `b` together;

```objc
NSInteger c = a + b;
```
In the current case, `c` will be set to the value of `3`. However, if were to change either `a` or `b`, their new sum would be captured into `c`:

```objc
NSInteger a = 2;
NSInteger b = 4;

NSInteger c = a + b;
```
The variable `c` will now represent the value `6`.

## Varying a Variable
Just as easily as we can assign a value to a variable name, we can *re-assign* a different value to that variable name. In Objective-C **it has to be a value of the same type**. In our case, this means keeping with `NSInteger`.

```objc
NSInteger a = 1;
NSInteger b = 2;

NSInteger c = a + b;

a = 2;
b = 4;
```
You'll notice that we don't write `NSInteger` again after the variable has been declared. This is called "redefining" a variable. It's important to note, however, that `c` will not automatically update itself to reflect the new values of `a` and `b`; unless `c` is directly redefined, its value will remain at `3`.

A useful nature of redefitions is that a variable can be used in its own redifinition:

```objc
NSInteger a = 1;

a = a + 1;
```
Now `a` will hold the value `2`.

```objc
a = a * a;
```
And now it will hold the value `4`.

## Primitives vs. Objects

Variables can be of many types: strings, arrays, numbers, dictionaries, and many more. The types of variables which refer only to a value (such as `NSInteger`) are referred to as "**primitives**". This is because, unlike the other variable types called "**objects**", primitives are unable to perform behaviors on the values that they reference. Subsequently, an object is a variable which can refer to one or many values that it can itself perform actions upon (these actions are called "**methods**"). 

A string is a type of object which is used to store and manipulate text. In Objective-C, the base string class is `NSString`. We can create a string variable in much the same way as creating an integer variable.

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
```
You will notice, however, that unlike declaring our `NSInteger` variables earlier, declaring our `welcome` string requires a `*` ("star") between the class name and the variable name. This is Objective-C's syntax for creating an object.

**Advanced:** *The use of a* `*` *generates a pointer reference. Instead of pointing to a memory location which holds a value, a pointer reference is a location in memory which holds the memory address of another variable's value, or the addresses of a set of other variables' values. [Further Reading](http://www.drdobbs.com/mobile/pointers-in-objective-c/225700236)*

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
