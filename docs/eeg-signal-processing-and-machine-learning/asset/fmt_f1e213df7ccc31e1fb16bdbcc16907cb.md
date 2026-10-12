
# Common Component Analysis

Common component analysis can be formulated as follows. Assume a set of high‐dimensional covariance matrices **X**[t] ∈ ℜ^(n×n), 1 ≤ t ≤ T. The key hypothesis driving the common component analysis concept is that the high‐dimensional covariance matrices are indeed a linearly transformed version of a set of low‐dimensional covariance matrices **Y**[t] ∈ ℜ^(r×r), 1 ≤ t ≤ T, i.e.:

(5.63)
```
X_t = U Y_t U^T + E_t
```
where **U** ∈ ℜ^(n×r) and **E**[t] is the residual matrix. In the above equation both **U** and **Y**[t] are unknown given that **U** is orthonormal. In order to estimate them, the following optimization is carried out:

(5.64)
```
min_{U, Y_t} Σ_{t=1}^T ||X_t - U Y_t U^T||_F^2 subject to: U U^T = I_r
```

This is called common component analysis because **U** determines a common subspace for all the covariance matrices. If there is only one covariance matrix **X**[1], then the model reduces to standard PCA. For more than one covariance matrices, the problem can be solved using tensor decompositions approaches.

## 5.13 Canonical Correlation Analysis

Another popular method for EEG analysis is called canonical correlation analysis (CCA). CCA is used to identify and measure the associations among two sets of variables. CCA determines a set of canonical variates, orthogonal linear combinations of the variables within each set that best explain the variability both within and between sets. In this decorrelation process, very similar to common spatial patterns (CSP), the sources are estimated from their mixtures in such a way that they are temporally maximally correlated and mutually uncorrelated. The main purposes for CCA are: (i) Data reduction: this explains the covariation between two sets of variables using small number of linear combinations and (ii) Data interpretation: this is to find features (i.e. canonical variates) that are important for explaining covariation between sets of variables.

Let **X** = (**x**[1], **x**[2], …, **x**[p])′ and **Y** = (**y**[1], **y**[2], …, **y**[q])′ with covariance matrices Σ[x] and Σ[y] respectively and cross‐covariance of Σ[xy]. Considering **U** = **W**[x]**X** and **V** = **W**[y]**Y**, the objective is to find the optimum **W**[x] and **W**[y] to maximize the correlation between **U** and **V** denoted as ρ(**U**, **V**):

(5.65)
```
ρ(U, V) = (W_x Σ_xy W_y^T) / (√(W_x Σ_x W_x^T) √(W_y Σ_y W_y^T))
```

CCA is used for feature detection [[168]](#c05.xhtml#c5-bib-0168) or source separation [[169]](#c05.xhtml#c5-bib-0169). There have been many applications of CCA to analysis of EEG signals such as in [[170]](#c05.xhtml#c5-bib-0170) for separation of muscle artefacts from EEG signals.

## 5.14 Summary

During the past two decades a large number of BSS methods have been proposed. A BSS problem becomes more difficult to solve when the signals are convolutively mixed, the number of sources is more than the number of sensors, the signals are nonstationary, or the system is nonlinear. In this chapter the BSS problem for different scenarios have been explained. Recently introduced tensor factorization approaches can highly alleviate these problems by relying on their three fundamental properties: first, they can map the signals into a multidimensional space where the sources can become disjoint; second, their ranks are often higher than any of the corresponding two‐dimensional representations of the data; and third, any related constraint can be easily incorporated to ensure the desired unique solution. The concepts in this chapter can be a good foundation for understanding many other approaches in BSS. The new techniques in underdetermined source separation allow k‐sparsity for which the number of active sources at each time can be very close to the number of mixtures. Representation of multichannel data, which vary from segment to segment and from subject to subject, in tensor form, efficiently exploits the data diversity for separation and classification purposes.

## References

1.  **1** Cardoso, J.‐F. (1997). Infomax and maximum likelihood for blind source separation. IEEE Signal Processing Letters 4 (4): 112–114.

2.  **2** Cardoso, J. (1989). Source separation using higher order moments. *Proceedings of the International Conference on Acoustics, Speech and Signal Processing (ICASSP)*, 2109–2112.

3.  **3** Mathis, H. and Douglas, S.C. (2004). On the existence of universal nonlinearities for blind source separation. IEEE Transactions on Signal Processing 50: 1007–1016.

4.  **4** Cohen, L. (1995). Time‐Frequency Analysis. Prentice Hall.

5.  **5** Platt, C. and Fagin, F. (1992). Networks for the separation of sources that are superimposed and delayed. In: Advances in Neural Information Processing Systems, vol. 4, 730–737. Morgan Kaufmann.

6.  **6** Herault, J. and Jutten, C. (1986). Space or time adaptive signal processing by neural models. *Proceedings of the AIP Conference on Neural Network for Computing*, 206–211. American Institute of Physics.

7.  **7** Torkkola, K. (1996). Blind separation of delayed sources based on information maximization. *Neural Networks for Signal Processing VI. Proceedings of the 1996 IEEE Signal Processing Society Workshop*, Kyoto, Japan, 423–432, 3509–3512. Atlanta, Georgia.

8.  **8** Torkkola, K. (1996). Blind separation of convolved sources based on information maximization. *Neural Networks for Signal Processing VI. Proceedings of the 1996 IEEE Signal Processing Society Workshop*, Kyoto, Japan, 315–323, 423–432.

9.  **9** Wang, W., Sanei, S., and Chambers, J.A. (2005). Penalty function based joint diagonalization approach for convolutive blind separation of nonstationary sources. IEEE Transactions on Signal Processing 53 (5): 1654–1669.
