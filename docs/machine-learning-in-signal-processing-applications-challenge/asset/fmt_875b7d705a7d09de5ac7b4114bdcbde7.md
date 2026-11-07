
## 8.3 Multiresolution Analysis
To study the reconstruction of a function from wavelet coefficients and the idea behind `WNN`, multiresolution analysis (`MRA`) plays an important role. `MRA` views a function at various levels of approximations or scales. Decomposition of a function *x*(*t*) into various scales begins by projecting it into a sufficiently high-resolution subspace **C**[*M*], i.e.

$$x\_{M} = \\sum\\limits\_{k}c\_{M,k}\\phi\\left( {2^{M}t - k} \\right) \\in \\mathbf{C}\_{M}$$

(8.13)

Thus, subspace **C**[∞] is the space of original analog (continuous-time) signal *x*(*t*), and *x*[*M*] ∈ **C**[*M*] ⊆ **C**[∞] is its lower resolution version. Subspace **C**[*j*] at each level is itself composed of coarser approximation subspace **C**[*j* − 1] and a wavelet subspace **W**[*j* − 1]. Since the subspaces are nested, we can write

**C**[*M*] = **W**[*M* − 1] + **C**[*M* − 1]

$$= \\sum\\limits\_{i = 1}^{I}\\mathbf{W}\_{M - i} + \\mathbf{C}\_{M - I}$$

(8.14)

where
1. *I* is the number of levels of subspace or wavelet decomposition.

The signals in the corresponding subspaces are related as

$$x\_{M}\\left( t \\right) = \\sum\\limits\_{i = 1}^{I}y\_{M - i}\\left( t \\right) + x\_{M - I}\\left( t \\right)$$

(8.15)

where
1. *x*[*M* − *I*](*t*) is the coarsest approximation of *x*[*M*], and

$$x\_{j}\\left( t \\right) = \\sum\\limits\_{k}c\_{j,k}\\phi\\left( {2^{j}t - k} \\right) \\in \\mathbf{C}\_{j}$$

(8.16)

$$y\_{j}\\left( t \\right) = \\sum\\limits\_{k}w\_{j,k}\\psi\\left( {2^{j}t - k} \\right) \\in \\mathbf{W}\_{j}$$

(8.17)

### 8.3.2 Wavelet Neural Network
`WNN` combines the principles of wavelet and neural network into one. From Equation (8.15), it can be concluded that an arbitrary function can be approximated using basis functions from wavelet and approximation subspaces. This idea has led to the development of `WNN` where scale and position factors are iteratively adapted to approximate a target function.

