
## 12.

You are the network administrator and have configured shared folder permissions and NTFS permissions on the accounting folder. You have given the accountants the NTFS permission of Read but the share permission of Change. What is the effective permission when the accountants connect to the share from across the network?

A. Full Control

B. Read

C. Change

D. Read + Change

### Performance-Based Questions

## 13.

Write the command you would use in Linux to set the permissions on a file called `test.txt` so that the owner has Read, Write, and Execute permissions, while all others only have Read: _______________________________________________________________________

## 14.

Match the following terms to their description by drawing a line from the term on the left to the description on the right.

![Image](f0323-01.jpg)

## 15.

Place the environments listed on the left in the proper order where applications should be tested.

![Image](f0323-02.jpg)

## SELF TEST ANSWERS

### Host and Application Security Solutions

## 1.

![Image](boxt.jpg) **B.** Salting is taking a random value and joining it with the value being hashed, in this case the password, in order to create a hash value that is better protected against password-cracking tools that run dictionary words through hashing in order to crack passwords.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. Encryption is not used with hashing; it would be used instead of. Tokens are used with sensitive data in a database such as credit card numbers. Secure Boot is a boot integrity technology that prevents the system from booting from an altered boot state.

## 2.

![Image](boxt.jpg) **C.** Tokenization is when sensitive data is substituted with random, nonrelevant data and the mapping of the sensitive data and substituted data is stored in a token service. Applications then send a request to the token service to look up the sensitive data by supplying the substituted data.

![Image](boxx.jpg) **A, B,** and **D** are incorrect. Encryption is used to protect sensitive data in a database, but tokenization is common with sensitive data that is used frequently. Salting is when a random value is combined with data and then the combination of the two are run through the hashing algorithm. Hashing is when data is run through a hashing algorithm to create a unique hash value (checksum type value).

## 3.

![Image](boxt.jpg) **D.** Data loss prevention (DLP) is a solution that prevents data leaks from occurring, such as someone sending sensitive information in an e-mail message or downloading the data to a USB drive.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. Anti-malware is software that prevents the system from virus infection. A host-based firewall is used to limit communication to a system. A next-generation firewall (NGFW) includes firewall features but also intrusion prevention features to stop an attack.

### Implementing Host-Based Firewalls and HIDS

## 4.

![Image](boxt.jpg) **D.** A host-based firewall should be used whenever a system is going to be connected to an untrusted network.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. These do not represent recommendations to implement regarding the security of Mark's laptop.

## 5.

![Image](boxt.jpg) **B.** Most firewalls have a default rule of deny all traffic once the firewall has been enabled.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. These do not represent the default rule. Most firewalls allow you to modify the default rule from deny all to allow all.

## 6.

![Image](boxt.jpg) **C.** The TCP wrappers feature in Linux allows you to control which clients can connect to which services.

![Image](boxx.jpg) **A, B,** and **D** are incorrect. Virtualization is the hosting of multiple operating systems in virtual machines on one physical machine. Cloud computing is having a provider host your servers for you while you connect to them remotely across the Internet for administration of the systems. A host-based firewall controls communication to the system.

## 7.

![Image](boxt.jpg) **A.** A host-based IDS analyzes log files, file attributes, and dynamic data such as connections and memory on the system to identify suspicious activity.

![Image](boxx.jpg) **B, C,** and **D** are incorrect. Network traffic and packet analysis are performed by network-based intrusion detection software. The TCP wrappers feature does not look for suspicious traffic; it simply controls access to services.

### Protecting Against Malware

## 8.

![Image](boxt.jpg) **B.** Windows Server Update Services (WSUS) is a service that allows you to download, review, approve, and deploy patches to groups of systems on the network.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. Virus protection and host-based firewalls do not deal with patching a system. Using Windows Update on every system is an administrative nightmare, so WSUS should be used.

## 9.

![Image](boxt.jpg) **D.** It is critical after installing antivirus software that you ensure the virus definitions are up to date. Most virus protection software can schedule the updating of virus definitions.

![Image](boxx.jpg) **A, B,** and **C** are incorrect. Host-based firewalls have nothing to do with maintaining the antivirus software, and you should not disable the automatic updates of virus definitions; you should *enable* them. You also should not disable real-time protection, because it scans files as they are accessed.

## 10.

![Image](boxt.jpg) **C.** Having an e-mail address available on the Internet, whether on a web page or submitted through someone's web site, always runs the risk that the e-mail address could be sent unsolicited messages.

![Image](boxx.jpg) **A, B,** and **D** are incorrect. Spyware, viruses, and phishing are not concerns associated with supplying an e-mail address.

### Device Security and Data Security

## 11.

![Image](boxt.jpg) **B** and **D.** You should ensure that you are locking the screen and encrypting data on the mobile device to protect it from unauthorized access.

![Image](boxx.jpg) **A, C,** and **E** are incorrect. You should have a password enabled instead of disabled, and never disable emergency calling, so that if the phone is locked, you can still call 911. Bluetooth should be disabled if not used, but most people use Bluetooth for wireless headsets.

## 12.

![Image](boxt.jpg) **B.** When the share permission conflicts with the NTFS permission, the most restrictive is applied—in this case, that is Read.

![Image](boxx.jpg) **A, C,** and **D** are incorrect. These are not the most restrictive permissions in the scenario.

### Performance-Based Questions

## 13.

The following command in Linux is used to set the permissions on a file called `test.txt` so that the owner has Read, Write, and Execute permissions, while all others only have Read: `chmod 744 test.txt`

## 14.

The following is the matching of endpoint security terms and their description. On the real exam you may be asked to drag the term onto the matching description.

![Image](f0326-01.jpg)

## 15.

The following is the order of environments that a new application should be tested in. Again, on the real exam you may be asked to drag the terms into the boxes to represent the correct order to verify code.

![Image](f0326-02.jpg)

## Chapter 8

## Securing the Network Infrastructure

### CERTIFICATION OBJECTIVES

[8.01 Understanding Firewalls](#ch08.xhtml#ch8obj01)
