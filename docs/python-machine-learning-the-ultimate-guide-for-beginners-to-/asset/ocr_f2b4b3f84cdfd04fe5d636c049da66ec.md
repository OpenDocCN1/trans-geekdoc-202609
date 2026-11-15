proximity to every single class. The decision limit needs to be optimal and therefore we cannot just randomly select it. These optimal data points are known as support vectors, hence the name of our algorithm. Keep in mind that they are a mathematical concept and we will not dig too deep into how they are calculated and so on. At this stage you don't need to know the core details that lie in fairly complex algebra.

Now, let's see a practical example on how to apply a support vector machine that does everything we discussed. For this demonstration you will need to use several libraries and packages. Here's the code:

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
dataset = pd.read_csv ("bank_note.csv")
print (dataset.shape)
```

The shape function is used to extract some information about the dataset. Namely, it tells us how many rows and columns we have. For the purpose of this exercise we are interested only in the first 5 rows (out of over 1,300).

Now type the following line to see the result:

```
print (dataset.head())
```

| Variance | Skewness | Curtosis | Entropy | Class |
|---|---|---|---|---|
| 3.62160 | 8.6661 | -2.8073 | -0.44699 | 0 |
| 4.454590 | 8.1674 | -2.4586 | -1.46210 | 0 |
| 3.86600 | -2.6383 | 1.9242 | 0.10645 | 0 |
| 3.45660 | 9.5228 | -4.0112 | -3.59440 | 0 |
| 0.32924 | -4.4552 | 4.5718 | -0.98880 | 0 |

The columns represent the attributes we mentioned earlier, namely the variance, skewness and so on. Now we can start processing this