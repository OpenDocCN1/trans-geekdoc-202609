
NumPy arrays support "reshape" method that enables you to restructure the dimensions of an array of numbers. In general, if a NumPy array contains m elements, where m is a positive integer, then that array can be restructured as an m1 x m2 NumPy array, where m1 and m2 are positive integers such that m1*m2 = m.

Listing 2.17 displays the contents of numpy-reshape.py that illustrates how to use the reshape() method on a NumPy array.

# LISTING 2.17: numpy-reshape.py

```
import numpy as np

x = np.array([[2, 3], [4, 5], [6, 7]])
print(x.shape) # (3, 2)

x = x.reshape((2, 3))
print(x.shape) # (2, 3)
print('x1:',x)

x = x.reshape((-1))
print(x.shape) # (6,)
print('x2:',x)

x = x.reshape((6, -1))
print(x.shape) # (6, 1)
print('x3:',x)

x = x.reshape((-1, 6))
print(x.shape) # (1, 6)
print('x4:',x)
```

Listing 2.17 contains a NumPy array called x whose dimensions are 3x2, followed by a set of invocations of the reshape() method that reshape the contents of x. The first invocation of reshape() method changes the shape of x from 3x2 to 2x3. The second invocation changes the shape of x from 2x3 to 6x1. The third invocation changes the shape of x from 1x6 to 6x1. The final invocation changes the shape of x from 6x1 to 1x6 again.

Each invocation of the reshape() method is followed by a print() statement so that you can see the effect of the invocation. The output from launching Listing 2.17 is here:

```
(3, 2)
(2, 3)
'x1': array([[2, 3, 4],
[5, 6, 7]])
(6,)
'x2': array([2, 3, 4, 5, 6, 7])
(6, 1)
'x3': array([[2,
[3],
[4],
[5],
[6],
[7]])
```

# CALCULATING THE MEAN AND STANDARD DEVIATION

If you need to review these concepts from statistics (and perhaps also the mean, median, and mode as well), please read the appropriate on-line tutorials.

NumPy provides various built-in functions that perform statistical calculations, as the the following list of methods:

```
np.linspace() <= useful for regression
np.mean()
np.std()
```

The np.linspace() method generates a set of equally spaced numbers between a lower bound and an upper bound. The np.mean() and np.std() methods calculate the mean and standard deviation, respectively, of a set of numbers. Listing 2.18 displays the contents of sample-mean-std.py that illustrates how to calculate statistical values from an array.

# LISTING 2.18: sample-mean-std.py

```
import numpy as np

x2 = np.arange(8)
print('mean = ',x2.mean())
print('std = ',x2.std())
```

```
x3 = (x2 - x2.mean())/x2.std()
print('x3 mean = ',x3.mean())
print('x3 std = ',x3.std())
```

Listing 2.18 contains a NumPy array x2 that consists of the first eight integers. Next, the mean() and std() that are “associated” with x2 are invoked in order to calculate the mean and standard deviation, respectively, of the elements of x2. The output from launching Listing 2.18 is here:

```
('a':         array([1, 2]))
('b':         array([3, 4]))
```

# CALCULATING MEAN AND STANDARD DEVIATION

The code sample in this section extends the code sample in the previous section with additional statistical values, and the code in Listing 2.19 can be used for any data distribution. Keep in mind that the code sample uses random numbers simply for the purposes of illustration; after you have launched the code sample, replace those numbers with values from a CSV file or some other dataset containing meaningful values.

Moreover, this section does not provide details regarding the meaning of quartiles, but you can learn about quartiles here:
https://en.wikipedia.org/wiki/Quartile

Listing 2.19 displays the contents of stat-values.py illustrates how to display various statistical values from a NumPy array of random numbers.

# LISTING 2.19: stat-values.py

```
import numpy as np

from NumPy import percentile
from NumPy.random import rand

# generate data sample
data = np.random.rand(1000)

# calculate quartiles, min, and max
quartiles = percentile(data, [25, 50, 75])
data_min, data_max = data.min(), data.max()

# print summary information
print('Minimum: %.3f' % data_min)
print('Q1 value: %.3f' % quartiles[0])
print('Median: %.3f' % quartiles[1])
print('Mean Val: %.3f' % data.mean())
print('Std Dev: %.3f' % data.std())
print('Q3 value: %.3f' % quartiles[2])
print('Maximum: %.3f' % data_max)
```

The data sample (shown in bold) in Listing 2.19 is from a uniform distribution between 0 and 1. The NumPy percentile() function calculates a linear interpolation (average) between observations, which is needed to calculate the median on a sample with an even number of values. As you can surmise, the NumPy functions min() and max() calculate the smallest and largest values in the data sample. The output from launching Listing 2.19 is here:

```
Minimum: 0.000
Q1 value: 0.237
Median: 0.500
Mean Val: 0.495
Std Dev: 0.295
Q3 value: 0.747
Maximum: 0.999
```

Chapter 4: VISUALIZATION

Now that you have seen some basic examples of lines in the Euclidean plane, let us look at some code samples that use NumPy and Matplotlib to display scatter plots of points in the plane.

# PLOTTING A LINE WITH NUMPY AND MATPLOTLIB

Listing 2.20 displays the contents of np-plot.py that illustrates how to plot multiple points on a line in the plane.

# LISTING 2.20: np-plot.py

```
import numpy as np
import matplotlib.pyplot as plt

x = np.random.randn(15,1)
```
