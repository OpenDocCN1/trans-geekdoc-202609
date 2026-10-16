
| Part 4: Defenses, Countermeasures, and Advanced Topics || Obfuscation/deobfuscation  

Anti-debugging/anti-anti-debugging  

Packing/unpacking  

Cryptors/decryptors  

Architectural defenses  

Legal  

Timeless debugging  

Binary instrumentation  

Intermediate representations  

Decompiling  

Automatic structure recovery  

Visualization  

Theorem provers  

Symbolic analysis  

Cracking extravaganza || Master defenses and counter-defenses.  

Evaluate defensive posture and tradeoffs.  

Explore advanced topics.  

Exercise reverse engineering and cracking tools, techniques, and mindset. |

### Hands-On Experience and Labs

The best way to learn reverse engineering and software cracking is by doing it. For this reason, this book will include several hands-on labs that demonstrate the concepts described in the text.

The goal of this book isn't to teach a particular set of tools and techniques. While the focus is on x86 software running in Windows, many of the approaches and techniques will translate to other platforms. This book will attempt to demonstrate a wide range of tools, including open-source, freeware, shareware, and commercial solutions. With an understanding of what tools are available and their relative strengths and weaknesses, you can more effectively select the right tool for the job.

Hands-on labs and exercises will also focus on reverse engineering and cracking a variety of different targets, including the following:

*   **Real software:** Some exercises will use real-world software carefully selected to avoid copyright violations.

*   **Manufactured examples:** Software written specifically for this book to illustrate concepts that are impractical to demonstrate with real-world examples.

*   **Crackmes:** Manufactured software developed by crackers to illustrate a concept or challenge others.

### Companion Download Files

The book mentions some additional files, such as labs or tools. These items are available for download from `https://github.com/DazzleCatDuo/X86-SOFTWARE-REVERSE-ENGINEERING-CRACKING-AND-COUNTER-MEASURES`.

## History

Before diving into the nitty-gritty details of cracking and reverse engineering, it is useful to understand its history. Software protections and the tricks and techniques used to overcome them have been evolving for decades.

### The First Software Protections

The first software copy protections emerged in the 1970s. Some of the early movers in the space were as follows:

*   **Apple II:** The Apple II incorporated proprietary disk drivers that would allow writing at half-tracks, writing extra rings, and staggering and overlapping sectors. The purpose of this was to make the disks unusable by non-Apple machines and software that wouldn't know to read and write at these odd offsets.

*   **Atari 800:** Atari 800 systems would intentionally include bad sectors in their disks and attempt to load these sectors. If these loads didn't return a “bad sector” error, then the software knew it wasn't a valid disk and would halt execution.

*   **Commodore 64:** Legitimate Commodore 64 software was distributed only on read-only disks. The software would attempt to overwrite the disk, and, if it succeeded, it knew the disk was counterfeit.

These protections all depended on unusual behavior by the software, such as the use of invalid memory or attempting to overwrite the program's own code. Defeating these protections required an understanding of how the software worked.

### The Rise of Cracking and Reverse Engineering

The rise of cracking and reverse engineering began in the 1980s. However, these early crackers weren't in it for the money. Cracking was a contest to determine who could figure out and bypass software protections the quickest.

Over the next several decades, the reverse engineering and cracking scene evolved. These are some of the key dates in the history of reverse engineering:

*   **1987:** Fairlight's formation in 1987 by Bacchus defines one of the first operational groups. Fairlight will later come to prominence in FBI crackdowns of the early 2000s. For more historic details visit `www.fairlight.to` and `csdb.dk`.

*   **1990:** Elliot J. Chikofsky and James H. Cross II defined reverse engineering as “the process of analyzing a subject system to identify the system's components and their interrelationships and to create representations of the system in another form or at a higher level of abstraction. (“Reverse Engineering and Design Recovery: A Taxonomy.” *IEEE Software*, Vol. 7, Issue 1, Jan 1990).

*   **1997:** Old Red Cracker (handle +ORC) founds the Internet-based High Cracking University (+HCU) to allow everyone to learn about cracking. +ORC released “how to crack” lessons online and authored academic papers. +HCU students had handles that began with an +.

*   **1997–2009:** The “warez scene” emerges with groups competing to be the first to release copyrighted material. Insiders (aka “suppliers”) provided early access to their groups, “crackers” broke the protections, and “couriers” distributed cracked software to FTP sites. Between 2003 and 2009, approximately 3,164 active groups were on “the scene”, competing primarily for pride and bragging rights, not money.

*   **2004:** The FBI and other countries begin raids against “the scene”. Operation Fastlink (2004) led to the conviction of 60 warez members, and Operation Site Down (2005) took down 25 warez groups.

The arms race between software protections and crackers continues to rage, and reverse engineering is an invaluable skill set on both sides. Crackers need to understand how a program works to manipulate it and bypass defenses. On the defensive side, it's important to understand the latest cracking techniques to develop defenses that protect intellectual property and other sensitive data.

## Legal

The best way to learn is by doing. This is why this book includes labs and exercises with real-world software as well as manufactured examples and crackmes. We are not lawyers, and those with concerns should consult a lawyer. We recommend the Electronic Frontier Foundation (`www.eff.org`). [Chapter 15](#c16.xhtml) covers legal topics because we feel it's important for everyone to understand the US-based laws that affect this area. There are two main laws to be aware of: the Copyright Act and the Digital Millennium Copyright Act (DMCA).

The Fair Use Clause of the Copyright Act (Copyright Act, 17 U.S.C. § 107) states that reverse engineering falls under “fair use” when done for “…purposes such as criticism, comment, news reporting, teaching (including multiple copies for classroom use), scholarship, or research….” This exception is balanced against “the effect of the use upon the potential market for or value of the copyrighted work.” In essence, reverse engineering used for educational purposes is legal if you don't share or sell the cracked software.

In October 2016, the DMCA also added an exception for good faith security research. It states, “accessing a computer program solely for purposes of **good-faith testing**, …where such activity is carried out in a controlled environment designed to **avoid any harm** to individuals or the public, …and is not used or maintained in a manner that facilitates copyright infringement.”

The software examined in this book and used in exercises was carefully selected to fall under the fair use and DMCA exceptions. If you are planning to reverse engineer and crack software for anything other than self-education, you should consult a lawyer. The legal considerations of reverse engineering will also be explored in greater detail in a later chapter.

Software reverse engineering and cracking have a rich history, and this skill set has both offensive and defensive applications. However, it is important to understand the laws around these disciplines and ensure that your activities fall under the good-faith testing and fair use exemptions.

