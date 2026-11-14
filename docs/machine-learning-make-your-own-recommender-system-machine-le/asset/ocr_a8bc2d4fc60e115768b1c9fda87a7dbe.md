known preference will then be sent to the user as part of a promotional email campaign.

# # About Nearest Neighbors

Nearest neighbors is a simple clustering technique that creates clusters based on the closest distance between data points. This technique finds the shortest distance between two data points and fuses them into one cluster. This step is repeated so that the next shortest distance between two data points is found, which either expands the size of the first cluster or forms a new cluster between two individual data points. For this exercise, we are searching for the closest three data points to a specified data point, which is determined by the user’s earlier search query.

# ## Step 1

The first step is to install our libraries. For this exercise, we need to import Pandas and nearest neighbors from Scikit-learn.

```
import pandas as pd
from sklearn.neighbors import NearestNeighbors
```

# ## Step 2

The next step is to import the dataset into Jupyter Notebook using pd.read_csv. The dataset is called Melbourne_housing_FULL and should be first downloaded and unzipped from https://www.kaggle.com/anthonypino/melbourne-housing-market/.

```
df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')
```

This command will load the data into a Pandas dataframe, and we can use the head command to preview the dataset inside Jupyter Notebook.

```
df.head()
```