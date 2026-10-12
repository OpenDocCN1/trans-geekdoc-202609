
## Honeywall Configuration

### Network Interfaces
*   **Eth1**: `192.168.59.20`
*   **Eth2**: `192.168.40.8`

### Honeynet Public IP Addresses
In the following, we type the external IP addresses for the honeypots. These IP addresses are the attackers:

**IP addresses**: `192.168.59.22`; `192.168.59.23`

### Honeynet Network
Here, we type the honeynet network in CIDR notation:

**Honeynet network CIDR**: `192.168.59.0/24`

### Broadcast Address of the Honeynet
`192.168.59.255`

### Management Interface
The third interface will be used for remote management. This interface helps us to remotely manage the honeywall through SSH and Walleye Web interface. We use Eth2 for the management interface.

*   **IP address of the management interface**: `192.168.40.8`
*   **Network mask of the management interface**: `255.255.255.0`
*   **Default gateway for the management interface**: `198.168.40.1`
*   **DNS server IP for honeywall gateway**: `192.168.40.2`
*   **SSH listening port**: `22`
*   **Space delimited list of TCP ports allowed into the management interface**: `22 443`
*   **Space delimited list of IP addresses that can access the management interface**: `192.168.40.0/24`

### Firewall Restrictions
The double-honeynet configured to perform unlimited outbound connections as mentioned in (7.2) above.

### Configure Sebek Variables
*   **Destination IP address of the Sebek packets**: `192.68.59.20`
*   **Destination UDP port of the Sebek packets**: `1101`

### Honeypots Configuration
The following are the details of the honeypots machines properties:

#### Honeypot 1
**Machine Properties**
*   **Operating system**: Windows XP
*   **Number of network cards**: We use one network card: Eth0
*   **IP address**: `192.168.59.22`

#### Honeypot 2
**Machine Properties**
*   **Operating system**: Ubuntu Linux 9.10
*   **Number of network cards**: We use one network card: Eth0
*   **IP address**: `192.168.59.23`

## Signature Generator Configuration
The function of the signature generator is to generate signatures for polymorphic worms samples.

### Machine Properties
*   **Operating system**: Ubuntu Linux 9.10
*   **Number of network cards**: One network card: Eth0
*   **IP address**: Eth0: `192.168.55.22`

## 7.5 Summary
This chapter discussed two parts. In the first part, we gave full details of the double-honeynet system. In the second part, we gave a brief introduction about the software used to implement the double-honeynet system and double-honeynet configurations using VMware.

## References
*   **[1]** M.M.Z.E. Mohammed, H.A. Chan, N. Ventura, M. Hashim, and I. Amin, "A modified Knuth-Morris-Pratt algorithm for zero-day polymorphic worms detection," *Proceedings of the International Conference on Security & Management*, 2 Vols, CSREA Press, Las Vegas, NV, pp. 652–657, July 13–16, 2009.
*   **[2]** M.M.Z.E. Mohammed, and H.A. Chan, "Honeycyber: Automated signature generation for zero-day polymorphic worms," *Proceedings of the IEEE Military Communications Conference*, San Diego, CA, pp. 1–6, November 17–19, 2008.
*   **[3]** M.Z.E.M. Mohssen, H.A. Chan, N. Ventura, M. Hashim, and I. Amin, "Accurate signature generation for polymorphic worms using principal component analysis," *Proceedings of the IEEE GLOBECOM Workshop on Web and Pervasive Security*, Miami, FL, pp. 1555–1560, December 6–10, 2010.
*   **[4]** Know Your Enemy: Honeywall CDROM Roo, <https://projects.honeynet.org/honeywall/>, last accessed August 18, 2012.
*   **[5]** The Honeynet Project. Roo CDROM User's Manual, <http://old.honeynet.org/tools/cdrom/roo/manual/index.html>, last accessed August 18, 2012.
*   **[6]** Know Your Enemy: Sebek—A Kernel Based Data Capture Tool, <http://old.honeynet.org/papers/sebek.pdf>, last accessed August 18, 2012.
*   **[7]** Snort—The de facto standard for intrusion detection/prevention, <http://www.snort.org>, last accessed August 18, 2012.
*   **[8]** M.M.Z.E. Mohammed and A.-S. K. Pathan. *Automatic Defense against Zero-day Polymorphic Worms in Communication Networks*, ISBN 9781466557277, CRC Press, Taylor & Francis Group, Boca Raton, FL, 2013.

