

## 3 Preliminary: Embedding-Based Pooling

When dealing with set-level representation learning on graphs, a widely used solution is **embedding-based pooling** [19]. In our problem, it computes the bag probability \(\theta(\mathcal{X}) \in [0, 1]\) in the following way:

\(\theta(\mathcal{X}) = \text{CLS}(\text{AGGR}(\{\alpha_i \cdot \text{MP}(v_i), v_i \in \mathcal{X}\}))\)

\(\alpha_i = \text{ATT}(v_i)\)

Here, \(\theta(\mathcal{X})\) consists of 4 functions: MP, CLS, ATT, and AGGR. MP consists of message-passing layer(s), and works as a node feature extractor. Attention module ATT computes the attention weight \(\alpha_i\) for node \(v_i\), which can be used to measure the instance contribution in the bag representation and interpret model predictions. The aggregator AGGR aggregates the attended instance embeddings to obtain a bag representation. The most common practice is **sum**, with alternative choices including **max** [23]. Finally, the bag embedding is processed by the classifier CLS, and a bag label is predicted. The selection of MP, CLS, ATT and AGGR jointly determines the implementation of a pooling method and its effectiveness and complexity.

## 4 Proposed Method: Instance-Based Pooling

One inherent limitation of embedding-based pooling is its inability to train instances in the label space. For node-level MIL tasks, a natural assumption is that an effective pooling method should be capable of estimating instance probabilities during training. To achieve this, we do not require complex designs—simply swapping CLS and AGGR in embedding-based models suffices. We refer to the new model as **instance-based pooling**, which is formulated as follows:

\(\theta(\mathcal{X}) = \text{AGGR}(\{\text{CLS}(\alpha_i \cdot \text{MP}(v_i)), v_i \in \mathcal{X}\})\)

\(\alpha_i = \text{ATT}(v_i)\)

Different from embedding-based pooling, **CLS** learns the instance probability \(\theta(v_i)\) during training, which is then combined by **AGGR** to form the bag probability \(\theta(\mathcal{X})\). This allows the learning model to effectively accommodate both bag-level training and instance-level inference<sup>1</sup>. Similarly, the implementations of MP, ATT, CLS and AGGR are task-specific. Finally, an illustration of aforementioned two types of pooling paradigms is shown below in Fig. 2.

<sup>1</sup> Another alternative design of instance-based pooling follows the formulation \(\theta(\mathcal{X}) = \text{AGGR}(\alpha_i \cdot \{\text{CLS}(\text{MP}(v_i)), v_i \in \mathcal{X}\}), \alpha_i = \text{ATT}(v_i)\).

![](img/f56761e6196132d5b74909d98468408f_160_0.png)

Fig. 2. A comparison between embedding-based pooling (existing) and instance-based pooling (proposed). Embedding-based pooling: instance embedding - bag embedding - bag probability; instance-based pooling: instance embedding - instance probability - bag probability.

## 5 Key Theoretical Properties of Pooling Models

In this section, we first prove that the transformation from embedding-based pooling to instance-based pooling does not compromise the original model's permutation invariance (Sect.5.1) or expressive power (Sect.5.2), which are key properties of MIL models and graph neural networks, respectively. Finally, by investigating the relationship between instance probability and SHAP values (Sect.5.3), we demonstrate that instance-based models offer superior interpretability.

### 5.1 Permutation-Invariance

The standard MIL assumption (please refer to Eq. (1)) suggests that neither the ordering nor the dependency of instances within a bag exists. Therefore, when computing the bag probability \(\theta(\mathcal{X})\), for any permutation \(\pi\), we should have \(\theta(\{v_1, v_2, ..., v_m\}) = \theta(\{v_{\pi(1)}, v_{\pi(2)}, ..., v_{\pi(m)}\})\). Such property is referred to as *permutation-invariance*. To verify whether the pooling models possess this property, we first introduce the following Fundamental Theorem of Symmetric Functions with monomials [11,30]:

> **Theorem 1.** *A function F(X) operating on a countable set X is invariant to the permutation of instances in X if and only if it can be decomposed in the form* \(\rho(\sum_{v_i \in \mathcal{X}} \psi(v_i))\)*, where* \(\rho\) *and* \(\psi\) *are suitable transformations.*

Theorem 1 introduces a general form of functions that satisfy the property of permutation invariance. Based on it, we make the following corollary:

**Corollary 1.** *When AGGR is the summation operator, both embedding-based pooling and instance-based pooling are invariant to permutation.*

Proof. The set function \(F(\mathcal{X})\) in Theorem 1 is the bag probability \(\theta(\mathcal{X})\). For embedding-based pooling, when sum is the aggregator, transformation \(\psi\) and \(\rho\) corresponds to \(\alpha_i \cdot \text{MP}(v_i)\) and CLS, respectively. For instance-based pooling, \(\psi\) is the instance probability \(\text{CLS}(\alpha_i \cdot \text{MP}(v_i))\), and \(\rho\) is the identity function.

### 5.2 Expressiveness

The expressive power of a GNN refer to its ability to encode and process feature information on the graph as well as graph structure information, e.g., the ability to distinguish non-isomorphic graphs [31]. In graph theory, the Weisfeiler-Leman test (WL test) is a classic heuristic method to judge whether two graphs are isomorphic [16]. We prove below that when certain conditions are satisfied, both embedding-based pooling and instance-based pooling are capable of retaining distinct information in the graph. To begin, we first state the following theorem concerning the expressive power of graph pooling operators [1]:

