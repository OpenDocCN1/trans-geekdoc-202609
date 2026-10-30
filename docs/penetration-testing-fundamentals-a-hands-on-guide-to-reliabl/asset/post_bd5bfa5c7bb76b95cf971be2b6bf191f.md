
![](img/fa54c6d61c14db5421f8f63e6d594bb5_286_0.png)

FIGURE 11-7 recon/domains-vulnerabilities/xssposed.

## Dmitry

Dmitry is Deepmagic Information Gathering Tool. It is essentially a search and scanning tool. Figure 11-8 shows the available options.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_286_1.png)

FIGURE 11-8 Dmitry.

Let’s use Dmitry on my own website again. We will type in

```
dmitry -i -s -e www.chuckeasttom.com
```

- **-i** is a whois lookup.
- **-s** is a search for subdomains.
- **-e** is a search for email addresses.

Figure 11-9 shows the results.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_287_0.png)

FIGURE 11-9 Dmitry Scanning.

As you can see, Dmitry is another easy to use reconnaissance tool that is part of Kali Linux.

## Sparta

Sparta is a tool that gives you access to many vulnerability scanners in one, including:

- Mysql-default
- Nikto
- Snmp-enum
- Smtp-enum-vrfy
- Snmp-default
- Snmp-check

Sparta is also an easy to use GUI tool, rather than command line. Figure 11-10 shows a host being added to the scanner.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_288_0.png)

FIGURE 11-10 Sparta Main Screen.

Among other items, Sparta includes a basic nmap scan as demonstrated in Figure 11-11.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_289_0.png)

FIGURE 11-11 Sparta Scan Results.

Sparta even includes a brute force password cracker, as shown in Figure 11-12.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_289_1.png)

FIGURE 11-12 Sparta Brute Force Cracker.

## John the Ripper

John the Ripper is a well-known password cracking tool. Kali Linux has a shell version of John the Ripper and a GUI version named Johnny, seen in Figure 11-13.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_290_0.png)

FIGURE 11-13 Johnny.

It is fairly easy to use, particularly with the GUI. You must keep in mind, however, that there is no guaranteed password cracker. Any password cracking tool can simply make its best effort to crack a password.

## Hashcat

Hashcat is a rainbow table tool that tries to find passwords. It is completely shell, no GUI. Its main strength is that it can work with a variety of hash formats. Different applications can store their hashed passwords in a variety of ways. Hashcat can handle several widely used formats, including Mac OS X, as shown in Figure 11-14.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_291_0.png)

FIGURE 11-14 Hashcat.

## macchanger

This particular tool is meant to change the MAC address your Kali machine sends out. That makes it more difficult to trace the attack back to the Kali machine. Also, MAC spoofing can be a way to circumvent some forms of authentication. Figure 11-15 shows the available macchanger options.

macchanger is a very easy to use tool. You can see in Figure 11-15 that it consists of just a few commands. The basic syntax is three steps:

STEP 1. Turn off your network card:

```
ifconfig eth0 down
```

STEP 2. Run macchanger as follows:

```
macchanger -m a1:b2:c3:11:22:33 eth0
```

or set it to some random number:

```
macchanger -r eth0
```

STEP 3. Bring your network card back up:

```
ifconfig eth0 up
```

If you get errors, the most common issue is not having root-level privileges.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_292_0.png)

FIGURE 11-15 macchanger.

### Note

While ifconfig is commonly used, it does have known bugs, some of which are listed in the man page. There is an alternative, the package iproute2, with the tool ip. Here are the equivalent ip commands for bringing up/down an interface and changing its MAC address:

- ip link set eth0 down
- ip link set address a1:b2:c3:11:22:33 eth0
- ip link set eth0 up

## Ghost Phisher

Ghost Phisher is a very versatile tool with several interesting functions. Figure 11-16 shows the main screen.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_293_0.png)

FIGURE 11-16 Ghost Phisher.

Each of the first four tabs on the left has settings to turn your Kali Linux machine into one of the following:

- A fake wireless access point
- A fake DNS server
- A fake DHCP server
- A fake HTTP server

