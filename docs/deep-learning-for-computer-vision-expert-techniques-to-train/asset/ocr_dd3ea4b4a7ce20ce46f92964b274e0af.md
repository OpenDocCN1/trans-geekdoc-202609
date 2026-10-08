# The bigger deep learning models

We will go through several model definitions that have achieved state-of-the-art results in the ImageNet competitions. We will look at them individually on the following topics.

# The AlexNet model

AlexNet is the first publication that showed a wide interest in deep learning for computer vision. Krizhevsky et al. (https://papers.nips.cc/paper/4824-imagenet-deep-convolutional-neural-networks.pdf) proposed AlexNet and it has been a pioneer and influential in this field. This model won the ImageNet 2013 challenge. The error rate was 15.4%, which was significantly better than the next. The model was relatively simple architecture with five convolution layers. The challenge was to classify 1,000 categories of objects. The image and data had 15 million annotated images with over 22,000 categories. Out of them, only 1,000 categories are used for the competition. AlexNet used ReLU as the activation function and found it training several times faster than other functions. The architecture of the model is shown here:

![](bbox=[0.125, 0.497, 0.879, 0.693])

Reproduced with permission from Krizhevsky et al.

The paper also used data augmentation techniques such as image translations, horizontal flips, and random cropping. The dropout layer prevents overfitting. The Stochastic Gradient Descent (SGD) for training. The parameters of SGD are carefully tuned. The learning rate changes over a fixed set of training iterations. The momentum and weight decay take fixed values for training. There is a concept Local Response Normalization (LRN) introduced in this paper. The LRN layers normalize every pixel across the filters to avoid huge activation in a particular filter.