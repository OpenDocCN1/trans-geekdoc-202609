

| Symbol | Description |
|--------|-------------|
| τ | Shear stress |
| θ_G | Parameters of the generator |
| ε | (Normal) Strain |
| ξ | Empirical geometry factor |
| A | Area |
| ar | Aspect ratio |
| b | Bias |
| C | Stiffness |
| c | cos of angle |
| Cfiber | Circumference of fiber |
| cov(x, y) | Covariance of variables x and y |
| covr, covg | Covariance of real and generated images |
| D | Discriminator |
| d | Diameter |
| d(x, xi) | Distance from known point xi to unknown point x |
| dE | Euclidean distance |
| D_x | Definition domain of structuring element |
| E | Young’s modulus |
| e | Charge of an electron |
| E_p | Distance function or error/cost function |
| F × F | Filter dimension |
| F | Force |
| f | Mapping |
| f(x, y) | Filter mask |
| f_1 | Fiber length probability density function |
| G | Generator |
| G(x, y) | Gaussian function |
| G_f, G_m, G_ij | Shear modulus (of the fibers, the matrix or considering the two coordinate axes i and j) |
| G_A | Glyph to tensor A |
| h^(l) | Hidden layer |
| I | Radiation intensity |
| i | Input |
| I(x) | Image intensity function |
| I_0 | Initial condition of radiation intensity |
| K_i | Orthogonal K-invariants |
| l | (Fiber) Length |
| l(y, y_hat) | Log loss/BCE loss |
| l_c | Critical fiber length |
| l_d | Detector pixel size |
| L_FD | Distance between focus and detector |
| L_FO | Distance between focus and object |
| l_t | Length of fiber in order to transfer load |
| l_v | Voxel size |
| L_i | Specific fiber length of the i-th fiber |
| m | Mass |
| m_e | Mass of an electron |
| m_g | Geometric magnification |
| m_i | Moments of i |
| N × N | Image dimension |
| n / N | Number (amount of instances of certain parameter/variable) |
| O | Output size |
| o | Soft sign activation function |
| o(x) | Output image |
| P | Padding |
| p_g | Distribution of the generator |
| p_z | Distribution of noise variables |
| p_i | Probabilities |
| p_j | Fractions of below-threshold and above-threshold pixels |
| R | Mean separation of the fibers normal to their length |
| r / r_f | Radius / Fiber radius |
| r_1 | Learning rate |
| R_i | Orthogonal R-invariants |
| S | Stride |
| s | sin of angle |
| s | Isotropic voxel size |
| t | Threshold |
| T_Otsu | Otsu threshold |
| u | Activation potential |
| U_a | Acceleration voltage |
| V | Volume |
| v | Velocity |
| V(D, G) | Value function |
| v_f | Fiber volume content |
| w_f | Fiber weight content |
| w_i | Weights (fraction) |
| x_n | Input values |
| y_j | Output values |
| z_i | Class label |
| z_j | Gray value |

## Vectors

| Symbol | Description |
|--------|-------------|
| h | Hidden layer vector (output) |
| p | Unit vector describing fiber orientation |
| v_i | Eigenvector |
| x | Location |

## Tensors (2nd order)

| Symbol | Description |
|--------|-------------|
| $\bar{\sigma}$ | Effective stress |
| $\bar{\varepsilon}$ | Effective strain |
| $\Lambda$ | Diagonal eigenvalue matrix |
| $\sigma$ | Stress |
| $\tau$ | Shear stress |
| $\varepsilon$ | Strain |
| A | (Fiber) orientation tensor of second order |
| C | Second order stiffness tensor |
| H | Hessian matrix |
| J | Final structure tensor |
| $K_\sigma$ | Gaussian Blur of width $\sigma$ |
| R | Rotation matrix (composed of the eigenvectors $v_i$) |
| S | Structure tensor |
| W | Weight matrix |
| **UL, ..., LR** | Measured tensors of second order (respectively denoting “Upper Left”, ..., “Lower Right”, etc.). All together form the set of measured tensors $\mathcal{T}_m$ |

## Tensors (4th order)

