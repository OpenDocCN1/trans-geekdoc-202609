
These aren't the only things we can enumerate when it comes to web applications. We could scan networks for different web applications or look to enumerate users. Looking for directories that are on the web server is also useful because it can help us identify applications as well as data that may be available.

### Countermeasures

There is a lot of information that can be leaked from web servers. There are some techniques you can use to protect against web‑based enumeration, though.

*   **Restrict Information Provided**   Headers and error messages should not provide information about the server and especially version numbers, including information about the underlying operating system or application stack.

*   **Use Appropriate Access Control**   Ensure all web applications have strong authentication enabled and appropriate access controls to protect resources from unauthorized users.

*   **Disable Directory Listings**   Disable open directory listings from web servers to protect potentially sensitive files from open access.

## Summary

Enumeration is the process of gathering a lot of information further up the network stack than just IP addresses and ports. At this point, we are moving up to the Application layer. We're looking for things like usernames, where we can find them, and network shares and any other footholds we may be able to gather. To accomplish this enumeration work, there are a number of protocols and tools that we can use. The first is `nmap`, because we need to go beyond just identifying open ports. We need to identify the services that are in use, including the software being used. One feature of `nmap` that is useful, especially in these circumstances, is its scripting capability. This includes, especially, all the scripts that are built into `nmap`.

When it comes to `nmap`, there are scripts that can be used not only to probe services for additional details but also to take advantage of the many enumeration capabilities. One of the protocols we can spend time looking at is the SMB protocol. `nmap` includes a number of scripts that will probe systems that use SMB. This includes identifying shares that may be open as well as, potentially, users and other management‑related information that can be accessed using SMB.

SMB relies on RPCs. NFS, a file sharing protocol developed by Sun Microsystems, also uses RPC. We can use `nmap` to enumerate RPC services, since these services register dynamically with a mapping or registry service. Probing the RPC server will provide details about the programs and ports that are exporting RPC functionality. If the program is written in Java, it will use RMI instead of `portmap` or the SunRPC protocol.

Another program you can use across a number of protocols for enumeration is Metasploit. Metasploit comes with lots of modules that will enumerate shares and users on SMB, services using SunRPC, and a number of other protocols. If there is information that can be enumerated, Metasploit probably has a module that can be run. This includes modules that will enumerate users in mail servers over SMTP. You can also enumerate information using SNMP. Of course, when it comes to SNMP, you can also use tools like `snmpwalk`.

While Metasploit can be used across a lot of different protocols to look for different pieces of useful information, it is not the only tool you can use. There are built‑in tools for gathering information from SMB, for example. You're more likely to find those tools on Windows systems, but you can also find tools on Linux systems, especially if you have Samba installed. Samba is a software package that implements the SMB protocol on Unix‑like systems. There are also a lot of open source tools that can be used for different protocols. If you are OK with using Linux, Kali Linux is a distribution that includes hundreds of security‑related tools.

As you are performing this enumeration, you should be taking notes so you have references when you are going forward. One advantage to using Metasploit, not to oversell this software, is that it uses a database backend, which will store a lot of information automatically. This is certainly true of services and ports but also of usernames that have been identified. This is not to say that Metasploit can be used to store every aspect of your engagement, but you can refer to details later by querying the Metasploit database as needed.

Every service that can be enumerated should have countermeasures deployed to protect those services. Each service will have different countermeasures, though in general, restricting who has access to the different services, to the extent possible, will help protect the service from having information gathered easily.

## Review Questions

You can find the answers in the appendix.

1.  What are RPCs primarily used for? 

    1.  Interprocess communications

    2.  Interprocess semaphores

    3.  Remote method invocation

    4.  Process demand paging

2.  What would you be trying to enumerate if you were to use enum4linux? 

    1.  Procedures

    2.  Linux‑based services

    3.  Shares and/or users

    4.  Memory utilization

3.  How do you authenticate with SNMPv1? 

    1.  Username/password

    2.  Hash

    3.  Public string

    4.  Community string

4.  What SMTP command would you use to get the list of users in a mailing list? 

    1.  `EXPD`

    2.  `VRFY`

    3.  `EXPN`

    4.  `VRML`

5.  What type of enumeration would you use the utility `dirb` for? 

    1.  Directory listings

    2.  Directory enumeration

    3.  Brute‑force dialing

    4.  User directory analysis

6.  What are data descriptions in SNMP called? 

    1.  Management‑based information

    2.  Data structure definition

    3.  Extensible markup language

    4.  Management information base

7.  What is the process Java programs identify themselves to if they are sharing procedures over the network? 

    1.  RMI registry

    2.  RMI mapper

    3.  RMI database

    4.  RMI process

8.  You are working with a colleague, and you see them interacting with an email server using the `VRFY` command. What is it your colleague is doing? 

    1.  Verifying SMTP commands

    2.  Verifying mailing lists

    3.  Verifying email addresses

    4.  Verifying the server config

9.  What is the SMB protocol used for? 

    1.  Data transfers using NFS

    2.  Data transfers on Windows systems

    3.  Data transfers for email attachments

    4.  Data transfers for Windows Registry updates

10.  Which of these is a built‑in program on Windows for gathering information using SMB? 

     1.  `nmblookup`

     2.  `smbclient`

     3.  Metasploit

     4.  `nbtstat`

11.  What status code will you get if your attempt to use the `VRFY` command fails? 

     1.  550

     2.  501

     3.  250

     4.  200

12.  What program would you use to enumerate services? 

     1.  `smbclient`

     2.  `nmap`

     3.  `enum4linux`

     4.  `snmpwalk`

13.  Which version of SNMP introduced encryption and user‑based authentication? 

     1.  1

     2.  2

     3.  2c

     4.  3

14.  Which of these could you enumerate on a WordPress site using `wpscan`? 

     1.  Plugins

     2.  Posts

     3.  Administrators

     4.  Versions

15.  Which of these tools allows you to create your own enumeration function based on ports being identified as open? 

     1.  Metasploit

     2.  `nmap`

     3.  Netcat

     4.  `nbtstat`

16.  What underlying functionality is necessary to enable Windows file sharing? 

     1.  Network File System

     2.  Common Internet File System

     3.  Remote procedure call

     4.  Remote method invocation

17.  What is the `IPC$` share used for? 

     1.  Process piping

     2.  Interprocess construction

     3.  Remote process management

     4.  Interprocess communication

18.  What tool does a Java program need to use to implement remote process communication? 

     1.  JRE

     2.  `rmic`
