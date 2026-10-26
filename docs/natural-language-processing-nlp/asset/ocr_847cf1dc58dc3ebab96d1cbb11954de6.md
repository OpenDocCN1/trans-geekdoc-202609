![](bbox=[0.32, 0.13, 0.65, 0.24])

Figure 18.6: A general view of neural attention. The dotted box indicates that each $\alpha_{m\to n}$ can be viewed as a gate on value $n$.

operation is differentiable. For each key $n$ in the memory, we compute a score $\psi_\alpha(m, n)$ with respect to the query $m$. That score is a function of the compatibility of the key and the query, and can be computed using a small feedforward neural network. The vector of scores is passed through an activation function, such as softmax. The output of this activation function is a vector of non-negative numbers $[\alpha_{m\to1}, \alpha_{m\to2}, \dots, \alpha_{m\to N}]^\top$, with length $N$ equal to the size of the memory. Each value in the memory $v_n$ is multiplied by the attention $\alpha_{m\to n}$; the sum of these scaled values is the output. This process is shown in Figure 18.6. In the extreme case that $\alpha_{m\to n}=1$ and $\alpha_{m\to n'}=0$ for all other $n'$, then the attention mechanism simply selects the value $v_n$ from the memory.

Neural attention makes it possible to integrate alignment into the encoder-decoder architecture. Rather than encoding the entire source sentence into a fixed length vector $z$, it can be encoded into a matrix $\mathbf{Z} \in \mathbb{R}^{K \times M^{(S)}}$, where $K$ is the dimension of the hidden state, and $M^{(S)}$ is the number of tokens in the source input. Each column of $\mathbf{Z}$ represents the state of a recurrent neural network over the source sentence. These vectors are constructed from a bidirectional LSTM (see § 7.6), which can be a deep network as shown in Figure 18.5. These columns are both the keys and the values in the attention mechanism.

At each step $m$ in decoding, the attentional state is computed by executing a query, which is equal to the state of the decoder, $h_m^{(t)}$. The resulting compatibility scores are,

$$\psi_\alpha(m, n) = v_\alpha \cdot \tanh\big(\Theta_\alpha[h_m^{(t)}; h_n^{(s)}]\big).\tag{18.36}$$

The function $\psi$ is thus a two layer feedforward neural network, with weights $v_\alpha$ on the output layer, and weights $\Theta_\alpha$ on the input layer. To convert these scores into attention weights, we apply an activation function, which can be vector-wise softmax or an element-wise sigmoid:

# Softmax attention

$$\alpha_{m\to n} = \frac{\exp \psi_\alpha(m, n)}{\sum_{n'=1}^{M^{(s)}} \exp \psi_\alpha(m, n')}\tag{18.37}$$