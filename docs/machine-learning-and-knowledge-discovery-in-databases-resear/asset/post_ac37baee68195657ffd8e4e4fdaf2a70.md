
![](img/f56761e6196132d5b74909d98468408f_493_0.png)

Fig. 4. The result after pruning the probabilistic circuit from Fig. 1a, with the generative significance method set to eliminate the five nodes with the lowest top down probabilities (shown in blue). (Color figure online)

```
Algorithm 1. Step 2: Pruning input nodes in PC
Require: Pruned PC M', high-probability examples E_HPR, examples E
Ensure: M' with pruned input nodes
1: lower_bound = F_1(E_M', E_HPR)
2: repeat
3: for each input node n in M' do
4: M'' <- M' / n  <| Prunes node n
5: if F_1(E_M'', E_HPR) >= lower_bound then
6: M' <- M''
7: until M' has not changed
8: return M'
```

the circuit output. In Fig. 4 we show its application on the circuit of Fig. 1a, annotating each node by its top down probability, i.e., the probability that the node will be visited when unconditionally drawing samples from the circuit. This function is parameterised by the number of edges it must eliminate. The fourth approach is based on circuit flows, which works similar to the third approach but it first adjusts the sum node mixture weights by conditioning on a given dataset. In this way, it considers how many samples from the dataset flow through each node. This pruning function is parameterised by the number of edges it must eliminate and the dataset on which to condition.

Applying Pruning Functions. PUTPUT first identifies the preferred values of the parameters (i.e., the number of edges to eliminate) of the pruning function that lead to the highest F1-score (Eq. 1). This can be achieved exhaustively or by using a search function such as golden section search [25]. We used the latter in our evaluation to conclude that pruning based on circuit flows is the preferred pruning function. The result of step 1 is a pruned probabilistic circuit such that the F1-score is maximised (see Fig. 4).

### 5.2 Step 2: Pruning Input Nodes

The first step already decreases the aggregated entropy due to its correlation with circuit size. The second step decreases this even further by considering for each input node whether it is beneficial to prune them. While the first step prunes some sum node inputs, the second step prunes them further and in addition also prunes input nodes that lead into product nodes.

The F1-score resulting from the first step is used as a lower bound in this second step. Pruning children of a product node may influence whether it is beneficial to prune a node that was previously considered. PUTPUT therefore employs an iterative procedure that reconsiders all input nodes until no more changes are made. The pseudocode for this step is shown in Algorithm 1. The circuit resulting from step 1 is denoted as M', while E_M' are the examples e ∈ E for which P'_M'(e) > 0, as these are the examples covered by the logical formula derived from M' (see Section 2.2). Note that probability threshold t is implicitly present in E_HPR. If we apply this second step on Fig. 4, we obtain Fig. 5.

![](img/f56761e6196132d5b74909d98468408f_494_0.png)

Fig. 5. The circuit after applying step 2 of PUTPUT, with E_HPR = {(s1,m1,v1),(s1,m1,v2),(s1,m2,v1)}.

## 6 Evaluation

The proposed PUTPUT method is empirically evaluated to answer the following research questions:

- 1. Which pruning function results in the highest F1-score (step 1)?
- 2. Does pruning of the input nodes improve the aggregated entropy (step 2)?
- 3. How does PUTPUT perform more generally, including on the music playlist generation task?

### 6.1 Setup

Given a dataset of positive and unlabeled examples E, we first learn a probabilistic circuit M using the Hidden Chow Liu Tree method [18] available in the JUICE package [10]. Next, we find the probability threshold t that identifies the high probability regions. A higher threshold t leads to a smaller, more precise region. However, if the threshold t is too high, the resulting formula will overfit, leading to lower recall and thus reduced F1-score. The user's choice of t, which dictates the trade-off, is therefore important. As this depends on a specific use case, we instead determine an appropriate value for t through a more generalized approach, using the elbow method on the generated posterior probabilities, which is inspired by work on finding the reject threshold in pattern recognition [7].

