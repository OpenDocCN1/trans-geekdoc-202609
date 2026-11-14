
# Multiple Choice Questions

## Question 81
b. Increased utilization of storage resources  
c. Expansion of storage space without downtime  
d. All of the above

## Question 82
The LUN is basically:

a. An address for host operating system to communicate to the device  
b. A unique number that is assigned to each storage device or partition of the storage that the storage can support  
c. An address that is hard coded into a `FC HBA` and is used to identify individual port (`N_Port` or `F_Port`) in the fabric  
d. An address to communicate `FC` devices

## Question 83
`WWN` is basically:

a. An Address for host operating system to communicate to the device.  
b. A unique number that is assigned to each storage device or partition of the storage that the storage can support.  
c. An address that is hard coded into a `FC HBA` and is used to identify individual port (`N_Port` or `F_Port`) in the fabric  
d. An address to communicate `FC` devices

## Question 84
`WWN` address that is encoded into each port by the manufacturer is of:

a. 16 bit  
b. 24 bit  
c. 48 bit  
d. 64 bit

## Question 85
What are the services provided by fabric to all the nodes?

a. Fabric login  
b. Fabric address notification  
c. Registered state change notification  
d. All of the above

## Question 86
What is the smallest unit of information transfer in `FC`?

a. Packet  
b. Frame  
c. Sequence  
d. Exchange

# Descriptive Questions

1. Describe different phases of an `SCSI` command and also describe `SCSI` protocol write and read request sequences.

2. When a server or storage is connected to a fabric, describe each login process that take place to establish the communication.

3. Describe and highlight purposes of `iSCSI`, `FCIP` and `iFCP` protocols.

# Quiz Questions

1. What are `SCSI` initiator and target?

2. If an `IP` address is equivalent to `FCID`, `MAC` address is equivalent to `WWPN`, then what are equivalent to `DHCP` client and server?

3. `FC` construct is similar to grammatical equivalents of any language. `FC` word is also similar to word in any language. `FC` frame is equivalent to sentence then, what are equivalent to paragraph and entire conversation?

4. What is analogous to `iSNS` server for `iSCSI`?

5. Explain difference between host I/O timeout and latency.

# Glossary and Key

*   **`SAS`**: Serial attached `SCSI` interface protocol for disk drive.
*   **`SATA`**: Serial Advanced Technology Attachment interface protocol for disk drive.
*   **`HBA`**: Host bus adapter. An adapter used to connect the host server to the fabric.
*   **`SFP`**: Small Form Factor Pluggable transceiver, converts the electrical signal into an optical signal.
*   **`WWN`**: World wide name is a unique `FC` identifier consisting of a 16 character hexadecimal number. `WWN` is required for each `FC` communication port.
*   **`WWNN`**: Worldwide node name is a globally unique 64 bit number that identifies a node process.
*   **`WWPN`**: Worldwide port name is a globally unique 64 bit number that identifies a node port.
*   **`ISL`**: Inter site link, a connection from one `FC` switch to another `FC` switch.
*   **`FC`**: Fibre Channel, a high-speed network technology mainly used to connect storage to host servers. `FC` supports several common transport protocols including `IP` and `SCSI`.
*   **`FCoE`**: Fibre Channel over Ethernet. Consolidates LANs and SANs.
*   **`Fabric`**: A network of `FC` switches or hubs and other devices.
*   **`FCID`**: Fibre Channel ID, 24 bit `FC` address obtained during Fabric login (`FLOGI`).
*   **`iSCSI`**: Internet `SCSI` interface protocol, used for block-level access of `IP` storage devices.
*   **`IQN`**: `iSCSI` qualified name, a unique name in `IP` storage system used for accessing `iSCSI` devices.
*   **`iSCSI HBA`**: Hardware `iSCSI` initiator adapter card.
*   **`iSNS`**: Internet Storage Name Service, a name registration service for `IP` storage devices.
*   **`CHAP`**: Challenge-Handshake Authentication Protocol, for providing security to `iSCSI` storage volume.
*   **`CNA`**: Converged network adapter that functions like `FC HBAs` and Ethernet `NICs` both.
*   **`NQN`**: `NVMe` qualified name, which is similar to an `iSCSI` qualified name, a unique name in `NVMe` storage system used for accessing `NVMe` devices.

# Community

Join our Discord space

Join our Discord workspace for latest updates, offers, tech happenings around the world, new releases, and sessions with the authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![QR-Logo](images/fm1.png)

# Chapter 5: Storage Networking to Share Storage

## Introduction

When computer networking evolved, industry trend had changed to multiple cluster servers hosting different applications. So, an additional requirement of centralized storage for sharing data evolved. Therefore, a new network, called `SAN`, for sharing storage systems came into picture.

In other words, a computer network is a communication network which allows exchanging data among host servers and storages.

![Figure 5.1: Computer networking](images/Fig_5.1.jpg)

Figure 5.1: Computer networking

Refer to the following [Figure 5.2](#ch05.xhtml#fig5-2):

![Figure 5.2: Storage networking to share storage](images/Fig_5.2.png)

Figure 5.2: Storage networking to share storage

`SAN` fabric is a logical entity that consists of multiple `FC` switches connected together. Connection between two switches is called inter-switch link (`ISL`).

## Structure

Upon successful completion of this chapter, you will be able to learn following key areas of storage networking:

*   `SAN` topology
*   Zoning
*   LUN masking
*   Multipath

## Objectives

In this chapter, you will learn different network topologies through which host servers and storage systems are connected. You will also learn about network configurations to control various access of storage system by the host servers, such as zoning and LUN masking.

It is because of some specific network physical connectivity and access configuration multiple paths get created between host server and storage system, in this chapter you will also learn about how virtual volumes are accessed over multiple path along with load balance and failover.

### SAN Topology

At the time of designing `SAN`, topology is one of the most important considerations. Topology is mainly driven by the requirement on how big or small the network is going to be, how many host servers and storage storages are going to be connected to it, and so on.

One or two switches are connected to each other to form a fabric. Again, one or two fabrics together is called a `SAN`.

Following figure shows single fabric and dual-fabric `SAN`. At least two fabrics are needed to have no single point of failure (`NSPOF`) environment, in which any fabric failure does not impact host server communication to storage.

![Figure 5.3: Single fabric and dual fabric SAN](images/Fig_5.3.png)

Figure 5.3: Single fabric and dual fabric SAN

To have redundancy, best practice is to have two fabrics and devices connect to both. This ensures availability of one path in the event of a fabric failure.

There are three types of topologies available in a `SAN` fabric:

*   **Single switch topology**: Only one switch is used to form the fabric and to connect host server to storage system. This is mainly used for entry level storage solution with few number of host servers connected to a storage system.

    ![Figure 5.4: Single switch topology](images/Fig_5.4.png)

    Figure 5.4: Single switch topology

    Though, this is cost effective solution, failure of the switch will cause communication failure between host server and the storage.

*   **Mesh fabric**: In a mesh fabric, switches are connected to other switch using `ISL`.

    Mesh fabric is of two types, that is, full mesh and partial mesh. In full mesh topology, every switch is connected to every other switch using `ISLs`. Host traverse a maximum of one hop to access its storage. The hop count is defined as the number of switches in the path between the host server and storage system. Most switch vendors support maximum of 7 hops.

    ![Figure 5.5: Full and partial mesh topology](images/Fig_5.5.png)

    Figure 5.5: Full and partial mesh topology
