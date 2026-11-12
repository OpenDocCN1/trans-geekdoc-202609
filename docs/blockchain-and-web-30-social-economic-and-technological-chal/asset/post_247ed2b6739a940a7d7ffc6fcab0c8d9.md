
## Table 14.1. Screenshot of the messages provided by the client when iterates inside the data structure provided by the Fabric framework while encrypts and saves every element.

```
################################
#                              #
#           EABLOCK            #
#     YOUR SAFE BUSINESS       #
#                              #
#       eablock.com            #
#     info@eablock.com         #
#                              #
################################
```

```
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log.evtx
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log.txt
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log.xml
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log_2.evtx
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log_2.txt
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log_2.xml
#
#
INFO: Downloading and Decryption of data ...
#
```

## Table 14.1 (Continued)

```
Result of Decryption (filename only)
log_3.evtx
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log_3.txt
#
#
INFO: Downloading and Decryption of data ...
#
Result of Decryption (filename only)
log_3.xml
#
#
```

![](img/a0011e82f3a3a41227dc70cd0ddb893a_248_0.png)

## Figure 14.2 Screenshot of the Eablock client exposing the decrypted content from the Blockchain to the final user.

Since we also encrypt the file name, to steal a specific file becomes much more complicate for an attacker. Data can be recovered from the blockchain afterwards using the symmetric scheme.

Table 14.2 shows a screen where the client iterates inside the data structure provided by the Fabric framework and decrypts and saves every element.

![](img/a0011e82f3a3a41227dc70cd0ddb893a_249_0.png)

## Figure 14.3 Screenshot of the messages provided by the client when iterates inside the data structure provided by the Fabric framework while encrypts and saves every element.

## Table 14.2 Screenshot of the messages provided by the client when iterates inside the data structure provided by the Fabric framework while decrypts and saves every element.

```
###############################################
#                                             #
#                EABLOCK                      #
#                                             #
#         YOUR SAFE BUSINESS                  #
#                                             #
#                 eablock.com                 #
#                 info@eablock.com            #
#                                             #
###############################################
```

```
INFO: Encryption and uploading to BlockChain
#
log.evtx
#
#
INFO: Encryption and uploading to BlockChain
#
log.txt
#
#
INFO: Encryption and uploading to BlockChain
#
log.xml
#
#
```

## Table 14.2 (Continued)

```
INFO: Encryption and uploading to BlockChain
#
log_2.evtx
#
#
INFO: Encryption and uploading to BlockChain
#
log_2.txt
#
#
INFO: Encryption and uploading to BlockChain
#
log_2.xml
#
#
INFO: Encryption and uploading to BlockChain
#
log_3.evtx
#
#
INFO: Encryption and uploading to BlockChain
#
log_3.txt
#
#
INFO: Encryption and uploading to BlockChain
#
log_3.xml
#
#
```

## Conclusions

In this chapter, we reported an analysis of the use of Hyperledger Fabric for managing CRM in a “secure by design” approach. Information security is the main target CRM must address in order to protect customer data from accesses by unauthorized parties. The use of blockchain technology natively supports encryption anonymization and decentralization, allowing the CRM to be built on a zero trust system support where there is no need of any trust in the infrastructure hosting software components. This allows data to be encrypted in the client application under the user control. The data are available and accessible only to authorized users and unintelligible to others. The native digital signatures allow precise identification of the sender, who cannot dissociate from any action. Data integrity is natively ensured on the blockchain by encryption and hashing functions that allow the prevention of any dishonest data alteration. The encrypted data are saved on a back end based on blockchain. We implement this scheme with a permissioned Blockchain that requires a precautionary verification of network participants. We use “Fabric” by Hyperledger, a project finalized with the creation of Blockchain for Enterprise. The permission structure of Hyperledger reduces the risk of security problems, allowing transactions only between authorized parts. With Fabric, chaincode can manage interactions with databases and transactions are executed according to a selected consensus mechanism. In such architecture, web applications connected to the Internet are replaced by the Fabric blockchain. The graphical interface and the user interaction are delegated to an endpoint application where encryption is enabled on the client side end to end. The user interacts with the Fabric back end through a channel after his requests are acknowledged by an ACL and verified by chaincode, which is the only way to interact with the ledger. The internal communications are implemented with specific ACL policies. Every interaction with the data stored into the distributed ledger occurs by means of chaincode invoked only by authorized users. Each operation on data, before being accepted, is validated by the smart contracts deployed irreversibly on the blockchain. This ensures automation and security because interactions among clients and the database are executed on the basis of an ACL (access control list) containing only valid operations, reducing the surface for external attacks. We realized a prototype working stand-alone in which data flux occurs inside the software product but is enabled to connect and integrate with preexisting external systems, and we developed the client both in command line modality and in graphical user interface. By means of this prototype, we show how the concept of CRM “secure by design” can be practically implemented relying on Fabric Hyperledger. Our research drives the existing research on CRM toward a blockchain approach that exploits the most relevant features of this new technology

For More eBooks Or Request, Support hill0 & Purchase a Premium Here in My Blog Thanks & Enjoy! https://arxhm.se/blogs/hill0

