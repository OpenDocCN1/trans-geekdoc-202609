
- Stable Vision Concept Transformers for Medical Diagnosis ............ 317  
  Lijie Hu, Songning Lai, Yuan Hua, Shu Yang, Jingfeng Zhang, and Di Wang

- Gx2Mol: De Novo Generation of Hit-Like Molecules from Gene Expression Profiles ............ 333  
  Chen Li and Yoshihiro Yamanishi

- Alternate Geometric and Semantic Denoising Diffusion for Protein Inverse Folding ............ 350  
  Chenglin Wang, Yucheng Zhou, Zhe Wang, Zijie Zhai, Jianbing Shen, and Kai Zhang

## Images and Computer Vision

- Self-generated Cross-Modal Prompt Tuning ............ 369  
  Guiming Cao, Zonghan Wu, Huan Huo, Yuming Ou, and Guandong Xu

- Quality-Preserving Extreme Image Compression: Using Interpretable Conditioning Inputs with Diffusion Models ............ 387  
  Shayan Ali Hassan, Danish Humair, Ihsan Ayyub Qazi, and Zafar Ayyub Qazi

- Beyond General Edge Utilization: Edge Attention Mean Teacher for Semi-Supervised Medical Image Segmentation ............ 405  
  Kaiwei Sun, Luhan Wang, and Jin Wang

## Interpretability and Explainability

- Queryable and Interpretable PU Learning Through Probabilistic Circuits ............ 425  
  Sieben Bocklandt, Vincent Derkinderen, Koen Vanderstraeten, Wouter Pijpops, Kurt Jaspers, Luc De Raedt, and Wannes Meert

- Interpretable Hybrid-Rule Temporal Point Processes ............ 443  
  Yunyang Cao, Juekai Lin, Hongye Wang, Wenhao Li, and Bo Jin

- SVEBI: Towards the Interpretation and Explanation of Spiking Neural Networks ............ 460  
  Jasper De Laet, Hamed Behzadi-Khormouji, Lucas Deckers, and Jose Oramas

- Towards Better Generalization and Interpretability in Unsupervised Concept-Based Models .................... 478  
  Francesco De Santis, Philippe Bich, Gabriele Ciravegna, Pietro Barbiero, Tania Cerquitelli, and Danilo Giordano

- Tree-Based OWL Class Expression Learner over Large Graphs .................................... 495  
  Caglar Demir, Moshood Yekini, Michael Röder, Yasir Mahmood, and Axel-Cyrille Ngonga Ngomo

- Smooth InfoMax - Towards Easier Post-Hoc Interpretability ................................... 512  
  Fabian Denoordt, Bart de Boer, and José Oramas

- Conformalized Exceptional Model Mining: Telling Where Your Model Performs (Not) Well ................... 528  
  Xin Du, Sikun Yang, Wouter Duivesteijn, and Mykola Pechenizkiy

- Author Index .................................................................... 545

## Graph Neural Networks

## MPG: An Efficient Multi-scale Point-Based GNN for Non-uniform Meshes

Qinxin Wu, Pengwei Liu, Xingyu Ren, and Dong Ni

Zhejiang University, Hangzhou, Zhejiang 310027, China  
{22360247,liupw,12332063,dni}@zju.edu.cn

### Abstract

