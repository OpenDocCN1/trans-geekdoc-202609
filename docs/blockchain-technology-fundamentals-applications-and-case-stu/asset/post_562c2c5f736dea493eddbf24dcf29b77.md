
53. S. J. Russell, and N. Norvig. Artificial Intelligence: A Modern Approach. Pearson Education Limited, Kuala Lumpur 2016.

54. S. S. Gill, et al. “Transformative effects of IoT, Blockchain and Artificial Intelligence on cloud computing: Evolution, vision, trends and open challenges.” Internet of Things (2019): 100118.

55. A. A. Ali, and M. M. Alam. “SecOff-FCIIoT: Machine learning based secure offloading in Fog-Cloud of smart city applications.” Internet of Things 7 (2019): 100070.

56. A. Dawoud, S. Shahristani, and C. Raun. “Deep learning and software-defined networks: Towards secure IoT architecture.” Internet of Things 3–4, 2018.

57. S. Tuli, Basumary, and R. Buyya. “EdgeLens: Deep Learning Architecture in Integrated IoT, Fog and Cloud Computing Environments.” in: Proceedings of the 4th IEEE International Conference on Information Systems and Computer Networks (ISCON 2019, IEEE Press, Mathura, India, November 21–22, 2019.

58. K. K. Nguyen, D. T. Hoang, D. Niyati, P. Wang, D. Nguyen, and E. Kwiatkowski, “Cyberattack detection in mobile cloud computing: A deep learning approach.” in: 2018 IEEE Wireless Communications and Networking Conference (WCNC), IEEE, 2018, pp. 1–6.

59. A. Efshariat, A. Esmail, and M. Pedram. BottleNet: A Deep Learning Architecture for Intelligent Mobile Cloud Computing. arXiv preprint arXiv:1902.01000.

60. S. O. Asia, A. S. Shamsabadi, A. Taheri, K. Katevas, S. Sadmanesh, and H. R. Barrie, Lane analytics. arXiv preprint arXiv:1703.02952.

61. S. You, and H. An. “Software engineering meets services and cloud computing.” Computer 44 (10) (2011): 47–53.

62. T. Østerler, Cloud Computing: Impact on Software Engineering Research and Practice. Norwegian University of Science and Technology (NTNU), Trondheim, 2009.

63. I. Schelet Cloud Technology in the era of IoT, Blockchain, Machine Learning and AI, White paper, available at https://blog.userjournal.com/cloud-technology-in-the-era-of-iot-blockchain-and-chain.machine-learning-and-ai/f4a19476832, 2018.

64. S. Singh, and I. China. “QoS-aware resource management in cloud computing: A systematic review.” ACM Computing Surveys (CSUR) 48 (3) (2016): 42.

65. F. Bonomi, R. Milito, J. Zhu, and S. Addepali. “Fog computing and its role in the internet of things.” in: Proceedings of the first edition of the MCC workshop on Mobile computing, ACM, 2012, pp. 13–16.

66. A. A. Ali, and M. M. Alam. “SecOff-FCIIoT: Machine learning based secure offloading in Fog-Cloud of smart city applications.” Internet of Things 7 (2019): 100070.

67. A. Dawoud, S. Shahristani, and C. Raun. “Deep learning and software-defined networks: Towards secure IoT architecture.” Internet of Things 3–4 (2018): 82–89.

# 4 IoT and Blockchain

A. Mohana Priya, R. Malathi,
S. Hemalatha, and K. E. Kannamal
Department of Computer Science and Engineering,
Sri Shakthi Institute of Engineering and Technology

# CONTENTS

- 4.1 Introduction .......................................................................................... 44
- 4.1.1 IoT Architecture....................................................................... 45
- 4.1.2 Applications in IoT.................................................................................. 48
- 4.1.2.1 Wearable Gadgets...................................................................... 48
- 4.1.2.2 Smart Home Appliances............................................................................... 48
- 4.1.2.3 Smart City........................................................................................... 48
- 4.1.2.4 Amazon Go........................................................................................... 49
- 4.1.2.5 Smart Grids........................................................................................... 49
- 4.1.2.6 Smart Farming......................................................................................... 49
- 4.1.2.7 Smart Supply Chain.................................................................................. 49
- 4.2 Application Implementation.................................................................... 49
- 4.2.1 Garden Monitoring System and Controlling Pesticide Using IoT......................... 49
- 4.2.1.1 Sensors with Raspberry Pi........................................................................... 50
- 4.2.1.2 Block Diagram......................................................................... 51
- 4.2.1.3 Implementation........................................................................ 52
- 4.2.2 Implementation of Smart Home Automation using Arduino.................................. 55
- 4.3 Advantages of IoT.................................................................................. 57
- 4.4 Disadvantages of IoT................................................................................ 57
- 4.4.1 Complexity................................................................................ 57
- 4.4.2 Jobs................................................................................ 58
- 4.4.3 Compatibility................................................................................ 58
- 4.4.4 Privacy and Security................................................................................ 58
- 4.5 Industrial IoT................................................................................ 58
- 4.5.1 Industrial 4.0................................................................................ 58
- 4.6 How IIoT Works................................................................................ 59
- 4.7 Benefits of IoT................................................................................ 60
- 4.8 IIoT versus IoT................................................................................ 61
- 4.9 Vendors in IIoT................................................................................ 61
- 4.10 Enterprise and IIoT................................................................................ 62
- 4.10.1 Blockchain and IIoT............................................................... 62
- 4.10.2 Economy................................................................................ 63
- 4.10.3 Speed................................................................................ 63
- 4.10.4 Identity and Access Management ............................................... 64
- 4.10.5 Resilient and Reliable Transaction.................................................. 64
- 4.10.6 Security ................................................................. 64
- 4.11 Challenges of Blockchain IoT...................................................... 66
- 4.12 Discussion on Appropriate Use Cases......................................................... 67
- 4.12.1 Shared Economy.................................................................. 67
- 4.12.2 Supply Chain Management....................................................................... 68
- 4.12.3 Smart City Applications............................................................................. 69
- 4.12.4 Blockchain IoT Architecture.................................................... 69
- 4.12.5 Network Layer..................................................................... 70
- 4.12.6 Distributed Ledger Technologies (DLT)................................................ 70
- 4.12.7 Data Models................................................................................ 72
- 4.12.8 Processes................................................................................ 72
- 4.12.9 Services............................................................................. 72
- 4.12.10 A Decentralized Application (DApp, dApp, or dapp)........................ 72
- 4.12.11 Physical-Cyber Security Layer....................................................... 72
- 4.13 Summary......................................................................... 72
- References ................................................................72

## 4.1 Introduction

Though Internet of Things (IoT) and blockchain are emerging in their own way, the convergence of these two technologies will help leverage each other. The analytical capability of IoT had paved new paths in many enterprise applications, it has also led to serious security issues. Blockchain has proved itself to be a strong and secure technology with the success of bitcoins. IDC states that 20% of all IoT deployments will enable blockchain-based solutions by 2019.

This chapter focuses on the following topics:

- How IoT works?
- What are the issues in IoT?
- What are some of the related technologies of IoT?
- How blockchain can help overcome the some of the issues in IoT?
- What are the design considerations to be kept in mind while designing the distributed ledger-based IoT architecture?

The recent trends in computing technologies have brought much more changes in the fields and made effortless usability with hidden technical exertions. IoT is one of the emerging platforms where the things communicate with each other without or with less human intervention. It makes things (embedded, nonphone devices) [1,2] smart with the presence of Internet; it mainly makes use of sensors, actuators, wireless