## Acknowledgments

The authors are grateful to the ContaminationLab (C-Lab) of Cagliari University, which partially hosted the work and supported the Eablock project.

## Bibliography

- Barton, Dominic (2012). “Making Advanced Analytics Work”, Harvard Business Review.
- Bragagnolo, Santiago, Rocha, Henrique, Denker, Markus and Ducasse, Stephane (2018). “SmartInspect: Solidity smart contract inspector”, 2018 International Workshop on Blockchain Oriented Software Engineering (IWBOSE), Campobasso, Italy, pp. 9–18. ISBN: 978-1-5386-5987-8.
- Concas, Giulio, Destefanis, Giuseppe, Marchesi, Michele, Ortu, Marco and Tonelli, Roberto (2013). “Micro patterns in agile software”, International Conference on Agile Software Development, pp. 210–222.
- Destefanis, Giuseppe, Ortu, Marco, Counsell, Steve, Swift, Stephen, Marchesi, Michele and Tonelli, Roberto (2016). “Software development: Do good manners matter?”, PeerJ Computer Science, vol. 2, p. 73.
- Destefanis, Giuseppe, Ortu, Marco, Counsell, Steve, Swift, Stephen, Tonelli, Roberto and Marchesi, Michele (2017). “On the randomness and seasonality of affective metrics for software development”, Proceedings of the Symposium on Applied Computing, pp. 1266–1271.
- Destefanis, Giuseppe, Tonelli, Roberto, Concas, Giulio and Marchesi, Michele (2012). “An analysis of anti-micro-patterns effects on fault-proneness in large Java systems”, Proceedings of the 27th Annual ACM Symposium on Applied Computing, pp. 1251–1253.
- Ethereum white paper: https://github.com/ethereum/wiki/wiki/White-Paper
- Greenberg, P. (2009). “CRM at the Speed of Light”, in Social CRM Strategies, Tools, and Techniques for Engaging Your Customers. Fourth Edition. McGraw Hill, p. 30.
- Hulea, M.E., Rosu, O., Miron, R. and Astilean A. (2018). “Pharmaceutical cold chain management: Platform based on a distributed ledger” (Conference Paper), 21st IEEE International Conference on Automation, Quality and Testing, Robotics, AQTR 2018, 3 July 2018, pp. 1–6, Cluj-Napoca; Romania; 24 May 2018 through 26 May 2018; Category number CFP18AQT-PRT; Code 137740.
- Hyperledger Fabric white paper: www.hyperledger.org/resources/publications#white-papers
- Hyperledger white paper: www.hyperledger.org/resources/publications#white-papers
- Kinkelin, H., Hauner, V.E., Niedermayer, H.E. and Carle, G. (2018). “Trustworthy configuration management for networked devices using distributed ledgers” (Conference Paper), IEEE/IFIP Network Operations and Management Symposium: Cognitive Management in a Cyber World, NOMS 2018, 6 July 2018, pp. 1–5, Taipei, Taiwan; 23 April 2018 through 27 April 2018; Category number CFP18NOM-ART; Code 137784.
- Lenarduzzi, Valentina, Tonelli, Roberto, Marchesi, Michele and Lunesu, Maria Ilaria (2018). “Blockchain applications for Agile methodologies”, 19th International Conference on Agile Processes in Software Engineering and Extreme Programming. XP proceedings.
- Mantyla, Mika, Adams, Bram, Destefanis, Giuseppe, Graziotin, Daniel and Ortu, Marco (2016). “Mining valence, arousal, and dominance: possibilities for detecting burnout and productivity?”, Proceedings of the 13th International Conference on Mining Software Repositories, pp. 247–258.
- Marchesi, Michele, Ortu, Marco, Tonelli, Roberto, Destefanis, Giuseppe, Bracciali, Andrea and Hieronis, Robert (2018). “Smart Contracts vulnerabilities: A call for Blockchain Software Engineering?”, International Workshop on Blockchain Oriented Software Engineering (IWBOSE), pp. 19–24. doi:10.1109/IWBOSE.2018.8327567.
- Nakamoto, Satoshi, “Bitcoin: A Peer-to-Peer Electronic Cash System”, Bitcoin white paper.
- Ortu, Marco, Destefanis, Giuseppe, Adams, Bram, Murgia, Alessandro, Marchesi, Michele and Tonelli, Roberto (2015). “The JIRA repository dataset: Understanding social aspects of software development”, Proceedings of the 11th International Conference on Predictive Models and Data Analytics in Software Engineering, p. 1.
- Ortu, Marco, Destefanis, Giuseppe, Counsell, Steve, Swift, Stephen, Tonelli, Roberto and Marchesi, Michele (2016). “Arsonists or firefighters? Affectiveness in agile software development”.
- Ortu, Marco, Destefanis, Giuseppe, Kassab, Mohamad, Counsell, Steve, Marchesi, Michele and Tonelli, Roberto (2015). “Would you mind fixing this issue? An Empirical Analysis of Politeness and Attractiveness in Software Developed Using Agile Boards”, Agile Processes in Software Engineering, and Extreme Programming, pp. 122–140.
