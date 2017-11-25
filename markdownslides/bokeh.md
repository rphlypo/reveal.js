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
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [seaborn](http://seaborn.pydata.org): matplotlib overlay, statistical data visualisation
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [mayavi](http://code.enthought.com/projects/mayavi/): 3D rendering by [Enthought](https://www.enthought.com)
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

* [bokeh](https://bokeh.pydata.org/en/latest/index.html): javascript = notebook + interaction, interfaces with `python`, `R`, `scala`, and `julia`

* [plot.ly](https://plot.ly/python/): online account, interaction
<!-- .element: class="fragment fade-out" data-fragment-index="1" -->

---

### bokeh

* bokeh: focus on your __data__

* easy to create __webapp__ from your python code

  * (modern) web browser &leftrightarrow; web apps

  * multi-platform

  * power of CSS styling, javascript interaction, svg images, &#8230;

* [examples](https://bokeh.pydata.org/en/latest/docs/gallery.html#gallery)
