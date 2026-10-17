
# Your Turn!

## Hands On - Keras Fully Connected

Take couple of minutes and try to play with the number of layers and the number of parameters in the layers to get the best results.

```
model = Sequential()
model.add(Dense(100, input_shape=(dims,)))

# ...
# ...
# Play with it! add as much layers as you want! try and get better results.

model.add(Dense(nb_classes))
model.add(Activation('softmax'))
model.compile(optimizer='sgd', loss='categorical_crossentropy')

model.summary()
```

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_4 (Dense)              (None, 100)               9400      
_________________________________________________________________
dense_5 (Dense)              (None, 9)                 909       
_________________________________________________________________
activation_3 (Activation)    (None, 9)                 0         
=================================================================
Total params: 10,309
Trainable params: 10,309
Non-trainable params: 0
_________________________________________________________________
```

```
model.fit(X_train, Y_train, validation_data = (X_val, Y_val), epochs=20, 
          batch_size=128, verbose=True)
```

```
Train on 52596 samples, validate on 9282 samples
Epoch 1/20
52596/52596 [==============================] - 1s - loss: 1.2107 - val_loss: 0.8821
Epoch 2/20
52596/52596 [==============================] - 1s - loss: 0.8204 - val_loss: 0.7798
Epoch 3/20
52596/52596 [==============================] - 1s - loss: 0.7577 - val_loss: 0.7393
Epoch 4/20
52596/52596 [==============================] - 0s - loss: 0.7280 - val_loss: 0.7176
Epoch 5/20
52596/52596 [==============================] - 1s - loss: 0.7097 - val_loss: 0.7028
Epoch 6/20
52596/52596 [==============================] - 1s - loss: 0.6973 - val_loss: 0.6929
Epoch 7/20
52596/52596 [==============================] - 1s - loss: 0.6883 - val_loss: 0.6858
Epoch 8/20
52596/52596 [==============================] - 1s - loss: 0.6813 - val_loss: 0.6804
Epoch 9/20
52596/52596 [==============================] - 1s - loss: 0.6757 - val_loss: 0.6756
Epoch 10/20
52596/52596 [==============================] - 1s - loss: 0.6711 - val_loss: 0.6722
Epoch 11/20
52596/52596 [==============================] - 1s - loss: 0.6672 - val_loss: 0.6692
Epoch 12/20
52596/52596 [==============================] - 0s - loss: 0.6641 - val_loss: 0.6667
Epoch 13/20
52596/52596 [==============================] - 0s - loss: 0.6613 - val_loss: 0.6636
Epoch 14/20
52596/52596 [==============================] - 0s - loss: 0.6589 - val_loss: 0.6620
Epoch 15/20
52596/52596 [==============================] - 0s - loss: 0.6568 - val_loss: 0.6606
Epoch 16/20
52596/52596 [==============================] - 0s - loss: 0.6546 - val_loss: 0.6589
Epoch 17/20
52596/52596 [==============================] - 0s - loss: 0.6531 - val_loss: 0.6577
Epoch 18/20
52596/52596 [==============================] - 0s - loss: 0.6515 - val_loss: 0.6568
Epoch 19/20
52596/52596 [==============================] - 0s - loss: 0.6501 - val_loss: 0.6546
Epoch 20/20
52596/52596 [==============================] - 0s - loss: 0.6489 - val_loss: 0.6539



<keras.callbacks.History at 0x1285bae80>
```

Building a question answering system, an image classification model, a Neural Turing Machine, a word2vec embedder or any other model is just as fast. The ideas behind deep learning are simple, so why should their implementation be painful?

#### Theoretical Motivations for depth

> Much has been studied about the depth of neural nets. Is has been proven mathematically\[1\] and empirically that convolutional neural network benifit from depth!

\[1\] - On the Expressive Power of Deep Learning: A Tensor Analysis - Cohen, et al 2015

#### Theoretical Motivations for depth

One much quoted theorem about neural network states that:

> Universal approximation theorem states\[1\] that a feed-forward network with a single hidden layer containing a finite number of neurons (i.e., a multilayer perceptron), can approximate continuous functions on compact subsets of $\\mathbb{R}^n$, under mild assumptions on the activation function. The theorem thus states that simple neural networks can represent a wide variety of interesting functions when given appropriate parameters; however, it does not touch upon the algorithmic learnability of those parameters.

\[1\] - Approximation Capabilities of Multilayer Feedforward Networks - Kurt Hornik 1991

## Addendum

[2.3.1 Keras Backend](2.3.1%20%20Keras%20Backend.ipynb)

# 2.3.1 Keras Backend

# Keras Backend

In this notebook we will be using the [Keras backend module](http://keras.io/backend/), which provides an abstraction over both Theano and Tensorflow.

Let's try to re-implement the Logistic Regression Model using the `keras.backend` APIs.

The following code will look like very similar to what we would write in Theano or Tensorflow (with the *only difference* that it may run on both the two backends).

```
import keras.backend as K
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
```

```
Using TensorFlow backend.
```

```
from kaggle_data import load_data, preprocess_data, preprocess_labels
```

```
X_train, labels = load_data('../data/kaggle_ottogroup/train.csv', train=True)
X_train, scaler = preprocess_data(X_train)
Y_train, encoder = preprocess_labels(labels)

X_test, ids = load_data('../data/kaggle_ottogroup/test.csv', train=False)

X_test, _ = preprocess_data(X_test, scaler)

nb_classes = Y_train.shape[1]
print(nb_classes, 'classes')

dims = X_train.shape[1]
print(dims, 'dims')
```

```
9 classes
93 dims
```

```
feats = dims
training_steps = 25
```
