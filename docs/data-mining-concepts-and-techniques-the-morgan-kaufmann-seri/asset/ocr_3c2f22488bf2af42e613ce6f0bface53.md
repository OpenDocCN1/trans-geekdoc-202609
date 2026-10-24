![](bbox=[0.15, 0.12, 0.82, 0.61])

FIGURE 7.14 Information gain vs. pattern frequency (support) for three UCI data sets. A theoretical upper bound on information gain ($IG_{Upper Bound}$) is also shown. Source: Adapted from Cheng, Yan, Han, and Hsu [CYHH07].

+   2. Feature selection: Apply feature selection to F, resulting in FS, the set of selected (more discriminating) frequent patterns. Information gain, Fisher score, or other evaluation measures can be used for this step. Relevancy checking can also be incorporated into this step to weed out redundant patterns. The data set D is transformed to D', where the feature space now includes the single features and the selected frequent patterns, FS. Commonly used feature selection methods were introduced in Section 7.1.

+   3. Learning of classification model: A classifier is built on the data set D'. Any learning algorithm can be used as the classification model.

The general framework is summarized in Fig. 7.15(a), where the discriminative patterns are represented by dark circles. Although the approach is straightforward, we can encounter a computational