# Index
**Note:** Locator followed by `f` and `t` denotes figure and table in the text.

## A
*   **Access domain**, [11](#06_Chapter01.xhtml#page_11)
*   **Acknowledgement (ACK) scan approach**, [51](#08_Chapter03.xhtml#page_51)
*   **Address resolution protocol (ARP)**, [27](#06_Chapter01.xhtml#page_27)–[28](#06_Chapter01.xhtml#page_28)
    *   address resolution process, [28f](#06_Chapter01.xhtml#page_28)
    *   packet format, [27f](#06_Chapter01.xhtml#page_27)
    *   protocol vulnerabilities, [57](#08_Chapter03.xhtml#page_57)–[58](#08_Chapter03.xhtml#page_58)
        *   scan, [57](#08_Chapter03.xhtml#page_57)
        *   spoofing and poisoning, [57](#08_Chapter03.xhtml#page_57)–[58](#08_Chapter03.xhtml#page_58)
*   **Advanced blackhat attack**, [97](#10_Chapter05.xhtml#page_97)–[98](#10_Chapter05.xhtml#page_98)
*   **Agents**, [156](#11_Chapter06.xhtml#page_156)–[157](#11_Chapter06.xhtml#page_157)
    *   DHCP relay, [24](#06_Chapter01.xhtml#page_24)–[25](#06_Chapter01.xhtml#page_25)
    *   host-based IDPS, [155](#11_Chapter06.xhtml#page_155), [158](#11_Chapter06.xhtml#page_158)
    *   IDPS, [139](#11_Chapter06.xhtml#page_139)
*   **Allaple worm**, [75](#09_Chapter04.xhtml#page_75)
*   **Alternate data stream (ADS)**, [64](#08_Chapter03.xhtml#page_64)
*   **Anomaly-based detection method**, [78](#09_Chapter04.xhtml#page_78), [135](#11_Chapter06.xhtml#page_135)–[137](#11_Chapter06.xhtml#page_137), [149](#11_Chapter06.xhtml#page_149)
    *   advantage of, [135](#11_Chapter06.xhtml#page_135)
    *   to develop scheme, [136](#11_Chapter06.xhtml#page_136)
    *   disadvantage of, [137](#11_Chapter06.xhtml#page_137)
    *   problem with use of, [137](#11_Chapter06.xhtml#page_137)
    *   profiles, [136](#11_Chapter06.xhtml#page_136)
    *   technique, [81](#09_Chapter04.xhtml#page_81)
*   **Antivirus, computer software program**, [126](#11_Chapter06.xhtml#page_126)–[127](#11_Chapter06.xhtml#page_127)
    *   IDPS
        *   components, [139](#11_Chapter06.xhtml#page_139)–[140](#11_Chapter06.xhtml#page_140)
        *   detection methods, [134](#11_Chapter06.xhtml#page_134)–[139](#11_Chapter06.xhtml#page_139)
        *   integration of multiple, [159](#11_Chapter06.xhtml#page_159)–[160](#11_Chapter06.xhtml#page_160)
        *   products, [160](#11_Chapter06.xhtml#page_160)–[163](#11_Chapter06.xhtml#page_163)
        *   security capabilities, [140](#11_Chapter06.xhtml#page_140)–[141](#11_Chapter06.xhtml#page_141)
        *   technology types, [142](#11_Chapter06.xhtml#page_142)–[159](#11_Chapter06.xhtml#page_159)
    *   modern, [126](#11_Chapter06.xhtml#page_126)
