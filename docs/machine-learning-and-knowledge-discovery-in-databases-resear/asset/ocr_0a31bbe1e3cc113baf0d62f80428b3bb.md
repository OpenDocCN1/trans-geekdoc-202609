# Community-Aware Graph Transformer:
Preserving Community Semantics
for Effective Global Aggregation

Yutai Duan, Jie Liu(✉), Jianhua Wu, and Jialin Liu

College of Artificial Intelligence, Nankai University, 300350 Tianjin, China
{ytduan,wujianhua,2120220573}@mail.nankai.edu.cn, jliu@nankai.edu.cn

Abstract. Graph Transformers (GTs) address the locality limitation of traditional GNNs, which aggregate only local neighbor information, by leveraging global attention. However, they suffer from two significant issues: neglecting community structures and information over-squeezing. In this paper, we first identify these two problems and propose a Community-Aware Graph Transformer (CoGT) to solve them. CoGT introduces a novel node-community-global hierarchical aggregation framework. This design preserves community-level semantics while reducing the volume of aggregated information, alleviating the over-squeezing problem. CoGT first employs a two-stage positional encoding to identify latent communities and enhance semantic consistency. Then, a hierarchical and parallel transformer computation method based on community representations facilitates global information interaction. Furthermore, we enable community-wise parallel attention computation, improving computational efficiency. Experimental results demonstrate that CoGT outperforms existing methods across multiple real-world datasets.

Keywords: Graph transformer · Graph representation learning

# 1 Introduction

The core objective of Graph Representation Learning (GRL) [27] is to capture both topological structure and semantic information by modeling node interactions. Traditional Graph Neural Networks (GNNs) [24], limited by local neighborhood aggregation, struggle to uncover long-range dependencies [3,23]. Graph Transformers (GTs) [22,26], using global attention mechanisms [16], enable interactions across all nodes, significantly enhancing node representations. This global aggregation can overcome local neighborhood limitations and identify distant nodes with potential benefits [25]. However, many studies have focused on improving the efficiency of GTs while ignoring the problems of global aggregation in GRL: the loss of community structure semantics and information over-squeezing.