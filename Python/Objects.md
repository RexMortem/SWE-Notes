Objects.
## Everything is an Object

Even literals (like ints, bools), functions, and lambda expressions are objects (unlike other languages).

You can see this yourself in Python by using the **dir()** method which outputs all the attributes (methods, properties etc) of an object.

```python
print("INT LITERAL: ", dir(5), "\n\n")

def x(a, b):
    return a + b

print("FUNCTION: ", dir(x), "\n\n")

l = lambda x: x+1

print("LAMBDA EXPRESSION: ", dir(l), "\n\n")
```
