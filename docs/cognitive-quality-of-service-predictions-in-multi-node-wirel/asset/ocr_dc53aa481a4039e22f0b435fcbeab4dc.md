# # Cognitive quality of service predictions in multi-node wireless sensor networks

Muhammad Ateeq ^a, Muhammad Khalil Afzal ^b, Sheraz Anjum ^b, Byung-Seo Kim ^c, *

* Faculty of Computing, The Islamia University of Bahawalpur, Pakistan
b Department of Computer Science, Comsats University Islamabad, Wah Campus, Pakistan
c Department of Software and Communications Engineering, Hongik University, South Korea

# ### ARTICLE INFO

+   Keywords:
+   - Performance predictions
+   - Machine learning
+   - Internet of things
+   - Wireless sensor networks
+   - Quality of service

# ### ABSTRACT

Wireless sensor networks lead the way to the realization and penetration of the internet of things into daily life. As the sensors and communication devices interconnect things and people more, the quality of service demands become stringent and diverse. Optimizing conflicting quality of service goals is NP-hard. Moreover, the need for the communication systems to dynamically adapt has grown as factors like scale, application-specific performance demands, and deployment scenarios evolve. In this article, we intend to predict the quality of service with an aim to improve the performance of services in the internet of things. We conducted experiments using a real test-bed and collected performance data under a wide range of communication parameter configurations. Statistical analysis revealed a significant relationship between communication parameters and quality of service metrics. Based on the correlations, we trained deep learning models to assess the predictability of the metrics. The prediction results are encouraging. The outcomes of this research pave the way to lay the foundation for a data-driven design of adaptive quality of service in wireless sensor networks and the internet of things.

# ## 1. Introduction

The ubiquitous presence of Wireless Sensor Networks (WSNs) has contributed greatly to the realization of the internet of things (IoT) [1], and this increasing scale also positions IoT in more challenging situations. WSNs find applications in many areas of daily life where sensor nodes are used to carry out specific tasks without the intervention of humans. Some of the application domains include agriculture, medical units, underwater monitoring systems, smart home appliances, smart industries, etc. [2,3]. Lately, wearable sensor technologies have caused a surge in the number of people connected to the internet. [4]

The evolution in WSNs has diversified its application domains and hence meeting performance goals become challenging. It is common to find particular Medium Access Control (MAC) and physical (PHY) layer solutions to meet the performance demands of specific application domains. However, devising MAC and PHY protocols leads to heavy experimentation, standardization, and manufacturing costs. The costs come in the form of monitory as well as time. The other major limitation of the aforementioned approach is the lack of adaptivity. The protocols are usually hard-defined with minimal configurability and cannot self-tune as the network and application scenarios exhibit evolution. We can address the problem of adaptivity by maximizing the configurability of various parameters protocols by identifying their

respective relationships with the quality of service (QoS) metrics as well as selecting appropriate MAC protocol. It is pertinent to mention that configurability of parameters means assigning appropriate values to different parameters at different layers of the protocol stack in use (e.g., packet size, traffic rate, transmission power, backoff, etc.). Some of these parameters (which are protocol specific) can contribute to the configuration of a protocol. Whereas, we also propose to choose a particular protocol depending on the QoS need. For example, the current implementation of Contiki operating systems allows for choosing CSMA or TSCH as a MAC layer protocol. Both have different characteristics and can behave differently under different conditions. Understanding the relationships among the communication parameters and QoS metrics is vital to meeting the conflicting QoS goals in changing network conditions and emerging application requirements. [5].

Research in the domain of WSNs has been extended to diverse considerations. Work presented in [6] highlights the importance of efficient wireless sensor and actuator node organization in critical sectors like agriculture. The proposed solution is not based on any adaptive method like machine learning. Considering the growing importance of the cloud and integration of WSNs with it, [7] proposed a solution to reduce the network load being transferred to the cloud by facilitating processing at the edge. The proposed solution can benefit from possible

* Corresponding author.
E-mail address: jsnbs@hongik.ac.kr (B.-S. Kim).

https://doi.org/10.1016/j.comcom.2022.06.042
Received 25 February 2022; Received in revised form 22 May 2022; Accepted 29 June 2022
Available online 6 July 2022