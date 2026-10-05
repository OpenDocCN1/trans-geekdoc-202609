# 9. Logistic regression code

The logistic regression code is given in Table A.2.

Table A.2 Logistic regression code.

```
import numpy as np pandas as pd import deepchem as dc
from sklearn.model_selection import train_test_split
from sklearn.decomposition import PCA
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, roc_auc_score, f_1
from sklearn.model_selection import KFold import matplotlib.pyplot as plt # If you use
 Colab to run the code you need to mount the drive # If you use your computer to
run the code, do not need these commands from google.colab import drive
drive.mount('/content/drive') # Read data
data = pd.read_csv('/content/drive/My Drive/tox21.csv')
smiles = data.loc[:,columns=='smiles'] labels = data.loc[:,columns=='NR-AR-LBD'] # use DeepChem to extract ECF features features for SMILES sample
featurizer = dc.feat_cross.CircularFingerprint(size=1024) XD=[] for i in range(len(smiles)):
efp = featurizer.featurize(smiles[i]) ecfp = np.squeeze(ecfp) XD.append(ecfp) XD =
p.array(XD) labels = np.array(labels) removes NaN labels from the dataset
index = np.where(~np.isnan(labels)) labels = labels[index[0]] XD = XD[index[0]]; # To
evaluate the k-fold cross-validation is used KFold(n_splits=5) acc=, acc_t=[]
f1=[], f1_t=[]; roc=[], roc_t=[] for train_index, test_index in k.split(XD):
print("TRAIN:", "TEST:", test_index)
X_train, X_test = XD[train_index], XD[test_index]
y_train, y_test = labels[train_index], labels[test_index] # Fit Logistic regression models on
training samples
clf = LogisticRegression(random_state=0, class_weight='balanced').fit(X_train, y_train)
y_pred = clf.predict(X_train) # Compute evaluation measures on training samples in each
fold acc.append(accuracy_score(y_train, y_pred)) f1.append(f1_score(y_train, y_pred))
roc.append(roc_score(y_train, y_pred)) y_pred = clf.predict(X_test) # Compute
```