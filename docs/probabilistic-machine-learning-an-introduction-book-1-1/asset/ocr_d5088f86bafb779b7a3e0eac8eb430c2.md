# 13.6.2.3 Hierarchical MOEs

If each expert is itself an MoE model, the resulting model is called a **hierarchical mixture of experts** [JJ94]. See Fig. 13.27 for an illustration of such a model with a two level hierarchy.

An HME with $L$ levels can be thought of as a “soft” decision tree of depth $L$, where each example is passed through every branch of the tree, and the final prediction is a weighted average. (We discuss decision trees in Sec. 18.1.)

# 13.7 Exercises

**Exercise 13.1** [Backpropagation for a 1 layer MLP]

(Source: Kevin Clark.)

Consider the following classification MLP with one hidden layer:

**x** = input  (13.114)
**z** = **W**x + **b**₁  (13.115)
**h** = ReLU(**z**)  (13.116)
**a** = **U**h + **b**₂  (13.117)
**p** = S(**a**)  (13.118)
ℒ = CrossEntropy(**y**, **p**)  (13.119)

where **x** ∈ ℝ^{D×1}, **b**₁ ∈ ℝ^{K×1}, **W** ∈ ℝ^{K×D}, **b**₂ ∈ ℝ^{C×1}, **U** ∈ ℝ^{C×K}, where $D$ is the size of the input, $K$ is the number of hidden units, and $C$ is the number of classes. Show that the gradients for the parameters and input are as follows:

∂ℒ/∂**U** = δ₁**h**ᵀ  (13.120)
∂ℒ/∂**b**₂ = δ₁  (13.121)
∂ℒ/∂**W** = δ₂**x**ᵀ  (13.122)
∂ℒ/∂**b**₁ = δ₂  (13.123)
∂ℒ/∂**x** = δ₂**W**  (13.124)

where the gradient of the loss wrt the two layers (hidden and logit) are given by the following:
δ₁ = ∂ℒ/∂**a** = (**p** − **y**)ᵀ  (13.125)
δ₂ = ∂ℒ/∂**z** = δ₁ **U** ⊙ H(**h**)  (13.126)