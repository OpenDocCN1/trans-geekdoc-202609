
$J\_{1}: = \frac{\text{trace}\{\Sigma\_{m}\}}{\text{trace}\{\Sigma\_{w}\}},\quad J\_{2} = \frac{|\Sigma\_{m}|}{|\Sigma\_{w}|},\quad J\_{3} = \text{trace}\left\{ \Sigma\_{w}^{- 1}\Sigma\_{b} \right\},$

where $|\cdot|$ denotes the determinant of a matrix. Note that large values of the previous criteria indicate good feature selection.

![Figure 7.10 Three different choices of two-dimensional feature spaces: (A) small within-class variance and small between-class distance; (B) large within-class variance and small between-class distance; and (C) small within-class variance and large between-class distance. The last one is the best choice out of the three.](images/B9780443292385000135/gr010.jpg)

The $J\_1$ criterion is the easiest to understand. To simplify the arguments, let us focus on the two-dimensional (two features, $x\_1$, $x\_2$) case involving three classes. Recall from the definition of the covariance matrix of a random vector $\mathbf{x}$ in Eq. [(2.31)](#Chp002_19-64_B9780443292385000081.xhtml) of Chapter [2](#Chp002_19-64_B9780443292385000081.xhtml) that the elements across the main diagonal are the variances of the respective random variables. Thus, for each class, $k = 1, 2, 3$, the trace of the corresponding covariance matrix will be the sum of the variances for each one of the two features, i.e.,

$\text{trace}\{\Sigma[k]\} = \sigma\_{k1}^2 + \sigma\_{k2}^2.$

Hence, the trace of $\Sigma\_w$ is the average total variance of the two features over all three classes,

$\text{trace}\{\Sigma\_w\} = \sum\limits\_{k = 1}^{3}P(\omega\_k)\left( \sigma\_{k1}^{2} + \sigma\_{k2}^{2} \right): = s\_w.$

On the other hand, the trace of $\Sigma\_b$ is equal to the average, over all classes, of the total squared Euclidean distance of each individual feature mean value from the corresponding global one, i.e.,
