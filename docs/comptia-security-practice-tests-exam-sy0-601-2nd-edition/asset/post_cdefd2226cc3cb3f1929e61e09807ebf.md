
22. Daniel works for a mid-sized financial institution. The company has recently moved some of its data to a cloud solution. Daniel is concerned that the cloud provider may not support the same security policies as the company's internal network. What is the best way to mitigate this concern?

- A. Implement a cloud access security broker.
- B. Perform integration testing.
- C. Establish cloud security policies.
- D. Implement security as a service.

23. The company that Angela works for has deployed a Voice over IP (VoIP) environment that uses SIP. What threat is the most likely issue for their phone calls?

- A. Call interception
- B. Vishing
- C. War dialing
- D. Denial-of-service attacks

24. Alaina is concerned about the security of her NTP time synchronization service because she knows that protocols like TLS and BGP are susceptible to problems if fake NTP messages were able to cause time mismatches between systems. What tool could she use to quickly protect her NTP traffic between Linux systems?

- A. An IPSec VPN
- B. SSH tunneling
- C. RDP
- D. A TLS VPN

25. Ramon is building a new web service and is considering which parts of the service should use Transport Layer Security (TLS). Components of the application include:

1. Authentication
2. A payment form
3. User data, including address and shopping cart
4. A user comments and reviews section

Where should he implement TLS?

- A. At points 1 and 2, and 4
- B. At points 2 and 3, and 4
- C. At points 1, 2, and 3
- D. At all points in the infrastructure

26. Katie’s organization uses File Transfer Protocol (FTP) for contractors to submit their work product to her organization. The contractors work on sensitive customer information, and then use organizational credentials provided by Katie’s company to log in and transfer the information. What sensitive information could attackers gather if they were able to capture the network traffic involved in this transfer?

- A. Nothing, because FTP is a secure protocol
- B. IP addresses for both client and server
- C. The content of the files that were uploaded
- D. Usernames, passwords, and file content

27. What security benefits are provided by enabling DHCP snooping or DHCP sniffing on switches in your network?

- A. Prevention of malicious or malformed DHCP traffic
- B. Prevention of rogue DHCP servers
- C. Collection of information about DHCP bindings
- D. All of the above

28. Aaron wants to use a certificate for the following production hosts:

```
www.example.com
blog.example.com
news.example.com
```

What is the most efficient way for him to provide Transport Layer Security (TLS) for all of these systems?

- A. Use self-signed certificates.
- B. Use a wildcard certificate.
- C. Use an EV certificate.
- D. Use an SSL certificate.

29. Cassandra is concerned about attacks against her network’s Spanning Tree Protocol (STP). She wants to ensure that a new switch introduced by an attacker cannot change the topology by asserting a lower bridge ID than the current configuration. What should she implement to prevent this?

- A. Enable BridgeProtect.
- B. Set the bridge ID to a negative number.
- C. Disable Spanning Tree protocol.
- D. Enable Root Guard.

30. Charles finds a PFX formatted file on the system he is reviewing. What is a PFX file capable of containing?

- A. Only certificates and chain certificates, not private keys
- B. Only a private key
- C. A server certificate, intermediate certificates, and the private key
- D. None of the above, because PFX files are used for certificate requests only

31. Which device would most likely process the following rules?

```
PERMIT IP ANY EQ 443
DENY IP ANY ANY
```

- A. NIPS
- B. HIPS
- C. Content filter
- D. Firewall

32. Ted wants to use IP reputation information to protect his network and knows that third parties provide that information. How can he get this data, and what secure protocol is he most likely to use to retrieve it?

- A. A subscription service, SAML
- B. A VDI, XML
- C. A subscription service, HTTPS
- D. An FDE, XML

33. What does setting the secure attribute for an HTTP cookie result in?

- A. Cookies will be stored in encrypted form.
- B. Cookies will be sent only over HTTPS.
- C. Cookies will be stored in hashed form.
- D. Cookies must be accessed using a cookie key.

