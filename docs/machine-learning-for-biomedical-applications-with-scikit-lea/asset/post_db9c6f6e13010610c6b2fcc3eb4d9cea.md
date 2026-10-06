
# loop over batches

```
for i, (data, labels) in enumerate(data_test_loader):
    # predict the labels for the batch
    data = data.to(device).detach().cpu()
    pred = torch.argmax(pred, dim=1)
    # loop over images in the batch
    for j in range(pred.shape[0]):
            # flatten to vectors
            y=labels[j,...].flatten()
            y_pred=pred[j,...].flatten()
            # calculate and save the scores
            f1_scores.append(f1_score(y,y_pred))
            prec_scores.append(prec_score(y,y_pred))
            recall_scores.append(recall_score(y,y_pred))
```

```python
# print out scores averaged over test images
print('f1 score:',np.round(np.mean(f1_scores),2))
print('precision:',np.round(np.mean(prec_scores),2))
print('recall:',np.round(np.mean(recall_scores),2))
>>> f1 score: 0.9
>>> precision: 0.94
>>> recall: 0.87
```

The performance of the segmentation network is good. Dice score (F1 score) 0.9 for the complicated structure such as cortex is quite high. Precision is higher than recall, so we can say that the network is better at not making a mistake with a positive prediction (a pixel belongs to the cortex) than with correctly identifying all the pixels that belong to the cortex ground truth. In other words, the network is slightly more likely to miss some cortical pixels than assign the background pixels to the cortex.

# 11.4.5 Exercises

- 1. Implement the segmentation of cortex in 2D Neonatal MRI by following the code in this section.
- 2. Modify the NeonatalDataset class to predict white matter, instead of cortex, by taking pixel values in interval [165, 215] as the white matter label.

> 8 Dataset, skeleton code and solution is available from github.com/MachineLearningBiomedicalApplications/notebooks.

- 3. Modify the code to perform multi-label segmentation of 5 classes: background (0), CSF (1), cortex (2), white matter (4). To obtain the labels, you can process the segmentations in the NeonatalDataset object with

```python
seg = np.round(labels/62.5,0)
```

Note that you also need to change the number of outputs of the UNet object to five. Evaluation also needs to be performed for each label sample. For details of how to evaluate performance of multi-label segmentation, see Sect. 4.1.5. Hint: You will need to increase the number of feature maps in the lowest-level encoder convolution and the decoder convolutions.

# 11.5. Conclusion

Congratulations! You have just trained and evaluated your first advanced neural network for image segmentation. And this is where the learning objectives of this book have been fully achieved. Of course, there is so much to learn: Machine learning and deep learning, in particular, are very fast evolving fields, with new ideas, algorithms and concepts being generated every year. There are many more architectures to learn, such as attention mechanisms, visual transformers and generative adversarial networks, which are all widely used in biomedical applications. We hope that the strong foundation that you gained while studying the material in this book will motivate you to confidently explore these advanced concepts. And, as importantly, we hope that you enjoyed learning with us!

# References

[1] C. Bass, M. Silva, C. Sudre, P. Tudius, S. Smith, E. Robinson, ICAM: interpretable classification by disentangled representations and feature attention mapping; in NeurIPS 2020, 2020.

[2] M. Belkin, P. Niyogi, Laplacian eigenmaps for dimensionality reduction and data representation, Neural Computation 15 (6) (2003) 1373–1396.

[3] J. Borg, P. Groenen, M. Torgndner Multidimensional Scaling: Theory and Applications, Springer Science & Business Media, 2008.

[4] L. Breiman, Bagging, predictors, Machine Learning 24 (2) (1996) 123–140.

[5] L. Breiman, Random forests, Machine Learning 45 (1) (2001) 5–32.

[6] L. Buitinck, G. Goulee, M. Blondel, F. Pedegosa, A. Mueller, O. Grisel, V. Niculae, P. Prettenhofer, A. Gramfort, G. Jobbert, R. Layton, J. Vanderplas, A. Jolly, B. Holt, G. Varquaux, API design for machine learning software engineering; in: ECML PKDD Workshop: Languages for Data Mining, 2013, pp. 108–122.

