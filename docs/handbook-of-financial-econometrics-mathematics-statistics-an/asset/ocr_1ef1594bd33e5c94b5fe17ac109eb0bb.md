problems related to MC² linear programming has been extensively studied (Lee et al., 1990; Shi, 1991; Shi and Yu, 1992). Key ideas of MC² linear programming, a primary theoretical foundation of this chapter, are outlined as follows.

An MC² linear programming problem can be formulated as

Max λᵗ Cx
s. t. Ax ≤ Dγ
x ≥ 0,

where C ∈ R^{qxn}, A ∈ R^{mxn}, and D ∈ R^{mxp} are matrices of qxn, mxn, and mxp dimensions, respectively, x ∈ R^{n} are decision variables, λ ∈ R^{q} is called the criteria parameter and γ ∈ R^{p} is called the constraint level parameter. Both (λ, γ) are assumed unknown.

Denote the index set of the basic variables {x_{j1}, …, x_{jm}} for the MC² problem by J = {j1, …, jm}. Note that the basic variables may contain some slack variables. Without confusion, J is also called a basis for the MC² problem. Since a basic solution J depends on parameters (λ, γ), define that (i) a basic solution J is feasible for the MC² problem if and only if there exists a γ⁰ > 0 such that J is a feasible solution for the MC² problem with respect to γ⁰; and (ii) J is potentially optimal for the MC² problem if and only if there exist a λ⁰ > 0 and a γ⁰ > 0 such that J is an optimal solution for the MC² problem with respect to (λ⁰, γ⁰). For an MC² problem, there may exist a number of potentially optimal solutions {J} as parameters (λ, γ) vary depending on decision situations.

Seiford and Yu (1979) derived a simplex method to systematically locate the set of all potentially optimal solutions {J}. The computer software of the simplex method (called MC² software) was developed by Hao and Shi (1996). This software consists of five subroutines in each iteration: (i) pivoting, (ii) determining primal potential bases, (iii) determining dual potential bases, (iv) determining the effective constraints for the primal weight set and (v) determining the effective constraints for the dual weight set (Yu, 1985, Chapter 8). It is written in PASCAL and operates in a man–machine interactive fashion. The user cannot only view the tableau of each iteration but also trace the past iterations. In the following section, the framework of the MC² problem, as well as its software, will be used to formulate and solve using the fuzzy set approach for international transfer pricing problems.

# 54.3.2 Multiple factor transfer pricing model

The review of existing transfer pricing models shows that two major shortcomings, from a management point of view, need to be overcome in the