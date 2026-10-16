+   - Then we can rotate it with an orthogonal $R$, giving $RSW$. Since $R$ is orthogonal, $R^T R = I$. Its covariance matrix is $\Sigma_{RSW} = (RSW)^T RSW = W^T S^T R^T RSW = W^T S^2 W$.

Squaring a matrix is a bit complicated, but it turns out the $S$ only has entries on its diagonal and squaring it means we just square the values on the diagonal. Crisis averted.

If we now work backwards, from the end data $RSW$ and the end covariance matrix $\Sigma_{RSW}$, we have

+   - From EIGD on the covariance matrix: eig($\Sigma_{RSW}$) gives $\Sigma_{RSW} V = V L$ or $\Sigma_{RSW} = V L V^T$.
+   - From SVD on the data matrix: svd($RSW$) = $(U D V^T)^T U D V^T = V D U^T U D V^T = V D^2 V^T$.

Subject to a few caveats, we can identify $RS$—our stretching and rotating—with $V L$ and $V D^2$. In the real world, we start with interesting data that comes to us in the form of $RSW$. We don’t see the component pieces. Then we use SVD or EIG to figure out the $RS$ that could conceptually get us from white-noise data to the data we observed.

# PCA’s Crew: PPCA, FA, and ICA

PCA can be related to several other techniques: probabilistic PCA (PPCA), factor analysis (FA), and independent component analysis (ICA). All of these techniques can be used in a fashion similar to PCA: create newly derived features and keep fewer of them than what we started with.

PCA is closely related to PPCA and FA. All of these techniques care about accounting for the variance in the data but they make different modeling assumptions about the nature of the covariance of the data being analyzed. PCA takes the covariance matrix as is. PPCA adds a shared random amount of variance to each feature. FA adds varying random amounts of variance to each feature.

ICA swaps out maximizing variance for maximizing kurtosis. There are other ways of describing and understanding ICA as well; ICA has an interpretation as minimizing mutual information. Kurtosis is a characteristic of distributions similar to the mean and variance. The mean is the center of the data and the variance is the spread of the data; kurtosis—loosely (there are several quibbles with most verbal descriptions)—describes how heavy the tails of the data are or how quickly the probability curve drops off to zero. Practically speaking, while PCA wants to find directions that account for variance and are orthogonal (uncorrelated) from one another, ICA wants to find directions that are maximally statistically independent from one another.

# Manifolds

My discussion of manifolds blended the general idea of manifolds with the more specific idea of differentiable manifolds. Now you know why I didn’t mention it in the main text. But the details are that manifolds have some nice equivalence with Euclidean space—our normal playground for graphing datasets and functions. Differentiable manifolds are a bit more strict: they have an equivalence with linear subsets of Euclidean space. If you recall your calculus, you took derivatives by approximating—with a line—the slope at very, very small intervals of a function. Differentiable manifolds extend