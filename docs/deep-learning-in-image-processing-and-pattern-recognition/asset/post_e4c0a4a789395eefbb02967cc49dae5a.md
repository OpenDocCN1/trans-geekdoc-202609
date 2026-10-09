
2. The slow–fast learning paradigm was quoted for NAS, which further optimizes the overall architecture vector through pseudo gradient iteration, stabilizing the optimal search process, which improves the update and rate of convergence speed of the architecture for HSI classification.
3. To better train the HSI classification model, the Lion optimizer has been introduced, which not only effectively improves the accuracy of HSI data classification but also reduces memory overhead and training time because the algorithm only tracks momentum and uses symbol operations to calculate updates.

## 2. Materials and Methods

### 2.1. Search Framework

Figure 1 illustrates the proposed NAS framework for HSI classification in this paper. Initially, the hyperspectral image is divided into patches using a sliding window approach. These patches are then fed into the automatic architecture search model, which consists of both normal cells and reduction cells. Secondly, the NAS network includes supernet architecture search and final network optimization. We designed a multi-scale attention mechanism search operator for the search space (The different colored arrows represent different candidate operations), enhancing the ability to extract multi-scale spectral–spatial features from HSI data, thereby improving classification performance. Then, we utilized the slow–fast learning paradigm to effectively update the overall architecture vector, improving the efficiency of constructing hypergrid architecture units. Finally, we introduced the Lion optimizer to accelerate model convergence and alleviate model memory overhead.

![](img/e4200cc4308edaf8913e513b0f96dbb6_157_0.png)

**Figure 1.** The overall framework of the proposed MS³ANAS model.

### 2.2. Neural Architecture Search Algorithm

MS³ANAS consists of three architecture search components: the search space of the multi-scale expanding attention mechanism, the search strategy of the slow–fast learning paradigm, and the Lion optimizer. Here is a detailed explanation of each component.

#### 2.2.1. Multi-Scale Attention Mechanism Expanded Search Space

1. Multiple attention mechanism guided search space

Applying different attention mechanisms to different datasets may face varying challenges. For example, in some HIS datasets, it may be more challenging to use spatial attention mechanisms due to strong correlations between data. In contrast, it may be more difficult to use channel attention mechanisms due to highly variable features. Moreover, the performance of attention mechanisms can also be affected by factors such as dataset size and quality, model architecture, and hyperparameters. Therefore, it is important to choose appropriate attention mechanisms based on different HSI datasets and tasks to achieve optimal performance and effectiveness. In addition, various samples in the HSI dataset exhibit long-tailed distributions, resulting in imbalanced HSI classification results. We propose a multiple search space with rich attention for HSI classification, which can effectively improve classification accuracy and reduce computational complexity. We select four types of attention mechanisms to form it. They are the convolutional block attention module (CBAM) [38], squeeze-and-excitation (SE) module [36], triplet attention (TA) module [39], and coordinate attention mechanism (CA) [40], as shown in Figure 2.

![](img/e4200cc4308edaf8913e513b0f96dbb6_158_0.png)

(a)

![](img/e4200cc4308edaf8913e513b0f96dbb6_158_1.png)

(b)

![](img/e4200cc4308edaf8913e513b0f96dbb6_158_2.png)

(c)

![](img/e4200cc4308edaf8913e513b0f96dbb6_158_3.png)

(d)

**Figure 2.** Multiple attention mechanism search space (a) CBAM; (d) CA; (b) SE; (c) TA.

To reduce repetition, various attention mechanisms have been proposed in the literature. One such mechanism is the CBAM module, which combines channel attention and spatial attention. It aggregates spatial features by performing max-pooling on top of global average pooling. This allows the network to focus on important spatial information. Another attention mechanism is the SE module, which enhances the network's sensitivity to informative features. It recalibrates filter responses through squeeze-and-excitation operations, improving the learning ability of convolutional layers. The TA module is composed of three parallel branches, each serving a distinct purpose. The first branch focuses on establishing spatial attention, while the other two branches aim to capture cross-dimensional interactions between the channel and spatial dimensions. The final output is obtained by averaging the outputs from these three branches. The CA mechanism learns weights by combining features at each position with their corresponding coordinate information. This mechanism effectively captures spatial correlations, leading to improved model performance. By incorporating these attention mechanisms, models can effectively reduce redundancy and improve the performance of HSI classification tasks.

As NAS-based HSI classification requires the determination of the search space, we propose search space $\mathcal{O}$. Formally, let $\mathcal{O}$ denote a sequence of candidate operations (multiple attention guided operations), where each operation represents a function $p_{i}(\cdot)$ to be applied to $s_{i}$. For each cell $q$, we configure an architectural parameter $\alpha_{p_{i}}^{q}$ for operation $p_{i}$. To ensure continuity of the search space, we relax the search space to allow it to be optimized via gradient descent. Specifically, we relax the architectural parameter $\alpha_{p_{i}}^{q}$ to be continuous, and then compute the operational probabilities for different operations by applying softmax over all $\alpha_{p_{i}}^{q}$.

$$ R_{p_{i}}^{q} = \frac{\exp(\alpha_{p_{i}}^{q})}{\sum_{j=1}^{n} \exp(\alpha_{p_{j}}^{q})} $$

Here, $n$ represents the number of candidate operations available. The larger value of $R_{p_{i}}^{q}$ indicates a higher likelihood of selecting the representative operation. The output of the cell is obtained by taking the weighted sum of all possible operations.

$$ \overline{p}(y_{i}) = \sum_{p \in \mathcal{P}} R_{p_{i}}^{q} p_{i}(y_{i}) $$

The notation $p_{i}(y_{i})$ signifies the application of operation $p_{i}$ on input $y_{i}$. Consequently, the search process is transformed into a learning process of a set of architectural parameters $\{\alpha_{p_{i}}^{q}\}$. Furthermore, as the network weights $w$ also need to be learned, we are required to solve the following bi-level optimization problem.

$$
\begin{array}{l} 
\min_{\alpha} \mathcal{L}_{val}(w^{*}, \alpha) \\ 
s.t. \ w^{*} = \operatorname{argmin}_{w} \mathcal{L}_{train}(w, \alpha) 
\end{array}
$$

The purpose of the above formulae is to search for the architectural parameters that minimize the validation loss $\mathcal{L}_{val}(w^{*}, \alpha)$, and the network weights $w^{*}$ are obtained by minimizing the training loss $\mathcal{L}_{train}(w, \alpha)$. It is important to note that the training loss and the validation loss are identical.

The objective of the aforementioned formulae is to search for architectural parameters that minimize the validation loss $\mathcal{L}_{val}(w^{*}, \alpha)$, while the network weights $w^{*}$ are obtained by minimizing the training loss $\mathcal{L}_{train}(w, \alpha)$. It is crucial to emphasize that the training loss and the validation loss are indeed the same.

2. Multi-scale attention mechanism search space

Different types of convolutions have varying computational requirements and parameter counts. Building deeper models can be challenging due to the expensive parameters and time required for high-dimensional convolutions. This can limit the efficiency and feasibility of constructing deeper models. Therefore, high-dimensional convolutions are often replaced with lower-dimensional separable convolutions to alleviate this issue. The novel operation MCS_sepConv(_b x b) (b = 3, 5, 7) in the search space combines spectral-spatial CBAM with spatial separable convolution [41], which helps to extract deeper spectral-spatial features, and it can enhance the spectral-spatial adaptive learning ability of the data. In addition, we use small filters to reduce parameters while maintaining a large-scale receptive field. We have strengthened the ability to extract scale spectral-spatial features from data, thereby
