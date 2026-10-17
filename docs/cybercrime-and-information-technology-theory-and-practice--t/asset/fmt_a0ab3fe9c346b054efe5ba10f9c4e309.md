
# Cryptography

*Cryptography* began thousands of years ago, protecting secrets by applying a code to encrypt and then decrypt a message. A parallel technique, called *cryptanalysis*, was invented to breach or break the adversary’s code. According to the book *The Art of War* by the ancient Chinese military strategist Sun Tsu (c. 5th century B.C.), “Knowledge of the enemy’s dispositions can only be obtained from other men. Hence the use of spies, of whom there are five classes: (1) Local spies; (2) inward spies; (3) converted spies; (4) doomed spies; (5) surviving spies.”^([^(292)](#fn292))

Ancient civilizations invented ingenious ways to encrypt or decrypt secret messages. The algorithm or process of implementing both encryption and decryption is called *cipher* or *cypher.* Some examples include evidence of concealed information found in clay tablets as early as 1500 B.C. in Mesopotamia.^([^(293)](#fn293))

Ancient Greeks also used a wooden baton or *scytale* (σκυτάλη) to send cipher messages during military conflicts ([Figure 6.2](#c6.xhtml#f6.2)). Spartans used a belt containing a strip of parchment that contained a written message. When the messenger, wearing the belt, arrived at his destination, the receiver decrypted the message, by wrapping the parchment strip around a *scytale* of the same diameter.^([^(294)](#fn294))

![FIGURE 6.2 A scytale. Photograph from Free Software Foundation](images/fig6.2.jpg)

**FIGURE 6.2** A scytale. Photograph from Free Software Foundation

**TABLE 6.1** Polybius Square

|  || 1 || 2 || 3 || 4 || 5 |

| --- | --- | --- | --- | --- | --- |

| 1 || A || B || C || D || E |

| --- | --- | --- | --- | --- | --- |

| 2 || F || G || H || I/J || K |

| 3 || L || M || N || O || P |

| 4 || Q || R || S || T || U |

| 5 || V || W || X || Y || Z |

Julius Caesar, on the other hand, used a method called the Caesar cipher or Caesar code, that moved each letter a fixed number of places.^([^(295)](#fn295))

**TABLE 6.2** The Caesar Cipher with Three Shifted Places 

| Plain Alphabet  |

| --- |

| A || B || C || D || E || F || G || H || I || J || K || L || M |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| X || Y || Z || A || B || C || D || E || F || G || H || I || J ||  |

|  || M || N || O || P || Q || R || S || T || U || V || W || X || Y || Z |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| J || K || L || M || N || O || P || Q || R || S || T || U || V || W |

| Caesar Cipher |

During World War II, the Germans developed and used numerous mechanical and electromechanical machines for encrypting communication. Their best-known cipher machines are the *Enigma* ([Figure 6.3](#c6.xhtml#f6.3)), built by the Chiffriermaschinen Aktiengesellschaft (Cipher Machines Corporation), and the *SZ-40/SZ-42*, built by Standard Elektrik Lorenz ([Figure 6.4](#c6.xhtml#f6.4)). The British gave these encrypting machines the codename FISH Machines.^([^(296)](#fn296))

![FIGURE 6.3 Enigma machine. Courtesy of Shutterstock](images/fig6.3.jpg)

**FIGURE 6.3** Enigma machine. Courtesy of Shutterstock

![FIGURE 6.4 Lorenz-SZ42 machine.](images/fig6.4.jpg)

**FIGURE 6.4** Lorenz-SZ42 machine.

Different terminologies have been used to describe computer security*.* All the terms relate to the protection of Internet-connected computing.

The most important subcategories of computer security include:

*   *Application security* is a general term for securing applications. It includes security features within applications and measures often used for finding, fixing, and preventing security vulnerabilities against cyberthreats. Examples include email, Directory Services, Web browsers, video conferencing applications like Zoom and Skype, and file transfers.  

    Application security concentrates on keeping applications and computing devices secure from SQL injection, DoS attacks, data breaches, and more. For additional information on the OSI model and the application layer, see [Chapter 5](#c5.xhtml#c5).

*   *Cybersecurity* refers to protection from criminal activity facilitated by the Internet. It also relates to the protection of Internet-connected devices, computer programs, networks, and data from cybercriminals. In other words, cybersecurity protects physical security, which consists of sites, equipment, infrastructure, etc., and logical security, which consists of software safeguards such as user passwords, access, and authentication of Information and Communications Technology (ICT). Additionally, cybersecurity includes neglected and non-intentional incidents that compromise the confidentiality, integrity, and availability of computing systems and data*.*

*   *Network security* involves the use of countermeasures to protect the networking infrastructure, both software and hardware, from intruders.

*   *Information security*, or *InfoSec*, refers to safeguarding data in storage, in transit, and while being used.

According to 44 U.S.C. 3542—Definitions^([^(297)](#fn297))

> (1) The term “information security” means protecting information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction to provide—

> 

> 1.  (A) *Integrity*, which means guarding against improper information modification or destruction, and includes ensuring information nonrepudiation and authenticity. Integrity safeguards that data and systems are authentic, neither modified nor corrupted.

> 2.  (B) *Confidentiality*, which means preserving authorized restrictions on access and disclosure, including means for protecting personal privacy and proprietary information. Confidentiality ensures that only authorized users can access or modify data and systems and includes methods for protecting privacy. A loss of confidentiality occurs when unauthorized access or security breach occurs.

> 3.  (C) *Availability*, which means ensuring timely and reliable access to and use of information. Availability ensures accessibility and reliability by authorized users.

These three concepts are commonly known as the *CIA Triad Model*, which has been used in information security to direct policies of keeping and protecting confidential and sensitive data. The National Institute of Standards and Technology (NIST)^([^(298)](#fn298))

![FIGURE 6.5 The CIA Triad model.](images/fig6.5.jpg)

**FIGURE 6.5** The CIA Triad model.

Vulnerability in any of these areas of security can vary, and it has been necessary to categorize the levels of threat they pose. Therefore, the NIST’s Standards for Security Categorization of Federal Information and Information Systems (FIPS 199) has defined the levels of potential impact for Confidentiality, Integrity, and Availability as Low, Moderate, and High.

The potential impact is **LOW** if—

*   The loss of confidentiality, integrity, or availability could be expected to have a **limilted** adverse effect on organizational operations, organizational assets, or individuals.  

    A limited adverse effect means that, for example, the loss of confidentiality, integrity, or availability might: (i) cause a degradation in mission capability to an extent and duration that the organization is able to perform its primary functions, but the effectiveness of the functions is noticeably reduced; (ii) result in minor damage to organizational assets; (iii) result in minor financial loss; or (iv) result in minor harm to individuals.

*   The potential impact is **MODERATE** if— 

    *   The loss of confidentiality, integrity, or availability could be expected to have a **serious** adverse effect on organizational operations, organizational assets, or individuals.  
