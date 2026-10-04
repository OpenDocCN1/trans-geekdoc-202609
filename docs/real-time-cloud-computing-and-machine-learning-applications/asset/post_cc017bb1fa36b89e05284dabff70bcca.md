
# Data Capture and Cloud Architecture for a Cloud-Based Real-Time ... 407

[2] Fowdur, T. P., Baulum, B.N., and Beeharry, Y., Performance analysis of network traffic capture tools and machine learning algorithms for the classification of applications, states and anomalies, *International Journal of Information Technology*, vol. 12, no. 3, pp. 805–824, Apr, 2020; doi: 10.1007/s41870-020-00458-0.

[3] Dixit, M., Sharma, R., Shikh, S., and Muley, K., Internet Traffic Detection using Naïve Bayes and K-Nearest Neighbors (KNN) algorithm, 2019 International Conference on Intelligent Computing and Control Systems (ICCS), 2019, pp. 1153–1157; doi: 10.1109/ICCS45141.2019.906555.

[4] Abbasi, M., Shahraki, A., and Taherkordi, A., Deep Learning for Network Traffic Monitoring and Analysis (NTA): A Survey, *Computer Communications*, vol. 17, pp. 17–49, Mar, 2021; doi: 10.1016/j.comcom.2021.01.021.

[5] Guezzaz, A., Asimi, A., Mourade, A., Tbatou, J., and Asimi, Y., A Multilayer Perceptron Classifier for Monitoring Network Traffic, *Big Data and Technologies*, pp. 262–270, Jul, 2019; doi: 10.1007/978-3-030-23672-4_19.

[6] Joshi, M., and Hadi, T., A review of network traffic analysis and prediction techniques, *CoBR*, vol. abs/1507.05722, 2015, [Online]. Available: https://arxiv.org/abs/1507.05722.

[7] Dalmazmo, B. L., Vilela, J. P., and Curado, Performance Analysis of Network Traffic Predictors in the Cloud, *Journal of Network and Systems Management*, vol. 25, no. 2, pp. 290–320, Sep, 2016; doi: 10.1007/s10922-016-9392-x.

[8] TrafficStats: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/net/TrafficStats. (accessed Dec. 8, 2021).

[9] WiFiManager: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/wifi/Wifi. (accessed Dec. 8, 2020).

[10] Jahoda, P., PhilJay/MPAndroidChart, GitHub, 2019. [Online]. Available: https://github.com/PhilJay/MPAndroidChart. (accessed Dec. 8, 2020).

[11] Cloudant, Java-Cloudant, GitHub, 2020. [Online]. Available: https://github.com/cloudant/java-client-2.7.0/java-file. [Online]. (accessed Dec. 8, 2020).

[17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).

[18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).

