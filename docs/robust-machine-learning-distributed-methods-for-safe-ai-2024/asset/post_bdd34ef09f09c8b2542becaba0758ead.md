
## Contents

- 1 Context and Motivation ... 1
  - 1.1 Brief History of Artificial Intelligence ... 1
    - 1.1.1 Can Machines Think? ... 1
    - 1.1.2 Machine Learning ... 2
    - 1.1.3 Applications of Machine Learning ... 4
  - 1.2 Robust Machine Learning ... 6
    - 1.2.1 Fragility of Machine Learning ... 6
    - 1.2.2 The Quest for Robust Machine Learning ... 7
  - 1.3 Content of the Book ... 9
    - 1.3.1 Summary ... 9
    - 1.3.2 Organization ... 10
  - 1.4 Chapter Notes ... 11
  - References ... 12
- 2 Basics of Machine Learning ... 15
  - 2.1 Supervised Classification ... 15
    - 2.1.1 Problem Statement ... 16
    - 2.1.2 Hypothesis Classes and Loss Functions ... 18
  - 2.2 Standard Optimization Algorithms ... 21
    - 2.2.1 Gradient-Descent Methods ... 23
    - 2.2.2 Convergence Rates ... 25
    - 2.2.3 Training Error and Gradient Complexity ... 29
  - 2.3 Chapter Notes ... 30
  - References ... 30
- 3 Federated Machine Learning ... 33
  - 3.1 Machine Learning as a Distributed Problem ... 33
    - 3.1.1 Problem Statement ... 34
    - 3.1.2 Distributed Gradient-Descent Methods ... 36
  - 3.2 Convergence of Distributed Mini-batch Gradient Descent (DMGD) ... 37
    - 3.2.1 Assumptions and Notation ... 38
    - 3.2.2 Non-convex Loss Functions ... 38
    - 3.2.3 Strongly Convex Loss Functions ... 43
    - 3.2.4 Analyzing Gradient and Stochastic Gradient Descents ... 47
  - 3.3 Chapter Notes ... 51
  - References ... 52
- **4 Fundamentals of Robust Machine Learning** ... 55
  - 4.1 Getting Started with Robustness ... 55
    - 4.1.1 Fragility of Distributed Gradient Descent ... 56
    - 4.1.2 Robustifying Distributed Gradient Descent ... 57
    - 4.1.3 Robust Aggregation ... 59
  - 4.2 Measuring Robustness ... 63
    - 4.2.1 Definition of Resilience ... 64
    - 4.2.2 Breakdown Point ... 65
  - 4.3 Robust Averaging: A Primitive for Robust Aggregation ... 66
    - 4.3.1 Consistency with Majority ... 67
    - 4.3.2 Robustness Coefficients ... 68
  - 4.4 Resilience of Robust DMGD ... 70
    - 4.4.1 Deviation from Traditional DMGD ... 70
    - 4.4.2 Case of Non-convex Loss Function ... 75
    - 4.4.3 Case of Strongly Convex Loss Function ... 82
  - 4.5 Chapter Notes ... 87
  - References ... 90
- **5 Optimal Robustness** ... 93
  - 5.1 Pre-aggregation by Nearest-Neighbor Mixing ... 94
    - 5.1.1 Description of Nearest-Neighbor Mixing ... 94
    - 5.1.2 Robustness Amplification ... 95
  - 5.2 Pre-aggregation by Bucketing ... 101
    - 5.2.1 Description of Bucketing ... 101
    - 5.2.2 Robustness Amplification for Bucketing ... 103
  - 5.3 Order-Optimal Training Error ... 106
    - 5.3.1 Upper Bound on the Training Error ... 106
    - 5.3.2 Lower Bound on the Training Error ... 107
  - 5.4 Chapter Notes ... 110
  - References ... 112
