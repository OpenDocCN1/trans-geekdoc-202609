The following boundary conditions are imposed for a beam with two ends simply supported.

```
$U = W = \mathcal{M}_h^b = \mathcal{M}_m^b = 0 \quad (8.17)$
```

The assumed mechanical transverse load $q(x)$ is developed in a sinusoidal Fourier series:

```
$q(x) = \sum_{n=1}^{\pi} a_n \sin(n\lambda x) \quad (8.18)$
```

The coefficients $a_n$ are provided below for some loads.

+   $n = 1 \Rightarrow \mathfrak{q}_1 = q_0 \quad (8.19)$

+   Uniform distribution case:
\mathfrak{q}_n = \frac{4q_0}{n\pi}(n = 1, 3, 5) \quad (8.20)$

So, analytical solutions may be reached from the eigenvalues system below for any fixed value of "$n$:

```
$[K - \omega_m^2(M)][\Delta] = \{F\} \quad (8.21)$
```

In the static problem case, Eq. (8.24) becomes:

```
$[K][\Delta] = \{F\} \quad (8.22)$
```

$[K] = \begin{bmatrix} k_{11} & k_{12} & k_{13} & k_{14} \ k_{21} & k_{22} & k_{23} & k_{24} \ k_{31} & k_{32} & k_{33} & k_{34} \ k_{41} & k_{42} & k_{43} & k_{44} \end{bmatrix} [M] = \begin{bmatrix} m_{11} & m_{12} & m_{13} & 0 \ m_{21} & m_{22} & m_{23} & m_{24} \ m_{31} & m_{32} & m_{33} & m_{34} \ 0 & 0 & 0 & 0 \end{bmatrix}, [\Delta] = \begin{bmatrix} U_s \ W_{ba} \ W_m \ \phi_s \ 0 \end{bmatrix}, \{F\} \quad (8.23)$

$(k_{11}, k_{12}, k_{13}, k_{14}, k_{21}, k_{22}, k_{23}, k_{24}, k_{31}, k_{32}, k_{33}, k_{34}, k_{41}, k_{42}, k_{43}, k_{44})$ and $(m_{11}, m_{12}, m_{13}, m_{22}, m_{23}, m_{33}, m_{34}, m_{44})$ are given in Appendix A.

# 8.3 Numerical results and discussion

In this part, a uniform transverse load is applied to the S-S FG beam. Numerical examples are proposed first to validate the model presented above and assess its