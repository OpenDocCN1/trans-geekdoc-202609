# CHAPTER 4 Classical algorithms for tabular data

The distribution shown in figure 4.1 is extremely skewed to the right, with many outlying values being the plotted values up to 10,000. However, before 2,000, it is hard to distinguish any bar depicting such frequencies. This becomes even more evident by plotting a boxplot, which is a very useful tool when one to visualize the core part of the distribution of a variable lies. A boxplot for a variable is a plot where the key measurements of the distribution are depicted as a box with "whiskers": two lines outside the box that stretch to the expected limits of the variables' distribution. The box is delimited by the interquartile range (IQR), determined by the 25th and 75th percentiles, and split into two by the line of the median. The whiskers stretch up and down to 1.5 times the IQR. Everything above or below the edges is considered an outlier: an unusual or unexpected value. Let's plot a boxplot for the price variable, using a built-in method in pandas DataFrame, the boxplot method (see 4.2):

![](bbox=[0.176, 0.403, 0.824, 0.655])

Not surprisingly, the box and whiskers are squeezed in the lower part of the chart and are almost indistinguishable from each other. A long queue of outliers elongates from the upper limit of the upper extremity of the boxplot. This is an evident case of a skewed distribution. In such cases, a standard solution to remediate the variable is to transform the target using a logarithm transformation. It is common practice to add a constant to offset the values into the positive number field for handling values of zero and below. In our case, it is unnecessary, since all the values are positive and above zero. In the following code snippet, we represent the transformed price feature by application of a logarithmic transformation (see figures 4.3 and 4.4):

```
np.log1p(data[`
```