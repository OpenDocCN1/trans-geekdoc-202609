
29. J. Gu, B. Sun, X. Du, J. Wang, Y. Zhuang et al., “Consortium blockchain-based malware detection in mobile devices,” IEEE Access, vol. 6, pp. 12118–12128, 2018.

30. P. Fairley, “Blockchain word-feeding the blockchain beast if bitcoin ever does livestream, the electricity needed to sustain it is enormous,” IEEE Spectrum, vol. 54, no. 10, pp. 36–39, 2017.

31. T. B. Baker, R. F. Silva, V. D. Calhoun, A. Sarvate and S. M. Plis, “Large scale collaboration with autonomy: Decentralized data CA,” in 2015 25th Workshop on Machine Learning for Signal Processing (MLSP), Boston, MA, 2015, pp. 1–6, doi: 10.1109/MLSP.2015.7324344.

32. M. Peck, “Blockchain-do you need blockchain? This chart will tell you if the technology can solve your problem,” IEEE Spectrum, vol. 54, no. 10, pp. 38–60.

33. K. Xie, W. Luo, Wang. D. Xie, J. Cao et al., “Decentralized context sharing in vehicular udelay relay networks with compressive sensing,” 2016 IEEE International Conference on Distributed Computing Systems (ICDCS), Nara, Japan, pp. 169–178, 2016.

34. K. Kotobi and S. G. Billion, “Secure blockchains for dynamic spectrum access: A decentralized database in moving cognitive radio enhances network security and user access,” IEEE Technology Magazine, vol. 13, no. 1, pp. 32–39, 2020.

35. C. Vaidya, P. Khobagade, and A. Golgate, “Gate detection and security in cloud computing,” GR Journals Global Research Development for Engineering, vol. 1, no. 12, pp. 137–140, 2021.

36. Z. Wang, Y. Tian, and J. Zhu, “Data sharing and tracing scheme on blockchain,” in 2018 International Conference on Logistics, Informatics and Service Sciences (LISS), Toronto, ON, Canada, 2018, pp. 1–6, doi: 10.1109/LISS.2018.8593225.

37. A. Dorri, M. Steeger, S. Kaneher and R. Rudak, “A distributed solution for automotive security and privacy,” IEEE Communications, vol. 55, pp. 119–125, 2017.

38. K. Kotobi and S. G. Billion, “Blockchain-enabled spectrum access in cognitive radio networks,” in 2017 Wireless Telecommunications Symposium (WTS), Chicago, IL, USA, 2017, pp. 1–6, doi: 10.1109/WTS.2017.7943523.

39. P. Khobagade, L. G. Malik, “A review on data for digital forensic investigation damning,” ICAT International Journal of Computing and Technology, vol. 1, no. 3, pp. 372–375, 2021.

40. D. R. Dandekar and P. R. Deshmukh, “Energy balancing in multi-hop wireless sensor networks,” in 2013 3rd IEEE International Advanced Computing Conference (IAC), pp. 408–412, IEEE, 2013.

41. T. K. Jain, D. S. Saini, and S. V. Bhoosh, “Increasing lifetime of a wireless sensor network usinging,” in 2014 International Conference on Information Technology: New Generations, pp. 616–619, IEEE, 2014.

42. Z. Cui, X. E. Fei, S. Zhang, C. Cai, W. Wang, and J. Chen, “A hybrid blockchain-based identity authentication scheme for multi-WSN,” IEEE Transactions on Services Computing, vol. 13, no. 2, pp. 241–251, 2020.

43. Z. Noshad, A. Javed, M. Zahid, I. Ali, and N. Javed, “Node recovery in wireless networks via blockchain,” in International Conference on P2P, Parallel, Grid and Internet Computing, pp. 94–105, Springer, Cham, 2019.

44. A. Mateen
45. N. Islam, Towards a Secure and Efficient Wireless Sensor Network using Blockchain and a Novel Clustering Approach, 2018.

46. D. P. Abreu, K. Velasquez, M. Curado, and E. Monteiro, “A resilient internet of things architecture for smart cities,” Annals of Telecommunications, vol. 72, no. 1–2, pp. 19–39, 2017.

