Firstly, [[Objects#Everything is an Object|everything in Python is an object]].

Secondly, more accurately, everything in Python is an object or a **reference** to an object. For instance:

```python
x = 5
```
Here, `5` is an object. `x` is a reference to the object `5`.

Thirdly, assignment (`=`) never copies values. It simply references (binds) and changes what your reference is referencing (rebinding). For example:
```python
a = [1,2]
a[0] = 5
```
`a[0] = 5` here simply rebinds `a[0]`- it now references the object `5` instead of the object `1`. 

Fourthly, passing arguments in Python is just assignment. 

Putting it all together, passing arguments in Python is by reference. However, it may have the appearance of having call by value when dealing with passing immutable values (such as ints, tuples, strings) - see [[Objects#Mutable and Immutable Objects]].
## Sources

- https://nedbatchelder.com/text/names.html (a good source for programmers who haven't experimented with Python)