
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_508_0.png)

Figure 15.10: Illustration of an LSTM. Adapted from Figure 8.9.4 of [Zha+19a].

where **O**_t is the **output gate**. See Fig. 15.10 for an illustration. Note that **H**_t is used as the output of the unit as well as the hidden state for the next time step. This lets the model remember what it has just output (short-term memory), whereas the cell **C**_t acts as a long-term memory.

Sometimes we add **peephole connections**, where we pass the cell state as an additional input to the gates. Many other variants have been proposed. In fact, [JZS15] used genetic algorithms to test over 10,000 different architectures. Some of these worked better than LSTMs or GRUs, but in general, LSTMs seemed to do consistently well across most tasks. Similar conclusions were reached in [Gre+17]. More recently, [ZL17] used an RNN controller to generate strings which specify RNN architectures, and then trained the controller using reinforcement learning. This resulted in a novel cell structure that outperformed LSTM. However, it is rather complex and has not been adopted by the community.

## 15.3 1d CNNs

Convolutional neural networks (Chapter 14) compute a function of some local neighborhood for each input using tied weights, and return an output. They are usually used for 2d inputs, but can also be applied in the 1d case, as we discuss below. They are an interesting alternative to RNNs that are much easier to train, because they don’t have to maintain long term hidden state.

### 15.3.1 1d CNNs for sequence classification

In this section, we discuss the use of 1d CNNs for learning a mapping from variable-length sequences to a fixed length output, i.e., a function of the form $f_\theta : \mathbb{R}^{DT} \to \mathbb{R}^C$, where $T$ is the length of the

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_509_0.png)

Figure 15.11: Illustration of the TextCNN model for binary sentiment classification. Adapted from Figure 15.3.5 of [Zha+19a].

input, D is the number of features per input, and C is the size of the output vector (e.g., class logits). A basic 1d convolution operation applied to a 1d sequence is shown in Fig. 14.3. Typically the input sequence will have D > 1 input channels (feature dimensions). In this case, we can convolve each channel separately and add up the result, using a different 1d filter (kernel) for each input channel to get $z_i = \sum_d \mathbf{x}_{i-k:i+k,d}^\top \mathbf{w}_d$, where $k$ is size of the 1d receptive field, and $\mathbf{w}_d$ is the filter for input channel $d$. This produces a 1d vector $\mathbf{z} \in \mathbb{R}^T$ encoding the input (ignoring boundary effects). We can create a vector representation for each location using a different weight vector for each output channel $c$ to get $z_{ic} = \sum_d \mathbf{x}_{i-k:i+k,d}^\top \mathbf{w}_{d,c}$. This implements a mapping from $TD$ to $TC$. To reduce this to a fixed sized vector, $\mathbf{z} \in \mathbb{R}^C$, we can use max-pooling over time to get $z_c = \max_i z_{ic}$. We can then pass this into a softmax layer.

In [Kim14], they applied this model to sequence classification. The idea is to embed each word using an embedding layer, and then to compute various features using 1d kernels of different widths, to capture patterns of different length scales. We then apply max pooling over time, and concatenate the results, and pass to a fully connected layer. See Fig. 15.11 for an example.

### 15.3.2 Causal 1d CNNs for sequence generation

To use 1d CNNs in a generative setting, we must convert them to a causal CNN, in which each output variable only depends on previously generated variables. (This is also called a convolutional Markov model.) In particular, we define the model as follows:

$p(\mathbf{y}|\mathbf{x}) = \prod_{t=1}^T p(y_t|\mathbf{y}_{1:y-m}, \mathbf{x})$ (15.20)

where $m$ is the memory length of the model, $\mathbf{x}$ is some optional conditioning information, $T$ is the length of the output, and $p(y_t|\mathbf{y}_{1:t-m}, \mathbf{x})$ is implemented using causal convolution. This is like

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_510_0.png)

*Figure 15.12: Illustration of the wavenet model using dilated (atrous) convolutions, with dilation factors of 1, 2, 4 and 8. From Figure 3 of [oor+16]. Used with kind permission of Aaron van den Oord.*

regular 1d convolution except we “mask out” future inputs, so that $y_t$ only depends on the past values, rather than past and future values. In order to capture long-range dependencies, we can use dilated convolution (Sec. 14.4.4.1), as illustrated in Fig. 15.12.

This model has been successfully used to create a state of the art **text to speech** (TTS) synthesis system known as **wavenet** [oor+16]. In particular, they stack 10 causal 1d convolutional layers with dilation rates 1, 2, 4, …, 256, 512 to get a convolutional block with an effective receptive field of 1024. (They left-padded the input sequences with a number of zeros equal to the dilation rate before every layer, so that every layer has the same length.) They then repeat this block 3 times to compute deeper features.

In wavenet, the conditioning information **x** is a set of linguistic features derived from an input sequence of words; the model then generates raw audio using the above model. It is also possible to create a fully end-to-end approach, which starts with raw words rather than linguistic features (see [Wan+17]).

Although wavenet produces high quality speech, it is too slow for use in production systems. However, it can be “distilled” into a parallel generative model [Oor+18]. We discuss these kinds of parallel generative models in the sequel to this book, [Mur22].

## 15.4 Attention

In all of the neural networks we have considered so far, the hidden activations are a linear combination of the input activations, followed by a nonlinearity: $z = \varphi(\mathbf{w}^\top \mathbf{h})$. The weights **w** are fixed parameters that are learned on a training set and applied to dynamically computed hidden states **h**. In this section, we consider models in which the weight vectors are also computed dynamically, in an input-dependent way. That is, we consider models which use the following kind of unit:

$z = \varphi\big(f(\mathbf{h};\boldsymbol{\theta})^\top \mathbf{h}\big)$

(15.21)

where $f(\cdot;\boldsymbol{\theta})$ is a learnable function that predicts what weights to use at run-time. This is a form of multiplicative unit.

Models with units of the form Eq. (15.21) are said to be using **attention**, since it allows the model to adaptively “pay attention to” different parts of its inputs by adjusting the weights. Attention mechanisms can be applied to many kinds of neural nets, but were first used in the context of RNNs,

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_511_0.png)

Figure 15.13: Illustration of seq2seq with attention for English to French translation. Used with kind permission of Minh-Thang Luong.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_511_1.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_511_2.png)

Figure 15.14: Illustration of the attention heatmaps generated while translating two sentences from Spanish to English. (a) Input is “hace mucho frio aqui.”, output is “it is very cold here.”. (b) Input is “¿todavia estan en casa?”, output is “are you still at home?”. Note that when generating the output token “home”, the model should attend to the input token “casa”, but in fact it seems to attend to the input token “?”. Generated by https://bit.ly/2QIIrBt.

so we explain the approach in more detail in that context below.

### 15.4.1 Seq2seq with attention

Consider the seq2seq model from Sec. 15.2.3. This uses an RNN decoder of the form $h_t^d = f_d(h_{t-1}^d, c)$, where $c$ is a fixed-length context vector, representing the encoding of the input. Usually we set $c = h_T^e$, which is the final state of the encoder RNN (or we use a bidirectional RNN with average pooling). However, for tasks such as machine translation, this can result in poor performance, since the output does not have access to the input words themselves. We can avoid this bottleneck by allowing the output words to directly “look at” the input words. But which inputs should it look at? After all, word order is not always preserved across languages (e.g., German often puts verbs at the
