$\nabla^2$ is the Laplacian operator and is defined for the three spatial coordinates of $x, y, z$ by the following equation:

```
\nabla^2 = \partial^2/\partial x^2 + \partial^2/\partial y^2 + \partial^2/\partial z^2
```

Poisson’s equation is widely used to describe potential distributions such as electric and gravitational fields [38]. Specifically, when an electric charge distribution is presented, Poisson’s equation is used to find the potential distribution. Poisson’s equation also plays an important role in areas such as fluid mechanics and heat conduction. In one-dimensional space, the one-dimensional Poisson’s equation can be written as

```
$\frac{\partial^2 u}{\partial x^2} - t = 0$ \hspace{3cm} $(4.17)$
```

When the definition domain and boundary conditions are set as follows,

```
\begin{gather*} (x, t) \in [0,1] \times [0,1] \\ u|_{x=-1} = 0;\; u|_{x=1} = 0 \end{gather*}
```

the exact solution is obtained as follows:

```
$u = \frac{x^2}{2}t - \frac{t}{2}$ \hspace{3cm} $(4.18)$
```

In the exact solution of Poisson’s equation, the domain of definition of $x \in [0,1]$ and $t \in [0,1]$ is sampled, and $u(x, t)$ is computed based on their coordinates, which are considered pseudo-measurement data. The partial differential term candidate library is constructed as follows:

```
$\mathbf{\Phi} = [u_x, \mathbf{u}_{xx}, u_{xxx}]$
```

The results are shown in the top color map diagram in Figure 4.15.

First, derivation of Poisson’s equation is performed in N10. Results in which the NN has the minimum error are shown in the middle color map diagram in Figure 4.15. The lower color map diagram in Figure 4.15 shows the error distribution $(\hat{u} - u)$ between the NN model and the exact solution.

The data distribution $\{u(x,t) | t = 0.25, 0.5, 0.75\}$ at fixed time is also shown below the error distribution. In addition, the bottom row of Figure 4.15 shows the derived PDE, but the derivation error is not sufficient because of the large number of candidate partial derivative terms in the library.