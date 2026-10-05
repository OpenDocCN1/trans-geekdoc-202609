we included the outliers in the calculation, they would have exerted a large
influence and produced a mean of approximately 4.09.

Trimming data is different from winsorizing, as it discards outliers. A 20%
trimmed mean would remove the lowest 10% and highest 10% of the data
and compute the mean. Continuing with our example data, the 20% trimmed
mean would be 5. The code to implement this is the following:

```
from scipy stats
stats.trim_mean(data_win, 0.2)
```

In this section, we looked at transforms for filtering noisy measurements from
data. There are many other useful filters, such as the low-pass filter, Kalman
filter, and Butterworth filter. The analyst will need to decide on the best
transform and its required parameter values. This will depend on the data\and the use case. Visualization and automated evaluation can help. For an
excellent treatment of digital filters, see [31].

# 10.2 Transforms for Treating Scale

# 10.2.1 Order of Magnitude and Use of Logarithm

When we think about scale, we think about a variable $X$ that takes values
in $[0, 10]$, and a second variable $Y$ that generally takes values in $[10, 20]$,
 occasionally takes much larger values such as 10,000. A value's order
of magnitude is that value expressed as a power of 10. It can be written in scientific notation as
1 $	imes 10^4$. Next, let's think about differences in order of magnitude between
two numbers. The difference in order of magnitude between 100 and 200 (or $1 \times 10^2$)\and 10,000 (or $1 \times 10^4$) is large. Large differences in order of magnitude can
cause trouble when visualizing data and fitting certain models to data.
Let us consider a small example, where $x$ and $y$ each contain list of values:

+   x = [0, 1, 2, 3, 4, 5]
y = [10, 10, 20, 20, 10000]

We are expecting the $y$-value of 10,000. Figure 10.3 graphs
datas. As we expected, the 10,000 makes the smaller $y$ values appear
as zero or nearly zero. Depending on the context, this can be problematic.
If the question is: how many fatalities were there in a given year, and $y$
represented these fatalities, then an answer of zero is very different from one,
ten, or twenty.

Since we are trying to better understand all of this data, we are looking
for a way to better represent it. A common technique when facing values
with different orders of magnitude is to take the logarithm of the data using