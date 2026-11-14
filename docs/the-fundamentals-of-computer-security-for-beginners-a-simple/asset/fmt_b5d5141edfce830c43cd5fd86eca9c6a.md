
# General Security Practices

In general, you should always change the default settings (the default configuration of a device, password and other services are in the public domain), disable unused services, periodically update the firmware, keep the devices in secure rooms and follow the configuration baseline.

## NAT and PAT

performance and the hardening on the THE NAT

NAT (Network Address Traslation) converts private IPs to public IPs. It was created to improve addressing but has the collateral benefit of hiding the addresses used in the internal network from the outside. Currently it is preferred to use the PAT (Port Address Traslation) which converts several private IP addresses into one public IP by differentiating recipients by port number.

## Wireless Network Vulnerability

Wireless networks suffer from all the vulnerabilities of wired networks to which other specific threats are added:

1. **Jamming/Interference**  
   Use a transmitter to interfere with WiFi communications and launch a Denial of Service (DoS) attack.

2. **Rogue access point**  
   You can place an access point in public areas of airports, hotels or stations in case you want to make an untargeted attack to steal sensitive information and data from unknown users.

3. **Evil twin**  
   Configure an AP (access point) with the victim's SSID to persuade clients to connect.

4. **Eavesdropping**  
   On WiFi connections, if not encrypted, it is easier to intercept communications than on the LAN.

5. **IV Attack**  
   Initialization Vector Attack subtracts passwords on Wep encrypted networks.

6. **War driving**  
   When someone goes looking for vulnerable WiFi in the city.

7. **Warchalking**  
   Draw visible symbols, for example on walls, to indicate the presence of vulnerable nets.

## Wireless Network Encryption

WEP, WPA and WPA2 can be used in Wi-Fi encryption.

### WEP

WEP (Wired Equivalent Privacy) is a standard that aims to implement the same level of security as wired networks. It encrypts data with RC4 with a 64bit key (40 bit for the password plus 24 bit for the initialization vector). It is currently unreliable and has been replaced by WPA and WPA2 networks. The initialization vector (24 bits) is so short that it is often repeated and is also added after encryption and remains clear. By intercepting two packets with the same initialization vector and comparing them you can intercept the password.

![](rsrcK1.jpg)

### WPA and WPA2

WPA and WPA2 (Wi-FI Protected Access) are two standards based on 802.11i. WPA2 fully applies the 802.11 specifications while WPA partially applies them to maintain WEP compatibility; in fact, WPA works with the same hardware designed for WEP while WPA2 needs dedicated hardware. WPA is based on TKIP (Temporal Key Integrity Protocol) which always uses RC4 but solves WEP weaknesses by changing the encryption key for each packet, while WPA2 is based on CCMP (Counter-Mode/CBCMac Protocol) which uses the AES algorithm, one of the most secure. WPA and WPA2 allow personal or enterprise authentication. WPA Personal requires the same key for everyone, while in WPA Enterprise authentication each user must log in with their own credentials or a certificate (you must configure an AAA Server as RADIUS).

### WPS

WPS (WiFi Protected Setup) makes it easy to pair a device to the Wi-Fi network. Pairing is done without a Password by entering an 8-digit Pin or pressing a button on the device and AP. Care must be taken as this technology is very vulnerable to attack.

## Wi-Fi Hardening

Wi-Fi hardening practices are:

- **A) Use the most secure encryption available**
- **B) Change the access key regularly**
- **C) Change the default password to configure the AP**
- **D) Disable APs when not needed**
- **E) Carry out periodic checks at the site to locate unsafe or unauthorised access points**
- **F) Disable WPS**
- **G) Change the default SSID**
- **H) Limiting the Wi-Fi signal strength**  
  You can use some metal-based paints on the perimeter walls to block the signal or use unidirectional antennas.
- **I) MAC address filtering**
- **L) Hiding the SSID**
- **M) Create separate connections for guests**  
  In open networks Clients can be forced to pass through a Captive Portal where they must enter their credentials. The network is isolated from the internal network.

## Patch Management

Patch management is important in Host security. Upgrading OS is essential since most attacks are based on software vulnerabilities already discovered by manufacturers. The management of updates is divided into four steps:

### Steps

- **A) Draw up a plan**  
  Determine which updates to install.
- **B) Test them first on a test machine**  
  Updating can make the machines unusable.
- **C) Install them**
- **D) Perform a post-installation check**  
  Check that the system is working properly.

### Types of Updates

1. **Hotfix**  
   They're quick updates to fix a few bugs.
2. **Patch**  
   These are updates published quickly by the manufacturer when errors are found.
3. **Service Pack**  
   These are cumulative updates that apply different OS corrections and take a long time.
4. **New versions**  
   They fix the errors of the previous version and add new features but are so radical that they can create new problems.

## Host Hardening

The Host's hardening practices are:

- **A) OS Hardening**  
  Change the default passwords and disable unnecessary accounts and services.
- **B) Choose safe and supported OS**
- **C) Patch Management**
- **D) Install and keep up to date security software**  
  Protection against malware and spam.
- **E) Hardening of applications**
- **F) Create baseline configurations**  
  A list of safe configurations is useful so that technicians do not forget anything when setting up new PCs.

Host security is also linked to fault tolerance (data redundancy), environmental safety (power supply, fire protection) and secure connections (VPN and communication encryption).

## Hardware Security

Of further importance is hardware security. Small and portable devices must be secured using security cabinets or safes and cable locks. Cable locks allow laptops to be tied to fixed objects.

## Virtualization

Virtualization allows you to create virtual machines on a physical machine. The hypervisor divides its resources among guest machines. The most critical resource is usually RAM so the hypervisor must have much more than normal. Among the various applications that allow you to use virtualization are VMWARE and VirtualBox. The main advantages are related to hardware optimization as one hypervisor runs several virtual machines giving the possibility of testing and sandboxing. Sandboxing allows you to separate virtual machines from the rest of the network with the ability to create honeypots or even observe how malware acts. Test environments separated from the rest are called sandboxes. Sandboxes are used by antivirus engines to run and analyze potential malware in a secure environment. Java applications are also run in a virtual machine that acts as a sandbox. Virtual machines must have the same security as real machines and of course the hypervisor must be more secure.

## Cloud Computing

Cloud computing allows you to use applications and other resources from specialized providers (Google Drive or iCloud). The cloud is increasingly used because it is flexible as the customer only pays for the necessary services and for the time needed, allowing savings on management costs as the provider only takes care of the management of the servers and services it offers, including maintenance tasks. Finally, it is usually safer against attacks and disasters as the provider usually has a robust security and backup system that a small business cannot afford.

Depending on who can access the service may be:

1. **Private**  
   Accessible only from the company network.
2. **Public**  
   Also accessible from the Internet.
3. **Hybrid**  
   A mixed-up solution.
4. **Community**  
   Service sharing between partner companies.
