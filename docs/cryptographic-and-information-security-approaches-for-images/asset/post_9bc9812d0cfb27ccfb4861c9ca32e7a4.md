
𝒫𝒫 together with the system master key ℳ𝒦. The public parameters 𝒫𝒫 include a description of the message space ℳ. The attribute universe U is union of both signing attribute universe Uₛ, and encryption/decryption attribute universe Uₑ. That is, U = Uₛ ∪ Uₑ.

**DecKeyGen**(𝒫𝒫, ℳ𝒦, A_d, δ_d) This decryption key generation algorithm is executed by CA to compute a decryption key 𝒟𝒦_{A_d,δ_d} for a set A_d ⊂ U_e (|A_d| ≥ δ_d) of decryption attributes and a threshold δ_d.

**SignKeyGen**(𝒫𝒫, ℳ𝒦, A_s, δ_s) The signing key generation algorithm is executed by CA to compute the signing key 𝒮𝒦_{A_s,δ_s} for a set A_s ⊂ U_s of signing attributes and a threshold δ_s. Note that |A_s| ≥ δ_s.

**Signcrypt**(𝒫𝒫, 𝒮𝒦_{A_s,δ_s}, W_e, W_s, msg) A signcrypting party executes this algorithm with the input 𝒫𝒫, a message msg ∈ ℳ, signing key 𝒮𝒦_{A_s,δ_s} for the attribute set A_s, an encryption attribute set W_e ⊂ U_e and a signing attribute set W_s ⊆ A_s with |W_s| ≥ δ_s. It produces a ciphertext 𝒞𝒯. The encryption attribute set W_e and the signing threshold δ_s are included in 𝒞𝒯.

**Unsigncrypt**(𝒫𝒫, 𝒞𝒯, W_v, 𝒟𝒦_{A_d,δ_d}) This algorithm is executed by ciphertext receivers with the input 𝒫𝒫, 𝒞𝒯, a signature verification attribute set W_v and a decryption key 𝒟𝒦_{A_d,δ_d} of a decryption attribute set A_d. It will correctly recover the message msg only if |A_d ∩ W_e| ≥ δ_d and the ciphertext 𝒞𝒯 contains a valid signature corresponding to W_v. Otherwise, it outputs ⊥, indicating that either the ciphertext is not valid or the ciphertext cannot be decrypted.

## Definition 9.1.
*The tABSC scheme is correct if it satisfies the following property:*

| | |
|---|---|
| **Setup** (κ,U) → (𝒫𝒫,MK) | ⇒ **Unsigncrypt** |
| **DecKeyGen** (𝒫𝒫,ℳ𝒦,A_d,δ_d) → 𝒟𝒦_{A_d,δ_d} | (𝒫𝒫,𝒞𝒯,W_v,𝒟𝒦_{A_d,δ_d}) = msg |
| **SignKeyGen** (𝒫𝒫,ℳ𝒦,A_s,δ_s) → 𝒮𝒦_{A_s,δ_s} | |
| **Signcrypt**(𝒫𝒫,𝒮𝒦_{A_s,δ_s},W_e,W_s,msg) → 𝒞𝒯 | |
| W_v = W_s and |A_d ∩ W_e| ≥ δ_d. | |

## 9.3.2 Security Definitions

We define here the message confidentiality and ciphertext unforgeability which are essential security notions of attribute-based signcryption.

**Message Confidentiality** We define the security notion of message confidentiality in tABSC through indistinguishability of ciphertexts under selective encryption attribute set and adaptive chosen ciphertext attack (IND-sEA-CCA2 security). This security notion is defined by the following game Game^{IND-sEA-CCA2}_{tABSC} played between a challenger 𝒞 and an adversary 𝒜.

**Commit.** A sends an encryption attribute set W_e* ⊂ U_e to C.
**Setup Phase.** C gets [PP, MK] ← Setup(κ, U) and sends PP to A.
**Query Phase 1.** A adaptively issues the following queries a polynomial number of times.

