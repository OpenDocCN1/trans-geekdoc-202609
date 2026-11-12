
## 1 Introduction

Spoilers in movie reviews have become an important component of the movie-viewing experience on popular platforms like IMDb and Rotten Tomatoes [5]. For those who hope to learn the plot of the movie in advance to judge whether they like it or not, the spoilers are helping, while for those who prefer to experience a movie without prior knowledge, the spoilers can severely diminish the enjoyment by revealing crucial plot points, undermining suspense, and eliciting negative emotions among viewers [21]. Thus, effective spoiler detection methods are crucial for maintaining a positive user experience (Fig. 1).

![](img/f56761e6196132d5b74909d98468408f_86_0.png)

Fig. 1. An illustrative example of the data used in our spoiler detection study. The image shows a review of the movie Moana, including the movie's genres (Adventure, Animation), summary, the review's content, and user-specific details. All reviews from the user are color-coded: blue indicates non-spoiler content, while red indicates spoiler content.

Existing spoiler detection methods primarily focus on the textual content of reviews. For example, DNSD [6] integrates review sentences and movie genres, while SpoilerNet [36] utilizes a Hierarchical Attention Network and incorporates the item-specificity information. More recent approaches, such as MVSD [38], incorporate advanced techniques like syntax-aware graph neural networks and external movie knowledge to improve detection performance. Nevertheless, these methods still exhibit notable limitations. Solely relying on textual content proves insufficient for robust spoiler detection [38]. Moreover, spoilers are often genre-specific, with varying characteristics depending on the movie's genre—for instance, suspense films focus on plot details, whereas action films emphasize fight scenes. As a result, two significant challenges in spoiler detection remain unaddressed:

![](img/f56761e6196132d5b74909d98468408f_87_0.png)

Fig. 2. (a) Spoiler rate across different movie genres (partial) in LCS dataset. (b) Kernel density estimation plot and distribution histogram of spoiler across different users.

- **Diverse Genres**. Previous works have largely ignored the impact of movie genres on the spoiler rate. Our analysis of the dataset indicates substantial differences in spoiler rate across genres, with specific categories defined according to IMDb standards. As shown in Fig. 2(a), movies that heavily rely on plot twists and suspense, such as Film-Noir and Adventure, are more prone to having spoilers in reviews compared to genres like Musical or Documentary. This is understandable since plot-driven movies tend to have more critical plot points that can be spoiled. This variation in spoiler rate demonstrates the importance of considering genre-specific characteristics when developing spoiler detection models. By incorporating genre information, we could better capture these differences and improve the performance of spoiler detection.

- **User-specific Behavior Bias**. User behavior varies significantly, with some users being more prone to posting spoilers than others. Our statistical analysis shows a clear trend where certain users tend to post spoiler reviews more frequently. As illustrated in Fig. 2(b), the graph of user spoiler review distribution shows that a large proportion of users post very few spoilers, while a smaller, yet significant, group of users frequently post spoilers. This distribution indicates a noticeable user bias, highlighting that certain users are more likely to post spoilers than others. Leveraging these user-specific behavior bias can improve the detection performance by allowing models to adapt to user behavior bias.

To address the challenges of genre-specific spoiler tendencies and user bias in spoiler detection, we propose a comprehensive framework named GUSD (Genre-aware and User-specific Spoiler Detection). This framework integrates genre information, user behavior bias, and global perception GNN. Our method begins with preprocessing movie, user, and review data. Then user bias is captured from review history through dynamic graph modeling. After that, the core component, R2GFormer (RetGAT and GenreFormer), which consists of RetGAT (Retentive Graph Attention Network) and GenreFormer, processes the graph information. RetGAT aggregates all the features globally, and GenreFormer enhances representation by integrating genre features, allowing for comprehensive genre-specific and cross-genre interactions. And an Aggregator combines these features, and then the GMoE (Genre-Aware Mixture of Experts) model assigns reviews to different experts based on their corresponding movie genres, improving traditional MoE model performance. Finally, a classifier performs spoiler detection using the aggregated features.

