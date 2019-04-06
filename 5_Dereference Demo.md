# Dereference Demo
```cpp
#include <iostream>

int main()
{ 
	/********************
	*dereference operator*
	*********************/
	
	int num = 3; // declare an integer variable and assign it a value

	int *pNum = &num;  // declare a pointer to an int and assign the address of num

	std::cout << pNum << std::endl;  // output the address of the pointer pNum ( address of num)

	// in this output statement, we use the dereference operator
	// it is the same operator used to indicate a pointer variable
	// as well as the multiplication symbol
	// which demonstrates operator overloading in C++
	// the output of this statement will be the value that is stored in num
	// we get the value indirection because the dereference operator
	// "de-references" the memory address to get at the underlying value stored there
	std::cout << *pNum << std::endl;

	// here will show how using dereference operator allow us 
	// to change the underlying value stored in num
	*pNum = 45;
	std::cout << *pNum << std::endl;
	std::cout << num << std::endl;

	return 0;
}
```
