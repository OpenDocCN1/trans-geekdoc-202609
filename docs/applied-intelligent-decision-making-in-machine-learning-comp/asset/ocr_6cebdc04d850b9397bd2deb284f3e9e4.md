# 7.4.2 THE ADVANTAGE OF SFLA

SFLA is a very simple algorithmic structure because it has less controlling parameters, but it suffers from limitations: the population searching decreases; the worst solution is updated instead of the best; and the convergence speed of the algorithm is very slow. To avoid the limitations of basic SFLA by improving frog mapping size the search learning coefficient (S) is used to change the movement of the frog during a local search. The rule of leaping the frog is:

```
$x_w (new) = x_w + stp$
```

```
$stp = \varphi * stp^{-1} + S * rand()*(x_w - x_w) - Stp_{max} \leq stp \leq Stp_{max}$
```

$stp$ represents step $t$ at instance of the frog step's previous position iteration, $\varphi$ represents the inertia required to balance the search process. The value $\varphi$ decreases repeatedly from greater to smaller.

Binary shuffled-frog leaping encoding (0/1) is used for the presence and absence of the frog respectively. Each frog has two basic components such as velocity and position. The position of the frog gets updated with respect to its position and the position of the other frogs. The updated frog position is changed into a continuous value, and frogs are sorted into their fitness value. Accordingly, the whole population is divided into memplexes and the updating of the frog in the inter-cluster occurs throughout the population.

# 7.4.3 ALGORITHM FOR BSFLA-PSO

For this algorithm, we considered the parameters of population size (25), the number of memplexes (5), intra-updates of memplexes (8), and the number of improvisations (100).

+   Step-1: Selection of gene expression dataset. Using Min-Max normalization normalizes the dataset. Selection of best 250 genes.
Step-2: Initialization of variables such as number of memplexes (m); number of populations (n), improvisation with inter-cluster memplexes (nim), number of improvisations (Ni).
Step-3: Randomly generated NP frogs as the initial population. Consider the either (0/1). Initialization iteration as 0.
Step-4: Using KNN classifier, calculate fitness $F_p$. The frog with the highest fitness is in the first memplex, and so on.
Step-5: Set $i = 1$ and start each memplex.
Step-5.1: Set $j = 1$ and start each memplex. Find the best and worst fitness of the whole population represented as $F_{go}$ and $F_{gw}$
Step-5.2: Comparisons of fitness value between new and current. If new is greater than current then go to 8 or identify the position of the worst frog.