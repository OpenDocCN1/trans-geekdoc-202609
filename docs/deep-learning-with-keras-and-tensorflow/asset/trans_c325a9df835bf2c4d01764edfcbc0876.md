

# LSTM 网络

A LSTM network is an artificial neural network that contains LSTM blocks instead of, or in addition to, regular network units. A LSTM block may be described as a "smart" network unit that can remember a value for an arbitrary length of time.

Unlike traditional RNNs, an Long short-term memory network is well-suited to learn from experience to classify, process and predict time series when there are very long time lags of unknown size between important events.

![](gru.png)

```
keras.layers.recurrent.LSTM(units, activation='tanh', recurrent_activation='hard_sigmoid', use_bias=True, 
                            kernel_initializer='glorot_uniform', recurrent_initializer='orthogonal', 
                            bias_initializer='zeros', unit_forget_bias=True, kernel_regularizer=None, 
                            recurrent_regularizer=None, bias_regularizer=None, activity_regularizer=None, 
                            kernel_constraint=None, recurrent_constraint=None, bias_constraint=None, 
                            dropout=0.0, recurrent_dropout=0.0)
```

## Arguments

*   `units`: Positive integer, dimensionality of the output space.

*   `activation`: Activation function to use If you pass None, no activation is applied (ie. "linear" activation: `a(x) = x`).

*   `recurrent_activation`: Activation function to use for the recurrent step.

*   `use_bias`: Boolean, whether the layer uses a bias vector.

*   `kernel_initializer`: Initializer for the `kernel` weights matrix, used for the linear transformation of the inputs.

*   `recurrent_initializer`: Initializer for the `recurrent_kernel` weights matrix, used for the linear transformation of the recurrent state.

*   `bias_initializer`: Initializer for the bias vector.

*   `unit_forget_bias`: Boolean. If True, add 1 to the bias of the forget gate at initialization. Setting it to true will also force `bias_initializer="zeros"`. This is recommended in [Jozefowicz et al.](http://www.jmlr.org/proceedings/papers/v37/jozefowicz15.pdf)

*   `kernel_regularizer`: Regularizer function applied to the `kernel` weights matrix.

*   `recurrent_regularizer`: Regularizer function applied to the `recurrent_kernel` weights matrix.

*   `bias_regularizer`: Regularizer function applied to the bias vector.

*   `activity_regularizer`: Regularizer function applied to the output of the layer (its "activation").

*   `kernel_constraint`: Constraint function applied to the `kernel` weights matrix.

*   `recurrent_constraint`: Constraint function applied to the `recurrent_kernel` weights matrix.

*   `bias_constraint`: Constraint function applied to the bias vector.

*   `dropout`: Float between 0 and 1. Fraction of the units to drop for the linear transformation of the inputs.

*   `recurrent_dropout`: Float between 0 and 1. Fraction of the units to drop for the linear transformation of the recurrent state.

# GRU

Gated recurrent units are a gating mechanism in recurrent neural networks.

Much similar to the LSTMs, they have fewer parameters than LSTM, as they lack an output gate.

![](gru.png)

```
keras.layers.recurrent.GRU(units, activation='tanh', recurrent_activation='hard_sigmoid', use_bias=True, 
                           kernel_initializer='glorot_uniform', recurrent_initializer='orthogonal', 
                           bias_initializer='zeros', kernel_regularizer=None, recurrent_regularizer=None, 
                           bias_regularizer=None, activity_regularizer=None, kernel_constraint=None, 
                           recurrent_constraint=None, bias_constraint=None, 
                           dropout=0.0, recurrent_dropout=0.0)
```

# Your Turn! - Hands on Rnn

```
print('Build model...')
model = Sequential()
model.add(Embedding(max_features, 128, input_length=maxlen))

# !!! Play with those! try and get better results!
#model.add(SimpleRNN(128))  
#model.add(GRU(128))  
#model.add(LSTM(128))  

model.add(Dropout(0.5))
model.add(Dense(1))
model.add(Activation('sigmoid'))

# try using different optimizers and different optimizer configs
model.compile(loss='binary_crossentropy', optimizer='adam')

print("Train...")
model.fit(X_train, y_train, batch_size=batch_size, 
          epochs=4, validation_data=(X_test, y_test))
score, acc = model.evaluate(X_test, y_test, batch_size=batch_size)
print('Test score:', score)
print('Test accuracy:', acc)
```

# Convolutional LSTM

> This section demonstrates the use of a `Convolutional LSTM network`.

> 

> This network is used to predict the next frame of an artificially generated movie which contains moving squares.

## Artificial Data Generation

Generate movies with `3` to `7` moving squares inside.

The squares are of shape $1 \\times 1$ or $2 \\times 2$ pixels, which move linearly over time.

For convenience we first create movies with bigger width and height (`80x80`) and at the end we select a $40 \times 40$ window.

```
# Artificial Data Generation
def generate_movies(n_samples=1200, n_frames=15):
    row = 80
    col = 80
    noisy_movies = np.zeros((n_samples, n_frames, row, col, 1), dtype=np.float)
    shifted_movies = np.zeros((n_samples, n_frames, row, col, 1),
                              dtype=np.float)

    for i in range(n_samples):
        # Add 3 to 7 moving squares
        n = np.random.randint(3, 8)

        for j in range(n):
            # Initial position
            xstart = np.random.randint(20, 60)
            ystart = np.random.randint(20, 60)
            # Direction of motion
            directionx = np.random.randint(0, 3) - 1
            directiony = np.random.randint(0, 3) - 1

            # Size of the square
            w = np.random.randint(2, 4)

            for t in range(n_frames):
                x_shift = xstart + directionx * t
                y_shift = ystart + directiony * t
                noisy_movies[i, t, x_shift - w: x_shift + w,
                             y_shift - w: y_shift + w, 0] += 1

                # Make it more robust by adding noise.
                # The idea is that if during inference,
                # the value of the pixel is not exactly one,
                # we need to train the network to be robust and still
                # consider it as a pixel belonging to a square.
                if np.random.randint(0, 2):
                    noise_f = (-1)**np.random.randint(0, 2)
                    noisy_movies[i, t,
                                 x_shift - w - 1: x_shift + w + 1,
                                 y_shift - w - 1: y_shift + w + 1,
                                 0] += noise_f * 0.1

                # Shift the ground truth by 1
                x_shift = xstart + directionx * (t + 1)
                y_shift = ystart + directiony * (t + 1)
                shifted_movies[i, t, x_shift - w: x_shift + w,
                               y_shift - w: y_shift + w, 0] += 1

    # Cut to a 40x40 window
    noisy_movies = noisy_movies[::, ::, 20:60, 20:60, ::]
    shifted_movies = shifted_movies[::, ::, 20:60, 20:60, ::]
    noisy_movies[noisy_movies >= 1] = 1
    shifted_movies[shifted_movies >= 1] = 1
    return noisy_movies, shifted_movies
```

## Model

```
from keras.models import Sequential
from keras.layers.convolutional import Conv3D
from keras.layers.convolutional_recurrent import ConvLSTM2D
from keras.layers.normalization import BatchNormalization
import numpy as np
from matplotlib import pyplot as plt

%matplotlib inline
```

```
Using TensorFlow backend.
```

We create a layer which take as input movies of shape `(n_frames, width, height, channels)` and returns a movie of identical shape.

