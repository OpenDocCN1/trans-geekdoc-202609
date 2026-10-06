# # Computation graph (example)

## Can we find an algorithm to do it more systematically?

+   - The goal isn't to obtain closed-form solutions...
- but to be able to write a program that efficiently computes the derivatives.

We can diagram out the computations using a computation graph:

![](bbox=[0.638, 0.545, 0.846, 0.903])

+   - The nodes represent all the inputs and computed quantities
- The edges represent which nodes are computed directly as a function of which other nodes.