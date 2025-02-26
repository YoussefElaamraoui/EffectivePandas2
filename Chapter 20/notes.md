# Chapter 20: Math Methods in DataFrames

As well as in series object also in dataframes you can perform math operations

You can perform, Normalization or Standardization

- Normalization: scaling the data in each column to values between 0 and 1
*Xnorm = (X-Xmin)/(Xmax-Xmin)*
- Standardization: scaling the data in each column to have  mean is 0 and the standard deviation is 1
Xstandard=(X-u)/(deviazione standard)

You can perform math methods like add, or use operator like + - / and *, dunder methods are also available.

Usually you won’t make operations on dataframes but its still usefull to do it. Remember also that scikit-learn has already some built in methods that can help you do most of the operations.

For example you can perform principal component analysis (PCA), this is a technique to reduce the dimensionalty of the data.

> *A column with no **variance** has no information, you could remove that column and not lose any information from the data. Indeed in financen they use variance as a proxy to see if a stock is high risky or not, while in quality control  variance is used to measuer stability. This is strong when the data is normally distributed*
> 

PCA uses the variance to find the most important features in the data, it then create linear combination of the original features, these are called principal components. You can do PCA with plain pandas and numpy, you need to do this steps:

1. Center the data (subtract the mean from each column)
2. Calculate the covariance matrix
3. Calculate the eigenvectors (autovettori) and eigenvalues(autovalori) of the covariance matrix
4. Sort eigenvectors by the eigenvalues
5. Multiply the centered data by eigenvectors

> *The **covariance** is a measure of how much two variables change together. If the covariance is positive then the variables change together*
>