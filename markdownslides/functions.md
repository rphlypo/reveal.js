## Part III
### Functions and flow control

~~~~{.python}
def square(x):
    return x ** 2
for x in range(6)
    print("{x} * {x} = {y}".format(x=x, y=square(x)))
~~~~

---

### What is a function

* a __function__ takes arguments, __operates__ on these, ans (optionally) __returns__ a result

  * function declaration: __def__

  * function arguments: keys or key-value pairs 

~~~~{.python}
def square(x):  # declaration
    """ takes the square value of its argument
    """
    y = x ** 2  # operation
    return y    # return value
~~~~

---

### printing a variable's content

* the `__repr__` attribute (more on this later)

  Printing an object's value _calls_ its `__repr__` attribute

~~~~{.python}
x = 7
x.__repr__()
print(x)
y = 7.000
y.__repr__()
print(y)
l = [1, 3, 5]
l.__repr__()
print(l)
~~~~
