
## 6.2.1 Design of accident detection platform

A complete automatic traffic accident detection platform should include hardware and software. The hardware includes traffic flow detector, communication facilities, and central computer for data processing; and the software includes data collection, processing, and data algorithm for accident detection.

## 6.2.2 Operation mode of accident detection platform

At present, the more effective operation mode of accident detection platform is as follows:

- (1) Finding sudden change data information. After the traffic accident, the traffic data obtained by the platform will have a sudden change, mainly in traffic flow, occupancy, and speed.

  For example, due to the occurrence of traffic accidents, it may cause a sharp decline in road capacity and form a traffic bottleneck. Through the real-time detection of the sharp reduction of traffic flow on the road section, the location of traffic accidents can be calculated.

  After the traffic accident, it causes the vehicle to drive slowly, which results in the occupancy rate of the detector suddenly increasing. Besides, the occurrence of traffic accidents results in traffic jams, so that the speed detected by the adjacent detector is suddenly reduced. By acquiring and analyzing the aforementioned data, we can explain the abnormal traffic conditions on the road so as to measure and calculate the traffic accidents.

- (2) Finding data deviation from normal value. The data information obtained by the detection platform deviates greatly from the historical information of the place and the time period in the past, which also indicates that there is a traffic accident on the road in the time period and the place.

  For example, the traffic flow data detected by the detector is much smaller than the historical average value, indicating that traffic accidents may occur upstream or downstream of the detector. The occupancy rate detected by the detector is much larger than the previous historical data, indicating that there is a traffic accident downstream of the detector. The vehicle speed detected by the detector is much smaller than the historical data, indicating that traffic accidents may occur downstream of the detector.

The detection of sudden change data and data deviation from normal value is an important operation mode of traffic accident detection platform. In the actual operation of the platform, only one or two data changes cannot determine the traffic accident, and different kinds of data changes need to be combined to judge.

## 6.2.3 Location of traffic accident

The location of the traffic accident cannot be determined only by the data provided by the road section detector. After the data information is synthesized, the detection system can determine whether the traffic accident happened in the upstream or downstream of a section, but the distance from the section cannot be determined.

Therefore, the accident monitoring platform needs to integrate the data obtained by the adjacent section detector on the highway so as to determine the specific location of the traffic accident.

In fact, after the traffic accident, the data collected by the upstream detector and the downstream detector are different. Using this feature, the detection platform can determine the location of the traffic accident section as follows:

- (1) Data from upstream detector. When the traffic accident occurs, the capacity of the road section at the location where the traffic accident occurs suddenly drops, forming a traffic bottleneck, which will cause traffic congestion at the upstream of the location where the accident occurs. Therefore, the traffic data detected by the detector will have the following characteristics: reduced speed, increased occupancy rate, and reduced traffic flow. By using these three data features, the traffic accident monitoring platform can judge that the location of the traffic accident is at the downstream of the location section of the monitor.

- (2) Downstream detector. When a traffic accident occurs, the change of traffic digital information detected by the downstream detector is different from that detected by the upstream detector. Generally speaking, the changes of traffic flow digital information detected by the downstream detector have the following three characteristics: increased vehicle speed, reduced occupancy rate, and reduced traffic flow.

  The increase in vehicle speed is due to the decrease in the traffic capacity of the upstream section of the detector after the traffic accident occurs in the upstream section of the detector, resulting in the decrease in the downstream traffic density. Therefore, the vehicle speed will naturally produce a significant increase. When the vehicle speed is increased, the number of share obtained by the downstream detector section or the number of share on the lane where the accident occurred, will be significantly reduced. Similarly, the data of traffic flow obtained by the downstream detector section will be significantly reduced.

In a word, by making full use of the function of data and collecting and detecting the traffic data information, we can diagnose the traffic condition on the road and find the time and place of traffic accidents in time.

## 6.3 Passenger Flow Detection Platform

Passenger flow data of traffic operation is an important data base of traffic planning, design, and operation management. Using the passenger flow detection platform to carry out scientific statistical analysis on the passenger flow data of urban traffic operation can provide a basis for the evaluation of traffic operation, assist and support the management department and the operation unit in formulating corresponding plans, and also provide data support for the planning and design of public transport.

In April 2017, Chongqing Traffic Administrative Law Enforcement Team released the news that Chongqing's first comprehensive traffic law enforcement closed management system was officially launched in Chongqing north railway station. The system can not only monitor the number of vehicles passing in real time but also reflect the demand of transportation capacity of North Station.

Four new eagle eye panoramic cameras added to the system can achieve 90% coverage of the ground monitoring of the North Square. More than 50 surveillance cameras are respectively installed on the first floor of the North Station, the exit of passengers, and other places so as to realize the coverage of the underground monitoring of the North Station. Through the surveillance video, the real-time situation of the scene can be understood.

The system can reflect the number of vehicles passing in real time. Eagle eye monitoring will clearly find the main gathering place of the crowd, especially in the peak period of the traffic flow in Spring Festival and National Day holidays. It can reflect the capacity demand of the North Station in real time so as to allocate the capacity in time to ensure the evacuation of passengers.

The operation result of the passenger flow monitoring platform is an important basis for traffic operation and passenger flow data analysis. According to the location and time data of passengers and vehicles entering in and exiting to a certain area, the time and space rules of passenger flow can be analyzed to reflect the actual passenger flow demand.

Moreover, the traffic operation manager also needs to rely on the passenger flow monitoring platform to understand, analyze, and control the dynamic situation of traffic passenger flow under abnormal conditions, for example, the change rule of passenger flow in special weather conditions, holidays, and large-scale activities such as concerts and sports events.

Let us take the metro passenger flow detection platform as an example to demonstrate its application of big data.

## 6.3.1 Design of passenger flow detection platform

The function of passenger flow detection platform is to monitor the number of current passenger flow, obtain accurate data of passenger flow, and analyze it so as to realize dynamic and network management control of passenger flow, and then achieve comprehensive control of the passenger flow. Only when the passenger flow detection platform can fully and scientifically collect and use big data can it help the traffic management department to humanely disperse the passenger flow so as to effectively cope with the peak of large passenger flow and improve the operation efficiency.

A mature passenger flow detection platform consists of four parts:

- (1) Passenger flow monitoring module. In this module, the number and flow direction of passengers in each region are obtained in real time,
