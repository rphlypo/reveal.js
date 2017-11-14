## Part IV
### Flow control

````python
from math import log
from random import uniform
motivated = True
while motivated:
    print("Keep going ...")
    if -log(1 - random.uniform(0, 1)) > 5:
        break

````

---

### Exception handling

* Exception ("error") &rightarrow; if not handled, code execution is stopped

* handling Exceptions &rightarrow; `try` &#8230; `except` (&#8230; `finally`)

    ````python
    try:
        4 / 0
        print("All is well")
    except:
        print("Exception occurred")
    ````

    ````python
    try:
        L = [1, 2]
        L[5]
        print("All is well")
    except ZeroDivisionError:                          # filter ZeroDivisionError exception
        print("ZeroDivisionError Exception occurred")  
    except:                                            # others handled separately
        print("Any other exception lands here")
    ````

<div class="exo">Exceptions</div>

---

### logical predicates

* 2 boolean values : `True` and `False`

* comparison operators : `==`, `>`, `<`, `<=`, `>=`, `~=`, `is`

    * `==`: similar or equality in value

    * `is`: same thing

* negation: `not`, `^`


````python
print(True == 1)         # 1 is similar to a boolean True value
print(True is 1)         # however, it is not the boolean True value
print(True == 1 is True) # operator precedence?
````

---

### combining logical predicates

* joining by logical operations

    * `and`, `or`

---

### Logical predicates and the if-statement


* `if`-statement : `if` (&#8230; `elif`) (&#8230; `else`)

````python
weather = "rainy" # other possibilities: "sunny", "cloudy"
if weather is "sunny":         # Remark the colon ":"
    print("Sprinkle flowers")  # Remark the indentation : 4 spaces!
elif weather is "cloudy":      # elif is shorthand for else: if:
    print("Wait and see")
elif weather is "rainy":
    print("No need to water the plants")
````

---

### Logical operators

* logical unary operators: (`~`) `not`

* logical binary operators: `&` (`and`), `|` (`or`), `^` (`xor`)

    * composing logical predicates

````python
weather = "rainy"
temperature = "cold"
if weather is "rainy" and temperature is "cold":
    print("Be careful concerning black ice")
elif weather is "rainy" and temperature is "hot":
    print("Be careful for stormy weather coming up")
````

---

### Recall: operator precedence

| Operator | Description |
|:---------|:------------|
| ~        | complement |
| &        | bitwise __and__ |
| ^ &vert; | bitwise exclusive and regular __or__ |
| <= < > >= | comparison operators |
| <> == != | equality operators |
| is, is not | __identity__ operators |
| in, not in | membership operators |
|not, or, and | logical operators |

<div class="exo">logic</div>

---

### The `while`-statement

* Execute while statement is `True`

*

---

### `for`-statement

* `for` iterates over an __iterable__

* __iterables__: lists, dictionaries, tuples, &#8230; all objects that implement `__iter__`

    ````python
    L = list()
    print(L.__iter__())  # lists implement an iterator method
    ````

* iterating over elements of an iterator

    ````python
    L = ["spam", "eggs"]
    for word in L:        # does litterally iterate over elements in L
        print(word)
    for character in L[0]:
        print(character)
    ````
