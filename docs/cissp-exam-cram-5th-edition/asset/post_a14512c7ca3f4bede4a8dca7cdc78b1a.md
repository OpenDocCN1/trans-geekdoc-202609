
A Common Criteria certification contains either a protection profile (PP) or a security target (ST).

Assurance requirements define how well a product is built. Assurance requirements inspire confidence in the product and show the correctness of its implementation.

**ExamAlert**

Common Criteria’s seven levels of assurance and two security requirements are required knowledge for the CISSP exam.

## System Validation

No system or architecture will ever be completely secure; there will always be a certain level of risk. Security professionals must understand this risk and be comfortable with it, mitigate it, or offset it through a third party. All the documentation and guidelines already discussed dealt with ways to measure and assess risk. These can be a big help in ensuring that the implemented systems meet your requirements. However, before you begin to use the systems, you must complete the two additional steps of certification and accreditation.

U.S. federal agencies are required by law to have their IT systems and infrastructures certified and accredited. Although you shouldn’t expect to see in-depth certification and accreditation questions on the CISSP exam, it is worth knowing if you plan to interact with any agencies that require their use. These methodologies look at much more than a standard penetration test; they are more like an audit. They must validate that the systems are implemented, configured, and operating as expected and meet all security policies and procedures.

## Certification and Accreditation

*Certification* is the process of validating that implemented systems are configured and operating as expected. It also validates that the systems are connected to and communicate with other systems in a secure and controlled manner and that they handle data in a secure and approved manner. The certification process is a technical evaluation of the system that can be carried out by independent security teams or by the existing staff. Its goal is to uncover any vulnerabilities or weaknesses in the implementation.

The results of the certification process are reported to the organization’s management for mediation and approval. If management agrees with the findings of the certification, the report is formally approved. The formal approval of the certification is the *accreditation process*. Management usually issues accreditation as a formal, written approval that the certified system is approved for use as specified in the certification documentation. If changes are made to the system or in the environment in which the system is used, a recertification and accreditation process must be repeated. The entire process is periodically repeated at intervals, depending on the industry and the regulations the organization must comply with. For example, Section 404 of Sarbanes-Oxley requires an annual evaluation of internal systems that deal with financial controls and reporting systems.

> **ExamAlert**
> 
> For the CISSP exam, you might want to remember that certification is seen as the technical aspect of validation, whereas accreditation is management’s approval.

> **Note**
> 
> Nothing lasts forever, including certification. The certification process should be repeated when systems change, when items are modified, or on a periodic basis.

## Vulnerabilities of Security Architectures

Like most other chapters of this book, this one also reviews potential threats and vulnerabilities. Any time a security professional makes the case for stronger security, there will be those who ask why funds should be spent that way. It's important to point out not only the benefits of good security but also the potential risks of not implementing good practices and procedures.

We live in a world of risk. As security professionals, we need to be aware of the threats to security and understand how the various protection mechanisms discussed throughout this chapter can be used to raise the level of security.

### Buffer Overflows

Buffer overflows occur because of poor coding techniques. A buffer is a temporary storage area that has been coded to hold a certain amount of data. If additional data is fed to the buffer, it can spill over or overflow to adjacent buffers. This can corrupt those buffers and cause the application to crash or possibly allow an attacker to execute his own code that he has loaded onto the stack. Ideally, programs should be written with error checking—such as to check that you cannot type 32 characters into a 24-character buffer; however, this type of error checking does not always occur. Error checking is really nothing more than making sure that buffers receive the correct type and amount of information required. Here is an example of a buffer overflow:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int abc()
{
char buffer[8];
strcpy(buffer, "AAAAAAAAAA");
return 0;
}
```

OS vendors are also working to make buffer overflow attacks harder by using techniques such as data execution prevention (DEP) and address space layout randomization (ASLR). DEP marks some areas of memory as either executable or non-executable. DEP can help avert some attacks by preventing the writing of malicious commands designed to be stored in memory. ASLR randomly rearranges address space positions of data. Think of the shell game, where a small ball is placed under one of three shells and is then moved around. To win the game, you must guess which shell the ball is under. Most modern operating systems, such as Android, Windows, and FreeBSD, make use of ASLR.

Other defenses for buffer overflows include code reviews, using safe programming languages, and applying patches and updates in a timely manner. Finally, because all data should be suspect by default, data being input, processed, or output should be checked to make sure it matches the correct parameters.

### Backdoors

Backdoors are potential threats to the security of systems and software. Programmers use backdoors, which are also sometimes referred to as maintenance hooks, during development to allow easy access to a piece of software. Often these backdoors are undocumented. A backdoor can be used when software is developed in sections and developers want a means of accessing certain parts of the program without having to run through all the code. If backdoors are not removed before the release of the software, they can allow an attacker to bypass security mechanisms and access the program.

### State Attacks

A state attack is a form of attack that typically targets timing. The objective is to exploit the delay between the time of check (TOC) and the time of use (TOU). These attacks are sometimes called asynchronous attacks or race conditions because the attacker races to make a change to the object after it has been checked but before the system uses it.

For example, if a program creates a data file to hold the amount a customer owes, and the attacker can race to replace this value before the program reads it, he can successfully manipulate the program. In reality, it can be difficult to exploit a race condition because a hacker might have to attempt to exploit the race condition many times before succeeding.

### Covert Channels

Covert channels provide a means of moving information in a manner that was not intended. Covert channels are a favorite of attackers because they know that you cannot deny what you must permit. The term was originally used in TCSEC documentation to refer to ways of transferring information from a higher classification to a lower classification. Covert channel attacks can be broadly separated into two types:

- **Covert timing channel attacks:** Timing attacks are difficult to detect. They function by altering a component or by modifying resource timing.

- **Covert storage channel attacks:** These attacks use one process to write data to a storage area and another process to read the data.

Here is an example of how covert channel attacks happen in real life. Your organization has decided to allow ping (Internet Control Message Protocol [ICMP]) traffic into and out of your network. Based on this knowledge, an attacker has planted the Loki program on your network. Loki uses the payload portion of a ping packet to move data into and out of your network. Therefore, the network administrator sees nothing but normal ping traffic and is not alerted, even though the attacker is busy stealing company secrets. Sadly, many programs can perform this type of attack.

> **ExamAlert**
> 
> The CISSP exam expects you to understand the two types of covert channel attacks.

### Incremental Attacks

The goal of an incremental attack is to make changes slowly over time. By making small changes over long periods, an attacker hopes to remain undetected. Two primary incremental attacks are **data diddling**, which is possible if the attacker has access to the system and can make small incremental changes to data or files, and **salami attack**, which is similar to data diddling but involves making small changes to financial accounts or records, often referred to as “cooking the books.”

### Emanations
