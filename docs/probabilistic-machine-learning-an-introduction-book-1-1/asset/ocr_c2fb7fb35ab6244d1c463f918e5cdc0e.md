![](bbox=[0.27, 0.15, 0.82, 0.35])

*Figure 15.12: Illustration of the wavenet model using dilated (atrous) convolutions, with dilation factors of 1, 2, 4 and 8. From Figure 3 of [oor+16]. Used with kind permission of Aaron van den Oord.*

regular 1d convolution except we “mask out” future inputs, so that $y_t$ only depends on the past values, rather than past and future values. In order to capture long-range dependencies, we can use dilated convolution (Sec. 14.4.4.1), as illustrated in Fig. 15.12.

This model has been successfully used to create a state of the art **text to speech** (TTS) synthesis system known as **wavenet** [oor+16]. In particular, they stack 10 causal 1d convolutional layers with dilation rates 1, 2, 4, …, 256, 512 to get a convolutional block with an effective receptive field of 1024. (They left-padded the input sequences with a number of zeros equal to the dilation rate before every layer, so that every layer has the same length.) They then repeat this block 3 times to compute deeper features.

In wavenet, the conditioning information **x** is a set of linguistic features derived from an input sequence of words; the model then generates raw audio using the above model. It is also possible to create a fully end-to-end approach, which starts with raw words rather than linguistic features (see [Wan+17]).

Although wavenet produces high quality speech, it is too slow for use in production systems. However, it can be “distilled” into a parallel generative model [Oor+18]. We discuss these kinds of parallel generative models in the sequel to this book, [Mur22].

# 15.4 Attention

In all of the neural networks we have considered so far, the hidden activations are a linear combination of the input activations, followed by a nonlinearity: $z = \varphi(\mathbf{w}^\top \mathbf{h})$. The weights **w** are fixed parameters that are learned on a training set and applied to dynamically computed hidden states **h**. In this section, we consider models in which the weight vectors are also computed dynamically, in an input-dependent way. That is, we consider models which use the following kind of unit:

$z = \varphi\big(f(\mathbf{h};\boldsymbol{\theta})^	op \mathbf{h}\big)$

(15.21)

where $f(\cdot;\boldsymbol{\theta})$ is a learnable function that predicts what weights to use at run-time. This is a form of multiplicative unit.

Models with units of the form Eq. (15.21) are said to be using **attention**, since it allows the model to adaptively “pay attention to” different parts of its inputs by adjusting the weights. Attention mechanisms can be applied to many kinds of neural nets, but were first used in the context of RNNs,