

While copulae have been widely used in recent years for modelling dependence structures, using a copula requires parameter estimation and is usually suitable only for scenarios where all feature variables are of the same type. If only continuous feature variables are present, those three Archimedean copula‐based classifiers naturally perform better than CIBer. With the presence of `x₅`, a randomly discretized feature variable, which happens normally in practice (perhaps due to censoring and personal privacy, for example), CIBer steadily performs better than those three copula‐based classifiers. Instead of merely focusing on datasets with all feature variables of the same type, CIBer is designed to handle datasets with multiple feature variable types at the same time. In the real world, discrete, continuous, and categorical feature variables do appear in a dataset. Moreover, independence and comonotonicity are two extreme and universal dependence structures that are entirely non‐parametric. By making use of only these two dependence structures, CIBer can avoid complex computations, in contrast to classifiers based on specific parametric copulae, which also risk overfitting on the training dataset. CIBer is not prone to this error, and it demonstrates a promising performance on the test dataset. To echo the end of [Chapter 8](#c08.xhtml), CIBer can be regarded as a special case of the highly versatile vine copula, with an all‐or‐nothing treatment of the dependence among feature variables which does not lose much generality.

### 12.5.6 CIBer in Action in Finance and Insurance

A Python package has been created and is available for download on PyPI *(The Python Package Index*). It can be installed by the command `pip install CIBer`. As discussed in [Section 2.3](#c02.xhtml#c02-sec-0004), we shall first open a command terminal such as Anaconda Prompt, and then type the command in. The package will be downloaded automatically, as seen in [Figure 12.4](#c12.xhtml#c12-fig-0004), and an installation guide is available through the QR code in [Figure 12.5](#c12.xhtml#c12-fig-0005).

In this subsection, we demonstrate the effectiveness of CIBer versus some representative machine learners through the evaluation of several model assessment methods by analyzing two real datasets from finance and insurance:

1. **Bank Churners** [\[20\]](#c12.xhtml#c12-bib-0020): An important source of income for banks is the annual fees and charges paid by credit card holders. As a result, customer attrition is one of the major issues of concern. It is crucial for banks to predict whether a cardholder is likely to withdraw their credit card services because this can better facilitate their analysis on the attributing factors, helping them to improve their services in a timely manner.

   ![FIGURE 12.2 Boxplot of upper F 1‐scores for all classifiers in the simulation study.](images/c12f002.png)

   [**FIGURE 12.2**](#c12.xhtml#R_c12-fig-0002) Boxplot of `F₁`‐scores for all classifiers in the simulation study.

   ![FIGURE 12.3 Boxplot of accuracies for all classifiers in the simulation study.](images/c12f003.png)

   [**FIGURE 12.3**](#c12.xhtml#R_c12-fig-0003) Boxplot of accuracies for all classifiers in the simulation study.

   ![FIGURE 12.4 Downloading CIBer package in Python via terminal.](images/c12f004.png)

   [**FIGURE 12.4**](#c12.xhtml#R_c12-fig-0004) Downloading CIBer package in Python via terminal.

   ![FIGURE 12.5 GitHub for CIBer.](images/c12f005.png)

   [**FIGURE 12.5**](#c12.xhtml#R_c12-fig-0005) GitHub for CIBer.

2. **Default Premium Payment** [\[18\]](#c12.xhtml#c12-bib-0018): The on‐time collection of insurance premiums is crucial to insurance companies as this is a major component of their cash flow. However, policyholders may defer or even terminate premium payments due to various reasons. Therefore, it is important for insurance companies to be able to predict the emergence of such unfavourable events and alert their company agents to take timely action in advance.

Both datasets are highly imbalanced in nature. For example, a balanced dataset with roughly half of their customers in default would obviously bankrupt the company. We also note that there are some missing entries in both datasets. For simplicity, we assume the missing mechanism of *missing completely at random* and remove observations containing any missing entry. [Figure 12.6](#c12.xhtml#c12-fig-0006) shows the distribution of the labels in the bank churners (left) and default premium payment (right) datasets after missing entries are removed.

![FIGURE 12.6 Class label distributions of bank churners (left) and default premium payment (right) datasets after removing missing entries.](images/c12f006.png)

[**FIGURE 12.6**](#c12.xhtml#R_c12-fig-0006) Class label distributions of bank churners (left) and default premium payment (right) datasets after removing missing entries.

Next, we describe the experimental procedure for each of the two datasets. Since each dataset contains thousands of records, it suffices for us to (under‐)sample a small, yet representative enough, portion of the original dataset as our training dataset. We denote the training sample size by `n_train`. Next, we shall randomly pick `n_test` data points from each label of the remaining dataset as our test dataset, resulting in a testing size of `2 n_test`. The actual values of `n_train` and `n_test` for each dataset are subject to their original sizes of each binary label and hence their corresponding degrees of imbalance, which we shall state explicitly in the course of the following discussion. Algorithm 12.4 presents a summary of the experimental procedure.

As before, in implementing CIBer, we shall first discretize the continuous features by binning (referring to [Section 12.5.2](#c12.xhtml#c12-sec-0008)), and then perform a joint encoding scheme for categorical features. Comonotonic clusters are then identified using the AGNES algorithm with the totally‐ordered Kendall's `τ̂_como` ([12.17](#c12.xhtml#c12-disp-0042)) as the underlying association measure. The value of the maximum cluster‐wise distance `δ` is determined by grid search at the values of `0, 0.05, 0.1, 0.15, ..., 1`, with the `F₁`‐score as the assessment metric.

