## Part IV
### Flow control

```python
from math import log
from random import uniform
motivated = True
while motivated:
    print("Keep going ...")
    if -log(1 - random.uniform(0, 1)) > 5:
        break

```

---

### Exception handling

* Exception ("error") &rightarrow; if not handled, code execution is stopped

* handling Exceptions &rightarrow; `try` &#8230; `except` (&#8230; `finally`)

    ```python
    try:
        4 / 0
        print("All is well")
    except:
        print("Exception occurred")
    ```

    ```python
    try:
        L = [1, 2]
        L[5]
        print("All is well")
    except ZeroDivisionError:   # filter ZeroDivisionError exception
        print("ZeroDivisionError Exception")  
    except:                     # others handled separately
        print("Any other lands here")
    ```

<div class="exo">Exceptions</div>


---

### logical predicates

* 2 boolean values : `True` and `False`

* comparison operators : `==`, `>`, `<`, `<=`, `>=`, `~=`, `is`

* negation: `not`, `!`

---

### to be or not to be

```python
print(True == 1)         # 1 similar to boolean True
print(True is 1)         # it *is not* boolean True
print(True == 1 is True) # operator precedence?
```

| operator | meaning |
|:-------- |:----|
| `==` | similar _or_ equal in __value__|
| `is` | identical _or_ same __object__ |

---

### combining logical predicates

* joining statements &rightarrow; logical operations

    * `and`, `or`

    * bitwise `&` (and), `|` (or), `^` (xor)

```python
print(True and False)
print(True or True and False)  # operator precedence?
print(bin(0b1100 ^ 0b1010))    # binary
print(bin(12 ^ 10))            # dynamic
```

---

### implicit booleans

* predicates are used in flow control `if`, `while`

* all following statements evaluate to `True`

  ```python
  0 == False
  0 is not False
  1 == True
  1 is not True
  2 != True
  not 2 == True
  bool(2) == True
  bool(2) is True
  bool([1, 2]) is True
  bool([]) is False
  ```

<div class="exo">boolean logic</div>

---

### compound statements

* compound statement = header + suite

* separator `:`

* suite &rightarrow; __4 space__ indentation

  * header:<br />
    &bbrk;&bbrk;&bbrk;&bbrk;suite

```python
if True:
    print("execute me")
```

---

### flow control: `while`

* while <condition>:
  &bbrk;&bbrk;&bbrk;&bbrk;<suite>

* repeat <suite> as long as `bool(<condition>)` is `True`

```python
l = list(range(10))   # list with elements from 0 to 9
print(l)              
while l:              # bool of empty list is False, otherwise True
    element = l.pop() # pop last element from list (LIFO or stack)
    print('popped element {} from list'.format(element))
    print('list = {}'.format(l))
```

<div class="exo">buffer</div>

---

### flow control: `if`

* `if`-statement : `if` (&#8230; `elif`) (&#8230; `else`)

```python
weather = "rainy" # other possibilities: "sunny", "cloudy"
if weather is "sunny":         # Remark the colon ":"
    print("Sprinkle flowers")  # Remark the indentation : 4 spaces!
elif weather is "cloudy":      # elif is shorthand for else: if:
    print("Wait and see")
elif weather is "rainy":
    print("No need to water the plants")
```

---

### `for`-statement

* `for` iterates over an __iterable__ (an iterator)

* __iterables__: lists, dictionaries, tuples, &#8230; all objects that implement `__iter__`

    ```python
    L = list()
    print(L.__iter__())  # lists implement an iterator method
    ```

* iterating over elements of an iterator

    ```python
    l = ["spam", "eggs"]
    for word in l:         # does literally iterate over elements in l
        print(word)
    for character in l[0]: # does iterate over elements in l[0]="spam"
        print(character)
    ```

<div class="exo">iterables</div>

---

### iterables, iterators, generators, &#8230;

* __iterable__: returns its members one after another `__getitem__()`

* __iterator__: datastream returning member after member `__next__()`

* __generator__: function yielding a series of objects `yield`

---

![iterables, iterators, generators, &#8230;](../images/itergen.png)

Borrowed from [nvie.com](http://nvie.com/posts/iterators-vs-generators/)

<div class="exo">iterables</div>

---

### `range`

* `range(start, stop, step)`

    * `range(5)` &rightarrow; `[0, 1, 2, 3, 4]`

    * `range(2, 5)` &rightarrow; `[2, 3, 4]`

    * `range(0, 5, 2)` &rightarrow; `[0, 2, 4]`

* `iterator`, not an `iterable`

    * `list(range(5))` transforms into iterable

---

### list comprehension

* constructing lists from iterators

  ```python
  y = list()
  for x in range(10):
      y.append(x ** 2)
  z = [x ** 2 for x in range(10)] # z = y
  ```

* more involved with conditional statements

  ```python
  w = [(x, y) for x in [1, 2, 3] for y in [1, 2, 3] if x < y]
  t = [(x, y) if x < y else (x, ) for x in [1, 2, 3] for y in [1, 2, 3]]
  ```

---

### `break`, `continue`, and `pass`

* `break`: breaks out of innermost `for`- or `while`-loop

    * `else` executed if no break occurs

* `continue`: continues with next iteration of loop

* `pass`: does nothing (but syntactical necessity)

```{python}
try:
    1/0
except ZeroDivisionError:
    pass
finally:
    print("all is ok, we do as if nothing happened")
```
<div class="exo">primes</div>
