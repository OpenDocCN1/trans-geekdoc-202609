# Installing Deep Learning Libraries

Now we will install Python libraries used for deep learning, including TensorFlow and Keras.

# Installing TensorFlow

Open Anaconda Prompt and type the following commands.
To install the GPU version of TensorFlow:

```
C:\> pip install tensorflow-gpu
If your machine or system is the only CPU supported then use the below command for installing
CPU-only version of TensorFlow:
C:\> pip install tensorflow
We we test the installation by running this program on shell:
>>> import tensorflow as tf
If there is no error, it means tensorflow is successfully installed.
```

# Installing keras

Open Anaconda Prompt and type the following commands.
pip install keras

# DATASETS WITHIN KERAS

Finding the right dataset is a challenging and most common problem in building and testing a predictive model. Keras provides a widely available standard datasets for building machine learning applications. List of popular datasets:

+   - Boston Housing (regression)
- MNIST (classification of 10 digits)
- Fashion-MNIST (classification of 10 fashion categories)
- CIFAR10 (classification of 10 image labels)
- CIFAR100 (classification of 100 image labels)
- IMDB Movie Reviews (binary text classification)
- Reuters News (multiclass text classification)

# BUILDING A DEEP NEURAL NETWORK USING SEQUENTIAL APPROACH FOR OBJECT DETECTION USING CIFAR DATASET

# What is CIFAR-10?

CIFAR-10 (Canadian Institute for Advanced Research) dataset shown in Figure 10 is a classical computer-vision dataset comprising of 60,000 colored images of 32x32 dimension each and having 10 different