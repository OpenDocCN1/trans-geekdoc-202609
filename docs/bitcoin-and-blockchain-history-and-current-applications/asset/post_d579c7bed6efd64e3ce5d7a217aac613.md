
![](img/115a7d47166d21dfa1d1dc5986da244b_15_0.png)

**Dr. Mohammed Kayed** received an M.Sc. degree in Computer Science from Minia University, Minia, Egypt in 2002 and a Ph.D. degree in Computer Science from Beni-Suef University, Beni-Suef, Egypt in 2007. From 2005 to 2006, he was a research and teaching assistant in the Department of Computer Science and Information Engineering at the National Central University, Taiwan. Since 2007, he has been an assistant professor with Department of Mathematics and Computer Science, Faculty of Science, Beni-Suef University, Beni-Suef, Egypt. He is currently an associate professor and head of Computer Science Department, Faculty of Computer and Artificial Intelligence, Beni-Suef University, Egypt. He is the author of more than 18 articles. His research interests include Web Mining, Opinion Mining, Information Extraction, and Information Retrieval.

## Contributors

**Naseem Ahamed**
Finance and Accounting Department
ICFAI Business School
Hyderabad, Telangana, India

**Chiranji Lal Chowdhary**
School of Information Technology and Engineering
VIT University
Vellore, Tamil Nadu, India

**Jaipal Dhobale**
Operation and IT Department
ICFAI Business School
Hyderabad, Telangana, India

**Ahmed A. Elngar**
Computer Science
Beni-Suef University
Beni-Suef, Egypt

**Parv Garg**
Computer Science and Engineering
ICFAI Foundation for Higher Education (Deemed to be University)
Hyderabad, Telangana, India

**Ajay Kumar Jena**
School of Computer Engineering
KIIT (Deemed to be University)
Bhubaneswar, Odisha, India

**D. Kesavaraja**
Department of Computer Science and Engineering
Dr. Sivanthi Aditanar College of Engineering
Tiruchendur, Tamil Nadu, India

**Neeraj Khadse**
Computer Science and Engineering
ICFAI Foundation for Higher Education (Deemed to be University)
Hyderabad, Telangana, India

**Vaibhav Mishra**
Operation and IT Department
ICFAI Business School
Hyderabad, Telangana, India

**Subhasish Mohapatra**
School of Computer Engineering
ADAMAS University
Kolkata, West Bengal, India

**Sandeep Kumar Panda**
Computer Science and Engineering
ICFAI Foundation for Higher Education (Deemed to be University)
Hyderabad, Telangana, India

**Smita Parija**
Electrical Engineering Department
National Institute of Technology
Rourkela, Odisha, India

**S. Porkodi**
Department of Computer Science and Engineering
Dr. Sivanthi Aditanar College of Engineering
Tiruchendur, Tamil Nadu, India

**K. Varaprasada Rao**
Computer Science and Engineering
ICFAI Foundation for Higher Education (Deemed to be University)
Hyderabad, Telangana, India

## Contributors

**P. Praneeth Reddy**  
Computer Science and Engineering  
ICFAI Foundation for Higher Education  
(Deemed to be University)  
Hyderabad, Telangana, India

**Tushar Sharma**  
Computer Science and Engineering  
ICFAI Foundation for Higher Education  
(Deemed to be University)  
Hyderabad, Telangana, India

**S. Saikrishna**  
Computer Science and Engineering  
ICFAI Foundation for Higher Education  
(Deemed to be University)  
Hyderabad, Telangana, India

**Santosh Kumar Swain**  
School of Computer Engineering  
KIIT (Deemed to be University)  
Bhubaneswar, Odisha, India

**Sathya A.R.**  
Computer Science and Engineering  
ICFAI Foundation for Higher Education  
(Deemed to be University)  
Hyderabad, Telangana, India

**Mutyala Sree Teja**  
Computer Science and Engineering  
ICFAI Foundation for Higher Education  
(Deemed to be University)  
Hyderabad, Telangana, India

## 1 Bitcoin
### *A P2P Digital Currency*
*Sathya A.R.*  
ICFAI Foundation for Higher Education  
(Deemed to be University)

*Ahmed A. Elngar*  
Beni-Suef University