| Symbol | Description |
|--------|-------------|
| A | (Fiber) orientation tensor of fourth order |
| C | Fourth order stiffness tensor |
| E | Eshelby tensor |
| H⁰ | Reference tensor |
| I | Identity tensor |
| Iˢ | Identity on symmetric tensors |
| L | Localization tensor |
| M | Localization tensor |
| S | Compliance tensor (inverse stiffness tensor) |

## Sets

| Symbol | Description |
|--------|-------------|
| ℝ³ | Real coordinate space of dimension 3 |
| C | Closure approximation |
| P | Probability of finding fiber in direction p |
| S | Two-dimensional unit sphere |
| Tₘ | Set of measured tensors of second order |
| Tᵢ = Tₓ,ᵧ | Set of interpolated tensors of second order at specific (x,y) grid position |
| SO(3) | Special orthogonal group in 3 dimensions |

## Operators

| Symbol | Description |
|--------|-------------|
| (·)’ | Deviatoric part |
| (·)ᵀ | Transpose |
| (·)⁻¹ | Inverse |
| : | Double contraction of tensors |
| * | Convolution |
| (̄·) | Averaged/Effective quantity |
| · | Scalar product or single contraction of tensors |
| det | Determinant |
| (̇·) | Material time derivative |
| ∇(·) | Gradient |
| ⟨·⟩ | Volume average |
| ||(·)|| | Euclidean tensor norm |
| ∇ | Depending on the context, one of the three differential operators gradient, divergence or rotation |
| ⊖ | Erosion |
| ⊕ | Dilation |
| ⊗ | Dyadic product |
| ∂ | Partial derivative |
| * | Rayleigh product |
| tr(·) | Trace of a matrix |
| d | Derivative |

## Quaternions

| Symbol | Description |
|--------|-------------|
| q | Unit quaternion |

## Contents

- Abstract ... i
- Kurzfassung ... iii
- Acknowledgements ... v
- Symbols and acronyms ... vii
- 1 Introduction ... 1
  - 1.1 Motivation ... 1
  - 1.2 Objectives of the thesis ... 3
  - 1.3 Outline of the thesis ... 4
  - 1.4 Remark on the use of own publications in this thesis ... 5
- 2 State of the Art ... 7
  - 2.1 Fiber reinforced polymers ... 7
    - 2.1.1 Fiber reinforcement architectures ... 8
    - 2.1.2 Basic elastic mechanics of FRP ... 12
  - 2.2 Quantitative metrics of DicoFRP microstructures and their determination ... 29
    - 2.2.1 Fiber volume content ... 29
    - 2.2.2 Fiber length distribution ... 34
    - 2.2.3 Fiber orientation distribution ... 41
    - 2.2.4 Representative volume elements and microstructure generation ... 62
  - 2.3 Computed tomography ... 64
    - 2.3.1 Theoretical principles ... 64
    - 2.3.2 Specific challenges of CT scans of CFRP ... 68
    - 2.3.3 Artifacts ... 70
    - 2.3.4 Image processing ... 70
  - 2.4 Artificial intelligence ... 79
    - 2.4.1 Theoretical principles of ANNs ... 80
    - 2.4.2 Generative adversarial networks ... 101
    - 2.4.3 Neural networks in materials science ... 109
- 3 Materials and Methods ... 111
  - 3.1 Materials and processes ... 111
    - 3.1.1 Polyamide 6 ... 111
    - 3.1.2 Polycarbonate ... 112
    - 3.1.3 Carbon fibers ... 113
    - 3.1.4 Glass fibers ... 113
    - 3.1.5 The LFT-D manufacturing process ... 115
    - 3.1.6 Preparation of specimens ... 117
  - 3.2 CT scans ... 120
    - 3.2.1 Device ... 120
    - 3.2.2 Procedure ... 121
    - 3.2.3 Parameter settings ... 121
  - 3.3 Investigations of the initial charge/plastificate ... 122
    - 3.3.1 Initial orientation state ... 122
    - 3.3.2 Porosity and volume determination ... 123
  - 3.4 Determination of fiber volume content ... 127
    - 3.4.1 Chemical dissolution ... 127
    - 3.4.2 Computational methods ... 128
  - 3.5 Determination of fiber length distributions ... 145
  - 3.6 Determination of fiber orientation tensors ... 146
  - 3.7 Interpolation of fiber orientation tensors ... 151
    - 3.7.1 General notes on the interpolation methods ... 152
    - 3.7.2 Component averaging ... 153

