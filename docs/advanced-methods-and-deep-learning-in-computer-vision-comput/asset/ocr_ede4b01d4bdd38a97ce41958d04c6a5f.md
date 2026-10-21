# 6. Deep face recognition using full and partial face images

![](bbox=[0.05, 0.12, 0.95, 0.38])

Interestingly, this operation introduces translational invariance with respect to elastic distortions. The fully connected layer has neurons that have full connection to the activation of the previous layer and unlike the CONV and POOL layers, the FC layer is 2D. They are typically configured to output the predicted label/classes of the network. Hence the FC is usually the last layer of the network. In the work that won the 2012 ImageNet Large Scale Visual Recognition Competition (ILSVRC) (Krizhevsky et al., 2012), 3 FC layers were used, and since then this has been a typical arrangement. Intuitively, flattening the 3D feature maps at the end of the computation gives us an avenue for interpreting the learned spatially invariant features.

The most usual arrangement used by researchers starts with the image input layer and ends with an FC (decision) layer, in between these two are repeated stacks of CONV-ReLU layers followed by POOL layers, then a few FC-ReLU layers. This layered pattern can be described mathematically as:

INPUT ⇒ NM(CONV ⇒ ReLU) ⇒ POOL ⇒ K(FC ⇒ ReLU) ⇒ FC, (6.3)

where N, M, and K are positive real-valued parameters. Usually, the number of CONV-ReLU layers that appear before POOL is within the range 0 < N < 4, and the combinations of variables M and K are usually greater than 1.

# 6.1.1.2 Methods of training CNNs

Generally, there are three ways of deploying CNNs – training a network from scratch, fine-tuning an existing model, or using off-the-shelf CNN features. The latter two approaches are referred to as transfer learning. Since training CNNs from scratch, using the backpropagation algorithm involves the automatic learning of millions of parameters, this approach requires an enormous amount of data. More so, the data-hungry nature of CNNs consequently demands large computational power. Furthermore, the procedure involves the adjustment of several hyperparameters. Thus, an entire network is rarely trained from scratch.

Fine tuning involves transferring the weights of the first n layers learned from a base network, and then continuing the backpropagation using the new dataset. Hence, the target network is trained using the new dataset for a specific task, usually different from that of the base network. Fine tuning is normally used when the new dataset is moderately large (tens of hundreds of thousands) and very different from the dataset used to train the base network. Using the weights of the old network to initialize helps the backpropagation algorithm, thereby leading to relatively fast automatic learning of more specific features.