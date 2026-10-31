
## 11 Nonlinear Dynamical Systems

S. Brunton

Dynamical systems provide a mathematical framework to describe the evolution of complex physical systems, such as unsteady fluid dynamics. The field of dynamical systems lives at the interface of many fields of mathematics, including linear algebra, differential equations, topology, geometry, and numerical analysis. Modern dynamical systems began with the seminal work of Poincaré on the chaotic motion of planets, and it may be viewed as the culmination of hundreds of years of mathematical modeling with differential equations. This chapter presents a modern perspective on dynamical systems in the context of current goals and open challenges in fluid dynamics. Data-driven dynamical systems is a rapidly evolving field, and therefore, we focus on a mix of established and emerging methods that are driving current developments. In particular, we will focus on the three key challenges of (1) high-dimensionality, (2) discovering dynamics from data, and (3) finding data-driven representations that make nonlinear systems amenable to linear analysis.

### 11.1 Introduction

In recent decades, the field of dynamical systems has grown rapidly, with analytical derivations and first principle models giving way to data-driven approaches. Thus, machine learning and big data are driving a paradigm shift in the analysis and understanding of dynamical systems in science and engineering. This trend is particularly evident in the field of fluid dynamics, which is one of the original big data fields.

In addition, the classical geometric and statistical perspectives on dynamical systems are being complemented by a third operator-theoretic perspective, based on the evolution of measurements of the system. This so-called Koopman operator theory is poised to capitalize on the increasing availability of measurement data from complex systems. Moreover, Koopman theory provides a path to identify intrinsic coordinate systems to represent nonlinear dynamics in a linear framework. Obtaining linear representations of strongly nonlinear systems has the potential to revolutionize our ability to predict and control these systems (Figure 11.1). See Chapters 10 and 7 for overviews of linear systems and Koopman theory, respectively.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_238_0.png)

Figure 11.1 Schematic depiction of increasing nonlinearity in dynamical systems. Behavior goes from periodic to quasiperiodic, and eventually becomes chaotic. Reproduced from Brunton et al. (2017).

### 11.2 Dynamical Systems

### 11.2.1 Continuous-Time Systems

Throughout this chapter, we will consider dynamical systems of the form

$$\frac{d}{dt}\mathbf{x}(t) = \mathbf{f}(\mathbf{x}(t), t; \boldsymbol{\beta}),\qquad (11.1)$$

where $\mathbf{x}$ is the state of the system and $\mathbf{f}$ is a vector field that possibly depends on the state $\mathbf{x}$, time $t$, and a set of parameters $\boldsymbol{\beta}$.

Finite-dimensional representations of the Navier–Stokes equations take this form in which case the state $\mathbf{x}$ may contain the flow-field variables on a discretized grid, or a finite number of Fourier coefficients. These dynamics are typically high-dimensional, often requiring millions or billions of degrees of freedom. It is also possible to obtain low-dimensional dynamical systems that describe a fluid flow in terms of the dynamics of the amplitudes of a small set of modes, for example, by Galerkin projection of the governing equations onto a truncated set of Proper Orthogonal Decomposition (POD) modes. In these projected models, the dynamics in (11.1) have quadratic nonlinearities due to the convective nonlinearity $(\mathbf{u}\cdot\nabla)\mathbf{u}$ in the Navier–Stokes equations.

The Lorenz (1963) system

$$\dot{x} = \sigma(y - x),\qquad (11.2a)$$
$$\dot{y} = x(\rho - z) - y,\qquad (11.2b)$$
$$\dot{z} = xy - \beta z\qquad (11.2c)$$

is one of the earliest nonlinear reduced-order models of an unsteady fluid system, as it was developed to model chaotic Rayleigh–Benard convection. The $x$, $y$, and $z$ variables denote the amplitudes of three spatial modes, posited by Saltzman (1962), onto which the Navier–Stokes equations are Galerkin projected. In this case, the state vector is $\mathbf{x} = [\,x\quad y\quad z\,]^{\mathsf{T}}$ and the parameter vector is $\boldsymbol{\beta} = [\,\sigma\quad \rho\quad \beta\,]^{\mathsf{T}}$. A trajectory of the Lorenz system is shown in Figure 11.2, with parameters σ = 10, ρ = 28, and β = 8/3.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_239_0.png)

Figure 11.2 Chaotic trajectory of the Lorenz system from (11.2). From Brunton and Kutz (2019), reproduced with permission of the Licensor through PLSclear.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_239_1.png)

Figure 11.3 Depiction of uncertainty in the Lorenz system. A cube of initial conditions is evolved along the flow. Although the trajectories stay close together for some time, after a while, they begin to spread along the attractor.

