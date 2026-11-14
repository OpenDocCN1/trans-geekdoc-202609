```
def forward(self, x) :
    denom = (x ** 2).mean(dim=-1, keepdims=True)
    denom = torch.sqrt(denom + self.epsilon)
    return x / denom * self.gamma
```

+   - LayerNorm (Lines 5–16):
+     – __init__ (Lines 6–10): Initializes the layer. Here, we initialize two learnable parameters, gamma and beta, with a size equal to the number of channels for element-wise scaling and shifting.
+     – forward (Lines 12–16): Implements the standardization formulation as described in Equation 11.1. Note that in the current implementation, we normalize over the last dimension, which is the channel/embedding dimension of the input.

+   - RMSNorm (Lines 19–28):
+     – __init__ (Lines 20–23): Initializes the layer. In contrast to LayerNorm, we only initialize the scaling parameter gamma.
+     – forward (Lines 25–28): Implements the root-mean-square normalization formulation in Equation 11.2. Similar to the above LayerNorm implementation, we also normalize over the channel/embedding dimension of the input.

# # 11.4 Positional Encoding and Embedding

# ## 11.4.1 Sinusoidal Positional Encoding

In the original transformer paper [Vaswani et al., 2017], the authors used position encodings added on top of the input embedding vectors of each word token to allow the attention model to disambiguate words from different positions along the sequence. Specifically, given a sequence of word tokens, the transformer model looks up the corresponding embeddings of each vector and then forms a tensor of shape (`batch_size`, `seq_len`, `emb_size`). Then, for each sequence position by embedding position, an encoding value is added based on the formulation:

```
PE_{(p,2i)} = sin (p/(10000^{2i/d_{model}}))
PE_{(p,2i+1)} = cos (p/(10000^{2i/d_{model}}))
(11.3)
```

where

+   - p is the position index starting from 0,