The simplest form of `WNN` consists of only one hidden neuron as shown in [Figure 8.3](#ch08.xhtml#f8_3). It consists of input *x*, wavelet function translated by *τ* and dilated by factor *δ*. The output of the function is *y* and computed as follows:

![FIGURE 8.3 A single wavelon.](`images/Fig08_03.jpg`)

[**FIGURE 8.3**](#ch08.xhtml#f8_3b) A single wavelon.

$$y = \\psi\_{\\delta,\\tau}\\left( x \\right) = \\psi\\left( \\frac{x - \\tau}{\\delta} \\right)$$

(8.18)

The output *y* of such a neuron is nonzero only when the input lies within the support of the function *ψ*[*δ*, *τ*](*x*). Several such single “wavelet neurons” or “wavelons” form a hidden layer of `WNN` and their output are linearly combined to approximate a given function.

Wavelet neural networks are mainly of two types based on their architecture. The first on is based on relation (8.16) in which a given function is approximated using scaling function *ϕ* only. In this variety of `WNN`, wavelet analysis and neural network operations are performed separately ([Veitch 2005](#ch08.xhtml#r8_51)). Such networks are called *wavenet*, in which signal input to the network is decomposed using different wavelet basis in the hidden layer and then combined at the output layer. In the architecture of wavenets, translation and dilation factors are fixed initially and are not changed during learning process of neural network. Only weights *w*[*i*] from hidden layer to the output nodes are modified. The output of such a network is given as

$$y = \\sum\\limits\_{i = 1}^{N\_{\\phi}}w\_{i}\\phi\_{\\delta,\\tau}\\left( x \\right)$$

(8.19)

where
1. *N*[*ϕ*] is the number of hidden layer units required to cover the domain of the function to be analyzed, and *ϕ*[*δ*, *τ*] is a scaling function.

Wavenets are limited by their fixed set of basis functions and are not suitable for modeling channels with time-varying response. The architecture of wavelet networks in which translation and dilation parameters of the hidden units are also modified, along with output weights of the network, is in the process of training. In prevalent nomenclature, such networks are referred to as *wavelet networks* and are considered in this work. In all the subsequent discussions, we shall mean `WNN` to be wavelet networks only. [Figure 8.4](#ch08.xhtml#f8_4) shows the architecture of a one-dimensional `WNN`. In contrast to multidimensional `WNN` discussed in the next section, input *x* to this network is a scalar or a one-dimensional sequence. Wavelons in this network are shown as *ψ*[1], …, *ψ*[*N*[*ψ*]] with corresponding values of translation parameters *τ*[1], …, *τ*[*N*[*ψ*]] and dilation parameters *δ*[1], …, *δ*[*N*[*ψ*]]. Output *y* is obtained by weighted sum as

![FIGURE 8.4 One-dimensional wavelet neural network.](`images/Fig08_04.jpg`)

[**FIGURE 8.4**](#ch08.xhtml#f8_4b) One-dimensional wavelet neural network.

$$y = \\sum\\limits\_{i = 1}^{N\_{\\psi}}c\_{i}\\psi\_{i}\\left( x \\right) + a\_{0}$$

(8.20)

where
1. *c*[1], …, *c*[*N*[*ψ*]] are output layer weights.

The term *a*[0] in Equation (8.20) is the bias parameter and is required for approximating functions whose mean is not zero.

## 8.4 Multidimensional Wavelet Neural Network
Based on the `WNN` model in [Alexandridis and Zapranis (2013)](#ch08.xhtml#r8_6), a multidimensional wavelet network is constructed in which different inputs are interconnected with multiple hidden units. Outputs of the hidden units *ψ*[*j*](**x**), as well as direct inputs *x*[*i*], are then linearly combined, to obtain the final output *ŷ*. [Fig. 8.5](#ch08.xhtml#f8_5) shows the structure of single hidden-layer multidimensional `WNN`. For *N*[*I*] input wavelet network with *N*[*ψ*] hidden units or wavelons, input-output relation is given as

$$\\hat{y} = f\\left( \\mathbf{x} \\right) = \\sum\\limits\_{j = 1}^{N\_{\\psi}}c\_{j}\\psi\_{j}\\left( \\mathbf{x} \\right) + \\sum\\limits\_{i = 1}^{N\_{I}}a\_{i}x\_{i} + a\_{0}$$

(8.21)

where
1. *c*[*j*] are weights from wavelons to output,
2. *a*[*i*] are weights from input layer to the output, and
3. *a*[0] is the bias at the output layer.

In the expression (8.21), *ψ*[*j*](**x**) is a multidimensional wavelet given as

$$\\psi\_{j}\\left( \\mathbf{x} \\right) = \\prod\\limits\_{i = 1}^{N\_{I}}\\psi\\left( z\_{ij} \\right)$$

(8.22)

where
1. *z*[*i**j*] = (*x*[*i*]−*τ*[*i**j*])/*δ*[*i**j*].
2. The weights *τ*[*i**j*] correspond to translation and *δ*[*i**j*] correspond to dilation factors.

For performance evaluation of the proposed equalizer, Mexican hat function is considered for mother wavelet and is given as

*ψ*(*z*) = (1−*z*²)*e*^( − *z*²/2)

(8.23)

A `WNN` with *N*[*I*] inputs and scalar output *ŷ* is considered, which is trained using a set of *N* examples {**x**(*n*),*y*(*n*)}, where **x**(*n*) = [*x*[1](*n*),…, *x*[*N*[*I*]](*n*)]^(*T*) is the input vector for training example *n*. The objective of the training is to minimize mean-square error (MSE) *E*\[|*y*−*ŷ*|²\] between target output *y*(*n*) and actual network output *ŷ*(*n*). The `WNN` can be represented in the form of a parametrized nonlinear model ([Figure 8.5](#ch08.xhtml#f8_5)):

![FIGURE 8.5 Architecture of a multidimensional wavelet neural network.](`images/Fig08_05.jpg`)

[**FIGURE 8.5**](#ch08.xhtml#f8_5b) Architecture of a multidimensional wavelet neural network.

*ŷ*(*n*) = *f*(**x**(*n*),**w**)

(8.24)

where the set of adjustable parameters of the `WNN` is **w** = {*a*[0], *a*[*i*],*c*[*j*],*τ*[*i**j*],*δ*[*i**j*]} with *i* = 1, …, *N*[*I*] and *j* = 1, …, *N*[*ψ*].

## 8.5 Proposed WNN DFE Architecture
### 8.5.1 Equalizer Architecture
