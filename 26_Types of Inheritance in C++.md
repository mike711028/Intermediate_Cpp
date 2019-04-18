# Types of Inheritance in C++
**C++ supports three different forms of inheritance, public, private, and protected**. 
Public inheritance describes how a derived class inherits all the member variables 
of a base class, both private and public, but is only able to directly access the public 
members of the base class.  All members of the base class will retain their accessibility
in the derived class.  Let's see an example.

## Person.h
```cpp
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
## Student.h
```cpp
 #pragma once
    #include "Person.h"

    class Student :
        public Person
    {
    public:
        Student();
        ~Student();
    };
```
## Student.cpp
```cpp
 #include "stdafx.h"
    #include "Student.h"


    Student::Student()
    {
    }

    Student::~Student()
    {
    }

    // this line will cause a compiler error    
    firstName = "Tom";
```
## Main.cpp
```cpp
    #include "stdafx.h"
    #include "Person.h"
    #include "Student.h"

    int main()
    {

        Student student1;

        // this line will generate a compiler error
        student1.firstName = "Tom";

        // this line is ok
        student1.SayHello();


        return 0;
    }
```
