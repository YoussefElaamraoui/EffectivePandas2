## Chapter 12 : Indexing Operations

### Prepping data

If you want to change the index labels, then you can use the method rename, we can pass a dictionary to map the previous index label to the new label

```python
seris1 = series1.rename(index={0:'first')
```

***Common mistake :** using just a scalar (string) into rename changes the name of the series not the name of the label*

```python
series1.reaname('first') 
```

We can also reset the indexes if we want to, so we have all the indexes going from zero to the number of elements, but this will return not a series but a dataframe, which has the previous column(the previous column of labels and then a column before with just the values from 0 to number of elements)

```python
series1.reset_index() #returns a data frame

# to drop the current index and return just a seris with a column of 0 to elements
# be sure before doing it 
series1.reset_index(drop=True)

```

to sort the indexes then we can use the methods, .sort_values() or .sort_index() 

### Loc attribute

the loc attribute is used to deal with index labels, here are some of the most important actions we can perform:

*1 - Retrieve the element/s with the corresponding label:* 

```python
series.loc['first']
```

There is a catch, if there are two elements with the first label, perfect, because it will return a list with the elements, otherwise it will return just a scalar value, which is usually not ideal, to prevent this from happening we can do this instead

```python
series.loc[['first']]
```

2 *- Retrieve the element/s by slicing:*

We can also use the slicing way of retrieve data, however, also in this case there is a catch, in this case pandas follows the **closed interval** rules, it means that it will consider also the lower and upper bound, for instance

```python
serie1.loc['first':'last']
```

in python you would just take the first and the element before the last one, in pandas the values returned do take count of the first **and** last one (they are called **half-open interval rules** for python and **closed-intervals in pandas)**

***Common mistake:** the series has to be sorted  (if there are duplicates) otherwise it will return a KeyError*

One more trick you can use the .loc but just with strings that are not actual labels, this can be very beneficial sometimes

```python
series1.sort_index().loc["F":"J"]
```

Its also possible to pass in pandas in the loc

```python
series1.loc[pd.Index(["first"])
```

***common mistake:** if there were multiple elements duplicated in the passed index, meaning if i were to have → pd.Index([”first”,”first”]), the returned list will have a combinatoric explosion, meaning if there are just three values corresponding to that label i will found myself with 9 (m^n, in this case m=3, and n=2, because of the three values corresponding and the two duplicates first in the index)*

You can also use the boolean array to the loc, the boolean array was if you remember the array which is like this (true,false,true,false,false etc…), just an array with boolean valuse, try to thing what can happen in this case, yes its simple it just takes the true and ditches the false

```python
# mask will have true if the value is >20 in seris or false otherwise
mask = series1 > 20

#then I can use this mask 
series1.loc[mask]
```

### Iloc attribute

The iloc attribute is similar to the loc but has some differences, the main one is, loc works with labels while iloc works with attributes 

```python
series1.loc['first']

series1.iloc[0]
```

We can use the slice also with iloc but in this case the rule is not the closed interval rule, but the half-open interval rule common to the slicing

### Heads, tails & sampling

Two methods that are used to pull out values at the start or end of the series

```python
series1.head(10) #retrieve the first 10 elements
series1.tail(10) #retrieve the last 10 elements
```

Though easy to use, the sampling method is a better choice to inspect data

```python
series1.sample(10,random_state=42)
```

***Note: I did not mention the other methods (reindexing and filtering), maybe I will come back to this section in the future***