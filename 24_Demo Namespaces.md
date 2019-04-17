# Demo Namespces

   + ensure that the value for the exponent is positve

## math.h(using namespace)
```cpp
#pragma once

namespace MyMath
{
	static class math
	{
	public:
		math();
		~math();

		static int pow(int, int);

	};
}
```
## math.cpp(implement file)
```cpp
#include "math.h"
#include <iostream>
MyMath::math::math()
{
}

MyMath::math::~math()
{
}

int MyMath::math::pow(int value, int exp)
{
	std::cout << std::endl << "In MyMath::math::pow" << std::endl;

	int result = 1;

	if (exp > 0)
	{
		for (int i = 0; i < exp; i++)
		{
			result = result * value;
		}
	}
	else
	{
		std::cout << "Enter only positive value for the exponent" << std::endl;
		result = 0;
	}
	return result;
}
```
## demo file
```cpp
#include <iostream>
#include "math.h"
int main()
{
	

	int a = MyMath::math::pow(2, -12);
	
	std::cout << a << std::endl;

	return 0;
}
```
