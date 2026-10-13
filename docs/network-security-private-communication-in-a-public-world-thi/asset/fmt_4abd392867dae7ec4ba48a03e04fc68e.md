
The concepts in TLS (Transport Layer Security) have been covered in [Chapter 11](#ch11.xhtml#ch11) *[Communication Session Establishment](#ch11.xhtml#ch11)*, and the concepts are similar to IPsec. Alice and Bob authenticate and establish cryptographic keys for the session.

TLS grew out of Netscape’s SSL (Secure Sockets Layer) protocol. When the IETF took it over to improve and standardize it, they renamed it TLS (Transport Layer Security). Since being called TLS, it has gone through three revisions, so the latest version is 1.3 (RFC 8446). There is no real logic to why the TLS versions were named TLS 1.0, TLS 1.1, TLS 1.2, and TLS 1.3 rather than TLS version 1, TLS version 2, TLS version 3, and TLS version 4 or even why TLS 1.0 was not named SSL version 4. Most of ...

## 14 Electronic Mail Security

The first thing that springs to mind with the phrase *email security* is a message from Alice to Bob signed by Alice with her private key and encrypted with Bob’s public key. Lotus Notes had a proprietary, widely deployed implementation of encrypted email in 1989. PGP was created and released as open source by Phil Zimmermann in 1991. Various email standards for user-to-user signed and encrypted email were developed over twenty years ago, including

*   PEM [RFC 1421—Feb 1993]
*   PGP/GPG [RFC 2015—October 1996]
*   S/MIME [RFC 2311—March 1998]

In the early 1990s, there were deployment barriers such as export controls and patents, but these have been resolved. So it is somewhat astonishing that none of these, or anything implementing ...

## 15 Electronic Money

Money has a long and storied history as a medium of exchange and a mechanism for measuring and storing wealth. Nations control the minting of coins, the printing of paper currency, and the quantity of money in circulation, trying hard through physical means to avoid counterfeit bills and coins. Nowadays, almost all but the smallest payments are made using credit cards, checks, and electronic funds transfers. Large cash transactions (suitcases full of money) are usually used only for illicit or illegal transactions.

Forms of electronic money have been common for many years. The Internet is used to manage bank accounts, make purchases with credit cards, do wire transfers, and pay bills.

New protocols for dealing with money, ...

## 16 Cryptographic Tricks

We’ve covered the major cryptographic building blocks, such as secret key encryption and integrity checks, public key encryption and signatures, and hashes/message digests. In this chapter we’ll talk about some other functions. We won’t go into great detail about the math, or proofs, but we will at least demystify what these functions are attempting to do, give some intuition about how they accomplish it, and give examples of those that are used in actual real-world protocols.

### 16.1 Secret Sharing

Secret sharing is a way for someone, say, Alice, to store a piece of information, say, `S`, that must be kept secret from all except Alice but must also be retrievable by Alice. There is a tradeoff between robustly storing `S` so ...

## 17 Folklore

*Whenever I made a roast, I always started off by cutting off the ends, just like I’d seen my grandmother do. Someone once asked me why I did it, and I realized I had no idea. It had never occurred to me to wonder. It was just the way it was done. Eventually I remembered to ask my grandmother. “Why do you always cut off the ends of a roast?” She answered “Because my pan is small, and otherwise the roasts would not fit.”*

—anonymous

Many things have become accepted security practice. Most of these are to avoid problems that could be avoided in other ways if you really knew what you were doing. It’s fine to get in the habit of doing these things, but it would be nice to know at least *why* you’re doing them. A lot of these issues have ...

## Glossary

**access control—**a mechanism for limiting use of some resource to authorized users.

**access control set—**a synonym for access control list; some people make the distinction that the order of entries in an access control set cannot be significant, while the order of entries in an access control list might be.

**ACL (access control list)—**a data structure associated with a resource that specifies the authorized users.

**active attack—**one in which an attacker does something other than simply eavesdropping, for instance, transmits data, modifies data, or subverts the system so that it can impersonate an address.

**ancilla—**a qubit that is used by a quantum computation but which is initialized to a value independent of the computations’s input.

**ANSI— ...**

## Math

This supplement was written solely by me[3] (Mike Speciner) with the intention of providing material to expand and deepen your knowledge of the mathematics and algorithms behind many of the techniques explained in the book. You should be able to understand the rest of the book without this knowledge, but I[3] think it could still be helpful, or at least enlightening. This supplement, including the homework problems: `https://github.com/ms0/docs/blob/main/math.pdf`.

### M.1 Introduction

Computing technology has encouraged us to turn pretty much everything into bits. We use bits to represent numbers, text, images, audio, video, objects, scents, and even more abstract concepts like spacetime, quantum fields, and money. For a few of these, the representation ...

## Bibliography

AGRA04 Agrawal, M., Kayal, N., Saxena, N., “PRIMES is in P”, *Annals of Mathematics*, Vol. 160 #2, September 2004, pp. 781–793.

ALAG93 Alagappan, K., *Telnet Authentication: SPX*, RFC 1412, January 1993.

BALE85 Balenson, D., “Automated Distribution of Cryptographic Keys Using the Financial Institution Key Management Standard”, *IEEE Communications*, Vol. 23 #9, September 1985, pp. 41–46.

BALE93 Balenson, D., *Privacy Enhancement for Internet Electronic Mail: Part III: Algorithms, Modes, and Identifiers*, RFC 1423, February 1993.

BELL74 Bell, D. E. and LaPadula, L. J., *Secure Computer Systems: Mathematical Foundations and Model*, M74-244, Mitre Corp., October 1974.

BELL90 Bellovin, S. M. and Merritt, M., “Limitations of the Kerberos Authentication ...

## Index

Numerics

3DES, [61](#ch03.xhtml#page_61), [72](#ch03.xhtml#page_72)

A

Abel, Niels Henrik, M-[4](#ch01.xhtml#page_4)

Abelian group, M-[4](#ch01.xhtml#page_4)

absorb phase, [123](#ch05.xhtml#page_123)

Abstract Syntax Notation [1](#ch01.xhtml#page_1). *See* [ASN.1](#index.xhtml#idx23)

access control list, [14](#ch01.xhtml#page_14)

ACL, [14](#ch01.xhtml#page_14)

active attack, [7](#ch01.xhtml#page_7)

address filter, [22](#ch01.xhtml#page_22)

address-based authentication, [253](#ch09.xhtml#page_253)–[255](#ch09.xhtml#page_255)

adjugate, M-[24](#ch01.xhtml#page_24)

Adleman, Leonard, [140](#ch06.xhtml#page_140)

Advanced Encryption Standard, [75](#ch03.xhtml#page_75)–[81](#ch03.xhtml#page_81), M-[16](#ch01.xhtml#page_16)–M-[18](#ch01.xhtml#page_18)

AES, [61](#ch03.xhtml#page_61), [75](#ch03.xhtml#page_75)–[81](#ch03.xhtml#page_81), M-[16](#ch01.xhtml#page_16)–M-[18](#ch01.xhtml#page_18)

AES-GCM, [344](#ch11.xhtml#page_344)

AH, [349](#ch12.xhtml#page_349), [356](#ch12.xhtml#page_356)–[365](#ch12.xhtml#page_365)

alternating group, M-[27](#ch01.xhtml#page_27)

amplitude, [171](#ch07.xhtml#page_171)

ancilla, [184](#ch07.xhtml#page_184)

anonymity, [397](#ch14.xhtml#page_397)

append attack, [115](#ch05.xhtml#page_115)

application level gateway, [23](#ch01.xhtml#page_23)

ASN.1, [151](#ch06.xhtml#page_151)

associated data, [101](#ch04.xhtml#page_101)

associativity, M-[3](#ch01.xhtml#page_3)

asymmetric, [4](#ch01.xhtml#page_4)

attack

active, [7](#ch01.xhtml#page_7)

chosen-ciphertext, [206](#ch08.xhtml#page_206)

chosen-plaintext, [46](#ch02.xhtml#page_46), [85](#ch04.xhtml#page_85)

ciphertext-only, [45](#ch02.xhtml#page_45)
