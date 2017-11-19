## Part VI
### handling input/output

```python
with open('test.html', 'r') as f:
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

### handling files (1/)

* files should be opened, processed, and closed

* `open(<filename>, <mode>)` with modes

    * `r` read only

    * `w` rewrite = erase file and write

    * `a` append

    * `b` (modifier `rb`, `wb`, `ab`) binary mode

    * `+` (modifier `r+`, `w+`, `a+`)

```python
fid = open('file.txt', 'r')
# do operations on file.txt through fid
close(fid)
```

---

### handling files (2/)

* one should not forget to `close`

* better: context &rightarrow; _file identifier_ only defined within context `with`

    ```python
    with open('file.txt', 'r') as fid:
        #do operations on file.txt through fid
    close(fid) # will return error, since fid not defined outside context
    ```
