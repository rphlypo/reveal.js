## Part X
### Data in python

```python
import numpy as np
from scipy.stats import gaussian_kde

X = np.random.uniform(size=(100, 100))
s = X.sum(axis=0)
gaussian_kde(s)
```

---

### `numpy` package

* part of the Python scientific stack

* purpose: numerical computing

* central object: `ndarray`

```python
import numpy as np
x = np.identity(10)             # The identity matrix in IF^{10x10} (IF = IR ou IC)
y = np.ones(shape=(10, 10)) * 1
z = y - x
z = np.diag(z.sum(axis=1)) - z  # Laplacian of the fully connected symmetric graph
```

<div class="see-also">[numpy quickstart](https://docs.scipy.org/doc/numpy-dev/user/quickstart.html)</div>

---

### arrays

* `ndarray` main attributes

| attribute | description |
|:---:|:---|
| `ndim`  | matrix &mapsto; 2, vector &mapsto; 1 |
| `shape` | number of elements in each of the dimensions, as a tuple |
| `size` | total number of elements = `np.prod(ndarray.shape)` |
| `dtype` | data type of the elements |
| `itemsize` | size in bytes of each element (related to `dtype`) |
| `data` | buffer containing the elements, __do not use directly__ |

<div class="see-also">[numpy data types](https://docs.scipy.org/doc/numpy/user/basics.types.html)</div>
<div class="exo">numpy</div>

---

### `ndarray` vs. `matrix`

<div class="warning fragment fade-up" data-fragment-index="1">Always prefer `ndarray` over `matrix`</div>

* `matrix` is Matlab&reg;&ndash;like
  * incoherence: `/` is element-wise, `*` is matrix product
  * **only** 2-dim arrays &Rightarrow; vector shape `(n, 1)`

* `ndarray`
  * all operators act element-wise, matrix product = `numpy.dot`
  * unified interface for n-dim arrays &Rightarrow; vector shape `(n, )`

* `numpy` functions : type preservation
  * `matrix` &mapsto; `matrix`
  * `ndarray` &mapsto; `ndarray`

---

### `ndarray` operations

* `ufunc` (universal functions)
  * element-wise

* unary functions (mostly `ndarray` methods)
  * `ndarray`-wise
  * __axis__ keyword &rightarrow; specific dimension

* binary functions (`ndarray` methods and functions)
  * interaction between `ndarray`s

<div class="warning fragment fade-up" data-fragment-index="1">upcasting: result is most precise (general) numeric class</div>
<div class="see-also">[numpy routines](https://docs.scipy.org/doc/numpy-dev/reference/routines.html#routines)</div>

---

### `ndarray` operations: examples

* non-exhaustive list !

| ufunc | unary | binary |
|:---:|:---:|:---:|
| +&nbsp; *&nbsp; /&nbsp; ** | sum, prod, cumsum | dot, inner, outer |
| >&nbsp; <&nbsp; >=&nbsp; <= | min, max | minimum, maximum |
| sin, cos, exp | ravel |  |

<div class="exo">operations</div>

---

### indexing

* 1-dim `ndarray`s: much like `list`s<br />
  &rightarrow; `start:stop:step`

* `ndarray` (dim > 1)<br />
  &rightarrow; `:` selects all elements in this dimension<br />
  &rightarrow; `...` selects all elements in remaining dimensions
  &rightarrow; omitted indices equivalent to `...`

    ```python
    x = np.empty(shape=(3, 4, 5, 6))
    x[0, 1, 2, 3]     # 0-dim result selects single element
    x[0, 1, 2, :]     # 1-dim result of shape (6, )
                      # equivalent to x[0, 1, 2] and x[0, 1, 2, ...]
    x[0, 1, ...]      # 2-dim result of shape (5, 6)
                      # equivalent to  x[0, 1] and x[0, 1, :, :]
    x[0, ..., 3]      # 2-dim result of shape (4, 5)
    ```

---

### `ndarray` as an iterable

<div class="warning fragment fade-up" data-fragment-index="1">`flat` attribute returns an element-wise __iterator__ for `ndarray`</div>

* since `x[0] = x[0, ...]` we have

    ```python
    x = np.empty(shape=(3, 4, 5, 6))
    for r in x:
        print(r.shape)   # shape (4, 5, 6)
    ```

* iterating is __always__ over 1st non-empty axis

* element-wise iteration

    ```python
    for el in x.flat:
        print el        # single entries
    ```

<div class="exo">indexing</div>

---

### reshaping

* reshape/resize
    * `reshape` &rightarrow; __return__ reshaped
    * `resize` &rightarrow; __in-place__ reshape

* ravel/flatten/flat
    * `ravel` &rightarrow; __return__ unfolded
    * `flatten` &rightarrow; __in-place__ unfolding
    * `flat` &rightarrow; __return__ iterator

* transpose
    * `T` &rightarrow; __return__ transposed

Note:
most use C-order, force F-order if needed
joker dimension -1

---

### copy and view (1/2)

* ... or _data_ and _reference_

* `ndarray` = `list` + extra attributes &Rightarrow; mutable

* memory organisation &equiv; list + __view__

  * shape &in; __view__ (2, 3)
    * C-order _row first_ &mapsto; [[0, 1, 2], [3, 4, 5]]
    * Fortran-order _column first_ &mapsto; [[0, 2, 4], [1, 3, 5]]


| method | description |
|:---|:---|
| `view()` | look at data &equiv; referencing |
| `copy()` | copy data, new instance |

---

### copy and view (2/2)

* assignment &mapsto; view

  ```python
  x = np.arange(12).reshape(3, 4, order='C')  # default 'C'
  y = x
  print(y is x)  # prints True!
  y.resize()
  ```

* indexing &mapsto; (partial) view

  ```python
  x = np.arange(12).reshape(3, 4, order='F')
  x[1, 2]     # single element
  x[:, 2]     # single column
  x[[1, 2], [0, 3]] # two elements
  x[0][1]     #
  ```

<div class="exo">copy and view</div>

---

### indexing revisited

* repeated indices &rightarrow; using `ndarray`s as indices

* boolean indices &rightarrow; allow filtering
  &rightarrow; useful in re-assignment

* `np.ix_` to get minors

* __broadcasting__
  * autocomplete arrays for dimension compatibility
  * operations without needless copying

<div class="exo">broadcasting</div>
<div class="see-also">[broadcasting](https://docs.scipy.org/doc/numpy-dev/user/basics.broadcasting.html)</div>

---

### to go further

| package | description |
|:---|:---|
| `pandas` | &rightarrow; data exploration, requests, manipulation, plotting, &#8230;<br />&rightarrow; special functions for timeseries |
| `scipy` | &rightarrow; special functions<br />&rightarrow; signal processing<br />&rightarrow; numerical integration/differentiation |
| `sympy` | &rightarrow; formal computation, symbolic computing |
| `scikit-learn` | &rightarrow; machine learning |
| `skimage` | &rightarrow; image processing |

---

## Many, many thanks to you all!
