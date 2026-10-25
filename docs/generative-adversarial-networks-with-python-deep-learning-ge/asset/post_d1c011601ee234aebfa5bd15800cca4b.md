

```python
# example of negative label smoothing
from numpy import zeros
from numpy.random import random

# example of smoothing class=0 to [0.0, 0.3]
def smooth_negative_labels(y):
    return y + random(y.shape) * 0.3

# generate 'fake' class labels (0)
n_samples = 1000
y = zeros((n_samples, 1))
# smooth labels
y = smooth_negative_labels(y)
# summarize smooth labels
print(y.shape, y.min(), y.max())
```

Listing 5.18: Example demonstrating negative label smoothing.

```
(1000, 1) 0.00019305316963429408 0.299785314665858
```

Listing 5.19: Example output from demonstrating negative label smoothing.

### 5.5.4 Use Noisy Labels

The labels used when training the discriminator model are always correct. This means that fake images are always labeled with class 0 and real images are always labeled with class 1. It is recommended to introduce some errors to these labels where some fake images are marked as real, and some real images are marked as fake. If you are using separate batches to update the discriminator for real and fake images, this may mean randomly adding some fake images to the batch of real images, or randomly adding some real images to the batch of fake images. If you are updating the discriminator with a combined batch of real and fake images, then this may involve randomly flipping the labels on some images. The example below demonstrates this by creating 1,000 samples of real (class = 1) labels and flipping them with a 5% probability, then doing the same with 1,000 samples of fake (class = 0) labels.

```python
# example of noisy labels
from numpy import ones
from numpy import zeros
from numpy.random import choice

# randomly flip some labels
def noisy_labels(y, p_flip):
    # determine the number of labels to flip
    n_select = int(p_flip * y.shape[0])
    # choose labels to flip
    flip_ix = choice([i for i in range(y.shape[0])], size=n_select)
    # invert the labels in place
    y[flip_ix] = 1 - y[flip_ix]
    return y

# generate 'real' class labels (1)
n_samples = 1000
y = ones((n_samples, 1))
# flip labels with 5% probability
y = noisy_labels(y, 0.05)
# summarize labels
print(y.sum())

# generate 'fake' class labels (0)
y = zeros((n_samples, 1))
# flip labels with 5% probability
y = noisy_labels(y, 0.05)
# summarize labels
print(y.sum())
```

Listing 5.20: Example demonstrating noisy labels.

Try running the example a few times. The results show that approximately 50 of the 1s are flipped to 0s for the positive labels (e.g. 5% of 1,000) and approximately 50 0s are flipped to 1s for the negative labels.

```
951.0
49.0
```

Listing 5.21: Example output from demonstrating noisy labels.

### 5.6 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 5.6.1 Papers

- Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks, 2015.
  https://arxiv.org/abs/1511.06434

- Tutorial: Generative Adversarial Networks, NIPS, 2016.
  https://arxiv.org/abs/1701.00160

- Improved Techniques for Training GANs, 2016.
  https://arxiv.org/abs/1606.03498

### 5.6.2 API

- Keras API.
  https://keras.io/

- NumPy Random sampling (numpy.random) API.
  https://docs.scipy.org/doc/numpy/reference/routines.random.html

- NumPy Array manipulation routines.
  https://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html

### 5.6.3 Articles

- ganhacks: How to Train a GAN? Tips and tricks to make GANs work.
  https://github.com/soumith/ganhacks

- Ian Goodfellow, Introduction to GANs, NIPS 2016.
  https://www.youtube.com/watch?v=9JpdAg6uMXs

- Soumith Chintala, How to train a GAN, NIPS 2016 Workshop on Adversarial Training.
  https://www.youtube.com/watch?v=X1mUN6dD8uE

- Deconvolution and Checkerboard Artifacts, 2016.
  https://distill.pub/2016/deconv-checkerboard/

### 5.7 Summary

In this tutorial, you discovered how to implement a suite of best practices or GAN hacks that you can copy-and-paste directly into your GAN project. Specifically, you learned:

