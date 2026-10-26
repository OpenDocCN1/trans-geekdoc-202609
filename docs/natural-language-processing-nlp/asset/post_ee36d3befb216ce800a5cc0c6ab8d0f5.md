
as the input to an LSTM at layer i + 1:

$\boldsymbol{h}_m^{(s,1)} = \text{LSTM}(\boldsymbol{x}_m^{(s)}, \boldsymbol{h}_{m-1}^{(s)})$ [18.33]

$\boldsymbol{h}_m^{(s,i+1)} = \text{LSTM}(\boldsymbol{h}_m^{(s,i)}, \boldsymbol{h}_{m-1}^{(s,i+1)}), \quad \forall i \ge 1.$ [18.34]

The original work on sequence-to-sequence translation used four layers; in 2016, Google’s commercial machine translation system used eight layers (Wu et al., 2016).⁴

⁴Google reports that this system took six days to train for English-French translation, using 96 NVIDIA K80 GPUs, which would have cost roughly half a million dollars at the time.

- Significant improvements can be obtained by creating an ensemble of translation models, each trained from a different random initialization. For an ensemble of size N, the per-token decoding probability is set equal to,

$\mathrm{P}(w^{(t)} \mid \boldsymbol{z}, \boldsymbol{w}_{1:m-1}^{(t)}) = \frac{1}{N} \sum_{i=1}^{N} \mathrm{p}_i(w^{(t)} \mid \boldsymbol{z}, \boldsymbol{w}_{1:m-1}^{(t)})$ [18.35]

where $\mathrm{p}_i$ is the decoding probability for model $i$. Each translation model in the ensemble includes its own encoder and decoder networks.

- The original sequence-to-sequence model used a fairly standard training setup: stochastic gradient descent with an exponentially decreasing learning rate after the first five epochs; mini-batches of 128 sentences, chosen to have similar length so that each sentence on the batch will take roughly the same amount of time to process; gradient clipping (see § 3.3.4) to ensure that the norm of the gradient never exceeds some predefined value.

## 18.3.1 Neural attention

The sequence-to-sequence model discussed in the previous section was a radical departure from statistical machine translation, in which each word or phrase in the target language is conditioned on a single word or phrase in the source language. Both approaches have advantages. Statistical translation leverages the idea of compositionality — translations of large units should be based on the translations of their component parts — and this seems crucial if we are to scale translation to longer units of text. But the translation of each word or phrase often depends on the larger context, and encoder-decoder models capture this context at the sentence level.

