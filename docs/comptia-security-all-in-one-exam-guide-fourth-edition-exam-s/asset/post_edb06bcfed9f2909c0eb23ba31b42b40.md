
- 3. B. MDM provides the capability to secure, monitor, and support mobile devices.
- 4. D. Alternative environments are typically methods of applying computer control to physical processes such as HVAC, elevators, alarms, and so forth. Malfunctions can have real-world physical consequences. Total control of a physical system can present unique risks.
- 5. D. Bluetooth devices should always have discoverable mode turned off unless the user is deliberately pairing a device.
- 6. D. Common basic security functionality such as encryption, authentication, and access control is not included in many alternative systems.
- 7. C. Static environments such as embedded systems, SCADA, and others are configured for specific functionality and are designed to run without updates or system alterations.
- 8. Possible answers include network segmentation, manual updates, wrappers, firmware control, control redundancy, and diversity.
- 9. MAC address filtering, IP address routing, VLANs, access control management, and application layer filtering.
- 10. A. Application layer firewalls enforce communication rules at the application layer.
- 11. A. Mainframes are highly flexible, capable of hosting multiple virtualized OSs and presenting a fairly complex security posture in a modern enterprise. Although the base OS may be very secure, the large number and variety of VM instances can pose an interesting challenge from a security standpoint.
- 12. B. Because firmware updates can completely change the functionality of a device and because of the lack of internal security controls, they should be tightly controlled and manually performed.
- 13. C. Wrappers can be used to provide integrity and authentication services for data streams, such as in tunneling and VPNs.
- 14. B. Cost is a driving concern in the design of many embedded systems, the result of which is reduced functionality to only those functions that are absolutely needed. Security is often viewed as not important enough to include in any significant fashion.
- 15. The security policy should address the same issues that are addressed in regular IT environments. Policies should be specific regarding what needs to be accomplished, not how it should be accomplished. Alternative environments need the same basic security functionality as regular IT systems. Data and systems should be protected to a level commensurate with the risk of failure.

## Access Control and Authentication

In this chapter, you will

- Learn about the methods and protocols for remote access to networks
- Distinguish between identification, authentication, authorization, and accounting (AAA) protocols
- Be introduced to AAA methods and the security implications in their use
- Compare and contrast the function of authentication services
- Given a scenario, select the appropriate identification, authentication, authorization, or access control

Access control and authentication are important to control who has access to computer systems and resources. Principles of controlling access and properly authenticating apply to both internal access and remote access. Remote access requirements are more rigorous, but the same principles can be applied to internal access.

Remote access enables users outside a network to have network access and privileges as if they were inside the network. Being outside a network means that the user is working on a machine that is not physically connected to the network and must therefore establish a connection through a remote means, such as dialing in, connecting via the Internet, or connecting through a wireless connection. A user accessing resources from the Internet through an Internet service provider (ISP) is also connecting remotely to the resources via the Internet.

### Authentication Services

Authentication is the process of establishing a user's identity to enable the granting of permissions. To establish network connections, a variety of methods are used, which depend on network type, the hardware and software employed, and any security requirements. Microsoft Windows has a specific server component called Remote Access Service (RAS) that provides remote access capabilities to client applications on computers running Windows. Cisco has implemented a variety of remote access methods through its networking hardware and software. UNIX systems also have built-in methods to enable remote access.

The term remote access typically involves two elements: a temporary network connection and a series of protocols to negotiate privileges and communicate. The temporary network connection can occur via the Internet, wireless access, or any other method of connecting to a network. Once the connection is made, the primary issue is authenticating the identity of the user and establishing proper privileges for that user. This is accomplished using a combination of protocols and the operating system on the host machine.

The three steps in the establishment of proper privileges are authentication, authorization, and accounting (AAA). **Authentication** is the matching of user-supplied credentials to previously stored credentials on a host machine, and it usually involves an account username and password. Once the user is authenticated, the authorization step takes place. **Authorization** is the granting of specific permissions based on the privileges held by the account. Does the user have permission to use the network at this time, or is her use restricted? Does the user have access to specific applications, such as mail and FTP, or are some of these restricted? These checks are carried out as part of authorization, and in many cases, this is a function of the operating system in conjunction with its established security policies. A last function, **accounting**, is the collection of billing and other detail records. Network access is often a billable function, and a log of how much time, bandwidth, file transfer space, or other resources were used needs to be maintained. Other accounting functions include keeping detailed security logs to maintain an audit trail of tasks being performed. All of these standard functions are part of normal and necessary overhead in maintaining a computer system, and the protocols used in remote access provide the necessary input for these functions.

By using encryption, remote access protocols can securely authenticate and authorize a user according to previously established privilege levels. The authorization phase can keep unauthorized users out, but after that, encryption of the communications channel becomes very important in preventing unauthorized users from breaking in on an authorized session and hijacking an authorized user's data or credentials. As more and more networks rely on the Internet for connecting remote users, the need for and importance of remote access protocols and secure communication channels will continue to grow.

When a user connects to the Internet through an ISP, the user is establishing a connection to the ISP's network, and the same security issues apply. The issue of authentication, the matching of user-supplied credentials to previously stored credentials on a host machine, is usually done via a user account name and password. Once the user is authenticated, the authorization step takes place.

Access controls define what actions a user can perform or what objects a user is allowed to access. Access controls are built upon the foundation of elements designed to facilitate the matching of a user to a process. These elements are identification, authentication, and authorization.

### RADIUS

Remote Authentication Dial-In User Service (RADIUS) is a protocol that was developed originally by Livingston Enterprises (acquired by Lucent) as an AAA protocol. It was submitted to the Internet Engineering Task Force (IETF) as a series of RFCs: RFC 2058 (RADIUS specification), RFC 2059 (RADIUS accounting standard), and updated RFCs 2865–2869
