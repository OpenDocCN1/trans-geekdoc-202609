
## 13.8 Summary and Conclusions

Hydrodynamic stability theory has played a central role in the development of theoretical fluid mechanics. It has motivated the development of a great many mathematical and computational tools to probe the behavior of perturbations about a steady or quasi-steady flow state and has formed the foundation for subsequent research fields, such as flow control. Starting in the beginning to determine the large-time stability of generic configurations, it has matured into a sophisticated set of tools applicable to large-scale systems and multiscale simulations. During this process, many fundamental assumptions and limitations of early stability theory have been (and will continue to be) challenged and abandoned. They will be replaced by a general and flexible numerical platform based on complex optimization, fast solvers, and parallel algorithms. In this manner and form, modern hydrodynamic stability theory will assert its central position in the quantitative analysis of complex fluid systems.

## Part V
### Applications

## 14 Machine Learning for Reduced-Order Modeling

B. R. Noack, D. Fernex, and R. Semaan

We describe data-driven reduced-order modeling (ROM) approaches using powerful methods of machine learning. The focus is gray-box models (GBMs) distilling coherent structure dynamics from snapshot data. We highlight two generally applicable methods: the proper orthogonal decomposition (POD) Galerkin method and cluster-based models. The Galerkin method has deep roots in the mathematical investigation of the Navier–Stokes equations and comes with illuminating physical insights. Yet, the accurate data-driven variant requires a rich set of tuning tools and tends to have a narrow range of validity. As an alternative, the recently developed cluster-based network model is inherently robust, can easily integrate numerous operating conditions, and its construction can fully be automated. However, we lose connection to first principles. Of course, there are many different shades of gray, which will briefly be reviewed. The chapter concludes with a tutorial of xROM, a freely available software for POD and cluster modeling for different types of grids and a large volume of data.

### 14.1 Introduction

ROM has a long tradition in fluid mechanics. The focus of this chapter is gray-box modeling,¹ which resolves the coherent structure flow dynamics. Over 500 years ago, Leonardo da Vinci made the first paintings of wake vortices. von Helmholtz (1858) laid the foundation of their dynamic modeling with his famous vortex laws. In the years that followed, many vortex models were proposed. Examples are a pair of two equal vortices rotating about their axis, a pair of two equal but opposite vortices moving uniformly, leapfrogging ring vortices, the Föppl (1913) vortex model of the near wake, the von Kármán (1911) vortex model for vortex shedding, a shear-layer vortex model (Hama 1962), the recirculation zone model (Suh 1993), the vortex-model-based feedback control (Noack et al. 2004, Protas 2004), just to name a few. The reduced-order vortex models inspired high-dimensional simulations with vortex blobs (Leonard 1980), and vortex filaments (Ashurst & Meiburg 1988). Vortex models are closely tied to first principles and robustly model coherent structures and their convection.

¹ The term is adopted from Wiener (1948).

Another branch of reduced-order models can be traced back to stability analysis of Orr (1907) and Sommerfeld (1908) and the Galerkin (1915) method. These foundations corroborated the idea that fluid dynamics can be understood as a superposition of global physical modes. Landau (1944) and Hopf (1948) even considered turbulence as originating from a sequence of many Hopf bifurcations. The mean-field theory of Stuart (1958) beautifully explained the nonlinear saturation of instability modes. Subsequently, the Galerkin method was not only applied to instability modes but also to mathematical modes from Hilbert space considerations (Busse 1991, Noack & Eckelmann 1994). As with vortex models, the Galerkin method was increasingly generalized and became a foundation of computational fluid mechanics.

Data-driven reduced-order models have arguably originated from Galerkin methods with a POD expansion (Lorenz 1956, Lumley 1967). The POD of a given snapshot ensemble yields a Galerkin expansion with minimal representation error for given number of modes. The pioneering wall turbulence model of Aubry et al. (1988) demonstrated their use in explaining complicated dynamics. In the last three decades, a myriad of POD models have been proposed. The initial excitement of POD was mitigated by the increasing realization of the fragility of the resulting Galerkin models (Rempfer 2000) and their limited range of validity. Galerkin methods are detailed in Section 14.2.

