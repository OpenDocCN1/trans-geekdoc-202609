# Backdoor Attacks on Graph Classification via Data Augmentation and Dynamic Poisoning

Yadong Wang$^1$, Zhiwei Zhang$^{1(\otimes)}$, Pengpeng Qiao$^2$, Ye Yuan$^1$,
and Guoren Wang$^1$

$^1$ Beijing Institute of Technology, Beijing, China
bit.wangyd@gmail.com, {zwzhang, yuan-ye}@bit.edu.cn, wanggrbit@126.com
$^2$ Institute of Science Tokyo, Tokyo, Japan
peng2qiao@gmail.com

**Abstract.** Graph neural networks (GNNs) have gained widespread adoption in domains such as bioinformatics, social networks, and chem-informatics, yet they remain susceptible to backdoor attacks. Existing backdoor attacks typically rely on subgraph triggers, which often introduce detectable anomalies and employ random poisoned sample selection, resulting in reduced stealthiness and efficiency. To address these limitations, we propose a novel backdoor attack framework that leverages data augmentation-based triggers and dynamic poisoned sample selection. Specifically, we design three alternative data augmentation strategies, edge modification guided by cosine similarity, edge removal based on degree centrality, and feature masking via gradient saliency, as backdoor triggers. Furthermore, we introduce a dynamic poison sample selection method informed by forgetting events. This method dynamically prioritizes high-impact poisoned samples to enhance attack efficiency while reducing the number of samples required to achieve the corresponding attack success rate (ASR). Experiments on four benchmark datasets, PROTEINS, NCI1, Mutagenicity, and ENZYMES, demonstrate the superiority of our method.

**Keywords:** GNNs · Graph Classification · Backdoor Attacks

# # 1 Introduction

Graph classification has emerged as a fundamental research direction across multiple domains, particularly in bioinformatics and drug discovery [17], chemoinformatics [11], protein-protein interaction networks [10], and social network analysis [5]. With the rapid advancement of GNNs [1,2,9,14], the ability to model and process graph-structured data has significantly improved. By capturing high-order dependencies between nodes and edges, GNNs have demonstrated outstanding performance in graph classification tasks. However, the widespread