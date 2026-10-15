**Step 2:** The position and memory of the crows are randomly configured.

**Step 3:** Calculate the fitness function for each crow.

**Step 4:** Generate new solution by Eq (2).

**Step 5:** Check the feasibility of new solution: By relying on the feasibility or infeasibility of the solution where if the solution is feasible, the crow adjusts its location and the solution is acceptable, otherwise the solution is rejected and the crow remains in its current location.

**Step 6:** Calculate the fitness function for each crow in a new location.

**Step 7:** Update memory:

Crows change their memories according to the formula below:

$$m^{i,iter+1} = \begin{cases} x^{i,iter+1} \ f(x^{i,iter+1}) \ is\ better\ than\ f(m^{i,iter}) \\ m^{i,iter} \ otherwise \end{cases}\tag{3}$$

**Step 8:** Check the end criterion by repeating steps from 4-7 until the termination criterion is met.

# 7.2.4. Pseudocode of CSA

```
Random initialization of the position of a flock of N crows in the search space
Evaluation of the position of the crows
Initialization of the memory of each crow
While iter < iter_max
    for i=1:N (all N crows of the flock)
        Random selection of one of the crows to follow (e.g. j)
        Define an awareness probability
```