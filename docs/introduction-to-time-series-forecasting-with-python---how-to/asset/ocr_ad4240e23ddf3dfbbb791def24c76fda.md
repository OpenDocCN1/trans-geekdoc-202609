+   • Weekend or not.
• Season of the year.
• Business quarter of the year.
• Daylight savings or not.
• Public holiday or not.
• Leap year or not.

From these examples, you can see that you’re not restricted to the raw integer values. You can use binary flag features as well, like whether or not the observation was recorded on a public holiday. In the case of the minimum temperature dataset, maybe the season would be more relevant. It is creating domain-specific features like this that are more likely to add value to your model. Date-time based features are a good start, but it is often a lot more useful to include the values at previous time steps. These are called lagged values and we will look at adding these features in the next section.

# 5.5  Lag Features

Lag features are the classical way that time series forecasting problems are transformed into supervised learning problems. The simplest approach is to predict the value at the next time (t+1) given the value at the current time (t). The supervised learning problem with shifted values looks as follows:

```
Value(t), Value(t+1)
Value(t), Value(t+1)
Value(t), Value(t+1)
```

Listing 5.6: Example of lag features.

The Pandas library provides the shift() function1 to help create these shifted or lag features from a time series dataset. Shifting the dataset by 1 creates the t column, adding a NaN (unknown) value for the first row. The time series dataset without a shift represents the t+1. Let’s make this concrete with an example. The first 3 values of the temperature dataset are 20.7, 17.9, and 18.8. The shifted and unshifted lists of temperatures for the first 3 observations are therefore:

```
Shifted,  Original
NaN,     20.7
20.7,     17.9
17.9,     18.8
```

Listing 5.7: Example of manually shifted rows.

We can concatenate the shifted columns together into a new DataFrame using the concat() function2 along the column axis (axis=1). Putting this all together, below is an example of

1http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.shift.html
2http://pandas.pydata.org/pandas-docs/stable/generated/pandas.concat.html