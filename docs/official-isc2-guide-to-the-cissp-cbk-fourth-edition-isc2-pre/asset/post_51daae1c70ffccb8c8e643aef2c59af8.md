
- **Flawfinder** – Scans C and C++
- **RIPS** – RIPS is a static source code analyzer for vulnerabilities in PHP Web applications.
- **Brakeman** – Brakeman is an open source vulnerability scanner specifically designed for Ruby on Rails applications.
- **Codesake Dawn** – Codesake Dawn is an open source security source code analyzer designed for Sinatra, Padrino, and Ruby on Rails applications. It can work also for non-Web applications written in Ruby programming language.
- **VCG** – Scans C/C++, Java, C# and PL/SQL for security issues and for comments that may indicate defective code. The config files can be used to carry out additional checks for banned functions or functions that commonly cause security issues.

Commercial tools of this type:
- IBM Security AppScan Source Edition (formerly Ounce)
- Insight (KlocWork)
- Parasoft Test
- Seeker: Seeker performs code security without actually doing static analysis. Seeker does Interactive Application Security Testing (IAST), correlating runtime code and data analysis with simulated attacks. It provides code level results without actually relying on static analysis.
- Source Patrol (Pentest)
- Static Source Code Analysis with CodeSecure (Armorize Technologies)
- Static Code Analysis (Checkmarx)
- Security Advisor (Coverity)
- Veracode

## Malicious Software (Malware)

Malware is a term created to address the need to discuss software or programs that are intentionally designed to include functions for penetrating a system, breaking security policies, or carrying malicious or damaging payloads. Because this type of software has started to develop a bewildering variety of forms – such as backdoors, data diddlers, DDoS, hoax warnings, logic bombs, pranks, RATs, Trojans, viruses, worms, zombies, etc. – the term malware has come to be used for the collective class of malicious software. However, the term is often used very loosely simply as a synonym for virus in the same way that virus is often used simply as a description of any type of computer problem.

Viruses are the largest class of malware, in terms of both numbers of known entities and impact in the current computing environment. Viruses will therefore be given primary emphasis in this discussion, but they will not be the only malware type examined.

Programming bugs or errors are generally not included in the definition of malware, although it is sometimes difficult to make a hard and fast distinction between malware and bugs. For example, if a programmer left a buffer overflow in a system and it creates a loophole that can be used as a backdoor or a maintenance hook, did he do it deliberately? The answer to this question is not easily discerned, and the security professional would have to guess as to the intentions of the programmer, without necessarily knowing for sure what the intent of the programmer truly was.

In addition, it should be noted that malware is not just a collection of utilities for the attacker. Once launched, malware can continue an attack without reference to the author or user and in some cases will expand the attack to other systems. There is a qualitative difference between malware and the attack tools, kits, or scripts that have to operate under an attacker’s control, and which are not considered to fall within the definition of malware. There are gray areas here as well because RATs and DDoS zombies provide unattended access to systems, but they need to be commanded to deliver a payload.

Malware can attack and destroy system integrity in a number of ways. Viruses are often defined in terms of their ability to attach to programs (or to objects considered to be programmable) and so must, in some way, compromise the integrity of applications. Many viruses or other forms of malware contain payloads (such as data diddlers) that may either erase data files or interfere with application data over time in such a way that data integrity is compromised and data may become completely useless.

When considering malware, one should be aware of an additional type of attack on integrity. As with attacks where the intruder takes control of your system and uses it to explore or assail further systems, to hide his own identity, malware (viruses and DDoS zombies in particular) are designed to use your system as a platform to continue further assaults, even without the intervention of the original author or attacker. This can create problems within domains and intranets where equivalent systems “trust” each other, and it can also create “badwill” when organizations doing business with each other find out one is sending viruses to the other.

