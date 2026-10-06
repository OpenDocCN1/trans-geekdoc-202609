# Neuron
NeuroResource

# CellPress

Figure 8. Comparison of DUNL with LFADS; DUNL finds local components in single trials

# A

Raster

Synthetic Experiment

![](bbox=[0.105, 0.15, 0.335, 0.215])

Raster

Smoothed Raster

![](bbox=[0.105, 0.245, 0.335, 0.305])

Raster

True Codes

![](bbox=[0.105, 0.335, 0.335, 0.395])

# B

LFADS

Factor 1

![](bbox=[0.395, 0.15, 0.625, 0.315])

Trials

Factor 2

![](bbox=[0.395, 0.335, 0.625, 0.495])

# C

Raster

DUNL

Smoothed Raster

![](bbox=[0.105, 0.355, 0.335, 0.415])

Raster

DUNL estimated rate

![](bbox=[0.105, 0.445, 0.335, 0.505])

# D

Raster

Smoothed Raster

![](bbox=[0.395, 0.355, 0.625, 0.415])

Raster

LFADS estimated rate

![](bbox=[0.395, 0.445, 0.625, 0.505])

# E

Raster

25 trials

![](bbox=[0.105, 0.54, 0.335, 0.6])

Raster

100 trials

![](bbox=[0.395, 0.54, 0.625, 0.6])

# F

LFADS

![](bbox=[0.105, 0.635, 0.625, 0.695])

+   (B) LFADS estimates parameters for the entire trial

+   (C) We estimate rate (and smoothed raster on top). (DUNL estimates rates in 25 ms bins (middle) and LFADS identifies local codes for the two kernels (bottom). LFADS estimates rate at the original rate (middle) and DUNL spans the entire trial (bottom). Note: DUNL uses 5ms for visualization at 1ms resolution, using piecewise-constant.

+   (E) Kernel learned by DUNL with 25, 50, 100, 400, and 1600 training trials, compares with the true kernels (gray).

+   (F) Average LFADS factors across different training scenarios

See Figures S1–S7 and S8.

# DISCUSSION

We introduced unbiased learning-based neural networks$^{20,31}$ to recover local-rule structures and deplexed neural activity in human-interpretable latent variables. Based on algorithm$^{49,50}$ this approach enables the design of deep neural networks. For this test, we apply temporal sparse coding to neural recordings, detecting, and characterizing sparse events in latent space. Our approach shows that DUNL meets criteria for a decomposition method: it supports neural input data, operates on limited datasets, and adapts to various signals. Unlike other methods, which span entire trials for dimensionality reduction (5), DUNL and LFADS$^{39}$ scales well in scalability and stability across neurons, time, and trials. It outperforms methods like convNM$^{25,36}$ and seqNM$^{37}$ (see supplemental discussion for details).

Our method combines the convolutional property and sparsity constraints with techniques like the statistical framework of GLM; and the power of deep learning: enables; finding local-rule structures by learning (covariates) leveraging deep and backpropagation for data fitting, such that neural response functions, and event-spikes in single trials are extracted directly from data, and latent variables and representations.

when users prefer to impose kernel constraints (e.g., orthogonality in PCA, NMF, or bases in GLM). Constraints and regulations (such as global co-activation, non-group sparsity, sparsity) can be incorporated into the architecture as needed.

Exhaustious behavior, and neural activity time as a fundamental variable, sparse coding has long served as an interpretable framework for sensory processing$^{38}$. Our method, through expressive neural sparse coding of single-neural activity into space, temporally aggregating components that correlate with stimuli and activity/behavior. Our approach characterizes

differential equations. The GLM-like statistical foundation of our models connects latent representations to neural data, while algorithm learning integrates these into translate

Neuron 1/7, 1151–1168, April 16, 2023