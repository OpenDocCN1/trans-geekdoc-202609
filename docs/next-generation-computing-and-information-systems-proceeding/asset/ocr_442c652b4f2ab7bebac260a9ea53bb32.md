In the above Figure 4, the iteration of 5-dimensional images is shown in the form of cluster and bar graphs. The selected image (Pine Data set) has 5 phases, based on their visibility a log value has been plotted to identify the correct visible area of the pine. The B(1) and D(1) significantly improved visibility from 40% to 47%, which is 3% greater than the t-SNE algorithm (Kumari et al. 2021). For validation purposes, Tables 1 and 2 present the best underlying result obtained after applying PCA before applying RNN to the selected data set. In Table 1 the obtained accuracy is presented for the three selected methods (i.e., PCA, t-SNE & RNN). From these tables, it is clear that the RNN achieves a better and more stable result as compared to t-SNE and PCA algorithms. t-SNE tends to yield outcomes suggesting that this approach is more effective, in reducing the dimensionality of data samples. This characteristic is also evident, in the results obtained through Kernel t-SNE.

Table 1. For every iteration up to (20) shown in Figure 4, dimensionality reduction technique for each individual data set.

| Method | Pine-12 | Pine-13 | Pine-14 | Pine-16 | Pine-17 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| PCA | 0.99 | 0.93 | 0.9972 | 0.92 | 0.90 |
| t-SNE | 0.96 | 0.97 | 0.93 | 0.97 | 0.91 |
| RNN | 0.98 | 0.97 | 0.99 | 0.94 | 0.96 |

Table 2. For every cluster up to (20) data-points shown in Figure 4, dimensionality reduction technique for each individual data set.

| Method | TF 2012 | TF 2013 | TF 2014 | TF 2016 | TF 2017 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| PCA | 0.9965 | 0.9944 | 0.9978 | 0.9912 | 0.9866 |
| t-SNE | 0.9966 | 0.9942 | 0.9910 | 0.9954 | 0.9926 |
| Kernel t-SNE | 0.9857 | 0.9539 | 0.9571 | 0.9852 | 0.9773 |

Ultimately, the combination of RNN and PCA surpassed all other approaches in every respect. The calculation speed was excellent, being the second fastest. Additionally, it successfully demonstrated the presence of well-separated clusters, which were anticipated. PCA is used for pre-processing datasets before linear RNN training. Only one model underwent PCA pre-processing. Both RNNs had 25 first-layer nodes and two second-layer nodes. Table 1 highlights the superiority of PCA, with high accuracy scores (e.g., Pine-14: 0.9972). While t-SNE also performed well, it didn’t consistently surpass PCA. The efficacy of our RNN models, especially when coupled with PCA preprocessing, is evident in the competitive error differences detailed in Table 1. In Table 2 we can see how PCA consistently achieved accuracy scores ranging from 98.65%, to 99.78% surpassing the performance of both t-SNE and Kernel t- SNE. Although t-SNE and Kernel t-SNE also performed well in the TF 2012 and TF 2014 datasets PCA maintained its superiority. These findings highlight the reliability of PCA in preserving the structure of data during dimensionality reduction. This underscores the computational efficiency and predictive power of our proposed approach.

# 4 CONCLUSION

PCA may enhance predicted outcomes for linear RNN problems. This study shows that PCA preprocessed data typically yielded more accurate predicted findings. Unfortunately, it isn’t always clear whether an RNN has been designed for a linear or nonlinear problem. MLP networks are trained using recorded observations, not deterministic equations like those utilized in this paper. RNN training without PCA preprocessing is possible if the problem’s linearity is unknown. If an MLP network trained using PCA-processed data outperforms its