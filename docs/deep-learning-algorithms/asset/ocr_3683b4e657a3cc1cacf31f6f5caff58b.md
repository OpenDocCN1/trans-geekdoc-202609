The performance evaluation of the networks was carried out using a held-out test set 30% of the data. The calculation of the loss and accuracy was achieved as follows:

```
Loss = -\(\left(\frac{1}{n}\right) \sum_{i=1}^n \log P(C)\),

(1)

Accuracy = \(\frac{C}{N}\)
```

where P(C) is the probability of the correctly classified images, n is the number of images, while N is the total number of images during the training and/or testing phases.

# CNN Training

The model architecture and training settings for the CNN employed to perform the classification of brain haemorrhage are presented in this section. Extensive tests are performed to determine the best learning parameters that optimize the neural network.

Note that out of the retrieved 12635 brain CT images, 8855 images are used for training and 3790 images are used for validating the trained network. The CNN architecture employed for the classification of brain haemorrhage images is shown in Figure 3, where “Conv” denotes a convolution layer, “BN” denotes batch normalization, “FM” denotes feature maps, and “FC” denotes fully connected layer.

In this paper, all convolution operations are performed using convolution filters of size 3 × 3 with zero padding; all pooling operations are performed using max pooling windows of size 2 × 2; the input images to the model are of size 32 × 32.

For designing the proposed architecture, we take into consideration the size of available (i.e., limited) training data for constructing a learning model that is considerably regularized.

For example, we employ batch normalization and dropout training schemes which have been shown to improve model generalization [38–40]. For optimizing the proposed model, we employ minibatch optimization via gradient descent; we use a batch size of 60. In addition, we use a learning rate of 0.001 and train the model for 100 epochs. The learning curve for the trained CNN is shown in Figure 4; a validation accuracy of 90.65% is achieved.