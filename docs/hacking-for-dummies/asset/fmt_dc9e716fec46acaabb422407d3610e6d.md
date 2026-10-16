
Are locking laptop bags required? What about power-on passwords? Encryption can solve a lot of physical security-related weaknesses.

How easily can someone connect to a wireless access point signal or the access point itself to join the network? Rogue access points are also important to consider. I cover wireless networks in detail in [Chapter 10](#c10.xhtml).

Are network firewalls, routers, switches, and hubs (basically, anything with an Ethernet or console connection) easily accessible, enabling an attacker to plug into the network easily?

Are all cables patched through on the patch panel in the wiring closet so that all network drops are live (as in the case of the unmonitored lobby area I mention earlier in this chapter)?

![warning](images/warning.png)This setup is common but a bad idea because it allows anyone to plug into the network anywhere and gain access, as well as to spread malware.

#### Countermeasures

Network and computer security countermeasures are simple to implement yet difficult to enforce because they involve people’s everyday actions. Here’s a rundown of these countermeasures:

- Make your users aware of what to look out for so that you have extra sets of eyes and ears helping you.
- Require users to lock their screens — which takes only a few clicks or keystrokes — when they leave their computers. Better yet, set a Group Policy Object in Active Directory or local computer policy to force timeouts.
- Ensure that strong passwords are used. (I cover this topic in [Chapter 8](#c08.xhtml).)
- Require laptop users to lock their systems to their desks with a locking cable — especially important for remote workers and travelers, as well as employees of large companies and/or those who work in locations with a lot of foot traffic.
- Require all laptops to use full disk encryption technologies. One example is BitLocker in Windows, ideally combined with the central management software called Microsoft BitLocker Administration and Monitoring, which you can find at [`https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/mbam-v25/`](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/mbam-v25/). Another option is WinMagic SecureDoc Full Disk Encryption ([`https://www.winmagic.com/products/full-disk-encryption-for-windows`](https://www.winmagic.com/products/full-disk-encryption-for-windows)). FileVault built into the macOS is a good option for that growing group of computers. It’s also important to consider encryption for removable media since sensitive information inevitable ends up there.
- Keep server rooms and wiring closets locked, and monitor those areas for any wrongdoing.
- Keep a current inventory of hardware and software within the organization so that it’s easy to determine when extra equipment appears or goes missing — especially important in computer rooms.
- Replace traditional door locks and keys with more modern access control systems.
- Properly secure computer media during storage and transport.
- Scan for rogue wireless access points, and shut them down.
- Use cable traps and locks that prevent intruders from unplugging network cables from patch panels or computers and using those connections for their own computers.
- Use a bulk eraser on magnetic media and shred them before they’re discarded.

Chapter 8

# Passwords

IN THIS CHAPTER

![check](images/check.png)`Identifying password vulnerabilities`

![check](images/check.png)`Examining password-hacking tools and techniques`

![check](images/check.png)`Hacking operating system passwords`

![check](images/check.png)`Hacking password-protected files`

![check](images/check.png)`Protecting your systems from password hacking`

Password hacking is one of the easiest and most common ways that attackers obtain unauthorized network, computer, or application access. You often hear about it in the headlines, and study after study, such as the `Verizon Data Breach Investigations Report`, reaffirms that weak passwords are at the root of many security problems. I have trouble wrapping my head around the fact that I’m `still` talking about (and businesses are suffering from) weak passwords, but that fact is a reality. As an information security testing professional, you can certainly do your part to minimize the risks.

Although strong passwords — ideally, longer, stronger passphrases, which are difficult to crack (or guess) — are easy to create and maintain, network administrators and users often neglect this aspect of password management. Therefore, passwords are among the weakest links in the information security chain. Passwords rely on secrecy. After a password is compromised, its original owner isn’t the only person who can access the system with it. That’s when accountability goes out the window and bad things start happening.

External attackers and malicious insiders have many ways to obtain passwords. They can glean passwords simply by asking for them or by looking over the shoulders of users *(shoulder surfing)* while they type their passwords. Hackers can also obtain passwords from local computers by using password-cracking software. To obtain passwords from across a network, attackers can use remote cracking utilities, keyloggers, or network analyzers.

This chapter demonstrates how easily the bad guys can gather password information from your network and computer systems. I outline common password vulnerabilities and describe countermeasures that help prevent these vulnerabilities from being exploited on your systems. If you perform the tests and implement the countermeasures outlined in this chapter, you’ll be well on your way to securing your systems’ passwords.

## Understanding Password Vulnerabilities

When you balance the cost of security and the value of the protected information, the combination of a user id and a secret password is usually adequate. Passwords create a false sense of security, however, as the bad guys know, and they attempt to crack passwords as a step toward breaking into computer systems.

One big problem with relying solely on passwords for security is that more than one person can know them. Sometimes, multiple people knowing a password is intentional; often, it’s not. The tough part is that there’s no way of knowing who, besides the password’s owner, knows a password.

![remember](images/remember.png)Knowing a password doesn’t make someone an authorized user.

Here are the two general types of password vulnerabilities:

- **Organizational or user vulnerabilities:** Include lack of password policies that are enforced within the organization and lack of security awareness on the part of users
- **Technical vulnerabilities:** Include weak encryption methods and unsecure storage of passwords on computer systems

I explore these classifications in more detail in the following sections.

Before computer networks and the Internet, the user’s physical environment was an additional layer of password security that worked pretty well. Now that most computers have network connectivity, that protection is gone. [Chapter 7](#c07.xhtml) provides details on managing physical security in this age of networked computers and mobile devices.

### Organizational password vulnerabilities