- The simultaneous training of generator and discriminator models in GANs is inherently unstable.
- How to implement seven best practices for the deep convolutional GAN model architecture from scratch.
- How to implement four additional best practices from Soumith Chintala's GAN Hacks presentation and list.

### 5.7.1 Next

This was the final tutorial in this part. In the next part you will begin developing your own GAN models from scratch.

## Part II

## GAN Basics

## Overview

In this part you will discover how to implement, train and use GAN models. After reading the chapters in this part, you will know:

- How to develop a GAN model for a one-dimensional target function (Chapter 6).
- How to develop and use a GAN for generating black and white handwritten digits (Chapter 7).
- How to develop and use a GAN for generating small color photographs of objects (Chapter 8).
- How to explore the latent space of a trained GAN using interpolation and vector arithmetic (Chapter 9).
- How to identify different failure modes when training GAN models (Chapter 10).

## Chapter 6

### How to Develop a 1D GAN from Scratch

Generative Adversarial Networks, or GANs for short, are a deep learning architecture for training powerful generator models. A generator model is capable of generating new artificial samples that plausibly could have come from an existing distribution of samples. GANs are comprised of both generator and discriminator models. The generator is responsible for generating new samples from the domain, and the discriminator is responsible for classifying whether samples are real or fake (generated). Importantly, the performance of the discriminator model is used to update both the model weights of the discriminator itself and the generator model. This means that the generator never actually sees examples from the domain and is adapted based on how well the discriminator performs.

This is a complex type of model both to understand and to train. One approach to better understand the nature of GAN models and how they can be trained is to develop a model from scratch for a very simple task. A simple task that provides a good context for developing a simple GAN from scratch is a one-dimensional function. This is because both real and generated samples can be plotted and visually inspected to get an idea of what has been learned. A simple function also does not require sophisticated neural network models, meaning the specific generator and discriminator models used on the architecture can be easily understood. In this tutorial, we will select a simple one-dimensional function and use it as the basis for developing and evaluating a generative adversarial network from scratch using the Keras deep learning library. After completing this tutorial, you will know:

- The benefit of developing a generative adversarial network from scratch for a simple one-dimensional function.
- How to develop separate discriminator and generator models, as well as a composite model for training the generator via the discriminator's predictive behavior.
- How to subjectively evaluate generated samples in the context of real examples from the problem domain.

Let's get started.

### 6.1 Tutorial Overview

This tutorial is divided into six parts; they are:

- 1. Select a One-Dimensional Function
- 2. Define a Discriminator Model
- 3. Define a Generator Model
- 4. Training the Generator Model
- 5. Evaluating the Performance of the GAN
- 6. Complete Example of Training the GAN

### 6.2 Select a One-Dimensional Function

The first step is to select a one-dimensional function to model. Something of the form:

$y = f(x)$ (6.1)

Where $x$ are input values and $y$ are the output values of the function. Specifically, we want a function that we can easily understand and plot. This will help in both setting an expectation of what the model should be generating and in using a visual inspection of generated examples to get an idea of their quality. We will use a simple function of $x^2$; that is, the function will return the square of the input. You might remember this function from high school algebra as the u-shaped function. We can define the function in Python as follows:

```python
# simple function
def calculate(x):
    return x * x
```

Listing 6.1: Example of defining a target function.

We can define the input domain as real values between -0.5 and 0.5 and calculate the output value for each input value in this linear range, then plot the results to get an idea of how inputs relate to outputs. The complete example is listed below.

```python
# demonstrate simple x^2 function
from matplotlib import pyplot

# simple function
def calculate(x):
    return x * x

# define inputs
inputs = [-0.5, -0.4, -0.3, -0.2, -0.1, 0, 0.1, 0.2, 0.3, 0.4, 0.5]
# calculate outputs
outputs = [calculate(x) for x in inputs]
# plot the result
pyplot.plot(inputs, outputs)
pyplot.show()
```

Listing 6.2: Example of plotting the domain for the target function.

