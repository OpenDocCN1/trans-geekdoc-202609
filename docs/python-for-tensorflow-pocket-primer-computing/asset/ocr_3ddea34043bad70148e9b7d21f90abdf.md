Listing 3.4 defines the Pandas DataFrame df that consists of 5 rows and 2 columns of random integers between 1 and 5. Notice that the columns of df are labeled "a" and "b." In addition, the next code snippet adds two rows consisting of the sum and the mean of the numbers in both columns. The output of Listing 3.4 is:

```
a      b
0     1.0  2.0
1     1.0  1.0
2     4.0  3.0
3     3.0  1.0
4     1.0  2.0
sum    10.0  9.0
mean   2.0  1.8
```

# COMBINING PANDAS DATAFRAMES (1)

Listing 3.5 displays the contents of Pandas-combine-df.py that illustrates how to combine Pandas DataFrames.

# LISTING 3.5: pandas-combine-df.py

```
import pandas as pd
import numpy as np

df = pd.DataFrame({'foo1' : np.random.randn(5),
                   'foo2' : np.random.randn(5)})

print("contents of df:")
print(df)

print("contents of foo1:")
print(df.foo1)
```