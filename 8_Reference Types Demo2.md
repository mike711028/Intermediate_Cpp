# Reference Types Demo2
```cpp
#include <iostream>

// function prototype. Normally found in header files
// but used here to keep the simple code simple
void passByValue(int num1);
void passByRef(int &);
int main()
{ 
	int num = 3;
	std::cout << "In main()" << std::endl;
	std::cout << "Value of num is " << num << std::endl;

	passByValue(num);
	//passByRef(num);

	std::cout << "Back in main and the value of num is " << num << std::endl;

	return 0;
}

void passByValue(int num1)
{
	std::cout << "In passByValue()" << std::endl;
	std::cout << "Value of num1 is " << num1 << std::endl;

	// modify num1, won't impact num
	num1++;

	std::cout << "num1 is now " << num1 << std::endl;
}

void passByRef(int &num1)
{
	std::cout << "In passByRef()" << std::endl;
	std::cout << "Value of num1 is " << num1 << std::endl;

	// modify num1, will impact num
	num1++;

	std::cout << "num1 is now " << num1 << std::endl;
}
```
