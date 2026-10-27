# Chapter 6

# Matrix Encryption

Polygraphic substitution ciphers replace characters in groups, rather than one at a time. In Section 4.4, we examined the Playfair cipher, which falls into this category, because the characters are substituted for in pairs. We now turn to a more mathematically sophisticated example, matrix encryption.

# 6.1 Levine and Hill

Lester Hill (Figure 6.1) is almost always given credit for discovering matrix encryption, but as David Kahn pointed out in his definitive history of the subject, Jack Levine’s work in this area preceded Hill’s. Levine (Figure 6.2) also pointed this out in a 1958 paper.¹ Nevertheless, matrix encryption is typically referred to as the Hill cipher. Levine explained how this happened:²

> Sometime during 1923-1924 while I was a high-school student I managed to construct a cipher system which would encipher two completely independent messages so that one message could be deciphered without disclosing that a second message was still hidden (I also did for three messages). Not long thereafter (end of 1924) Flynn’s Weekly magazine started a cipher column conducted by M. E. Ohaver (Sanyam of A.C.A.), a most excellent series appearing every few weeks. Readers were encouraged to submit their systems which Ohaver then explained in a later issue. So I sent him my system mentioned above and it appeared in the Oct. 22, 1926 issue with its explanation in the Nov. 13, 1926 issue. Ohaver gave a very good explanation and some other interesting remarks [...] In 1929 Hill’s first article appeared in the Math. Association Monthly Journal recognized he had a very general system which could encipher plaintext units of any length very easily, but the basic principle was the same as my 2-message system

¹ Levine, Jack, “Variable Matrix Substitution in Algebraic Cryptography,” American Mathematical Monthly, Vol. 65, No. 3, March 1958, pp. 170–179.

² The Jack Levine Papers, 1716--994, North Carolina State University, MC 308.1.7, Correspondence 1981–1991, Various, Levine, Jack, letter to Louis Kruh, July 24, 1989.