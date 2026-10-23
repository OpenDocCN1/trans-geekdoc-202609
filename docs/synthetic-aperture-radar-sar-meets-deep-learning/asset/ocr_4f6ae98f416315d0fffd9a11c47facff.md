to replace the PGE-PCA in the traditional LS unwrapping method. As the accuracy of the phase gradient estimated by PGENet is significantly higher and more robust than that of the phase gradient estimated by PGE-PCA, the proposed method has higher accuracy than the traditional LS phase unwrapping method. A series of experimental results of simulated wrapped phase and real InSAR data demonstrate that the proposed method outperforms the other five well-established phase unwrapping methods and is robust to noise.

This paper is organized as follows. Section 2 introduces the principles of phase unwrapping, problem analysis, PGENet, and the proposed method. In Section 3, the data generation method, loss function, performance evaluation index, and experiment settings are described. In Section 4, a series of experimental results using simulated and real InSAR data are presented. Section 5 and Section 6 present the discussion and conclusions of the paper, respectively.

# 2. PGENet-LS Phase Unwrapping Method

In this section, we first introduce the principle of phase unwrapping and how to use deep neural networks instead of PGE-PCA to estimate the phase gradient. Then we describe the detailed structure of PGENet, and finally introduce the processing flow of the PGENet-LS phase unwrapping method.

# 2.1. Principle of Phase Unwrapping

The wrapped phase is distributed in (−π, π] containing the ambiguities of integral multiples of 2π. For an image pixel point (i,j), the relationship between the wrapped phase φ_{i,j} and the unwrapped phase φ'_{i,j} can be expressed as

$$\varphi'_{i,j} = \varphi_{i,j} + 2\pi k_{i,j} \tag{1}$$

where k_{i,j} is a sequence of integers, which is called the wrap count. When k_{i,j} is known, the unwrapped phase can be recovered from the wrapped phase. However, a unique solution k_{i,j} cannot be obtained because there are two unknowns in (1). Therefore, in the traditional phase unwrapping method, the phase continuity assumption is used to ensure the uniqueness of the phase unwrapping result. Under this assumption, the LS phase unwrapping method can be divided into the following two steps: phase gradient estimation and implementation of the least squares solver. The flowchart is shown in Figure 1.

Step 1: According to the phase continuity assumption, for the two-dimensional phase unwrapping issue, the horizontal gradient and vertical phase gradient can be estimated by

$$\Delta^x'_{i,j} = \begin{cases} \varphi_{i,j+1} - \varphi_{i,j}, & -\pi \le \varphi_{i,j+1} - \varphi_{i,j} \le \pi \\ \varphi_{i,j+1} - \varphi_{i,j} - 2\pi, & \pi < \varphi_{i,j+1} - \varphi_{i,j} \le 2\pi \\ \varphi_{i,j+1} - \varphi_{i,j} + 2\pi, & -2\pi \le \varphi_{i,j+1} - \varphi_{i,j} < -\pi \end{cases} \tag{2}$$ $$\Delta^y'_{i,j} = \begin{cases} \varphi_{i+1,j} - \varphi_{i,j}, & -\pi \le \varphi_{i+1,j} - \varphi_{i,j} \le \pi \\ \varphi_{i+1,j} - \varphi_{i,j} - 2\pi, & \pi < \varphi_{i+1,j} - \varphi_{i,j} \le 2\pi \\ \varphi_{i+1,j} - \varphi_{i,j} + 2\pi, & -2\pi \le \varphi_{i+1,j} - \varphi_{i,j} < -\pi \end{cases} \tag{3}$$

where Δ^x'_{i,j} and Δ^y'_{i,j} are the horizontal gradient and vertical gradient, respectively. For brevity, the step is called PGE-PCA. Step 2: After obtaining the estimated horizontal gradient Δ^x'_{i,j} and vertical gradient Δ^y'_{i,j}, the final unwrapping result φ'_{i,j} can be calculated according to the least squares solver of (4). $$\arg\min_{\varphi'_{i,j}} \sum_i \sum_j \left| \varphi'_{i,j+1} - \varphi'_{i,j} - \Delta^x'_{i,j} \right|^2 + \sum_i \sum_j \left| \varphi'_{i+1,j} - \varphi'_{i,j} - \Delta^y'_{i,j} \right|^2 \tag{4}$$