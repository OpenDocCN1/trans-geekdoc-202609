
# Table 8.1 Literature reviews. (Continued)

| Ref. | Algorithm | Advantages | Disadvantages |
|:---|:---|:---|:---|
| [16] | SVR | - It is resistant to irregularities.<br>- Updates to the decision model are simple.<br>- It has a strong capacity for generalisation and good prediction accuracy.<br>- It's simple to put into practice. | - For huge datasets, they are not appropriate.<br>- When there is additional noise in the data set, such as when the target classes overlap, the decision model does not perform effectively. |
| [17] | SVM | - Effective in spaces with high dimensions<br>- Memory-efficient since just a portion of the training points are used (support vectors) | - Heuristics are used to choose kernel functions.<br>- Inability to use data outside of the class spectrum |
| [18] | KRR | - A benefit of kernel ridge regression is that there are methods that compute the classification error rate and leave-one-out mean-squared error using the results of a single training on the entire training set. | - The coefficients vector is not sparse, hence the idea of “support vectors” does not exist. Since support vector machines only need to sum so over set of support vectors and not the full training set, this makes the difference at the time of prediction. |
| [19] | LSTM | - Selection from a variety of LSTM parameters, such as learning rates with input and output biases. As a result, there is no need for fine adjustments. | - They require a significant amount of time and resource for learning in the real world, the linear layers available in each cell, they require high memory bandwidth, which the systems cannot often provide. |

networks are getting attention in order to meet the capacity requirement. As a result, more precise planning tools are required, and the important components to achieving this are accurate models of transmission quality (QoT) and impairments. Additionally, since the margin is small, it is important to maintain the optical network's dependability, and OPM is necessary. OPM enables controllers to identify anomalies and modify the physical layer's setup. However, employing conventional analytical techniques to create such precise modelling and monitoring tools is challenging given the heterogeneity of the contemporary optical network, whereas in [12], with an infinite budget, comprehensive monitoring is available. Although optical networks' future is difficult to foresee, the value of OPM rises as transparency does. The way that networks are changing makes higher degrees of OPM desirable, if not necessary. To meet this OPM demand, numerous technologies have been developed. Applying these strategies in a way that strikes the correct balance between monitoring coverage, sensitivity, and cost will be the problem moving ahead.

In [2], the authors proposed 1D features (the IQHH and IQHD) and 2D IQH features to study OPM in FMF-based optical networks. Using a 10 Gbaud-DP-QPSK signal, they conducted simulations and experiments to assess OPM's performance. The findings demonstrated their ability to predict OSNR values between 8 and 20 dB, CD values between 160 and 1100 ps/nm, and various mode coupling coefficient values. However, the monitoring performance will be significantly impacted by the presence of impairment(s) with level(s), rendering IQH features almost indistinguishable for various circumstances.

In [11], the authors state that the deep neural network (NN)-based OPM technique currently in use lacks the capacity to select the input data. They always accept but also process everything, which could lead to major monitoring errors and undermine the monitoring system's credibility. Due to the diversity of the sent data in future heterogeneous optical networks, which is likely to go beyond the capabilities of the monitoring system. In their new OPM architecture, they suggest an unsupervised generative adversarial network (GAN) as even the judgement module to choose the lawful material that falls within the purview of the monitoring system. Encoder-decoder-encoder (EDE) sub-network, which makes up the generator, jointly learns the image with hidden feature distribution of the legal data. Additionally, the OPM analyser network's training data are the same as the training data for the network in the newly added judgement module, so no additional data are acquired, saving money. To test the model's performance in the judgement module of the simulation, four modulation formats at two-bit rates are considered. The maximum area under the curve (AUC) value is 0.942 when a 60 Gbps 64QAM signal is used as unlawful data. A single image's judgement takes roughly 12ms. Additionally, the impact of task weights and latent feature shape on judgement performance is examined. The current OPM scheme's credibility and safety have been significantly improved by the newly included judging module.

## 8.2 Algorithms Employed for Performance Monitoring

