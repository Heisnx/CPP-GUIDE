# C++ IF STATEMENTS AND FOR/WHILE LOOPS EXPLAINED

> This is a brief guide on c++ "if" statements and "for/while" loops\
> We will go over many interesting concepts

## Table of Contents

- [If Statements](#if)
- [For Loops](#for)
- [Cstdlib Library](#the-cstdlib-library)
- [While Loops](#while)

## IF

If statements in c++ are like conditions in real life

- If the weather is rainy tomorrow, I will not go out to the park
- If the integer variable named "a" is not equal to 5, output "a = 5" onto the console

The above two example illustrate how if statements are used in c++ as well as in most other coding languages such as Python and JavaScript\
_An example illustrating its usage in code will be provided below:_

```cpp
#include <iostream> // To use "std::cout" and "std::cin"
#include <limits> // This is to use numeric limits

int main()
{
    int first_number, second_number; // Variables can be declared in one line if their value is unspecified initially
    std::cout << "Input the value for the first number: ";
    std::cin >> first_number;
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n'); // This and the line above will clear the buffer to prevent input buffer errors and help provide a cleaner inputting experience; it's not really mandatory to understand what exactly this does
    std::cout << "Input the value for the second number: ";
    std::cin >> second_number;

    if (first_number > second_number)
    {
        std::cout << first_number << " is bigger than " << second_number << std::endl;
        /* The usage of "<<" in-between the variables and the text is like sticthing them together like we would do with a +
        The output will be "<first_number> is bigger than <second_number>" where the values inside of the "<>" are replaced with numbers*/
    }
    else if (first_number < second_number)
    {
        std::cout << first_number << " is less than " << second_number << std::endl; // This is an inverse of the first condition
    }
    else
    {
        std::cout << first_number << " is equal to " << second_number << std::endl; // This is the last condition where both numbers are equal; we don't need to mention that they're equal (by using "==") since if the earlier 2 conditions fail, this means that the first number is not more or less than the second number (as such, they're equal)
    }

    return 0;
}
```

## FOR

### > **Generic For Loops**

For loops work like another real life situation

- For every apple in your basket, I will give you a dollar
- For the variable `int i = 0`, until it becomes equal to 5: `i <= 5`, and on the condition that it grows by 1: `++i`, I will write "Hello"

The example provided is hard to grasp at this stage, but the examples below will clear up all the fog\
_An example illustrating its usage in code will be provided below:_

```cpp
#include <iostream> // To use "std::cout"

int main()
{
    for (int i = 0; i <=5; ++i)
    {
        std::cout << "Hello!" << std::endl;
    }

    /* The for loop above creates a new variable "i" which begins at 0 and grows by 1 every time the for loop writes "Hello!" into the console
    The "i <= 5" part is translated to "when i is lesser or equal to 5"*/

    return 0;
}
```

### > **In-Range For Loops**

This type of for loops reflects another real life situation

- For one apple in range of an entire apple basket, count every apple individually
- For variable `const int &i` in range of the vector `std::vector<int> v`, iterate over every element in the vector "v"

This one's even more confusing: what is "&i" or a vector?
Don't worry since we'll go over it\
_An example illustrating its usage in code will be provided below:_

```cpp
#include <iostream> // To use "std::cout"
#include <vector> // To use "std::vector"

int main()
{
    std::vector<int> v = {31, 12, 46, 97, 4}; // This is a vector that stores a collection of integers; a vector is essentially just a list just like those lists you might've seen in other coding languages; vectors are used to store multiple values of the specified type; in this case, the integer type

    for (const int &i : v)
    {
        std::cout << i << ' ' << std::endl;
    }

    /* In this example, we declared i as a constant integer by reference; we will go over references and pointers later, but basically, it's a way to refer to the exact address of a value instead of having to copy the entire value from scratch, which makes references important for performance purposes
    Alternatively, we can use the "auto" type which calibrates itself based on how it was used*/

    for (auto j : v)
    {
        std::cout << j << ' ' << std::endl;
    }

    /* Here, the "auto" type determined that the variable "j" is being used as an integer, so it start to behave like an integer
    Additionally, we can use forwarding reference by replacing the "auto" with "auto&&"*/

    return 0;
}
```

## THE CSTDLIB LIBRARY

A brief break for the explanations\
I will explain how the "cstdlib" library in c++ works to help you understand the next example

The official link to the explanation page on [cplusplus.com](https://cplusplus.com/) will be included below\
[Official cstdlib Explanation](https://cplusplus.com/reference/cstdlib/)

This library is used to convert strings into numeric-based data types with the usage of functions (such as "atof")\
Alternatively, you can use it to generate pseudo-random numbers with the usage of "rand" and "srand"

There are many more things you can do with this one library, but for this situation, we are only going to go over "rand" and "srand"

### > **Srand**

Srand is used as an initializer for "rand" and is based on "seed" values\
The seed determines which succession of results that "rand" would use

### > **Rand**

Rand is used to quote "generate" pseudo-random numbers\
When using it, you give it a starting point and an ending point\
_Here's how you would use it together with "srand":_

```cpp
#include <iostream> // To use "std::cout"
#include <cstdlib> // To use "std::srand" and "std::rand"

int main()
{
    std::srand((unsigned) time(NULL)); // An unsigned seed value
    int random_number = 50 + (std::rand() % 51); // Outputs a number that is anywhere from 50 to 100
    std::cout "Random Number: " << random_number;

    return 0;
}
```

## WHILE

You've guessed it, user; while loops are yet another condition that are reflective of the real world

- While you're doing the laundry, I'll be cleaning up my room, but I will stop the instant you finish your laundry
- While the boolean "is_valid" is set to true, I will continue printing nothing by zeros into the console

I understand, these examples are pretty weird, but they do the job at explaining the condition\
Regardless, we will get into this right now\
_An example illustrating its usage in code will be provided below:_

```cpp
#include <iostream> // To use "std::cout" and "std::cin"
#include <limits> // To clear the buffer with "std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n')"
#include <cstdlib> // This library will allow us to generate random numbers

// We will have a little fun with a number guessing simulator
int main()
{
    bool correct_answer = false;
    int x; // The user's answer

    // First, we have to provide a seed value
    std::srand((unsigned) time(NULL));

    int random_number = (std::rand() % 101); // From 0 to 100

    while (!correct_answer)
    {
        std::cout << "Guess what number I'm thinking of!\nYou're my friend, so you get infinite tries\nYour Guess: ";
        std::cin >> x;
        std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n'); // So every succeeding guess is correctly passed into the output stream

        if (x == random_number)
        {
            std::cout << "Wow, you've guessed my secret number!\nYou Win";
            correct_answer = true; // Cancels out the condition
        }
        else
        {
            std::cout << "Incorrect! Try again!\n";
            // In this case scenario, the correct_answer boolean stays false, so the while loops will "loop" again
        }
    }

    // This is a very simple version of this game, but we will enhance it later

    return 0;
}
```
