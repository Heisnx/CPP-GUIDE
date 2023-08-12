# C++ VECTORS, CLASSES AND OOP EXPLAINED

> In this brief guide for c++, we'll go over classes and their many different attributes\
> Prepare to engage in a long one since classes are a very popular topic when it comes to c++\
> In fact, c++ is often called "C with OOP" where classes work hand to hand with the OOP part\
> OOP stands for "Object-Oriented Programming" and classes are essentially this ruleset for each "object"

## Table of Contents

- [Vectors](#vectors)
- [Class-Access-Levels](#class-access-levels)
- [Classes](#classes)
- [Inheritance](#inheritance)
- [Objects](#objects)
- [Polymorphism](#polymorphism)

## Vectors

Vectors are essentially "packets" or "lists" of stuff\
They can only contain values of the specified data type\
They're usually declared like `std::vector<type> vector_name = { // A list of elements of specified data type };`

_A link to the official page on [cplusplus.com](https://cplusplus.com/) will be shown below:_\

- [Vectors](https://cplusplus.com/reference/vector/vector/)

Here's an example that is reflective of real life

- You have two baskets: one of them is only meant for apples, and the other one is only meant for oranges; the first basket is now an "apple" vector (list), and the second basket is an "orange" vector (list)
- Vectors function very much like those lists you might've seen in different programming languages; these ones are static, though

Now, since there is so much to vectors in c++, I cannot explain everything here at once without making this file absurdly long\
As such, for those who want to learn more about vectors, I included a link to the explanation of the library\
As of this guide, I will explain every relevant bit about vectors procedurally as we meet them

_An example illustrating vectors will be shown below:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string"
#include <vector> // To use "std::vector"

int main()
{
    std::vector<int> number_vector = { 1, 2, 3, 4, 5 }; // An integer vector
    std::vector<std::string> food = { "Cheese", "Bread", "Carrot", "Pie", "Cherry" }; // A string vector

    number_vector.push_back(6); // Add 6 to the end of the vector
    food.push_back("Pear"); // Adds "Pear" to the end of the vector

    for (int i : number_vector)
	{
		std::cout << i << ' ';
	}

	std::cout << std::endl; // To insert a newline character into the buffer

	for (std::string i : food)
	{
		std::cout << i << ' ';
	}

	std::cout << '\n' << number_vector.front() << ' ' << number_vector.at(2) << ' ' << number_vector.back() << '\n'; // The first, 3nd, and last elements of the numeber_vector vector
	// You might be confused at why we accessed the 3rd element by using 2 as our value; that is because vectors start counting from 0, meaning that the 1st element is number 0

	number_vector.pop_back(); // Removes the last element of the vector (6)
	// So if we print the elements out again, we get the vector without the 5
	for (int i : number_vector)
	{
		std::cout << i << ' ';
	}

	food.clear(); // Clears the food vector of all elements

	if (food.empty()) // my_vector.empty() returns a true/false value that states whether the vector is empty or not; in this case, it returns true due to the food vector actually being empty
	{
		std::cout << "\nThe food vector is empty" << std::endl;
	}

	// I will stop here, but there is still some stuff to vectors; this is a good view of it, though

    return 0;
}
```

## Class Access Levels

This one comes right before the classes\
Basically, classes come with 3 different protection levels\
If you don't specify, your computer will assume that all the elements are of private access\

- Private: Cannot be used outside the main class
- Protected: Can only be accessed within [_inherited classes_](#inheritance)
- Public: Can be accessed at any time

## Classes

Classes are a very big part of c++\
They can be tough to grasp at times, but I'll make sure to start with an example reflective of real life

- Imagine a passport with the credentials of a certain individual; every passport contains the same/similar info about an individual; this "template" which is used to make passports is the "class"; essentially, classes are like templates used for creating copies of something (Not to confuse this with "templates" from c++)
- Classes are defined like `class class_name { // class attributes };` where the semicolon at the end is crucial

We will still get into examples within code, though\
Something called "Encapsulation" will be also shown: basically, it's just the way you access private members of a class from outside a class\
You might be confused to why we'd need to do that, but it's to avoid any unwanted errors like accidentally mentioning a class member (if it's public)\
The "methods" (functions) used to return and set the values of the private members are always of public access

_An example illustrating the declaration of classes in c++ will be shown below:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string"

class Car
{
    private:
    std::string car_brand;
	std::string car_model;
    int manufacture_year;
    bool used;

    public:
	// "Getters" are functions that return the private values from within this class
	int get_manufacture_year() const { return manufacture_year; } // The "const" is necessary
	std::string get_car_brand() const { return car_brand; }
	std::string get_car_model() const { return car_model; }
	bool is_used() const { return used; }

	// "Setters" are functions that change the value of the private variables
	void set_manufacture_year(int new_manufacture_year) { manufacture_year = new_manufacture_year; } // No "const" here + setters are void type functions
	void set_car_brand(const std::string &new_car_brand) { car_brand = new_car_brand; } // We get a constant string value by reference (like we learnt to do within the previous guides)
	void set_car_model(const std::string &new_car_model) { car_model = new_car_model; }
	void set_used_status(bool new_used_status) { used = new_used_status; } // We just equate the initial (old) value to the newly passed in value
};

int main()
{
	Car my_car; // This is an object; we will get into objects after classes and inheritance

	my_car.set_manufacture_year(1999); // Year 1999
	my_car.set_car_brand("BMW"); // BMW M3 Coupe 1999
	my_car.set_car_model("M3 Coupe"); // Car model
	my_car.set_used_status(true); // Was used by previous owner

	int my_car_year = my_car.get_manufacture_year(); // We just call it: no need to pass in any values
	std::string my_car_brand = my_car.get_car_brand();
	std::string my_car_model = my_car.get_car_model();
	std::string my_car_is_used = (my_car.is_used() == 1) ? "Used" : "Unused"; // A ternary statement used to convert numerical boolean output into textual output for readability purposes

	std::cout << my_car_brand << ' ' << my_car_model << std::endl;
	std::cout << "Year of Car's Manufacture: " << my_car_year << std::endl;
	std::cout << "Used Status: " << my_car_is_used << std::endl;

    return 0;
}
```

## Inheritance

To showcase in inheritance, we will use the exact same code example from above since we will be "inheriting" attributes from the "Car" class\
We will only replace the code within the "main" function\
Basically, a class can inherit another class's attriutes whilst having its own unique attributes\
Inheriting another class's attributes goes like `class child_class : public parent_class { // Code };`\
It's something in the realm of a parent and child relationship

_An example illustrating inheritance of classes will be shown below:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string"

class Car
{
    private:
    std::string car_brand;
	std::string car_model;
    int manufacture_year;
    bool used;

    public:
	// "Getters" are functions that return the private values from within this class
	int get_manufacture_year() const { return manufacture_year; } // The "const" is necessary
	std::string get_car_brand() const { return car_brand; }
	std::string get_car_model() const { return car_model; }
	bool is_used() const { return used; }

	// "Setters" are functions that change the value of the private variables
	void set_manufacture_year(int new_manufacture_year) { manufacture_year = new_manufacture_year; } // No "const" here + setters are void type functions
	void set_car_brand(const std::string &new_car_brand) { car_brand = new_car_brand; } // We get a constant string value by reference (like we learnt to do within the previous guides)
	void set_car_model(const std::string &new_car_model) { car_model = new_car_model; }
	void set_used_status(bool new_used_status) { used = new_used_status; } // We just equate the initial (old) value to the newly passed in value
};

class CarAndOwner: public Car // The "CarAndOwner" class is used to describe the car's owner whilst also describing what vehicle they're driving
{
	private:
	std::string owner_name; // The owner's full name
	int owner_age; // The owner's age
	bool license_status; // If the owner owns a license

	public:
	// Getters [It really is he same over here]
	std::string get_owner_name() const { return owner_name; }
	int get_owner_age() const { return owner_age; }
	bool get_license_status() const { return license_status; }

	// Setters
	void set_owner_name(const std::string &new_owner_name) { owner_name = new_owner_name; }
	void set_owner_age(int new_owner_age) { owner_age = new_owner_age; }
	void set_license_status(bool new_license_status) { license_status = new_license_status; }
};

int main()
{
	CarAndOwner car_1; // An object

	// Set all of the values
	// Car class
	car_1.set_car_brand("BMW");
	car_1.set_car_model("M3 Coupe");
	car_1.set_manufacture_year(1999);
	car_1.set_used_status(true);
	// CarAndOwner class
	car_1.set_owner_name("Henry Spite");
	car_1.set_owner_age(27);
	car_1.set_license_status(true);

	// Setting up the variables
	// Car class
	std::string car_1_brand = car_1.get_car_brand();
	std::string car_1_model = car_1.get_car_model();
	int car_1_year = car_1.get_manufacture_year();
	std::string car_1_is_used = (car_1.is_used() == 1) ? "Used" : "Unused";
	// CarAndOwner class
	std::string car_1_owner_name = car_1.get_owner_name();
	int car_1_owner_age = car_1.get_owner_age();
	std::string car_1_has_license = (car_1.get_license_status() == 1) ? "Yes" : "No";
	char car_1_license_type = car_1.get_license_status();

	// Time to print all this out
	std::cout << car_1_owner_name << "'s" << car_1_brand << ' ' << car_1_model << std::endl;
	std::cout << car_1_owner_name << "'s age " << car_1_owner_age << std::endl;
	std::cout << "Year of Car's Manufacture: " << car_1_year << std::endl;
	std::cout << "Used Status: " << car_1_is_used << std::endl;
	std::cout << "Has a License: " << car_1_has_license << std::endl;

    return 0;
}
```

## Objects

Objects in c++ are essentially like copies made from a mold that is the class\
You declare them like `<class_name> my_obj;` where the "class_name" is replaced with the name of the class\
You can declare multiple objects in one project\
We'll still use the "Car" class as an example

_A brief example will go over this:_

```cpp
#include <iostream> // To use "std::cout"
#include <string> // To use "std::string"
#include <vector> // To use "std::vector"

class Car
{
    private:
    std::string car_brand;
	std::string car_model;
    int manufacture_year;
    bool used;

    public:
	// "Getters" are functions that return the private values from within this class
	int get_manufacture_year() const { return manufacture_year; } // The "const" is necessary
	std::string get_car_brand() const { return car_brand; }
	std::string get_car_model() const { return car_model; }
	bool is_used() const { return used; }

	// "Setters" are functions that change the value of the private variables
	void set_manufacture_year(int new_manufacture_year) { manufacture_year = new_manufacture_year; } // No "const" here + setters are void type functions
	void set_car_brand(const std::string &new_car_brand) { car_brand = new_car_brand; } // We get a constant string value by reference (like we learnt to do within the previous guides)
	void set_car_model(const std::string &new_car_model) { car_model = new_car_model; }
	void set_used_status(bool new_used_status) { used = new_used_status; } // We just equate the initial (old) value to the newly passed in value
};

int main()
{
	Car car_1; // 1st car object
	Car car_2; // 2nd car object
	Car car_3; // 3rd car object

	// 1st Car
	car_1.set_car_brand("BMW");
	car_1.set_car_model("M3 Coupe");
	car_1.set_manufacture_year(1999);
	car_1.set_used_status(true);

	// 2nd Car
	car_2.set_car_brand("Honda");
	car_2.set_car_model("Civic Ferio");
	car_2.set_manufacture_year(1996);
	car_2.set_used_status(true);

	// 3rd Car
	car_3.set_car_brand("Toyota");
	car_3.set_car_model("Corolla");
	car_3.set_manufacture_year(2023);
	car_3.set_used_status(false);

	// Vector where we'll store all these cars (list)
	std::vector<Car> cars = { car_1, car_2, car_3 };
	int n = 1; // This is the order of the car

	for (Car &car : cars)
	{
		// We define the variables
		std::string car_brand = car.get_car_brand();
		std::string car_model = car.get_car_model();
		int car_year = car.get_manufacture_year();
		std::string car_is_used = (car.is_used() == 1) ? "Used" : "Unused";

		// We print out the details of each car
		std::cout << "Car No. " << n << std::endl;
		std::cout << car_brand << ' ' << car_model << std::endl;
		std::cout << "Year of Car's Manufacture: " << car_year << std::endl;
		std::cout << "Used Status: " << car_is_used << "\n\n";
		++n; // Increment the car count
	}
	return 0;
}
```

## Polymorphism

This is when you sort of make inherited (child) classes, but they're a variation of the "parent" class, instead\
If "CarAndOwner" appended info on top of the "Car" class, polymophism allows you to make variations of the "parent" class

_An example illustrating "Polymorphism" will be show below:_

```cpp
#include <iostream> // To use "std::string"

class mathematics
{
	public:
	int operation(int x, int y) { std::cout << "perform a Maths operation"; }
};

class addition : public mathematics
{
	public:
	int operation(int x, int y)
	{
		int sum = x + y;
		return sum;
	}
};

class subtraction : public mathematics
{
	public:
	int operation(int x, int y)
	{
		int diff = x - y;
		return diff;
	}
};

int main()
{
	addition my_addition;
	subtraction my_subtraction;

	int my_sum = my_addition.operation(2, 4); // 6
	int my_diff = my_subtraction.operation(11, 5); // 6

	std::cout << my_sum << ' ' << my_diff << std::endl; // 6 6

	return 0;
}
```

Here we see that we made one class from which we made 2 variations of it
