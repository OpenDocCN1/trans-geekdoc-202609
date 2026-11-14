```
import pandas as pd
import numpy as np
```

When that is done, we can go through and read some of the sample data that will help us to create our analysis. We also want to be able to get a good summary of how this is going to look. Some of the codings that we need to use here include the following:

```
SALES=pd.read_csv("sample-sales.csv")
SALES.head()
```

Take some time to go through this and run the compiler so that you can see what is going to show up, and how the information is going to look. You should get a nice table that has all of the necessary data to make this easier.

When this is all done, we are able to go on to the next step. We want to use what is known as the function of a pivot table. This is going to be used to help us summarize the sales and then will turn the rows of data into something that we are able to use. Since this is our first project, we are going to keep it as simple as possible so work with the code below:

```
report = SALES.pivot_table(values=['quantity'],index=['Account Name'],columns=['category'],aggfunc=np.sum)
report.head(n=10)
```

When we do this, we are going to be able to do a few more things. This particular command is going to show us the number of products that all of