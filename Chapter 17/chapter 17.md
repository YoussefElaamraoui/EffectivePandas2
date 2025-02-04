## Chapter 17: Categorical Manipulation

We have two types of categorical data, ***ordinal values*** (for instance shoes sizes, or t-shirt sizes: small,medium,large ) or ***nominal values*** (are categories with values such as colors) 

### Benefits of categorical data

Categorical computation is fast for many operations, and we still have also the str attribute (used for strings) so all the methods can be used also in this case. Another benefit, they use less memory, because every category is saved just one time.

### Conversion to Ordinal Categories

You can make ordinal categorical categories as ordinal, you can do so by doing the following:

```python
make_type = pd.CategoricalDType(categories=sorted(make.unique()),order=True)
ordered_make=make.astype(make_type)
```

if you want to preserve the order you just have to do:

```python
make.astype('category').cat.as_ordered()
```

as you can see there it is also a cat attribute

### Generalization

Sometimes you will need to limit the number of categorical values, one way of doing so its by using where method:

```python
# I write the snippet provided in the book
def generalize_topn(ser,n=5,Other='other'):
	topn= ser.value_count().index[:n]
	if isinstance(ser.dtype,pd.CategoricalDtype):
		ser = ser.cat.set_categories(
					topn.set_categories(list(topn)+[other]))
	return ser.where(ser.isin(topn),other)
	
	
cat_make.pipe(generalize_topn,n=20,other='NA')
	
```

Because often you will do something like this its useful to create the function