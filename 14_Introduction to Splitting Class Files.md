# Introduction to Splitting Class Files
   + why would we split our classes into separate files?
   + programmer using class doesn't need to know how class works inside
   + like car's manual for drivers talk abouts how to drive this car
   + car's manual for car itself talks about how the engine works, electronics work

If an aspect of object-oriented programming is encapsulation, then **why would we split 
our classes into separate files?** Why not keep it all in one if we wish to "encapsulate" 
all there is about the class?

Recall that **a part of encapsulation is also data hiding**.  Think about your car for a bit as
we use it in an analogous way.  A car is a complex device that contains many different components.
**You are able to operate your car without the need to understand the complexities of the internal 
combustion engine or the radio electronics**.  You don't need that knowledge to be able to effectively
operate the car.

Likewise, a programmer using your class files **does not need to know how you have implemented 
your methods to achieve the functionality**.  In fact, perhaps you have a proprietary algorithm
for a spell checker that is really fast and you don't want anybody to know how it works.  
Users of that class also don't need to know how you implemented the spellchecker.  **They only need to 
know how to make use of it**.   "How to make us of it" comes in the form of the methods and their signatures.
As long as a user knows how to call your methods and what to expect as a return value, if any, 
they can use your class in their application.

In the car analogy, the owner's manual is analogous to the method signatures.  It specifies what
you can do to operate the car and how to interact with the car's "interface".  In the separation of 
class files, the header file (.h file), is analogous to the car's owner's manual.  It specifies what
"interface" elements are available (methods), providing information on how to use them.   There are
no implementation details in the header file just as there are no implementation details on the 
internal workings of your car's engine, in the owner's manual.
