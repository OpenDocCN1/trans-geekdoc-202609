
# Updating Anaconda

Open Anaconda Prompt and type the following command(s) to update anaconda.
conda update conda
conda update --all

# Installing CUDA

Once we have NVidia GPU, we can download CUDA toolkit from NVidia website. (https://developer.nvidia.com/cuda-downloads) by selecting package corresponding to the underlying operating system followed by extracting the packages.

Figure 7.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_61_0.png)

# Downloading cuDNN

Download the latest version of cuDNN. Choose your version depending on your Operating System and CUDA. Membership registration is required.
https://developer.nvidia.com/cudnn
Put your unzipped folder in C drive

# Adding cuDNN to Environment Path

- Open Run dialogue (Win + R) and run the command sysdm.cpl
- In Windows-10 System Properties, please select the Tab Advanced.
- Select Environment Variables and add the following path in your Environment add the following command to environment path

# Deep Learning Keras

Figure 8.

# NVIDIA cuDNN

The cuDNN Deep Neural Network library cuDNN is a GPU-accelerated library of primitives for deep neural networks. cuDNN provides highly tuned implementations for standard routines such as forward and backward convolution, pooling, normalization, and activation layers.
Deep learning researchers and frameworks developers rely on cuDNN for high-performance GPU acceleration. It allows them to focus on training neural networks and developing applications without worrying about low-level GPU details. Many widely used frameworks, such as Caffe, Theano, cuBLAS, cuDNNT, TensorFlow, and PyTorch, use cuDNN. For access to cuDNN optimized deep learning framework containers, which have cuDNN integrated into the frameworks, visit NVIDIA cuDNN to learn more and get started.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_62_0.png)

# cuDNN Download

NVIDIA cuDNN is a GPU-accelerated library of primitives for deep neural networks.

- I Agree To Terms of the cuDNN Software License Agreement

Note: Please refer to the Installation Guide for release prerequisites, including supported GPU architectures and compatibility. For more information, refer to the cuDNN Developer Guide, Installation Guide and Release Notes on the Deep Learning

| Download cuDNN v7.6.3 (August 23, 2019), for CUDA 10.1 |
| Download cuDNN v7.6.3 (August 23, 2019), for CUDA 10.0 |
| Download cuDNN v7.6.3 (August 23, 2019), for CUDA 9.2 |
| Download cuDNN v7.6.3 (August 23, 2019), for CUDA 9.0 |
| Archived cuDNN Releases |

Figure 9.

```
C:\cudnn-9.0-windows10-x64-v7
```

C:\cudnn-9.0-windows10-x64-v7\cuda\bin

# Creating Anaconda Environment

Create a conda environment named "new_env" (you can change the name) by invoking the following command: create -n new_env python=3.7
Now, activate the conda environment by issuing the following command:
activate new_env
(new_env)C:> # Your prompt should change according to the new environment.

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

- Boston Housing (regression)
- MNIST (classification of 10 digits)
- Fashion-MNIST (classification of 10 fashion categories)
- CIFAR10 (classification of 10 image labels)
- CIFAR100 (classification of 100 image labels)
- IMDB Movie Reviews (binary text classification)
- Reuters News (multiclass text classification)

# BUILDING A DEEP NEURAL NETWORK USING SEQUENTIAL APPROACH FOR OBJECT DETECTION USING CIFAR DATASET

# What is CIFAR-10?

CIFAR-10 (Canadian Institute for Advanced Research) dataset shown in Figure 10 is a classical computer-vision dataset comprising of 60,000 colored images of 32x32 dimension each and having 10 different

# Deep Learning Using Keras

category of objects such as automobile, cat, dog, airplane, etc. Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton prepared the dataset (Krizhevsky, Nair and Hinton, 2014) covering the task of object detection in the images intended for computer vision research.

Figure 10. Example of images in CIFAR10 dataset (Kaggle, 2019)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_64_0.png)

# Step 1. Loading the CIFAR10 dataset

