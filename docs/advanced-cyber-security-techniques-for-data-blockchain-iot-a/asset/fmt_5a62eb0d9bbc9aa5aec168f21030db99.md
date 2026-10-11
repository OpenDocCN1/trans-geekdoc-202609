
#### Table 9. Overall Comparison between Training and Testing data

| Malicious | | Training | | Testing |
| --- | --- | --- | --- | --- |
| Model/Classifier | | Error Rate | Accuracy | Error Rate | Accuracy |
| NB | | 0.25 | 0.7519 | 0.24 | 0.7566 |
| Log | | 0.07 | 0.9301 | 0.06 | 0.9421 |
| KNN | | 0.15 | 0.8532 | 0.2 | 0.7962 |
| DT | | 0.000 | 1.000 | 0.011 | 0.9888 |
| RF | | 0.000 | 1.000 | 0.005 | 0.9947 |
| Benign | | Training | | Testing |
| Model/Classifier | | Error Rate | Accuracy | Error Rate | Accuracy |
| NB | | 0.08 | 0.9169 | 0.08 | 0.9178 |
| Log | | 0.18 | 0.8244 | 0.19 | 0.8128 |
| KNN | | 0.21 | 0.7904 | 0.33 | 0.6667 |
| DT | | 0.000 | 1.000 | 0.019 | 0.9810 |
| RF | | 0.000 | 1.000 | 0.008 | 0.9916 |

A detailed comparison of all models and classifiers in the training and testing parts of the dataset is detailed in [Table 9](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor262) and [Figure 8](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor263). Importantly, the proposed method using random forest (`RF`) classifier provides consistently better results compared to other models in all aspects of various statistical analysis. The superior `RF` is highlighted in accuracy, precision, recall and F1-score. It can be clearly seen that during the training time, `RF` provides a 0% error rate and 100% accuracy in both categories, malicious and benign. During the testing time, it is noted that `RF` provides 99.47% and 99.16% overall accuracy and 0.5% and 0.8% error rate in both categories, malicious and benign, respectively. Furthermore, in order to provide a general approach, the proposed method is combined with existing methods, as described in [Table 10](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor264). This comparison shows its superior performance over methods of the past, emphasizing `RF` power. In particular, `RF` exhibits high precision, recall, and F1 scores, thus confirming its effectiveness in PDF-based malware detection.

#### Figure 8. Overall Comparison between Training and Testing data

![979-8-3693-9225-6.ch010.f08](image/979-8-3693-9225-6.ch010.f08.png)

#### Table 10. Proposed Method vs Existing Methods