### 8.2.1 Artificial Neural Networks

Information-processing systems called artificial neural networks (ANNs) provide appealing alternatives to traditional approaches like numerical modelling techniques, analytical techniques, or empirical modelling solutions because they generalise by abstraction and learn from observations [20, 21].

ANNs are straightforward to utilise and have the capacity to describe multi-dimensional nonlinear interactions. Additionally, the neural network approach is quick to respond and versatile (i.e., the same modeling technique may be utilised for passive/active devices/systems). These characteristics have made the ANN method popular as a strong tool in many fields, including pattern recognition, voice processing, control, and bio-medical engineering. More recently, it has also been used in RF modelling, microwave design, and optical performance monitoring. Often, the

![](img/d2107fc60629942e7da5355e47fcc33d_146_0.png)

Figure 8.2 Layers of artificial neural networks.

electrical/optical behaviour of passive and active parts/circuits/systems is first modelled using neural networks. When employed in advanced modelling and design, these trained neural networks can provide quick solutions to the problem they were taught [8].

Multiple layers of processing units known as neurons make up an ANN. The coefficients below reflect the strength of the connections between each neuron and the neurons in the next layers. The correlations between sets of input-output data that represent properties of the device or system under examination are discovered by ANNs. The outputs of the ANN are compared to the desired outputs, and errors are determined, after the input vectors are given to the input neurons and the output vectors are generated. As soon as the network has seen all of the training sets, error derivatives are computed and added for each weight. The weights for the neurons are updated using the error derivatives, and training is continued until the errors achieve the desired low levels. The levels of ANN are shown in Figure 8.2.

### 8.2.2 Deep Neural Networks

Each link among the hidden layers of nonlinear processing units (neurons) used in ANN pattern recognition has a corresponding weight. In order for the ANN to learn how to represent complicated models, it must go through an iterative training process in which the input layer first receives raw data, which is then modified and processed by each succeeding hidden

![](img/d2107fc60629942e7da5355e47fcc33d_147_0.png)

Figure 8.3 Layers of DNN.

layer. The number of hidden layers and neurons is a crucial design factor for ANNs since it affects the network’s ability to learn [22].

Regardless of the fact that ANNs have been effectively employed for many years, technological advancements are forcing ANNs to perform at higher and higher levels due to the growing number of datasets. Deep neural networks (DNNs), models based on deep learning, may now be used to tackle these performance problems since they have the speed and accuracy to handle massive amounts of data in parallel using graphic processing units. A network is often referred to as a DNN when it includes two to ten hidden layers [Figure 8.3] and is capable of learning complicated functions more quickly than the conventional ANNs (also called shallow neural networks) [23]. Sigmoid activation functions have historically been utilised by DNNs; however, when hidden layers are added, the network starts to perform worse and converge more slowly. As a result, a unique DNN architecture known as deep rectifier neural networks was created, which replaced the sigmoid activation functions along with rectifier linear functions.

### 8.2.3 Convolutional Neural Networks

The weight matrices of a convolutional neural network (CNN), a particular type of neural network structure, are produced by convolution with filter masks. The better ability of CNNs to interpret organised arrays of data, such as pictures, talks, and audio signal inputs, sets them apart from other neural networks. In this part, we study the matrix form of CNNs in order to comprehend convergence of CNNs. We present an architecture of deep neural networks with larger widths that is inspired by CNNs [24]. CNNs have extensively adopted deep learning (DL) computations and the majority of certain NN categorization, especially in high dimensional information, such as images and recordings. It achieves Deep Neural Network’s superiority, which hinders scaling well with multidimensional privately connected information [25].

As a result, CNN is crucial for information bases, where it was necessary to create a large number of hubs or boundaries. The diagram below shows the CNN architecture. Here is a definition of CNN’s several levels in its architecture.

#### 8.2.3.1 Convolutional Layer

The convolutional layer, which determines the yield of linked input in an open region, is the fundamental component of something like the convolution neural network. A two-dimensional activation guide of the track
