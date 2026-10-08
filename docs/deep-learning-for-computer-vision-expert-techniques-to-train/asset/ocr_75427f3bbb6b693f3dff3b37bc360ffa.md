# CUDA Deep Neural Network - CUDNN

The CUDNN library provides primitives for deep learning algorithms. Since this package is provided by NVIDIA, it is highly optimized for their hardware and runs faster. Several standard routines for deep learning are provided in such libraries. These packages are used by famous deep learning libraries as tensorflow, caffe, and so on. In the next section, instructions are provided for installing CUDNN. You can download CUDNN from the NVIDIA portal at https://developer.nvidia.com/rdp/cudnn-download.

User account is required (free signup).

![](bbox=[0.133, 0.29, 0.187, 0.347])

Copy the relevant files to the CUDA folders, making them faster to run on GPUs. We will use CUDA and CUDNN libraries directly. TensorFlow uses these to work on GP-GPU with optimized routines.

# Installing software packages

There are several libraries required for trained deep learning models. We will install the following libraries and see the reason for selecting the following packages over the competing packages:

+   * Python and other dependencies
* OpenCV
* TensorFlow
* Keras

# Python

Python is the de-facto choice for any data science application. It has the largest community and support ecosystem of libraries. TensorFlow API for Python is the most complete, and hence, Python is the natural language of choice. Python has two versions—Python2.x and Python3.x. In this book, we will discuss Python3.x. There are several reasons for this:

+   * Python 2.x development will be stopped by 2020, and hence, Python3.x is the future of Python