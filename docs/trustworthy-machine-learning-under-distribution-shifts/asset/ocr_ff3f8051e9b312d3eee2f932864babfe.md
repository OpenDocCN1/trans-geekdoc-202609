the effectiveness of MVT and demonstrate its superiority under various OOD scenarios on many well-known vision models.

To sum up, our contributions are threefold:

+   - We design a novel Machine Vision Therapy paradigm to enhance computer vision models by effectively leveraging the knowledge of MLLMs without needing additional label information.

+   - We propose a Denoising In-Context Learning strategy to successfully align MLLMs with vision tasks.

+   - Through comprehensive quantitative and qualitative studies on many well-known datasets, we demonstrate that the proposed method can enhance: (1) generalization on both ID and OOD data, (2) robustness against domain shift, (3) robustness against common corruptions, (4) performance on recognizing Fine-Grained attributes, (5) robustness against spurious correlations, (6) detection on prediction errors and OOD data.

# 5.2 Related Work

In this section, we provide a brief discussion of the OOD generalization problem and multimodal large-language models.

# 5.2.1 OOD Generalization

OOD data refers to those with different distributions from training data. OOD generalization aims at improving the performance of deep models to unseen test environments. Researchers attempted to tackle the problem from different perspectives, such as data augmentation, OOD detection, invariant causal mechanisms [152, 282, 283, 284], and so on. Data augmentation is effective in improving model generalization. Typical methods include Cutout [285], which randomly occludes parts of an input image; CutMix [286], which replaces a part of the target image with a different image; Mixup [287], which produces a convex combination