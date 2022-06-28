# Reading 13 
## Linear Regression in Python

> What Is Regression? 
- Regression searches for relationships among variables. 
- For example, you can observe several employees of some company and try to understand how their salaries depend on their features, such as experience, education level, role, city of employment, and so on.
- This is a regression problem where data related to each employee represents one observation. The presumption is that the experience, education, role, and city are the independent features, while the salary depends on them.
- you can try to establish the mathematical dependence of housing prices on area, number of bedrooms, distance to the city center, and so on.
- Generally, in regression analysis, you consider some phenomenon of interest and have a number of observations. Each observation has two or more features.


> When Do You Need Regression?
- Typically, you need regression to answer whether and how some phenomenon influences the other or how several variables are related.
- For example, you can use it to determine if and to what extent experience or gender impacts salaries.
- It is also useful when you want to forecast a response using a new set of predictors.


> Problem Formulation 
- When implementing linear regression of some dependent variable 𝑦 on the set of independent variables 𝐱 = (𝑥₁, …, 𝑥ᵣ), where 𝑟 is the number of predictors
- you assume a linear relationship between 𝑦 and 𝐱: 𝑦 = 𝛽₀ + 𝛽₁𝑥₁ + ⋯ + 𝛽ᵣ𝑥ᵣ + 𝜀. This equation is the regression equation.
- 𝛽₀, 𝛽₁, …, 𝛽ᵣ are the regression coefficients, and 𝜀 is the random error.


> Regression Performance
- The variation of actual responses 𝑦ᵢ, 𝑖 = 1, …, 𝑛, occurs partly due to the dependence on the predictors 𝐱ᵢ. However, there’s also an additional inherent variance of the output.
- The coefficient of determination, denoted as 𝑅², tells you which amount of variation in 𝑦 can be explained by the dependence on 𝐱, using the particular regression model. 
  - Simple Linear Regression
  - ![Simple Linear Regression](https://files.realpython.com/media/fig-lin-reg.a506035b654a.png)


> Multiple Linear Regression
- Multiple or multivariate linear regression is a case of linear regression with two or more independent variables.
- If there are just two independent variables, then the estimated regression function is 𝑓(𝑥₁, 𝑥₂) = 𝑏₀ + 𝑏₁𝑥₁ + 𝑏₂𝑥₂.


> Polynomial Regression
- You can regard polynomial regression as a generalized case of linear regression. 
- You assume the polynomial dependence between the output and inputs and, consequently, the polynomial estimated regression function.


> Underfitting and Overfitting
- One very important question that might arise when you’re implementing polynomial regression is related to the choice of the optimal degree of the polynomial regression function.
- There’s no straightforward rule for doing this.
- It depends on the case
- You should, however, be aware of two problems that might follow the choice of the degree: underfitting and overfitting.
  - Underfitting: 
    - occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity. 
    - It often yields a low 𝑅² with known data and bad generalization capabilities when applied with new data.
  - Overfitting : 
    - it happens when a model learns both data dependencies and random fluctuations.
    - In other words, a model learns the existing data too well. Complex models, which have many features or terms, are often prone to overfitt


> Python Packages for Linear Regression
- NumPy 
  - is a fundamental Python scientific package that allows many high-performance operations on single-dimensional and multidimensional arrays
- scikit-learn
  - it is a widely used Python library for machine learning, built on top of NumPy and some other packages. 
  - It provides the means for preprocessing data, reducing dimensionality, implementing regression, classifying, clustering etc.


> Example of using Linear Regression in python
- Import the packages and classes that you need.
```
>>> import numpy as np
>>> from sklearn.linear_model import LinearRegression
```
- Provide data to work with, and eventually do appropriate transformations.
```
>>> x = np.array([5, 15, 25, 35, 45, 55]).reshape((-1, 1))
>>> y = np.array([5, 20, 14, 32, 22, 38])
```
- Create a regression model and fit it with existing data.
```
>>> model = LinearRegression()
```
- the above statement creates the variable model as an instance of LinearRegression. You can provide several optional parameters to LinearRegression:
  - fit_intercept is a Boolean that, if True, decides to calculate the intercept 𝑏₀ or, if False, considers it equal to zero. It defaults to True.
  - normalize is a Boolean that, if True, decides to normalize the input variables. It defaults to False, in which case it doesn’t normalize the input variables.
  - copy_X is a Boolean that decides whether to copy (True) or overwrite the input variables (False). It’s True by default.
  - n_jobs is either an integer or None. It represents the number of jobs used in parallel computation. It defaults to None, which usually means one job. -1 means to use all available processors.


- Check the results of model fitting to know whether the model is satisfactory.

```
>>> r_sq = model.score(x, y)
>>> print(f"coefficient of determination: {r_sq}")
coefficient of determination: 0.7158756137479542
```

```
>>> print(f"intercept: {model.intercept_}")
intercept: 5.633333333333329

>>> print(f"slope: {model.coef_}")
slope: [0.54]
```


- Apply the model for predictions.
```
>>> y_pred = model.predict(x)
>>> print(f"predicted response:\n{y_pred}")
predicted response:
[ 8.33333333 13.73333333 19.13333333 24.53333333 29.93333333 35.33333333]
```
```
>>> y_pred = model.intercept_ + model.coef_ * x
>>> print(f"predicted response:\n{y_pred}")
predicted response:
[[ 8.33333333]
 [13.73333333]
 [19.13333333]
 [24.53333333]
 [29.93333333]
 [35.33333333]]
```

> Beyond Linear Regression
- Linear regression is sometimes not appropriate, especially for nonlinear models of high complexity.
- Fortunately, there are other regression techniques suitable for the cases where linear regression doesn’t work well.
- Some of them are support vector machines, decision trees, random forest, and neural networks.
- There are numerous Python libraries for regression using these techniques.
  - Most of them are free and open-source. That’s one of the reasons why Python is among the main programming languages for machine learning.
- The package scikit-learn provides the means for using other regression techniques in a very similar way to what you’ve seen.
  - It contains classes for support vector machines, decision trees, random forest, and more, with the methods .fit(), .predict(), .score(), and so on.


> Conclusion
- linear regression is and how you can implement it with Python and three open-source packages: NumPy, scikit-learn, and statsmodels.
- You use NumPy for handling arrays. Linear regression is implemented with the following:
  - scikit-learn if you don’t need detailed results and want to use the approach consistent with other regression techniques
  - statsmodels if you need the advanced statistical parameters of a model


> _________________________________________THE END _________________THANKS FOR READING _________________________________________

> Resources
- https://realpython.com/linear-regression-in-python/#linear-regression
- https://www.crayondata.com/how-to-run-linear-regression-in-python-scikit-learn/