### CONTENTS
- 1.1 Introduction ........................................................................................................ 2
- 1.2 Digital Currencies before Bitcoin ................................................................. 2
- 1.2.1 Blinded Cash ................................................................................................. 3
- 1.2.2 Web-Based Money ....................................................................................... 3
- 1.2.3 B-Money ........................................................................................................ 3
- 1.2.4 Bit Gold .......................................................................................................... 3
- 1.2.5 Hashcash ........................................................................................................ 3
- 1.3 Bitcoin in a Nutshell ............................................................................................ 4
- 1.4 Transaction ............................................................................................................ 5
- 1.4.1 Construct a Transaction ................................................................................ 5
- 1.4.2 Getting the Right Input ................................................................................. 5
- 1.4.3 Creating the Output ...................................................................................... 6
- 1.5 Timestamp Server ................................................................................................. 6
- 1.6 Proof of Work ........................................................................................................ 7
- 1.7 Bitcoin Development Environment .................................................................... 9
- 1.7.1 Bitcoin Core Implementation ........................................................................ 9
- 1.7.2 Wallet Setup and Encryption ....................................................................... 11
- 1.8 Keys, Wallets, and Addresses ............................................................................. 12
- 1.8.1 Digital Signature .......................................................................................... 12
- 1.8.2 Keys ............................................................................................................... 13
- 1.8.3 Wallets ........................................................................................................... 13
- 1.8.4 Addresses ....................................................................................................... 14
- 1.9 Security Attacks on Bitcoin System and Countermeasures ........................... 15
- 1.9.1 Major Security Attacks ................................................................................ 15
- 1.9.1.1 Double Spending ................................................................................. 15
- 1.9.1.2 Mining Pool Attacks ............................................................................. 15
- 1.9.1.3 Client-Side Security Threat ............................................................... 17
- 1.9.1.4 Bitcoin Network Attacks ...................................................................... 17
- 1.9.2 Minor Attacks...................................................18
- 1.9.2.1 Sybil Attack...................................................18
- 1.9.2.2 Eclipse Attack..................................................18
- 1.9.2.3 Tampering.......................................................19
- 1.10 Privacy and Anonymity in Bitcoin...................................19
- 1.11 Reclaiming Disk Space..............................................20
- 1.12 Conclusion..........................................................20
- References..............................................................20

### 1.1 INTRODUCTION
Over the past few decades, there have been many new applications on the Internet, solving problems in a supportive and distributed way. There are many well-known applications that are non-commercial and collaborative; for example, Hashcash, Anonymous Communication, and BitTorrent. Generally, few applications materialize soon after the software concept is perceived. But, there are few exceptions; one such idea is digital money. The concept of digital money is around since the 1980s, but it took few decades to develop as a fully distributed solution. As per Ref. [1], several attempts had been made to build digital currencies, but they required a central authority like bank to handle transactions. Later approaches such as Bitgold, B-money, Reusable Proof of Work (RPoW), and Karma suggested to have a cryptographic puzzle named proof of work (PoW). Based on this model, every user can mine their money but using a central bank to maintain the transactional details.

To eliminate the central authority, the register which records all transaction details should also be distributive in nature. However, a serious risk involved in digital currencies or any distributed currency is double spending. As digital copies are smaller, it is possible for any malicious user to make two parallel transactions using the same coins to two different users. In traditional centralized models, the central authority like banks can identify and prevent such malicious acts, whereas it is not easy in a distributed model. The reason is that keeping the distributed information and mutual acceptance in a consistent state is challenging, especially in a malicious users environment. This goes down similar to the Byzantine Generals Problem [2]. This vision leads to employing quorum systems. Quorum systems [3] understand and accept that in a distributed environment, it is possible to have faulty information and mischievous users. Hence, to ensure a correct ledger, the voting concept was introduced assuming majority of peers are honest. However, this election approach leads to Sybil attacks [4], in which malicious users can set up several peers to challenge the electoral process and implant wrong information. Propagation delays are ignored and lead to brief inconsistencies. Bitcoin design overcomes all these difficulties.

### 1.2 DIGITAL CURRENCIES BEFORE BITCOIN
One of the earliest attempts to create cryptocurrency started few decades back in the Netherlands. When a petrol station in the Netherlands suffered nighttime thefts, few developers tried to link money with newly designed smart cards. A user who needs to access the petrol station can use these smart cards instead of cash. This can be
