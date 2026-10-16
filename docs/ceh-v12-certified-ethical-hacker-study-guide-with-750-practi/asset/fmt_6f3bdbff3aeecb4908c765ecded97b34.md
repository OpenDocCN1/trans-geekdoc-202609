
4. C. Sniffing can be used to collect information that may be needed to launch wireless attacks. A deauthentication attack can be used to force a station to generate traffic. An evil twin attack uses a rogue access point to pretend to be a legitimate network. In order to decrypt network traffic, you would need the key. One way to get the key is to reuse information from network traffic that generated a known key. This is a key reinstallation attack.

5. C. Bluetooth doesn't use ports. While profiles are important, you get the profile capabilities during the pairing process. Just performing a scan won't get you a list of supported profiles. While you should be able to identify vendors as part of the process of running a Bluetooth scan, it's not the purpose of the scan. The purpose is to identify endpoints and their associated addresses so you can run other attacks on them.

6. B. The purpose of a deauthentication attack is to force stations to reauthenticate. This allows the attacker to collect information from the authentication and handshake. This information could be used later to potentially derive the key, as in WEP transmissions. A deauthentication attack doesn't disable stations. There is no way to reduce the number of steps in a handshake, and downgrading encryption is considerably harder, if it's possible at all.

7. A. Bring your own device (BYOD) is a policy that allows employees to use their own devices on an enterprise network. This opens the door to the potential for attacks from unknown and unexpected devices. None of the other answers is a real thing.

8. C. The initialization vector is a random value that seeds the key used for encryption and decryption. In WEP, the algorithm specified for the initialization vector yielded nonrandom, predictable values. While the initialization vector is part of keying, it's not the keying itself that was weak. Seeding vector is not a real thing, and Diffie–Hellman is a process used to derive and exchange keys securely. It's not part of WEP.

9. B. The four‑stage handshake is used to authenticate stations against wireless networks. As part of the handshake, encryption keys are generated. Keys are derived on both sides of the transaction rather than being exchanged directly. This is handled during the four‑stage handshake. Keys are not passed. Messages can't be encrypted until the four‑stage handshake is complete and the keys are generated. There is no such thing as initialization seeding.

10. C. The service set identifier (SSID) is used to identify a network. It is the name of the network you would select when you were trying to connect to a network. The SSID is not the MAC address, and it has nothing to do with keys or encryption.

11. D. Ad hoc and infrastructure are types of wireless networks. Only infrastructure uses access points, but infrastructure is not a type of access point. WPA is an encryption protocol. A rogue access point, meaning one that isn't legitimate, is used in an evil twin attack by pretending to be a legitimate access point.

12. B. An evil twin attack uses an access point masquerading as the point of connection for stations trying to connect to a legitimate wireless network. Stations reach out to make connections to this access point masquerading as another access point. While you may phish for credentials as part of an evil twin attack, credential phishing is not how evil twin attacks work. SSIDs don't get changed as part of an evil twin attack, meaning no SSID that exists will become another SSID. Injecting four‑stage handshakes won't do much, since four‑stage assumes both ends are communicating, so the injection of a full communication stream will get ignored.

13. C. The Apple App Store and the Google Play Store are controlled by Apple and Google. It's not impossible to get malware onto mobile devices through them, but it's difficult because apps get run through a vetting process. While some Android devices will support external storage, it's not an effective way to get malware onto a smartphone or other mobile device. Jailbreaking can lead to malware being installed, but it's not the means to get malware onto a mobile device. Third‑party app stores can be a good means to get malware onto mobile devices because some third‑party app stores don't vet apps that are submitted.

14. B. A bluebugging attack is used to gain access to a smartphone to initiate a call out to the attacker's phone. This allows the attacker to listen to anything happening around the phone owner. Scanning is used to identify Bluetooth devices nearby. There is no particular attack used to enable a phone's camera. Gathering data from a target device or system is bluesnarfing.

15. A. While there are Bluetooth devices that will transmit much farther, a common range is about 300 feet (100 meters) for Bluetooth 4.0.

16. D. `tcpdump` can be used to capture frames/packets. Ettercap is used for captures and spoofing attacks. Neither can capture all headers, including radio headers in a wireless network. The package `aircrack-ng` includes the program `airmon-ng`, which can turn on monitor mode on a network interface. The program `aircrack-ng` itself cannot do that.

17. B. Bluesnarfing is an attack that connects to a Bluetooth device to grab data from that device. Bluesnarfing sends data to the attacker. Bluejacking can be used to send information to a Bluetooth device, such as a text message. Neither of these attacks installs a keylogger.

18. C. Wireshark is used to capture packets/frames from a network. Ettercap is used for spoofing attacks. The program `aircrack-ng` can be used to crack wireless keys. `wifiphisher`, though, can be used to set up an evil twin attack.

19. B. WPA supports both Personal and Enterprise authentication. Personal authentication makes use of a pre‑shared key, while Enterprise authentication uses usernames and passwords to authenticate specific users, providing accounting and access control, meaning we know exactly who has connected to the network.

20. D. Radio headers in a wireless network will provide you with the capabilities of the devices, since that's negotiated during the association process. You will also see probe requests asking what networks are in the area, including specific networks that a station knows about. These requests will include the SSID. The responses will also include the SSID. You will not get the network type in the headers.

21. C. WPA3 uses the simultaneous authentication of equals (SAE). Previous versions have used the four‑stage handshake alone. The other two answers are not real.

22. D. The Bluesmack attack is a denial‑of‑service attack that is caused by manipulating packet sizes sent to a victim system. The other attacks are Bluetooth but do not result in a denial‑of‑service attack.

23. B. A Pringles can may be used to increase the wireless signal, so it is helpful for wireless footprinting or wardriving. Evil twin is used to mimic an existing wireless network. Key reinstallation is another type of wireless attack. Bluesnarfing is a Bluetooth attack and wouldn't require a Pringles can.

24. A. The BDADDR is needed to perform a Bluedump attack. An IP address would not be used in a Bluetooth attack. The other answers aren't real things.

25. D. Plywood and sheetrock effectively offer no resistance to a wireless signal. Glass offers minimal resistance. If you wanted to keep your wireless signal inside your building, you should use concrete as a building material. Masonry blocks and bricks would also work well.

## Chapter 12: Attack and Defense

1. B. While DNS is also used for amplification attacks, Smurf attacks are a result of someone sending ICMP echo requests to the broadcast address of a network. The echo responses would be sent to the address in the source of the request, which would be spoofed. If enough systems respond, the volume of responses can overwhelm the target system.
