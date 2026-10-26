# # Deep Belief Nets and Boltzmann Machines

![](bbox=[0.233, 0.206, 0.448, 0.685])

![](bbox=[0.513, 0.206, 0.719, 0.685])

+   - DBMs are fully un-directed models (Markov random fields).
+     - Can be trained similarly as RBMs via MCMC (Hinton & Sejnowski, 1983)
+     - Use a variational approximation of the data distribution for faster training (Salakhutdinov & Hinton, 2009)
+     - Similarly, can be used to initialize other networks for downstream tasks