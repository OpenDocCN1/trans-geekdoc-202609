
and associated weights \(\hat{w}_{ij} \in \mathbb{R}\), where the weights are predicted over the concept embedding, i.e., \(\hat{w}_{ij} = \phi_i(\mathbf{c}_j)\), and \(\phi_i\) is a class-specific function parameterized by a neural network. The output prediction \(\hat{y}\) is then computed as \(\hat{y} = \text{argmax}_i p(y_i|c) = \text{argmax}_i \sum_j \hat{w}_{ij} \cdot \hat{c}_{ij}\). Note that \(\hat{w}_{ij}\) depends on the concept embedding \(\mathbf{c}_j = g(x)\) predicted for a specific sample. This means that while the final prediction is provided by means of a linear classification over the concept scores, thus preserving locally the interpretability of standard CBMs, the network \(\phi\) can predict different weights \(\hat{w}_{mj}\) for different samples, thus overcoming the representation bottleneck of standard CBMs.

### 3.4 Concept Decoder

As previously introduced, we parametrize the decoding function with a neural network \(\psi\). To improve the image reconstruction capabilities, also in this case we rely on the concept embeddings \(\mathbf{c}\). However, to still take into account the associated concept predictions \(\hat{c}\), we multiply the embeddings \(\mathbf{c}_j\) by the corresponding concept prediction \(\hat{c}_j\) before feeding them to the concept decoder. As a result, the input is reconstructed as \(\hat{x} = \psi(\hat{c} \cdot \mathbf{c})\).

## 4 Experiments

In this section, we present the experiments conducted to evaluate our proposed methodology. The experiments are designed to address the following key research questions:

- 1. **Generalization:** How effectively does the model generalize for classification tasks? Is the concept representation *complete*?
- 2. **Concept Representation Evaluation:** How much information is captured from \(c\) with respect to both the input image \(x\) and the label \(y\)? Are the learnt concepts *representative* of the data?
- 3. **Concept Interpretability:** How interpretable are the learnt concepts produced? Are they *aligned* with human representations?
- 4. **Model Interpretability:** Are the final predictions interpretable in terms of the discovered concepts? Can a user modify the concept prediction to extract counterfactual predictions?

### 4.1 Experimental Setting

In the following we report the dataset, metrics and baselines that we consider for evaluating and comparing our model. We conducted experiments using two backbones \(g\): ResNet-18 and ViT-base-patch32. Instead, we always use a decoder \(\psi\) composed by five transposed convolutional layers.

**Dataset.** This study uses seven image classification datasets of varying complexity. We employ two MNIST [20] variants, *Even/Odd* (digit parity) and *Addition*

![](img/f56761e6196132d5b74909d98468408f_544_0.png)

Fig. 4. Comparison of the generalization performance across the evaluated datasets. LCBM consistently provides the highest generalization accuracy across concept-based models, closing the gap with end-to-end black box ones.

(paired digits summed as labels). CIFAR-10 and CIFAR-100 contain 10 and 100 natural image classes, with models extracting 15 and 20 macro-class concepts, respectively [17]. Tiny ImageNet includes 200 classes but is tested on 30 concepts for added challenge [42]. Skin Lesions classifies dermatoscopic images into 4 macro categories [37]. Finally, CUB-200 [39] covers 200 bird species with species and attribute annotations.

Metrics. We use specific metrics to address each research question. All results are reported with the mean and standard deviation, computed over the test sets by repeating the experiments with three different initialization seeds.

- 1. Generalization: To assess the classification generalization performance, we compute the Task Accuracy.
- 2. Concept Representation Evaluation: We employ the Information Plane approach [36] to analyze the information retained in the different concept representations. The information plane reports the evolution of the mutual information between the concept representation and both the input x (I(C, X)) and the label y (I(C, Y)) as the training epoch increases. For models reconstructing the input from the concepts, we assess the Input Reconstruction Error by computing the Mean Squared Error (MSE) between the inputs x and their reconstructions \(\hat{x}\).
- 3. Concept Interpretability: For datasets with annotated concepts, we assess their alignment with the learnt concepts using the macro Concept F1 Score (best-match approach) and the Concept Alignment Score (CAS) [8] for concept representation alignment. Additionally, we conducted a user study with 72 participants, each answering 18 questions. The study evaluated Plausibility by asking users to (i) select an image that best represents a given concept and (ii) identify an intruder image among those representing a single concept. It also assessed Human Understanding by having participants assign a name to a set of images illustrating a concept. Finally, we provide qualitative insights through Concept Dictionaries, showcasing images with the strongest activations for each concept.
- 4. Model Interpretability: We perform Concept Interventions [16] to observe how model predictions change when concept predictions are modified. As posi-

![](img/f56761e6196132d5b74909d98468408f_545_0.png)

Fig. 5. Information Plane for the different models in terms of Mutual information between concept and input variables $I(X, C)$, and between the concept and output variables $I(C, Y)$. The size of the markers is proportional to the training epoch.

Table 1. We report the Input Reconstruction Error in terms of MSE for those methods that explicitly reconstruct the input.

