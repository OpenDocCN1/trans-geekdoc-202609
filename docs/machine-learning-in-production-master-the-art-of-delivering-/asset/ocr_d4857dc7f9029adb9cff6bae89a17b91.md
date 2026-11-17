Now, let’s install whylogs, if it’s not already installed, using the following command, or simply install whylogs using pip:

```
pip install -q "whylogs[whylabs]"
```

First, declare variables with org id, access key, and project id. Next, load the data and build the model.

```
1. whylabs_org = 'org-ELqbpF'
2. whylabs_key = '0Ji9w2gC7q.
lQQ4pxgQBEUdx********************D0vvDrL'
3. whylabs_project = 'model-5'
4.
5. # Importing the required packages
6. import numpy as np
7. import pandas as pd
8. from sklearn.linear_model import LogisticRegression
9.
10. from sklearn import preprocessing
11. from sklearn.model_selection import train_test_split,
GridSearchCV
12. from sklearn import metrics
13. import whylogs as why
14. import os
15. from whylogs.api.writer.whylabs import WhyLabsWriter
16. import datetime as dt
17. writer = WhyLabsWriter()
18. os.environ["WHYLABS_DEFAULT_ORG_ID"] = whylabs_org # ORG-ID is
case sensitive
19. os.environ["WHYLABS_API_KEY"] = whylabs_key
20. os.environ["WHYLABS_DEFAULT_DATASET_ID"] = whylabs_project
21.
22. # Read the data
23. data = pd.read_csv("https://gist.githubusercontent.
com/suhas-ds/a318d2b1dda8d8cbf2d6990a8f0b7e8a/
raw/9b548fab0952dd12b8fdf057188038c8950428f1/loan_dataset.csv")
```