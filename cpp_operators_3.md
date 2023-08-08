# C++ OPERATORS EXPLAINED

> This is a brief summary of operators in C++\

## Operators

Operators determine relations between different parts of your code\
You might've already heard of "operators" in maths, and you would be correct to assume that they work in a similar way\
We will briefly go over each operator

To skip to operators of specific type, please refer to the menu below

- [Arirthmetic Operators](#arirthmetic-operators)
- [Assignment Operators](#assignment-operators)
- [Comparison Operators](#comparison-operators)
- [Logic Operators](#logic-operators)
- [Input/Output Operators](#inputoutput-operators)
- [Increment/Decrement Operators](#incrementdecrement-operators)
- [Operators Example](#operators-example)

### Arirthmetic Operators

- `+` - Addition and Concatenation
- `-` - Subtraction
- `*` - Multiplication
- `/` - Division
- `%` - Modulo (Division's Remainder)

### Assignment Operators

- `=` - Equality (Arithmetic)
- `+=` - Add Sum (Arithmetic) [x = x + y]
- `-=` - Subtract Sum (Arithmetic) [x = x - y]
- `*=` - Multiply Sum (Arithmetic) [x = x * y]
- `/=` - Divide Sum (Arithmetic) [x = x / y]
- `%=` - Module Sum (Arithmetic) [x = x % y]

### Comparison Operators

- `==` - Equivalent
- `!=` - Not Equivalent/Different
- `>` - Greater
- `<` - Lesser
- `>=` - Greater/Equal
- `<=` - Lesser/Equal

### Logic Operators

- `&&` - And
- `||` - Or
- `!` - Not

## Input/Output Operators

- `<<` - Print/Output
- `>>` - Receive/Input

### Increment/Decrement Operators

- `++` - Increment
- `--` - Decrement

### Operators Example

_An example illustrating how operators work will be shown below:_

```cpp
#include <iostream> // To use "std::cout" and "std::cin"
#include <cstdlib> // To generate random numbers
#include <limits> // To clear the buffer on invalid input

int main()
{
    // Arirthmetic Operators
    int my_sum = 2 + 4; // Addition: 6
    int my_difference = 4 - 2; // Subtraction: 2
    int my_product = 2 * 4; // Multiplication: 8
    int my_quotient = 4 / 2; // Division: 2
    int my_modulo = 5 % 2 // Modulo: 1

    // Assignment Operators
    int bigger_sum = my_sum += 5; // 6 + 5 = 11
    int smaller_difference = my_difference -= 2; // 2 - 2 = 0
    int bigger_product = my_product *= 2; // 8 * 2 = 16
    int smaller_quotient = my_quotient /= 2; // 2 / 2 = 1
    int new_modulo = my_modulo % 1; // 1 % 1 = 0

    // Comparison, Logic, and IO Operators
    if (my_sum < bigger_sum && my_difference > smaller_difference)
    {
        std::cout << my_sum << " is lesser than " << bigger_sum << '\n' << my_difference " is greater than " << smaller_difference; << std::endl;
        // The "<<" operator is used to output the values, the "&&" is used in place of the word "and", and the "<" and ">" work just like you'd expect them to work
    }

    std::srand((unsigned) time(NULL));
    int random_number = 0 + (std::rand() % 26);
    std::cout << "Input a number and see if it's bigger than my number!\nI will only select from 0 to 25\nYou only have 10 tries!\n";

    for (int i = 0; i < 10; ++i) // The "++" operator is used to increment the value of "i" by 1 every time the loop finishes
    {
        int x;
        bool valid_input = false;

        while (!valid_input) // Here, we used the logic operator "!", which means "not/invalid" (while valid_input is invalid/false)
        {
            std::cout << "Select: "; // Prompt to guess
            std::cin >> x; // Your guess

            if (x < 0 || x > 25) // Here, we used the logic operator "||", which means "or" (if x < 0 or x > 25)
            {
                std::cout << "Only numbers from 0 to 25!\n"; // Warns the user about the acceptable range
            }
            else
            {
                std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n'); // Clears the buffer
                valid_input = true; // Exits the while loop
            }
        }

        if (x == random_number)
        {
            std::cout << "Wow, you've guess my number!\nMy number was " << random_number << std::endl;
            break; // This will exit the for loop early (if you still had some attempts remaining)
        }
        else
        {
            if (x < random_number)
            {
                std::cout << "Too low!\n"; // Uses the "<" operator
            }
            else std::cout << "Too high\n"; // Uses the ">" operator
        }
    }

    return 0;
}
```
