# 530 CHAPTER 23 Special Algorithms for Protocols

To distribute the shadows, first choose a random value $r$ and compute

$M' = M + rp$$

The shadows, $k_i$, are

$k_i = M' \pmod{d_i}$$

Any $m$ shadows can get together and reconstruct $M$ using the Chinese remainder theorem, but any $m-1$ cannot. See [65] for details.

# **Karn-Green-Hellman**

This scheme uses matrix multiplication [818]. Choose $n+1$ $m$-dimensional vectors, $V_0, V_1, \dots, V_n$ such that any possible $m \times m$ matrix formed of those vectors has rank $m$. The vector $U$ is a vector of dimension $m+1$.

$M$ is the matrix product $UV_i$. The shadows are $U-V_i$, where $i$ is a number from 1 to $n$.

Any $m$ shadows can be used to solve the $m \times m$ system of linear equations, where the unknowns are the coefficients of $U. UV_i$ can be computed from $U$. Any $m-1$ shadows cannot solve the system of linear equations and therefore recover the secret.

# **Advanced Threshold Schemes**

The previous examples illustrate the simple threshold schemes: Divide a secret into $n$ shadows such that any $m$ can be used to recover the secret. These algorithms can be used to create more complicated schemes. The following examples will use Sham's algorithm, although any of the others will work.

To create a scheme where one person is more important than another, if it takes five shadows to recreate a secret and one person has three shadows while else has only one, then that person and two other people can recreate the secret. Without that person, it takes five to recreate

Two or more people could get multiple shadows. Each person could have a different number of shadows. No matter how the shadows are distributed, any $m$ of them can be used to reconstruct the secret. With $m-1$ shadows, it be one person or a hostile ele, cannot do it.

In other types of schemes, imagine a scenario with two hostile delegations. They share the secret so that two people from the 7 Delegation A and 3 people from the 12 Delegation B are required to reconstruct the secret. Make a polynomial of degree 3 that is the product of a linear expression and a quadratic expression. Give everyone from Delegation A a shadow that is the result of an evaluation of the linear equation, give everyone from Delegation B a shadow that is the evaluation of the quadratic equation.

Any two shadows from Delegation A can be used to reconstruct the linear equation, but no matter how many shadows the group has, they cannot get any about the secret. The same is true for Delegation B: They can get three shadows together to reconstruct the quadratic equation, but they cannot get any