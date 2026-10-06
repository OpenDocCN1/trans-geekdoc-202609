
# Chapter 10
## Malaria Detection System Using Convolutional Neural Network Algorithm

Kanika Gautam
Mody Uravity of Science and Technology, Lakshmangarh, India

Sunil Kumar Jangir
Mody Uravity of Science and Technology, Lakshmangarh, India

Manish Kumar
Mody Institute of Science and Technology, Lakshmangarh, India

Jay Sharma
JECRC, Jaipur, India

# ABSTRACT

Malaria is a disease caused when a female Anopheles mosquito bites. There are over 200 million cases recorded per year with more than 400,000 deaths. Current methods of diagnosis are effective; however, they work on technologies that do not produce higher accuracy results. Henceforth, to improve the prediction rate of the disease, modern technologies need to be performed for accurate results. Deep learning algorithms are developed to detect, learn, and determine the containing parasites from the red blood smears. This chapter shows the implementation of a deep learning algorithm to identify the malaria parasites with higher accuracy.

# INTRODUCTION

Malaria is a disease which is caused by infected female Anopheles mosquitoes. The bite of the mosquito causes effects on the red blood cells of the human body. The estimations by the world malaria report show that there are around 216 million malaria cases registered worldwide every year and around 445,000 deaths which include 75% children below 5 years of age (Widiwathi, Nugroho, and Ardiyanto 2016).

DOI: 10.4018/9-1798-3095-5.ch010

# Malaria Detection System Using Convolutional Neural Network Algorithm

The parasites that cause malaria in humans are **Plasmodium falciparum, plasmodium vivax, plasmo-malaria, and plasmodium ovale.** Out of the entire world population infected with malaria, of 70%-90% approximately cases are observed in Asia, Central and South America and the Middle East.

The presence of malaria parasites in human blood cells needs to be known early so that proper diagnosis can be done and get rid of the infection. The infection in the red blood cells grows very rapidly. Various technologies are available which are used for the detection of malaria parasites in the human blood cells. However, these techniques fail get results with higher accuracy and value skills and manual labor. Hence, many automated systems are designed which resolve such problems in terms of time as well as accuracy.

# LITERATURE REVIEW

Analyzing various results from various systems being already designed, the CNN model is designed to get better results which gave beneficial results with the accuracy of 90%-95%.

# BACKGROUND

Above mentioned methods turned out to be failure as it required great training, time taking and highly skilled professionals for performing the detection of malaria. The use of this method-

# Table 1. Comparative study of different methodologies used by different authors

| S.No. | Author and Year | Approach used | Results and Discussions |
|---|---|---|---|
| 1. | (Poochi et al. 2018) | Deep learning, Image Acquisition, Feature Extraction | Enables larger test sets on the patient level. Automated microscopy turns out to be cheap, simple and reliable. |
| 2. | (Dong, Jiang, Shen, and Pan 2017) | Deep learning, CNN, SVM, LeNet, AlexNet and GoogLeNet | Results came out with 95% accuracy. Features of the datasets were learned automatically |
| 3. | (Rahman et al. 2019) | Data Splitting, Stain Normalization, Min-Max Normalization, Data Augmentation | The results were less accurate. The layout of the original image changed. |
| 4. | (Rahman et al. 2019) | K means clustering algorithm, classification, KNN classifier | Separation of infected cells. Malaria parasites detected and classified. |
| 5. | (Nagrob, Akbar, and Murhandurarti 2016) | Histogram, Feature Extraction, Classification, Backpropagation | The proposed method results accuracy of 87.8%, sensitivity of 81.7%, and specificity of 90% for detecting malaria parasites in red blood smears. |
| 6. | (Khan et al. 2017) | Color translation, K-Means clustering. | The feature set obtained b*-color channel from the CIE L*a*b* color space provides better clustering results. |
| 7. | (Pattaenaik, Swarnikar, and Sheet 2017) | Object Detection, Kalman Filter: Kernel Based Detection, Computer vision. | The newly acquired representation enhances the detection performance of infected malaria parasites in thin blood smear images. |

