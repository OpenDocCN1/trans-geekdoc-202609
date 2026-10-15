
start graphic ![cover](image_fi/book_art/cover.png) end graphic 

Table of Contents

[Cover](#cover.html)

[Chapter 1: Web Browser Security](#c01.html)

[A Principal Principle](#c01.html#h1-c01-0001)

[Exploring the Browser](#c01.html#h1-c01-0002)

[Evolutionary Pressures](#c01.html#h1-c01-0003)

[Core Security Problems](#c01.html#h1-c01-0004)

[Browser Hacking Methodology](#c01.html#h1-c01-0005)

[Summary](#c01.html#h1-c01-0006)

[Questions](#c01.html#h1-c01-0007)

[Chapter 2: Initiating Control](#c02.html)

[Understanding Control Initiation](#c02.html#h1-c02-0001)

[Control Initiation Techniques](#c02.html#h1-c02-0002)

[Summary](#c02.html#h1-c02-0003)

[Questions](#c02.html#h1-c02-0004)

[Chapter 3: Retaining Control](#c03.html)

[Understanding Control Retention](#c03.html#h1-c03-0001)

[Exploring Communication Techniques](#c03.html#h1-c03-0002)

[Exploring Persistence Techniques](#c03.html#h1-c03-0003)

[Evading Detection](#c03.html#h1-c03-0004)

[Summary](#c03.html#h1-c03-0005)

[Questions](#c03.html#h1-c03-0006)

[Chapter 4: Bypassing the Same Origin Policy](#c04.html)

[Understanding the Same Origin Policy](#c04.html#h1-c04-0001)

[Exploring SOP Bypasses](#c04.html#h1-c04-0002)

[Exploiting SOP Bypasses](#c04.html#h1-c04-0003)

[Summary](#c04.html#h1-c04-0004)

[Questions](#c04.html#h1-c04-0005)

[Chapter 5: Attacking Users](#c05.html)

[Defacing Content](#c05.html#h1-c05-0001)

[Capturing User Input](#c05.html#h1-c05-0002)

[Social Engineering](#c05.html#h1-c05-0003)

[Privacy Attacks](#c05.html#h1-c05-0004)

[Summary](#c05.html#h1-c05-0005)

[Questions](#c05.html#h1-c05-0006)

[Chapter 6: Attacking Browsers](#c06.html)

[Fingerprinting Browsers](#c06.html#h1-c06-0001)

[Bypassing Cookie Protections](#c06.html#h1-c06-0002)

[Bypassing HTTPS](#c06.html#h1-c06-0003)

[Abusing Schemes](#c06.html#h1-c06-0004)

[Attacking JavaScript](#c06.html#h1-c06-0005)

[Getting Shells using Metasploit](#c06.html#h1-c06-0006)

[Summary](#c06.html#h1-c06-0007)

[Questions](#c06.html#h1-c06-0008)

[Chapter 7: Attacking Extensions](#c07.html)

[Understanding Extension Anatomy](#c07.html#h1-c07-0001)

[Fingerprinting Extensions](#c07.html#h1-c07-0002)

[Attacking Extensions](#c07.html#h1-c07-0003)

[Summary](#c07.html#h1-c07-0004)

[Questions](#c07.html#h1-c07-0005)

[Chapter 8: Attacking Plugins](#c08.html)

[Understanding Plugin Anatomy](#c08.html#h1-c08-0001)

[Fingerprinting Plugins](#c08.html#h1-c08-0002)

[Attacking Plugins](#c08.html#h1-c08-0003)

[Summary](#c08.html#h1-c08-0004)

[Questions](#c08.html#h1-c08-0005)

[Chapter 9: Attacking Web Applications](#c09.html)

[Sending Cross-origin Requests](#c09.html#h1-c09-0001)

[Cross-origin Web Application Detection](#c09.html#h1-c09-0002)

[Cross-origin Web Application Fingerprinting](#c09.html#h1-c09-0003)

[Cross-origin Authentication Detection](#c09.html#h1-c09-0004)

[Exploiting Cross-site Request Forgery](#c09.html#h1-c09-0005)

[Cross-origin Resource Detection](#c09.html#h1-c09-0006)

[Cross-origin Web Application Vulnerability Detection](#c09.html#h1-c09-0007)

[Proxying through the Browser](#c09.html#h1-c09-0008)

[Launching Denial-of-Service Attacks](#c09.html#h1-c09-0009)

[Launching Web Application Exploits](#c09.html#h1-c09-0010)

[Summary](#c09.html#h1-c09-0011)

[Questions](#c09.html#h1-c09-0012)

[Chapter 10: Attacking Networks](#c10.html)

[Identifying Targets](#c10.html#h1-c10-0001)

[Ping Sweeping](#c10.html#h1-c10-0002)

[Port Scanning](#c10.html#h1-c10-0003)

[Fingerprinting Non-HTTP Services](#c10.html#h1-c10-0004)

[Attacking Non-HTTP Services](#c10.html#h1-c10-0005)

[Getting Shells using BeEF Bind](#c10.html#h1-c10-0006)

[Summary](#c10.html#h1-c10-0007)

[Questions](#c10.html#h1-c10-0008)

[Chapter 11: Epilogue: Final Thoughts](#c11.html)

[Introduction](#flast.html)

[Overview of This Book](#flast.html#h1-flast-0001)

[Who Should Read This Book](#flast.html#h1-flast-0002)

[How This Book Is Organized](#flast.html#h1-flast-0003)

[What’s on the Web](#flast.html#h1-flast-0004)

[Compiling Your Arsenal](#flast.html#h1-flast-0005)

[Authorization Denied](#flast.html#h1-flast-0006)

[Good to Go!](#flast.html#h1-flast-0007)

 start graphic ![titlepage](image_fi/book_art/titlepage.png) end graphic 

# Chapter 1

# Web Browser Security

A lot of responsibility is placed upon the broad shoulders of the humble web browser. The web browser is designed to request instructions from all over the Internet, and these instructions are then executed almost without question. The browser must faithfully assemble the remotely retrieved content into a standardized digestible form and support the rich feature set available in today’s Web 2.0.

Remember, this is the same software with which you conduct your important affairs—from maintaining your social networks to online banking. This software is also expected to protect you even if you venture down the many figurative dark alleys of the Internet. It is expected to support venturing down such an alleyway while making a simultaneous secure purchase in another tab or window. Many assume their browser to be like an armored car, providing a secure and comfortable environment to observe the outside world, protecting all aspects of one’s personal interests and deflecting anything dangerous. By the end of this book, you will have the information to decide if this is a sound assumption.

The development team of this “all singing and all dancing” software has to ensure that each of its numerous nooks and crannies don’t provide an avenue for a hacker. Whether or not you consciously know it, every time you use a browser, you are trusting a team of people you have probably never met (and likely never will) to protect your important information from the attackers on the Internet.

This chapter introduces a methodology for web browser hacking that can be employed for offensive engagements. You explore the web browser’s role in the web ecosystem, including delving into the interplay between it and the web server. You also examine some browser security fundamentals that will provide a bedrock for the remaining chapters of this book.

# A Principal Principle

We invite you to forget about the web browser for a moment and reflect on a blank security canvas. Picture yourself in this situation: You are in charge of maintaining the security of an organization, and you have a decision to make. Do you deploy a piece of software based on the level of risk it will pose? The software will be installed on the Standard Operating Environment (SOE) for almost every machine in an organization. It will be used to access the most sensitive data and conduct the most sensitive operations. This software will be a staple tool for virtually all staff including the CEO, Board, System Administrators, Finance, Human Resources, and even customers. With all this control and access to business-critical data, it certainly sounds like the hacker’s dream target and a high-risk proposition.

The general specifications of the software are as follows:

*   It will request instructions from the Internet and execute them.

*   The defender will not be in control of these instructions.

*   Some instructions tell the software to get more instructions from:

*   Other places on the Internet

*   Other places on the intranet

*   Non-standard HTTP and HTTPS TCP ports

*   Some instructions tell the software to send data over TCP. This can result in attacks on other networked devices.

*   It will encrypt communication to arbitrary locations on the Internet. The defender will not be able to view the communication.

*   It will continually increase what attackers can target. It will update in the background without notifying you.

*   It often depends on plugins to allow effective use. There is no centralized method to update the plugins.

In addition, field research into the software reveals:

*   The plugins are generally considered to be less secure than the core software itself.
