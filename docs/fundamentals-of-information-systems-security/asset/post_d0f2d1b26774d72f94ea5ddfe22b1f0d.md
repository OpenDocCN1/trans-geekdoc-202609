
Malware developers write and compile many of these viruses using high-level languages. The C and C++ languages are common choices because of their ability to provide the power and flexibility viruses need to be successful. In contrast, they often use assembly language to write boot record infectors. Although the coding of file infector viruses can be quite complex, the architecture of most executable programs is relatively straightforward.

Viruses of this type attach themselves to the original program file. They control the execution of that file until it can replicate and infect other files and possibly deliver a payload.

One type of file infector, a companion virus, is really a separate program file that does not attach itself to the original host program. Instead it creates a new program with a matching filename but with an extension that executes earlier than the original. For example, Windows executes .com files before it executes .exe files. It creates this file in the same directory path as the real program. When the user runs the program, the operating system calls the malware instead of the legitimate program. After the virus finishes its work, it simply executes the command to start the original program. FIGURE 11-3 shows how a file infector virus works.

## Macro (Data File) Infectors

**Macro viruses** became a problem when software vendors added recording capabilities to popular office applications. Users use macro-recording capabilities to record their actions in a program. The application in which the actions are recorded stores these instructions with the data file. The user can then execute the actions automatically when he or she opens the file or presses a predefined keystroke sequence. The original purpose of macros was to automate repetitive processes. Users liked the feature because it made applications more convenient and efficient. However, these macros opened the door for malicious code to carry out its own instructions.

Macro viruses infect these document files and insert their own commands. When users share the infected document with other users, the malware spreads and replicates. The connected nature of most office applications makes it easy for infected documents to spread to other computers and users. Macros can move easily between platforms, and they are quite simple to construct. For this reason, macro viruses are extremely popular among hackers.

The electronic mail bomb is a form of malicious macro attack. This type of attack typically involves an email attachment that contains macros designed to inflict maximum damage.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_381_0.png)

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_382_0.png)

Attackers can send the document attachment through an anonymous remailer to reach its targets with great precision. Someone who receives the email bomb need only open the attachment to launch the macro virus. In some cases, simply previewing the email message activates the email bomb. FIGURE 11-4 shows how a macro virus works.

## Other Virus Classifications

Viruses can use any of a number of techniques to propagate and avoid detection by antivirus software. Most single computer viruses work by copying exact replicas of themselves to each file, boot sector, or document they infect. The virus accomplishes subsequent infections in the same manner, making exact duplicates byte for byte. This predictable action produces a signature pattern. Many antivirus and anti-malware programs look for this signature to detect malware. Some viruses, such as the following, behave differently:

- Polymorphic viruses—Polymorphic viruses include a separate encryption engine that stores the virus body in encrypted format while duplicating the main body of the virus. The virus exposes only the decryption routine for possible detection. It embeds the control portion of the virus in the decryption routine, which seizes control of the target system and decrypts the main body of the virus so that it can execute. True polymorphic viruses use an additional mutation engine to vary the decryption process for each iteration. This makes even this portion of the code more difficult to identify. FIGURE 11-5 shows how a polymorphic virus infects a computer.

- Stealth viruses—Stealth viruses, also called armored viruses, use a number of techniques to conceal themselves from users and from detection software. By installing a low-level system service function, they can intercept any system request and alter the service output to conceal their presence. Stealth viruses can have size stealth, read stealth, or both. FIGURE 11-6 shows how a stealth/armored virus works.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_382_1.png)

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_383_0.png)

**FYI**

Size stealth hides the fact that an infected file is bigger than it used to be. The virus intercepts system requests for file information and subtracts its own size from the reply before passing it back to the requesting process. Read stealth hides the fact that the virus moved the boot sector code. The virus intercepts read/write requests for the normal boot sector, which the virus has relocated and replaced with the viral code. The virus redirects the request to the new hidden location of the original boot sector code.

- **Slow viruses**—Slow viruses counter the ability of antivirus programs to detect changes in infected files. This class of virus resides in the computer's memory, where antivirus software cannot detect it. It waits for certain tasks, like copying or moving files, to execute. As the operating system reads the file into memory, the virus alters data read from the input file before writing to the output file, making it much harder to detect. FIGURE 11-7 shows how a slow virus works.