Graph Neural Networks (GNNs) have become a powerful tool for modeling complex physical simulations, leveraging their ability to learn from irregular data representations. However, non-uniform meshes introduce significant challenges, particularly in adaptive multi-scale sampling, topological reconstruction, and efficient feature aggregation, often leading to high computational costs. Existing methods struggle to balance efficiency and accuracy due to their inability to dynamically adapt to irregular mesh structures. To address these limitations, we introduce Multi-Scale Point-Based Graph Neural Networks (MPG), a framework that combines point-cloud downsampling with topology-constrained strategies. MPG employs density-aware hierarchical sampling to adaptively retain critical nodes while leveraging a learnable neighborhood aggregation mechanism to enhance local structural sensitivity. Additionally, we introduce adaptive Constrained Delaunay reconstruction, which preserves global topology by eliminating invalid edges and maintaining boundary constraints during coarsening. To further improve efficiency, our model integrates lightweight residual MLPs, enabling scalable dimensions on multi-scale features. MPG's architecture supports dynamic multi-scale compression across diverse physical domains. Evaluations on fluid dynamics, thermochemical reactions, and cavity flow demonstrate that MPG reduces parameter count by at least 84.5% and accelerates training by 17.7% ~ 86.1% per epoch compared to baseline models, while maintaining high single-step rollout accuracy (RMSE < 10^-2). These results establish MPG as a new benchmark for efficient and accurate simulations on non-uniform meshes, offering a versatile solution for complex physical systems.

### Keywords

Non-uniform meshes · Multi-scale · Graph Neural Networks · Physical simulation · Surrogate model

### 1 Introduction

Non-uniform meshes are widely used in computational fluid dynamics (CFD) and other physics-based simulations, as they enhance accuracy in high-gradient regions and complex geometries. However, their irregular structure poses significant challenges for feature extraction and efficient computation. Traditional numerical solvers, such as finite difference methods [1] and finite element methods [2], provide accurate solutions but suffer from high computational costs, particularly in large-scale or real-time applications. To improve efficiency, data-driven methods have been explored for mesh-based simulations [3–5]. For example, convolutional neural networks (CNNs) leverage local receptive fields and weight sharing, making them effective for structured data [6–8]. However, their reliance on uniform grids necessitates resampling non-uniform meshes, leading to information loss and artificial smoothing. Moreover, CNNs struggle to capture the topological relationships inherent in non-uniform meshes, limiting their ability to model connectivity-dependent physical interactions.

Graph-based neural networks (GNNs) offer a more flexible framework for modeling complex physical systems [9]. By employing edge-node message passing (MP), GNNs can effectively capture local node interactions without the constraints of grid-based representations. As a result, they have been successfully applied to fluid dynamics [10], solid mechanics [11], and multi-physics coupling [12]. Among these, MeshGraphNets [10] stands out as a foundational end-to-end framework, demonstrating the potential of GNNs in mesh-based simulations. However, GNNs face notable challenges in large-scale simulations, including quadratic complexity in message passing [13] and feature oversmoothing [14], which hinder their scalability and accuracy.

To overcome the limitations of standard GNNs, multi-scale GNNs have been introduced to improve computational efficiency and enable hierarchical feature extraction [12,15–18]. These models construct coarse sub-level graphs to enable longer-range interactions and reduce MP iterations. However, existing methods face challenges in preserving graph connectivity during coarsening. Current methods primarily rely on spatial proximity [17–19], learnable sampling [15], manual mesh partitioning [13,16], algebraic multigrid algorithms [20], and automated bi-stride sampling [12], each with inherent limitations. Specifically, learnable or random sampling can introduce artificial partitions, hindering information exchange. Spatial proximity-based coarsening often generates incorrect edges, while algebraic multigrid algorithms suffer from cubic complexity. Bi-stride sampling preserves topology but lacks adaptability in feature dimension and sampling scale. Crucially, all these methods rely on deep MP stacks for information propagation, leading to high computational costs.

To overcome these limitations, we propose MPG, an efficient multi-scale GNN that integrates point-based feature extraction and graph-based topology preservation. MPG is designed to construct topology-preserving multi-scale graphs, enhance adaptive neighborhood aggregation, and achieve computational efficiency without deep MP stacking.

As illustrated in Fig. 1, MPG effectively coarsens non-uniform meshes while preserving key structural features. By combining hierarchical density-based sampling, topology-constrained Delaunay reconstruction, and residual MLP-based feature extraction, MPG sets a new benchmark for scalable, high-fidelity sim-