- **DecKey Query:** A gives a decryption attribute set A_d ⊂ U_e and a threshold δ_d such that |A_d ∩ W_e*| < δ_d, and obtains DK_{A_d,δ_d} ← DecKeyGen (PP, MK, A_d, δ_d) from C.
- **SignKey Query:** A sends a signing attribute set A_s ⊂ U_s with a threshold δ_s, and receives SK_{A_s,δ_s} ← SignKeyGen (PP, MK, A_s, δ_s) from C.
- **Unsigncrypt Query:** A submits [CT, W_s, A_d, δ_d] to C and gets back the output of Unsigncrypt (PP, CT, W_s, DK_{A_d,δ_d}), where DK_{A_d,δ_d} ← DecKeyGen (PP, MK, A_d, δ_d).

**Challenge.** A outputs two equal length messages msg0*, msg1* ∈ M and a signing attribute set W_s* ⊂ U_s, C selects a random bit μ ∈ {0,1} and sends the challenge ciphertext CT* ← Signcrypt (PP, SK_{A_s,δ_s}, W_e*, W_s*, msg_μ*) to A, where W_s* ⊆ A_s with |W_s*| ≥ δ_s, and SK_{A_s,δ_s} ← SignKeyGen (PP, MK, A_s, δ_s).

**Query Phase 2.** A continues to adaptively issue DecKey, SignKey and Unsigncrypt queries, as in Query phase 1, but with the restrictions that A cannot issue an Unsigncrypt query [CT*, W_s*, A_d, δ_d] such that |A_d ∩ W_e*| ≥ δ_d.

