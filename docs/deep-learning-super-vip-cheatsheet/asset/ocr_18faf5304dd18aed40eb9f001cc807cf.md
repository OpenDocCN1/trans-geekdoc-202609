| Type of gate | Role | Used in |
|---|---|---|
| Update gate Γ_u | How much past should matter now? | GRU, LSTM |
| Relevance gate Γ_r | Drop previous information? | GRU, LSTM |
| Forget gate Γ_f | Erase a cell or not? | LSTM |
| Output gate Γ_o | How much to reveal of a cell? | LSTM |

GRU/LSTM – Gated Recurrent Unit (GRU) and Long Short-Term Memory units (LSTM) deal with the vanishing gradient problem encountered by traditional RNNs, with LSTM being a generalization of GRU. Below is a table summing up the characterizing equations of each architecture:

| | Gated Recurrent Unit (GRU) | Long Short-Term Memory (LSTM) |
|---|---|---|
| \tilde{c}^{<t>} | tanh(W_c[Γ_r * a^{<t-1>}, x^{<t>}] + b_c) | tanh(W_c[Γ_r * a^{<t-1>}, x^{<t>}] + b_c) |
| c^{<t>} | Γ_u * \tilde{c}^{<t>} + (1 - Γ_u) * c^{<t-1>} | Γ_u * \tilde{c}^{<t>} + Γ_f * c^{<t-1>} |
| a^{<t>} | c^{<t>} | Γ_o * c^{<t>} |
| Dependencies | [GRU dependency diagram] | [LSTM dependency diagram] |

> *Remark: the sign * denotes the element-wise multiplication between two vectors.*

Variants of RNNs – The table below sums up the other commonly used RNN architectures:

| Bidirectional (BRNN) | Deep (DRNN) |
|---|---|
| [Bidirectional RNN diagram with y^{<t>}, a^{<t>}, x^{<t>}] | [Deep RNN diagram with multiple layers] |

# 2.3 Learning word representation

In this section, we note V the vocabulary and |V| its size.

# 2.3.1 Motivation and notations

Representation techniques – The two main ways of representing words are summed up in the table below:

| 1-hot representation | Word embedding |
|---|---|
| [1-hot 3D diagram with book, soft, teddy bear] | [Word embedding 3D diagram with book, soft, teddy bear] |
| - Noted o_w
- Naive approach, no similarity information | - Noted e_w
- Takes into account words similarity |

Embedding matrix – For a given word w, the embedding matrix E is a matrix that maps its 1-hot representation o_w to its embedding e_w as follows:

```
e_w = E o_w
```

> *Remark: learning the embedding matrix can be done using target/context likelihood models.*

# 2.3.2 Word embeddings

Word2vec – Word2vec is a framework aimed at learning word embeddings by estimating the likelihood that a given word is surrounded by other words. Popular models include skip-gram, negative sampling and CBOW.

![](bbox=[0.51, 0.66, 0.95, 0.83])

Skip-gram – The skip-gram word2vec model is a supervised learning task that learns word embeddings by assessing the likelihood of any given target word t happening with a context word c. By noting θ_t a parameter associated with t, the probability P(t|c) is given by: