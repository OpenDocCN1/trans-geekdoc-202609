The Lagrangian penalty factor $\alpha$ is introduced, and finally the dual type of soft interval Gaussian kernel SVM is obtained as follows:

```
$$\begin{gathered} \min _{\alpha} \frac{1}{2} \sum_{i=1}^{N} \sum_{j=1}^{N} \alpha_{i} \alpha_{j} y_{i} y_{j} \exp \left(-\gamma\left\|x_{i}-x_{j}\right\|^{2}\right)-\sum_{i=1}^{N} \alpha_{i} \\ s.t. \quad 0 \leq \alpha_{i} \leq c, \quad i=1,2, \cdots N, \\ \sum_{i=1}^{N} \alpha_{i} y_{i}=0 \end{gathered}$$

(24)
```

# ## 6. Experiment and Simulation

The method based on VMD-MMFD is used for feature extraction and the fault diagnosis of fault circuits. The specific process is shown in Figure 2.

![](bbox=[0.18, 0.32, 0.61, 0.56])

To verify the effectiveness of this method, simulation experiments and calculations were carried out through the software Multisim, Matlab, and Python. The Sallen-Key band-pass filter circuit was taken as an example to verify the analysis method of soft-fault diagnosis based on variational-mode decomposition and mathematical morphology fractal dimensions. The circuit diagram is shown in Figure 3.

![](bbox=[0.18, 0.69, 0.83, 0.88])