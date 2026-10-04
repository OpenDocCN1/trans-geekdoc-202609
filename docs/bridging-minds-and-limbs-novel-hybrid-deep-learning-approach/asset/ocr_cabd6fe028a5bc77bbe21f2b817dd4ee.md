Z. Sun et al.

Biomedical Signal Processing and Control 112 (2020) 108528

activation, (4) and (5) fully connected. A complete CNN structure contains multiple blocks of these layers, with a classifier at the end:

```
$f_i(X) = \sigma(W_i \otimes X + b_i)$
```

Here, $X$ represents the $i$-th convolution layer, $W_i$ denotes the convolution kernel (weights), and $b_i$ is the bias. The operator $\otimes$ denotes the convolution operation, computes the map by sliding the kernel over the input and performing element-wise multiplications and summations. For each convolutional layer,

+   * The input $X$ is convolved with the kernel $W_i$.
* The bias $b_i$ is added to the convolution.
* The result is then passed through an activation function (e.g., ReLU) and a pooling layer to reduce dimensionality and maintain important features.

O, is the output activation, $W$ and $b$ are the weight matrix and bias for the output gate, $h_t$ is the current hidden state, which serves as both the output of the LSTM and the input to the next step.

Unlike LSTM models, which only consider the past, bidirectional structure of LSTM enables to model both past and future information. This is particularly beneficial for medical imaging (MI) tasks, such as EEG non-stationary signals that span multiple time scales. The bidirectional structure improves the network's ability to capture long-range temporal correlations and phase shifts in EEG, leading to more accurate feature representation.

Fig. 5 illustrates the LSTM-architecture and the internal mechanism of an LSTM. Here, the Bi-LSTM is shown in "unrolled" format across multiple time steps (t-1, t, t+1), both forward and backward temporal. Each block represents an LSTM unit. (b) zooms into the internal structure of a single LSTM cell, detailing the forget gate ($f_t$), output gate ($o_t$), cell gate ($c_t$), and hidden state ($h_t$). The multiplication and addition operations, as shown in equations (4)-(8), use learned parameters and weights to integrate the input to generate the new cell state and hidden state. By combining the left (unrolled) and right (inter-interval) views, Fig. 5 provides a comprehensive overview of how the Bi-LSTM processes EEG data.

The outputs of the activated blocks are aggregated (sum) to form the final representation $f_i(X)$, which is subsequently fed into fully connected layers and a classifier for the final classification. The entire network is trained-end-to-end using backpropagation with a optimizer to adjust the weights and biases.

# 2.5.2. Long-Term Memory

Long-Term Memory (LSTM) networks are crucial for EEG processing due to their ability to capture long-term dependencies in time series. This is particularly important for the temporal analysis of behavioral patterns during memory monitoring tasks. LSTMs use three gates: the forget gate, input gate, and output gate, to control the information flow, allowing the model's ability to adapt to time-dependent changes [3]

The forget gate controls which information from the previous step is retained or discarded, preserving relevant temporal information:

```
$f_t = \sigma(W_f \cdot [h_{t-1}, X_t] + b_f)$
```

Where, $f_t$ is the forget gate activation at time $t$, $X_t$ is the input at time $t$, $h_{t-1}$ is the hidden state from the previous step, $W_f$ is the weight matrix associated with the forget gate, $b_f$ is the bias, and $\sigma$ denotes the sigmoid activation function, which maps values to the range [0,1].

The input gate controls what new information is updated in the long-term and short-term memory:

```
$i_t = \sigma(W_i \cdot [h_{t-1}, X_t] + b_i), \tilde{C}_t = \tanh(W_c \cdot [h_{t-1}, X_t] + b_c)$
```

Where, $i_t$ is the input gate activation, $	ilde{C}_t$ is the candidate cell state, and $W_i$ are the weights for the input gate and cell state respectively, $b_i$ and $b_c$ are the corresponding bias, and $\tanh$ is the hyperbolic tangent function.

The cell state $C_t$ is updated by combining the information from the previous cell state and the new cell state:

```
$C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$ (5)
```

where denotes element-wise multiplication, and $C_{t-1}$ is the previous cell state.

Finally, the output gate controls the current hidden state $h_t$ by passing the updated cell state through a non-linear transformation:

```
$o_t = \sigma(W_o \cdot [h_{t-1}, X_t] + b_o), h_t = o_t \odot \tanh(C_t)$ (7)
```

# 2.5.3. Particle Algorithm

CNN networks effectively extract spatial features from EEG, but the LSTM kernels affect their performance. The Particle Swarm Optimization (PSO) algorithm can optimize the number of parameters by competition and cooperation among particles [5]. In PSO, solution candidates are called "particles", which have position and velocity. The position and velocity of the $i$-th particle in a D-dimensional space are denoted as...

```
$v_i^{d+1} = v_i^d + c_1 r_1 (p_i^d - x_i^d) + c_2 r_2 (g^d - x_i^d)$ (8)
$x_i^{d+1} = x_i^d + v_i^{d+1}$
```

In this context, the reward enters the influence of the velocities on the current iteration, $j$ denotes the number of iterations of $i$, and $r_1, r_2$ are cognitive and social learning factors that determine the relative importance of a particle's performance and the global best positions, $r_1$ and $r_2$ are uniformly distributed variables in the range [0, 1], $p_i^d$ and $p_{global}^d$ introducing stochasticity to avoid local optima, and the personal and global best positions at iterations [j]. The PSO process terminates when one of the following conditions is met: (1) the improvement in classification accuracy becomes negligible over consecutive iterations, or (2) the predefined maximum number of iterations is reached. This ensures a balance between computational efficiency and optimization effectiveness.

5