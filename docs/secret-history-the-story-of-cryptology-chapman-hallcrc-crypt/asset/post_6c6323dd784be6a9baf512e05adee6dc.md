
RC₆ = 00100000
RC₇ = 01000000
RC₈ = 10000000
RC₉ = 00011011

RC₉ is the first to require reduction modulo x⁸ + x⁴ + x³ + x + 1.

## 20.3.5 Putting It All Together: How AES-128 Works

We start by XORing our message with the 0th round key (just the first 128 bits of our expanded key). This is followed by nine rounds, which are identical, except for a different round key being applied each time. Each round consists of the four steps above being applied in the same order as presented. Finally, the 10th round is a bit shorter than the previous 9. The MixColumns step is skipped. That's all there is to it!

## 20.4 AES Attacks

In October 2000, Bruce Schneier made the incredible comment “I do not believe that anyone will ever discover an attack that will allow someone to read Rijndael traffic.”³⁴ But by 2003, he and coauthor Niels Ferguson were putting doubts into print, “We have one criticism of AES: we don’t quite trust the security.”³⁵ They went on to explain the reason for their distrust:³⁶

What concerns us the most about AES is its simple algebraic structure. It is possible to write AES encryption as a relatively simple closed algebraic formula over the finite field with 256 elements. This is not an attack, just a representation, but if anyone can ever solve those formulas, then AES will be broken. This opens up an entirely new avenue of attack. No other block cipher we know of has such a simple algebraic representation. We have no idea whether this leads to an attack or not, but not knowing is reason enough to be skeptical about the use of AES.

They referenced a paper by Ferguson and others, detailing the simple representation of AES.³⁷ Nevertheless, in 2005, AES was publicly endorsed by the National Security Agency, which made it part of their “Suite B” list of recommendations.

There is, as of this writing, no practical attack against properly implemented AES. There are some theoretical attacks, but this is a completely different matter. If someone finds a way to break a cipher in 2% of the time that a brute-force attack would require, it will be of tremendous interest to cryptologists, but if that 2% still requires millions of years on the world’s fastest computer,

³⁴ Schneier, Bruce, “AES Announced,” Crypto-Gram Newsletter, October 15, 2000, http://www.schneier.com/crypto-gram-0010.html.
³⁵ Ferguson, Niels and Bruce Schneier, Practical Cryptography, Wiley, Indianapolis, Indiana, 2003, p. 56.
³⁶ Ferguson, Niels and Bruce Schneier, Practical Cryptography, Wiley, Indianapolis, Indiana, 2003, p. 57.
³⁷ Ferguson, Niels, Richard Schroeppel, and Doug Whiting, “A Simple Algebraic Representation of Rijndael,” in Vaudenay, Serge and Amr M. Youssef, editors, Selected Areas in Cryptography: 8th Annual International Workshop, SAC 2001, Lecture Notes in Computer Science, Vol. 2259, Springer, New York, 2001, pp. 103–111.

it has no importance to someone simply wanting to keep his messages private. A few theoretical attacks and attacks against reduced rounds versions of AES can be found in the papers referenced at the end of this chapter.

## 20.5 Security Guru Bruce Schneier

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_590_0.png)

