# 7.5.1 Data Loading from S3 and Library.

Now we will load all the required Python Library for our model building and deployment.

```
import numpy as np
import pandas as pd
import boto3
import re
import sagemaker
from sagemaker import get_execution_role
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.base import TransformerMixin
from warnings import filterwarnings
filterwarnings('ignore')
from sklearn.base import BaseEstimator, TransformerMixin,
RegressorMixin, clone
from sklearn.neighbors import LocalOutlierFactor
```

Load the IAM Role which has been created during the notebook instance.

```
role = get_execution_role()
role
```