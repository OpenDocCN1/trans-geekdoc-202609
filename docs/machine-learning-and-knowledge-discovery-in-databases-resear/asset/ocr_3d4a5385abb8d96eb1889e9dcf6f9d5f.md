sentation by integrating genre features, allowing for comprehensive genre-specific and cross-genre interactions. And an Aggregator combines these features, and then the GMoE (Genre-Aware Mixture of Experts) model assigns reviews to different experts based on their corresponding movie genres, improving traditional MoE model performance. Finally, a classifier performs spoiler detection using the aggregated features.

Extensive experiments show that GUSD achieves state-of-the-art performance. We also conduct robustness studies, ablation studies, and specific experiments on GMoE and user bias to validate our proposed modules' effectiveness.

# Our main contributions are summarized as follows:

+   - We are the first to model the complex interactions between genre-specific information and long-term user review behaviors for spoiler detection, providing a nuanced approach by understanding genre-specific spoiler characteristics and leveraging user behavior bias.

+   - We propose the GUSD framework, a novel spoiler detection system that integrates several key components: the GenreFormer to capture genre-specific spoiler tendencies, the GMoE model to dynamically assign reviews based on genres, and dynamic graph modeling to capture user bias. This cohesive integration enhances overall accuracy and robustness.

+   - Our method GUSD achieves state-of-the-art performance in spoiler detection. Extensive experiments on two benchmark datasets demonstrate its robustness and effectiveness, showing superior performance across various conditions.

# 2 Related Work

# 2.1 Spoiler Detection

The goal of automatic spoiler detection is to identify spoilers in reviews from domains like television [3], books [36], and movies [3]. Existing approaches to spoiler detection can be broadly classified into three categories: keyword matching methods, machine learning techniques, and deep learning models.

**Keyword Matching Methods.** These approaches rely on a set of predefined keywords to identify spoilers. Examples include keywords related to sports teams or events [25], or actors’ names [12]. Although useful in specific scenarios, this method requires manual keyword definition and lacks generalizability across different application contexts.

**Machine Learning Techniques.** These methods often involve topic modeling or support vector machines using handcrafted features. For example, Guo et al. [13] applied a bag-of-words representation combined with an LDA-based model for spoiler detection. Jeon et al. [16] developed an SVM classifier incorporating four extracted features, while Boyd et al. [3] utilized lexical features and meta-data of review subjects (e.g., movies and books) in an SVM model.