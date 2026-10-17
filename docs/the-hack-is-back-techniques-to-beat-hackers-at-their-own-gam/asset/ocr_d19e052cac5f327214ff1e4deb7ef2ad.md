For us to attempt to use default credentials, we must first find potential devices. This is covered in detail in Chapter 3, Web Application Hacking, where we are searching for many types of subdomains and open ports. In the context of this chapter, we will be exploring a simple IP range on a sample local subnet.

To find devices on the network, we must start with a port scan. Based on the intelligence from our initial starting point, we can determine what our local subnet is and where we are located logically. This can be found with our IP address on our system, using commands such as ip a for Linux and ipconfig /all for a Windows machine.

In the example below, we can see that the IP address in interface eth0 has been assigned the IP address of 192.168.40.191 with a CIDR of 24. This indicates that the local subnet is within the range of 192.168.40.0/24.

```
(chris@kali) - [~/config]
└$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host proto kernel_lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:02:29:0b brd ff:ff:ff:ff:ff:ff
    inet 192.168.40.191/24 brd 192.168.40.255 scope global dynamic noprefixroute eth0
       valid_lft 23754sec preferred_lft 23754sec
    inet6 fe80::20c:29ff:fe02:290b/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```

Using that information, we can scan the 192.168.40.0/24 subnet for active devices. The tool nmap is well suited for this and has been available for decades. From an operational perspective, we're looking for devices that are available on the network and have open ports. We can accomplish this with a command similar to below:

```
$ sudo nmap -sV -sC 192.168.40.0/24 -oA nmap_output
```

This command scans the local network we're on and searches for the top 1,000 most common TCP ports. It will additionally try to fingerprint what services are available with the -sV switch, and some common enumeration scripts with the -sC switch, and then save the output in multiple formats with the -oA switch. One of the most important formats we'll use in later tools is the XML type, in our example the output will be saved as nmap_output.xml.

Now that we have a sense of the assets available on the network, we need to determine which ones have available services to log into. There are many ways to help determine this, but one of the easiest ways to identify web services is with the EyeWitness program. This will take the XML formatted file we created and automate taking screenshots of applicable web services for us to review. Using a report of compiled screenshots allows us to quickly review and determine if a website is potentially vulnerable or may be worth investigating further.

EyeWitness can be run using the following command:

```
$ eyewitness -x nmap_output.xml --delay 15
```

What this does is read from the XML file we created with nmap, then wait 15 seconds to take a screenshot for each web service. The delay is important, as many IoT devices have lower power and can take longer than expected to load a webpage.