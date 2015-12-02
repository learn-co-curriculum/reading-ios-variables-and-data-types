# Variables: Primitives & Objects

## Objectives

1. Connect the basic nature of variables in programming to variables in algebra.
2. Declare and define a variable.
3. Redefine an existing variable, and redefine it using itself.
4. Recognize the basic distinction between objects and primitives, and the role of `*` ("star") in variable declarations.


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

A useful nature of redefinitions is that a variable can be used in its own redefinition:

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

A string is a type of object which is used to store and manipulate text. We've already seen that the string literal can be used in conjunction with `NSLog()` to print directly to the console:

```objc
NSLog(@"%@", @"Welcome to the Flatiron School!");
```
This will print: `Welcome to the Flatiron School!`.

In Objective-C, we can also capture a string value into a variable that is of the `NSString` type. This is because the string literal that we've been using implicitly creates values of the `NSString` type. We can create a string *variable* in much the same way as creating an integer variable, however, since strings are *objects*, their declaration syntax requires a `*` ("star") between the type name and the variable name:

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
```
**Advanced:** *The use of a* `*` *generates a pointer reference. Instead of pointing to a memory location which holds a value, a pointer reference is a location in memory which holds the memory address of another variable's value, or the addresses of a set of other variables' values. [Further Reading](http://www.drdobbs.com/mobile/pointers-in-objective-c/225700236)*

We'll cover in detail the distinction between objects and primitives in a later topic on Object-Oriented-Programming. For now, just recognize that objects hold values and can change them through behaviors called "methods", while primitives just hold a value. Because of this, primitives **do not** employ the `*` in the their declaration syntax.

**Note:** *Assigning an integer to a variable of type* `NSInteger *` *will cause the compiler to generate an* `Incompatible integer to pointer conversion` *warning. The same goes for declaring any of the data types. This syntax does serve a purpose so the language permits it, but your application won't do what you expect.*

While you can reference the complete list of [Foundation Data Types](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Miscellaneous/Foundation_DataTypes/index.html#//apple_ref/doc/c_ref/NSTimeInterval) here, the primitives with which you'll interact the most are:

```objc
NSInteger
NSUInteger
CGFloat
BOOL
```
Most other variables you create will be objects.

## Code Commenting

Comments are text that the compiler is told to ignore. They're useful for inserting notes to yourself or to other programmers about the code. There a couple of different syntaxes that you might see:

```objc
// A line comment is declared with two slashes and comments out
// all the text to the right of the slashes.
```

```objc
/*
A block comment will comment-out all the text between 
its opening and closing symbols. They use a slash and star 
to open, and a star and slash to close.
*/
```

Commenting is useful for documenting behavior that isn't immediately obvious, but it is not a substitute for well-written code. Learn to keep your commenting to a minimum and use the code itself to document your intent.

### Choose Descriptive Variable Names Instead

Don't rely on comments to document how a variable is meant to be used; use the variable name itself! 

```objc
// avoid shorthand variable names with comment explanations

NSInteger w = 12; // 12 weeks in the course
NSInteger d = w * 5; // days in the course is weeks times 5
```

You can rely on Xcode's autocomplete tool to fill in the bulk of variable names once you've declared them, so don't be afraid of being somewhat verbose:

```objc
// use descriptive variable names

NSInteger weeksInCourse = 12;
NSInteger daysInCourse = weeksInCourse * 5; // five days in a course week
```
#### Avoid "Magic Numbers"

While we chose good names for the variables above, there's still a small problem with that code snippet: the "magic number" `5`. "Magic numbers" are values in the code that have no reference to their origin or intent; we have to rely on the comment to understand what value this represents—if there even is a comment. It's best to save this value into a variable and use the variable name to document the nature of the value that it holds:

```objc
// use a variable to document a "magic number"

NSInteger weeksInCourse = 12;
NSInteger daysPerWeekInCourse = 5;
NSInteger daysInCourse = weeksInCourse * daysPerWeekInCourse;
```
Now we can read the code itself and know what the values mean. Then, if we have another use for these variables but need to change the values, such as when describing a weekend course, we can change the values instead of the "magic numbers":

```objc
// changing variables' values documents itself

NSInteger weeksInCourse = 4;
NSInteger daysPerWeekInCourse = 2;
NSInteger daysInCourse = weeksInCourse * daysPerWeekInCourse;
```

<a href='https://learn.co/lessons/reading-ios-variables-and-data-types' data-visibility='hidden'>View this lesson on Learn.co</a>
