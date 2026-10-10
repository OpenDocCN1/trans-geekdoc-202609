
# References (Chapter 4)

[11] Beck, R., J. S. Czepluch, N. Lollike, and S. Malone. "Blockchain the gateway to trust-free cryptographic transactions" [in English]. In *Twenty-Fourth European Conference on Information Systems (ECIS), Istanbul, Turkey, 2016*, 1–14. Springer Publishing Company, Istanbul, 2016. https://www.tib.eu/en/search/id/TIBKAT%3A875848443/24th-European-Conference-on-Information-Systems/

[12] Buterin, V. *Ethereum: A Next-Generation Smart Contract and Decentralized Application Platform*. https://github.com/ethereum/wiki/wiki/White-Paper. Accessed: August 22, 2016, 2014.

[13] Croman, K., C. Decker, I. Eyal, A. E. Gencer, A. Juels, A. Kosba, A. Miller et al. "On scaling decentralized blockchains." *Financial Cryptography and Data Security* 9604 (February 2016): 106–125. doi:10.1007/978-3-662-53357-4_8.

[14] Aman, M. N., M. H. Basheer, and B. Sikdar. "Two-factor authentication for IoT with location information." *IEEE Internet of Things Journal* 6, no. 2 (April 2019): 3335–3351. ISSN: 2327-4662. doi:10.1109/JIOT.2018.2882610.

[15] Aman, M. N., K. C. Chua, and B. Sikdar. "Physical unclonable functions for IoT security." In *Proceedings of the 2nd ACM International Workshop on IoT Privacy, Trust, and Security*, 10–13. IoTPTS'16. Xi'an, China: ACM, 2016. ISBN: 978-1-4503-4283-4. doi:10.1145/2899007.2899013.

[16] Tosh, D., S. Shetty, X. Liang, C. Kamhoua, and L. L. Njilla. "Data provenance in the cloud: A blockchain-based approach." *IEEE Consumer Electronics Magazine* 8, no. 4 (July 2019): 38–44. ISSN: 2162-2248. doi:10.1109/MCE.2019.2892222.

[17] Rosenfeld, K., E. Gavas, and R. Karri. "Sensor physical unclonable functions" [in English (US)]. In *Proceedings of the 2010 IEEE International Symposium on Hardware-Oriented Security and Trust, HOST 2010*, 112–117. 2010. ISBN: 9781424478101. doi:10.1109/HST.2010.5513103.

[18] Guilley, S., and R. Pacalet. "SoCs security: A war against side-channels." *Annals of Telecommun*., 59, no. 7 (2004): 998–1009.

[19] Kirkpatrick, M., S. Kerr, and E. Bertino. System on chip and method for cryptography using a physically unclonable function. Patent US 8750502 B2 (US), filed issued March 22, 2012.

[20] Bohm, C., and M. Hofer. *Physical Unclonable Functions in Theory and Practice*. Springer-Verlag, New York, 2012. ISBN: 146145039X, 9781461450399. https://www.springer.com/gp/book/9781461450399

[21] Mao, W., and C. Boyd. "Towards formal analysis of security protocols." In *Proceedings Computer Security Foundations Workshop VI*, 147–158. June 1993. doi:10.1109/CSFW.1993.246631.

[22] Abadi, and Needham. "A logic of authentication." *ACM Transactions on Computer Systems*, no. 8 (February 1990): 18–36. doi:10.1145/77648.77649.

[23] Popov, S. "The tangle." 2015. https://www.iota.org/research/academic-papers

[^1]: https://www.iota.org

# Chapter 5: On blockchain and its complementarity with fog computing to secure management systems

**Chaima Khalfaoui, Samiha Ayed, and Moez Esseghir**

## Contents

- [5.1 Introduction](#16_Chapter05.xhtml#rsec5_1)
- [5.2 IoT context](#16_Chapter05.xhtml#rsec5_2)
- [5.3 Fog computing](#16_Chapter05.xhtml#rsec5_3)
  - [5.3.1 Fog computing strengths and weaknesses](#16_Chapter05.xhtml#rsec5_3_1)
- [5.4 Blockchains](#16_Chapter05.xhtml#rsec5_4)
  - [5.4.1 What is blockchain structure?](#16_Chapter05.xhtml#rsec5_4_1)
  - [5.4.2 How does blockchain work?](#16_Chapter05.xhtml#rsec5_4_2)
  - [5.4.3 What are blockchain key features?](#16_Chapter05.xhtml#rsec5_4_3)
  - [5.4.4 What are blockchain performance and security weaknesses?](#16_Chapter05.xhtml#rsec5_4_4)
  - [5.4.5 What is a smart contract?](#16_Chapter05.xhtml#rsec5_4_5)
- [5.5 Blockchain and fog complementarity](#16_Chapter05.xhtml#rsec5_5)
- [5.6 Proposition](#16_Chapter05.xhtml#rsec5_6)
- [5.7 Conclusion](#16_Chapter05.xhtml#rsec5_7)
- [References](#16_Chapter05.xhtml#rsec5_ref)

## 5.1 Introduction

The Internet of Things (`IoT`) allows billions of limited power devices to interconnect every day with the aim of enhancing data exchange and automating daily services. However, to manage these huge amounts of data, many security and performance challenges must be addressed. Such a challenge requires a solution with efficient decision making, short delays, and data protection. We propose an architecture based on blockchain technology with the use of fog computing to increase data security and user privacy with the shortest delays. The use of the fog computing paradigm allows the support of the high computing demand of `IoT` applications. Therefore, the security of this infrastructure is still an open issue mainly because of the lack of mechanisms able to secure information in such an untrustworthy environment. In this context, we propose the collaboration of blockchains with fogs to fill the security gap and ensure effective services. There are recent works [[1]](#16_Chapter05.xhtml#ref5_1), [[2]](#16_Chapter05.xhtml#ref5_2) that studied the use of fogs or blockchains separately to improve computing performances or security. However, privacy and security issues were not addressed for works associating both fogs and blockchains paradigms simultaneously. In this work, we propose the collaboration between blockchain technology and fog computing through a three-layer architecture aiming to exchange and manage data securely and effectively.

## 5.2 IoT Context

The `IoT` is "the network of physical objects, devices, vehicles, buildings and other items which are embedded with electronics, software, sensors, and network connectivity, permitting these objects to gather and interchange data" [[3]](#16_Chapter05.xhtml#ref5_3), [[4]](#16_Chapter05.xhtml#ref5_4), [[5]](#16_Chapter05.xhtml#ref5_5). There is no doubt that the `IoT` network is playing a major role in the everyday life of users through the development of a huge number of applications in different fields such as transportation, health care, and smart environments or assisted systems today. Thanks to `IoT`, it becomes possible to monitor your home and enterprise remotely and even to keep an ambient climate in your home through temperature sensors exchanging data with remote services. Real-time data sensing functions and automatic data collection and transfer are providing innumerable benefits to improve the quality of services.

Despite the benefits mentioned, `IoT` scenarios require specific architecture and measurements. More precisely, network and security issues have to be addressed. Let's start by identifying the main attributes of `IoT` devices:

- **Lack of security**: `IoT` devices are vulnerable to security threats because they have low energy and computation capabilities unable to support robust security algorithms.
- **Heterogeneity**: `IoT` devices deployed in a system are heterogeneous and based on multiple networks most of the time. Therefore, the key requirement is deploying an architecture that supports heterogeneous direct connectivity.
- **Huge continuous increase in number of devices**: It is predicted to be 18 billion devices by 2022 [[6]](#16_Chapter05.xhtml#ref5_6). A scalable platform needs to be designed to meet the requirements.
