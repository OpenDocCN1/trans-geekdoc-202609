196 Introduction to python

# Table A.7 Convolutional neural network—con'd

| to_categorical(X_test,70) Removes samples with NaN labels from the test samples index = |
| np.where(~np.isnan(y_test)) y_test = y_test[index[0]] X_test = X_test[index[0]:] |
| test_results.append(interactionModel.evaluate(X_test, y_test)) # Print the results on the |
| training samples print(np.mean(train_results,axis=0)) # Print the results on the test samples |
| print(np.mean(test_results,axis=0)) |

# References

+   - Amigó, E., Gonzalo, J., Artiles, J., & Verdejo, F. (2009). A comparison of extrinsic clustering metrics based on formal constraints. Information Retrieval, 12(4), 461–486.
- Camp, C. H. (2019). PyMCR: A python library for multivariate resolution analysis with alternating regression (MCR-AR). Journal of the National Institute of Standards and Technology, 124, 1–10.
- Cao, D. S., Liang, Y. Z., Jan, J., Tan, G. S., Xu, Q., & Liu, S. (2013). PyDPI: Freely available python package for chemformatics, bioinformatics, and chemomics studies. ACS Journal of Chemical Information and Modeling, 53(11), 3086–3096.
- Cao, D. S., Xu, Q. S., Hu, Q. N., & Liang, Y. Z. (2020). ChemPy: Freely available python package for computational biology. Bioinformatics, 29(8), 1092–1106.
- Moulton, I. P., Ferreira, M., & Helberg, A. S. (2020). A comparison of clustering algorithms for automatic modulation classification. Expert Systems with Applications, 151, 113317.
- Salgado, P. (2021). PEP 619–Python 3.10 release schedule.
- Stewart, J. J. (1990). MOPAC: A semempirical molecular orbital program. Journal of Computer-Aided Molecular Design, 4(1), 1–103.
- Van Rosum, G., & Drake, F. L. (1995a). Python reference manual. Amsterdam: Centrum voor Wiskunde en Informatica.
- Van Rosum, G., & Drake, F. L. (1995b). Python tutorial. Vol. 620. Amsterdam: Centrum voor Wiskunde en Informatica.
- Xu, D., & Tian, Y. (2015). A comprehensive survey of clustering algorithms. Annals of Data Science, 2(2), 165–193.