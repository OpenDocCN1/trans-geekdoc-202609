
#### Protecting Against Malicious Software

For the Security+ certification exam, you need to know about the different types of malicious software, but you also need to know how to protect against malicious software. The following is a list of countermeasures against malicious software:

- **Use antivirus software.** Ensure that you are using antivirus software on all desktop clients and servers. Ensure that the antivirus software supports real-time protection that will scan files and memory for viruses as you access data.
- **Keep virus definitions up to date.** The virus definition database is a listing of known viruses, and it is critical to keep the database up to date so that your virus protection software knows about the latest viruses.
- **Keep a close eye on listening ports.** You can use the `netstat` command in Windows and Linux to view a listing of listening ports.
- **Keep a close eye on running processes.** You can use the `tasklist` command in Windows or the `ps -A` command in Linux to view a listing of running processes. It is important to closely watch what processes are running in the background.
- **Use good surfing habits.** Educate your users to stay away from unknown web sites and to not open attachments received in e-mail messages from unknown sources.

If you are looking for some free software to help protect against malicious software or even to remove malicious software, you can use the following:

- **Windows Defender** This is virus protection, spyware protection, and malware protection software that Microsoft includes in all supported operating systems. Like other virus protection software, Windows Defender offers real-time protection against malware.
- **Microsoft Malicious Software Removal Tool** If you have a system that has been infected, you can download the Malicious Software Removal Tool from Microsoft, which is updated on a regular basis. It is a great tool to help remove malicious software from an infected system.

Another point that should be made is that if you find you have an infected system, you cannot trust any software running on that infected system, including antivirus software. In this situation, you will need to boot off a live disc or USB stick that has its own operating system and virus protection software. Once you boot off the live OS, you can then launch the antivirus software from the live OS to scan the system and remove viruses.

### CERTIFICATION OBJECTIVE 5.04

### Threats Against Hardware

Not only do you need to worry about system threats such as malicious software when protecting your systems, but you also need to worry about hardware-related features of a system that should be secured. In this section, you learn about popular hardware features for properly securing a system.

#### BIOS Settings

The BIOS chip in a computer contains the low-level code that is used to communicate with the hardware in a system. The BIOS code also contains what is known as the *CMOS setup program*, which is a program used to configure hardware settings on the system such as the types of memory and drives in the system and the date and time on the computer.

As it relates to security, the CMOS setup program (an example of which is shown in [Figure 5-8](#ch05.xhtml#ch5fig8)) can be used to control which devices can be booted from. It is a security best practice to ensure that systems can boot only from the local hard disk and not from the network card, USB drive, or an optical disc drive that exists on the system. It is too easy for someone to use a live disc (a USB drive or DVD containing a bootable OS) to boot an OS into memory to gain access to the system. To ensure this does not happen, configure CMOS to not allow booting from anything but the hard disk, if possible.

![Image](f0208-01.jpg)

FIGURE 5-8  

Using CMOS settings to help secure a system

In the CMOS setup program, you can also set up a “user” password, which is a password required to use the system. Do not confuse this password with the Windows password, because the CMOS password appears *before* the operating system is loaded. Also make sure you set up an “administrator” password, which is a password required if someone wants to change the CMOS settings.

If you are worried about people connecting unauthorized devices to the computer and potentially taking data away with them or compromising the system through the unauthorized device, you should ensure that unnecessary ports are disabled through the CMOS setup program.

#### USB Devices

Regarding ports, it is important to update your security policy and to educate users on what types of data are allowed to be placed on USB drives. Because it is easy for employees to take a copy of data with them on a flash drive, the security policy must be clear regarding what data types are allowed to be placed on USB drives. In high-security environments, you may decide that the USB ports should be disabled so that they cannot be used.

![Image](exam.jpg)

**Because worm viruses are known to replicate from a thumb drive to a system, you should consider disabling the USB ports on systems in the office.**

One of the important risks surrounding the use of USB thumb drives is that an employee could have a virus on their system at home and place the USB drive in their system, enabling the worm virus to replicate to the thumb drive. The security issue with this from a business point of view is that if the employee takes the thumb drive to the office and connects it to a system, the virus could replicate to the work systems.

#### Smart Phones and Tablets

Mobile devices such as smart phones and tablets are critical devices in today’s business operations. Most employees are given a phone or tablet as part of their employment, and it is important to keep data on the mobile devices secure. Most of today’s cell phones are known as smart phones because they do more than make phone calls. They store business contact information and sensitive documents, and they have data plans that allow connections to the Internet for purposes of checking e-mail and browsing the Internet.

From a security point of view, ensure that employees are locking their smart phones and tablets when not in use and that they are encrypting the data on these devices. This will protect the company from having someone outside the company viewing confidential data on an employee’s phone if it is lost or stolen.

As a security professional, you should research the vulnerabilities of all mobile devices used by employees in your business. It is important to be familiar with all the features of devices used by your company and to educate yourself on the different vulnerabilities that exist with each of these products.

Because most mobile devices today use Bluetooth, a wireless technology that allows one Bluetooth device to communicate with another Bluetooth device over a short distance (up to 30 feet), it is easy for hackers to communicate with your phone and to steal data from it if Bluetooth is enabled. Today’s phones are vulnerable to various attacks, including the following:

- **Bluesnarfing** A Bluetooth exploit that allows the hacker to connect to a Bluetooth-enabled phone and to retrieve data off the phone
- **Bluejacking** The sending of unsolicited messages from one Bluetooth device to another Bluetooth device
- **Bluebugging** A Bluetooth exploit that involves the hacker gaining access to the phone and leveraging its full capabilities, including making calls using the AT command set on the phone

### EXERCISE 5-2

![Images](video.jpg)

**Exploiting a Bluetooth Device**

In this exercise, you use Kali Linux to learn commands related to the concept of bluesnarfing—the attack type that exploits Bluetooth devices such as smart phones and tablets.

1. Ensure that you have Kali Linux running with a Bluetooth card installed.
2. Go to the Kali Linux system and start a terminal.
