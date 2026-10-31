
CCTV cameras, CDs, or any other kind of electronic devices are presented in front of a court if they are compatible enough to prove the crime or defend the innocent person. Also, 65B(4) says that this evidence can only be presented by an expert who has enough training, knowledge, and experience in the required field, which was decided by a bench of U Lalit and Justice AK Goel.

## KEYWORDS

- **android data**
- **digital forensics**
- **iPhone data**
- **malicious programs**
- **mobile devices**
- **mobile forensics**
- **operating system**
- **test access ports**

## REFERENCES

Agar, J., (2003). Constant Touch: A Global History of the Mobile Phone. Cambridge: Icon Books, 172 pp., 20 illus., cloth $20, ISBN 1-84046-419-4.
Al-Mutawa, N., Baggili, I., & Marrington, A., (2012). Forensic analysis of social networking applications on mobile devices. Digital Investigation, 9, S24–S33.
Ayers, R., Jansen, W., Moenner, L., & Delaître, A., (2007). Cell Phone Forensic Tools: An Overview and Analysis Update. NISTIR 7387.
Bates, J., (1998). Fundamentals of Computer Forensics. Information Security Technical Report, Elsevier.
Bharati, W., Ramith, N., & Amala, N., (2015). Mobile Operating System: Analysis and Comparison of Android AND IOS. ISSN: 2348 - 6090.
Brown, L. D., Hua, H., & Gao, C., (2003). A widget framework for augmented interaction in scape. In Proceedings of the 16th Annual ACM Symposium on User Interface Software and Technology (UIST ’03). Association for Computing Machinery, New York, NY, USA, 1–10.
Carrier, B., (2001). Performing an autopsy examination on FFS and EXT2FS partition images: An introduction to TCTUTILs and the autopsy forensic browser. Proc. SANSFIRE 2001 Conference.
Casey, E., (2010). Handbook of Digital Forensics and Investigation. Academic Press.
Conder, S., & Darcey, L., (2009). Android Wireless Application Development. Addison Wesley.
Dasari, M. S., Nandagiri, R. G. K. P., & Satish, D., (2015). The Forensic Process Analysis of Mobile Device. 6(5), 4847-4850.
Forman, G., (2003). An extensive empirical study of feature selection metrics for text classification. J. Mach. Learn. Res., 3, 1289-1305.
Garber, L., (2001). Computer forensics: High-tech law enforcement. IEEE Computer, 34(1), 202-205.
Garfinkel, S., (2010). Digital forensics research: The next 10 years. Digital Investigation, 7, S64-S73.
Garner, (2011). Sales of mobile Devices in Second Quarter of 2011 Grew 16.5 Percent Year-on-Year; Smartphone Sales Grew 74%. Gartner, Inc.
Halderman, J., Schoen, S., Heninger, A., & Felten, E., (2008). Lest we remember - cold boot attacks on encryption keys. Proc. 17th USENIX Security Symposium.
Jansen, W., & Ayers, R., (2007). Guidelines on Cell Phone Forensics. Recommendations of the National Institute of Standards and Technology.
Kostadinov, D. (2019). The Mobile Forensics Process: Steps and Types. Infosec Resources, (n.d.). https://resources.infosecinstitute.com/topic/mobile-forensics-process-steps-types/ (accessed January 30, 2023).
Park, J., Chung, H., & Lee, S., (2012). Forensic analysis techniques for fragmented flash memory pages in smartphone. Digital Investigation, 9(2), 109-118.
Raghav, S., & Saxena, A. K., (2009). Mobile forensics: Guidelines and challenges in data preservation and acquisition. IEEE Student Conference on Research and Development (pp. 5-8). Malaysia.
Sannella, M. J., (1994). Constraint Satisfaction and Debugging for Interactive User Interfaces. Doctoral Thesis. UMI Order Number: UMI Order No. GAX95- 09398. University of Washington.
Sathe, S. C., & Dongre, N., M., (2018). IEEE 2018 2nd International Conference on Inventive Systems and Control (ICISC)-Coimbatore, India (2018.1.19-2018.1.20). 2018 2nd International Conference on Inventive Systems and Control (ICISC)-Data Acquisition Techniques in Mobile Forensics.
Sengul, D., & Erhan, A., (2017). Analysis of Mobile Phones in Digital Forensics. MIPRO, Opatija, Croatia.
Spector, A. Z., (1989). Achieving application requirements. In: Mullender, S., (ed.), Distributed Systems.
Yates, I. I., (2010). Practical investigations of digital forensics tools for mobile devices. In: 2010 Information Security Curriculum Development Conference. ACM.
Yu, Y. T., & Lau, M. F., (2005). A comparison of MC/DC, MUMCUT and several other coverage criteria for logical decisions. Journal of Systems and Software. (in press).
Zareen, & Baig, S., (2010). Mobile phone forensics challenges, analysis and tools classification. Fifth International Workshop on Systematic Approaches to Digital Forensic Engineering (SADFE.2010) (pp. 47-55).

