
## Scale-out NAS

Scale-out NAS is a type of file-level storage that incorporates a distributed file system that can scale a single volume with a single namespace across many nodes. Scale-out NAS file-level storage solutions can scale up to several PBs all while handling thousands of clients. As capacity is scaled out, performance is scaled up.

## Conclusion

Host systems and storage systems are designed to use standard protocols to communicate with each other. Host systems and storages can be from different vendors as long as they both support the standard protocol, like `SCSI`, `FC`, `iSCSI`, and `FCoE` for block storage and `NFS` and `CIFS/SMB` for file storage. Though, over the network client system uses `NFS` or `CIFS` to read or write shared files, within the file storage, `SCSI` protocol is used to eventually write data onto the disk drive.

`SCSI` is the fundamental protocol used for an initiator to perform read/write; `FC`, `iSCSI`, and `FCoE` are transport protocols that encapsulate the `SCSI` packet for transporting the data.

`FC` is a carrier for other protocols like `SCSI`, `FICON`, `IP`, or `HiPPi`. `FC` is like `Ethernet` in `LAN`. It defines how data needs to be transmitted. It supports both media options: copper cables or optical cables. There are two types of fibre cables: multimode and single-mode.

Multimode cables are usually used for short distances, for example, connecting equipment within a rack, whereas single-mode cables are used for long distances, for example, two buildings within a city or a locality.

`iSCSI` is an emerging industry-wide popular `SCSI` block I/O protocol to be transmitted over an `IP` network. It encapsulates `SCSI` packets inside `IP` frames and transmits data between initiator and target devices.

File-level `NAS` storage uses file-level protocols such as `SMB/CIFS` and `NFS` for I/O operations within shared files.

## Case Studies

### Case Study 1: Identifying SCSI Disks in Linux Host with DAS Solution

Let us identify `SCSI` disks in a Linux host with a `DAS` solution:

#### Requirement

In a `DAS` solution, `JBOD` is connected to a Linux host server via a `SCSI` adapter. `JBOD` has a total of four disk drives in alternate bays starting from the first bay. The disk in the first bay has the `OS` installed. Provide steps to identify the disk in the operating system so that a file system can be configured on them.

#### Analysis

As described in the following figure, each disk connected via a `SCSI` adapter has a unique `SCSI` ID. The `SCSI` ID depends on the bay position in the `JBOD`.

![Figure 4.19: Identifying disks in a DAS](images/Fig_4.19.jpg)

*Figure 4.19: Identifying disks in a DAS*

There are several ways to list storage devices in Linux. `lsscsi` is one of the commonly used utilities to get details of `SCSI` devices along with their `B.T.L` details.

#### Solution

```
[root@localhost ~]# lsscsi
[2:0:0:0] disk VENDORNAME MK5061GS MF00 /dev/sda
[2:0:2:0] disk VENDORNAME MK6072FH MF00 /dev/sdb
[2:0:4:0] disk VENDORNAME MK5033KS MF00 /dev/sdc
[2:0:8:0] disk VENDORNAME MK5034KS MF00 /dev/sdd
[root@localhost ~]#
```

As the channel value is `0`, here the bus value is `2` for the `SCSI` adapter installed in the host server. The bus value depends on the `PCI` slot of the host server in which this `SCSI` adapter is installed. If a second `SCSI` adapter was installed in the server, another bus value would have been assigned to it.

`0`, `2`, `4`, and `8` are target values. The target value is also referred to as the `SCSI` ID. It depends on the bay position of the disk in the `JBOD`. `0` corresponds to the disk in bay #1, `1` for bay 2, and so on. `SCSI` IDs `6` and `7` are reserved for the `SCSI` adapter.

### Case Study 2: Fibre Channel Node and Port Types for Storage Devices in SAN Environment

Let us look at fibre channel node and port types for storage devices in a `SAN` environment:

#### Requirement

Two `FC` switches connected via a cable. A host server connected to the first switch and storage to the second switch. A tape device connected to an `FC` hub, which is connected to the second switch. Draw the `SAN` diagram along with `FC` node and port types.

