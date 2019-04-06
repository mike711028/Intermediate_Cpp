# Simple Pointers Demo
```cpp
#include <iostream>

int main()
{ 
	/**************
	*simple poitner*
	****************/
	
	int num = 3; // an integer variable initialized to the value 3

	// Create a pointer variable to an int type
	int *pNum;

	// Assign the address of num to pNum
	// so that it points to the num variable in memory
	pNum = &num;

	// Output the value of num
	std::cout << num << std::endl;

	// Output the address of num to compare
	// with the value in pNum
	std::cout << &num << std::endl;

	// Output the value stored in pNum
	std::cout << pNum << std::endl;

	return 0;
}
```
