
- [36] Andrés Bruhn, Joachim Weickert, and Christoph Schnörr. Lucas/kanade meets horn/schunck: Combining local and global optic flow methods. International Journal of Computer Vision, 61(3):211–231, 2005.

- [37] A Marchaud. Sur les dérivées et sur les différences des fonctions de variables réelles. PhD thesis, Impr. Gauthier-Villars, 1927.

- [38] Deqing Sun, Stefan Roth, and Michael J Black. Secrets of optical flow estimation and their principles. In IEEE Computer Society Conference on Computer Vision and Pattern Recognition, 2432–2439, 2010.

- [39] Tom M. Apostol. Calculus, volume-I, one-variable calculus, with an introduction to linear algebra (vol. 1). John Wiley & Sons, 2007.

- [40] Guido Fubini. Sugli integrali multipli. Rend. Acc. Naz. Lincei, 16:608–614, 1907.

- [41] S.V. Fomin and M Gelfand. Calculus of variations. Dover Publications, 2012.

- [42] Mahinder Kumar Jain. Numerical methods for scientific and engineering computation. New Age International, 2003.

- [43] Richard Hamming. Numerical methods for scientists and engineers. Courier Corporation, 2012.

- [44] Shi Jie, Wang Wei, Gao Yuanqi, and Yu Nanpeng. Optimal placement and intelligent smoke detection algorithm for wildfire-monitoring cameras. IEEE Access, 8:72326–72339, 2020.

- [45] Wang Yue, Wee Chua Teck, Chang Richard, and Trung Pham Nam. Real-time smoke detection using texture and color features. In International Conference on Pattern Recognition, 2012.

- [46] Mohammad Hossin and Md Nasir Sulaiman. A review on evaluation metrics for data classification evaluations. International Journal of Data Mining & Knowledge Management Process, 5(2):1, 2015.

- [47] Charles E. Metz. Basic principles of ROC analysis. Seminars in Nuclear Medicine, 8:283–298, 1978. Elsevier.

- [48] Abdel Aziz Taha and Allan Hanbury. Metrics for evaluating 3D medical image segmentation: Analysis, selection, and tool. BMC Medical Imaging, 15(1):1–28, 2015.

- [49] Sebastian Destercke. Multilabel prediction with probability sets: The hamming loss case. In International Conference on Information Processing and Management of Uncertainty in Knowledge-Based Systems. Springer, 496–505, 2014.

- [50] Sarang Narkhede. Understanding AUC-ROC curve. Towards Data Science, 26(1):220–227, 2018.

- [51] Janez Demšar, Tomaž Curk, Aleš Erjavec, Črt Gorup, Tomaž Hočevar, Mitar Milutinović, Martin Možina, Matija Polajnar, Marco Toplak, Anže Starič, et al. Orange: Data mining toolbox in python. The Journal of Machine Learning Research, 14(1): 2349–2353, 2013.

- [52] Saima Majid, Fayadh Alenezi, Sarfaraz Masood, Musheer Ahmad, Emine Selma Gündüz, and Kemal Polat. Attention based CNN model for fire detection and localization in real-world images. Expert Systems with Applications, 189:116114, 2022.

- [53] Faisal Saeed, Anand Paul, P Karthigaikumar, and Anand Nayyar. Convolutional neural network based early fire detection. Multimedia Tools and Applications, 79(13):9083–9099, 2020.

- [54] Khan Muhammad, Jamil Ahmad, and Sung Wook Baik. Early fire detection using convolutional neural networks during surveillance for effective disaster management. Neurocomputing, 288:30–42, 2018.

- [55] Salman Khan, Khan Muhammad, Shahid Mumtaz, Sung Wook Baik, and Victor Hugo C. de Albuquerque. Energy-efficient deep CNN for smoke detection in foggy IoT environment. IEEE Internet of Things Journal, 6(6):9237–9245, 2019.

- [56] Zilong Wang, Tianhang Zhang, Xiqang Wu, and Xinyan Huang. Predicting transient building fire based on external smoke images and deep learning. Journal of Building Engineering, 47:103823, 2022.

