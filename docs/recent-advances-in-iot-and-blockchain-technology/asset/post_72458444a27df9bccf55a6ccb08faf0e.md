
pp. 92-107.

[http://dx.doi.org/10.1016/B978-0-12-820203-6.00010-2]

[63] K. Singhal, and D. Sharma, "Fuzzy Systems in Medicine and Healthcare: Need, Challenges and Applications", In: Soft Computing Applications and Techniques in Healthcare. CRC Press, 2020, pp. 139-162.

## Application of IoT in Patient Health Monitoring System

Rinky Dwivedi1*, Harshit Mittal1, Manik Agarwal1 and Sahil Dwivedi1

1 Department of Computer Science and Engineering, Maharaja Surajmal Institute of Technology, C-4 Janakpuri, New Delhi 100058, India

Abstract: The Internet of Things (IoT) is the infrastructure that enables the process of collecting data using various devices which in turn communicate with each other and store this data over the cloud. This helps to retrieve, analyze, and communicate data to any part of the world faster with great efficiency. IoT has indeed opened the doors to endless new possibilities in different areas and industries. From smart home appliances to remotely observing and controlling different objects to self-driven cars and whatnot. The healthcare industry has still not leveraged the true power of this modern IoT revolution. Specifically, when it comes to monitoring the health of elderly people, the techniques used today are still not robust and lack conviction. This has been an area of concern for a long time, and it is an even bigger challenge to remotely monitor the health condition. In this paper, our goal is to depict the current situation of the technologies of the health monitoring projects based on IoT and propose an improvement in the actual practices currently prevalent in remote monitoring of the health of elderly people. We will also try to forecast the trend of various health parameters demonstrated in the paper beforehand to make the concerned people aware with precision if any alarming situation is spotted so that instant action can be taken, thus ensuring a reduction of casualties.

Keywords: Arduino, Internet of Things (IoT), Remote monitoring, Forecasting, Moving Averages, Health Assistant.

## INTRODUCTION

The phrase “Internet of Things” is thought to have been coined at the beginning of the century, when work on the MIT Auto-ID Center [1] was underway to develop a smart identification system that would help minimize error rates while boosting efficiency and automating the process. However, the notion of IoT has grown rapidly in many ways since then, such as with the help of a large number of small networks that can stay linked to each other and transfer data to the main network without the need for human interaction.

* Correspondence author Rinky Dwivedi: Department of Computer Science and Engineering, Maharaja Surajmal Institute of Technology, C-4 Janakpuri, New Delhi 100058, India; Tel: 9958433922; E-mail: rinkydwivedi@msit.in

Quality of service in healthcare has always been under constant criticism in the modern era, as it is a very touchy subject. Monitoring the health of elderly people specifically has been a concern for a long time. In this modern world, most people have a hectic work life with long hours of continuous work, due to which the elderly are left neglected and vulnerable. It is difficult to keep a constant check on the elderly people in the house. Also, keeping an attendant or a servant is very expensive nowadays. In this situation, remote health monitoring based on IoT can help solve the problem.

IoT provides the means by which it is possible to collect and analyze data remotely without any human interaction. So, this helps us to possibly foresee and minimize any future hazard with precision and further notify the concerning authority like the family member or the physician if there is an alarming situation. IoT is important for this project for two main reasons. Firstly, it is automated, so no human intervention is needed. And secondly, because of automation, the process is less prone to errors, i.e., having a more robust system indicating a better quality of service.

In this paper, we describe how we collected data regarding three health parameters, namely temperature, heartbeat, and lung capacity, and used the time series algorithm to forecast these parameters to cope with any alarming situation looming in the future and take necessary actions beforehand to prevent it.

The paper is structured in the following way; the introduction is included in section 1. In section 2, previous works related to IoT in healthcare being discussed. The proposed system is described in section 3, which includes the methodology, block diagram, and system architecture. section 4 describes the equipment details. Section 5 contains the performance measurements and section 6 includes the conclusion. Finally, section 7 contains the future scope.

## RELATED WORK

Extensive research on the topic related to the system shows a very few of the related works could build their preliminary framework and prototype of the system. Some of the works like the research conducted on Ambient Assisted Living (AAL) [2] did more of a literature survey of the state of its present condition of the monitoring system via IoT. They also tried to identify and highlight the critical issues and the quality of service as well as the user-driven experiences in their work. Some others worked on showing or highlighting the importance of IoT in the health sector and some proposals for the health monitoring architectures.

Some related findings used specific models for the health monitoring aspect. Like the abstraction of the **Model-Driven Tree Reference Model (MDTRM)** [3], where they explained the necessity of this model in the health field as well as identifying the complexities of the models. They also benchmarked the models which came in handy for the initial phase of this research.

One of the other related models we found is **General Domain Model Architecture (GDMA)** [3], the health monitoring and sensing with cloud processing was also a helpful source behind the research, as it was useful for generating ideas to get raw data from wearable devices which are compatible and capable of measuring many physical values which we can be used to obtain meaningful results.

**Masimo Radical-7** [4], a health monitor for the clinical environment helps to collect data and wirelessly transmit it for ongoing display. This provides high-resolution display of information with higher graphical capabilities. It also has a touch-based user interface. But as it can already be assumed how cost-effective it is, it can’t send an alarm message to notify of any emergencies. **Freescale Home Health Hub reference platform** [4] stores patient data in the cloud via various sensors, which the people related to the patient can have access to. This platform too can’t notify about any alarming situations to the people engaged with the patient.

Some surveys of ours also lead us to projects which even discussed monitoring the health whole area through wireless network sensors [5, 6]. They also tried to share their ideas by giving a model of their frameworks like cloud-based processing [7] and big data [8-14]. However, these systems face several attacks, and research works are being carried out to detect such activities [15].

## SYSTEM ARCHITECTURE

### A. System Structure

In this paper, we used three health parameters that we will monitor using three different sensors namely body temperature, heartbeat, and lung capacity as shown in Fig. (1). Once we have collected all the sensors, the first step is to integrate these sensors into the microcontroller. A microcontroller is a cheap, small-sized computer, that can be portable and multitasking. We have used Arduino Uno as our microcontroller in the paper. Also, to keep a check on the values that are being collected by the sensors in real-time we have attached an LCD to our microcontroller for this purpose.

![](img/acd73a27093a44d669c4d9968aa1626b_113_0.png)

Fig. (1). Architecture of IoT-based Remote Patient Monitoring System.

Integration of sensors with the microcontroller is not enough to send our data over the internet. We need a WIFI module that will send our collected data over the internet.

For this purpose, we integrate the ESP8266 WIFI module into our microcontroller so that we could send the data over the internet and store it on our server.

After integrating and configuring all the sensors and WIFI Module with the microcontroller, we send our data collected from three sensors as a query string over the internet to the server where it is stored in the database (see Fig. 2).

Once we have enough data collected, we start forecasting the trend of the three health parameters. Forecasting is done by using the time series algorithm. In this paper, we have compared the results of three techniques under the time series algorithm namely naive moving average, simple moving average, and weighted moving average.

A moving average is a calculation used to analyze data points by creating a series of averages of different subsets of the full data set. By calculating the moving average, the impacts of random, short-term fluctuations on the values of various health parameters over a specified time frame are mitigated.
