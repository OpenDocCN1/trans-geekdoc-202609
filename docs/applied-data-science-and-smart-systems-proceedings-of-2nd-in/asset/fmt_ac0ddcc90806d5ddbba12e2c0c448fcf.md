
*   [Lalkhen, A. G. and McCluskey, A.](#ch36.xhtml#R_ref36_45) (2008). Clinical tests: sensitivity and specificity. Cont. Educ. Anaes. Crit. Care Pain, 8(6), 221–223.

*   [Van S., Karlijn J., Stel, V. S., Reitsma, J. B., Dekker, F. W., Zoccali, C., and Jager, K. J.](#ch36.xhtml#R_ref36_46) (2009). Diagnostic methods I: Sensitivity, specificity, and other measures of accuracy. Kidney Int., 75(12), 1257–1263.

*   [Csurka, G., Larlus, D., Perronnin, F., and Meylan, F.](#ch36.xhtml#R_ref36_47) (2013). What is a good evaluation measure for semantic segmentation? Bmvc, 27, 10–5244.

*   [Wong, H. B. and Lim, G. H.](#ch36.xhtml#R_ref36_48) (2011). Measures of diagnostic accuracy: Sensitivity, specificity, PPV and NPV. Proc. Singapore Healthcare, 20(4), 316–318.

*   [Xu, Y., Wang, Y., Yuan, J., Cheng, Q., Wang, X., and Carson, P. L.](#ch36.xhtml#R_ref36_49) (2019). Medical breast ultrasound image segmentation by machine learning. Ultrasonics, 91, 1–9.

*   [Badea, M.-S., Felea, I.-I., Florea, L. M., and Vertan, C.](#ch36.xhtml#R_ref36_50) (2016). The use of deep learning in image segmentation, classification and detection. arXiv preprint arXiv:1605.09612.

*   Kaur, Jaspreet, and Alka Jindal. (2012). Comparison of thyroid segmentation algorithms in ultrasound and scintigraphy images. International Journal of Computer Applications. 50(23), 1–4.

*   [Poudel, Prabal, Alfredo Illanes, Debdoot Sheet, and Michael Friebe](#ch36.xhtml#R_ref36_52). (2018). Evaluation of commonly used algorithms for thyroid ultrasound images segmentation and improvement using machine learning approaches. Journal of healthcare engineering. 2018. doi: [https://doi.org/10.1155/2018/8087624](https://doi.org/10.1155/2018/8087624), 1–14.

*   Shenoy, N. R. and Jatti, A. (2021). Ultrasound image segmentation through deep learning based improvised U-Net. Indonesian J. Elec. Engg. Comp. Sci., 21(3), 1424–1434.

*   [Shah, Chintan, and Anjali G. Jivani](#ch36.xhtml#R_ref36_54). (2013). Comparison of data mining classification algorithms for breast cancer prediction. In 2013 Fourth international conference on computing, communications and networking technologies (ICCCNT). 1–4. IEEE, 2013. [10.1109/ICCCNT.2013.6726477](http://dx.doi.org/10.1109/ICCCNT.2013.6726477)

*   [Frannita, E. L., Nugroho, H. A., Nugroho, A., and Ardiyanto, I.](#ch36.xhtml#R_ref36_55) (2018). Thyroid nodule classification based on characteristic of margin using geometric and statistical features. 2018 2nd Int. Conf. Biomed. Engg. (IBIOMED), 54–59.

*   [Ying, X., Yu, Z., Yu, R., Li, X., Yu, M., Zhao, M., and Liu, K.](#ch36.xhtml#R_ref36_56) (2018). Thyroid nodule segmentation in ultrasound images based on cascaded convolutional neural network. Neural Inform. Proc. 25th Int. Conf. ICONIP 2018, Siem Reap, Cambodia, December 13–16, 2018, Proc., Part VI 25, 373–384.

# 37 Hybrid security of EMI using edge-based steganography and three-layered cryptography

Divya Sharma^([^(37)](#fn37))

Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

DOI: [10.1201/9781003471059-37](https://dx.doi.org/10.1201/9781003471059-37)

## Abstract

To enhance the security and ensure privacy of a larger data set of electronic medical images (EMI) each of which varies in properties while they are in storage, or before being transmitted, and accessed through real-time applications has become a challenging issue. Stored EMI should be easily accessible anytime while ensuring secrecy and privacy. The proposed hybrid method (PHM) is a combination of steganography with cryptography which ensures security while reducing the computational time so that they can secure EMI in real time. Initially, in PHM the EMI is hidden using edge-based steganography and then applied with three-layered cryptography. The proposed hybrid method is implemented using MATLAB. The efficiency metrics applied are: total time which combines steganography with encryption time, decrypt and de-steganography time thus overall processing time, Peak Signal to Noise Ratio (PSNR), Mean Square Error (MSE), Kullback-Leibler Divergence (KLD), Root Mean Square Error (RMSE), Bit Error Rate (BER), etc. This article aims to secure a larger data set of 5856 EMI images of varying dimensions sized 1.16 GB by implementing the PHM which is a combination of cryptography and steganography. Further performance analysis demonstrates its efficiency and effectiveness in terms of reduced total processing time, encryption, and decryption time. Therefore, PHM can be used by hospitals to enhance security and privacy while providing real-time access to EMI. The PHM achieved is 0.99, R is 0.99, while better value for Kullback-Leibler Divergence (KLD), Root Mean Square Error (RMSE), Bit Error Rate (BER), Universal Average Changed Intensity (UACI), Number of Changing Pixel Rate (NPCR), etc. Hence proving its statistical relevance.

**Keywords:** Secrecy, privacy, electronic medical image (EMI), steganography, cryptography

## Introduction

Initially, there was digital data which is a raw form of information that could be stored locally or remotely or transferred over the Internet. Popular storage devices such as optical disk, solid state disk or drive (SSD), universal serial bus (USB), compact disk (CD), digital-versatile disk (DVD), etc., are used for storing digital data. Nowadays, digital data has grown with the increase in population.

### Digital data

Digital data in information sciences is the representation of information in a format that is understandable to computers ([Sharma and Kawatra, 2023](#ch37.xhtml#ref37_26)). Generally, a computer understands 0 and 1’s, and anything saved in such format is called digital data. The various types of popular storage mediums are shown in [Figure 37.1](#ch37.xhtml#fig37_1). There are four types of digital data are as follows:

![Figure 37.1 Commonly used data storage devices](images/fig37_1_C.jpg)

[Figure 37.1 Commonly used data storage devices](#ch37.xhtml#R_fig37_1)

1.  Digital text

2.  Digital image

3.  Digital audio

4.  Digital video.

### Introduction to electronic health records (EHR)

The advent of electronic health records (EHR) (Al [Hamid et al., 2017](#ch37.xhtml#ref37_13); [Ali et al., 2022](#ch37.xhtml#ref37_6)) has led to a rise in issues related to the security of the EHR. EHR often consists of patient records, X-ray images ([Agarwal and Prabha, 2022](#ch37.xhtml#ref37_3)), CT scans, etc., (Al [Hamid et al., 2017](#ch37.xhtml#ref37_13)). These are collected by hospitals, laboratories, pharma companies, etc., ([Ali et al., 2022](#ch37.xhtml#ref37_6)) for research, analysis, and development purposes. Popular EMI such as X-ray, MRI, etc., are created, accessed, stored, and maintained on the computer as digital images. Some common EMI known can be seen in [Figure 37.2](#ch37.xhtml#fig37_2). Thus, an EHR can be said to be a collection of EMI, patients’ details, etc.

![Figure 37.2 Common types of EMI](images/fig37_2_C.jpg)

[Figure 37.2 Common types of EMI](#ch37.xhtml#R_fig37_2)

### Internet of medical things (IOMT)

IOMT are devices and applications which help create EHR and also allow sharing them with various devices like computer, android, etc., through Internet. Some IOMT devices currently in use are depicted in [Figure 37.3](#ch37.xhtml#fig37_3). IOMT data such as medical records and imaging is currently facing security and privacy concerns like theft or ransomware attacks ([Sharma and Prabha, 2021](#ch37.xhtml#ref37_28); [Lin et al., 2023](#ch37.xhtml#ref37_20)). The goal of this research is to develop a hybrid steganography and cryptography method for EMI security and protection from modification, theft or loss attacks while they reside on storage devices.

![Figure 37.3 Commonly used smart medical devices that generate EHR](images/fig37_3_C.jpg)

[Figure 37.3 Commonly used smart medical devices that generate EHR](#ch37.xhtml#R_fig37_3)

### Problem statement
