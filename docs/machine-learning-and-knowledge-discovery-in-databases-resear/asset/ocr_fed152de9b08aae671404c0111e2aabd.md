```
**Algorithm 1.** INTERVENE($\mathbf{H}_V, r$)

1: **Input**: Variant prompt tensor $\mathbf{H}_V \in \mathbb{R}^{T \times N \times d}$, intervention rate $r$
2: **Output**: Intervened variant prompt $\hat{\mathbf{H}}_V \in \mathbb{R}^{T \times N \times d}$
3: $\hat{\mathbf{H}}_V \leftarrow \mathbf{H}_V$
4: **for** s=1,2,...,$\lfloor \frac{sN}{2} \rfloor$ **do**
5:   Randomly sample a node pair $(w, v)$ s.t. $w, v \in [1, N]$;
6:   Randomly select a time step pair $(i, j)$ s.t. $i, j \in [1, T]$;
7:   $\hat{\mathbf{H}}_V[i, w] \leftarrow \mathbf{H}_V[j, v]$, $\hat{\mathbf{H}}_V[j, v] \leftarrow \mathbf{H}_V[i, w]$;
8: **end for**
9: **return** $\hat{\mathbf{H}}_V$
```

in order to alter the raw data distribution. Also, when STGNNs are used as the predictor pred($\cdot$), multiple complex forward passes are required to optimize Eq.(4), which is computationally impractical considering the large spatial and temporal spans $N$ and $T$ in urban flow graphs.

**Latent Intervention Mechanism.** In this paper, we innovatively propose to generate spatial-temporal interventions in the latent space, which more effectively mimics the changes in the learnable patterns after possible distribution shifts within the input data. Specifically, given the extracted variant prompts $\mathbf{H}_V$, we exchange features in $\mathbf{H}_V$ between different nodes and time points with a predefined rate $r$. The details of the latent intervention mechanism are described in Algorithm 1. To be succinct, we simplify this process into the following:

\(\hat{\mathbf{H}}_V = \text{INTERVENE}(\mathbf{H}_V, r),\) (8)

where $\hat{\mathbf{H}}_V$ denotes the intervened variant prompts after $rN$ feature exchanges between nodes have taken place. Note that, the swap is not constrained to node features at the same time step, so as to account for the spatial-temporal fluctuations within the variant patterns. Also, by producing intervened variant prompts with representations learned from the original input data, the generated $\hat{\mathbf{H}}_V$ remains plausible and challenging for refining the invariant prompts $\hat{\mathbf{H}}_I$.

**Invariant Learning.** After obtaining the intervened variant prompts $\hat{\mathbf{H}}_V$, we are able to train the prompt extractor described in Sect. 4.1 via invariant learning, so as to distinguish the invariant and variant prompts. To achieve this, the invariant and the intervened variant prompts are concatenated and then input into a supplementary predictor pred($\cdot$) to generate predictions:

\(\tilde{\mathbf{Y}} = \text{pred}(\mathbf{H}_I || \hat{\mathbf{H}}_V, \mathbf{A}),\) (9)

where $||$ denotes tensor concatenation along the last dimension, \(\tilde{\mathbf{Y}} \in \mathbb{R}^{T \times N \times k}\) is the predicted urban flow at all locations and time steps. The choice of pred($\cdot$) is flexible with most STGNNs. Since pred($\cdot$) is only responsible for differentiating invariant and variant prompts and will be used for computing the final predictions, we adopt GWNet [33], a simple yet effective STGNN as pred($\cdot$). For training, we first define the loss for a single node $n$ at one time step $t$: