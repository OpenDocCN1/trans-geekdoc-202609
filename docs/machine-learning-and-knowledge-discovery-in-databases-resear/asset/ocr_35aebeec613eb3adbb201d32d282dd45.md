and associated weights \(\hat{w}_{ij} \in \mathbb{R}\), where the weights are predicted over the concept embedding, i.e., \(\hat{w}_{ij} = \phi_i(\mathbf{c}_j)\), and \(\phi_i\) is a class-specific function parameterized by a neural network. The output prediction \(\hat{y}\) is then computed as \(\hat{y} = \text{argmax}_i p(y_i|c) = \text{argmax}_i \sum_j \hat{w}_{ij} \cdot \hat{c}_{ij}\). Note that \(\hat{w}_{ij}\) depends on the concept embedding \(\mathbf{c}_j = g(x)\) predicted for a specific sample. This means that while the final prediction is provided by means of a linear classification over the concept scores, thus preserving locally the interpretability of standard CBMs, the network \(\phi\) can predict different weights \(\hat{w}_{mj}\) for different samples, thus overcoming the representation bottleneck of standard CBMs.

# 3.4 Concept Decoder

As previously introduced, we parametrize the decoding function with a neural network \(\psi\). To improve the image reconstruction capabilities, also in this case we rely on the concept embeddings \(\mathbf{c}\). However, to still take into account the associated concept predictions \(\hat{c}\), we multiply the embeddings \(\mathbf{c}_j\) by the corresponding concept prediction \(\hat{c}_j\) before feeding them to the concept decoder. As a result, the input is reconstructed as \(\hat{x} = \psi(\hat{c} \cdot \mathbf{c})\).

# 4 Experiments

In this section, we present the experiments conducted to evaluate our proposed methodology. The experiments are designed to address the following key research questions:

+   1. **Generalization:** How effectively does the model generalize for classification tasks? Is the concept representation *complete*?
+   2. **Concept Representation Evaluation:** How much information is captured from \(c\) with respect to both the input image \(x\) and the label \(y\)? Are the learnt concepts *representative* of the data?
+   3. **Concept Interpretability:** How interpretable are the learnt concepts produced? Are they *aligned* with human representations?
+   4. **Model Interpretability:** Are the final predictions interpretable in terms of the discovered concepts? Can a user modify the concept prediction to extract counterfactual predictions?

# 4.1 Experimental Setting

In the following we report the dataset, metrics and baselines that we consider for evaluating and comparing our model. We conducted experiments using two backbones \(g\): ResNet-18 and ViT-base-patch32. Instead, we always use a decoder \(\psi\) composed by five transposed convolutional layers.

**Dataset.** This study uses seven image classification datasets of varying complexity. We employ two MNIST [20] variants, *Even/Odd* (digit parity) and *Addition*