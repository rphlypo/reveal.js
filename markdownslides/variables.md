## Part III
### Variables and variable manipulation in python

<pre><code data-trim data-noescape class="python">
a = int()             # initialisation (no mere declaration!)
b = "Hello world!"    # No declaration, only initialisation
b = 3                 # Type change without any problem
b == 3.0              # dynamic variables ! b is casted to float before comparison
</code></pre>

---

### data types in Python

* different types = different functionalities

  * scalars: `bool`, `int`, `float`, `complex`

  * strings: `string`

  * sequences: `list`, `tuples`

  * collections: `list`, `dictionary`, `set`

* data type inspection &rightarrow; `type( )`

<div class="exo ">data types</div>

---

### indexing in Python (1/3)

Example

```python
x = [1, 2, 3, 4, 5, 6]
```

* python: `0`-based indexing

    ```python
    x[0] = 1
    ```

* tail-based indexing: negative numbers

    ```
    x[-1] = 6
    ```

<div class="exo">indexing</div>

---

### indexing in Python (2/3)

<div class="warning fragment fade-up" data-fragment-index="1">the `stop` index is not included!</div>

* the slicer `:` (lists, tuples, strings)

  * `start:stop`
  * `:stop`
  * `start:`
  * `start:stop:step`
  * `start::step`
  * `:stop:step`
  * `::step`

---

### indexing in Python (3/3)

```python
s = "Hello world!"
s[4:7]
s[:5]  # Hello
s[6:]  # world!
s[:-1] # Hello world
s[3:-2:2] # l ol
s[::-1] # !dlrow olleH
```

---

### basic operators in Python (1/5)

* assignment: `=`

* mathematical operators: `+`, `-`, `*`, `/`, `//`, `%`, `**`

* string / list of string operators: `+`, `join`, `split`, ...

* list operators: `+`, `append`, `extend`, `pop`, `insert`, `index`, ...

* mixed operators: `*`

    ```python
    a = "Hello "
    b = "world! "
    (a+b) * 3     # mixed operator combining string & int
    ```

---

### basic operators in Python (2/5)

* comparison operators `<`, `>`, `<=`, `>=`, `==`, `!=`

* inline operators `+=`, `-=`, `*=`, `/=`, `%=`, `//=`

* membership operator `in`

* logical operators `&`, `|`, `^`, `~` (bitwise), `and`, `or`, `^` (xor), `and`, `not`

* identity operator `is`

* bitwise shifts `<<`, `>>`

---

### basic operators in Python (3/5)

(mathematical) operators are evaluated as

1. parentheses first

1. order of precedence

  2. `**`
  2. `*`, `/`, `//`, `%`
  2. `+`, `-`

1. from left to right

---

| Operator | Description |
|:---------|:------------|
| **       | exponentation |
| ~ + -    | complement, __unary__ plus and minus |
| * / % // | multiply, divide, modulo and floor division |
| + -      | addition and subtraction |
| >> <<    | right and left bitwise shift |
| &        | bitwise __and__ |
| ^ &vert; | bitwise exclusive and regular __or__ |
| <= < > >= | comparison operators |
| <> == != | equality operators |
| = %= /= //= -= += *= **= | inline assignment operators |
| is, is not | __identity__ operators |
| in, not in | membership operators |
|not, or, and | logical operators |

---

### basic operators in Python (5/5)

Exercise: what are the truth values (`True` or `False`) ?

```python
5 == 5
5 == 5.0
5 is 5
5 is 5.0
"Python" in "Monty Python"
"Python" == "python"
1 in [1, 2, 3]
1 not in [1, 2, 3]
1 in [[1, 2], 3]
1 in {1, 2, 3}
(4 < 5) ^ (6 > -1)
x >> k == x // 2 ** k
```

<div class="exo">operators</div>

---

### strings and docstrings (1/2)

* strings are encapsulated by '&emsp;' or "&emsp;" ('''&emsp;''' or """&emsp;""" for multiline)

* docstrings start with `#` or are encapsulated by """&emsp;""" (multiline)

    ```{python}
    s1 = "Hello world!"     # basic string of which I'm the docstring
    s2 = "Spam and Eggs"    """ I'm a multiline
                            docstring, documenting
                            myself
                            """
    s3 = """ This is
    a multiline
    string
    """                     # docstring of multiline string
    ```

---

### strings and docstrings (2/2)

* string formatting: `<string>.format(<value>)`

    * `{}` &rightarrow; in order of presentation

    * `{<key>}` &rightarrow; key&mdash;value pairs

    * `{<key> : <formatter>}` &rightarrow; formatting is chosen

```python
"I am a {}".format("string")
"x equals {}, y equals {}".format(3, 5)                # order of appearance
"x = {x}, y = {y}, x = {x} again".format(x = 3, y = 7) # key-value pairs
"x equals {:.5g}".format(1/3)
"x equals {x:.5g}, y equals {y:.5f}".format(x = 10/3, y = 10/7)
```

<div class="exo">strings</div>

---

### number representation (1/5)

computers = manipulation of __bits__

* integers &#10004;

* &Rightarrow; rational numbers &#10004;

  * irrational numbers ? transcendent numbers ?

  * RSA &rightarrow; factorisation in primes = difficult

    &Rightarrow; fraction approximation of real numbers = difficult

  * easier : denominator = $2^k, k\in\mathbb Z$


