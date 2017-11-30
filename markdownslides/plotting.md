## Part IX
### Interactive plotting in Python

```python
from bokeh.plotting import figure, output_file, show

x, y = range(5), [1, 4, 2, 5, -1]
output_file("test.html")
p = figure(title="my first plot", x_axis_label="x", y_axis_label="y")
p.line(x, y, legend="data", line_width=2)
show(p)
```

---

### Plotting libraries

* [matplotlib](http://matplotlib.org): matlab-like, no "one and only one obvious way &#8230;"

* [seaborn](http://seaborn.pydata.org): matplotlib overlay, statistical data visualisation

* [mayavi](http://code.enthought.com/projects/mayavi/): 3D rendering by [Enthought](https://www.enthought.com)
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [bokeh](https://bokeh.pydata.org/en/latest/index.html): javascript = notebook + interaction, interfaces with `python`, `R`, `scala`, and `julia`

* [plot.ly](https://plot.ly/python/): online account, interaction
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

---

### bokeh

![bokeh](./images/bokeh_logo.png)

---

### bokeh

* bokeh: focus on your __data__

* easy to create standalone __webapp__ from your python code

  * (modern) web browser &leftrightarrow; web apps

  * multi-platform

  * power of CSS styling, javascript interaction, svg images, &#8230;

* [examples](https://bokeh.pydata.org/en/latest/docs/gallery.html#gallery)

<div class="exo">Bokeh intro</div>

---

### Your first Bokeh figure

* An empty plot, containing no glyphs, no data
  * in the jupyter notebook (needs `output_notebook()`)

    ```python
    from bokeh.plotting import figure
    from bokeh.io import show, output_notebook

    output_notebook()

    p = figure()
    show(p)
    ```

  * export to a stand-alone html document

    ```python
    from bokeh.plotting import figure
    from bokeh.io import show, output_file

    output_file("firstBokehPlot.html")

    p = figure()
    show(p)
    ```  

Note:
remark the `tools` on the right-hand side

---

### Your first Bokeh plot

* adding glyphs to a plot: lines, circles, &#8230;

```python
from bokeh.plotting import figure
from bokeh.io import show, output_notebook

output_notebook()

p = figure(title="My first Bokeh plot")
p.circle(range(5), range(5)[::-1], size=range(5, 30, 5), color='navy', alpha=0.3)
show(p)
```

<div class="exo">1<sup>st</sup> Bokeh plot</div>
<div class="see-also">[basic glyphs in Bokeh](https://bokeh.pydata.org/en/latest/docs/user_guide/plotting.html)</div>

---

### Bokeh apps

![Bokeh server model](./images/bokeh_serve.svg)

---

### matplotlib

![matplotlib](./images/matplotlib.svg)

---

### matplotlib

* plotting library inspired by Matlab&reg;

* plot &in; axes &in; figure

* publication&ndash;ready

* adding interactions in notebook &rightarrow; magic %matplotlib notebook

    ```python
    import matplotlib.pyplot as plt
    %matplotlib notebook
    ```

* mainly 2D plots (3D &agrave; la Matlab&reg;)
  * less so for pie charts, fancy figures, &#8230;

<div class="see-also">[matplotlib](http://matplotlib.org)</div>

---

### pyplot or OO

> While it is easy to quickly generate plots with the matplotlib.pyplot module, we recommend using the object-oriented approach for more control and customization of your plots.

<div class="see-also">[matplotlib OO](http://matplotlib.org/api/pyplot_summary.html#the-object-oriented-api)</div>

* A nice starting point: [the matplotlib API](http://matplotlib.org/api/index.html)

---

### Choosing your colormap

* categorical or nominal data &rightarrow; qualitative schemes

* periodically valued data &rightarrow; cyclic schemes

* unipolar (positive or negative only) &rightarrow; sequential schemes

* bipolar (amplitude and sign) &rightarrow; diverging schemes

![colormaps](./images/colormaps.png)

<div class="see-also">[colormaps](http://matplotlib.org/tutorials/colors/colormaps.html#sphx-glr-tutorials-colors-colormaps-py)</div>
