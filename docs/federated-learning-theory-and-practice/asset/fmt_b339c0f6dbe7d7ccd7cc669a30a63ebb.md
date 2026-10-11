
In this chapter, we study the relatively unexplored problem of hyper-parameter optimization (HPO) for federated learning (FL-HPO). We clearly formulate the FL-HPO problem, contrast it with traditional centralized HPO, and highlight the various potential novel challenges in the federated setup. Thoroughly walking through the HPO literature for federated learning, we discuss how existing FL-HPO approaches fare against the FL-HPO challenges. In particular, we introduce **F**ederated **Lo**ss Su**R**face **A**ggregation (FLoRA), a general FL-HPO solution framework that can address use cases of tabular data and any machine learning (ML) model, including gradient boosting training algorithms, SVMs, neural networks, among others, and therefore further expands the scope of FL-HPO. FLoRA enables single-shot FL-HPO: identifying a single set of good hyper-parameters that are subsequently used in a *single* FL training. Thus, it enables FL-HPO solutions with minimal additional communication overhead compared to FL training without HPO. Moreover, we briefly cover the optimality guarantee for FLoRA and other state-of-the-art FL-HPO solutions. The empirical evaluation of FLoRA for multiple ML algorithms demonstrates significant model accuracy improvements over the considered baseline, and robustness to increasing number of clients involved in FL-HPO training.

### Keywords

Hyper-parameter optimization; Loss surface; Single-shot HPO

## 13.1 Introduction

Despite the unique advantages federated learning or FL brings forth, there are many open problems in the FL domain [[18]](#Chp013_237-255_B9780443190377000223.xhtml#br0090), [[20]](#Chp013_237-255_B9780443190377000223.xhtml#br0100), one of which is hyper-parameter optimization for FL. Existing FL systems require a user (or all participating clients) to pre-set (agree on) multiple hyper-parameters (HPs) (i) for the model being trained (such as number of layers and batch size for neural networks or tree depth and number of trees in tree ensembles), and (ii) for the aggregator (if such hyper-parameters exist). Hyper-parameter optimization (HPO) for FL is important because the choice of HPs can have dramatic impact on performance [[26]](#Chp013_237-255_B9780443190377000223.xhtml#br0130). While HPO has been widely studied in the centralized ML setting, it comes with unique challenges in the FL setting. In this chapter, we will take a deep look at the FL-HPO problem which is the problem of performing HPO in an FL setup. Before describing the different challenges that arise with FL-HPO, we will first describe the FL-HPO problem in detail.

### 13.1.1 FL-HPO problem definition

In the centralized machine learning setting, we would consider a model class $\mathcal{M}$ and its corresponding learning algorithm $\mathcal{A}$ parameterized collectively with a hyper-parameter (HP) configuration $\boldsymbol{\theta} \in \boldsymbol{\Theta}$, and given a training set $D$, we can learn a single model $\mathcal{A}(\mathcal{M}, \boldsymbol{\theta}, D) \to \boldsymbol{w} \in \mathcal{M}$. The HP configuration can include (i) model-specific hyper-parameters such as the number of layers in a neural network and the number of neurons in each layer, and (ii) learning-algorithm-specific hyper-parameters such as the learning rate or weight decay. Here, we will consider both these classes of hyper-parameters collectively.

Given some predictive loss $\mathcal{L}(\boldsymbol{w}, D')$ of any learned model $\boldsymbol{w} \in \mathcal{M}$ evaluated on some held-out dataset $D'$, the centralized hyper-parameter optimization or HPO problem can be stated as

$$
\min_{\boldsymbol{\theta} \in \boldsymbol{\Theta}} \mathcal{L}(\mathcal{A}(\mathcal{M}, \boldsymbol{\theta}, D); D').
$$

(13.1)

In the most general federated learning or FL setting, we have $n$ clients $P_1, \dots, P_n$ each with their private local training dataset $D_m, m \in [n]$ where $[n]$ denotes the index set $\{1, 2, \dots, n\}$. Let $D \coloneqq \bigcup_{m=1}^n D_m$ denote the aggregated training dataset and $\bar{D} \coloneqq \{D_m\}_{m \in [n]}$ denote the set of per-client datasets. Each model class (and corresponding learning algorithm) is parameterized by global HPs $\boldsymbol{\theta}_G \in \boldsymbol{\Theta}_G$ shared by all clients and per-client local HPs $\boldsymbol{\theta}_L^{(m)} \in \boldsymbol{\Theta}_L, m \in [n]$ with $\boldsymbol{\Theta} \coloneqq \boldsymbol{\Theta}_G \times \boldsymbol{\Theta}_L$. FL systems usually include an aggregator with its own set of HPs $\boldsymbol{\phi} \in \boldsymbol{\Phi}$. We make this separation between the hyper-parameter type to highlight the novel aspects of the FL-HPO problem. We use $\boldsymbol{\theta} \in \boldsymbol{\Theta}$ to denote HPs that are part of the learning that is present both in the centralized and FL settings, while we use $\boldsymbol{\phi} \in \boldsymbol{\Phi}$ to denote HPs that only arise in the FL setting.

**Example 13.1**

With a neural network model, HPs such as the number of layers in a neural network or the activation function or learning rate would be HPs we consider as being part of $\boldsymbol{\theta}$, while HPs such as the number of sampled clients or the gradient compression rate are examples of HPs that only appear in an FL setting and we denote these with $\boldsymbol{\phi}$. With $\boldsymbol{\theta} \in \boldsymbol{\Theta}$, we further differentiate between global HPs $\boldsymbol{\theta}_G$ shared across all clients such as the architectural HPs for the network (depth, width, activation), and per-client local HPs $\boldsymbol{\theta}_L^{(m)}, m \in [n]$ that can be different between clients such as the learning rate or batch size.

**Example 13.2**

Such a distinction also exists for other machine learning models such as gradient boosted tree ensembles like XGBoost [[5]](#Chp013_237-255_B9780443190377000223.xhtml#br0025). HPs such as the ensemble size, tree depth, and discretization level are present even in the centralized setting and hence we denote them as $\boldsymbol{\theta} \in \boldsymbol{\Theta}$. HPs such the histogram merging strategy [[29]](#Chp013_237-255_B9780443190377000223.xhtml#br0145) are unique to XGBoost in the FL setting and would correspond to $\boldsymbol{\phi}$. The ensemble HPs such as number of trees and tree depth would constitute $\boldsymbol{\theta}_G$ while discretization level can constitute the per-client local HP $\boldsymbol{\theta}_L^{(m)}, m \in [n]$, allowing the model to account for the potential heterogeneity in the per-client data distributions.

Finally, we have an FL algorithm $\mathcal{F}$ that takes as input the model class, learning algorithm, HPs and the per-client datasets, and outputs a model $\boldsymbol{w}$:

$$
\mathcal{F}(\mathcal{M}, \boldsymbol{\phi}, \boldsymbol{\theta}_G, \{\boldsymbol{\theta}_L^{(i)}\}_{i \in [n]}, \mathcal{A}, \bar{D}) \to \boldsymbol{w} \in \mathcal{M}.
$$

(13.2)
