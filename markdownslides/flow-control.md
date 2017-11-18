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

    * `is`: same thing (identity)

* negation: `not`, `!`


````python
print(True == 1)         # 1 is similar to a boolean True value
print(True is 1)         # however, it *is not* the boolean True value
print(True == 1 is True) # operator precedence?
````

---

### combining logical predicates

* joining statements &rightarrow; logical operations

    * `and`, `or`

    * bitwise `&` (and), `|` (or), `^` (xor)

````python
print(True and False)
print(True or True and False)  # operator precedence?
print(bin(0b1100 ^ 0b1010))    # binary
print(bin(12 ^ 10))            # dynamic

````

---

### implicit booleans

* predicates are used in flow control `if`, `while`

* all following statements evaluate to `True`

````python
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
````

<div class="exo">boolean logic</div>

---

### compound statements

* compound statement = header + suite

* separator `:`

* suite &rightarrow; __4 space__ indentation

* header:<br />
&bbrk;&bbrk;&bbrk;&bbrk;suite

````python
if True:
    print("execute me")
````

---

### flow control: `while`

* repeat as long as conditional statement evaluates to `True`

    * actually `bool(condition)`

    ````python
    l = list(range(10))   # list with elements from 0 to 9
    print(l)              
    while l:              # bool of empty list is False, otherwise True
        element = l.pop() # pop last element from list (LIFO or stack)
        print('popped element {} from list'.format(element))
        print('list = {}'.format(l))
    ````

<div class="exo">buffer</div>
---

### flow control: `if`


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

### `for`-statement

* `for` iterates over an __iterable__ (an iterator)

* __iterables__: lists, dictionaries, tuples, &#8230; all objects that implement `__iter__`

    ````python
    L = list()
    print(L.__iter__())  # lists implement an iterator method
    ````

* iterating over elements of an iterator

    ````python
    l = ["spam", "eggs"]
    for word in l:         # does literally iterate over elements in l
        print(word)
    for character in l[0]: # does iterate over elements in l[0]="spam"
        print(character)
    ````

<div class="exo">iterables</div>

---

### iterables, iterators, generators, &#8230;

* __iterable__: returns its members one after another `__iter__`

* __iterator__: datastream returning member after member `__next__`

* __generator__: function yielding a series of objects `yield`

---

![iterables, iterators, generators, &#8230;](../images/itergen.png)
