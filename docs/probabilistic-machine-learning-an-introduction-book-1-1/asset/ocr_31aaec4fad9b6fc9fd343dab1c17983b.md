so as to minimize time and intermediate memory allocation.³ The library is best illustrated by the examples in einsum_demo.py.

Note that the speed of einsum depends on the order in which the operations are performed, which depends on the shapes of the relevant arguments. The optimal ordering minimizes the treewidth of the resulting computation graph, as explained in [GASG18]. In general, the time to compute the optimal ordering is exponential in the number of arguments, so it is common to use a greedy approximation. However, if we expect to repeat the same calculation many times, using tensors of the same shape but potentially different content, we can compute the optimal ordering once and reuse it multiple times.

# C.3 Matrix inversion

In this section, we discuss how to invert different kinds of matrices.

# C.3.1 The inverse of a square matrix

The inverse of a square matrix **A** ∈ ℝ^{n×n} is denoted **A**^{-1}, and is the unique matrix such that

**A**^{-1} **A** = **I** = **A** **A**^{-1}. (C.101)

Note that **A**^{-1} exists if and only if det(**A**) ≠ 0. If det(**A**) = 0, it is called a **singular** matrix.

The following are properties of the inverse; all assume that **A**, **B** ∈ ℝ^{n×n} are non-singular:

(**A**^{-1})^{-1} = **A** (C.102)
(**A** **B**)^{-1} = **B**^{-1} **A**^{-1} (C.103)
(**A**^{-1})^{⊤} = (**A**^{⊤})^{-1} ≜ **A**^{-T} (C.104)

For the case of a 2 × 2 matrix, the expression for **A**^{-1} is simple enough to give explicitly. We have

**A** = [[a, b],[c, d]], **A**^{-1} = 1/|**A**| [[d, -b],[-c, a]] (C.105)

For a block diagonal matrix, the inverse is obtained by simply inverting each block separately, e.g.,

[[**A**, 0],[0, **B**]]^{-1} = [[**A**^{-1}, 0],[0, **B**^{-1}]] (C.106)

# C.3.2 Schur complements

In this section, we review some useful results concerning block structured matrices.

Theorem C.3.1 (Inverse of a partitioned matrix). Consider a general partitioned matrix

**M** = [[**E**, **F**],[**G**, **H**]] (C.107)