# Predicting Numerical Values:
Getting Started with Regression

```
In [1]:
# setup
from mlwpy import *
%matplotlib inline
```

# 4.1 A Simple Regression Dataset

Regression is the process of predicting a finely graded numerical value from inputs. To illustrate, we need a simple dataset that has numerical results. sklearn comes with the diabetes dataset that will serve us nicely. The dataset consists of several biometric and demographic measurements. The version included with sklearn has been modified from raw numerical features by subtracting the mean and dividing by the standard deviation of each column. That process is called standardizing or z-scoring the features. We’ll return to the standard deviation later; briefly, it is a measure of how spread out a set of values are.

The net result of standardizing the columns is that each column has a mean of 0 and a standard deviation of 1. We standardize, or otherwise rescale, the data so that differences in feature ranges—heights within 50–100 inches or incomes from $20,000 to $200,000—don’t incur undo weight penalties or benefits just from their scale. We’ll discuss standardization and scaling more in Section 10.3. The categorical values in diabetes were recorded numerically as {0, 1} and then standardized. I mention it to explain why there are negative ages (the mean age is zero after standardizing) and why the sexes are coded, or recorded, as {0.0507, −0.0446} instead of {M, F}.