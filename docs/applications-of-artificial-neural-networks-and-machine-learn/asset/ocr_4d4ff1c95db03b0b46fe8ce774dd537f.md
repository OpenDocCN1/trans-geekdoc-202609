and for the hidden layers:

$$\delta_{pt} = f_t'(\text{net}_{pt}) \sum_k \delta_{pt} w_{kt}$$ (5.6)

The derivative of the activation function that is utilized in Eq. (5.5) is given as:

$$f_t' = \frac{\partial o_{pt}}{\partial net_{pt}} = o_{pt}(1 - o_{pt})$$ (5.7)

where $k$ indicates an upper layer unit (the output layer is the uppermost, and the input layer is the lowermost layer).

The learning rule associated with the backpropagation method is known as the generalized delta rule. According to this rule, to modify the weights in the network, for a given pattern $p$, the following relation can be employed:

$$\Delta w_{st}(n) = \eta \delta_{pr} o_{pt} + \alpha w_{st}(n - 1)$$ (5.8)

where $n$ is the input–output presentation number and $h$ is the learning rate and $a$ is the momentum. The momentum, $a$, is a fraction that is multiplied by the previous weight change and added to the current weight change; $a$ should be positive and less than 1. These two terms are not independent and should be selected and adjusted as a pair. Although the dynamic adjustment of both parameters can generally accelerate convergence, a tremendous value for either $h$ or $a$ may lead to instability in the training process. Once the change to the weights is observed, the new weights are measured as:

$$w_{st}(n + 1) = w_{st}(n) + \Delta w_{st}(n)$$ (5.9)

The errors are usually huge at the commencement of the learning process, which requires more changes in weights in the preceding stages of the learning process. By applying the backpropagation procedure, the network determines delta signals for the output layer and hidden layers, utilizing Eqs. (5.5) and (5.6), respectively. These deltas are employed to measure the changes for all amounts of weight according to Eq. (5.8) and the subsequent weight values using Eq. (5.9).

# 5.3.2 Feedforward Neural Networks

In artificial neural networks, feedforward neural networks (FFNN) incorporate a set of processing elements called neurons [10]. Feedforward neural networks, trained with a backpropagation learning algorithm, Fig. 5.7, are the most popular neural networks employed for a wide variety of applications. There are no cycles or loops in feedforward networks. In such networks, the information moves only in the forward