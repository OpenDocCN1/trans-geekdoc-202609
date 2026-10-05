# 286 Recursive Solutions to Large Eigenproblems

variation methods, which may involve substantial numerical computations. As a result, the efficiency and accuracy of such methods are of paramount importance. In this review, we will restrict our attention to methods based on the variation principle and consider some nondraditional diagonalization algorithms. These algorithms take advantage of recursive matrix-vector multiplication and are thus amenable to large eigenproblems. In particular, vibrational spectra of polyatomic molecules may be used as examples to illustrate the numerical approaches.

# Discretization

A numerical solution of the Schrödinger equation in Eq. [1] often starts with the discretization of the wave function. Discretization is necessary because it converts the differential equation to a matrix form, which can then be readily handled by a digital computer. This process is typically done using a set of basis functions in a chosen coordinate system. As discussed extensively in the literature,$^{5,11}$ the proper choice of the coordinate system and the basis functions is vital in minimizing the size of the problem and in providing a physically relevant interpretation of the solution. However, this important topic is out of the scope of this review and we will only discuss some related issues in the context of recursive diagonalization. Interested readers are referred to other excellent reviews on this topic$^{5,9,10}$.

Assuming that the basis functions used in discretization ($|phi_iangle$) are complete and orthonormal, the wave function in Eq. [1] can be expressed in the following expansion:

```
$|\\rangle = \sum_{i=1}^{N} b_i |\phi_i\rangle$
```

In principle, the sum in Eq. [2] contains infinite terms. However, a judicious choice of the coordinate system and basis functions allows for a truncation with finite (N) terms without sacrificing accuracy. Substituting Eq. [2] back to Eq. [1], we have

```
$Hb = \epsilon b$
```

Here, $\epsilon$ is the eigenvalue, and the Hamiltonian matrix and the eigenvector respectively defined as

```
$H_{ij} = \langle\phi_i|H|\phi_j\rangle$
```

```
$b = (b_1, b_2, \dots, b_N)^T$
```