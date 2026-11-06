
This situation is even more difficult to be programmed as IoT introduces a more number of treats than the Internet. IoT technologies are more exposed to unauthenticated intermediate message processors, open WiFi, multiple protocols, and spoofed sensors. Any vulnerable or compromised device in an IoT system is more dangerous than an intruder from outside and hence increases the probability of attacks. Also, all the devices of the IoT system are having their own memory and processing power, which enables them to bypass the control or to change it according to the intruder intentions. This also generates the possibility of newer treats to the system.

### 1.11.1 Need
A computer system can be secured by using latest security software, which works fine until the system is not connected to the Internet. Connecting to Internet invites much vulnerability in the system which requires updated security mechanisms to work continuously in order to keep the system secure. Many sophisticated software patches are available to achieve the high-end security, but this also requires enough memory and computing power at the host end. Unfortunately, in most of the IoT systems, the devices are having low computing power and minimum memory to accommodate such massive security mechanisms. This is the most important aspect which makes the IoT systems more vulnerable to security threats. Also, having the Internet access to the IoT system makes the situation even worse. Search engines like Shodan are the perfect example by which the openness of IoT systems may be visualized. And anything which is visible on Internet has cent percent chances to get hacked. Hence, to prevent such a hostile IoT environment, machine learning can be helpful to have a detailed analysis. IoT devices generated millions of data which could be a good source for machine learning approaches to have an estimation of abnormal activities and potential threats.

### 1.11.2 Levels of IoT Security
The IoT system consists of multiple protocols and various peer-to-peer communications among the devices involved. This multi-variant layers of operating systems require an effective security mechanism which should provide a comprehensive security solution while performing well on all the key points of the IoT system. Securing an IoT system requires implementation of security subroutines mainly at the following four levels.

#### 1.11.2.1 Device
It is directly related with all the hardware and respective drivers associated with the devices which are the part of the IoT system deployed. It introduces the security at the physical layers of systems by implementing device authentication through MAC addresses and encryption keys, secure booting, and identification of devices.

#### 1.11.2.2 Communication
It refers to the concept of securing the communication channels among the devices connected through an IoT system. Most of the communication channels are wireless, and hence the potential threats of attacking on these channels are very high. Sophisticated mechanisms like advanced public encryption, firewalls, web socket, virtual tunneling, and Secure WiFi are used to secure these open communication links. Also, due to often communication delays, these security mechanisms should be fast enough to cater the needs within a stipulated time frame.

#### 1.11.2.3 Cloud
It refers to the backbone of IoT system, where all the data are collected, classified, analyzed, processed and then routed back in the system. It is the main software which is responsible for meeting the objectives of overall IoT system. Securing this part of IoT system is the most complex task, as most the security breaches are targeted here.

#### 1.11.2.4 Life cycle
This is somewhat more comprehensive approach in the IoT system to provide security to the overall system while managing the system prompt and updating all the time. It ensures that the security mechanisms placed at all the fore-mentioned points should work cohesively with each other to build a higher level security protection. Various merits like risks analysis, auditing, and activity assessment are regularly monitored to provide quick and correct results by the IoT system.

![](Images/fig0001.jpg)

### 1.11.3 Automation of Security Mechanisms
With the growth of IoT systems, the requirement of security mechanisms has also increased. Generally, these activities are handled manually, like allotting and revoking of certificates, blacklisting of malicious nodes, and isolating the compromised devices. Better security systems are needed to be incorporated in IoT systems, which should not only be efficient but intelligent enough to minimize the human intervention for taking small decisions. For example, simple classification of malicious nodes as per their behavior can be taken care by an intelligent subroutine which can learn by historic data. This automation will enable the IoT system to take appropriate security decision while making it autonomous. There are many ways through which we can achieve automation, like we may create an inference system, or a neural network, or combination of any machine learning techniques. Machine learning techniques can be classified as (1) supervised machine learning, where predictions are made as per a given set of samples by searching for patterns within the labels assigned to data points, (2) unsupervised machine learning, where there are no labels associated with data points. It initially organizes the data into a group of clusters to describe its structure for further analysis, and (3) reinforcement machine learning, where an action is to be taken first, and later learn how good the action was. Over the time, it changes the strategy to learn better and achieve the best reward. Machine learning for securing IoT systems can be applied at device points or network points.

#### 1.11.3.1 Device-based solutions
The major concern in device-based security solutions is the low memory and less storage capacity for executing the subroutines. For a better analysis of threats and the record keeping of signatures and authentication, the devices are required to be equipped with enough processing power and storage. Various techniques like threading can help to implement high-level protection in less resources.

#### 1.11.3.2 Network-based solutions
Securing IoT systems can also be done at the network level by registering all the devices to the network and regular auditing of data traffic to and from the IoT system. And if anything goes beyond expected or suspicious, alarms can be activated for safe guarding the data and control points of the system. This traffic monitoring scheme could be used to identify and classify the compromised nodes based on their behavior and past experiences.

### 1.11.4 Classification of IoT Security Techniques

#### 1.11.4.1 Network security
Protecting and securing the IoT network is the key for the high-end security mechanism. However, it is often a more complex task due to the heterogeneous communication protocols, standards, and most importantly device capacities. Firewalls and intrusion prevention methods can be applied on network to avoid the potential threats from intruders.

#### 1.11.4.2 Authentication
It enables the users to authenticate the trusted IoT devices by using pin codes, certificates, or biometrics. It is a manual but yet a powerful technique to avoid attacks.

#### 1.11.4.3 Encryption
It is always better to encrypt the data and control to achieve better security. Various encryption protocols may be used to keep the data safe from outsiders. Public or private key encryption may be used secure the IoT system.

#### 1.11.4.4 Analytics
