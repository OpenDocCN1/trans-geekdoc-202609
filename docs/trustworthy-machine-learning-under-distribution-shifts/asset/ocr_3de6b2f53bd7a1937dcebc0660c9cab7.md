# 3.1 INTRODUCTION

![](bbox=[0.263, 0.137, 0.735, 0.372])

FIGURE 3.18. Illustration of photon-light corruptions.

perception systems [119, 28, 120]. During the training, the encountered corruptions are essentially perceived as a distribution shift, which would significantly hinder the prediction results [35, 121, 121, 122, 124]. Therefore, to mitigate the performance degradation, generalizing to corrupted data distributions has drawn lots of attention [69, 125].

In the real world, noise corruptions are commonly known as photon-light imaging problems [126, 127, 128, 129] which arise due to numerous small photon corruptions arriving at an image sensor. Consequently, different numbers of captured photons would form different levels of corruption severity, further producing multiple data distributions and varying impacts on learning models [114]. Specifically, the encountered photon-light corruption $\mathcal{C}$ is a composition of multiple noise photons $u_i$, which is triggered by some discrete factors with a certain probability during a time. For example, a photon $u$ can be triggered by each platform changing, redistribution, transmission, etc. More photons are captured, and severe corruption would be applied to the image. Therefore, the severity $s$ of the photon-limited corruptions $\mathcal{C}$ can be modeled by Poisson distribution, i.e., $s \sim P(s; \lambda) = \frac{\lambda^s e^{-\lambda}}{s!}$, which is illustrated in Figure 3.1. As a result, the real-world dataset is not completely composed of clean data, but contains corrupted data with various severities.

Dealing with such a realistic problem by vanilla empirical risk minimization can achieve satisfactory average accuracy on the whole training set. However, to the extremely limited