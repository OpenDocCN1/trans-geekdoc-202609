![](bbox=[0.16, 0.07, 0.48, 0.3])

![](bbox=[0.52, 0.07, 0.84, 0.3])

![](bbox=[0.16, 0.33, 0.48, 0.56])

![](bbox=[0.52, 0.33, 0.84, 0.56])

Fig. 17. Gene importance of all genes pertaining to Dataset2 produced via ssvm1 (a), ssvm2 (b), ssvm3 (c), and lasso (d).

In terms of results retrieved via enrichment analysis tools, the ranking score indicates the order of the retrieved terms. The lower the value, the better the ranking is when the term is related to the studied experiment. The overlap indicates the number of common genes between uploaded genes and retrieved terms. For a given term Z, a value in the form of X/Y denotes that X is the number of common genes between the uploaded genes to Enrichr and the term Z, where Y denotes the number of genes related to term Z. P-values and adjusted p-values are related to the significant of retrieved terms with respect to the uploaded genes, where the former is calculated from Fisher exact test and the later is corrected with Benjamini-Hochberg method (Xie et al., 2021).

features and is derived based on the margin notion. However, lasso depends on linear models, including L1 penalty, to shrink coefficients to zero. According to our results in Section 3.2, results derived from our models relying on margin theory are better than those depending on linear models such as lasso (Ahn et al., 2020; Chen et al., 2022b; Feng et al., 2019).

In the “Sparse Models Explanation” section, we demonstrate important information pertaining to studied sparse models, including ssvm1, ssvm2, ssvm3, and lasso. Specifically, Figs. 14, 16, and 18 demonstrate the statistical significance of induced models, which are expected to acquire a good generalization when discriminating between the two classes of healthy controls and LP. However, Figs. 15, 17, and 19 explored induced sparsity, in which genes of weak discriminative power were set to zero. It can be observed that the additional constraint $\|W\|_1 \le \lambda$ enforced sparsity. Our models (i.e., ssvm1, ssvm2, and ssvm3) are based on SVM and therefore rely on the margin theory, in which the aim is to maximize the margin ($\frac{2}{\|W\|}$), which is equivalent to minimizing the margin ($\frac{\|W\|^2}{2}$) subject to additional constraints, as shown in Eqs. (1)–(4). The weight vector w provides importance of

We set parameters for the four methods as follows. ssvm1(c = 2, k = 1, $\lambda$ = 0.05), ssvm2(c = 2, k = 1, $\lambda$ = 0.05, r = 0.1), ssvm3(c = 2, k = 2, $\lambda$ = 0.05, r = 0.1), lasso($\lambda$ = 0.05). As the output of each of our methods was 100, the probability for other results coinciding with ours in the three datasets are ($\frac{1545}{\binom{100}{100}}$, $\frac{1916}{\binom{100}{100}}$, and $\frac{1355}{\binom{100}{100}}$, respectively; $\binom{n}{k}$ denotes the binomial coefficient, where n is the number of genes in the studied dataset and k refers to the number of genes selected by our method. Therefore, it is very unlikely that the results of other methods coincide with ours.

# 5. Conclusion and future work

Here, we introduce a computational framework consisting of machine learning coupled with enrichment analysis to identify important genes and drugs related to LP. The input to our framework was a gene expression dataset pertaining to healthy controls and LP patients; we downloaded three gene expression datasets from the gene expression omnibus (GSE63741, GSE193351, GSE52130). In each processed dataset, each sample was associated with a binary label (i.e., healthy