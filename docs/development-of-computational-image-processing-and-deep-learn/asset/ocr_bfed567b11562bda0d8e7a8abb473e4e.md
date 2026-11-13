# 4. Split

Before being fed into the neural network, the data, consisting of CT scan arrays coupled with their respective, experimentally (destructively) observed FVC values, are split into a *training* and a *validation set*. The larger training set is used for the initial tuning of the network's parameters similar to [289].

In between each training epoch, the validation set is used to verify the model's performance on unseen data, which prevents overfitting and allows for an estimation of the model's ability to generalize beyond the training set. More details on the training process are discussed in the *Network training process* paragraph below.

**Network architecture** ⁵ A special characteristic of the network implemented in this work is the direct input of a 3D scan along with a singular scalar value representing its corresponding FVC making it a mixed network. However, the output of the network is only the predicted FVC as a singular value between 0 and 1 for a given scan.

For image processing tasks, the conventional type of neural network is a CNN.

The model architecture in this work consists of several layers of convolutions, pooling, dense, and dropout layers. Overall, the neural network can be divided into two stages: The feature extraction stage, where the convolution is happening and the subsequent feature processing stage, where the extracted features are mapped to a corresponding output.

The input layer takes in a 3D tensor of depth, width, and height, representing the CT-scan data, as a single channel since the CT-scans are in gray scale. Furthermore, the single scalar value for the FVC is passed along.