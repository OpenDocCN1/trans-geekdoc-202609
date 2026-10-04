
31.W. Ayadi, W. Elhamzi, I. Charfi, and M. Atri, “A hybrid feature extraction approach for brain MRI classification based on Bag-of-words,” *Biomed. Signal Process. Control*, vol. 48, pp. 144–152, 2019.

32.S. S. R. Phaye, A. Sikka, A. Dhall, and D. R. Bathula, “Multi-level dense capsule networks,” in *Asian Conference on Computer Vision*, 2018, pp. 577–592.

[33](#chap11.xhtml#fs33).E.-S. A. El-Dahshan, T. Hosny, and A.-B. M. Salem, “Hybrid intelligent techniques for MRI brain images classification,” *Digital Signal Process*., vol. 20, pp. 433–441, 2010.

[34](#chap11.xhtml#fs34).Muhammad, Khan, Tanveer Hussain, and Sung Wook Baik, “Efficient CNN based summarization of surveillance videos for resource-constrained devices,” *Pattern Recogn. Lett*., vol. 130, pp. 370–375, 2020.

[35](#chap11.xhtml#fs35).Hussain, Tanveer, Khan Muhammad, Javier Del Ser, Sung Wook Baik, and Victor Hugo C. de Albuquerque, “Intelligent Embedded Vision for Summarization of Multiview Videos in IIoT.” *IEEE Trans. Industr. Inform*., vol. 16, no. 4, pp. 2592–2602, 2019.

[36](#chap11.xhtml#fs36).Hussain, Tanveer, Khan Muhammad, Salman Khan, Amin Ullah, Mi Young Lee, and Sung Wook Baik. “Intelligent baby behavior monitoring using embedded vision in IoT for smart healthcare centers.” *J. Artif. Intell. Syst*., vol. 1, no. 1, pp.110–124, 2019.

© 2021 World Scientific Publishing Company

[https://doi.org/10.1142/9789811218842_0012](https://doi.org/10.1142/9789811218842_0012)

# Chapter 12

# Classification of Travel Patterns Including Wandering Based on Bi-directional Long Short-Term Memory Networks

Nhu Khue Vuong^([\*](#chap12.xhtml#fn1),[‡](#chap12.xhtml#fn2)), Yong Liu^([†](#chap12.xhtml#fn3),[§](#chap12.xhtml#fn4)), Syin Chan^([†](#chap12.xhtml#fn3),[¶](#chap12.xhtml#fn5)), Chiew Tong Lau^([†](#chap12.xhtml#fn3),[||](#chap12.xhtml#fn6)), Zhenghua Chen^([\*](#chap12.xhtml#fn1),[\*\*](#chap12.xhtml#fn7)), Min Wu^([\*](#chap12.xhtml#fn1),[††](#chap12.xhtml#fn8)) and Xiaoli Li^([\*](#chap12.xhtml#fn1),[‡‡](#chap12.xhtml#fn9))

^([\*](#chap12.xhtml#fnr1)) *Institute for Infocomm Research, Singapore*

^([†](#chap12.xhtml#fnr3))*School of Computer Engineering, Nanyang Technological University, Singapore*

^([‡](#chap12.xhtml#fnr2))*[vuong_nhu_khue@i2r.a-star.edu.sg](mailto:vuong_nhu_khue@i2r.a-star.edu.sg)*

^([§](#chap12.xhtml#fnr4))*[stephenliu@ntu.edu.sg](mailto:stephenliu@ntu.edu.sg)*

^([¶](#chap12.xhtml#fnr5))*[asschan@ntu.edu.sg](mailto:asschan@ntu.edu.sg)*

^([||](#chap12.xhtml#fnr6))*[asctlau@ntu.edu.sg](mailto:asctlau@ntu.edu.sg)*

^([\*\*](#chap12.xhtml#fnr7))*[Chen_Zhenghua@i2r.a-star.edu.sg](mailto:Chen_Zhenghua@i2r.a-star.edu.sg)*

^([††](#chap12.xhtml#fnr8))*[wumin@i2r.a-star.edu.sg](mailto:wumin@i2r.a-star.edu.sg)*

^([‡‡](#chap12.xhtml#fnr9))*[xlli@i2r.a-star.edu.sg](mailto:xlli@i2r.a-star.edu.sg)*

## Abstract

Classification of travel patterns including wandering is important for early recognition of cognitive deterioration and other health conditions in people with dementia (PWD). In this chapter, we develop machine learning (ML) and deep learning (DL) models to recognize dementia-related wandering patterns based on the orientation data available in mobile devices. In particular, we use DL with long short-term memory networks (LSTM) and bi-directional LSTM to detect direct, pacing, lapping and random travel patterns. Experimental results on a real dataset collected from 14 subjects show that deep LSTM classifiers improve the classification accuracy by 2% compared to traditional ML classifiers. The results and proposed methodology can be further improved so as to develop useful healthcare applications for dementia-related wandering monitoring and management.

**Keywords:** classification, dementia, dementia-related wandering, detection, wandering behavior, wandering patterns, wandering management

## 1.Introduction

Dementia is a condition which affects the brain and usually leads to memory loss, mental decline and deterioration of intellectual functions, and its global prevalence is expanding rapidly \[[1](#chap12.xhtml#fsr1)\]. Wandering is a common but dangerous behavior among people with dementia (PWD). A five-year study of clinical records in patients with preclinical dementia \[[2](#chap12.xhtml#fsr2)\] found that wandering is the earliest symptom followed by cognitive complaints. Evidence also shows that changes in locomotion patterns begin many years prior to the onset of dementia \[[3](#chap12.xhtml#fsr3)\] and gait-related motor disturbances present in all subtypes of dementia, even in the early and preclinical stages \[[4](#chap12.xhtml#fsr4)\], \[[5](#chap12.xhtml#fsr5)\]. Therefore, monitoring wandering patterns is very important to provide information on the cognitive deterioration and health conditions of the wanderers \[[6](#chap12.xhtml#fsr6)\].

Some features of wandering patterns are further demonstrated to be associated with cognitive declination, health status, and other physiological effects in PWD. Patients with mild cognitive impairment were found to have greater variability in walking speeds and activity levels than those without the diagnosis \[[7](#chap12.xhtml#fsr7)\]. Increased stride time variability is also correlated negatively with cognitive performance and increased the risk of falls in community-dwelling elders \[[8](#chap12.xhtml#fsr8)\]. Algase *et al*. \[[9](#chap12.xhtml#fsr9)\] found that pacing patterns among PWD who wander are signals of agitation and discomfort. Hence, it is essential to measure the wandering patterns in PWD in order to identify and quantify their declines in cognitive functions.

In Martino-Saltzman *et al*. \[[10](#chap12.xhtml#fsr10)\], four types of travel patterns, namely direct travel, pacing, lapping and random travel, were defined to characterize wandering behavior of PWD. The findings in \[[9](#chap12.xhtml#fsr9), [10](#chap12.xhtml#fsr10)\] indicate that direct travel is not wandering, while the other three types of patterns show different severity of dementia. To classify these four types of travel patterns, manual approach by visually inspecting the recorded movements of PWD from videotapes is common in the gerontology research community. However, it is labor-intensive and susceptible to human error. In addition, informed consent is required as visual observation is considered invasive of a subject’s privacy.

Many other methods have been used for automated classification of travel patterns, including wandering. Localization modalities such as RFID \[[11](#chap12.xhtml#fsr11)\] and WiFi \[[12](#chap12.xhtml#fsr12)\] had been used to track and analyze the sequences of locations traversed to recognize travel patterns, including wandering. Lin *et al*. \[[13](#chap12.xhtml#fsr13)\] and Delaunay and Guerin \[[14](#chap12.xhtml#fsr14)\] used GPS trajectories and developed algorithms based on GPS data to detect loop-like patterns. Gochoo *et al*. \[[15](#chap12.xhtml#fsr15)\] had employed binary passive infrared sensor and deep learning (DL) to classify travel patterns, including wandering. Recently, inertial sensors from mobile and wearable devices have been used to track the orientation information while a person travels in order to determine travel patterns \[[16](#chap12.xhtml#fsr16)\]. Clearly, inertial sensors are cheaper and more readily available compared to other methods using video cameras, RFID \[[11](#chap12.xhtml#fsr11)\], infrared sensors \[[15](#chap12.xhtml#fsr15)\] and ultrawide band localization systems, hence can be widely used for monitoring dementia patients \[[17](#chap12.xhtml#fsr17)\].
