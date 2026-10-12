
## Lab A19: Introduction to the Metasploit Framework

In this lab, you will download and install the Metasploit Framework within your NETinVM lab environment and perform simple exploitation of your Debian machines. You will perform scanning and mild exploitation of your Debian 5 Apache server from within the NETinVM environment while learning the syntax of the Metasploit Framework Console. Learning how an Apache server can be exploited will help you to secure your server from attacks.

To download the necessary software, go to:

`www.metasploit.com/download/`

1. Run VMware Player and load the NETinVM environment.
2. Click **Run All** from within NETinVM.
3. Open the Firefox web browser from the OpenSUSE machine.
4. Visit the Metasploit site and download the Full 32bit Linux binary.
5. Open a terminal from the OpenSUSE machine.
6. Enter `su`, and enter the passphrase.
7. Navigate to the download directory; enter `cd Downloads`.
8. Enter `chmod +x framework-4.0.0-linux-full.run`. You may have to alter this to reflect the version of the framework that you have downloaded.
9. Enter `./framework-4.0.0-linux-full.run`.
10. You will be presented with the Metasploit installer; use the defaults with the exception of automatic updates.
11. Enter `msfupdate` to manually update Metasploit.
12. Enter `msfconsole` from the OpenSUSE root shell to enter the Metasploit Framework Console.
13. Note that you have a fully functional console session. Enter `ifconfig` to view the system network interfaces.
14. Enter `ping -c 2 10.5.0.10` to ping the exta Debian 5 machine with two packets.
15. Enter `help` from within the MSF Console.
16. From within the Metasploit Framework Console, enter `db_database postgresql`.
17. Enter `db_nmap 10.5.1.10` to scan the Debian 5 Apache web server from within the Metasploit Framework Console. Note that Nmap has now been integrated into Metasploit.
18. Observe the results; note that the Apache web server is indeed listening on port 80.
19. Enter the following:

```
use auxiliary/scanner/http/mod_negotiation_scanner
```

20. Enter `set rhosts 10.5.1.0/24`.
21. Enter `run`.

Now that you have located a web server with `mod_negotiation` enabled, try to exploit that via a brute-force attack that takes advantage of this feature being enabled. Enter the following:

```
use auxiliary/scanner/http/mod_negotiation_brute
```

22. Enter `set rhosts 10.5.1.10/32`.
23. Enter `run`.

This simple yet effective method permitted you to view all files located on your `mod_negotiation`-enabled Apache web server. In this scenario there was only the `index.html` file; however, in a real-world scenario this information could lead to further exploitation and the exfiltration of potentially sensitive data. Tools like this are used to fingerprint a server and exploit known vulnerabilities.

There are many resources for the Metasploit Framework, including the Metasploit Unleashed website. Both the `Metasploit.com` website and the `exploit-db.com` site offer information and downloads of additional exploits that can assist in customizing your penetration test:

- `www.metasploit.com/modules/`
- `www.exploit-db.com/`
- `www.offensive-security.com/metasploit-unleashed/Metasploit_Unleashed_Information_Security_Training`
- `www.amazon.com/Metasploit-The-Penetration-Testers-Guide/dp/159327288X`

## Lab A20: Sniffing NETinVM Traffic with Wireshark

You installed Wireshark on your host system back in Lab A2. To capture traffic from your virtual network, you need to install the Microsoft Loopback Adapter on your host machine.

In Windows Vista and 7, this feature can be enabled in Control Panel. Take the following steps to enable the loopback network adapter in Windows 7 or Vista using the New Hardware Wizard:

1. Click Start, enter `hdwwiz`, and then click Next.
2. Choose **Install Hardware Manually** from the list that appears, and click Next.
3. Select **Network Adapter** and click Next.
4. Select **Microsoft** and **Microsoft Loopback Adapter**, click Next twice, and choose Finish.

Note that Network Discovery and File Sharing need to be enabled while performing exercises that require communication between the host and guest systems through the Windows Firewall. Instructions for doing so under Windows Vista and 7 are located here:

- `http://windows.microsoft.com/en-US/windows-vista/Enable-or-disable-network-discovery`
- `http://windows.microsoft.com/en-US/windows7/Enable-or-disable-network-discovery`

Now you are ready to try using Wireshark to sniff virtual network traffic:

1. Open VMware Player, load NETinVM, and click **Run All**.
2. From the base system, open a Terminal.
3. Enter `su`, enter the passphrase, and enter `ifconfig`. Observe that no IP address has been assigned to the `eth0` interface. (`su` refers to SuperUser, a Unix administrator.)
4. Enable Network Discovery and File Sharing under the host Windows OS Network and Sharing.
5. Connect to the VMware Player Network Adapter.
6. Perform another `ifconfig` from within the base system and note that `eth0` now has an IP address. Take note of the IP address that has been assigned to `eth0`.
7. Open a terminal from the Windows host and enter `ipconfig /all`. Take note of the VMNet interface that is located within the same subnet as your base system's `eth0` interface. In my lab this was `VMnet8`, which was assigned an IP address of `192.168.184.1`. The base system's `eth0` interface was assigned the IP address `192.168.184.128`.
8. Verify connectivity between the two; enter `ping 192.168.184.128` from your Windows host.
9. Test the path from your Windows host to the base system. Enter `tracert 192.168.184.128`. Observe that you now have a direct connection. This performs like a virtual switch.
10. Verify connectivity from the base system to the Windows host; enter `ping 192.168.184.1`.
11. Now that you have verified connectivity, you can capture some live traffic. Open Wireshark on the Windows host.
12. Select the appropriate VMware Adapter, probably the last one listed, and click **Capture**.
13. From your base system, enter `ping 192.168.184.1` in order to generate some ICMP traffic; then stop the ping with `Ctrl+C`.
14. Stop the capture by clicking the **Stop The Running Live Capture** icon from the main toolbar and briefly peruse the results.
15. In the packet list pane, highlight the first ICMP ping request.
16. In the packet details pane, expand everything.
17. Double-click on **Response In: #**. You are now viewing the echo reply to the initial request.
18. In the packet details pane, under header checksum, select the source IP address.
19. Start Wireshark under your base system in NETinVM.
20. Capture traffic over the `tap0` interface; recall this is the external network.
21. Log into exta as root and attempt to elicit a connection over port 31337 with the base system using netcat. Enter `nc 10.5.0.1 31337`. This connection will be refused.
22. Return to the base system and stop the Live capture.
23. Observe the results.
24. Now you will play with some simple Wireshark Display Filters. I'm also providing the URL to Wireshark Capture Filters, which we will discuss shortly.
25. - `http://wiki.wireshark.org/DisplayFilters`
    - `http://wiki.wireshark.org/CaptureFilters`
26. Enter `http` in the filter toolbar and click **Apply**. This is a basic example of perhaps the strongest feature of Wireshark. It's famous for its filtering capabilities.
27. Click **Clear**.
