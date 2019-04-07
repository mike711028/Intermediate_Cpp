# Reference Types Demo1
demonstrate how the reference type affect num 
   + the reference type and variable affect each other
   + both of them are pointed to the same memory location
```cpp
#include <iostream>

int main()
{ 
	// declare and initialize an int variable
	int num = 3; 

	// create a reference type and assign num to it
	int &refNum = num;

	// output the value contained in num and refNum - they are the same value
	std::cout << "num contains " << num << std::endl;
	std::cout << "refNum contains " << refNum << std::endl;

	// increment refNum by 1
	refNum++;

	// output the new value of num and refNum - they are the same value
	std::cout << "num contains " << num << std::endl;
	std::cout << "refNum contains " << refNum << std::endl;

	// increment num by 1
	num++;

	// output the new value of num and refNum - they are the same value
	std::cout << "num contains " << num << std::endl;
	std::cout << "refNum contains " << refNum << std::endl;

	// output the memory address of refNum and num - they point to the same location
	// therefore they are the same value and the same "identity"
	std::cout << "refNum is located in " << &refNum << std::endl;
	std::cout << "num is located in " << &num << std::endl;

	return 0;
}
```
