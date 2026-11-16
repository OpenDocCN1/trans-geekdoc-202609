
## Review Questions

You can find the answers in the Appendix.

- 1. What are the two types of wireless networks?
  - A. Star and ring
  - B. Bus and hybrid
  - C. Infrastructure and hybrid
  - D. Infrastructure and ad hoc

- 2. How many stages are used in the WPA handshake?
  - A. Two
  - B. Four
  - C. Three
  - D. One

- 3. What mode has to be enabled on a network interface to allow all headers in wireless traffic to be captured?
  - A. Promiscuous
  - B. Monitor
  - C. Radio
  - D. Wireless LAN

- 4. What wireless attack would you use to take a known piece of information in order to be able to decrypt wireless traffic?
  - A. Sniffing
  - B. Deauthentication
  - C. Key reinstallation
  - D. Evil twin

- 5. What is the purpose of performing a Bluetooth scan?
  - A. Identifying open ports
  - B. Identifying available profiles
  - C. Identifying endpoints
  - D. Identifying vendors

- 6. What is the purpose of a deauthentication attack?
  - A. Disabling stations
  - B. Forcing stations to reauthenticate
  - C. Reducing the number of steps in the handshake
  - D. Downgrading encryption

- 7. What is the policy that allows people to use their own smartphones on the enterprise network?
  - A. Bring your own device
  - B. Use your own device
  - C. Bring your own smart device
  - D. Use your own smart device

- 8. What part of the encryption process was weak in WEP?
  - A. Keying
  - B. Diffie-Hellman
  - C. Initialization vector
  - D. Seeding vector

- 9. What is the four-stage handshake used for?
  - A. Passing keys
  - B. Deriving keys
  - C. Encrypting messages
  - D. Initialization seeding

- 10. What is the SSID used for?
  - A. Encrypting messages
  - B. Providing a MAC address
  - C. Identifying a network
  - D. Seeding a key

- 11. What kind of access point is being used in an evil twin attack?
  - A. Infrastructure
  - B. Ad hoc
  - C. WPA
  - D. Rogue

- 12. How does an evil twin attack work?
  - A. Phishing users for credentials
  - B. Spoofing an SSID
  - C. Changing an SSID
  - D. Injecting four-way handshakes

- 13. What method might you use to successfully get malware onto a mobile device?
  - A. Using the Apple Store or Google Play store
  - B. Using external storage on an Android
  - C. Using a third-party app store
  - D. Jailbreaking

- **14. What would you use a bluebugging attack for?**
  - A. Identifying Bluetooth devices nearby
  - B. Listening to a physical space
  - C. Enabling a phone's camera
  - D. Gathering data from a target system

- **15. What would a signal range for a Bluetooth device commonly be?**
  - A. 300 ft.
  - B. 3,000 ft.
  - C. 75 ft.
  - D. 500 ft.

- **16. What tool could you use to enable sniffing on your wireless network to acquire all headers?**
  - A. Ettercap
  - B. Tcpdump
  - C. Aircrack-ng
  - D. Airmon-ng

- **17. Why is bluesnarfing potentially more dangerous than bluejacking from the standpoint of the victim?**
  - A. Bluejacking sends while bluesnarfing receives.
  - B. Bluejacking receives while bluesnarfing sends.
  - C. Bluejacking installs keyloggers.
  - D. Bluesnarfing installs keyloggers.

- **18. What tool would allow you to run an evil twin attack?**
  - A. Wireshark
  - B. Ettercap
  - C. Wifiphisher
  - D. Aircrack-ng

- **19. What types of authentication are allowed in a WPA-encrypted network?**
  - A. Handshake and personal
  - B. Personal and enterprise
  - C. Enterprise and handshake
  - D. 802.11 and personal

- **20. What wouldn't you see when you capture wireless traffic that includes radio headers?**
  - A. Capabilities
  - B. Probe requests
  - C. SSIDs
  - D. Network type

