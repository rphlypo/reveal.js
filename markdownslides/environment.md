## Part II
### Setting up the environment

<!--
REPL
Anaconda, miniconda, environments (?)
IDLE, Spyder, IPython, Jupyter notebook
-->

---

### REPL

* read-eval-print loop

    * interpreted language

    * interactive shell (`>>>>`)

    * no compilation needed  

---

### IDLE

* integrated development and learning environment

    * good starting point for interactive programming with Python

    * itself entirely written in Python (`tkinter`)

    * debugger, color code, &#8230; (much like Matlab&reg;'s)

* scientific programming IDLE: __Spyder__ (even more Matlab&reg; like)

    * included in _Python(x,y)_

---

### Distributions

* CPython

* Anaconda, inc.

* Enthought's python
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [IPython](http://ipython.org) (enchanced interactive Python shell) &rightarrow; [Jupyter](http://jupyter.org)

* Embedded Python, Python for ARM
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [Jython](http://www.jython.org) Python for JAVA
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [PyPy.js](http://pypyjs.org) javascript implementation that is Python-compliant
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

---

### Anaconda

* for-profit &amp; community

    * free to use

    * paid service and rack space

* isolated environments (different python/package versions)

* package manager with dependency checks

    ```bash
    conda install <package>
    conda update <package>
    conda install -c conda-forge <package>
    conda create --name mynewenv python=3.6 scipy=1.0
    ```

* alternative: `pip`

---

### The Jupyter notebook

<div class="warning fragment fade-up" data-fragment-index="1">Once a variable is declared it can be used everywhere else!</div>

* extension of IPython

* cells can be executed in any order

* mixing code, figures, and text (annotations)

* declaration of variables in temporal order, not spatial order!

<div class="exo">NB Intro</div>
