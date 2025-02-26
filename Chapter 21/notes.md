## Chapter 21: Looping and aggregation

It’s possibile to use for loops with dataframes, however its something you should not be doing because its a slow operation, you should always be taking advantage of vectorization. Its possible to use loops for labeling plots

The methods are .items and .itertuples

```python
.items -> method that returns
a tuple with the column name and the column

.itertuples -> method that 
gives you a row represented as a named tuple
```

Aggregations, available for series, are also available with dataframes but with dataframes you can aggregate across both dimensions.

You can also use dictionaries in aggregation

```python
dataframe.agg({'Luck':['count','size'],
'Overall':['count','max']})

```

> count is the count of the non-missing rows
> 

Dataframes also have the .apply method, like in the series its better not to use the apply method , moreover in this case we have two-dimensional structure this means that it will be more difficult for you to make good code, but also  readability

When using apply you should try to improve the code, because as you now .apply does not use vectorization this means that you will have a slow code, because apply is done to every single element of the column. 
To solve there are different approaches 

- Cython translates Python-like code into C, which is then compiled into a shared library (.so file) for faster execution.
- Numba, a JIT(just in time compiler) for python that translates a python function in a machine code at runtime.