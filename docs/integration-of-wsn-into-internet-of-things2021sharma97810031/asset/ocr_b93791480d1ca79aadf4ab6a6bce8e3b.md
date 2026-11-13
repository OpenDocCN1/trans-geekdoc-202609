The primordial operation in ECC systems is known as scalar multiplication and represents consecutive application of k elliptic curve group operations over an elliptic curve group generator or base point P, where k is known as the scalar. In such systems, the group operation is additive and follows well-defined formulae for a given elliptic curve model. For this reason, k additions of the base point are represented as multiplying P by the scalar k. In ECC, k is generally used as the private key and kP as the public key. With this context, finding the secret key k is akin to solving an instance of the ECDLP. The most efficient classical algorithms for this task have exponential complexity; hence, this problem is considered intractable in the scope of classical computing.

When the ECC system is tailored to constrained devices, it is said to be lightweight. This means that the solutions can observe trade-offs of performance, area, energy, or security. Generally, prioritizing one of these aspects represents compromising the others. Identifying the adequate trade-offs and creating designs that can be adapted to the application requirements are important components of lightweight cryptography.

Software and hardware realizations of PKC algorithms for constrained environments must overcome significant challenges in order to achieve optimal performance while observing the restrictions of the underlying system. In Table 5.1, we summarize the state of the art for the performance of lightweight realizations of the elliptic

# TABLE 5.1
# The Top Lightweight ECDH Realizations, with Security Levels of 128 Bits for Multiple Target Platforms. The Latency Represents the Cycle Count Required for Performing the Two Scalar Multiplications Required in the Classic ECDH Protocol

| Year | References | Curve | Field | Size (bits) | Technology | Cycles |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| \multicolumn{7}{c}{In Software} |
| 2016 | [6] | GLV+TEC | Prime | 256 | Atmega128 | 21,002,000 |
| 2016 | [7] | MoTE P255 | Prime | 255 | MSP430F1611 | 25,429,000 |
| \multicolumn{7}{c}{In Application-Specific Integrated Circuits (ASIC)} |
| 2013 | [8] | secp256r1 | Prime | 256 | 130nm | 6,734,000 |
| 2015 | [9] | K283 | Binary | 283 | 130 nm | 3,132,000 |
| 2015 | [10] | – | Binary | 283 | 65 nm | 1,025,000 |
| 2016 | [11] | P256 | Prime | 256 | 130nm | 12,400,000 |
| 2016 | [12] | – | Prime | 256 | 180nm | 1,680,000 |
| \multicolumn{7}{c}{In Field-Programmable Gate Arrays (FPGA)} |
| 2011 | [13] | P256 | Prime | 256 | Virtex II | 1,899,902 |
| 2016 | [14] | P256 | Prime | 256 | Virtex 5 | 3,807,300 |
| 2016 | [12] | – | Prime | 256 | – | 1,680,000 |
| 2019 | [15] | BE251 | Binary | 251 | Spartan 6 | 1,690,000 |
| 2019 | [15] | BE251 | Binary | 251 | Spartan 6 | 58,188 |