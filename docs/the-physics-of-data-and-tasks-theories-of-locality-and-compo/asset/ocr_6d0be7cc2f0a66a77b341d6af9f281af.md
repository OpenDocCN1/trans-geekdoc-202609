![](bbox=[0.19945, 0.07345, 0.70055, 0.21685])

Figure 42: Noisy (optimally-regularized) vs noiseless (ridgeless) learning curves for depth-three deep convolutional NTKs ($v = 1/2$) in a teacher-student setting. Comparison between the learning curves in the noisy and noiseless case. Dashed lines represent the rates predicted with source-capacity bounds and replica calculations, respectively. Shaded areas represent the empirical standard deviations, b. Decay of the optimal ridge with the number of training points.

is a hierarchical RFK ($v = 3/2$), the target function corresponds to the output of an infinite-wide, deep hierarchical neural network at initialization. The error rates are obtained from Equation 66, after setting the smoothness exponent $m = v_T$ (the smoothness exponent of the teacher covariance kernel).

The first case consists of one-hidden-layer convolutional teacher (left) and student (right) kernels.

![](bbox=[0.17845, 0.5134500000000001, 0.69655, 0.57345])

As highlighted in blue, the output of the teacher is a linear combination (dashed lines indicate the learning weight outputs) of $s_1$-dimensional functions of the input patches. If the structure of the student is matched to one of the teacher, the learning problem becomes effectively $(s_1 - 1)$-dimensional, and the error decays instead of $P^{-1/d_T}$, with $d_T$ the total input dimension with the number of spherical constants subtracted (one per patch). Notice that the role of the student's structure, i.e., the algorithm, is as crucial as the role of the teacher, i.e., the task. Indeed, using a fully-connected student with no prior on the task's locality would result in an error's decay caused by dimensionality. However, in contrast to fully-connected students, shallow students are only able to learn tasks with the same structure. In particular, any task entails nonlinear interactions between patches – which are arguably crucial in order to learn data image – belongs to their null space.

> See, e.g. Lee et al. [Lee+17] for the equivalence between infinitely-wide networks and Gaussian random fields with covariance given by the RFK.