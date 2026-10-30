# WEP

Wired Equivalent Privacy (WEP) uses the stream cipher RC4 to secure the data and a CRC-32 checksum for error checking. Standard WEP uses a 40-bit key (known as WEP-40) with a 24-bit initialization vector (IV), to effectively form 64-bit encryption. 128-bit WEP uses a 104-bit key with a 24-bit IV.

Because RC4 is a stream cipher, the same traffic key must never be used twice. The purpose of an IV, which is transmitted as plain text, is to prevent any repetition, but a 24-bit IV is not long enough to ensure this on a busy network. The way the IV is used also opens WEP to a related-key attack. For a 24-bit IV, there is a 50% probability the same IV will repeat after 5,000 packets.

# WPA

Wi-Fi Protected Access (WPA) uses Temporal Key Integrity Protocol (TKIP). TKIP is a 128-bit-per-packet key, meaning that it dynamically generates a new key for each packet. WPA works in two modes:

+   - **WPA-Personal:** Also referred to as *WPA-PSK* (Pre-shared key) mode. Is designed for home and small office networks and doesn’t require an authentication server. Each wireless network device authenticates with the access point using the same 256-bit key.
+   - **WPA-Enterprise:** Also referred to as *WPA-802.1x* mode. Is designed for enterprise networks, and requires a RADIUS authentication server. An Extensible Authentication Protocol (EAP) is used for authentication. EAP has a variety of implementations such as EAP-Transport Layer Security (EAP-TLS) and EAP-Tunneled Transport Layer Security (EAP-TTLS).

# WPA2

WPA2 is based on the IEEE 802.11i standard. It is the only one of the three protocols that fully implements the 802.11i standard. Much of this will make sense to you, if you have read Chapter 3, “Cryptography.”

WPA2 uses the Advanced Encryption Standard (AES) using the Counter Mode-Cipher Block Chaining (CBC)-Message Authentication Code (MAC) Protocol (CCMP) that provides data confidentiality, data origin authentication, and data integrity for wireless frames. Unless there is some compelling reason not to, one should always use WPA2.

# BSSID

When considering 802.11 Wi-Fi devices, the most interesting piece of information is the basic service set identifier (BSSID). Wireless networks have a basic service set that has an ID, the BSSID. That BSSID is preset during manufacture and is the MAC address of the wireless access point. If you have a BSSID in a log but don’t know where that wireless access point is, there are websites where one can take the BSSID and look up the geographic location, for example https://wigle.net/. That is just one use of the BSSID.