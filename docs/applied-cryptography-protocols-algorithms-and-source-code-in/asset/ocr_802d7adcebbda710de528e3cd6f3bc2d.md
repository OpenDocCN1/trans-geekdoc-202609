# CHAPTER 7 Key Length

# Table 7.6
Recommended Public-key Key Lengths (in bits)

| Year | vs. Individual | vs. Corporation | vs. Government |
| 1995 | 768 | 1280 | 1536 |
| 2000 | 1024 | 1280 | 1536 |
| 2005 | 1280 | 1536 | 2048 |
| 2010 | 1280 | 1536 | 2048 |
| 2015 | 1536 | 2048 | 2048 |

Recommended to take the value of the key into account. Public keys are often used to secure digits of value for a long time: the bank's master key for a digital cash system, the government uses to certify its passports, or a notary public's digital signature. It probably isn't worth the effort to spend months of computing time to break an individual's private key, but if you can print your own money with a broken key the idea becomes more attractive. A 1024-bit key is long enough to sign something that will be verified within the week, or month, or even a few. But you don't want to stand up in 20 years from now with a digitally signed document and have the opposition demonstrate how to forge documents with the same signature.

Making predictions beyond the near future is even more foolish. Who knows what kind of advances in computing, networking, and mathematics are going to happen by 2020? However, if you look at the broad picture, every decade we can factor numbers twice as long as in the previous decade. This leads to Table 7.7.

On the other hand, factoring technology may reach its Omega point long before 2045. Twenty years from now, we may be able to factor anything. I think that is unlikely, though.

Not everyone will agree with my recommendations. The NSA has mandated 512-bit to 1024-bit keys for their Digital Signature Standard (see Section 20.1)—far less than I recommend for long-term security. Pretty Good Privacy (see Section 24.12) has a maximum RSA key length of 2047 bits. Arjen Lenstra, the world's most suc

# Table 7.7
Long-range
Factoring Predictions

| Year | Key Length [in bits] |
| 1995 | 1024 |
| 2005 | 2048 |
| 2015 | 4096 |
| 2025 | 8192 |
| 2035 | 16,384 |
| 2045 | 32,768 |