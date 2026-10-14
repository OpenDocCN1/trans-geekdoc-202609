𝒫𝒫 together with the system master key ℳ𝒦. The public parameters 𝒫𝒫 include a description of the message space ℳ. The attribute universe U is union of both signing attribute universe Uₛ, and encryption/decryption attribute universe Uₑ. That is, U = Uₛ ∪ Uₑ.

**DecKeyGen**(𝒫𝒫, ℳ𝒦, A_d, δ_d) This decryption key generation algorithm is executed by CA to compute a decryption key 𝒟𝒦_{A_d,δ_d} for a set A_d ⊂ U_e (|A_d| ≥ δ_d) of decryption attributes and a threshold δ_d.

**SignKeyGen**(𝒫𝒫, ℳ𝒦, A_s, δ_s) The signing key generation algorithm is executed by CA to compute the signing key 𝒮𝒦_{A_s,δ_s} for a set A_s ⊂ U_s of signing attributes and a threshold δ_s. Note that |A_s| ≥ δ_s.

**Signcrypt**(𝒫𝒫, 𝒮𝒦_{A_s,δ_s}, W_e, W_s, msg) A signcrypting party executes this algorithm with the input 𝒫𝒫, a message msg ∈ ℳ, signing key 𝒮𝒦_{A_s,δ_s} for the attribute set A_s, an encryption attribute set W_e ⊂ U_e and a signing attribute set W_s ⊆ A_s with |W_s| ≥ δ_s. It produces a ciphertext 𝒞𝒯. The encryption attribute set W_e and the signing threshold δ_s are included in 𝒞𝒯.

**Unsigncrypt**(𝒫𝒫, 𝒞𝒯, W_v, 𝒟𝒦_{A_d,δ_d}) This algorithm is executed by ciphertext receivers with the input 𝒫𝒫, 𝒞𝒯, a signature verification attribute set W_v and a decryption key 𝒟𝒦_{A_d,δ_d} of a decryption attribute set A_d. It will correctly recover the message msg only if |A_d ∩ W_e| ≥ δ_d and the ciphertext 𝒞𝒯 contains a valid signature corresponding to W_v. Otherwise, it outputs ⊥, indicating that either the ciphertext is not valid or the ciphertext cannot be decrypted.

# **Definition 9.1.** *The tABSC scheme is correct if it satisfies the following property:*

| | |
|---|---|
| **Setup** (κ,U) → (𝒫𝒫,MK) | ⇒ **Unsigncrypt** |
| **DecKeyGen** (𝒫𝒫,ℳ𝒦,A_d,δ_d) → 𝒟𝒦_{A_d,δ_d} | (𝒫𝒫,𝒞𝒯,W_v,𝒟𝒦_{A_d,δ_d}) = msg |
| **SignKeyGen** (𝒫𝒫,ℳ𝒦,A_s,δ_s) → 𝒮𝒦_{A_s,δ_s} | |
| **Signcrypt**(𝒫𝒫,𝒮𝒦_{A_s,δ_s},W_e,W_s,msg) → 𝒞𝒯 | |
| W_v = W_s and |A_d ∩ W_e| ≥ δ_d. | |

# **9.3.2 Security Definitions**

We define here the message confidentiality and ciphertext unforgeability which are essential security notions of attribute-based signcryption.

**Message Confidentiality** We define the security notion of message confidentiality in tABSC through indistinguishability of ciphertexts under selective encryption attribute set and adaptive chosen ciphertext attack (IND-sEA-CCA2 security). This security notion is defined by the following game Game^{IND-sEA-CCA2}_{tABSC} played between a challenger 𝒞 and an adversary 𝒜.