| Dataset | Graphs | Avg. Nodes | Avg. Edges | Classes |
|---|---|---|---|---|
| NCI1 | 4,110 | 29.8 | 32.3 | 2 |
| PROTEINS | 1,113 | 39.1 | 72.8 | 2 |
| Mutagenicity | 4,337 | 30.3 | 30.8 | 2 |
| ENZYMES | 600 | 32.6 | 62.1 | 6 |

| Dataset | GCN | GIN |
|---|---|---|
| PROTEINS | 0.7130 | 0.7264 |
| NCI1 | 0.7251 | 0.7615 |
| Mutagenicity | 0.7707 | 0.8099 |
| ENZYMES | 0.3583 | 0.3833 |

centrality, and 15% of their features are masked. For the poisoned sample selection mechanism, we set the initial \(\alpha\) to 0.5, the number of iterations \(S\) to 40, the ASR rollback threshold \(\Delta_{th}\) to 0.05, and the adjustment rates \(\eta_1\) and \(\eta_2\) to 1.

For the baseline methods we compared, we adopt the parameter configuration specified in their original implementation.

**Baseline Methods.** Subgraph [21]: This method inserts a randomly generated fixed subgraph into a subset of training samples and assigns them to a target label. The trigger subgraph remains consistent across all poisoned samples. **Motif** [22]: This method utilizes frequent subgraph motifs as triggers, making them more naturally embedded in real-world datasets. **TRAP** [19]: TRAP flips edges in poisoned samples based on meta-gradients to create imperceptible perturbations that influence model predictions. **GTA** [15]: This method generates adversarial subgraphs using neural networks and injects them into poisoned samples, enhancing the attack's flexibility while maintaining stealthiness.

Our approach is named **Ours-Cos** when utilizing the first data augmentation strategy, **Ours-Deg** for the second, and **Ours-Mas** for the third.

# 5.2 Overall Performance of Backdoor Attacks

We use GCN as the backdoor model for trigger injection and sample selection. To evaluate our method, we measure the ASR and CAD on GCN models with the same architecture, representing a white-box attack scenario. Additionally, we assess the transferability of our attack by testing it on GIN models, which correspond to black-box attack settings.

Table 4 presents the experimental results. Among our three proposed strategies, Ours-Cos and Ours-Deg consistently achieve the highest ASR, while maintaining competitive or even lower CAD compared to baseline methods. This indicates that our method achieves better attack performance with comparable evasiveness to the baseline.

In comparison, Ours Cos has a slightly higher CAD, while Ours Deg achieves a better balance between ASR and CAD. Ours-Mas, which perturbs features rather than structure, shows the lowest ASR among our three strategies but still surpasses some baselines like Subgraph Backdoor and TRAP. This result suggests that structural perturbations are more effective than feature perturbations