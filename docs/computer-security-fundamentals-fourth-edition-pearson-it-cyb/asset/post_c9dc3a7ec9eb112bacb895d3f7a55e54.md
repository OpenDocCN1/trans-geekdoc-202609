
crossover cable, but you could connect 2 computers directly. But what do you do if you want to connect more than 2 computers? What if you have 100 computers that you need to connect on a network? There are three devices that can help you to accomplish this task: the hub, the switch, and the router. These each use Cat 5 or Cat 6 cable with RJ-45 connectors and are explained in the following sections.

## The Hub

The simplest connection device is the hub. A hub is a small box-shaped electronic device into which you can plug network cables. It will have 4 or more (commonly up to 24) RJ-45 jacks, each called a port. A hub can connect as many computers as it has ports. (For example, an 8-port hub can connect eight computers.) You can also connect one hub to another; this strategy is referred to as “stacking” hubs. Hubs are quite inexpensive and simple to set up: Just plug in the cable. However, hubs have a downside. If you send a packet (a unit of data transmission) from one computer to another, a copy of that packet is actually sent out from every port on the hub. All these copies leads to a lot of unnecessary network traffic. This occurs because the hub, being a very simple device, has no way of knowing where a packet is supposed to go. Therefore, it simply sends copies of the packet out all of its ports. While you may go to your favorite electronics store and buy something called a “hub,” true hubs no longer exist. What you are really getting is a switch, which we will discuss later in this section.

## The Repeater

A repeater is a device used to boost signal. Basically if your cable needs to go further than the maximum length (which is 100 meters for UTP), then you need a repeater. There are two types of repeaters: amplifiers and signals. Amplifier repeaters simply boost the entire signal they receive, including any noise. Signal repeaters regenerate the signal, and thus don’t rebroadcast noise.

## The Switch

A switch is basically an intelligent hub; it works and looks exactly like a hub, with one significant difference. When a switch receives a packet, it sends that packet only out the port for the computer to

- **802.11a:** This was the first widely used Wi-Fi; it operated at 5GHz and was relatively slow.
- **802.11b:** This standard operated at 2.4GHz and had an indoor range of 125 feet with a bandwidth of 11Mbps.
- **802.11g:** There are still many of these wireless networks in operation, but you can no longer purchase new Wi-Fi access points that use 802.11g. This standard includes backward compatibility with 802.11b. 802.11g has an indoor range of 125 feet and a bandwidth of 54Mbps.
- **802.11n:** This standard was a tremendous improvement over preceding wireless networks, providing bandwidth of 100Mbps to 140Mbps and operating at frequencies of 2.4GHz or 5.0GHz over an indoor range of up to 230 feet.
- **IEEE 802.11n-2009:** This technology provides bandwidth of up to 600Mbps with the use of four spatial streams at a channel width of 40MHz. It uses multiple-input multiple-output (MIMO), in which multiple antennas coherently resolve more information than is possible using a single antenna.
- **IEEE 802.11ac:** This standard, which was approved in January 2014, has throughput of up to 1Gbps and at least 500Mbps. It uses up to 8 MIMO.
- **IEEE 802.11ad Wireless Gigabit Alliance:** Supports data transmission rates up to 7Gbps, which is more than 10 times faster than the highest 802.11n rate.
- **IEEE 802.11af:** Also referred to as “White-Fi” and “Super Wi-Fi,” this standard, which was approved in February 2014, allows WLAN operation in TV white space spectrum in the VHF and UHF bands between 54MHz and 790MHz.
- **802.11aj:** IEEE 802.11aj is a rebranding of 802.11ad for use in the 45GHz unlicensed spectrum available in some regions of the world (specifically China).

The methods for securing Wi-Fi have evolved over the years. First there was Wired Equivalent Privacy (WEP), then Wi-Fi Protected Access (WPA), then WPA2, and most recently WPA3.

WEP uses the stream cipher RC4 to secure the data and a CRC-32 checksum for error checking. Standard WEP (known as WEP-40) uses a 40-bit key with a 24-bit initialization vector (IV) to effectively form 64-bit encryption. 128-bit WEP uses a 104-bit key with a 24-bit IV.

Because RC4 is a stream cipher, the same traffic key must never be used twice. The purpose of an IV, which is transmitted as plain text, is to prevent any repetition, but a 24-bit IV is not long enough to ensure this on a busy network. The way its IV is used also opens WEP to a related key attack. For a 24-bit IV, there is a 50% probability the same IV will repeat after 5000 packets.

WPA uses Temporal Key Integrity Protocol (TKIP), which is a 128-bit per-packet key, meaning that it dynamically generates a new key for each packet.

WPA2 is based on the IEEE 802.11i standard and provides the Advanced Encryption Standard (AES) using the Counter Mode-Cipher Block Chaining (CBC)-Message Authentication Code (MAC) Protocol (CCMP), which provides data confidentiality, data origin authentication, and data integrity for wireless frames.

WPA3 requires attackers to interact with your Wi-Fi for every password guess they make, making it much harder and time-consuming to crack. With WPA3’s “Wi-Fi Easy Connect,” however, you can connect a device by merely scanning a QR code on your phone. One of the important new security features is that with WPA3, even open networks will encrypt your individual traffic.

## Bluetooth

Short-distance radio using the 2.4GHz to 2.485GHz frequency. The IEEE standardized Bluetooth as IEEE 802.15.1, but it no longer maintains the standard. This standard enables devices to discover other Bluetooth devices within range. The name comes from king Harald “Bluetooth” Gormsson, a tenth-century Danish king who united the tribes of Denmark. The idea behind the Bluetooth technology is that it unites communication protocols. (The king’s nickname has been explained a few different ways. One explanation is that he had a bad tooth that was blue. Another is that he was often clothed in blue.) The speed and range of Bluetooth depends on the version, as outlined in Table 2.3.

## Table 2.3 Bluetooth Bandwidth and Range

| Version | Bandwidth | Range |
|---------|-----------|-------|
| 3.0     | 25Mbps    | 10 meters (33 feet) |
| 4.0     | 25Mbps    | 60 meters (200 feet) |
| 5.0     | 50Mbps    | 240 meters (800 feet) |

## Other Wireless Protocols

There are several other wireless communication protocols, including the following:

- **ANT+:** This wireless protocol is often used with sensor data such as in bio sensors or exercise applications.
- **ZigBee:** This standard was developed by a consortium of electronics manufacturers for mainly residential applications of wireless devices related to appliances and security. It is based on the 802.15.4 standard. What appears to be confusing is that the standard is represented by the name “ZigBee” rather than a number. The term ZigBee is used similar to the way the term Wi-Fi is used.
- **Z-Wave:** This wireless communications protocol is used primarily for home automation. It uses a low-energy radio for appliance-to-appliance communication using a mesh network.

## Data Transmission

We've seen, briefly, the physical connection methods; but how is data actually transmitted? To transmit data, a packet is sent. The basic purpose of a cable is to transmit packets from one machine to another. It does not matter whether the packets are part of a document, a video, an image, or just some internal signal from the computer. So what, exactly, is a packet? As we discussed earlier, everything in a computer is ultimately stored as 1s and 0s, called bits, which are grouped into sets of eight, each called a byte. A packet is a certain number of bytes divided into a header and a body. The header is 20 bytes at the beginning of the packet that tells you where the packet is coming from, where it is going, and more. The body contains the actual data, in binary format, that you wish to send. The aforementioned routers and switches work by reading the
