# # Desiderata for a good loss function

![](bbox=[0.081, 0.183, 0.335, 0.545])

![](bbox=[0.353, 0.183, 0.61, 0.545])

![](bbox=[0.627, 0.183, 0.883, 0.545])

+   - Must be smooth and not have many poor local optima
- Low slopes far from the optimum == bad
  - Initial estimates far from the optimum will take forever to converge
- High slopes near the optimum == bad
  - Steep gradients