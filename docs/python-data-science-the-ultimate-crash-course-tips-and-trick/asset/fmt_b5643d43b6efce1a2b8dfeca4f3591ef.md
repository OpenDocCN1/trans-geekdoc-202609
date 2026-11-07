
# Reading CSV with Pandas

Reading the csv file from Kaggle using pandas (`pd.read_csv`).

```python
In [3]: df.isnull().any()
Out[3]:
id               False
date             False
price            False
bedrooms         False
bathrooms        False
sqft_living      False
sqft_lot         False
...
dtype: bool
```

Checking to see if any of our data has null values. If there were any, we’d drop or filter the null values out.

```python
In [4]: df.dtypes
Out[4]:
id                 int64
date              object
price            float64
bedrooms           int64
bathrooms        float64
sqft_living        int64
sqft_lot           int64
...
dtype: object
```

Ok, at first this is going to seem like a mess and it is hard to understand what is here to start with. But now we are going to spend some time going through all of this to figure out what is there, and why all of it is going to be so important to the work that we are trying to accomplish. To start here, we took some time to import the data frame from the CSV file with the help of the `Pandas` library. Then we made sure to check whether or not this would read in the proper manner. The `isnull()` function is in place to make sure that any of the data we have will be usable for the regression that we want to accomplish. When we are doing this in real life, a single column could possibly have the data in the form of strings, integers, or `NaN`, all in one place. This means that you will need to take some time in your own project to double-check that all of the types are matching and that the data you are using is going to be suitable for the regression that you are doing here. Since we are just doing a practice one here, the set of data that we are using is going to be prepared already, so it is ready to go, unlike most other databases. With this in mind, it is time for us to get a better understanding of the data that we are working with before we go any further. It is important for us to go through the shape of the data and see whether or not the data seems to be reasonable or not. Corrupted data is not that uncommon so it is going to be good practice for us to run two checks, otherwise, the information that we get in our algorithm is not going to be as accurate as we would like.

## Data Checks and Descriptive Statistics

In the first check, we are going to use the function of `df.describe()`. This one is helpful to work with because it helps us to look at all of the variables that are found in our analysis. When that part is done, we are going to spend some time plotting the histograms of the variables that the analysis is targeting using the function of `plt.pyplot.hist()`. The coding that we are going to work with here, and the output that comes with it will include:

```python
In [5]: df.describe()
Out[5]:
```

|  || price  || bedrooms  || bathrooms  || sqft_living  |
| --- | --- | --- | --- | --- |
| count  || 21613  || 21613  || 21613  || 21613  |
| --- | --- | --- | --- | --- |
| mean  || 540088.10  || 3.37  || 2.11  || 2079.90  |
| std  || 367127.20  || 0.93  || 0.77  || 918.44  |
| min  || 75000.00  || 0.00  || 0.00  || 290.00  |
| 25%  || 321950.00  || 3.00  || 1.75  || 1427.00  |
| 50%  || 450000.00  || 3.00  || 2.25  || 1910.00  |
| 75%  || 645000.00  || 4.00  || 2.50  || 2550.00  |
| max  || 7700000.00  || 33.00  || 8.00  || 13540.0 0  |

Quick takeaways: We are working with a data set that contains 21,613 observations, the mean price is approximately $540k, the median price is approximately $450k, and the average house’s area is 2080 ft2

## Visualizing Distributions

```python
fig = plt.figure(figsize=(12, 6))
sqft = fig.add_subplot(121)
cost = fig.add_subplot(122)
sqft.hist(df.sqft_living, bins=80)
sqft.set_xlabel('Ft^2')
sqft.set_title("Histogram of House Square Footage")
cost.hist(df.price, bins=80)
cost.set_xlabel('Price ($)')
cost.set_title("Histogram of Housing Prices")
plt.show()
```

In the coding that we did above, we used `matplotlib` to help us print out two different histograms. Go ahead and work through this one to see how these histograms are going to look through in your compiler. These are going to show us the distribution of housing prices compared to the square footage that is in each house. What we are going to find here is that both variables are going to come with a distribution that is skewed to the right, though one is a bit more than the other. This is going to provide us with a good sense of the set of data that we are working with, and we also know more about the distributions of the variables that we would like to measure as well. With all of this in place, we are able to move on and work with our regression analysis to learn more about the information and how it is able to help us.

## OLS Regression Analysis

First, we will need to import the stats models to get the least-squares regression estimator function. The module that we are going to use here is known as the Ordinary Least Squares, and it is going to take on the majority of the work when it comes to crunching some of the numbers that we need for a Python regression. The coding that we are going to need to make this one happens will include the following:

```python
In [15]: import statsmodels.api as sm
from statsmodels.formula.API import ols
```

When you code to produce a linear regression summary with `OLS` with only two variables this will be the formula that you use:

```python
Reg = ols('Dependent variable ~ independent variable(s)', dataframe).fit()
print(Reg.summary())
```

When we look at housing prices and square footage for houses in King’s county, we print out the following summary report:

```python
In [16]: m = ols('price ~ sqft_living', df).fit()
print(m.summary())
```

When we take a few moments to print out the summary that we need for this regression, all of the information that is relevant to our questions will be easily found. This is going to include things like the coefficients of correlation, standard error, t-statistics, R-squared, and more. Looking at what output we are able to get form this, it is clear that there is going to be a huge relationship that shows up in the market between the housing prices and the square footage of the house. When you go through this, you will find that there is also a decent amount of magnitude that shows up in the process as well. For example, every time we add in additional 100-square feet to home, we will find that the pricing of that house, on average, is going to be about $28,000 higher. It is easy to adjust this formula in order to include more than one variable that is independent, based on what information we would like to be able to do with this kind of program.

As we can see, working with a regression problem in Python and using it to help us sort through some of our data and learn more about how this process is meant to work is going to be beneficial to us in many ways. In the examples above, we spent our time looking at what correlation between the housing prices and the amount of square footage that was in the house for a specific market. But we can work with the same kind of idea no matter what our business problem may be, or how we would like to work with this data science process.