#### Analysis

As per [Table 4.2](#ch04.xhtml#tab4-2), `FC` port type depends on the device type and the network type to which it is connected. For example, two `FC` switches are connected via `E_Ports`. `N_Port` is a node port that is connected to an `FC` switch. `F_Port` is a switch port that is connected to an `FC` fabric. Again, `L_Port` is a node port that is connected to an `FC` loop.

#### Solution

The following figure shows all devices mentioned along with their connectivity. Each `FC` port is labeled with the `FC` port type.

![Figure 4.20: FC node and port type](images/Fig_4.20.jpg)

*Figure 4.20: FC node and port type*

### Case Study 3: Cost-Effective High-Performance Storage Solution

Let us look at a cost-effective high-performance storage solution:

#### Requirement

Your company is looking for a cost-effective high-performance storage solution for a database application. Primarily looking for leveraging existing network infrastructure. Describe the solution that is suitable for this requirement.

#### Analysis

Block storage systems are most suitable for database applications. High-performance block storage can only be implemented either with `FC` or `iSCSI` transport protocols. There are three primary reasons that `iSCSI` storage environments have become popular in recent days:

- `iSCSI` uses `Ethernet` as its underlying communications fabric. Leveraging this technology avoids the need to build separate infrastructures, including switches, cables, connectors, and so on.
- `iSCSI` is much less expensive than `FC` and operates at speeds of `10Gbps`, `25Gbps`, `40Gbps`, and `100Gbps`.
- `iSCSI` advances along with `Ethernet`.

#### Solution

An `iSCSI` storage solution can be proposed for high-performance block-level storage access. It is also a cost-effective solution. It uses standard `Ethernet` switches and cabling. Refer to [Figure 4.13](#ch04.xhtml#fig4-13) for a schematic diagram of the proposed solution.

## Learning Check

### Objective Questions

1. `N_Port` device can be a member of two separate zones:
   a. Yes
   b. No

2. Sequence of login for `FC` login processes:
   a. Process login (`PRLI`), port login (`PLOGI`), fabric login (`FLOGI`)
   b. Port login (`PLOGI`), process login (`PRLI`), fabric login (`FLOGI`)
   c. Fabric login (`FLOGI`), port login (`PLOGI`), process login (`PRLI`)
   d. Fabric login (`FLOGI`), process login (`PRLI`), port login (`PLOGI`)

3. During which login process does an `N_Port` inform the fabric name server of its personality and capabilities?
   a. Port login (`PLOGI`)
   b. Process login (`PRLI`)
   c. Fabric login (`FLOGI`)
   d. Process logout (`PLOGO`)

4. Process login can only be between:
   a. Two switch ports
   b. Two initiators
   c. Two targets
   d. One pair of initiator and target

5. As per standard, maximum of how many bytes can be accommodated within an `FC` frame?
   a. 2048 bytes
   b. 2112 bytes
   c. 2011 bytes
   d. 1024 bytes

6. Which of the following statements related to an exchange is incorrect?
   a. Multiple exchanges are active at any given time between initiator and target
   b. An exchange has a unique identification number
   c. Always two exchanges are active at any given time between initiator and target
   d. Multiple exchanges may occur within a single login session

7. Originator exchange ID (`OX_ID`) and responder exchange ID (`RX_ID`) are:
   a. 16-bit
   b. 32-bit
   c. 64-bit
   d. 128-bit

8. `Fibre Channel` address has:
   a. 16-bit
   b. 24-bit
   c. 32-bit
   d. 40-bit

9. During speed negotiation, each port starts with:
   a. Lower speed, then steps up to higher
   b. Higher speed, then steps down to lower
   c. Randomly selects the speeds
   d. Depends on vendor’s implementation

10. Which of the following statements related to an idle is incorrect?
    a. Idles are sent continuously when no frames are being transmitted to maintain synchronization and to make the link active
    b. Idle frame has all zero bits
    c. In an idle transmission word, the first character is `K28.5`, the second is the idle character, and the last two characters are any characters that satisfy disparity
    d. Idles are transmitted between frames
