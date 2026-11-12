
![](img/f56761e6196132d5b74909d98468408f_211_0.png)

Fig. 2. The main components of MIP.

where \(\mathbf{W}_Q \in \mathbb{R}^{k \times d}\) and \(\mathbf{b}_Q \in \mathbb{R}^d\) are trainable parameters of the linear layer. As \(\mathbf{Q}_t\) contains both invariant and variant patterns, we further disentangle them by querying the invariant memory bank. To obtain invariant prompts, we multiply the query matrix \(\mathbf{Q}_t\) with the memory bank \(\mathbf{\Phi}\) to obtain an affinity matrix \(\mathbf{S}^t_I\), based on which the invariant prompt can be drawn from the memory bank in a self-attentive fashion. This process can be formulated as:

```
\(\mathbf{H}^t_I = \mathbf{S}^t_I \mathbf{\Phi}, \mathbf{S}^t_I = \text{softmax}(\mathbf{Q}_t \mathbf{\Phi}^\top), \tag{6}\)
```

where \(\mathbf{H}^t_I \in \mathbb{R}^{N \times d}\) is the computed invariant prompt. Similarly, the variant prompt can be extracted in an analogous process, with a minor modification:

```
\(\mathbf{H}^t_V = \mathbf{S}^t_V \mathbf{\Phi}, \mathbf{S}^t_V = \text{softmax}(-\mathbf{1} \cdot \mathbf{Q}_t \mathbf{\Phi}^\top), \tag{7}\)
```

where negation is applied before the softmax function, so as to flip the score distribution and assign higher weights to invariant patterns that are less relevant to the memory \(\mathbf{\Phi}\). As this is executed for all time steps, we can obtain a sequence of \(T\) prompts \(\{\mathbf{H}_I^1, \mathbf{H}_I^2, ..., \mathbf{H}_I^T\}\) and \(\{\mathbf{H}_V^1, \mathbf{H}_V^2, ..., \mathbf{H}_V^T\}\). By respectively concatenating invariant and variant prompts across time, we can obtain two prompt tensors \(\mathbf{H}_I, \mathbf{H}_V \in \mathbb{R}^{T \times N \times d}\) for subsequent computations.

## 4.2 Invariant Learning with Latent Intervention

As per our discussions earlier, the variant prompt \(\mathbf{H}_V\) is environment-dependent but unrelated to the label \(\mathbf{Y}\), and the invariant prompt \(\mathbf{H}_I\) is causally linked to \(\mathbf{Y}\). To distill \(\mathbf{H}_I\) from \(\mathbf{X}\), a common approach as described in Sect. 3.2 is to perform invariant learning with intervened raw data \(\tilde{\mathbf{X}}\). However, directly intervening the raw data is a less favorable option for urban flow prediction tasks due to the risk of introducing additional noises, while some workarounds [30, 32, 35] need to additionally parameterize and learn the underlying environments

```
**Algorithm 1.** INTERVENE($\mathbf{H}_V, r$)

1: **Input**: Variant prompt tensor $\mathbf{H}_V \in \mathbb{R}^{T \times N \times d}$, intervention rate $r$
2: **Output**: Intervened variant prompt $\hat{\mathbf{H}}_V \in \mathbb{R}^{T \times N \times d}$
3: $\hat{\mathbf{H}}_V \leftarrow \mathbf{H}_V$
4: **for** s=1,2,...,$\lfloor \frac{rN}{2} \rfloor$ **do**
5:   Randomly sample a node pair $(w, v)$ s.t. $w, v \in [1, N]$;
6:   Randomly select a time step pair $(i, j)$ s.t. $i, j \in [1, T]$;
7:   $\hat{\mathbf{H}}_V[i, w] \leftarrow \mathbf{H}_V[j, v]$, $\hat{\mathbf{H}}_V[j, v] \leftarrow \mathbf{H}_V[i, w]$;
8: **end for**
9: **return** $\hat{\mathbf{H}}_V$
```

in order to alter the raw data distribution. Also, when STGNNs are used as the predictor pred($\cdot$), multiple complex forward passes are required to optimize Eq.(4), which is computationally impractical considering the large spatial and temporal spans $N$ and $T$ in urban flow graphs.

### Latent Intervention Mechanism.

In this paper, we innovatively propose to generate spatial-temporal interventions in the latent space, which more effectively mimics the changes in the learnable patterns after possible distribution shifts within the input data. Specifically, given the extracted variant prompts $\mathbf{H}_V$, we exchange features in $\mathbf{H}_V$ between different nodes and time points with a predefined rate $r$. The details of the latent intervention mechanism are described in Algorithm 1. To be succinct, we simplify this process into the following:

\(\hat{\mathbf{H}}_V = \text{INTERVENE}(\mathbf{H}_V, r),\) (8)

