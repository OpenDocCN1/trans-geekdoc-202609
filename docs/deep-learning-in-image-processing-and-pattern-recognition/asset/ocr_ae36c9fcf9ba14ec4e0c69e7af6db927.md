$W_z$ and $U_z$ are the weights learned in the update gate.

(2) The hidden state of the current timestep $t$ is calculated by Equation (11):

$$h^t = zh^{t-1} + (1-z)\tilde{h}^t \tag{11}$$

where $\tilde{h}^t$ contains the input of the current timestep and at the same time, the hidden state of the hidden unit of the previous timestep is added into the current hidden state; the calculation formula is shown in (12):

$$\tilde{h}^t = \phi\left(Wx^t + U\left(r\bigcirc h^{t-1}\right)\right) \tag{12}$$

where $W$ represents the weight of the current input and $U$ represents the weight of the hidden state of the hidden unit in the previous timestep.

In the GRU, when the update gate approaches 0, the hidden state ignores the previous hidden state and updates only with the current input, which ensures that the hidden state selectively retains relevant important information and that the information can be expressed more compactly.

In summary, in the model training process, the hidden state $h^{t-1}$ passed down from the previous timestep and the input $x^t$ of the current timestep are used as the input of BiGRU. On one hand, it obtains the two gating states of the reset gate and the update gate and normalizes the obtained information through the sigmoid function to make it act as a gating signal. On the other hand, the image feature sequence is converted into a context vector $C_t$ as the output.

This work introduces an attention mechanism to the encoder-decoder structure to give weights to the output of the encoder. The main implementation details of the attention mechanism are as follows: first, the input data are fed through a feedforward neural network to generate query vectors and key vectors. Then, the similarity between the query vectors and key vectors is calculated and the resulting scores are normalized to obtain the final attention weights. Finally, the attention weights are applied to the value vectors and summed up to obtain the weighted sum as the output feature vector. Through this process, the attention mechanism can learn the importance of different parts of the input data and enable the decoder to better utilize the information from the encoder. It also has strong interpretability and generalization ability.

Specifically, the attention mechanism learns a special attention weight by adding an additional feedforward neural network to the network structure $\alpha_{t_E,t_D}$ where $t_E$ and $t_D$ represents the $t$-th timestep of the encoder and decoder, respectively. The introduction of this weight into the neural network helps to further reconcile the relationship between the hidden states in the encoder and decoder to highlight the focus of model training. The context vector $C_t$ of the output of the $t$-th timestep encoder can be assigned by Equation (13):

$$C^t = \sum_{t_E=1}^{T} \alpha_{t_E,t_D}h_{t_E} \tag{13}$$

At the $t$-th timestep of the decoder, $C_t$ is the weighted sum containing all encoder hidden states and their corresponding attention weights.

The structure of the decoder BiLSTM is similar to that of the encoder. When calculating the prediction sequence, the input values accepted by the decoder are the context vector $C_t$ weighted by the attention mechanism, the system state $S_{t-1}$ of the output of the decoder at the previous timestep, and the hidden state $S_{t-1}$ of the decoder at the previous timestep. With the help of such information, the decoder can calculate the hidden state $h_t$ of the current time node and the probability distribution of the output sequence of the node according to the probability calculation formula, as shown in (14).