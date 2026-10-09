(3) Let $t$ be a moving point on $C_{0}$, $m = \operatorname{dim} G/T = \operatorname{dim} G - \operatorname{dim} T$. Then, $G(t)$ is a $G/T$-type orbit and its $m$-dimensional volume is a function whose domain is $C_{0}$. We call it the (main) orbital volume function and denote it by $v(t)$. Since each orbit $G(t)$ is the same $G/T$-type homogeneous Riemannian space, its volume ratio is equal to the ratio of its volume elements. We can take a benchmark of $G/T$ homogeneous Riemannian space. For each $G/T$-type orbit $G(t)$, the coset $g \cdot t$ mapped to $g(t)$ is a homogeneous Riemannian space between the $G$-isometric mapping $E$

$$E: G/T \rightarrow G(t), g \cdot t \mapsto g(t) = gtg^{-1} \,. $$

Then, the ratio of the volume element of the above is the Jacobi determinant of the above mapping $E_{t}$, i.e., the object of the volume function $v(t)$ can be calculated by

$v(t) = c \cdot \operatorname{det}(dE_{t|_{0}}) \,, \tag{1.5}$

where $c$ is an undetermined proportional constant and $dE_{t|_{0}}$ is the linear mapping of the base point on the tangent space.

$$\operatorname{d}E_{t|_{0}}: \oplus_{a \in \Delta^{+}} R_{(t,a)}^{2} \rightarrow \mathfrak{J}_{0}(G(t)) \,. \tag{1.6}$$

(4) Since $E_{t}$ is $G$-isomorphic, $dE_{t|_{0}}$ is a $T$-norm (because the base point is a fixed point under the effect of $T$). Thus, $dE_{t|_{0}}$ can be decomposed into linear straight sums of the following two-dimensional $T$-invariant subspace

$$dE_{t|_{0}}, a: R_{(t,a)}^{2} \rightarrow \mathfrak{J}_{0}(G_{0}(t)) \,. \tag{1.7}$$

Hence, we can use the following formula to calculate $\operatorname{det}(dE_{t|_{0}})$, i.e.,

$$\operatorname{det}(dE_{t|_{0}}) = \prod_{a \in \Delta^{+}} \operatorname{det}(dE_{t|_{0}}, a) \,. \tag{1.8}$$

However, $\operatorname{det}(dE_{t|_{0}})$ is proportional to the $S^{2}$-type(main) orbit volume function in $Ga/Ta \equiv \widehat{G}_{a} \equiv S^{3}$. In other words, we can use the diagram

![](bbox=[0.3125, 0.625, 0.90625, 0.7083333333333334])

to put the calculation of $\operatorname{det}(dE_{t|_{0,a}})$ into the $S^{2}$-type volume function in $\widehat{G}_{a}$($\widehat{G}_{a}$ is an isomorphism with $S^{3}$ or SO(3); hence, $\widehat{G}_{a}$ has the same volume elements as $S^{3}$ and we thus see $\widehat{G}_{a}$ as $S^{3}$ in the above problem). Then, we get

$$\operatorname{det}(dE_{t} |_{0,a}) = c' \cdot \sin^{2}\pi(a,H) \tag{1.10}$$

where $H$ satisfies $t = \exp H$ (note that the positive root of $S^{3}$ is $2\Theta$). By integrating formulas (1), (4), and (5), we get

$$v(\exp H) = c^{"} \cdot \sin^{2}\pi(a,H) = c \cdot [\widehat{Q}(\exp H)]^{2} \tag{1.11}$$

where $\widehat{Q}(\exp H) = \prod_{a \in \Delta^{+}} (e^{\pi i(a,H)} - e^{-\pi i(a,H)})$.