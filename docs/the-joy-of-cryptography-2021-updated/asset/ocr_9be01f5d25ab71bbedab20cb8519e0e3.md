# Contents

# 0 Review of Concepts & Notation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1

+   0.1 Logs & Exponents . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1

+   0.2 Modular Arithmetic . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1

+   0.3 Strings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4

+   0.4 Functions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5

+   0.5 Probability . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 5

+   0.6 Notation in Pseudocode . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7

+   0.7 Asymptotics (Big-O) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 8

# 1 One-Time Pad & Kerckhoffs’ Principle . . . . . . . . . . . . . . . . . . . . . . . . . . 10

+   1.1 What Is [Not] Cryptography? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10

+   1.2 Specifics of One-Time Pad . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13

# 2 The Basics of Provable Security . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21

+   2.1 How to Write a Security Definition . . . . . . . . . . . . . . . . . . . . . . . . . . . . 21

+   2.2 Formalisms for Security Definitions . . . . . . . . . . . . . . . . . . . . . . . . . . . 25

+   2.3 How to Demonstrate Insecurity with Attacks . . . . . . . . . . . . . . . . . . . . . . . 30

+   2.4 How to Prove Security with The Hybrid Technique . . . . . . . . . . . . . . . . . . . . 33

+   2.5 How to Compare/Contrast Security Definitions . . . . . . . . . . . . . . . . . . . . . . 38

# 3 Secret Sharing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47

+   3.1 Definitions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47

+   3.2 A Simple 2-out-of-2 Scheme . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 51

+   3.3 Polynomial Interpolation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 54

+   3.4 Shamir Secret Sharing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 58

+   ★ 3.5 Visual Secret Sharing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 62

# 4 Basing Cryptography on Intractable Computations . . . . . . . . . . . . . . . . . . . . 67

+   4.1 What Qualifies as a “Computationally Infeasible” Attack? . . . . . . . . . . . . . . . . . 67

+   4.2 What Qualifies as a “Negligible” Success Probability? . . . . . . . . . . . . . . . . . . . 70

+   4.3 Indistinguishability . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 72

+   4.4 Birthday Probabilities & Sampling With/out Replacement . . . . . . . . . . . . . . . . . . 76

# 5 Pseudorandom Generators . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 85

+   5.1 Definitions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 85

+   5.2 Pseudorandom Generators in Practice . . . . . . . . . . . . . . . . . . . . . . . . . . . . 87

+   5.3 Application: Shorter Keys in One-Time-Secret Encryption . . . . . . . . . . . . . . . . . 90

+   5.4 Extending the Stretch of a PRG . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 92

+   ★ 5.5 Applications: Stream Cipher & Symmetric Ratchet . . . . . . . . . . . . . . . . . . . . . 98

# 6 Pseudorandom Functions & Block Ciphers . . . . . . . . . . . . . . . . . . . . . . . . . . . 106

+   6.1 Definition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 107

+   6.2 PRFs vs PRGs; Variable-Hybrid Proofs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 110

+   6.3 Block Ciphers (Pseudorandom Permutations) . . . . . . . . . . . . . . . . . . . . . . . . . 120

+   6.4 Relating PRFs and Block Ciphers . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 121