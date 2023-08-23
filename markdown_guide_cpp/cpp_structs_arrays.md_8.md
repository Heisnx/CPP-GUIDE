# C++ STRUCTS AND ARRAYS EXPLAINED

> I guess I should've went over arrays much earlier\
> Well, at least before I went over vectors

> Basically, they both serve to contain something\
> Let's begin shall we?

## Table of Contents

- [Structs](#structs)
- [Arrays](#arrays)

## Structs

"Structs" or "Structures" work pretty similar to how objects derived from classes work\
However, their key difference is that they're actually used to group variables together\
Hence, each variable of the structure is known as a member of the struct\
A struct is declared like `struct <name> { <variable_declarations> } <structure_variables>;`\
"name" is optional, "variable_declarations" is the declaration of one or more variables, "structure_variables" is the declaration of one or more variables that entail all the attributes from "variable_declarations"

**Side note: you don't have to name a structure when declaring it - it's optional**

This does seem pretty similar to how arrays or vectors work, right?
Not quite since structures can actually store multiple different data types at once whereas arrays and vectors are strictly static\
This might seem slightly weird for a static coding language like c++, but it, in fact, is a pretty useful tool

_An example explaining how "Structs" work will be shown:_

```cpp
#include <iostream> // To use "cout"
#include <string> // To use "string"

int main()
{
    struct // The "struct" keyword is used to declare a struct
    {
        // Variable declarations
        int my_number;
        std::string my_string;
        bool my_boolean;
    } my_structure; // This is a "struct variable" which entails all three of the variables above

    my_structure.my_number = 5;
    my_structure.my_string = "abc";
    my_structure.my_boolean = true;

    // That was a very basic way to use structs

    struct Milkshake // This is a named structure
    {
        std::string flavour;
        double price;
        bool in_stock;
    } strawberry, banana, chocolate; // You declare more than one of these variables

    // Another way to create and define struct variables is this
	Milkshake milkshakes[3];

	// Defining the strawberry type
	milkshakes[0] = { "Strawberry", 2.49, true };

    // Defining the banana type
	milkshakes[1] = { "Banana", 2.99, false };

    // Defining the chocolate type
	milkshakes[2] = { "Chocolate", 1.99, true };

	// Printing the results out
    std::cout << "==================\n";
	for (int i = 0; i < 3; ++i)
	{
		std::string milkshake_availability = (milkshakes[i].in_stock == 1) ? "In Stock" : "Out of Stock";
		std::cout << "Milkshake " << i + 1 << ":\n";
        std::cout << "Flavour: " << milkshakes[i].flavour << "\n";
        std::cout << "Price: " << "$" << milkshakes[i].price << "\n";
        std::cout << "Availability: " << milkshake_availability << "\n";
        std::cout << "==================\n";
	}
    return 0;
}
```

## Arrays

Arrays are incredibly similar to the vectors that we learnt in an earlier guide\
However, they have their own key differences\
They're usually declared like `<type> <array_name>[<amount_of_elements][optional_other_dimensions] = {<elements>};`\
Arrays can also possess multiple "dimensions," which kind of work like multiple stories to the array\
This, in turn, provides more versatile static arrays

_An example going over arrays in c++ will be shown:_

```cpp
#include <iostream> // To use "std::cout"

int main()
{
    int number_array[3] = { 2, 4, 6 }; // The simplest declaration of an array
	int number_array_size = sizeof(number_array) / sizeof(number_array[0]); // To get the array size

	for (int i = 0; i < number_array_size; ++i)
	{
		std::cout << number_array[i] << ", "; // We use a for loop to output each element of the array with respect to the array's size
	}

	// You can have multiple of these "stories" or "dimensions" within one array
	double multi_dimensional_array[2][3] = {
		{ 3.141, 2.718, 6.28 }, { 1.148, 4.854, 9.667 }
	};
	int multi_dimensional_array_dimensions = sizeof(multi_dimensional_array) / sizeof(multi_dimensional_array[0]);
	int multi_dimensional_array_size = sizeof(multi_dimensional_array) / sizeof(multi_dimensional_array[0][0]) / multi_dimensional_array_dimensions;
	std::cout << std::endl; // New line

	for (int i = 0; i < multi_dimensional_array_dimensions; ++i)
	{
		for (int j = 0; j < multi_dimensional_array_size; ++j)
		{
			std::cout << multi_dimensional_array[i][j] << ", ";
		}
	}
}
```

