# How to communicate

+   - Parameter server, e.g. Bosen, SSP
+     - A parameter server (PS) is a shared memory system that provides a shared access for the global model parameters θ
+   - Deep learning can be trivially data-parallelized over distributed workers using PS by 3 steps:
+     - Each worker computes the gradients (∇L) on their own data partition ($D_p$) and send them to remote servers;
+     - servers receive the updates and apply (+) them on globally shared parameters;
+     - Each worker pulls back the updated parameters ($\theta_t$)