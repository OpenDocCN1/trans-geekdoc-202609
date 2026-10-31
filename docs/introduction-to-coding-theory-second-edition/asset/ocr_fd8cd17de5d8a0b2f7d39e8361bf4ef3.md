Z and ask for which subspace U this is satisfied. Let A = (a_{jj'}) ∈ GL(m,q) and U = P = (b1 : ... : bm) ∈ PG(m-1, L) a point. Let tr = tr_{L|F_q}. The condition is

tr(xb_j β^{(i+n)z}) = Σ_{j'} a_{jj'} tr(xb_{j'}, β^{i z})

for all i, all j and x ∈ L. As β^n = α, an equivalent condition is

tr(x β^{i z} (γ^z b_j - Σ_{j'} a_{jj'} b_{j'})) = 0,

which is equivalent to γ^z b_j = Σ_{j'} a_{jj'} b_{j'}; in other words, b (written as a column vector) is an Eigenvector for the Eigenvalue γ^z of A.

Here is an algorithmic view again. The constacyclic length n additive codes are direct sums of their constituents, where the constituents correspond to cyclotomic cosets in Z/unZ. Let Z be such a cyclotomic coset, z ∈ Z, |Z| = s, L = F_{q^s} and β, α, γ = β^n as usual. The irreducible subcodes are the contractions of C(z,P) where P = (b1,...,bm) ∈ L^m has to satisfy AP = γ^z P (and we write P as a column vector). This irreducible length n constacyclic code contr(C(z,P)) has dimension s. Its codewords are w(x), x ∈ L. The entry of w(x) in outer coordinate i = 0,1,...,n-1 and inner coordinate j is tr_{L|F_q}(xb_j β^{i z}). The effect of the generator g = g(I,...,I,A,(0,...,n-1)) of the cyclic group G is g(w(x)) = w(β^z x).

# 18.39 Proposition.

Let C be a q-linear q^m-ary length n code, which is invariant under g(I,...,I,A,(0,1,...,n-1)), where gcd(n,p) = 1 and A of order u = q^m - 1 represents multiplication by a primitive element γ in F_{q^m}. Then C is F_{q^m} linear.

# PROOF

It suffices to prove this for irreducible constacyclic codes contr(C(z,P)). The generic codeword w(x) has been described above. Applying matrix A in each outer coordinate i = 0,...,n-1 yields the codeword w(γ^z x), which is still in the code.

Proposition 18.39 applies in particular in the cases q = 2, m = 2, u = 3 and q = 2, m = 3, u = 7.

# 18.40 Corollary.

Each quaternary additive code which is cyclic in the monomial sense either is quaternary linear or is equivalent to cyclic in the permutation sense.

# PROOF

Use Proposition 18.13 to obtain a code which is invariant under g = (I,...,I,A,(0,...,n-1)) where A ∈ GL(2,2) and u = det(A). If u = 1 or u = 2 or when u = 3 and n not divisible by 3, then the additive code is cyclic