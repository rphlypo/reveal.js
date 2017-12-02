## Part VIII
### Good coding practice

```bash
mypackage/
    __init__.py
    subpackage1/
        __init__.py
        module1.py
        module2.py
    subpackage2/
        __init__.py
        module3.py
```

<div class="see-also">see also: [modules](https://docs.python.org/3/tutorial/modules.html)</div>

---

### PEP 8

* follow [PEP8](https://www.python.org/dev/peps/pep-0008/) whenever it makes sense

---

### unit testing

* write your test (objective) before your implementation

  * __what__ &rightarrow; __how__

* functionalities should be separated out

  * module = one objective

  * function = one behaviour

  * pure functions only

  <div class="see-also">[unittest](https://docs.python.org/3/library/unittest.html) and [nose](https://nose.readthedocs.io/en/latest/)</div>

---

### idioms and patterns

* many code chunks have been written by others, often more experienced than you

  * don't reinvent the wheel

<div class="see-also">[idioms](http://docs.python-guide.org/en/latest/writing/style/#idioms)</div>

---

### readable code

* use sensible variable names

  * ~~x, y, z~~
  * n_persons, xcoord, area, &#8230;

* cases

| object | case | example |
|:---|:---|:---|
| variable | lower case | `n_persons` |
| class | word upper case | `NewClass` |
| modules | lower case | `bigthing` |
| constants | UPPER_CASE | `UNIVERSAL_CONSTANT` |

---

### still having appetite?

<div class="see-also">see [best of the best practices guide for Python](https://gist.github.com/sloria/7001839)</div>
