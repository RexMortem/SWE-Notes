References are an alias for existing variables - they are implemented by storing the memory address of the existing variable.

References differ from pointers in three key ways:
- a reference cannot do pointer-specific operations i.e. pointer arithmetic
- a reference essentially does dereferencing for you i.e. it acts exactly like the other variable
- always points to the same memory address i.e. it is a constant pointer

Bjarne Stroustrup has referred to a reference as "a restricted form of a pointer with some added syntactic sugar" ([Brief Intro to C++'s model for type and resource safety](https://www.stroustrup.com/resource-model.pdf)) which fits since:
- "restricted form" refers to being a constant pointer and not being able to do pointer arithmetic
- "added syntactic sugar" refers to doing dereferencing for you i.e. acting like a normal variable
## Sources

- https://www.geeksforgeeks.org/cpp/pointers-vs-references-cpp/
- [Brief Intro to C++'s model for type and resource safety](https://www.stroustrup.com/resource-model.pdf)