- [57] Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. Deep residual learning for image recognition. IEEE Conference on Computer Vision and Pattern Recognition, 770–778, 2016.

## Early Prediction of Cardiac Diseases Using Ensemble Learning Techniques

## A Machine Learning Technique to Deal with Heart Disease Problems

Rima Sen and A. Manimaran

Department of Mathematics, School of Advanced Sciences, VIT-AP University, India

## 11.1 INTRODUCTION

Cardiovascular diseases have lately become the leading cause of death worldwide. Several advanced techniques and even different statistical prediction methods are increasingly being utilized for cardiovascular disease prediction. The results of such a diagnostic approach, while using the current algorithms, are insufficient in identifying heart disease patients. They also confront a huge hurdle in terms of service quality [1–3]. Accurately detecting sickness and efficiently treating patients are both critical aspects of service quality. Inadequate diagnosis can lead to unfavorable outcomes [4, 5]. Age, gender, smoking, obesity, physical inactivity, poor diet, family history, cholesterol, high blood pressure and alcohol use are all risk factors for a heart disorder, as are inherited risk factors [6], including high blood pressure and diabetes. Some risk factors can be prevented. Aside from those aforementioned variables, lifestyle choices such as eating habits, obesity and physical inactivity are also substantial risk factors [7–9]. Coronary heart disease, angina pectoris, congestive heart failure, cardiomyopathy, congenital heart disease, arrhythmias and myocarditis are all examples of heart illnesses [10]. Manually calculating the chances of developing heart disease based on risk factors is too challenging. To deal with such medical emergencies in the healthcare industry, a prediction system based on ensemble learning techniques has been developed. Learning techniques prove to be effective in assisting decision making and predictions from the large quantity of data produced by the healthcare industry [11–13]. Hence, this paper uses a machine learning approach known as a classification to forecast heart disease risk from risk variables by examining patient data and classifying the presence of heart disease. It includes an ensemble technique of several supervised algorithms [14, 15] such as Naïve Bayes [16] and Decision Tree [17], Support Vector Machine [18], and Random Forest [19] model to enhance the accuracy of forecasting heart disease risk addressing the challenges in the healthcare sector.

### 11.1.1 Problem Statement

The major challenge in cardiac disease is its identification. Several tools can forecast heart disease, but they are either too expensive or ineffective in quantifying the risk of heart disease in humans. Early detection of cardiac diseases can decrease the mortality rate and overall consequences of heart disorders. However, it is not possible to precisely monitor patients every day in all circumstances, and a doctor’s 24-hour consultation is not available since it needs more intelligence, time and skill [20]. Due to the availability of a humongous amount of data, various machine learning algorithms can be used to analyze the data for hidden trends in data. Hidden patterns in medical data can be utilized for health diagnosis too [21, 22]. In this research, the ensemble learning technique based on majority voting (max voting) is performed on the medical dataset to enhance the performance as well as the accuracy measure. The Cleveland dataset [23] is considered to train the model as well as to obtain a favorable result after testing it.

The problem statement framework is shown in Figure 11.1.

![](img/9c1422d4c6a10143e1802787075307de_201_0.png)

FIGURE 11.1 Problem statement framework.

## 11.2 RELATED WORK

Several studies have been developed for predicting heart disease using automated technologies [24]. Although those algorithms are beneficial in the healthcare field, they have a few drawbacks. In this paper, a few of those implementations are discussed, along with their limitations, to emphasize the importance of the proposed learning technique. See Table 11.1.

## 11.3 METHODOLOGY

### 11.3.1 Dataset Description

In this research, a dataset from Kaggle named Cleveland dataset [23], which consists of 298 instances and 14 attributes, is used. A brief description of the features of the dataset is discussed in Table 11.2.

This dataset includes patients ranging in age from 29 to 79. Male patients have a gender value of 1, while female patients have a gender value of 0. Four different forms of chest discomfort (CP) are considered heart disease. Symptoms of heart-disease-reduced blood flow cause type 1 angina. Because of constricted coronary arteries, blood flow to the heart muscles
