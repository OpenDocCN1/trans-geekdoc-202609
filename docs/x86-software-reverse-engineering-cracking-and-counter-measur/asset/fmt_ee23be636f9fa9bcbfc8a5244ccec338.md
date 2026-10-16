
The server will verify the expected hash and the activation key. If they validate, it uses an algorithm to produce a decryption key, which it will send back to the application. The loader can then decrypt the application, enabling it to run.

An attacker will not be able to “mimic” your remote server and algorithm without access to the server-side code. The only way to research the software will be to activate it online. The application can have decryption code be resident in memory only. This way, each startup requires server interaction.

The main challenge of this approach is that implementing cryptography and enterprise key management solutions is not trivial. A mistake may allow a cracker to bypass the validation code and generate their own decryption keys. As discussed with packed applications, once it's unpacked in memory, you could take a memory dump of it for future static analysis. However, that memory dump can't easily (or sometimes not at all) be turned into a decrypted application capable of running. The memory dump won't be useful for patching or testing modifications but never discount the value of static analysis.

### Is This a Strong Protection?

Remote authentication provides mixed reviews when compared against the CIA triad:

*   **Confidentiality:** Some (the application will eventually be decrypted in memory, but the binary at rest is restricted)

*   **Integrity:** Yes (the server should be doing some type of integrity checking prior to releasing the response)

*   **Availability:** Possibly negative

One possible attack against a remote server is to set up a fake server. To start, activate the application online and capture all communication between the application and server.

Then, stand up a fake server with appropriate responses. The application's code will be decrypted and can be saved to disk.

This approach does require a single online application to get the decrypted code. However, this allows a full, decrypted binary to be created, making further online authentication unnecessary. But note that this approach can't always work if the application does good due diligence in requiring certain certificates from the server or if the challenge/response from the server is not always the same (i.e., changes with time or date).

## Lab: ProcMon

This lab shows that there is more than one possible way to crack a program. Head back to the book's GitHub page (`https://github.com/DazzleCatDuo/X86-SOFTWARE-REVERSE-ENGINEERING-CRACKING-AND-COUNTER-MEASURES`) and locate the ProcMon lab.Skills.

This lab uses ProcMon and IDA to understand opportunities for alternative cracking solutions. Some key skills being tested include the following:

*   Analyzing program behavior dynamically

*   Identifying indirect approaches to circumventing software defenses

### Takeaways

Watching what a process does from the outside can be quicker/easier than watching it from the inside (that is, debugging is not always the best approach).

There are usually many ways to crack a program; finding the best takes practice.

## Summary

This chapter presented various methods of protecting against software cracking and reversing. Some techniques are generally ineffective, while others can work but also have some downsides.

It's important to remember that almost any defense can be defeated given enough time and effort. The goal is to slow an attacker down and, ideally, make them frustrated enough to give up.

# CHAPTER 15  

Legal

In an “Introducton” the legal implications and considerations of reverse engineering and cracking were explored at a high level. This section provides a more in-depth discussion of relevant U.S. laws and their impacts and interpretations.

## U.S. Laws Affecting Reverse Engineering

Laws regarding copyrights, hacking, etc., vary based on jurisdiction. This section covers some applicable laws in the United States. If you are located elsewhere, check your local laws and restrictions.

### The Digital Millennium Copyright Act

Digital rights management (DRM) is a solution designed to protect intellectual property. DRM solutions can track and control protected content after it reaches the marketplace.

The Digital Millennium Copyright Act (DMCA) was passed by Congress in 1998. It brought the United States into compliance with international copyright agreements.

### Computer Fraud and Abuse Act

The Computer Fraud and Abuse Act (CFAA) was enacted in 1984. It is a federal anti-hacking statute that prohibits unauthorized access to computers and networks.

Lawmakers wrote the law so poorly that creative prosecutors have been abusing it ever since. However, in recent years, efforts have been made to protect security researchers from being prosecuted under it. `Wired.com` said this about the CFAA in a 2014 article:

> *A high profile case involving misuse of the statute occurred in 2008 when three MIT students were barred from giving a presentation at the Def Con hacker conference. The students had found flaws in the electronic ticketing system used by the Massachusetts Bay Transportation Authority that would have allowed anyone to obtain free rides. The MBTA sought and obtained a temporary restraining order to bar the students from speaking about the flaws. In granting the temporary gag order, the judge invoked the CFAA, saying that information the students planned to present would provide others with the means to hack the system. The judge's words implied that simply talking about hacking was the same as actual hacking. The ruling was publicly criticized, however, as an unconstitutional prior restraint of speech, and when the MBTA subsequently sought a court order to make the restraining order permanent, another judge rejected the request, ruling in part that the CFAA does not apply to speech and therefore had no relevance to the case.*

> 

> `www.wired.com/2014/11/hacker-lexicon-computer-fraud-abuse-act`

A second high-profile, and very sad, abuse of the CFAA resulted in a high-profile suicide. This came after a U.S. attorney used CFAA to launch a heavy-handed prosecution against Internet activist Aaron Swartz for what many considered a minor infraction. Swartz, who helped develop the RSS standard and was a cofounder of the advocacy group Demand Progress, was indicted after he gained entry to a closet at MIT and allegedly connected a laptop to the university's network to download millions of academic papers that were distributed by the JSTOR subscription service. Swartz was accused of repeatedly spoofing the MAC address of his computer to bypass a block MIT had placed on the address he used.

Although JSTOR did not pursue a complaint, the Justice Department pushed forward with prosecuting Swartz. U.S. Attorney Carmen Ortiz insisted that “stealing is stealing” and that authorities were just upholding the law. Swartz, in despair over his pending trial and the prospect of a felony conviction, committed suicide in 2013. In response to the tragedy, two lawmakers proposed a long-overdue amendment to the law that would help prevent prosecutors from overreaching in their use of it. The amendment, referred to as Aaron's law, was introduced months after Swartz's death by Rep. Zoe Lofgren (D-Calif.) and Sen. Ron Wyden (D-Oregon). The amendment would exclude breaches of terms of service and user agreements from the law and also narrow the definition of unauthorized access to make a clear distinction between criminal hacking activity and simple acts that exceed authorized access on a minor level. Instead, the amendment proposes to define unauthorized access as “circumventing one or more technological measures that exclude or prevent unauthorized individuals from obtaining or altering” information on a protected computer. The amendment also would make it clear that the act of circumvention would not include a user simply changing his MAC or IP address to gain access to a system.

### Copyright Act
