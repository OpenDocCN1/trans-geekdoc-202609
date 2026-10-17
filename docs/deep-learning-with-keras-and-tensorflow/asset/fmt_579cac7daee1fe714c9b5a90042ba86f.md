
```
model.compile(optimizer='rmsprop', loss='categorical_crossentropy', metrics=['accuracy'])
model.fit([input_data_1, input_data_2], targets)  # we pass one data array per model input
```

## Try yourself

### Step 1: Get Data - MNIST

```
# let's load MNIST data as we did in the exercise on MNIST with FC Nets
```

```
# %load ../solutions/sol_821.py
```

### Step 2: Create the Multi-Input Network

```
## try yourself
```

```
## `evaluate` the model on test data
```

Keras supports different Merge strategies:

*   `add`: element-wise sum

*   `concatenate`: tensor concatenation. You can specify the concatenation axis via the argument `concat_axis`.

*   `multiply`: element-wise multiplication

*   `average`: tensor average

*   `maximum`: element-wise maximum of the inputs.

*   `dot`: dot product. You can specify which axes to reduce along via the argument `dot_axes`. You can also specify applying any normalisation. In that case, the output of the dot product is the cosine proximity between the two samples.

You can also pass a function as the `mode` argument, allowing for arbitrary transformations:

```
merged = Merge([left_branch, right_branch], mode=lambda x: x[0] - x[1])
```

* * *

# Even more interesting

Here's a good use case for the functional API: models with multiple inputs and outputs.

The functional API makes it easy to manipulate a large number of intertwined datastreams.

Let's consider the following model (from: [https://keras.io/getting-started/functional-api-guide/](https://keras.io/getting-started/functional-api-guide/) )

## Problem and Data

We seek to predict how many retweets and likes a news headline will receive on Twitter.

The main input to the model will be the headline itself, as a sequence of words, but to spice things up, our model will also have an auxiliary input, receiving extra data such as the time of day when the headline was posted, etc.

The model will also be supervised via two loss functions.

Using the main loss function earlier in a model is a good regularization mechanism for deep models.

![](c260610f.png)

```
from keras.layers import Input, Embedding, LSTM, Dense
from keras.models import Model

# Headline input: meant to receive sequences of 100 integers, between 1 and 10000.
# Note that we can name any layer by passing it a "name" argument.
main_input = Input(shape=(100,), dtype='int32', name='main_input')

# This embedding layer will encode the input sequence
# into a sequence of dense 512-dimensional vectors.
x = Embedding(output_dim=512, input_dim=10000, input_length=100)(main_input)

# A LSTM will transform the vector sequence into a single vector,
# containing information about the entire sequence
lstm_out = LSTM(32)(x)
```

```
Using TensorFlow backend.
```

Here we insert the auxiliary loss, allowing the LSTM and Embedding layer to be trained smoothly even though the main loss will be much higher in the model.

```
auxiliary_output = Dense(1, activation='sigmoid', name='aux_output')(lstm_out)
```

At this point, we feed into the model our auxiliary input data by concatenating it with the LSTM output:

```
from keras.layers import concatenate

auxiliary_input = Input(shape=(5,), name='aux_input')
x = concatenate([lstm_out, auxiliary_input])

# We stack a deep densely-connected network on top
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)

# And finally we add the main logistic regression layer
main_output = Dense(1, activation='sigmoid', name='main_output')(x)
```

### Model Definition

```
model = Model(inputs=[main_input, auxiliary_input], outputs=[main_output, auxiliary_output])
```

We compile the model and assign a weight of 0.2 to the auxiliary loss.

To specify different `loss_weights` or `loss` for each different output, you can use a list or a dictionary. Here we pass a single loss as the `loss` argument, so the same loss will be used on all outputs.

#### Note:

Since our inputs and outputs are named (we passed them a "name" argument), We can compile&fit the model via:

```
model.compile(optimizer='rmsprop',
              loss={'main_output': 'binary_crossentropy', 'aux_output': 'binary_crossentropy'},
              loss_weights={'main_output': 1., 'aux_output': 0.2})
```

```
# And trained it via:
model.fit({'main_input': headline_data, 'aux_input': additional_data},
          {'main_output': labels, 'aux_output': labels},
          epochs=50, batch_size=32)
```

# Conclusions

*   Keras is a powerful and battery-included framework for Deep Learning in Python

*   Keras is `simple` to use..

*   ...but it is `not` for simple things!

![](keras_rank.jpg)

![](keras_rank_details.jpg)

## Some References for ..

### Cutting Edge

*   Fractal Net Implementation with Keras: [https://github.com/snf/keras-fractalnet](https://github.com/snf/keras-fractalnet) -

*   Please check out: [https://github.com/fchollet/keras-resources](https://github.com/fchollet/keras-resources)

### Hyper-Cool

*   Hyperas: [https://github.com/maxpumperla/hyperas](https://github.com/maxpumperla/hyperas) 

    *   A web dashboard for Keras Models

### Super-Cool

*   Keras.js: [https://github.com/transcranial/keras-js](https://github.com/transcranial/keras-js) 

    *   Your Keras Model `inside your Browser`

    *   Showcase: [https://transcranial.github.io/keras-js/](https://transcranial.github.io/keras-js/)
