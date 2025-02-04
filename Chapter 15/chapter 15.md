## Chapter 15 : Dates in the index

Sometimes the data is already as the index, here are some usefull operations you need to make in these cases 

### Find missing data

Withe the method any you can check is there are any missing values

```python
series.isna().any()
```

### Filling missing data

As we already saw we can fill the data using the method .fillna(), as you already know this is not the best solution, due to operation filling the indexes with a constant value, there are more efficient ways to do it.

With dates maybe they are consecutive and so I need to fill forward (or backwards) you can do so using this methods

```python
series.loc["the range":"the range"].ffill()
#or backwards
series.loc["the range":"the range"].bfill()
```

> ***Never use backwards when trying to do machine learning, don’t use future data to predict the past, this is called data leakage***
> 

you can also use interpolate() to fill missing values, but also in this case you are using future data to predict past data, which is a data leakage

### Dropping missing values

Sometimes you don’t want to fill data, but just dropping it, you can do so by using dropna()

```python
series.loc['':''].dropna()
```

> Be careful do it only when you are sure about it, because it will be hard to tell later if the data is missing
> 

### Shifting data

sometimes is very helpful to flip sequence data, you can do so by using

```python
series.shift(1)
# or backwards
series.shift(-1)
```