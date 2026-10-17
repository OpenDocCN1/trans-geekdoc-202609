
optimization method, the momentum was set to 0.9. For Adam, the gradient decay rate was set to 0.9, the squared gradient decay rate was set to 0.999, and the denominator offset {\_{<

different networks is displayed in Table 3. In addition, we choose the better results in each deep neural network to show the training loss against number of iterations during the fine-tuning process (See Figure 6). The words inside parenthesis indicate the corresponding optimization method.

In Table 3, the ResNet with SGD optimization method gets the highest test accuracy 96.51%. In identifying tomato leaf diseases, the performance of Adam optimization method is inferior to the SGD optimization method, especially in combining with AlexNet. In the following paper, AlexNet (SGD), GoogLeNet (SGD), and ResNet (SGD) are referred to as AlexNet, GoogLeNet, and ResNet, respectively.

As it can be seen in Figure 6, the training loss of ResNet drops rapidly in the earlier iterations and tends to stable afar 3000 iterations. Consistent with Table 3, the performance of AlexNet and GoogLeNet is similar and both inferior to the ResNet.

**Figure 4**. The architecture of GoogLeNet \[22, 45\].

本书版权归Arcler所有

![Image 778](index-171_1.jpg)

![Image 779](index-171_2.png)

![Image 780](index-171_3.png)

![Image 781](index-171_4.png)

![Image 782](index-171_5.png)

Can Deep Learning Identify Tomato Leaf Disease?

145

**Figure 5**. ResNet bottleneck residual building block \[26\].

**Table 3**. Model recognition accuracy.

**Experiments on Batch Size and Number of Iterations**

From the experiment on optimization methods, the ResNet obtains the highest classification accuracy. Next, we evaluated the effects of batch size and the number of iterations on the performance of the ResNet. Te batch size was set to 16, 32, and 64, respectively. Meanwhile, the number of iterations was set to 2496, 4992, and 9984. The classification accuracy of different training scenarios is given in Table 4. At the same time, the classification accuracy of each label’s representative leaf disease category (See Table 1) is given. In this experiment, the initial learning rate was set to 0.001 and dropped by a factor of 0.5 every 2496 iterations.

In Table 4, the best overall classifcation accuracy 97.19% is got by the ResNet combining with batch size 16 and

本书版权归Arcler所有

![Image 783](index-172_1.jpg)

![Image 784](index-172_2.png)

![Image 785](index-172_3.png)

![Image 786](index-172_4.png)

Deep Learning Algorithms

146

Iterations 4992. As shown in Table 4, whether increasing the number of iterations or batch size, the performance of corresponding models has not been improved significantly in identifying tomato leaf disease. A small batch size with a medium number of iterations is quite effective in this work. Moreover, a larger batch size and number of iterations increases the training duration. We have not tried higher or lower values for the attempted parameters, since different classification task may have various suitable parameters, and it is hard to give a certain rule in setting hyperparameters.

**Figure 6**< + process.

**Experiments on Full Training and Fine-Tuning of ResNet** This section is designed for exploring the performance of CNN by changing the structure of the models. In practical, a deep CNN always owns a large size which means a large number of parameters. Thus, full training of a deep CNN requires extensive computational resources and is time-consuming. In addition, full training of a deep CNN may led to overftting when the training data is limited. So we compared the performance of the pretrained CNN

through full training and fine-tuning their structures.

We changed the structure of ResNet, and combination of the best parameters from the front experiments was utilized.

本书版权归Arcler所有

![Image 787](index-173_1.png)

![Image 788](index-173_2.png)

![Image 789](index-173_3.png)

![Image 790](index-173_4.png)

Can Deep Learning Identify Tomato Leaf Disease?

147

**Table 4** +

of the ResNet. The numbers inside parenthesis indicate batch size and number of iterations.

ResNet50 has 177 layers if the layers for each building block and connection are calculated. In this experiment, the last three layers of ResNet

\` £¥|'

The structure was changed by freezing the weights of a certain number of layers in the network by setting the learning rate in those layers to zero.

During training, the parameters of the frozen layers are not updated. Full

\+ # #

\`{+£¥| + (37-“fc”, 79-“fc”, 111-“fc”, 141- “fc”,

163-“fc”). The accuracy and training time of different network structure

<# # !

combined; the initial learning rate was set to 0.001 and dropped by a factor of 0.1 every 2496 iterations. In order to get more convincing conclusions, ResNet (16, 9984), which gets the second place in Table 4, was also used to execute the experiments.

In Table 5, the accuracy and training time of different network structures are presented. In two cases, i.e., the 4992 iterations and 9984 iterations of ResNet, the accuracy of the model from the 37 layer fne-tuning structure are higher than that of the full training model. In the case where the number of

+

structure is equal to that of the full training model.The fonal column of the Table 5 represents the training time of the corresponding network, and it is

\+ models is greatly lowered than

the full training model. Because the gradients of the frozen layers do not need to be computed, freezing the weights of initial layers can speed up network

¨ # + models (37-“fc”, 79-“fc”,

111-“fc”) always led to a performance superior or approximately equal to the full training models. Thus, we suggest that, for practical application, 本书版权归Arcler所有

![Image 791](index-174_1.jpg)

![Image 792](index-174_2.png)

![Image 793](index-174_3.png)

![Image 794](index-174_4.png)

Deep Learning Algorithms

148

\+ models may be a good choice. Especially for the

\+ models may achieve

good performance while saving computational resources and time.

~

(16, 4992, 37-“fc”) were examined by utilizing the t-distributed Stochastic Neighbor Embedding (t-SNE) algorithm (see Figure 7) \[48\]. 1176 test images were used to extract the features. In Figure 7, different colors represent different labels; the corresponding disease categories of the labels were listed in Table 1. As shown in Figure 7, 9 different color points are clearly separated, which indicates that the features learned from the ResNet with the optimal structure can be used to classify the tomato leaf disease precisely.

**Figure 7**. Two-dimensional scatter plot of high-dimensional features generated with t-SNE.

本书版权归Arcler所有

![Image 795](index-175_1.png)

![Image 796](index-175_2.png)

![Image 797](index-175_3.png)

![Image 798](index-175_4.png)

Can Deep Learning Identify Tomato Leaf Disease?

149

**CONCLUSION**

Tis paper concentrates on identifying tomato leaf disease using deep convolutional neural networks by transfer learning. The utilized networks are based on the pretrained deep learning models of AlexNet, GoogLeNet, and ResNet. First we compared the relative performance of these networks by using SGD and Adam optimization method, revealing that the ResNet with SGD optimization method obtains the highest result with the best accuracy, 96.51%. Ten, the performance evaluation of batch size and number of iterations affecting the transfer learning of the ResNet was conducted. A small batch size of 16 combining a moderate number of iterations of 4992