There are also tabs for session hijacking and harvesting credentials.

The GHOST Trap tab will be more useful to you after you read through Chapter 12, “General Hacking Techniques.” This tab allows you to set up a fake website that downloads Metasploit exploits to computers that visit the fake website. You can see this in Figure 11-17.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_294_0.png)

FIGURE 11-17 Ghost Phisher GHOST Trap Settings.

Each of these tabs allows you to turn your Kali Linux machine into a trap of some type. This can be very useful in penetration testing.

## Summary

This chapter looked at many of the basic tools found in Kali Linux. Kali comes with literally hundreds of tools. The goal of this chapter was to introduce you to some of the more popular tools and provide you with a basic level of familiarity with their function. Once you have found tools that you prefer, you should spend more time getting more familiar with those specific tools.

## Test Your Skills

## MULTIPLE CHOICE QUESTIONS

- 1. What is the default password for Kali Linux?
  A. password
  B. toor
  C. root
  D. kali
- 2. What type of tool is John the Ripper?
  A. Password cracker
  B. Firewall breacher
  C. Vulnerability scanner
  D. Wi-Fi cracker
- 3. Which tool will work on Macintosh password hashes?
  A. Sparta
  B. Dmitry
  C. John the Ripper
  D. hashcat
- 4. Dmitry primarily is used for what?
  A. Password cracking
  B. Reconnaissance
  C. Web cracking
  D. Wi-Fi cracking

## PROJECTS

## PROJECT 1: Sparta

Perform a Sparta vulnerability analysis on your own IP address.

## PROJECT 2: recon-ng

Use recon-ng to gather information about a website of your choice. You can also use my website, www.ChuckEasttom.com.

## Chapter 12

## General Hacking Techniques

## Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

- Use Kali Linux to perform basic functions
- Understand social engineering
- Launch a denial of service attack

There are general techniques used in hacking (and in penetration testing) that you should be familiar with. These are techniques that attackers will often use against your network; therefore, you must test your network for these items. Some of these will use Kali Linux, which you learned about in Chapter 11, “Introduction to Kali Linux,” but others do not need Kali.

## Wi-Fi Testing

Wi-Fi testing is clearly needed in a penetration test. In this chapter I will briefly introduce the topic and some techniques that can be used to test Wi-Fi related security. Chapter 18, “Additional Pen Testing Topics,” will provide more specific techniques for attacking Wi-Fi.

## Create a Hotspot

With the ubiquitous nature of Wi-Fi, rogue hotspot attacks, also called evil twin attacks, are fairly common. There are many ways to set up a fake wireless access point (WAP); let us examine a few.

## The WiFi Pineapple

The WiFi Pineapple is a product from Hak5 LLC. The tool contains a number of Wi-Fi penetration testing tools and uses a web interface to configure. One of the things that the WiFi Pineapple can do is
set up a rogue access point. It then tracks the devices that connect to it and can be used to capture their traffic. You can get the WiFi Pineapple from https://www.wifipineapple.com/.

## Turn Your Laptop into a WAP

Many modern laptops have the capability of being a wireless access point. The laptop itself should first be connected to some Internet source (Wi-Fi or cellular) so it can route the incoming packets to that source. You will also need to have some packet sniffer running in order to view the data from the devices that connect to the laptop wireless access point. tcpdump or Wireshark will work well for this purpose, and both were discussed in Chapter 8, “Vulnerability Scanning.”

In Windows, you can simply use the network settings, as shown in Figure 12-1 for Windows 10. Note that how to find these settings will depend on what version of Windows you have. In Windows 10, typing settings into Cortana search brings you the result Network and Internet, which you have to click on to get to network settings.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_297_0.png)

FIGURE 12-1 Windows 10 Mobile Hotspot Settings.

You have probably used the first button, Wi-Fi, many times, and likely the second button, Airplane mode. The third button turns your laptop into a mobile hotspot. Simply clicking on it will activate it, after which you can right-click on it to get the Go to Settings option, as shown in Figure 12-2.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_297_1.png)

FIGURE 12-2 Turning On the Mobile Hotspot.
