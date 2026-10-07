
## 9.5. Adding Layers: Step 4: ANN – Full Connection

The full connection step, which basically consists of making an ANN composed of fully-connected layers (instead of hidden layer).

- To convert our input image into this one-dimensional vector that contains some information of the spatial structure of some pixel patterns in the image.
- We use this input vector as the input layer of a classic ANN. A classic ANN can be a classifier for nonlinear problem like image classification.
- Since we already have our input layer as a hidden layer i.e a fully-connected layer.

Fully-connected layer: This is similar to previous chapter, but output-layer will have two nodes.

- We use `Dense()` method add `cnn_classifier.add()` to the fully-connected layer (hidden layer).
- Parameters:
  - units: is the number of nodes in the hidden layer.
  - Because, there was no rule of thumb to choose a number of nodes of the hidden layer.
  - We saw that a common practice is to choose a number of hidden nodes between the number of input nodes and the number of output nodes.
- But here we have too many input nodes, because we pooled feature-maps and each contains many cells, those are contained in flattened-one-single-vector which is the input layer of our fully-connected layer. Thus we end up with a lot of input nodes.

- So we are not gonna count all of them now, remember that we shouldn't take a too-small number.
- We are gonna choose 128.
- Remember this choice of results from experimentation: 128 is not so small and too big to make it compute-intensive.

By experimenting with this output parameter, we realize that a number around 100 is a good choice. We could have picked 100, but it is common practice to pick a power of 2 (i.e 2^7 = 128).

- ii. activation: The activation function, will be "relu" for the fully connected layers `activation="relu"`.

```python
cnn_classifier.add(Dense(units=128)
```

- Output-layer: The last layer that we need to add is the output layer. The value of `output_dim = 1` because out output will be cat/dog. We are expecting one node that is going to be the predicted probability of one, the cat or the dog.
- The activation function is the SIGMOID activation function because we have a binary output, cats or dog.
- If we have an outcome with more two categories, we would need to use the SOFTMAX activation function.

```python
cnn_classifier.add(Dense(units=1)
```

This full connection step consists of adding the fully-connected layer, that is the hidden layer, and then the output layer to get the final predictions.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_305_0.png)

```python
# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128)
```

## 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```python
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our classifier cnn_classifier.

- Parameters:
  - optimizer: adam specifies the SGD algorithm. It is the Adam algorithm.
- Loss: we choose the binary_crossentropy for two reasons:
  - First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification model like logistic regression.
  - The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
  - If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
  - metrics: To choose the performance metric. The most common performance metric is the accuracy metric.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_306_0.png)

## 9.5.11 Image Preprocessing

We just completed part: Building the CNN. We designed the architecture of our CNN.

- Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

- We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting.
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize these correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.

Right now, we are working with 10,000 images, 8,000 images in the training, and that is actually not much to get great performance on results. We either need more *images*, or we can use *data augmentation* trick.

Image augmentation creates many batches of *images*, and in each batch it will contain some random transformations on a random selection of our images, by *rotating*, *flipping*, *shifting*, or *shearing*, and eventually we will get more *diverse images* within those batches, and therefore a lot more material to train.

That's why we call *image augmentation* that because the amount of our images is augmented. Besides, because of the random transformations, our model never sees the same picture across batches.

In summary, *image augmentation* is a technique that allows us to *enrich* our data, without adding more *images* and therefore allows us to get *good performance* results with little or no overfitting, even with a small amount of images.

We're gonna use this TensorFloweras Documentation shortcut. In our browser, you can type *keras image preprocessing tensorflow*. Search for the link Documentation.

We're gonna look for the *imagedatenerator*: the code might change in latest version. Now we will use the following link:

```
https://tensorflow.org/api_python/tf/keras/preprocessing/ImageDataGenerator
```

The *Keras Library Documentation* is currently available on:

```
https://faroit.com/keras-docs/2.0/preprocessing/
```

