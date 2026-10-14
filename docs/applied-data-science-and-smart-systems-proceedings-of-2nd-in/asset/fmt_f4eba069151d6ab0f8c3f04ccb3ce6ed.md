
# 32 Optimization techniques for wireless body area network routing protocols: Analysis and comparison

Swati Goel, Kalpna Guleria^([^(32)](#fn32))

Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

DOI: [10.1201/9781003471059-32](https://dx.doi.org/10.1201/9781003471059-32)

## Abstract

Wireless body area networks (WBANs) are a type of wireless network used to monitor and collect data from various sensors attached to the human body. WBAN has enormous applications like assisted living, healthcare, sports, defense, entertainment, military, and many others. The successful deployment and operation of WBANs come with several challenges, including energy efficiency, on-time data transmission, reliability, scalability, security, and network lifetime. Routing is a critical and important aspect of WBAN communication, and several optimization techniques have been proposed to improve the routing performance in WBANs. Optimization techniques plays a crucial role in optimizing and improving the performance of WBANs routing protocol. These techniques aim to optimize various parameters such as power consumption, data rate, energy efficiency, throughput, network bandwidth, delay, network lifetime etc. This paper provides an overview of the optimization techniques used for routing in WBANs in recent years (2014–2023). These optimization techniques can significantly improve the performance of WBAN routing protocols and enable them to be used for various applications related to medical and non-medical domains. The paper discusses the various optimization techniques proposed in the literature, their strengths, weaknesses and simulators used to evaluate WBAN routing performance. By analyzing and summarizing existing research, this paper aims to provide valuable insights into the current state of optimization techniques in WBAN routing and identify potential research gaps for future exploration.

**Keywords:** Wireless body area networks, technology, optimization techniques, sensors, WBAN, routing, energy

## Introduction

WBANs emerged as a promising technology for the last few decades as they found their applications in a vast number of sectors both related to medical and non-medical fields. These networks have very small, low-powered sensors attached to the human body to monitor various physiological parameters. The sensor’s collected data is wirelessly transmitted to a central monitoring station for analysis and diagnosis. It has gained significant attention in recent years for its potential applications in healthcare. To ensure efficient data transmission; routing in WBAN plays a very crucial role ([Negra, Jemili, and Belghith, 2016](#ch32.xhtml#ref32_18)). A good routing protocol helps to achieve reliable and timely communication among the various medical sensors and devices. However, the design of WBANs poses several challenges, such as limited power, bandwidth, interference, processing capabilities, etc., ([Shunmugapriya et al., 2022](#ch32.xhtml#ref32_27)). To overcome these challenges, nowadays optimization techniques have been proposed to improve the performance of WBANs routing protocol. There are a lot of parameters that are used to evaluate the WBAN routing protocol performance. The various metrics that can be used to evaluate WBAN routing protocol performance are temperature rise, delay, scalability, throughput, stability, reliability, security, network lifetime, energy efficiency, packet delivery ratio, etc., ([Shokeen and Parkash 2019](#ch32.xhtml#ref32_26); [Qadri et al., 2020](#ch32.xhtml#ref32_20)). Before the advancement of optimization algorithms, the traditional approaches were used to perform routing in WBAN. But with advancements and awareness towards the optimization techniques in the last few decades, the various routing parameters can be optimized resulting in enhanced network performance. Optimization techniques play a crucial role in addressing the various challenges, making them an indispensable part of WBAN ([Rani et al., 2021](#ch32.xhtml#ref32_22)). Traditional routing methods may be simple but often lack adaptability, energy efficiency, and QoS guarantees required in WBANs, especially for healthcare applications ([Guleria and Verma, 2019](#ch32.xhtml#ref32_11)). Optimization techniques, on the other hand, offer dynamic, energy-efficient, secure, and adaptable routing solutions that are better suited to the challenges posed by WBANs, making them efficient for the routing process ([Mahmoud, Fadel, and Akkari, 2020](#ch32.xhtml#ref32_16)).

Optimization techniques play a pivotal role in overcoming the challenges associated with WBAN especially related to WBAN routing. From enhancing energy efficiency to ensuring data reliability, and optimizing spectrum allocation to safeguarding security and privacy, these techniques are essential for the successful deployment and operation of WBANs in healthcare, medical, and non-medical applications ([Guleria, Kumar, and Verma, 2019](#ch32.xhtml#ref32_10); [Bhola et al., 2022](#ch32.xhtml#ref32_6)). As technology continues to advance, ongoing research and development in optimization will further improve the performance and capabilities of WBANs, ultimately benefiting both healthcare providers and patients.

### Objective of the paper

To be used as a foundation for future study and the creation of more sophisticated WBAN routing protocols, the goal of this work is to provide insight into the optimization approaches currently employed in WBAN routing with the help of a systematic review and to outline the various advantages and limitations of the various optimization techniques used to perform efficient WBAN in recent last decade i.e., from 2014 to 2023.

### Contribution

In this article; a systematic study is conducted to present the current state of art of the optimization techniques used in WBAN routing. The importance of optimization algorithms for WBAN routing protocols is highlighted. The recent published research papers between the years 2014–2023 for routing protocols using optimization techniques are presented in this review article. The systematic review methodology is followed to select the high-quality research articles to justify the work. Four research questions (RQs) are framed and addressed to conduct the review in an efficient way for better understanding and to organize the review. The research questions are defined below named as RQ1 to RQ4.

**RQ1.** What is the annual trend of growth in the WBAN domain?

**RQ2.** How is the routing associated and important in WBAN?

**RQ3.** Which state-of-the-art optimization techniques are used in the WBAN domain to perform efficient routing?

**RQ4.** What are the limitations and challenges involved in WBAN routing protocols?

### Article organization

The paper’s organization is shown with the help of the road map provided below as shown in [Figure 32.1](#ch32.xhtml#fig32_1). Initially, a brief introduction about WBAN, WBAN routing, and the need for optimization followed by research questions are defined which is named as an introduction followed by the methodology adopted for article selection. Following this the background is discussed and provides answers to our first two research questions RQ1 and RQ2 which corresponds to our RQ3 and provides state-of-the-art work related to WBAN routing using optimization techniques. A comparative study of various WBAN routing protocols based on optimization techniques highlighting the main objective, advantages, disadvantages, and simulation tool used. Finally the paper is concluded with a focus on future work.

![Figure 32.1 Organization of paper](images/fig32_1_C.jpg)
