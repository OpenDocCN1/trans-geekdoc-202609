
Each chapter serves as a testament to the dynamic nature of this interdisciplinary domain. The survey chapters provide invaluable summaries of the state-of-the-art, while the applied chapters showcase real-world implications, from securing IoT systems in smart cities to enhancing cybersecurity against crypto ransomware.

As editors, we extend our heartfelt gratitude to the esteemed authors who have contributed their expertise and insights to make this reference book a comprehensive and forward-looking resource. We hope this compilation sparks further exploration, research, and collaboration in the ever-evolving realms of machine learning and cryptography.

In the spirit of continuous learning and innovation, we invite readers to delve into the depths of this book, embracing the opportunities presented by the cross-pollination of ideas, and contributing to the ongoing narrative of progress in the fascinating confluence of machine learning and cryptography.

May this reference book inspire future generations of researchers, academics, and practitioners to unravel new dimensions in securing information and advancing the frontiers of technology.

# Chapter 1

*   Preeti Mariam Mathews
    MIT Mahaguru Institute of Technology, India
*   Anjali Sandeep Gaikwad
    Bharati Vidyapeeth, India
*   Mathu Uthaman
    Mahaguru Institute of Technology, India
*   B. Sreelekshmi
    Mahaguru Institute of Technology, India
*   V. Dankan Gowda
    [![Orcid Image](i/orcid.svg)https://orcid.org/0000-0003-0724-0333](https://orcid.org/0000-0003-0724-0333)
    BMS Institute of Technology and Management, India

## ABSTRACT

Cryptography and machine learning are part of mega-tech today. The whole of this chapter is about digital currencies. This is what will happen in the encryption world. First, the authors show how to use `PMBeast-1` for something and then later on with bitcoin cryptography where information privacy is concerned. The objective of cryptography is to make data impossible for a human eye by encryption so that only someone in possession of the secret key can determine their length. Yet cryptography is ancient. But actually, it's only within the last few hundred years that their methods and purpose have completely changed. Later parts of this chapter review some recent advances in areas such as symmetric and asymmetric encryption, public-key infrastructure (`PKI`), and cryptographic hashes. In this way, information becomes one's tutor—machine-like learning. The only difference is that we want these next-generation machines to understand the process of machine learning so as to enhance encryption systems.

## 1. INTRODUCTION

In an era of technology so advancing by the nano-second that it is known as cutting edge only if you have a single letter hanging off it somewhere--the age itself seems to be mutating into a technical one. But among all this change two fields enjoy ascendancy over everything else; each field wields its power and potential according to its own particularity. The twin foundations that are transforming our digital world, machine learning (a technical subfield of artificial intelligence in which a computer does discoveries and creates new facts) lets the Internet learn from itself; cryptography is an age-old discipline for encrypting information. Their convergence represents a nexus of innovation and transformation, with profound implications for the realm of cybersecurity and beyond. In this chapter, we will explore the vast landscape of machine learning and the complex web of contemporary encryption. Our mission is twofold: to unravel the essential concepts and techniques that underlie these fields and to illuminate the extraordinary synergy that emerges at their intersection.

Cryptography and Cryptanalysis are two subfields of cryptology, the field that studies cryptosystems generally ([Figure 1](#979-8-3693-1642-9.ch001.xhtml#f01)). The art and science of cryptography come together to build cryptosystems, which provide strong protection for sensitive data ([M. N. Reza, and M. Islam, 2021](#979-8-3693-1642-9.ch001.xhtml#r12)). This field revolves around the practical aspect of safeguarding digital data, involving the design and implementation of mechanisms based on mathematical algorithms. These mechanisms serve as the foundation for essential information security services, effectively forming a versatile toolkit for security applications. In parallel, Cryptanalysis serves as the complementary counterpart to Cryptography within the realm of cryptology. While cryptography generates ciphertext for secure transmission or storage, cryptanalysis is concerned with the analysis and potential decryption of these cryptographic systems. Cryptanalysts study cryptographic mechanisms with the aim of breaking them, revealing vulnerabilities, and identifying weaknesses (Kumar, Pullela SVVSR, & Chaturvedi, Abhay, 2023). Additionally, cryptanalysis plays a crucial role in the development of new cryptographic techniques by rigorously testing their security strengths and assessing their resilience against potential attacks. These two branches, cryptography and cryptanalysis, coexist in the ongoing quest for information security and encryption advancements.

| Figure 1. Context of cryptology |
| --- |
| ![Figure979-8-3693-1642-9.ch001.f01](i/ch001.f01.png) |

### Cryptography: Safeguarding Secrets Through the Ages

The ancient practice of cryptography, dating back millennia, has been a silent sentinel guarding secrets and sensitive information from prying eyes. From the rudimentary ciphers of ancient civilizations to the complex algorithms of today, cryptography has evolved in response to the ceaseless quest for secure communication- (Kumar, R and B. Ashreetha, 2023). We traverse the annals of history, tracing the evolution of cryptographic methods and their pivotal role in wars, diplomacy, and espionage. Yet, it is in the contemporary digital age that cryptography finds its most significant challenges and opportunities. With the advent of symmetric and asymmetric encryption, the establishment of Public-Key Infrastructure (`PKI`), and the ubiquity of cryptographic hashing, we are compelled to explore the intricate mechanisms that safeguard our digital world. The inception of cryptography coincided with the development of written language. As human societies progressed, forming tribes, groups, and kingdoms, concepts such as power, warfare, dominance, and politics emerged. These ideas fueled the ever-changing landscape of encryption, which in turn fueled people's natural inclination to communicate discreetly with chosen receivers ([S. Tan, B. Knott and D. J. Wu, 2021](#979-8-3693-1642-9.ch001.xhtml#r18)). The ancient Egyptians used hieroglyphs for encrypted communication some 4000 years ago, which is the first known application of cryptography. This code remained the exclusive knowledge of scribes entrusted with transmitting messages on behalf of kings. The use of basic mono-alphabetic substitution ciphers was subsequently adopted by intellectuals between 500 and 600 BC. The secret rule that allowed one to decode the original message was used as a replacement for letters inside the message using this approach ([P. H. Kumar and T. Samanta, 2022](#979-8-3693-1642-9.ch001.xhtml#r7)). One well-known early Roman cryptography system was the Caesars Shift Cipher, which included moving a message's characters around by a certain number, usually three. To get the original message back, the receiver would have to move the characters backwards by the same amount ([Figure 2](#979-8-3693-1642-9.ch001.xhtml#f02)).

| Figure 2. Oldest cryptographic technique |
| --- |
| ![Figure979-8-3693-1642-9.ch001.f02](i/ch001.f02.png) |

| Figure 3. Steganography (invisible watermarking) |
| --- |
| ![Figure979-8-3693-1642-9.ch001.f03](i/ch001.f03.png) |