As noted, malware can compromise programs and data to the point where they are no longer available. In addition, malware generally uses the resources of the system it has attacked and can, in extreme cases, exhaust CPU cycles, available processes (process numbers, tables, etc.), memory, communications links and bandwidth, open ports, disk space, mail queues, and so forth. Sometimes this can be a direct DoS attack, and sometimes it is a side effect of the activity of the malware. Malware such as backdoors and RATs are intended to make intrusion and penetration easier. Viruses such as Goner, Klez, and SirCam send data files from your system to others (in these particular cases, seemingly as a side effect of the process of reproduction and spread). Malware can be written to do directed searches and send confidential data to specific parties and can also be used to open covert channels of other types.

The fact that you are infected with viruses, or compromised by other types of malware, can become quite evident to others. This compromises confidentiality by providing indirect evidence of your level of security, and it may also create public relations problems. It has long been known that the number of variants of viruses or other forms of malware is directly connected to the number of instances of a given platform. The success of a given piece of malware is also related to the relative proportion of a given platform in the overall computing environment.

The modern computing environment is one of consistency. The Intel platform has achieved dominance in hardware, and Microsoft has a near monopoly on the desktop. In addition, compatible application software (and the addition of functional programming capabilities in those applications) can mean that malware from one hardware and operating system environment can work perfectly well in another. The functionality added to application macro and script languages has given them the capability to either directly address computer hardware and resources or easily call upon utilities or processes that have such access. This means that objects previously considered to be data, and therefore immune to malicious programming, must now be checked for malicious functions or payloads.

In addition, these languages are very simple to learn and use, and the various instances of malware carry their own source codes, in plaintext and sometimes commented, making it simple for individuals wanting to learn how to craft an attack to gather templates and examples of how to do so, without even knowing how the technology actually works. This expands the range of authors of such software enormously.

## Malware Types

Viruses are not the only form of malicious software. Other forms include worms, Trojans, zombies, logic bombs, and hoaxes. Each of these has its own characteristics. Some forms of malware combine characteristics of more than one class, and it can be difficult to draw hard and fast distinctions with regard to individual examples or entities, but it can be important to keep the specific attributes in mind. Viruses and Trojans are being used to spread and plant Remote Access Trojans (RATs), and RATs are being used to install zombies. In some cases, hoax virus warnings are being used to spread viruses. Virus and Trojan payloads may contain logic bombs and data diddlers.

## Viruses

A computer virus is a program written with functions and intent to copy and disperse itself without the knowledge and cooperation of the owner or user of the computer. A final definition has not yet been agreed upon by all researchers. A common definition is "a program that modifies other programs to contain a possibly altered version of itself." This definition is generally attributed to Fred Cohen from his seminal research in the mid-1980s, although Dr. Cohen’s actual definition is in mathematical form. The term computer virus was first defined by Dr. Cohen in his graduate thesis in 1984.23 Cohen credits a suggestion from his advisor, Leonard Adleman (of RSA fame), for the use of the term.

Cohen’s definition is specific to programs that attach themselves to other programs as their vector of infection. However, common usage now holds viruses to consist of a set of coded instructions that are designed to attach to an object capable of containing the material, without knowledgeable user intervention. This object may be an email message, program file, document, thumb drive, CD-ROM, short message system (SMS) message on cellular telephones, or any similar information medium.

A virus is defined by its ability to reproduce and spread but to do so with the aid of the user in some form. Just as a cold or flu spreads after one person gets sick and interacts with others, leaving behind the virus, the computer virus spreads after a sick person helps by exposing uninfected people to it.

A worm, which is sometimes seen as a specialized type of virus, is currently distinguished from a virus because a virus generally requires an action on the part of the user to trigger or aid reproduction and spread, while a worm spreads on its own. The action on the part of the user is generally a common function, and the user generally does not realize the danger of the action or the fact that he or she is assisting the virus. The only requirement that defines a program as a virus is that it reproduces. There is no necessity that the virus carries a payload, although a number of viruses do. In many cases (in most cases of successful viruses), the payload is limited to some kind of message.
