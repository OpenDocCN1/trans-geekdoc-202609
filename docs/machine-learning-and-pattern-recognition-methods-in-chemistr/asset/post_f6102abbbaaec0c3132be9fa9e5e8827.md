
# Table A.2 Logistic regression code—cont'd

| evaluation measures on test samples in each fold |
| :--- |
| acc_t.append(accuracy_score(y_test, y_pred)) f1_t.append(score(y_test, y_pred)) |
| roc_t.append(roc_auc_score(y_test, y_pred)) # Print the results on training samples |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
| # Print the results on test samples print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 10. Support vector machine

The SVM is given in Table A.3.

Table A.3 Support vector machine.

| import numpy as np pandas as pd import deepchem as dc |
| :--- |
| from sklearn.linear_model import LogisticRegression |
| from sklearn.metrics import accuracy_score, roc_auc_score, f1_score |
| from sklearn.model_selection import KFold from sklearn.svm import SVC # If you use |
| Google Colab to run the code you need to mount the drive # If you use your computer to |
| run the code, you do not need these commands from google.colab import |
| drive.mount('/content/drive') # Read data |
| data = np.read_csv('/content/drive/My_tox21.csv') |
| smiles = data.loc[:], data.columns = 'smiles' labels = data.loc[:], data.columns = 'NR-AR-LBD' # Use DeepChem to extract ECFP features for EACH SMILES sequence |
| featureizer = dc.CircularFingerprint(size=1024) ecfp = featureizer.featurize(smiles) |
| XD=[] for i in range(len(smiles)): ecfp = featureizer.featurize(smiles.loc[i]) ecfp = |
| np.square(ecfp) XD = np.append(XD,index[0]) # To evaluate the model, k-fold cross-validation is |
| samples with NaN labels from the dataset index = np.where(np.isnan(labels)) labels = |
| labels[index[0]] k=KFold(splits=5) kf.get_n_splits(XD) acc=1, acc_t=[], f1_t=[], roc_t=[] |
| [] for train_index, test_index in kf.split(XD): |
| X_train, X_test = XD[train_index], XD[test_index] |
| y_train, y_test = labels[train_index], labels[test_index] y_train = y_train + (-1)*(train==0) |
| y_test = y_test + (-1)*(test==0) # Fit SVM models on training samples. The kernel |
| parameter could be set to another value. For help, please see the documentation of or |
| the scikit-learn package. |
| clf = SVC(gamma='auto', kernel='rbf', class_weight='balanced').fit(X_train, y_train) |
| y_pred = clf.predict(X_train) # Compute evaluation measures on training samples in |
| fold acc.append(accuracy_score(y_train, y_pred)) f1.append(f1_score(y_train, y_pred)) |
| roc.append(roc_auc_score(y_train, y_pred)) y_pred = clf.predict(X_test) # Compute |

# Table A.3 Support vector machine—cont'd

| evaluation measures on test samples in each fold |
| :--- |
| acc_t.append(accuracy_score(y_test, y_pred)) f1_t.append(score(y_test, y_pred)) |
| roc_t.append(roc_auc_score(y_test, y_pred)) # Print the results on training samples |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
# # Print the results on test samples print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 11. Random forest code

The random forest code is given in Table A.4.

# Table A.4 Random forest.

```python
import numpy as np pandas as pd import deepchem as ds
from sklearn.metrics import accuracy_score, roc_auc_score, f1_score
from sklearn.model_selection import KFold
from sklearn.ensemble import RandomForestClassifier # If you use Google Colab to run
t code you need to mount the drive # If you use your computer to run the code, you do not
need these commands from google.colab drive.mount('/content/drive') # Read
data data = pd.read_csv('/drive/smiles.csv'); labels = data.loc[:]; data.columns == 'NR-AHR' # should choose another task # Use DeepChem to extract ECFP features for each SMILES sequence featurizer=dc.CircularFingerprint(size=1024) XD = []
for i in range(len(smiles)): ecfp = featurizer.featurize(smiles.loc[i]) ecfp = np.squeeze(ecfp)
XD.append(ecfp) labels = np.array(labels) # Remove samples with NaN from dataset index = np.where(np.isnan(labels)) labels = labels[index[0]]
X = XD[index[0], # Use cross-validation to evaluate the model
kf = KFold(n_splits=5); acc = [], acc_t = [], f1_t = [], roc_t = [] # for train_index, test_index in kf.split(XD)
print("TRAIN", train_index, "TEST:", test_index)
X_train, X_test = XD[train_index], XD[test_index]
y_train, y_test = labels[train_index], labels[test_index] # Fit the random forest model on training samples. "estimators", "criterion", and "max_depth" could be set to another value. For help, please see the documentation of the scikit-learn package.
clf = RandomForestClassifier(estimators=100,criterion='gini',class_weight='balanced',max_depth=4).fit(X_train, y_train)
y_pred = clf.predict(X_train) # Compute evaluation measures on training samples in each fold acc.append(accuracy_score(y_train, y_pred)) f1.append(f1_score(y_train, y_pred)) roc.append(roc_auc_score(y_train, y_pred))
y_pred = clf.predict(X_test) # Compute evaluation on test samples in each fold acc_test.append(accuracy_score(y_test, y_pred))
```

# Table A.4 Random forest—cont'd

| roc_t.append(roc_auc_score(y_test, y_pred)) # Print the results on training samples |
| print(np.mean(np.array(acc))) print(np.mean(np.array(f1))) print(np.mean(np.array(roc))) |
| # Print the results on training samples print(np.mean(np.array(acc_t))) |
| print(np.mean(np.array(f1_t))) print(np.mean(np.array(roc_t))) |

# 12. Deep learning for regression task

The deep learning for the regression task is given in Table A.5.

Table A.5 Deep learning for regression task.

```python
import numpy as np pandas as pd import keras
from keras.models import Model
from keras.preprocessing import sequence
from keras.models import Sequential, load_model
from keras.layers import Dense, Dropout, Activation
from keras.layers import Embedding
from keras.models import Model
from keras.callbacks import ModelCheckpoint, EarlyStopping
from keras import optimizers, layers from tensorflow.keras import regularizers
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score # If you use Google Colab
run the code need to mount the drive to your computer to run the code, you not need these commands from google.colab drive.mount('/content/drive') # Read data data = pd.read_csv('/content/Drive/Delney-processed.csv')
smiles = data.loc['smiles']
labels = data.loc['ESOL predicted log solubility in mols per litre'] # Show each element of SMILES sentences with an integer (number)
smiles_dict = {"#2": "29", "#30": "31", "#31": "1", "#4": "32", "#33": "34", "#2": "2", "#35": "0", "#3": "3", "#36": "2", "#4": "5", "#37": "4", "#5": "7", "#8": "6", "#9": "9", "#8": "7", "#40": "4", "#41": "A", "#42": "8", "#42": "B", "#9": "E", "#43": "D", "#10": "G", "#44": "F", "#11": "#45": "H5", "#12": "K", "#46": "M", "#47": "L", "#13": "O", "#48": "N", "#14": "P", "#15": "S", "#49": "#16": "R", "#16": "U", "#50": "T", "#17": "W", "#51": "V", "#18": "Y", "#52": "#53": "Z", "#23": "Z", "#19": "54", "#20": "a", "#55": "s", "#56": "b", "#21": "e", "#57": "d", "#22": "g", "#58": "#23": "f", "#24": "l", "#59": "h", "#60": "o", "#25": "i", "#61": "n", "#26": "s", "#62": "#27": "t", "#28": "u", "#64": "6", "#65": "6", "#67": "67", "#68": "p", "#69": "j"}
```

# Table A.5 Deep learning for regression task—cont'd

| and set X_train, X_test, y_train, y_test = train_test_split(labels, test_size=0.3) |
| :--- |
| Define the architecture of the model XInput(shape=(100,)) |
| FC1 = Dense(1024, activation='relu')(XInput) |
| FC2 = Dropout(0.1)(FC1) |
| FC3 = Dense(1024, activation='relu')(FC2) |
| FC4 = Dropout(0.1)(FC3) |
| FC5 = Dense(512, activation='relu')(FC4) |
| predictions = Dense(1,activity_regularizer=Regularizers.l1(1e-5))(FC5) # Create the model |
| interactionModel = Model(inputs=XInput, outputs=predictions) # Print the architecture of |
| the model in the output interactionModel.summary() # Compile the model. Choose loss |
| function, optimizer algorithm and metrics |
| interactionModel.compile(optimizer='sgd', loss='mse', metrics=['mse']) # Prepare the |
| training data to feed into the model XD = np.array(X_train) labels = np.array(y_train) |
| Remove samples with NaN labels from the training samples index = |
| np.where(~np.isnan(labels)) labels = labels[index[0],:] XD = XD[index[0],:] # Train the model |
| interactionModel.Fit(XD,labels, batch_size=256,epochs=100) # Predict on the training |
| samples y_pred = interactionModel.predict(np.array(XD)) # Print the evaluation measures |
| on the training samples print(mean_squared_error(labels, y_pred)) |
| print(r2_score(labels, y_pred)) |
