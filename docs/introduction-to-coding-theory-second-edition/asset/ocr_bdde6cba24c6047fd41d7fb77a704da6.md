# Chapter 12

# Subfield codes and trace codes

# 12.1 The trace

**Basic concepts:** Field extensions, primitive polynomials.
The Frobenius automorphism, the Galois group, the trace.

A general construction idea for good codes over some field $\mathbb{F}_q$ is to first construct a code over a larger field $\mathbb{F}_{q^r}$ and then to go down in some way from the large field to the small field. The most fruitful methods of “going down” are the trace codes and the subfield codes. Before we can discuss these methods, we need to know more about finite fields, in particular, about pairs of finite fields contained in one another.

We saw that, for every prime $p$ and every natural number $r$, there is a field $\mathbb{F}_{p^r}$ of order $p^r$. It can be constructed as an extension of the prime field $\mathbb{F}_p$, using an irreducible polynomial of degree $r$ with coefficients in $\mathbb{F}_p$. In fact, we chose not to give all the details, as this would have led us too deeply into field theory. We chose to accept without proof that all the required irreducible polynomials exist over finite fields (not over all fields: there is, for example, no irreducible polynomial of odd degree over the reals) and also that, for each order $p^r$, there is only one field.

Consider fields $\mathbb{F}_{p^s}$ and $\mathbb{F}_{p^r}$ of the same characteristic $p$, where $s \le r$. When is $\mathbb{F}_{p^s} \subset \mathbb{F}_{p^r}$? If this is the case, then the larger field $\mathbb{F}_{p^r}$ is in particular a vector space over $\mathbb{F}_{p^s}$ (the field axioms are stronger than the vector space axioms), of some dimension $d$. Then $p^r = (p^s)^d = p^{sd}$. It follows that $s$ divides $r$, and the dimension is $d = r/s$. If, on the other hand, $s|r$, we can choose an irreducible polynomial of degree $d = r/s$ with coefficients in $\mathbb{F}_{p^s}$ and construct $\mathbb{F}_{p^r}$ as an extension field of $\mathbb{F}_{p^s}$, by the method from Section 3.2 (we believe that these irreducible polynomials always exist).