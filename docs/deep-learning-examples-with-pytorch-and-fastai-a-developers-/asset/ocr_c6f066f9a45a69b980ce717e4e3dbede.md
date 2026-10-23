epoch train_loss valid_loss error_rate time 0 0.800914 0.891309 0.264547
01:01 1 0.403630 0.329750 0.096752 01:00

```
learn.save('resnet50-stage_2')
) stage_2.pth’)
```

Well, running the training loop for only two epochs on this large model is definitely not sufficient. If we want to use this model in a production environment we will have to do more epochs.

Yet for demonstration purposes the model returns acceptable results with a minimum number of lines of code.

# Chapter 2
Build an Image Classifier from Scratch

This chapter will guide you through the creation of a deep learning model for a classification task from scratch.
We will build our own deep learning model to recognize handwritten digits.
To train our classifier we will use the MNIST training dataset. This dataset consists of grayscaled images of handwritten digits.

You can find some more info on this dataset at wikipedia: https://en.wikipedia.org/wiki/MNIST_database. We will use the URLs-class from fastai for easy downloading of all the mnist data.

Now import the vision libraries from fastai and download the mnist dataset.
This time we will use the lowest level api from fastai to access our data.

```
from fastai.basics import *
from fastai.vision.all import *
from fastai.callback.all import *

path = untar_data(URLs.MNIST)
```