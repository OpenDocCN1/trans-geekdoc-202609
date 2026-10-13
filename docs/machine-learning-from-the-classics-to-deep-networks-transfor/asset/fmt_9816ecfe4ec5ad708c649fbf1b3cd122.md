
A number of algorithms have been developed around the idea of higher-order cumulants, which are also known as `tensorial methods`. Tensors are generalizations of matrices, and cumulant tensors are generalizations of the covariance matrix. Moreover, note that as the eigenanalysis of the covariance matrix leads to uncorrelated (principal) components, the eigenanalysis of the cumulant tensor leads to independent components. The interested reader can obtain a more detailed account of such techniques from [39,57,119].

#### ICA ambiguities

Any ICA method can (approximately) recover the independent components within the following two indeterminacies.

*   Independent components (ICs) are recovered to within a constant factor. Indeed, if `A` and `z` are the recovered quantities by an ICA algorithm, then `(1/a)A(1/a)A` and `az` is also a solution, as is readily seen from Eq. [(20.44)](#Chp020_1103-1179_B9780443292385000263.xhtml#deq59). Thus, usually the recovered latent variables (ICs) are normalized to unit variance.

*   We cannot determine the order of the ICs. Indeed, if `A` and `z` have been recovered and `P` is a permutation matrix, then `AP^(-1)` and `Pz` is also a solution, because the components of `Pz` are the same as those of `z` in a different order (with the same statistical properties).

### 20.5.3 Non-Gaussianity and independent components

The fourth-order (auto)cumulant of a random variable, `z`,

```
κ[4](z) = 𝔼[z⁴] − 3(𝔼[z²])²
```

is known as the `kurtosis` of the variable, and it is a measure of `non-Gaussianity`. Variables following the Gaussian distribution have zero kurtosis. Sub-Gaussian variables (variables whose PDF decays at a lower rate than the Gaussian for the same variance) have negative kurtosis. Super-Gaussian variables (corresponding to PDFs that decay at a higher rate than the Gaussian) have positive kurtosis. Thus, if we keep the variance fixed (e.g., for variables normalized to unit variance), maximizing the sum of squared kurtosis, it results in maximizing the non-Gaussianity of the recovered ICs. Usually, the absolute value of the kurtosis of the recovered ICs is used as a measure of ranking them. This is important if ICA is used as a feature generation technique. [Fig. 20.8](#Chp020_1103-1179_B9780443292385000263.xhtml#f0060) shows some typical examples of a sub-Gaussian and a super-Gaussian together with the corresponding Gaussian distribution. Also, another typical example of a sub-Gaussian distribution is the uniform one.

![Figure 20.8 A Gaussian (full-gray line), a super-Gaussian (dotted red line), and a sub-Gaussian (full-red line).](images/B9780443292385000263/gr008.jpg)

[Figure 20.8](#Chp020_1103-1179_B9780443292385000263.xhtml#cf0620) A Gaussian (full-gray line), a super-Gaussian (dotted red line), and a sub-Gaussian (full-red line).

Recall from Chapter [12](#Chp012_583-634_B9780443292385000184.xhtml) (Section [12.8.1](#Chp012_583-634_B9780443292385000184.xhtml)) that the Gaussian distribution is the one that maximizes the entropy under the variance and mean constraints. In other words, it is the most random one, under these constraints, and from this point of view the least informative with respect to the underlying structure of the data. In contrast, distributions that have the least resemblance to the Gaussian are more interesting as they are able to better unveil the structure associated with the data. This observation is at the heart of `projection pursuit`, which is closely related to the ICA family of techniques. The essence of these techniques is to search for directions in the feature space where the data projections are described in terms of non-Gaussian distributions [97,106].

### 20.5.4 ICA based on mutual information

The approach based on zeroing the second- and fourth-order cross-cumulants is not the only one. An alternative path is to estimate `W` by minimizing the `mutual information` among the latent variables. The notion of mutual information was introduced in Section [2.5](#Chp002_19-64_B9780443292385000081.xhtml). Elaborating a bit on Eq. [(2.158)](#Chp002_19-64_B9780443292385000081.xhtml) and performing the integrations on the right-hand side (for the case of more than two variables), it is readily shown that

```
I(z) = - H(z) + ∑(i=1 to l) H(z_i)
``` (20.51)
