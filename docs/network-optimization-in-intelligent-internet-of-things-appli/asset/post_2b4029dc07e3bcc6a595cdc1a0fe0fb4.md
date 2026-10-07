
314 Network Optimization in Intelligent IoT Applications

# TABLE 18.1 (Continued)
Description of Related Work

| Author | Description | Key Findings | Limitations |
| --- | --- | --- | --- |
| Singh et al. (2002) [11] | Concept of cybersecurity and electronics have been integrated in Intel device. | Multiple purposes such as data cloning and jamming | Limited to death and cloning attacks |
| Chan and Chun (2021) [12] | Attacks particular to beam systems are explored. | Beacons have been focused | Accurate outlier detection can be achieved |
| Kondaveeti (2021) [13] | Prototyping with Arduino has been analyzed and compared. | Best techniques while prototyping with Arduino have been listed. | More conventional techniques could have been identified |
| Najath et. (2022) [14] | Low-cost network jammer that creates between 315 MHz and 433 MHz has been described. | Illegal activities using DoS are prevented | Applicable to area only within the 100-meter range |
| Pahlavan and Krishnamarthy (2021) [5] | The study provides an overview of the evolution of Wi-Fi technology and its applications that has been experienced in the last few decades. | The role of Wi-Fi in our daily lives has been discussed. Moreover, how the IEEE 802.11 standards for Wi-Fi had been first implemented and radiofrequency (RF) cloud enables some important cyberspace applications. | The features should be same between two devices which might not be possible as the electronic implementation of a device is unique which results in the differences. |

## 18.3 JAMMING TECHNIQUES

When a transmitter detects a faulty or busy signal at a receiver, a Wi-Fi jammer uses radio frequencies to make the communication medium busy by interfering with wireless communications [4]. Attacks on the physical layer are the ones that typically targeted by jamming; however, cross-layer attacks can also occur. In this section, we have elaborated on various types of jammers and the placement of jammers to maximize the jammed area.

## Wi-Jammer, a Threat to IoT Networks

### 18.3.1 TYPES OF ATTACKS

Attacks mounted through Wi-Fi jammers come under Denial-of-Service (DoS) attacks. Under these attacks, malicious nodes interfere with legitimate network communication [6–8].

### 18.3.1.1 Deauthentication Attack (Deauth)

Denial-of-service attacks, such as a deauth attack, target user-to-wireless access point communication. In this attack, the attacker forces devices to lose access and reconnect to a network controlled by [9, 10].

In other words, it is a type of DoS attack interfering with communication between routers and devices. One of the main purposes of deauthentication is to force the user already connected to the router or wireless access point to connect to an evil twin access point which can then be used for capturing network packets transferred between the user and the router.

### 18.3.1.2 Clone Beacon

A clone beacon attack is a spoofing cyberattack that tricks the user to connect to a fake Wi-Fi access point that appears be part of a legitimate network [11]. The user gets access to information from network traffic, including login credentials. A clone beacon attack is a kind of wireless attack in which an attacker creates a replica or clone of a legitimate connection to devices into a fake access point. Once connected, the attacker can eavesdrop on the traffic passing between the victim's device and the Internet, or launch further attacks against the victim, such as a man-in-the-middle attack or a phishing attack [12].

### 18.3.1.3 Beacon

The purpose of this attack is to confuse wireless clients by sending several fake beacon frames. This makes things difficult to find a genuine network, and prevents the wireless clients from connecting to their preferred networks [11]. A beacon is a signal periodically transmitted by wireless access points to announce the availability of a network. In a beacon attack, the attacker creates a fake beacon with the same network name (SSID) and other network parameters as the legitimate access point [12]. The fake beacon is transmitted on the same frequency and with the same power as the legitimate beacon, so devices within range may be deceived into connecting to the fake access point instead of the legitimate one.

### 18.3.2 MOUNTING AN ATTACK

This subsection presents the working of Wi-Fi jammer in a step-wise fashion:

- Step 1: Initially, a user and the router will maintain a connection between them. The user will first send the request for authentication and association.
- Step 2: Successful authentication refers to successfully completing the authentication process between a user and a Wi-Fi access point, which is router here.

When a device wants to connect to a Wi-Fi network, it must go through an authentication and encryption process to establish a secure connection. The authentication process typically involves exchanging handshake messages between the client and the access point to verify their identities and establish a secure connection.

- Step 3: A successful association involves establishing a connection between a user and a Wi-Fi access point by sending an association request containing the client's information.

When a Wi-Fi client device wants to join a Wi-Fi network, it needs to perform an association process. During this process, depending on the client's capabilities and supported encryption methods. The access point responds with an association response, indicating whether the association was successful or not.

- Step 4: A disassociation notification or deauthentication notification refers to a message sent by the access point to a connected client device, instructing it to disconnect from the Wi-Fi network.

Deauthentication is a legitimate mechanism in Wi-Fi networks and is used by access points to terminate the connection. It can be initiated for various reasons, including security purposes, network management, or to enforce access control. The objective is to disrupt or block the wireless communication between the client and the access point, preventing successful authentication.

img/e0b54a8aa310236950fcfeb80a6_332_0

FIGURE 18.1 Flow chart of mounting an attack.

## Wi-Fi Jammer, a Threat to IoT Networks

A jammer can disrupt the handshake process by interfering with the-- signals, causing the authentication to fail. As a result, the client device won't be able to connect with the access point and access the network. Moreover, it can prevent successful association. As a result, the client device won't be able to join the network.

The flow chart for mounting the attack is shown in Figure 18.1.

## 18.4 SYSTEM REQUIREMENT

System requirements refer to the minimum specifications and capabilities that a computer or other electronic device must meet to run a particular software or operating system. This section discusses both hardware and software requirement for Wi-Fi jammer.

## 18.5 HARDWARE REQUIREMENT

For building a Wi-Fi jammer, NODEMCU, charging module, and booster module are required as discussed below:

### 18.5.1 NODEMCU

NODEMCU is an open source IoT platform with inbuilt microcontroller and Wi-Fi module as shown in Figure 18.2. It contains ESP8266 Wi-Fi chip on it. It is programmed using Lua scripting language. LUA scripting language is a programming language used to program various ESP boards.

### 18.5.2STER MODULE

The booster module is a DC-DC connection that boosts the voltage from its input to its output shown in Figure 18.3. In our device, the booster module will enhance the battery voltage from 3.3V to 5V.

### 18.5.3 CHARGING MODULE

This module as shown in Figure 18.4 is mainly useful in charging rechargeable batteries using the constant charging method. The battery’s energy is used to power the device that it is connected to, and it will gradually decrease over time. When the battery’s charge is depleted, it needs to be recharged in order to continue providing power. A charging module, on the other hand, is a device that is used to charge the battery. It takes an external power source, such as a wall outlet or a USB port and converts it into the proper voltage and current to charge the battery.