Open tf.keras. You get a lot of *informations* about *Keras* and ready-to-use codes that you can take for your deep learning project.

```python
tf.preprocessing.image.ImageDataGenerator(
  featurewise_mode,
  sample_center=False,
  sample_std_normalization=False,
  zca_whitening=False,
  rescale=1,
  rotation_range=0,
  width_shift_range=0.0,
  height_shift_range=0.0,
  bright_range=0,
  shear_range=0,
  zoom_range=0,
  channel_shift_range=0.0,
  fill_mode='nearest',
  cval=0,
  horizontal_flip=False,
  vertical_flip=False,
  rescale=None,
  preprocessing_function=None,
  data_flow=None,
)

```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_305_0.png)

```python
# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128)
```

## 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```python
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our classifier cnn_classifier.

- Parameters:
  - optimizer: adam specifies the SGD algorithm. It is the Adam algorithm.
- Loss: we choose the binary_crossentropy for two reasons:
  - First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification model like logistic regression.
  - The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
  - If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
  - metrics: To choose the performance metric. The most common performance metric is the accuracy metric.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_306_0.png)

## 9.5.11 Image Preprocessing

We just completed part: Building the CNN. We designed the architecture of our CNN.

- Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

- We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting.
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize these correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.

Right now, we are working with 10,000 images, 8,000 images in the training, and that is actually not much to get great performance on results. We either need more *images*, or we can use *data augmentation* trick.

Image augmentation creates many batches of *images*, and in each batch it will contain some random transformations on a random selection of our images, by *rotating*, *flipping*, *shifting*, or *shearing*, and eventually we will get more *diverse images* within those batches, and therefore a lot more material to train.

That's why we call *image augmentation* that because the amount of our images is augmented. Besides, because of the random transformations, our model never sees the same picture across batches.

In summary, *image augmentation* is a technique that allows us to *enrich* our data, without adding more *images* and therefore allows us to get *good performance* results with little or no overfitting, even with a small amount of images.

We're gonna use this TensorFloweras Documentation shortcut. In our browser, you can type *keras image preprocessing tensorflow*. Search for the link Documentation.

We're gonna look for the *imagedatenerator*: the code might change in latest version. Now we will use the following link:

```
https://tensorflow.org/api_python/tf/keras/preprocessing/ImageDataGenerator
```

The *Keras Library Documentation* is currently available on:

```
https://faroit.com/keras-docs/2.0/preprocessing/
```

Open tf.keras. You get a lot of *informations* about *Keras* and ready-to-use codes that you can take for your deep learning project.

```python
tf.preprocessing.image.ImageDataGenerator(
  featurewise_mode,
  sample_center=False,
  sample_std_normalization=False,
  zca_whitening=False,
  rescale=1,
  rotation_range=0,
  width_shift_range=0.0,
  height_shift_range=0.0,
  bright_range=0,
  shear_range=0,
  zoom_range=0,
  channel_shift_range=0.0,
  fill_mode='nearest',
  cval=0,
  horizontal_flip=False,
  vertical_flip=False,
  rescale=None,
  preprocessing_function=None,
  data_flow=None,
)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_305_0.png)

```python
# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128)
```

## 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```python
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our classifier cnn_classifier.

- Parameters:
  - optimizer: adam specifies the SGD algorithm. It is the Adam algorithm.
- Loss: we choose the binary_crossentropy for two reasons:
  - First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification model like logistic regression.
  - The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
  - If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
  - metrics: To choose the performance metric. The most common performance metric is the accuracy metric.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_306_0.png)

## 9.5.11 Image Preprocessing

We just completed part: Building the CNN. We designed the architecture of our CNN.

- Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

- We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting.
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize these correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.

Right now, we are working with 10,000 images, 8,000 images in the training, and that is actually not much to get great performance on results. We either need more *images*, or we can use *data augmentation* trick.

