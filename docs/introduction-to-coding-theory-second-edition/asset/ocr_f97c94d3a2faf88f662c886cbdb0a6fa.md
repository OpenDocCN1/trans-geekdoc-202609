# Chapter 3

# General linear codes

# 3.1 Prime fields

**Basic concepts:** Fields, congruences, prime fields.

We have defined codes in general, but considered linear codes only in the binary case. This is not general enough. The tactical advantage when we consider linear codes is that linear algebra helps us in finding, describing and applying these structures. Linear algebra works over any field. In the binary case the underlying field is 𝔽₂ = {0,1}, the smallest of all. Many fruitful code constructions rely on codes defined over a large field and involve “going down” to codes over a small field. Also, there are constructions that work best over larger fields. There is simply no reasonable way to get around linear codes over general finite fields.

The basic properties of a field K are the following: addition and multiplication both define commutative groups (in particular a + b = b + a and a · b = b · a for all a,b ∈ K), the collaboration of addition and multiplication is defined by the distributive law (a(b + c) = ab + ac). Most important is the following requirement: every nonzero element of K possesses a multiplicative inverse, in formulas: for every 0 ≠ a ∈ K there is some a⁻¹ ∈ K such that a · a⁻¹ = 1. The existence of the inverse has the following important consequence: if a ≠ 0 and b ≠ 0, then a · b ≠ 0 (nonexistence of 0-divisors). For finite fields these conditions (existence of the inverse and nonexistence of 0-divisors) are equivalent. Let us prove one direction:

# 3.1 Lemma. *If multiplicative inverses exist, then there are no 0-divisors.*

**PROOF** Assume ab = 0 and b ≠ 0. We want to show that necessarily