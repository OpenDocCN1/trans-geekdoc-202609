![](bbox=[0.05, 0.05, 0.95, 0.35])

the corresponding label, to be in the labeled set L. ε should be high enough to avoid incorrect labeling. The classification model C is updated by retraining the classifier using L. Model R is comprised of only the cooccurrence matrix ψ and it is incremented using the new labeled instances.

# 3.2.4 Applications

In this section, we discuss a few applications where context-aware active learning can be utilized to reduce the manual labeling effort. We primarily discuss three different applications – joint scene-object classification, activity recognition, and document classification. As shown in Fig. 3.4, the applications have data that share relationships among them. We use linear classifiers such as Support Vector Machine (SVM) (Chang and Lin, 2011) as a baseline classifier in all the applications discussed next. In active learning, methods are compared against the full-set performance, i.e., the performance obtained when all the data points (except the test set) are labeled and used for training. We also compare with other popular active learning methods in literature, i.e., Batch Rank (Chakraborty et al., 2015), BvSB (Li et al., 2012), Entropy (Settles, 2012; Holub et al., 2008), Density-Based Sampling (DENS) (Settles, 2012), Expected Gradient Length (GRL) (Settles and Craven, 2008) and Random Sampling.

# Scene-object classification

Scene and objects tend to cooccur in images. Although scene and object classifiers are separate, their joint understanding can be beneficial (Yao et al., 2012), which can be exploited