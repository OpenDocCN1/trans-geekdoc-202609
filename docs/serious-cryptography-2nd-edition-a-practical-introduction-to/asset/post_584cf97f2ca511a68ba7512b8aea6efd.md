
```
sage: x = 1234567
sage: y = power_mod(x, e, n); y
1904832305575504
sage: power_mod(y, d, n)
1234567
```

*Listing 10-2: Computing the RSA trapdoor permutation back and forth*

You assign the integer 1,234,567 to *x* and then use the `power_mod(x, e, n)` function, the exponentiation modulo *n*, or *x*<sup>*e*</sup> mod *n* in equation form, to calculate *y*. After computing *y* = *x*<sup>*e*</sup> mod *n*, you calculate *y*<sup>*d*</sup> mod *n* with the trapdoor *d* to return the original *x*.

How hard is it to find *x* without the trapdoor *d*? An attacker able to factor big numbers could break RSA by recovering *p* and *q* and then φ(*n*) to compute *d* from *e*. Another risk to RSA lies in an attacker’s ability to compute *x* from *x*<sup>*e*</sup> mod *n*, or *e*th roots modulo *n*, without necessarily factoring *n*. While both risks seem closely connected, we don’t know for sure that they’re equivalent.

Assuming that factoring and finding *e*th roots are about equally hard, RSA’s security level depends on three factors: the size of *n*, the choice of *p* and *q*, and how the trapdoor permutation is used. If *n* is too small, one could factor it in a realistic amount of time, revealing the private key. To be safe, *n* should be at least 2,048 bits long (a security level of about 90 bits, requiring a computational effort of about 2<sup>90</sup> operations) but preferably 4,096 bits long (a security level of approximately 128 bits). The values *p* and *q* should be unrelated random prime numbers of similar size. If they’re too small or too close together, it’s easier to determine their value from *n*. Finally, you shouldn’t use the RSA trapdoor permutation directly for encryption or signing, as I’ll discuss shortly.

## Encrypting with RSA

Typically, RSA is used in combination with a symmetric encryption scheme, where RSA encrypts a symmetric key that serves to encrypt a message with a symmetric cipher, such as AES-GCM. But encrypting a message or symmetric key with RSA is more complicated than simply converting the target to a number *x* and computing *x*<sup>*e*</sup> mod *n*.

In the following subsections, I explain why a naive application of the RSA trapdoor permutation is insecure and how strong RSA-based encryption works.

### Textbook RSA Encryption’s Malleability

The phrase *textbook RSA encryption* describes the simplistic RSA encryption scheme wherein the number exponentiated contains only the message you want to encrypt. For example, to encrypt the string *RSA*, you first convert it to a number—for example, by concatenating the ASCII encodings of each of the three letters as a byte: *R* (byte 52), *S* (byte 53), and *A* (byte 41). The resulting byte string 525341 is equal to 5,395,265 when converted to decimal, which you might then encrypt by computing 5,395,265^e mod n. Without knowing the secret key, there’s no way to decrypt the message—at least in theory.

However, textbook RSA encryption is deterministic: if you encrypt the same plaintext twice, you’ll get the same ciphertext twice. And there’s an even bigger problem: given two textbook RSA ciphertexts y₁ = x₁^e mod n and y₂ = x₂^e mod n, you can derive the ciphertext of x₁ × x₂ by multiplying these ciphertexts together:

$$y_1 \times y_2 \bmod n = x_1^e \times x_2^e \bmod n = (x_1 \times x_2)^e \bmod n$$

The result is (x₁ × x₂)^e mod n, the ciphertext of the message x₁ × x₂ mod n. An attacker could create a new valid ciphertext from two RSA ciphertexts, compromising the security of your encryption by allowing them to deduce information about the original message. This weakness makes textbook RSA encryption *malleable*. (If you know x₁ and x₂, you can compute (x₁ × x₂)^e mod n, too, but if you know only y₁ and y₂, you shouldn’t be able to multiply ciphertexts and get the ciphertext of the multiplied plaintexts.)

Another problem with the naive textbook RSA encryption is the existence of “special” messages. Whatever n and e are, 1^e = 1. Thus, the message 1 is left unchanged through encryption. Textbook RSA has many other problems, but you’ll learn to avoid them by using a strong RSA encryption.

## Strong RSA Encryption with OAEP

To make RSA ciphertexts nonmalleable, the number exponentiated during encryption should combine message data with additional data called *padding*, as Figure 10-1 shows.

