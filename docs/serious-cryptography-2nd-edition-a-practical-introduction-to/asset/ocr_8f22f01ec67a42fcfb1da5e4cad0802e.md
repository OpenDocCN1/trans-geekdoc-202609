of problems that impacted real deployments of threshold signatures, from widely used open source software to commercial solutions.

# Papers vs. Code

When engineers need to implement a threshold signature protocol from their research papers, they encounter challenges. These papers, primarily aimed at cryptography researchers, often vary in editorial quality and are complicated, heavy in mathematics, and quite new. This recency can mean that an experimental protocol might not be as secure as intended. These factors contribute to a range of real-world security issues, which can be categorized into four main areas:

# Insecure protocol

If the protocol isn’t secure on paper, it won’t be more secure in implementation. Common issues include overlooked edge cases or inadequate validation when receiving inputs from other parties. For example, some protocols failed to verify if an encrypted number falls within the expected range, leading to practical attacks.

# Incomplete description

Research papers aren’t technical specifications but are written for academic audiences, so they often lack practical implementation details like networking and encoding. A notable example is the TSSHOCK attack on threshold signatures, which exploited ambiguous encoding in a hash function’s input elements, as described in “Collisions from Domain Separation Failures” on page 305.

# Incomplete implementation

The complexity of threshold signing protocols, with their numerous subcomponents and detailed requirements, can lead to overlooked security validations, particularly if these are mentioned only in appendixes. An instance of this was when a protocol required a number N = pq (for Paillier encryption) to be verified as the product of two large enough primes via a zero-knowledge proof, but this verification was omitted in the implementation, allowing insecure N values.

# Insecure component choice

Descriptions of protocols usually don’t say “use the hash function BLAKE3” or “use the 256-bit elliptic curve nistp256”; instead, they say “use a hash function and an elliptic curve that offer the security level you need.” It’s thus up to the implementers to pick suitable primitives and use their programming interfaces securely. For example, using an RSA modulus of 1,024 bits isn’t enough to ensure 128-bit security.

Additionally, risks arise when implementers intentionally modify a protocol, perhaps to enhance efficiency or fit a specific use case. This usually doesn’t end well. For examples of attacks on threshold signatures, see the papers “Alpha-Rays: Key Extraction Attacks on Threshold ECDSA Implementations” by Dmytro Tymokhanov and Omer Shlomovits (https://eprint.iacr.org/2021/1621) and “Practical Key-Extraction Attacks in Leading