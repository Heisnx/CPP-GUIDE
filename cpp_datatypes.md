# C++ PRIMITIVE DATA TYPES AND THEIR VARIABLE DECLARATIONS EXPLAINED

> This is a brief guide on C++ data types

## Table of Contents

- [General](#general)
- [Integer](#integer)
- [Float/Double](#float/double)
- [Boolean](#boolean)
- [Character](#character)
- [String](#string)
- [Void](#void)

## General

Data types are fundamentally similar to different types of ice cream flavour\
If you get chocolate ice cream, you won't get a strawberry taste\
Just like you can't store text in an numerical container like _int_ or _double_\
C++ will most of the time pick up on what data type you wanted to use unless you specified it earlier

The declaration of variables usually looks like `type name = value;`\
Variables can also inherit additional attributes like _const_ which makes the variable constant\
There are many more attributes, and we will get into them when we start talking about pointers and reference variables\
Fundamentally, variables are like a child that doesn't want to eat vegetables but will eat candy\
The candy being the values that they accept

## Integer

> Declared with an _int_ at the start, this data type represents whole numbers within a 32 bit limit\*\*\
> _Examples will be shown below:_

```cpp
#include <iostream> // This is necessary for us to use "std::cout"

int main()
{
    int my_integer = 5; // How to declare a variable of type int
    std::cout << 5; // How to output a value of type int
    const int my_constant_integer = 10; // The 10 here is a constant variable

    return 0; // This is necessary because the "main" function is expected to return an integer value, and 0 is used to handle it
}
```

## Float/Double

> Declared with either _float_ or _double_, these variables contain floating-point numbers\
> Numbers of type _float_ always an _f_ after the number\
> Numbers of type _double_ are more precise than those of type _float_ due to using 8 byte/64 bit to store its values\
> _Examples will be shown below:_

```cpp
int main()
{
    float my_float = 3.14f; // How to declare a variable of type float
    double my_double = 3.141592; // How to declare a variable of type double

    return 0;
}
```

## Boolean

> Declared with _bool_, these variables can only store a true or false response\
> _true_ is represented as a 1; _false_ is represented as a 0\
> Boolean variables use 1 byte or 8 bits of storage which may be wasteful\
> _Examples will be shown below:_

```cpp
int main()
{
    bool my_true_boolean = true; // A variable of type bool storing a true value
    bool my_false_boolean = false; // A variable of type bool storing a false value

    return 0;
}
```

## Character

> Declared with a _char_, these variables store a single character/key\
> _char_ type values are usually stored in single quotes\
> _Examples will be shown below:_

```cpp
int main()
{
    char my_char = 'a' // How to declare a variable of type char
    char my_cstring[6] = "abcde"; // This is how they used to write strings in C before the string and standard libraries

    return 0;
}
```

## String

> Declared with either _std::string_ or _string_ if you're using the _std_ namespace, this variable type stores text-like information\
> The declaration process of this type of variables is more complex than the others and is shown below\

```cpp
#include <string>

int main()
{
    std::string my_string = "Hello";
    return 0;
}
```

## Void

> The _void_ type is a valueless type: this means that they return or store no values
