# C++ FUNCTIONS EXPLAINED

> In yet another explanation, we will go over what "functions" are in c++

## Table of Contents

- [General](#general)
- [Numeric](#numeric)
- [Boolean](#boolean)
- [Void](#void)
- [Additional](#additional)

## General

Functions in c++ are essentially these snippets of code that work like their standalone machine\
Functions in c++ can be of different types just like variables\
Declaring usually looks like `type function_name(aguments) { execution; }`

Fun fact: the `int main(){}` part is actually a function of type _int_, which means that is must return an _int_ value\
That is why we write `return 0;` at the end of the "main" function\
C++ will search for the "main" function everytime you try to run it (doesn't matter if it's in a file with a different name)

_An example reflective of real like would be:_

- Your function is to keep stirring that bowl and return me the mixed up bowl
- A function takes two numbers, adds them together, and returns the user the sum of both numbers

As usual, I make one example that is closer to life and another that is closer to code\
As you can see, there isn't too much to be afraid of when approaching function\
Functions do make up a lot of code, though: you have entire libraries and "classes" consisting of functions (also called methods)\
We will go over "classes" soon enough, but they're essentially like a set of rules by which you define objects (containers of data)

_An example will illustrate how a function is declared:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string"

int main()
{
    // type function_name(arguments) { execution };

    int addition(int x, int y) { return x + y; }
    double division(double x, double y) { return x / y; }
    std::string print(const std::string &text) // You already know what "const" does, but we will go over referenced variables in a different explanation guide
    {
        std::string new_text = "You wrote: " + text;
        return new_text; // Type "std::string"
    }

    // I hope you get how the rest works

    return 0; // Returning "0" within the "main" function
}
```

## Numeric

Numeric-based functions are functions that return an integer type value after execution

_Move to cmath's pow and sqrt explanation here:_

- [cmath](#cmath)

_An example illustrating the usage of an int and double type functions will be shown below:_

```cpp
#include <iostream> // To use "std::cout"
#include <cmath> // This is the c++ "math" library, and I'll be using powers and square roots

int rectangle_area(int length, int width)
{
	// A = l * w
	return length * width;
}

double pythagorean(double leg_a, double leg_b)
{
    // c = sqrt(a^2 + b^2)
    double squared_sum = std::pow(leg_a, 2) + std::pow(leg_b, 2);
	double hypothenuse = std::sqrt(squared_sum);
	return hypothenuse;
}

int main()
{
	std::cout << "The hypothenuse of a right triangle with legs 5 and 12 is " << pythagorean(5.0, 12.0) << std::endl; // To pass onto a new line
	std::cout << "The area of a rectangle with length 5 and width 3 is " << rectangle_area(5, 3);

    return 0;
}
```

### Cmath

Cmath is an official library made to be used in C++ (They use math.h in C)\
It's a pretty big library, but we will only go over "pow" and "sqrt"\
_An example illustrating both will be provided below:_

```cpp
#include <iostream> // To use "std::cout"
#include <cmath> // To use "std::pow" and "std::sqrt"

int main()
{
    // std::pow(double var, int var);
    double power = std::pow(4.0, 2); // "power" will, now, store a double type number "16.0" because 4 ^ 2 = 16

    // std::sqrt(float or double var);
    double square_root = std::sqrt(81.0); // "square_root" will, now, store a double type number "9.0" because sqrt(81) = 9

    std::cout << "4 to the power of 2 is " << power << std::endl;
    std::cout << "The square root of 81 is " << square_root;

    return 0;
}
```

## Boolean

Boolean functions (I call them logic functions) can only return a true or false statement\
This equates to them only being able to return 1 for true and 0 for false

_An elaborate example will go over to use boolean functions:_

```cpp
#include <iostream> // To use "std::cout"

bool is_prime(int number)
{
	bool prime = true; // The conditon that the number is a prime number; it's initially set to true since we're trying to prove that the number provided is not prime

    // We will only take positive integer values (and those that don't exit the 32 bit int limit)
    if (number <= 1 || number > 2147483647)
    {
        prime = false; // This will make any negative number with the except of 1 and numbers above the 32-bit int limit return false
    }

    // We will check if a number is prime by using modulo equations and a for loop
    for (int i = 2; i <= number / 2; ++i)
	{
    	if (number % i == 0)
		{
      	prime = false;
      	break;
   		}
  	}

	return prime; // Returns true if it was impossible to prove that the number variable stored a non-prime number
}

int main()
{
    is_prime(11) ? std::cout << " true\n" : std::cout << " false\n"; // The usage of "?" here is a ternary statement, which basically means is "condition ? if it worked : if it failed"

    return 0;
}
```

## Void

Non-return type functions (alternatively, void functions) are functions that don't return any value after execution\
This can be a function that only writes text without returning any value\
It's a pretty common type of function, and the main thing that goes for it is the returning of nothing (void)

_An example illustrating a void function will be shown below:_

```cpp
#include <iostream> // To use "std::cout" and "std::cin"
#include <limits> // To clear the buffer in-between prompts

void subtraction()
{
    int x, y;
    std::cout << "Input the value of the first number: ";
    std::cin << x;
    std::cin.ignore(std::numeric_limits<std::steamsize>::max())
    std::cout << "Input the value of the second number: ";
    std::cin << y;
    int difference = x + y;
    std::cout << "The difference of " << x << " and " << y << " is " << sum << std::endl;
}

int main()
{
    subtraction(); // An entirely flexible void type function that prompts the user to input 2 numbers and subtracts them from each other

    return 0;
}
```

## Additional

In this section, I will include the other types of functions that exist\
The reason I moved them to "additonal" is because they're usually less significant that the logic-intensive numeric, boolean, and void function types\
Nonetheless, you'll still find plenty of use cases for a char or even std::string type function

_An example illustrating a "std::string" function will be provided below:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string

std::string greeting_sentence(const std::string &name) // Again, we'll go over this soon in the pointer exaplanation guide
{
    std::string greet = "Hello, " + name + "!";
    return greet; // This one's a very basic function, but I'm just trying to give you the idea of how it would work
}

int main()
{
    std::string greeting_a_friend = greeting_sentence("Jared");
    std::cout << greeting_a_friend; // Hello, Jared!

    // I won't include a char type function, but basically, they're sometimes used in logic and don't really have many use cases when it comes to fun

    return 0;
}
```
