
However, we have no way to determine (in advance) what percentage of people will pass their written driver’s test, or the percentage of people who will pass their course. Datasets containing outcomes for these types of scenarios need to be trained, and logistic regression can be a suitable technique for doing so.

### Logistic Regression: Important Assumptions

Logistic regression requires the observations to be independent of each other. In addition, logistic regression requires little or no multi collinearity among the independent variables. Logistic regression handles numeric, categorical, and continuous variables, and also assumes linearity of independent variables and log odds, which is defined here:

odds = p/(1-p) and logit = log(odds) 

This analysis does not require the dependent and independent variables to be related linearly; however, another requirement is that independent variables are linearly related to the log odds.

Logistic regression is used to obtain odds ratio in the presence of more than one explanatory variable. The procedure is quite similar to multiple linear regression, with the exception that the response variable is binomial. The result is the impact of each variable on the odds ratio of the observed event of interest.

### Linearly Separable Data

Linearly separable data is data that can be separated by a line (in 2D), a plane (in 3D), or a hyperplane (in higher dimensions). Linearly nonseparable data is data (clusters) that cannot be separated by a line or a hyperplane. For example, the XOR function involves datapoints that cannot be separated by a line. If you create a truth table for an XOR function with two inputs, the points (0,0) and (1,1) belong to class 0, whereas the points (0,1) and (1,0) belong to class 1 (draw these points in a 2D plane to convince yourself). The solution involves transforming the data in a higher dimension so that it becomes linearly separable, which is the technique used in SVMs (discussed earlier in this chapter).

## Keras, Logistic Regression, and Iris Dataset

As this book goes to print, you need Python 3.7.x in order to install TensorFlow on your machine, and also to launch the code sample in this section.

``` 
[Listing 8.9](#ch08.xhtml#list8.9) displays the contents of tf2_keras_iris.py that defines a Keras-based model to perform logistic regression.
```

***LISTING 8.9: tf2_keras_iris.py***
``` 
import tensorflow as tf import matplotlib.pyplot as plt  from sklearn.datasets import load_iris  from sklearn.model_selection import train_test_split  from sklearn.preprocessing import OneHotEncoder, StandardScaler  iris = load_iris() X = iris['data'] y = iris['target']  #you can view the data and the labels: #print("iris data:",X) #print("iris target:",y)  # scale the X values so they are between 0 and 1 scaler = StandardScaler() X_scaled = scaler.fit_transform(X)  X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size = 0.2)  model = tf.keras.models.Sequential() model.add(tf.keras.layers.Dense(activation='relu', input_dim=4, units=4, kernel_initializer='uniform'))  model.add(tf.keras.layers.Dense(activation='relu', units=4,  kernel_initializer='uniform'))  model.add(tf.keras.layers.Dense(activation='sigmoid', units=1,  kernel_initializer='uniform'))  #model.add(tf.keras.layers.Dense(1, activation='softmax'))  model.compile(optimizer='adam', loss='mean_squared_error', metrics=['accuracy'])  model.fit(X_train, y_train, batch_size=10, epochs=100)  # Predicting values from the test set y_pred = model.predict(X_test)  # scatter plot of test values-vs-predictions fig, ax = plt.subplots() ax.scatter(y_test, y_pred) ax.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], 'r*--') ax.set_xlabel('Calculated') ax.set_ylabel('Predictions') plt.show() 
```

[Listing 8.9](#ch08.xhtml#list8.9) starts with an assortment of import statements, and then initializes the variable iris with the Iris dataset. The variable X contains the first three columns (and all the rows) of the Iris dataset, and the variable y contains the fourth column (and all the rows) of the Iris dataset.

The next portion of [Listing 8.9](#ch08.xhtml#list8.9) initializes the training set and the test set using an 80/20 data split. Next, the Keras-based model contains three Dense layers, where the first two specify the relu activation function and the third layer specifies the sigmoid activation function.

The next portion of [Listing 8.9](#ch08.xhtml#list8.9) compiles the model, trains the model, and then calculates the accuracy of the model via the test data. Launch the code in [Listing 8.9](#ch08.xhtml#list8.9) and you will see the following output:

```
Train on 120 samples Epoch 1/100 120/120 [==============================] - 0s 980us/sample - loss: 0.9819 - accuracy: 0.3167 Epoch 2/100 120/120 [==============================] - 0s 162us/sample - loss: 0.9789 - accuracy: 0.3083 Epoch 3/100 120/120 [==============================] - 0s 204us/sample - loss: 0.9758 - accuracy: 0.3083 Epoch 4/100 120/120 [==============================] - 0s 166us/sample - loss: 0.9728 - accuracy: 0.3083 Epoch 5/100 120/120 [==============================] - 0s 160us/sample - loss: 0.9700 - accuracy: 0.3083 // details omitted for brevity Epoch 96/100 120/120 [==============================] - 0s 128us/sample - loss: 0.3524 - accuracy: 0.6500 Epoch 97/100 120/120 [==============================] - 0s 184us/sample - loss: 0.3523 - accuracy: 0.6500 Epoch 98/100 120/120 [==============================] - 0s 128us/sample - loss: 0.3522 - accuracy: 0.6500 Epoch 99/100 120/120 [==============================] - 0s 187us/sample - loss: 0.3522 - accuracy: 0.6500 Epoch 100/100 120/120 [==============================] - 0s 167us/sample - loss: 0.3521 - accuracy: 0.6500 
```

[Figure 8.3](#ch08.xhtml#fig8.3) displays a scatter plot of points based on the test values and the predictions for those test values.

The accuracy is admittedly poor (abysmal?), and yet it’s quite possible that you will encounter this type of situation. Experiment with a different number of hidden layers and replace the final hidden layer with a Dense layer that specifies a softmax activation function—or some other activation function—to see if this change improves the accuracy.

![Figure 8.3 ¶ A Scatter Plot and a Best-Fitting Line.](images/fig8.3.jpg)

Figure 8.3 ¶ A Scatter Plot and a Best-Fitting Line.

## Sklearn and Linear Regression

This optional section shows you how to perform linear regression on a set of randomly generated points in the Euclidean plane, and also how to render those points with a best-fitting line. However, there is no NLP-related functionality, which means that you can ignore this section with no loss of continuity. Later chapters discuss machine learning and machine learning classifiers. This code sample is one of the only code samples in this book that pertains to linear regression in machine learning.

[Listing 8.10](#ch08.xhtml#list8.10) displays the contents of sklearn_lin_reg.py that illustrates how to generate some random numbers in the Euclidean plane and then use linear regression in order to find the best-fitting line for those points.

***LISTING 8.10: sklearn_lin_reg.py***
``` 
