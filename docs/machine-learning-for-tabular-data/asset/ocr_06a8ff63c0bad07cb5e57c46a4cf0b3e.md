# PyTorch with TabNet

# Listing 8.10 Import statements for TabNet

![](bbox=[0.495, 0.095, 0.865, 0.21])

```
# pip install pytorch-tabnet
import torch
from pytorch_tabnet.tab_model import TabNetClassifier
```

> Imports the TabNetClassifier library. We will use this library to define the model.

Note that, unlike the fastai import statements, the statements for TabNet in listing 8.10 include an explicit statement to import the PyTorch library.
Unlike the fastai solution, which does not have any explicit code to define the pipeline and has unique code to define the dataset, the TabNet solution uses the same code as the Keras and XGBoost solutions up to including the definition of the pipelines. After the pipeline definitions, the TabNet solutions use similar code to XGBoost to convert the list of NumPy arrays that come from the pipeline into a NumPy array of lists, as shown in the following listing.

# Listing 8.11 Statements to generate NumPy arrays of lists

```
list_of_train = []
list_of_test = []
list_of_valid = []
for i in range(0,7):
    list_of_train.append(X_train[i].tolist())
    list_of_valid.append(X_valid[i].tolist())
    list_of_test.append(X_test[i].tolist())
X_train = np.array(list_of_train, T)
X_valid = np.array(list_of_valid, T)
X_test = np.array(list_of_test, T)
y_train = dtrain.target
y_valid = dval.target
y_test = test.target
```

> Defines lists of lists for the training, validation, and test datasets (one list for each)
Converts the list of lists into a NumPy array of lists
Converts the validation list of lists into a NumPy array of lists
ines variables for the training, validation, and test sets

The transformations shown in listing 8.11 are needed because the TabNet solution expects the input to be in the form of a NumPy array of lists. The TabNet solution includes code to define the model.

# Listing 8.12 Statements to define the TabNet model

```
tb_cls = TabNetClassifier(optimizer_fn=torch.optim.Adam, optimizer_params=dict(lr=1e-3),
```

> define a TabNetClassifier object as the model for the solution and specify an optim optimizer
Sets the learning rate for the model