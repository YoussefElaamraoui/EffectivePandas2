# Chapter 14 : Date and Time manipulation

Coordinated Universal Time or Universal Temps Coordonné (UTC) is the time standard at 0 degrees longitude


> To search for the data online, just search IANA and then the city
> 

When working with date data, you want this :

- Time
- Time zone
- Offset

generally you should store data as UTC and then convert it in local times as needed, so store one of these two options:

- UTC date and time zone
- Local date, offset and time zone

If you the time and then the offset, one way to perform the transformation is to use this process, first of all use the method, .groupby(”list of offset”) then use the transform method, here an example:

```python
time = pd.Series(["your values of time"])
offset = pd.Series([-7,-7,-6,-7 etc])

pd.to_datetime(time).groupby(offset).transform("what you want to do")
```

When using data that comes from CSV remember that data needs to be converted to dates, because by default comes as a column

```python
# in this ase if you want date time 
dates = pd.to_datetime(.....).astype('timestamp[ns][pyarrow])
```

To perform date operations use the .dt, in this case these are not methods but rather properties.

> **Properties vs Methods**:  **Methods** are functions that take parameters and perform operations, modifying or interacting with data. This differs from **properties**, which operate on existing attributes within the object without requiring parameters. 
To quickly distinguish between the two, check if there’s a () after calling it—if there is, it’s a **method**; if not, it’s a **property**.
> 

There are different dt proprieties you can choose from, I won’t state them all