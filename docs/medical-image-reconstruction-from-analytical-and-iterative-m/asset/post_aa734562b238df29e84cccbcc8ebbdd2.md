
A dense layer is able to perform image processing in the sense of traditional convolution, which is essential in denoising and super-resolution tasks because convolution is a special case of inner product and every common neuron contains an inner product operation.

Both of convolutional layers and dense layers require multiple kernels for a single input image. The fully connected architecture implements these multiple kernels by using multiple neurons in each layer. The CNN architecture implements these multiple convolution kernels by using multiple channels in each layer. The CNN architecture further assumes that the convolutional kernels are shift-invariant, while the kernels for the fully connected network generally do not have the shift-invariant property. Therefore, it is not proper to call the inner products in a fully connected network as convolutions.

## 9.10 Summary

- The power of machine learning is in its ability of creating a general mapping between two numerical strings or two images. The key characteristic of the mapping is nonlinearity, which is more general and more powerful than the linear mapping. When given a group of n-tuple/m-tuple pairs, the network tries its best to fit those pairs if the network is large enough. A nonlinear m-dimensional “label” space is created.
- After the network is trained, when an unseen n-tuple is fed to the network, an m-tuple in the “label” space is selected as the output. This selected m-tuple has the common features of those training labels.
- From our own perspectives, the real power of machine learning in imaging is through the versatility of the inner product operation. It can be used for matched filtering, image backprojection, re-gridding, inverse Fourier transform, and so on.
- The training of a network is to determine the model parameters through optimizing an objective function, which is formed by the training pairs and the distance between the model outputs and the labels. The training algorithms are mostly gradient-based. The gradients are calculated by the chain rule, which is referred to as the backpropagation.
- The machine learning techniques can be applied to image reconstruction in many ways:
  - End-to-end direct reconstruction: The network input is a sinogram (or k-space data in MRI). The network output is the reconstructed image.
  - Analytic reconstruction: The network is used as nonlinear denoising filter, which can be applied in the measurement domain or in the image domain. The nonlinear network filter can also replace the ramp filter.
  - Iterative reconstruction: The network can be used as a denoising filter which can be applied to the images at every iteration. The network output can also be used in the objective function of an image reconstruction algorithm.
  - The network model can be used in other areas such as extension of the under-sampled measurements, motion corrections, artifact reduction, and so on.
- Machine learning models contain nonlinearities. Even a quadratic least-squares cost function is used for the training, though the cost function has many local minima. It is most likely that our trained neural network is suboptimal, regardless the optimization algorithms. Some cost functions and some optimization algorithms perform better than others.
- There is no substitute for the measurements of high-quality data. Image denoising and super-resolution do not generate reliable results especially in the medical fields because image denoising or super-resolution neural networks may remove vital details.
- Finally, we should always be alert that the machine learning generated model may not give correct results in some cases. For example, if the sinogram is under-sampled and the object contains something that is never found in the training pairs, it is unlikely that this thing can be recovered by the machine-learned model. If the image is too noisy, the output of a denoising model is still noisy. Therefore, it is unrealistic to expect the network model to produce a perfect result.

## Problem

Problem 9.1 Consider one layer of a dense layer, whose input is an image consisting of 512^2 pixels and the output is an image of the same size. Calculate the total number of parameters in this dense layer. Then consider only layer of a CNN with one channel and the convolution kernel is 3 × 3. Calculate the total number of parameters in this convolutional layer.

Problem 9.2 Consider a U-net. Calculate the total number of pixels in all channels at each layer.

Problem 9.3 For the small dense network shown in Figure 9.34, find the gradient ∂J/∂b1.

Problem 9.4 Write an objective function for iterative Bayesian image reconstruction for the following situation. The image may have some artifacts, which can be effectively detected by a neural network model m. When an image x is fed to m, the model produces a positive value symbolically denoted as m(x). A large value m(x) indicates severe artifacts in the image x. No artifacts are found if m(x) is zero.

## Bibliography

