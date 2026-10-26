are then assembled into a translation (Yamada and Knight, 2001; Galley et al., 2004); in **tree-to-string translation**, the source side is parsed, and then transformed into a string on the target side (Liu et al., 2006). A key question for syntax-based translation is the extent to which we phrasal constituents align across translations (Fox, 2002), because this governs the extent to which we can rely on monolingual parsers and treebanks. For more on syntax-based machine translation, see the monograph by Williams et al. (2016).

# 18.3 Neural machine translation

Neural network models for machine translation are based on the **encoder-decoder** architecture (Cho et al., 2014). The encoder network converts the source language sentence into a vector or matrix representation; the decoder network then converts the encoding into a sentence in the target language.

$$z = \text{ENCODE}(\boldsymbol{w}^{(s)})\tag{18.24}$$  $$\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)} \sim \text{DECODE}(\boldsymbol{z}),\tag{18.25}$$

where the second line means that the function DECODE(z) defines the conditional probability p(\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)}).

The decoder is typically a recurrent neural network, which generates the target language sentence one word at a time, while recurrently updating a hidden state. The encoder and decoder networks are trained end-to-end from parallel sentences. If the output layer of the decoder is a logistic function, then the entire architecture can be trained to maximize the conditional log-likelihood,

$$\log p(\boldsymbol{w}^{(t)} \mid \boldsymbol{w}^{(s)}) = \sum_{m=1}^{M^{(t)}} p(w_m^{(t)} \mid w_{1:m-1}^{(t)}, z)\tag{18.26}$$  $$p(w_m^{(t)} \mid w_{1:m-1}^{(t)}, \boldsymbol{w}^{(s)}) \propto \exp\left(\beta_{w_m^{(t)}} \cdot h_{m-1}^{(t)}\right)\tag{18.27}$$

where the hidden state $h_{m-1}^{(t)}$ is a recurrent function of the previously generated text $\boldsymbol{w}_{1:m-1}^{(t)}$ and the encoding $z$. The second line is equivalent to writing,

$$w_m^{(t)} \mid w_{1:m-1}^{(t)}, \boldsymbol{w}^{(s)} \sim \text{SoftMax}\left(\beta \cdot h_{m-1}^{(t)}\right),\tag{18.28}$$

where $\beta \in \mathbb{R}^{(V^{(t)} \times K)}$ is the matrix of output word vectors for the $V^{(t)}$ words in the target language vocabulary.

The simplest encoder-decoder architecture is the **sequence-to-sequence model** (Sutskever et al., 2014). In this model, the encoder is set to the final hidden state of a **long short-term**