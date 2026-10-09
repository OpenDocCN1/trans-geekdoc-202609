
![](img/e4200cc4308edaf8913e513b0f96dbb6_313_0.png)

It is generally believed that the more primitive the information, the more complete the information, and direct conversion of data generally leads to information loss. In theory, if the input is waveform data, there is a network that can automatically achieve FFT calculation, and it can also achieve any form of feature extraction. However, based on experience, manually defined transformations, such as spectrum or MFCC, are considered to perform well in speech emotion recognition tasks, so it is unnecessary to try another neural network to discover a better feature, which requires additional computational costs. The characteristic of Mel-spectrogram is that it contains both time-domain and frequency-domain information, and traditional transformations, such as FFT and Mel-filter, are also included. Therefore, Mel-spectrogram contains a large amount of original information, and some necessary transformations reduce the computational burden of the model. In addition, Mel-spectrogram can directly link convolutional layers, which makes it very suitable as an input for DRSN. Therefore, Mel-spectrogram is selected as input feature in this research.

## 3.2. Deep Residual Shrinkage Network

The notion behind the incorporation of the residual shrinkage module into the deep residual network has led to the development of the deep residual shrinkage network, as exemplified in Figure 4. The deep residual shrinkage network (DRSN) is a sophisticated deep neural network that employs attention mechanism and soft threshold function to remove noise in data. The self-attention mechanism utilized by the DRSN methodically selects relevant features while eliminating ineffectual features and noise, thereby elevating the deep neural network’s capacity to extract valuable features from noisy data.

![](img/e4200cc4308edaf8913e513b0f96dbb6_313_1.png)

Convolution layer is an important component of the model, which can extract local features and reduce the number of weights through local connections and weight sharing of convolution kernels. The size of convolution kernels is an important parameter in building a model. Common convolution kernel sizes include $3 \times 3$, $5 \times 5$, and $7 \times 7$. A large convolution kernel size can increase the receptive field of the model, but the convolution calculation will also increase. If the size of the convolution kernel is small, the convolution calculation can be reduced, but then the receptive field becomes smaller. In the research of VGG-19, it is analyzed that stacking two layers of $3 \times 3$ convolution layer can be equivalent to $5 \times 5$ receptive field, and stacking three layers of $3 \times 3$ convolution layer can be equivalent to $7 \times 7$ receptive field [30]. When the receptive field is the same, multiple $3 \times 3$ convolution layers use multiple non-linear activation function, which will increase the non-linear expression ability, thus providing more complex pattern learning. In addition, using $3 \times 3$ convolution kernels can reduce parameters. Assuming that there are currently three layers of $3 \times 3$ convolution kernels stacked in a convolution layer with C input and output channels, its total number of parameters is $3 \times 3 \times 3 \times \text{C} \times \text{C} = 27\text{C}^{2}$. For one convolution layer with the same size of receptive field, the convolution kernel is $7 \times 7$. If the number of input and output channels are both C, the total number of its parameters is $7 \times 7 \times \text{C} \times \text{C} = 49\text{C}^{2}$. Overall, the stacking of $3 \times 3$ convolution kernel not only increases the depth of the network but also reduces the number of parameters, so the stacking of layers with $3 \times 3$ convolution kernel is selected for the network in this paper.

### 3.2.1. Residual Shrinkage Building Unit

Residual Shrinkage Building Unit (RSBU) is the basic unit of DRSN. The structure of residual shrinkage module is shown in Figure 5.

As shown in Figure 5, the DRSN is composed of two-batch normalization (BN), two activation functions (Mish), two convolution layers (Conv), one identity mapping, and one soft threshold learning subnetwork. There is a sub-network in each part and its function is to learn a set of thresholds independently. Its learning process is as follows:

- (1) Take absolute values for all input features;
- (2) An feature $A$ is obtained after global average pooling (GAP);
- (3) Input $A$ into a fully connected network. The sigmoid function is on the last layer, and the output is a coefficient $\alpha$ in the range of 0 to 1;
- (4) $\alpha A$ is the threshold to be learned.

![](img/e4200cc4308edaf8913e513b0f96dbb6_314_0.png)

Figure 5. Residual shrinkage building unit.

In this way, the threshold is guaranteed to be positive and not too large. Different feature maps learn different thresholds, so the above subnetworks can be used as an attention mechanism, the soft threshold converts the observed invalid features to zero; important features noted are preserved.

### 3.2.2. Soft Thresholding

In this paper, the soft threshold function is used to remove the features close to 0 and retain the positive and negative features. The soft threshold function is shown in Equation (4). In the equation, *x* is the input feature, *y* is the output feature, and *thr* is the threshold.

