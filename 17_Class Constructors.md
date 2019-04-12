# Class Constructors
Let's now turn our attention to the concept of **constructors** and **destructors** in our classes.  
The topic of constructors was covered briefly in the Introduction to C++ course but we'll offer a review here 
and expand on the topic of constructors in this lesson, adding in concepts around destructors.

**A constructor is used to initialize data members of a class**. The format of a constructor, at its most basic level,
is that it contains the same name as the class itself, has no return type, and may or may not contain
a parameter list.  Constructors are also, almost always, public although you can have a private constructor for use
within the class only.  **Some developers create a private constructor that is called via a public constructor, 
for the purposes of initializing private aspects of a class**.

Classes can have multiple constructors. **Constructors can be overloaded** in the same way that **functions can be overloaded**.  
**If you don't create a constructor in your class file, the compiler will create a default constructor automatically 
that will initialize member variables to default values** in some compilers, but other compilers will not use default values.  
Check your compiler documentation to find out how default constructors work. The C++ standard indicates that when a compiler 
follows the standard, **the member variables will be initialized to "indeterminate values"**.  **A class has one, and only one, 
default constructor**. If you do create a default constructor or any other constructor in your class, then the compiler 
will not create one.  This is an important consideration because **if you require or want a default constructor as well as
other constructors, then you MUST create your own default constructor**.  The default constructor, if provided, is one 
that **does not have any parameters** such as:
```cpp
class Person
    {
    public:
        Person();
        ~Person();
    };
```
This code sample demonstrates the template that is provided in Microsoft Visual Studio when creating a new C++ class. 
It completes the template with a very simple class definition that includes the class name (Person) and two public members,
the **default constructor (Person();) and the destructor (~Person();)**.  Destructors will be covered in the topic on destructors.

There are actually two more, equally important, reasons for defining a default constructor in your classes.  First off, 
compound types (arrays or pointers) that may be defined inside a code block, can **have undefined values when initialized 
to their default values**.  You should **ensure that these members are initialized correctly by creating your own default 
constructor** and performing the initialization yourself.

The second reason is a little more complex and arises **when your class contains a member that is a class itself. 
The compiler's default constructor is unable to initialize that member**.

The following code sample demonstrates the use of three different constructors, **one default constructor, 
one that accepts two arguments and one that accepts three arguments**. 

## Person.h
```
    #pragma once
    
    #include <string>
    
    class Person
    {
    
    private:
        std::string firstName;
        std::string lastName;
    
        int age;
    
    public:
        Person();
    
        Person(std::string fName, std::string lName);
    
        Person(std::string fName, std::string lName, int age);
    
        ~Person();

        void SayHello();
    };
```
## Person.cpp
```cpp
    #include "stdafx.h"
    #include "Person.h"
    #include <iostream>
    
    Person::Person()
    {
    
    }
    
    Person::Person(std::string fName, std::string lName)
    {
        this -> firstName = fName;
        this -> lastName = lName;
    }
    
    Person::Person(std::string fName, std::string lName, int age)
    {
        this -> firstName = fName;
        this -> lastName = lName;
    
        this -> age = age;
    }
    
    
    Person::~Person()
    {
    }
```
**The first constructor is the default constructor**. It has **no parameters** and because we have **not initialized 
our private member variables**, this constructor will do so with **the default values for data types of
those member variables**.

**The second constructor** takes two arguments and uses those to **initialize the first and last name member
variables in the class**.  Here is where you need to do a little research on the compiler you are using to determine
how the age variable will be initialized.  The reason is, because **we do not initialize age in the class** when 
we declared it and because **this constructor does not initialize it either**, if you try to use the age variable 
in an instance of Person, what result will you get?  The default constructor will initialize age to a default value 
(dependent on compiler), **but if you call the second constructor, age may or may not get initialized**.
