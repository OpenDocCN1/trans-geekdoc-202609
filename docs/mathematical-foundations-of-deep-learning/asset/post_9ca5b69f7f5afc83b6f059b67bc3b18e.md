
bounds have been instrumental in analyzing neural networks, Bayesian ensembles, and stochastic processes, offering theoretical guarantees even in high-dimensional, non-convex optimization landscapes.

## 4.2 Spectral Regularization

The concept of spectral regularization, which refers to the preferential learning of low-frequency modes by neural networks before high-frequency modes, emerges from a combination of Fourier analysis, optimization theory, and the inherent properties of deep neural networks. This phenomenon is tightly connected to the functional approximation capabilities of neural networks and can be rigorously understood through the lens of Fourier decomposition and the gradient descent optimization process.

### Literature Review

Jin et al. (2025) [102] introduced a novel confusional spectral regularization technique to improve fairness in machine learning models. The study focuses on the spectral norm of the robust confusion matrix and proposes a method to control spectral properties, ensuring more robust and unbiased learning. It provides insights into how regularization can mitigate biases in classification tasks.

Ye et al. (2025) [103] applied spectral clustering with regularization to detect small clusters in complex networks. The work enhances spectral clustering techniques by integrating regularization methods, allowing improved performance in anomaly detection and community detection tasks. The approach significantly improves robustness in highly noisy data environments.

Bhattacharjee and Bharadwaj (2025) [104] explored how spectral domain representations can benefit from autoencoder-based feature extraction combined with stochastic regularization techniques. The authors propose a Symmetric Autoencoder (SymAE) that enables better generalization of spectral features, particularly useful in high-dimensional data and deep learning applications.

Wu et al. (2025) [105] applied spectral regularization to geophysical data processing, specifically for high-resolution velocity spectrum analysis. The approach enhances the resolution of velocity estimation in seismic imaging by using hyperbolic Radon transform regularization, demonstrating how spectral regularization can benefit applications beyond traditional ML.

Ortega et al. (2025) [106] applied Tikhonov regularization to atmospheric spectral analysis, optimizing gas retrieval strategies in high-resolution spectroscopic observations. The work significantly improves methane (CH4) and nitrous oxide (N2O) detection accuracy by reducing noise in spectral measurements, showcasing the impact of spectral regularization in remote sensing and environmental monitoring.

Kazmi et al. (2025) [107] proposed a spectral regularization-based federated learning model to improve robustness in cybersecurity threat detection. The model addresses the issue of non-IID data in SDN (Software Defined Networks) by utilizing spectral norm-based regularization within deep learning architectures.

Zhao et al. (2025) [108] introduced a regularized deep spectral clustering method, which enhances feature selection and clustering robustness. The authors utilize projected adaptive feature selection combined with spectral graph regularization, improving clustering accuracy and interpretability in high-dimensional datasets.

Saranya and Menaka (2025) [109] integrated spectral regularization with quantum-based machine learning to analyze EEG signals for Autism Spectrum Disorder (ASD) detection. The proposed method improves spatial filtering and feature extraction using wavelet-based regularization, leading to more reliable EEG pattern recognition.

Dhalbisoit et al. (2024) [110] developed a Regularized Zero-Forcing (RZF) method for spectral efficiency optimization in beyond 5G networks. The authors demonstrate that spectral regularization techniques can significantly improve signal-to-noise ratios in wireless communication systems, optimizing data transmission in massive MIMO architectures.

Wei et al. (2025) [111] explored the use of spectral regularization in medical imaging, particularly in 3D near-infrared spectral tomography. The proposed model integrates regularized convolutional neural networks (CNNs) to improve tissue imaging resolution and accuracy, demonstrating an application of spectral regularization in biomedical engineering.

Let us define a target function \( f(\mathbf{x}) \), where \( \mathbf{x} \in \mathbb{R}^d \), and its Fourier transform \( \hat{f}(\boldsymbol{\xi}) \) as

\(\hat{f}(\boldsymbol{\xi}) = \int_{\mathbb{R}^d} f(\mathbf{x}) e^{-i 2 \pi \boldsymbol{\xi} \cdot \mathbf{x}} \, d\mathbf{x}\) (153)

