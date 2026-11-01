
This expression can be evaluated by looping through the variables in order, multiplying CPT entries as we go. For each summation, we also need to loop over the variable’s possible values. The structure of this computation is shown as a tree in `Figure 13.10` ([Figure 13.10](#Chapter13-03.xhtml#fig13-10)). Using the numbers from `Figure 13.2` ([Figure 13.2](#Chapter13-01.xhtml#fig13-2)), we obtain `P(b | j, m) = α × 0.00059224`. The corresponding computation for `¬b` yields `α × 0.0014919`; hence,

Description

An empty node is connected to a positive node using a line labeled `P (b), 0.001`. The first positive node is connected to two other positive nodes and the paths are labeled `P (e) 0.002` and `P (not e) 0.998`. The second positive node with path `P (e) 0.002` is connected to two nodes whose paths are labeled `P (“a” given b, e) 0.95` and `P (not “a” given b, not e) 0.05`. The other positive node is connected to two nodes whose paths are labeled `P (“a” given b, not e) 0.94,` and `P (not “a” given b, not e) 0.06`. The node with path `P (“a” given b, e) 0.95` is connected to a node with path `P (j given “a”) 0.90`. This node is connected to another node with a path `P (m given “a”) 0.70`. The node with path `P (not “a” given b, e) 0.05` is connected to a node with path `P (j given not “a”) 0.05`. This node is connected to another node with path `P (m given not “a”) 0.01`. The node with path `P (“a” given b, not e) 0.94` is connected to a node with path `P (j given “a”) 0.90`. This node is connected to another node with path `P (m given “a”) 0.70`. The node with path `P (not “a” given b, not e) 0.06` is connected to a node with path `P (j given not “a”) 0.05`. This node is connected to another node with path `P (m given not “a”) 0.01`.

×![](images/Fig-177.jpg)

`Figure 13.10` The structure of the expression shown in `Equation (13.5)` ([Equation (13.5)](#Chapter13-03.xhtml#eq13-5)). The evaluation proceeds top down, multiplying values along each path and summing at the “+” nodes. Notice the repetition of the paths for `j` and `m`.

`P(B|j,m) = α ⟨0.00059224, 0.0014919⟩ ≈ ⟨0.284,0.716⟩`.

That is, the chance of a burglary, given calls from both neighbors, is about 28%.

The `ENUMERATION-ASK` algorithm in `Figure 13.11` ([Figure 13.11](#Chapter13-03.xhtml#fig13-11)) evaluates these expression trees using depth-first, left-to-right recursion. The algorithm is very similar in structure to the backtracking algorithm for solving CSPs ([Figure 5.5](#Chapter05-03.xhtml#fig5-5)) and the DPLL algorithm for satisfiability ([Figure 7.17](#Chapter07-06.xhtml#fig7-17)). Its space complexity is only linear in the number of variables: the algorithm sums over the full joint distribution without ever constructing it explicitly. Unfortunately, its time complexity for a network with `n` Boolean variables (not counting the evidence variables) is always `O(2^n)`—better than the `O(n 2^n)` for the simple approach described earlier, but still rather grim. For the insurance network in `Figure 13.9` ([Figure 13.9](#Chapter13-02.xhtml#fig13-9)), which is relatively small, exact inference using enumeration requires around `227` million arithmetic operations for a typical query on the cost variables.

×![](images/Fig-178.jpg)

`Figure 13.11` The enumeration algorithm for exact inference in Bayes nets.

If you look carefully at the tree in `Figure 13.10` ([Figure 13.10](#Chapter13-03.xhtml#fig13-10)), however, you will see that it contains repeated subexpressions. The products `P(j | a)P(m | a)` and `P(j | ¬a)P(m | ¬a)` are computed twice, once for each value of `E`. The key to efficient inference in Bayes nets is avoiding such wasted computations. The next section describes a general method for doing this.

## 13.3.2 The variable elimination algorithm

The enumeration algorithm can be improved substantially by eliminating repeated calculations of the kind illustrated in `Figure 13.10` ([Figure 13.10](#Chapter13-03.xhtml#fig13-10)). The idea is simple: do the calculation once and save the results for later use. This is a form of dynamic programming. There are several versions of this approach; we present the variable elimination algorithm, which is the simplest. Variable elimination works by evaluating expressions such as `Equation (13.5)` ([Equation (13.5)](#Chapter13-03.xhtml#eq13-5)) in right-to-left order (that is, bottom up in `Figure 13.10` ([Figure 13.10](#Chapter13-03.xhtml#fig13-10))). Intermediate results are stored, and summations over each variable are done only for those portions of the expression that depend on the variable.

<p class="sidebar">Variable elimination</p>

Let us illustrate this process for the burglary network. We evaluate the expression

`P(B | j,m) = α Σ_e Σ_a f1(B) f2(E) f3(A,B,E) f4(A) f5(A)`.

Notice that we have annotated each part of the expression with the name of the corresponding factor; each factor is a matrix indexed by the values of its argument variables. For example, the factors `f4(A)` and `f5(A)` corresponding to `P(j|a)` and `P(m|a)` depend just on `A` because `J` and `M` are fixed by the query. They are therefore two-element vectors:

<p class="sidebar">Factor</p>

`f4(A) = [P(j|a), P(j|¬a)]ᵀ = [0.90, 0.05]ᵀ` and `f5(A) = [P(m|a), P(m|¬a)]ᵀ = [0.70, 0.01]ᵀ`.

`f3(A,B,E)` will be a `2 × 2 × 2` matrix, which is hard to show on the printed page. (The “first” element is given by `P(a | b, e) = 0.95` and the “last” by `P(¬a | ¬b, ¬e) = 0.999.` ) In terms of factors, the query expression is written as

`P(B | j,m) = α f1(B) × Σ_e f2(E) × Σ_a f3(A,B,E) × f4(A) × f5(A)`.

Here the “ × ” operator is not ordinary matrix multiplication but instead the pointwise product operation, to be described shortly.

<p class="sidebar">Pointwise product</p>

The evaluation process sums out variables (right to left) from pointwise products of factors to produce new factors, eventually yielding a factor that constitutes the solution—that is, the posterior distribution over the query variable. The steps are as follows:

•First, we sum out `A` from the product of `f3`, `f4`, and `f5`. This gives us a new `2 × 2` factor `f6(B,E)` whose indices range over just `B` and `E`:

`f6(B,E) = Σ_a f3(A,B,E) × f4(A) × f5(A) = (f3(a,B,E) × f4(a) × f5(a)) + (f3(¬a,B,E) × f4(¬a) × f5(¬a)).`

Now we are left with the expression

`P(B | j,m) = α f1(B) × Σ_e f2(E) × f6(B,E)`.

•Next, we sum out `E` from the product of `f2` and `f6`:

`f7(B) = Σ_e f2(E) × f6(B,E) = f2(e) × f6(B,e) + f2(¬e) × f6(B,¬e).`

This leaves the expression

`P(B|j,m) = α f1(B) × f7(B)`
