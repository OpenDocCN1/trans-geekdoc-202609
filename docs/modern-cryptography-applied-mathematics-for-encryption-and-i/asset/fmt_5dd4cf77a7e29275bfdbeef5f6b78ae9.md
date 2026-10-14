
![image](Images/image00484.jpeg) `PRNG` People often select third-party products to generate random numbers for cryptographic keys. Any competent programmer with a working knowledge of cryptographic backdoors could create a product that generated random numbers/keys with a backdoor. Such a product could then be released as freeware, or via a web site, guaranteeing a significant number of people might use the PRNG.

![image](Images/image00484.jpeg) `Product tampering` Any individual working in a technology company, if that individual works in the appropriate section of the company, could potentially introduce a backdoor without the company being aware of it.

![image](Images/image00484.jpeg) `Hacking` Although this is more difficult and thus less likely to occur, there is always the potential of someone hacking into a device and compromising its cryptography. For example, a router with VPN capabilities must generate new keys for each VPN session. Theoretically, someone could hack that router and alter its key generation. Such a task would be difficult, however.

**Note**

Although I indicate that I have not yet heard of individuals or small groups creating cryptographic backdoors, that may be due simply to a lack of skills on their part. The primary purpose in my writing this book was to provide a real understanding of cryptography. The same lack of knowledge about the details of cryptography also permeates the hacking community.

#### Countermeasures

Detecting cryptographic backdoors is a very difficult task. As you have seen earlier in this chapter, one of the goals of a cryptographic backdoor is to be undetectable. You could, of course, subject any random number generator or cipher to extensive cryptanalysis to determine if a backdoor is likely, but that process is very time-consuming and beyond the capabilities of most organizations. And waiting until some researcher discovers a likely backdoor is inefficient. You could be using that backdoor cipher for quite a few years before some researcher discovers the backdoor.

The first issue is key generation. There is always a risk when you rely on a third party for key generation. The best solution, assuming you have the necessary skills in programming and basic mathematics, is to write code for your own key generation. For symmetric keys, I recommend implementing Blum, Blum, Shub, Yarrow, or Fortuna. Crépeau and Slakmon state the following: “This suggests that nobody should rely on RSA key generation schemes provided by a third party. This is most striking in the smartcard model, unless some guarantees are provided that all such attacks to key generation cannot have been embedded.”^([15](#part0029.xhtml#ch18note15a))

For many, writing code for key generation is not a viable option. For example, many programmers who write applications for Microsoft Windows rely on the Microsoft CryptoAPI for key generation. A simple mechanism, at least for generating symmetric keys, would be to take that API (or any other) and subject it to a cryptographic hash that has the appropriate sized output, and then use that output as the key. An even simpler approach would be to generate two random numbers, and then XOR them together using the resulting number as the key. Either technique will essentially bury the cryptographic backdoor in another operation. The cryptographic hashing technique is the more secure and reliable of the two methods.

There have been some attempts in the industry to address this issue as well. The Open Crypto Audit Project is an attempt to detect cryptographic flaws, including backdoors, in open source software. The group includes a number of respected cryptographers. Its web site (`https://opencryptoaudit.org/`) lists the organization’s charter:

![image](Images/image00484.jpeg) `Provide technical assistance to free open source software (“FOSS”) projects in the public interest`

![image](Images/image00484.jpeg) `Coordinate volunteer technical experts in security, software engineering, and cryptography`

![image](Images/image00484.jpeg) `Conduct analysis and research on FOSS and other widely used software in the public interest`

![image](Images/image00484.jpeg) `Contract with professional security researchers and information security firms to provide highly specialized technical assistance, analysis, and research on FOSS and other widely used software in the public interest`

#### Conclusions

This chapter provided an introduction to cryptographic backdoors. Since the Snowden revelations of 2013, this topic has become very widely discussed in the security community. Cryptographic researchers have been exploring backdoors for many years before those revelations, however.

You need not know the details of the specific implementations discussed in this chapter; however, the general concepts of output indistinguishability, confidentiality, and so on, are critical, and you should have a solid working knowledge of these topics. It is also important that you have some knowledge of the countermeasures discussed in this chapter.

#### Test Your Knowledge

[1](#part0029.xhtml#ch18qu1). `With regard to cryptographic backdoors, what is output indistinguishability?`

[2](#part0029.xhtml#ch18qu2). `With regard to cryptographic backdoors, what is confidentiality?`

[3](#part0029.xhtml#ch18qu3). `What made the Clipper chip relevant to backdoors?`

[4](#part0029.xhtml#ch18qu4). `\_\_\_\_\_\_\_\_\_\_\_\_ is a colloquial term for creating cryptographic algorithms that resemble the original/actual algorithms, but provide the creator an advantage in cracking encrypted messages.`

[5](#part0029.xhtml#ch18qu5). `In simple terms, the backdoor in Dual_EC_DRBG is based on what?`

##### Answers

[1](#part0029.xhtml#ch18qu1a). `With output indistinguishability, you cannot distinguish the backdoor version of a cipher from the traditional version of the cipher.`

[2](#part0029.xhtml#ch18qu2a). `The cipher with the backdoor should still be secure from attackers who don’t know about the backdoor.`

[3](#part0029.xhtml#ch18qu3a). `It was designed so that all cryptographic keys would be kept in an escrow that would be available to law enforcement.`

[4](#part0029.xhtml#ch18qu4a). `Kleptography`

[5](#part0029.xhtml#ch18qu5a). `The selection of P and Q`

#### Endnotes

[1](#part0029.xhtml#ch18note1). `N. Sullivan, “How the NSA (may have) put a backdoor in RSA’s cryptography: A technical primer,” 2014, [http://arstechnica.com/security/2014/01/how-the-nsa-may-have-put-a-backdoor-in-rsas-cryptography-a-technical-primer/](http://arstechnica.com/security/2014/01/how-the-nsa-may-have-put-a-backdoor-in-rsas-cryptography-a-technical-primer/).`

[2](#part0029.xhtml#ch18note2). `A. Young and M. Yung, “Kleptography: Using Cryptography Against Cryptography,” 2002, [http://cryptome.org/2013/09/klepto-crypto.pdf](http://cryptome.org/2013/09/klepto-crypto.pdf).`

[3](#part0029.xhtml#ch18note3). `B. Schneier, “Defending Against Crypto Backdoors,” 2013, [www.schneier.com/blog/archives/2013/10/defending_again_1.html](http://www.schneier.com/blog/archives/2013/10/defending_again_1.html).`

[4](#part0029.xhtml#ch18note4). `B. Schneier, M. Fredrikson, T. Kohno, and T. Ristenpart, “Surreptitiously Weakening Cryptographic Systems,” 2015, [https://eprint.iacr.org/2015/097.pdf](https://eprint.iacr.org/2015/097.pdf).`

[5](#part0029.xhtml#ch18note5). `K. Gjøsteen, “Comments on Dual-EC-DRBG/NIST SP 800-90, Draft December 2005,” 2006, [www.math.ntnu.no/~kristiag/drafts/dual-ec-drbg-comments.pdf](http://www.math.ntnu.no/~kristiag/drafts/dual-ec-drbg-comments.pdf).
