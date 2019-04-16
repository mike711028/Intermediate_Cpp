# Namespaces
**Class scope covered an important aspect of working in C++ with class files** but it isn't the only place
that scope comes into consideration.  C++ provides the standard template library (STL) that consists
of many classes and functionality.  It is conceivable that at some point in your career as
a software developer, you will create classes with names that conflict with those in the STL 
or with other code in a software project.  C++ uses namespaces to help resolve these conflicting issues.

**A namespace is a "scope container"** where you can place your classes, variables, or other identifiers to
**prevent conflicts with others**.  Anytime you want to reduce ambiguity or name collisions, you use the
namespace designator ahead of the identifier. You have already seen an example of this in the sample
code used so far in this course with std::cout.  the cout function exists in the namespace std.  
**The :: is the scope resolution operator and allows you gain access to the cout function in the std namespace**.

A contrived example where you're code also contains a function called cout might cause naming collisions and
ambiguity if your code required the use of std::cout and your cout function, unless you used namespaces. 
For example, **you might create a namespace for your code such as myNS.  In which case if you needed to use
both cout functions in your code, you would call the C++ version using std::cout and your version using myNS::cout. 
In this way, there is no ambiguity as to which function you are calling**.

C++ also permits the use of using statement to **help reduce the amount of code that you have to tyep
when classes are inside a namespace**. For example, you could place the following statement
at the top of your C++ file:
```cpp
using namespace std;
```
By doing this, **you can now simple use cout << "Hello"; in your code instead of typing the namespace and
scope resolution operator, saving you some keystrokes**.   However, take note that you cannot apply using
statement if there is a chance of ambiguity in the code.  For example, you could not use the following code:
```cpp
    using namespace std;
    using namespace myNS;
    
    int main()
    {   
        //you will be misunderstand which one is std or myNs
        cout << "std version of cout";  
        
        cout << "myNS version of cout";
    }
```
**The compiler has no way of knowing which cout to call in these two lines**. 
However you could theoretically write code such as:
```cpp
    using namespace std;
    
    int main()
    {
        // it is easy to tell which "cout" belongs to std or myNS
        cout << "std version of cout";
        
        myNS::cout << "myNS version of cout";
    }
```
**You can define your own namespace by using the keyword namespace**, followed by the chosen name 
and then **enclosing your code within the curly braces**. You also have the option of creating 
nested namespaces if you choose to provide more separation of identifiers in your code. 
Just remember that each namespace you nest, creates more code you need to type.  
A code sample demonstrates this.
```cpp
    namespace Microsoft
    {
        namespace Geometry
        {
            const double PI = 3.14159;
    
            double Area(double radius)
            {
                return PI*(r*r);
            }
        }
        
    }
```
## Example with using statement
```cpp
 using namespace Microsoft;     // only use namespace of "Microsoft"

    int main()
    {

        double radius = 12.5;

        double area = Geometry::Area(radius)   // still need to call namespace of Geometry
    
    }
```
## Example with using statement
```cpp
    int main()
    {

        double radius = 12.5;

        double area = Microsoft::Geometry::Area(radius);   
        // because don't use any "using namespace"
        // need to call "Microsoft" and "Geometry"
    }
```
**To keep the code simplified so we can focus on namespaces**, we have omitted classes and access modifiers. 
In the first code segment we have **created a namespace called Microsoft and a nested namespace
called Geometry**.  Within Geometry we have a constant to represent PI and a function that will 
calcuate the area of a circle given a radius.  **The second and third code segments show how we 
would make use of this namespace and function in code**.
