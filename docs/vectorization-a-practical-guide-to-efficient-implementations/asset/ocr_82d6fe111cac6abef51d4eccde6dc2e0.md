```
# Layers
self.rope = RotaryPositionalEncoding(self.head_dim, 1024)
self.project_q = nn.Linear(emb_dim, emb_dim, bias=False)
self.project_k = nn.Linear(emb_dim, emb_dim, bias=False)
self.project_v = nn.Linear(emb_dim, emb_dim, bias=False)
self.project_o = nn.Linear(emb_dim, emb_dim, bias=False)

def attention(self, query, key, value, mask=None):
    # Apply rotary embeddings
    query = self.rope(query)
    key = self.rope(key)

    # Compute attention score
    scores = torch.matmul(
        query.permute(0, 2, 1, 3),
        key.permute(0, 2, 3, 1)
    )
    scores = scores / math.sqrt(self.emb_dim)

    # Masking
    if mask is not None:
        # true indicate the entries to keep
        mask = mask.unsqueeze(0).unsqueeze(0)
        scores += (1 - mask) * -1e9

    if self.causal:
        causal_mask = torch.triu(torch.ones(scores.shape[-2:]))
        scores += causal_mask.to(scores.device) * -1e9

    attn = F.softmax(scores, dim=-1)
    output = torch.matmul(attn, value.permute(0, 2, 1, 3))
    output = output.permute(0, 2, 1, 3)

    return output, attn

def forward(self, q, k, v, mask=None):
    # projecting each input
    x_q = self.project_q(q)
    x_k = self.project_k(k)
    x_v = self.project_v(v)

    # (batch_size, seq_len, emb_size)
    b, t, d = q.shape
    shape = (b, t, self.num_heads, self.head_dim)
    # reshaping ->
    # (batch_size, seq_len, num_heads, emb_size // num_heads)
    query = x_q.view(*shape)
    key = x_k.view(*shape)
    value = x_v.view(*shape)

    # Compute attention
    x_attn, attn_weight = self.attention(query, key, value, mask=mask)

    # Reshaping back to (batch_size, seq_len, emb_size)
```