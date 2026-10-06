
目标函数必须在以下约束条件下得到优化。第一个约束在方程 15.8 中给出，任务必须在传输到 FN 之后才能处理 [18]。

(15.8)

`ST[i j] ≥ IT[j] + TQT[j] ∀j ∈ n, i ∈ m`

方程 15.9 中的约束表明，每个任务只能由一个 FN 处理 [18]。

(15.9)

`Σ_{i=1}^{n} Σ_{j=1}^{m} X_ij = 1 ∀j ∈ n, i ∈ m`

## 15.4 改进的爬虫搜索算法

2021 年，Laith Abualigah 等人介绍了一种受自然现象启发的元启发式算法 RSA [20]。该算法模拟鳄鱼在求偶和捕猎时的行为。在该算法中，解的位置根据鳄鱼的行为更新。更新的目的是更好地搜索并找到更高质量的解，使该算法适用于复杂问题。通过函数测试和真实工程问题，验证了该算法的效果 [20]。该算法的探索能力和开发能力受到鳄鱼在自然界中的约束、捕猎和社会行为机制的启发，这些行为机制被数学模型化，用于优化操作。RSA 与大多数进化算法一样，基于种群，可以用于解决带有特定约束的优化问题。下面，我们将全面考察该算法的工作原理。

### 15.4.1 第一阶段

在第一阶段，优化过程从构建初始种群集合开始，该集合是随机生成的。初始种群是问题的可能解的集合。初始种群的一个例子在方程 15.10 中显示 [20]。

(15.10)

```
X = [ x_11  ...  x_1n
       ...        ...
       x_n1  ...  x_nn ]
```

其中 `X` 是随机生成的初始种群，依据变量在问题中可取值的下限和上限。

数学公式保持不变：

