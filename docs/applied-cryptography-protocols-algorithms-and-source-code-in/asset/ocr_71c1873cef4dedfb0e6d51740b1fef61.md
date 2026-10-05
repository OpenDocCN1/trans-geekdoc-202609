# CHAPTER 17 Other Stream Ciphers

+   - Statistical criteria such as ideal k-tuple distributions.
- Confusion—every keystream bit must be a complex transformation of all or most of the key bits.
- Diffusion—redundancies in substructures must be dissipated into long-range statistics.
- Nonlinearity criteria for Boolean functions like mth-order correlation immunity, design to linear functions, avalanche criterion, and so on.

This list of design criteria is not unique for stream ciphers designed by the system-theoretic approach; it is true for all stream ciphers. It is even for all block ciphers. The unique point about the system-theoretic approach is that stream ciphers are designed to satisfy these goals directly.

The major problem with these cryptystems is that nothing can be proven about their security; the design criteria have never been proved to be either necessary or for security. A keystream generator may satisfy all the design principles, but could still turn out to be insecure. Another could turn out to be secure: There is still some magic to the process.

On the other hand, each of these keystream generators is a different problem for a cryptanalyst. If enough different generators are out there, it may not be the cryptanalyst's time to break each one. He may better achieve fame and glory by figuring out better ways to factor large numbers or calculating logarithms.

# 17.9 COMPLEXITY-THEORETIC APPROACH TO STREAM-CIPHER DESIGN

Rueppel delineated a complexity-theoretic approach to stream-cipher design. Here, a cryptographer attempts to use complexity theory to prove that his generators are secure. Consequently, the generators tend to be more complicated, based on the same sorts of hard problems as public-key cryptography. And like public-key algorithms, they tend to be bulky and cumbersome.

# Shamir's Pseudo-Random-Number Generator

Adi Shamir used the RSA algorithm as a pseudo-random-number generator [1417]. While Shamir showed that predicting the output of the pseudo-random-number generator is equivalent to breaking RSA, potential biases in the output were demonstrated in [1401,200].

# Blum-Micali Generator

This generator gets its security from the difficulty of computing discrete logarithms [200]. Let g be a prime and p be an odd prime. A key x_0, starts the process:

```
x_{i+1} = g^{x_i} \pmod p
```

The output of the generator is 1 if x_i < (p-1)/2, and 0 otherwise.