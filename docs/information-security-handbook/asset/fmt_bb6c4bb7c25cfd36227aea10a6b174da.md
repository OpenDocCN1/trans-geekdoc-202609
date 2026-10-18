
We need to calculate the accuracy and precision differences between the old system and the one we newly developed. Then we are going to make a code for implementing adversarial attacks on the fabricated system. In the testing phase, a particular sample is classified as a malevolent or a benign one based on its internal structure. But for making the classifier misclassify that particular sample set during the adversarial testing, we need to implement something that would be able to inject fabricated code into the file according to the nature of the file, so that during the adversarial attack, a benign PDF file should be classified as a malicious one, and, in the same way, a malicious PDF file should be classified as a benign one ([Figure 7.16](#ch07.xhtml#fig7_16)).

![Figure 7.16 Implementing adversarial attacks during the testing phase.](Images/fig7_16.jpg)

[Figure 7.16 Implementing adversarial attacks during the testing phase.](#ch07.xhtml#Ffig7_16)

In our system, we have used different modules for training the system, extracting the features from the files while the system is getting trained, ETS (educational testing service) module, and the testing module, which can classify the given file with greater accuracy based on its extracted features.

In this thesis work, we will be fabricating an adversarial code to implement the adversarial attack on the dynamic PDF classifier system, which, in turn, would be successfully able to evade the system and make it misclassify the sample nature ([Figure 7.17](#ch07.xhtml#fig7_17)).

![Figure 7.17 Testing procedure.](Images/fig7_17.jpg)

[Figure 7.17 Testing procedure.](#ch07.xhtml#Ffig7_17)

The above figure shows the main strategy we have implemented to classify the PDF file during the testing phase. It takes the references from the ETS generated during the testing procedure once the file is provided to the system. It extracts all the features from the given PDF file and tries to make the decision by taking references from the file. We need to further design a code that can make the file act as an adversarial sample to evade the classifier. This requires focusing on a uniform code that can make the required changes to the sample under inspection for making it evade the system.

## [7.13 Conclusions and Future Directions](#ch07.xhtml#c_sec7_13)

In this paper, we overviewed the various kinds of learning-based PDF malware classifiers. Fundamentally, the PDF classifiers are of two kinds, specifically, static and dynamic classifiers. The static classifiers distinguish the indications of malwares by parsing through the entire archive. While the dynamic classifiers run the record in imitated conditions to review the practices of the document during the execution. The greater part of the dynamic classifiers fundamentally center around the JavaScript code in the record as the lion's share of the malignant examples have JavaScript content inserted into them. From the outset, we have introduced the design of the PDF documents and how they are parsed utilizing a parsing programming. Following that, we talked about the designs of various static and dynamic classifiers. At that point, we led a near examination on the reviewed models. The features, grouping system, true positive (TP) rate, false positive (FP) rate, and F1 score were looked at among the changed classifiers.

We can also create more obfuscated adversarial PDF samples by embedding the malicious image file inside a PDF file object inside of the body part. The image object can be removed from the cross-reference table so that the object will not be seen by the classifier, even at the dynamic runtime inspection process. The classifier needs to be strengthened with more advanced techniques to read even the most obfuscated part for correctly classifying these kinds of variants. Hybrid classification systems would be recommended for these samples, but the time constraint should be taken care of side by side.

## [References](#ch07.xhtml#c_chapter7_RL_1)

1.  [Lu, X.](#ch07.xhtml#Cref7_1), Zhuge, J., Wang, R., Cao, Y., & Chen, Y. (2013). De-obfuscation and detection of malicious PDF files with high accuracy. Proceedings of the Annual Hawaii International Conference on System Sciences, 4890–4899. [10.1109/HICSS.2013.166](http://doi.org/10.1109/HICSS.2013.166).

2.  [Almrezeq, N.](#ch07.xhtml#Cref7_2) (2021). Cyber security attacks and challenges in Saudi Arabia during COVID-19. Turkish Journal of Computer and Mathematics Education (TURCOMAT), *12*(10), 2982–2991.

3.  [Rani, P.](#ch07.xhtml#Cref7_3), Kavita, Verma, S., & Nguyena, N. G. (2020). Mitigation of black hole and gray hole attack using swarm inspired algorithm with artificial neural network. IEEE Access, *8*. [10.1109/ACCESS.2020.3004692](http://doi.org/10.1109/ACCESS.2020.3004692).

4.  [Zhang, J.](#ch07.xhtml#Cref7_4) (2018). MLPdf: An effective machine learning-based approach for PDF malware detection. *arXiv*, 1–6. Retrieved from [http://arxiv.org/abs/1808.06991](http://arxiv.org).

5.  [Kang, A. R.](#ch07.xhtml#Cref7_5), Jeong, Y. S., Kim, S. L., & Woo, J. (2019). Malicious PDF detection model against adversarial attack built from benign PDF containing javascript. Applied Sciences (Switzerland), *9*(22). [10.3390/app9224764](http://doi.org/10.3390/app9224764).

6.  [Lin, Y. C.](#ch07.xhtml#Cref7_6), Hong, Z. W., Liao, Y. H., Shih, M. L., Liu, M. Y., & Sun, M. (2017). Tactics of adversarial attack on deep reinforcement learning agents. Proceedings of the IJCAI International Joint Conference on Artificial Intelligence, 3756–3762. [10.24963/ijcai.2017/525](http://doi.org/10.24963/ijcai.2017/525).

7.  [Biggio, B.](#ch07.xhtml#Cref7_7), & Roli, F. (2018). Wild patterns: Ten years after the rise of adversarial machine learning. Pattern Recognition, *84*, 317–331. [10.1016/j.patcog.2018.07.023](http://doi.org/10.1016/j.patcog.2018.07.023).

8.  [Almadhoor, L.](#ch07.xhtml#Cref7_8) (2021). Social media and cybercrimes. Turkish Journal of Computer and Mathematics Education (TURCOMAT), *12*(10), 2972–2981.

9.  [Srndic, N.](#ch07.xhtml#Cref7_9), & Laskov, P. (2013). Detection of malicious PDF files based on hierarchical document structure. Proceedings of the 20th Annual Network & Distributed Systems Symposium. Retrieved from [http://scholar.google.com/scholar?hl=en&btnG=Search&q=intitle:Detection+of+Malicious+PDF+Files+Based+on+Hierarchical+Document+Structure#0](http://scholar.google.com).

10.  [Schmitt, F.](#ch07.xhtml#Cref7_10), Gassen, J., & Gerhards-Padilla, E. (2012). PDF scrutinizer: Detecting JavaScript-based attacks in PDF documents. Proceedings of the 2012 10th Annual International Conference on Privacy, Security and Trust, PST 2012, 104–111. [10.1109/PST.2012.6297926](http://doi.org/10.1109/PST.2012.6297926).

11.  [Batra, I.](#ch07.xhtml#Cref7_11), Verma, S., Kavita, Ghosh, U., Rodrigues, J. J. P. C., Nguyen, G. N., Sanwar Hosen, A. S. M., & Mariappan, V. (2020). Hybrid logical security framework for privacy preservation in the green Internet of Things. MDPI-Sustainability, *12*(14), 5542. [10.3390/su12145542](http://doi.org/10.3390/su12145542).

12.  [Nissim](#ch07.xhtml#Cref7_12), N., Cohen, A., Moskovitch, R., Shabtai, A., Edri, M., BarAd, O., & Elovici, Y. (2016). Keeping pace with the creation of new malicious PDF files using an active-learning based detection framework. Security Informatics, *5*(1), 1–20. [10.1186/s13388-016-0026-3](http://doi.org/10.1186/s13388-016-0026-3).
