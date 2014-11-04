#
#Objective-C Reference Guide

##Intro to Variables
We can print a string or a number to the console using `NSLog`. Let's print a
greeting:

```objc
NSLog(@"Welcome to The Flatiron School!");
```

What if we need to greet 3 people in succession as they walk through the door?

```objc
NSLog(@"Welcome to The Flatiron School!");
NSLog(@"Welcome to The Flatiron School!");
NSLog(@"Welcome to The Flatiron School!");
```

So we just had to type in (or copy) the same thing 3 times. What happens when we have to greet 100
people? It'd be nice to store the string "Welcome to The Flatiron School!" in
the computer's memory. We can do this by giving our string a name, also known
as a variable. Then we can *assign* our string to our *variable*.

```objc
NSString *greeting = @"Welcome to The Flatiron School!";

NSLog(greeting); // prints Welcome to The Flatiron School!
NSLog(greeting); // prints Welcome to The Flatiron School!
NSLog(greeting); // prints Welcome to The Flatiron School!
```

Using variables makes working with data much easier for us. Previously, if we wanted to add to our greeting, we would have to type out the whole new NSString, making our previous work useless. Using variables, we can do this instead:

```objc
NSString *greeting = @"Welcome to The Flatiron School!";

NSLog(@"Hi, my name is Chris! @", greeting); // prints Hi, my name is Chris! Welcome to the Flatiron School!
```

Just as easily as we can assign a value to a variable, we can *reassing* a different value to that variable. In Objective-C, it has to be data of the same type, i.e. NSString in this case.

```objc
NSString *greeting = @"Welcome to The Flatiron School!";

greeting = @"¡Hola! Bienvenidos a la Escuela de Flatiron!"; // greeting is now equal to the Spanish greeting
greeting = 5; // this results in a compiler error: Implicit conversion of 'int' to 'NSString *' is disallowed with ARC. This means that 5 is of type 'int' and it needs to be of type NSString
```

These examples use NSStrings, but variables can hold all kinds of different values, as we'll see in the following sections. Here are some examples of different data types being assigned to variables:

```objc
int x = 1;
NSInteger y = 2;
NSString *name = @"Joe";
BOOL isProgramming = YES;
CGFloat price = 4.50;
float change = 2.00;
```

##Data Types 
- **int, NSInteger**
  - Integers; 1, 5, 500, 1000
  - `int` is typically used as a control loop variable, i.e. `for (int count = 0; count < [array length]; count++)`
	- `NSInteger` will determine the size of the variable based on processor architecture so you don't have to. As this maintains data integrity when passing a value as an argument to or a return value from a function, use of NSInteger outside of control loop variables is encouraged.
- **float, double, CGFloat**
	- Rational Numbers; 1.2, 3.14, 33.3333
	- A double has 2x the precision of a float. Float is 32-bit while double is 64-bit
	- `CGFloat` will determine the size of the variable based on processor architecture so you don't have to. It is the rational number version of `NSInteger`
- **BOOL**
	- `YES` or `NO`, 1 or 0
	- `nil` == 0 == `NO`
	- Logging:
		- `NSLog(@"isReadyBool value is %d", isReadyBool); //prints 0 or 1`
		- `NSLog(@"isReadtBool value is %@", isReadyBool ? @"True" : @"False"); //prints True or False`
- **id**
  - The id type is a generic type for any Objective-C object, similar to C's void pointer. Because the id type stores a *reference* to any type of object, it automatically implies that the variable is a pointer and so the `*` is not necessary.
  - `id car = [[FISCar alloc] init];`

##Declaring Variables

- Variables let us store values for future use. We can declare a variable by
  stating its type followed by a its name:

	```objc
	int count;
	```

- And we can subsequently set the variable's value, or we can accomplish this
all in one line.

	```objc
	count = 3;
	BOOL counting = YES;
	```

- **Ampersands (&) and Stars (*)** 
  - `&` is the **reference operator**. The reference operator gives us the
    memory "address of" a variable. This can be read as "address of".
	
		```objc
		int x = 5;
		NSLog(@"The memory address of variable x is: %p", &x);
		NSLog(@"The value of variable x is %d", x);

		```
  - `*` in the declaration of a pointer just means that the variable is a pointer. This will be seen with all objects in Objective-C, with the exception of the *id* type as being a pointer is implied.