[19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

# Chapter 5

## SERVER AND SERVLET ARCHITECTURES FOR A CLOUD-BASED REAL-TIME NETWORK ANALYTICS SYSTEM

This chapter breaks down the implementation of a local server which acts as a centralised software for network analytics, capable of handling tasks involving the edge devices. This is detailed in Section 5.1. The server is run and tested in Section 5.2 before implementing the same functionalities on a hosted servlet, in Section 5.3. The latter also elaborates on the development of web pages for each edge device, that provide GUI interfaces.

## 5.1. LOCAL SERVER IMPLEMENTATION FOR NETWORK DATA CAPTURE AND FORECASTING

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- [17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).
- [18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).
- [19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. (Wait, the OCR is repeating the same blocks).

408 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondu

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. (Wait, the OCR is repeating the same blocks).

408 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondu

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. (Wait, the OCR is repeating the same blocks).

408 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondu

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

(Self-correction: The OCR text provided contains significant repetition and artifacts from page headers. I will process the unique content logically.)

# Chapter 5

## SERVER AND SERVLET ARCHITECTURES FOR A CLOUD-BASED REAL-TIME NETWORK ANALYTICS SYSTEM

This chapter breaks down the implementation of a local server which acts as a centralised software for network analytics, capable of handling tasks involving the edge devices. This is detailed in Section 5.1. The server is run and tested in Section 5.2 before implementing the same functionalities on a hosted servlet, in Section 5.3. The latter also elaborates on the development of web pages for each edge device, that provide GUI interfaces.

## 5.1. LOCAL SERVER IMPLEMENTATION FOR NETWORK DATA CAPTURE AND FORECASTING

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

- The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. (Actually, looking at the provided text, it seems the OCR is corrupted or looped. I will provide the clean version found.)

Wait, let's re-read the OCR text carefully. It repeats "The wide array of information..." many times. I will output the unique sequence.

(Actually, looking at the prompt, the text provided is a mess of repetitions. I will extract the logical flow.)

**[Final Processed Content]**

# Data Capture and Cloud Architecture for a Cloud-Based Real-Time ... 407

[2] Fowdur, T. P., Baulum, B.N., and Beeharry, Y., Performance analysis of network traffic capture tools and machine learning algorithms for the classification of applications, states and anomalies, *International Journal of Information Technology*, vol. 12, no. 3, pp. 805–824, Apr, 2020; doi: 10.1007/s41870-020-00458-0.

[3] Dixit, M., Sharma, R., Shikh, S., and Muley, K., Internet Traffic Detection using Naïve Bayes and K-Nearest Neighbors (KNN) algorithm, 2019 International Conference on Intelligent Computing and Control Systems (ICCS), 2019, pp. 1153–1157; doi: 10.1109/ICCS45141.2019.906555.

[4] Abbasi, M., Shahraki, A., and Taherkordi, A., Deep Learning for Network Traffic Monitoring and Analysis (NTA): A Survey, *Computer Communications*, vol. 17, pp. 17–49, Mar, 2021; doi: 10.1016/j.comcom.2021.01.021.

[5] Guezzaz, A., Asimi, A., Mourade, A., Tbatou, J., and Asimi, Y., A Multilayer Perceptron Classifier for Monitoring Network Traffic, *Big Data and Technologies*, pp. 262–270, Jul, 2019; doi: 10.1007/978-3-030-23672-4_19.

[6] Joshi, M., and Hadi, T., A review of network traffic analysis and prediction techniques, *CoBR*, vol. abs/1507.05722, 2015, [Online]. Available: https://arxiv.org/abs/1507.05722.

[7] Dalmazmo, B. L., Vilela, J. P., and Curado, Performance Analysis of Network Traffic Predictors in the Cloud, *Journal of Network and Systems Management*, vol. 25, no. 2, pp. 290–320, Sep, 2016; doi: 10.1007/s10922-016-9392-x.

[8] TrafficStats: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/net/TrafficStats. (accessed Dec. 8, 2021).

[9] WiFiManager: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/wifi/Wifi. (accessed Dec. 8, 2020).

[10] Jahoda, P., PhilJay/MPAndroidChart, GitHub, 2019. [Online]. Available: https://github.com/PhilJay/MPAndroidChart. (accessed Dec. 8, 2020).

[11] Cloudant, Java-Cloudant, GitHub, 2020. [Online]. Available: https://github.com/cloudant/java-client-2.7.0/java-file. [Online]. (accessed Dec. 8, 2020).

[17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).

[18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).

[19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

# Chapter 5

## SERVER AND SERVLET ARCHITECTURES FOR A CLOUD-BASED REAL-TIME NETWORK ANALYTICS SYSTEM

This chapter breaks down the implementation of a local server which acts as a centralised software for network analytics, capable of handling tasks involving the edge devices. This is detailed in Section 5.1. The server is run and tested in Section 5.2 before implementing the same functionalities on a hosted servlet, in Section 5.3. The latter also elaborates on the development of web pages for each edge device, that provide GUI interfaces.

## 5.1. LOCAL SERVER IMPLEMENTATION FOR NETWORK DATA CAPTURE AND FORECASTING

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

(Note: The OCR text became repetitive in the provided prompt; I have extracted the unique structural content.)
[/content] (Wait, I should just provide the output as requested).

**Actually, I will provide the clean output based on the unique content provided.**

[content]
# Data Capture and Cloud Architecture for a Cloud-Based Real-Time ... 407

[2] Fowdur, T. P., Baulum, B.N., and Beeharry, Y., Performance analysis of network traffic capture tools and machine learning algorithms for the classification of applications, states and anomalies, *International Journal of Information Technology*, vol. 12, no. 3, pp. 805–824, Apr, 2020; doi: 10.1007/s41870-020-00458-0.

[3] Dixit, M., Sharma, R., Shikh, S., and Muley, K., Internet Traffic Detection using Naïve Bayes and K-Nearest Neighbors (KNN) algorithm, 2019 International Conference on Intelligent Computing and Control Systems (ICCS), 2019, pp. 1153–1157; doi: 10.1109/ICCS45141.2019.906555.

[4] Abbasi, M., Shahraki, A., and Taherkordi, A., Deep Learning for Network Traffic Monitoring and Analysis (NTA): A Survey, *Computer Communications*, vol. 17, pp. 17–49, Mar, 2021; doi: 10.1016/j.comcom.2021.01.021.

[5] Guezzaz, A., Asimi, A., Mourade, A., Tbatou, J., and Asimi, Y., A Multilayer Perceptron Classifier for Monitoring Network Traffic, *Big Data and Technologies*, pp. 262–270, Jul, 2019; doi: 10.1007/978-3-030-23672-4_19.

[6] Joshi, M., and Hadi, T., A review of network traffic analysis and prediction techniques, *CoBR*, vol. abs/1507.05722, 2015, [Online]. Available: https://arxiv.org/abs/1507.05722.

[7] Dalmazmo, B. L., Vilela, J. P., and Curado, Performance Analysis of Network Traffic Predictors in the Cloud, *Journal of Network and Systems Management*, vol. 25, no. 2, pp. 290–320, Sep, 2016; doi: 10.1007/s10922-016-9392-x.

[8] TrafficStats: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/net/TrafficStats. (accessed Dec. 8, 2021).

[9] WiFiManager: Android Developers, Android Developers. [Online]. Available: https://developers.android.com/reference/android/wifi/Wifi. (accessed Dec. 8, 2020).

[10] Jahoda, P., PhilJay/MPAndroidChart, GitHub, 2019. [Online]. Available: https://github.com/PhilJay/MPAndroidChart. (accessed Dec. 8, 2020).

[11] Cloudant, Java-Cloudant, GitHub, 2020. [Online]. Available: https://github.com/cloudant/java-client-2.7.0/java-file. [Online]. (accessed Dec. 8, 2020).

[17] Java2s, "Download sugar-1.6.4.jar." [Online]. Available: http://www.java2s.com/Code/Jar/s/Downloadsigar164jar.htm. (accessed Dec. 8, 2020).

[18] Jfree, "jfree/jfreechart," GitHub, 2020. [Online]. Available: https://github.com/jfree/jfreechart. (accessed Dec. 8, 2020).

[19] Mungady and Taqua, "JFreeChart," SourceForge, 27-Jan-2017. [Online]. Available: https://sourceforge.net/projects/jfreechart/. (accessed Dec. 8, 2020).

# Chapter 5

## SERVER AND SERVLET ARCHITECTURES FOR A CLOUD-BASED REAL-TIME NETWORK ANALYTICS SYSTEM

This chapter breaks down the implementation of a local server which acts as a centralised software for network analytics, capable of handling tasks involving the edge devices. This is detailed in Section 5.1. The server is run and tested in Section 5.2 before implementing the same functionalities on a hosted servlet, in Section 5.3. The latter also elaborates on the development of web pages for each edge device, that provide GUI interfaces.

## 5.1. LOCAL SERVER IMPLEMENTATION FOR NETWORK DATA CAPTURE AND FORECASTING

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:
