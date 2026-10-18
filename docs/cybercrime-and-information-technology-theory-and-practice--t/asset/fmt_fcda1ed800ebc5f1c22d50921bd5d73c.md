
[Figure 6.26](#c6.xhtml#f6.26) demonstrates a hash function that takes a variable-length input and generates a fixed-length output. [Figure 6.27a](#c6.xhtml#f6.27) and [b](#c6.xhtml#f6.27) shows the difference between encryption and hashing algorithm.

![FIGURE 6.26 The hashing algorithm.](images/fig6.26.jpg)

**FIGURE 6.26** The hashing algorithm.

![Figure 6.27a and b The difference between encryption and hashing algorithm.](images/fig6.27.jpg)

*Figure 6.27a and b* The difference between encryption and hashing algorithm.

#### [What Does “Salting” a Hashtag Mean?](#contents.xhtml#re_h-6-24)

In hashing, the term “Salt” describes a unique use of random characters added to a one-way function. Salting uses the additional input to safeguard password hashes against dictionary attacks. A new salt is randomly generated for each password and increases the computational power of hashed passwords. In other words, the Salt and the password are concatenated and processed, making a password hash output unique and much less vulnerable to attack. For example, if Bob and Alice use the same password, such as `123456`, both would share the same hash. Consequently, the hacker can predict the password that maps to that hash value by using the dictionary and brute-force attacks. If the password is known, the hacker can access all the accounts that use the hash. With Salt added before the hashing process, the passwords are unique and can better safeguard passwords in storage.

*   If we take the most common password, `123456`, by applying the Secure Hash Algorithm (SHA-256),^([^(345)](#fn345))

*   b59936bb842a7bcccc54004091069467d78b85b7372e0f843c2b346c186daa14

*   When Salt is added `A1ndQngn2m3` to the password `123456`, and we hash it then, the salted input becomes :`123456A1ndQngn2m3`. As a result, the hash algorithm will be something like this  

      70c1e0b744121ea8197422639cfee796282696f1b1070165186b1e446abada94

The length of the hash depends on the hashing algorithm. Some common hashing algorithms include:

*   `Message Digest Algorithm 5 (MD5)` was introduced in 1992 and creates 128-bit outputs. The MD5 algorithm has been shown to have weaknesses which make it easy to break. Although a hash function is designed to work only in one direction, MD5 is easy to reverse.^([^(346)](#fn346))

*   `Secure Hash Algorithm (SHA)` family 

    *   SHA-1 was designed by the National Security Agency (NSA) in 1993 and creates 160-bit hash values.

    *   SHA-2 creates hash values with 224-bit, 256-bit, 384-bit, or 512-bits. It was designed by the NSA in 2001 and is recommended for secure hashing.^([^(347)](#fn347))

    *   SHA-3 is the latest version of SHA family and was developed by the NSA in 2012. It is designed to protect against brute-force attacks.^([^(348)](#fn348))

## [6.7 Conclusion](#contents.xhtml#re_h-6-25)

As more smart devices connect to the Internet, cybercrime will continue to evolve transnationally. The threats posed by the different forms of cybercrime will increasingly dominate our lives. As we create barriers to their crimes, hackers will continue to become more sophisticated and will always develop new techniques and tools.

Lack of information security, knowledge, and training lead to errors in the mishandling of sensitive data and hacking attacks. Electronic health records (EHRs) and sensitive payment information from credit cards continue to be used for fraud or sold on the Dark Web for profit. Our expectations of privacy continue to suffer.

But then, for any type of cyberattack, there is, hopefully, a defense that we must learn and use.

So far, we humans have been the weakest link in cybersecurity. With IoT and other devices proliferating, the future of cybersecurity relies on a combination of machine learning, artificial intelligence (AI), and savvy people to detect security threats and malicious activities and secure computing devices and networks. Ultimately, understanding and influencing human behavior will help create a better approach to cybersecurity.

## [6.8 Key Words](#contents.xhtml#re_h-6-26)

| Access Control || Exploit |

| --- | --- |

| Active Attacks || Firewall |

| Advanced Encryption Standards || FIPS 199 |

| (AES) || Hacker |

| Adware || Hash Functions |

| Antivirus Software || Integrity |

| Application Security || Information Security |

| Authorization || Intrusion Detection System (IDS) |

| Authentication || Intrusion Prevention System (IPS) |

| Asymmetric Encryption || Malware |

| Behavioral Analytics || Network Security |

| Biometrics || Passive Attacks |

| Caesar cipher || Phishing |

| CIA Triad Model || Protocols |

| Cloud Security || Security Audit |

| Crime-as-a-Service (CaaS) || Security Threat |

| Cryptography || Software-as-a-Service (SaaS) |

| Confidentiality || Spam |

| Cybersecurity || Spoofing |

| Cyberwarfare || SQL Injection |

| Data Breach || Steganography |

| Demilitarized Zone (DMZ) || Symmetric Encryption |

| Denial of service (DoS) || Virtual Private Network (VPN) |

| Digital Certificates and Certificate || Vulnerability |

| Authority (CA) || Wi-Fi Hacking |

# [Chapter 7 Internet of Things (IoTs)](#contents.xhtml#re_c7)

DOI: [10.4324/9780429318726-7](https://doi.org/10.4324/9780429318726-7)

## [Objectives](#contents.xhtml#re_h-7-1)

After completing this chapter, the student will be able to:

*   Understand the Internet of Things (IoTs) and the four different lead stages

*   Understand real-world applications

*   Understand industrial IoT and its relation to manufacturing

*   Illustrate IoT architecture

*   Explain different types of IoT protocols and standards

*   Describe the IoT ecosystem—bandwidth, interoperability, power usage, and range

*   Understand the importance of security in IoT devices

*The Neuwirth family is returning from a weekend visiting relatives in a neighboring state. As they reach a point about an hour from home, they want to make the house ready for their arrival. Using their phone, they set the thermostat in the downstairs and bedrooms to 70 degrees; turn on the lights in the family room and kitchen; notify their pet sitter that they will be stopping by to pick up Roddy, their golden retriever; and turn on the oven, setting it to 350 degrees so they can pop in a prepared casserole as soon as they arrive.*

*Sara Taffley, a second grader, has had Type 1 diabetes since the age of 3. She wears an insulin delivery pump to make sure that her glucose level does not go out of bounds. At 10 o’clock one morning, her mother receives an alert on her smartphone that Sara’s glucose has exceeded 200 mg/dl and she has just received 30 units of insulin to bring it down. Sara’s pediatrician has received the same alert, as has the nurse’s office in her school. Sara’s mother leaves work and heads to Sara’s school. By the time she arrives, Sara is resting comfortably in the nurse’s office, and her doctor has already checked in with the school. Sara’s glucose is now 99 mg/dl, a normal reading.*

## [7.1 The Internet of Things—An Introduction](#contents.xhtml#re_h-7-2)

Like the `Industrial Revolution`, which began around 1760^([^(349)](#fn349))

The phrase “Internet of Things” was coined by Kevin Ashton in 1999.^([^(350)](#fn350))

A few years later, a book^([^(351)](#fn351))
