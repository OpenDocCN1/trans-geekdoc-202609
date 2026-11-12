# Stable Vision Concept Transformers for Medical Diagnosis

Lijie Hu$^{1,2}$, Songning Lai$^{1,2}$, Yuan Hua$^{1,2,3}$, Shu Yang$^{1,2}$, Jingfeng Zhang$^{1,2,4}$, and Di Wang$^{1,2(\textcircled{S})}$

$^1$ Provable Responsible AI and Data Analytics (PRADA) Lab, Thuwal, Saudi Arabia
lijie.hu@kaust.edu.sa
$^2$ King Abdullah University of Science and Technology, Thuwal, Saudi Arabia
$^3$ Tsinghua University, Beijing, China
$^4$ University of Auckland, Auckland, New Zealand

Abstract. Transparency is a paramount concern in the medical field, prompting researchers to delve into the realm of explainable AI (XAI). Among these XAI methods, Concept Bottleneck Models (CBMs) aim to restrict the model's latent space to human-understandable high-level concepts by generating a conceptual layer for extracting conceptual features, which has drawn much attention recently. However, existing methods rely solely on concept features to determine the model's predictions, which overlook the intrinsic feature embeddings within medical images. To address this utility gap between the original models and concept-based models, we propose V ision C oncept T ransformer (VCT). Furthermore, despite their benefits, CBMs have been found to negatively impact model performance and fail to provide stable explanations when faced with input perturbations, which limits their application in the medical field. To address this faithfulness issue, this paper further proposes the S table V ision C oncept T ransformer (SVCT) based on VCT, which leverages the vision transformer (ViT) as its backbone and incorporates a conceptual layer. SVCT employs conceptual features to enhance decision-making capabilities by fusing them with image features and ensures model faithfulness through the integration of Denoised Diffusion Smoothing. Comprehensive experiments on four medical datasets demonstrate that our VCT and SVCT maintain accuracy while maintaining interpretability compared to baselines. Furthermore, even when subjected to perturbations, our SVCT model consistently provides faithful explanations, thus meeting the needs of the medical field.

Keywords: Explainable medical image classification · Explainability · Stability · Medical diagnosis

L. Hu, S. Lai, and Y. Hua—Equal contribution.

Supplementary Information The online version contains supplementary material available at https://doi.org/10.1007/978-3-032-06066-2_19.