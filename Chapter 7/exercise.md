# Chapter 7: Series Deep Dive
## Notes 

The read_csv function can accept not only URLs but also Zip files, we can use this function because this ZIP files contains only a single file.

the pandas library provide a lot of methods for the data, and we can find it by running this code 

```python
dir(city_mpg)#with city_mpg being a series
```

There are categories:

- Dunder methods
- numeric operations
- aggregate methods (.mean,.max.sum etc)
- conversion methods (starts with .to_)
- string manipulation (begin with .str.)
- date manipulation (begin with .dt.)
- Transformation methods


## Exercises 
1. Explore the documentation for five attributes of a series from Jupyter

I found these 5:
1. cov -> Compute covariance with Series, excluding missing values.
2. mean -> Compute mean with Series, excluding missing values.
3. drop -> Remove elements of a Series based on specifying the index labels
4. dot -> Compute the dot product between the Series and the columns of other.
5. fillna -> Deprecated since version 2.1.0: Use ffill or bfill instead.





2. How many attributes are found on the .str attribute? Look at the documentation for three of them

I found these 3:
1. count -> Count occurrences of pattern in each string of the Series/Index
2. capitalize -> Convert strings in the Series/Index to be capitalized
3. strip -> Remove trailing characters




3. How many attributes are found on the .dt attribute? Look at the documentation for three of them

I found these 3:
1. date -> Returns numpy array of python datetime.date objects
2. time -> Returns numpy array of datetime.time objects
3. month -> The month as January=1, December=12. 