This transform breaks down \( f(\mathbf{x}) \) into frequency components indexed by \( \boldsymbol{\xi} \). In the context of deep learning, we seek to approximate \( f(\mathbf{x}) \) with a neural network output \( f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta}) \), where \( \boldsymbol{\theta} \) represents the set of trainable parameters. The loss function to be minimized is typically the mean squared error:

\(\mathcal{L}(\boldsymbol{\theta}) = \int_{\mathbb{R}^d} |f(\mathbf{x}) - f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta})|^2 \, d\mathbf{x}\) (154)

We can equivalently express this loss in the Fourier domain, leveraging Parseval's theorem:

\(\mathcal{L}(\boldsymbol{\theta}) = \int_{\mathbb{R}^d} \left| \hat{f}(\boldsymbol{\xi}) - \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \right|^2 \, d\boldsymbol{\xi}\) (155)

To solve for \( \boldsymbol{\theta} \), we employ gradient descent:

\(\boldsymbol{\theta}^{(t+1)} = \boldsymbol{\theta}^{(t)} - \eta \nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta})\) (156)

where \( \eta \) is the learning rate. The gradient of the loss function with respect to \( \boldsymbol{\theta} \) is

\(\nabla_{\boldsymbol{\theta}} \mathcal{L}(\boldsymbol{\theta}) = 2 \int_{\mathbb{R}^d} \left( \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) - \hat{f}(\boldsymbol{\xi}) \right) \nabla_{\boldsymbol{\theta}} \hat{f}_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \, d\boldsymbol{\xi}\) (157)

At the core of this gradient descent process lies the behavior of the gradient \( \nabla_{\boldsymbol{\theta}} f_{\text{NN}}(\boldsymbol{\xi}; \boldsymbol{\theta}) \) with respect to the frequency components \( \boldsymbol{\xi} \). For neural networks, particularly those with ReLU activations, the gradients of the output with respect to the parameters are expected to decay for high-frequency components. This can be approximated as

\(\mathcal{R}(\boldsymbol{\xi}) \sim \frac{1}{1 + \| \boldsymbol{\xi} \|^2}\) (158)

which implies that the neural network is inherently more sensitive to low-frequency components of the target function during early iterations of training. This spectral decay is a direct consequence of the structure of the network’s activations, which are more sensitive to low-frequency features due to their smoother, lower-order terms. To understand the role of the neural tangent kernel (NTK), which governs the linearized dynamics of the neural network, we define the NTK as

\(\Theta(\mathbf{x}, \mathbf{x}'; \boldsymbol{\theta}) = \sum_{i=1}^P \frac{\partial f_{\text{NN}}(\mathbf{x}; \boldsymbol{\theta})}{\partial \theta_i} \frac{\partial f_{\text{NN}}(\mathbf{x}'; \boldsymbol{\theta})}{\partial \theta_i}\) (159)

The NTK essentially describes how the output of the network changes with respect to its parameters. The evolution of the network’s output during training can be approximated by the solution to a linear system governed by the NTK. The output of the network at time \( t \) is given by

\( f_{\text{NN}}(\mathbf{x}; t) = \sum_k c_k \left( 1 - e^{-\eta \lambda_k t} \right) \phi_k(\mathbf{x}) \) (160)

where \(\{ \lambda_k \}\) are the eigenvalues of \( \Theta \), and \(\{ \phi_k(\mathbf{x}) \}\) are the corresponding eigenfunctions. The eigenvalues \( \lambda_k \) determine the speed of convergence for each frequency mode, with low-frequency modes (large \( \lambda_k \)) converging more quickly than high-frequency ones (small \( \lambda_k \)):

\( 1 - e^{-\eta \lambda_k t} \to 1 \text{ for large } \lambda_k \text{ and } 1 - e^{-\eta \lambda_k t} \to 0 \text{ for small } \lambda_k \) (161)

This differential learning rate for frequency components leads to the spectral regularization phenomenon, where the network learns the low-frequency components of the function first, and the
