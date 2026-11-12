through molecular graph topology remapping, enabling more comprehensive representation of molecular structures.

+   2. To the best of our knowledge, this is the first work to achieve uncertainty-aware metabolic stability prediction by integrating Beta-Binomial subjective logic into graph neural networks, providing crucial confidence estimates for drug discovery applications.

+   3. Extensive experiments conducted on a dataset comprising 10,031 compounds reveal that our TrustworthyMS model outperforms existing methods in comparison to the baseline model. Specifically, it demonstrates a remarkable 46.1% improvement in robustness on out-of-distribution (OOD) data, while also surpassing current state-of-the-art approaches in both classification (0.622 MCC) and regression (0.833 P-score) tasks.

# 2 Related Work

**Feature Engineering.** Traditional assessments of metabolic stability have largely depended on laboratory experiments [3]. In contrast, computational approaches capitalize on chemical domain knowledge through feature engineering strategies. The descriptor-based approach extracts quantitative molecular properties (e.g., molecular weight, logP) from chemical structures. For instance, [15,19] utilized such descriptors to build random forest models. Complementing this, the fingerprint-based methodology encodes structural patterns into binary vectors using techniques such as ECFP and MACCS fingerprints. Notably, [1,16] integrated these fingerprints with molecular descriptors to construct compound representations.

**Graph Representation Learning.** Molecular graph representation methods have been applied to metabolic stability prediction through SMILES-derived topological constructions [10]. [18] proposed converting SMILES sequences into molecular graphs processed by graph convolutional networks (GCNs), employing node feature aggregation across graph neighborhoods. [2] presented CMMS-GCL, a method combining SMILES sequence similarity features with molecular graph structural features through feature concatenation. Current implementations primarily focus on atom-level representations and neighborhood information propagation, while chemical bond attributes patterns have not been fully explored in these architectures, as noted in [21].

# 3 Methods

Figure 1 illustrates the TrustworthyMS architecture, a novel framework addressing metabolic stability predictisoin through three synergistic modules. The system processes SMILES inputs via: (1) **Molecular Graph Topology Remapping (Fig. 1a)**, where RDKit-constructed [9] molecular graphs are augmented with bond-centric nodes (atom-bond-atom triplets) to form dual representations,