
Following successful access, the next step is to obtain responses from compromised devices via `JTAG` or serial console [[31](#chapter8.xhtml#ref8_31), [32](#chapter8.xhtml#ref8_32)]. Attackers carry out this action by employing software cracking tools, some of which are listed in [Table 8.1](#chapter8.xhtml#tbl8_1).

### Table 8.1 Types of Software Attacks on IoT with Exploitation Tool

| Types of Attack | Name of Tool |
| --- | --- |
| **Web Testing** | * `ZAP` * `sqlmap` * `sslyze` * `Gobuster` |
| **Debugging** | * `GDB` * `OpenOCD` |
| **Bug Finder** | * `Flawfinder` * `Metasploit Framework` |
| **Binary Reversing** | * `IAD Pro` * `Radare2` * `Binaryaninja` |
| **Firmware Analysis** | * `Firmwalker`: `cpu_rec`, `binwalk` * `FAT` (`Firmware-Analysis-Toolkit`) * `FACT` (`Firmware Analysis and Comparison Tool`) |

## 8.3.2 Attacks on IoT Hardware

The hardware attack is targeted at the hardware system of the IoT infrastructure, and the steps used to exploit vulnerabilities in the devices are the same as the software attacks. Some of the hardware attack tools are represented in [Figure 8.3](#chapter8.xhtml#fig8_3) and are used to exploit IoT infrastructure. In the term "hardware attacks" [[31](#chapter8.xhtml#ref8_31)], they are furthermore divided into three types:

![FIGURE 8.3 Types of hardware attacker tools.](images/fig8_3.jpg)

[FIGURE 8.3](#chapter8.xhtml#b8fig8_3) Types of hardware attacker tools.

*   Non-invasive attacks
*   Semi-invasive attacks
*   Fully invasive attacks

### 8.3.2.1 Non-invasive Attacks

Attackers do not have direct access to device chips, but they can listen to IoT network traffic for a specific device and send forging data into `JTAG` or change the firmware update code to gain access, or send random or garbage data to devices to keep them busy working against their intended users [[31](#chapter8.xhtml#ref8_31), [33](#chapter8.xhtml#ref8_33)].

The non-intensive attacks are performed with a side channel attack, which is basically used to intercept network traffic, find vulnerabilities, and then execute exploitation. There are various types of attacks in this, such as:

*   **Timing attacks**: These attacks target the device's computation timing, and if a vulnerability is discovered, it is used as a loophole in the device's security, specifically for authentication. Another thing that can be done by this attack is to monitor the missed cache and processed cache on the chip of the device and compare the difference; based on that, the attacker is able to find out the instructions written on the chip, access register values, or regenerate the memory content of the device [[34](#chapter8.xhtml#ref8_34)].
*   **Hardware glitching**: An attacker can manipulate the device's power supply and damage its chips by increasing or decreasing the voltage. In addition, attackers can control the clock speed of the device chip that controls the instructions, slowing down the chip's performance [[35](#chapter8.xhtml#ref8_35)].
*   **Power analysis**: The power analysis is done for the intercepted devices based on the processed data and the written instructions. As a result, the attackers can obtain information about the data being processed on the chip. These can be done with simple power analysis, differential power analysis, the EM radiation channel, or the acoustic channel [[36](#chapter8.xhtml#ref8_36)].

### 8.3.2.2 Semi-invasive Attacks

This attack is performed on the chip physically. The attacker first analyses the target's location for the attack by disabling the device and emitting infrared light on the chip. In response to this action on the chip, photon emission is generated, and based on that, an attacker can analyse the chip and identify the target component to attack. Typically, this is used to break the device's encryption by changing the bit of the flip and employing leacher [[31](#chapter8.xhtml#ref8_31), [33](#chapter8.xhtml#ref8_33)].

### 8.3.2.3 Completely Invasive Attacks

This device attack requires expert knowledge and much more effort and cost than other attacks, but it is 100% successful. In this, the attacker modifies the chip by using an ion beam on it to generate a micro probing pattern of the chip, and the attacker can reconfigure it [[31](#chapter8.xhtml#ref8_31)].

## 8.3.3 Types of Attacks on IoT Infrastructure

Based on the above categorization of attacks on IoT infrastructure, these attacks can be divided into different types for IoT devices as follows.

### 8.3.3.1 Privacy Attack

This attack is performed on the IoT network to gather information about an individual or group of users from the network. This attack can be used to steal an authenticated user's identity by regenerating any type of security access card or password. The attack can also be used to learn about the targeted user's financial situation and details by determining how many devices and expensive services he or she is using. As in IoT network infrastructure, a large number of users are connected, so if any other kind of attack is made, that may also risk the privacy of the users [[37](#chapter8.xhtml#ref8_37)].

### 8.3.3.2 Device Attack

In the device attack, the main concept is to gain access to the IoT network by compromising any of the network devices. As a sensor, it will be compromised and used as a Trojan horse to send viruses on the IoT network that infect the whole network and provide access to attackers. This attack is very serious because if one device is infected, the whole network infrastructure will be affected. The process of detecting the infected device is time-consuming and costly, given the large number of connected devices. So, prevention is better than cure, and for that, device encryption and authentication may help [[31](#chapter8.xhtml#ref8_31), [37](#chapter8.xhtml#ref8_37)].

### 8.3.3.3 Network Attack

The attack is mainly targeting the communication performance of the IoT network through denial of service (`DoS`) attacks. It can cause communication delays or slow down network computation performance [[32](#chapter8.xhtml#ref8_32)]. This attack is also known as "network availability." An example of this attack is to send false information into the processing unit of a banking IoT network, which would take a huge amount of time to verify the authenticity of the information. For the authenticated user, these types of attacks cause panic or slow communication in the IoT network. The communication process in the IoT network is critical, and even a minor incident can result in high-cost damage and security intrusion. Using encrypted data transmission and a decentralized data storage system, the attack can be avoided [[32](#chapter8.xhtml#ref8_32), [37](#chapter8.xhtml#ref8_37)].

### 8.3.3.4 Data Attack

The attack on data, transmitting between devices, and providing storage or utility in the IoT network to compromise the network weakens or exposes the infrastructure. It is more dangerous than a duplex data communication system. A simple example of this is a smart metre manipulation by a customer to save amounts on bills; the manipulation may harm the whole network. To prevent this, data integrity is a must inside the IoT network [[32](#chapter8.xhtml#ref8_32)].

Based on these attacks on the IoT infrastructure and devices, it can identify the behaviour of different attacks and how much that are dangerous to the IoT infrastructure. [Figure 8.4](#chapter8.xhtml#fig8_4) shows the number of attacks reported by victims, and [Figure 8.5](#chapter8.xhtml#fig8_5) shows the losses reported from recent years. This report is generated based on some of the attacks listed in [Table 8.2](#chapter8.xhtml#tbl8_2) and from the Internet Crime Complaint Center (`IC3`) only for the United States of America [[42](#chapter8.xhtml#ref8_42)].

![FIGURE 8.4 Types of attacks in recent years and number victims.](images/fig8_4.jpg)
