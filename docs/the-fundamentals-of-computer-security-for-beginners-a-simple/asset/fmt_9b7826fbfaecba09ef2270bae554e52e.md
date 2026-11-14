
# MALWARE TYPES

## 1) Macro
They delete the original data of the file and replace it. These are viruses that spread through the Office package. Every time a command is executed, the virus spreads. Office blocks Macros from unsafe files.

## 2) Worm
Worms spread using a vulnerability. This type of malware is independent and does not need other files to propagate. The main means of dissemination is e-mail. Worms often act as a vehicle for the automatic installation of other malware, such as backdoors and keyloggers, on most machines.

## 3) RootKit
The RootKit is usually a collection of malicious software used to gain access to a computer. This malware works as close to the kernel space as possible. The name itself indicates the characteristic of this malware, i.e. to be able to obtain an escalation privilege that allows to reach the root (system administrator) permissions.

## 4) Backdoor and Bot
Backdoors allow you to control a computer remotely. The infected computer is called Bot. Using bots, the hacker can conceal his identity and create a network of bots only for future attacks. This network, which is essentially made up of infected computers, is called BotNet. Bots, on the other hand, are malicious processes that, after infecting the victim, create a connection with the main servers that act as a command centre for the infected devices connected to this network.

## 5) KeyLogger
The keyLogger simply records everything you type in input. Virtually everything the victim types on the keyboard (e.g. username and password) is recorded by the malware.

## 6) Ransomware
This type of malware restricts access to the device and makes the system unusable. Usually, after locking the system, the hacker requests a ransom to hand over the unlock key, otherwise he will delete all the content.

## 7) Logic Bomb
The logic bomb has the special feature of only going into operation when a particular condition occurs. Basically it has the same effects as other viruses but it changes the way it goes into action.

## 8) Spyware and Adware
Adware simply displays unwanted advertising and presents itself through pop-ups and windows. Spyware, on the other hand, spies pc in different ways stealing sensitive data. In general, this malware records the user's browsing habits and redirects him to malicious sites and then steals sensitive information from them.

## 9) Trojans
The Trojan is not really malware since it is a "trick" used to spread malware. It looks like normal software but actually opens the door to other malware. One type of trojan is the RAT (Remote Access Trojan) which allows you to control a system with administrator privileges.

## 10) Hoaxes
They're nothing but computer buffaloes. These malware are intended to spread panic by, for example, providing fake communications about the spread of a virus.

# INFECTION TECHNIQUES
Each malware uses a technique that allows it to infect the victim. The techniques of infection are manifold:

## 1) Boot Sector
This technique allows malware to infect the boot sector of the `HDD` (hard disk drive). Malware in this way presents itself at every system boot. This technique can render the system unusable.

## 2) Multi-partite viruses
This technique allows you to infect executable files and disk boot. In order to completely eliminate malware, every single infected component must be removed.

## 3) Companion
This technique creates a file with the same name as the original one and changes its extension. This weakness was present on `DOS`. For example: `name.exe` (original file) and `name.com` (virus). The system would run the infected file because in alphabetical order `.com` comes before `.exe`.

## 4) Polymorphism
This technique allows malware to change form (code) every time the malware is executed in a way that is difficult for antivirus software to recognize.

# CONCEALMENT TECHNIQUES
In addition to infection techniques there are also concealment techniques that allow malware to hide and not be deleted:

## 1) Retrovirus
This technique allows you to attack the antivirus. The purpose is to destroy or damage the antivirus database by blocking updates and trying to deactivate it.

## 2) Stealth
Malware using this technique tries to be invisible to the antivirus. When a scan request is made, the malware provides a "clean" copy of the infected file.

## 3) Armored
These malware are called "armor-piercing" and are intended to make the code unreadable for the antivirus by sending misleading information (e.g. entering unnecessary instructions).

# THE ANTIVIRUS
Once you have analyzed the malware and the techniques used by them, you should also know how to defend yourself:

1. Always have anti-malware software.
2. It is important to update software and definitions.
3. Perform periodic scans.
4. The operating system must be updated.
5. Do not use pirated software.
6. It is important to be careful about the sites you visit and the e-mail attachments.

The antivirus is a control software and consists of a database of definitions (where the characteristics of known viruses are listed). The heuristic techniques allow the detection of a virus even if a program is not exactly equal to the definitions in the database; in fact, it is enough that there are some features in common with known viruses that the program in question is reported to the user.

## Dangerous Extensions to Block

### 1) Executable Extensions
`.bat` `.com` `.exe` — Which are executable.

### 2) JavaScript
`.js` — Javascript.

### 3) Winhelp
`.hlp` — Winhelp, program guide.

### 4) Program Information File
`.pif` — Instructions for the operating system.

### 5) Screen Saver
`.scr` — Screen saver.

### 6) Visual Basic Script
`.vbs` — Visual basic and macro in Office.

# VULNERABILITIES
Security is put at risk not only by malware but also by vulnerabilities. Vulnerability is nothing more than a weakness or defect in a system where security measures are absent, reduced, compromised or violated. If exploited, it can lead to unexpected behaviour on the part of the system and can easily be used by criminals to compromise system security.

Software vulnerabilities can result from:

1. **Bugs** — Errors in the software code.
2. **System complexity** — Very large systems can have weak points due to difficult management.
3. **Lack of input control** — Many programs assume that the input entered by the user is safe.
4. **Connectivity** — Systems connected to others are exposed to the danger of unauthorised access.

# ATTACKS
Attacks can be classified according to their target. There are access and abort attacks. Access attacks refer to interception, modification and falsification, while interrupt attacks compromise data availability. There are many types of attacks:

## 1) Eavesdropping
Allows you to listen and read the data silently. In the passive version it allows the hacker to read only the data while in the active version of the attack it is possible to intrude into a conversation by sending bogus data.

### A) Modification attack
Edit and delete data.

### B) Repudiation attack
Steal access information and take the user's place to make attacks.

## 2) Hijacking
This attack refers to hijacking, i.e. the attacker takes over the session. There are different types of hijacking:

### A) Clickjacking
Edit web page elements trying to redirect the user's click to a different object.

### B) Session hijacking
Traffic entry on an already authenticated session. The attacker tries to replace one of the two interlocutors.

### C) Hijacking URL
Register domain names similar to other known ones and let the victim navigate on a malicious site.

### D) Domain hijacking
Changing domain registration information by associating the domain name to a malicious site.

### E) Session Theft
It consists of stealing the cookie victim and using it for identity theft.

### F) Man in the Middle
Interception and modification of data between client and server, tapping on cables, `arp spoofing`, `dns spoofing`.

## 3) Sniffing
