# Class Destructors
Now that we know how to create objects, and we know that they consume memory while they
hang around in our application's executable memory space, we also need to know **how to release
that memory** when we no longer require the objects.  **We do so with the use of a destructor**.

In the previous code samples, you may have noticed that the destructor looked a lot like the 
default constructor, only **preceded with a tilde (~)**.  While it looks similar to the a constructor,
having no return type and the same name as the class, except for the tilde, it's important to
note that **a destructor cannot have any arguments passed in to it**.  Therefore, when writing your 
own destructors, **you should not place arguments between the parentheses for the destructor**.

The compiler will handle the actual calling of the destructor when your object expires or the application
is closing.  If you choose, you can place code inside the destructor.  One reason you may want to do this
is to ensure that any resources used by the object, that may not be destroyed or cleaned up, are taken
care of in your object's destructor code.
