# WEB-BASED SERVICES

# 17

+   * Application initialization
* Dynamic IP address restrictions
* Centralized SSL Certificate Support
* CPU throttling
* FTP logon attempt restrictions
* Server Name Indication (SNI) support
* Improved SSL and configuration scalability
* Support for multicore scaling on NUMA architecture

Even if you're not needing a webserver by date, it's never a bad idea to understand the current Windows server—so not skip Chapter 19, "Web Server Management with IIS."

# MICROSOFT MANAGEMENT CONSOLE GETS THE AXE!

| In Windows Server 2012 R2 the Microsoft Management Console (MMC) snap-in is deprecated for Internet Information Services (IIS) Manager 6.0. In future releases of Windows Server, this will be removed. |

# FTP Server

Microsoft gets some right and some things wrong. In a few cases, the company gets things terribly wrong, as was the case with the built-in File Transfer Protocol (FTP) server software that shipped with Windows for the past 15 years or so. It was clunky, was so difficult to configure, and offered much minimally logs and an inability to configure things that should have been childishly easy to configure (such as user home directories) that just about everyone who needed a Windows FTP server ended shelling out a few bucks for a third-party FTP. Starting with Windows Server 2008 and R2, however, things changed considerably. As far as we can see, Microsoft tossed out all the FTP server code and rebuilt it from scratch. In Windows Server 2012 R2, they also added the ability to restrict the number of failed logon attempts that can be made to an FTP account in a certain period. If you need a Windows-based FTP server, flip over to the IIS chapter (Chapter 19) to learn about the new changes to the FTP server.

You can read more about web server management in Chapter 19.