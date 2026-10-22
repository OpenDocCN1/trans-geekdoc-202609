# Exhibit 7.22 NIST Recommended Key Sizes

| Symmetric Key Size (bits) | RSA and Diffie-Hellman Key Size (bits) | Elliptic Curve Key Size (bits) |
|---|---|---|
| 80 | 1024 | 160 |
| 112 | 2048 | 224 |
| 128 | 3072 | 256 |
| 192 | 8192 | 384 |
| 256 | 15360 | 521 |

Source: National Security Agency, "The Case for Elliptic Curve Cryptography," www.nsa.gov/business/programs/elliptic_curve.shtml.

Thus, in order to use RSA to protect a 256-bit AES key, one should use a key of 15,360 bits, which is an order of magnitude larger than the key sizes currently in use throughout the Internet. However, an elliptic curve key would need to be only 521 bits. Elliptic curve algorithms can use smaller keys, because the math involved makes the inverse, or decryption, operations harder as the key length increases.⁶⁰

Another feature that makes elliptic curves appealing is the fact that they are more efficient than the current implementations of public key cryptography, which tend to be relatively slow, causing them to be used more as key distribution methods than data encryption methods. Exhibit 7.23 shows the ratio of Diffie-Hellman computations versus elliptic curve computations for each of the key sizes listed in Exhibit 7.22.⁶¹

# 7.6.2 RSA Patent Expires.

On September 6, 2000, RSA Security released the RSA public key encryption algorithm into the public domain. This means that anyone can now create products that incorporate this algorithm (provided it is their own implementation and not one licensed from RSA). In effect, RSA Security waived its rights to enforce the patent for any development activities that include the RSA algorithm occurring after September 6, 2000. The U.S. patent for the RSA algorithm actually expired on September 20, 2000. The result has been an even broader use of public key encryption, at lower cost.

The RSA patent was always somewhat controversial, because it applied to a piece of mathematics, which is not what most people think of when they think of an invention. The owners of the patent were never able to expand protection beyond the United States. As a result, versions of public key encryption based on alternatives to the RSA algorithm were developed and marketed outside the country, by companies

# Exhibit 7.23 Relative Computation Costs of Diffie-Hellman and Elliptic Curves

| Security Level (bits) | Ratio of DH Cost : EC Cost |
|---|---|
| 80 | 3:1 |
| 112 | 6:1 |
| 128 | 10:1 |
| 192 | 32:1 |
| 256 | 64:1 |

Source: National Security Agency, "The Case for Elliptic Curve Cryptography," www.nsa.gov/business/programs/elliptic_curve.shtml.