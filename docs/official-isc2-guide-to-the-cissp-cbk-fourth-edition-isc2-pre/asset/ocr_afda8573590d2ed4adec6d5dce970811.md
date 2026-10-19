upstream and downstream transmissions.

+   - **Very High Bit Rate DSL (VDSL)** — Supports much higher transmission rates than other DSL technologies, such as 13 Mbps downstream and 2 Mbps upstream.

There are two significant issues with all variations of DSL:

+   1. There is a limit to the length of the phone line between the CO and the customer. The precise limit depends on several factors, including the quality of the cable and transmission rates. In other words, the customer cannot be too far from the CO.
+   2. DSL allows the users to be connected to the Internet for much longer time intervals. Certainly, this is very convenient for the user, but extended time exposed to the Internet greatly increases the risk of being attacked. To mitigate this serious risk, it is imperative that the host has a firewall, vendor security patches are installed, and dangerous and unused protocols are disabled.

# Cable Modem

As with DSL, cable modems allow home users to enjoy high-speed Internet connectivity. Instead of sending data through the phone company, cable modems use their cable provider as an ISP. The user connects their PC Ethernet NIC to a cable modem, which is connected to the cable provider’s network. Most major cable providers supply cable modems that comply with Data-Over-Cable Service Interface Specifications (DOCSIS), which helps ensure compatibility. See Figure 4.27.

At a high level, when a cable modem is powered on, it is assigned upstream and downstream channels. Next, it establishes timing parameters by determining how far it is from the head end (the core of the cable network). The cable modem makes a Dynamic Host Configuration Protocol (DHCP) request to obtain an IP address. To help protect the cable provider from piracy and its users from their data being intercepted by other cable users, the modem and head end exchange cryptography keys. From that point forward, all traffic between the two ends is encrypted.