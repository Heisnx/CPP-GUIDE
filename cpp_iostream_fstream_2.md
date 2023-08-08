# C++ IOSTREAM AND FSTREAM EXPLAINED

> This is a short guide to the standard iostream library

## Table of Contents

- [Link to IOstream](#cpp-iostream)
- [IOstream](#iostream)
- [Link to Fstream](#cpp-fstream)
- [Fstream](#fstream)

## CPP-IOstream

Below is a link to the IOstream page on [cplusplus.com](https://cplusplus.com/)
[**C++ IOstream Explanation**](https://cplusplus.com/reference/iostream/)

## IOstream

cout, cin, and etc. are all elements of the iostream library within the standard namespace\
That is why you write them like std::cout as in "from standard namespace character output"

_An example below will list the basics:_

```cpp
#include <iostream> // The think we're working with

int main()
{
    int my_number; // We need a container to store a value in
    std::cout << "Hello World"; // "cout" stands for "character output" and outputs text onto the console
    std::cin >> my_number; // "cin" stands for "character input" and, instead, receives input from the user onto the console
    // In addition, we have
    std::cerr << "Error: you need to re-read this one for sure"; // "cerr" is used to output errors within its own output stream
    std::clog << "This one will sure \"clog\" your mind"; // "clog" is used for logging and has its own output stream
    // Little things
    std::cout << "I've used a newline character\nTo output text on two lines at once!" << std::endl; // Both '\n' and "std::endl" are used to create new lines; "endl" stands for "end line"
    std::wcout << L"Meant for the wide boys"; // These ones are used for wchar_t, which are essentially wide characters

    return 0;
}
```

## CPP-Fstream

Below is a link to the IOstream page on [cplusplus.com](https://cplusplus.com/)\
[**C++ Fstream Explanation**](https://cplusplus.com/reference/fstream/)

## Fstream

This one is used to manipulate external files; as such, the name of the library is "file stream"\
They also derive from the same "standard" namespace

_An example below will list the basics:_

```cpp
#include <fstream> // The file-stream library

int main()
{
    std::ofstream my_file("example.txt"); // This one will create a text file named "example"
    my_file << "I just wrote text into this file"; // Writes into the "example.txt" file
    my_file.close() // Closes the file; you can use ".is_open()" to make sure that your file is open

    std::ifstream my_file("example.txt"); // This will read the file's contents; in this case, the line from earlier
    my_file.close();

    std::fstream my_file;
    my_file.open("example.txt", ios_base::in); // "ios_base::in means" open for reading and "ios_base::out" means open for writing
    if (my_file.is_open())
    {
        std::cout << "The file has successfully opened"; << std::endl; // This one is the usage of an "if" statement that we'll go later and the "is_open" function
    }
    else
    {
        std::cout << "Failed to open file!" << std::endl; // If the file didn't exist or something else went wrong
        return 1; // This is like returning error status code 1, which means that something went wrong
    }

    // The same wide versions of these methods exist for wide characters

    return 0;
}
```