Extensive experiments show that GUSD achieves state-of-the-art performance. We also conduct robustness studies, ablation studies, and specific experiments on GMoE and user bias to validate our proposed modules' effectiveness.

## Our main contributions are summarized as follows:

- We are the first to model the complex interactions between genre-specific information and long-term user review behaviors for spoiler detection, providing a nuanced approach by understanding genre-specific spoiler characteristics and leveraging user behavior bias.

- We propose the GUSD framework, a novel spoiler detection system that integrates several key components: the GenreFormer to capture genre-specific spoiler tendencies, the GMoE model to dynamically assign reviews based on genres, and dynamic graph modeling to capture user bias. This cohesive integration enhances overall accuracy and robustness.

- Our method GUSD achieves state-of-the-art performance in spoiler detection. Extensive experiments on two benchmark datasets demonstrate its robustness and effectiveness, showing superior performance across various conditions.

## 2 Related Work

### 2.1 Spoiler Detection

The goal of automatic spoiler detection is to identify spoilers in reviews from domains like television [3], books [36], and movies [3]. Existing approaches to spoiler detection can be broadly classified into three categories: keyword matching methods, machine learning techniques, and deep learning models.

**Keyword Matching Methods.** These approaches rely on a set of predefined keywords to identify spoilers. Examples include keywords related to sports teams or events [25], or actors’ names [12]. Although useful in specific scenarios, this method requires manual keyword definition and lacks generalizability across different application contexts.

**Machine Learning Techniques.** These methods often involve topic modeling or support vector machines using handcrafted features. For example, Guo et al. [13] applied a bag-of-words representation combined with an LDA-based model for spoiler detection. Jeon et al. [16] developed an SVM classifier incorporating four extracted features, while Boyd et al. [3] utilized lexical features and meta-data of review subjects (e.g., movies and books) in an SVM model.

**Deep Learning Models.** These models mainly leverage NLP techniques, employing RNNs, LSTMs, Transformer, and language models to process review texts and movie information through end-to-end training. Bao et al. [2] utilized LSTMs, BERT, and RoBERTa for sentence-level spoiler detection. DNSD [6] focused on incorporating external genre information using GRU and CNN. SpoilerNet [36] introduced item-specificity and bias with bi-RNN enhanced by GRU. SDGNN [7] leveraged dependency relations between context words in sentences with graph neural networks to capture semantics.

While some existing methods incorporate genre information and user bias [6,40], they often rely on quite simple techniques such as concatenating or adding these additional features to the initial review features. Such approaches lack the sophistication needed for more effective and intricate modeling of genre features and user biases.

### 2.2 Mixture of Experts

The Mixture of Experts (MoE) approach, grounded in the Divide-and-Conquer principle, segments an input sample into sub-tasks and trains specialized experts for each sub-task. This method is extensively utilized in NLP to boost model capacity [33] and enhance reasoning capabilities [23]. Shazeer et al. [33] introduced a sparsely-gated Mixture-of-Experts layer, enabling conditional computing in large language models. Fedus et al. [10] developed simplified routing algorithms for MoE to enhance training stability and reduce computational costs. Furthermore, Soft-MoE [29] was introduced to mitigate issues like training instability and token dropping inherent in traditional MoE approaches.

Despite these advancements, traditional MoE methods assign tokens dynamically, which can cause incorrect token assignment, particularly when the dataset contains explicit category information such as movie genres and their associated reviews.

## 3 Methodology

Figure 3 shows the architecture of our proposed GUSD framework. This framework integrates genre-specific information, user behavior bias, and global receptive RetGAT for spoiler detection. Specifically, movie, user, and review data are first to be preprocessed, while user bias is extracted from review history using dynamic graph modeling. The R2GFormer component, consisting of RetGAT and GenreFormer, then processes graph features. RetGAT aggregates graph data, while GenreFormer handles genre-specific data. An Aggregator aggregates these features. The GMoE model assigns reviews to experts based on their related movie genres. Finally, a classifier utilizes the aggregated features to detect spoilers.
