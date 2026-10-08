# Applied Intelligent Decision Making in Machine Learning

```
if rand < \lambda, then
```

```
rand < c, or d = d_r (4.1)
```

```
DE mutation = (d) = hr1(d) + F.(Hr2(d) - Hr3(d)); (4.2)
```

```
BBO migration = H_j \propto u_j; (4.3)
```

```
u(d) = H_j(d); (4.4)
```

where N is the population, D is the problem dimension, c is the crossover likelihood, and F is the scaling factor.

DE/BBO can replace the original mutation by considering the hybrid migration. For the purpose of calculating the migrant rate operator, the DE/BBO differs from the original BBO. The DE/BBO can be very optimistic in comparison to DE and BBO.

# 4.2.5.2.2 Local-DE/BBO

The improvement of BBO can be made with the help of local topologies. The DE/BBO with local topologies considered a reliable predictor of hybrid BBO, which creates three categories of DE/BBO: RingDB, SquareDB, and RandDB. RingDB encompasses ring topology, whereas SquareDB and RandDB are related to square topology and random topology (Zheng et al., 2019). This triple local algorithm is more optimistic and is an improvement on DE/BBO. It is more realistic than the DE on the functional dimension.

```
DE mutation = u_i(d) = Hr2(d) + F..(Hr2(d) - Hr3(d)) (4.5)
```

# 4.2.5.2.3 Self-Adaptive DE/BBO

Self-adaptive DE/BBO is an upgraded form of DE, and the main function of this model is in dealing with multiple mutation and choosing the most suitable one. The suitable mutation is very optimistic in functional analysis. The appropriate mutation combined works with the relevant parameters. A general approach for obtaining the information from initial values is:

```
V = V + t/t_max(V_max - V_min) (4.6)
```

where t is the current, max is the maximum, and min is the minimum generation number of the algorithm.

The obtained probability of mutation and migration is estimated by:

```
P_k(G) = \frac{S_k(G)}{\sum_{k\in S} S_k(G)} (4.7)
```