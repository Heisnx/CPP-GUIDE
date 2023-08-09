# C++ POINTERS AND REFERENCES EXPLAINED

> In this brief guide for pointers and references, we will go over why they're important and what exactly they do

## Table of Contents

- [Pointers](#pointers)
- [References](#references)

## Pointers

Pointers in c++ are used to save the addresses of variables' values\
Basically, you have the variable and the value that the variable is storing\
I will provide an analogy of the situation through the lenses of real life (again)

- You have this house that we'll call "variable", and the "pointer" would be house's address
- A variable only stores its assigned value, but a pointer stores the value and the memory address of the variable, meaning that your computer won't have to copy the value over and over

This analogy is quite weird, but it's the most of what I could tinker to make this as understandable as possible\
To declare a pointer: `type* pointer = &existing_variable` where the "\*" and "&" are very important, and the "type" is the same type of the "existing_variable" variable\
We will get into examples, though

_An example about pointers will be shown below:_

```cpp
#include <iostream> // To use "std::cout"

int main()
{
    int my_number = 15; // The variable
    int* my_number_pointer = &my_number; // The pointer

    std::string cheese_variation_1 = "Parmesan";
    std::string* ptr_cheese_1 = &cheese_variation_1;

    std::cout << my_number << ", " << my_string << std::endl; // 15, Parmesan
    std::cout << my_number_pointer << ", " << ptr_cheese_1; // Addresses aren't meant to be read by humans

    return 0;
}
```

## References

References in C++ provide an alternative way to access the values of variables without copying them directly\
Think of references as aliases, like a nickname for a friend

- Your friend is named "variable", and the reference would be your friend's nickname
- References don't store the memory address like pointers do; they simply become another name for the same value

The main advantage of references is that they provide a cleaner syntax compared to pointers, and you don't have to deal with memory addresses directly\
To declare a reference: `type& reference = existing_variable` where the "&" is crucial

_An example illustrating the usage of references will be shown below:_

```cpp
#include <iostream> // To use "std::cout"

int main()
{
    int my_number = 10; // The variable
    int& my_number_reference = my_number; // The reference

    std::string favorite_color = "Blue";
    std::string& color_reference = favorite_color;

    std::cout << my_number << ", " << favorite_color << std::endl; // 10, Blue
    std::cout << my_number_reference << ", " << color_reference << std::endl; // 10, Blue

    my_number_reference = 20; // This will change the value of my_number as well
    std::cout << my_number << ", " << my_number_reference << std::endl; // 20, 20

    return 0;
}
```
