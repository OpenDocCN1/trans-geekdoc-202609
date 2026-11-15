![](bbox=[0.31, 0.09, 0.69, 0.23])

# **FIGURE 3.2** Detailed look at neurons in layers.

```
y = w₁x₁ + w₂x₂ + w₃x₃ + ... + wₙxₙ + b
z = Activate (y)
```

x₁, x₂, x₃...xₙ are the n inputs which are received by the neuron and w₁, w₂, w₃...wₙ are the weights assigned to the inputs received and b is the bias assigned to the neuron. The neuron transmits z to the next layer of neurons.

# ## 3.2.3 IMPORTANCE OF BIAS AND WEIGHTS IN A NEURAL NETWORK

# ### 3.2.3.1 Weights

Weights are used with each feature given as an input to the neuron and weights tell which feature is more important. As an example, if the weight of one feature is more than another then that means that feature is more important while predicting the output than the other feature with less weight value. Negative value of weights determine that the feature is inversely proportional to the target value which we are predicting.

# ### 3.2.3.2 Biases

Bias is a constant value added to the summation of product of weights and features. Bias is added to make the activation function to shift its direction in either left or right, as an example if we are making the decision that if summation value is greater than 0.5 we will assign class 1 and if less than 0.5 we will assign class 0. This threshold value 0.5 which we have set can be used in comparison and this threshold constant is used in decision making. Let's consider the case when the summation is greater than 0

```
∑ wᵢ.xᵢ > 0.5
∑ wᵢ.xᵢ - 0.5 > 0
```

As we can now see, it is easier for the activation function to fit properly on the given data where boundaries are defined for the summation being greater than 0 in the case of class 1 and the summation being less than 0 in class 0. Bias value can also be considered as intercepts; it doesn’t change the slope but changes the position of the graph so that it can fit as per our needs.