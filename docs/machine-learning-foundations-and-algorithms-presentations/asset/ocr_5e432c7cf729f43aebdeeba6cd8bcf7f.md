# 2nd order methods

+   * **Quasi-Newton methods (BFGS most popular):** instead of inverting the Hessian (O(N³)), approximate inverse Hessian with rank 1 updates over time (O(N²) each).
* **L-BFGS (Limited memory BFGS):** Does not form/store the full inverse Hessian.
  - Usually works very well in full batch, deterministic mode i.e. if you have a single, deterministic f(x) then L-BFGS will probably work very nicely
  - Does not transfer very well to mini-batch setting. Gives bad results. Adapting L-BFGS to large-scale, stochastic setting is an active area of research.

In practiseise:
* **Adam** is a good default choice in most cases, but also try SGD (mini-batches) with learning rate schedule if you think overfit with **Adam**
* If you can afford to do full batch updates then try out L-BFGS (and don’t forget to disable all sources of noise)