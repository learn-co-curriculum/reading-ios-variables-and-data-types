# Objective-C Variables
----

## Objectives

1. Understand the basic nature of instance variables.
2. Learn how to declare and define an instance variable.
3. Understand that instance variables can reference other variables.

## What is a Variable?

In the most general sense, a **variable** is a quantity which can change in value. For those who can think back to school math class, the comparison to algebra and geometry is helpful here. Let's take a look at the equation for the Pythagorean Theorum:

*a*<sup>2</sup> + *b*<sup>2</sup> = *c*<sup>2</sup>

OR

*c* = √(*a*<sup>2</sup> + *b*<sup>2</sup>)

The equation itself is unintelligible without understanding what it represents: *The sum of the squares of the lengths of the two shorter sides of any right triangle is equal to the square of the length of the hypotenuese (the longest side of the triangle).*

The letters *a*, *b*, and *c* are variables which represent the values of the lengths of the sides of the right triangle. Understanding the context of this equation, we can set the known variables so we can calculate the value of the unknown one.

## Creating an Instance Variable

In programming, an **instance variable** is the value that a programmer assigns which can later be recalled through the instance variable's name. Let's start with Objective-C's integer class `NSInteger`. Creating an instance variable is done in two steps:

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
NSInteger sideC = sqrt(sideA^2 + sideB^2);
```
In our case here, if `sideA` has the value `3` and `sideB` has the value `4`, then `sideC` will result to the value `5`. We can verify this through the [special trigonometry](http://en.wikipedia.org/wiki/Special_right_triangles) of the 3:4:5 Right Triangle.

**Note:** *You will occasionally encounter situations in which you'll need to declare a variable and wait to define it until later, but usually you'll be declaring and setting variables on the same line.*

## Varying a Variable
Just as easily as we can assign a value to a variable name, we can *re-assign* a different value to that variable name. In Objective-C **it has to be data of the same type**. In our case, this means keeping with `NSInteger`.

```objc
sideA = 5;
sideB = 12;
```

Because we set `sideC` to the equation by referencing `sideA` and `sideB`, and becuase 5:12:13 is another Pythagorean Triple, `sideC` will now result to the value `13`.

## String Variables

Variables can be of many types: strings, arrays, numbers, dictionaries, and many more. Strings are a data type used to store and manipulate text. In Objective-C, the string class is `NSString`. We can create a string variable in much the same way as creating an integer variable.

```objc
NSString *welcome = @"Welcome to the Flatiron School!";
```
**Note:** *Declaring a string variable requires a* `*` *("star") between the class name and the variable name. This is because* `NSInteger` *is a* ***primitive*** *type, while* `NSString` *is an* ***object*** *type. This distinction is a part of the Objective-C syntax that we'll explain later.*

The next reading will discuss strings and string formatting in more detail.
