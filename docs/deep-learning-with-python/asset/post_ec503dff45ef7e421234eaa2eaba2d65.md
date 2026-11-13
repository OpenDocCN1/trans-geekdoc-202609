
are all we need. This is, in turn, a byproduct of the rise of the consumer internet and Moore’s law applied to storage media.

- The availability of fast, highly parallel computation hardware at a low price—Especially the GPUs produced by NVIDIA—first gaming GPUs and then chips designed from the ground up for deep learning. Early on, NVIDIA CEO Jensen Huang took note of the deep learning boom and decided to bet the company’s future on it, which paid off in a big way.

- A complex stack of software layers that makes this computational power available to humans—The CUDA language, frameworks like TensorFlow that do automatic differentiation, and Keras, which makes deep learning accessible to most people.

In the future, deep learning will not be used only by specialists—researchers, graduate students, and engineers with an academic profile—it will be a tool in the toolbox of every developer, much like web technology today. Everyone needs to build intelligent apps: just as every business today needs a website, every product will need to intelligently make sense of user-generated data. Bringing about this future will require us to build tools that make deep learning radically easy to use and accessible to anyone with basic coding abilities. Keras has been the first major step in that direction.

## 14.1.5 The universal machine learning workflow

Having access to an extremely powerful tool for creating models that map any input space to any target space is great, but the difficult part of the machine learning workflow is often everything that comes before designing and training such models (and, for production models, what comes after, as well). Understanding the problem domain so as to be able to determine what to attempt to predict, given what data, and how to measure success, is a prerequisite for any successful application of machine learning, and it isn’t something that advanced tools like Keras and TensorFlow can help you with. As a reminder, here’s a quick summary of the typical machine learning workflow as described in chapter 6:

- 1 Define the problem: What data is available, and what are you trying to predict? Will you need to collect more data or hire people to manually label a dataset?

- 2 Identify a way to reliably measure success on your goal. For simple tasks this may be prediction accuracy, but in many cases it will require sophisticated, domain-specific metrics.

- 3 Prepare the validation process that you’ll use to evaluate your models. In particular, you should define a training set, a validation set, and a test set. The validation- and test-set labels shouldn’t leak into the training data: for instance, with temporal prediction, the validation and test data should be posterior to the training data.

- 4 Vectorize the data by turning it into vectors and preprocessing it in a way that makes it more easily approachable by a neural network (normalization and so on).

- 5 Develop a first model that beats a trivial common-sense baseline, thus demonstrating that machine learning can work on your problem. This may not always be the case!

- 6 Gradually refine your model architecture by tuning hyperparameters and adding regularization. Make changes based on performance on the validation data only, not the test data or the training data. Remember that you should get your model to overfit (thus identifying a model capacity level that's greater than you need) and only then begin to add regularization or downsize your model. Beware of validation-set overfitting when tuning hyperparameters—the fact that your hyperparameters may end up being overspecialized to the validation set. Avoiding this is the purpose of having a separate test set.

- 7 Deploy your final model in production—as a web API, as part of a JavaScript or C++ application, on an embedded device, etc. Keep monitoring its performance on real-world data, and use your findings to refine the next iteration of the model!

## 14.1.6 Key network architectures

The four families of network architectures that you should be familiar with are densely connected networks, convolutional networks, recurrent networks, and Transformers. Each type of model is meant for a specific input modality. A network architecture encodes assumptions about the structure of the data: a hypothesis space within which the search for a good model will proceed. Whether a given architecture will work on a given problem depends entirely on the match between the structure of the data and the assumptions of the network architecture.

These different network types can easily be combined to achieve larger multimodal models, much as you combine LEGO bricks. In a way, deep learning layers are LEGO bricks for information processing. Here’s a quick overview of the mapping between input modalities and appropriate network architectures:

- Vector data—Densely connected models (Dense layers).
- Image data—2D convnets.
- Sequence data—RNNs for timeseries, or Transformers for discrete sequences (such as sequences of words). 1D convnets can also be used for translation-invariant, continuous sequence data, such as birdsong waveforms.
- Video data—Either 3D convnets (if you need to capture motion effects), or a combination of a frame-level 2D convnet for feature extraction followed by a sequence-processing model.
- Volumetric data—3D convnets.

Now, let's quickly review the specificities of each network architecture.

### Densely connected networks

A densely connected network is a stack of Dense layers meant to process vector data (where each sample is a vector of numerical or categorical attributes). Such networks assume no specific structure in the input features: they're called _densely connected_ because the units of a Dense layer are connected to every other unit. The layer attempts to map relationships between any two input features; this is unlike a 2D convolution layer, for instance, which only looks at _local_ relationships.

Densely connected networks are most commonly used for categorical data (for example, where the input features are lists of attributes), such as the Boston Housing Price dataset used in chapter 4. They're also used as the final classification or regression stage of most networks. For instance, the convnets covered in chapter 8 typically end with one or two Dense layers, and so do the recurrent networks in chapter 10.

Remember, to perform _binary classification_, end your stack of layers with a Dense layer with a single unit and a sigmoid activation, and use `binary_crossentropy` as the loss. Your targets should be either 0 or 1:

```
from tensorflow import keras
from tensorflow.keras import layers
inputs = keras.Input(shape=(num_input_features,))
x = layers.Dense(32, activation="relu")(inputs)
x = layers.Dense(32, activation="relu")(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="binary_crossentropy")
```

To perform _single-label categorical classification_ (where each sample has exactly one class, no more), end your stack of layers with a Dense layer with a number of units equal to the number of classes, and a softmax activation. If your targets are one-hot encoded, use `categorical_crossentropy` as the loss; if they're integers, use `sparse_categorical_crossentropy`:

```
inputs = keras.Input(shape=(num_input_features,))
x = layers.Dense(32, activation="relu")(inputs)
x = layers.Dense(32, activation="relu")(x)
outputs = layers.Dense(num_classes, activation="softmax")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="categorical_crossentropy")
```

To perform _multilabel categorical classification_ (where each sample can have several classes), end your stack of layers with a Dense layer with a number of units equal to the number of classes, and a sigmoid activation, and use `binary_crossentropy` as the loss. Your targets should be multi-hot encoded:

```
inputs = keras.Input(shape=(num_input_features,))
x = layers.Dense(32, activation="relu")(inputs)
x = layers.Dense(32, activation="relu")(x)
outputs = layers.Dense(num_classes, activation="sigmoid")(x)
model = keras.Model(inputs, outputs)
model.compile(optimizer="rmsprop", loss="binary_crossentropy")
```
