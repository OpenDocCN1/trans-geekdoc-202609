![](bbox=[0.14, 0.1, 0.88, 0.36])

Figure 11.8 Corresponding values in R and X to be multiplied. Suppose we have an embedding size of 12 and a sequence length of 4. The R tensor (a) should have the shape 4 x 12 x 12, and the sequence input tensor X (b) should have the shape 4 x 12. Due to the sparsity nature of the matrix R (a block diagonal matrix), the only effective multiplication is between the corresponding upper left corner regions in R (the upper left corner 4-grid square block) and X (the first two grids in the first row). In this example, the first block in R is multiplying together with the first pair in X, at the corresponding sequence position.

Notice that this is the same as representing the right-hand side column vector in Equation 11.6 (as the result of the multiplication) as a complex value.

This means if we represent the diagonial block as a vector of complex numbers and convert each pair of embedding values into a complex number as well, then we can simply do an element-wise product between the transformed vectors and then recover the result by converting the complex results back into a pair of numbers along the embedding dimension. Therefore, we can implement the following two functions which we can use to apply the rotary positional encoding on an input of shape (batch_size, seq_len, ..., emb_size), where the elided dimension can be the additional num_heads dimension depending on the specific settings of the attention mechanism.

```
import torch

def create_phi(emb_size, seq_len):
    pos = torch.arange(seq_len).unsqueeze(1)
    depths = torch.arange(emb_size//2).unsqueeze(0)
    theta = 10000**(-2*depths/emb_size)
    # (seq_len, emb_size // 2)
    p_theta = theta * pos
    # cos (p_theta) + sin (p_theta) j
```