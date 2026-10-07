# Lightweight Cryptography Algorithms in IoT

as constrained application protocol (CoAP), IEEE 802.15.4 standard, and the IPv6 over low-power wireless personal area networks (6LoWPAN) are used to achieve data confidentiality.

+   C. Maintaining Privacy of Communication: The privacy of communication, data, and images are the main priority and security concerns. Such issues arise due to multiple resource-constrained device connectivity. User credentials such as passwords, IDs, images, and other sensitive information such as location need to be maintained.

+   D. Ensuring Mutual authentication: Authentication is required at different levels in the IoT framework as it involves sensors, Gateway Node (GWN), and user devices. The user’s authenticity should be verified before communication takes place [16].

# 11.4.2 Key Requirements for IoT Security

Therefore, an hour is required to use IoT communication so that the majority of people can effectively it. Confidentiality, authentication, and integrity are important requirements of IoT communication. The IoT devices are resource-constrained. Therefore, there must be a strong authentication method to identify the legitimate user of the system.

# 11.4.3 IoT Threats

All IoT devices are receiving data from sensors and transfer that data over the internet to communicating entities. Due to an open internet connection, such communication is susceptible to many attacks [17, 18]. Some attacks modify the user data while others can only get relevant information. Considering the above-mentioned cases, IoT systems are categorized as:

+   1. Denial of service (DoS): Either by jamming or flooding the network component. These attacks allow not legitimate users to access the communication link.

+   2. Impersonation attack: The attacker by masquerading identity behaves like a legitimate user and accesses the communication link. An adversary can access the sensor node and send false information to legitimate users. An authentication scheme is required to address this issue.

+   3. Reply attack: A malicious node by copying the original message sends the same message to the receiver. An authentication scheme should avoid the use of the same messages for each communication.

+   4. Mutual authentication: In an IoT communication scenario, mutual authentication is a must between users, sensor nodes, and base station.

+   5. Man-in-middle attack: Where the intruder may attempt to control the communication channel.