Image augmentation creates many batches of *images*, and in each batch it will contain some random transformations on a random selection of our images, by *rotating*, *flipping*, *shifting*, or *shearing*, and eventually we will get more *diverse images* within those batches, and therefore a lot more material to train.

That's why we call *image augmentation* that because the amount of our images is augmented. Besides, because of the random transformations, our model never sees the same picture across batches.

In summary, *image augmentation* is a technique that allows us to *enrich* our data, without adding more *images* and therefore allows us to get *good performance* results with little or no overfitting, even with a small amount of images.

We're gonna use this TensorFloweras Documentation shortcut. In our browser, you can type *keras image preprocessing tensorflow*. Search for the link Documentation.

We're gonna look for the *imagedatenerator*: the code might change in latest version. Now we will use the following link:

```
https://tensorflow.org/api_python/tf/keras/preprocessing/ImageDataGenerator
```

The *Keras Library Documentation* is currently available on:

```
https://faroit.com/keras-docs/2.0/preprocessing/
```

Open tf.keras. You get a lot of *informations* about *Keras* and ready-to-use codes that you can take for your deep learning project.

```python
tf.preprocessing.image.ImageDataGenerator(
  featurewise_mode,
  sample_center=False,
  sample_std_normalization=False,
  zca_whitening=False,
  rescale=1,
  rotation_range=0,
  width_shift_range=0.0,
  height_shift_range=0.0,
  bright_range=0,
  shear_range=0,
  zoom_range=0,
  channel_shift_range=0.0,
  fill_mode='nearest',
  cval=0,
  horizontal_flip=False,
  vertical_flip=False,
  rescale=None,
  preprocessing_function=None,
  data_flow=None,
)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_305_0.png)

```python
# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128)
```

## 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```python
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our classifier cnn_classifier.

- Parameters:
  - optimizer: adam specifies the SGD algorithm. It is the Adam algorithm.
- Loss: we choose the binary_crossentropy for two reasons:
  - First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification model like logistic regression.
  - The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
  - If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
  - metrics: To choose the performance metric. The most common performance metric is the accuracy metric.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_306_0.png)

## 9.5.11 Image Preprocessing

We just completed part: Building the CNN. We designed the architecture of our CNN.

- Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

- We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting.
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize these correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.

Right now, we are working with 10,000 images, 8,000 images in the training, and that is actually not much to get great performance on results. We either need more *images*, or we can use *data augmentation* trick.

Image augmentation creates many batches of *images*, and in each batch it will contain some random transformations on a random selection of our images, by *rotating*, *flipping*, *shifting*, or *shearing*, and eventually we will get more *diverse images* within those batches, and therefore a lot more material to train.

That's why we call *image augmentation* that because the amount of our images is augmented. Besides, because of the random transformations, our model never sees the same picture across batches.

In summary, *image augmentation* is a technique that allows us to *enrich* our data, without adding more *images* and therefore allows us to get *good performance* results with little or no overfitting, even with a small amount of images.

We're gonna use this TensorFloweras Documentation shortcut. In our browser, you can type *keras image preprocessing tensorflow*. Search for the link Documentation.

We're gonna look for the *imagedatenerator*: the code might change in latest version. Now we will use the following link:

```
https://tensorflow.org/api_python/tf/keras/preprocessing/ImageDataGenerator
```

The *Keras Library Documentation* is currently available on:

```
https://faroit.com/keras-docs/2.0/preprocessing/
```

Open tf.keras. You get a lot of *informations* about *Keras* and ready-to-use codes that you can take for your deep learning project.

