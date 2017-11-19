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
<!-- .element: class="fragment grow" -->

* Anaconda, inc.
<!-- .element: class="fragment grow" -->

* Enthought's python

* [IPython](http://ipython.org) (enchanced interactive Python shell) &rightarrow; [Jupyter](http://jupyter.org)
<!-- .element: class="fragment grow" -->

* Embedded Python, Python for ARM

* [Jython](http://www.jython.org) Python for JAVA

* [PyPy.js](http://pypyjs.org) javascript implementation that is Python-compliant

---

### Anaconda

* for-profit and community contributions

* free for all, paid customer service and rack space

* isolated environments (different python/package versions)

* package manager with dependency checks

* alternative: `pip`

    ```bash
    conda install <package>
    conda update <package>
    conda install -c conda-forge <package>
    conda create --name mynewenv python=3.6 scipy=1.0
    ```

---

### python modules

1. use your favorite text editor (or an IDLE)

1. create python code and save as `.py`

1. from command line or from other file
     * command line: `python mymod.py` to execute
     * from file: `import mymod` &rightarrow;

* _HINT_: use `if __name__="main":` to make a file
    * callable from command
    * and ready for import

* _HINT_: shebang `#!/usr/bin/pyton` on first line
