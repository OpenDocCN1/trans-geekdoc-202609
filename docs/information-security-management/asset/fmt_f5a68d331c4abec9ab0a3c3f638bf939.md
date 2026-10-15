
With all the advantages of public key cryptographic schemes, you may be inclined to wonder why people bother with symmetric key schemes. While asymmetric key schemes have a lot of advantages, the processing power required to compute the necessary information can be significant. For that reason, symmetric and asymmetric schemes are often used together, with public key encryption used to securely pass a symmetric key for a given communication session, which is then used to secure the message traffic in route.

A digital certificate is verification from a trusted third party, called a CA, that the public key bound to the certificate belongs to the entity named in the certificate. This bound identity information and public key are digitally signed by the certificate authority with its private key. The certificate authority’s public key is bound to a special certificate, called a root certificate, which is distributed to anyone who would need to validate a digital certificate signed by it. In addition to the establishment of a certificate authority and a root certificate, the infrastructure to handle digital certificates, often referred to as the Public Key Infrastructure or PKI, requires that there must be some way to revoke a certificate if it is in some way compromised. Revocation of a digital certificate is accomplished using a Certificate Revocation List (CRL). This special list, issued by a CA, contains information about all certificates that it has digitally signed that are no longer to be trusted. This can occur if certificates are issued to a party that is later found to be fraudulent or has expired because certificates have a “shelf-life.”

### 10.3.4 Public Key Algorithms: RSA as an Example

As with DES, 3DES, IDEA, and AES for private key cryptography, there are also algorithms for public key cryptography. Two of the most common are RSA and PGP, although note that PGP is sort of a hybrid because it dispenses a public key, but creates a private key that is encoded with a public key cryptography. RSA is named for the three individuals responsible for its creation: Ron Rivest, Adi Shamir, and Len Adleman. RSA, like the symmetric algorithms DES, AES, and IDEA, is a block cipher. The block size is variable, but typically around 1024 bits.[^(17)](#9781284211658_CH10_08.xhtml#c10-bib0017) RSA, unlike most other algorithms we’ve covered, conceptually works on integers rather than strict bits, with a 1,024-bit integer being 309 decimal digits. The algorithm relies on the difficulty of factoring large numbers and generates large numbers as the product of two prime numbers. The algorithm proceeds as follows beginning with the generation of key pair. We will continue with an illustration using the conventional naming of communicative partners of Alice and Bob in our scenario (for more detail, see Kaufman et al.).[²](#9781284211658_CH10_08.xhtml#c10-bib0002)

1.  Alice chooses two relatively large, unique prime numbers, which we’ll label `p`, `q`.

2.  The product of the two prime numbers is calculated: `n = p × q`

3.  With Euler’s totient function, denoted: `(Φ(n))` calculate `n`. Euler’s function returns the number of positive integers less than `n` that are relatively prime to `n`. Being relatively prime means that the greatest common factor between the two numbers is 1. A good way to think of this is to make a fraction and see if you can reduce it. For example, if we chose to calculate `Φ(10)`, we could create the following fractions: 1/10, 2/10, 3/10, 4/10, 5/10, 6/10, 7/10, 8/10, and 9/10. As 1/10 is not reducible, only 1 and 10 are relatively prime to each other. The value 2/10 is reducible to 1/5, as they are both evenly divisible by 2, thus 2 is not relatively prime to 10. Continuing, we find that 1, 3, 7, and 9 are all relatively prime to 10, so `Φ(10) = 4`. As it turns out, a quick way to calculate Euler’s totient if you already have two factors is just to calculate the product of each factor minus 1. That is, knowing that 2(5) = 10, if we wanted to compute totient of 10 we could calculate `(2 – 1)(5 – 1) = (1)(4) = 4`.

4.  An integer is chosen by the algorithm such that it is less than and relatively prime to `Φ(n)`, which we’ll call `e`.

5.  An integer, `d`, is calculated that is congruent to `e^(–1)` modulo `Φ(n)`. Remember that two integers are congruent if the modulo value means that they both calculate to the same value, as with `39 ≡ 13` modulo `26`. In this case, we’re looking for the value that is congruent to the inverse value chosen in step 4 modulo the value calculated in step 3. While we can hit on a correct value through trial and error, Euclid’s algorithm for finding the greatest common divisor can be used.

The result of these calculations gives the key generator we provide to Alice, which really means a variety of values. Her public key would be the values `e`, determined in step 4, and `n`, determined in step 2. Her private key would be the values `d`, calculated in step 5, and `n`, from step 2. Alice would publish her public key where people who wanted to establish a secure communication channel with her could find it. If others wanted to send her an encoded message, they would break the message into chunks smaller than the value `n` in Alice’s public key. For each chunk of data smaller than `n`, the sender would convert it to an integer value and raise it the power `e` and take the result modulo `n`. By this we mean, the ciphertext would be `Message^e` modulo `n`. To decrypt the message, Alice would take the ciphertext value she received, raise it to the power `d`, and take the result mod `n`. Let’s see an example similar to one given by Stallings (p. 270),[^(17)](#9781284211658_CH10_08.xhtml#c10-bib0017) except worked all the way through:

1.  To generate an RSA public/private key pair, Alice chooses `p = 7` and `q = 11`.

2.  `n = p × q = 7 × 11 = 77`.

3.  `Φ(77)` is calculated (`Φ(77) = (7 – 1)(11 – 1) = 60`).

4.  A value relatively prime to 60 that we’ll choose is 17, so `e = 17`.

5.  We’ll calculate `d ≡ e^(–1) mod Φ(n) = 17^(–1) mod 60`: Using extended Euclid’s Algorithm = –7 ≡ 53.

6.  The public key is then {17, 77}, and the private key is {53, 77}.

If we wanted to send the message: “MEET ME AT PORTER HALL” using the method described, we could covert the message to bits using an ASCII table. The result would be seen as follows:

![](images/9781284211658_CH10_01_PG_321-1.jpg)

Converting that value into an integer would be 6.731217654514961e+42, which if we were using a larger `n` would be fine, but is much greater than our `n` of 77, so we will have to break it into smaller chunks. We’ll break it into 4-bit chunks, which will give us decimal values of between 0 and 15, and that gives us the values as follows:

![](images/9781284211658_CH10_01_PG_321-2.jpg)

Then converting the binary values to integers gives us:

![](images/9781284211658_CH10_01_PG_321-3.jpg)

Encrypting the values (X) with the public key would use the equation `X[^(17)](#9781284211658_CH10_08.xhtml#c10-bib0017)` mod 77 resulting in the values:

![](images/9781284211658_CH10_01_PG_322-1.jpg)

To reverse the process, the decryption algorithm would take the values received (X) and compute the plaintext using the equation `X^(53) mod 77`. So, for example, to confirm that the equation will yield the values in the previous table, we confirm that `16^(53) mod 77 = \[(16^(10) mod 77) × (16^(10) mod 77) × (16^(10) mod 77) × (16^(10) mod 77) × (16^(10) mod 77) × (16³ mod 77)\] mod 77 = \[23 × 23 × 23 × 23 × 23 × 15\] mod 77 = 96545145 mod 77 = 4. As you can see, they are congruent. While all this may seem straightforward, there are many complexities that we have omitted. However, this should give some glimpse into how cryptography works in general.

## 10.4 Cryptographic Uses