- [1] Widrow B, Samuel D (1985) Stearns: Adaptive Signal Processing, Prentice Hall, ISBN 0-13-004029-0.
- [2] Hornik K, Stinchcombe M, White H (1989) Multilayer feedforward networks are universal approximators (PDF). Neural Networks 2:359–366, Pergamon Press.
- [3] Lu Z, Pu H, Wang F, Hu Z, Wang L (2017) The expressive power of neural networks: A view from the width. Adv Neural Inf Process Syst 30:6231–6239, Curran Associates, arXiv:1709.02540.
- [4] Zhu B, Liu Z, Cauley SF, Rosen BR, Rosen MS (Mar 2018) Image reconstruction by domain-transform manifold learning. Nature 555(7697):487–492.
- [5] Reader AJ, Corda G, Mehranian A, D. Costa-luis C, Ellis S, Schnabel JA (Jan 2021) Deep learning for PET image reconstruction. IEEE Trans Radiat Plasma Med Sci 5(1):1–25, doi: 10.1109/TRPMS.2020.3014786.
- [6] Wang G (2016) A perspective on deep imaging. IEEE Access 4:8914–8924, doi: 10.1109/ACCESS.2016.2624938.
- [7] Zeng GL (2021) A deep-network piecewise linear approximation formula. IEEE Access 9:120665–120674, doi: 10.1109/ACCESS.2021.3109173, PMCID: PMC8442618, NIHMSID: NIHMS1738616, PMID: 34532202, https://ieeexplore.ieee.org/document/9526604?source=authoralert.
- [8] Lv L, Zeng GL, Zan Y, Hong X, Guo M, Chen G, Tao W, Ding W, Huang Q (2022) A back-projection-and-filtering-like (BPF-like) reconstruction method with the deep learning filtration from listmode data in TOF-PET. Med Phys 49(4):2531–2544, https://doi.org/10.1002/mp.15520.
- [9] Zeng GL (2022) Examples of machine learning models from classic to modern. 2022 Intermountain Engineering, Technology and Computing (IETC), 1–6, doi: 10.1109/IETC54973.2022.9796796. https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9796796.

## Index

- AᵀA Fourier equivalence 190
- κ-curve 123
- κ-line 121
- κ-plane 122
- π-segment 104, 106
- l₁ norm 164
- l₂ norm 164
- p.v. 36
- x-gradient 191
- y-gradient 192
- z-gradient 190
- pinv 170
- 1/r weighting 102
- 2D convolution 53
- 2D Fourier transform 196
- 3D backprojection-then-filtering algorithm for Radon data 113
- 3D convolution 97
- 3D Radon inversion formula 112–113
- 3D ramp filter 98
- a priori 173
- absolute temperature 185
- activation function 237
- ADC 200
- adjoint 10
- algebraic reconstruction technique 138
- all-pass filter 35
- analog-to-digital converter 200
- analytic 32
- analytic continuation 31
- angular derivative 103
- antenna 188
- arc length 108–109
- arc orbit 105
- ART 153–154
- attention 237, 238, 254, 261
- attenuation 148
- attenuation corrected FBP algorithm 81
- attenuation correction 80
- attenuation factor 80
- attenuation map 80, 88
- autoencoder 248–249
- backprojection 7–8, 9, 10, 28–29, 52
- backprojection angle 81
- backprojection-then-filtering 26, 96
- backprojection-then-filtering algorithm 54
- backprojection-then-filtering for parallel line-integral data 108
- backprojection–derivative–Hilbert transform 42
- backpropagation 260, 265
- bandwidth 145
- baseband signal 195
- Bayesian 152, 160, 173
- Bayesian objective function 152
- Bayes' law 152
- Beer's law 71
- bias 235
- blob 147
- blob effect 148
- blurred reconstruction 49
- blurring 7
- Boltzmann constant 185
- calculus of variations 207
- center of rotation 82
- central ray 52
- central slice theorem 20–21, 37, 127
- central slice theorem for the Radon transform in 3D 99
- central slice theorem in 3D 94
- CG 155
- chord length 3
- circular cone-beam focal-point orbit 101
- classification 234
- clique 152
- closed loop 137
- closed-form Landweber 189
- coil 188
- coincidence detection 76
- convolutional neural network (CNN) 250–255
- collimator 76
- complete data set 94
- complex analysis 32
- complex central slice theorem 89
- complex signal 196
- complex variable 32
- compressed sensing 133
- Compton scattering 72
- computed tomography 3
- condition number 146
- conditional probability 152
- cone angle 101, 128
