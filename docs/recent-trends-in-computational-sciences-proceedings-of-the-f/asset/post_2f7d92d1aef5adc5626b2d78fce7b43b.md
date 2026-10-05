
Recent Trends in Computational Sciences – Guraraj, Pooja & Flamminini (Eds)
© 2024 The Author(s), ISBN 978-1-032-42685-3

# Smart helmet for accident detection using IoT

H.T. Chethana
VVCE
ORCID ID: 0000-0003-0131-7395

S. Kunal & Sahil Jain
Department of Computer Science, Vidyavardaka College of Engineering, Mysuru,
ORCID ID: 0000-0093-1634-0309

ABSTRACT: Nowadays there is drastic increase in the number of accidents occurring in two-wheeler than other vehicles. Even though many rules and regulations are issued by the government to avoid accidents but many people will die due to accidents. The smart helmet is used for accident detection and wearing a smart helmet is needed while riding the vehicle. Attempt is made in this research paper which smart helmets can be used for accident detection using IoT. If the accident occurs, information such as the rider's current location, heart rate, the temperature of the rider, and consumption of alcohol by the rider is sent to the authorized person.

Keywords: Accidents, Alcohol Detection, Smart Helmet, Two Wheeler, Infrared Sensors

# INTRODUCTION

The Internet of things (IoT) refers to a connection with the internet rather than people. It is found in many fields such as security systems, home automation, medical and health care. IoT sensors provide the data and proves the conclusion. An accident is an event that occurs unexpectedly. Sometimes accidents can kill the person who may change the life of the own family. The number of accidents occurring in two-wheeler is more. Than 80,000 people died due to alcohol consumption and riding a two-wheeler without a helmet. A smart helmet is much needed to provide safety and security to two-wheeler riders. The death rate can be reduced by wearing a helmet during riding a two-wheeler.

Sensors such as alcohol sensor, infrared sensor, pulse rate sensor, DHT11 sensor, and ADXL sensor are used in the smart helmet which sends the necessary information to the authorized person. If the rider rides a two-wheeler by consuming alcohol, the probability of an accident is higher. If a heart attack occurs during riding, this condition should be checked and informed to the authorized person. Suppose the rider rides a two-wheeler by wearing a helmet, an alcohol sensor is used to detect whether the rider has consumed the alcohol or not through a buzzer, and the information is provided to the authorized person. Infrared sensors are used to detect whether any obstacle occurs while riding. The pulse rate

![](img/a35f8e852e0ee65e528c95ad0821783b_293_0.png)

Figure 1. Accidents rates through various modes.

DOI: 10.1201/97810003363781-40

sensor is used to detect the pulse of the rider and DHT11 sensors are used to detect the humidity and temperature [10]. By using the ADLX sensor, the accident can be detected and the message of the accident where the location is sent to the authorized person.

# 2 LITERATURE REVIEW

This discusses a brief literature review on various methods implemented for accident detection using IOT. In India, the rate of accidents and death of two-wheeler riders is increasing daily. Given these circumstances and to help the riders some applications have been developed.

Mohammed et al. [1] have proposed a system in which thermal sensing is done through the helmet which avoids spreading of covid-19. Jayasree et al. [2] have proposed a system that provides safety and security to construction workers during construction. accelerometer and gyroscope sensors are used for monitoring the workers.

Praveen M Dhulavagal et al. [3] proposed a system for accident detection. Global positioning systems (GPS), Global systems for mobile communication (GSM), and the are used to track the location of accidents. Jesudoss et al. [4] have proposed a system to detect whether a rider has consumed alcohol or not helps in preventing accidents. In this system, the bill will not start provided the rider has consumed alcohol. If any accident occurs, a notification will be sent to the authorized person. Sayan Tapadar et al. [5] have proposed a system with a vector mechanism to detect accidents and check whether alcohol is consumed by the rider during an accident.

Jayasree et al. [6] have proposed a system using the smart helmet to detect the drowsiness of the rider. This system also detects the alcohol consumption of the rider avoiding accidents. Kesari Shravya et al. [7] have proposed a system in which detection of accidents, consumption of alcohol by the rider, and if the rider is falling during an accident can be detected by using various sensors in smart helmets.

Mohamed Atiq Rahman et al. [8] have proposed a prototype with 3 modules helmet, an automobile, and a mobile application. If an accident occurs, the mobile application is used to send notifications to the police station as well as to the authorized person. Rohith Ravindran et al. [9] have proposed a system that is used to detect whether the rider is under stress or not riding a vehicle. Rithik Modi et al. [11] have proposed a system using IOT. This system detects whether the rider is wearing a helmet or not. If so, it detects the consumption of alcohol and the GSM module is used for sending a message to the authorized person if any accident occurs.

According to a literature review, most of the works [12–14] are addressed in the field of IOT for accident detection which will detect features such as alcohol consumption of the rider and the location.

# 3 PROPOSED SYSTEM

The accidents are increasing day by day, the proposed system provides safety to the rider. If an accident occurs, an emergency message is sent to the authorized person. The architecture of the proposed system using IOT is shown in Figure 2. It includes IR sensor, alcohol sensor, temperature, accelerometer, pulse rate sensor.

![](img/a35f8e852e0ee65e528c95ad0821783b_295_0.png)

Figure 2. Architecture of the proposed system using IOT.

The architecture of the proposed system consists of the following components. They are as follows

- **Battery**: A rechargeable battery of 12v is used in the proposed system to power the circuit and the proposed system needs a battery.
- **Raspberry Pi**: It is a small PC that is integrated with the pulse rate sensors, GPS, and camera module. The emergency message will be sent to defined contacts. With the help of a secure digital (SD) card, the proposed system can store all the information.
- **GPS Module**: It is a location tracker which is used to track the current location of the user. The information is used to find the exact address as such as street, area, or nearby which helps in easily reaching the location. If GPS is not working, longitude and latitude information is sent via mail or SMS.
- **GSM Module**: It is used for communication between the computer and the GPS system. The sim card is inserted within the mobile phones. To receive and send SMS, the GSM sim card should be registered to the proposed system.
- **Buzzer**: Buzzer is the one that generates an alarm when there is a detection of alcohol or not.
- **Alcohol Sensor**: It is used to detect whether the rider has consumed alcohol or not. If consumed, then the amount of alcoholic substance by the rider is also detected using an alcohol sensor. When the consumption of alcohol by the rider is detected, the authorized person can make the rider safe.
- **IR Sensor**: It is used to detect obstacles. While riding the bike, if the rider encounters any obstacle it can be detected and noticed.
- **ADXL (Accelerometer) Sensor**: Accelerometer is the device used to measure the speed. Using the ADXL sensor, accidents are detected when the angle of inclination changes towards gravity.
- **Pulse Rate Sensor**: It is used to check the pulse rate of the rider continuously. If it reaches irregular values, then the information is sent to the authorized one.
