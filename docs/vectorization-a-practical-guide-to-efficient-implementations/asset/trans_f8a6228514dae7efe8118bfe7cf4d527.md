

## Layers

```
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
x_attn = x_attn.reshape(b, t, d)

# Final projection layer
x_attn = self.project_o(x_attn)

return x_attn, attn_weight


class DecoderBlock(nn.Module):
    def __init__(self, emb_dim, ffn_size, num_heads=4, causal=False):
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
        y, _ = self.mhattn(y, y, y)
        y += x

        z = self.ffn_ln(y)
        z = self.ffn(z)
        z += y

        return z


class TransformerPlusPlus(nn.Module):
    def __init__(self, n_layers):
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
213 logits = self.output_layer(x[:, -1, :])
214 return logits
215
```

-RMSNorm (第 6–16 行)：实现 RMSNorm 层。这只是之前实现的副本，未做任何修改。

-RotaryPositionalEncoding (第 19–74 行)：将之前实现的两个函数 create_phi 和 apply_rotary_position_encoding 作为模块的一部分。

-The __init__ 方法 (第 21–24 行)：调用 create_phi 静态方法来预先计算 phi 矩阵。

-The forward 方法 (第 73–74 行)：调用 apply_rotary_position_encoding 方法。

-apply_rotary_position_encoding 方法的第 58–68 行：这是为在 Apple Silicon 设备（“MPS”）上训练而设的变通方法，因为在这些设备上未实现两个复杂张量之间的乘法。相反，我们根据公式 11.9 实现了一个子程序 complex_multiply_to_real (第 58–65 行) 来替换第 67 行 torch.view_as_real (x * phi)。另请参阅 PyTorch GitHub 问题 #105665 [Paszke et al., 2023]。

-FFNSwiGLU (第 77–93 行)：这是第 11.1.2 节中 SwiGLU 激活前馈层之前实现的副本。

-RoPEMultiHeadedAttention (第 96–164 行)：这是带有 RoPE 以编码位置信息的注意力层。

-__init__ (第 98–106 行)：此方法初始化：

-旋转位置编码层 (第 106 行) 用于在计算注意力分数之前应用位置编码。

-query、key 和 value 的输入投影层 (第 107–109 行)。

-输出投影层 (第 110 行) 用于额外投影。

-attention (第 112–136 行)：此方法实现按公式 11.4 描述的缩放点积注意力逻辑。

-第 114 和 115 行将旋转位置编码添加到 query 和 key 中，两者形状均为 (batch_size, seq_len, num_heads, head_dim)，其中 num_heads * head_dim = emb_size。

-第 118–120 行通过执行 query 和 key 之间的点积来计算注意力分数。这会产生形状为 (batch_size, num_heads, query_seq_len, key_seq_len) 的张量。

-第 122 行通过 $\sqrt{d_{\text{model}}}$ 归一化分数。

-第 125–129 行将预定义掩码应用于注意力分数。这里的诀窍是向分数添加一个很大的负数以供忽略，这样在 softmax 激活后，分数将接近于零。

-第 130 和 131 行将因果掩码应用于注意力分数。它创建一个上三角掩码，用于指示分数的哪部分将被掩码。

-第 134 行使用 softmax 激活分数。

-第 135 行通过将注意力权重与 value 相乘来完成注意力公式。

-第 136 行重新排列索引，使输出形状为 (batch_size, seq_len, num_heads, head_dim)。

-forward (第 140-164 行)：此方法实现多头注意力层的主要逻辑。

-第 142-144 行对 query、key 和 value 执行一系列投影。

-第 147-148 行确定多头注意力输入的形状，即 (batch_size, seq_len, num_heads, head_dim)。

-第 151-153 行将上述形状应用于 query、key 和 value。

-第 156 行调用 attention 方法来计算注意力后的输出 x_attn，以及注意力分数 attn_weight。

-第 159 行：attention 方法的输出仍然具有形状 (batch_size, seq_len, num_heads, head_dim)，因此我们希望将输出重新整形为 batch_size, seq_len, emb_size，方法是将最后两个维度合并在一起。

-第 162 行对输出执行最终线性投影。

-DecoderBlock (第 167–188 行)：这是我们之前实现的 PreLNEncoderBlock 层的改编版本。

-__init__ (第 168–177 行)：DecoderBlock 层替换了以下组件：

-第 170-174 行：不再使用 PyTorch 原始的 nn.MultiHeadAttention 层，而是使用我们自己的 RoPEMultiHeadedAttention 作为注意力机制。请注意，我们通过设置 causal=True 使用因果注意力。在原始 Transformer 论文的术语中，这实际上是使用因果注意力的解码器层。因此，用于文本生成的 GPT 和 LLaMA 模型是仅解码器架构。

-第 175 行：不再使用我们之前使用 nn.Sequential 实现的带有 GELU 激活的两个前馈层，而是使用我们上面实现的 FFN-SwiGLU 前馈层。

-第 176–177 行：不再使用 nn.LayerNorm，而是使用我们上面实现的 RMSNorm。

-forward (第 179–188 行)：这与我们之前在 PreLNEncoderBlock 中的实现相同。

-TransformerPlusPlus (第 191–215 行)：此模块构建我们的最终 Transformer++（又称 LLaMA）模型。

-__init__ (第 193–200 行)：

-第 194 行：根据 `vocab_size` 和 `embed_dim` 初始化标记嵌入。这里，我们假设索引 0 用于填充。

-第 195–198 行：初始化一系列解码器块。

-第 199 行初始化一个最终 RMSNorm 层，该层将在 Transformer 块中调用。

-第 200 行初始化一个最终输出层，该层将隐藏状态投影为每个标记的 logit 值。

-forward (第 202–215 行)：

-第 204 行查找输入中每个标记的嵌入。

-第 206–207 行将标记序列的嵌入表示传递通过 Transformer 块。

-第 210 行通过 RMSNorm 添加最终层归一化。

-第 213 行通过线性投影计算词汇表中每个标记的 logit 值。在这里，我们使用序列的最后一个隐藏状态作为该层的输入，因为我们希望预测下一个标记。

我们可以通过 torchsummary 可视化模型结构。

```
# View model architecture
from torchsummary import summary
model = TransformerPlusPlus(
    n_layers=4, vocab_size=vocab_size, embed_dim=256, ffn_size=512, num_heads=4
)
summary(model)
```

结果如下

| 层 (类型:深度-索引) | 参数数量 |
| :--- | :--- |
| Embedding: 1-1 | 7,813,888 |
| ModuleList: 1-2 | -- |
| DecoderBlock: 2-1 | -- |
| RoPEMultiHeadedAttention: 3-1 | (294,912) |
| FFNSwiGLU: 3-2 | 393,216 |
| RMSNorm: 3-3 | 256 |
| RMSNorm: 3-4 | 256 |
| DecoderBlock: 2-2 | -- |
| RoPEMultiHeadedAttention: 3-5 | (294,912) |
| FFNSwiGLU: 3-6 | 393,216 |
| RMSNorm: 3-7 | 256 |
| RMSNorm: 3-8 | 256 |
| DecoderBlock: 2-3 | -- |
| RoPEMultiHeadedAttention: 3-9 | (294,912) |
| FFNSwiGLU: 3-10 | 393,216 |
| RMSNorm: 3-11 | 256 |
| RMSNorm: 3-12 | 256 |

