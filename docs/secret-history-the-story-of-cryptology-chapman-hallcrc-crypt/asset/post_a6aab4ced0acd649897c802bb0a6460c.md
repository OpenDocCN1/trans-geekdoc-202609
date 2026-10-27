
each multiplication will take a certain amount of time, dependent on the machine doing it. These times then correspond to particular keys.

**PATCH:** In the paper that introduced his attack, Kocher also put himself in the defensive position and suggested patches. He explained how random delays may be inserted into the decryption algorithm to throw the timing off, but moving back to offense indicated that an attacker could still break the system by collecting more data. Another patch is proposed called *blinding*. Blinding had previously been used in another context. Here it meant multiplying the received ciphertext by a random, but invertible number *r* raised to the value of the enciphering exponent (modulo *n*), prior to any deciphering. So, one is then left to decipher *r*<sup>e</sup>*C*. This is done in the normal manner, by exponentiation to the power *d*. We get (*r*<sup>e</sup>*C*)<sup>d</sup> = *r*<sup>ed</sup>*C*<sup>d</sup> = *rM*. The recipient must then multiply by the inverse of *r* to recover the message. Using a different *r* each time will prevent an attacker from being able to find a correlation between the original ciphertext block and the time needed to decipher.

## 15.1.11 **Attack 11. Textbook RSA Attack**<sup>14</sup>

If one is unable to factor the modulus *n*, there’s still a way that factoring can pay off. Simply shift the focus from *n* to the message *M*. Because, *C* = *M*<sup>e</sup> (mod *n*), if *M* can be factored as *M* = *M*<sub>1</sub>*M*<sub>2</sub>, then *C* = (*M*<sub>1</sub>*M*<sub>2</sub>)<sup>e</sup> = *M*<sub>1</sub><sup>e</sup>*M*<sub>2</sub><sup>e</sup> (mod *n*). It follows that

$$C/M_2^e = M_1^e \pmod n$$

For the moment, let’s assume that *M*<sub>1</sub> ≤ 2<sup>m<sub>1</sub></sup> and *M*<sub>2</sub> ≤ 2<sup>m<sub>2</sub></sup> for some positive integers *m*<sub>1</sub> and *m*<sub>2</sub>.

Now, if all we have is the intercepted ciphertext *C*, we don’t know *M* and cannot attempt to factor it directly, but the equality above allows us to determine the factorization. We begin by building a table of *M*<sub>1</sub><sup>e</sup> (mod *n*) values for all *M*<sub>1</sub> = 2, 3, …, 2<sup>m<sub>1</sub></sup>. Next, we start calculating *C*/*M*<sub>2</sub><sup>e</sup> (mod *n*) for *M*<sub>2</sub> = 2, 3, …, 2<sup>m<sub>2</sub></sup>. As each of these latter values is calculated, it is checked for in the *M*<sub>1</sub><sup>e</sup> (mod *n*) table. When a match is found, we have the values of *M*<sub>1</sub> and *M*<sub>2</sub> satisfying *C*/*M*<sub>2</sub><sup>e</sup> = *M*<sub>1</sub><sup>e</sup> (mod *n*). Multiplying the values *M*<sub>1</sub> and *M*<sub>2</sub> together gives us the message *M*.

This attack should remind you of the attack on double DES presented in [Section 13.4](#). Both are meet-in-the-middle attacks.

A similar attack works against ElGamal, a system detailed in [Sections 16.8 and 17.2.4](#).

**PATCH:** Randomly pad the message prior to encryption, so that *M* is not small compared to *n*. This is also a way to patch against attacks 7 and 8. It is very important to pad! The term “textbook RSA” basically means RSA *without padding*, because that is how RSA is often presented in textbooks.

## 15.1.12 **Attack 12. Ron Was Wrong, Whit Is Right Attack**

In February 2012, a group of six researchers released a paper titled “Ron was wrong, Whit is Right.”<sup>15</sup> The paper ended with

> > Factoring one 1024-bit RSA modulus would be historic. Factoring 12720 such moduli is a statistic. The former is still out of reach for the academic community (but

14. Boneh, Dan, Antoin Joux and Phong Q. Nguyen, “Why textbook ElGamal and RSA encryption are insecure,” in Okamoto, Tatsuaki, editor, *Advances in Cryptology – ASIACRYPT 2000 Proceedings*, Lecture Notes in Computer Science, Vol. 1976, Springer, Berlin, Germany, 2000, pp. 30–43.

15. Lenstra, Arjen K., James P. Hughes, Maxime Augier, Joppe W. Bos, Thorsten Kleinjung and Christophe Wachter, “Ron was wrong, Whit is right,” February 2012, https://anonymous-proxy-servers.net/paper/064.pdf.

## 15.2 A Factoring Challenge

The first part of this chapter was concerned with nonfactoring attacks on RSA. We now take the direct approach. Various algorithms for factoring are considered, although none are quick enough to break RSA with the size primes presently used. Factoring is especially hard when the number is a product of two large primes. To help convince yourself that this is a difficult problem, try to factor

```
25195908475657893494027183240048398571429282126204
03202777713783604366202070759555626401852588078440
69182906412495150821892985591491761845028084891200
72844992687392807287776735971418347270261896375014
97182469116507761337985909570009733045974880842840
17974291006424586918171951187461215151726546322822
16869987549182422433637259085141865462043576798423
38718477444792073993423658482382428119816381501067
48104516603773060562016196762561338441436038339044
1495263443219011467574445417842402092461615723350
7787077498171257724679629263865367328991215483143
8167899885040453640235273819513786365643912120103
97122822120720357
```

This number has 617 digits in base 10, but it’s called RSA-2048, because it has that many bits in base 2. There was once a $200,000 prize offered by RSA Security for anyone who could find the two prime factors and explain how they did it. The RSA factoring challenge has expired, but they did give away prizes for the factorization of other, smaller products. See Table 15.1 for sizes and prizes.

## Table 15.1 RSA Factoring Challenge Prizes

| Challenge Number | Prize ($US) | Status | Submission Date | Submitters |
|---|---:|---|---|---|
| RSA-576 | $10,000 | Factored | December 3, 2003 | J. Franke et al. |
| RSA-640 | $20,000 | Factored | November 2, 2005 | F. Bahr et al. |
| RSA-704 | $30,000 | Not factored |  |  |
| RSA-768 | $50,000 | Not factored |  |  |
| RSA-896 | $75,000 | Not factored |  |  |
| RSA-1024 | $100,000 | Not factored |  |  |
| RSA-1536 | $150,000 | Not factored |  |  |
| RSA-2048 | $200,000 | Not factored |  |  |

*Note:* The website that was the source for this table has been archived at http://web.archive.org/web/20071126084720/http://www.rsa.com:80/rsalabs/node.asp?id=2093.

RSA Security answers an obvious question in the FAQ section of their website:

## Why is the RSA Factoring Challenge no longer active?

Various cryptographic challenges—including the RSA Factoring Challenge—served in the early days of commercial cryptography to measure the state of progress in practical cryptanalysis and reward researchers for the new knowledge they have brought to the community. Now that the industry has a considerably more advanced understanding of the cryptanalytic strength of common symmetric-key and public-key algorithms, these challenges are no longer active. The records, however, are presented here for reference by interested cryptographers.

I think the challenge also served as a show of strength for the company. Not many businesses will put their products to the test in such a straightforward way. Attempts to factor the larger numbers continued even after the financial incentive went away. RSA-768 was factored in 2009 by an international team. The smaller RSA-704 held out until 2012, when it was factored by Shi Bai, Emmanuel Thomé, and Paul Zimmermann. The rest remain unsolved as of this writing.

### 15.2.1 An Old Problem

> > The problem of distinguishing prime numbers from composite numbers and of resolving the latter into their prime factors is known to be one of the most important and useful in arithmetic.… The dignity of the science itself seems to require that every possible means be explored for the solution of a problem so elegant and celebrated.
> >
> > —Carl Friedrich Gauss (1801)

There was no practical reason for wanting to find an efficient factoring algorithm in Gauss’s day, but despite this fact, the problem already had a long history. We begin our brief survey of factoring algorithms with a method from the ancient world that lives on, in a modified form, as a piece in the best non-quantum methods of today.

## 15.3 Trial Division and the Sieve of Eratosthenes (c. 284–204 BCE)

To factor a number, one may simply try dividing by each number less than that number. For example, to factor 391, one would first try 2 as a factor. It doesn’t work. One would then go on to try 3, 4, 5, 6, 7, …, 390, until a factor is found. We quickly find ways to improve this approach. If 2 is not a factor, then 4, 6, 8, etc., won’t be factors. If 3 is not a factor, then 6, 9, 12, 15, etc., won’t be factors. Hence, we only need to check prime numbers when seeking factors; that is, we need
