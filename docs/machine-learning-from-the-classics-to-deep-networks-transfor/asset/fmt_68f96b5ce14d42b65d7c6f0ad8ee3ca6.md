
$||\mathbf{x}_{n} - \mathbf{x}||^{2} \approx ||\widehat{\mathbf{x}}_{n} - \widehat{\mathbf{x}}||^{2} = \left\| \sum\limits_{i = 1}^{m}z_{ni}\mathbf{u}_{i} - \sum\limits_{i = 1}^{m}z_{i}\mathbf{u}_{i} \right\|^{2} = ||\mathbf{z}_{n}^{(m)} - \mathbf{z}||^{2}$

![Equation](images/B9780443292385000263/si64.png)

where **z** : = [$z_{1}$, …, $z_{m}$]^{(T)}

![Equation](images/B9780443292385000263/si65.png). In other words, Euclidean distances are computed in the lower-dimensional subspace, which leads to substantial computational gains (see, for example, [22,63,160] and the references therein). This method is also known as *latent semantics indexing*.

### Orthogonalizing properties of PCA and feature generation

We will now shed light on PCA from a different angle. We have just discussed, in the context of the information retrieval application, that PCA can also be seen as a feature generation method that generates a set of new feature vectors, **z**, whose components describe a pattern in terms of the principal axes. Let us now assume (to make life easier) that *N* is large enough and the sample covariance matrix is a good approximation of the (full rank) covariance matrix $\Sigma = \mathbb{E}[\mathbf{x}\mathbf{x}^{(T)}]$

![Equation](images/B9780443292385000263/si66.png). We know that any vector $\mathbf{x} \in \mathbb{R}^{(l)}$

![Equation](images/B9780443292385000263/si67.png) can be described in terms of $\mathbf{u}_{1}$, …, $\mathbf{u}_{l}$

![Equation](images/B9780443292385000263/si68.png), that is,

$\mathbf{x} = \sum\limits_{i = 1}^{l}z_{i}\mathbf{u}_{i} = \sum\limits_{i = 1}^{l}(\mathbf{u}_{i}^{T}\mathbf{x})\mathbf{u}_{i}.$

![Equation](images/B9780443292385000263/si69.png)

Our focus now turns to the covariance matrix of the random vectors, **z**, as **x** changes randomly. Taking into account that
