
**Surrogate Gradient:** At last, training SNNs can be challenging due to the non-differentiable nature of the Heaviside step function. In this work, we use the surrogate gradient method [23] to handle this. This means using the Heaviside step function in the forward pass, but replacing it by a differentiable function for computing the gradient in the backward pass. Similarly to [15], we use a sigmoidal approximation of the derivative of the step function.

## 3.2 ANN Interpretation and Explanation Method

When designing an interpretation method or an explanation method, it is important to base the method on attributes derived directly from the model. As explained in Sect. 3.1, the non-differentiable nature of the LIF-neuron prevents us from computing the gradients of the model. While computing gradients using a surrogate gradient function during training has shown to be effective, these are not the actual gradients of the model. This motivates our decision to adopt an activation-based approach, as the activations can be easily obtained from an SNN. In addition to this, it has been shown that SNNs following architectures and topologies inspired from non-spiking ANNs can achieve reasonable results [15, 37, 41, 44, 48]. Consequently, we opt to develop a post-hoc interpretation method, as it eliminates the need to design a new SNN architecture.

The Visual Explanation By Interpretation (VEBI) method, proposed in [25], is capable of both achieving a level of interpretation as well as explanation of ANNs. Both the interpretation and explanation are based on a post-hoc approach to identify a set of internal relevant filters per class for a given pretrained model. This method consists out of two main steps. First, the extraction of the input-wise internal responses from the network F for all N images, where N denotes the number of images used to train the model F. The second step includes using these image-wise responses to obtain a matrix W \in \mathbb{R}^{m \times C} that indicates what layer-filter pairs are relevant to what class by solving a \mu-lasso problem (Eq. 3). Here, m denotes the total number of considered filters (or features in general) and C the total number of classes.

```
W^* = argmin_W \|X^T W - L^T\|_F^2
```

Here, X is a matrix containing the input-wise responses for all N images where X \in \mathbb{R}^{m \times N}. L is a matrix containing the predicted labels (in one-hot encoding format) for all N inputs where L \in {0, 1}^{C \times N}. In order to enforce that only a subset of the most relevant features are selected in W, a sparsity constraint \mu is added in the following manner \|w_j\|_1 \le \mu, \forall j \in {1, 2, ..., C}. This makes it a \mu-lasso problem.

**Model Interpretation:** This is achieved by producing via visualizations that aim to depict the visual patterns encoded by the extracted relevant features. In [25], these visualizations are produced via average images computed from the top-k 100 images for which the identified relevant filters have the highest responses. Prior to the average operation, these images are cropped to the size of the receptive field of the relevant filter centered at the location that has the maximum activation in the filter response.

**Model Explanation:** This is achieved by accompanying the class label predicted by the model with heatmap visualizations derived from the set of relevant filters supporting the prediction. Since in [25] the generation of these explanations involves computing the gradient through backpropagation — a process not directly feasible for SNNs, as outlined in Sect. 3.1—we have not further extended the explanation method presented in [25]. Instead, we have come up with our own method for generating visual explanations (Sect. 4.2).

## 4 Proposed Method

We propose SVEBI, a pipeline capable of both achieving interpretability and explainability of SNNs. It is composed out of two core elements. First, a method for the identification and inspection of features that are of importance to the classes of interest. This is achieved by finding the relationship between internal activations and predicted class labels (Sect. 4.1). Second, an approach for estimating layer-level responses which can serve as means for explanation by aggregating the average activation maps of filters relevant to the predicted class (Sect. 4.2). SVEBI can be considered an SNN counterpart of VEBI.

### 4.1 Identifying Class-Relevant Filters

We devise a method for identifying class-relevant filters by extending the method from VEBI [25] (see Sect. 3.2). Our method is an adaptation that allows for producing the $W$ matrix that indicates the relevant layer-filter pairs per class by taking into account the disparities between non-spiking ANNs and SNNs.

The main difference lies in the first step, the extraction of input-wise responses $x_i$ for every $i^{th}$ training image which involves the collection of the internal responses of each filter in the architecture. For non-spiking ANNs, this means collecting a single activation map containing continuous values for each filter. However, an SNN uses spikes over time to propagate information through the network. This means that the filter responses of a single filter are activation maps consisting of binary events. Furthermore, passing a single image through the network is done over a number of timesteps $T$. Thus, when passing a single image through an SNN $G$, each filter in $G$ produces an activation map for each timestep. We approach this difference in the following manner: When passing the $i^{th}$ image through $G$, we collect $T$ activation maps for each filter. We denote an activation map as $S_{it}^f$ per filter $f$, where $t \in \{1, 2, 3, ..., T\}$. We squeeze the resulting $T$ activation maps by defining a single average activation map $\bar{S}_i^f$ for filter $f$. As the activation maps can be seen as matrices, we obtain this by computing the element-wise mean as follows:

```
\(\bar{S}_i^f = \frac{1}{T} \sum_{t=1}^T S_{it}^f\) (4)
```

This is done for each filter, followed by the subsequent steps described in VEBI [25]. Consequently, this average activation map forms the SNN equivalent for the single activation map that is collected per filter for non-spiking ANNs. As before, the above is repeated for all \(N\) training images which is followed by using the \(N\) input-wise responses to define the matrix \(X \in \mathbb{R}^{m \times N}\) and then estimate \(W \in \mathbb{R}^{m \times C}\) by solving the \(\mu\)-lasso problem (see Eq. 3). As described in Sect. 3.2, sparsity is enforced via the constraint \(\mu\).

### 4.2 Generating Explanatory Heatmaps

We generate visual explanations for SNNs in the form of heatmap visualizations using the relevant filters identified by our method (Sect. 4.1) as a basis. The heatmap visualization is based on the spiking behaviour within the identified relevant filters of a layer with respect to a single input image belonging to a specific class.

This begins by passing an image \(i\) through the SNN \(G\) and collecting the output activation map \(S^f_{it}\) of the specific relevant filter \(f\) for all \(t \in \{1, 2, 3, ..., T\}\). Analogous to the previous sections, this is followed by producing a single average activation map \(\bar{S}^f_i\) (via Eq. 4). This is then repeated for all class-relevant filters of a single layer for the predicted class, after which we add all resulting average activation maps together. We can produce the heatmap explanation by upscaling the summed activation map to the size of the input image \(i\), applying normalization, and then superimposing on the input image \(i\).

### 4.3 Computational Considerations

The most significant computational cost introduced by our method arises during the identification of relevant filters, as this step requires processing the entire training set with the model. The generation of explanation heatmaps at inference time results in only minimal overhead, comparable to a standard forward pass through the model, as it involves collecting activation maps and executing a set of lightweight computations.

## 5 Evaluation

We evaluate our methods by conducting several experiments. First, we investigate the impact of the identified relevant filters on the performance of the model. This experiment serves as a fundamental sanity check that determines whether the identified filters are indeed critical for the decision-making process (Sect. 5.2). Secondly, we assess the layer-wise distribution of the identified relevant filters of the model (Sect. 5.3). This is followed by a qualitative analysis of the identified relevant filters by generating visual feedback. The objective of this experiment is to understand what the model has learned, thereby achieving model interpretation (Sect. 5.4). Then, we present our explanatory heatmaps, which we qualitatively evaluate by comparing to the maps produced by SNN-Grad2D
