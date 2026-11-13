
## Postmortem Concentrations: Distributed Privacy-Preserving Blockchain Authentication Framework in Cloud Forensics

Rohit Kaushik and Eva Kaushik

## 8.1 Introduction

Due to the blockchain’s cost-effectiveness and modesty, many small businesses provide processing power and storage space to cloud storage. Each block contains the previous block’s crypto-hash, time stamps, and transaction information. Blockchain is a growing collection of records connected by encryption, known as blocks. Blockchain can give immutability, ability to track, transparency, auditing ability, and accountability in addition to its security and immutable nature of the cryptographic hash linkages between blocks and instances. The gain of employing a blockchain system in digital forensics is that the administrator can supply authentication, upon which he can access digital evidence, which successfully builds verifiable evidence chains with hash functions [1]. To confirm the immutable nature, visibility, and public trust within the case examination, the blockchain uses encryption. The process of verifying that any reasonable evidence has been collected, tracked, and protected with the help of a court of law is known as the forensic report. A required stage in the forensic analysis may be the forensic report. Although it is frequently used as evidence, it must be proven that it was not tampered with during investigations for it to be accepted in a court or in legal proceedings [2][3]. Therefore, regardless of whether the evidence is used in court or not, a decent process should be followed for routine dealing and management of evidence (whether digital or not). The main branches of digital forensics are shown in Figure 8.1.

In today’s situation, crime rate is high, and once it’s ever-changing, the post-mortem report is quite straightforward. Cybercrime is currently emerging as one of the major crimes. The investigation will therefore go via several hierarchical levels using digital evidence. It plays a crucial function in preserving the accuracy and integrity of each document, providing transparency, and giving information clarity without tampering with the papers in the blockchain system. There are numerous strategies adopted to end life. Be it hanging, gunshot, cyanide, and forensic toxicology (poison consumption). The recreation of a crime scene after an occurrence can be challenging, because some evidence is left behind that helps investigators find the crime. For a proper analysis to be reached, it

![](img/f7b65e1b6017d6bb4f421d92025cbdc6_190_0.png)

### FIGURE 8.1
Main branches of digital forensics.

needs the investigation officer's skill and rhetorical understanding. To identify replicated crime scenes, meticulous analysis of the crime scene at the following points as well as an autopsy study are necessary. As numerous pieces of evidence are found at a crime scene, keep an eye out for them [4]. Drawing or image-depicting the scenario: with the suspension in place, inspection of the hanging material (noose, knot, loop, etc.); documentation of the support needed to achieve the hanging goal, ante-mortem examination of ligature material (rope) and direction of fiber on victim's body/neck; selection of swab from close to the injury (nail mark); examining the chest/throat for fingerprints and hanging-related postmortem signs; drug or alcohol use; gun fingerprints; a body shot area; and other factors evidence of dragging; suicide letter and telephone call to review decision-making history; case history, etc. When determining the cause of death, the forensic pathologist must be cautious because criminals have been known to disguise homicides as suicides in the past. The forensic pathologist's role in determining the manner of gunshot death is highlighted in the case under consideration. The downward particle distribution of the body was visible on a chest X-ray. Chest injuries caused by pellets fired from a smoothbore firearm were the cause of death. As a result of these ongoing cybercrimes that take place in the modern digital era, this proof includes a critical component of cybernetic evidence that verifies the original evidence and the evidence's relationship to the cybercrimes. It has a significant issue with Internet evidence. Managing and tracking digital evidence is done according to a custody chain approach [5]. As a result, several hierarchical layers, or top-to-bottom companies, process the forensic evidence to handle cybercrime investigations. Procedure for a cloud forensic analysis and identification: different forensic tools are shown in Table 8.1.

- The two most important procedures during the initial stage of digital forensics, case identification, are gathering data and recognizing occurrences. These two stages are essential for demonstrating the case scenario occurrence.

- The second phase is the gathering and preservation of evidence from various digital devices, such as a mobile phone, an email account, a hard drive, and other different types of digital media. The data is then secured for future processing while maintaining its integrity [6]. The security of the evidence gathered during a criminal investigation will be improved as we work to overcome

### TABLE 8.1 Forensic Tools

