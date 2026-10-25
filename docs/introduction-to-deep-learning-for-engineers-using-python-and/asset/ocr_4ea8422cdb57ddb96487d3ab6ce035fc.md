# # Introduction to PyTorch

# ## 2.1　INTRODUCTION

PyTorch is a highly optimized library that can manipulate data in the form of tensors. This library was introduced in 2016, and since then, it has been used in creating deep learning models effectively using GPUs and CPUs. The PyTorch documentation and libraries can be found at [4].

For multi-dimensional data manipulation, machine learning architectures use tensors as their primary data structure. François Chollet [5] defined tensor as a container of data, and also classified typically used multi-dimensional tensors in neural-networks. A Tensor can be 0-D (only one scalar value), 1-D (one-dimensional vector), 2-D (two-dimensional matrix), 3-D (three-dimensional array to represent three channels of RGB for color images), 4-D (four-dimensional array, which can be a collection of RGB color images), and 5-D collection of RGB images represented by four-dimensional tensors at different times. Although the concept of a tensor is different in the field of physics and engineering, in recent years, the machine learning community widely adopted this term to explain generalized matrices. So, in this book, we will consider tensor as a vehicle to organize information in more than two dimensions. The multi-dimensional tensors can be illustrated by using cubes, as shown in Fig. 2.1.

In deep learning architecture, the tensor-based data can quickly become enormous during weight and back-propagation calculations. Hence, most of the models are executed on GPUs for parallel computing and effective data manipulations. In 2018, Google released TPU (Tensor Processing Units), which is specially designed for Google’s Tensorflow software to train deep neural networks [6].

# ## 2.2　SETTING UP PYTORCH

PyTorch is relatively easy to learn, especially by someone who already knows a few NumPy operations. Both NumPy and PyTorch use similar syntaxes. The “numpy.zeros()” produces an array of zeros, “numpy.ones()” produces an array of ones, and numpy.random.rand() produces an array of random numbers. Similarly, when we use PyTorch, we can use “torch.zeros()” to produce a tensor of zeros, “torch.ones()” to produce a tensor of ones, and “torch.rand()” to produce a tensor of random numbers.

Before running PyTorch in Jupyter Notebook, it is important to change the programming environment using Anaconda Prompt (Anaconda3). The procedure of changing the environment in Anaconda prompt, and running Jupyter Notebook are given in the following steps.