34. Charles wants to use IPSec and needs to be able to determine the IPSec policy for traffic based on the port it is being sent to on the remote system. Which IPSec mode should he use?

- A. IPSec tunnel mode
- B. IPSec IKE mode
- C. IPSec PSK mode
- D. IPSec transport mode

35. Wi-Fi Protected Setup (WPS) includes four modes for adding devices to a network. Which mode has significant security concerns due to a brute-force exploit?

- A. PIN
- B. USB
- C. Push button
- D. Near-field communication

36. Claire wants to check whether a certificate has been revoked. What protocol is used to validate certificates?

- A. RTCP
- B. CRBL
- C. OCSP
- D. PKCRL

37. Nick is responsible for cryptographic keys in his company. What is the best way to deauthorize a public key?

- A. Send out a network alert.
- B. Delete the digital certificate.
- C. Publish that certificate in the CRL.
- D. Notify the RA.

38. What two connection methods are used for most geofencing applications?

- A. Cellular and GPS
- B. USB and Bluetooth
- C. GPS and Wi-Fi
- D. Cellular and Bluetooth

39. Gabriel is setting up a new e-commerce server. He is concerned about security issues. Which of the following would be the best location to place an e-commerce server?

- A. DMZ
- B. Intranet
- C. Guest network
- D. Extranet

40. Janelle is the security administrator for a small company. She is trying to improve security throughout the network. Which of the following steps should she take first?

- A. Implement antimalware on all computers.
- B. Implement acceptable use policies.
- C. Turn off unneeded services on all computers.
- D. Set password reuse policies.

41. Ben is responsible for a new application with a worldwide user base that will allow users to sign up to access existing data about them. He would like to use a method of authentication that will permit him to verify that users are the correct people to match up with their accounts. How can he validate these users?

- A. Require that they present their Social Security number.
- B. Require them to use a federated identity via Google.
- C. Require them to use knowledge-based authentication.
- D. Require them to validate an email sent to the account they signed up with.

48. Nelson uses a tool that lists the specific applications that can be installed and run on a system. The tool uses hashes of the application’s binary to identify each application to ensure that the application matches the filename provided for it. What type of tool is Nelson using?

- A. Antivirus
- B. Blacklisting
- C. Antimalware
- D. Whitelisting

49. Which type of firewall examines the content and context of each packet it encounters?

- A. Packet filtering firewall
- B. Stateful packet filtering firewall
- C. Application layer firewall
- D. Gateway firewall

50. As part of his wireless network deployment efforts, Scott generates the image shown here. What term is used to describe this type of visualization of wireless networks?

![](img/a9d117a1cc3b6e0dee61fc3cc6c7b63e_116_0.png)

- A. A heatmap
- B. A network diagram
- C. A zone map
- D. A DMZ

51. You’re designing a new network infrastructure so that your company can allow unauthenticated users connecting from the Internet to access certain areas. Your goal is to protect the internal network while providing access to those areas. You decide to put the web server on a separate subnet open to public contact. What is this subnet called?

- A. Guest network
- B. DMZ
- C. Intranet
- D. VLAN

52. Madhuri’s web application converts numbers that are input into fields by specifically typing them and then applies strict exception handling. It also sets a minimum and maximum length for the inputs that it allows and uses predefined arrays of allowed values for inputs like months or dates. What term describes the actions that Madhuri’s application is performing?

- A. Buffer overflow prevention
- B. String injection
- C. Input validation
- D. Schema validation

53. You’re outlining your plans for implementing a wireless network to upper management. What wireless security standard should you adopt if you don’t want to use enterprise authentication but want to provide secure authentication for users that doesn’t require a shared password or passphrase?

- A. WPA3
- B. WPA
- C. WPA2
- D. WEP

54. Brandon wants to ensure that his intrusion prevention system (IPS) is able to stop attack traffic. Which deployment method is most appropriate for this requirement?

- A. Inline, deployed as an IPS
- B. Passive via a tap, deployed as an IDS
- C. Inline, deployed as an IDS
- D. Passive via a tap, deployed as an IPS
