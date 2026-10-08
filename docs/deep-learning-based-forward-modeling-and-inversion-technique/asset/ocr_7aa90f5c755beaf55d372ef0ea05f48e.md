# Deep Learning-Based Forward Modeling and Inversion Techniques

![](bbox=[0.215, 0.093, 0.755, 0.358])

FIGURE 2.25

The training curve of the passive cases.

# 2.3.6 Results

After building up the required dataset and constructing the network, it is feasible to embark on the training process. The training is conducted on TensorFlow 2.0 [35] on Windows Server 2019 using a Dell Precision Workstation 7920 with Intel Xeon Silver 4214 CPUs and a GeForce RTX 2080 Ti (VRAM:11G) GPU. During the training, the loss on both the training and testing are recorded, respectively. Once they have declined to a low level, the network is regarded to be successfully trained. Then, testing sets are employed to measure the performance of the network. This section includes two modules, where the training curves, numerical results, generalization ability, statistical analysis and computing acceleration of the passive and active cases are discussed, respectively.

# 2.3.6.1 Passive Cases

+   - A. Training

As mentioned before, there are three datasets for the passive cases, namely the Basic dataset, the enhanced dataset, and the open-source dataset, where only the first two are trained. Figure 2.25 provides a clear view of the loss on both the training set and the testing set.

In the experiments, 70% of the 12000 samples on the basic dataset and 20000 samples on the enhanced dataset are trained, respectively. After about 1.5 × 10^5 epochs and 6 hours, both the two training reach convergence.

+   - B. Numerical results