---

### number representation (2/5)

* decimal number system

  * $x=(-1)^s\sum_{k=-\infty}^{+\infty}a_k\ 10^k\qquad$    for    $\qquad a_k\in [0,\,9]\cap \mathbb{Z}$

  * s is the sign $\in\{0,\,1\}$

* binary number system

  * $x=(-1)^s\sum_{k=-\infty}^{+\infty}b_k\ 2^k\qquad$    for    $\qquad s, b_k\in \{0,\,1\}$

  * signed/unsigned, little/big endian, base-2 binary representation
  * stored in memory by byte : 1 Byte = 2 hex = 8 bit $\in \lbrace 0,\,1,\,\ldots,\,9,\,A,\,B,\,C,\,D,\,E,\,F \rbrace^2$, e.g., AF

Note:
big/little endian : most/least significant byte in lowest memory

---

### number representation (3/5)

* Example 1: decimal 23

  $\begin{align}23 &= 2\times 10^1 + 3\times 10^0\newline &=  1\times 2^4 + 0 \times 2^3 + 1\times 2^2 + 1\times 2^1 + 1\times 2^0=\_b 10111\newline &= \_B 17\end{align}$

* Example 2 : decimal 1025

    ```python
    x = 23
    x.to_bytes(1, 'big')
    y = 1025
    y.to_bytes(2, 'big')     # big endian
    y.to_bytes(2, 'little')  # little endian
    ```

---

### number presentation (4/5)

* representing __any__ number

  * `float`: __IEEE 754-2008__

  * s = _sign_, c = _significand_, q = _exponent_, b = _base_ (_radix_)

    $x = -1^s\times c\times b^q = (-1)^s\times c \times b^q$

  * representation for `qNaN`n `sNaN`, `-Inf`, `+Inf` (overflow)

Note:
quiet NaN and signalling NaN

* Any number is __represented__ (approximated through a finite, truncated representation)

  * e.g., 1/10 : easy in decimal (fractional) representation, difficult in binary representation

---

### number representation (5/5)

```python
x = 1/10
print(x)
x.as_integer_ratio()
print("x = {:.6g}".format(x))  # 6 significative digits / format(x, '.6g')
format(x, '.24g') # 24 significative digits
y = 3 * 10 - 1
print(y)
format(y, '.24g') # 24 significative digits
y.as_integer_ratio()
```

<div class="exo">representation</div>

---

### declaration, initialisation, and allocation (1/3)

<div class="warning fragment fade-up" data-fragment-index="1">only initialisation in Python</div>

* __declaration__ = type &amp; name ; pointer to memory address

* __allocation__ = allocate specific value to memory block

* __initialisation__ = declaration + allocation

---

### declaration, initialisation, and allocation (2/3)


```C
int a; // declaration : 'a' points to (random) 'int'-sized memory
a = 3; // allocation : x0000 0000 0000 0011 into memory
string b = "Hello world!"; // initialisation = declaration + allocation
```

```python
a = int() # initialisation : a --> memory containing '0'
a = 3     # same memory now contains '3'
b = "Hello world!" # b --> another memory block
```

---

### declaration, initialisation, and allocation (3/3)

* data type &rightarrow; __constructor__

    * `x = set([1, 2, 3])` equivalent to `x = {1, 2, 3}`
    * `x = list([1, 2, 3])` equivalent to `x = [1, 2, 3]`
    * `x = int(5.0)` equivalent to `x = 5`

* also allows to __cast__ variables (_convert_ data type)

    ```python
    x = "5.1"
    print("x is of type {}".format(type(x)))
    y = int(x)
    print("y is of type {}".format(type(y)))
    z = tuple(y)
    print("z is of type {}".format(type(z)))
    ```

<div class="exo">casting</div>

---

### More on containers: mutable or immutable (1/4)

* Strings are not lists

    * strings can be indexed as lists &#8230;

    * &#8230; but no reassignment

      ```python
      s = "spam eggs"
      s[4] = " and "
      TypeError
      ```

---

### More on lists, sets, dictionaries, and tuples (2/4)

sets and dictionaries are __unordered__

```python
p = {1, 2, 3, 4}
p[0]
d = {"a": 1, "b": 2, "c": 3}
d[0]
```

---

### More on lists, sets, dictionaries, and tuples (3/4)

* `list`, `dict`, and `set` &rightarrow; __mutable__

    * object is passed by __reference__

    * _contents_ are changed __without__ changing its reference

* `int`, `float`, `str`, `frozenset`, `tuple` &rightarrow; __immutable__

    * changing contents &Rightarrow; new reference / object

<div class="exo">containers</div>

---

### More on lists, sets, dictionaries, and tuples (4/4)

* `tuple`, `int`, `float`, `string`, `frozenset`, &#8230; &rightarrow; immutable

* __hashable__ object (unique `id`) &rightarrow; index

   ```python
   x = (1, 2, 3)      # immutable & hashable
   s = "Hello world!" # immutable & hashable
   d = {x: 0, s: 1}   
   print(d[(1, 2, 3)])
   ```

<div class="exo">matrix</div>
