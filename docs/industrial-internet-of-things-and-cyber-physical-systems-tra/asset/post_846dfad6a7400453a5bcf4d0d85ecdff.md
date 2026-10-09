
## Change Cipher Protocol
It defines the state of the cipher. Value is 1 byte for change cipher statement. It transforms the pending state to the current state.

## Alerts
There are two fields used such as level and alert field. The length of the level is 1 byte. The level can be classified into two types such as warning and fatal error.

The server generates an error in the form of the following messages:
- Unpredicted data
- Useless record-Message Authentication Code
- Unsuccessful data compression
- Unsuccessful linking
- Illegitimate Constraints

The server sends to the client in the form of the warning message that can be:
- Notification to close the credential
- Unverified Documentation
- Retract
- Unlicensed
- Unidentified

# NETWORK LAYER
This is the 3$^{nd}$ layer in the TCP/IP suite and 5$^{th}$ layer in the OSI model. The responsibility of the network layer is to route the packet. The router is used at the network layer. The protocol that has been defined for the network is called Internet Protocol. The router is an intelligent device that finds the shortest path for IP. IP consists of the source address, destination address, and data that has to be transmitted. The network layer does not provide error control and flow control of IP.

## Network Layer Security
The router is used to route the packet. The packet must be secured while in transmission over the network. The protocol that has been defined for packet security is called IP Security. The network layer is secured by IPsec. IPsec is used to implement security above the network layer and below the transport layer. IPsec can be implemented in various parts. It can be used to provide security to the application programs. Security service is provided to the transport layer by IPsec. It provides security to each node in a network such as intradomain or inter-domain protocols. It is used to encapsulate the information. It stops the interference of any other communication channel. It provides data authentication from the origin and verifies that the data has been transmitted to the receiver. It permits the exchange of secret keys and manages them. In a perfect world, any establishment would need its very own private system for correspondence to guarantee security. Be that as it may, it might be expensive to set up and keep up such a private system over the topographically scattered zone. It would require to oversee a composite foundation of correspondence links, switches. IPsec gives a simple component to executing the Virtual Private Network for such organizations. VPN technology permits the establishment's official traffic to be sent over the open Internet by scrambling traffic before entering the open Internet and coherently isolating it from other network transmissions.

### Mode of IPsec
The IPsec can be worked in two ways such as transport or tunnel mode. Transport mode is used to secure the packet that is coming from the transport layer. It provides security to the information at the network layer that is coming from the transport layer. The header is not protected by IPsec in transport mode, nor is a complete packet. It provides protection to the information in the entire packet. IPsec is used to protect the peer to peer transmission.

The information has been encrypted at the upper layer and comes to the network layer. A new header is used to be added with encrypted data in tunnel mode. IPsec is applied to a complete packet including the IP header. The original header is different from the newly added header. Tunnel mode is used for a wide area network, which means that the routers can be communicated with other routers or hosts with a different network. The tunnel is created between the sender and receiver for secure data transmission. This is the imaginary path to protect the initial IP header.

### Protocol of IPsec
IPsec has two protocols that are used to provide the security to the header and information in entire packets. The protocols are AH and ESP. AH protocol does not provide secrecy of information. It is used to provide the source verification and also give the validation of information in the packet. The hash function (MD5) is used for authentication and conventional private key. AH is added by the message digest. The mode of operation is used to define the location of AH for transmission. The length of AH is 32 bits. The real limit of the internet protocol header is 51. The AH is comprised of six fields such as the next header, information span, set aside, safety constraints, categorization quantity, and hashing for authentication.

Each field has its own responsibility. The next header is used to define the format of information that is carrying in the IP packet. The size of the next header is eight-bit. The value of the header is 51 before the encryption of data. The length of data in AH can be multiple of four-bytes but it does not contain the first eight bits. From security associations, when it is distinguished that the security convention is AH, the parameters of the AH header are determined. The process is associated with the security parameter index. And the maximum length has been defined for SPI is 32 bits. The sequence number can be 32 bit long and defines the flow of information. When IP transmits again, the sequence number does not change; it does not repeat its sequence. The hash function is used for authentication of data and it has a variable length.

The AH protocol does not care about the secrecy of data. In this case, IPsec has introduced another protocol named as Encapsulation Security Payload (ESP) protocol. It is used to provide the source verification, the validity of data and secrecy of data. To make the determination easier, the data of verification is used to be added at the last position of the IP packet. The value of the protocol in the header is 50. Encapsulation header and trailer are added in the IP packet. The header in Encapsulation Security Payload has two fields that are SPI and sequence number. 32 bits long is the size of the header. The characteristics of the header are similar to the Authentication Header. 32 bits long is the trailer of Encapsulation. The field has been defined for the trailer is padding and length. The working principle of Encapsulation Security Payload is given as:
- The Information is added by the trailer.
- The Information and trailer are used to encapsulate by using conventional symmetric key algorithms.
- Header is being added before transmission.
- The verification of data is generated by the header, information, and trailer of Encapsulation Security Payload.
- The MD5 algorithm is used to create the authentication data.
- The generated digest is used to be added at the last place of the trailer.
- Finally, the header of IP is appended after the modification of the protocol and the value is 50 that is assigned to the header.

The origination of IPsec transmission is based on security associations. The connection is generated by the sender and the receiver is the functionality of the security association. When connection successfully linked then data is being transferred. The encapsulation of data and verification of data is done in various ways. IPsec is used to provide options for data hiding and confirmation. Security association helps to determine the algorithm of encapsulation as well as the hash algorithm for both users. Security association gives the parameter that defines the relationship between systems. The two-way communication between the systems can be done with the help of security associations. SPI is used to determine the security association at the system. IPsec is used to transmit data fastly.

The maximum size of the SPI is 32 bit long. It set the value of the security association that can be a maximum 32 bit long. It is used to give a difference between two security associations with similar IPsec. IPsec has two types of database named as Security Association Database (SAD) and Security Policy Database (SPD). The Security Association Database saves the condition of the security association of endpoints. There are nine conditions that have been defined in SAD.

The sequence number for outbound transmission as well as overflow flag is used for authentication header and Encapsulation Security Payload. The maximum length can be 32 bit long. The prevention of replay is determined by a separate window. The time to live for security association is defined in the database. The header algorithm of authentication and Encapsulation Security Payload is used to define the database. The working of IPsec is also defined in the database. The prevention of fragmentation is also done in the database.

The security association database has three parts that are SPI, parameter, and destination IP address. The purpose of the security policy database is to route the packet. It indicates the security association
