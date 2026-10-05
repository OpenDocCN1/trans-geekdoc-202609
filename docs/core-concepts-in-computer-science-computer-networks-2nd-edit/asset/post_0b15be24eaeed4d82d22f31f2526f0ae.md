
# REVIEW QUESTIONS

- 1. Discuss the different types of network topology.
2. What is switching?
3. For devices in a network, what is the number of cable links required for a mesh, ring, bus, and star topology?
4. Why is sync pulse required in TDM?
5. What is the difference between frequency division multiplexing and wavelength division multiplexing?

# REFERENCES

- 1. Carr, B., Sury, O., Palet Martinez, J., Davidson, A., Evans, R., Yilmaz, F., Wijte, Y., IPv6 Address Allocation and Assignment Policy, RIPE document ripe-481, September 2009
- 2. D. Andersen; H. Balakrishnan; M. Kaashoek; R. Morris (October 2001), Resilient Overlay Networks, Association for Computing Machinery, retrieved 2011-11-12
- 3. Inductee Details - Donald Watts Davies. National Inventors Hall of Fame. Retrieved 6 September 2017.
- 4. Mohammad Alzadeh, Albert Greenberg, David Maltz, Jitendra Padhye, Parveen Patel, Balaji Prabhakar, Sudipta Sengupta and Murari Sridharan, “Data Center TCP (DCTCP)”, Proceedings of ACM SIGCOMM 2010, September 2010.
- 5. Nanoscale Communication Networks, Bush, S. F., ISBN 978-1-60807-003-9, Artech House, 2010. [2]
- 6. Teletraffic Engineering Handbook (PDF), ITU-T Study Group 2, archived from the original (PDF) on 2007-01-11

# CHAPTER 5

# DATA LINK PROTOCOLS

![](img/f7819d05465fc14719b3ebbba980271a_156_0.png)

Computer Networks communicate using protocols, which define the procedures that the systems involved in the communications process will use. A data-link protocol is a set of rules implementing and governing an orderly exchange of data between layer two devices, such as line control units and front-processors.

After studying this chapter, you will understand the core concepts of:

- Functions and Requirements of the Data Link Protocols
- Data Transmission Modes

# INTRODUCTION

Data Link Protocols are a crucial set of rules and conventions governing data exchange between devices within a communication network. Operating at the Data Link Layer (Layer 2) of the OSI model, these protocols facilitate reliable and efficient communication over various physical transmission media. They address key aspects of data transmission, such as framing, addressing, error detection, correction, flow control, and media access control. Framing involves breaking data into manageable frames, enabling the receiver to identify the beginning and end of each unit.

Addressing assigns unique identifiers to devices, ensuring accurate data delivery to the intended recipients. Error detection and correction mechanisms identify and rectify transmission errors, enhancing data integrity.

Flow control regulates data flow between devices to prevent overwhelming receivers and Additionally, media access control resolves contention issues when multiple devices transmit simultaneously on shared channels.

Several well-known data link protocols include Ethernet for wired LANs, Wi-Fi (IEEE 802.11) for wireless LANs, PPP for point-to-point connections, HDLC for WANs, and Frame Relay for remote site connections. The appropriate choice of data link protocol depends on the network's characteristics, devices used, and specific application requirements.

![](img/f7819d05465fc14719b3ebbba980271a_157_0.png)

# CORE CONCEPT: FUNCTIONS AND REQUIREMENTS OF THE DATA LINK PROTOCOLS

A data link is a method for connecting one location to another in telecommunications, in order to transmit and receive digital information. Data transfer happens over a certain link protocol that allows data to be transferred from the source to the destination. In the OSI model for computer networking, the data link essentially makes up the second layer.

Computer networks communicate using protocols, which define the procedures for the systems involved in the communications process will use. A data-link protocol is a set of rules implementing and governing an orderly exchange of data between two devices, such as line control units and front-end processors.

The purpose of the data link layer is to transfer blocks of data without error between two adjacent devices. Adjacent devices are physically connected by a communication channel such as telephone lines, coaxial cables, optical fibers, or satellites. The implication of such a physical link is that the data bits are delivered in exactly the same order in which they are sent. The physical has no inherent storage capacity; therefore the propagation delay over the link.

