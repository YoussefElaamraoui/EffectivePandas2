# Chapter 8 : Dunder Methods & Operators

Quando si fanno delle operazioni normali in python ad esempio 

```python
2 + 4 #The code does this 
(2).__add__(4)#under the hoood 
```

## BroadCasting

We can do the broadcasting 

```python
s2+5
```

## Iteration

When using series it’s better to avoid using the for and instead use the iter method provided, if you use the for its a code smells which means you are probably doing things incorrectly.

When you use the dundder methods usually they fill in NaN (or <NA>for int64)when of the operands is missing following index allignment

## Chaining

Another stylistic reason to prefer the methods to operations is to for stylistic reasons for manipulations chaining, this because most of the pandas methods do not change the data but create a new object with the data changed. Moreover, its really usefull to build clear and efficient code.

## Notes


## Exercises 

1. Add a numeric seris to itself
2. Add 10 to a numericc series
3. Use the .add method to add a numeric series
4. Read the documentation for the .add method
