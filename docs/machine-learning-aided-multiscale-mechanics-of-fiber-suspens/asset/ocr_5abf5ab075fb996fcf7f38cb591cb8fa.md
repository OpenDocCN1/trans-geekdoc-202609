through the whole DMN, which is undesirable for the offline training. Once the parameter vectors $\underline{n}$ and $\underline{w}$ are known, they remain unchanged and are used in the *online evaluation* to predict the non-linear response of the studied material. In sections 5.3.4, 5.4.2, and 5.3.5, we discuss the offline training and the online evaluation for the proposed FDMN architecture.

# 5.3.2 Architecture of flexible deep material networks

With the results of the previous sections 5.2.1-5.2.3 at hand, we present an extended DMN architecture that is able to treat fluid phases and infinite material contrast. Compared to the architecture of (direct) DMNs shown in Figure 5.2, the lowest layer of laminates is replaced by a layer of rank-$R$ CLMs $\mathcal{C}_R$, see Figure 5.3. The rank $R$ of the CLM $\mathcal{C}_R$ and the

![](bbox=[0.15, 0.48, 0.9, 0.69])

Figure 5.3: Weight and material property propagation (from the bottom to the top) in a two-phase FDMN (Gajek et al., 2021) of depth $K = 3$ with rank-3 CLMs. Figure adapted from Sterr et al. (2024a, Figure 3).

restrictions on its layering directions $\boldsymbol{n}_r$ are problem dependent, and chosen such that the non-singularity condition (A.11) is satisfied. This guarantees that only non-singular material tensors $\mathbb{A}^i_k$ are propagated