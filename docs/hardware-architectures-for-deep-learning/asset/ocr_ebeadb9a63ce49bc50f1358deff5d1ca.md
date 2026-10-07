# 200 Hardware architectures for deep learning

identical to the size of the convolutions in the original AlexNet. However

The significant difference between the iterative version of AlexNet and the original AlexNet is that the number of output channels is significantly lower in each uCNN.

# 9.5 ICNN training schemes

Training of the ICNN was completed in multiple steps. In each training step, the weights were initialized from a Gaussian distribution with zero mean and a standard deviation of 0.01. Each training step is started with a learning rate of 0.01. The learning rate is then reduced by 2x every 20-epoch until the learning rate was as low as $10^{-6}$. By one-epoch, we refer to one of all the 1.2 million images in ImageNet; however, for data augmentation purposes, every few epochs in the order of the images were modified, the image crops were extended and horizontal mirror of the images was used. To train the network, Tesla K80 GPUs were deployed.

When training the ICNN, two different training policies could be adopted. In the first method, the iterations are trained in sequence and in the second method, all iterations are trained in parallel. Each training process, the implications of each training approach, and the trade-offs for adopting one training approach vs. other are discussed.

# 9.5.1 Sequential training

The first training method introduced is a multistep training process carried out sequentially. In this approach, the first uCNN network is separated and its weights are trained as described in Section 9.10.1. Starting from second iteration and moving up, each uCNN is then trained without changing the filter weights in the previous iterations. When training the i-th uCNN (uCNN[i]), this training constraint is enforced by keeping the learning rate of convolutional layers in uCNN[1]-uCNN[i-1] equal to zero. Hence, the weights in the previous iterations are only used during forward propagation. of error during the training process, without affecting the back propagation's update

# 9.5.2 Parallel training

The second training method is a two-step training process. In the first step, the FC layers of the intermediate iterations are removed, and only the FC layers of the last iteration which combine the features from the last CONV layer of all iterations are kept. The resulting network, which is the last iteration of ICNN, is trained first using the training process described earlier, yielding the weights for the FC layer of the last iterations, and CONV layers of all the iterations (Figure 9.7).

In the second step, the FC layers in all other iterations are added to construct parallel networks for the rest of the iterations. Subsequently, the weights in all the CONV layers are kept constant by setting their learning rate to zero, and the

![](bbox=[0.095, 0.963, 0.135, 0.993])