Figure 1. IBM Watson generated report for 3 consecutive years

![](img/c5cbbc72cd5e7b9be32079eac36d685c_240_0.png)

# Malaria Detection System Using Convolutional Neural Network Algorithm

ology required a great economic effort which was indeed very difficult to maintain. Rapid diagnostic tests methodology was also used for the detection of malaria parasites in the red blood cells. This test was comparatively easy to perform as in this methodology skills and special equipment were not required. These tests take less time to compare with the others but not generate results with higher accuracy values.

To get the results with higher accuracy and low costs, staining methods were used for the detection of parasites. The drawback of using this method was that it is time-consuming and requires manual labor. The presence of dirt, bacteria, precipitation, etc. could not be examined by using this methodology, hence it produces false results in many cases.

# Requirement Analysis

The problem with the existing system for detecting malaria and manual diagnosis needs to be rectified hence the idea of designing an automated system. There was a greater need to design a system that could generate better results with higher accuracies and which are also cost-effective. The automation system for detecting malaria parasites in the red blood cells becomes a major requirement for resource-scarce areas. Designing of the automation system does not require manual labor and is not time-consuming as well.

Automation system enables a machine to work with greater efficiency to generate higher accuracy with minimum or zero chances of any error being generated.

# SOLUTIONS AND RECOMMENDATIONS

Considering the failures in the results obtained from the already existing outdated system, it becomes a major requirement to design a system that operates on modern deep learning methodologies to find better and more accurate results.

The automated system should be designed to study the image given as input and generate the corresponding results. The working of the automated systems should take place step by step and systematically. The working of the system begins by taking an image from the dataset as input can be infected or uninfected. Various algorithms also apply several pre-processing methods on the dataset available to arrange images in some format. Next is the detection of the image points out various objects (like platelets) present in the image (Poochi et al. 2018) 

After the detection of various objects in the image, the model designed is identifies various objects (whether parasite or no) and separates them as classes while designing the model. In designing various automated systems for the detection of malaria parasites in the red blood cells. Several Machine Learning Algorithms have been tested on their results of predicting the best accuracies. Computer-Aided Diagnosis, SVM and CNN Algorithms have been designed to get prediction results with higher accuracy.

The binary SVM used gave the results with an accuracy of 80–85%, which were better than the results from the existing systems.

Machine Learning Algorithms generated good results with the datasets that contained fewer images, and Deep Learning Algorithms worked efficiently with the datasets containing a large number of input images (Liang et al. 2017). Perhaps, the results obtained by both methodologies were more or less the same. Deep CNN Algorithm with multiple layers was designed to find patches in the input image and identify them, this gave very good results with an accuracy of 94.26%.

CNN Algorithms may sometimes cause a problem of overfitting in the dataset but there are many ways to overcome this problem and hence, CNN Algorithm can be used to generate good results in detecting Malaria Parasites in the red blood smears.

# METHODOLOGIES

In this work, a CNN Model-based algorithm is used for detecting malaria parasites in red blood smears from the American origin dataset taken as the input. The algorithm uses various Machine Learning python libraries (Keras, Tensorflow, PIL, Tkinter) and layer implementations for building model and deriving results. The working of the algorithm processes as follows:

# Image Datasets

The designed CNN Algorithm requires a dataset that contains a large number of images for prediction (Red Blood Cell Images n.d.). The dataset is divided into two subsections of which contains all the red blood cells images which are infected from parasites whereas the other part contains the images which are healthy and does not contain any parasites (Nanoti et al. 2017).

> Figure 2. Sample Dataset containing infected and uninfected red blood smears

![](img/c5cbbc72cd5e7b9be32079eac36d685c_242_0.png)

(a) (b)