$$x_{i,j}(t + 1) = \left\{ \begin{matrix} {Best_{j}(t) \times \eta_{i,j}(t) \times \beta - R_{i,j}(t) \times rand,t < T/4} \\ {Best_{j}(t) \times x_{r_{1},j} \times \text{ES}(t) \times rand,t \leq 2^{T}/4andt > T/4} \\ \end{matrix} \right.$$

where `Bestj` is the position of the best-obtained so far solution, `rand` is a function that generates a random number in [0, 1], `t` is the index of the current iteration, and `T` is the maximum number of iterations. The hunting operator is denoted by `ηi,j` for the *j*th position in the *i*th solution; this operator is obtained from Equation 15.12. The parameter that controls the accuracy of exploration is fixed `β = 0.1`. To decrease the search region, the function `R[i],j` is defined as in Equation 15.13. In this equation `ε` is a small random number. `r[2]` is a random number in [1*N] that select a solution. The position of a selected solution, indicated by `x[r1,j]`, and *N* is the size of the initial population. Evolutionary Sense `ES(t)` is calculated using Equation 15.14, which is a probability ratio. During the iterations of the algorithm, `ES(t)` takes a random value in [−22], and `r[3]` is a random number in [−11].

(15.12)

`ηi, j` = `Bestj` × `P[i, j]`

(15.13)

$$R_{i,j}(t) = \frac{Best_{j}(t) \times x_{r_{2},j}}{Best_{j}(t) + \varepsilon},$$

(15.14)

$$ES(t) = 2 \times r_{3} \times (1 - \frac{1}{T}).$$

In Equation 15.12, `P[i][,j]` is the difference between the position of the best-obtained solution and the current solution and is calculated using Equation 15.15.

(15.15)

$$P_{i,j} = \alpha + \frac{x_{i,j} - M(x_{i})}{Best_{j}(t) \times (\text{UB}_{j} - \text{LB}_{j}) + \varepsilon},$$

where `M(x[i])` is the average of solution *x[i]* and is calculated in Equation 15.16. `UB(j)` is the upper bound and `LB(j)` is the lower bound of variables in a solution. Fixed parameter `α = 0.1` is a parameter that controls the difference between solutions for the hunting cooperation over the iterations.

(15.16)

$$M(x_{i}) = \frac{1}{n}\sum\limits_{j = 1}^{n}x_{i,j}.$$

### 15.4.3 Phase 3 (Exploitation)

In this section, the efficiency of the algorithm is described using the behavior of crocodiles in hunting. Coordination and cooperation in hunting, which are among the hunting strategies of crocodiles, help in the exploitation search and convergence of the algorithm and getting closer to the optimal solution. These two strategies are modeled in Equation 15.17.

(15.17)

$$x_{j}(t + 1) = \left\{ {\begin{matrix} {Best_{j}(t) \times P_{i,j}(t) \times rand,t < 3T/4andt > 2T/4} \\ {Best_{j}(t) - \eta_{i,j} \times \epsilon - R_{i,j}(t) \times rand,t \leq Tandt > 3T/4} \\ \end{matrix},} \right.$$

In this equation `Bestj` is the position of the best-obtained so far solution; the hunting operator is denoted by `ηi,j` for the *j*th position in the *i*th solution; function `R[i],j` is the decrease function, which is calculated using Equation 15.13; `P[i][,j]` is difference between the position of the best-obtained solution and the current solution, which is calculated using Equation 15.15; `ε` is a small random number; and `rand` is a function that produces a random number between 0 and 1. Therefore, after several iterations, the search is done near the optimal solution and the answers converge to the optimal solution. As a result, the algorithm can find an almost optimal solution. According to the explanations mentioned in this algorithm, until less than half of the iterations are done, the exploration phase is done, and when more than half of the iterations are done, the algorithm enters the exploit phase, and the search around the optimal solution is done until the algorithm converges.

These two phases are summarized in Figures 15.2 and 15.3. In these figures, the prey is shown in white color, and in the initial iterations (less than ^(*T*)/2), the reptiles, which are shown in different colors, search the entire problem space, and in the later iterations (more than ^(*T*)/2), the search is performed around the prey, which is the optimal solution, and then the convergence happens. The pseudo-code of the RSA is shown in Algorithm 1.

![Figure 15.2 Exploration phase before T/2 iterations.](img/fig15_2_B.jpg)

Figure 15.2 Exploration phase before T/2 iterations.

![Figure 15.3 Exploitation phase after T/2 iterations.](img/fig15_3_B.jpg)

Figure 15.3 Exploitation phase after T/2 iterations.

### Algorithm 1 Pseudo-code of the Reptile Search Algorithm (RSA)

```
1.  Initialization phase
2.  Initialize RSA parameters.
3.  Initialize the solutions’ positions randomly. X : i = 1,...N.
4.  while (t < T) do
5.  Calculate the fitness function for the candidate solutions (X).
6.  Find the best solution so far.
7.  Update the ES using Equation 15.14.
8.  The beginning of the RSA
9.  for (i = 1 to N) do
10.  for (j = 1 to n) do
11.  Update the η, R, P, and values using Equation 15.12, Equation 15.13, and Equation 15.15 respectively.
12.  if (t ≤ T/4) then
13.  x(i,j) = Best[j](t) × (−ηi,j) × β − R[i],j× rand. {High walking}
14.  else if t ≤ 2T/4 and t > T/4 then
15.  x(i,j) = Best[j](t) × x[r1,j] × ES(t)× rand. {Belly walking}
16.  else if t ≤ 3T/4 and t > 2T/4 then
17.  x(i,j) = Best[j](t) × P[i],j× rand {Hunting cooperation}
18.  else
19.  x(i,j) = Best[j](t) − ηi,j × ε − R[i],j× rand. {Hunting cooperation}
20.  end if
21.  end for
22.  end for
23.  t = t + 1
24.  end while
25.  Return the best solution (Best(X)).
```

In the pseudo-code of the algorithm shown in Figure 15.4, it is clear that this algorithm, like most evolutionary algorithms, starts working with an initial population of candidate solutions. Then, during the iterations of the algorithm, they are guessed with the defined mechanisms to search for optimal solutions, and then they converge to the optimal solution in the last iterations of the algorithm.

![Figure 15.4  Total delay vs data size.](img/fig15_4_B.jpg)

Figure 15.4  Total delay vs data size.

### 15.4.4 Phase 4 (Scaling)

To strengthen the capabilities of exploration and exploitation, which is one of the most important capabilities of evolutionary algorithms, we suggest the linear scaling method. In contrast to the advantages mentioned for the algorithm and its good capability in searching the problem space and finding the optimal solution, there are also disadvantages. Among them, we can mention early convergence and getting stuck in local optima, especially in complex problems with more constraints. To solve these disadvantages in this research, we used the idea of linear scaling. Linear scaling is one of the scaling methods that is known for its simple implementation and robust performance.