| | MNIST E/O | MNIST Add. | CIFAR10 | CIFAR100 | Tiny ImageNet | Skin Lesion | CUB200 |
|---|---|---|---|---|---|---|---|
| BotCL | 1.40 ± 0.09 | 1.57 ± 0.03 | 0.87 ± 0.02 | 0.82 ± 0.01 | 1.35 ± 0.06 | 0.72 ± 0.02 | 0.07 ± 0.01 |
| SENN | 0.62 ± 0.02 | 0.93 ± 0.03 | 0.81 ± 0.04 | 0.74 ± 0.01 | 1.10 ± 0.02 | 0.61 ± 0.04 | 0.05 ± 0.01 |
| LCBM | **0.32** ± **0.01** | **0.71** ± **0.11** | **0.51** ± **0.01** | **0.55** ± **0.01** | **0.72** ± **0.01** | **0.32** ± **0.01** | **0.05** ± **0.01** |

tive concept interventions are non-trivial in unsupervised concept settings, we perform negative interventions [8]. Negative interventions involve randomly swapping the values of the concept scores with a given probability, expecting model accuracy to decrease as intervention probability increases. For LCBM, to switch a concept to inactive, we set \(\hat{c}_j = 0\), while to activate it, we set \(\hat{c}_j = 1\) and replace the concept embedding with the concept prototype \(\bar{c}_j = \mathbf{t}_j\). Additionally, we provide _Qualitative Explanations_ generated by LCBM using as concept importances the predicted weights multiplied by the concept predictions \(w_{ij} \cdot \hat{c}_j\).

**Baselines.** To compare the performance of the proposed approach, we test it against unsupervised approaches like _SENN_ [3] and two variants of a SOTA model BotCL [40]: _BotCL (Recon)_, which employs an autoencoder-based approach to reconstruct the input image from the concept bottleneck, and _BotCL (Contr)_, which applies a contrastive term to the loss to encourage distinct concept activations for different classes. Also, we consider a prototype based approach _ProtoPNet_ [6] and Label-Free CBM (LF-CBM) [26] a recent hybrid approach. If the concepts were known (e.g., MNIST Addition), we used CLIP to align the model with concept captions (e.g., this image contains the digit 4). If the concepts were unknown, we used the LLM to generate a list of possible concepts. Finally, we compare with a standard black-box model trained end-to-end (E2E).

### 4.2 Generalization

LCBM is the most accurate interpretable model (Fig. 4). The proposed methodology significantly outperforms the baselines. In the most challenging scenario (Tiny ImageNet with only 30 concepts), it achieves up to a 50% increase in task accuracy compared to the worst baseline (BotCL (recon)) and up to a 17% improvement over the runner-up model, ProtoPNet. Our model consistently delivers the best generalization accuracy across all datasets, with higher gaps in challenging gaps with lower concept-class ratios. This result is valid even when we compare LCBM with LF-CBM which exploit the pre-existing knowledge within a VLM to extract concept annotations. Only in the very simple MNIST Even/Odd dataset a few methods perform better, by a few decimals. We attribute this improvement to the unsupervised concept embeddings, which allows learning more complete representations for task prediction.

**LCBM closes the gap with black-box models (Fig. 4).** Figure 4 also shows that LCBM achieves results comparable to the E2E black-box model. The generalization loss is always less than 1–2%. Notably, on the MNIST addition dataset, a setting where reasoning capabilities over concepts are required, our approach outperforms the black-box model with a task accuracy improvement of 2%. Overall, LCBM demonstrates its capability to achieve high interpretability without sacrificing accuracy in unsupervised concept learning settings.

### 4.3 Concept Representation Evaluation

**LCBM concept representation retains more information regarding both the input and the output (Fig. 5).** The concept representation obtained through unsupervised concept embedding is significantly richer than that derived from simple concept scores. As training progresses, most baselines experience a reduction in mutual information with the input I(X, C) while increasing the mutual information with the output I(Y, C). This observation supports the conclusion that unsupervised CBM models tend to lose input-related information while attempting to optimize task performance [34], even for those models that explicitly require concepts to be representative of the input, such as SENN and BotCL (Recon). On the contrary, LCBM overcomes this limitation by means of concept embeddings, which facilitate a better balance between competing objectives, as evidenced by the monotonic increase in mutual information with both the input and output during training.

**LCBM allows better input reconstruction (Table 1).** To understand why the mutual information I(X, C) of LCBM is consistently higher compared to other reconstruction-based unsupervised CBMs, we assess the Input Reconstruction Error in terms of MSE. As shown in Table 1, LCBM achieves lower MSE in image reconstruction compared to the runner-up model (usually SENN), with values ranging from 0.18 to 0.38. We believe that concept embeddings facilitate more accurate and efficient reconstruction by allowing more information to flow to the decoder network when a concept is active (\(\hat{c}_j = 1\)). Unlike other unsupervised models that can only pass a single value (\(\hat{c}_j\)), LCBM passes the entire associated concept embedding (\(\vec{c}_j\)) to the decoder.
