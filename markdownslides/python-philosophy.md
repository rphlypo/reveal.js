## Part I
### Python : a philosophy

```python
print("Hello world!")
```

---

### The Origins (1/2)
* **what?** ABC general purpose programming language and programming environment

* **where?** CWI : Centrum voor Wiskunde en Informatika &mdash; Amsterdam, the Netherlands

* **who?** Guido Van Rossum

* **when?** 1991

* **how?** Monty Python's flying circus

---

<center>
<iframe width="854" height="480" src="https://www.youtube.com/embed/Q1sXeUHBHgk" align="top" frameborder="0" gesture="media" allowfullscreen></iframe>
</center>
<!--_-->

---

### The Origins (2/2)

* **Feb'91:** version 0.9 of source code published on _alt.sources_

 _Exception handling, objects, functions, modules, &#8230;_

* **Jan'94:** Python 1.0

  _functional programming : lambda, filter, map, reduce_

* **Oct'00:** Python 2.0

  _list comprehension, garbage collector, unicode support_

* **Dec'08:** Python 3.0

  _print() ~~print~~, integer division &mapsto; float, &#8230;_

---

### [PEP 20](https://www.python.org/dev/peps/pep-0020/) : The zen of Python (1/4)

* Beautiful is better than ugly.

* Explicit is better than implicit.

* Simple is better than complex.

* Complex is better than complicated.

* Flat is better than nested.

---

### [PEP 20](https://www.python.org/dev/peps/pep-0020/) : The zen of Python (2/4)

* Sparse is better than dense.

* Readability counts.

* Special cases aren't special enough to break the rules.

* Although practicality beats purity.

---

### [PEP 20](https://www.python.org/dev/peps/pep-0020/) : The zen of Python (3/4)

* Errors should never pass silently.

* Unless explicitly silenced.

* In the face of ambiguity, refuse the temptation to guess.

* There should be one &mdash; and preferably only one &mdash; obvious way to do it.

* Although that way may not be obvious at first unless you're Dutch.

---

### [PEP 20](https://www.python.org/dev/peps/pep-0020/) : The zen of Python (4/4)

* Now is better than never.

* Although never is often better than *right* now.

* If the implementation is hard to explain, it's a bad idea.

* If the implementation is easy to explain, it may be a good idea.

*	Namespaces are one honking great idea &mdash; let's do more of those!

---

### Why Python ?

[PSF Python brochure Vol.1](http://brochure.getpython.info/media/releases/psf-python-brochure-vol.-i-final-download.pdf/at_download/file): a list of applications that should convince _anyone_ of the widespread use of Python

* web applications

* data science / machine learning

* graphical user interfaces

* (bash-like) automation processes

* IoT

---

### Some Useful Python Acronyms

* __OO:__ object oriented, objects are 1<sup>st</sup> class citizens in Python

* __PEP:__ [Python enhancement proposals](https://www.python.org/dev/peps/) maintains coherence throughout

* __PSF:__ [Python software foundation](https://www.python.org/psf/) non-profit organsation
  > <small>The mission of the Python Software Foundation is to promote, protect, and advance the Python programming language, and to support and facilitate the growth of a diverse and international community of Python programmers.</small>
  > &mdash; extract of PSF mission statement

---

### OO language

* object = 1<sup>st</sup> class citizen

    * functions, strings, integers, &#8230; are all objects

* object = description + actions

    * description: characteristics or _attributes_

    * action: _methods_ to change attributes or functionality

---

### OO language : examples

* geometry : point in 3D space

  &rightarrow; attributes = coordinates x, y, z (wrt a basis)

  &rightarrow; actions = reflecting, translating, rotating, homotopy, &#8230;

* daily objects : car

  &rightarrow; attributes = make, model, cylinders, color, gpm, &#8230;

  &rightarrow; actions = fill fuel, drive to, tire wear, &#8230;

---

### sampling PEPs

* [__PEP 1__](https://www.python.org/dev/peps/pep-0001/) :Purpose and Guidelines

* [__PEP 5__](https://www.python.org/dev/peps/pep-0005/): Guidelines of language evolution (community driven)

* [__PEP 8__](https://www.python.org/dev/peps/pep-0008/): Style Guide for Python Code

* [__PEP 20__](https://www.python.org/dev/peps/pep-0020/): The Zen of Python

* [__PEP 285__](https://www.python.org/dev/peps/pep-0285/): Adding a bool type

* [__PEP 450__](https://www.python.org/dev/peps/pep-0450/): Adding A Statistics Module To The Standard Library

---

### PSF's sponsors

<center>
![Sponsor logos](./images/logos.png "PSF Sponsors")
</center>

---

### Python = community effort

<center>You will progressively become __pythonistas__ !</center>

---

### Before going further &#8230;

In what follows we'll use

* quick testing: IPython console (search the _Holy Grail_)

* exercises: Jupyter Notebooks