[7] C.-C. Chang, C.-J. Lin, SVM: library for support vector machines, ACM Transactions on Information Systems and Technology 2 (3) (2011) 1–27.

[8] J.R. Clark, D.-R. Balbour, P. Marsden, C. Prieto, A. Jaeger, A.P. King, MRI slicing using manifold learning software engineering project; in: 2018 IEEE 15th International Symposium on Biomedical Imaging (ISBI), 2018, IEEE, pp.319–323.

[9] T.M. Cooper, J.A. Thomas, et al., Entropy rate and mutual information, Elements of Information Theory 2 (1) (1999) 12–23.

[10] Antonini Carini, James Shotton, Ernst Komodoglu, Decision trees: a unified framework for classification, regression, and manifold learning and semi-supervised learning, Foundations and Trends in Computer Graphics and 7 (3-2012) 81–227.

[11] D.L. Noble, C. Grimes, Hessian eyeglasses: locally linear embedding techniques for high-dimensional data, Proceedings of the National Academy of Sciences 100 (15) (2003) 5591–5596.

[12] H. Drucker, Improving regression using boosting techniques; in: ICML. Citeseer, 97, 197.

[13] A.P.D. Edwards, D. Ruckert, S.M. Smith, S. Ao Sena, A. Linarsky, J. Albambis, J. Johnson, T. Tonichi, A. Arkulov, M. Bakstiani, D. Batelle, L. Baxter, J. Boazek, E. Braithwaite, J. Jordan, O. Carney, A. Chevy, D. Davisson, R. Wright, C. Chung, K. Cordford, C. Londonero-Grande, S.J. Counsel, H. Cullen, J. Caputt, C. Curtis, A. Davidson, M. Deprez, L. Lincoln, D. Rimikoupol, R. Dimitrov, E.J. Hughes, J. Hunter, M. J. Hall, S. Johnson, J. Jones, V. Kahlis, V. Kyriakopoulos, G. Ley, A. Makropoulos, S. Malik, L. Fossati, N. Casarsli, R. G. Nunes, C. O’Keefe, J. O’Keefe-heartag, H. Patel, J. Passerat-Palmbach, M. Pietnich, A.N. Price, E.C. Robinson, M.A. Rutherford, A. Schuluth, S. Pododius, S. Reinwig, P.A. Tegmark, T. Teney, D.-J. U, N. Us, A. Vchenko, L. Vito, W. Williams, R. Wright, The developing human project related data.

[14] Ehthemi, M. Ta, P. Johannes van Diest, N. Gneken, K. Arsemijer, L. Litgens, A.M.W. der Kla, CAMELY16: diagnostic assessment of deep learning for detection of lymph node metastases in breast cancer, JAMA 318 (2017).

[15] Y. Freund, R.E. Shapira, A. A theoretical generalization of on-line learning and an application to boosting, Journal of Computer Systems 55 (1) (1997) 119–139.

[16] J.H. Friedman, Greedy function approximation: a gradient boosting machine, The Annals of Statistics (2001) 1189–1232.

[17] K.. Garcia, E.C. Robinson, D. Alexopoulos, D. Dierker, M.F. Geiger, T.S. Cool, C.M. Ortman, D. Rueckert, L.A. Taber, D.C. Essen, Dynamic patterns of cortical expansion during folding of the preterm brain, Proceedings of the National Academy of Sciences 115 (12) (2018) 3156–3161.

[18] Grigrescu, L. Cordero, A.D. Edwards, J. Hajnal, M. Deprez, Interpretable convolutional networks for birth classification, Medical Imaging in Deep Learning, MIDL, 2019.

[19] C.R. Harris, K.J. Millman, S.J. van Walt, R. Gommers, P. Courpeau, E. Wieser, J. Taylor, N. Berg, S. Hoyer, M. Pikus, J. Kerk, K. Brett, A. Haldane, M. F. J. Johnson, S. J., R. R., Array programming with NumPy, Nature in Science & Engineering 5 (785), A. A, S. J, L. Vito, R. Wright, The developing human project.

