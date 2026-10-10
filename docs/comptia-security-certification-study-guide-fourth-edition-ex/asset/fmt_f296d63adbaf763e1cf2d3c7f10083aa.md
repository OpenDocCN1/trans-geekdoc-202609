
# System Hardening Procedures

## 5. Which of the following security technologies involves controlling access to a wired or wireless network using a central authentication server such as RADIUS?

A. Port security
B. 802.1X
C. MAC filtering
D. Firewall

## 6. What feature of a network switch allows you to control which system can be physically connected to a specific network port by its MAC address?

A. 802.1X
B. MAC filtering
C. Firewall
D. Port security

## 7. A new network administrator in the office has been reading about the company requirement that all systems have the initial security baseline applied. She is looking at a listing of 50 different policy settings that need to be applied and is wondering if there is an easy way to deploy the settings. What should she do?

A. Configure the settings in the local security policies.
B. Import a registry file.
C. Use a security template.
D. Build a macro.

## 8. What type of reporting mechanism should a system or application use to notify the administrator of an event that requires immediate attention?

A. Alert
B. Trend
C. Log
D. Alarm

# Server Hardening Best Practices

## 9. Your company has a primary DNS server at its head office and a secondary DNS server at two other offices around the world. What should you do to secure the DNS data?

A. Allow zone transfers only to the head office DNS server.
B. Limit zone transfers to the IP addresses of the secondary servers.
C. Block TCP port 53 on the firewall in the head office.
D. Block UDP port 53 on the firewall in the head office.

## 10. Which of the following identifies a security concern with SMTP servers?

A. Relaying of messages
B. Zone transfers
C. E-mail spoofing
D. Invalid address assignment

## 11. Your manager would like to implement additional security measures on the DHCP server. What actions would you recommend? (Choose two.)

A. Disable zone transfers.
B. Modify the scope to include only one address for each host on the network.
C. Deactivate the scope.
D. Configure an address reservation for each of the addresses in the DHCP scope.
E. Disable DHCP.

# Performance-Based Question

## 12. Using the exhibit, match the mitigation technique on the left side to the term or description that best matches on the right side.

![Image](f0266-01.jpg)

# SELF TEST ANSWERS

## Understanding Operating System Hardening

### 1. 
**B.** System hardening involves disabling unnecessary services and uninstalling unnecessary software from the system. System hardening also involves disabling unused accounts and patching the system.

**A, C,** and **D** are incorrect. These are all network hardening techniques and not system hardening techniques. MAC filtering controls which systems can send data to other systems, port security controls which systems can connect to a port by MAC address, and 802.1X controls who has access to a wired or wireless network by using a central authentication server.

### 2. 
**D.** When you harden the system by uninstalling unneeded software and disabling unnecessary services, you are reducing the attack surface of the system.

**A, B,** and **C** are incorrect. Although removing some software may close ports on the system, choice D is the better answer. Assessing vulnerability identifies what the vulnerabilities are on the system—it doesn’t harden the system. Fuzzing is a software-testing procedure where invalid data is entered into an application to see how the application responds.

### 3. 
**C.** `Hotfix` is the term used for an update to a piece of software that should be applied immediately.

**A, B,** and **D** are incorrect. A patch is a fix to a software error that does not necessarily need to be applied immediately. A service pack contains all the patches and hotfixes since the previous service pack or release of the software. An update is a general term for applying patches to a system.

### 4. 
**A.** When working with mobile devices, ensure that employees password-protect their devices so that if a device is lost or stolen, the data on the device is not easily accessible.

**B, C,** and **D** are incorrect. Running a mobile OS on the phone is necessary for it to function, and features like texting and e-mail are popular features that will most likely be used by the employee, so they cannot be disabled.

## System Hardening Procedures

### 5. 
**B.** The 802.1X standard controls access to a wired or wireless network by using a central authentication server such as RADIUS.

**A, C,** and **D** are incorrect. Port security controls which systems can connect to a port by MAC address. MAC filtering controls which systems can send data to other systems, and a firewall controls what traffic is allowed to enter or leave the network.

### 6. 
**D.** Port security controls which systems can connect to a port on a switch by configuring the port for a specific MAC address.

**A, B,** and **C** are incorrect. The 802.1X standard controls access to a wired or wireless network by using a central authentication server such as RADIUS. MAC filtering controls which systems can send data to other systems, and a firewall controls what traffic is allowed to enter or leave the network.

### 7. 
**C.** Security templates are a great way to help create a security baseline for systems because you can configure a number of “policy” settings in the security template file and then import the template into a system.

**A, B,** and **D** are incorrect. Configuring the settings in the local security policies of each system will take too much time—better to use security templates and then import the template into the local security policy. Importing a registry file will not work because these are policy settings, so a template should be used if you are looking to do an import. Macros are not a part of system configuration.

### 8. 
**D.** An alarm is a reporting method that notifies the administrator of a security event and expects immediate action.

**A, B,** and **C** are incorrect. An alert is a notification that may not require corrective action from the administrator. A trend is what you look for when analyzing system or network activity, and a log may be viewed to see activity on a system or application.

## Server Hardening Best Practices

### 9. 
**B.** To help secure your DNS server, ensure that zone transfers are limited to delivering the DNS zone data only to the secondary DNS servers.

**A, C,** and **D** are incorrect. The head office server is the primary DNS server, so it does not receive zone transfers. You cannot block TCP 53 at the firewall in this case, because that is the port that zone transfers run over, and you need that port open so the secondary servers can do the zone transfers. Blocking UDP 53 is not an option because it is used by DNS queries and not zone transfers.

### 10. 
**A.** Ensure that SMTP servers are not relaying SMTP messages, because hackers could then send spam messages to your server to relay them to the destination.
