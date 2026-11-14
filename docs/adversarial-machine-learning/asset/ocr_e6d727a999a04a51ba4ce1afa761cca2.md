# 6.3.2 PCA-GRID

The PCA-GRID algorithm introduced by Croux et al. (2007) is a projection pursuit technique as described in Equation 6.4. It finds a K-dimensional subspace that approximately maximizes \(S\{\cdot\}\), a robust measure of dispersion, for the data \(\mathbf{X}\) as in Equation (6.4). The robust measure of dispersion used by Croux et al. and also incorporated into ANTIDOTE is the well-known MAD estimator because of its high degree of distributional robustness—it attains the highest achievable breakdown point of \(\epsilon^* = 50\%\) and is the most robust M-estimator of dispersion (cf. Hampel et al. 1986, Chapter 2). For scalars \(r^{(1)}, \dots, r^{(T)}\) the MAD is defined as

\(\text{MAD} \{r^{(1)}, \dots, r^{(T)}\} = \text{median} \{ |r^{(i)} - \text{median} \{r^{(1)}, \dots, r^{(T)}\}| \} \quad (6.5)\)
\(S^{\text{MAD}} \{r^{(1)}, \dots, r^{(T)}\} = \omega \cdot \text{MAD} \{r^{(1)}, \dots, r^{(T)}\},\)

where the coefficient \(\omega = \frac{1}{\Phi^{-1}(3/4)} \approx 1.4826\) rescales the MAD so that \(S^{\text{MAD}}\{\cdot\}\) is an estimator of the standard deviation that is asymptotically consistent for normal distributions.

The next step requires choosing an estimate of the data's central location. In PCA, this estimate is simply the mean of the data. However, the mean is also not a robust estimator, so we center the data using the spatial median instead:

\(\hat{c}\{\mathbf{x}^{(t)}\} \in \underset{\boldsymbol{\mu} \in \mathbb{R}^D}{\operatorname{argmin}} \sum_{t=1}^T \|\mathbf{x}^{(t)} - \boldsymbol{\mu}\|_2\)

which is a convex optimization that can be efficiently solved using techniques developed by Hössjer & Croux (1995).

After centering the data based on the location estimate \(\hat{c}\{\mathbf{x}^{(t)}\}\) obtained above, PCA-GRID finds a unitary direction \(\mathbf{v}\) that is an approximate solution to Equation (6.4) for the scaled MAD dispersion measure. The PCA-GRID algorithm uses a grid search for this task. To motivate this search procedure, suppose one wants to find the best candidate between some pair of unit vectors \(\mathbf{w}^{(1)}\) and \(\mathbf{w}^{(2)}\) (a 2D search space). The search space is the unit circle parameterized by \(\phi\) as \(\mathbf{w}(\phi) = \cos(\phi)\mathbf{w}^{(1)} + \sin(\phi)\mathbf{w}^{(2)}\) with \(\phi \in [-\frac{\pi}{2}, \frac{\pi}{2}]\). The grid search splits the domain of \(\phi\) into a mesh of \(G + 1\) candidates \(\phi^{(k)} = \frac{\pi}{2}(\frac{2k}{G} - 1), k = 0, \dots, G\). Each candidate vector \(\mathbf{w}(\phi^{(k)})\) is assessed, and the one that maximizes \(S\{(\mathbf{x}^{(t)})^\top \mathbf{w}(\phi^{(k)})\}\) is selected as the approximate maximizer \(\hat{\mathbf{w}}\).

To search a more general \(D\)-dimensional space, the search iteratively refines its current best candidate \(\hat{\mathbf{w}}\) by performing a grid search between \(\hat{\mathbf{w}}\) and each of the unit directions \(\mathbf{e}^{(j)}\) with \(j \in 1 \dots D\). With each iteration, the range of angles considered progressively narrows around \(\hat{\mathbf{w}}\) to better explore its neighborhood. This procedure (outlined in Algorithm 6.1 approximates the direction of maximal dispersion analogous to an eigenvector in PCA.

To find the \(K\)-dimensional subspace \(\{\mathbf{v}^{(k)} \mid \forall j=1, \dots, K (\mathbf{v}^{(k)})^\top \mathbf{v}^{(j)} = \delta_{k,j}\}\) that maximizes the dispersion measure, the GRID-SEARCH is repeated \(K\)-times. After each