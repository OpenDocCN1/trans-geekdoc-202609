inner product (in its standard form) is defined on V = F^n by

(x, y) = \sum_{i=1}^{n} x_i y_i.

Here u is the image of u under the nontrivial automorphism of F | F_q, and T(u) = u + u^q, N(u) = u^{q+1} \in F_q. Clearly the Hermitian inner product is biadditive and satisfies (\lambda x, y) = \lambda (x, y), (x, \lambda y) = \lambda (x, y) for \lambda \in F. The second equality is what makes the Hermitian inner product not bilinear. It is a sesquilinear form.

Duality can be based not only on any nondegenerate bilinear form but also on nondegenerate sesquilinear forms. It should be clear by now what we see as the basic rules of duality. In particular, we can consider dual codes with respect to the Hermitian inner product. Here is a construction of quantum codes based on q^2-ary linear codes, which are self-orthogonal with respect to the Hermitian form.

# 18.51 Theorem. Let C be a linear [n,k,d]_{q^2} code containing its dual with respect to the Hermitian form. There is an F_q isomorphism from C to a pure [[n,2k - n,d]]_q quantum code Q.

PROOF Choose 0 \neq \gamma \in F = F_{q^2} such that T(\gamma) = 0 and define \Phi : F \longrightarrow F_q by \Phi(u) = T(\gamma u). The kernel of \Phi is F_q. Fix \alpha such that \Phi(\alpha) = 1. As \alpha + \alpha^q \in F_q, it follows that \Phi(\alpha) = -1.

Let 0 \neq \omega_1 \in F arbitrary and define \omega_2 by \alpha = \omega_1 \omega_2. Then \omega_1, \omega_2 form a basis of F | F_q (if \omega_2 = \lambda \omega_1 with \lambda \in F_q, then \alpha \in F_q, hence \Phi(\alpha) = 0, a contradiction). Define projections \pi_1, \pi_2 : F \longrightarrow F_q by u = \pi_1(u) \omega_1 + \pi_2(u) \omega_2. This defines an F_q isomorphism \tau : F_{q^2}^n \longrightarrow F_q^{2n}, where

\tau(x_1, \dots, x_n) = (\pi_1(x_1), \pi_2(x_1), \dots, \pi_1(x_n), \pi_2(x_n)).

Denote by ( , ) the Hermitian form on F_{q^2}^n and define a bilinear form \langle , \rangle on F_q^{2n} by \langle \tau(x), \tau(y) \rangle = \Phi(x, y). It is clear from the definition that \langle , \rangle is biadditive and bilinear. It is nondegenerate, as the Hermitian form is nondegenerate. If y = x, then (x, x) \in F_q, hence \Phi(x, x) = 0. This shows that \langle , \rangle is symplectic (compare Section 17.2). We see that Q = \tau(C) contains its dual with respect to the symplectic form, as claimed. As \tau acts coordinatewise, the weight of x \in F^n equals the weight of \tau(x) \in E^n, where E = F_q^2 is the hyperbolic plane.

Once again consider the hexacode, one of our favorite codes. Generator matrices were first given in the problems of Section 3.4. We see that this [6,3,4]_4 code is self-dual with respect to the Hermitian form while it is not self-dual with respect to the dot product. In fact, there is no [6,3,4]_4-code which is self-dual with respect to the dot product. Application of Theorem 18.51 yields a [[6,0,4]]_2 quantum code.