Figure 20.7 Bruce Schneier (1963–), Master of Metaphors. (Photograph by Per Ervland; http://www.schneier.com/photo/).

One of the finalists for the AES competition mentioned above was Twofish, designed by a team that included Bruce Schneier (Figure 20.7). Schneier was also the creator of Blowfish. In addition to his technical skills, Bruce has one of the most entertaining writing styles of anyone working in the field of computer security. You will see his works cited in footnotes throughout part two of this book. In recent years, Bruce has focused on practicalities of security (e.g., implementation issues, non-cryptanalytic attacks, etc.) and broad issues. His style is informal and contains numerous metaphors and examples. His monthly Crypto-Gram email newsletter now also exists in blog form.38 It's packed with links to articles covering all aspects of security. Schneier was a strong critic of policies implemented under George W. Bush following 9/11. A conclusion he and coauthor Niels Ferguson drew from their years of experience is a bit unsettling:39

> > In all our years working in this field, we have yet to see an entire system that is secure.
> > That's right. Every system we have analyzed has been broken in one way or another.

38 Schneier, Bruce, Schneier on Security, A blog covering security and security technology, http://www.schneier.com/. There are links here to many of his published essays, as well as links for purchasing signed copies of his books.

39 Schneier, Bruce and Niels Ferguson, Practical Cryptography, Wiley, Indianapolis, Indiana, 2003, p. 1.

Koblitz, Neal, Alfred J. Menezes, and Scott Vanstone, “The State of Elliptic Curve Cryptography,” Designs, Codes and Cryptography, Vol. 19, Nos. 2–3, March 2000, pp. 173–193.

Lenstra, Jr., Hendrik W., “Factoring Integers with Elliptic Curves,” Annals of Mathematics, second series, Vol. 126, No. 3, November 1987, pp. 649–673. Lenstra had his result in 1984, before elliptic curves served any other cryptologic purpose. See Koblitz, Neal, Random Curves: Journeys of a Mathematician, Springer, Berlin, Germany, 2008, p. 299.

Menezes, Alfred J. Elliptic Curve Public Key Cryptosystems, Kluwer Academic Publishers, Boston, Massachusetts, 1993. This was the first book devoted completely to elliptic curve cryptography.

Miller, Victor S., “Use of Elliptic Curves in Cryptography,” in Williams, Hugh C., editor, Advances in Cryptology — CRYPTO ’85 Proceedings, Lecture Notes in Computer Science, Vol. 218, Springer, Berlin, Germany, 1986, pp. 417–426.

NSA/CSS, The Case for Elliptic Curve Cryptography, National Security Agency/Central Security Service, Fort George G. Meade, Maryland, January 15, 2009, https://web.archive.org/web/20090117023500/http://www.nsa.gov/business/programs/elliptic_curve.shtml. The reasons behind the National Security Agency’s endorsement of elliptic curve cryptography are detailed in this essay. The concluding paragraph states,

Elliptic Curve Cryptography provides greater security and more efficient performance than the first generation public key techniques (RSA and Diffie-Hellman) now in use. As vendors look to upgrade their systems they should seriously consider the elliptic curve alternative for the computational and bandwidth advantages they offer at comparable security.

Rosing, Michael, Implementing Elliptic Curve Cryptography, Manning Publications Co., Greenwich, Connecticut, 1999.

Smart, Nigel P., “The Discrete Logarithm Problem on Elliptic Curves of Trace One,” Journal of Cryptology, Vol. 12, No. 3, Summer 1999, pp. 193–196. This paper presents an attack against a very rare sort of elliptic curve that can easily be avoided.

Solinas, Jerome A., “An Improved Algorithm for Arithmetic on a Family of Elliptic Curves,” in Kaliski, Jr., Burton S., editor, Advances in Cryptology — CRYPTO ’97 Proceedings, Lecture Notes in Computer Science, Vol. 1294, Springer, Berlin, Germany, 1997, pp. 357–371. At the Crypto ’97 conference, Solinas gave an analysis of an improved algorithm for computations on the curves Koblitz proposed. This was the first paper presented publicly at a cryptography meeting by an NSA employee.41

Washington, Lawrence C., Elliptic Curves: Number Theory and Cryptography, CRC Press, Boca Raton, Florida, 2003.

## On AES

Biham, Eli and Nathan Keller, “Cryptanalysis of reduced variants of Rijndael,” Proceedings of the Third Advanced Encryption Standard Conference, National Institute of Standards and Technology (NIST), Washington, DC, 2000, pp. 230–241.

Biryukov, Alex, Dmitry Khovratovich, and Ivica Nikolić, “Distinguisher and related-key attack on the full AES-256,” in Halevi, Shai, editor, Advances in Cryptology — CRYPTO 2009 Proceedings, Lecture Notes in Computer Science, Vol. 5677, Springer, Berlin, Germany, 2009, pp. 231–249. The abstract includes the following:

Finally we extend our results to find the first publicly known attack on the full 14-round AES-256: a related-key distinguisher which works for one out of every 2^35 keys with 2^120 data and time complexity and negligible memory. This distinguisher is translated into a key-recovery attack with total complexity of 2^131 time and 2^65 memory.
