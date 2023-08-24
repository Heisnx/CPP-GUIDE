# C++ EXCEPTIONS EXPLAINED

> Handle errors with ease similar to how it worked in a few other programming languages\
> The basic process is straightforward, but the ways in which you can use this can be as complex as you imagine

## Exceptions

As the naming says, you create exceptions for certain scenarios if they go wrong\
It's like an exception to a rule: an ambulance vehicle speeding in order to reach the patient on time\
These are important since if you fail to consider exceptions, your code will have certain "holes" in it which could be used to break your programs\
Aside from the defitinions, the concept is actually pretty simple:

1. You "Try" to do something
2. You "Throw" an error in case something goes wrong
3. You "Catch" that thrown error and resolve it

_An example that goes over exceptions will be shown below:_

```cpp
#include <iostream> // You likely have a clear understand of this library
#include <string> // Strings

int input_check(const std::string &prompt) // In this example, we will use an integer function to cover a common type of error
{
	while (true)
	{
		try
    	{
    		int x; // "x" is the number that we will be checking for an "Integer Parsing" error (when you provide invalid output in place of an integer)
    		std::cout << prompt << std::endl; // The "prompt" variable stores the prompt provided to the user
			std::cin >> x; // Prompts the user to input an integer value for the variable "x"
	        if (std::cin.fail()) // Assuming the value for variable "x" is invalid (Will, also, prompt the user every time)
        	{
            	throw std::invalid_argument("Invalid Input");
        	}
			else
			{
				return x; // Just returns the value
			}
    	}
		catch(const std::exception &error)
		{
			std::cerr << "\33[31m" << error.what() << "\33[0m" << std::endl;
			continue;
		}
	}
}

int addition(int x, int y) // This you know from the functions explanation
{
	int sum = x + y;
	return sum;
}

int main()
{
	int first_number = input_check("Input the first number: ");
	int second_number = input_check("Input the second number: ");
	int sum = addition(first_number, second_number);
	std::cout << "The sum of " << first_number << " and " << second_number << " is " << sum << std::endl;
    return 0;
}
```
