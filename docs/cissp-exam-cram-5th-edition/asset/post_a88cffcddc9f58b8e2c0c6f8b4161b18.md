
information rate (CIR) that specifies the maximum guaranteed bandwidth the customer is promised. The customer can send more data than specified in the CIR if additional bandwidth is available. If there is additional bandwidth, the data passes; otherwise, the data is marked discard eligible (DE) and is discarded.

Frame Relay can use permanent virtual circuits (PVCs) or switched virtual circuits (SVCs). A PVC is used to provide a dedicated connection between two locations. An SVC works much like a phone call in that connections are set up on a per-call basis, and a call is disconnected when it is complete.
Switched virtual circuits are good when data transmission is sporadic and for teleconferencing and phone calls.

## Asynchronous Transfer Mode (ATM)

ATM is a cell-switching-based physical layer protocol. It supports high-bandwidth data needs and works well for time-sensitive applications.
Because the switching process occurs in hardware, delays are minimized. ATM uses a fixed cell size of 53 bytes. ATM can be implemented on LANs or WANs.

ATM is being surpassed by newer technologies, such as MPLS, which is described earlier in this chapter. MPLS designers recognized that data didn’t need to be converted into 53-byte cells. MPLS packets can be much larger than ATM cells. MPLS can provide traffic engineering, and it enables the creation of VPNs without end-user applications. MPLS can carry many types of traffic, handles addresses via labels, and does not encapsulate header data.

**Note**

For the CISSP exam, keep in mind that MPLS uses labels to simplify WAN routing and can carry voice and data.

## Circuit Switching

Circuit switching comes in either analog or digital configurations. At the heart of circuit switching is multiplexing. Multiplexing is a technique used to combine multiple channels of data over a single set of wires or a transmission path. Today the most common form of circuit switching is the plain old telephone service (POTS), but ISDN, T-carrier, and Digital Subscriber Line (DSL) are also options. The sections that follow describe these circuit-switching options in more detail.

### Plain Old Telephone Service (POTS)

POTS is a voice-grade analog telephone service used for voice calls and for connecting to the Internet and other locations via modem. Modem speeds can vary from 9600 bps to 56 Kbps. Although POTS is relatively inexpensive and widely available, it offers only low data speeds.

### Integrated Services Digital Network (ISDN)

ISDN is a communication protocol that operates similarly to POTS, except that all-digital signaling is used. Although originally planned as a replacement for POTS, ISDN was not hugely successful. ISDN uses separate frequencies called channels on a special digital connection. It consists of B channels used for voice, data, video, and fax services and a D channel used for signaling by the service provider and user equipment. Keeping the D signaling data separate makes it harder for attackers to manipulate the service. The D channel operates at a low 16 Kbps; the B channels operate at speeds up to 64 Kbps. By binding the B channels together, ISDN can achieve higher speeds. ISDN is available in two levels: Basic Rate Interface (BRI) at up to 128 Kbps and Primary Rate Interface (PRI) at up to 1.544 Mbps. BRI comprises 2 B channels and 1 D channel, and PRI comprises 23 B channels and 1 D channel.

### T-Carrier

T-carrier service is used for leased lines. A leased line, which is locked between two locations, is very secure, and users pay a fixed monthly fee for this service, regardless of use. The most common T-carrier is a T1. A T1 uses time-division multiplexing and consists of 24 digital signal 0 (DS0) channels. Each DS0 channel is capable of transmitting 64 Kbps of data; therefore, a T1 can provide a composite rate of 1.544 Mbps. T3s are the next available choice. A T3 is made up of 672 DS0s and has a composite data rate of 45 Mbps. For those who don’t need a full T1 or a full T3, fractional service is available. A fractional T-line is just a portion of the entire carrier. Table 5.8 details common T-carrier specifications and contrasts them with POTS, ISDN, and DSL.

Table 5.8 Circuit-Switching Specifications

| Service | Characteristics | Maximum Speed |
| :--- | :--- | :--- |
| POTS dialup service | Switch line; widely used | 56 Kbps |
| ISDN BRI digital | Requires a terminal adapter; can be costly | 128 Kbps |
| ISDN PRI digital | Requires a terminal adapter; can be costly | 1.54 Mbps |
| DSL | Typically asymmetric; downloads faster than uploads | Up to 52 Mbps |
| T1 | Dedicated leased line; 24 bundled phone lines | 1.54 Mbps |
| T3 | Dedicated leased line; 28 bundled T1s | 44.736 Mbps |

> T1s are the standard in the United States, and Europe uses an E-carrier system. An E1 carries 30 channels; an E3 is 16 E1s. E1s are dedicated 2.048 Mbps circuits, and E3 are dedicated 34.368 Mbps circuits.

### Digital Subscriber Line (DSL)

DSL is another circuit-switching connectivity option. DSL is typically asymmetric, which means that the download speed is much faster than the upload speed. The theory is that you usually download more than you upload.
DSL modems are always connected to the Internet; therefore, you do not have to dial in to make a connection. As long as your computer is powered on, it is connected to the Internet and is ready to transmit and receive data. This is the primary security concern with DSL. An advantage of DSL is that it maintains a more fixed speed than cable modems typically do. Table 5.9 provides details about the different DSL types.

Table 5.9 DSL Types and Speeds

| DSL Type | Data Rate | Max Distance |
| :--- | :--- | :--- |
| IDSL (ISDN DSL) | 160 Kbps | Up to 18,000 ft., 24 AWG |
| HDSL (High-Bit-Rate DSL) | 1.544 Mbps 2.048 Mbps | Up to 12,000 ft., 24 AWG |
| SDSL (Symmetric DSL) | 1.544 Mbps 2.048 Mbps | Up to 10,000 ft., 24 AWG |
| ADSL (Asymmetric DSL) | 1.5–9 Mbps 16–640 Kbps | Down 9,000–18,000 ft., 24 AWG Up |
| VDSL (Very-High-Bit-Rate DSL) | 13–52 Mbps 1.5–2.3 Mbps | Down 1,000–4,500 ft., 24 AWG Up |

## Cable Internet Access

Cable Internet access refers to the delivery of Internet access over the cable television infrastructure. The Internet connection is made through the same coaxial cable that delivers the television signal to your home. The coaxial cable connects to a special cable modem that demultiplexes the TCP/IP traffic. This always-on Internet connection presents a big security issue if no firewall is used. One of the weaknesses of cable Internet access is that there is a shared amount of bandwidth among many users. Cable companies control the maximum data rate of each subscriber by capping the maximum data rate. Some unscrupulous individuals attempt to uncap their line to obtain higher speeds. Uncappers can be caught and prosecuted because cable Internet providers routinely check for this illegal action.

> **Note**
> 
> Although uncapping a cable connection might lead only to a disconnection of your service, service providers might push for criminal charges. That’s what happened to one Buckeye Cable customer whose home was searched by the FBI; the individual in that case was charged with fifth-degree felonies for tampering with the service connection in violation of law.

Problems with cable modems continue to be discovered. It is possible to hijack some cable modems by simply visiting a vulnerable website (see www.gnucitizen.org/blog/bt-home-flub-pwnin-the-bt-home-hub/).

Another lingering concern is loss of confidentiality. Individuals have worried about the possibility of sniffing attacks. Most cable companies have addressed this issue by implementing the Data Over Cable Service Interface Specification (DOCSIS) standard. The DOCSIS standard specifies encryption and other security mechanisms that prevent sniffing and protect privacy. DOCSIS is currently at Version 3.1.

### Other WAN Technologies
