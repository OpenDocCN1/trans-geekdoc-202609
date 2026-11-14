```
Algorithm 6.6: Tabu search.
t := 0 // counts iterations
c := 0 // counts number of steps with no progress
Initialize x0
x* := x0 // current best incumbent
while c < cmax do
    x_{t+1} = argmax_{x \in nbr(x_t) \\ {x_{t-r},...,x_{t-1}}} f(x)
    if f(x_{t+1}) > f(x*) then
        x* := x_{t+1}
        c := 0
    else
        c := c + 1
    t := t + 1
return x*
```

state that has not been seen before. We can enforce this by keeping a tabu list which tracks the \(\tau\) most recently visited states. This forces the algorithm to explore new states, and increases the chances of escaping from local maxima. We continue to do this for up to \(c_{max}\) steps (known as the "tabu tenure"). The pseudocode can be found in Algorithm 6.6. (If we set \(c_{max} = 1\), we get greedy hill climbing.)

For example, consider what happens when tabu search reaches a hill top, \(x_t\). At the next step, it will move to one of the neighbors of the peak, \(x_{t+1} \in \text{nbr}(x_t)\), which will have a lower score. At the next step, it will move to the neighbor of the previous step, \(x_{t+2} \in \text{nbr}(x_{t+1})\); the tabu list prevents it cycling back to \(x_t\) (the peak), so it will be forced to pick a neighboring point at the same height or lower. It continues in this way, "circling" the peak, possibly being forced downhill to a lower level-set (an inverse basin flooding operation), until it finds a ridge that leads to a new peak, or until it exceeds a maximum number of non-improving moves.

According to [RN10, p.123], tabu search increases the percentage of 8-queens problems that can be solved from 14% to 94%, although this variant takes an average of 21 steps for each successful instance and 64 steps for each failed instance.

# 6.7.1.3 Random search

A surprisingly effective strategy in problems where we know nothing about the objective is to use random search. In this approach, each iterate \(x_{t+1}\) is chosen uniformly at random from \(\mathcal{X}\). This should always be tried as a baseline.

In [BB12], they applied this technique to the problem of hyper-parameter optimization for some ML models, where the objective is performance on a validation set. In their examples, the search space is continuous, \(\Theta = [0, 1]^D\). It is easy to sample from this at random. The standard alternative approach is to quantize the space into a fixed set of values, and then to evaluate them all; this is known as grid search. (Of course, this is only feasible if the number of dimensions \(D\) is small.) They found that random search outperformed grid search. The intuitive reason for this is that many