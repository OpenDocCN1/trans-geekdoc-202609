

# train the model, output generated text after each iteration

```
for iteration in range(1,10):
    print()
    print('-' * 50)
    print('Iteration', iteration)
    model.fit(x_male, y_male, batch_size=128, epochs=1)

    start_index = random.randint(0, len(male_post) - maxlen - 1)

    for diversity in [0.2, 0.4, 0.6, 0.8]:
        print()
        print('----- diversity:', diversity)

        generated = ''
        sentence = male_post[start_index : start_index + maxlen]
        generated += sentence
        print('----- Generating with seed: "' + sentence + '"')

        for iteration in range(400):
            try:
                x = np.zeros((1, maxlen, len(character_set_male)))
                for t, char in enumerate(sentence):
                    x[0, t, char_indices[char]] = 1.

                preds = model.predict(x, verbose=0)[0]
                next_index = sample(preds, diversity)
                next_char = indices_char[next_index]

                generated += next_char
                sentence = sentence[1:] + next_char
            except:
                continue

        print(sentence)
        print()
```

# 8.1 Custom Layer

# Custom Keras Layer

## Idea:

We build a custom activation layer called `Antirectifier`, which modifies the shape of the tensor that passes through it.

We need to specify two methods: `get_output_shape_for` and `call`.

Note that the same result can also be achieved via a `Lambda` layer (`keras.layer.core.Lambda`).

```
keras.layers.core.Lambda(function, output_shape=None, arguments=None)
```

Because our custom layer is written with primitives from the Keras backend (`K`), our code can run both on TensorFlow and Theano.

```
from keras.models import Sequential
from keras.layers import Dense, Dropout, Layer, Activation
from keras.datasets import mnist
from keras import backend as K
from keras.utils import np_utils
```

```
Using TensorFlow backend.
```

## AntiRectifier Layer

```
class Antirectifier(Layer):
    '''This is the combination of a sample-wise
    L2 normalization with the concatenation of the
    positive part of the input with the negative part
    of the input. The result is a tensor of samples that are
    twice as large as the input samples.

    It can be used in place of a ReLU.

    # Input shape
        2D tensor of shape (samples, n)

    # Output shape
        2D tensor of shape (samples, 2*n)

    # Theoretical justification
        When applying ReLU, assuming that the distribution
        of the previous output is approximately centered around 0.,
        you are discarding half of your input. This is inefficient.

        Antirectifier allows to return all-positive outputs like ReLU,
        without discarding any data.

        Tests on MNIST show that Antirectifier allows to train networks
        with twice less parameters yet with comparable
        classification accuracy as an equivalent ReLU-based network.
    '''

    def compute_output_shape(self, input_shape):
        shape = list(input_shape)
        assert len(shape) == 2  # only valid for 2D tensors
        shape[-1] *= 2
        return tuple(shape)

    def call(self, inputs):
        inputs -= K.mean(inputs, axis=1, keepdims=True)
        inputs = K.l2_normalize(inputs, axis=1)
        pos = K.relu(inputs)
        neg = K.relu(-inputs)
        return K.concatenate([pos, neg], axis=1)
```

### Parametrs and Settings

```
# global parameters
batch_size = 128
nb_classes = 10
nb_epoch = 10
```

## Data Preparation

```
# the data, shuffled and split between train and test sets
(X_train, y_train), (X_test, y_test) = mnist.load_data()

X_train = X_train.reshape(60000, 784)
X_test = X_test.reshape(10000, 784)
X_train = X_train.astype('float32')
X_test = X_test.astype('float32')
X_train /= 255
X_test /= 255
print(X_train.shape[0], 'train samples')
print(X_test.shape[0], 'test samples')

# convert class vectors to binary class matrices
Y_train = np_utils.to_categorical(y_train, nb_classes)
Y_test = np_utils.to_categorical(y_test, nb_classes)
```

```
60000 train samples
10000 test samples
```

## Model with Custom Layer