The Lorenz system is among the simplest and most well-studied dynamical systems that exhibit chaos, which is characterized as a sensitive dependence on initial conditions. Two trajectories with nearby initial conditions will rapidly diverge in behavior, and after long periods, only statistical statements can be made. This sensitivity is depicted in Figure 11.3, where a cube of initial conditions is evolved along the flow of the dynamical system, showing that after some time the initial conditions become spread out along the attractor. This type of chaotic mixing is characteristic of turbulence.

We will often consider the simpler case of an autonomous system without time dependence or parameters:

$$\frac{d}{dt}\mathbf{x}(t) = \mathbf{f}(\mathbf{x}(t)).\tag{11.3}$$

### 11.2.2 Discrete-Time Systems

In addition to the aforementioned continuous-time dynamics, we will also consider discrete-time dynamical systems

$$\mathbf{x}_{k+1} = \mathbf{F}(\mathbf{x}_k).\tag{11.4}$$

Discrete-time dynamics are often more natural when considering experimental data and simulations, as data is typically generated discretely in time.

Also known as a map, the discrete-time dynamics are more general than the continuous-time formulation in (11.3), encompassing discontinuous and hybrid systems as well.

As an example, consider the logistic map, which is a simple model to explore the complexity of population dynamics:

$$x_{k+1} = \beta x_k (1 - x_k).\tag{11.5}$$

As the parameter β is increased, the attracting set becomes increasingly complex, shown in Figure 11.4. A series of period-doubling bifurcations occur until the attracting set becomes fractal. The complexity of turbulence is also often understood as the result of a sequence of period-doubling Hopf bifurcations.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_240_0.png)

Figure 11.4 Attracting sets of the logistic map for varying parameter β. From Brunton and Kutz (2019), reproduced with permission of the Licensor through PLSclear.

$$\mathbf{F}_t(\mathbf{x}(t_0)) = \mathbf{x}(t_0) + \int_{t_0}^{t_0+t} \mathbf{f}(\mathbf{x}(\tau)) d\tau. \tag{11.6}$$

### 11.2.3 Linear Dynamics and Spectral Decomposition

As explored in Chapter 10, whenever possible it is desirable to work with linear dynamics of the form

$$\frac{d}{dt}\mathbf{x} = \mathbf{A}\mathbf{x}. \tag{11.7}$$

Even for nonlinear systems, it is often possible to understand the behavior near fixed points in terms of locally linearized dynamics.

Linear dynamical systems admit closed-form solutions, and there are a wealth of techniques for the analysis, prediction, numerical simulation, estimation, and control of such systems. The solution of (11.7) is given by

$$\mathbf{x}(t_0 + t) = e^{\mathbf{A}t}\mathbf{x}(t_0). \tag{11.8}$$

The dynamics are entirely characterized by the eigenvalues and eigenvectors of the matrix $\mathbf{A}$, given by the *spectral decomposition* (eigendecomposition) of $\mathbf{A}$:

$$\mathbf{A}\mathbf{T} = \mathbf{T}\mathbf{\Lambda}. \tag{11.9}$$

When $\mathbf{A}$ has $n$ distinct eigenvalues, then $\mathbf{\Lambda}$ is a diagonal matrix containing the eigenvalues $\lambda_j$ and $\mathbf{T}$ is a matrix whose columns are the linearly independent eigenvectors $\xi_j$ associated with eigenvalues $\lambda_j$. In this case, it is possible to write $\mathbf{A} = \mathbf{T}\mathbf{\Lambda}\mathbf{T}^{-1}$, and the solution in (11.8) becomes

$$\mathbf{x}(t_0 + t) = \mathbf{T} e^{\mathbf{\Lambda}t} \mathbf{T}^{-1} \mathbf{x}(t_0). \tag{11.10}$$

More generally, in the case of repeated eigenvalues, the matrix $\mathbf{\Lambda}$ will consist of Jordan blocks (Perko 2013). Note that the continuous-time system gives rise to a discrete-time dynamical system, with $\mathbf{F}_t$ given by the solution map $\exp(\mathbf{A}t)$ in (11.8). In this case, the discrete-time eigenvalues are given by $e^{\Delta t}$.

For non-normal operators $\mathbf{A}$, the eigenvectors may be nearly parallel. In this case, even with stable eigenvalues, the system may exhibit *transient* growth, where an initial condition first grows before eventually converging to the origin. Transient growth is observed in many shear flows, and the excursion from the origin often results in perturbation amplitudes that are large enough to excite nonlinear dynamics. For example, pipe flow is linearly stable at all Reynolds numbers, but non-normality and transient energy growth results in sustained turbulence at finite Reynolds numbers.

The matrix $\mathbf{T}^{-1}$ defines a transformation, $\mathbf{z} = \mathbf{T}^{-1}\mathbf{x}$, into intrinsic eigenvector coordinates, $\mathbf{z}$, where the dynamics become decoupled:

$$\frac{d}{dt}\mathbf{z} = \mathbf{\Lambda}\mathbf{z}. \tag{11.11}$$
