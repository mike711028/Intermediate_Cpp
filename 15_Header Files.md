# Header Files
   + In C++, the common prctice is to create your classes as two separate files
   + one is header file which contains all the declarations found in the class file
   + the other is cpp file where there are all implementations of functions
   + #pragma once
   + static class

In C++, your code will often contain multiple class files.  As a review, recall that **class files 
allow you to model real-world objects in your code, and they also provide a container for functionality 
and behavior of coding structures**.

C++ applications typically consist of multiple files. Each of these files in your application may use
any or all of the class files that you define in your application.  If this is the case, that class file
definition must be the same in each and every file that uses it.  In order to avoid the duplication of
code, C++ uses the concept of a header file and the #include preprocessor directive.

**In C++, the common practice is to create your classes as two separate files.  The header file, with a .h extension
on the filename, is used to contain the declarations found in the class file.  Declarations include function prototypes 
and class constructors typically. The actual implementation of the code that performs the processing, exists in
the implementation file that has the .cpp or .c filename extension.**

To illustrate an example, let's go back to one of the examples found in the Introduction to C++ course on edX by Microsoft.  
In Module 4 we created functions that represented some common mathematical operations to calculate the power of a base
raised to an exponent, calculate the sine of an angle, and finally one to calculate the average of values in an array.
For this example, we will start to focus on building our own math library.

In C++, there is an existing l**ibrary called cmath**. **This library contains many common mathematical functions and we can
simply make use of cmath rather than create our own library**, but the exercise of doing so will serve a couple of purposes
in this course.  First, it will allow you to learn how to create class files with header files.  Next, you will learn 
how to deal with namespaces, which are covered later in this module, and finally, the culmination of the math functions 
that you will build will help to serve as a project for this course.

This sample code will provide a starter for you by demonstrating the use of header and implementation files for a class
called Math with a function for calculating the value of a base raised to an exponent.  We'll call this function pow.
## Math.h
```cpp
    // Math.h
    // Header file for the Math class

    #pragma once     // preproceoor directive tells the compiler to "only include this header once"

    // Math class definition
    static class Math
    {
        public:

        // given base and exponent, calculate value
        static int Math::pow(int base, int exp);
    };
```
Let's evaluate the code listings one at a time.  In the first section, Math.h, we see the header file for our Math class. 
Outside of the comments we see a line that indicates ```#pragma once```. **This is a preprocessor directive that tells
the compiler to only include this header once, regardless of how many times it has been imported in the program**.

Next we see the class definition, static class Math.  The ```static``` keyword needs a little explanation so let's get that out of the way first.  **When we declare a class as static, it is an indicator that we do not have to instantiate the class to use it in our program**.  For example, if Math were **not static**, before we could use it in our program, we would **need to create an instance of it** as shown here:
```cpp
    Math math = new Math();
    math.pow(2, 8);
```
For the Math class that we are creating in this course, we will consider it to **be a utility class** and therefore we want it to **be static so we don't have to create an instance each time** we want to use functionality in that class.

Next, our class definition continues with the opening curly brace and then the keyword ```public:```
**Anything after the public: keyword is considered to be of public visibility.  That is, it can be
called from other classes directly.**  

After public: we declare our function for generating the power of a base raised to an exponent.  Note that this method is also using the ```static``` designation. **In order to call the function from a static class, the function must also be static**.

Note that **the function contains no implementation details** however.  We simply indicate the data types of the parameters that we expect to use with this function.  As a matter of fact, we don't even have to use parameter names in this declaration at all, simply using ```static int Math::pow(int, int)```; is sufficient as we only need to indicate **the data types** that are expected by the function.

The last key piece to note about this declaration of the Math class is that we **end it with a semicolon after the closing curly brace**.  Most new programmers have a tendency to forget this.  Microsoft Visual Studio automatically adds the semicolon for you and many newer IDEs may also do the same.
