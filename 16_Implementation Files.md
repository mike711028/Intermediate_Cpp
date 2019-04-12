# Implementation Files
Let's now look at the implementation file, the one with the .cpp extension and the file
that **contains the actual functionality**.

## Math.cpp
```cpp
    #include "stdafx.h"
    #include "Math.h"       // include header file is important!

    int Math::pow(int base, int exp)
    {
        int result = 1;

        for (int i = 0; i < exp; i++)
        {
            result = result * base;
        }

        return result;
    }
```
## MathTest.cpp
```cpp
    // MathTest.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h" 
    //"stdafx.h" 並為先行編譯型別加入包含檔。任何類型的先行編譯檔，包括標頭檔，都支援較快的編譯時間，
    //方式是限制編譯為只需要編譯的檔案。一旦建置專案，您會發現後續組建的組建時間會加快許多，這是因為先行編譯標頭檔之故。
    #include "Math.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        int result = Math::pow(2, 10);
    
        cout << result << endl;

        return 0;
    }
```
Let's evaluate the code listings one at a time.  In the first section we saw Math.h, the header file for our Math class.  In this section, we discuss the Math.cpp file.  This is the **implementation file** for the Math class.  

We open the class file with two #include statements.  One includes the stdafx header file and the second brings in the Math header file.  The stdafx.h file is the precompiled header directive that is used in Visual Studio but some other compilers also make use of it.  Next, we include ```Math.h``` because **the compiler needs to know what functions are part of this class**.  Recall the discussion about function prototypes.  These now **exist in the header file and not in the .cpp file**.

The rest of the class contains the implementation details for calculating the power function.  The function name looks a little different now.  Instead of just the function name, we are using ```Math::pow``` as the function name.  This is using the concept of a **scope resolution operator (::)**.  There are a couple of uses for the scope resolution operator, and it will be covered again in the discussion on namespaces but, in this instance, it is required to call static members of the class.  

The code in this function implements the functionality using a for loop to calculate the base raised to the exponent provided.  Also note that there is no semicolon at the end of the closing curly brace.

Finally, in MathTest.cpp we see our standard main() function that we use for testing purposes.  Some refer to this as a driver program used for testing our code.  In the main() function, declare an int variable called result and assign it the value that is returned from the pow function in Math.   Note the use of the scope resolution operator again (::) and that **we did not create an instance of the Math class but simply called the function directly on the class itself.  This is an example of a static class in action**.

So **how exactly does the header file factor into our code?**  It is a concise method of describing what the class is intended to do.  In other words, **it provides a look into the functions that exist in a class without concerning ourselves with the implementation details of those methods**.  It also provides us with a mechanism to help reduce coding bugs by having the compiler catch omissions and misuses of the class and its components.  However, once again think about declaring a class in your applications main file, the one that includes main().  In our sample code with the Math class, if we did not include the Math.h file directive in MathTest.cpp, then MathTest will have no knowledge of Math.cpp and the compiler will generate an error.  By placing the include directive in MathTest.cpp, the compiler will actually make a copy of the contents of Math.h inside MathTest.cpp, which will mean that the function declarations will be included, and the compiler will understand the Math class.
