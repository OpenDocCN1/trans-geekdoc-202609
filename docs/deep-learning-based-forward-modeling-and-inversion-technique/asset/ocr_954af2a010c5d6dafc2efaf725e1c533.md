# 116 Deep Learning-Based Forward Modeling and Inversion Techniques

# 4.2.2.1 Genetic Algorithm

Genetic algorithm (GA) is a computing model of biological evolution process which simulates the natural selection and evolution mechanism of Darwin's biological theory. GA is an efficient, parallel and global search method, which can automatically acquire and accumulate knowledge about the search space during the iteration process. Generally speaking, the genetic algorithm with three rules at each iteration to yield the next generation from the current one:

+   - Selection rules randomly select examples from the current generation (called parents).

+   - Crossover rules randomly integrate two parents to create children for the next generation.

+   - Mutation rules randomly apply to some parents when generating children.

During each generation, the fitness of the population is calculated to ensure the evolving direction. After several iterations, GA has a certain probability to reach the global optimum. The genetic algorithm is not constrained to specific fields, hence has strong robustness in many applications.

# 4.2.2.2 Particle Swarm Optimization

In 1995, inspired by the regularity of birds'7 foraging behavior, James Kennedy and Russell Eberhart established a simplified algorithm which finally formed the particle swarm optimization (PSO) after years of improvement. The particle swarm optimization algorithm has the advantages of fast convergence, few parameters, and easy implementation (for high-dimensional optimization problems, the particle swarm optimization converges to the optimal solution faster than the genetic algorithm)

In particle swarm optimization, the particles travels in the whole space of the optimization problem. The spatial position of each particle indicates a candidate solution to the unknown optimization problem. By changing the velocity according to certain rules, each searches for better positions in the solving domain. The PSO algorithm begins by creating random positions for the particles, within an initialization domain $V' \subset V$, where the velocities/positions of the particles are initialized within $V'$. During the iterations of the algorithm, the velocities are updated until a condition is satisfied.

```
$v_i^{t+1} = w v_i^t + \varphi_1 \tilde{U}_1^t (\vec{p}_i^t - x_i^t) + \varphi_2 \tilde{U}_2^t (\vec{l}_i^t - x_i^t) \quad (4.16)$
```

```
$x_i^{t+1} = x_i^t + v_i^{t+1} \quad (4.17)$
```