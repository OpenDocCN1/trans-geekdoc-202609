
Another important physical security threat against systems that you should be aware of is human error. For example, an employee trying to perform an upgrade to a system—maybe adding memory or replacing a hard drive—could fry the motherboard of the system through `electrostatic discharge (ESD)`. ESD is the buildup of static electricity on yourself that is transferred to another object such as a computer component when you touch it. This transfer of static electricity is enough to kill or seriously damage computer components.

To prevent this type of situation, educate the desktop support team on ESD and on using an antistatic wrist strap in order to always ground themselves before servicing the systems.

#### Sabotage

Another common threat against systems is sabotage, which is typically, but not always, the result of a disgruntled employee. It is important to identify situations where company assets are vulnerable to sabotage. Too many times in my security courses I hear stories from students about incidents where a company database was tampered with by a disgruntled employee.

You need to identify systems that are susceptible to sabotage and be sure to have a recovery plan in place for those systems. A `recovery plan` involves step-by-step procedures to recover the system, but also ensures that you have adequate spare parts on the shelf in the server room.

### CERTIFICATION OBJECTIVE 5.03

### Looking at Malicious Software

Now that you understand some of the popular physical threats against systems, let’s take a look at some types of malicious software that pose a threat to systems today. Malicious software is any software that harms or misuses the system, which includes deleting files from the system, monitoring activity on the system, and even something as simple as slowing down the system.

#### Privilege Escalation

Privilege escalation is when a hacker finds a flaw in the operating system, or in a piece of software installed on the system, that, when exploited, elevates the hacker’s privileges from normal user capabilities to administrative access. Once the hacker has gained administrative access to the system, they can make whatever changes they want to the system, including planting a back door for future access.

There are three types of privilege escalation:

- **Vertical privilege escalation** When someone with normal user access is able to raise their privileges to administrative access
- **Horizontal privilege escalation** When the same level of access is maintained, but the resource being accessed is different
- **Privilege de-escalation** When someone with administrative access is able to lower their privilege level so that they can access data that a specific user has access to

#### Viruses

One of the biggest areas of concern with security is when a system is overtaken with a virus. A virus is malicious software that infects a system such as a computer, tablet, or smart phone. The infection can destroy data on the system, prevent the system from booting, or simply use resources on the system, which results in slowing the system down. This section discusses common types of viruses.

##### Executable Virus

Older viruses were executable viruses, where the virus was attached to an executable file but was not activated until you ran the file. This virus was typically spread from system to system by the user sharing files via floppy disks, flash drives, or a network drive.

##### Boot Sector Virus

A boot sector virus is a serious virus that attacks the boot sector code and overwrites it. The boot sector is the first sector on the disk and contains operating system loader code that starts the boot sequence. When a boot sector virus overwrites this sector, it prevents the system from booting from the infected disk.

##### Macro Virus

Most applications today support macros, which are a way to automate a task within the software application. With the Microsoft Office suite, for example, we are able to create macros using Visual Basic for Applications (VBA), which is a powerful program language that can manipulate the application and the operating system.

A macro virus is code that is written using a macro language that performs a malicious action such as deleting files or e-mailing everyone in your address book. The macro is usually created in a file and then triggered automatically when someone opens the file.

##### Logic Bomb Virus

A logic bomb is a type of virus that is planted on the system by you installing a piece of software that contains the logic bomb. The software application you installed acts as it is supposed to until a certain event, such as a specific date, occurs. When you run the software, it always checks for that specific date, and if the software is run on that date, it performs its malicious act. This is a common method disgruntled employees have used to sabotage company data after quitting or being fired. They program the software (which normally runs fine) to delete data on a specific date.

![Image](exam.jpg)

**For the exam, know that the logic bomb virus waits for a specific event, such as a certain date, to occur before being activated.**

##### Worm Virus

A worm virus is a harmful and common virus today. The worm virus is a scary virus type because it has the unique characteristic of being able to replicate itself without needing a user to activate it. Worm viruses can replicate themselves in a number of ways:

- **Network protocols** A worm virus can replicate itself automatically across the network by using standard network protocols and compromising a system through vulnerabilities in networking applications running on the system. A good example is the Blaster worm from 2003 that replicated over the RPC port (port 135). Who could forget the SQL Slammer worm virus, also from 2003, which infected approximately 75,000 systems on the Internet in 10 minutes? SQL Slammer exploited a known buffer overflow vulnerability on SQL Server and connected to nonpatched SQL Servers over UDP port 1434.
- **E-mail** Worm viruses can be spread automatically using e-mail. The virus is sent to a user in an e-mail message, and when that user opens the message, the virus code executes and loops through the user’s contact list and sends the e-mail to all the contacts. Examples of infamous e-mail viruses are the ILOVEYOU virus in 2000 and the virus that was sent with a subject line reading “Here you have” in 2010.
- **Flash drives** A new wave of worm viruses infects systems by replicating through the use of flash drives (thumb drives). Once the worm virus is on a system, it waits for someone to plug in a flash drive on that system, and the worm virus then replicates to the thumb drive. The user takes the thumb drive to another system, and once the drive is connected to the USB port, the virus replicates from the thumb drive to the system. Conficker was a worm virus that could replicate through the use of USB thumb drives.

##### Trojan Virus

A Trojan virus is a program that a user is tricked into installing because it appears to do something useful, but in reality, it is a virus that infects the system. The Trojan virus typically modifies the system by opening a TCP/IP port on the system, which allows the hacker to connect to the system and take control of it.

It should be noted that the Trojan virus can do more than open a port on the system, and because most people have firewalls today to block access to the port the Trojan opens, you may find that the Trojan virus puts adware on the system or a keylogger.

[Table 5-1](#ch05.xhtml#ch5tab1) list the popular Trojan viruses and the ports they open on a system.

TABLE 5-1  

Popular Trojan Virus Port Numbers

![Image](t0198-01.jpg)

![Image](exam.jpg)

**You should know that a Trojan virus typically opens a TCP/IP port on the system to act as a back door for the hacker. You should also know that a worm virus is a self-replicating virus.**
