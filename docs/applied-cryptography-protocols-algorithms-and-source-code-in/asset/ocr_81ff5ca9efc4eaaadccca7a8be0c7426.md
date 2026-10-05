# 5.4 Identity-Based Public-Key Cryptography

# Patents

Chaum has patents for several flavors of blind signatures (see Table 5.1).

# 5.4 IDENTITY-BASED PUBLIC-KEY CRYPTOGRAPHY

Alice wants to send a secure message to Bob. She doesn't want to get his public key from a key server, she doesn't want to verify some third-party's identity on her public-key certificate; and she doesn't want to store Bob's public key on her own computer. She just wants to send him a secure message.

**Identity-based systems**, sometimes called Non-Interactive Key Sharing (NIKS), solve this problem [1422]. Bob's public key is based on his name and network (or telephone number, or physical address, or whatever). With normal public-key cryptography, Alice needs a certificate that associates Alice's Bob with her identity. With identity-based cryptography, Bob's public key is his identity. This is a really cool idea, and as ideal as you can get for a mail system: If Alice knows Bob's, she can send him secure mail. It makes the cryptography as transparent as possible.

If Alice's private key is compromised, she has to change some aspect of her identity to get another one. A serious problem is designing a system in which a collision of users cannot forge a key.

A lot of work has been done on the mathematics of sorts of schemes—most of it in Japan—which turns out to be infuriatingly complicated to make secure. Many of the proposed solutions involve choosing a random number for each user—in my opinion defeats the real point of the system. Some of the algorithms discussed in Chapters 19 and 20 can be identity-based. For details, algorithms, and cryptanalysis, see [19,1422,891,1022,1515,1202,1196,908,674,1131,1023,1516,1536,1544,63,1210,314,313,1549,1543,993,1517,748,1228]. An algorithm that does not rely on any random numbers is [1035]. The system discussed in [1546,1547,1507] is insecure against a chosen-public-key attack, so is the system proposed as NIKS-TAS [1542,1540,1541,993,375,158]. Honestly, nothing proposed so far practical and secure.

> TABLE 5.1
Chaum's Blind Signature Patents

| U.S. PATENT # | DATE | TITLE |
|---|---||
| 4,759,063 | 7/19/88 | Blind Signature Systems [323] |
| 4,759,064 | 7/19/88 | Blind Unanticipated Signature Systems [324] |
| 4,914,698 | 3/3/90 | One-Show Blind Signature Systems [326] |
| 4,949,380 | 8/14/90 | Returned-Value Blind Signature Systems [328] |
| 4,991,210 | 2/5/91 | Unpredictable Blind Signature Systems [331] |

![](bbox=[0.15, 0.936, 0.849, 0.966])