The elbow method selects a probability threshold t by first ordering all examples based on their probability, in descending order. More formally, we use E to denote a set of examples, M to denote a probabilistic circuit, and p(e) to denote the probability of e ∈ E according to M. Let L = [e1, ..., en] be the examples in E, ordered according to probability p(e), such that e1 has the highest probability and en the lowest. The elbow method then finds threshold t by searching for a sudden sharper decrease in probability. I.e., find example ei such that

```
i = \arg \min_{x=1..|\mathcal{E}|} (x \mid \frac{p(e_{x+1}) - p(e_x)}{p(e_x) - p(e_{x-1})} \ge 0.3), (8)
```

after which the threshold is defined as t = p(ei). The value of 0.3 in the elbow method is a user-specified parameter. We decided this value by analysing the results of the music use case in collaboration with a music expert of Tunify. Since there is no expert for the open-source datasets, we reuse the same threshold t throughout the experiments (Fig. 6).

![](img/f56761e6196132d5b74909d98468408f_495_0.png)

Fig. 6. The elbow method selects threshold t, identifying high probability regions.

Using this threshold t, we determine the high probability region examples E_HPR ⊆ E. Afterwards, we apply PUTPUT to prune M, leading to the discriminative formula ψ.

### 6.2 Datasets

- Tunify provided real-world data, 360 000 songs, annotated with 14 categorical features having 7 to 120 possible values, and a set of intended playlist concepts. From this private data 15 classes were constructed, each representing a different playlist concept that has to be learned. We consider two types of concepts, based on the playlists used by customers from Tunify.
  - Single playlist concept: 5 known product playlist concepts with their respective songs, e.g., Rock.
  - Disjunctive playlist concepts: 10 combinations of two known concepts that have a disjunctive form, e.g., Rock or Easy Lounge.
- the FMA music dataset [12] used for genre classification (8 classes, 9217 examples), which is the open source dataset that is most similar to the Tunify dataset.
- black and white images of:
  - MNIST (10 classes, 2500 examples) [13],
  - fashionMNIST (10 classes, 2500 examples) [36],
  - EMNIST letters (26 classes, 2600 examples) [8].
- the mushrooms (2 classes, 8124 examples) [31] and splice (3 classes, 3190 examples) [32] datasets of the UCI machine learning repository.

Setup. A class in a dataset determines the positive labels. We consider a PU learning setting wherein most of the examples are unlabeled. More specifically, for each class in each dataset, we create 10 subsets of the data and randomly label only 5% of the positively labeled examples, resulting in 740 PUTPUT datasets. We evaluate on the full dataset.

Example. We provide a small example to motivate our goal of extracting a discriminative classifier, and to illustrate the general applicability beyond music playlist generation. We learned a probabilistic circuit on black and white images of MNIST data containing 13 positively labeled examples representing the digit 0. We then applied PUTPUT to obtain the following logical formula $\psi$ with ($W=$White, $B=$Black).

```
$p_{12,22}=W\wedge p_{14,15}=B\wedge p_{14,16}=B\wedge(p_{8,15}=W\vee p_{8,17}=W)\wedge(p_{15,9}=W\vee p_{13,12}=B)$
```

Apparently, the high probability region of the learned probabilistic circuit only considers seven of the 784 pixels to predict whether an MNIST digit depicts a 0. Figure 7 shows two MNIST digits that match $\psi$ and are part of the high probability regions of the probabilistic circuit. The latter can be verified by evaluating the probabilistic circuit for the given image. In addition to being more interpretable, the domain expert can also use description $\psi$ as a starting point to further refine their intended concept.

### 6.3 Experiments

Experiment 1: Comparing Pruning Methods. To address research question 1, we evaluate the first step of PUTPUT with the two previously described pruning functions on the open-source benchmarks. Table 1 indicates that pruning by circuit flows results in the best average F1-score and circuit size, the latter of which likely leads to a decreased aggregated entropy. In the following experiments, we therefore use pruning by circuit flows.
