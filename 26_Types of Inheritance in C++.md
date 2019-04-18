# Types of Inheritance in C++
**C++ supports three different forms of inheritance, public, private, and protected**. 
Public inheritance describes how a derived class inherits all the member variables 
of a base class, both private and public, but **is only able to directly access the public 
members of the base class**.  **All members of the base class will retain their accessibility
in the derived class**.  Let's see an example.

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
In this example we have a Person class.  We are only listing the header file for this example
so as not to get bogged down in the implementation details just yet. Next we show the header file 
for a Student class.  **Note that the class name Student, is followed by a colon and then public
Person**.  This indicates that Student is a derived class of Person **using public inheritance**. 
Also note that the Student class contains a default constructor and a destructor.  
These are **separate from** the constructor and destructor for the Person class.

In the main.cpp file we declare a Student object called student1.  We then attempt to set the 
firstName variable to a value.  That line of code will generate a compiler error even though Student
has inherited the firstName member variable from Person.  The reason is the public inheritance
rule and the fact that **the firstName member variable is declared as private in Person**.  We'll 
cover how to access these variables in a little bit.  But notice that the ```student1.SayHello()``` 
function call will work as ```SayHello()``` is a public function.  Also note that in the Student.cpp class,
we attempt to use the ```firstName``` variable directly but the compiler will throw an error
against this line as well.

At this point you might be asking what use the private member variables are if they can't be accessed 
in a derived class.  The answer is a simple one in that we need to go back and think about encapsulation 
again.  **Providing public getters and setters for these private member variables is the proper way to
gain access to them from outside the class**. 

As mentioned, there are three types of inheritance in C++, public, protected, and private.  
This table explains the differences:

| Type of Inheritance| | |
|:---|:---|:---|
|public|protected|private|
|public members are public in derived class and can be accessed directly by **member functions and nonmember functions**|public members become protected members in derived class and can be accessed directly by **member functions**|public members become private in derived class and can be accessed directly by **member functions**|
|protected members are protected in derived class and can be accessed directly by member functions|protected members become protected members in derived class and can be accessed directly by member functions|protected members become private in derived class and can be accessed directly by member functions|private members are hidden in derived class and can be accessed by member functions though public or protected member functions|
|private members are hidden in derived class and can be accessed by member functions though public or protected member functions|private members are hidden in derived class and can be accessed by member functions though public or protected member functions|private members are hidden in derived class and can be accessed by member functions though public or protected member functions|

You can **initialize members of the base class by calling the base class constructor from your derived class**. 
It is recommended that you **make the call to the base class constructor as the first thing in your derived 
class to ensure that member variables in the base class are initialized** before they are accessed or used 
in the derived class.  The way to call the base class constructor from your derived class is demonstrated here.
```cpp
    Student::Student():Person("Tom", "Thumb") // initialize members of the base class
    {
    }
```
Note that immediately following the constructor for Student we see a colon and then a call to the Person 
constructor that accepts two arguments.  You can place any valid constructor here including one that 
takes no arguments, in which case the default constructor will be called. **Make it a good programming
practice to call the base class constructor in this manner to ensure your base class is initialized
before entering the body of your derived class**.  Other languages, such as Objective-C, require that
the base class is initialized before your derived classes.
