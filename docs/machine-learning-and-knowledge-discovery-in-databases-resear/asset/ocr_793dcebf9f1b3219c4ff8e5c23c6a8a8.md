# Table 1. Methods for backdoor attacks on graph classification tasks.

| Attack Name | Trigger Type | Injection Method | Sample Selection |
|---|---|---|---|
| Subgraph Backdoor[21] | fixed subgraph | subgraph injection | random |
| GNNExplainer[18] | fixed subgraph | subgraph injection | random |
| GTA[15] | adaptive subgraph | subgraph injection | random |
| TRAP[19] | perturbation-based | flip edges | random |
| Motif[22] | motif subgraph | subgraph injection | random |
| Ours | data augmentation | flip edges/mask features | dynamic selection |

sample selection mechanism that prioritizes poisoned samples based on their contribution to the attack. This method identifies critical samples that have the highest impact on backdoor learning, ensuring that the model learns the trigger with minimal poisoned samples. The main contributions are as follows.

+   - We introduce a novel data augmentation-based trigger design that leverages topology-level or feature-level transformations to create stealthy and effective backdoor triggers for graph classification models.
+   - We introduce a dynamic poisoned sample selection strategy based on the occurrence of forgetting events, enabling the selection of poisoned samples that contribute more effectively to the backdoor attack.
+   - We conducted attack evaluations on GCN and GIN models across four benchmark datasets. The results demonstrate that our approach achieves better attack performance while maintaining a low clean accuracy drop (CAD).

# 2 Related Work

Backdoor attacks in graph classification remain an emerging area of research, with significant challenges yet to be addressed. Early research by [21] pioneered the idea of injecting predefined fixed subgraph patterns into training samples, prompting the GNN model to associate these subgraphs with attacker-designated target labels. Based on this, [18] further explored how the injection position of trigger subgraphs affects the attack performance, revealing that strategic placement at critical positions significantly influences attack success. [15] introduced an adaptive trigger generation approach using neural networks, producing triggers with fixed node counts but varied topologies, thereby enhancing the attack's flexibility and reducing detectability. [19] proposed perturbation-based triggers, leveraging meta-gradients computed on adjacency matrices to guide structural modifications. More recently, [22] investigated how different subgraph motifs influence the effectiveness of backdoor attacks from a motif-based perspective. Despite these advancements, existing methods have largely ignored the critical role of sample-level variations in backdoor attack effectiveness, leaving room for more efficient and stealthy approaches. We summarize and compare mainstream backdoor attack methods on graph classification tasks in Table 1.