
### Clear Desk and Clear Screen
User’s desks should be kept clear of any physical papers or storage media that may contain sensitive or classified information. Certain types of information have legal storage requirements that must be followed. All sensitive documents and storage media must be locked up. Sensitive information should be removed from printers immediately after printing. Computers, terminals, and digital devices that may contain sensitive information should be logged off, screen protected, or secured when not in use.

### Test Your Understanding

4.  
   a. What is siting?  
   b. Distinguish between UPSs and electrical generators.  
   c. If wiring cannot be run through walls, what should be done to protect the wiring?  
   d. What should be done to protect laptops taken off-premises?  
   e. What controls should be applied to off-site equipment maintenance?  
   f. What controls should be applied to equipment disposal or reuse?  
   g. What controls should be placed over employees taking equipment off-site?  
   h. What controls should be applied to sensitive information sitting on desks or shown on screens when users are away from their desks?

### Other Physical Security Issues

Although ISO/IEC 27002 Security Clause 11 is very comprehensive, there are several areas in which additional concern is needed.

### Terrorism

Due to increasing threats from terrorism, terrorist attacks must be considered in all matters of physical security. For instance, new buildings should be set back from streets and protected with rolling hill landscaping. In appropriate situations, guards may be armed. Bulletproof doors may also be needed to guard sensitive areas.

### Piggybacking

Enforcing entrance controls is very difficult because of a social engineering trick called **piggybacking**. (It is also called **tailgating**.) When an authorized user opens a door with an access device, an intruder may follow the authorized user through. (Often, the intruder will approach a door with his or her arms loaded with papers and reach ineffectually in his or her pocket to get a key.)

To not allow someone to piggyback after you seems very rude to most people, so the prohibition of piggybacking is difficult to enforce. However, unless piggybacking is eliminated, physical access security is nearly impossible. Although eliminating piggybacking is difficult, it is possible with effort. One of the authors spent an hour in the entrance hall of one large computer firm and watched employees enter. Not one piggybacked on another. It simply was not done or tolerated by other employees.

### Monitoring Equipment

**ISO/IEC 27002** frequently refers to monitoring. Typically, this involves remote sensors that are connected by wire to a central security center. Usually, this security center is staffed by uniformed guards. If a sensor is activated, an alarm goes off in the security center. If a wire to a sensor is disabled, this should also set off an alarm.

Sometimes monitoring involves **closed-circuit television (CCTV)**, which allows the security staff to see an area visually. CCTV systems must be selected very carefully. The firm should not use a system that uses videotape because videotape quality degrades rapidly with tape reuse.

In turn, digital CCTV systems, which store information on hard drives and digital backup tapes, vary widely in **image resolution**, which is the number of picture elements on the screen. Most digital security cameras have low resolution, making subject identification questionable. High-resolution cameras exist, but they are somewhat expensive. In addition, high-resolution cameras require more storage capacity for recordings than low-resolution cameras.

To reduce storage burdens, many systems only record the video feed if there is motion. Some go beyond simple **motion detection** and only record the video feed when there is a *specific type* of motion, say when an object larger than a bird moves across the screen from left to right.

### Dumpsters

A final common building-related threat is **dumpster diving**, in which an attacker goes through a firm’s dumpsters looking for documents, backup tapes, floppy disks, and other information-carrying media. Building dumpsters should be located in a secure and lighted area, preferably under CCTV surveillance. This area must be on the *company premises* because once dumpsters are moved beyond the company premises, their contents usually are considered to be abandoned and have no legal protection.

### Desktop PC Security

To reduce the danger of theft, individual desktop PCs in ordinary office areas can be locked onto their desks with a cable—provided that there is something on the desk to wrap the cable around. In addition, each PC should have a login screen that requires a complex password and a screen saver so that an intruder cannot simply walk up to it and use it.

- **Terrorism**
  - Building setback from street
  - Armed guards
  - Bullet-proof glass
- **Piggybacking**
  - Following an authorized user through a door
  - Also called tailgating
  - Psychologically difficult to prevent
  - But can and should be done
- **Monitoring Equipment**
  - CCTV
  - Tapes wear out
  - High-resolution cameras are expensive and consume a great deal of disk space
  - Low-resolution cameras may be insufficient for recognition needs
- **Trash Bins**
  - Protect trash that may contain sensitive information
  - Maintain trash inside the corporate premises and monitor until removed
- **Desktop PC Security**
  - Locks that connect the computer to an immovable object
  - Login screens and screen saver with strong passwords

*Figure 5-4 Other Physical Security Issues (Study Figure)*

### Notebook Security

Security for notebooks that are taken off-site is a complex topic. We will discuss it in a later chapter.

### Test Your Understanding

5.  
   a. What special controls are required by terrorism threats?  
   b. Why is it necessary to prevent piggybacking?  
   c. What advice would you give a company about CCTV?  
   d. What is dumpster diving?  
   e. How should dumpsters be protected?  
   f. What can be done to reduce the dangers of desktop PC theft and unauthorized use?

## 5.3 Passwords

5.3 Explain reusable passwords.

There are many technologies for access control. Undoubtedly, the most common is the password. To log onto a server, for instance, you normally need to know your account name (which is not secret) and its secret password. This is called a **reusable password** because it is used for weeks or months at a time. By contrast, a **one-time password** is used only once.

### Password-Cracking Programs

Over a network, an attacker could try to log in repeatedly with different possible account names and passwords. However, such an attacker will almost always be locked out after a few attempts. Lockouts might frustrate users who cannot get into their locked-out accounts, but lockouts will not give attackers access to their resources.

If the attacker can physically enter a site, however, he or she has a much more effective way to crack passwords—installing a password-cracking program on a server. These programs try thousands of possible account name/password combinations per second until one works.

Another way to exploit a machine with physical access is to copy the password file and crack it later on another machine. This is less obtrusive than taking the time to run a **password-cracking program** on a server during an intrusion.

### Test Your Understanding

6.  
   a. What are reusable passwords?  
   b. Why is password cracking over a network difficult to do?  
   c. In what two ways can password-cracking programs be used?  
   d. Which is safer for the cracker? Why?

### Password Policies

Given the large number of threats that face reusable passwords, companies need to have strong password policies. Good password policies help stop attackers from taking advantage of the inherent weaknesses associated with using reusable passwords.