$$y = \left\{ \begin{array}{ccc} x - thr & & x > thr \\ 0 & & -thr \le x \le thr \\ x + thr & & x < -thr \end{array} \right.\tag{4}$$

Equation (5) is derived from Equation (4), and the soft threshold function becomes 1 or 0 after derivation.

$$\frac{\partial y}{\partial x} = \left\{ \begin{array}{ccc} 1 & & x > thr \\ 0 & & -thr \le x \le thr \\ 1 & & x < -thr \end{array} \right.\tag{5}$$

The process of soft threshold can also be converted into Equation (6), in which, *x* is the input data of the sub-network, *thr* is the threshold after network learning, and *sign*(*) is the symbolic function.

$$soft = (x, a) = sign(x) * \max\{\,|x| - thr, 0\}\tag{6}$$

The key of soft thresholding is to obtain the range of threshold independently. The deep neural network has good performance in self-learning, so the combination of soft thresholding and deep neural network can well distinguish effective features from irrelevant features.

### 3.2.3. Self-Attention Mechanism

The attention mechanism principle involves facilitating neural network models to independently learn input features and assign weights to them. This approach allows the model to allocate ample computing resources to acquire crucial features, leading to improved performance.

The attention mechanism involves a process of key-value mapping through the query operation of vector matrix. This entails computing the similarity between dimension vectors and deriving the corresponding weight values, which are then normalized via the SoftMax function. Subsequently, the weight value is multiplied to the vector of each matrix dimension and their sum is obtained to formulate the final attention matrix. When *K = V = Q*, the process is referred to as self-attention and can be represented by Equation (7).

$$Attention(Q, K, V) = softmax\left\{\frac{QK^T}{\sqrt{d_k}}\right\}\tag{7}$$

In which, $Q = (q_1, q_2, ..., q_l) \in R^{n \times d}$, $K = (k_1, k_2, ..., k_l) \in R^{n \times d}$, $V = (v_1, v_2, ..., v_n) \in R^{n \times d}$, $d$ is the dimension of a single vector, $n$ is the number of input vectors, which are obtained by linear transformation of input matrix $X$. $K^T$ is the transposition of $K$, and $d_k$ is a matrix with dimension $k$ for adjusting inner product. The input sequence linear mapping process formula is as follows:

$$\left\{ \begin{array}{l} Q = W_q X \\ K = W_k X \\ V = W_v X \end{array} \right.\tag{8}$$

In which, $w_g$, $w_k$, and $w_z$ are three linear mapping parameter matrices, which are self learned in model training process.

## 3.3. Bi-Directional Gated Recurrent Unit

The gated recurrent unit (GRU) is a type of lightweight cyclic neural network that differs from other neural networks due to its internal “gate” structure. This unique structure enables the network to determine which data are relevant and which data can be discarded based on their relationship, facilitating effective data transmission within the network and effectively controlling internal information. As a result, the GRU partially addresses the issue of long-term dependence in neural networks. The internal structure of the GRU consists of three main components, the reset gate, update gate, and hidden state, which work together to extract temporal information and obtain long-term dependencies. The individual functions of these gates are described in further detail below, while the internal structure of the GRU is displayed in Figure 6.

### (1) Reset gate and update gate

The input for the reset and update gates is obtained through the fully connected layer that operates on the current input $x_t$ and the hidden state of the previous time step $h_{t-1}$. An activation function is applied to transform the input of the reset gate into a value between 0 and 1. This value is then used to determine the relevancy of the input. Specifically, an input with a value of 0 will be discarded whereas an input with a value of 1 will be retained. The product of the reset output and the previous hidden state is calculated element-wise. The update gate regulates the extent to which the previous state information is incorporated into the current state. Both the reset and update gates influence the candidate hidden state of the current neuron simultaneously. The reset gate can be computed as per Equation (9).

$r_t = sigmoid\left(\left[w_{hr}|w_{xr}\right] \otimes [h_{t-1}|x_t]^T\right)$ (9)

![](img/e4200cc4308edaf8913e513b0f96dbb6_316_0.png)

In which $\otimes$ is cross product of matrix, $t$ is the current time point, $t-1$ is the last time point, $x_t$ is the input sequence of current time point, $h_{t-1}$ is the hidden state of last time point, and $w_{hr}$ and $w_{xr}$ are the hidden state of last time and weight matrix of input sequence at current time point. According to the current information selection of the reset gate, the candidate hidden state is calculated by Equation (10).

$\tilde{h}_t = \tanh\left(w_{\tilde{h}} \otimes [h_{t-1} \circ r_t]|x_t\right)$ (10)
