+   1. *Commitment:* The prover picks a random number r and computes R = rG.
+   2. *Challenge:* The prover computes c = H(G || R || A); you must include the values G and A to bind the c generation to the generator parameter G and to the public key A of the prover.
+   3. *Response:* The prover computes s = r + c a and generates the proof as an encoding of R and s.

To verify a proof (R, s) received from the prover with public key A, a verifier recomputes the challenge c = H(G || R || A) and checks the equality if sG = R + cA.

The trick in hash function protocol data to replace verifier-generated challenges was formalized by the Fiat–Shamir transform, a general technique to turn an interactive protocol into a noninteractive one. For this transform to be applicable, a verifier’s random challenges must be independent of the prover’s message and be public (nonsecret) values.

# zkSNARKs

Let’s talk about the kind of zero-knowledge proof that’s seen wide adoption in blockchain applications due to its power and efficiency. For example, zkSNARKs are the cornerstone of the Zcash confidential transaction platform: in Zcash, zkSNARKs prove that a certain amount has been deducted from an account and credited to another account, without revealing the amount of the accounts and without leading to a prohibitively large amount of computation or storage.

A zkSNARK is a type of noninteractive proof of knowledge that offers the zero-knowledge (zk) property, where SNARK stands for the following:

+   **Succinct** The proof is very small compared to the size of the statement and the secret. It may be similar in size to the statement size’s logarithm, or even of constant size—always of the same size regardless of the statement’s size.
+   **Noninteractive** A SNARK is a noninteractive argument of knowledge, typically using the Fiat–Shamir transform to turn an interactive protocol into a noninteractive one. It doesn’t need the verifier to send messages to the prover.
+   **Argument** The argument of knowledge is a computationally secure proof that is conditionally secure. In other words, it wouldn’t be secure against an attacker with infinite computing power, which is generally a tolerable limitation.
+   **Of knowledge** A SNARK offers completeness and soundness, as an argument of knowledge.

In addition, proving and verifying a zkSNARK must be computationally efficient.

Generating such a succinct proof when you want to prove the knowledge of a solution to a problem whose description doesn’t even fit in the proof size sounds counterintuitive. For example, what about statements like