## Chapter 22 : columns types, .assign, and memory usage

There are various methods and functions for changing the types of a series in pandas, for instance .astype to update column types. 
Or you can even use .assign method that return a new dataframe with the updated type.

*You should master .assign*

Some peculiarities, if the argument name is an existring column it will change the column values if the argument name is a new column it creates a new column.(But rememeber its a new dataframe it does not mutate the existing one)

> Why changing the data type? simply because the memory usage its more efficient
> 

**Astype**

```python
import pandas as pd

df = pd.DataFrame({'A': ['1', '2', '3'], 'B': [4.5, 5.1, 6.3]})
df['A'] = df['A'].astype(int)  # Converts column 'A' to integer
print(df.dtypes)
```

**Assing**

```python
df = pd.DataFrame({'A': ['1', '2', '3'], 'B': [4.5, 5.1, 6.3]})

# Changing type using .assign() (returns a new DataFrame)
df_new = df.assign(A=df['A'].astype(int))

print(df_new.dtypes)  # 'A' is now an integer
print(df.dtypes)      # Original dataframe remains unchanged
```

**Use .astype()** when you just need to change a column’s type.

**Use .assign()** when you want to apply functions, transformations, or create new columns in a **chained and clean** way.