Keras datasets provide cifar10.load_data() function which can be used to download the dataset automatically independently of downloading and installing it in a directory. It comprises of training and testing dataset with 50,000 and 10,000 colored images (channel=3) having 32*32 pixel dimensions respectively. The actual label for the train and test set is stored in y_train and y_test arrays and we acquire the size of the datasets and their labels using shape attribute.

Figure 11.

```
import numpy as np
from keras.datasets import cifar10

(X_train, Y_train), (X_test, Y_test) = cifar10.load_data()
print(X_train.shape, Y_train.shape)
print(X_test.shape, Y_test.shape)

Using TensorFlow backend.
Downloading data from https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz
170500096/170498071 = [====================================] - 3s 0us/step
(50000, 32, 32, 3) (50000, 1)
(10000, 32, 32, 3) (10000, 1)
```

# Step 2. Visualizing the Dataset

The first 10 training images will be displayed using matplotlib library.

Figure 12.

```
import matplotlib.pyplot as plt
img_rows, img_cols, channels= 32,33,2
for i in range(0,9):
    plt.subplot(330 + 1 + i)
    plt.imshow(X_train[i])
plt.show()
```

Figure 13.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_65_0.png)

# Deep Learning Using Keras

# Step 3. Normalization

The images can be rescaled from 0-255 to 0-1 by subtracting the mean and dividing it by standard deviation of all pixel values. It is useful to remove distortions in image.

Figure 14.

```
X_train = (X_train - np.mean(X_train)) / np.std(X_train)
X_test = (X_test - np.mean(X_test)) / np.std(X_test)
```

# Step 4. One Hot Encoding

The actual output of these images are provided as integer. We have to convert these integers using categorical() functions shown in Figure 15.

| index | label |
|---|---|
| 0 | airplane (0) |
| 1 | automobile (1) |
| 2 | bird (2) |
| 3 | cat (3) |
| 4 | deer (4) |
| 5 | dog (5) |
| 6 | frog (6) |
| 7 | horse (7) |
| 8 | ship (8) |
| 9 | truck (9) |

Figure 15.

```
num_classes=10
from keras import utils as np_utils
y_train = np_utils.to_categorical(Y_train)
Y_test = np_utils.to_categorical(Y_test)
```
```

# Step 5. Building a Sequential Model From Scratch

The convolution layer comprises of a set of independent filters where each filter allows us to find pattern or features in the image (Figure 17). A random weight is assigned to all filters which will be learned during backpropagation. 32 filters (size 3*3*3) are convolved over the input (size 32*32*3) independently in the first layer resulting in feature map of 30*30*32 dimension using the formula (n-f+1, n-f+1) where n is input size and f is the filter size. However, the image can shrink down to 1 by 1 if we continue this process for a few more layers. In addition, pixel values on every corner of the image is used only by these filters while it are many in the middle. To overcome these problems of shrinking output and data loss from the edges, we have used “padding” in our example. Padding helps us adding border around the image. These convolution layers are added sequentially in the layers followed by activation, max pool and dropout layers.

# Activation Layer

We not use linear activation/identity function for the activation map (output of convolution layer) as the images are highly non-linear in nature and using non-linear activation function as ReLu is valuable after a linear convolution operation.

# Maxpool Layer

Pooling layers operate on each feature map (output of convolution layer) independently in the network. It helps in gradually reducing the number of parameters and computational power of the network. A filter size of 2*2 and stride of 2*2 is used to reduce network parameters in this example.

# Batch Normalization and Dropout Layer

Batch normalization is used for improving the speed, performance, and stability of neural networks while dropout prevents the network from overfitting. Dropout randomly turn off some of the nodes in the layers of the network by setting some probability of eliminating a node in the neural network. We are eliminating 25%, 25% and 50% of the nodes in layer 1, layer 2 and layer 3 respectively.

# Fully Connected Layer-

The entire network in CNN is divided into two parts: feature extraction and classification. The convolution layers are accountable for extracting meaningful features from the images while fully connected layers serve the purpose of predicting the class probability.
