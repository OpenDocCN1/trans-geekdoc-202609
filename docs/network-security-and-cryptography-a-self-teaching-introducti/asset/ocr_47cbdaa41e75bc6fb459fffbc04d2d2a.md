# 308 • NETWORK SECURITY AND CRYPTOGRAPHY

= (128 mod 11, (100 × 100 × 100 × 30) mod 11)
= (7, 8)

+   3. Decryption
Knowing (x, g, p), user “A” will decrypt the cipher-text C as follows:
A. Compute (-x) mod Φ(p) mod 10 = 10 - x = 10 - 5 = 5
B. Compute (gᵃᵏ)⁻ mod p = (7)⁵ mod 11 = (49 × 7) mod 11
= (5 × 5 × 7) mod 11 = 10
C. Compute (M × yᶠ × gᵃ⁻ᵈ) mod p = (8 × 10) mod 11
= 3 = M (Original Message)

# 7.7 ELLIPTIC CURVE CRYPTOGRAPHY (ECC)

Elliptic Curve Cryptography (ECC) makes use of Elliptic Curves that draw values for their variables and coefficients from finite fields. It is a futuristic technology for Public Key Cryptography. The older technologies like RSA require exceedingly large key-sizes to provide desired levels of security. Larger key sizes result in higher overheads for Encryption/Decryption. The ECC promises the same levels of security with smaller key sizes; thus, with much lower overheads. The U.S. National Security Agency has already endorsed the ECC technology for the protection of classified information up to Top Secret, with a key-size of 384 bits.

# 7.7.1 Elliptic Curves

Mathematically, an Elliptic Curve is expressed by a quadratic equation of the form:
Y² = x³ + ax + b
where “x” and “y” are variables and “a” and “b” are coefficients.
The Elliptic Curve is represented by the set of (x, y) pairs that satisfies the previous quadratic equation. There will be an infinite set of (x, y) pairs satisfying the quadratic equation. The set also includes a point at infinity, called the zero point. The complete set of points forms an abelian group, with the point at infinity forming the identity element.