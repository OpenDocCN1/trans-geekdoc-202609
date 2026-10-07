# Deep Belief Networks for Intelligent Fault Diagnosis 43

Inspired by the prior research, this chapter presents a deep learning model based on DBN for induction motor fault diagnosis. The deep model is built on restricted Boltzmann machine (RBM) which is the building unit of a DBN and by stacking RBMs by one, the deep network architecture can be constructed. It can learn high-level features from frequency distribution of measured signals for diagnosis tasks. Including this section, this chapter is organized in five sections. Section 3.2 presents theoretical background of the deep learning algorithm. Section 3.3 presents the proposed fault diagnosis approach, where the deep architecture based on DBN is described in detail. Experiments to verify the effectiveness of the proposed deep model are detailed in Section 3.4, where classification performance is discussed. Section 3.5 summarizes the whole study and gives directions.

# THEORETICAL FRAMEWORK

DBN is a deep architecture with multiple hidden layers that has the capability to learn hierarchical representations automatically in an unsupervised and perform classification at the same time. In order to accurately structure the model, it contains unsupervised pre-training and supervised fine-tuning. Generally, it is difficult to learn a large number of parameters in a deep architecture which has multiple hidden layers due to the vanishing gradient problem. To address this issue, an effective training algorithm, which learns one layer at a time and each pair of layers is seen as one RBM model, proposed which was introduced by Mohamed, Yu, and Deng (2010) and Chen and Lin (2014). As DBN is formed by units of RBM, the basic unit of DBN, i.e., RBM, is introduced first.

# Architecture of RBM

RBM is a commonly used mathematical model in probability statistics and follows the theory of log-linear Markov random field (MRF) (Tran, Al'Thobiani, and Ball (2014)) which has several special forms and is one of them. An RBM model contains two layers: One layer is the input layer which is also called visible layer, and the other layer is the output layer also called hidden layer. RBM can be represented as a bipartite undirected graphical model. All the visible units of the RBM are fully connected to hidden units, units within one layer do not have any connections between each other. That is to say, there are no connection between visible units or between hidden units. The architecture of a RBM is shown in Figure 3.1.

![](bbox=[0.107, 0.735, 0.791, 0.903])

FIGURE 3.1 Architecture of restricted Boltzmann machine.