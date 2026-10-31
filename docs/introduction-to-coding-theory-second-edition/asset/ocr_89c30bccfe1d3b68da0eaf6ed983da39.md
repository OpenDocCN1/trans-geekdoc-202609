# 20.4 Some hyperelliptic equations

Let char(K) ≠ 2 and the function field F be defined as a quadratic extension of K(x) by an equation

y² = f(x) ∈ K[x]

where f(x) is a polynomial of degree n = 2m + 1 ≥ 3.

First of all: as deg(f) is odd, f(x) is not a square in K(x), so y² − f(x) is an irreducible equation (over K(x)) and we really have a function field F = K(x, y) of degree 2 over K(x).

Consider F as a degree 2 extension of K(x) = K(1/x) and use the basic formula

deg((x)_∞) = deg((x)_0) = ∑ v_{P_i}(x) deg(P_i) = 2.

Let Q_∞ be the place at infinity for K(x). In principle there are three possibilities where the places P of F over Q_∞ are concerned:

+   - There are two such places P₁, P₂ and v_{P_i}(x) = −1, [F_{P_i} : K] = 1.
+   - There is only one such extension place P_∞ and v_P(x) = −1, [F_P : K] = 2.
+   - There is only one such extension place P_∞ and v_P(x) = −2, F_P = K.

In our original ring-theoretic language, a place P of F over the place Q_∞ of K(x) corresponds to a valuation ring O ⊂ F with maximal ideal P such that P ∩ K(x) = Q_∞. We will not use that terminology any more and rather speak of places and functions.

Let P over Q_∞ be one of those places. The equation shows v_P(y²) = 2v_P(y) = n v_P(x). As n is odd, we must have v_P(x) = −2. This decides the case: the last of the scenarios above is what happens. We also have v_P(y) = −n. In particular, P is a rational place (F_P = K). It follows that K̃ = K is the full field of constants. Also, whenever x is defined at a place, then so is y. It follows that P is the only place where y is not defined, and (y)_∞ = nP.

Consider L(2rP). For large r we have, by Riemann-Roch, dim(2rP) = 2r + 1 − g. On the other hand, L(2rP) contains 1, x, …, x^r, y, xy, …, x^{r−m−1} y. These are 2r + 1 − m linear independent elements:

# 20.42 Lemma. Let x₁,…,xₙ be elements of a function field F and P a place such that the v_P(x_i) are all different. Then x₁,…,xₙ are linearly independent over the constant field K.

The proof of Lemma 20.42 is obvious. In the present situation we conclude 2r + 1 − g ≥ 2r + 1 − m, so g ≤ m. We have seen the following: