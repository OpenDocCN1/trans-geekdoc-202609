
![](img/f56761e6196132d5b74909d98468408f_580_0.png)

Fig. 2. Interpolated latent representations between two audio signals (“bidi” and “baga”) using SIM. Each plot shows the decoded signal for different interpolation factors \(\alpha\). Listen to the decoded audio, among others, on Google Colab.

## Quantitative Evaluation of Specific Information Spread.

To assess how vowel and speaker information is distributed across latent dimensions, we train linear classifiers (without bias) on average-pooled representations from \(g_{enc}^1(\cdot)\), \(g_{enc}^2(\cdot)\), and \(g_{enc}^3(\cdot)\). Classifier weights indicate the relevance of each dimension, with large magnitudes signifying high importance.

### Results.

As shown in Fig. 3, SIM concentrates vowel/speaker information in fewer dimensions, which is beneficial for interpretability. GIM, on the other hand, spreads this information more broadly thereby requiring a larger number of neurons to be studied. Accuracy for vowel identification in GIM: 95.94%, 92.81%, 94.06%, and in SIM: 87.5%, 93.44%, 91.87%. For speaker identification, GIM: 88.29%, 97.83%, 98.56%, and SIM: 68.36%, 91.76%, 94.32%.

![](img/f56761e6196132d5b74909d98468408f_580_1.png)

Fig. 3. Distribution of linear classifier weights for vowel prediction (artificial dataset, left) and speaker identification (LibriSpeech, right), trained on representations from \(g_{enc}^1(\cdot), g_{enc}^2(\cdot), g_{enc}^3(\cdot)\). SIM’s classifiers show more weights near zero, indicating that vowel and speaker information is concentrated in fewer dimensions.

## Quantitative Evaluation of General Information Spread.

To further observe the impact on interpretability through unit analysis and to analyze whether our representations align with the known disentanglement properties from \(\beta\)-VAE’s regularizer [6, 12, 15], we introduce a metric to measure how effectively a decoder \(D : \mathcal{Z}^m \rightarrow \mathcal{X}\) can reconstruct a target signal when only the most relevant latent dimensions are modified. This serves as a proxy for entanglement, especially given that the artificial dataset has only a few ground truth factors, requiring far fewer dimensions than the available 512.

For each pair of starting and target representations \((\mathbf{z}^m_{\text{start}}, \mathbf{z}^m_{\text{target}})\), we define an interpolated representation, \(\mathbf{z}^m_{\alpha=1}\), where only the \(N\) most important dimensions (those with the greatest average difference over 64 time frames) are altered to match \(\mathbf{z}^m_{\text{target}}\). The similarity between the decoded \(\mathbf{z}^m_{\alpha=1}\) and \(\mathbf{z}^m_{\text{target}}\) measures how many dimensions are needed to transform the signal. The relative error is computed as:

\(\delta = \frac{\text{MAE}\left(D(\mathbf{z}^m_{\text{target}}), D(\mathbf{z}^m_{\alpha=1})\right)}{\text{MAE}\left(D(\mathbf{z}^m_{\text{start}}), D(\mathbf{z}^m_{\alpha=1})\right)}\) (12)

Here, \(\delta\) ranges from 0 (exact match to target) to 1 (no effect from altering dimensions).

### Decoder Details.

Each decoder \(D(\mathbf{z}^m_t)\) is trained for 50 epochs on representations from a specific module \(g^m_{enc}(\cdot)\), using the MSE loss, a learning rate of \(2 \times 10^{-4}\), and batch size 8. The decoder mirrors the encoder architecture, but for the first module, two additional layers (kernel size 3, padding 1, stride 1) were added to improve reconstruction.

### Results.

Table 2 shows the relative errors. Across all depths, SIM reconstructs the target signal using fewer dimensions than GIM. For the artificial dataset, GIM needs at least half of the dimensions for successful reconstruction, whereas SIM achieves similar results with just 1/8th. Given the limited information in this dataset, which theoretically requires far fewer than 512 dimensions, multiple of GIM’s dimensions seem sensitive to similar attributes. This implies a more entangled representation, which aligns with earlier findings in Fig. 3. For LibriSpeech, SIM consistently requires fewer dimensions, averaging around half the number used by GIM, showing potential to scale well to more complex datasets.

**Table 2.** Relative reconstruction error \(\delta\) (%) when only the \(N\) most important dimensions out of 512 are active. Lower values are preferred. GIM distributes relevant information across more dimensions than SIM.