[20] J.D. Hunter, Matlab: a graphics engine, Computing in Science 9 (3) (2007) 90–95.

[21] A. Huaymin, Batch normalization: algorithms and applications, Neural Networks 33 (5) (2000) 411–430.

[22] I. Sooffe, Batch normalization: stabilizing deep neural network training by internal covariate shift, arXiv:1502.03167, 2015.

[23] E. Isensee, P. Jager, K.H. Maier, U-Net: self-configuring method for deep learning-based medical segmentation, Nature 18 (2021) 203–211.

[24] K. Mamatos, W. Ba, S. Ferrante, N. Sinclair, R. Pawlowski, D. Majchl, D. Lee, ensembles of multiple models and architectures for robust segmentation, in MICCAI, 2017, pp. 450–462.

[25] Diederik P. Kingma, Jimmy Ba, Adam: A Method for Stochastic Optimization, arXiv:1412.6980, 2014.

[26] A. Kulesa, M. Krzewynski, N. Altman, Sampling distributions and the bootstrap, Nature Methods 12 (2015) 477–478.

[27] Y. LeC, P. Paffier, H. Loffatto, Y. Bengio, Objective regularization with gradient-based learning, in Shape, Contour and Grouping in Computer Vision, Springer, Berlin, 1999, pp. 319–345.

[28] R. Duerck, A. Makopoulos, L.S. Gouvanos, C. Ledig, A. Serraj, Automated segmentation of the developing neonatal brain, IEEE Transactions on Medical Imaging 39 (2014) 1818–1823.

[29] The MathWorks Inc., MATLAB: version 9.1(R2022), Massachusetts, 2022.

[30] J.J. O'Meara, E.C. Robinson, M. Pietch, T. Wolfers, D. Batalle, K. Vecchiato, J. Hotter, R.P.G. Teijenga, E. Jura, K. Fitzberg, H. Hughes, A.N. Price, D. Reukert, R. Rutherford, S. Cowan, Application of deep learning to detect direct white matter injury in neonatal born infants, 34 (2) (2020) 467–479.

[31] Travis Elifant, A Guide to NumPy, version 1, Technical Publishing, USA, 2019.

[32] A. Pazke, S. Gross, F. Massa, J. Bradley, G. Chanson, K. Tillen, N. Gnelish, L. Vong, A. Demaison, E. Karp, Y. van Dijk, M. Raison, S. Kilambkurty, B. Steiner, F. Jang, B. Su. Chen, Contrastive learning in an imperative high-style, high performance deep learning, in W. Hall, H. Wallack, L. Archechelas, Y. Gelmaier, F. D'Albuche, E. Fox, R. Garner (Eds.), Advances in Neural Information Processing Systems, 32, Curran Associates, Inc., 2019.

[33] F. Pedregosa, G. Varquaux, A. Gramfort, V. Michel, B. Thilion, O. Grnel, M. Molnar, A. Muller, J. Nathan, G. Luque, P. Petchesauer, R. Weiss, V. Dubbous, J. Vanderplas, A. Pasos, D. Courpeau, M. Perrot, M. Picard, and., Scikit-learn: machine learning library, Journal of Machine Learning 12 (2021) 2825–2839.

[34] F-Pérez-García, R. Sparks, S. Ourselin, TORCH: a python library for efficient loading, preprocessing, augmentation and patch-based segmentation of medical images in deep learning, Computer Methods and Programs in Biomedicine (2021) 106–236.

[35] E. Puyol-Antón, B. Ruijsk, B. Gerber, M.S. Amzulescu, H. Langet, M. De Craene, J.A. Schnabel, P. Piro, A.P. King, Multi-view learning for cardiac motion analysis: application to identification of dilated cardiomyopathy, IEEE Transactions on Biomedical Engineering 64 (4) (2019) 956–966.
