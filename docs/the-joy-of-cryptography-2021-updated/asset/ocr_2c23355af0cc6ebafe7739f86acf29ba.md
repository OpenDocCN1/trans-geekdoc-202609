3.8. Suppose there are 9 people on an important committee: Alice, Bob, Carol, David, Eve, Frank, Gina, Harold, & Irene. Alice, Bob & Carol form a subcommittee; David, Eve & Frank form another subcommittee; and Gina, Harold & Irene form another subcommittee. Suggest how a dealer can share a secret so that it can only be opened when a majority of each subcommittee is present. Describe why a 6-out-of-9 threshold secret-sharing scheme does **not** suffice.

![](bbox=[0.3, 0.22, 0.8, 0.35])

★ 3.9. (a) Generalize the previous exercise. A **monotone formula** is a boolean function \(\phi : \{0, 1\}^n \to \{0, 1\}\) that when written as a formula uses only AND and or operations (no nots). For a set \(A \subseteq \{1, \dots, n\}\), let \(\chi_A\) be the bitstring where whose \(i\)th bit is 1 if and only if \(i \in A\). For every monotone formula \(\phi : \{0, 1\}^n \to \{0, 1\}\), construct a secret-sharing scheme whose authorized sets are \(\{A \subseteq \{1, \dots, n\} \mid \phi(\chi_A) = 1\}\). Prove that your scheme is secure.

Hint: express the formula as a tree of AND and OR gates

(b) Give a construction of a \(t\)-out-of-\(n\) secret-sharing scheme in which all shares are binary strings, and the only operation required of Share and Reconstruct is xor (so no mod-\(p\) operations). How big are the shares, compared to the Shamir scheme?

3.10. Prove that share \(s_2\) in Construction 3.14 is distributed independently of the secret \(m\).

3.11. Using actual transparencies or with an image editing program, reconstruct the secret shared in these two images:

![](bbox=[0.34, 0.67, 0.53, 0.86])

![](bbox=[0.56, 0.67, 0.75, 0.86])