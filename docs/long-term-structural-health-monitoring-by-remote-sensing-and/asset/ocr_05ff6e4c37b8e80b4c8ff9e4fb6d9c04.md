# 2.3.1.1 Hamiltonian Monte Carlo Sampling

The HMC sampling is a Markov Chain Monte Carlo technique for obtaining a sequence of random samples from a target probability distribution when the direct sampling process is intractable (Neal 2011). This method corresponds to an instance of the Metropolis–Hastings algorithm with a Hamiltonian dynamics evolution that can be simulated by using a time-reversible and volume-preserving numerical integrator to provide a move to a new sample. Unlike the Metropolis–Hastings algorithm, the HMC method decreases the correlation between successive sampled states by performing moves to far states that can provide a high probability of acceptance owing to having approximate energy conserving characteristics of the simulated Hamiltonian dynamic. Simply speaking, the reduced correlation makes sense that fewer Markov chain samples are required to approximate integrals with respect to the target probability distribution.

Assume that \( f(\mathbf{x}) \) is the target distribution that is supposed to be sampled by using a chain of samples \( \{\mathbf{x}_0, \mathbf{x}_1, \mathbf{x}_2, ...\} \). Accordingly, the Hamilton’s equations are written in the following forms:

```
\frac{\mathrm{d}x_i}{\mathrm{d}t} = \frac{\partial H}{\partial w_i} \quad (2.22)
\frac{\mathrm{d}w_i}{\mathrm{d}t} = \frac{\partial H}{\partial x_i} \quad (2.23)
```

where \( x_i \) and \( w_i \) denote the \( i \)th element of the parameter and momentum vector, respectively. Moreover, \( H \) refers to the Hamiltonian function. Suppose that \( \mathbf{M} \) is a symmetric and positive definite (mass) matrix. On this basis, the Hamiltonian is expressed as follows:

```
H(\mathbf{x}, \mathbf{w}) = U(\mathbf{x}) + \frac{1}{2}\mathbf{w}^T \mathbf{M}^{-1} \mathbf{w} \quad (2.24)
```

where

```
U(\mathbf{x}) = - \ln f(\mathbf{x}) \quad (2.25)
```

From Eq. (2.25), one can understand that the sampling method under the algorithm of HMC relies on the logarithmic function related to the target distribution. Moreover, this sampler exploits the leap-frog technique (Neal 2011), which is an approximate solution to the motion of non-interacting classical particles, to determine the parameter and momentum components at any time. For this purpose, the sampling algorithm needs a positive integer for the number of leap-frog steps \( L \) and a positive number for the step size \( \Delta t \). Subsequently, it draws a random Gaussian momentum \( \mathbf{w}(0) \) from a Gaussian distribution with zero mean and covariance equal to the mass matrix \( \mathbf{M} \). In the next step, the particle runs under Hamiltonian