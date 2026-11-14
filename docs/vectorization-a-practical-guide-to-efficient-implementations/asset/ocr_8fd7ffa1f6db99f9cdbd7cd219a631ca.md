+   - Line 25: We slice the sequence dimension of phi such that phi and x have identical sequence lengths. In practice, it is possible that x can have variable size sequence lengths over different training or inference batches, we would need to precompute the matrix phi with an expected maximum sequence length for inference.

+   - Lines 26-29: This determines the broadcasting shape of the matrix phi. We would like to insert some singleton dimensions for batches, and optionally, the num_heads dimension (which may or may not exist depending on how we formulate attention).

+   - Line 30 applies the reshaping so that the singleton dimensions for broadcasting are inserted.

+   - Line 32: We first perform element-wise multiplication between the two complex matrices (with additional broadcasting). Then, we convert the complex-valued results back into real-value tensor, resulting in a shape of (batch_size, seq_len, <num_heads>, emb_size // 2, 2).

+   - Line 34: This reshapes the last two dimensions of the above tensor, giving back a result of shape (batch_size, seq_len, <num_heads>, emb_size).

# 11.5 Activation Functions in Feedforward Layer

Recall in Chapter 9, when we were implementing the Vision Transformer model, we implemented the feedforward layer that follows the multiheaded attention layer as

```
self.ffn = nn.Sequential(
    nn.Linear(embed_dim, ffn_size),
    nn.GELU(),
    nn.Dropout(dropout),
    nn.Linear(ffn_size, embed_dim),
)
```

Here, nn.GELU() is an activation function applied to the first dense layer of the feedforward layer. This is an improvement on top of the original transformer paper, which used a simple rectified linear unit (ReLU) activation function, and did not add a dropout layer before the second dense layer. Subsequent studies have, therefore, attempted to use more sophisticated activation functions to capture the nonlinearity in the feedforward layer. Specifically, a family of linear unit-based activation functions seemed to have various degrees of success, including but not limited to exponential linear unit (ELU) [Clevert et al., 2016],