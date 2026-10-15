# 6.1.3 Scaling Output Variables

The output variable is the variable predicted by the network. You must ensure that the scale of your output variable matches the scale of the activation function (transfer function) on the output layer of your network.

If your output activation function has a range of [0,1], then obviously you must ensure that the target values lie within that range. But it is generally better to choose an output activation function suited to the distribution of the targets than to force your data to conform to the output activation function.

> — Should I normalize/standardize/rescale the data? Neural Nets FAQ.

If your problem is a regression problem, then the output will be a real value. This is best modeled with a linear activation function. If the distribution of the value is normal, then you can standardize the output variable. Otherwise, the output variable can be normalized.

# 6.2 Data Scaling scikit-learn API

There are two types of scaling of your data that you may want to consider: normalization and standardization. These can both be achieved using the scikit-learn library.

# 6.2.1 Data Normalization

Normalization is a rescaling of the data from the original range so that all values are within the range of 0 and 1. Normalization requires that you know or are able to accurately estimate the minimum and maximum observable values. You may be able to estimate these values from your available data. If an x value to be normalized is outside the bounds of the minimum and maximum values, the resulting value will not be in the range of 0 and 1. You could check for these observations prior to making predictions and either remove them from the dataset or limit them to the pre-defined maximum or minimum values. You can normalize your dataset using the scikit-learn object MinMaxScaler. Good practice usage with the MinMaxScaler and other scaling techniques is as follows:

+   - **Fit the scaler using available training data.** For normalization, this means the training data will be used to estimate the minimum and maximum observable values. This is done by calling the `fit()` function.
+   - **Apply the scale to training data.** This means you can use the normalized data to train your model. This is done by calling the `transform()` function.
+   - **Apply the scale to data going forward.** This means you can prepare new data in the future on which you want to make predictions.

The default scale for the MinMaxScaler is to rescale variables into the range [0,1], although a preferred scale can be specified via the feature_range argument and specify a tuple including the min and the max for all variables.