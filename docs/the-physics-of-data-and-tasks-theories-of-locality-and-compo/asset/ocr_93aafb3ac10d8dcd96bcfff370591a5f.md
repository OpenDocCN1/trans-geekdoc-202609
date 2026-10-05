| Symbol | Definition |
| --- | --- |
| $\chi(t)$ | The dynamical susceptibility, measuring the total volume of correlated changes. |
| $\xi$ | The correlation length of token changes. |

# Task Compositionality & Model Editing

| Symbol | Definition |
| --- | --- |
| $	heta_0$ | The parameters of a pre-trained model before fine-tuning. |
| $	heta_t^i$ | The parameters of a model after fine-tuning on task $t$. |
| $	au_t$ | The task vector for task $t$, defined as the difference in weights: $	au_t = 	heta_t^i - 	heta_0$. |
| $\mathcal{D}_t$ | The data support (the subset of the input space) for a specific task $t$. |
| $f_{lin}$ | The linearized version of a neural network function, based on its first-order Taylor expansion around $	heta_0$. |
| $	ilde{\zeta}(a_1, a_2)$ | The disentanglement error, measuring the interference between two tasks when their task vectors are combined. |