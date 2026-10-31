# The automorphism group of 𝒢₁₂.

The discussion in the preceding subsection shows that there is up to monomial equivalence exactly one [12,6,6]₃ code. We can in fact determine its automorphism group. Let Aut(𝒢₁₂) be the automorphism group of the ternary Golay code 𝒢₁₂. More precisely, it is the stabilizer of 𝒢₁₂ under the monomial group of order 2¹²12!

We need some more practice with monomial operations. Each element of the monomial group will be written g = πm, where π is a permutation of {1,2,…,12} and m = m(1,2,…,12) = (m₁,m₂,…,m₁₂) ∈ {1,2}¹². For the permutation π we use the cycle notation introduced in Section 12.4. Element g acts by at first permuting the columns of G according to π and then multiplying column i by mᵢ, for all i. An element g belongs to Aut(𝒢₁₂) if it stabilizes the ternary Golay code 𝒢₁₂ = ⟨v₁,v₂,v₃,v₄,v₅,v₆⟩, in other words, if the image of vᵢ under g is contained in 𝒢₁₂, for all i = 1,…,6.

What happens if π is the identity permutation? We leave it to the reader to verify that m = (m₁,…,m₁₂) ∈ Aut(𝒢₁₂) if and only if either all mᵢ = 1 or all mᵢ = 2. Denote the latter element by −1.

The columns of the generator matrix G generate the point set 𝒬 = {Q₁,Q₂,…,Q₁₂} ⊂ PG(5,3). Each element g ∈ Aut(𝒢₁₂) induces a permutation of 𝒬. This permutation is of course π, where g = πm.

17.13 Definition. Let Aut(𝒢₁₂) be the stabilizer of the ternary Golay code 𝒢₁₂ in the monomial group. Write g = πm as above. Let

M₁₂ = {π | g = πm ∈ Aut(𝒢₁₂) for some m}

the permutation group on {1,…,12} (which we identify with the set 𝒬 of points in PG(5,3) describing the columns of the generator matrix G) determined by Aut(𝒢₁₂). This subgroup M₁₂ ⊂ S₁₂ of the symmetric group on 12 objects is known as the Mathieu group on 12 symbols.

As mentioned above, whenever g = πm ∈ Aut(𝒢₁₂), then −g = π(−m) is the only other element of Aut(𝒢₁₂) with permutation π. The orders, the number of elements of these groups, are therefore related by |Aut(𝒢₁₂)| = 2 × |M₁₂|. In practice we can concentrate on the permutation part π and adapt m by setting m₁ = 1.

We already have a lot of information about these groups. Consider subsets of six coordinates. The 132 blocks of the Witt design S(5,6,12) correspond to the 6-hyperplanes and to (6,6) submatrices of G which have rank 5 (hence determinant 0). The remaining (12 choose 6) − 132 = 12 × 11 × 6 sets of six columns correspond to regular (6,6) submatrices of G, information sets of coordinates. Examples of such information sets are the first six and the last six coordinates. We have shown above that the generator matrix can be given a special form starting from any information set. This shows that M₁₂ is transitive on information sets. By a basic principle of permutation groups, we have that the order of M₁₂ is |M₁₂| = 12 × 11 × 6 × |H|, where H is the