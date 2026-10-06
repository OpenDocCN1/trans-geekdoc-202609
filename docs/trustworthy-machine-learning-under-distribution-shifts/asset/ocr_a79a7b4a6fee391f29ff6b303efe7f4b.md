# 3.2 ROBUST GENERALIZATION METHODS

learn invariant information without being influenced by the distribution shift between differ-ent environments.

**Risk Extrapolation (REx)** [144] targets at generalization to out-of-distribution (OOD) environments. Inspired by the discovery that penalizing the loss across distributions REx proposes to achieve improved performance on OOD generalization, to optimize via:

```
$$\min_{\theta\in\Theta} \mathcal{L}_{REx} := \sum_{v\in\mathcal{V}} \mathcal{L}^v(\theta) + \beta Var(\mathcal{L}^1,...,\mathcal{L}^m)$
```

where $eta$ controls the penalization level. Intuitively, REx seeks to achieve risk fairness among all $m$ training environments, so to increase the similarity of different learning tasks. As a result, the training model can capture the invariant information that helps generalize to unseen distributions.

**GroupDRO** [125, 145, 132] deal with the situation when the correlation between class label $y$ and unknown attribute $a$ differs in the training and test set. Such a difference is called spurious correlation, which could seriously mislead the model prediction. As a solution, GroupDRO considers each combination of attribute as a group $g$. By conducting risk minimization through:

```
$$\min_{\theta\in\Theta} \mathcal{L}_{GroupDRO} := \max_{g} \mathbb{E}_{(x,y)\sim P_g} [\mathcal{L}(\theta; (x, y))]$
```

The worst-case group from the distribution $P_g$, which commonly holds spurious correlation, is emphasized, breaking the spurious correlation.

**Discussion:** IRM and REx both focus on learning invariant knowledge across environments. However, when the training set contains extremely imbalanced noisy distributions, as shown in Figure 3.1, the invariant learning results would be greatly misled by the most dominating distribution. Thus, the extracted invariant feature would be questionable for generalization against distribution shift. Although emphasizing the risk minimization of worst-case data via GroupDRO can alleviate the imbalance problem, its generalization performance is still sub-optimal when facing novel test data. However, SharpDRO can not