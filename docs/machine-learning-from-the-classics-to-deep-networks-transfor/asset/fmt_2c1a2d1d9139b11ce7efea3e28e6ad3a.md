
# Transformer Inference Process

Once training has been completed via the backpropagation algorithm, all the unknown parameters have been estimated and fixed. In other words, we have obtained estimates of all the parameters that are associated with all the `W^(q)`, `W^(k)`, `W^(v)`, `W⁰` matrices of all the layers and blocks as well as the parameters that define all the fully connected networks and the vocabulary embedding matrices, in the encoder and the decoder parts.

During inference, a sequence of words is presented to the input of the encoder and the transformer network responds by providing a corresponding output at the decoder. Let us focus on our translation example.

## Step 1: Input Tokenization

The input sequence “Je suis étudiant” is tokenized via vocabulary and positional embeddings, and augmented with the corresponding embeddings of the `⟨SOS⟩` and `⟨EOS⟩` tokens, to form the sequence `x[0], x[1], …, x[4]` that feeds the first encoder block.

## Step 2: Encoder Output

The corresponding output embeddings of the encoder, `h[0]^(L), h[1]^(L), …, h[4]^(L)`, are fed to all the blocks of the decoder, in the respective encoder-decoder attention layers.

## Step 3: Decoder Autoregressive Generation

The following sub-steps are in order:

### 1. n = 0

The decoder input consists of `y[0]`, which is set equal to the embedding that corresponds to the `⟨SOS⟩` token. The decoder responds with assigning values to the output `ŷ_0`. The values of this vector are conditional probabilities, given the input sequence at the encoder as well as the embedding of `⟨SOS⟩`. The dimension `i` of the element in `ŷ_0` with the largest value is selected, after a hard-thresholding operation, and this is considered as the id of the vocabulary word that the decoder decides. For the case of our example, assuming that the decision is correct, and if the vocabulary index of the word “I” is, say, 1524, then the dimension with the largest value in `ŷ_0` should be equal to `i = 1524`.

### 2. n = 1

The decoder input consists of `y[0], y[1]`, where `y[1]` is the embedding associated with “I.” The decoder will respond with a new output vector `ŷ_1`. After hard-thresholding, the dimension associated with the element of the largest value indicates the id of the word to be decided at this step. For the case of our example, this dimension should be equal to 235, since this is the id that we have assumed for the word “am.”
