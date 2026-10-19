Countermeasures against IP spoofing can be executed at layer 3 (see IP Address Spoofing and Syn-Ack Attacks). As TCP sessions only perform an initial authentication, application layer encryption can be used to protect against man-in-the-middle attacks.

# SYN Scanning

As traditional TCP scans became widely recognized and were blocked, various stealth scanning techniques were developed. In TCP half scanning (also known as TCP SYN scanning), no complete connection is opened; instead, only the initial steps of the handshake are performed. This makes the scan harder to recognize; for instance, it would not show up in application log files. However, it is possible to recognize and block TCP SYN scans with an appropriately equipped firewall.