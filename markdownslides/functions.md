## Part VI
### Functions

~~~~{.python}
def square(x):
    return x ** 2
s = [square(x) for x in range(1, 11)]
~~~~

---

### What is a function

* a __function__ takes arguments, __operates__ on these, and (optionally) __returns__ a result

  * function declaration: __def__

  * function arguments: __positional__ or __keyword__-value

  * `return` statement (returns tuple)

---

### function example

```python
def pow(x, a=2):  # declaration
    """ takes the square value of its argument
    """
    y = x ** a    # operation
    return y      # return value
```

* possible function calls

```python
print(pow(3))         # uses default a=2
print(pow(3, 3))      # only positional arguments
print(pow(4, a=3))    # positional argument followed by keyword argument
print(pow(x=5, a=3))  # only keyword arguments
```

---

### function arguments

* either `positional` or `keyword`

  * `positional` &rightarrow; required at function call

  * `keyword`-`value` pairs

    * specify default values at declaration

    * after `positional` arguments in calls

    * can be arbitrarily permuted, omitted, &#8230;

* can be annotated (optional metadata)

  * `key: type` (positional) or `key: type = value` (keyword)

  * `-> type` for return value

<div class="exo">derangements</div>

---

# function documentation

```python
def repeat(x: str, n: int = 2) -> str:
    """ this function repeats the argument n times
    the argument x will first be converted to a string, then repeated
    """
    if not type(n) is type(int()):
        raise TypeError("n must be an integer")
    return str(x) * n

print(repeat.__doc__)
print(repeat("spam"))
print(repeat("spam", n=4))
```

---

### packing and unpacking

```python
def fun(a, b, c=1, d=2):
    print("{a}, {b}, {c}, {d}".format(a=a, b=b, c=c, d=d))
```

* iterables (list, dict, tuple, set) can be _unpacked_

  * `*[5, 6]` &rightarrow; `5, 6`

    ```python
    x = [5, 6]
    fun(*x) # evaluates fun(5, 6, c=1, d=2)
    ```

  * `**{c: 8, d: 9}` &rightarrow; `c=8, d=9`

    ```python
    y = {'c': 8, 'd': 9}
    fun(*x, **y) # evaluates fun(5, 6, c=8, d=9)
    z = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
    fun(**z) # evaluates fun(a=1, b=2, c=3, d=4)
    ```

---

### passing through

```python
def fun(a, b, *args, c=1, d=2, **kwargs):
    print(a + b + c + d)


---

### the anonymous function

* lambda = function with no name

    ```python
    sq = lambda x: x ** 2  # matlab: sq = @(x) x^2
    print(sq(3))
    ```

* comes in handy when a function is to be returned

    ```python
    def pow(a=2):
        return lambda x: x ** a
    cube = pow(3)
    print(cube(3))
    ```

---

### name spaces / contexts

* make  names __unique__ to avoid ambiguity

    * orange

    * unique? fruit or colour
    <!-- .element: class="fragment" data-fragment-index="1" -->

* Python namespace = `dict`: name &mapsto; value

* namespaces

  * __built-in__ names (`while`, `def`, &#8230;): python start-up &rightarrow; quitting python

  * __global__ namespace of module: module `import` &rightarrow; script end

  * __local__ namespace of function: function call &rightarrow; return/`Exception`



---

### variable scope

* _region_ of program where variable is unambiguous

  * access to variable without namespace prefix

  * defined statically, used dynamically

* different levels (as per search priority)

  * innermost scope: local variables

  * scopes of enclosing functions (__closure__): from nearest to furthest

  * next-to-last: module global variables

  * outermost: built-in <a href="https://docs.python.org/3.6/library/functions.html">functions</a> and <a href="https://docs.python.org/3.6/library/stdtypes.html">types</a>

```python
def func1(a):
    x = a
    def func2(b):
        y = a # "a" known in enclosing function
        x = b # x is local, not referring to b
        return x, y
    return func2
```

<div class="exo">nested functions</div>

---

### Closure

<div style="background-color:#b3d9ff; text-align:center; font-weight: bold;">inner functions have access to the enclosing scope!</div>

* __pure function__: return value = $\mathcal f$(arguments)

  * no side-effects

  * no other than local variables

<div class="exo">variable scope</div>

---

### Function decorators

* define $\mathcal g: \mathcal f\mapsto \mathcal h$

* goal: extend/modify functionality of $\mathcal f$

```python
def modifier(func):
    def wrapper(x, y):
        return func(x, -y)
    return wrapper
def add(x, y):
    return x + y
add = modifier(add)  # new function, but refer to it as "add"
print(add(2, 3))
```

 <div class="see-also">See also <a href="https://www.python.org/dev/peps/pep-0318/">pep 318</a></div>

---

### About mutable arguments

* Surprising side effects (not a pure function!)

```python
def popper(x):
    """ pop element from list, do not return the list
    """
    x.pop()

l = [1, 2, 3] # mutable
popper(l)
print(y, l)
```

---

### To go further

* `global`

* `nonlocal` (Python 3 and up)

<div class="see-also">See also <a href="https://www.python-course.eu/python3_global_vs_local_variables.php">local, global, and nonlocal variables</a></div>

---

### Exercise

The goal is to construct a graph, where the nodes are keys in a dictionary (using strings, for instance), the edges are encoded in the node values. The graph is directed, and could be cyclic or acyclic.

Required functionalities on a graph `G` at `node`:
* get_descendants of a node at level $n$
* get_ancestors of a node (parent, &#8230;)
* get_siblings of a node (children of its parent node)
* "distance" between two nodes (_if b is child of a in an acyclic graph, dist(a, b) = 1, dist(b, a) = $+\infty$_)

The functions should be written in a separate file `graphs.py` and imported as a module. Providing a possibility to have the file run in demo mode from the command line will be appreciated.

<div class="exo">graphs</div>