- **Retro viruses**—Retro viruses attack countermeasures such as antivirus signature files or integrity databases. A retro virus searches for these data files and deletes or alters them, thereby crippling the antivirus software’s ability to function. Other viruses, especially boot viruses (which gain control of the target system at startup), modify Windows Registry keys and other operating system key startup files to disable AV, firewall, and intrusion detection system (IDS) software if found. FIGURE 11-8 shows how a retro virus works.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_383_1.png)

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_384_0.png)

- Cross-platform viruses—Cross-platform viruses are less prevalent but can still be potent threats. There have been a number of documented viruses that target multiple operating systems (Apple Macintosh HyperCard viruses, for instance). If those platforms also run Windows emulation software, they become as susceptible to Windows viruses as a native Windows computer:

- Multipartite viruses—As previously mentioned, multipartite viruses are hybrid viruses that exhibit multiple behaviors. There are two main types of multipartite virus: Master Boot Record/boot sector viruses and file infecting viruses. Such viruses may exist as file infectors within an application. Upon execution of the infected application, the virus might spawn a Master Boot Record infection, which then infects other files when you restart the system. FIGURE 11-9 shows how a multipartite virus works.

Some multipartite viruses, such as the One Half virus, isolated in 1994, may also exhibit both stealth and polymorphic characteristics.

## Rootkits

A rootkit is a type of malware that modifies or replaces one or more existing programs to hide the fact that a computer has been compromised. It is common for rootkits to modify parts of the operating system to conceal traces of their presence. Rootkits can exist at any level, from the boot instructions of a computer up to the applications that run in the operating system.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_384_1.png)

Once installed, rootkits provide attackers with access to compromised computers and easy access to launching additional attacks. Rootkits are newer than other types of malware and did not appear until around 1990. They can be very difficult to detect and remove since their main purpose is to hide their own existence. But identifying and removing rootkits is crucial to maintaining a secure system.

In 2015, reports began to emerge that described very serious types of rootkits. It was discovered that rootkits could be burned into the firmware of hard disk drives or even into a computer’s Basic Input/Output System (BIOS). These rootkits would survive complete operating system reinstallation and hard drive reformatting. In the case of the BIOS rootkit, even replacing a disk drive with a completely new disk drive would not remove the rootkit. These newer types of rootkits are extremely pervasive and difficult to remove without substantial technical skill. In 2016, several sources reported that the U.S. National Security Agency (NSA) has used hard drive firmware rootkits to enable surveillance on specific targets.

## Ransomware

Another type of malware attempts to generate funds directly from a computer user. This type of malware is also one of the fastest-growing menaces. Ransomware attacks a computer and limits the user’s ability to access the computer’s data. It can limit access by slowing the computer down, denying access for authorized users, or blocking access to specific programs or resources. Many current ransomware programs operate by encrypting important files or even the entire disk and making them inaccessible.

One of the first ransomware programs was CryptoLocker, which was released in 2013. Ransomware programs have become even more sophisticated and dangerous since then. The attacker generally alerts the users to the restrictions and demands a payment to restore full access. The demand for a payment, or ransom, gives this type of malware its name. The attacker promises to decrypt the user’s data or remove any mechanisms that block access once the ransom is paid. Most computer users rely on their computers and the data they store. Few computer users can lose access to their data and other resources without encountering ongoing frustration.

Business users may find ransomware to be far more than a simple annoyance. The inability to access key parts of a business computing system can have the same effect as a DoS attack. A ransomware attack can cost an organization large sums of lost profits in a very short period of time. Attackers that launch ransomware attacks expose themselves to huge risks but also can realize large profits. Ransomware is a growing trend in malware. User reliance on mobile devices makes such devices attractive targets. As computers and other devices become more mobile, they become even more vulnerable to potential ransomware attacks.

## NOTE

So, how can malware simply take control of a computer? Malware can use many different techniques, but two common ones depend on lazy programmers. A buffer overflow is a condition when a program allows more data to be loaded into a variable than it expected. When this happens, the “extra” data can change protected data in memory or even change a program’s instructions. A similar weakness is an integer overflow, an arithmetic operation that results in a number that is too large to be stored in a simple integer variable. In both cases, programmers should handle the errors and alert the user, but many programs behave in unusual ways when overflows occur.

## Spam

**Spam** is one of the most bothersome challenges faced by network administrators. Not only does spam often contain viruses or other
