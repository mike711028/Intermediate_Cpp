# Inheritance Refresher

   + base classes, sub-classes
   + sub-classes can also have their own specific variables

**New classes can be derived from existing classes using a mechanism called "inheritance"**. 
Classes that are derived FROM are called "**base classes**" and derived classes are also 
known as **sub-classes**. The following is an example:
```cpp
class Vehicle     // base classes
{ 
    private:
       string Make;
       string Color;
       ...
}; 

class Car: Vehicle     // sub-classes
{ 
     // member list includes Make and Color
     // **other Car specific members would go here.**
};
```
In this example, Vehicle is the base class and Car is the derived class. Car automatically
inherits the Make and Color properties and **is also free to implement its own properties 
and methods that are specific for a Car**.