47. I. D. Buldin, M. G. Gorodichev, S. S. Makhrov, and E. N. Denisova, “Next generation industrial blockchain-based wireless sensor networks,” in 2018 Wave Electronics and Its Application in Information and Telecommunication Systems (WECONF), pp. 1–5. IEEE, 2018.

48. M. A. Ferrag, M. Derdour, M. Mukherjee, A. Derhab, L. Maglaras and H. Janicke, “Blockchain Technologies for the Internet of Things: Research Issues and Challenges,” IEEE Internet of Things Journal, vol. 6, no. 2, pp. 2188–2204, 2019, doi: 10.1109/JIOT.2018.2882794.

49. M. A. Ferrag, L. Maglaras, and A. Rahim, “Privacy-preserving schemes for ad hoc social networks: A survey,” IEEE Communications Surveys & Tutorials, vol. 19, no. 4, pp. 3015–3045, 2017.

# 14 Privacy-Preserving Machine Learning on Non-Co-Located Datasets Using Federated Learning Challenges and Opportunities

Jyoti L. Bangare, Niles P. Sable, Parikshit N. Mahalle, and Gitanjali Shinde

In the age of big data and distributed computing, it is becoming more common to find datasets that are not physically located in the same location. Since these datasets are spread across several locations (i.e. they are non-co-located) and are hosted by diverse organizations, combining and analyzing them presents a variety of difficulties. Recent developments in ML methods, particularly federated learning, provide interesting options for overcoming these difficulties while preserving the confidentiality and privacy of the data [1, 2].

Datasets that are hosted by multiple companies or situated across the globe are considered non-co-located datasets. Information obtained from various sources, such as sensors, mobile devices, and web sources, may be included in this. The quantity of information included in the non-co-located datasets may be useful for applications in the fields of healthcare, finance, transportation, and many others. However, datasets are harder to combine and interpret because of their scattered nature [3].

Integrating and analyzing datasets that are not physically located together presents a number of issues. A key difficulty is data heterogeneity, or variances in datasets. Data ownership and access rights can be complex, needing cooperation from stakeholders [4].

## 14.1.3 THE MACHINE LEARNING APPROACHES FOR PRIVACY PRESERVATION IN IOT

Due to the sensitive and private data that IoT devices acquire, privacy preservation is crucial in the Internet of Things (IoT). The privacy issues in IoT are largely addressed by machine learning (ML) techniques, as shown in Figure 14.1. Here are some typical techniques for protecting privacy:

- Federated learning: IoT devices can train cooperatively without transferring raw data. Instead, individual devices train locally, and only model changes are sent to an aggregator. By ensuring that the data stays on the device, this method preserves privacy.
- Differential privacy: This is a technology that ensures privacy by introducing noise to the data prior to training. Due to this, it is difficult to distinguish individual data points while still enabling model training.
- Homomorphic encryption: Calculations can be made on encrypted data without having to first decrypt it. This method enables the training of ML models using encrypted data in IoT. The model is trained on the encrypted data, which is then transmitted back to the IoT devices after being educated on a central server.
- Secure multi-party computation (SMPC): SMPC is a cryptographic method that permits several workers to work to compute a result without disclosing their individual inputs. ML operations on encrypted data can be carried out using SMPC in the context of IoT. Without disclosing the underlying data, each IoT device encrypts its own data and works together to compute the model changes.
- Secure aggregation: When combining data or model updates from many IoT devices, secure aggregation solutions work to protect user privacy. These methods aggregate the data or model changes while protecting user privacy using cryptographic mechanisms.

![14.1 Machine learning approaches for privacy in IoT](img/a29e06af76c776aadcc01782d63c0d5_339.png)

## 14.1.4 OVERVIEW OF FEDERATED LEARNING

Recent advances in federated learning eliminate the requirement for centralized data storage by enabling many users to cooperatively train models on various data sources [5], as shown in Figure 14.2. Participants can avoid providing raw data to a centralized server by locally training their own models.