| Forensic Equipment | Information |
| :--- | :--- |
| Memory | It's been utilized to acquire the possible remains in the computer memory when no data is left on a hard drive or being erased (e.g., volatility). |
| Digital | It's being taken into consideration majorly to retrieve the evidence from the computer. It contains preservation, data retrieval, and identification (e.g. SANS toolkit and forensics). |
| Mobile devices | Evidence that is on any mobile device; nowadays, communication has made various advancements in portable devices (e.g., AXIOM and XRY, etc.). |

numerous obstacles, including hacking. The evidence is kept in a safe place so that no unauthorized individuals can access it. This innovation will double the system’s security.

- Examining and analyzing the devices for evidence as digital hints is part of the third stage, which is organizing the evidence. To begin, the investigator gathers the data for the case’s investigation and examines the data’s characteristics. In the second step, analysis, the investigator examines and connects the data to determine the truth and determine whether the evidence is conclusive.

- Presentation. The investigator then creates reports based on the investigation’s findings and updates them as necessary with supporting documentation before presenting them before the court.

## 8.2 Problem Statement

It has been noted that forensic reports are altered frequently while an inquiry is underway. Data in forensic reports may change due to unrecognized sources. Most of the time, as a result, the needy may not receive justice, and the verdict may not be fair. Therefore, it is imperative to create a system that guarantees the security of forensics reports from the point at which they are generated to the point at which they are used in legal proceedings.

## 8.3 Literature Review

- 1. Blockchain increases trust and transparency; it has primarily been employed in the forensics of medicine. Digital evidence, which was established earlier, will play a crucial part in a blockchain-based forensic system. Numerous uses of blockchain technology are being employed to collect proof of the theory. Our database is regularly checked for alteration using a single one-way hash code and notarial service, which is regularly utilized both internally and externally. The external service, which is more trustworthy, needs to verify our network, whereas the internal service is primarily contained within the database system itself. This process is divided into two stages: processing (during which the tuple’s hash values are retrieved and notarized), as well as verification (during which all the hashes are determined repeatedly and verified with the most recent attested values) [7][8]. The presence of tampering is evident if there is any contradiction between these values. Through the blockchain system, we may discreetly monitor financial accounting systems when fraud, or the altering of accounting data, occurs. We can simply apprehend the individual who attempted to access and alter the account’s data. So in this system, we can incorporate both the public and private sectors as well as the government of India institutions. The use of a blockchain system will be a protected area for owners; nevertheless, fraudulent or manipulators may use it as a means of continuing their criminal activity without being caught.

- 2. Investigations using digital forensics are no longer solely technical in nature. Aspects of business, systems, and law are included. The authors have developed a thorough, business- and legally oriented digital forensic framework [9]. It, as a result, developed an entirely crime-oriented architecture that will help with crime investigation.

- 3. Exploratory forensics on the smart contract’s forensic investigation framework in this study considered a variety of tools, evidence items, data formats, and other factors. According to the study’s author, hackers exploit IoT devices and other sources to steal information, and to combat this, they employ blockchain technology to create a framework for storing data and thwarting it using a variety of tactics. While we propose a framework that will aid in the prosecution of crimes like murder, they mainly focus on preventing hackers from accessing the Internet of Things.

## 8.4 Background of Related Work

- 1. Kent, P., et al. [10]. Blockchain is a type of distributed database or ledger—one of today’s top tech trends—which means the power to update a blockchain is distributed between the nodes, or participants, of a public or private computer network. Blockchain analysis is a brand-new area of study and development that only recently became popular among Bitcoin enthusiasts in 2014. This movement was primarily pushed by its decentralized and transparent nature.

- 2. Akinbi, A., et al. [11]. In regard to the recognition algorithms, they first draw attention to the distinction between system characterization, which refers to the capabilities of the technology being used and the characterization of the forensic system that will give the court objective results.

- 3. Bain, T., et al. [12]. Blockchains store information on monetary transactions using cryptocurrencies, but they also store other types of information, such as product tracking and other data. The review includes user access management, smart cards, mobile security, Internet/web-based security, forensics, and other existing and potential uses in an e-world. Additionally, each chapter includes an outline that explains how the book is organized.

- 4. Jaquet-Chiffelle et al. [13]. Blockchain technology can store linked information in the context of a decentralized platform within a peer-to-peer (P2P) network because it is a decentralized network that depends on ledger-based transactions.