Is it possible for translation to be both contextualized and compositional? One approach is to augment neural translation with an attention mechanism. The idea of neural attention was described in § 17.5, but its application to translation bears further discussion. In general, attention can be thought of as using a query to select from a memory of key-value pairs. However, the query, keys, and values are all vectors, and the entire
operation is differentiable. For each key $n$ in the memory, we compute a score $\psi_\alpha(m, n)$ with respect to the query $m$. That score is a function of the compatibility of the key and the query, and can be computed using a small feedforward neural network. The vector of scores is passed through an activation function, such as softmax. The output of this activation function is a vector of non-negative numbers $[\alpha_{m\to1}, \alpha_{m\to2}, \dots, \alpha_{m\to N}]^\top$, with length $N$ equal to the size of the memory. Each value in the memory $v_n$ is multiplied by the attention $\alpha_{m\to n}$; the sum of these scaled values is the output. This process is shown in Figure 18.6. In the extreme case that $\alpha_{m\to n}=1$ and $\alpha_{m\to n'}=0$ for all other $n'$, then the attention mechanism simply selects the value $v_n$ from the memory.

![](img/ba66a8f6f22adeb28512d560b999a231_462_0.png)

Figure 18.6: A general view of neural attention. The dotted box indicates that each $\alpha_{m\to n}$ can be viewed as a gate on value $n$.

Neural attention makes it possible to integrate alignment into the encoder-decoder architecture. Rather than encoding the entire source sentence into a fixed length vector $z$, it can be encoded into a matrix $\mathbf{Z} \in \mathbb{R}^{K \times M^{(S)}}$, where $K$ is the dimension of the hidden state, and $M^{(S)}$ is the number of tokens in the source input. Each column of $\mathbf{Z}$ represents the state of a recurrent neural network over the source sentence. These vectors are constructed from a bidirectional LSTM (see § 7.6), which can be a deep network as shown in Figure 18.5. These columns are both the keys and the values in the attention mechanism.

At each step $m$ in decoding, the attentional state is computed by executing a query, which is equal to the state of the decoder, $h_m^{(t)}$. The resulting compatibility scores are,

$$\psi_\alpha(m, n) = v_\alpha \cdot \tanh\big(\Theta_\alpha[h_m^{(t)}; h_n^{(s)}]\big).\tag{18.36}$$

The function $\psi$ is thus a two layer feedforward neural network, with weights $v_\alpha$ on the output layer, and weights $\Theta_\alpha$ on the input layer. To convert these scores into attention weights, we apply an activation function, which can be vector-wise softmax or an element-wise sigmoid:

### Softmax attention

$$\alpha_{m\to n} = \frac{\exp \psi_\alpha(m, n)}{\sum_{n'=1}^{M^{(s)}} \exp \psi_\alpha(m, n')}\tag{18.37}$$

### Sigmoid attention

α_{m→n} = σ(ψ_α(m, n))  [18.38]

The attention α is then used to compute a context vector c_m by taking a weighted average over the columns of Z,

c_m = Σ_{n=1}^{M^{(s)}} α_{m→n} z_n,  [18.39]

where α_{m→n} ∈ [0, 1] is the amount of attention from word m of the target to word n of the source. The context vector can be incorporated into the decoder’s word output probability model, by adding another layer to the decoder (Luong et al., 2015):

h̃_m^{(t)} = tanh( Θ_c [h_m^{(t)} ; c_m] )  [18.40]

p(w_{m+1}^{(t)} | w_{1:m}^{(t)}, w^{(s)}) ∝ exp( β_{w_{m+1}^{(t)}} · h̃_m^{(t)} ).  [18.41]

Here the decoder state h_m^{(t)} is concatenated with the context vector, forming the input to compute a final output vector h̃_m^{(t)}. The context vector can be incorporated into the decoder recurrence in a similar manner (Bahdanau et al., 2014).

## 18.3.2 Neural machine translation without recurrence

In the encoder-decoder model, attention’s “keys and values” are the hidden state representations in the encoder network, z, and the “queries” are state representations in the decoder network h^{(t)}. It is also possible to completely eliminate recurrence from neural translation, by applying self-attention (Lin et al., 2017; Kim et al., 2017) within the encoder and decoder, as in the transformer architecture (Vaswani et al., 2017). For level i, the basic equations of the encoder side of the transformer are:

z_m^{(i)} = Σ_{n=1}^{M^{(s)}} α_{m→n}^{(i)} (Θ_v h_n^{(i-1)})  [18.42]

h_m^{(i)} = Θ_2 ReLU( Θ_1 z_m^{(i)} + b_1 ) + b_2.  [18.43]

For each token m at level i, we compute self-attention over the entire source sentence. The keys, values, and queries are all projections of the vector h^{(i-1)}: for example, in Equation 18.42, the value v_n is the projection Θ_v h_n^{(i-1)}. The attention scores α_{m→n}^{(i)} are computed using a scaled form of softmax attention,

α_{m→n} ∝ exp(ψ_α(m, n)/M),  [18.44]

![](img/ba66a8f6f22adeb28512d560b999a231_465_0.png)

Figure 18.8: Translation with unknown words. The system outputs unk to indicate words that are outside its vocabulary. Figure adapted from Luong et al. (2015).

Convolutional neural networks (see § 3.4) have also been applied as encoders in neural machine translation (Gehring et al., 2017). For each word w_m^{(s)}, a convolutional network computes a representation h_m^{(s)} from the embeddings of the word and its neighbors. This procedure is applied several times, creating a deep convolutional network. The recurrent decoder then computes a set of attention weights over these convolutional representations, using the decoder’s hidden state h^{(t)} as the queries. This attention vector is used to compute a weighted average over the outputs of another convolutional neural network of the source, yielding an averaged representation c_m, which is then fed into the decoder. As with the transformer, speed is the main advantage over recurrent encoding models; another similarity is that word order information is approximated through the use of positional encodings.⁶

⁶A recent evaluation found that best performance was obtained by using a recurrent network for the decoder, and a transformer for the encoder (Chen et al., 2018). The transformer was also found to significantly outperform a convolutional neural network.

## 18.3.3 Out-of-vocabulary words

Thus far, we have treated translation as a problem at the level of words or phrases. For words that do not appear in the training data, all such models will struggle. There are two main reasons for the presence of out-of-vocabulary (OOV) words:

- New proper nouns, such as family names or organizations, are constantly arising — particularly in the news domain. The same is true, to a lesser extent, for technical terminology. This issue is shown in Figure 18.8.
- In many languages, words have complex internal structure, known as morphology. An example is German, which uses compounding to form nouns like Abwasserbehandlungsanlage (sewage water treatment plant; example from Sennrich et al. (2016)).

§ 3.3.4), residual connections around the nonlinear activations (see § 3.2.2), and a non-monotonic learning rate schedule.
