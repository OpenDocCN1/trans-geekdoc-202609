# Periodic kernels

The **periodic kernel** captures repeating structure, and has the form

$\mathcal{K}_{\text{per}}(r;\ell,p)=\exp\left(-\frac{2}{\ell^2}\sin^2\left(\pi\frac{r}{p}\right)\right)$

(17.23)

where $p$ is the period. See Fig. 17.4a for an illustration.

In the limit that $\ell \to \infty$, we get the **cosine kernel**:

$\mathcal{K}(r;p)=\cos\left(2\pi\frac{r}{p}\right)$

(17.24)

See Fig. 17.4b for an illustration.

# 17.2.2.2 Making new kernels from old

Given two valid kernels $\mathcal{K}_1(\mathbf{x},\mathbf{x}')$ and $\mathcal{K}_2(\mathbf{x},\mathbf{x}')$, we can create a new kernel using any of the following methods:

+   - $\mathcal{K}(\mathbf{x},\mathbf{x}') = c\mathcal{K}_1(\mathbf{x},\mathbf{x}')$, for any constant $c > 0$  (17.25)
+   - $\mathcal{K}(\mathbf{x},\mathbf{x}') = f(\mathbf{x})\mathcal{K}_1(\mathbf{x},\mathbf{x}')f(\mathbf{x}')$, for any function $f$  (17.26)
+   - $\mathcal{K}(\mathbf{x},\mathbf{x}') = q(\mathcal{K}_1(\mathbf{x},\mathbf{x}'))$ for any function polynomial $q$ with nonneg. coef.  (17.27)
+   - $\mathcal{K}(\mathbf{x},\mathbf{x}') = \exp(\mathcal{K}_1(\mathbf{x},\mathbf{x}'))$  (17.28)
+   - $\mathcal{K}(\mathbf{x},\mathbf{x}') = \mathbf{x}^\top \mathbf{A} \mathbf{x}'$, for any psd matrix $\mathbf{A}$  (17.29)

For example, suppose we start with the linear kernel $\mathcal{K}(\mathbf{x},\mathbf{x}') = \mathbf{x}\mathbf{x}'$. We know this is a valid Mercer kernel, since the corresponding Gram matrix is just the (scaled) covariance matrix of the data. From the above rules, we can see that the polynomial kernel $\mathcal{K}(\mathbf{x},\mathbf{x}') = (\mathbf{x}^\top \mathbf{x}')^M$ is a valid Mercer kernel. This contains all monomials of order $M$. For example, if $M = 2$ and the inputs are 2d, we have

$(\mathbf{x}^\top \mathbf{x}')^2 = (x_1x_1' + x_2x_2')^2 = (x_1x_1')^2 + (x_2x_2')^2 + (x_1x_1')(x_2x_2')$

(17.30)

We can generalize this to contain all terms up to degree $M$ by using the kernel $\mathcal{K}(\mathbf{x},\mathbf{x}') = (\mathbf{x}^\top \mathbf{x}' + c)^M$. For example, if $M = 2$ and the inputs are 2d, we have

$(\mathbf{x}^\top \mathbf{x}' + 1)^2 = (x_1x_1')^2 + (x_1x_1')(x_2x_2') + (x_1x_1')$
$\quad + (x_2x_2)(x_1x_1') + (x_2x_2')^2 + (x_2x_2')$
$\quad + (x_1x_1') + (x_2x_2') + 1$

(17.31)

We can also use the above rules to establish that the Gaussian kernel is a valid kernel. To see this, note that

$||\mathbf{x} - \mathbf{x}'||^2 = \mathbf{x}^\top \mathbf{x} + (\mathbf{x}')^\top \mathbf{x}' - 2\mathbf{x}^\top \mathbf{x}'$

(17.32)

and hence

$\mathcal{K}(\mathbf{x},\mathbf{x}') = \exp(-||\mathbf{x} - \mathbf{x}'||^2 / 2\sigma^2) = \exp(-\mathbf{x}^\top \mathbf{x} / 2\sigma^2) \exp(\mathbf{x}^\top \mathbf{x}' / \sigma^2) \exp(-(\mathbf{x}')^\top \mathbf{x}' / 2\sigma^2)$

(17.33)

is a valid kernel.