
### Integrated Windows authentication
You are required to log on to the server, but your username and password are sent to the server in an encrypted format. This authentication method is more secure than basic authentication if users are required to log on.

### Kerberos
A popular mutual authentication protocol used by default with Microsoft Active Directory environments. Active Directory adheres to the Lightweight Directory Access Protocol (`LDAP`) standard, which is the Internet protocol for accessing and querying a directory. Kerberos uses a key distribution center (`KDC`) server that is responsible for issuing tickets. These tickets are needed in order for a client to request a service from any other server on the network (known as a realm). The Kerberos process starts when the client logs on to the network. The `KDC` has a component known as the authentication server (`AS`), which gives the client a ticket-granting ticket (`TGT`), giving the client permission to request a service ticket. The service ticket is required to request service from a server on the network. When the client wants to connect to a specific server on the network, it must request a ticket from the ticket-granting service (`TGS`), which is another component of the `KDC`. The `TGS` grants the ticket to the client so the client can access the required server on the network.

![Image](exam.jpg)

**The Security+ exam expects you to know the different authentication methods just listed. Be sure to know that the `KDC` is used in Kerberos as the system that sends tickets to clients who need to access services on the network.**

#### Common Authentication Protocols
The preceding authentication methods are very “Microsoft-centric,” but standard protocols are used to perform authentication as well. These standard authentication protocols are used by various network services such as remote access service (`RAS`) and virtual private network (`VPN`).

`RAS` is a remote access technology that supports point-to-point connections using Point-to-Point Protocol (`PPP`) as the remote access protocol for a telephony application (for dial-up) to connect to the `RAS` server. `VPN` connects to a remote server (`VPN` server) using a secure channel over an untrusted network such as the Internet. Regardless of whether a dial-up connection with `RAS` or a secure `VPN` connection is used, both `RAS` and `VPN` support the following authentication protocols:

### Password Authentication Protocol (`PAP`)
Password Authentication Protocol sends the user’s credentials in plain text and is very insecure because of how easy it is for someone to analyze and interpret the logon traffic. This is the authentication protocol used by the basic authentication method mentioned previously.

### Challenge Handshake Authentication Protocol (`CHAP`)
With the Challenge Handshake Authentication Protocol, the server sends a challenge to the client that is then used in the authentication process. The following steps are performed by `CHAP`:

1. The server sends the client a challenge (a key).
2. The client then combines the challenge with the password. Both the user’s password and the challenge are run through the `MD5` hashing algorithm (a formula), which generates a hash value (a mathematical answer). The hash value is sent to the server for authentication.
3. The server uses the same key to create a hash value with the password stored on the server and then compares the resulting value with the hash value sent by the client. If the two hash values are the same, the client has supplied the correct password. The benefit is that the user’s credentials have not been passed across the network at all.

### Microsoft Challenge Handshake Authentication Protocol (`MS-CHAP`)
`MS-CHAP` is a variation of `CHAP` that uses `MD4` as the hashing algorithm, versus `MD5` used by `CHAP`. `MS-CHAP` also uses the Microsoft Point-to-Point Encryption (`MPPE`) protocol to encrypt all traffic from the client to the server.

### MS-CHAPv2
With `MS-CHAP` version 2, the authentication method has been extended to authenticate both the client and the server. `MS-CHAPv2` also uses stronger encryption keys than `CHAP` and `MS-CHAP`.

### Extensible Authentication Protocol (`EAP`)
The Extensible Authentication Protocol allows for multiple logon methods such as smartcard logon, certificates, Kerberos, and public-key authentication. `EAP` is also frequently used with `RADIUS`, which is a central authentication service that can be used by `RAS`, wireless, and `VPN` solutions, as described in the next section.

If you have remote users who connect across the Internet to access company resources, you should use a `VPN` that encrypts the communication from the user’s computer to the `VPN` server.

![Image](exam.jpg)

**The Security+ certification exam expects you to know the common authentication protocols used in networking environments.**

#### Authentication Services
Now that you understand some of the different authentication protocols you need to know for the exam, let’s move on to authentication services. When thinking of authentication services, we think of the following:

### Identification
The process of presenting identification information about yourself to the system. The identification process typically requires the user to type a username, but could require the user to insert a smartcard into a card reader, for example.

### Authentication
The authentication service is responsible for validating the credentials presented by the user and typically involves having an authentication database of criteria. For example, when a user logs on with a username and password, that information is then verified against an account database.

### Authorization
Once the account information has been verified, the user is granted access to the network. The authorization component may need other criteria besides account information before granting access. For example, the authorization service may require that the authentication request come from a specific subnet.

### Accounting
Accounting deals with logging activity. This could be logging of activity so that you track what users are doing and hold them accountable, or it could be tracking of usage of a service or application so that you can bill different departments for their usage of the system.

It is important to note that the authentication services of authentication, authorization, and accounting are collectively known in the industry as `AAA`. Many `AAA` services have come out over the years, such as `RADIUS`, `DIAMETER`, and `TACACS+`. These services offer the benefit of a central authentication system that can offer authentication, authorization, and accounting for many types of environments, such as wireless, `RAS`, and `VPNs`.

##### RADIUS
Remote Authentication Dial-In User Service (`RADIUS`) is a central authentication service that has been popular for many years. As its name suggests, it was originally used with dial-in services. The client computer that needs access to the network connects to the network by dialing into an `RAS` server or making a connection to a `VPN` server from across the Internet. The `RAS` or `VPN` server in this case is known as the `RADIUS` client because it sends the authentication request to the `RADIUS` server that is running in the background. This `RADIUS` server verifies the credentials and sends back a reply as to whether the network client is to be granted or denied access (see [Figure 10-1](#ch10.xhtml#ch10fig1)).

![Image](f0450-01.jpg)

**FIGURE 10-1**  
`RADIUS` is a central authentication service for services and devices.

`RADIUS` is an `AAA` protocol that uses the User Datagram Protocol (`UDP`) as the transport layer protocol and uses the following `UDP` ports:

- `UDP` port 1812 for authentication and authorization services
- `UDP` port 1813 for accounting services
