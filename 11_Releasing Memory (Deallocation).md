# Releasing Memory (Deallocation)
One final point that we need to make in your use of pointers and dynamic memory allocation
is **releasing memory**. **Each time you allocate memory in your application, it is reserved by the 
operating system so that other applications cannot access that memory address**.  This has security
implications as well as importance for separation of application code to prevent system wide crashes
if an errant application behaves badly.

**If you do not release the memory in your application, the operating system will not reclaim it and 
this is known as a memory leak**.  It is compounded if your application continues to dynamically allocate
memory and doesn't release it.

The simple way of releasing your allocated memory is to use the keyword **delete**.  For the sample code above,
you would make use of the delete keyword as demonstrated here.
```cpp
    // declare a pointer to int and allocate space for it
    // with the keyword new
    int *pInt = new int; 

    // declare a pointer to double and allocate space for it
    // with the keyword new
    double * pDouble = new double;

    // store the value 3 in the memory location
    // pointed to by pInt
    *pInt = 3; 

    // store the value 5.0 in the memory location
    // pointed to by pDouble
    *pDouble = 5.0;

    delete pInt;
    delte pDouble;
```
We have simply issued the delete keyword in reference to each pointer we have in the application code.
The operating system will now **reclaim the memory used by those pointers and our code no longer has a memory leak**.
Use whatever method makes sense to you to ensure that memory is released like using a delete keyword for every new keyword.
