# Demo: Class Scope
## Person.h(header file of class)
```cpp
#pragma once
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

		void SetFirstName(std::string fName);
		std::string GetFirstName();

		void SetLastName(std::string lName);
		std::string GetLastName();

		void SetAge(int age);
		int GetAge();

		void SayHello();

};
```
## Person.cpp(implement file)
```cpp
#include "Person.h"

Person::Person()
{

}

Person::Person(std::string fName, std::string lName)
{
	this->firstName = fName;
	this->lastName = lName;
}

Person::Person(std::string fName, std::string lName, int age)
{
	this->firstName = fName;
	this->lastName = lName;

	this->age = age;
}

Person::~Person()
{
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
	if (age > 0)
	{
		this->age = age;
	}
	else
	{
		std::cout << "Please enter a valid age" << std::endl;
	}
}

int Person::GetAge()
{
	return this->age;
}

void Person::SayHello()
{
	std::cout << "Hello" << std::endl;
}
```
## dog.h(header file of class)
```cpp
#pragma once
#include <iostream>

class dog
{
private:
	std::string firstName;
	std::string lastName;
	int age;

public:
	// three constructors
	dog();

	dog(std::string fName, std::string lName);

	dog(std::string fName, std::string lName, int age);
	// one destructor
	~dog();

	void SetFirstName(std::string fName);
	std::string GetFirstName();

	void SetLastName(std::string lName);
	std::string GetLastName();

	void SetAge(int age);
	int GetAge();

	void SayHello();

};
```
## dog.cpp(implement file)
```cpp
#include "dog.h"

dog::dog()
{
}

dog::dog(std::string fName, std::string lName)
{
	this->firstName = fName;
	this->lastName = lName;
}

dog::dog(std::string fName, std::string lName, int age)
{
	this->firstName = fName;
	this->lastName = lName;
	this->age = age;
}

dog::~dog()
{
}

void dog::SetFirstName(std::string fName)
{
	this->firstName = fName;
}

std::string dog::GetFirstName()
{
	return this->firstName;
}

void dog::SetLastName(std::string lName)
{
	this->lastName = lName;
}

std::string dog::GetLastName()
{
	return this->lastName;
}

void dog::SetAge(int age)
{
	if (age > 0)
	{
		this->age = age;
	}
	else
	{
		std::cout << "Please enter a valid age" << std::endl;
	}
	
}

int dog::GetAge()
{
	return this->age;
}

void dog::SayHello()
{
	std::cout << "Whoof" << std::endl;
}
```
## demo.cpp
```cpp
#include <iostream>
#include "Person.h"
#include <string>
#include "dog.h"

int main()
{
	Person *p = new Person("Tom", "Thumb");
	std::cout << "Person first name = " << p->GetFirstName() << std::endl;

	p->SayHello();

	dog *d = new dog("fido", "Thumb");

	std::cout << "Dog first name = " << d->GetFirstName() << std::endl;

	d->SayHello();

	return 0;
}
```
