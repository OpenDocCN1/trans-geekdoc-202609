
area networks for resilient and efficient transfer of data packets at rates scalable to many gigabits per second. This WG is currently in hibernation.¹⁰

### 802.18—Radio Regulatory Technical Advisory Group (RR-TAG).

On behalf of other 802 WGs using radio-based communication, this TAG monitors, and actively participates in, ongoing national and international radio regulatory activities.

### 802.19—Wireless Coexistence Working Group.

Develops and maintains policies defining the responsibilities of 802 standards developers to address issues of coexistence with existing standards and other standards under development.

### 802.20—Mobile Broadband Wireless Access (MBWA) Working Group.

Defines the specification for a packet-based wireless interface that is optimized for IP-based services. The goal is to enable worldwide deployment of affordable, ubiquitous, always on, and interoperable multivendor mobile broadband wireless access networks that meet the needs of business and residential end user markets. This WG is currently in hibernation.

### 802.21—Media Independent Handover Services Working Group.

Developing standards to enable handover and interoperability between heterogeneous network types including both 802 and non-802 networks.

### 802.22—Wireless Regional Area Networks (WRAN) Working Group.

Developing a standard for a radio-based PHY, MAC, and air interface for use by license-exempt devices on a noninterfering basis in the spectrum allocated to broadcast television.

### 802.23—Emergency Services Working Group.

This working group was created to define an IEEE 802 framework for LANs that would comply with applicable civil authority requirements for communications systems. This working group has been disbanded.

### 802.24—Smart Grid Technology Advisory Group.

This TAG was created to provide liaison between the 802 committee and the smart grid industry and regulatory bodies, and to provide coordination and collaboration amongst 802 working groups related to smart grids.

## 6.5.3 IEEE 802.3 CSMA/CD Standard.

The original IEEE 802.3 standard, first published in 1985, describes the PHY and MAC for a CSMA/CD bus network operating over thick coaxial cable. Today, an 802.3 network implementation can employ any of a number of media types, including UTP and optical fiber. Without question, star-wired UTP implementations are the most popular.

The 802.3 committee anticipated the different media types that might be used, and they developed a nomenclature to identify the actual physical implementation, using the format:

```
[speed (Mbps)]|[signaling type]|[segment length (m) or media type]
```

The original 802.3 specification, for example, operated at 10 Mbps, used baseband (digital) signaling and limited a single coaxial cable segment to a length of 500 m (1,640 feet); the cable was designated 10BASE5. In fact, the largest distance between two 802.3 stations could be 2.8 km (9,200 feet), so repeaters might be used to interconnect several 500-m coaxial cable segments.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_209_0.png)

### Exhibit 6.11 IEEE 802.3 Frame Format

A less expensive version, called CheaperNet, was later introduced that operated over thin coaxial cable segments limited to 185 m (610 feet); this PHY is denoted 10BASE2.

In the mid-1980s, AT&T introduced a product called StarLAN, which operated at 1 Mbps over UTP. Although this product has long been relegated to obscurity, it was the first to break the 1-Mbps barrier on UTP. Subsequent versions of 802.3 that employ UTP all use a star topology where each network node connects directly back to a central hub. The first 10-Mbps version of 802.3 was denoted 10BASE-T, the T indicating use of the UTP medium (which structured wiring standards say is limited to a distance of 100 m, or 330 feet). The 10-Mbps optical fiber version of 802.3 is 10BASE-F. Today, of course, 100-Mbps and 1-Gbps versions (i.e., 100BASE-T and 1000BASE-T) are available. Full-duplex Ethernet takes advantage of the point-to-point links in a star configuration and effectively doubles the line speed by allowing both stations to transmit at the same time.

Exhibit 6.11 shows the format of an IEEE 802.3 MAC frame, primarily for reference purposes. The fields and their functions are:

- **Preamble.** Used for clock synchronization: employs 7 repetitions of the 8-bit pattern 10101010. (8 binary bits = 1 byte = 1 octet)
- **Start frame delimiter (SFD).** The bit pattern 10101011 denotes the actual beginning of the frame. 1 octet.
- **Destination address (DA).** 48-bit MAC address of the station that should receive this frame. An all-1s address in 48 binary bits (ff-ff-ff-ff-ff-ff in hexadecimal) is the broadcast address, indicating that all stations should receive this message.
- **Source address (SA).** 48-bit MAC address of the station sending this frame.
- **Length.** Number of octets in the LLC data field, a value between 0 and 1500. 2 octets.
- **LLC Data.** Data from LLC (and higher layers). This field contains a 3-octet LLC Header, 5-octet 802.2 Subnetwork Access Protocol (SNAP) header, and 38 to 1492 octets of higher layer data.
- **PAD.** Additional octets to ensure that the frame is at least 64 octets in length; this minimum is required by CSMA/CD networks as part of the collision detection mechanism.
- **Frame check sequence (FCS).** Remainder from CRC-32 calculation used for bit error detection. 4 octets.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_210_0.png)

### EXHIBIT 6.12 Ethernet II Frame Format

## 6.5.4 Ethernet II.

The IEEE’s CSMA/CD standard is based on the Ethernet specification developed at Xerox’s Palo Alto Research Center (PARC) in the mid-1970s. When Xerox first decided to market Ethernet, there was no OSI model or any LAN standards or products. Given that environment, Xerox sought industry support for this new specification. The Ethernet specification has been jointly distributed (and marketed) by Digital Equipment Corporation (DEC, now Compaq), Intel, and Xerox (hence sometimes known as DIX Ethernet). While the 802.3 standard is based on Ethernet II, the two are not exactly the same.

Exhibit 6.12 shows the format of an Ethernet MAC frame, primarily for purposes of comparison to the IEEE frame. The fields and their functions are:

- **Preamble**. Used for clock synchronization; employs the bit pattern 10101010 ... 10101011. 8 octets.
- **Destination address (DA)**. 48-bit MAC address of the station that should receive this frame. An all-1s address (ff-ff-ff-ff-ff-ff) is the *broadcast address*, indicating that all stations should receive this message.
- **Source address (SA)**. 48-bit MAC address of the station sending this frame.
- **Protocol identifier (PID)**. Indicator of the protocol information transported in the Information field. Sample values include 2048 and 2054 to indicate the Internet Protocol (IP) and Address Resolution Protocol (ARP), respectively. 2 octets.
- **Information**. Protocol data unit from the protocol identified in the PID field. 46 to 1,500 octets. (It is the responsibility of the higher layer to ensure that there are at least 46 octets of data in the frame.)
- **Frame check sequence (FCS)**. Remainder from CRC-32 calculation used for bit error detection. 4 octets.

The point in comparing the frame formats of Ethernet and 802.3 is primarily of historical purposes because today’s implementations are 802.3 and not Ethernet. That said, it is interesting to note that the two specifications are, in fact, different. It is a minor thing, perhaps, and was a common misnomer in the industry to refer to IEEE 802.3 Ethernet (even the IEEE 802.3 committee is now known as the Ethernet Working Group), but it was an important difference to both a network administrator and a security professional.

In particular, in years past, if one LAN device only understood Ethernet encapsulation, it would not be able to communicate successfully with another LAN device that only understood IEEE 802.3 encapsulation. Both devices, however, can share the same
