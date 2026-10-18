$S_t = \phi\,(w x_t + H x_{t-1})$

where $S_t$ represents the hidden state at time $t$, $w$ is the weight, $H$ is some hidden state, and $\phi$ represents some activation function, which can be a sigmoid or tanh function [19]. This RNN can solve any supervised or unsupervised task and outperforms traditional machine learning algorithm in intrusion or fraud detection. The number of layers and the epochs varies depending on the task on which it acts [20]. This RNN includes a recurrent layer with neurons that maintain the previous information along with the current time information, depicted in Figure 13.14. Followed by a recurrent layer, batch normalization and regularization are done to preclude overfitting and to speed up the training rate. Finally, classification is done with a particular activation function based on the output class.

![](bbox=[0.11, 0.4, 0.83, 0.56])

FIGURE 13.14 Recurrent neural network.

# 13.7.4 Deep Neural Networks (DNNs)

An intrusion detection system is the need of the hour in today’s world due to the rapid development of information technology. DNN takes on the major role in finding security breaches without accessing the information inside the packet, thus maintaining data privacy [23]. The model created by DNN includes multiple hidden layers, and the neurons in the layers are interconnected. Forward-propagation with the appropriate activation function for the perceptron is depicted in Figure 13.15.