# Demo: Dynamic Memory Allocation with Classes
what is deconstructor and how it works?

## header file "Person.h"
```cpp
#include <iostream>

class Person
{
	private:
		std::string firstName;
		std::string lastName;
		int age;

	public:
		// three constructors
		Person();

		Person(std::string fName, std::string lName);

		Person(std::string fName, std::string lName, int age);
		// one destructor
		~Person();

		// member variables
		void SetFirstName(std::string fName);
		std::string GetFirstName();

		void SetLastName(std::string lName);
		std::string GetLastName();

		void SetAge(int age);
		int GetAge();

		void SayHello();
};
```
## function "Person.cpp"
```cpp
#include <iostream>
#include "Person.h"
// default function
Person::Person()
{

}

Person::Person(std::string fName, std::string lName)
{
	firstName = fName;
	lastName = lName;
}

Person::Person(std::string fName, std::string lName, int age)
{
	firstName = fName;
	lastName = lName;
	age = age;
}

Person::~Person()
{
	std::cout << "Person destructor called" << std::endl;
}

void Person::SetFirstName(std::string fName)
{
	this->firstName = fName;
}

std::string Person::GetFirstName()
{
	return this->firstName;
}

void Person::SetLastName(std::string lName)
{
	this->lastName = lName;
}

std::string Person::GetLastName()
{
	return this->lastName;
}

void Person::SetAge(int age)
{
	this->age = age;
}

int Person::GetAge()
{
	return this->age;
}

void Person::SayHello()
{

}
```
## demo file "demo.cpp"
```cpp
#include <iostream>
#include "Person.h"
#include <string>

int main()
{
	Person *pOne = new Person("tom", "thumb", 25);

	std::cout << "First name of pOne = " << pOne->GetFirstName() << std::endl;

	std::cout << "Memory address of pOne = " << &pOne << std::endl;

	delete pOne;

	return 0;
}
```
