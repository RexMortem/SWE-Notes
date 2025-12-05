Objects.
## Everything is an Object*

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

\*Technically it might be more accurate to say **everything is an object or a reference to an object**. In the above, `l` is a reference to the lambda expression `lambda x: x+1` (which is an object).
### Mutable and Immutable Objects

This might not seem to make sense since you can do things like:
```python
x = (x + 1) * 3
```
However this is actually a bunch of operations that each return a new object.
So `(x + 1)` here returns a new int object. `* 3` also returns a new int object. 

Ints are an example of **immutable** objects - objects that cannot be changed. Immutable objects are very safe to use since they can't switch up on you. Tuples are also immutable objects:
```python
coord = (15, 16)
coord[0] = 5 # ILLEGAL OPERATION: tuples are immutable!
```
When you think you've changed an immutable object, you've really just created a new object.

When you use **mutable** objects (can be changed), you have to remember that multiple references may point to the same object (so changing it through one reference will change it for every other reference pointing to that object). 

An example involving mutable objects:
```python
aList = [3, 6, 10, 15]
sameList = aList

aList[0] = 500
print(sameList) # [500, 6, 10, 15]
```
Here, `aList` and `sameList` point to the same (mutable) object. Changing it via any of the references (`aList`, `sameList`) will change it for all references.

## Sources
- https://nedbatchelder.com/text/names.html (a good source for programmers who haven't experimented with Python)