```python
tf.preprocessing.image.ImageDataGenerator(
  featurewise_mode,
  sample_center=False,
  sample_std_normalization=False,
  zca_whitening=False,
  rescale=1,
  rotation_range=0,
  width_shift_range=0.0,
  height_shift_range=0.0,
  bright_range=0,
  shear_range=0,
  zoom_range=0,
  channel_shift_range=0.0,
  fill_mode='nearest',
  cval=0,
  horizontal_flip=False,
  vertical_flip=False,
  rescale=None,
  preprocessing_function=None,
  data_flow=None,
)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_305_0.png)

```python
# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128)
```

## 9.5.10 Compilation: CNN model

We just need to compile the NN by choosing a SGD algorithm, a loss function and, eventually, a performance metric. It is as same as the classic-CNN in the previous chapter.

```python
# compile the NN
nn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

We apply compile() over our classifier cnn_classifier.

- Parameters:
  - optimizer: adam specifies the SGD algorithm. It is the Adam algorithm.
- Loss: we choose the binary_crossentropy for two reasons:
  - First of all, because this function performs the logarithmic loss, which is the loss function we use in general for classification problems using a classification model like logistic regression.
  - The second reason is that we have a binary outcome, cat or dog, and therefore, we need to choose the binary-crossentropy loss function.
  - If we have more than two classes, like cats, dogs, and birds, we would need to choose categorical-cross-entropy loss function.
  - metrics: To choose the performance metric. The most common performance metric is the accuracy metric.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_306_0.png)

## 9.5.11 Image Preprocessing

We just completed part: Building the CNN. We designed the architecture of our CNN.

- Now we're beginning part two: Image Preprocessing where we will fit our CNN to our images.
- We will do it in one step because we're gonna use a shortcut, the Keras Documentation.

- We will use Keras Documentation for a process called image augmentation, which basically consists of preprocessing your images to prevent overfitting.
- If we don't do this Image Augmentation, we will get a great accuracy on the training set, but a much lower accuracy on the test set.

Image Augmentation Purpose: We know that one of the situations that lead to overfitting is when we have few data to train our model. In this situation, our model finds some correlations in the few observations of the training set, but fail to generalize these correlations on some observations.

And when it comes to we actually need a lot of images to train and generalize some correlations, because in Computer Vision, our model doesn't need to find correlations between independent and dependent variables. It needs some patterns in the pixels, and to do this it requires a lot of images.

Right now, we are working with 10,000 images, 8,000 images in the training, and that is actually not much to get great performance on results. We either need more *images*, or we can use *data augmentation* trick.

Image augmentation creates many batches of *images*, and in each batch it will contain some random transformations on a random selection of our images, by *rotating*, *flipping*, *shifting*, or *shearing*, and eventually we will get more *diverse images* within those batches, and therefore a lot more material to train.

That's why we call *image augmentation* that because the amount of our images is augmented. Besides, because of the random transformations, our model never sees the same picture across batches.

In summary, *image augmentation* is a technique that allows us to *enrich* our data, without adding more *images* and therefore allows us to get *good performance* results with little or no overfitting, even with a small amount of images.

We're gonna use this TensorFloweras Documentation shortcut. In our browser, you can type *keras image preprocessing tensorflow*. Search for the link Documentation.

We're gonna look for the *imagedatenerator*: the code might change in latest version. Now we will use the following link:

```
https://tensorflow.org/api_python/tf/keras/preprocessing/ImageDataGenerator
```

The *Keras Library Documentation* is currently available on:

```
https://faroit.com/keras-docs/2.0/preprocessing/
```

Open tf.keras. You get a lot of *informations* about *Keras* and ready-to-use codes that you can take for your deep learning project.

```python
tf.preprocessing.image.ImageDataGenerator(
  featurewise_mode,
  sample_center=False,
  sample_std_normalization=False,
  zca_whitening=False,
  rescale=1,
  rotation_range=0,
  width_shift_range=0.0,
  height_shift_range=0.0,
  bright_range=0,
  shear_range=0,
  zoom_range=0,
  channel_shift_range=0.0,
  fill_mode='nearest',
  cval=0,
  horizontal_flip=False,
  vertical_flip=False,
  rescale=None,
  preprocessing_function=None,
  data_flow=None,
)
```
