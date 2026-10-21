each portfolio. This result is consistent with most studies that find that the financial price series follow a random walk process.

# Appendix 100B Identification of the Simultaneous Equation System

Note that, given G is non-singular, Π = −G⁻¹H in equation (100.19) can be written as follows:

AW = 0, (100B.1)

where

A = [G H] = ( g11 g12 … g1n h11 h12 … h1n ; g21 g22 … g1n h21 h22 … h2n ; ⋮ ⋮ ⋱ ⋮ ⋮ ⋮ ⋱ ⋮ ; gn1 gn2 … gnn hn1 hn2 … hnn )

W = [Π I_n]' = ( π11 π12 … π1n 1 0 … 0 ; π21 π22 … π1n 0 1 … 0 ; ⋮ ⋮ ⋱ ⋮ ⋮ ⋮ ⋱ ⋮ ; πn1 πn2 … πnn 0 0 … 1 )

That is, A is the matrix of all structure coefficients in the model with dimension of (n × 2n), and W is a (2n × n) matrix. The first equation in (100B.1) can be expressed as

A1W = 0, (100B.2)

where A1 is the first row of A, i.e., A1 = [g11 g12 … g1n h11 h12 … h1n].

Since the elements of Π can be consistently estimated, and In is the identity matrix, equation (100B.2) contains 2n unknowns in terms of π’s. Thus, there should be n restrictions on the parameters to solve equation (100B.2) uniquely. First, one can try to impose normalization rule by setting g11 equal to 1 to reduce one restriction. As a result, there are at least n − 1 independent restrictions needed in order to solve (100B.2).

It can be illustrated that the system represented by equation (100.17) is exactly identified with three endogenous and three exogenous variables. It is entirely similar to those cases of more variables. For example, if n = 3,