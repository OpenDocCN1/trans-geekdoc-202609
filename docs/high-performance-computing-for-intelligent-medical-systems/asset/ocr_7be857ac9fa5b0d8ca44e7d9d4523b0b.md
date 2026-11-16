# 8.9.2 Inter-block/inter-frame fuzzy search algorithm

The Inter-Block/Inter-Frame Fuzzy Search (IIFS) was proposed by Roan et al [35]. It uses the inter-block and inter-frame fuzzy prediction to determine the motion vectors of image blocks efficiently. It beats the common and famous BMAs like FS, TSS, DS, SES, 4 s, 2DLS, and a few others in terms of the following measures: (1) Avg. of prediction error for absolute prediction per pixel, (2) Avg. block distortion measure (e.g., MAD), (3) Avg. PSNR value, (4) Avg. Euclidean distance between actual MV and predicted MV, (5) Avg. probability to select the actual MV, (6) computational cost, and (7) bit requirement for the encoding of MV.

# 8.9.3 Basic block-matching using particle swarm optimization

Kennedy and Eberhart [43] proposed PSO which is inspired by nature and optimizing in nature. This algorithm became popular due to its optimizing ability and speed of convergence. This PSO algorithm is also used in the field of video compression to optimize the ME process. This algorithm is easier to use in practice than GA as it doesn’t use mutation and cross-over to regenerate the off spring. Moreover, PSO is based on the nature of bird flocking and doesn’t have a gradient, and is self-adaptive. Du et al [44] had used PSO for the first time to optimize the ME which overcomes the problem of local optima.

A solution in a search window or solution space in PSO is denoted by a particle that searches through the solution space for the best match location by adjusting the velocity dynamically. The particle position in a solution space which represents the position of a particle with the highest fitness value becomes the best matching location and it gives the required MV. Using the experience of a flying swarm and its knowledge, a particle updates the velocity. In a D-dimensional space, particles are represented as volume less point. Xp(best) represents the personal best coordinates location having the highest fitness value, whereas Xg(best) denotes the best location within the population.

+   $Si = (Si_1, Si_2, ..., Si_d)$ denotes ‘i’th particle in PSO and
+   $Pi = (Pi_1, Pi_2, ..., Pi_d)$ represents the Xp(best) position of that particle.

Each particle updates its velocity vector ‘V’ and position vector ‘X’ according to equations (8.1) and (8.2).

```
$VId(t + 1) = w * Vid(t) + C1 \times rand1( . ) \times (Pid - Xid)
+ C2 \times rand2( . ) \times (Pid - Xid)$ (8.1)
```

```
$Xid(t + 1) = Xid(t) + Vid(t + 1), 1 \leqslant i \leqslant N, 1 \leqslant d \leqslant D$ (8.2)
```

$N = \text{No. of Particles}, D = \text{Dimensionality}
Vi = (Vi_1, Vi_2, ..., Vi_d), Vid \in [-Vmax, Vmax]: 'ith' particle’s velocity vector
Xi = (Xi1, Xi2, ..., Xid), Xid \in [-Xmax, Xmax]: 'ith' particle’s position vector,
w = inertia weight, C1 and C2 are constants known as acceleration constants and taken as 2.0; $r_1$ and $r_2$ are random numbers between [0,1], Pg and Pi are global best and local best. The steps of PSO based BMA [45-54] are briefed below.