| Research | | Accuracy | Precision | Recall | F1-score |
| --- | --- | --- | --- | --- | --- |
| [Issakhani et al. (2022)](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor272) | | 0.9884 | 0.988 | 0.989 | 0.9885 |
| [Al-Haija et al. (2022)](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor265) | | 0.9884 | 0.988 | 0.989 | 0.988 |
| Lakshmanan Nataraj et al. (2021) | | 0.9593 | | | |
| [Li et al. (2019)](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor274) | | 0.9511 | 0.9757 | 0.9087 | 0.9410 |
| [Mohammed et al. (2021)](#979-8-3693-9225-6.ch010.bits-pdf.xhtml#_idTextAnchor280) | | 0.8956 | | | |
| Proposed [`RF`] | | 0.9930 | 0.9900 | 0.9900 | 0.9900 |

### 5. CONCLUSION

This chapter presents a comprehensive analysis of the protective creation of PDF-based malware using intelligent search. The chapter provides a valuable comparative analysis of different PDF-based malware detectors, highlighting their performance, capabilities, and ethical considerations, and also serves as a practical guide for practitioners and researchers. It covers emerging trends such as the integration of machine learning and automation, as well as the development of advanced detection techniques. This chapter proposes a novel method that has the capability to detect malware with an accuracy rate of 99.30%. The proposed method also delivers its best outcomes compared to existing methods in terms of precision, recall, and F1-score. This indicates a system that could have the potential to diagnose PDF-based malignancies according to their impact. The proposed method is also able to achieve a lower error rate compared to others. In the future, deep learning-based models and new datasets may be explored to achieve more robust results.

### REFERENCES

Al-Haija, . (2022). PDF malware detection based on Optimizable Decision trees. Electronics (Basel), 11(19), 3142. DOI: [10.3390/electronics11193142](http://dx.doi.org/10.3390/electronics11193142)

Bilal Sowan et al., (2024). PDF Malware Detection: A Hybrid Approach Using Random Forest and K-Nearest Neighbors. DOI: [10.1109/ICCR61006.2024.10533046](http://dx.doi.org/10.1109/ICCR61006.2024.10533046)

Binsawad, M. (2024). Enhancing PDF Malware Detection through Logistic Model Trees. Computers, Materials & Continua/Computers. Computers, Materials & Continua, 0(0), 1–10. DOI: [10.32604/cmc.2024.048183](http://dx.doi.org/10.32604/cmc.2024.048183)

Chaubey, N. K., & Prajapati, B. B. (2020). Quantum Cryptography and the Future of Cyber Security. (2020). In Advances in information security, privacy, and ethics book series. IGI Global., DOI: [10.4018/978-1-7998-2253-0](http://dx.doi.org/10.4018/978-1-7998-2253-0)

CIC-Evasive-PDFMal2022 | Datasets | Canadian Institute for Cybersecurity | UNB. (n.d.). [https://www.unb.ca/cic/datasets/pdfmal-2022.html](https://www.unb.ca/cic/datasets/pdfmal-2022.html)

Elingiusti., . . .. (2018). PDF-malware detection: a survey and taxonomy of current techniques. [https://iris.uniroma1.it/retrieve/e383531c-a499-15e8-e053-a505fe0a3de9/Elingiusti_Postprint_PDF-Malware-Detection_2018.pdf](https://iris.uniroma1.it/retrieve/e383531c-a499-15e8-e053-a505fe0a3de9/Elingiusti_Postprint_PDF-Malware-Detection_2018.pdf)

Endignoux, G. (2016). Introduction to PDF syntax | Blog | Guillaume Endignoux. [https://gendignoux.com/blog/2016/10/04/pdf-basics.html](https://gendignoux.com/blog/2016/10/04/pdf-basics.html)

Falah, , Pan, L., Huda, S., Pokhrel, S. R., & Anwar, A. (2020). Improving malicious PDF classifier with feature engineering: A data-driven approach. Future Generation Computer Systems, 115, 314–326. DOI: [10.1016/j.future.2020.09.015](http://dx.doi.org/10.1016/j.future.2020.09.015)

He, , Zhu, Y., He, Y., Liu, L., Lu, B., & Lin, W. (2020). Detection of Malicious PDF Files Using a Two-Stage Machine Learning Algorithm. Chinese Journal of Electronics, 29(6), 1165–1177. DOI: [10.1049/cje.2020.10.002](http://dx.doi.org/10.1049/cje.2020.10.002)

Introduction to Decision Tree. (2020). Capable Machine; Capable Machine. [https://capablemachine.wordpress.com/2020/05/05/decision-tree-2/](https://capablemachine.wordpress.com/2020/05/05/decision-tree-2/)

Issakhani, . (2022). PDF Malware Detection based on Stacking Learning. Proceedings of the 8th International Conference on Information Systems Security and Privacy. DOI: [10.5220/0010908400003120](http://dx.doi.org/10.5220/0010908400003120)

Issakhani, . (2022). PDF Malware Detection based on Stacking Learning. Proceedings of the 8th International Conference on Information Systems Security and Privacy. DOI: [10.5220/0010908400003120](http://dx.doi.org/10.5220/0010908400003120)

Jani, K. A., & Nirbhay Chaubey. (2020). IoT and Cyber Security. IGI Global EBooks, 203–235. https://doi.org/DOI: [10.4018/978-1-7998-2253-0.ch010](http://dx.doi.org/10.4018/978-1-7998-2253-0.ch010)

Jiang, , Song, N., Yu, M., Chow, K.-P., Li, G., Liu, C., & Huang, W. (2021). DETECTING MALICIOUS PDF DOCUMENTS USING SEMI-SUPERVISED MACHINE LEARNING. IFIP Advances in Information and Communication Technology, 612, 135–155. DOI: [10.1007/978-3-030-88381-2_7](http://dx.doi.org/10.1007/978-3-030-88381-2_7)

Lakshmanan Nataraj et al. (2021). OMD: Orthogonal Malware Detection Using Audio, Image, and Static Features. ArXiv (Cornell University). https://doi.org//arxiv.2111.04710 DOI: [10.48550](http://dx.doi.org/10.48550)

Li, . (2019). Research on KNN Algorithm in Malicious PDF Files Classification under Adversarial Environment. Proceedings of the 2019 4th International Conference on Big Data and Computing - ICBDC 2019. DOI: [10.1145/3335484.3335527](http://dx.doi.org/10.1145/3335484.3335527)
