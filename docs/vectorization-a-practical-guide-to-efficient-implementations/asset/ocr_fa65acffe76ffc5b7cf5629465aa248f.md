```
x_attn = x_attn.reshape(b, t, d)

# Final projection layer
x_attn = self.project_o(x_attn)

return x_attn, attn_weight


class DecoderBlock(nn.Module):
    def __init__(self, self, emb_dim, ffn_size, num_heads=4, causal=False):
        super().__init__()
        self.mhattn = RoPEMultiHeadedAttention(
            emb_dim=embed_dim,
            num_heads=num_heads,
            causal=causal,
        )
        self.ffn = FFNSwiGLU(embed_dim, ffn_size)
        self.input_ln = RMSNorm(embed_dim)
        self.ffn_ln = RMSNorm(embed_dim)

    def forward(self, x):
        y = self.input_ln(x)
        Y, _ = self.mhattn(y, y, y)
        y += x

        z = self.ffn_ln(y)
        z = self.ffn(z)
        z += y

        return z


class TransformerPlusPlus(nn.Module):
    def __init__(self, self, n_layers):
        super().__init__()
        self.embed = nn.Embedding(vocab_size+1, embed_dim, padding_idx=0)
        self.encoder = nn.ModuleList([
            DecoderBlock(embed_dim, ffn_size, num_heads, causal=True)
            for _ in range(n_layers)
        ])
        self.final_ln = RMSNorm(embed_dim)
        self.output_layer = nn.Linear(embed_dim, vocab_size)

    def forward(self, tokens):
        # (batch_size, seq_len, emb_size)
        x = self.embed(tokens)
        # passing through encoder layers
        for enc in self.encoder:
            x = enc(x)

        # Final layer normalization
        x = self.final_ln(x)

        # output layer
```