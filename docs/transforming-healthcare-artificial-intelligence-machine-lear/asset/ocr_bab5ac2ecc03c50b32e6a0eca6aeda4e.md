# Melanoma detection by hybrid attention DCNN-BiLSTM architecture 389

The weights for the spatial attention layer are $\beta_s=[\beta_{s,1},\beta_{s,2},\dots,\beta_{s,n}]$. The weight matrix is denoted by $W_{sp}$, while the bias is denoted by $B_{sp}$. The normalisation function is called softmax. The dot product of the model is indicated by $(\ast)$. The weighted outcome is shown as $O_s$.

CNN's convolutional layers are fundamental components of DCNN. To improve recognition accuracy and learn features from initial data, convolutional layers have their ability to automatically choose input features during training. The input data are connected to different filters or kernel sizes. CNN employs kernels that have been optimised and adopted through a supervised training process to maximise the activation level, is identified by the following equation:

```
$s_{p,q} = g\sum_{i=1}^{D} W_{i,l} \cdot m_{p,i+q} + B$
```

$s_{p,q}$ stands for the $q$ samples within the layer $h$ feature map, $g$ represents a non-linear function (in this research, the Sigmoid function is chosen), $W_{i,l}$ stands for the convolution kernel matrix via a size of $D\times C$, $B$ denotes the bias of the feature map, and $m_{p,i+q}$ displays the activation value linked to the neuron $(p,q)$. From the information provided, DCNN may acquire features with progressively higher levels of abstraction. A convolution layer frequently collaborates with a pooling layer to prevent feature distortions. To limit the number of parameters required for the calculation, the max pooling layer also aids to decrease the dimensionality of the derived feature map. Equation (18.46) provides information on the max-pooling layer's output.

```
$y_{p,q} = \max_{z\in Z}(S_{p,A+z,q})$
```

where $A$ is the pooling stride and $Z$ is the dimension of the layer that is

The primary challenge in employing recurrent neural networks (RNN) for long-term learning is gradient fading or explosion. Two gated RNN algorithms, gated recurrent unit (GRU) and long-term memory (LSTM), are suggested to solve this RNN challenge. GRU requires less learning time and fewer parameters, but LSTM performs better with larger datasets. Using memory cells to store and output data, the LSTM is trained to handle sequential data to learn long-scale temporal correlations.

Combining LSTM with a bidirectional recurrent neural network (RNN) yields BiLSTM. BiLSTM differs from LSTM networks in that it connects data from both the past and the future. Figure 18.3 illustrates how the result of the BiLSTM cell contains the current state $k_s$ as well as the