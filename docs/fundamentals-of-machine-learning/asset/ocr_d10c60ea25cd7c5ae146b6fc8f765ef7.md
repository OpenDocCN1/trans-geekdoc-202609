A. Schematic neuron B. Schematic synapse

![](bbox=[0.195, 0.137, 0.804, 0.276])

**Fig. 4.1** Outline of the components of a neuron and its connectivity to other neurons in the brain that make up the neural network. Outline of a synaptic terminal where neurotransmitters are released that can trigger the opening of ion channels in the receiving neuron, which in turn triggers change of the electric state of the neuron.

referred to the McCulloch–Pitts neuron. Such a unit is shown in figure 4.2A with three input channels, although neurons typically have much larger number of input channels. Input values are labeled by i with a subscript for each channel. Each channel has an associated **weight parameter**, $w_i$, representing the "strength" of a synapse.
MMcCulloch-Pitts perceptron operates in the following way. Each input value is multiplied by the corresponding weight value, and these weighted values are then summed together, mimicking the superposition of electric charges. Finally, if the weighted sum is larger than a certain threshold value, $w_0$, then the output is set to 1 and 0 otherwise. Mathematically this can be written as

```
$y(\mathbf{x}; \mathbf{w}) = \begin{cases} 1 & \text{if } \sum_{i} w_i x_i > w_0 \ 0 & \text{otherwise} \end{cases}$
```

This simple neuron model can be written in a more generic form that we will call the **perceptron**. In this more general model, we calculate the output of a neuron by applying a gain function $g$ to the weighted sum,

```
$y(\mathbf{x}; \mathbf{w}) = g(\mathbf{w}^T \mathbf{x}),$
```

where $\mathbf{w}$ are parameters that need to be set to specific values, or in other words, they are the parameters of our parameterized model for supervised learning. We will come back to this point later regarding how to choose them. The original McCulloch-Pitts neuron in these terms is a threshold perceptron with a threshold gain function,

```
$g(x) = \begin{cases} 1 & \text{if } x > 0 \ 0 & \text{otherwise} \end{cases}$
```

This threshold gain function is a first example of a non-linear function that transforms the sum of the weighted inputs. The gain function is sometimes called the activation function, the transfer function, or the output function in the neural network literature. Non-linear gain functions are an important part of artificial neural networks as further discussed in later chapters.