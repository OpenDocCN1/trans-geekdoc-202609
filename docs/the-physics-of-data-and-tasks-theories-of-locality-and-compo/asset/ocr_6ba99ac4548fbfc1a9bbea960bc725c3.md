Therefore, $\mathbb{E}|c_k|^2$ is non-zero only for $k$'s which have at most $t$ consecutive components greater or equal to, and the remaining $s-t$ being strictly zero. Inserting Equation 167 into Equation 160,

```
$\mathcal{B}(P) = \sum_{k\in P}\langle k|k_P\rangle \sum_{l=1}^{s} \sum_{j=1}^{t} \delta(k\sim k^{(l)}, 0) \Lambda_{k^{(j)}}^{(t)} \int^{\infty} dkt^{1-k}(a_l+t)} \sim P^{-\frac{s}{2}}$$\n(168)$
```

When using a local detector, the convolutional eigenfunctions in the RHS of Equation 162 are replaced by the local eigenfunctions $\Phi_{k,s}(\mathbf{x})$ of Equation 39. Repeating the computations, one finds

```
$k_c = \left(\frac{P}{d/s}\right)^{\frac{1}{2}}$$\n(169)$
```

```
$\mathbb{E}|c_k|^2 = \frac{s}{d} \sum_{l=1}^{s} \sum_{j=1}^{t} \delta(k\sim k^{(l)}, 0) \Lambda_{k^{(j)}}^{(t)}$.$\n(170)$
```

As a result,

```
$\mathcal{B}(P) = \sum_{k\in P}\langle k|k_P\rangle \sum_{l=1}^{s} \sum_{j=1}^{t} \delta(k\sim k^{(l)}, 0) \Lambda_{k^{(j)}}^{(t)}$$\n(171)$$\n\sim \int^{\infty} \left(\\frac{P}{pr_s}\right)^{\frac{1}{2}} dkt^{1-k}(a_l+t) \sim \left(\frac{P}{d/s}\right)^{\frac{1}{2}}$$\n(172)$
```

As we showed in Section A.3, when the patches overlap the set of wavevectors is restricted from $Z^d$ to the union of the $F^u$ for $u=0,...,s$. In addition, the eigenvalues with $k\in F^u, 0<u<s$, are rescaled by a factor $(s-u+1)/d$. Therefore, in the overlapping case the eigenvalues do not decrease monotonically with $k$ and $B(P)$ cannot be written as a sum over $k$'s with modulus larger than a certain threshold $k_c$. By considering also, with $t\le s$, $\mathbb{E}|c_k|^2$ is non-zero only for $k$'s which have at most $t$ nonnegative components, we have

```
$\mathcal{B}(P) = \sum_{u=0}^{s} \sum_{k\in F^u} \mathbb{E}|c_k|^2(\Lambda_k^{(s)}>\Lambda_P)$$\n(173)$
```

where $\Lambda_P$ denotes the $P$-th largest and the indicator function $(\Lambda_k^{(s)}>\Lambda_P)$ ensures that the sum over all the first $P$ eigenfunctions of the students. The sets $\{F^u\}_{u<t}$ have all null measure in $Z^d$, $F'$ is finite in $Z^d$, thus the asymptotics of $B(P)$ are dictated by the sum over $F'$. When $k$ are restricted to the latter set, eigenvalues are again decreasing functions of $k$ and the constraint $\Lambda_k^{(s)}>\Lambda_P$ translates into $k>k_c(P)$. Having changed, with respect to the non-overlapping case, only an infinitesimal fraction of the eigenvalues, the asymptotic scaling of $k_c(P)$ with $P$ remains unaltered