
Instead of a single self-attention head, there can be `h` parallel self-attention heads; this is known as multi-head attention. In the original transformer paper, the authors used `h` = 8 heads. Multi-head attention provides different subspace representations instead of just a single representation for the inputs, which helps capture different aspects of the same inputs. It also helps the model expand the focus to different positions. Each head can learn something different, for example, in machine translation, it may be about learning grammar, tense, conjugation, etc.

Multi-head attention have multiple sets of query/key/value weight matrices, each resulting in different query/key/value matrices for the inputs, finally generating output matrices `z`[*i*]. These output matrices from each head are concatenated and multiplied with an additional weight matrix, `W`[*O*], to get a single final matrix, `Z`, with vectors `z`[*i*] as output for each input `x`[*i*]. The parallel input to output transformations for all the heads is depicted in [Fig. 2.12](#ch2.xhtml#fig2_12).

![Figure 2.12 Multi-head attention.](images/fig2_12.jpg)

[Figure 2.12](#ch2.xhtml#b2fig2_12) Multi-head attention.

``` 
head_i = attention(W_q_i^i Q, W_k_i^i K, W_v_i^i V)
```

(2.18)

``` 
multihead(Q, K, V) = W_O concat(head_1, ..., head_h)
```

(2.19)

#### 2.4.2.3 Masked multi-head attention

We want the decoder to learn from the encoder sequence and a particular decoder sequence, which has been already seen by the model, to predict the next word/character. Thus, for the first layer of the decoder, similar to the sequence-to-sequence architecture, only previous target tokens need to be present and others to be masked. This special alteration results in the masked multi-head attention. This is implemented by having a masking weight matrix **M** that has -∞ for future tokens and 0 for previous tokens. This computation is inserted after the scaling of the multiplication of **Q** and **K**^(*T*) and before the softmax so that the softmax results in the actual scaled values for previous tokens and the value 0 for future tokens.

``` 
masked~Attention(Q, K, V) = softmax( (QK^T + M) / sqrt(d_k) ) V
```

(2.20)

#### 2.4.2.4 Encoder-decoder multi-head attention

In the decoder side there is a need to learn the attention relationship between the entire source input and the target output at a given time. Therefore, the query vectors from the target sequence (before a given time) and the keys and values from the entire input sequence of the encoder are passed to the self-attention layer in the decoder as shown in [Fig. 2.7](#ch2.xhtml#fig2_7).

### 2.4.3 Residuals and Layer Normalization

Similar to ResNets, the inputs, **X**, are short circuited to the output, **Z**, and both are added and passed through layer normalization *addAndNorm*(**X** + **Z**) \[[105](#refbib.xhtml#refbib_105)\]. Layer normalization ensures each layer to have 0 mean and a unit (1) variance.

For each hidden unit, *h*[*i*], we can compute

``` 
h_i = (g / σ)(h_i - μ)
```

(2.21)

where *g* is the gain variable (can be set to 1), *μ* is the mean given by $\\frac{1}{H}{\\sum\_{i = 1}^{H}h\_{i}}$ and *σ* is the standard deviation given by $\\sqrt{\\frac{1}{H}{(h\_{i} - \\mu)}^{2}}$.

Layer normalization reduces the **covariance shift**, i.e., the gradient dependencies between each layer, and therefore speeds up the convergence as fewer iterations are needed \[[13](#refbib.xhtml#refbib_13)\]. This is related to batch normalization, where batch normalization happens at one hidden unit level and a 0 mean and a unit (1) variance is achieved on that one batch \[[130](#refbib.xhtml#refbib_130)\]. Advantage of layer normalization is that it works independent of the batch size, i.e., can give a single example, small batch or a large batch.

### 2.4.4 Position wise Feed-forward Networks

Both encoder and decoder contain a fully connected feed-forward network after the attention sub layers. For each position, similar linear transformations with a ReLU activation in between is performed.

``` 
FFN(x) = max(0, xW_1 + b_1)W_2 + b_2
```

(2.22)

Every position goes through the same transformations and they are different only at the layer level.

### 2.4.5 Encoder

The encoder block in the transformer consists of *n* blocks of {*multiheadAttention*, *addAndNorm*, *FFN*, *addAndNorm*} as shown in [Fig. 2.7](#ch2.xhtml#fig2_7). Every layer of multi-head attention in the encoder side attends to the input or the source, i.e., attention between inputs and inputs. Tenney et al. show that each layer of transformer in the encoder side performs a different NLP task in classical sense such as part-of-speech, constituents, dependencies, entity resolution, etc. \[[244](#refbib.xhtml#refbib_244)\].

### 2.4.6 Decoder

The decoder block in the transformer consists of *n* blocks of {*maskedMultiheadAttention*, *addAndNorm*, *encoderDecoderAttention*, *addAndNorm*, *FFN*, *addAndNorm*} as shown in [Fig. 2.7](#ch2.xhtml#fig2_7). The first layer of multi-head attention in the decoder side attends to the target, i.e., attention between masked outputs with themselves. The encoder-decoder attention layer creates attention between the source and the target.

## 2.5 Case Study: Machine Translation

### 2.5.1 Goal

This section will go through a real-world use case of sequence to sequence in the NLP domain—machine translation between English and French sentences. We will apply attention-based and transformer-based techniques to understand, compare, and contrast between the two architectures.

### 2.5.2 Data, Tools, and Libraries

The English-French parallel corpus from [https://www.manythings.org/​anki/​](https://www.manythings.org) is used for the machine translation. For necessary data wrangling and visualization, we use standard Python libraries like Pandas, NumPy, and Matplotlib. We use TorchText and spaCy for basic text processing such as tokenization. Attention-based and Transformer-based sequence-to-sequence are implemented using the PyTorch library.

### 2.5.3 Experiments, Results, and Analysis

#### 2.5.3.1 Exploratory data analysis

Basic data preprocessing like converting sentences to ASCII and filtering out the pairs that are too long is performed as a text normalization step. Then we tokenize the sentences, convert the words to token IDs, and append < bos > and < eos > IDs to the beginning and end of the token ID sequences. Padding the variable-length sequences to the maximum observed length in the batch using the < pad > token ensures a fixed-size tensor for training and evaluation.

The total of 135,842 language pairs after filtering reduce to 131,951 and we further split it into 80% training, 10% validation and 10% test data, i.e., 105,460, 13,308, and 13,183 respectively.

[Figs. 2.13](#ch2.xhtml#fig2_13) and [2.14](#ch2.xhtml#fig2_14) show the distribution plots as histograms for English/French and joint distribution. Most of the sentences in the parallel corpus are between 4 and 8 tokens/words length.

![Figure 2.13 Sentence length distribution for English and French sentences.](images/fig2_13.jpg)

[Figure 2.13](#ch2.xhtml#b2fig2_13) Sentence length distribution for English and French sentences.

![Figure 2.14 Joint distribution for English and French sentences based on length.](images/fig2_14.jpg)

[Figure 2.14](#ch2.xhtml#b2fig2_14) Joint distribution for English and French sentences based on length.
