The SN includes preprocessing, feature extraction, feature reduction, feature concatenation and classification stages. The pictorial description of the SN is shown in figure 2.1.

As shown in figure 2.1, signal concatenation, DCT and FFT are used in preprocessing to generate secondary signals. SVD and TP are chosen as feature extractors. The extracted SVD-based and TP-based features are concatenated and two types of features are obtained. These are SVD-based and TP-based features. Finally, 2560 TP-based and 80 SVD-based features are extracted from an sEMG signal. In the feature reduction phase, firstly NCA generates weights then these weights and a tangent sigmoid-based feature reduction method are applied onto TP- and SVD- based features. 10-fold cross-validation is employed to obtain results. The milestones of the SN are explained in the subsection.

![](bbox=[0.17, 0.35, 0.83, 0.86])

Figure 2.1. The block diagram of the SN.