# Allocating Memory
Allocating memory during runtime of an application is a common requirement. For example, you may not
know how many objects your application will need until the application is running.  **Allocating memory
to newly created objects at runtime makes use of pointers. This is the only way to gain access to memory 
for new objects when your application is running**. A small code sample will serve to illustrate this.
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
```
In this code sample, we see the use of the keyword new.  We also notice that, unlike in previous code samples 
with pointers, we didn't assign a variable to the pointer.  Instead, we told the compiler that we wanted to 
create a pointer to an int and then, when the program runs, to **dynamically assign some memory to hold an 
int value**.   We won't know what the memory address is until run time. We also did the same thing with
a pointer to double.

**We use the dereference operator to assign a value to the memory location pointed at by pInt and pDouble**.  
Again, **we have no idea what these memory addresses are** because they are allocated dynamically during runtime.  
The application requests some memory large enough to store an int value in and a double value.   Because an int, 
at least on the computer used for this course authoring, is 4 bytes and a double is 8 bytes, **the operating system 
allocates 4 bytes for a value to be stored, starting at the memory address in pInt**, and 8 bytes for the double value, 
to be stored in the memory of the computer, starting at the address in pDouble.

**It's very important to note, at this point, that pInt and pDouble are both the same size, in this case 4 bytes, 
but the memory space storing the values are 4 bytes and 8 bytes respectively.  But how can that be when one is
an int and the other is a double?**

**Quite simply, a memory address is a fixed size on a specific computer architecture. In this case it takes 4 bytes
to hold a memory address . The start of that memory address is what pInt and pDouble point to. The computer must know 
the data type in order to work out how much total memory is assigned to that location.**

As a concrete example, when this code was executed, the memory address for pInt was set to 00F1FBA8 and the ending 
memory address was 00F1FBAC and the starting address for pDouble was 00F21330 with an ending address of 00F21338.  
Doing a little hexadecimal math **we can see that pInt indeed spans 4 bytes and pDouble spans 8 bytes**.  Recall that 
in hexadecimal, we only go as high as 9 then move on to letters so that we would count from the ending 8 in pInt to C 
as in 9, A, B, C.  That's 4 positions. (in order to get to the ending memory address for these pointers, **simply 
increment the pointer as in pInt++, and the computer will increase the memory address by the number of byes indicated 
by the data type pointed to**).
