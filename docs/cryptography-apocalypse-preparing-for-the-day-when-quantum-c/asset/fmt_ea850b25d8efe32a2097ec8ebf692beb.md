
`www.scmp.com/news/china/economy/article/2140860/china-winning-race-us-develop-quantum-computers`

`https://quantumcomputingreport.com/news/`

`www.executivegov.com/2019/04/energy-department-announces-quantum-computing-funding-opportunity/`

Interested investors can commit some of their capital to quantum-related firms, using a quantum-dedicated exchange-traded fund (ETF) like this one: `https://www.defianceetfs.com/qtum`. Private investors are pouring hundreds of millions of dollars directly into private companies, including those noted here: `www.nanalyze.com/2018/09/10-quantum-computing-startups/`. In general, a lot of private investment is chasing quantum computing–related investment opportunities. As great as the promise of quantum information sciences is, as with anything else, investors beware. Many quantum industry observers think that all it takes to garner a huge inflow of investment capital is the word *quantum* in a company’s name or prospectus, just like during the similar recent investment craze in the past if you included the word *bitcoin* or *cryptocurrency* in your company name. Many people lost fortunes in early bitcoin investments. There will be winners and losers in the quantum space as well.

## Other Quantum Information Science Besides Computers

The field of quantum information sciences includes more than just quantum computers. It includes many devices and software components, such as

* Quantum random number generators
* Quantum networking
* Quantum cryptography
* Quantum applications

Many firms concentrate on these types of quantum devices instead of trying to compete in the hugely expensive field of quantum computers. Most of these items will be discussed in more detail in future chapters.

Quantum information sciences is promising to open up a range of applications that will significantly change our world. Here are some of the promised applications:

* Faster computation
* Faster optimized searches
* Better artificial intelligence
* Better cryptography
* More secure networking
* Military uses
* Improved weather forecasting
* Improved medicines and chemicals
* Improved understanding of the quantum world, astrophysics, and our universe
* Perfect privacy (using something known as *fully homomorphic cryptosystems*)
* Better financial modeling (stock trading, derivative trading, etc.)
* Better fraud detection
* Traffic management for autonomous vehicles
* Better, longer-lasting, lighter batteries
* Quantum money

We will cover most of these topics in more detail in [Chapter 5](#c05.xhtml).

## For More Information

There are several good Internet articles and books on the history and state of quantum information science. If you are interested in more information, consider these sites:

`https://mitpress.mit.edu/books/quantum-computing-everyone`

`www.irtf.org/mailman/listinfo/qirg`

`www.nist.gov/history-and-future-quantum-information`

`www.wired.com/story/wired-guide-to-quantum-computing/`

`https://en.wikipedia.org/wiki/Timeline_of_quantum_computing`

`https://en.wikipedia.org/wiki/Quantum_computing`

`https://towardsdatascience.com/the-need-promise-and-reality-of-quantum-computing-4264ce15c6c0`

## Summary

Chapter 2 covered quantum computers, their types and architectures, components, and other quantum information sciences. We discussed the main differences between quantum and traditional binary computers, and explained the technology, advantages, and disadvantages of each quantum computing architecture approach. We also covered the various major vendors and their quantum information science concentrations. [Chapter 3](#c03.xhtml) will discuss how quantum computers will likely break most forms of traditional public-key cryptography within a few years.

# 3 How Can Quantum Computing Break Today's Cryptography?

This chapter covers how quantum computing is likely capable of breaking most forms of traditional public key encryption. We begin by discussing cryptography basics, paying particular attention to how most of today's public key encryption schemes provide protection. Then you will build on your foundation from [Chapter 2](#c02.xhtml) and learn how quantum computers can break that protection and what cryptography is or isn't overly susceptible to quantum cracking.

## Cryptography Basics

*Cryptography* is the science, study, and practice of securing and authenticating people, data, transactions, and other objects between authorized parties. It is done by using encryption, integrity checks, and algorithmic implementations. Cryptography allows confidentiality and integrity of data, communications, and participants to be maintained whenever desired between authorized, designated parties (or software or devices on their behalf). This section will cover digital encryption, authentication, and integrity hashing basics.

> **NOTE**  The term *subject* will be used throughout this chapter. It is used to refer to any identity that can be tied to a cryptographic action. A subject can be a user, group, computer, device, service, daemon, company, publisher, or any other identity object.

### Encryption

*Encryption* is a popular method for subjects to keep something secret. A single subject may want to keep something secret to itself, or the secret may be shared between a selected group of people or devices. The secret can be any type of content, the identities of participating parties, and any involved transactions and objects.

Encryption in various forms has been used for thousands of years, beginning with spoken codes and encoded writing. A common example is that of simple *substitution ciphers*, where letters and numbers of an alphabet are rearranged to create a coded message that only the intended parties understand. In its simplest application, the parties using the substitution cipher could have agreed to move every character of the unencrypted message forward one letter in the alphabet to encode and encrypt the message. Thus, the word FROG would become GSPH (F + 1 forward letter position = G, R + 1 = S, O + 1 = P, and G + 1 = H). All involved authorized receivers would need to be told that the resulting encoded message could be decoded by reversing the process (i.e., G – 1 = F, S – 1 = R, P – 1 = O, and H – 1 = G). See [Figure 3.1](#c03.xhtml#c03-fig-0001) for a graphical example.

![Figure 3.1: A simple substitution cipher](images/c03f001.png)

[**Figure 3.1**](#c03.xhtml#R_c03-fig-0001)**:** A simple substitution cipher

The original, unencoded message is known as the *plaintext message*. The encoded message is known as the *encrypted message*, or *ciphertext*. The process used to transform a plaintext text message to an encrypted form is called *encryption*. The process used to reverse an encrypted message back to its original, plaintext message form is called *decryption*. The documented process and steps used to encrypt or decrypt a message is known loosely as a *cipher*, or a *cipher algorithm*.

> **NOTE**  In the computer world, a message can be any type of digital content, including text, email, chat messages, data, sound, pictures, and videos.

Every cipher is essentially a more complex implementation of the basic encryption components covered earlier in the simple substitution example. There is always a plaintext message that is encoded and decoded using a cipher algorithm. In the simple substitution method earlier, the cipher algorithm is mathematically represented as +*X* or –*X* (i.e., + or –*X*, or +–*X*), where *X* is the number of positions in the alphabet to move forward or back for the encryption or decryption.
