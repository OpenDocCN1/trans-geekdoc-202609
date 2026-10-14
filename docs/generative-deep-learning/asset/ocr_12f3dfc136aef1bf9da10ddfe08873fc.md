The alpha gating parameters are learned by the network, to gradually blend in information from the vision data as training progresses.

![](bbox=[0.24, 0.14, 0.7, 0.52])

```
def gated_xattn_dense(
    y,  # input language features
    x,  # input visual features
    alpha_xattn, # xattn gating parameter - init at 0.
    alpha_dense, # ffw gating parameter - init at 0.
):
    """Applies a GATED XATTN-DENSE layer."""

    # 1. Gated Cross Attention
    y = y + tanh(alpha_xattn) * attention(q=y, kv=x)
    # 2. Gated Feed Forward (dense) Layer
    y = y + tanh(alpha_dense) * ffw(y)

    # Regular self-attention + FFW on language
    y = y + frozen_attention(q=y, kv=y)
    y = y + frozen_ffw(y)
    return y  # output visually informed language features
```

Figure 13-25. A Flamingo Language Model block, comprising a frozen language model layer from Chinchilla and a GATED XATTN-DENSE layer (source: Alayrac et al., 2022)