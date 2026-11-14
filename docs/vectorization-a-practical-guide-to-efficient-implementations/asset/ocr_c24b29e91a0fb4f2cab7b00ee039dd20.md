![](bbox=[0.116, 0.112, 0.692, 0.265])

# Figure 11.4 Sinusoidal positional encoding from the original transformer paper.

+   - i is the index along the embedding dimension, i \in (0, 1, 2, ..., d_{model} // 2),
+   - d_{model} is the embedding size.

This is typically referred to as sinusoidal positional encoding since it utilizes sinusoidal waves parameterized by position along the sequence and embedding dimensions. The following code block shows how to implement sinusoidal positional encoding from the original paper using PyTorch:

```
```
import torch

def sinusoidal_positional_encoding_vaswani(emb_size, seq_len):
    position = torch.arange(seq_len)
    timescales = torch.pow(
        1 / 10000,
        2 * (torch.arange(emb_size) // 2) / emb_size,
    )
    angles = position.unsqueeze(1) * timescales.unsqueeze(0)
    out = torch.zeros((seq_len, emb_size))
    # Interleaving sin and cos along embedding dimension
    out[:, 0:2] = torch.sin(angles[:, 0:2])
    out[:, 1:2] = torch.cos(angles[:, 1:2])
    return out
```
```

+   - Lines 4–9 implement the term inside the sine and cosine function in Equation 11.3. This creates a sequence (e.g. time) by embedding a dimension matrix.
+   - Line 10 creates the output placeholder, initialized with zeros.
+   - Lines 12–13 assign the even position with sine values and odd positions with cosine values, respectively.

We can plot out the positional encoding given the embedding size of 256 and sequence length of 500, as shown in Figure 11.4.