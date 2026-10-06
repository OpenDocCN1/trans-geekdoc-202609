# Network Architecture and Design 267

confidentiality, and CCMP (Counter Mode CBC MAC Protocol) to create a Message Integrity Check (MIC), which provides integrity. The less secure WPA (without the “2”) was designed for access points that lack the power to implement the full 802.11i standard, providing a better security alternative to WEP. WPA uses RC4 for confidentiality and TKIP for integrity. Use of WPA2 is recommended over WPA.

# Bluetooth

Bluetooth, described by IEEE standard 802.15.1, is a Personal Area Network (PAN) wireless technology, operating in the same 2.4-GHz frequency as many types of 802.11 wireless devices. Bluetooth can be used by small low-power devices as cell phones to transmit data over short distances. Bluetooth versions 2.1 and older operate at 3 Mbps or less; Versions 3 and higher offer faster speeds.

Bluetooth has three classes of devices, summarized below. Although Bluetooth is designed for short-distance networking, it is worth noting that class 1 can transmit up to 100 meters

+   - Class 3: under 10 meters
- Class 2: 10 meters
- Class 1: 100 meters

Bluetooth uses the 128-bit EO stream cipher. Cryptanalysis of E0 has proven it to be weak; practical attacks show the true strength to 38 bits or less.
Sensitive devices should disable automatic discovery by the secrecy of the 48-bit MAC address of the Bluetooth adapter. Even when disabled, Bluetooth devices may be discovered by guessing the MAC address. The first 24 bits are the OUI, which may be easily guessed; the last 24 bits may be determined by brute-force attack. For example, many Nokia phones use the OUI of 00:02:EE. If an attacker knows that a target device is a Nokia phone, the remaining challenge is guessing the last 24 bits of the MAC address.

# ZigBee

ZigBee, originally described by IEEE standard 802.15.4, is another Personal Area Network (PAN) wireless technology. It is low-power, low-range wireless mesh technology that is heavily used in warehouses, Internet of Things (IoT), Building Automation and Control (BAC), and Bluetooth. It also operates at 2.4 GHz frequency which follows the following frequencies on region: 784 MHz (China), 868 MHz (Europe), and 915 MHz (United States and Australia). It supports speeds up to 250kbps at a distance of up to 100 meters.\ZigBee uses battery-powered antennas, and the ZigBee standard requires 2 years of battery life.

NIST describes ZigBee: ZigBee is a wireless technology developed as an open global standard to address the unique needs of low-cost low-power wireless sensor networks. This standard takes full advantages of the IEEE 802.15.4 physical radio