The state diagram is

![](bbox=[0.393, 0.219, 0.603, 0.381])

We can check the distribution of $\mathbf{x}_{n+1}$ after transitioning $n$ times from the initial state $\mathbf{x}_1$ with distribution $\mathbf{p} = (p_1, p_2, p_3)$. Recall that this is given by $\mathbf{p}^T P^n$. For $n=20$, in our example, we have

$P^{20} \approx \begin{pmatrix} 0.1006 & 0.3984 & 0.5011 \ 0.0996 & 0.4012 & 0.4992 \ 0.1002 & 0.3994 & 0.5004 \end{pmatrix}$

The rows are getting close to $f = (1/10, 2/5, 1/2)$. Let's assume that $P^n$ converges to

```
$F = \begin{pmatrix} f_1 & f_2 & f_3 \ f_1 & f_2 & f_3 \ f_1 & f_2 & f_3 \end{pmatrix}$
```

as $n$ converges to then the distribution of $\mathbf{x}_{n+1}$ converges to

$\mathbf{p}^T = (f_1(p_1 + p_2 + p_3), f_2(p_1 + p_2 + p_3), f_3(p_1 + p_2 + p_3)) = \mathbf{f}^T$,

since $p_1 + p_2 + p_3 = 1$. Thus we can generate approximate samples for a given distribution $f$, by generating samples using a Markov chain for which $f$ is invariant irrespective of the starting distribution.

Convergence is due to the ergodic theorem, which is beyond the scope of this text, Norris (1998) gives a thorough treatment of Markov chains. If a finite Markov chain is irreducible and aperiodic, then the distribution of $\mathbf{x}_n$ converges to the invariant distribution $f$ irrespective of the initial distribution. The invariant distribution is then the equilibrium.

More generally, with any matrix of the form

```
$P = \begin{pmatrix} 1-\frac{\alpha+eta}{2} & \alpha & \beta \ \frac{\alpha}{4} & 1-\frac{\alpha+4\gamma}{4} & \gamma \ \frac{eta}{5} & \frac{\gamma}{5} & 1-\frac{eta+4\gamma}{5} \end{pmatrix} \quad (3.5)$
```