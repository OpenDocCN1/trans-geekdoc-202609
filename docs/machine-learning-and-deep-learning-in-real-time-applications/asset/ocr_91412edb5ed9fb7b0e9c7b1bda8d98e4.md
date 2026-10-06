# Deep Learning With TensorFlow

2) It is a suggestion to create a different (virtual) environment if you wish to install both TensorFlow variations on your machine. Without making virtual environments, it will either end up failing or when you start running code, there will consistently be incertainitude about which variation is being utilized to execute your code.

# Installation Steps

Step 1: The first step is to install Anaconda Python 3.7. It is optional, any python framework can be used but the authors would suggest using Anaconda because of its instinctive way of managing packages and setting up new virtual environments. Anaconda distribution can be downloaded from the given link: https://www.anaconda.com/download/

Step 2: Installation of TensorFlow CPU

It runs on the CPU of your machine. In some cases, you will feel the degradation of performance in comparison to TensorFlow GPU. It can be done in 3 simple steps:

# 2. 1 Create a new virtual environment (Optional)

+   a) Open Anaconda/ Prompt window

Figure 14.

![](bbox=[0.227, 0.543, 0.792, 0.723])

+   b) Type the following command given below:

Figure 15.

```
(base) C:\Users\sanwarul>conda create -n tensorflow_cpu mlpip python=3.6
```