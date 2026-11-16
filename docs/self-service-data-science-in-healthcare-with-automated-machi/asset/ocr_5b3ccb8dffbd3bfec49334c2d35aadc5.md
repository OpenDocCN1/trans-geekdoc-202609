# Select dataset for processing

You are now using t-test as a dataset to make a subset from. Please also select the target variable in the variables to include. You can select multiple columns by holding the ctrl or shift button while clicking.

+   1. Name of the dataset
+   2. Target variable
+   3. Columns to include

Figure C2. Screenshot 2 of of AutoML artefact A, the Web application interface (preference: GUI).

# AutoML notebook

Hi! Welcome to the AutoML notebook. In this notebook you will be enabled to use AutoML in a few steps.

+   1. Upload a raw dataset
+   2. Create a from this raw dataset to do your analysis on
+   3. Let AutoML create a good model for your data a model based on the provided subset

To use the notebook in the right way you have to run each code block. Above each code block there is an explanation of what is happening.

```
```python
from numpy import argwhere, delete
from pandas import read_csv, read_sql_table, DataFrame
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from tpot import TPOTClassifier
import warnings
warnings.filterwarnings('ignore')
```
```

# Step 1: Upload dataset

Upload a raw dataset, this has to be a .csv file. Copy the filepath into the location variable, use two '\\' instead of one to make sure that the file is uploade and no error is thrown. Denote the separator of the csv file in the separator variable. examples are commented in the lines below. The top of the dataframe is shown if it is successful.

```
```python
#separator = ","
location = "C:\\Users\\vrooms\\Desktop\\dataset_37_diabetes.csv"
separator = ","
location = 'D:\\22B\\_5. - RAPP - GWI - ML.csv'
df = pd.read_csv(location, sep = separator)
df.head()
```
```

|   | preg | plas | pres | skin | insu | mass | pedi | age | class |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 6 | 148 | 72 | 35 | 0 | 33.6 | 0.627 | 50 | tested_positive |
| 1 | 1 | 85 | 66 | 29 | 0 | 26.6 | 0.351 | 31 | tested_negative |
| 2 | 8 | 183 | 64 | 0 | 0 | 23.3 | 0.672 | 32 | tested_positive |
| 3 | 1 | 89 | 66 | 23 | 94 | 28.1 | 0.167 | 21 | tested_negative |
| 4 | 0 | 137 | 40 | 35 | 168 | 43.1 | 2.288 | 33 | tested_positive |

All variables that are not numeric are label-encoded to numeric values in this code section, so that the AutoML method can read your data. The output of this code block is a list with the names of the variables in your dataset.

Figure C3. Screenshot of AutoML artefact B, the Jupyter notebook interface (preference: Code).

# Appendix D

Overview of the refined hypotheses. For user interaction the hypotheses are:

+   1. Artefact A is preferred over Artefact B to upload a dataset.
+   2. Artefact A is preferred over Artefact B to create a subset.
+   3. Artefact B is preferred over Artefact A to find the way in the different steps.
+   4. Artefact B is preferred over Artefact A for the explanations of the workflow.

For model construction the hypotheses are:

+   1. Artefact B is preferred over Artefact A for progress reporting on model construction.
+   2. Artefact B is preferred over Artefact A for model construction.