# Dynamic Memory Allocation and Classes
When your application is coded, you may have no idea how many Person objects you will 
need during the program's lifetime.  As a result, it is likely not possible for you to create
sufficient Person objects in code and let the compiler determine how much memory is required
for these objects at compile time. Chances are, you will **be creating many objects dynamically 
as your application code executes**. In order to do so, the application must request memory from 
the operating system as the application is executing, (dynamically).  

This topic discusses **the importance of two C++ keywords** ```new``` and ```delete```.  The keyword new is used
to allocate memory for an object at runtime and delete is used to release that memory.  This is also 
**where the constructors and destructors play a big part**.   You will also need to change the way you
call functions and work with the objects, and we'll cover that in this topic.

Dynamically allocating memory to hold an object is done with the new keyword. Using the new keyword means
that you must be making the assignment to a pointer of the correct data type.  The following code shows
a valid and an invalid use of the new keyword.
```cpp
    Person *pOne = new Person();

    Person per = new Person();  // error, "nrw" requests a pointer
```
**In the first line**, we declare a pointer called pOne that will hold the memory address of a Person object 
that will reside in an area of computer memory known as the heap.  When the new keyword is encountered,
the computer will set aside enough memory to hold a Person object in memory and assign that memory
address to the variable pOne.   We have not created an actual object in memory yet, we have simply 
asked the computer to allocate sufficient memory to store the object. **How does it know how much
memory is needed?**  In the case of our Person class, the size is determined by looking at all the member
variables, (the classes data), and based on the data types, **it determines the maximum amount of memory
required for the object**.  **No values are assigned at this time either so the compiler uses the maximum 
size of the specified data type for each member variable**.

What happens if our class contains other classes nested within it?  The compiler will look at **all the members
of those classes as well and allocate sufficient memory for them as well**.

**In the second line** of code above, we simple declare a variable to be of type Person and call it per.  However,
the use of the new keyword **is not legal here**, at least when using Microsoft Visual Studio 2015.  The error 
message returned from the compiler indicates that "No suitable constructor exists to convert from Person * to Person." 
**This clearly indicates that new is seeking a pointer and not an object variable**.

Once you have used the new keyword to dynamically create an object in memory, the way in which you access the member
variables and functions is a little different than simply using the dot operator like you might be familiar
with in other languages such as C# or Java.  **You will now need to use the arrow selection operator to access
the members of the class, as shown in the following code sample**.
```cpp
    Person *pOne = new Person("Gerry", "O\'Brien");
    std::cout << pOne->GetLastName() << endl;
```
In the first line of code, we declare a pointer * pOne and assign it a memory address using the new keyword. 
The compiler sets aside memory for the object and assigns the first and last name values to the member variables 
using one of the constructors in our Person class.  (Refer to previous code samples for the constructors).  
Because the object has been dynamically allocated with the new keyword, we must use the arrow selection operator
and we see that in the second line of code where we access the GetLastName() member function to retrieve 
the value stored in the object pointed to by pOne.

