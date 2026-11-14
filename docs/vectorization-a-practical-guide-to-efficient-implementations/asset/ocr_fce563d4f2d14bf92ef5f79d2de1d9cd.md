```
10  phi = torch.polar(torch.ones_like(p_theta), p_theta)
11  return phi
12
13 def apply_rotary_position_encoding(phi, x):
14  """
15  Apply rotary positional encoding
16  """
17  x has (batch_size, seq_len, <num_heads>, emb_size)
18  phi has shape (max_seq_len, emb_size)
19  """
20  # (batch_size, ..., emb_size // 2, 2)
21  x = x.reshape(*x.shape[:-1], -1, 2)
22  # (batch_size, ..., emb_size // 2, 2), complex
23  x = torch.view_as_complex(x)
24  # Slice and reshape phi to match x
25  phi = phi[:, x.shape[1], :] # same length as x
26  broadcast_shape = [
27    d if ii == 1 or ii == x.ndim - 1 else 1
28    for ii, d in enumerate(x.shape)
29  ]
30  phi = phi.view(broadcast_shape)
31  # Multiply: (batch_size, ..., emb_size // 2, 2)
32  out = torch.view_as_real(x * phi)
33  # (batch_size, ..., emb_size)
34  out = out.flatten(out.ndim - 2)
35  return out
```

+   • create_phi (Lines 3-11): The function creates the (seq_len, emb_size) matrix of phi based on the formulation we have in Equation 11.7.

+   • apply_rotary_position_encoding (Lines 13-35): The function takes an input tensor of the shape (batch_size, seq_len, <num_heads>, emb_size) (where num_heads dimension may be optional) and the reformulated rotation phi (a (seq_len, emb_size) matrix) and apply the rotary positional encoding.

+   - Line 21: We first reshape the last dimension to create value pairs of the embeddings, converting the input tensor of shape (batch_size, seq_len, <num_heads>, emb_size) to (batch_size, seq_len, <num_heads>, emb_size // 2, 2), where the final dimension is a pair of embedding values.

+   - Line 23: Following the formulation in Equation 11.8, the torch.view_as_complex operation converts the pair of values along the last dimension into complex representations, resulting in a tensor of shape (batch_size, seq_len, <num_heads>, emb_size // 2).