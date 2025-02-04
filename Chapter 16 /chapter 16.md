## Chapter 16 : Plotting with a Series

Statistical summaries and tables can reveal much about your data, a technique to understand the data at a more intuitive level is to plot it.

Jupyter has a native integration with Matplotlib, but in older versions you needed to specify the cell magic

```python
%matplotlib inline
```

the series object has a .plot attribute from there you can plot all the data, some plotting styles are 

### Histograms

```python
series.plot.hist()
```

### BoxPlot

```python
series.plot.box()
```

### Kernel Density Estimation plot

is a smoothed histogram essentially

```python
series.plot.kde()
```

### Line Plots

Plots the values in the seires on the y-axis and the index on the x-axis, perfect for dates.

```python
series.plot.line()

#you can also do it just for the last n values 
series.tail(n).plot.line()
```

### Bar Plots

its perfect to compare values, this plot is different from the histogram.
Both visualizations help you understand the data, but box plots are better for summarizing and comparing distributions, while histograms are more effective for analyzing the overall shape and spread of data in more detail.

```python

series.plot.bar()

#you can also create a horizontal version
series.plot.barh()
```

> **Bar plots are really good with categorical data.**
As a rough rule the author suggest to create bar plot with less than 30 bars
>