| Module | Method | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 | 512 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 | 512 |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| \(g^1_{enc}\) | GIM | 99.32 | 98.71 | 97.6 | 95.46 | 91.2 | 82.35 | 62.96 | 24.33 | 0 | 95.55 | 91.77 | 87.47 | 81.12 | 71.65 | 58.02 | 39.52 | 16.8 | 0 |
| \(g^1_{enc}\) | SIM | 84.01 | 62.5 | 37.42 | 2 | 9.45 | 23 | 64.17 | 96.11 | 97.5 | 88.02 | 79.83 | 64.92 | 36.93 | 15.55 | 10.62 | 6.96 | 3.53 | 0 |
| \(g^2_{enc}\) | GIM | 98.86 | 97.91 | 96.17 | 93.07 | 87.58 | 77.8 | 59.81 | 27.46 | 0 | 97.35 | 94.88 | 90.82 | 84.7 | 76.6 | 67.02 | 54.25 | 31.32 | 0 |
| \(g^2_{enc}\) | SIM | 89.89 | 81.75 | 65.96 | 93.26 | 28.04 | 20.98 | 14.0 | 6.97 | 0 | 88.75 | 82.32 | 74.74 | 65.83 | 49.4 | 32.47 | 24.41 | 12.39 | 0 |
| \(g^3_{enc}\) | GIM | 99.01 | 98.16 | 96.59 | 93.9 | 89.29 | 81.09 | 65.23 | 31.76 | 0 | 94.37 | 90.65 | 85.08 | 78.1 | 71.47 | 65.68 | 57.0 | 35.95 | 0 |
| \(g^3_{enc}\) | SIM | 92.74 | 87.44 | 77.56 | 59.27 | 39.89 | 27.96 | 17.55 | 7.73 | 0 | 86.76 | 81.14 | 75.54 | 70.96 | 64.75 | 52.02 | 39.23 | 23.38 | 0 |

### Qualitative Analysis of Latent Shape.

To evaluate the structure of SIM’s latent space, we first compute the representations \(\mathbf{z}^3_t = g^3_{enc}(\mathbf{x}_t)\) for each sample from the test set. For each of their 512 dimensions, we construct a histogram with 100 bins, showing how all activations of the dataset for an individual dimension are spread. Figure 4 displays the histograms for a selected set of dimensions. SIM's activations consistently follow a Gaussian distribution, aligning with our design goal of regularizing the latent space toward a standard normal distribution. This predictable structure helps post-hoc interpretability tools by clearly describing the regions of interest. In contrast, the latent representations produced by GIM show greater variation. In particular, dimension 9 for the artificial dataset, and dimensions 13 and 14 for LibriSpeech are shifted away from the origin or differ from the other dimensions. Note that in GIM's current implementation, the latent spaces are implicitly constrained to center around the origin due to the use of a bias-free discriminator in Eq. 2. If the discriminator were non-linear or had a bias term, the shape of the latent space could potentially be even less predictable.

![](img/f56761e6196132d5b74909d98468408f_582_0.png)

Fig. 4. Top rows: Artificial Dataset, bottom: LibriSpeech. Distribution of activations per dimension. SIM's activations have a consistent shape across dimensions, whereas GIM enforces no latent space constraints, resulting in greater variation in certain dimensions. Other dimensions are available here.

## 5 Related Work

This work uses the benefits of \(\beta\)-VAE's regularization, applying them across multiple layers to improve post-hoc analysis of the network.

In terms of *interpretability through regularization*, various approaches have been explored. For instance, sparsity regularization in the activations of hidden representations [2,10,30] has been shown to improve the compression of information into fewer dimensions, reducing the number of neurons to analyze, yet this does not encourage disentanglement or smoothness. Similarly, [22] improves model interpretability through regularization of activations, modifying the model's behavior such that existing explainability methods produce explanations that better align with human perception. Another notable method involves tree regularization [32], which constrains neural networks to be well-approximated by decision trees, thereby improving interpretability. While effective, its applications are typically limited to simpler tasks where decision trees can easily be formed. In contrast, SIM relies on post-hoc tools for its analysis but is able to model complex audio or vision tasks. Regarding disentanglement, traditional methods have typically focused on regularizing a single layer in the architecture [6, 9, 12, 14, 15], whereas SIM applies one of these approaches in a new context and across multiple layers.

For *post-hoc interpretability*, SIM's decoder is similar to approaches like [8, 28], which reconstruct inputs from latent representations but rely on gradient ascent rather than a learned decoder. However, since NNs are not typically bijective, the reconstructions found do not necessarily map to a similar point from the dataset, resulting in often noisy and unclear reconstructions [8, 28]. To improve intelligibility, recent feature-activation-based methods incorporate human priors [20, 21, 23], guiding reconstructions toward more interpretable outputs. Decoders offer an alternative by directly learning to reconstruct inputs, implicitly encoding priors from the training data. However, they may introduce hallucinations that do not fully reflect the original model. Nonetheless, both gradient-based and decoder-based approaches could benefit from SIM's structured latent spaces due to their encouraged smoothness, better disentanglement, and well-defined shapes.

## 6 Discussion

We presented Smooth InfoMax, a self-supervised representation learning approach that incorporates interpretability into the design of the model. Our proposal demonstrates how \(\beta\)-VAE regularization can be integrated into GIM's contrastive learning framework at various depths in the network. As such, SIM enjoys GIM's computational advantages—such as decoder-less training, large-scale distributed training for architectures that would otherwise not fit in memory, and reduced vanishing gradients—while also preserving the well-structured latent space properties of \(\beta\)-VAEs across layers. Remarkably, this is achieved without significantly compromising performance. SIM enables more effective post-hoc interpretability, bringing us closer to understanding the internal workings of these neural networks.

### Limitations and Future Work.

Although the latent space properties of \(\beta\)-VAEs improve post-hoc interpretability, the overall success still depends on the faithfulness of the generated explanations and the clarity of the information encoded in the representations. Additionally, SIM shows a small performance
