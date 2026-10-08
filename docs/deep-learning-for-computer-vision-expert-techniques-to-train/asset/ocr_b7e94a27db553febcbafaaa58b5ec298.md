# Using RNN for captioning

Donahue et al., in the paper https://arxiv.org/pdf/1411.4389.pdf, proposed Long-term recurrent convolutional architectures (LRCN) for the task of image captioning. The architecture of this model is shown here:

| Input | Visual Features | Sequence Learning | |
|---|---|---||
| ![image] | CNN | LSTM | $y_1$ |
| ![image] | CNN | LSTM | $y_2$ |
| ... | ... | ... | ... |
| ![image] | CNN | LSTM | $y_T$ |

Both the CNN and LSTM is shown in the figure share weights across time, which makes this method scalable to arbitrarily long sequences.