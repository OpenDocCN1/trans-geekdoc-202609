
The tests carried out for two synthetic sources and different noise components [[85]](#c10.xhtml#c10-bib-0085) showed that the WL test has superior overall performance, and the AIC and WA perform well when the sources are close together.

These tests have been based on simulations of the sources and noise. It is also assumed that the locations and the orientations of the source dipoles are fixed and only the amplitudes change. For real EEG (or MEG) data, however, such information may be subject to change and generally unknown.

Probably the most robust approach for detection of the number of sources is that developed by Bai and He [[81]](#c10.xhtml#c10-bib-0081). In this approach an information criterion method in which the penalty functions are selected based on the spatiotemporal source model, has been developed to estimate the number of independent dipole sources from EEG or MEG. In this approach the following steps are followed:

1.  Calculating the covariance matrix `C[X]` from the measured data matrix `X`.

2.  Applying the SVD to decompose `C[X]` to obtain the eigenvalues `λ[i]`, where `λ[1] > … > λ[m]`.

3.  Calculating the information criterion value using the eigenvalues. The information criterion (`IC[k]`) can be calculated using either:

    [(10.88)](#c10.xhtml#R_c10-disp-0090)
    ```
    IC = w(n_e - k) log (1 / (n_e - k)) Σ_{i=k+1}^{n_e} λ_1 - w Σ_{i=k+1}^{n_e} log λ_1 + 2d(k, n_e)β(w)
    ```
    when the noise information is accurate. In [Eq. (10.88)](#c10.xhtml#c10-disp-0090) `d(k, m) = k(2m - k + 1)/2`. In places where the noise statistics is unknown or:

    (10.89)
    ```
    IC = -(w - 1 - k - (2(n_e - k)^2 + n_e - k + 2) / (6(n_e - k)) + Σ_{i=1}^k (λ̄_{n_e - k}^2 / (λ_i - λ̄_{n_e - k})^2)) · log(λ̄_{n_e - k}^{-(n_e - k)} Π_{i=k+1}^{n_e} λ_i) + 2d(k, n_e)β(w - 1)
    ```
    where in this equation `d(k, n_e) = k(n_e - k + 2)(n_e - k - 1)/2`, `λ̄_{n_e - k}` is the average of the `n_e - k` smallest eigenvalues. In both equations `n_e` is the number of electrode signals, `k` is the number of assumed dipole sources to be estimated, `w` is the number of time points to form a spatiotemporal data matrix, and `β(w)` is the penalty function which can have constant or logarithmic values [[81]](#c10.xhtml#c10-bib-0081).

4.  According to the rule of information criterion [[81]](#c10.xhtml#c10-bib-0081) the number of sources with minimum IC is selected as the estimated number of sources.

In various experiments it has been shown that in moderate noise environment, which is the case of EEG signals, the accuracy of the method is above 80%.

## 10.8 Other Hybrid Methods

In some other works the researchers have tried to better focus on the source of interest by applying some preprocessing of the data. As an example in [[90]](#c10.xhtml#c10-bib-0090), empirical mode decomposition followed by the wavelet transform have been used to filter the signals and focus on the sources within particular frequency bands active in certain time intervals. Then, multiple sparse priors (MSP) and iterative regularization algorithms have been used to solve the inverse localization problem.

In a recent review by Michel and Brunet [[91]](#c10.xhtml#c10-bib-0091) the different steps in brain source localization have been explained and a stand‐alone freely available academic software called Cartool has been used to illustrate the results of their analysis. In this article a brief table has been provided to illustrate various academic and commercial tools which can be used for source localization (see [Table 10.1](#c10.xhtml#c10-tbl-0001)). Most of these tools are used in many other EEG or MEG analyzes too.

## 10.9 Application of Machine Learning for EEG/MEG Source Localization

As stated in the previous sections of this chapter, the brain functional activity is associated with the generation of currents and resultant voltages which may be observed on the scalp as the EEG. The properties of the dipole sources may be studied by solving either the forward or inverse problems. The forward problem utilizes a volume conductor model for the head, in which the potentials on the conductor surface are computed based on an assumed current dipole at an arbitrary location, orientation, and strength. In the inverse problem, conversely, a current dipole, or a group of dipoles, is identified based on the observed EEG. Both the forward and inverse problems are typically solved by numerical procedures, such as a BEM and an optimization algorithm. The forward solutions require accurate head model and the inverse solutions are inaccurate, cannot handle multiple sources easily, and are computationally intensive.

**[Table 10.1](#c10.xhtml#R_c10-tbl-0001)** Most popular academic and commercial software packages that can be used for inverse solution to EEG source localization problems [[91]](#c10.xhtml#c10-bib-0091).
