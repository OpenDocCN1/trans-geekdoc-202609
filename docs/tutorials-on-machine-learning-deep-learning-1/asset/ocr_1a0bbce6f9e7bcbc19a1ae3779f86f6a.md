# # Feature-Scaling after Data Split

```
# Feature-Scaling
from sklearn.preprocessing import StandardScaler
# y dependent variable, not needed to be scaled: categorical, and 0 and 1
st_x = StandardScaler()
x_train, x_test = st_x.fit_transform(x_train)
x_test = st_x.transform(x_test)
```

# ## Part 2 : Creating ANN model with "Dropout-Regularization"

```
# 1. Importing "keras" libraries and packages
from tensorflow import keras
import keras as tensorflow_backend
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Dropout #
```

```
# 2. Initialize the ANN
ann_classifier = Sequential()

# 3. Add the "Hidden-Layer" and "First Hidden-Layer"
```

# ## Part 3 : Predictions and Evaluating the model

```
# Predict
y_pred = ann_classifier.predict(x_test)

# Converting probabilities into "true/false" form, because 1 for leaving the Bank
y_pred = (y_pred > 0.5)

# Making the confusion matrix using the function "confusion_matrix"
# In class imbalance, false negatives are costly
from sklearn.metrics import confusion_matrix
print(confusion_matrix(y_test, y_pred)) # Actual, Predicted value
```

Use our ANN model to predict the customer with the following informations leave the bank:

Geography: France
Credit Score: 600
Gender: Male
Age: 40 years old
Tenure: 3 years
Balance: 60000
Number of Products: 2
Does this customer have a credit card? Yes
Is customer Active Member?: Yes
Estimated Salary: $50000

So should we goodbye to that customer ?