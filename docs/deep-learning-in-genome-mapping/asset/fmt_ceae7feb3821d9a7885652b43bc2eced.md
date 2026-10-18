
## 5. Experimental Setup and Results

The experiments utilized an Intel Core i7-11700 processor, 16 GB of RAM, and Windows 10, implemented in `Python 3.11`. The `MOWEA` algorithm was tested on real-world genomic datasets to evaluate mapping prediction, fitness function, loss of function, and error rate.

### 5.1 Experimental Setup

The algorithm was initialized with a population size of `N = 150` and a maximum of `T [max] = 600` iterations. Coefficient vectors `A ∈ [−1, 1]` and `B ∈ [0, 2]` were dynamically adjusted to balance exploration and exploitation. A mutation rate of `µ = 0.1` and a crossover rate `ρ = 0.9` enhanced solution diversity. The algorithm was tested against `NSGA-II`, `MOPSO`, and `MODE` in 15 independent runs for comparison.

$$\\begin{array}{l} {A = \\frac{TP}{TP + FN}} \\\\ {R\_{c} = \\frac{1}{T\_{\\text{final~}}}{\\sum\\limits\_{t = 1}^{T\_{\\text{final~}}}F}\\left( X\_{\\text{best~}}^{t} \\right)} \\\\ \\end{array}$$  

### 5.2 Datasets

To validate the `MOWEA` framework, various publicly accessible genomic datasets were used, covering gene expression analysis and genome-wide association studies (`GWAS`). Each dataset represents a distinct domain within genomic research.

*   The complete genome (`HG`) sequence from the NCBI Genome Database offers chromosome-specific data, serving as a benchmark for genome mapping algorithm performance.

*   The `Arabidopsis` (`Arabi`) reference dataset is widely used for plant genome research and gene function analysis.

*   The `GWAS` dataset identifies associations between genetic variants and phenotypic traits, serving as a benchmark for evaluating the algorithm’s accuracy in mapping complex traits.

The proposed `MOWEA` algorithm was compared against `NSGA-II` ([Bohrer and Dorn 2024](#ch2.xhtml#ref2_3)), `MOPSO` ([Rafie and Moradi 2024](#ch2.xhtml#ref2_17)), and `MODE` ([Yu et al. 2024](#ch2.xhtml#ref2_22)). Each algorithm was executed 15 times per dataset to ensure statistical robustness, with results averaged over independent runs. The next section presents detailed experimental comparisons between `MOWEA` and baseline algorithms.

![Figure 1: HG dataset accuracy comparison for various algorithms over 600 generations.](images/fig2_1_B.jpg)

Figure 1: HG dataset accuracy comparison for various algorithms over 600 generations.

---

## MOWEA Algorithm for Genome Mapping Prediction

The `MOWEA 2` algorithm integrates exploration and exploitation strategies to optimize multi-objective genome mapping. It simultaneously refines gene sequence predictions while balancing competing objectives. The process begins with a randomly initialized whale population `X [i] 0` for `i = 1*, . . . , N` within the search space. During each iteration `t` (up to `T [max]`), whales evaluate their fitness `F [j] (X [i] )` across multiple objectives `j`, ensuring solution quality. Genome mapping accuracy `A(X [i] )` is computed using predefined criteria[Table 1](#ch2.xhtml#tab2_1) and `MOWEA` Algorithm 2.

Table 1: Terminologies, notations, and descriptions used in `MOWEA`.

| Notation | Terminology | Description |
| :--- | :--- | :--- |
| `X[i]t` | Position of whale | Position of whale `i` at iteration `t` in the search space. |
| `N` | Population size | Number of whales in the population. |
| `Tmax` | Maximum iterations | Maximum number of iterations allowed for the algorithm. |
| `F[j](X[i])` | Fitness function | Objective value `j` for whale `i` used to assess solutions. |
| `M` | Number of objectives | Total number of objectives to be optimized (multi-objective). |
| `A(X[i])` | Genome mapping accuracy | Accuracy of genome mapping for solution `X[i]` using true positives (`TP`) and false negatives (`FN`). |
| `TP` | True positives | Number of correctly predicted gene sequences. |
| `FN` | False negatives | Number of missed gene sequences in prediction. |
| `X[best]` | Best solution | Best solution based on Pareto dominance at the current iteration. |
| `a` | Control parameter | Linearly decreasing parameter that balances exploration and exploitation. |
| `r[1], r[2]` | Random numbers | Random values in the range `[0,1]`. |
| `A` | Encircling coefficient | Encircling behavior control, updated using `a` and `r[1]`. |
| `C` | Attraction coefficient | Controls attraction between whales, updated using `r[2]`. |
| `P(X[i])` | Genome mapping prediction | Prediction result for whale `i` after optimization. |
| `f(X[i])` | Prediction function | Function mapping input features to predicted gene sequences. |
| `ε[i]` | Error term | Small error added to the prediction to account for uncertainty. |
| `∆F` | Fitness change | Change in fitness value used as a termination criterion. |
| `ε` | Convergence threshold | Small positive value used to determine algorithm convergence. |

### Algorithm 2: MOWEA Algorithm for Genome Mapping Prediction

1. Initialize population `X[i]⁰` for `i = 1, …, N` with random positions in the search space
2. **for** each iteration `t = 1` to `T [max]` **do**
3. **for** each whale `i` **do**
4. Evaluate fitness `F[j] (X[i] )` for all objectives `j` where `j ∈ [1*, M*]`
5. Compute genome mapping accuracy `A(X[i] )` using:

   $$A\\left( X\_{i} \\right) = \\frac{TP}{TP + FN}$$  

   where `TP` is the number of true positives and `FN` is the number of false negatives.
6. **end for**
7. Identify `X[best]` as the best solution based on Pareto dominance
8. **for** each whale `i` **do**
9. Update `A` using:

   `A = 2*a ⋅ r[1] − a`  

10. Update `C` using:

    `C = 2 ⋅ r[2]`  

11. Update position `X[i]^(t+1)` using:

    `X[i]^(t+1) = X[best] − A ⋅ |C⋅X[best] − X[i]^(t)|`  

12. Update genome mapping prediction `P(X[i])` using:

    `P(X[i]) = f(X[i]) + ε[i]`  

    where `f(X[i])` is the function mapping the input features to the predicted gene sequences, and `ε[i]` is a small error term.
13. **end for**
14. **if** termination criteria met, i.e., `∆F < ε` or maximum iterations reached **then**
15. **break**
16. **end if**
17. **end for**
18. **return** Pareto front of optimal solutions and predicted gene sequences

$$A\\left( X\_{i} \\right) = \\frac{TP}{TP + FN}$$  

where `TP` represents the true positives, and `FN` denotes the false negatives. After assessing fitness, the algorithm identifies the best-performing solution `X [best]` based on Pareto dominance criteria. Subsequently, for each whale `i`, the algorithm updates the position using exploration and exploitation strategies, represented mathematically as:

$$A\\left( X\_{i} \\right) = \\frac{TP}{TP + FN}$$  

where `A` and `B` are coefficient vectors controlling the balance between exploration and exploitation. The exploration and exploitation functions are defined based on the distance to the best solution `X [best]`, enabling whales to effectively search for optimal gene sequences in the mapping process. The algorithm continues to iterate until a predefined termination condition is met, such as achieving a satisfactory convergence or reaching `T [max]`. Finally, the algorithm returns the Pareto front of optimal solutions, representing the best trade-offs among the multiple objectives in genome mapping.
