
# All code at once (practiced)

```python
# Convolutional Neural Network : CNN

# Install following packages
# Install theano
# Install Tensorflow
# Install Keras

# Part 1 - Building the CNN
# Importing the Keras libraries and packages
from keras.models import Sequential # to initialize as sequence-of-layers
from keras.layers import Convolution2D  # Convolution step for images
from keras.layers import MaxPooling2D  # not "MaxPool2D". Pooling step for images
from keras.layers import Flatten  # Flattening step
from keras.layers import Dense # adds fully-connected layers to classic ANN

# initializing the CNN
nn_classifier = Sequential()

# step 1 : Convolution
nn_classifier.add(Convolution2D(32,
validation_data=test_set,
validation_steps = 62 # test_size/batch_size
))
```

```python
training_set,
steps_per_epoch=math.floor((training_set.samples)/training_set.batch_size),
epochs=20,
validation_data=test_set,
validation_steps=math.floor((test_set.samples)/test_set.batch_size)
)
```

```python
# history = model.fit_generator(train_gen,
    steps_per_epoch=train_gen.samples/batch_size, # len(train_gen)
    epochs=10,
    validation_data=validation_gen,
    validation_steps=(validation_gen.samples/batch_size),
    callbacks=[checkpoint],
    workers=4)
```

# Part 3 - Making new predictions
import numpy as np
from tensorflow.keras.preprocessing import image
from keras.preprocessing import image # for old versions

# we can also use 'utils' module
from keras import utils
test_image = utils.load_img('dataset/single_prediction/cat_or_dog_2.jpg',target_size=(64, 64))
test_image = utils.img_to_array(test_image)

test_image = image.load_img('dataset/single_prediction/cat_or_dog_2.jpg',target_size=(64, 64))
test_image = image.load_img('dataset/single_prediction/cat_or_dog_1.jpg',target_size=(64, 64))

test_image = np.expand_dims(test_image, axis=0)
result = cnn_classifier.predict(test_image, 64, 3)

```python
idx = training_set.class_indices
if result[0][0]==1:
    prediction = 'dog'
else:
    prediction = 'cat'
```

# python_prctc_cnn.py

We can use 'utils' module
from keras import utils
test_image = utils.load_img('dataset/single_prediction/cat_or_dog_2.jpg',target_size=(64, 64))
test_image = utils.img_to_array(test_image)

| Name | Type | Size | Value |
|---|---|---|---|
| idx | dict | | {'cat':0, 'dogs':1} |
| prediction | str | | cat |
| result | Array of float32 | (1, 1) | [[0.4102794]] |
| test_datagen | preprocessing.im | 1 | ImageDataGenerator object of keras.preprocessing.image module |
| test_image | Array of float32 | (1, 64, 64) | [[239, 239, 239]] |
| test_set | preprocessing.im | 1 | ImageDataGenerator object of keras.preprocessing.image module |

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_321_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_321_1.png)

cat_or_dog_1.jpg cat_or_dog_2.jpg

# Chapter 10
# Dimensionality Reduction

Principal Component Analysis (PCA),
Linear Discriminant Analysis (LDA),
Kernel PCA

## 10.1 Dimensionality Reduction

- **Dimensionality**: The number of input features, variables, or columns in a given dataset is known as dimensionality, and the process to reduce these features is called dimensionality reduction.
- Huge number of features in various cases makes the predictive modeling task more complicated. It is very difficult to visualize or make predictions for the training dataset with a high number of features.

**Dimensionality Reduction**: It is a way of converting the higher dimensions into lesser dimensions dataset ensuring that it provides similar information. These techniques are widely used in machine learning for obtaining a better fit predictive model while solving the classification and regression problems.

It is commonly used in the fields that deal with high-dimensional data, such as speech recognition, signal processing, bioinformatics. It can also be used for data visualization, cluster analysis, etc.

**Curse of Dimensionality**: If the dimensionality of the input dataset increases, any algorithm and model becomes more complex. As the number of features increases, the number of samples also increases proportionally, and the chance of OVERFITTING also increases.

**Benefits of Dimensionality Reduction**: Some benefits of applying dimensionality reduction techniques are:

- i. By reducing the dimensions of the features, the space required to store the dataset also gets reduced.
- ii. Less Computation time is required for reduced dimensions of features.
- iii. Reduced dimensions of the features help in visualizing the data quickly.
- iv. It removes the redundant features (if present) by taking care of multicolinearity.

**Disadvantages of dimensionality reduction**: Some disadvantages of applying dimensionality reduction are:

- i. Some data may be lost to dimensionality reduction.
- ii. In the PCA dimensionality reduction technique, sometimes the principal components required to consider are unknown.

## 10.2 Approaches of Dimension Reduction

There are two ways to apply the dimension reduction technique, which are: **Feature Selection** and **Feature Extraction**.

**Feature Selection**: Feature selection is the process of selecting the subset of the relevant features and leaving out the irrelevant features in a dataset to build a model of high accuracy. In other words, it is a way of selecting the Optimal Features for the input dataset.

[1] **Filters Methods**: In this method, the dataset is filtered, and a subset that contains only the relevant features is taken. Some common techniques of filters method are:

- a) Correlation
- b) ChiSquare
- c) ANOVA

[2] **Wrappers Methods**: In this method, we use a machine learning algorithm to evaluate subsets of features. Some common techniques of wrapper methods are:

- a) Forward Selection
- b) Backward Selection
- c) Elimination
- d) LASSO
- e) Elastic Net
- f) Ridge

[3] **Embedded Methods**: In this method, the feature selection is built into the model construction process. Some common techniques of embedded methods are:

- a) Lasso
- b) Ridge
- c) Decision Trees

Feature Extraction: Feature extraction is the process of transforming the space containing many dimensions into fewer dimensions. This approach is useful when we want to keep the information. Some common techniques are:

- Principal Component Analysis (PCA)
- Linear Discriminant Analysis (LDA)
- Kernel PCA
- Quadratic Discriminant Analysis

## 10.3 Principal Component Analysis (PCA)

PCA is considered to be one of the most popular unsupervised algorithms. PCA is a statistical process that converts the observations of correlated features into a set of uncorrelated features with the help of orthogonal transformation. These new features are called the Principal Components.

It is widely used for operations such as:

- Visualization
- Feature extraction
- Noise filtering

It can also be in:

- Stock market predictions
- Gene data analysis

**Goal of PCA**: The goal of PCA is to reduce the dimensions of a d-dimensional dataset by projecting it onto a k-dimensional subspace where k is less than d (k < d) and retaining the most of information. If there is a strong correlation found you could Reduce the Dimensionality.

**Visualization of PCA**: PCA will be really helpful if we see the following links:

- https://plotly.io/python-notebook/principal-component-analysis/
- https://seaborn.io/ev/principal-component-analysis/