```
# build the model
model = Sequential()
model.add(Dense(256, input_shape=(784,)))
model.add(Antirectifier())
model.add(Dropout(0.1))
model.add(Dense(256))
model.add(Antirectifier())
model.add(Dropout(0.1))
model.add(Dense(10))
model.add(Activation('softmax'))

# compile the model
model.compile(loss='categorical_crossentropy',
              optimizer='rmsprop',
              metrics=['accuracy'])

# train the model
model.fit(X_train, Y_train,
          batch_size=batch_size, epochs=nb_epoch,
          verbose=1, validation_data=(X_test, Y_test))
```

```
Train on 60000 samples, validate on 10000 samples
Epoch 1/10
60000/60000 [==============================] - 4s - loss: 0.6029 - acc: 0.9154 - val_loss: 0.1556 - val_acc: 0.9612
Epoch 2/10
60000/60000 [==============================] - 3s - loss: 0.1252 - acc: 0.9662 - val_loss: 0.0990 - val_acc: 0.9714
Epoch 3/10
60000/60000 [==============================] - 3s - loss: 0.0813 - acc: 0.9766 - val_loss: 0.0796 - val_acc: 0.9758
Epoch 4/10
60000/60000 [==============================] - 3s - loss: 0.0634 - acc: 0.9810 - val_loss: 0.0783 - val_acc: 0.9747
Epoch 5/10
60000/60000 [==============================] - 3s - loss: 0.0513 - acc: 0.9847 - val_loss: 0.0685 - val_acc: 0.9792
Epoch 6/10
60000/60000 [==============================] - 3s - loss: 0.0428 - acc: 0.9867 - val_loss: 0.0669 - val_acc: 0.9792
Epoch 7/10
60000/60000 [==============================] - 3s - loss: 0.0381 - acc: 0.9885 - val_loss: 0.0668 - val_acc: 0.9799
Epoch 8/10
60000/60000 [==============================] - 3s - loss: 0.0314 - acc: 0.9903 - val_loss: 0.0672 - val_acc: 0.9790
Epoch 9/10
60000/60000 [==============================] - 3s - loss: 0.0276 - acc: 0.9913 - val_loss: 0.0616 - val_acc: 0.9817
Epoch 10/10
60000/60000 [==============================] - 3s - loss: 0.0238 - acc: 0.9926 - val_loss: 0.0608 - val_acc: 0.9825

<keras.callbacks.History at 0x7f2c140fbac8>
```

# Excercise

Compare with an equivalent network that is `2x bigger` (in terms of Dense layers) + `ReLU`)

```
## your code here
```

# 8.2 Multi-Modal Networks

# Keras Functional API

## Recall: All models (layers) are callables

```
from keras.layers import Input, Dense
from keras.models import Model

# this returns a tensor
inputs = Input(shape=(784,))

# a layer instance is callable on a tensor, and returns a tensor
x = Dense(64, activation='relu')(inputs)
x = Dense(64, activation='relu')(x)
predictions = Dense(10, activation='softmax')(x)

# this creates a model that includes
# the Input layer and three Dense layers
model = Model(inputs=inputs, outputs=predictions)
model.compile(optimizer='rmsprop',
              loss='categorical_crossentropy',
              metrics=['accuracy'])
model.fit(data, labels)  # starts training
```

# Multi-Input Networks

## Keras Merge Layer

Here's a good use case for the functional API: models with multiple inputs and outputs.

The functional API makes it easy to manipulate a large number of intertwined datastreams.

Let's consider the following model.

```
from keras.layers import Dense, Input
from keras.models import Model
from keras.layers.merge import concatenate

left_input = Input(shape=(784, ), name='left_input')
left_branch = Dense(32, input_dim=784, name='left_branch')(left_input)

right_input = Input(shape=(784,), name='right_input')
right_branch = Dense(32, input_dim=784, name='right_branch')(right_input)

x = concatenate([left_branch, right_branch])
predictions = Dense(10, activation='softmax', name='main_output')(x)

model = Model(inputs=[left_input, right_input], outputs=predictions)
```

Resulting Model will look like the following network:

![](multi_input_model.png)

Such a two-branch model can then be trained via e.g.:

