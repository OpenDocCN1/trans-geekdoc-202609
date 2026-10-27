γ = α ⊕ β = α * β      ∀α, β ∈ P      (13.10)
γ = α ⊖ β = β⁻¹ * α      ∀α, β ∈ P      (13.11)

The β⁻¹ represents the inverse permutation which is defined as

β⁻¹ = (k_i, k_j, k_l …)  s.t., β(k_i) < β(k_j) < β(k_l)  ∀k_i are indices of β      (13.12)

It is to be noted that abstract addition and subtraction operators are both non-commutative due to the non-commutative property of composition operator (*), i.e., α ⊕ β ≠ β ⊕ α, and α ⊖ β ≠ β ⊖ α.

To define the abstract scalar multiplication, it is required to choose a generating set forming the symmetric permutation group P. The set consisting of all permutations that swap the elements of adjacent positions is known as the set of all simple transpositions ⟨P_ST⟩. The generating set ⟨P_ST⟩ consists of n−1 elements, and its search space diameter is (n choose 2). In this work, the generating set of all simple transpositions ⟨P_ST⟩ has been chosen due to its simple search space structure, i.e., the composition of α ∈ P and ρ_i ∈ ⟨PST⟩ results in the swapping of elements at indices i and i+1 in α. The successive application of this simple property is helpful to transforming permutation ρ_i ∈ ⟨PST⟩ into the desired permutation.

The analogy for abstract scalar multiplication is similar to scalar numerical multiplication in Euclidean vector space. The multiplication of a scalar φ with permutation α ∈ P changes the length of permutation α as per the value of scalar φ. For given φ ≥ 0 and α ∈ P, the abstract scalar multiplication (φ ⊙ α) fulfills the following three conditions to simulate the scalar numerical multiplication in Euclidean vector space [12].

C1: α ⊙ φ = [α.|φ|];   C2: α ⊙ φ ≤ α      ∀φ ∈ [0,1];   C3: α ⊙ φ ≥ α      ∀φ > 1

There may be more than one permutation in P due to applications of C1–C3 and non-unique minimal decompositions of each permutation. The diameter also restricts the value of scalar φ, i.e., the scalar value must be a fraction of diameter. Due to the above restrictions, abstract scalar multiplication can be realized in many different ways. To implement the abstract scalar operation (⊙) on permutations, the following four cases are considered based on properties C1–C3.

α ⊙ φ = e if φ = 0      (13.13)
α ⊙ φ = α if φ = 1      (13.14)
α ⊙ φ ≤ α if 0 < φ < 1      (13.15)
α ⊙ φ ≥ α if φ > 1      (13.16)

Equations (13.13–13.16) follow the analogy of scalar numerical multiplication in Euclidean vector space. The abstract scalar multiplication can be computed using eqs. (13.13 and 13.14) and stochastic bubble sort algorithm [12–15].