where $\hat{\mathbf{H}}_V$ denotes the intervened variant prompts after $rN$ feature exchanges between nodes have taken place. Note that, the swap is not constrained to node features at the same time step, so as to account for the spatial-temporal fluctuations within the variant patterns. Also, by producing intervened variant prompts with representations learned from the original input data, the generated $\hat{\mathbf{H}}_V$ remains plausible and challenging for refining the invariant prompts $\hat{\mathbf{H}}_I$.

### Invariant Learning.

After obtaining the intervened variant prompts $\hat{\mathbf{H}}_V$, we are able to train the prompt extractor described in Sect. 4.1 via invariant learning, so as to distinguish the invariant and variant prompts. To achieve this, the invariant and the intervened variant prompts are concatenated and then input into a supplementary predictor pred($\cdot$) to generate predictions:

\(\tilde{\mathbf{Y}} = \text{pred}(\mathbf{H}_I || \hat{\mathbf{H}}_V, \mathbf{A}),\) (9)

where $||$ denotes tensor concatenation along the last dimension, \(\tilde{\mathbf{Y}} \in \mathbb{R}^{T \times N \times k}\) is the predicted urban flow at all locations and time steps. The choice of pred($\cdot$) is flexible with most STGNNs. Since pred($\cdot$) is only responsible for differentiating invariant and variant prompts and will be used for computing the final predictions, we adopt GWNet [33], a simple yet effective STGNN as pred($\cdot$). For training, we first define the loss for a single node $n$ at one time step $t$:

```
l(t, n) = \frac{1}{k} \sum_{k'=1}^k || \hat{\mathbf{Y}}[t, n, k'] - \mathbf{Y}[t, n, k'] ||,
```

based on which the invariant learning loss is defined:

```
\mathcal{L}_{inv} = \mathbb{E}_{(t,n)} l(t,n) + \lambda_1 Var_{(t,n)} l(t,n), t \in [1,T], n \in [1,N],
```

where the first and second terms respectively reduce the mean and variance of the prediction error across locations and time steps. More specifically, the first term ensures that pred(\cdot) is optimized towards correctly predicting the urban flow in different environments with \mathbf{H}_I, while the second term enforces that when the predictions are conditioned on \mathbf{H}_I, there are minimal performance fluctuations despite the presence of noisy signals from intervened variant prompts \mathbf{H}_V.

## 4.3 Urban Flow Prediction with Causal Graph Generation

Once the invariant features \mathbf{H}_I are extracted, a spatial-temporal backbone model is in place for producing the final predictions. In MIP, our backbone model consists of alternately stacked GNN layers and temporal Transformer layers, which take invariant prompts \mathbf{H}_I and adjacency matrix \mathbf{A} as its input. However, \mathbf{A} is normally constructed solely based on the physical distances between nodes. As a result, this can introduce biases during GNN's information propagation, because geographic proximity does not necessarily imply similar temporal patterns, especially in OOD scenarios. In this section, we introduce a memory-based approach for generating a causal graph as a supplement to \mathbf{A}, followed by details of the backbone STGNN.

### Causal Graph Generation.

To address the limitation of the geolocation graph that is purely distance-based, we introduce an auxiliary graph based on the semantic distance between causal node representations, which are constructed from highly invariant features from the memory bank \mathbf{\Phi}. This causal graph complements the geolocation-based graph, thus providing additional predictive signals. This memory bank-based causal graph is constructed as the following:

```
\tilde{\mathbf{A}} = \text{softmax}(\mathbf{E}_1 \mathbf{E}_2^\top), \mathbf{E}_1 = \mathbf{W}_A \mathbf{\Phi}, \mathbf{E}_2 = \mathbf{W}_B \mathbf{\Phi},
```

where \mathbf{W}_A, \mathbf{W}_B \in \mathbb{R}^{N \times M} are trainable projection matrices that map the M prototype vectors in the memory bank into N node representations \mathbf{E}_1 and \mathbf{E}_2. As the memory bank already encapsulates critical information about the urban flow, the newly developed causal adjacency matrix provides additional information propagation channels between nodes.

### GNN Layer.

The GNN layer is fed with both the geographical and causal adjacency matrices \mathbf{A}, \tilde{\mathbf{A}} and the invariant prompts \mathbf{H}_I to learn node representations with information propagation. Since the geographical adjacency matrix \mathbf{A} is symmetric and hardly captures the directed nature of interactions in urban flow data, we derive forward and backward transition matrices from \mathbf{A} through a bidirectional, degree-weighted random walk [17]:

```
\mathbf{P}_f = \mathbf{D}^{-1}\mathbf{A}, \mathbf{P}_b = (\mathbf{D}^\top)^{-1}\mathbf{A}^\top,
```
