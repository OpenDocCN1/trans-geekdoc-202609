
Optimization algorithms have significantly advanced healthcare applications. [Pradhan et al. (2023](#ch2.xhtml#ref2_16)) developed a self-adaptive sea lion optimization (SA-SLnO) algorithm for lung cancer detection using deep learning. [Joshi and Aziz (2024](#ch2.xhtml#ref2_9)) proposed a metaheuristic optimization framework integrating gene expression data for brain tumor classification. Reinforcement learning has emerged as a powerful tool for optimization. [Hu and Yu (2023](#ch2.xhtml#ref2_8)) introduced a reinforcement learning-based grey wolf optimizer for feature selection, while [Wang et al. (2023](#ch2.xhtml#ref2_21)) applied reinforcement learning-based particle swarm optimization to complex multi-objective problems. Genetic algorithms (GA) have been effectively used for hyperparameter optimization in deep learning models. [Lee et al. (2021](#ch2.xhtml#ref2_14)) combined GA with deep neural networks to enhance performance. [Emam et al. (2024](#ch2.xhtml#ref2_4)) developed a hybrid optimization framework for cancer diagnosis, utilizing genetic operators for tumor identification. Swarm intelligence has contributed new strategies for feature selection and optimization. [Mandle et al. (2024](#ch2.xhtml#ref2_15)) proposed the Whale Social Spider Optimization algorithm (WSSOA) for brain tumor classification. [Gülmez (2023](#ch2.xhtml#ref2_5)) integrated Grey Wolf Optimization (GWO) with deep learning for cotton disease detection. Several studies have explored optimization algorithms integrated with machine learning to solve complex problems. [Karim et al. (2021](#ch2.xhtml#ref2_11)) highlighted deep learning-based clustering methods for bioinformatics, while [Bai et al. (2023](#ch2.xhtml#ref2_2)) reviewed machine learning and optimization techniques applied to genome-scale metabolic networks.

The literature underscores the growing influence of intelligent optimization algorithms, GNNs, and hybrid deep learning models in bioinformatics, healthcare, and engineering. This chapter introduces a deep learning-based optimization algorithm tailored for genome mapping, integrating neural networks with evolutionary strategies to reduce computational complexity while ensuring high mapping accuracy.

## 3. Proposed Framework for Genome Mapping-based Prediction

The proposed genome mapping framework integrates multi-objective evolutionary algorithms with genomic techniques to improve accuracy and computational efficiency. It consists of key components designed to optimize mapping precision while minimizing processing time.

### 3.1 Data Preprocessing

Genomic data undergoes preprocessing to remove noise and irrelevant features. Let `D` represent genomic sequences and `F` denote extracted features. The transformation is mathematically expressed as:

(1)

`F′ = P(D)`

where `P` is the preprocessing function that refines raw genomic data into a structured feature set `F′`.

### 3.2 Multi-objective Optimization Model

The optimization model aims to maximize the accuracy `A` of the mapping and minimize the computational time `T`. The multi-objective function can be expressed as:

(2)

```
Minimize F(x) = [ f₁(x) ] = [ -A(x) ]
                [ f₂(x) ]   [  T(x) ]
```

where `x` is the decision variable representing the parameters of the mapping algorithm. The objectives `f[1]` and `f[2]` are to be minimized concurrently, resulting in a Pareto optimal solution.

### 3.3 Proposed Fitness Function

To assess genome mapping performance, the fitness function `F(x)` balances accuracy and computational efficiency:

(3)

```
F(x) = w₁ · A(x) + w₂ · ( 1 / T(x) )
```

where `w[1]` and `w[2]` are weights, `w[1] + w[2] = 1`. `A(x)` represents mapping accuracy and `T(x)` denotes computational time.

This function optimizes accuracy while minimizing processing time, for a balanced evaluation.

### 3.4 Convergence Criteria

The algorithm runs until convergence, determined by the improvement in the Pareto front:

(4)

```
Δ = || Fᵗ - Fᵗ⁻¹ || / || Fᵗ⁻¹ || < ε
```

where `Fᵗ` and `Fᵗ⁻¹` are the objective values at iterations `t` and `t` − 1 and `ε` is a predefined threshold.

### 3.5 Output

The proposed framework outputs a set of optimal gene mapping sequences:

(5)

`S* = {s[1], s[2], …, s[k]}`

where `S*` represents the optimal sequences, and `k` is the number of identified sequences. By integrating multi-objective evolutionary algorithms, the framework enhances genome mapping, balancing accuracy and computational efficiency.

## 4. Proposed Multi-objective Whale Evolutionary Algorithm (MOWEA)

The Multi-objective Whale Evolutionary Algorithm (MOWEA) draws inspiration from humpback whales’ social behavior and hunting strategies. It optimizes multi-objective problems by balancing competing objectives while ensuring computational efficiency. The algorithm follows key steps for effective implementation.

### 4.1 Algorithm Initialization

The Multi-Objective Whale Algorithm ([Sahoo et al. 2024](#ch2.xhtml#ref2_18)) begins by initializing a population of whales as solutions. Let `N` be the population size and `D` the solution space dimensionality. The initial positions are defined as:

(6)

`X[i]⁰ = rand(D), ∀i ∈ [1, N]`

where `X[i]⁰` represents the position of the `i`-th whale at iteration `t` = 0.

### 4.2 Fitness Evaluation

Each whale’s fitness is assessed using multi-objective functions:

(7)

`F[j](X[i]) = f[j](X[i]), ∀j ∈ [1, M]`

where `F[j]` is the `j`-th objective function, `M` is the total number of objectives, and `f[j](X[i])` evaluates the `j`-th objective for `i`.

### 4.3 Social Behavior

Whales in the MOWEA utilize two primary behaviors: first exploration, and second exploitation. The exploration phase involves searching for prey, while the exploitation phase involves the use of social interactions to improve solution quality. The position update for a whale can be mathematically expressed as:

(8)

`X[i]^(t+1) = X[best] − A ⋅ |C⋅X[best] − X[i]^(t)|`

where:

- `X[best]` is the position of the best whale (solution) in the current iteration,
- `A` is a coefficient that controls the exploration ability, calculated as:

(9)

`A = 2⋅a⋅r[1] − a`

- `a` decreases linearly from 2 to 0 over the course of iterations,
- `r[1]` is a random number in the range `[0, 1]`,
- `C` is a coefficient that influences the step size, calculated as:

(10)

`C = 2⋅r[2]`

where `r[2]` is another random number in the range `[0, 1]`.

### 4.4 Fitness Function and Pareto Dominance

To select the best solutions, MOWEA employs Pareto dominance. A solution `X[i]` is said to dominate `X[j]` if:

(11)

`∀k ∈ [1, M], F[k](X[i]) ≤ F[k](X[j]) ∧ ∃m ∈ [1, M] : F[m](X[i]) < F[m](X[j])`

The fitness function can be defined as:

(12)

```
F(X) = Σ(wⱼ · Fⱼ(X)) for j = 1 to M
```

where `w[j]` is the weight assigned to the `j`-th objective.

### 4.5 Termination Criteria

The algorithm iterates until a termination condition is met, which could be based on:

1. A maximum number of iterations `T[max]`.
2. A convergence threshold `ε`:

(13)

`ΔF < ε`

where `ΔF` is the improvement in fitness over iterations. The steps of the proposed MOWEA 1 can be summarized in the following pseudocode:

| Algorithm 1 Multi-objective Whale Evolutionary Algorithm (MOWEA) |
| --- |
| 1: Initialize population `X[i]⁰` for `i` = 1, . . . , `N` with random positions in the search space |
| 2: **for** each iteration `t` = 1 to `T[max]` **do** |
| 3: **for** each whale `i` **do** |
| 4: Evaluate fitness `F[j](X[i])` for all objectives `j` where `j` ∈ `[1, M]` |
| 5: **end for** |
