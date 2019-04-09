# Dynamic Memory Allocation Demo
   + the size of a pointer is 4 bytes
   + ever time you call the "new" keyword, you also have to call the "delete" in the final
```cpp
// dynamic memory allocation
#include <iostream>

int main()
{
	// declare a pointer to int and allocate space for it
	// with the keyword "new"
	int *pInt = new int;
	// declare a pointer to double and allocate space for it 
	// with the keyword "new"
	double *pDouble = new double;

	// note: the pointers of type have to match the value you store 

	// store the value 3 in the memory location
	// pointed to by pInt
	*pInt = 3;
	// store the value 5.0 in the memoroy location
	// pointed to by pDouble
	*pDouble = 5.0;

	// output the values and memory addresses
	std::cout << "value stored at pInt = " << *pInt << ": memory address = " << pInt << std::endl;
	std::cout << "value stored at pDouble = " << *pDouble << ": memory address = " << pDouble << std::endl;

	std::cout << "size of pInt = " << sizeof(pInt);
	std::cout << "size of *pInt = " << sizeof(*pInt) << std::endl;

	std::cout << "size of pDouble = " << sizeof(pDouble);
	std::cout << "size of *pDouble = " << sizeof(*pDouble) << std::endl;

	// let's now clean up the memory we have used
	// and release that memory back to the operating system
	// otherwise our application has a memory leak
	delete pInt;
	delete pDouble;    //******key point*************//
}
```
