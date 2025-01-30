# Chapter 13 : String Manipulation

if you stored string in a series the underlying type of the series was an object before pandas 2.0, right now if you have a series with numbers and strings the type is also an object.

Pandas 2.0 with the integration of PyArrow introduced the new pd.ArroDtype(pa.string()) it’s explicit and it supports also missing values that are not NaN, the PyArrow version uses less memory and its supports a lot of methods, however, it lacks support for the older methods.

If you have low cardinality string columns using categorical type is the most efficient way, because the operations are done only on the individual categories and not on each value.

### Str Accessor

The object pd.ArrowDType(pa.string()) and the category types have the .str accessor to the methods, so you can do the manipulation of the strings.

like:

```python
column_string.str.lower()
```

usefull methods are:

- Extract: which extracts all the elements in the series that do correspond, to limit the extraction so it does not return data frames use the keyword *expand=False

name.str.extract(’(you can write also regular expression in here)’,expand=False)*
- Splitting: to slipt is really usefull and important to do, here however is more usefull to use the expand = True, meaning sometimes it can happen to retrieve a series of lists, so its better to use a dataframe in that case

As we also did before a good way to optimize the good is to use vectorization with Numpy, but there are also other usefull ways to optimize our code

### Cython & Numba

cython is a superset of Python that converts the code in C and then compiles to machine code , to enable and use it in jupyter you have to install it and the run the following code

```python
%load_ext Cython
#Then in another line of code, a line before the code we want to run
%%Cython
.
.
.
.
.
```

another good library is Numba, uses JIT(Just in Time) compilation to do  the same thing of Cython, but in this case we are converting it in fast machine code. 
This provides significant code optimization, can be as fast as Cython and works best with numerical computation.

### Replacing text

To replace text we will have to use str.replace, if we want to replace single characters, but if you want to complete replacement for many values you should use .replace.

to specificy complete replacements you can use either a dictionary inside the replace method like this:

 

```python
column.replace({'Audi':'åudi','Alfa Romeo':'ålfa romeo'})
```

 or you can specify that you want to use regex (regular expressions)

```python
column.replace('A','å',regex=True)
```