**Guess.** A outputs its guess μ' ∈ {0,1} for μ, and wins the game if μ' = μ.
The advantage of A in this game is defined to be Adv_A^{IND-sEA-CCA2} := |Prob[μ' = μ] − 1/2|.
*Remark 1.* In the above game, it is not necessary for A to issue signcryption queries because he can obtain the signing key for any signature attribute set, and hence he can signcrypt on his own.

## Definition 9.2.
The tABSC scheme is said to be IND-sEA-CCA2 secure if all PPT adversaries have at most a negligible advantage in Game_{tABSC}^{IND-sEA-CCA2}.

## Ciphertext Unforgeability
This security notion is defined through existential unforgeability under selective signing attribute set and adaptive chosen message attack (EUF-sSA-CMA security). The following game Game_{tABSC}^{EUF-sSA-CMA} played between a challenger C and an adversary A captures EUF-sSA-CMA security.

**Commit.** A submits a signing attribute set W_s* ⊂ U_s to C.
**Setup Phase.** C obtains [PP, MK] ← Setup(κ, U) and gives PP to A.
**Query Phase.** A adaptively issues the following queries a polynomial number of times.

- **DecKey Query:** A gives a decryption attribute set A_d ⊂ U_e and a threshold δ_d, and obtains DK_{A_d,δ_d} ← DecKeyGen(PP,MK,A_d,δ_d) from C.
- **SignKey Query:** A sends a signing attribute set A_s ⊂ U_s with a threshold δ_s, such that |A_s ∩ W_s*| < δ_s, and then receives SK_{A_s,δ_s} ← SignKeyGen(PP,MK,A_s,δ_s) from C.
- **Signcrypt Query:** A submits [msg,W_e,W_s] to C and gets back a ciphertext CT ← Signcrypt(PP,SK_{A_s,δ_s},W_e,W_s,msg), where SK_{A_s,δ_s} ← SignKeyGen(PP,MK,A_s,δ_s) with W_s ⊆ A_s, |W_s| ≥ δ_s.
- **Forgery.** A returns a ciphertext CT* := [W_e*,…].

A wins the game if the ciphertext CT* := [W_e*,…] is valid and was not obtained from a Signcrypt query. That is, Unsigncrypt(PP,CT*,W_v,DK_{W_e*|W_v*}) = msg* ≠ ⊥ and A did not issue a Signcrypt query [msg*,W_e*,W_s*].

The advantage of A in this game is defined to be Adv_A^{EUF-sSA-CMA} := Prob[A wins].

Remark 2. In the above game, it is not necessary for A to issue unsigncryption queries because he can obtain the decryption key for any decryption attribute set, and hence he can unsigncrypt on his own.

## Definition 9.3.
The tABSC scheme is said to be EUF-sSA-CMA secure if all PPT adversaries have at most a negligible advantage in Game_{tABSC}^{EUF-sSA-CMA}.

## 9.3.3 Symmetric-Key Encryption

A symmetric-key encryption scheme Π_SE with key space K and message space M consists of two PPT algorithms, SE-Enc and SE-Dec, where SE-Enc(k,m) maps a key k ∈ K and a message m ∈ M to a ciphertext ct and SE-Dec(k,ct) recovers the message m from the ciphertext ct using the key k.

## Definition 9.4.
A one-time symmetric-key encryption scheme Π_SE is said to be semantically secure if for any PPT adversary A, the advantage | Prob[ i~ = i : (m^(0),m^(1)) ← A(1^κ); i ← {0,1}, k ← K; ct ← SE-Enc(k,m^(i)); i~ ← A(ct) ] - 1/2 | of A is at most negligible.

## 9.3.4 Key Derivation Function

A key derivation function [15] is an algorithm that produces cryptographically secure secret keys from input of an initial keying material. Part of the bits or keys output by the key derivation function should not leak information on the other generated bits. A key derivation function with the output length τ, denoted by KDF, takes as input an instance from a keying source, and outputs a string of τ bits, that is, KDF(I) ∈ {0,1}^τ where I denotes an initial secret key obtained from keying source.

## Definition 9.5.
The key derivation function with the output length τ, KDF is secure if for any PPT adversary 𝒜, the advantage |Prob[𝒜(KDF(I))=1] − Prob[𝒜(R)=1]| of 𝒜 is at most negligible, where I denotes an initial secret key obtained from keying source and R is chosen uniformly at random from {0,1}^τ.

## 9.4 Proposed tABSC Scheme

In this section, we propose a tABSC scheme and prove its security in a standard model.

## 9.4.1 Description of the Scheme

The proposed tABSC scheme is detailed in the following algorithms.

Setup(κ,U) This algorithm takes as input the security parameter κ and an attribute universe description U := U_s ∪ U_e, and creates the system public and secret parameters as follows.

- Select secure bilinear pairing parameters Σ := [p, 𝔾, 𝔾_T, g, e] such that 𝔾 = ⟨g⟩, where g is a generator of the group 𝔾.
- Sample a,b ←_R ℤ_p* and set g1 := g^a, g2 := g^b and Y := e(g1, g2).
- Choose z_i ←_R ℤ_p* and set h_i := g^{z_i} for each i ∈ U_s.
- Select t_i ←_R ℤ_p* and set k_i := g^{t_i} for each i ∈ U_e.
- Pick h0, k0, ξ1, ξ2, ξ3, u0, u1, ..., uℓ ← 𝔾.
- Choose H1 : {0,1}* → {0,1}^ℓ and H2 : {0,1}* → ℤ_p* from appropriate families of collision-resistant hash functions.
- Define a function 𝒲 : {0,1}^ℓ → 𝔾 by 𝒲(θ) := u0 ∏_{i=1}^ℓ u_i^{θ_i}, where θ := (θ1, ..., θℓ) ∈ {0,1}^ℓ.
- Let Π_SE := (SE-Enc, SE-Dec) be a one-time symmetric-key encryption scheme with key space 𝒦 := {0,1}^τ and message space ℳ := {0,1}*. Let KDF be the key derivation function with the output length τ.
