# Chapter 2

# Binary linear codes

# 2.1 The concept of binary linear codes

**Basic concepts:** Dimension, generator matrices, minimum weight.
Linear algebra over $\mathbb{F}_2$ : basis, rank, linear independence, determinant.

Our binary code $(6,8,3)_2$ has an additional structure, which greatly simplifies its description. Consider the following three of its codewords:

100110
010101
001011

Call them $z_1,z_2,z_3$. Consider all **linear combinations** of $z_1,z_2$ and $z_3$, that is, all vectors of the form $\lambda_1 z_1 + \lambda_2 z_2 + \lambda_3 z_3$, where $\lambda_i \in \mathbb{F}_2$. These linear combinations are different and they are just exactly the words of our code. We call $\{z_1,z_2,z_3\}$ a **basis** of our code and say that the code is **linear**. Another way of seeing this is by the following observation: the sum of any two codewords is a codeword again; the code is closed under sums. We take this as a definition:

**2.1 Definition.** *A binary code is* **linear** *if it is closed under addition.*

It is a basic fact from linear algebra that each linear code (abstractly: each linear space, each vector space) has a basis. Linear algebra applies to arbitrary fields. Most people are familiar with fields like the rational numbers, the real numbers and the complex numbers, but we can apply the basics of linear algebra to finite fields like $\mathbb{F}_2$ as well. This leads to the following basic fact: