
# Smart Homes 67

- Incorrect actuation (i.e., the operation was not as required by an authorized user).
- Prevented actuation (i.e., authorized user not able to initiate a desired actuation).
- Delayed actuation (i.e., actuation is initiated or completed later than desired by the user).
- Breach of physical privacy (i.e., covertly recording audio in a home).

Another category of home security focuses on the inside of the home autonomously detecting security-related situations (Dahmen et al., 2017):

- Detecting Resident-Based Target States: Systems using sensors learn inhabitant activity/activity patterns throughout the home to determine if intervention is needed. There are many methods using audio and video to detect individuals with the aging population. Sensors, wearables, and vibration sensors in the floor.
- Home-Based Target States: Sensing the location of inhabitants, looking for anomalies (i.e., finding data not conforming to expected behavior), and sensing visitors or intruders.
- Home-Anomaly Behavior Detection: Techniques to determine unexpected behavior patterns. Location in the home using mass doors and window sensors.
- Activity Anomaly Detection: A deeper level of activity recognition (i.e., health monitoring as sleep patterns or a decline in cognitive health).

## 6.2.2 Smart Home Design and Management

Security and privacy go hand in hand. A security breach causes a vulnerability that could expose an unsuspecting user to a privacy breach. For example, an IVA has four possible attacks: wiretapping, direct communication to an IVA-enabled device, malicious voice commands, and unintentional voice recognition. Figure 6.1 represents the four possible attacks in the IVA environment.

The IVA ecosystem is complex and heterogeneous, there are also various points where attacks can occur. In the first scenario, the IVA-enabled device is an attack that intercepts conversations between people and speakers by wirelessly the protocols that communicate with the cloud. In the second scenario, the speakers are compromised by hackers via eavesdropping devices that record what users say. Furthermore, in the third scenario, the hacker impersonates the user as a starting point for attacking the smart home to carry out criminal acts such as ordering things from the homeowner's account or opening the garage door to enter and steal from the home. Fourth, AI speakers inadvertently overhear what users say as wake-up words record it and send it to the cloud. This could be an unintentional recording attack because the user did not attempt to communicate with the speaker (Chung et al., 2017).

# What Every Engineer Should Know About IoT

![](img/41fdf2aa71adfa568d36836737f447e6_84_0.png)

**Figure 6.1** Threat scenarios in an intelligent virtual assistant (IVA) ecosystem. (Adapted from Chung et al., 2017).

O’Brolchain and Gordinin (2019) outlined recommendations to protect five perspectives on a SH as they pertain to vulnerable inhabitants:

- 1. Informational (e.g., controlling personal information),
- 2. Physical (e.g., solitude, mostly etc.),
- 3. Associational (e.g., medical context intimate experiences such as suffering and recovery from an illness),
- 4. Proprietary (e.g., anything related to a person’s DNA), and
- 5. Decisional privacy (e.g., taking medication in the home).

Some of the recommendations to increase privacy include:

- Permitting rights to set privacy settings,
- Obtaining electronic consent, making sure the consent is understood by the inhabitant,
- Anonymizing data, and
- Securing medical data.

Researchers have also attempted many ways to safeguard personal information privacy for SH services. Wang et al. created a taint propagation analysis model to analyze how software-defined networking uses sensitive information and investigates suspicious security vulnerabilities. Traditional taint analysis is a method to check which variables can be modified/contaminated by user/attacker input. The taint propagation model uses a weighted spanning tree analysis scheme to track data to. This method is focused on checking for exploits and suspicious behavior (Wang et al., 2016). Another solution for privacy management in the SH system is searchable encryption. Liu, Chen, and Huang (2019) proposed such a system – a searchable information retrieval of smart home data.

Typically, sensitive data is safeguarded with authentication methods. Authentication into the SH is a dominant theme researchers as privacy is a challenging quality requirement to integrate into a SH system. Research in this is at an early stage; thus, there are many recently proposed options. One authentication process proposed is access control mechanisms based on symmetric key cryptography. This provides secure access to IoT devices and stakeholders (Braeken et al., 2016). Other authentication schemes were proposed by Alshahrani and Traoire (2019) and Raniyal (2018). Alshahrani and Traoire (2019) proposed and validated design of an authentication scheme with dynamic/temporary identities and cumulative Keyedhash chain using various known attacks (i.e., eavesdropping, impersonation, man-in-the-middle, session key guessing). Raniyal et al. (2018) proposed two passphrase-protected device-to-device mutual authentication scheme.

In addition to data, another weak/vulnerability in SH are the smart appliances. Every added device adds a new way to access. In other words, remote access of devices such as smart appliances is highly desirable for SH system but come with a security risk. A more secure two-factor anonymous authentication was proposed in Shuai (2019). Others proposed encryption schemes for lightweight remote user authentication in the SH environment (Naoui, Elhdhili & Saidane, 2019). The goal of these authentication schemes is to know who is accessing the SH devices.

Along those same, an intrusion detection system (IDS) was proposed for nefarious hackers. The idea is that the IDS is shared between the devices on the home network. This distributed IDS aggregated data from the devices that is analyzed by an expert system using an anomaly-based data analysis (Gajweski et al., 2019). Other researchers provided architectures or frameworks focusing on security and privacy in an SH design:

- SHSec-based architecture is a design to secure and manage the SH network. This is a middleware to ensure the interoperability of SH devices. It also includes threat prevention and mitigation of network security attacks (Sharma et al., 2019).
- An architecture to be able to control the home system the same way set-top boxes are to stream multimedia was presented by Batalla and Gonciarz (2019). The home system is isolated from the Internet enabling secure communication from the homeowner to the SH.
- A Bluetooth, keyless door lock is proposed with an informal architecture (Dabbadeh et al., 2017). Bluetooth technology is more cost-efficient than radio frequency (RFID) and near-field communication (NFC) solutions. The system uses user detection, verification, request processing, and emergency actions.
- A SH security framework providing an integrity system to prevent security attacks and promotes data integrity using self-signing and access control (Kang, Moon & Park, 2017).
- A lightweight authorization scheme when heterogeneous SH IoT devices are integrated in an already-existing untrusted cloud SH framework (Chifor et al., 2018).
- An architecture using blockchain to store device transactions (Singh et al., 2019). The SH system is able to detect denial-of-service (DoS) and distributed-of-service (DDoS) attacks. The architecture consists for four main components: SH (i.e., IoT devices), blockchain (i.e., a distributed ledger), cloud computing (i.e., manages client requests), and a service layer (i.e., interacts with the service providers and SH users).

A risk analysis of SH automation system showed the human factor (e.g., connected devices user privacy, information registry exposing routes) and software components of the system (e.g., application programming interfaces (APIs) and mobile apps) were classified as the highest risk Jacobson, Boldt & Carlsson, 2016). The results indicate these risks can be minimized if a more general model of security is included in the design phase with the following steps:

- 1. Identify and categorize SH data in transit,
- 2. Perform analysis and describe the main risks to privacy and security,
- 3. Identify and implement mitigating measures to reduce risk, and
- 4. Develop a strategy for SH information management.

Diagnostic testing could reveal vulnerabilities to improve the trustworthiness of the SH. When testing an IVA system, it is important to understand where data is generated and where it flows. For example, the malfunctions occur during place by operating IVA-related services directly. Through the process of direct operation, we understand how the entire ecosystem of IVA is constructed. It roughly selects potential attack points out of the entire ecosystem where cyberattacks are likely to take place. Potential attack points can be hardware level, software level, network level, cloud level, and so on. Empirical experiments and fuzz testing (i.e., software testing that involves invalid, unexpected, or random data as inputs) are also effective to show vulnerabilities at each attack point (Yu et al., 2020). Through experimentation, it distinguishes a traditional attack from a completely new type of attack. This can help improve the reliability of IVAs in the future.

## 6.2.3 PHYSICAL SECURITY

Data privacy and protection is clearly an important aspect to a SH but will not prevent a traditional home invasion. Thus, SHs just like a traditional home still need physical security – but it can be smaller than the average motion sensor that alerts the owner with the captured video of a squirrel running across your path. For example, the traditional door chime and motion sensor to secure the physical security in a home can be transformed with IoT. Maybe we can determine exactly is at the door with a video doorbell camera, for example. When someone presses the doorbell, the app on the smartphone alerts you to check who visited the home remotely.
