
![](img/020125e0e698f9771fbbd32f2ace1e80_14_0.png)

# 1 Deep Learning Framework and Paradigm in Computational Physics

Computational physics is a new subject that uses computers to numerically simulate physical processes. The application of computational physics is usually fairly extensive and permeates all fields of physics. The research process of computational physics mainly includes modeling, simulation, and computing. Among them, modeling means the process of abstract physical processes into mathematical models. Simulation refers to the expression and exploration of physical laws, also known as computer experiments. Computing is the procedure of numerical research and analysis of theoretical problems using computers. Traditional computational physics includes the finite difference method [1, 2, 3], the finite element method [4, 5, 6], the variational method [7, 8], the moment of method [9], the dynamics method [10, 11], the Monte Carlo simulation method [12], etc. The detailed process of the finite element method is covered in later chapters of this book, so the first chapter will not be included. Here, the electromagnetic scattering calculation method based on MoM and the Monte Carlo simulation method based on steady-state heat conduction are briefly introduced.

## 1.1 Traditional Numerical Algorithms

### 1.1.1 Moment of Method

The first approach to be discussed in this chapter is the moment of method (MoM), which was first introduced to the realm of computational electromagnetics [13, 14]. The main methodology of MoM is to convert the continuous integral equation into discrete equations, which is able to be solved by computers [15]. The operator equation can be expressed by

```
L(f) = g \quad (1.1)
```

where $L$ denotes the integral equation operator of electric fields, $g$ and $f$ are the known and unknown functions, respectively. The basic process for the MoM to solve the operator equation could be included in the following parts:

DOI: 10.1201/9781003397830-1

## Deep Learning-Based Forward Modeling and Inversion Techniques

First of all, the discretization is implemented to express the function $f$ into the linear combination of the basis functions.

```
$f = \sum_{n=1}^{N} a_n f_n \quad (1.2)$
```

where $f_n$ and $a_n$ are the basis function of the $n$-th term and the corresponding expansion coefficient, respectively, and $N$ is the number of expansion terms. Since the integral operator is linear, the Eq. 1 can be substituted to obtain:

```
$$\sum_{n=1}^{N} a_n L(f_n) \approx g \quad (1.3)$$
```

In this way, the operator equation is transformed into a matrix equation. Next, sampling inspection is required, where the weight function (or trial function) needs to be selected. The frequently selected weight functions include the point matching method and Galerkin method [16], in which the unit impulse function or the basis function itself is selected as the weight function, respectively. For simplicity, the point-matching method is adopted here:

```
$$\omega_m(\mathbf{r}) = \delta(\mathbf{r}) \quad (1.4)$
```

One can define an inner product calculation (also called moment) that acts between the basis function and the weight function.

```
$$\langle f_m, f_n\rangle = \int_{f_m} f_m(\mathbf{r}) \cdot \int_{f_n} f_n(\mathbf{r}') d\mathbf{r}'d\mathbf{r} \quad (1.5)$$
```

In the method of methods

```
$$\sum_{n=1}^{N} a_n \langle\omega_m, L(f_n)\rangle = \langle\omega_m, g\rangle \quad (1.6)$$
```

Construct a matrix whose unit element is

```
$$z_{mn} = \langle\omega_m, L(f_n)\rangle \quad (1.7)$$
```

The right-hand side of Eq. 1.6 can be denoted as

```
$$b_{mn} = \langle\omega_m, g\rangle \quad (1.8)$$
```

Here, the inner product equation has been transformed into a matrix equation:

```
$$Ax = b \quad (1.9)$$
```

## Deep Learning Framework and Paradigm in Computational Physics

where $x$ represents the discretization of the total electric field, $b$ represents the discretization of the incident field, and complex matrix $A$ can be written as

$$A = I + G^D D^* \quad (1.10)$$

where $I$ is the unit matrix, $D$ is the diagonal matrix formed by the discretization of electromagnetic parameters in the scattering area, and $G^d$ is the coefficient matrix.

```
$$G_{p,q}^d = \begin{cases} \pi k_0 a H_1^{(2)}(k_0 a) - 2i, & p = q \\ \frac{1}{2}\pi k_0 a J_1(k_0 a) H_1^{(2)}(k_0 \rho_{p,q}), & p \neq q \end{cases} \quad (1.11)$$
```

where $k_0$ represents the wave number in vacuum, $J_1$ represents the second-class first-order Hankel function, $H_1^{(2)}$ represents the second-class zero-order Hankel function, and $a$ represents the radius of a circle to each grid area $\Delta^2$.

```
$$a = \sqrt{\frac{\Delta^2}{\pi}} \quad (1.12)$$
```

$\rho_{p,q}$ represents the distance between two grid center points.

```
$$\rho_{p,q} = \sqrt{(x_p - x_q)^2 + (y_p - y_q)^2} \quad (1.13)$$
```

Here, an example is used to illustrate the reliability of the method used. In the two-dimensional plane, there is a square scattering area with a side length of 2 m. The electromagnetic wave is incident along the $+x$ direction, and the incident wave is TM polarized; that is, the electric field has only the $z$ component. The frequency of the electromagnetic wave is 300 MHz. The scatter is elliptical, its semi-major axis is 0.5 m, and its eccentricity is $\frac{1}{2}$; the internal scatterer is a lossless medium, its dielectric constant is 4, and the background is vacuum.

![](img/020125e0e698f9771fbbd32f2ace1e80_18_0.png)

# FIGURE 1.1

The comparisons of the MoM algorithm and the COMSOL. (a) Fields calculated by the MoM algorithm, (b) fields computed by COMSOL, and (c) the errors.

### 1.1.2 Monte Carlo Method

The second method introduced here is the Monte Carlo method [12, 17, 18], which is also called the random sampling method. The algorithm makes use random number generated by the computer for statistical experiments and takes the statistical characteristics of the equation as the mean value and probability as the numerical solution of the equation. In recent years, the development of computer technology, the Monte Carlo algorithm has been widely used in the field of computational physics. Although with classical numerical methods such as the finite element method and finite difference method other methods cannot replace. For example, this method can solve the value of any point in the region independently without solving on the basis of other points, so it can realize fast parallel computing.

When applying the Monte Carlo method to solve partial differential equations, it is usually necessary to establish a probability model to obtain the probability of an event through numerical simulation, so as to obtain the numerical solution of the point. This chapter will take the steady-heat conduction equation as an example to introduce the process of using Monte Carlo simulation to solve the PDE approximate solution.

Suppose the problem in solution domain D

```
$$\nabla^2 u = 0$$
```

```
$$|u|_r = g(\Gamma)$$
```

Divide the space to be solved evenly, and the grid size is $\delta$. Assuming the internal point to be solved is $S$ and the grid point on the boundary
