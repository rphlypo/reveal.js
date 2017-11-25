## Part VII
### Classes and Objects

```python
class Program(object):
    """ nodes are functions, data are variable pipes
    """
    def __init__(self, nodes, data):
        self.nodes = nodes
        self.data = data  

    def __call__(self, entry):
        return self.traverse_graph(entry)
```

---

### `class` and `object`

* `class`

    * blueprint

    * define attributes / methods (functions)

* `object` or `instance`

    * concrete realisation / instance of `class`

---

### `class` and `object`

* examples:

| `class` | `instance` |
|---:|:---|
| movie | Monty Python and the Holy Grail |
| cat | the albino cat of the neighbours |
| person | you |

---

### `__init__`

* most important method of class

* called upon creation of object

* first argument: _self_ (auto-reference to __instance__)

* equivalent to __constructor__ in other languages

    ```python
    class Graph:
        def __init__(self, nodes, edges):
            self.nodes = nodes
            self.edges = edges
    ```

<div class="exo">class declaration</div>

---

### `attributes`

* class attributes vs. regular attributes

* class attribute = `constant` for the __class__

* regular attribute = `variable` for the __class__, `constant` for an __instance__

    ```python
    class Quadrilateral:
        n_sides = 4                # class attribute
        def __init__(self, sides): # __init__
            self.sides = sides     # instance attribute

        def circumference(self):   # instance method
            circumference = 0
            for s in self.sides:
                circumference += s
            return circumference
    ```

---

### creating and using instances

```python
q = Quadrilateral((1, 2, 3, 4))
print(q.n_sides)     # prints "4"
print(q.sides)       # prints "(1, 2, 3, 4)"
print(q.circumference())
print(q.valid_)      # prints "True"
```

<div class="exo">attr &amp; methods</div>

---

### inheritance

* can be considered as `class` / `subclass` hierarchy

```python
class Rectangle(Quadrilateral):
    def __init__(self, sides):
        self.sides = [sides[0], sides[1]] * 2

    # no need to define circumference and n_sides --> inherited from Quadrilateral !
```

* python offers _multiple_ inheritance

<div class="exo">inheritance</div>

---

### `super()`

* `super` is the parent class

* `super().method()` calls method from parent

    ```python
    class A:
        def __init__(self, x):
            self.x = x
        def dosomething(self):
            print(self.x)

    class B(A):
        def __init__(self, x):
            self.x = x
        def dosomething(self):      # priority
            print(self.x * 10)
            super().dosomething()   # prints self.x
    ```

---

### magic methods

* `__init__` __is__ a magic method

* many others: __overloading__ operators

---

### magic methods

| operator | magic |
|:---:|:---:||:--:|:---:|
| `+`, `-`, `*`, `/` | `__add__`, `__sub__`, `__mul__`, `__truediv__` |
| `//`, `%`, `**` | `__floordiv__`, `__mod__`, `__pow__` |
| `&`, <code>&#124;</code>, `^` | `__and__`, `__or__`, `__xor__` |
| `<`, `>`, `<=`, `>=` | `__lt__`, `__gt__`, `__le__`, `__ge__` |
| `==`, `!=` | `__eq__`, `__ne__` |
| `in`, `len` | `__contain__`, `__len__`  |
| `[]`, `()` | `__getitem__`, `__call__` |
| output of `print` | `__repr__` |

Note:
the `__int__`, `__float__`, `__str__` tells how to cast the object

---

### private methods and attributes

* weakly private: starts with `_`

  * mainly convention, little effect

* strongly private: starts with `__`

  * attribute is not readily available

* __goal__: hide attributes/methods for externals

---

### class methods

* method: instance &mapsto; `self`

* __class method__: class &mapsto; `cls`

```python
class Rectangle:
    def __init__(self, width, height):
        self.width, self.height = width, height

    def area(self):
        return self.width * self.height

    @classmethod
    def new_square(cls, side):
        return cls(self, side, side)


sq = Rectangle.new_square(5)
print(sq.area)
```

---

### static methods

* similar to class methods

* do not receive extra arguments (`cls`, `self`)

* identical to normal functions in behaviour

```python
class Rectangle:
    def __init__(self, width, height):
        self.width, self.height = width, height

    @staticmethod
    def validate_lengths(width, height):
        numeric = (int, float)
        if not (isinstance(width, numeric) and
                isinstance(height, numeric)):
            raise ValueError("Lengths must be numerical values")

Rectangle.validate_lengths(2, 3)
```

<div clas="exo">staticmethod</div>

---

### property or read-only attribute

* `@property` decorator &rightarrow; calls method() as attribute

* makes "attribute" read-only

```python
class Rectangle:
    def __init__(self, width, height):
        self.width, self.height = width, height

    @property
    def area(self):
        return self.width * self.height

r = Rectangle(2, 5)
print(r.area)    # and not r.area() !
```

<div class="exo">property</div>

---

### getter / setter

<div class="warning fragment fade-up" data-fragment-index="1">not pythonic! avoid whenever possible</div>

```python
class Rectangle:
    def __init__(self, width, height):
        self.width, self.height = width, height

    @property
    def area(self):
        return self.width * self.height

    @geometry.setter
    def geometry(self, g="Euclidean"):
        self.g = g

    @geometry.getter
    def geometry(self):
        return self.g

r = Rectangle(2, 5)
print(r.area)    # and not r.area() !
```

---

### Exercise

Implement a `computation graph`, where each node is an addition, subtraction, multiplication, or division. Edges in the graph correspond to data exchanges (input/output).

1. computations are carried out in the order of appearance in the graph
2. computations respect the mathematical priority rules

<div class="exo">computation graph</div>