Transmission of data over the link would be very simple indeed if no error ever occurred. Unfortunately, this is not so in a real physical link for a number of reasons:

- Natural phenomena as noises and interference are introduced into the link causing errors in detecting the data.
- There is a propagation delay in the link.
- There is a finite data processing time required by the transmitting and receiving stations.
- A data link protocol thus has to be designed to ensure an error-free transmission and also to achieve efficiency of the data transfer as high as possible.

Data-link protocol functions include line, flow control, and error control.

Line discipline coordinates hop-to-hop data delivery where a hop is a computer, a network controller, or some type of network-connecting device, such as a router.

# Data Link Layer

| Application |
| :--- |
| Presentation |
| Session |
| Transport |
| Network |
| Data link |
| Physical |

| Line discipline |
| :--- |
| Flow control |
| Error control |

Flow Control is the process of managing the rate of data transmission between two nodes to prevent a fast sender from overwhelming a slow receiver.

Figure 1: Data link control with OSI layer.

Line discipline determines which device is transmitting and which is receiving at any point in time.

Flow control coordinates the rate at which data is transported over a link and generally provides an acknowledgment mechanism that ensures that data is received at the destination.

Error control specifies a means of detecting and correcting transmission errors.

![](img/f7819d05465fc14719b3ebbba980271a_159_0.png)

**Figure 2**: Functions of data link control.

# Line Discipline

Line discipline is coordinating half-duplex transmission on a data communications network. The two fundamental ways that the line discipline is accomplished in a data communications network are enquiry/acknowledgement (ENQ/ACK) and poll/select.

## ENQ/ACK

ENQ/ACK line discipline determines which device is transmitting and which is receiving at any point in time. Flow control coordinates the rate at which data is transported over a link and generally provides an acknowledgment mechanism that ensures that data is received at the destination. Error control specifies a means of detecting and correcting transmission errors.

## Poll/Select

Line discipline is coordinating half-duplex transmission on a data communications network. The two fundamental ways that the line discipline is accomplished in a data communications network are enquiry/acknowledgement (ENQ/ACK) and poll/select.

The poll/select method of line discipline works with topologies where one device is designated as a primary station and the other device is secondary stations. Whenever multipoint link consists of a primary device and multiple secondary devices using a single transmission, all exchanges must be made through primary device. The primary device controls the link; the secondary device follows its instructions. It is up to the primary to determine which device is allowed to use the channel at a time. The primary therefore is the initiator of a session. If the primary wants to receive data and send data, it applies functions called poll and select. A poll is a solicitation from the primary to a secondary station to determine if the secondary station has data to transmit. The primary designates a secondary as a destination or recipient of data. A selection is also a query from the primary to determine if the secondary is ready to receive data. All secondary stations receive all polls and selections. With poll/select procedures each station is assigned one or more address for identification.

The primary polls station A, which responds with a negative acknowledgment to a poll (NAK), indicating that the received has no message to send. The primary polls station B, which responds with a positive acknowledgment to a poll (i.e., a message). The primary selects station B to see if it is ready to receive a message. Station B responds with a positive acknowledgment to the selection (ACK), indicating that it is ready to receive a message. The primary transmits the message to station B. The primary selects station C, which responds with a negative acknowledgment to the selection (NAK), indicating that it is not ready to receive a message.

![](img/f7819d05465fc14719b3ebbba980271a_159_1.png)

**Figure 3**: Line discipline.

An ACK transmitted in response to a message indicates that the message received without errors and NAK indicates that the message received with errors and it is an automatic request for retransmission.

# Flow Control

Flow control defines a set of procedures that the transmitting station has how much data it can send before it must stop and waiting for an acknowledgement from the destination station. The two common methods of flow control are stop and wait and sliding window.

- Stop-and-wait Flow Control: The sending station sends a frame of data and waits for an acknowledgement from the other station before sending further data. The other party can stop the flow of data by simply withholding an acknowledgement. Source may not send new frame until acknowledges the frame already sent. Very inefficient especially when a single message is broken into separate frames. The primary advantage is simplicity and the primary disadvantage is speed, the time lapse between each frame is wasted time. Each frame takes essentially twice as long to