![](img/ace4de942d037de8ea5835bc9fbe57cd_227_0.png)

The standard way to encrypt with RSA in this fashion is to use Optimal Asymmetric Encryption Padding (OAEP), a combination commonly called RSA-OAEP. This scheme involves creating a bit string as large as the modulus by padding the message with extra data and randomness before applying the RSA function.

> **NOTE**  Official documents such as the PKCS#1 standard and NIST’s Special Publication 800-56B refer to OAEP as RSAES-OAEP. OAEP improves on the earlier method PKCS#1 v1.5, which is one of the first in a series of Public-Key Cryptography Standards (PKCS) by RSA. It is markedly less secure than OAEP yet has remained in use in many systems after OAEP's introduction.

### Security

OAEP uses a PRNG to ensure the indistinguishability and nonmalleability of ciphertexts by making the encryption probabilistic. It's been proven secure as long as the RSA function and the PRNG are secure and, to a lesser extent, the hash functions aren't too weak. You should use OAEP when encrypting with RSA, rather than its predecessor, the standard PKCS#1 v1.5.

### Encryption

Encrypting with RSA in OAEP mode requires a message (such as a symmetric key, K), a PRNG, and two hash functions. To create the ciphertext, use a given modulus n long of m bytes (that is, 8m bits and therefore an n lower than 2^{8m}). To encrypt K, form the encoded message as

$M = H \| 00 \dots 00 \| 01 \| K$

where H is an h-byte constant defined by the OAEP scheme, followed by as many 00 bytes as necessary and a 01 byte. Figure 10-2 shows how to process this encoded message, M.

![](img/ace4de942d037de8ea5835bc9fbe57cd_228_0.png)

Figure 10-2: Encrypting a symmetric key, K, with RSA-OAEP, where H is a fixed parameter and R is random bits

You generate an h-byte random string R and set M = M ⊕ Hash1(R), where Hash1(R) is as long as M. Next, set R = R ⊕ Hash2(M), where Hash2(M) is as long as R. Now use these new values of M and R to form an m-byte string P = 00 || M || R, which is as long as the modulus n and which you can convert to an integer number less than n. This conversion results in the number x, which you then use to compute the RSA function x^e mod n to get the ciphertext.

To decrypt a ciphertext y, first compute x = y^d mod n and, from this, recover the final values of M and R. Next, retrieve M's initial value by calculating M ⊕ Hash1(R ⊕ Hash2(M)). Finally, verify that M is of the form H || 00 … 00 || 01 || K, with an h-byte H and 00 bytes followed by a 01 byte.

In practice, the parameters m and h (the length of the modulus and the length of Hash2's output, respectively) are typically m = 256 bytes (for 2,048-bit RSA) and h = 32 (using SHA-256 as Hash2). This leaves m − h − 1 = 223 bytes for M, of which up to m − 2h − 2 = 190 bytes are available for K (the “− 2” is due to the 01 byte separator in M). The Hash1 hash value is then composed of m − h − 1 = 223 bytes, which is longer than the hash value of any common hash function. To build a hash with such an unusual output length, the RSA standard specification defines a mask generating function technique to create hash functions that return arbitrarily large hash values from any hash function. As another approach, use an extendable output function (XOF) such as SHAKE or BLAKE3, although this differs from the standard specifications.

## Signing with RSA

Digital signatures can prove that the holder of the private key tied to a particular digital signature signed some message, typically to endorse its content. Because only the private key holder knows the private exponent d, no one else can compute a signature y = x^d mod n from some value x, but everyone can verify y^e mod n = x given the public exponent e. In principle, one can use that verified signature as evidence to demonstrate that the private-key holder signed some particular message; this is a property called nonrepudiation.

It’s tempting to see RSA signatures as the converse of encryption, but they aren’t. Signing with RSA isn’t the same as encrypting with the private key. Encryption provides confidentiality, whereas digital signatures help prevent forgeries. The most salient example of this difference is that it’s OK for a signature scheme to leak information on the message signed, because the message isn’t secret. For example, a scheme that reveals parts of the messages could be a secure signature scheme but not a secure encryption scheme.

Because of the necessary processing overhead, public-key encryption can process only short messages, which are usually secret keys rather than actual messages. A signature scheme, however, can process messages of arbitrary sizes by using their hash values Hash(M) as a proxy, and it can be deterministic yet secure. Like RSA-OAEP, RSA-based signature schemes can use a padding scheme, but they can also use the maximal message space allowed by the RSA modulus.
