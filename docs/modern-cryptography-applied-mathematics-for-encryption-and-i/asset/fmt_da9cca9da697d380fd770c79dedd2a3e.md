
[Endnotes](#part0029.xhtml#lev362)

[CHAPTER 19  The Future of Cryptography](#part0030.xhtml#ch19)

Cryptography and the Cloud

What Is the Cloud?

Cryptography Options for the Cloud

Homomorphic Cryptography

RSA

Goldwasser–Micali

Paillier

Quantum Cryptography

What Is Quantum Mechanics?

Quantum Key Distribution

Breaking Quantum Code

Conclusions

Test Your Knowledge

Answers

Endnotes

APPENDIX  Implementing Cryptography

Index

**Acknowledgments**

Writing a book is an arduous task. It is always my goal to make each book better than the last. I have to thank several people for aiding me in this ask. First, the very helpful editorial staff at McGraw-Hill Professional. They were simply wonderful to work with! And their commitment to quality is unsurpassed in the publishing world. The team included a copy editor and technical editor, both working to make sure no mistakes crept into the book. The McGraw-Hill Professional team included Meghan Manfre, Amy Stonebraker, and LeeAnn Pickrell. The technical editor did an excellent job of ensuring that all the details were technically correct, and nothing was overlooked. Without all their help, I could not have written this book. Finally, I must thank my wife, Teresa, who was so patient when I spent long hours working on this book.

**Introduction**

There are a number of cryptography books on the market today. Many are very well written. I would know; I have an extensive cryptography library and have read most of the books on the market. However, most of these books suffer from one common issue: they assume the reader has a solid mathematical background and approach cryptography from that perspective. It is also sometimes the case that cryptography authors write as if they were speaking to experienced cryptographers, or at least to those with a basic working knowledge.

This book was designed to bring cryptography to the general security community. You need not have any mathematics background beyond basic secondary school algebra. The book will cover the math you need. Furthermore, the book includes chapters on topics rarely covered in cryptography texts: cryptographic backdoors, military cryptography, and applied cryptography.

This book makes an excellent Introduction to Cryptography textbook for students taking a first course in cryptography. It is also appropriate for computer security professionals who wish to self-study and gain a working knowledge of cryptography. If you are reading this as self-study, pause at the end of each chapter, use the review questions, and ensure that you fully mastered the critical topics before proceeding.

The book is really a journey through cryptography, starting with historical cryptography and then moving into the mathematical foundations necessary to understand modern cryptography. The book then moves on to the symmetric and asymmetric algorithms used today. It also includes chapters on Secure Sockets Layer (SSL), cryptanalysis, military applications for cryptography, and the future of cryptography.

The book is replete with links to external sources where you can get additional information, particularly in the chapters on mathematics and number theory. Each chapter ends with a series of questions to test your knowledge. The Appendix includes a set of tutorials for using some cryptography tools. These make excellent labs if this book is used as a textbook. Also, instructors and professors can download slides from the publisher. The accompanying slides make this an excellent choice for teaching an introductory cryptography course.

PART I  

Foundations

### 1  

**History of Cryptography to the 1800s**

**In this chapter we will cover the following:**

![image](Images/image00483.jpeg)    `Single substitution ciphers`

![image](Images/image00483.jpeg)    `Multi-alphabet substitution`

![image](Images/image00483.jpeg)    `Devices`

![image](Images/image00483.jpeg)    `Transposition ciphers`

The desire to send secret communications is almost as old as written communication itself. For centuries, it often involved military secrets or political intrigue. Generals needed to communicate about troop movements to ensure that if a message was intercepted it wouldn’t be intelligible to the enemy. Political intrigue, such as a palace coup, required surreptitious communications.

Modern cryptography still includes military communications as well as political scheming, but it has expanded into more mundane areas as well. Online banking and shopping, for example, have made cryptography a part of most people’s daily lives, whether they are aware of it or not. Many people also choose to encrypt their computer hard drives or files. Others encrypt their e-mail transmissions. Today, cryptography permeates our lives.

**Note**

The release of Apple’s iOS 6.0 was interesting because it changed how the iPhone would implement cryptography.

#### Why Study Cryptography?

It is an unfortunate fact that most people have almost no knowledge of cryptography. Even within the discipline of computer science, and more specifically the profession of computer security, a dearth of cryptographic knowledge plagues the industry. Most computer security professionals have only the most basic understanding of cryptography. Some would even argue that a deeper knowledge of cryptography is unnecessary. It can be assumed that since you are reading this book, you feel a need to deepen and broaden your knowledge of cryptography, and there are clearly practical reasons to do so, particularly for those in the computer security profession.

By understanding cryptology, you can select the most appropriate cryptographic implementations to suit your needs. Even if you have no desire to be a cryptographer, you still have to choose which tool to use to encrypt a hard drive, for example. Should you use the Data Encryption Standard (DES)? Triple DES (3DES)? Blowfish? The Advanced Encryption Standard (AES)? If you use AES, then what key size do you use, and why? If you are interested in message integrity for e-mail, should you use the Secure Hash Algorithm (SHA-2)? Perhaps a message authentication code (MAC) or hash message authentication code (HMAC)? Which will provide the most appropriate solution to your particular problem, and why?

In addition, knowing about cryptology helps you understand issues that occur when cryptographic incidents broadly impact computer security. A good example occurred in 2013, when the *New York Times* reported that among the documents released by National Security Agency subcontractor Edward Snowden was evidence that the NSA had placed a cryptographic backdoor in the random number generator known as `Dual_EC_DRBG (Elliptic Curve Deterministic Random Bit Generator)`. This news story generated a flurry of activity in the computer security community. But what is a cryptographic backdoor? What does this mean for privacy and security? Does this mean that the NSA could read anyone’s e-mail as if it were published on a billboard?
