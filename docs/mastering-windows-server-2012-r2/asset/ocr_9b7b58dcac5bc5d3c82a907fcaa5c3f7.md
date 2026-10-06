# BEFORE RUNNING THE CONFIGURATION WIZARD

Install the Active Directory Domain Services role onto a fresh Windows Server 2012 by running the Add Roles and Features Wizard. Next, you need to have a static IP address assigned to your second DC. The DNS IP address points to the first DC so the server can locate the domain.

You will need to access the TCP/IP properties for the NIC. The easiest way to access the network adapters is to follow these steps:

+   1. Press Win+R on your Windows 2012 server keyboard.

+   2. Type ncpca.pl and click OK.

+   3. Click the Local Area Connection. Click the Properties button.

+   4. Select Internet Protocol Version 4 (TCP/IP/IPv4) and select Properties.

Ensure you have a statically assigned IP address with your network.

+   5. Enter the address of the DNS server, as shown in Figure 7.13.

In this example, the DNS server has an address of 192.168.0.45, so we have entered it as the IP address for the DNS server (see Figure 7.13).

# FIGURE 7.13
Configuring network settings

![](bbox=[0.403, 0.455, 0.743, 0.755])

+   6. Close all the windows and dialog boxes.

You don't need to join the server to the domain prior to promoting it to a domain controller. The configuration wizard will automatically take the necessary steps and move the computer object into the Domain Controller in Active Directory.