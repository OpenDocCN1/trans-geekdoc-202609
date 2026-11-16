```
Response: 220 w2K-STU-01 Microsoft FTP Service (version 5.0).
Request: USER testuser
Response: 331 Password required for testuser.
Request: PASS plaintext
Response: 230-This FTP Site is for authorized users only! Violators will be towed.
Response: 230 User testuser logged in.
Request: PORT 172,16,30,2,7,234
Response: 200 PORT command successful.
Request: LIST
Response: 150 Opening ASCII mode data connection for /bin/ls.
Response: 226 Transfer complete.
Request: PORT 172,16,30,2,7,235
Response: 200 PORT command successful.
Request: RETR textfile1.txt
Response: 150 Opening ASCII mode data connection for textfile1.txt(22 bytes).
Response: 226 Transfer complete.
Request: QUIT
Response: 221 See ya later
```

# FIGURE 7.4 Sniffing Plaintext Passwords

# Wiretapping

Wiretapping traditionally involved connecting to telephone wires, but today it can involve network sniffing, VoIP sniffing, and radio frequency sniffing (for 802.11 networking, cellular traffic, Bluetooth, and so on). If an organization does not encrypt communication before transmission takes place over public networks, attackers can passively or actively eavesdrop on that communication.

In the United States, the Communications Assistance for Law Enforcement Act (CALEA) requires that all telecommunication providers, regardless of the technologies involved, must make it possible to eavesdrop on all forms of communication so that law enforcement can collect information when a proper search warrant is issued. Some of the techniques used to intercept traffic include intercept access points, mediation devices, and programs installed at the ISP that perform the collection function. Although you might not be too concerned about the government intercepting data, you should be concerned about the fact that an attacker could also attempt to use techniques like these to intercept your sensitive and private information.

# DoS and DDoS Attacks