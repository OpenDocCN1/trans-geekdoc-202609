
6. [Kucuk, M. F., and Uysal, I.](#ch30.xhtml#R_ref30_6) (2022). Anomaly detection in self-organizing networks: conventional versus contemporary machine learning. IEEE Access, 10, 61744-61752. doi: [10.1109/ACCESS.2022.3182014.](http://dx.doi.org/10.1109/ACCESS.2022.3182014)

7. [Wighneswara, A. A., et al.](#ch30.xhtml#R_ref30_7) (2023). Network behavior anomaly detection using decision tree. In IEEE 12th International Conference on Communication Systems and Network Technologies (CSNT), Bhopal, India, (pp. 705-709.), doi: [10.1109/CSNT57126.2023.10134589](http://dx.doi.org/10.1109/CSNT57126.2023.10134589).

8. [Villalba, D. A. M., Varon, D. F. M., Pórtela, F. G., and Triana, O. A. D.](#ch30.xhtml#R_ref30_8) (2022). Intrusion detection system (IDS) with anomaly-based detection and deep learning application. In V Congreso Internacional en Inteligencia Ambiental, Ingeniería de Software y Salud Electrónica y Móvil (AmITIC), San Jose, Costa Rica, (pp. 1-4.), doi: [10.1109/AmIT-IC55733.2022.9941277](http://dx.doi.org/10.1109/AmIT-IC55733.2022.9941277).

9. [Shi, Y. and Miao, K.](#ch30.xhtml#R_ref30_9) (2019). Detecting anomalies in application performance management system with machine learning algorihms. In 3rd International Conference on Electronic Information Technology and Computer Engineering (EITCE), Xiamen, China, (pp. 1797-1800.), doi: [10.1109/EITCE47263.2019.9094916.](http://dx.doi.org/10.1109/EITCE47263.2019.9094916)

10. [Dmitrievich, A. G., and Nikolaevich, S. A.](#ch30.xhtml#R_ref30_10) (2020). Automated process control anomaly detection using machine learning methods. In Ural Symposium on Biomedical Engineering, Radioelectronics and Information Technology (USBEREIT), Yekaterinburg, Russia, (pp. 0536-0538.), doi: [10.1109/USBEREIT48449.2020.9117692.](http://dx.doi.org/10.1109/USBEREIT48449.2020.9117692)

11. [Das, S., Ashrafuzzaman, M., Sheldon, F. T., and Shiva, S.](#ch30.xhtml#R_ref30_11) (2020). Network intrusion detection using natural language processing and ensemble machine learning. In IEEE Symposium Series on Computational Intelligence (SSCI), Canberra, ACT, Australia, (pp. 829-835.), doi: [10.1109/SSCI47803.2020.9308268.](http://dx.doi.org/10.1109/SSCI47803.2020.9308268)

12. [Noor, S., Bazai, S. U., Ghafoor, M. I., Marjan, S., Akram, S., and Ali, F.](#ch30.xhtml#R_ref30_12) (2023). Generative adversarial networks for anomaly detection: a systematic literature review. In 4th International Conference on Computing, Mathematics and Engineering Technologies (iCoMET), Sukkur, Pakistan, (pp. 1-6.), doi: [10.1109/iCoMET57998.2023.10099175.](http://dx.doi.org/10.1109/iCoMET57998.2023.10099175)

13. [Kaggle](#ch30.xhtml#R_ref30_13) (2023). The profiling network traffic dataset uploaded from Kaggle repository ([www.kaggle.com](http://www.kaggle.com)) value as on dated August 2023. [https://www.kaggle.com/datasets/mandheer/profiling-network-traffic?select=`Profiling.csv`](https://www.kaggle.com/datasets/mandheer/profiling-network-traffic?select=Profiling.csv).

14. [Feng, Q., Zhu, Q., Yuan, C., and Lee, I.](#ch30.xhtml#R_ref30_14) (2016). Multi-linear regression coefficient classifier for recognition. In IEEE Congress on Evolutionary Computation (CEC), Vancouver, BC, Canada, (pp. 1382-1387.), doi: [10.1109/CEC.2016.7743950.](http://dx.doi.org/10.1109/CEC.2016.7743950)

15. [Katkar, V. D. and Bhatia, D. S.](#ch30.xhtml#R_ref30_15) (2013). Experiments on detection of denial of service attacks using `REPTree`. In Interna-tional Conference on Green Computing, Communication and Conservation of Energy (ICGCE), Chennai, India, (pp. 713-718.), doi: [10.1109/ICGCE.2013.6823527.](http://dx.doi.org/10.1109/ICGCE.2013.6823527)

# 31 Using MLP and convolutional neural networks (CNN) to perform decision making related to skin disease infections

Neha Chauhan^([^(30)](#fn30))

DOI: [10.1201/9781003534136-31](https://dx.doi.org/10.1201/9781003534136-31)

## Abstract

Skin diseases affect a large percentage of all living things. Keeping tabs on and identifying skin illnesses is a difficult task for the medical community. Infections leave a nearly visible mark on people’s skin, but determining the precise type can be dif- ficult due to the wide variety of people’s skin tones. That’s why early diagnosis and treatment of skin diseases is so crucial. There has been a recent uptick in the use of `AI` to healthcare. More often than not, deep learning (`DL`) and machine learning (`ML`) approaches are employed for diagnosis. The diagnostic procedure is both enhanced and accelerated by these methods. The purpose of this research is to advance skin disease categorization by creating a hybrid of `DL` and `ML`. The convolution neural networks (`CNN`) model is employed for the purpose of feature extraction and classification, utilizing `ML` models such as support vector machines (`SVM`) and multi-layer perceptron (`MLP`). In order to determine the most effective prediction model, a comparison analysis was conducted, revealing that the hybrid approach of `CNN` combined with `MLP` yielded the highest level of accuracy at 96.06%

**Keywords:** `CNN`, deep learning, `MLP`, skin diseases, support vector machine

## Introduction

The epidermis is the body’s largest and most visible skin layer, and it plays a crucial role in thermoregulation and the activation of heat and cold sensations, which in turn protects numerous internal organs from exter- nal injury and infections. The skin, however, is susceptible to change from both environmental and hereditary factors. Skin illnesses are quite widespread in the human population. Infectious skin disorders, bacterial skin disorders, and contact dermatitis disorders are the most common forms of skin issues. The texture or tone of the skin can be altered by a variety of skin conditions. Diseases of the skin are often incurable, easily spread from person to person, and even potentially cancerous. If discovered and treated early on, fungal and allergy illnesses are very simple medical conditions. However, when dealing with viral illnesses, prompt diagnosis is essential. Rapid progress has been made in the clinical sector in recent years using artificial intelligence (`AI`) models, machine learning (`ML`) [[1](#ch31.xhtml#ref31_1), [2](#ch31.xhtml#ref31_2)], and deep learning (`DL`) [[3](#ch31.xhtml#ref31_3), [4](#ch31.xhtml#ref31_4)]. Improved skin disease forecasts have been the focus of several ensemble based machine learning [[5](#ch31.xhtml#ref31_5)] and artificial neural network [[6](#ch31.xhtml#ref31_6)] based techniques. In this work, skin illnesses are categorised using a method that combines `ML` and `DL` models. Two `ML` mod- els—`SVM` and `MLP`—were utilised to create classifiers. Convolutional neural networks (`CNN`) are utilised for feature extraction. Finally, a battery of tests was run to determine which prediction models performed the best. The given paper is organized into following sections. Section 2 provides a literature review of studies regarding identification and diagnosis of skin diseases. Section 3 discusses methodology of the proposed approach. Section 4 presents experimental results followed by conclusion and references.

## Literature Review
