
In conclusion, linear regression is a fundamental algorithm in data science and machine learning. Although it is simple and interpretable, its assumptions and limitations make it suitable for specific problems. For more complex datasets, alternative regression techniques or algorithms may be better suited to capturing the underlying patterns.

# 17.2 Simple Linear Regression

Simple linear regression is a statistical technique used to model the relationship between two variables: a dependent variable (the target to be predicted) and an independent variable (the predictor). The relationship is represented by a straight line described by the equation `𝑦=𝑏0 + 𝑏1𝑥`, where `𝑏0` is the y-intercept (value of `𝑦` when `x = 0`) and `b1` is the slope (change in `𝑦` for a one-unit increase in `𝑥`). It is commonly used to analyze and predict outcomes based on a single predictor, with the line of best fit minimizing the error between observed and predicted values.

## Understanding Simple Linear Regression

Let’s break down the concept of simple linear regression step by step.

### The Equation

The equation for simple linear regression is as follows:

`𝑦 = 𝑏0 + 𝑏1𝑥`

On the left-hand side of the equation, `𝑦` represents the dependent variable—this is the value we aim to predict. On the right-hand side, `𝑥` is the independent variable, also known as the predictor or input feature.

### Components of the Equation

`𝑏0`: This is the y-intercept, also referred to as the constant. It indicates the value of `𝑦` when `𝑥 = 0`

`𝑏1`: This is the slope coefficient, which represents the change in `𝑦` for a one-unit increase in `𝑥`.

### Example: Predicting Corn Yield

To make this concept more concrete, let’s use a practical example: predicting the corn yield on a farm based on the amount of nitrogen fertilizer used.

![Corn cobs in a field AI-generated content may be incorrect.](image_rsrcF2P.jpg)

The equation for this scenario becomes:

`Corn Yield (tons) = 𝑏0 + 𝑏1 × Fertilizer Used (kg)`

Suppose we run a simple linear regression algorithm on the data, and it produces the following coefficients: `𝑏0=5 tons`, `𝑏1=2.5 tons per kilogram`.

## Intuitive Understanding Through Visualization

To better understand what these values mean, let’s visualize them on a graph:

• The x-axis represents the amount of nitrogen fertilizer used (in kilograms), our independent variable.
• The y-axis represents the corn yield (in tons), our dependent variable.

![A diagram of a simple linear regression AI-generated content may be incorrect.](image_rsrcF2R.jpg)

On this graph, we’ll plot a scatter plot of data points. Each point corresponds to a separate harvest where the farmer recorded how much fertilizer was used and the resulting corn yield.

### Interpreting the Line

The equation `𝑦=𝑏0+𝑏1𝑥` is represented by a sloped line that best fits the data points:

The y-intercept (`𝑏0 = 5`): This indicates that if no fertilizer is used (`𝑥=0`), the expected corn yield is 5 tons.

The slope coefficient (`𝑏1 = 2.5`): This means that for every additional kilogram of nitrogen fertilizer used, the corn yield is expected to increase by 2.5 tons.

### Bringing It Together

So, in practical terms: If the farmer uses 4 kilograms of fertilizer, the predicted corn yield would be:

`Y = 5 + 2.5 × 4=15 tons.`

### Key Notes

• The data points on the scatter plot are derived from real observations over multiple harvests.
• The line of best fit (the regression line) minimizes the error between the predicted and actual values.
• The numbers `𝑏0` and `𝑏1` in this example are illustrative and do not represent actual farming data.

This is how simple linear regression works: it provides a mathematical relationship between the predictor (`𝑥`) and the target variable (`𝑦`) and allows us to make predictions based on that relationship.

## 17.2.1 Understanding Ordinary Least Squares (OLS)

Let's revisit our corn and fertilizer example to understand how the Ordinary Least Squares (OLS) method helps us determine the "best" line in Simple Linear Regression.

Imagine we have collected data on corn yield (in tons) and the amount of fertilizer (in kilograms) used. The question is: How do we find the best line that models the relationship between the fertilizer applied and the corn yield?

For example:

• Is it this line?
• Or this one?
• Or perhaps another one?

As you can see, there are several possible lines that could fit our data points. But what does "best" mean? How do we determine which line provides the most accurate relationship between fertilizer and yield?

This is where the Ordinary Least Squares method comes into play. It provides a systematic approach to finding the "best" line for our data.

### How OLS Works

![A graph of the same number of numbers AI-generated content may be incorrect.](image_rsrcF2S.jpg)

#### Visualizing the Fit

To evaluate a line, we compare the actual corn yield (`𝑦i`) from our data to the predicted yield (`![](image_rsrcF2T.jpg)`) from the line. The difference between these two values is called the residual.

• `𝑦i`: The actual yield of corn for a specific amount of fertilizer.
• `![](image_rsrcF2T.jpg)`: The predicted yield of corn for the same fertilizer amount, based on the line we’re considering.

#### Example

Suppose:

• 15 kg of fertilizer was applied, and the actual yield was 3 tons of corn (`𝑦I =3`).
• The line we’re evaluating predicts the yield to be 2.8 tons (`![](image_rsrcF2U.jpg)i=2.8`).

The residual here is the difference: `𝑦i - ![](image_rsrcF2U.jpg)i = 3 − 2.8 = 0.2`

Residuals measure how far off the prediction is from the actual value.

#### Minimizing Residuals

The goal of OLS is to find the line that minimizes the sum of the squared residuals.

Why square the residuals? Squaring ensures all differences (whether positive or negative) are treated equally and emphasizes larger deviations more heavily. The formula for the sum of squared residuals is:

`Sum of Squared Residuals= ![](image_rsrcF2V.jpg)`

Here:

• `𝑦i`: Actual yield values
• `![](image_rsrcF2W.jpg)`: Predicted yield values from the regression line
• `𝑛`: Number of data points (e.g., different fertilizer amounts)

#### Parameters of the Line

The line itself is defined by its equation: `![](image_rsrcF2U.jpg)=𝑏0+𝑏1𝑥𝑖`

where:

• `𝑏0`: Intercept (predicted corn yield when no fertilizer is applied)
• `𝑏1`: Slope (rate of increase in corn yield per kilogram of fertilizer)
• `𝑥𝑖`: Fertilizer amount (in kilograms)

The OLS method works by finding the values of `𝑏0` (intercept) and `𝑏1` (slope) that minimize the sum of squared residuals.

#### Why is it the "Best" Line?

The "best" line minimizes the discrepancies between the predicted corn yield (`![](image_rsrcF2U.jpg)i`) and the actual yield (`𝑦i`) for all fertilizer levels. By minimizing the sum of squared residuals:

• The line closely fits the data points.
• It provides the most accurate linear relationship between fertilizer use and corn yield.

For example: If one line results in a total squared error of 4.5, and another results in 3.8, the second line is the "better" fit because it has smaller errors overall.

#### The Process in Action

• Take each data point (fertilizer amount and corn yield).
• Calculate the residual (`𝑦i - ![](image_rsrcF2U.jpg)i`) for a given line.
• Square each residual to eliminate negative values and emphasize larger differences.
• Sum up these squared residuals for all data points.
• Repeat the process for various lines and select the line with the smallest total squared residuals.

This method ensures the chosen line represents the best possible linear relationship between fertilizer use and corn yield.

#### Summary

• OLS finds the line where the sum of squared residuals (`![](image_rsrcF2X.jpg)`) is minimized.
