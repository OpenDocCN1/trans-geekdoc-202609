![](bbox=[0.2, 0.1, 0.45, 0.49])

Figure 28. Flow chart of SVM Classification.

In the literature [19], there is a wavelet neural network (WNN) analog circuit soft fault diagnosis method based on kernel partial least square (KPLS) feature extraction, which uses support vector machine (KPLS-WNN-SVM) for fault classification. In the literature [20], a multifractal extraction method based on empirical mode decomposition is combined with support vector machine (EMD-MFD-SVM). The diagnostic rate of the diagnostic model combined with support vector machine (VMD-MMFD-KPCA-SVM) in this paper is shown in Table 7, which shows that the VMD-MMFD-KPCA-SVM method has the highest diagnostic accuracy.

Table 7. Fault Diagnosis Rate. 
Diagnostic Model | Average Diagnostic Rate (%) 
KPLS-WNN-SVM | 87.3 
EMD-MFD-SVM | 91.9 
VMD-MMFD-KPCA-SVM | 96.3

# 7. Conclusions

This paper proposes a feature-extraction method based on VMD-MMFD-KPCA. Firstly, the fault signal is decomposed by VMD to obtain multiple modal IMF components, which greatly reduces the impact of modal aliasing. The appropriate IMF components were selected, and the fractal dimension of the mathematical morphology was calculated to obtain a large number of high-dimensional feature data sets. The data sets were reduced by KPCA to obtain low-dimensional data, which eliminated a large number of redundant and jumbled information in the high-dimensional data. The experimental results show that the feature-extraction method based on VMD-MMFD-KPCA has a good effect.