
### 19.3.8 Encoder: fully connected NNs layer

As it is shown in [Fig. 19.12](#Chp019_997-1102_B9780443292385000251.xhtml#f0065), each one of the output vectors of the “Add & Normalize” layer is presented as input to a feed-forward fully connected neural network (FCN); see Section [18.3.1](#Chp018_885-995_B978044329238500024X.xhtml). In [189], a two-layer FCN is used with an ReLU (Section [18.6.1](#Chp018_885-995_B978044329238500024X.xhtml)) nonlinearity in the hidden layer and linear output units. In [189], the `N + 2` FCNs are identical, i.e., they share the same parameters, which are learned during training. Each FCN outputs `d[m]` values which are stacked together into a vector. Hence, at the output of this layer `N + 2` `d[m]`-dimensional updated vector embeddings are produced.

![Figure 19.12 Each one of the FCNs comprises dm inputs and provides dm outputs. The first hidden layer employs ReLU nonlinearities. The second, output layer, uses linear units.](images/B9780443292385000251/gr012.jpg)

[Figure 19.12](#Chp019_997-1102_B9780443292385000251.xhtml#cf1140) Each one of the FCNs comprises `d[m]` inputs and provides `d[m]` outputs. The first hidden layer employs ReLU nonlinearities. The second, output layer, uses linear units.

### 19.3.9 Encoder: add & normalize layer II

This “Add & Normalize” layer is of the same structure as the one discussed before. It receives the `N + 2` outputs from the FCN layer below and it provides as outputs the respective normalized versions. Let us denote these vectors as `h[n]¹ ∈ ℝ^(d[m])`, `n = 0, 1, …, N + 1`. These vectors are the final *updated* embeddings that are computed and they comprise the outputs of the first block; this is the reason that we have used the superscript “1”; see [Fig. 19.10](#Chp019_997-1102_B9780443292385000251.xhtml#f0055).

The previous `N + 2` output vectors of the first block become the inputs to the second block, and so on. The outputs of the top, `L`th, block of the transformer are denoted as `h[n]^(L) ∈ ℝ^(d[m])`, `n = 0, 1, …, N + 1`, and they constitute the final outputs of the encoder part of the transformer. These vectors are the updated *contextualized* embeddings/representations/encodings of the original input embeddings. In other words, the encoder generates information-rich feature vectors that encode contextual information.

**Remarks 19.5**

*   Encoders based on the self-attention mechanism have been shown to be *universal approximators*, e.g., [107], [201]. In the latter, it is shown that transformer models with positional encoding can universally approximate arbitrary continuous sequence-to-sequence functions on a compact domain.
