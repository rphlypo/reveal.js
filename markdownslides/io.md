## Part V
### handling input/output

```python
with open('test.txt', 'w+') as f:
    line = True
    linecount = 0
    while line:
        line = f.readline()
        linecount += 1
        if "<script>" in line:
            print("there's a script starting at line {}".format(linecount))
```

Note:
with open("reveal.js/index.html") as f:
     line = True
     linecount = 0
     script = False
     while line:
         line = f.readline()
         linecount += 1
         if "<script" in line:
             print("script starting at line {}".format(linecount))
             if "<script>" in line:
                 line = line.split("<script>")[1]
                 print("\t" + line.strip())
                 script = True
         if "</script>" in line:
             line = line.split("</script>")[0]
             print("\t" + line.strip())
             print("script ending at line {}".format(linecount))
             script = False
         if script:
             print("\t" + line.strip())

---

### handling files

* a file must be opened, manipulated, then closed

    ```python
    fid = open("file.ext", "mode")
    # manipulate file
    fid.closed # returns False
    fid.close()
    fid.closed # returns True
    ```

* easier &rightarrow; context manager

    ```python
    with open("file.ext", "mode") as fid:
        # manipulate file
        fid.closed # returns False
    fid.closed # returns True
    ```

<div class="exo">file handling  </div>

---

### scripts

* save all your statements in a `.py`, e.g., `test.py`

* you can execute all statements by running `python test.py`

---

### modules &amp; packages

* a collection of variables, functions, statements, &#8230;

* modules __extend__ python's standard functions (quite limited)

* __packages/libraries__ contain multiple modules

    ```shell
    #!/usr/bin/python
    ```

    ```python
    if __name__ == "__main__":
        # some executable code if called
    ```
---

### Using modules

* `import module`

    * functions must be called as `module.function`

* `from module import function1, function2`

    * only specific functions

    * functions can be called as `function1`

* `from module import *`

    * __avoid__ whenever possible!

---

### Python's standard library

* a collection of modules available in the Python distribution

    * e.g., `math`, `sys`, `random`, `datetime`, `email`, &#8230;

* adds functionality

* other packages/modules

    * `Pypi` (Python package index)

    * `conda` (Anaconda inc.)

    * &#8230;
