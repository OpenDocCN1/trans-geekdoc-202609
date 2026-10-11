
16. [K. Yu](#chapter13.xhtml#b13ref13_16), A.K. Budhiraja, and P. Tokekar, “Algorithms for Routing of Unmanned Aerial Vehicles with Mobile Recharging Stations,” arXiv 2017, arXiv:1704.00079v3. Available online: [https://arxiv.org/abs/1704.00079](https://arxiv.org)

17. [J. Shao](#chapter13.xhtml#b13ref13_17), J. Cheng, B. Xia, K. Yang, and H. Wei, “A novel service system for long-distance drone delivery using the “Ant colony and A\*” algorithm,” IEEE Systems Journal, vol. 15, pp. 3348–3359, 2021.

18. [R. Alyassi](#chapter13.xhtml#b13ref13_18), M. Khonji, S. C. Chau, K. Elbassioni, T.C. Ming, and A. Karapetyan, “Autonomous Recharging and Flight Mission Planning for Battery-operated Autonomous Drones,” arXiv 2017, arXiv:1703.10049.

19. [T. Baca](#chapter13.xhtml#b13ref13_19), P. Stepan, V. Spurny, D. Hert, R. Penicka, M. Saska, J. Thomas, G. Loianno, and V. Kumar, “Autonomous landing on a moving vehicle with an unmanned aerial vehicle,” Journal of Field Robotics, vol. 36, pp. 874–891, 2019.

20. [Y. Feng](#chapter13.xhtml#b13ref13_20), C. Zhang, S. Baek, S. Rawashdeh, and A. Mohammadi, “Autonomous landing of a UAV on a moving platform using model predictive control,” Drones, vol. 2, p. 34, 2018.

21. [T. Hoffmann](#chapter13.xhtml#b13ref13_21), and G. Prause, “On the regulatory framework for last Mile delivery robots,” Machines, vol. 6, no. 3, p. 33, 2018.

22. [J. Sunghun](#chapter13.xhtml#b13ref13_22), and K. Hyunsu, “Analysis of amazon prime air UAV delivery service,” Knowledge and Information Systems, vol. 12, no. 2, pp. 253–266, 2017.

23. [A. Goodchild](#chapter13.xhtml#b13ref13_23), and J. Toy, “Delivery by drone: An evaluation of unmanned aerial vehicle technology in reducing CO[2] emissions in the delivery service industry,” Transportation Research, Part D: Transport and Environment, vol. 61, pp. 58–67, 2018.

24. [A. Troudi](#chapter13.xhtml#b13ref13_24), S. A. Addouche, S. Dellagi, and A. El Mhamedi, “Sizing of the drone delivery fleet considering energy autonomy,” Sustainability, vol. 10, p. 3344, 2018.

25. [Website](#chapter13.xhtml#b13ref13_25) [https://www.findlatitudeandlongitude.com/l/Connaught+Place%2C+New+Delhi-110001/394735/](https://www.findlatitudeandlongitude.com)

26. [Website](#chapter13.xhtml#b13ref13_26) [https://in.mathworks.com/discovery/drone-simulation.html](https://in.mathworks.com)

27. V. A. Budnyaev, I. F. Filippov, V. V. Vertegel, and S. Y. Dudnikov, “Simulink-based Quadcopter Control System Model,” 2020 1st International Conference Problems of Informatics, Electronics, and Radio Engineering (PIERE), 2020, pp. 246–250. [https://doi.org/10.1109/PIERE51041.2020.9314676](https://doi.org/10.1109/PIERE51041.2020.9314676)

28. [P. Mittal](#chapter13.xhtml#b13ref13_28), and R. Singh, “A simulated dataset in aerial images using Simulink for object detection and recognition,” International Journal of Cognitive Computing in Engineering, vol. 3, 2022, 144–151, ISSN 2666-3074. [https://doi.org/10.1016/j.ijcce.2022.07.001](https://doi.org/10.1016/j.ijcce.2022.07.001)

# 14 Relevance and Predictability in Wireless Multimedia Sensor Network in Smart Cities

Raj Gaurang Tiwari, Pratibha, Sandip Vijay, Sandeep Dubey, Ambuj Kumar Agarwal and Megha Sharma

DOI: [10.1201/9781003353034-14](https://doi.org/10.1201/9781003353034-14)

## 14.1 INTRODUCTION

Nowadays, multimedia application over wireless sensor network (`WSN`) is in great demand and it becomes a necessary part of everyone's day-to-day life in the era of smart cities. Due to certain limitations of `WSN`, such as battery issues, security issues, low communication speeds, etc., multimedia sensors are getting more attention from researchers. The most beneficial thing is that multimedia sensors are capable of exquisite video, audio, image, and scalar sensor data and transfer multimedia data via the sensor network.

`WSN`s consist of up to thousands of sensor nodes that work together to detect varying conditions like sound, motion, temperature, vibrations, pressure, etc. at distinct sites using IoT sensors [[1](#chapter14.xhtml#ref14_1), [2](#chapter14.xhtml#ref14_2)]. There are many applications where `WSN`s work well like target tracking, medical applications, security surveillance, habitat detecting, etc. There is more probability of data loss over `WSN`s at the time of data transfer than over wired networks. In wired networks, data get lost generally due to congestion problems; however, in `WSN`, there are many numbers of reasons due to why data get lost like node failure, habitat interface, noise, unreliable link, unexpected damage, etc. [[3](#chapter14.xhtml#ref14_3)].

Due to the limitations of inherent characteristics of sensor nodes communication over `WSN` is not so reliable. Whereas reliability is the main characteristic of a quality-orientated `WSN` and it becomes more difficult to attain reliable communication due to the ubiquity of wireless links with greater inaccuracy rate. There are some more challenges introduced due to the demand of multimedia application requirements like time constraints, high bandwidth, and varying reliability requirements [[4](#chapter14.xhtml#ref14_4), [5](#chapter14.xhtml#ref14_5)]. These are key factors to outline communication protocol to get a proficient multimedia transmission in sensor networks.

[Figure 14.1](#chapter14.xhtml#fig14_1) shows a traditional `WSN`. A sink node or base station confederates in between the network and users. Normally a `WSN` network carries thousands of sensor nodes and all sensor nodes can easily interact with each other via radio signals. These nodes are well attired with advanced computing and sensing devices, power components, and radio transceivers. A sensor node transmits the message including the image to the sink node when it finds out about a highly prior event [[6](#chapter14.xhtml#ref14_6), [7](#chapter14.xhtml#ref14_7)]. Urgent messages have greater significance with the least end-to-end deferral, whereas fewer prior messages have a large end-to-end delay. Data that get delayed at the receiver will be discarded, and it cannot be displayed. So, there is a need to use an advanced transport protocol that is suitable and convenient for multimedia communication and can handle all restrictions of sensor nodes.

![FIGURE 14.1 Conventional wireless sensors network.](images/fig14_1.jpg)

[FIGURE 14.1](#chapter14.xhtml#b14fig14_1) Conventional wireless sensors network.

The main objective to use an advanced transport protocol is to get better reliable and energy-efficient real-time multimedia data transmission over `WSN` and to achieve the extended life period of the network. To avoid congestion, a congestion control mechanism is also required to get better quality multimedia data [[8](#chapter14.xhtml#ref14_8)].

The subsequent part of this chapter is arranged as follows: [Section 14.2](#chapter14.xhtml#sec14_2) throws light on diverse work done in the field of transport protocols. In [Section 14.3](#chapter14.xhtml#sec14_3), the transport protocols are discussed. [Section 14.4](#chapter14.xhtml#sec14_4) compares existing protocols. [Section 14.5](#chapter14.xhtml#sec14_5) concludes the chapter. In [Section 14.6](#chapter14.xhtml#sec14_6), possible future works are suggested.

## 14.2 RELATED WORKS

Real-time multimedia transmission over wired/wireless networks/`WSN` is already possible with a number of existing protocols. It was proposed that the real-time transport protocol (`RTP`) [[9](#chapter14.xhtml#ref14_9)] be used for the transmission of multimedia data across an IP-based network. It does not allow for the fragmentation or re-assembly of traffic. Implementing `RTP` over a `WSN` is not a viable solution due to the high electricity consumption of `RTP`.
