#Objective-C Variables Guide

## Wait, Where Do I Type This?

We have to type this code somewhere! Issue is, how does XCode know where to start running code? By default, iOS will run any code that is inside the `didFinishLaunchingWithOptions` method in **AppDelegate.m** (you'll also often see 'FISAppDelegate.m' in labs). **Put your code between the two curly braces of this method.** 

Last, sometimes output (printed in the 'console') is hidden because the bottom window (the debugger window) is hidden. To show the debugger either press the keyboard shortcut command+shift+y or press the "Show Debug Area" button on the top right. 

##Intro to Variables
We can print strings to the console using `NSLog`. Let's print a greeting:

(*note: strings in objective-c are text surrounded by quotes and started with an @ symbol, like this:* **@"i am a string"** *)*

```objective-c
NSLog(@"Welcome to The Flatiron School!");
```
Enter that into your `didFinishLaunchingWithOptions` method and hit command+R. You should see your greeting in the console. Cool!

What if we need to greet 3 people in succession as they walk through the door? Try:

```objective-c
NSLog(@"Welcome to The Flatiron School!");
NSLog(@"Welcome to The Flatiron School!");
NSLog(@"Welcome to The Flatiron School!");
```

That works, but we just had to type in (or copy) the same thing 3 times. What do we do when we have to greet 100
people? Wouldn't it be nice to store our string in
the computer's memory so we can easily access it whenever we want? 

We can do this by giving our string a name, also known
as making it a **variable**.

```objective-c
NSString *greeting = @"Welcome to The Flatiron School!";

NSLog(greeting); // prints Welcome to The Flatiron School!
NSLog(greeting); // prints Welcome to The Flatiron School!
NSLog(greeting); // prints Welcome to The Flatiron School!
```

Using variables makes working with data much easier for us. Previously, if we wanted to add to our greeting, we would have to type out a whole new NSString. Now that we've stored it in a variable, we can easily re-use it!

##Creating Variables
So we just saw how to create a string variable. Let's break down variable creation.

- First, lets **declare** a variable by stating its type followed by its name:

	```objective-c
	NSInteger count;
	```

- Once it's declared, we can subsequently **set** the variable's value.

	```objective-c
	NSInteger count;
	count = 3;
	```
- That's cool, but we can also do it all at once on the same line!

	```objective-c
	NSInteger count = 3;
	```
*Note: You will encounter times where you'll need to simply declare a variable for later. Usually though, you'll be declaring and setting variables on the same line.*

## Varying Variables
Just as easily as we can assign a value to a variable, we can *re-assign* a different value to that variable. In Objective-C, **it has to be data of the same type**, i.e. NSString in this case.

```objective-c
NSString *greeting = @"Welcome to The Flatiron School!";

greeting = @"¡Hola! Bienvenidos a la Escuela de Flatiron!"; 
// greeting is now equal to the Spanish greeting :D

greeting = 5; // this results in a compiler error :(
// "Implicit conversion of 'int' to 'NSString *' is disallowed." 
// This means 'greeting' must be an NSString, so 5 (int) won't work.
```
These examples use NSStrings, but variables can hold all kinds of different values, as we'll see in the following sections. Here are some examples of different data types being assigned to variables:

```objective-c
int x = 1;
NSInteger y = 2;
NSString *name = @"Joe";
BOOL isProgramming = YES;
CGFloat price = 4.50;
float change = 2.00;
```

#### **More on Stars (*)**

-  `*` in the declaration of a variable means that the variable is actually just a **pointer**, as in its simply a name that *points* to the data its been assigned to. 
-  This will be seen with all objects in Objective-C, with the exception of the **id** type as being a pointer is implied. (more on that later)
-  Numbers (*with the exception of* `NSNumber`) are considered 'primitive types', and thus are not objects. For this reason, they do not need a pointer.
-  The vast majority of variables you'll create will be objects, so don't worry *too much* about stars :)

*Fun Fact: almost all 'primitive' types are types that exist in C, the very first programming language (and what Objective-C is built on top of)*

##More On Basic Data Types 
- **NSInteger**
  - Integers; 1, 5, 500, 1000
  - typically used as a control loop variable, i.e. `for (NSInteger count = 0; count < [array length]; count++)`
	- `NSInteger` will determine the size of the variable based on processor architecture so you don't have to. This maintains data integrity when passing a value as an argument to or a return value from a function. **tl;dr** — use NSInteger outside of control loop variables.
	- you may encounter code with `int`, the C version of an integer — avoid using it in your own code as it may cause errors
	- primitive type (does not require a * when declaring them)
- **float, double, CGFloat**
	- Rational Numbers; 1.2, 3.14, 33.3333
	- A double has 2x the precision of a float. Float is 32-bit while double is 64-bit.
	- `CGFloat` will determine the size of the variable based on processor architecture so you don't have to. It is the rational number version of `NSInteger`
	- all primitive types (none of these require a * when declaring them)
- **BOOL**
	- is either true or false, but written as `YES` or `NO`
	- can also be written as `1` or `0`
	- `nil` == 0 == `NO` (*meaning nil is considered false*)
	- Logging:
		- `NSLog(@"myBool value is %d", myBool); //prints 0 or 1`
	- primitive type (does not require a * when declaring them)

- **id**
  - The id type is a generic type for **any** Objective-C object, similar to C's void pointer. Because the id type simply stores a *reference* to any type of object, its automatically implied that the variable is a pointer, so the `*` is not necessary.
  - `id car = [[FISCar alloc] init];`

##Logging Variables with String Interpolation
Woah, that sounds awfully fancy. Remember before when we NSLog'd our greeting?

```objective-c
NSString *greeting = @"Welcome to The Flatiron School!";

NSLog(greeting); // prints Welcome to The Flatiron School!
```
Well what if you wanted to say something else, as well your variable? 
Using variables, we can do this:

```objective-c
NSString *greeting = @"Welcome to The Flatiron School!";

NSLog(@"Hi, my name is Chris! %@", greeting); 
// prints Hi, my name is Chris! Welcome to the Flatiron School!
```
This is called *string interpolation* (don't worry about remembering the term), and what it means is that we can write an ordinary string and enter variables into it using *format specifiers*. 

**Format specifiers are simply placeholders.** They always start with a % and have a single character depending on what type of variable is being passed in. The format specifier we use for strings is `%@`, as shown in the example. 

Once a string has format specifiers in it, put a comma and list the variables that you want to enter as they appear in the string (in order!). So let's try it out:

```objective-c
NSString *myName = @"Tom";
NSInteger myAge = 24;

NSLog(@"My name is %@ and I am %ld years old.", myName, myAge);
// prints "My name is Tom and I am 24 years old." 
```
Here we see the `%@` gets replaced with `myName`, and the `%ld` gets replaced with `myAge`. 

Documentation on format specifiers [lives here](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/Strings/Articles/formatSpecifiers.html). You can take a look, but **don't worry about memorizing them** — the important part is that you're aware of how these placeholders work. Plus, XCode has built-in features to help with these, and you'll start to remember after you use them enough times. :)

---
This may be a lot to take in all at once, but the best part is **now you have everything you need to know to start using variables in Objective-C!**