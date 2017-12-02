## Part VI
### Functions

```python
def square(x):
    return x ** 2
s = [square(x) for x in range(1, 11)]
```

---

### What is a function ?

* a __function__ takes arguments, __operates__ on these, and (optionally) __returns__ a result

  * function declaration: __def__

  * function arguments: __positional__ or __keyword__-value

  * __return__ statement:  returns `tuple`

---

### function example

    ```python
    def pow(x, a=2):  # declaration
        """ takes the square value of its argument
        """
        y = x ** a    # operation
        return y      # return value
    ```

* possible function calls based on positional/keyword arguments

    ```python
    pow(3)         # uses default a=2
    pow(3, 3)      # only positional arguments
    pow(4, a=3)    # positional followed by keyword argument
    pow(x=5, a=3)  # only keyword arguments
    ```

---

### function arguments (1/2)

* `positional` or `keyword`

  * `positional` &rightarrow; __required__ at function call

  * `keyword`-`value` pairs

    * specify __default values__ at declaration

    * after `positional` arguments in calls

    * can be arbitrarily permuted, omitted, &#8230;

---

### function arguments (2/2)

* function __annotation__ (optional metadata)

  * `key: type` (positional) or `key: type = value` (keyword)
  * `-> type` for return value

    ```python
    def pow(x: float, a: int = 2) -> float:
        return x ** a
    ```

<div class="exo">arguments</div>

Note:
no incidence on the use of the function, merely code documentation

---

### function documentation

```python
def repeat(x: str, n: int = 2) -> str:
    """ this function repeats the argument x n times
    the argument x will first be converted to a string, then repeated
    """
    if not isinstance(n, int):
        raise TypeError("n must be an integer")
    return str(x) * n

print(repeat.__doc__)
print(repeat("spam"))
print(repeat("spam", n=4))
```

---

### recursions

* Fibonacci, factorial, Hermite functions, derangements

  * common divisor: recursion

<div class="exo">derangements</div>

---

### packing and unpacking

```python
def fun(a, b, c=1, d=2):
    print("{a}, {b}, {c}, {d}".format(a=a, b=b, c=c, d=d))
```

* iterables (list, dict, tuple, set) can be _unpacked_

  * list unpacking `*[5, 6]` &mapsto; `5, 6`

    ```python
    x = [5, 6]
    fun(*x) # evaluates fun(5, 6, c=1, d=2)
    ```

  * dict unpacking `**{c: 8, d: 9}` &mapsto; `c=8, d=9`

    ```python
    y = {'c': 8, 'd': 9}
    fun(*x, **y) # evaluates fun(5, 6, c=8, d=9)
    z = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
    fun(**z) # evaluates fun(a=1, b=2, c=3, d=4)
    ```

---

### argument passing through

```python
def basic_fun(x, y, u="a", v="b"):
    print("x={}, y={}, u={}, v={}".format(x, y, u, v))

def fun(a, b, *args, c=1, d=2, **kwargs):
    print("a={}, b={}, c={}, d={}".format(a, b, c, d))
    basic_fun(*args, **kwargs)
```

<div class="exo">passing</div>

---

### the anonymous function

* lambda = function with no name

    ```python
    sq = lambda x: x ** 2  # matlab: sq = @(x) x^2
    print(sq(3))
    ```

* comes in handy when a simple function is to be returned

    ```python
    def pow(a=2):
        return lambda x: x ** a
    cube = pow(3)
    print(cube(3))
    ```

---

### zipping and unzipping

* suppose we have two lists

    ```python
    x = [1, 2, 3]
    y = ["a", "b", "c"]
    ```

* zipping: list of tuples &mapsto; multiple lists

    ```python
    z = zip(x, y)
    # z = [(1, "a"), (2, "b"), (3, "c")]
    ```

* unzipping: multiple lists &mapsto; list of tuples

    ```python
    x, y = zip(*z)
    # x, y = [1, 2, 3], ["a", "b", "c"]
    ```

---

### name spaces / contexts (1/2)

* make  names __unique__ to avoid ambiguity

    * orange
    * unique? fruit or colour
    <!-- .element: class="fragment" data-fragment-index="1" -->

---

### name spaces / contexts (2/2)

* Python namespace = `dict`: name &mapsto; value

* namespaces

  * __built-in__ names (`while`, `def`, &#8230;): python start-up &rightarrow; quitting python
  * __global__ namespace of module: module `import` &rightarrow; script end
  * __local__ namespace of function: function call &rightarrow; return/`Exception`



---

### variable scope (1/2)

* _region_ of program where variable is unambiguous

  * access to variable without namespace prefix
  * defined statically, used dynamically

* different levels (as per search priority)

  * innermost scope: local variables
  * scopes of enclosing functions (__closure__): from nearest to furthest
  * next-to-last: module global variables
  * outermost: built-in [functions](https://docs.python.org/3.6/library/functions.html) and [types](https://docs.python.org/3.6/library/stdtypes.html)

---

### variable scope (2/2)

<div class="warning fragment fade-up" data-fragment-index="1">inner functions have access to the enclosing scope!</div>

```python
def func1(a):
    x = a
    def func2(b):
        y = a # "a" known in enclosing function
        x = b # x is local, now referring to b
        return x, y
    return func2
```

<div class="exo">nested functions</div>

---

### Closure

<div class="warning fragment fade-up" data-fragment-index="2">impure functions may have undesirable side effects</div>

* __pure function__: return value = $\mathcal f$(args)

  * does not depend on context
  * no side-effects
  * only local variables

    ```python
    def pure(x):
        print(x)

    def impure():
        print(x)

    x, y = "spam", "eggs"
    pure(x)
    pure(y)
    impure()  # result?
    ```
    <!-- .element class="fragment fade up" data-fragment-index="1" -->

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

    add = modifier(add)  # new "add"
    print(add(2, 3))
    ```

 <div class="see-also">See also [pep 318](https://www.python.org/dev/peps/pep-0318/)</div>

---

### About mutable arguments

```python
def change(x: int) -> None:
    """ change the value of x locally
    """
    x = 3

y = 5
change(y)
print(y)
```

```python
def popper(x: list) -> None:
    """ pop element from list, change x locally?
    """
    x.pop()

l = [1, 2, 3] # mutable
popper(l)
print(l)
```
<!-- .element class="fragment fade-up" data-fragment-index="1" -->

---

### To go further

* `global`

* `nonlocal` ($\geq$ Python 3)

<div class="see-also">[local, global, and nonlocal variables](https://www.python-course.eu/python3_global_vs_local_variables.php)</div>

---

### Exercise

Construct a graph, nodes are keys in a `dict`, edges are `dict` values. The graph is directed, and could be cyclic or acyclic.

Required functionalities on a graph `G` at `node`:

* get_descendants of a node at level $n$
* get_ancestors of a node (parent, &#8230;)
* get_siblings of a node (children of its parent node)
* "distance" between two nodes (_if b is child of a in an acyclic graph, dist(a, b) = 1, dist(b, a) = $+\infty$_)

Create a separate file `graphs.py` and import as module. Provide a possibility to have the file run in demo mode from the command line.

<div class="exo">graphs</div>