A recent development of cluster-based reduced-order models (CROM) was pioneered by Burkardt et al. (2006) and Hof et al. (2004). Here, the dynamics are modeled as a stochastic transition between a small number of representative flow states. The k-means clustering of snapshots yields centroids as representative flow states with a minimal representation error. The dynamics can be framed in a Markov (Kaiser et al. 2014) and network model (Li et al. 2021). In Section 14.3, this branch of ROM is discussed including the latest innovations (Fernex et al. 2019, 2021).

Of course, there are different shades of gray with GBMs, which are outlined in Section 14.4. The chapter concludes with a tutorial of POD modeling (Section 14.5) with freely available software by the authors.

### 14.2 Proper Orthogonal Decomposition Galerkin Model

This section gives recipes and suggestions for the construction of POD Galerkin models. First, the considered configurations are specified in Section 14.2.1. Then, Sections 14.2.2 and 14.2.3 describe the kinematical and dynamical steps to a POD model. Sections 14.2.4 and 14.2.5 provide closures for an existing POD model and identification methods for experiment. Section 14.2.6 reviews common applications.

### 14.2.1 Flow Configuration

We assume an incompressible viscous flow in a steady domain Ω. A location in this domain is denoted by x = (x, y, z) = (x1, x2, x3). The time is represented by t. The velocity and pressure fields read u = (u, v, w) = (u1, u2, u3) and p, respectively. The Newtonian fluid is described by the density ρ and dynamic viscosity μ.

Let $D$ and $U$ be characteristic size and velocity scales of the configuration. The flow properties are characterized by the Reynolds number $Re = \rho U D / \mu$, or, equivalently by its reciprocal $\nu = 1/Re$. In the sequel, we assume that all quantities are nondimensionalized with $D$, $U$, $\rho$, and $\mu$.

The continuity and Navier–Stokes equations read

$$\nabla \cdot \boldsymbol{u} = 0 \tag{14.1}$$ $$\partial_t \boldsymbol{u} + \nabla \cdot (\boldsymbol{u} \otimes \boldsymbol{u}) = -\nabla p + \nu \Delta \boldsymbol{u}. \tag{14.2}$$

The Dirichlet boundary conditions at stationary walls $\boldsymbol{x} \in \partial \Omega$ are

$$\boldsymbol{u}(\boldsymbol{x},t) = \boldsymbol{0}. \tag{14.3}$$

In addition, a free-stream, stress-free, or von Neumann condition may be used for open flows.

The initial condition $\boldsymbol{u}(\boldsymbol{x},0)$ at time $t = 0$ may be a perturbed steady solution $\boldsymbol{u}_s(\boldsymbol{x})$ as in Chapter 1 of this book.

In what follows, we assume to have gathered $M$ snapshots $\boldsymbol{u}^m$, $m = 1, \dots, M$ from a post-transient flow solution. The snapshots are requested to be statistically representative for the computation of first and second moments.

### 14.2.2 Proper Orthogonal Decomposition

POD is a data-driven realization of a Galerkin approximation

$$\hat{\boldsymbol{u}}(\boldsymbol{x},t) = \boldsymbol{u}_0(\boldsymbol{x}) + \sum_{i=1}^{N} a_i(t) \boldsymbol{u}_i(\boldsymbol{x}) \tag{14.4}$$

of a velocity field $\boldsymbol{u}(\boldsymbol{x},t)$, as detailed in Chapter 6. Here, $\boldsymbol{u}_0$ is the basic mode, for example, the steady Navier–Stokes solution or the mean flow, and $\boldsymbol{u}_i$ are expansion modes with amplitudes $a_i$. These approximations rely on a square-integrable Hilbert space $\mathcal{L}^2(\Omega)$ equipped with an inner product between two elements $\boldsymbol{v}$ and $\boldsymbol{w}$,

$$(\boldsymbol{v},\boldsymbol{w})_\Omega := \int_{\Omega} d\boldsymbol{x}\, \boldsymbol{v} \cdot \boldsymbol{w}. \tag{14.5}$$

The corresponding norm reads $$||\boldsymbol{u}||_\Omega := \sqrt{(\boldsymbol{u},\boldsymbol{u})_\Omega}. \tag{14.6}$$

POD modes are an orthonormal set of expansion modes that minimize the in-sample representation error $$E = \frac{1}{M} \sum_{m=1}^{M} ||\boldsymbol{u}^m - \hat{\boldsymbol{u}}^m||_\Omega^2. \tag{14.7}$$ with respect to the snapshot ensemble.

The computation of the POD modes is performed in the following steps:
