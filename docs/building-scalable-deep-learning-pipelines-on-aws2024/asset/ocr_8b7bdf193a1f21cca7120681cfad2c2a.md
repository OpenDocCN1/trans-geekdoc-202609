functions, followed by an output layer. This model serves as our starting point for implementing regularization techniques (dropout, early stopping, L1 and L2 regularization) and fine-tuning enhancements.

The script starts with importing necessary libraries:

+   - **logging**: For logging information and errors
- **numpy**: For numerical operations
- **tensorflow**: For building and training the neural network
- **pyspark.sql**: For handling Spark DataFrames
- **pyspark.ml.feature**: For feature transformation
- **sklearn.metrics**: For calculating the R2 score
- **matplotlib.pyplot**: For plotting the training loss

```
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler,
StandardScaler
[In]: from sklearn.metrics import r2_score
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense
[In]: import matplotlib.pyplot as plt
```

Following this, we define the TLSARegressor class, which encapsulates the entire process of data preprocessing, model training, and evaluation. The class starts with an init method, which initializes a TLSARegressor object. This method sets up a logger, initializes a Spark session, and defines input_shape and model attributes for later use: