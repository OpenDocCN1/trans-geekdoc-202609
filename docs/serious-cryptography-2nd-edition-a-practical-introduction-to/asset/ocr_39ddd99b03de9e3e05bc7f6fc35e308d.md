anything about why. For example, the prover could prove that they know a solution to some hard computational problem without revealing the solution. You might create a ZKP for any **NP**-complete problems to prove you know a solution without revealing it.

More generally, ZKPs are used to prove a statement, such as “the number encrypted in this ciphertext is between 100 and 200” or “for a given plaintext *P* and ciphertext *C*, I know a secret key *K* for which *C* = **AES**(*K*, *P*).”

For a non-technical introduction to zero-knowledge proofs, I recommend cryptographer Amit Sahai’s video “Computer Scientist Explains One Concept in 5 Levels of Difficulty” (https://youtu.be/fOGdb1CTu5c). For mathematical details, see the links on https://github.com/matter-labs/awesome-zero-knowledge-proofs.

**NOTE** *The term zero-knowledge proof is a simplification of more accurate terms from the research literature. For example, many “zero-knowledge proof” protocols are in fact zero-knowledge arguments of knowledge. Researchers reserve the term proof for unconditional security and use argument for computational security. Furthermore, the term witness refers to the secret allowing the prover to prove its statement, as a generalization of secret or secret key, due to its broader scope.*

# Security Model

What does it mean for a ZKP protocol to be secure? Is the attacker the prover or the verifier? How can they attack the protocol? Let’s answer these questions by examining security goals and attacker models.

# Security Goals

A secure ZKP must satisfy the following notions:

+   - **Completeness** If the prover follows the protocol using the correct secret, an honest verifier is convinced of the truth of the statement. In other words, the protocol always works.
+   - **Soundness** If the prover doesn’t know the secret, they can’t convince the honest verifier of a false statement (except with negligible probability). In other words, provers can’t cheat.
+   - **Zero-knowledge** A verifier learns nothing beyond the fact that the statement is true. Specifically, they can’t learn anything about the prover’s secret.

The notion that a verifier “will be convinced of the truth of the statement” is guaranteed by the mutual agreement that the protocol satisfies these three properties—namely, that a prover could not complete the protocol if the statement was false (for example, if they didn’t know the solution they claim to).