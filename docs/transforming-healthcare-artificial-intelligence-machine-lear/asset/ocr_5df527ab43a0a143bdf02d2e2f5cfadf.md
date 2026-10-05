# Melanoma detection by hybrid attention DCNN-BiLSTM architecture 387

where BestS, GBest, and CBest all refer to the optimal, global, and current solutions, respectively, at the time $t$; fitness stands for the fitness function used to resolve the situation and $v$ denotes the frequency of the white shark’s wavy movements, which may be estimated using equation (18.39).

```
$p = \text{sgn}(d_g^x - \text{up } b) > 0 \quad (18.36)$
```

```
$q = \text{sgn}(d_g^x - \text{low } b) < 0 \quad (18.37)$
```

```
$d_0 = \oplus(p,q) \quad (18.38)$
```

```
$v = v_{min} + \frac{v_{max} - v_{min}}{v_{max} + v_{min}} \quad (18.39)$
```

where $p$ and $q$ represent binary vectors determined by equations (18.36) and (18.37), and $d_0$ is a logical vector derived using equation (18.38). The white shark’s sweeping movements oscillate in frequency $v_{min}v_{max}$ and the movement force is indicated by the parameter $n$, which is raised using the following iterative procedure:

```
$n = \frac{1}{p_0 + e^{\frac{0.5G-1}{p_1}}} \quad (18.40)$
```

where $p_0$ and $p_1$ are two parameters that control the exploitation and exploration behaviours. The phase $n$ aids in quickening the pace of the search and enhances the WSO’s exploration and exploitation behaviours. The following movement may be used to relax the best white shark convergent to the target:

```
$\hat{d}_{g+1} = dk_{best} + \eta_H \hat{W}_d \times \text{sgn}(r_2-0.5)ifr_3 < L \quad (18.41)$
```

where $\hat{d}_{g+1}$ denotes the gth white shark’s updated location with respect to its target; $	ext{sgn}(r_2-0.5)$ controls the search direction by returning either 1 or -1; $n_2$, $r_3$, and $\hat{W}_d$ are the separation between the white shark and its target, as given below:

```
$\hat{W}_d = |\text{rand} \times (dk_{best} - d_g^x)| \quad (18.42)$
```

While a great shark is very pursuing its prey, its sight and smell senses are at their peak, which is indicated by the parameter $L$ in equation (18.41). It can be expressed as:

```
$L = |1 - e^{\frac{-p_2G}{G}}| \quad (18.43)$
```