![](img/421171b17a0c0dfae0aacde15d9831c1_451_0.png)

## Chapter 12

## Attack and Defense

### THE FOLLOWING CEH TOPICS ARE COVERED IN THIS CHAPTER:

- Firewalls
- Network security
- Boundary protection appliances
- Log analysis tools
- Security models
- Information security incidents
- Technical assessment methods

![](img/421171b17a0c0dfae0aacde15d9831c1_452_0.png)

Attacking is an important element of an ethical hacking engagement. Once you've gotten through all of your evaluation of the environment, you can move into trying to gain access to it. While social engineering can be an important element in an attack, it's not the only way in. Once you get inside, you will also want to work on moving laterally. This can require some technical attacks. It may involve engaging with web applications and the different vulnerabilities that may be exposed there. You may also need to know about denial of service attacks. It may be necessary to take out a server while you are performing spoofing attacks. There are also application-level compromises of listening services.

Another element to consider while you are attacking a network is what defenses are in place. Since the primary objective of ethical hacking is to improve the defensive posture of an organization, it's helpful to understand defensive strategies. On the attack side, knowing what may be in place will help you circumvent the defenses. When you are providing remediations to the organization you are working with, you should have a better understanding of what might be done.

Web applications are a common way for users to get access to functions and data from businesses. There are several ways to attack web applications. Attacking a web application successfully may have multiple potential outcomes, including getting system-level access. Websites are also targets of denial of service attacks, sometimes. While bandwidth consumption attacks may come to mind when you think of denial of service, it's not the only type of denial of service attack. There are some ways to perform denial of service attacks that remain effective and have nothing to do with bandwidth consumption.

Attackers will usually try to move from system to system—a process we call lateral movement. Because of this, and because an easy avenue is often through already open holes, it's important to have a good defensive strategy. While defense in depth and defense in breadth have long been thought to be good approaches to protecting the network, another way to think about the network design is implementing a defensible network architecture.

## Web Application Attacks

Web applications are more than just a set of web pages. It's possible to have a static site where users have no programmatic interaction with the pages. Pages are presented to the user and there may be links and other content, but there is no place to enter anything into the page or otherwise send something to the server that may be acted on. A web application may have code within the page, using a scripting language, or code that runs on the server.

One way to think about a web application is from the architecture standpoint. A common way to develop an application is thought to be through the use of the model/view/controller pattern. Figure 12.1 shows a diagram of how the model/view/controller pattern would be implemented through a web application. The model is the structure of the data. While it is often stored in a database, there is often an application server that manages the model by creating the structure and acting on it. The application server uses the database server for persistent storage, but all handling of the data (the model) is done in the application server. This means all data manipulation is initiated in the application server, though execution of the logic may sometimes happen on the database server. Keep in mind that interaction with a database is done through the use of Structured Query Language (SQL). While the business and application logic happens in the application server, sometimes the manipulation is actually done on the database server.

### FIGURE 12.1 Model/view/controller design

![](img/421171b17a0c0dfae0aacde15d9831c1_453_0.png)

The controller is the part of the application that receives requests and handles them, vectoring the request to the correct part of the application running in the application server. Finally, the view is the user interaction component, generally a web browser. The model is presented in a way that is consumable by a user in the browser. There is code in the form of Hypertext Markup Language (HTML) used to describe and render the pages. There may also be scripts that help with the function of the page in the browser.

The application server handles the business logic of the application and may use different programming languages, depending on the type of application server. On Windows, someone maybe using Microsoft’s Internet Information Server, which would have an application server supporting .NET languages like C# and Visual Basic. Java applications are available from many vendors. Tomcat, WildFly (formerly JBoss), WebLogic, and many others are types of Java application servers. The application server itself may introduce different vulnerabilities and methods of attack, but there are also many generic attacks common across web applications.

One important consideration when you are looking at web application attacks, however, is which component is being attacked. Some attacks may be aimed at the client device (the
