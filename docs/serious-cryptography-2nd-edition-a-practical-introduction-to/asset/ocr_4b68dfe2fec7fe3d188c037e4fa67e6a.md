# Single-Signer Schnorr Signatures

Before seeing how multiparty signing works, let’s see how single-party Schnorr signing works. Suppose Alice has a private key a, with associated public key A = aG. Here a is a number, or scalar, in a given range of numbers (specifically, the finite field over which the elliptic curve is defined, typically positive integers modulo some large prime numbers, of at least approximately 256 bits), and G is a fixed base point of the curve.

To sign a message M, Alice proceeds as follows:

+   1. Pick a secret random number, r, and compute the point R = rG. The value r is a nonce, a one-time private key with R its public key.
+   2. Compute h = H(R || A || M), the value that you’ll “connect” to the private key a and the one-time private key r to sign M. We not only hash the message but also bind h to the signer and the nonce, respectively, via the nonsecret values A and R. Without these, different attacks would be possible.
+   3. Compute s = r + ha and return the pair (R, s) as a signature. You can see s as the multiplication between the secret key and the data to sign, where the secret r masks the result; without this, it’s trivial to recover the private key from a signature.

Verify a signature by checking that sG equals R + H(R || A || M)A. This works because from s = r + ha, substituting r + ha for s in sG, you obtain

sG = (r + ha)G = rG + haG = R + hA

with h = H(R || A || M), which the verifier must compute from the message M, the public key A, and the R part of the signature.

# Schnorr Multisignatures

In multisignatures we don’t have one signer but multiple ones. For the sake of simplicity, we’ll describe the case of two cosigners: meet Bob, who’ll sign messages jointly with Alice. Bob’s private key is b and his public key is B = bG. To jointly create a multisignature, Alice and Bob could proceed as follows to sign a message M:

+   1. Alice picks a nonce r_A, computes R_A = r_A G, and sends R_A to Bob.
+   2. Bob picks a nonce r_B, computes R_B = r_B G, and sends R_B to Alice.
+   3. They compute R = R_A + R_B and set h = H(R || A || B || M), the value that Alice and Bob will use to generate their part of the signature. A specific value of h is bound to the parties via their public keys (A and B) and bound to the current signing session via the nonce R only for the specific signature execution as defined by the nonce R.
+   4. Alice computes s_A = r_A + ha and sends it to Bob.
+   5. Bob computes s_B = r_B + hb and sends it to Alice.