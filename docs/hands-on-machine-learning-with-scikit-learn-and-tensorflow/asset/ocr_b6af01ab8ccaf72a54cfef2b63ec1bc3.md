Yann LeCun's website (“LENET” section) features great demos of LeNet-5 classifying digits.

# # AlexNet

The AlexNet CNN architecture won the 2012 ImageNet ILSVRC challenge by a large margin: it achieved 17% top-5 error rate while the best achieved only 26%! It was developed by Alex Krizhevsky (hence the name), Ilya Sutskever, and Geoffrey Hinton. It is quite similar to LeNet-5, much larger and deeper, and it was the first to stack convolutional layers directly on top of each other, instead of stacking a pooling layer on top of each convolutional layer. Table 14-2 presents this architecture.

| Layer | Type | Maps | Kernel size | Stride | Padding | Activation |
| --- | --- | --- | --- | --- | --- | --- |
| Out | Fully Connected | | 1,000 | -- | -- | Softmax |
| F9 | Fully Connected | | 4,096 | -- | -- | ReLU |
| F8 | Fully Connected | | 4,096 | -- | -- | ReLU |
| C7 | Convolution | 256 | 13 × 13 | 3 × 3 | 1 | ReLU |
| C6 | Convolution | 384 | 13 × 13 | 3 × 3 | 1 | ReLU |
| C5 | Convolution | 384 | 13 × 13 | 3 × 3 | 1 | ReLU |
| S4 | Max Pooling | 256 | 13 × 13 | 3 × 3 | 2 | VALID |
| C3 | Convolution | 256 | 27 × 27 | 5 × 5 | 1 | ReLU |
| S2 | Max Pooling | 96 | 27 × 27 | 3 × 3 | 2 | VALID |
| C1 | Convolution | 96 | 55 × 55 | 11 × 11 | 4 | ReLU |
| In | Input | 3 (RGB) | 227 × 227 | | | |

To avoid overfitting, the authors used regularization techniques: first applied dropout (introduced in Chapter 11) with a 50% dropout rate during training to the outputs of F8 and F9. Second, they performed data augmentation by randomly shifting the training images by various offsets, flipping them horizontally, and changing the lighting conditions.

> Data Augmentation
Data augmentation artificially increases the size of the training set by generating many realistic variants of each training instance. This reduces overfitting, making this a regularization technique. The generated instances should be as realistic as possible:

11 “ImageNet Classification with Deep Convolutional Neural Networks,” A. Krizhevsky et al. (2012).