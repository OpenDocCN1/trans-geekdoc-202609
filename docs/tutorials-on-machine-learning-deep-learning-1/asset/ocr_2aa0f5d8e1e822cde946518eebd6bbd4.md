```
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
encoder_x = LabelEncoder()
X[:,:] = encoder_x.fit_transform(X[:,])
onehotencoder = OneHotEncoder(categorical_features=[0])
X = onehotencoder.fit_transform(X).toarray()
# Encoding the Dependent Variable
labelencoder_y = LabelEncoder()
y = labelencoder_y.fit_transform(y)
```

# FAQ: Normalize data before or after split of training and testing data?

I want to separate my data into train and test set, should I apply normalization over data before or after the split? Does it make any difference while building predictive model?

+   - First need to split the data into training and test set (validation set could be useful too).
- Don't forget that testing data points represent real-world data. Feature normalization (or data standardization) of the explanatory (or predictor) variables is a technique used to center and normalise the data by subtracting the mean and dividing by the variance. If you take the mean and variance of the whole dataset you'll introducing future information into the training explanatory variables (i.e. mean and variance).
- Therefore, you should perform feature normalisation over the training data. Then perform normalisation on testing instances as well, but this using the mean and variance of training explanatory variables. In this way, we can test and evaluate whether our model can generalize well to new, unseen data points.

For a more comprehensive read, you can read my article

Feature Scaling and Normalisation in a nutshell