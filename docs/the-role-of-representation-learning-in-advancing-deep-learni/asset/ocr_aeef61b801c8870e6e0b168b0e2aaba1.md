```
27    return self.transformer(obs)[:, -1, :]
28
29
30 class Transformer(nn.Module):
31     def __init__(self, embedding_dim, data_dim, nhead, num_layers,
32                 dim_feedforward, dropout=0.1):
33         super(Transformer, self).__init__()
34         self.embedding_dim = embedding_dim
35         self.data_dim = data_dim
36
37         self.lin = nn.Linear(data_dim, embedding_dim)
38
39         encoder_layers = TransformerEncoderLayer(
40             d_model=self.embedding_dim,
41             nhead=nhead,
42             dim_feedforward=dim_feedforward,
43             dropout=dropout,
44             batch_first=True
45         )
46
47         self.transformer_encoder = TransformerEncoder(encoder_layers,
48                                            num_layers)
49
50     def forward(self, x):
51         # x is of shape (batch_size, seq_length, embedding_dim)
52         x = self.lin(x)
53         transformed = self.transformer_encoder(x)
54         return transformed
55
56
57 if __name__ == "__main__":
58     policy_kwargs = dict(
59         features_extractor_class=TransformerFeaturesExtractor,
60         features_extractor_kwargs=dict(embedding_dim=args.
61         transformer_embedding_dim,
62         nhead=args.transformer_nhead,
63         num_layers=args.transformer_num_layers,
64         dim_feedforward=args.
65         transformer_ff_dim,
66         dropout=args.transformer_dropout,
67         data_dim=data_dims[args.puzzle]))
68
69 model = PPO("MultiInputPolicy",
70             env,
71             policy_kwargs=policy_kwargs,
72             )

```

Listing E.4: Code example of a transformer-based feature extractor written in PyTorch, compatible with Stable Baselines 3's PPO. This encoder design allows for variable-length inputs, enabling generalization to previously unseen puzzle sizes.

# ## E.2 Environment Features

# ### E.2.1 Episode Definition

An episode is played with the intention of solving a given puzzle. The episode begins with a newly generated puzzle and terminates in one of two states.