## CHAPTER 12

## Analysis of Tree-Based Machine Learning Techniques for Credit Card Fraud Detection

JITENDER TANWAR,¹ SHUBHAM SINGH,² AKASH KUMAR,²
MANDEEP MITTAL,⁴ LEENA SINGH,² and SUDHANSHU TRIPATHI³

¹Amity Institute of Information Technology, Amity University, Noida, Uttar Pradesh, India

²Amity School of Engineering and Technology, Amity University, Noida, Uttar Pradesh, India

³Amity University in Tashkent, Labzak Tashkent City, Uzbekistan

⁴Department of Mathematics, Amity Institute of Applied Sciences, Amity University, Noida, Uttar Pradesh, India

## ABSTRACT

A credit card is an easy and most beneficial target for hackers. On the other hand, it is a huge threat to the financial industry. Thousands of people suffer great losses from this problem every year. Although it is not an easy problem, machine learning (ML) has given us hope and played an important role in the fraud detection of online transactions. Online fraud detection is facing difficulties like having unbalanced data, not having confidential data, non-availability of analyzed data, etc. The processed and analyzed data can significantly improve the performance of ML algorithms. In this chapter, we analyzed and compared the performance of Random Forest, AdaBoost Classifier, XGBoost Classifier and finally ensembled them to get better results.

We have evaluated their performances based on their Matthews correlation coefficient (CC) score, AUC-ROC score, and their confusion matrix. The result analysis shows the order of importance of features for selected ML algorithms. The results indicate that the Random Forest has the best score in both the evaluation metrics which comes out to be 0.9981.

### 12.1 INTRODUCTION

Fraud in credit card transactions is the usage of an account by an unauthorized user or some fraudster (Sahin, 2013). It is a criminal activity that brings serious consequences to financial industries. To avoid fraud activities there are two measures: fraud detection and prevention. Fraud prevention means anticipating and stopping the fraud before it happens. Fraud detection means detecting the fraud and stopping it if the fraud is attempted.

The world is filled with companies, clients, and fraudsters. Whenever a client suffers a fraud, the company must also suffer both financially and reputation-wise (Awoyemi, 2017). To provide quality service to customers, companies keep on hiring new schemes. They use data analysts to understand their customers. They use techniques to detect and prevent fraud and machine learning (ML) is one of the solutions. Using different ML techniques, we can identify fraudulent transactions and avert them from happening (Pozzolo, 2018). As e-commerce is rising the credit card transactions are also rising rapidly (Srivastava, 2008). This rise has made a serious impact on financial industries. The number of credit card users in 2019 in India was around 47 million and rise to 52 million in 2020. Numerous authorization techniques are not much effective in credit card fraud cases. Fraudsters use the internet to hide their identity and location. The global credit card fraud in 2018 reached 24.26 billion USD (Nilson Report, 2018).

In this chapter, the ML techniques are utilized for identifying frauds in credit card transactions, i.e., Random Forest, AdaBoost Classifier, and XGBoost Classifier. The real datasets are occupied from Kaggle, and it is generated by a python simulator PaySim through automation. The dataset has further divided into train, validation, and test datasets. The algorithms are trained over the testing data set, then validated through the validation dataset, and finally tested through the testing dataset. For the assessment of the models, evaluation metrics AUC-ROC and MCC (Matthew’s correlation coefficient) have been used, and a comparison has been made between them.
