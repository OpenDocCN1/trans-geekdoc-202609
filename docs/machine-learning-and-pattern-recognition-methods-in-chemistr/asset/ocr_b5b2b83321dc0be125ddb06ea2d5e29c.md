# Soft constraints in curve resolution problems

![](bbox=[0.203, 0.095, 0.82, 0.503])

**Fig. 1.2** Three different ways of augmentation of a three-way array (Richards et al., 2008).

**b.** Given some initial or intermediate estimate of $\mathbf{S}^T$, find every row of $\mathbf{C}_c$ (or every column of $\mathbf{C}_c^*$) such that it minimizes $|\mathbf{a}_{c,:} - \mathbf{Sc}_{c,:}\|$$ based on the constraints imposed on that row such as $\mathbf{c}_{c,:} = \mathbf{g}_{c,:}$ , where $\mathbf{g}_{c,:}$ specifies the constraint goals for concentration profiles.

These two steps are repeated iteratively to constrain $\mathbf{S}$ and $\mathbf{C}_c$ alternatively until convergence to the desired result. Fig. 1.3 illustrates the steps of applying constraints in the multi-way P-ALS method. The least-squares problem is solved using the adaptation of the constrained weighted method (Van Benthem et al., 2002) as described before.

An example is given to illustrate the implementation of the non-negativity and equality constraints simultaneously on the spectral values of a column-wise augmented data using the multi-way P-ALS approach. At first, the unconstrained least-squares problem is solved, and the resulting coefficient vector is illustrated below.