- **6 Practical Robustness** ... 113
  - 6.1 Robust DMGD with Local Momentum ... 113
    - 6.1.1 Robust Aggregation Error ... 115
    - 6.1.2 Deviation Between Momentums and Gradients ... 123
  - 6.2 Resilience of Robust Distributed Mini-Batch Heavy Ball ... 126
    - 6.2.1 Loss Function Growth Under Distributed Momentum ... 127
    - 6.2.2 Case of Non-convex Loss Function ... 129
    - 6.2.3 Case of Strongly Convex Loss Function ... 139
  - 6.3 Chapter Notes ... 152
  - References ... 153
- **A General Lemmas** ... 155
  - A.1 Lipschitz Smoothness Inequality ... 155
  - A.2 Polyak–Łojasiewicz Inequality Under Lipschitz Smoothness ... 156
- **B General Exponential Convergence** ... 157
- **C Derivation of Robust Coefficients** ... 161
  - C.1 Limitation on Robust Averaging ... 161
  - C.2 Coordinate-Wise Trimmed Mean ... 162
  - C.3 Krum ... 165
  - C.4 Geometric Median ... 168
  - C.5 Coordinate-Wise Median ... 169
  - References ... 170

## Acronyms

Although we try to minimize the use of acronyms for the sake of readability, the following acronyms are often used in the text.

| Acronym | Full Form |
| --- | --- |
| AI | Artificial Intelligence |
| CWMed | Coordinate-Wise Median |
| CWTM | Coordinate-Wise Trimmed Mean |
| DMGD | Distributed Mini-batch GD |
| DMHB | Distributed Mini-batch Heavy Ball |
| DSGD | Distributed SGD |
| ERM | Empirical Risk Minimization |
| GD | Gradient Descent |
| GeoMed | Geometric Median |
| NNM | Nearest-Neighbor Mixing |
| SGD | Stochastic Gradient Descent |

## Notation

We use bold lowercase letters to denote vectors and functions with multi-dimensional outputs and standard lowercase letters to denote scalars and real-valued functions. Depending on the context, we use either a calligraphic font or uppercase letters to denote ensembles: most of the time calligraphic font, sometimes uppercase letters to denote subsets or elements of a set of sets. The cardinality of a finite set S is denoted by |S|. For a positive integer N, we denote by [N] the set {1, . . . , N}. The set of real values and d-dimensional real-valued vectors are denoted by ℝ and ℝ^d, respectively. Furthermore, we denote by ℝ^+ and ℝ_+^∗ the sets of non-negative and strictly positive real values, respectively. For a real value v ∈ ℝ, |v| denotes its absolute value, and ⌈v⌉ denotes the smallest integer greater than or equal to v. For a vector v ∈ ℝ^d, we denote its k-th coordinate (or element) by [v]_k for all k ∈ [d] and its transpose by v^T. The inner product of two vectors v1, v2 ∈ ℝ^d is denoted by ⟨v1, v2⟩ := v1^T v2. The Euclidean norm of a vector v ∈ ℝ^d is denoted by ‖v‖ := √⟨v, v⟩.

For a (differentiable) real-valued function L : ℝ^d → ℝ, its gradient at any point θ ∈ ℝ^d is denoted by ∇L(θ). Whenever necessary, we write ∇_θ to specify that the gradient is with respect to the argument θ. For a function φ : ℝ^+ → ℝ^+, we use O_a(·) to denote the Bachmann–Landau notation for describing the infinite behavior of φ. Specifically, we write φ(a) ∈ O_a(ψ(a)) if lim_{a→∞} φ(a)/ψ(a) < ∞. We extend O_a(·) to O_{a1,a2}(·) for describing the asymptotic behavior when both a1 and a2 approach infinity. Lastly, we use the notation O_∗(·) and Ω_∗(·) to describe behavior of φ up to a multiplicative constant. Specifically, we write φ(a) ∈ O_∗(ψ(a)) if there exists a constant c ∈ ℝ^+ such that φ(a) ≤ c ψ(a) for all a ∈ ℝ^+, and φ(a) ∈ Ω_∗(ψ(a)) if there exists a constant c such that φ(a) ≥ c ψ(a) for all a ∈ ℝ^+.
