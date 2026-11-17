Here are some salient features of Tkinter:

+   * Tkinter is easy to use and quick to develop desktop applications.

+   * The syntax of Tkinter and its widget is simple to understand.

+   * Tkinter is shipped with Python, so you do not need to install it explicitly.

+   * Tkinter is open-source and free to use.

# Build an ML-based app using Tkinter

Here, you need to develop the Python code for data loading, data cleaning, feature engineering, model building and finally, saving trained models to serialized objects like pickles. Then you can use trained models to get predictions on the Tkinter app.

Let's consider a loan prediction scenario, where the goal is to predict whether a customer's loan will be approved. The focus will not be on hyperparameter tuning and model optimization. However, you can optimize a model to improve its overall performance. First, create train.py file as follows:

```
# Import the required packages
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
from sklearn.ensemble import RandomForestClassifier

from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from sklearn import metrics
import pickle
```

For the next step, load the datasets and capture numerical and categorical column names in separate variables.

```
# Load the data
data = pd.read_csv("loan_dataset.csv")
# Missing value treatment (if found)
```