**Theorem 2.** *For WL-distinguishable graphs, a graph pooler satisfying the following conditions will produce coarsened graphs that remain WL-distinguishable: (1) the message-passing layers compute different sums of node features; (2) the cluster assignment matrix is right-stochastic up to a constant* \(\lambda\); *(3) the features of supernodes are convex combinations of the input node features.*

We assume that the pooling models discussed in Sect. 3 and Sect. 4 satisfy the above properties. Note that in this case, MP is implied to be powerful, and AGGR is implied to be the summation operator. We prove below that, under additional constraints on CLS, both instance-based pooling and embedding-based pooling preserve the expressive power of MP:

**Corollary 2.** *Let* \(\mathcal{X}^1\) *and* \(\mathcal{X}^2\) *denote two WL-distinguishable bags, the pooled bags* \(\hat{\mathcal{X}}^1\) *and* \(\hat{\mathcal{X}}^2\) *generated by an instance-based model remain WL-distinguishable if the following additional conditions hold: (4) CLS is an additive function; (5) CLS is an injective function.*

Proof. Suppose that \(\mathcal{X}^1/\mathcal{X}^2\) contains *m* nodes, while \(\hat{\mathcal{X}}^1/\hat{\mathcal{X}}^2\) contains *l* supernodes (*l < m*). Let \(\mathcal{U}^1, \mathcal{U}^2, \hat{\mathcal{U}}^1\) and \(\hat{\mathcal{U}}^2\) denote the corresponding node embedding/probability matrix of \(\mathcal{X}^1, \mathcal{X}^2, \hat{\mathcal{X}}^1\) and \(\hat{\mathcal{X}}^2\), respectively. Here, \(\mathcal{U}^1\) and \(\mathcal{U}^2\) are computed by MP. Given condition 1, we have:

\(\sum_{i=1}^m \mathcal{U}_i^1 \neq \sum_{i=1}^m \mathcal{U}_i^2 \quad \text{(6)}\)

Here, \(\mathcal{U}_i^1\) and \(\mathcal{U}_i^2\) denote the \(i\)-th row of \(\mathcal{U}^1\) and \(\mathcal{U}^2\) respectively, which correspond to the vector of the \(i\)-th instance in the bag. Suppose that \(\hat{\mathcal{X}}^1\) and \(\hat{\mathcal{X}}^2\) are not WL-distinguishable. Then, there exists a one-to-one mapping \(\omega\) from \(\{1, 2, ..., l\}\) to \(\{1, 2, ..., l\}\) such that:

\(\hat{\mathcal{U}}_j^1 = \hat{\mathcal{U}}_{\omega(j)}^2, \forall j = 1, 2, ..., l \tag{7}\)

Let \(\mathcal{M} \in \mathbb{R}^{m \times l}\) denote the assignment matrix, where \(\mathcal{M}_{ij}\) represents the weight that assigns a node \(i\) to a supernode \(j\). Given condition 3, we have:

\(\sum_{i=1}^m \text{CLS}(\mathcal{U}_i^1 \cdot \mathcal{M}_{ij}^1) = \sum_{i=1}^m \text{CLS}(\mathcal{U}_i^2 \cdot \mathcal{M}_{i\omega(j)}^2), \forall j = 1, 2, ..., l \tag{8}\)

Given condition 4, we can swap CLS with the summation operator as:

\(\text{CLS}(\sum_{i=1}^m \mathcal{U}_i^1 \cdot \mathcal{M}_{ij}^1) = \text{CLS}(\sum_{i=1}^m \mathcal{U}_i^2 \cdot \mathcal{M}_{i\omega(j)}^2), \forall j = 1, 2, ..., l \tag{9}\)

Given condition 5, we have:

\(\sum_{i=1}^m \mathcal{U}_i^1 \cdot \mathcal{M}_{ij}^1 = \sum_{i=1}^m \mathcal{U}_i^2 \cdot \mathcal{M}_{i\omega(j)}^2, \forall j = 1, 2, ..., l \tag{10}\)

We sum the vectors of all supernodes:

\(\sum_{j=1}^l \sum_{i=1}^m \mathcal{U}_i^1 \cdot \mathcal{M}_{ij}^1 = \sum_{j=1}^l \sum_{i=1}^m \mathcal{U}_i^2 \cdot \mathcal{M}_{i\omega(j)}^2 \tag{11}\)

which can be rewritten as:

\(\sum_{i=1}^m \mathcal{U}_i^1 \cdot \sum_{j=1}^l \mathcal{M}_{ij}^1 = \sum_{i=1}^m \mathcal{U}_i^2 \cdot \sum_{j=1}^l \mathcal{M}_{i\omega(j)}^2 \tag{12}\)

Since \(\sum_{j=1}^l \mathcal{M}_{ij}^1 = \sum_{j=1}^l \mathcal{M}_{i\omega(j)}^2 = \lambda, \forall i = 1, 2, ..., m\) (Cond. 2). We have:

\(\sum_{i=1}^m \mathcal{U}_i^1 = \sum_{i=1}^m \mathcal{U}_i^2 \tag{13}\)

Notice that the above equation contradicts Eq. (6). Therefore, \(\hat{\mathcal{X}}^1\) and \(\hat{\mathcal{X}}^2\) remain WL-distinguishable.

For embedding-based models, note that Eq. (9) can be directly derived from Eq. (7). That means, it is not necessary to assume the additivity of CLS function to generate WL-distinguishable coarsened bags, while the remaining four conditions are required to hold.

