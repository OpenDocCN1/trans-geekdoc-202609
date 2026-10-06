# 9.6 NNet vs. PyTorch (brucele)

PyTorch is a machine learning framework initially developed by Facebook (now Meta AI). Since 2022, it is curated by the Linux Foundation. PyTorch was for a long time only accessible through Python, but in 2021, the developers of tidymodel created the R package breeze (Kuhn and Fabian (2022)), which makes some of the functionality from PyTorch available to tidymodel. This includes an MLP network implementation.

In this section, we will discuss the differences between a Neural Network created with the oet package and a Neural Network created by PyTorch (via the brulee package).

The oet package (Venables and Ripley (2002)) was one of the earliest R packages to support Neural Networks. It is well suited for educational purposes, especially to demonstrate how Neural Networks can be used for predictions and to display Neural Networks as graphs¹¹²

In contrast, PyTorch is an advanced science toolkit, and its Neural Network functionality is more up-to-date. Some of PyTorch's functionality, including support for MLP was recently included in R through brulee package.

There are quite a few differences between networks supported by oet and by PyTorch. In this section, we will focus on two aspects:

**Hyper-Parameters:** In PyTorch, you can set and tune numerous hyperparameters that are either unavailable in oet or are available, but not as advanced as. For example, in oet, you can tune the number of hidden neurons for one hidden layer. In PyTorch, you can set and tune the number of hidden neurons for multiple hidden layers.

**Activation Functions:** PyTorch allows us to use the Rectified Linear Unit (ReLU) activation function, while oet does not support ReLU activation function. In what we follow, we will introduce ReLU functions work and why they are superior to classical Sigmoid activation functions, which are supported in oet.

# 9.6.1 Hyper-Parameters

Below is a selective list of hyper-parameters that PyTorch supports. The list is limited to the hyper-parameters that we will later use in the interactive Section 9.7.

¹¹Using the oet package in combination with the NeuralTools package (Beck (2018)) allows us to convert any oet Neural Network into a graph and save as a peg-file.