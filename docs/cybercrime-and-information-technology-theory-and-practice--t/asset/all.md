![](images/cover.jpg)

![Cybercrime and Information Technology cover, Edited by Alex Alexandrou, published by CRC Press](images/cover.jpg)

First edition published 2022  
by CRC Press  
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press  
2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2022 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](http://mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

*Library of Congress Cataloging-in-Publication Data*

Names: Alexandrou, Alex (Professor of information technology security), author.  
Title: Cybercrime and Internet technology : theory and practice--the computer network infostructure and computer security, cybersecurity laws, internet of things (IoT), and mobile devices / Alex Alexandrou.  
Identifiers: LCCN 2021007948 (print) | LCCN 2021007949 (ebook) | ISBN 9780367251574 (hardback) | ISBN 9781032053851 (paperback) | ISBN 9780429318726 (ebook)  
Subjects: LCSH: Computer crimes. | Computer security. | Computer security--Law and legislation. | Computer networks--Security measures.  
Classification: LCC HV6773 .A425 2022 (print) | LCC HV6773 (ebook) | DDC 364.16/8--dc23  
LC record available at [https://lccn.loc.gov/2021007948](https://lccn.loc.gov)  
LC ebook record available at [https://lccn.loc.gov/2021007949](https://lccn.loc.gov)

 

ISBN: 978-0-367-25157-4 (hbk)  
ISBN: 978-1-032-05385-1 (pbk)  
ISBN: 978-0-429-31872-6 (ebk)

DOI: [10.1201/9781003020080](http://doi.org/10.1201/9781003020080)

Typeset in Minion  
by Deanta Global Publishing Services, Chennai, India  
Access the Support Material: [www.crcpress.com/9780367251574](http://www.crcpress.com/9780367251574)

*To my parents Achilleas and Maria Alexandrou, who taught me about humility, to have a good work ethic and a willingness to help others.*

*To my grandmother, Eleni who taught me to be an independent person and NEVER Give UP!*

# [Preface](#contents.xhtml#re_preface1)

My motivation for writing this book stems from my struggle to find a textbook that strengthens student understanding of the fundamentals of computer and network security and includes the study of cybercrime.

Therefore, the primary goal of this book is to provide a strong foundation of cybercrime knowledge along with the fundamental concepts of networking, computer security, Internet of Things (IoTs), and mobile devices.

With this knowledge base, students can also learn to design and implement mitigation strategies and can then follow the processes of developing security policies.

The textbook is appropriate for courses in the Computer Forensics and Criminal Justice curriculum and is relevant to those studying Security Administration, Public Administrations, Police Studies, Business Administration, Computer Science, and Information Systems.

The book is organized into eight chapters.

*   **[Chapter 1](#c1.xhtml#c1) –** This first chapter describes information processing, bytes and bits, Binary, Hexadecimal ASCII, EBCDIC, and UNICODE codes, Boolean algebra, logic gates, color depth, color models and resolution, compression, and a brief history of computing technology.
*   **[Chapter 2](#c2.xhtml#c2) –** This chapter studies the evolution and phases of cybercrime including: motives that make cybercrime alluring, different categories of cybercrime, the costs and the role of cryptocurrency, online child sexual abuse and exploitation, the connections among cybercrime, machine learning and artificial intelligence, and explains state-sponsored and cyber warfare.
*   **[Chapter 3](#c3.xhtml#c3)** – This chapter provides an overview of the legal system in the United States and the main barriers to prosecuting cybercriminals.
*   **[Chapter 4](#c4.xhtml#c4) –** The chapter describes cyberlaw standards, and regulations affecting cybercrime including anti-hacking laws, data security laws in critical infrastructure, the National Institute of Standards and Technology (NIST) cybersecurity framework, the public and private sector partnerships laws, and surveillance and privacy laws.
*   **[Chapter 5](#c5.xhtml#c5) –** This chapter explores computer networking, its history and evolution, and explains the essential computer network components and terminology, clarifies the different types of networking, and the different theoretical network models such as Open Systems Interconnection (OSI) and Transmission Control Protocol/Internet Protocol (TPC/IP).
*   **[Chapter 6](#c6.xhtml#c6)** – This chapter provides an overview of computer security technology, including its history and evolution, terminology, different types of cyberattacks, computer security prevention mechanisms, and encryption methodology.
*   **[Chapter 7](#c7.xhtml#c7) –** This chapter introduces the Internet of Things (IoTs), applications, and security vulnerabilities.
*   **[Chapter 8](#c8.xhtml#c8) –** The final chapter explains the historical significance of mobile phone technology, cellular networks, and the main components of network architecture, along with security threats and vulnerabilities.

# [Acknowledgment](#contents.xhtml#re_ack)

First and foremost, I express my heartfelt appreciation to the Taylor and Francis group for the development and production of this book, especially to Mr. Mark Listewnik, for his support, guidance, and patience. Special thanks to John and Patricia Pommells for their support and encouragement. I also owe an enormous debt of gratitude to the reviewers for their thoughtful comments and efforts, including Julia Vonferber, PhD; Muath Obaidat, PhD; Nina Russakoff, JD; and Sylvia Russakoff, MA, MBA.

Finally, I am eternally grateful to Ms. Sylvia Russakoff; without her advice, wisdom, and knowledge, this book would not have been possible.

# [Author’s Bio](#contents.xhtml#re_preface2)

![](images/inline0.1.jpg)

**Alex Alexandrou** is an Assistant Professor in the Department of Security, Fire, and Emergency Management at John Jay College of Criminal Justice. He received his bachelor’s degree from Youngstown State University, his master’s degree from Brooklyn College of the City University of New York, and his doctorate degree in computing studies from Pace University. Dr. Alexandrou has worked extensively in both business and academic environments. He has 18 years of experience in Health Information Technology and Operations leadership, including software integration, biometric and access control systems, deploying virtualization by transitioned use of physical servers into virtualization technology, and realigning IT architecture with cloud-based networks and security platforms/technologies. Dr. Alexandrou has taught courses in Cybersecurity, Health Information Technology, and Telemedicine at both undergraduate and graduate levels since 2015. He is a firm believer in *Hard work*, *determination and never giving up on what you really want to do.*

Dr. Alexandrou has conducted research studies on mobile device security in healthcare, Deep Fake videos, Cybercrime, and Biometric authentication. His current research interests include system security and privacy for healthcare applications, mobile forensics investigation, and mobile device vulnerabilities and threats.

# [Chapter 1 Understanding Essential Computer Concepts](#contents.xhtml#re_c1)

DOI: [10.4324/9780429318726-1](https://doi.org/10.4324/9780429318726-1)

## [Objectives](#contents.xhtml#re_h-1-1)

After completing this chapter, the student will be able to:

*   Understand information processing in computing devices
*   Explain the difference between a Bit and a Byte
*   Understand Binary, Hexadecimal ASCII, EBCDIC, and UNICODE codes
*   Understand Boolean algebra, logic gates, and truth tables
*   Explain color depth, color models, and screen resolution
*   Understand lossy and lossless compression
*   Understand the basics of quantum computing
*   Recognize computer terminology
*   Understand the history of computers and the technology surrounding them

## [1.1 Understanding Computation](#contents.xhtml#re_h-1-3)

### [Conventional Computer Systems](#contents.xhtml#re_h-1-4)

Technological innovation is a combination of the brain’s computing power and the desire to mimic human intelligence. The progression of technology is the result of the human desire to solve problems and improve the quality of life. Electronic devices are technological advancements that correlate with our efforts to solve problems.

The computer is an electronic device that accepts input, processes data by modifying or manipulating it, stores the data for further reference, and produces output, all according to a series of instructions or commands. This group of processes is the von Neumann architecture, or von Neumann concept, published in 1945 by John von Neumann, which describes a proposed architecture for a computer. The concept depicts a stored-program computer with instruction and program data stored in the same memory.^([¹](#fn1))

All conventional computing devices still operate through these four basic functions**:** receiving input, processing data, storing data, and producing output.

First, the user inputs information, using an input device like a touchpad, keyboard, mouse, trackpad, microphone, or video camera. The data is converted into binary data, identified as either 0s or 1s. The central processing unit (CPU), the “brain” of the computer, with the help of the memory, analyzes how to display each character.

Next, the CPU manipulates the binary data and stores it in memory for further reference. The CPU processes the binary data and creates output, viewed on a screen, speaker, or printer. To view the image on a monitor, the CPU works in conjunction with a software application, or program that sends instructions to the computer’s graphics card. The graphics card, which controls the visual display, decides how to arrange the screen to create the image. All this happens through a series of instructions or commands that the computer follows. Complex tasks, such as editing high definition video, or 3D modeling and rendering, require more processing power and memory. Lastly, the processed data is stored on the hard drive (HD). [Figure 1.1](#c1.xhtml#f1.1) summarizes information processing in a computing device.

![FIGURE 1.1 Information processing in a computing device.](images/fig1.1.jpg)

**FIGURE 1.1** Information processing in a computing device.

The term computer was initially mathematical. “The word *computer* is a combination of the Latin word *putare****,*** which means to ‘think or train,’ and *com,* which means ‘together.’ The Oxford English Dictionary dates the first use of the word to 1579, linking it with “arithmetical or mathematical reckoning.”^([²](#fn2))

![FIGURE 1.2 Computers at work – calculating test data. Ames Research Center, c1958. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.2.jpg)

**FIGURE 1.2** Computers at work – calculating test data. Ames Research Center, c1958. Photograph from National Aeronautics and Space Administration (NASA).

It is worth noting that the field of mathematical logic has had a major impact on the development of computer science. One instance of this is in the area of program verification. “Since a computer program is simply a formal description of calculation, it can be verified in the same way that a mathematical theorem can be verified using logic.”^([³](#fn3))

The Greek philosopher Aristotle provided a foundation for *mathematical logic* that enabled later ideas to become reality. Aristotle viewed logic as a tool for philosophers and scientists alike.^([⁴](#fn4))

The American space program of the 1960s, along with the research and development that went into its missions, helped to accelerate the development of the computing industry, causing a dramatic shift in electronics and computing systems ([Figures 1.3](#c1.xhtml#f1.3) and [1.4).](#c1.xhtml#f1.4)

![FIGURE 1.3 Electronic Machine Computing Branch, IBM 704 Date Processor, c1958. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.3.jpg)

**FIGURE 1.3** Electronic Machine Computing Branch, IBM 704 Date Processor, c1958. Photograph from National Aeronautics and Space Administration (NASA).

![FIGURE 1.4 Dr. Werner von Braun (seated) examining a Saturn computer in the Astrionics Laboratory at the Marshall Space Flight Center, c1966. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.4.jpg)

**FIGURE 1.4** Dr. Werner von Braun (seated) examining a Saturn computer in the Astrionics Laboratory at the Marshall Space Flight Center, c1966. Photograph from National Aeronautics and Space Administration (NASA).

## [1.2 Input](#contents.xhtml#re_h-1-5)

The user interface (UI) is the way in which the user interacts with the machine (computer). The basic human–computer interaction consists of physical inputs such as keyboards, mouse, voice commands, tabs in screen (with commands run inside), to convert physical actions and conditions to binary data ([Figure 1.5](#c1.xhtml#f1.5)). 

![FIGURE 1.5 A research to improve the human–computer interface, c1966. MAGIC (Machine for Automatic Graphics Interface to a Computer) Photograph from NIST Digital Archives.](images/fig1.5.jpg)

**FIGURE 1.5** A research to improve the human–computer interface, c1966. MAGIC (Machine for Automatic Graphics Interface to a Computer) Photograph from NIST Digital Archives.

### [Understanding Binary Data](#contents.xhtml#re_h-1-6)

Human languages use characters or symbols, letters and images to signify meaning. These characters are unintelligible to the wires and circuits within the computer. The computer does not act as we do; instead, it stores values as electrical charges. More specifically, when electricity flows through a wire, the electrical signal can be represented as either 1 or 0, True or False, Yes or No, or On or Off. [Figure 1.6](#c1.xhtml#f1.6) demonstrates the binary representation of an image.

![FIGURE 1.6 The Binary representation of an image.](images/fig1.6.jpg)

**FIGURE 1.6** The Binary representation of an image.

The 0 or 1 is referred to as a *bit* (short for binary digit), and is the smallest unit of information. The more electrical connections the computer uses, the more bits are flowing through its system.

While a bit can represent only a 0 or a 1, a *byte*, a collection of exactly 8 bits, represents a unique character. [Table 1.1](#c1.xhtml#t1.1) and [Figure 1.7](#c1.xhtml#f1.7) demonstrate the possible patterns or states of 0s and 1s that can be made from 1, 2, 3 and 4 bits. 

**TABLE 1.1** Bits and Their Possible Patterns

  
| Bits || Possible Patterns |
| --- | --- |
| 1 bit (2 possible values) || 0 or 1 |
| --- | --- |
| 2 bits (4 values) || 00 01 10 11 |
| 3 bits (8 values) || 000 001 010 011100 101 110 111 |

![FIGURE 1.7 Bits possible patterns.](images/fig1.7.jpg)

**FIGURE 1.7** Bits possible patterns.

To be able to represent more than 1 and 0, True/False, Yes/No, or On/Off, we collect 8 bits to form 1 byte. With 1 byte we can represent and store the numbers between 0 and 255 (2⁸). Therefore, a single byte can represent up to **256** different values.

By arranging bits into bytes, any number up to 255 can be represented using only 0s and 1s. Overall, each additional bit doubles the number of possible patterns ([Table 1.2](#c1.xhtml#t1.2)).

**TABLE 1.2** Bits and the Number of Patterns with Exponents

  
| Bits || Patterns || Exponents |
| --- | --- | --- |
| 1 bit || 2 || 2¹ |
| --- | --- | --- |
| 2 bits || 4 || 2² |
| 3 bits || 8 || 2³ |
| 4 bits || 16 || 2⁴ |
| 5 bits || 32 || 2⁵ |
| 6 bits || 64 || 2⁶ |
| 7 bits || 128 || 2⁷ |
| 8 bits (one byte) || 256 || 2⁸ |

In our everyday lives, we use a base**\-**10 numeric system with numbers from 0 to 9 (ten digits), whether we are dealing with money, weight, time, or volume. The prefix “dec-” means ten **(**deka**)** from Ancient Greek “δέκα” in the metric system. For example, the *dec*athlon event is equal to 10 meters, and a *dec*agon is a 10-sided polygon. It is quite likely we have been using the base**\-**10 system for thousands of years because humans have 10 fingers or digits, so that counting to 10 felt natural.

As noted earlier, a *binary number* is based on the power of 2 (2*^n* ). Why do almost all computers use the binary system? Computers use the binary number system as an alternative to the decimal system because it simplifies program design and makes it easier for the programmer to tell the computer what to do.

The computer understands electrical signals. We convey information through microscopic wires inside the computer. Each wire carries its own electrical signal. There are only two states possible for an electrical signal, charged and not charged. If a wire is carrying an electrical signal (charged), it corresponds to 1**.** It is in a “signal” state. If the wire is not carrying an electrical signal, it is not in signal state, and corresponds to 0. A bit is always either On (1) or Off (0), and the signal states change according to the instructions the computer is following. In the binary system, groups of 1s and 0s may represent any number**.** A single wire represents only one bit; many wires represent additional bits. Although a wire can carry variable amounts of electricity, it must interpret its content as either 0 or 1.

When *transistors* were invented, they could control the flow of electricity, acting like digital switches. The transistors inside the computer are so small that we would need an electron microscope to see them. Depending on the transistor and its threshold voltage, the transistor turns on when enough electricity flows through, and turns off when not. For example, if the threshold voltage of a transistor is 5V, any voltage of 3.5V or higher will turn the transistor on. Any voltage lower than 3.5V will turn the transistor off. In practice, when we plug a mouse into a Universal Serial Bus (USB) computer port, a transistor will notice the voltage required by the mouse and translate the state of the mouse to On, telling the computer that an external USB device is plugged into the port.

When we type a letter, number, or symbol on the keyboard, the computer converts each character to binary code instantaneously, simultaneously displaying the character on the monitor.

Computers process large amounts of data measured in MIPS (Millions of Instructions per Second). A single byte (8 bits) represents a single character. For example, the letter A is saved as 01000001, and the number 7 is saved as 0111. The number 77 is saved as 01001101 (see [Figure 1.8](#c1.xhtml#f1.8) and [Table 1.10](#c1.xhtml#t1.10)).

![FIGURE 1.8 Demonstrates the difference between a Bit and a Byte.](images/fig1.8.jpg)

**FIGURE 1.8** Demonstrates the difference between a Bit and a Byte.

The binary system is the main language used by computers because it is simple and reliable. Furthermore, it is efficient because it requires a minimum number of electric circuits, and is of low-cost, uses little energy, and occupies minimum space.

Computers calculate conversion to binary code much faster than a human could, but it is useful to know how to do conversion by hand (see [Table 1.3](#c1.xhtml#t1.3) Decimal vs Binary Systems and [Table 1.4](#c1.xhtml#t1.4) Computer Data Conversion).

**TABLE 1.3** Decimal vs Binary System

  
| Decimal System  
The decimal system uses 10 digits from 0 to 9  
 || Binary System  
The binary system uses only two digits, 0 & 1  
 |
| --- | --- |
|  ||  |
| --- | --- |
| The decimal system uses the powers of 10 for calculation (10⁰ =1, 10¹\=10, 10²\=100, 10³\=1000, 10⁴\=10000……). || The Binary system uses the powers of 2 (2⁰\=1, 2¹\=2, 2²\=4, 2³\=8, 2⁴\=16……). |

**TABLE 1.4** Computer Data Conversion

  
| Units  
*(byte prefixes)*  
 || Actual number of bytes  
*(decimal form)*  
 || Base-2 *(Number of bytes)* || Approximate  
Size in bytes  
*(decimal form)*  
 || Base-10 *(decimal)* |
| --- | --- | --- | --- | --- |
| Kilobyte (KB) || 1,024 || 2^(10) || One-thousand bytes || 10³ |
| --- | --- | --- | --- | --- |
| Megabyte (MB) || 1,048,576 || 2^(20) || One-million bytes || 10⁶ |
| Gigabyte (GB) || 1,073,742.824 || 2^(30) || One-billion bytes || 10⁹ |
| Terabyte (TB) || 1,099,511,627,776 || 2^(40) || One trillion bytes || 10^(12) |
| Petabyte (PB) || 1,125,899,906,842,624 || 2^(50) || One-quadrillion bytes || 10^(15) |
| Exabyte (EB) || 1,152,921,504,606,846,976 || 2^(60) || One-quintillion bytes || 10^(18) |
| Zettabyte (ZB) || 1,180,591,620,717,411,303,424 || 2^(70) || One-sextillion bytes || 10^(21) |
| Yottabyte (YB) || 1,208,925,819,614,629,174,706,176 || 2^(80) || One-septillion bytes || 10^(24) |

### [Conversion from Binary to Decimal](#contents.xhtml#re_h-1-7)

We would like to convert Binary 1001 to a decimal number. In Rows 1 and 2 of [table 1.5](#c1.xhtml#t1.5), we see the powers of two and their numerical equivalents written from right to left.

To convert a binary number to decimal, the key is to deconstruct the number as the sum of powers of two.

To find the decimal number represented by the binary code 1001, look at the table and calculate each column. Any 0 in binary will remain 0 in decimal, since the signal is Off. Reading from right to left: 1=1 (2⁰), 0=0 (2¹), 0=0 (2²), 1=1 (2³). Adding the numbers together yields 9. Therefore, the binary code 1001 is equal to the number 9.

In the next line, we convert 10011011 to its decimal value. Again, the 0s do not change, from right to left; the 1s are equal to 1,2,8,16,128. The sum of these numbers is 155. Therefore, the binary code 10011001 is equal to the number 155 ([Table 1.5](#c1.xhtml#t1.5)).

 **TABLE 1.5** Conversion from Binary to Decimal 

 
| 2^(10) || 2⁹ || 2⁸ || 2⁷ || 2⁶ || 2⁵ || 2⁴ || 2³ || 2² || 2¹ || 2⁰ || BinaryDecimal = 9BinaryDecimal =155 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1024 || 512 || 256 || 128 || 64 || 32 || 16 || 8 || 4 || 2 || 1 |
|  ||  ||  ||  ||  ||  ||  || 1 || 0 || 0 || 1 |
|  ||  ||  ||  ||  ||  ||  || 8 || +0 || +0 || +1 |
|  ||  ||  || 1 || 0 || 0 || 1 || 1 || 0 || 1 || 1 |
|  ||  ||  || 128 || +0 || +0 || +16 || +8 || +0 || +2 || +1 |
| **Right to Left**![](images/inline1.1.jpg) |

### [Conversion from Decimal to Binary](#contents.xhtml#re_h-1-8)

Now, let us convert in the other way – the decimal 23 to Binary. What is the largest power of two that is less than the number we are converting? The column represented by 32 (2⁵) is larger than 23, therefore we will begin with 16 (2⁴). When we omit the 0, the numbers left are 16 + 4 + 2 + 1=23. Therefore, the binary number 10111 is the digit 23. Another example shows that the binary number 111 is the digit 7 (4 + 2 + 1 = 7) (see [Table 1.6](#c1.xhtml#t1.6)). 

 **TABLE 1.6** Conversion from Decimal to Binary 

 
| 2^(10) || 2⁹ || 2⁸ || 2⁷ || 2⁶ || 2⁵ || 2⁴ || 2³ || 2² || 2¹ || 2⁰ || Decimals # 23BinaryDecimal # 7Binary |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1024 || 512 || 256 || 128 || 64 || 32 || 16 || 8 || 4 || 2 || 1 |
|  ||  ||  ||  ||  ||  ||  || 16 || +0 || +4 || +2 |
|  ||  ||  ||  ||  ||  ||  || 1 || 0 || 1 || 1 |
|  ||  ||  ||  ||  ||  ||  ||  ||  || 4 || +2 |
|  ||  ||  ||  ||  ||  ||  ||  ||  || 1 || 1 |
| **Right to Left**![](images/inline1.2.jpg) |

### [Hexadecimal](#contents.xhtml#re_h-1-9)

Another common number system used in computer science is Hexadecimal or Hex, also called Base 16, because it consists of 16 characters. Hexadecimal is derived from hexa, meaning six, like the six-sided hexagon, and “decimal’”from the number 10. The hexadecimal system uses only 10 digits (0–9), and 6 letters A, B, C, D, E, and F**.** The system utilizes letters instead of other symbols because it is easier to type them on a keyboard. Hexadecimal calculation is different from binary. Each hexadecimal character is equivalent to 4 bits or half a byte (for example, 1110), and is called a Nibble, or Nybble**.**

The hexadecimal system is efficient in computer programming, because only a single hexadecimal character represents 4 bits. [Table 1.7](#c1.xhtml#t1.7) displays decimals and hex values from 1 to 31.

**TABLE 1.7** Decimals and Hex values

  
| Decimals || Hex || Decimals || Hex |
| --- | --- | --- | --- |
| **0** || 0 || 16 || 10 |
| --- | --- | --- | --- |
| **1** || 1 || 17 || 11 |
| **2** || 2 || 18 || 12 |
| **3** || 3 || 19 || 13 |
| **4** || 4 || 20 || 14 |
| **5** || 5 || 21 || 15 |
| **6** || 6 || 22 || 16 |
| **7** || 7 || 23 || 17 |
| **8** || 8 || 24 || 18 |
| **9** || 9 || 25 || 19 |
| **10** || A || 26 || 1A |
| **11** || B || 27 || 1B |
| **12** || C || 28 || 1C |
| **13** || D || 29 || 1D |
| **14** || E || 30 || 1E |
| **15** || F || 31 || 1F |

For example, the single hexadecimal character E can represent the group of four bits 1110, called a Nybble. A group of eight bits, 1110 1100, called a byte, represents two hexadecimal characters EC. When we use hexadecimal characters in a code, we add **0x** to the beginning of the value, for example **0xEC.** When programmers write codes, they try to represent values as efficiently as possible. For example, the hexadecimal letter A**,** which represents the number 10, is more manageable than the binary number 1010, which also represents 10. In another example, the decimal number 252 is 1111 1100 in binary code, but in hex it is just FC. Developers of web pages use Hex to represent the specific colors within Hyper Text Markup Language (HTML) the standard markup language for Web pages within Cascading Style Sheets (CSS).

Cascading Style Sheets are a set of rules that determine how a webpage should look like, telling the browser what colors the developer wants and how to display them. This technology, alongside HTML and JavaScript, is the foundation of the World Wide Web (WWW).

The primary use of hexadecimal code is a human-friendly representation of binary**\-**coded values. The hexadecimal color system is the standard system for all web browsers. Each hexadecimal digit is a number between 0 and 255 in decimal numbers, but it is much easier to read as 2 hexadecimal digits from 00 to FF.

When choosing colors, the developer knows that the base colors Red, Green, and Blue (RGB), when mixed together, can reproduce a wide range of colors on a computer screen. On an 8-bit color screen, 8 bits can represent each color (or 2⁸ = 256). This means there are 256 possible values for each color, 00**–**255 which can be represented in a double**\-**digit hexadecimal code from 00 to FF, to shorten the HTML code length.

The purest white color in hexadecimal code displays red, green, and blue at the highest possible color brightness of the RGB model and is written in hex as #FFFFFF. In decimals, it would be nine digits, 255,255,255. Hex code makes it possible for 256 numbers to be represented by only two different characters, for example FF is represented by #255. In RGB the hex value of black is written as #000000, because all three colors, Red, Green, and Blue, have zero value. Yellow in RGB hex is written as #FFFF00 and is composed of 100% red or #255, 100% green or #255 value, and 0% or 0 value of Blue. Pure Red in RGB hex is written as #FF0000 and is composed of 100% Red or #255 value, 0% Green, and 0% Blue.

### [Converting from Hexadecimal to Binary](#contents.xhtml#re_h-1-10)

We learn to count from small numbers to very large ones. In contrast, the hexadecimal system has only 16 *characters* in its set of numbers. In hex we count **0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F –** and that is it! When we need a value in excess of the letter **F (decimal 15),** we go through the sequence again, but this time always beginning with 1, then with 2, and so on. Therefore, **hex 11** is equal to **decimal 17** and **hex 21** is equal to **decimal 33**. This is displayed in [Table 1.8](#c1.xhtml#t1.8), showing the first 255 hexadecimal numbers.

**TABLE 1.8** The first 255 in hexadecimal numbers

  
| Hexadecimal numbers from 0 to 255 |
| --- |
| 0 1 2 3 4 5 6 7 8 9 A B C D E F 10 11 12 13 14 15 16 17 18 19 1A 1B 1C 1D 1E 1F 20 21 22 23 |
| --- |
| 24 25 26 27 28 29 2A 2B 2C 2D 2E 2F 30 31 32 33 34 35 36 37 38 39 3A 3B 3C 3D 3E 3F 40 |
| 41 42 43 44 45 46 47 48 49 4A 4B 4C 4D 4E 4F 50 51 52 53 54 55 56 57 58 59 5A 5B 5C 5D |
| 5E 5F 60 61 62 63 64 65 66 67 68 69 6A 6B 6C 6D 6E 6F 70 71 72 73 74 75 76 77 78 79 7A 7B |
| 7C 7D 7E 7F 80 81 82 83 84 85 86 87 88 89 8A 8B 8C 8D 8E 8F 90 91 92 93 94 95 96 97 98 99 |
| 9A 9B 9C 9D 9E 9F A0 A1 A2 A3 A4 A5 A6 A7 A8 A9 AA AB AC AD AE AF B0 B1 B2 B3 |
| B4 B5 B6 B7 B8 B9 BA BB BC BD BE BF C0 C1 C2 C3 C4 C5 C6 C7 C8 C9 CA CB CC CD |
| CE CF D0 D1 D2 D3 D4 D5 D6 D7 D8 D9 DA DB DC DD DE DF E0 E1 E2 E3 E4 E5 E6 E7 |
| E8 E9 EA EB EC ED EE EF F0 F1 F2 F3 F4 F5 F6 F7 F8 F9 FA FB FC FD FE FF |

To convert a hex number to a binary number, once a hex number is larger than a *nybble* (4 bits or half a byte) the left digit is valued more. Look at each *nybble* independently (see [Table 1.9)](#c1.xhtml#t1.9).

**TABLE 1.9** Translate Hex to binary

  
| Hex || Conversion of Each Part || Binary Result |
| --- | --- | --- |
| 7F || **7=** 0111 and **F=**1111 || Therefore, Hex 7F=**0111 1111 Binary** |
| --- | --- | --- |
| D4B || **D**\=1101, **4**\=0100 and **b**\=1011 || Therefore, Hex **D4B**\=**1101 0100 1011 Binary** |
| FF301B || **f=**1111, **f=**1111, **3**\=0011, 0=0000, **1**\=0001 and **B**\=1011 || Therefore, Hex FF301B =**1111 1111 0011 0000 0001 1011 Binary** |

### [Conversion from Binary to Hexadecimal](#contents.xhtml#re_h-1-11)

To convert from binary to hexadecimal, follow the reverse of the above examples. The first example **1101** is very simple. The answer is D (13=D) in the hexadecimal system or **D** **[16]**. The second example is little complicated **10110111.** Each *nybble* is 4 bits or half a byte. The answer is **B7** (11 is B and 7) in the hexadecimal system or **B7** **[16.]** In the third example, the binary number is 1011101010 and the answer is **2EA** (2+14 which is E + 10 which is A) in the hexadecimal system or **2EA** **[16]** ([Figure 1.9](#c1.xhtml#f1.9)).

![FIGURE 1.9 Conversion from binary to hexadecimal.](images/fig1.9.jpg)

**FIGURE 1.9** Conversion from binary to hexadecimal.

### [ASCII, EBCDIC and UNICODE](#contents.xhtml#re_h-1-12)

ASCII is an acronym for American Standard Code for Information Interchange**.** This standard, established in the 1960s and rarely used today, was created to serve as a common language among computers using the English alphabet. The original ASCII code represents 128 characters as standard numeric values, lower and uppercase letters, symbols, numbers, punctuation marks, and control characters. Each character is assigned a number between 0 and 127, and contains 7-bit codes, meaning that there are 128 different characters within seven bits, including seven digits set to 0 or a 1, True or False, Yes or No, On or Off. Besides the printable characters, ASCII code also contains non-printable characters that control how text is processed.^([⁵](#fn5))

Another encoding system is the Extended Binary Coded Decimal Interchange Code (EBCDIC), developed in the late 1950s and early 1960s, and used by International Business Machines (IBM).^([⁶](#fn6))

[Table 1.10](#c1.xhtml#t1.10) displays the first 25 (0–25) decimals and characters in binary values and ASCII code.

**TABLE 1.10** Decimal numbers 0–25 and the alphabet in binary values and ASCII code

  
| Decimals || Binary || Alphabet uppercase || ASCII  
code  
 || Binary || Alphabet  
lowercase  
 || ASCII  
code  
 || Binary |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **0** || 0000 0000 || **A** || 065 || 0100 0001 || **A** || 097 || 0110 0001 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **1** || 0000 0001 || **B** || 066 || 0100 0010 || **B** || 098 || 0110 0010 |
| **2** || 0000 0010 || **C** || 067 || 0100 0011 || **C** || 099 || 0110 0011 |
| **3** || 0000 0011 || **D** || 068 || 0100 0100 || **D** || 100 || 0110 0100 |
| **4** || 0000 0100 || **E** || 069 || 0100 0101 || **E** || 101 || 0110 0101 |
| **5** || 0000 0101 || **F** || 070 || 0100 0110 || **F** || 102 || 0110 0110 |
| **6** || 0000 0110 || **G** || 071 || 0100 0111 || **G** || 103 || 0110 0111 |
| **7** || 0000 0111 || **H** || 072 || 0100 1000 || **H** || 104 || 0110 1000 |
| **8** || 0000 1000 || **I** || 073 || 0100 1001 || **I** || 105 || 0110 1001 |
| **9** || 0000 1001 || **J** || 074 || 0100 1010 || **J** || 106 || 0110 1010 |
| **10** || 0000 1010 || **K** || 075 || 0100 1011 || **K** || 107 || 0110 1011 |
| **11** || 0000 1011 || **L** || 076 || 0100 1100 || **L** || 108 || 0110 1100 |
| **12** || 0000 1100 || **M** || 077 || 0100 1101 || **M** || 109 || 0110 1101 |
| **13** || 0000 1101 || **N** || 078 || 0100 1110 || **N** || 110 || 0110 1110 |
| **14** || 0000 1110 || **O** || 079 || 0100 1111 || **O** || 111 || 0110 1111 |
| **15** || 0000 1111 || **P** || 080 || 0101 0000 || **P** || 112 || 0111 0000 |
| **16** || 0001 0000 || **Q** || 081 || 0101 0001 || **Q** || 113 || 0111 0001 |
| **17** || 0001 0001 || **R** || 082 || 0101 0010 || **R** || 114 || 0111 0010 |
| **18** || 0001 0010 || **S** || 083 || 0101 0011 || **S** || 115 || 0111 0011 |
| **19** || 0001 0011 || **T** || 084 || 0101 0100 || **T** || 116 || 0111 0100 |
| **20** || 0001 0100 || **U** || 085 || 0101 0101 || **U** || 117 || 0111 0101 |
| **21** || 0001 0101 || **V** || 086 || 0101 0110 || **V** || 118 || 0111 0110 |
| **22** || 0001 0110 || **W** || 087 || 0101 0111 || **W** || 119 || 0111 0111 |
| **23** || 0001 0111 || **X** || 088 || 0101 1000 || **X** || 120 || 0111 1000 |
| **24** || 0001 1000 || **Y** || 089 || 0101 1001 || **Y** || 121 || 0111 1001 |
| **25** || 0001 1001 || **Z** || 090 || 0101 1010 || **Z** || 122 || 0111 1010 |

## [1.3 Processing](#contents.xhtml#re_h-1-13)

### [Boolean Algebra, Logic Gates, and Truth Tables](#contents.xhtml#re_h-1-14)

As described above, we send bits through the computer using wires that represent 1s and 0s. The computer uses logic gates to enable these 1s and 0s to execute more complicated operations.

A logic gate is a device based on Boolean function that implements logical operations in any digital system. The miniature electronic circuits within the computer are the most basic building blocks, using one or more inputs to produce a single output (1 or 0), based on logical functions. Simply put, logic gates control the flow of electric current through a circuit. Certain circuits may have only a few logic gates, while others, like those found within a microprocessor, may have millions of logic gates. When the computer uses millions of logic gates, it is possible to perform highly complex operations.

Logic gates are the foundation for computers and other modern digital electronics. They are used in microprocessors and microcontrollers, and are embedded in system applications like mobile devices and IoT devices that integrate hardware circuitry and software programming techniques.

To understand logic gates**,** we need to understand the work of George Boole, the inventor of Boolean algebra. His mathematics are fundamental to computer science. George Boole was an English mathematician of the mid-1800s who developed logical statements that went beyond Aristotle’s mathematical logic. Boole wrote *The mathematical analysis of logic* in 1847*.*^([⁷](#fn7))

In Boolean algebra, the values of variables are expressed only as true or false, while in ordinary algebra the values of variables involve numbers, variables, and operations. Furthermore, the Boolean operation takes a specific input and produces a specific output, based on a set of rules. Logic gates implement basic logical functions and are the vital building blocks of digital integrated circuits.

The three basic logic gates are NOT, AND, and OR. Other gates include XOR, NAND, NOR, and XNOR. All gates are represented by symbols and truth tables. Truth tables help us understand how circuits work. The following are the three basic logic gates with their symbols and truth tables.

*   A NOT-gate is the simplest logic gate, also known as an inverter. The NOT-gate has only one input and one output. The output is the reverse of the input, so if the input is 0, the output must be 1, and vice versa. The gate flips True to False, and False to True.  
    The following illustration shows the symbol and truth table of a NOT-gate. The letter A represents the Input and the letter O represents the output. The term True is equal to 1 in binary code. This logic gate means that if the input is False the statement is True; if the input is True the statement is False (see [Figure 1.10](#c1.xhtml#f1.10) and [Table 1.11](#c1.xhtml#t1.11)).
*   The AND-gate consists of two inputs, A and B, and one output, O. If both inputs are turned On (True or 1), the output will turn On (True or 1). If none of the input or only one of the two inputs is turned On (True or 1), the output will be Off (False or 0). The following is the symbol and truth table of an **AND-gate** (see [Figure 1.11](#c1.xhtml#f1.11) and [Table 1.12](#c1.xhtml#t1.12)).
*   The OR-gate consists of two inputs, A and B, and one output (O). If at least one input is turned On (True or 1), the output will be 1. If both inputs are Off (False or 0), the output will be Off (False or 0). The only time that an OR-gate outputs a 0 (False) is if both inputs are 0. The output is True if either input A or input B is True (see [Figure 1.12](#c1.xhtml#f1.12) and [Table 1.13](#c1.xhtml#t1.13)).

![FIGURE 1.10 NOT-Gate.](images/fig1.10.jpg)

**FIGURE 1.10** NOT-Gate.

**TABLE 1.11** NOT-gate truth tables

  
| Input (A) || Output (O) || Input (A) || Output (O) |
| --- | --- | --- | --- |
| **True** || **False** || 1 || **0** |
| --- | --- | --- | --- |
| **False** || **True** || 0 || **1** |

![FIGURE 1.11 AND-Gate.](images/fig1.11.jpg)

**FIGURE 1.11** AND-Gate.

**TABLE 1.12** AND-gate truth tables

  
| Input (A) || Input (B) || Output (O) || Input (A) || Input (B) || Output (O) |
| --- | --- | --- | --- | --- | --- |
| **False** || False || **False** || 0 || 0 || **0** |
| **False** || True || **False** || 0 || 1 || **0** |
| **True** || False || **False** || 1 || 0 || **0** |
| **True** || True || **True** || 1 || 1 || **1** |

![FIGURE 1.12 OR-Gate.](images/fig1.12.jpg)

**FIGURE 1.12** OR-Gate.

**TABLE 1.13** OR-Gate truth tables

  
| Input (A) || Input (B) || Output (O) || Input (A) || Input (B) || Output (O) |
| --- | --- | --- | --- | --- | --- |
| **False** || False || **False** || 0 || 0 || **0** |
| --- | --- | --- | --- | --- | --- |
| **False** || True || **True** || 0 || 1 || **1** |
| **True** || False || **True** || 1 || 0 || **1** |
| **True** || True || **True** || 1 || 1 || **1** |

Developers use other gates, called derived logic gates**,** made from the combination of two or more of the three basic logic gates. Combining logic gates results in a complicated logical function.^([⁸](#fn8))

When the gate is On, current flows through the transistor. When the gate is Off, current cannot flow. In the same way, the output of a gate may be connected to the inputs of one or several other gates, resulting in outputs that are even more complicated. Most logic gates are made from metal oxide semiconductor field effect transistors (MOSFET), or metal oxide silicon transistors (MOS).^([⁹](#fn9))

![FIGURE 1.13 A typical CPU architecture.](images/fig1.13.jpg)

**FIGURE 1.13** A typical CPU architecture.

### [Processor Types (32-bit Processors vs 64-bit Processors)](#contents.xhtml#re_h-1-15)

In computing architecture, the two main categories of processors are 32-bit (also known as x86) and 64-bit (also known as x64). The number indicates how the hardware and software, such as the central processing unit (CPU), the operating system (OS), and the software, process data. For example, the 32-bit processor can process 4 bytes (4 × 8=32 bits) for each CPU cycle, roughly 4.3 gigabytes of RAM in total. The 64-bit processor can process 8 bytes (8 × 8 = 64 bits) per CPU cycle. Thus, the 64-bit processor can handle twice the amount of data compared to the 32-bit processor.

More specifically, the processor type represents how much data the CPU can load from the main memory (RAM) at a time. The 64-bit processor can calculate data faster, regardless of the processor’s clock speed (cycles per second).

*   A 32-bit processor (2^(32)) can access a limited amount of RAM. For example, using MS Windows, the processor can address 4,294,967,296 bytes of RAM or physical memory (4 GB of RAM or less). Computers built in the 1990s and early 2000s were built and designed specifically for 32-bit processors.
*   64-bit processors (2^(64)), can theoretically access 8,446,744,073,709,551,616 bytes of RAM or physical memory (any amount of physical memory greater than 4 GB of RAM). The operating systems of these processors must support the 64-bit processors. The number of calculations per second a 64-bit processor can achieve influences the speed of the computer and how fast a request for processing data can be completed. With a 64-bit processor, data in memory is accessed faster and programs load much faster into memory. Furthermore, the central processor clock speed determines how quickly the CPU can retrieve and interpret instructions. The CPU speed is measured, in numeric value such as million instructions per second (MIPS), or billion instructions per second (GIPS). CPU instruction rates are measured in Hz (megahertz or gigahertz). This measurement can be useful when evaluating processors made with similar architecture and a general idea of a computer’s speed ([Figure 1.13)](#c1.xhtml#f1.13).

## [1.4 Storage](#contents.xhtml#re_h-1-16)

Data storage is a process for archiving data in a variety of forms. Examples include:

*   Hard Drives (HD), a spinning disk with magnetic coatings and read/write heads in the form of magnetic patterns and Solid-State Drive (SSD) using flash memory. Old storage media, such as floppy disks and tapes also store data magnetically.
*   Removable media, such as Data storage devices, USB flash drives, CompactFlash cards (CF), Secure Digital cards (SD), and Memory Sticks.
*   Electro Optical devices such as Blu-ray, Compact Discs (CD), and Digital Versatile Discs (DVD). These devices use laser light or electromagnetic waves along with a reflective material incorporated into optical discs to read or write binary information. 
*   Another form of storage is the option for remote data storage, such as the Cloud storage model, in which computers store digital data in multiple servers and sometimes in multiple locations around the world.

Different types of data storage perform different functions in a computing environment. Computer memory/storage is classified into two categories:

*   **Volatile Memory** This type of memory loses its data if the power is turned off, for example Random-access memory (RAM).
*   **Non-Volatile Memory** This is a type of memory that holds and saves data even when the power is turned off, for example read-only memory (ROM), software that is rarely changed throughout the life of the system, like Complementary metal–oxide–semiconductor (CMOS) memory that holds the startup program (BIOS) of the computer.

Additionally, in computer architecture, it is important to understand *memory hierarchy.* The term defines the level of computer storage (how the computer handles data) by response time. The *memory hierarchy* consists of

*   **Primary Storage** 
    *   **CPU Registers** : (very fast computer processor memory used to execute programs and operations efficiently).
    *   **Cache Memory**: the fastest system memory that provides data storage of programs and instructions for fast access during operation of the CPU.
*   **Secondary Storage** 
    *   **Main Memory or Random Access Memory (RAM):**
    *   Fast memory used to temporarily hold programs and data, allowing information to be stored and retrieved while the computer is on.
    *   **Virtual Memory**: is extra memory that simulates RAM if more is needed. Virtual memory enables a system to run more than one large application at the same time without running out of memory (RAM) by temporarily transferring data from random access memory (RAM) to disk storage.
    *   **Hard Drives:** Magnetic Disks/SSD
    *   **Optical Devices:** CDs, DVDs and Blu-ray

[Figures 1.14](#c1.xhtml#f1.14) and [1.15](#c1.xhtml#f1.15) display the memory hierarchy and schematic overview of computer architecture.

![FIGURE 1.14 Memory hierarchy.](images/fig1.14.jpg)

**FIGURE 1.14** Memory hierarchy.

![FIGURE 1.15 Schematic overview of computer architecture.](images/fig1.15.jpg)

**FIGURE 1.15** Schematic overview of computer architecture.

### [Compression](#contents.xhtml#re_h-1-17)

Even though computers can store large amounts of data, size still matters. When a file is small, it can be stored, handled, and sent more easily, without taking up much space. Therefore, compression algorithms reduce file size while preserving the data. A compressed file takes up less space and can be sent and received faster ([Figure 1.16](#c1.xhtml#f1.16)). The file compression algorithm locates recurrent sequences and replaces them with shorter representations. Essentially, there are two different kinds of compression, lossy and lossless**.**

![FIGURE 1.16 Compression.](images/fig1.16.jpg)

**FIGURE 1.16** Compression.

### [Lossy Compression](#contents.xhtml#re_h-1-18)

Lossy compression is an algorithm that reduces file size by discarding bits of information that are less important. The process lowers the number of bits in the file, resulting in significantly smaller file size. However, it also affects file quality, and once lost, data cannot be restored. A compressed lossy file has less data than the original file. Lossy compression is most frequently used for files uploaded to the internet, such as audio, video (streaming media), and images. The advantage to lossy compression is that it keeps the file size small, while preserving relatively high-quality multimedia content.

During lossy compression, images and sounds that repeat are removed. After repeated compression and decompression, the file will progressively lose quality, called generation loss. In audio, for instance the algorithm discards frequencies that the human ear is not likely to detect, and also discards sounds of lower volume that the listener cannot hear, while reducing the size of the audio file and maintaining as much audio quality as possible. [Figure 1.17](#c1.xhtml#f1.17) demonstrates Lossless and Lossy compression.

![FIGURE 1.17 Compare Lossy and Lossless compression.](images/fig1.17.jpg)

**FIGURE 1.17** Compare Lossy and Lossless compression.

Computer programs that encode or decode video for viewing are called *codecs.* If you are trying to watch a video, and your computer does not have the right codec, it may prompt you to download it. Some examples of common image and video formats include image compression formats such as JPEG, PNG, video coding standards like MPEG and H.264/AVC, WMA, RealVideo, DivX and audio compression formats like MP3, AAC, and RealAudio.

### [Lossless Compression](#contents.xhtml#re_h-1-19)

Lossless compression algorithms can reconstruct the original data from the compressed data without any quality loss.^([^(10)](#fn10))

## [1.5 Output](#contents.xhtml#re_h-1-20)

### [Pixels](#contents.xhtml#re_h-1-21)

All digital photos, videos, and graphics are made of tiny squares called Pixels**.** A pixel, pel, or picture element, is the smallest unit of a digital image or graphic.^([^(11)](#fn11))

![FIGURE 1.18 Grayscale representation of pixel raster.](images/fig1.18.jpg)

**FIGURE 1.18** Grayscale representation of pixel raster.

However, most images today are not black and white, but are in color. Each individual pixel has an individual pixel value. This value is a single number that describes how bright that pixel is, and what color it should be. Each pixel value consists of three numeric color components, Red, Green, and Blue (RGB), that represent its color. Each red, green, and blue setting defines the intensity of the color as an integer between 0 and 255. Each individual pixel that represents a color image in a computer screen has a pixel value. This value describes how bright the pixel is. We use an integer between 0 and 255 because each pixel can be represented by 8 bits or 1 byte.

When we use the value 0, this means there is no contribution from the specific color. At the opposite end of the range, the value of 255 means the greatest or most saturated contribution of this color. Bear in mind that with 1 byte we can efficiently represent up to 255 different colors. For example, Pink is produced by combining three RGB values: Red (255), Green (105), and Blue (180). The color Aqua is Red (0), Green (255), and Blue (255). This model is used efficiently and just as importantly because it is the closest representation to the way the human eye perceives color.^([^(12)](#fn12))

**TABLE 1.14** Displays the colors in RGB, binary value and Hex

  
| Color || Decimal RGB || Binary RGB || Hex  
RGB  
 |
| --- | --- | --- | --- |
| Black || (0, 0, 0) || 00000000 00000000 00000000 || 00 00 00 |
| --- | --- | --- | --- |
| Blue || (0, 0, 255) || 00000000 00000000 11111111 || 00 00 FF |
| Cyan || (0, 255, 255) || 00000000 11111111 11111111 || 00 FF FF |
| Gray || (128, 128, 128) || 10000000 10000000 10000000 || 80 80 80 |
| Green || (0, 255, 0) || 00000000 11111111 00000000 || 00 FF 00 |
| Magenta || (255, 0, 255) || 11111111 00000000 11111111 || FF 00 FF |
| Red || (255, 0, 0) || 11111111 00000000 00000000 || FF 00 00 |
| White || (255, 255, 255) || 11111111 11111111 11111111 || FF FF FF |
| Yellow || (255, 255, 0) || 11001000 10110100 01111000 || C8 B4 78 |

### [Color Depth](#contents.xhtml#re_h-1-22)

The number of “bits” described in reference to an image is the amount of tonal variation in the image, the variation of lightness or darkness of a color. For example, there are numerous tones of a red color available, but they must be described differently to appear correct. All computers support 16-bit color, 24-bit, and 32-bit color. 

*   In the base powers of two numeral systems 8 bits or 1 byte contains one of 256 numeric values ranging from 0 to 255 because (2⁸) = 256 colors. In other words, the maximum number of colors the graphical function of the computer can display is 256 per channel, specifically 256 shades of green, 256 shades of blue, and 256 shades of red. At 8 bits per channel, an 8-bit RGB image would have total of 24 bits per pixel (8 for red, 8 for green, and 8 for blue).
*   A 16-bit RGB color (or high color) image uses two bytes (8 bits +8 bits) or 256 × 256 = 65,536 tonal values for each color. At 16 bits per channel, the image would have a total of 48 bits per pixel (16 for red, 16 for green, and 16 for blue).
*   A 24-bit RGB color (or true color) image uses 3 bytes (8 bits +8 bits + 8 bits) or 256 ×256 ×256 = 16,777,216 million possible combination of color that can be represented.
*   A 32-bit RGB color supports 16,777,216 colors like the 24-bit. However, the 32-bit has an alpha channel (an additional byte or 8 bits), therefore it can create more realistic gradients, shadows, and transparencies. A 32**\-**bit color (2^(32)) supports 256 ×256 ×256 ×256 = 4,294,967,296 color combinations.
*   A 48-bit RGB color supports (2^(48)) or 281,474,976,710,656 trillion colors). Each RGB channel uses 16 bits per pixel, containing up to 65,536 tone levels, supporting 281,474,976,710,656 trillion colors.

The RGB data value shows how much red, green, and blue intensity levels are combined within an image’s pixels. This greater number of bits per pixel provides higher color depth, resulting in more visually appealing features. Then again, with a higher color depth more system resources are required. [Table 1.15](#c1.xhtml#t1.15) below shows the bit depth and the number of colors available. 

**TABLE 1.15** Displays bit depth and the number of colors available

  
| Bit Depth || Number of Colors Available ||  |
| --- | --- | --- |
| 8-Bit || 256 tonal values for each color (RGB) || (2⁸) |
| --- | --- | --- |
| 16-Bit || 65,536 tonal values for each color (RGB) || (2^(16)) |
| 24-Bit || 16,777,216 tonal values for each color (RGB) || (2^(24)) |
| 32-Bit || 16,777,216 million possible combination of color + Transparency tonal values for each color (RGB) || (2^(32)) |
| 48-Bit || 281,474,976,710,656 trillion tonal values for each color (RGB) || (2^(48)) |

### [Color Models](#contents.xhtml#re_h-1-23)

There are numerous ways to represent colors with numbers. The most well-known color model is RGB. This model is an additive color model, meaning that it combines red, green, and blue light to create the colors we see on computer devices, and on television screens.^([^(13)](#fn13))

![FIGURE 1.19 Example of bit colors.](images/fig1.19.jpg)

**FIGURE 1.19** Example of bit colors.

Another important color model is the CMYK (Cyan, Magenta, Yellow, Black), which is a subtractive color model**.** A subtractive model reduces the light that is reflected, and is used for printing color images. When printers print colors on paper, they work with reflected light, which determines what colors we see. We see objects when they are illuminated by white light, either sunlight or artificial light. We see a white car, because it reflects all the visible wavelengths of light, and we see a black car because it absorbs all the visible wavelengths of light. We see a red color as we see a red apple, because the object absorbs some of the light but reflects the red.

To be able to do this, computers can use the opposing subtractive primaries of RGB, which are cyan, magenta, and yellow. “Cyan is directly opposed to red; magenta is the opposite of green; and yellow is the opposite of blue.”^([^(14)](#fn14))

### [Screen Resolution](#contents.xhtml#re_h-1-24)

The quality of the graphics card and the display monitor dictate the quantity, size, and color of the pixel display resolution. Computer-based images contain a matrix of thousands or millions of pixels. The screen generates the image you see by altering the colors of these tiny square pixels. The screen resolution depends upon how many pixels the screen can display horizontally and vertically. Computer screens of different sizes can still have the same screen resolution. A computer screen with a higher resolution (more pixels), will display an image more sharply. For example, a computer display resolution of 3,840 × 2,160, means that we see 3,840 pixels horizontally and 2,160 vertical pixels vertically (written as width × height). This resolution is commonly known as 4K Ultra HD, and refers to horizontal resolutions of around 4,000 pixels, which is exactly twice as many pixel rows and columns as a High Definition Television 1080p (1920 ×1080 pixels). However, the higher resolution also means that icons and text will look smaller.

In addition to screen resolution, brightness, color representation, and refresh rates are also very important. The refresh rate, or vertical refresh rate, is the number of times per second, measured in Hertz or Hz, that the monitor updates the screen with new information. Higher numbers are equivalent to better and less choppy images. 

## [1.6 Beyond Conventional Computing](#contents.xhtml#re_h-1-25)

### [Quantum Computing Is Poised to Change Everything](#contents.xhtml#re_h-1-26)

In 1981, Richard Feynman introduced the idea of a computer that can harness the power of quantum mechanics.^([^(15)](#fn15))

Earlier in this chapter we discussed how conventional computation works. While in conventional computing data is captured in bits**,** in quantum computing we use *Qubits***.** The term stands for Quantum Bit and is the smallest unit of quantum information.

In conventional computing, two bits can have four patterns (00, 01, 10, 11). In quantum computing, two qubits can have the same four patterns, but the qubits can represent and use all four at the same time. When we add more bits to a conventional computer, the computer still works with one state at a time. When we add qubits, because so many more computations happen simultaneously, the power of the quantum computer is exponentially greater.

In physics, we call this phenomenon *superposition*, and it describes the ability of a quantum system to be in several states at the same time. In other words, the state can exist in a superposition of 0s and 1s. A byte can be not merely a 0 or a 1, but a superposition of both states. If one qubit can be in a superposition of two states, then two qubits can be in a superposition of four states and three qubits of eight states.

For example, we say that a coin can have two positions, heads (0) or tails (1). In conventional computation, only one of those positions is possible. However, in quantum computation it would be as if the coin could be in both positions at once.

Another example involves using a computer program to crack a password. The conventional computer program will try each individual combination or potential password sequentially until it finds the correct answer. The quantum computer will configure this problem differently. The qubits will be in superposition of all the possible states or all possible password configurations, and by using interference, will amplify some answers and cancel others, finding the correct password much more quickly.

A third example involves using mapping software like Google Maps to go from point A to point B. Normal map computation looks at all the possible paths between A and B, one at a time, to determine the fastest route. A quantum computer will try every possible path between two points simultaneously and will determine the best route in a fraction of the time of a conventional computer. 

A larger number of qubits means that the number of states grows exponentially, creating millions of possibilities, and making possible solutions that are far beyond those of conventional computers. This has practical implications in scientific experiments and simulations, and as part of the development of new drugs and materials.

Even when fully developed, quantum computers will never completely replace conventional computers. However, this new type of computer will solve problems that would take a conventional computer thousands of years to solve. Quantum computers will never stream video from Netflix, nor will they play videos on the Web. Both conventional and quantum computing will coexist, serving different purposes.

The conventional computer may attempt to solve a difficult equation or a problem, calculating in bits and bytes. However, if the problem is too difficult, it may fail. The quantum computer can explore these exponential possibilities much more easily, since its strengths are almost limitless.

If we have “n” qubits, you can simultaneously represent (2^n) states. Three qubits (2³) = 8 states at the same time; 4 qubits (2⁴) = 16; and 64 qubits (2^(64)) = 18,446,744,073,709,600,000 probabilities. The conventional computer can represent this huge number (2^(64)) of states, but with only one state at a time. To cycle through all these combinations would take a conventional computer around 400 years, but the quantum computer will explore these much faster, as Google’s quantum research has demonstrated.^([^(16)](#fn16))

Quantum computers could boost the expansion of new advances in science, treatments, and medications, increase the speed of machine learning and artificial intelligence, and help in the discovery of better building materials for more efficient and safer structures.

However, we are not ready to abandon the conventional computer. Quantum computing is still in the experimental stage and will coexist with conventional computers in the foreseeable future.

## [1.7 A Brief History of Computing Devices](#contents.xhtml#re_h-1-27)

The following is a brief history, highlighting the most significant events in computing history from its beginning to the present.

The history of computers began with the invention of a calculating tool called the *abacus* ([Figure 1.20](#c1.xhtml#f1.20)). This first mechanical calculating device worked by manually sliding counters on rods. The exact origin of the abacus is still unknown. While some researchers credit the Babylonians around 2400 BC,^([^(17)](#fn17))

![FIGURE 1.20 Ancient abacus calculation device. Courtesy of Shutterstock.](images/fig1.20.jpg)

**FIGURE 1.20** Ancient abacus calculation device. Courtesy of Shutterstock.

In 1901, scientists found an important discovery in a shipwreck on the island of Antikythera, in Greece ([Figure 1.21](#c1.xhtml#f1.21)). Invented around the second century BC, the Antikythera Mechanism is known as the world’s first mechanical computer. This analogue computer was built by the ancient Greeks, who used it to predict the time and color of lunar and solar eclipses with impressive accuracy.^([^(18)](#fn18))

![FIGURE 1.21 Antikythera Mechanism. Courtesy of Shutterstock.](images/fig1.21.jpg)

**FIGURE 1.21** Antikythera Mechanism. Courtesy of Shutterstock.

During the 4th century BC (428–347), the Greek mathematician *Archytas of Tarentum* designed a mechanical bird called *The Pigeon*, which moved by steam^([^(19)](#fn19))

![FIGURE 1.22 Mechanical bird. Courtesy of Shutterstock](images/fig1.22.jpg)

**FIGURE 1.22** Mechanical bird. Courtesy of Shutterstock

![FIGURE 1.23 Siphon float and constant flow of Heron of Alexandria. Courtesy of Shutterstock.](images/fig1.23.jpg)

**FIGURE 1.23** Siphon float and constant flow of Heron of Alexandria. Courtesy of Shutterstock.

Early modern examples of mechanical computers include the calculators credited to mathematician and physicist, Blaise Pascal and mathematician Gottfried Wilhelm (von) Leibniz in the 17th century.^([^(20)](#fn20))

In 1822, Charles Babbage announced the invention of his calculating machine to the Royal Astronomical Society, in a paper titled “Note on the application of machinery to the computation of astronomical and mathematical tables.” Babbage’s calculating machine, or *difference engine*, used the decimal number system and was operated by cranking a handle^([^(21)](#fn21))

![FIGURES 1.24 Small part of Babbage’s mechanical calculating engine. Courtesy of Shutterstock.](images/fig1.24.jpg)

**FIGURES 1.24** Small part of Babbage’s mechanical calculating engine. Courtesy of Shutterstock.

![FIGURES 1.25 The thermionic valve.](images/fig1.25.jpg)

**FIGURES 1.25** The thermionic valve.

After Charles Babbage’s Analytical Engine, one of the most important innovations in computing came from John Atanasoff of Iowa State University ([Figure 1.26](#c1.xhtml#f1.26)). In 1939, along with Clifford Berry, Atanasoff built the Atanasoff-Berry Computer (ABC), the first electronic, digital, general-purpose device that used vacuum tubes.^([^(22)](#fn22))

![FIGURE 1.26 Atanasoff-Berry Computer at Durham Center, Iowa State University.](images/fig1.26.jpg)

**FIGURE 1.26** Atanasoff-Berry Computer at Durham Center, Iowa State University.

> The ABC was the first linear algebra computer, and its 1940 performance is very close to what Moore’s law predicts (the law is described later in this chapter). World War II prevented its innovations from being published and credited to Atanasoff and Berry.^([^(23)](#fn23))

Another innovation, the Z3 Computer, was built in Germany. Designed by *Konrad Zuse* in 1941, this binary machine was the first programmable, controlled, fully automatic digital computer and could store 64 floating-point numbers in binary memory. The original Z3 was destroyed during World War II^([^(24)](#fn24))

![FIGURE 1.27 A replica of the very first electronic computer (Z3) being built by Konrad Zuse. Courtesy of Shutterstock.](images/fig1.27.jpg)

**FIGURE 1.27** A replica of the very first electronic computer (Z3) being built by Konrad Zuse. Courtesy of Shutterstock.

Between 1939 and 1945, the British Colossus vacuum tube computing machine was one of the most important tools used against Germany during World War II. Analysts used this computer to break German war codes at England’s Bletchley Park. This machine was the first fully functioning electronic digital computer.

In 1946, the American Electronic Numerical Integrator and Computer (ENIAC) first used high-speed vacuum tubes and operated faster than any previous machine ([Figure 1.28](#c1.xhtml#f1.28)). Mauchly and Eckert built ENIAC at the University of Pennsylvania’s Moore School of Electrical Engineering.^([^(25)](#fn25))

![FIGURES 1.28 The ENIAC computer. Courtesy of the Library of Congress.](images/fig1.28.jpg)

**FIGURES 1.28** The ENIAC computer. Courtesy of the Library of Congress.

![FIGURE 1.29 The historical timeline of the beginnings of modern computer technology.](images/fig1.29.jpg)

**FIGURE 1.29** The historical timeline of the beginnings of modern computer technology.

In the 1950s and 1960s, Remington Rand Inc. introduced the Eckert-Mauchly Computer Corporation’s ERA 1101, or UNIVAC 1101, to the United States*.* This was the first computer commercially available, and the first customer was the U.S. government ([Figure 1.30](#c1.xhtml#f1.30)). The ERA’s magnetic drums used magnetic tapes and could hold up to two million bits, or 65,000 30-bit words. Its access time ranged from 8 to 64 milliseconds.^([^(26)](#fn26))

![FIGURE 1.30 ERA 1103 UNIVAC 2 Calculating Machine. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.30.jpg)

**FIGURE 1.30** ERA 1103 UNIVAC 2 Calculating Machine. Photograph from National Aeronautics and Space Administration (NASA).

In 1958, Jack St. Clair Kilby**,** an electrical engineer from Texas Instruments, manufactured the first integrated circuit or semiconductor chip, IC, also called a microchip***.***

The microchip is a group of miniature transistors joined in microscopic form during the manufacturing process. A modern computer chip, or silicon wafer, can hold billions of transistors.^([^(27)](#fn27))

For his invention, Jack St. Clair Kilby was awarded the Nobel Prize in Physics in the year 2000.^([^(28)](#fn28))

In 1964, International Business Machines (IBM) introduced the IBM System/360***.*** It was intended for business and science uses. IBM offered the 360 in a family of six models, small to large, that all used the same programs, thereby saving the customers money. By 1971, IBM’s net earnings exceeded 1 billion US dollars. The company became a leader in computer production and was unable to keep up with demand^([^(29)](#fn29))

![FIGURE 1.31 The IBM 7090 Data Processing System at Data Processing and Data Reduction at the NASA Ames Research Center, c1963. Photograph from National Aeronautics and Space Administration (NASA).](images/fig1.31.jpg)

**FIGURE 1.31** The IBM 7090 Data Processing System at Data Processing and Data Reduction at the NASA Ames Research Center, c1963. Photograph from National Aeronautics and Space Administration (NASA).

In 1965, Gordon E. Moore, hypothesized that the number of components on an integrated circuit would double every two years for the next 10 years. This hypothesis became Moore’s Law, predicting that as computation would increase in power, its cost would decrease exponentially. Moore’s Law is the barometer for the electronics industry, and a catalyst for innovation. Moore is the co-founder of the Intel Corporation.^([^(30)](#fn30))

As of 1969, in addition to continued developments in machinery, the ARPANET (Advanced Research Projects Agency network) emerged as the precursor of the Internet**.** The ARPANET began as a military computer network, using early packet-switching technology. It was the first network to implement the Transmission Control Protocol and Internet Protocol TCP/IP suite for more effective transmission over this early Internet ([Figure 1.32](#c1.xhtml#f1.32)).

![FIGURE 1.32 A map of the ARPANET in December 1970. Courtesy of DARPA.](images/fig1.32.jpg)

**FIGURE 1.32** A map of the ARPANET in December 1970. Courtesy of DARPA.

The first personal computer was Kenbak-1. It sold for $750 in *Scientific American* magazine in 1971. The Kenbak-1 did not sell well, but it did increase public awareness of home-based computers^([^(31)](#fn31))

![FIGURE 1.33 Kenbak-1. Photo courtesy of Mr. John Blankenbaker](images/fig1.33.jpg)

**FIGURE 1.33** Kenbak-1. Photo courtesy of Mr. John Blankenbaker

In 1972, Ray Tomlinson invented the e-mail system we know today. While working as an ARPANET contractor, Tomlinson selected the @ symbol *to* structure the address of a single user and its host (name-of-the-user@name-of-the-computer).^([^(32)](#fn32))

In 1976, Steve Jobs and Steve Wozniak founded the Apple Computer Company. In 1977, the Apple II revolutionized personal computers and created a device we easily recognize today. The Apple II was the first successful mass-produced microcomputer aimed at the general public. It had a plastic case and had the ability to display color graphics. It featured expandable RAM, 4K or 8K, the BASIC programming language, and included two game paddles, color graphics, and a demo cassette for $1,298 USD, $5,603 in today’s dollars ([Figure 1.34](#c1.xhtml#f1.34)).

![FIGURE 1.34 The Apple II computer. Courtesy of Shutterstock.](images/fig1.34.jpg)

**FIGURE 1.34** The Apple II computer. Courtesy of Shutterstock.

In 1981, IBM introduced the IBM Personal Computer, or IBM PC. It used the 8088 Intel microprocessor, and its operating system was PC-DOS, licensed from Microsoft. The IBM PC was so successful that “By 1984, IBM replaced Apple as the number one supplier of microcomputers. Apple had 26% of the PC business. IBM’s share had grown to 41%.”^([^(33)](#fn33))

![FIGURE 1.35 The IBM PC. Courtesy of Shutterstock.](images/fig1.35.jpg)

**FIGURE 1.35** The IBM PC. Courtesy of Shutterstock.

In the same year, Adam Osborne created the Osborne 1, the first commercially available portable computer, weighing 24.5 pounds and costing $1,795^([^(34)](#fn34))

![FIGURE 1.36 The Osborne 1.](images/fig1.36.jpg)

**FIGURE 1.36** The Osborne 1.

In 1984, Apple introduced the Macintosh***,*** which included a Graphical User Interface (GUI) and a much faster processor, the Motorola 68000 chip. The Macintosh included a monitor, keyboard, mouse, and a floppy drive that took 400 kB 3.5″ inch disks. The price for the Macintosh was $2,495^([^(35)](#fn35))

![FIGURE 1.37 The Macintosh. Courtesy of Shutterstock.](images/fig1.37.jpg)

**FIGURE 1.37** The Macintosh. Courtesy of Shutterstock.

In 1991, Tim Berners Lee**,** a scientist at the CERN laboratory in Switzerland invented the World Wide Web (WWW).^([^(36)](#fn36))

Bill Gates and Microsoft Corp released Windows 3.1 in 1992.^([^(37)](#fn37))

In 1995, the US Federal Networking Council (FNC) passed a resolution to define the Internet, in consultation with members of the internet and intellectual property rights communities.

> Internet refers to the global information system that (a) is logically linked together by a globally unique address space, based on the Internet Protocol (IP) or its subsequent extensions/follow-ons; (b) is able to support communications using the Transmission Control Protocol/Internet Protocol (TCP/IP) suite or its subsequent extensions/follow-ons, and/or other IP-compatible protocols; and (c) provides, uses or makes accessible, either publicly or privately, high level services layered on the communications and related infrastructure described herein.^([^(38)](#fn38))

By 1995, Internet service providers (ISPs), such as AOL, MCI, Sprint, and UUNET, began offering their services to large numbers of customers.^([^(39)](#fn39))

Since the beginning of the new millennium, the global positioning system (GPS) has been available to civilians. Previously available only to the military, GPS^([^(40)](#fn40))

In the early 2000s, the dotcom or internet bubble burst after the U.S. technology stock market over-invested in internet-based companies.^([^(41)](#fn41))

At the same time, social media platforms started attracting attention and gaining momentum. In 2003, MySpace and LinkedIn were launched, Facebook appeared in 2004, and YouTube in 2005.^([^(42)](#fn42))

In 2004, Google was the first major web company to go public.^([^(43)](#fn43))

In 2006, the commercialization of Cloud computing began when Amazon introduced its Web Service.^([^(44)](#fn44))

![FIGURE 1.38 The iPhone c2007. Courtesy of Shutterstock.](images/fig1.38.jpg)

**FIGURE 1.38** The iPhone c2007. Courtesy of Shutterstock.

As technology becomes smaller, faster, and cheaper, people want to take their mobile devices with them. The Internet has infiltrated all technologies today, resulting in the growth of the Internet of Things (IoT). Today, we can connect almost every device we purchase to the internet and to other devices. Smart locks, Bluetooth trackers, smart home devices, machine-learning devices like Amazon Echo, Apple Homepod, and Google Home can all now connect to the internet and be networked to other devices. These devices can and do distribute information anywhere in the world, despite security and privacy concerns.

In 2012, Cisco Systems introduced Fog computing,^([^(45)](#fn45))

In computer evolution, we have witnessed major advances in Artificial Intelligence (AI), Machine Learning (ML), and Robotic process automation. The field of Artificial Intelligence was founded in the 1950s, and the term “AI” was created by John McCarthy in 1956 at the Dartmouth Conference.^([^(46)](#fn46))

According to John McCarthy, AI “is the science and engineering of making intelligent machines.”^([^(47)](#fn47))

Currently, what we have is termed Machine learning (ML), a division of AI. ML is a computer algorithm that teaches computers to learn by performing data analysis, identifying patterns, and making decisions based on what it has learned. The goal of ML is to understand the formation of data, and to organize that data into models so it may be comprehended and used by humans.

Some examples of first-generation AI or ML technology are Apple’s Siri, Amazon’s Alexa, IBM Watson, Amazon Go, Music and Media streaming services such as Spotify, Netflix, and YouTube, Social Media feeds, Smart Home devices, and Google and Apple Maps. These applications use ML technology to classify queries and requests using spoken human language, and then to respond with answers from a database. ML utilizes neural network algorithms to model the data to provide the user with a sense that the computer actually understands the query – hence the belief in AI is established and strengthened.

In 2015, Google released an open source machine learning or deep learning tool called TensorFlow.^([^(48)](#fn48))

One example of how TensorFlow is used is in the detection of diabetic retinopathy. It utilizes a database of images provided and sorted by ophthalmologists. TensorFlow compares the images in its database with a patient’s image and can predict whether the patient’s diabetes has damaged the retina. Other examples include voice and sound recognition, voice search, sentiment analysis in customer relationship dialogues, text-based applications like Google Translate, image recognition, and video detection.

Using machine learning, computers can employ a command line interface and move into Neural Networks***.*** “An artificial neural network (ANN) is an interconnected group of artificial neurons simulating the thinking process. One can consider an ANN as a ‘magical’ black box trained to achieve expected intelligent processes, alongside the input and output information stream.”^([^(49)](#fn49))

To understand this, imagine taking a train for the first time and watching the train make every stop. The next time you take the train to the same destination, you might take the express train and go directly or close to the destination without making the local stops. Like the human brain, the Neural Network requires data to learn. The more data, the more precise the results will become. Gradually the algorithm becomes more efficient and makes connections that are more direct with fewer mistakes. To train Neural Networks, we need to transfer information to the dataset for the algorithm to learn the correlation between labels and raw data. This process is called supervised learning***.*** After the algorithm understands the raw data, it decides which label to assign to new data based on the pattern. Following are some examples in our everyday life:

*   Face identification and facial expression recognition (happiness, sadness, and anger from face images)
*   Gesture recognition system
*   Recognition and understanding of images and scenes
*   Spam Classification (classifying text as spam or fraudulent)
*   Voice-identification systems (detect voices, transcribe speech to text, voice cloning, mimicking the voices of friends, enemies, and celebrities

When it comes to common sense, reasoning, and human/animal interaction/behavior, AI is still in its infancy. Nonetheless, every piece of software can claim some level of AI technology based on a predefined algorithm that responds to a desired input by a programmer, and/or automatically adjusts to a user’s behavior.

Many believe that Artificial Intelligence is misused and mischaracterized in our data-driven society. As we see in movies like “The Terminator,” HBO’s series “Westworld,” and books and prophecies by the Singularity evangelist Ray Kurzweil (“The Singularity is Near”^([^(50)](#fn50))

Others strongly disagree, saying that we are not even close to the hypothesis described in Singularity, and will not ever get closer, since we do not fully understand the structure of the brain and how it responds to everyday changes.^([^(51)](#fn51))

Is the human mind able to build a cognitive computer simulating human behavior or reasoning? No one knows the answer – and no one knows how computers will evolve in the future.

[Table 1.16](#c1.xhtml#t1.16) summarizes major technological advancements in computing since 2000, and [Table 1.17](#c1.xhtml#t1.17) lists some of the most important definitions in computer science.

 **TABLE 1.16** Technological advances in computing since 2000 

 
| Major Technological Advancements in Computing Since 2000  |
| --- |
| 2000 || USB Flash drives introduced; Global Positioning System (GPS) goes mainstream. |
| --- | --- |
| 2001 || Mac OS X and Microsoft XP operating systems released; iTunes released. |
| 2002 || Supercomputer Earth Simulator is a massive, vector-based system that costs nearly 60 billion yen (roughly $600 million at the time). |
| 2003 || Blu-ray released; The Computer Science and Artificial Intelligence Laboratory (CSAIL) at MIT is formed by the merger of the Laboratory for Computer Science and the Artificial Intelligence Laboratory; MySpace founded; PowerMac G5 tower computer released |
| 2004 || Google is the first major Web company to float a publicly traded stock; “Web 2.0” brings back Interactivity. |
| 2005 || Lenovo acquires IBM's PC business; YouTube channel founded. |
| 2006 || “The Cloud”: Computer utilities return; WikiLeaks established; Hulu founded; Twitter & Amazon introduce the Web Service (cloud computing); FAA issued commercial drone permit. |
| 2007 || Dropbox founded; First 1 TB (terabyte) hard disk drive (HDD); Apple’s iPhone introduced; Amazon Kindle released |
| 2008 || “Satoshi Nakamoto,” likely a pseudonym, publishes Bitcoin. MacBook Air is released; Android’s OS introduced; |
| 2009 || Vendors announce cloud-based network-attached storage solutions for online backup; Roadrunner, IBM's supercomputer, is completed; Nakamoto 'mines' the first Bitcoins in January 2009, and a year later, a user orders two pizzas with them. Bitcoins’ value explodes in November 2013 before a gradual devaluation. |
| 2010 || Angry Birds becomes top-selling mobile game; China’s Tianhe supercomputers are operational; IBM’s Watson and Brad Rutter appear on Jeopardy! Apple iPad is released |
| 2011 || Arab Spring protests spread by social media; The Nest’s Learning Thermostat is an early product made for the emerging “Internet of Things”; Siri is introduced as a built-in feature with the Apple iPhone 4S smartphone; Passing of Steve Jobs. |
| 2012 || Facebook acquires Instagram; Raspberry Pi, a credit-card-size single board computer, is released as a tool to promote science education |
| 2013 || Amazon announces that the company is considering using drones.; Former CIA employee and NSA contractor Edward Snowden copies hundreds of thousands of classified documents; Microsoft Office 365 is unveiled; Microsoft introduces Xbox One; Sony releases PlayStation 4 |
| 2014 || Apple Pay mobile payment system is introduced; HTML 5 replaces HTML 4 |
| 2015 || Apple Watch is released |
| 2016 || In March, 2016, Amazon introduces the first version of the Amazon Echo Dot;Microsoft announces agreement to acquire LinkedIn for $26.2 billion. |
| 2017 || Open AI became the first AI to defeat the world's best DotA 2 player Danil "Dendi" Ishutin in a 1v1 game. The AI learned to play the game by playing against itself in less than a month with little coaching from humans. |
| 2018 || Google introduced the Google Pay service for all Android and iOS devices on January 8, 2018.; Stephen Hawking passed away; Microsoft began rolling out the Windows 10 Fall Creators Update on Oct. 17, 2017; Paul Allen passed away |
| 2019 || Huawei banned from doing business with U.S. companies due to the trade war with China. |
| 2020 || Machine Learning and AI, Robotic process automation, Blockchain technology, Virtual Reality (VR) & Internet of Things (IoT). |

**TABLE 1.17** Glossary of Common Terms in Computer Science

  
| Name || Computer Definitions |
| --- | --- |
| AI || Artificial Intelligence |
| --- | --- |
| Application (App) || A software program designed to execute a sequence of instructions used to accomplish a certain task, or an operation in a computing device. |
| ASCII || American Standard Code for Information Interchange. A character-encoding standard for electronic communication |
| Bluetooth || A short-range wireless standard for exchanging data between computing devices using Ultra High Frequency (UHF) radio signals. Uses less power, easy to use, and costs less to implement than Wi-Fi technology |
| Binary || A system based on powers of the two numeral system (2^n), which uses only two numbers: 0 and 1. |
| Bit (binary digit) || The smallest unit of digital information in computing. |
| Bytes || A larger unit of digital information. A byte is a collection of 8 bits. |
| BIOS || Abbreviation for Basic Input Output System. It performs the booting process (starts up the computer). |
| CMOS || Complementary Metal Oxide Semiconductor is a technology for building integrated circuits, including microprocessors. |
| CPU || Central Processing Unit, or main processor of the computer. Also identified as the computer’s Chip. |
| Multi-Core CPU || A CPU with two or more separate processing units. The parts of the processor that do parallel processing or multitasking tasks at a given time. |
| Firmware || A small piece of software that supports a specific piece of hardware. Examples include BIOS, keyboards, hard drive, or graphic card, etc. |
| GUI || Graphical User Interface. The screen(s) that enable users to interact with a computing device using menus, icons, and graphics. |
| Integrated Circuit || A group of miniature transistors joined microscopically. |
| Interface || The methods which describe the exchange of information between two or more separate components of a computer system or between a user and a computer. |
| ML || Machine Learning, a division of AI. ML is a computer algorithm that teaches computers to learn by performing data analysis, identifying patterns, and making decisions based on what has been learned. |
| Motherboard || A circuit board that comprises the principal components of a computer. |
| Non-Volatile || Retains stored information even when not powered. Examples include flash memory, hard drives, magnetic tape and optical discs. |
| Nybble (Nibble) || 4 bits or half a byte. |
| OS || Operating System. The main system software that interfaces and controls software and hardware on any computing device. Examples include Windows and Linux. |
| Power Supply || Hardware that converts alternating current (AC) to low-voltage direct current (DC) for the internal components of the computer. It also regulates voltage to limit overheating. |
| Quantum Computing || Quantum computing makes direct use of quantum mechanics to distribute better processing power and more intelligence in computation. |
| RAM || Random Access Memory. Temporarily stores data while the CPU is performing other tasks. With more RAM on the computer, the CPU can read less data from the external or secondary memory, allowing the computer to work with more information. |
| Software || A generic term for a computer program in a computer or other device. |
| Transistor || The transistor is an amplifier or a switch (On/Off) that controls an electrical current flow. |
| Utility || A utility is a piece of software in the computer that analyzes, configures, monitors, and maintains it. Usually comes installed with the OS. |
| Volatile Memory || Requires power to maintain the stored information. Example: RAM |
| Wi-Fi or Wireless Fidelity || A technology that utilizes radio waves to send and receive data to provide wireless local area networking (WLAN). This wireless technology is based on the IEEE 802.11 group of standards. |

 

## [1.8 Conclusion](#contents.xhtml#re_h-1-29)

The invention of the computer represents the desire of humans to explore, explain, and manipulate the environment. From finger counting to Aristotle’s mathematical logic, to Boolean algebra, logic gates, machine learning, and AI, the human brain continues to innovate.

Typical programming relies on simple statements (if A, then B). Nothing that goes into a computer is processed as entered, but as a code. A computer can do a billion things in a second but is still unable to imitate the complexity of intelligent human behavior. For the present, a computer is still just a machine without intellect.

As AI and Machine Learning progress, computing technology will continue to change our lives. The computer is one of the most powerful human innovations in history, and our lives are linked inseparably to its technologies. It is possible that some time in the future machine intelligence will “simply outlast” human intelligence. Maybe! However, for the moment we enthusiastically and cautiously enjoy the ride of technological advancements, which can be both positive and negative.

## [1.9 Key Words](#contents.xhtml#re_h-1-30)

 
| Abacus || Integrated Circuit |
| --- | --- |
| Artificial Intelligence (AI) || Internet of Things (IoT) |
| Application (App) || Logic Gates |
| Binary Data || Lossless compression |
| Bit || Lossy Compression |
| Bluetooth || Machine Learning (ML) |
| Boolean Algebra || Mathematical Logic |
| Byte || Pixels |
| Central Processing Unit (CPU) || Processor |
| Color Depth || Quantum Computing |
| Computer || Screen Resolution |
| Decimals || Storage |
| Graphics Card || Transistor |
| Hard Drive || Vacuum Tube. |
| Hexadecimals ||   |

# [Chapter 2 Cybercrime in a Data-Driven and Techno-Centric Society](#contents.xhtml#re_c2)

DOI: [10.4324/9780429318726-2](https://doi.org/10.4324/9780429318726-2)

## [Objectives](#contents.xhtml#re_h-2-1)

After completing this chapter, the student will be able to:

*   Understand the evolution and phases of cybercrime.
*   Recognize cybercrime weapons.
*   Explain the motives that make cybercrime attractive.
*   Recognize the categories of cybercrime.
*   Understand the cybercriminal.
*   Discuss the Internet of Things (IoT) and cybercrime.
*   Recognize the connections among Cybercrime, Machine Learning and Artificial Intelligence (AI).
*   Understand the costs of cybercrime and the role of cryptocurrency.
*   Understand online Child Sexual Abuse and Exploitation (CSAE).
*   Explain state-sponsored and cyber warfare.

## [2.1 Cybercrime and the Cybercriminal](#contents.xhtml#re_h-2-3)

It is hard to imagine our world without the Internet. Television and radio may shorten the distances between us or let us imagine the world from afar, but the Internet has changed our planet into a virtual global village with no boundaries.

New technologies and the Internet have transformed the way we communicate, how we access information, how we form opinions, and how we find and enjoy entertainment. It has changed the shopping experience and has altered the face of crime. While there are drawbacks to the techno-centric world of the 21st century, the Internet is generally seen as a powerful space that we would never choose to give up.

As the Internet and computing technologies continue to evolve, criminals have found ways to use these technologies to commit unlawful acts, giving rise to massive cybercriminal activity. Cybercrime, a relatively new type of crime, is committed using a computing device and the Internet. While in the 20th-century oil was our most valuable commodity, today, the most precious commodity is data,^([^(52)](#fn52))

As [Figure 2.1](#c2.xhtml#f2.1) illustrates the most common motivations for cybercrime are:

![FIGURE 2.1 Motives for Cybercrime.](images/fig2.1.jpg)

**FIGURE 2.1** Motives for Cybercrime.

*   **Financial gain:** skimming bankcard numbers and PINs, payment system fraud (PayPal, Bitcoin), identity theft, and use of tools like malware, ransomware, and phishing
*   **Espionage or spying:** accessing information/data from political entities, the military, government, industries, manufacturers, and corporations
*   **Ideology:** hacktivism, disagreement over politics or values, cyberterrorism, cyber warfare, or the desire to evoke fear
*   **Harassment, revenge, and fun:** seeking of revenge, fun, fame, thrill-seeking, recognition, or to control, manipulate, bully, or stalk.

Today, financial cybercrime is the biggest threat to companies and organizations. Cybercriminals may seek access to valuable data to sell them on the Dark Web. These data are personal, financial, and medical, as well as purchase-based consumer and social media data. The cybercriminal utilizes anonymous communication devices, such as The Onion Router (Tor) and OpenBazaar, an open source e-commerce protocol that uses cryptocurrency to hide illegal transactions.

However, not all cybercriminals seek financial gain. An Internet activist, or hacktivist, is a person who uses unauthorized data for political and subversive goals. Hacktivism began as a protest on the internet to effect change. A hacktivist needs to rebel and to spread an ideology. Some of the most infamous examples of hacktivism are the groups Anonymous, Lulz Security (LulzSec), Ghost Security Group (GhostSec) and WikiLeaks. The ultimate purpose of hacktivism is to spread a political or social message and cause a social change. In addition, the hacker becomes part of a community providing each member with emotional, political, or religious support, and a shared desire for power. [Table 2.1](#c2.xhtml#t2.1) summarizes cybercrime weapons:

**TABLE 2.1** A Summary of Cybercrime Weapons

  
| **Crime-as-a-Service (CaaS):** An on-demand marketplace where one can purchase cybercrime services and attack tools like exploit kits, ransomware, worms, and phishing tools. Found on the Dark Web |
| --- |
| **Cyberterrorism:** The use of the Internet as a tool to promote propaganda, cause fear, provide training, and disseminate advice on making bombs, promoting radicalization and planning attacks. Cyberterrorists use hacking tools to target critical social media infrastructure, with the intent of provoking fear, weakening government and diminishing social cohesion. |
| **Cyberwarfare:** A nation-state-sponsored cyber-attack on another nation-state to harm, alter, destroy, or steal information, or to conduct espionage and sabotage a computer network. Examples include distribution of malware that destroys files, and social media attacks that distribute false information and manipulate people to change their opinions and loyalties. |
| **Cyberbullying or Cyber Harassment:** A form of intimidation or mistreatment of an individual, targeting the victim online and sometimes extorting money. |
| **Denial of service (DoS):** An attack that occurs when a hacker makes computer resources inaccessible to its users by flooding the network with information, causing it to crash. DoS uses only a single computer to carry out the attack. |
| **Distributed denial-of-service (DDoS):** These more complex attacks occur when a hacker exploits security vulnerability to take control of multiple computers and turns them into botnets (zombie computers), and then uses the botnets to attack other computers or networks. DDoS attacks frequently extend worldwide. |
| **Fraud and financial crime:** A form of theft involving funds or property. A cybercriminal pretends to be a lawful merchant and advertises nonexistent goods and services, collecting money or property. Crimes include online purchase scams, auction fraud, mortgage fraud, sales fraud, embezzlement, Ponzi and pyramid schemes, credit and debit card fraud, money laundering and health care fraud. |
| **Hacker:** An individual accessing a computer device or computer system without the user’s knowledge and authorization. |
| **Hacktivist:** An individual hacker driven by an ideology or politically inspired reason. |
| **Identity theft:** A broad range of crimes, including theft of personal or medical information, accessing a victim’s bank accounts, credit cards, tax refunds, or impersonating another individual when apprehended for a crime. Personal data may be stolen and then sold to marketing firms worldwide. These data purchases can cost the marketing firms far less than traditional marketing research. |
| **Malware:** The term Malware is short for ‘malicious software’, and consists of computer viruses, worms, Trojan horses, ransomware, spyware, and all other types of destructive software or code. These impair or infiltrate a device or system without the user’s knowledge to execute specific damage. |
| **Phishing:** Phishing is a deceitful attempt to gather personal information such as usernames, passwords, and credit card information by using deceptive e-mails masked as legitimate. |
| **Ransomware:** Use of malicious software to extort victims by locking and encrypting their data unless the victim pays a ransom in cryptocurrency. Even after payment the data may not be restored. |
| **Spam:** Any unwelcome electronic message sent in bulk. Spam may be an advertising campaign or a malicious worm or virus with a primary mission to infect. |
| **Worm:** A type of malware that duplicates itself and spreads from computer to computer using removable media, e-mail attachments, or by downloading infected files from the Internet. |

## [2.2 The Origin and Definition of Cybercrime – It’s the Data, Always the Data](#contents.xhtml#re_h-2-4)

During the 1992 presidential campaign, James Carville, a campaign strategist of Bill Clinton, said repeatedly “It's the economy, stupid.” He intended to remind the staff to keep focused on the issues.^([^(53)](#fn53))

Today, data, information, hacking tools, and simple instructions for using them are available to anyone interested in cybercrime, with or without prior computer training. Cybercriminals make significant amounts of money by selling or trading data. These data, whether personal, medical, or financial, are the currency of a thriving underworld industry.

The data does not always have to be real. In the 2016 and 2020 U.S. presidential elections, falsified information was used as a tool of influence, in cyber attacks against the country’s critical infrastructure. ^([^(54)](#fn54))

In the law, cybercrime is not distinct from other crimes.^([^(55)](#fn55))

![FIGURE 2.2 Timeline of major Cybercrime incidents.](images/fig2.2.jpg)

**FIGURE 2.2** Timeline of major Cybercrime incidents.

Users can browse the Dark Web anonymously, buying and selling illegal goods in the form of data. Once purchased, the data can be sorted into categories, for purchase or for exploitation.

As these crimes transform and evolve, replacing older and clumsier tactics with new and more agile cyber tools and behaviors, our understanding of cybercrime is constantly expanding.

The cybercriminal’s weapon is not a gun or knife, but instead is a computing device that links to a network. He or she accesses the Internet and directly commits theft or vandalism. The current expansion of cybercrime coincides with the development of more advanced artificial intelligence (AI) and machine learning algorithms. We have defined cybercrime as a computer-based criminal act utilizing a computing device and a network. This act transcends national and international borders and raises jurisdictional issues that one nation alone cannot address.

## [2.3 Brief Summary of the Phases and Evolution of Cybercrime](#contents.xhtml#re_h-2-5)

Most Internet technologies are connected, using servers that cross political and cultural boundaries. These technologies provide a vast array of services and resources that are merely a click away. Valuable benefits, such as cheap storage using cloud computing, fast connectivity to businesses using e-commerce, and access to governments can be reached on a global scale in seconds. These technologies provide a rich environment for activities such as hacking, theft of information, installation of malware, and interference with network integrity and availability.

As we examine the history of cybercrime, we see four phases*.* However, the beginning of a new phase does not signal the end of the previous one; it is merely an addition to the repertory of cybercrimes. Today (2020), we can look back and observe all four phases.

The first phase began during the 1970s and 1980s. In this phase, we see an exploratory or experimental effort to control situations from a distance, using computer technology.

The second phase begins in the latter part of the 1980s. We see the formation of hacking groups, and the creation of a few highly effective viruses and worms aimed at crippling large systems.

The third phase originated in the early 2000s. Here we see the widespread adoption of Internet technology and use of social media, leading to crimes that are mostly financial.

The fourth phase commenced in 2011, a particularly challenging year for the Security industry. In this phase, we see massive breaches into organizations such as the Sony PlayStation Network and Nasdaq.^([^(56)](#fn56))

![FIGURE 2.3 Phases of Cybercrime.](images/fig2.3.jpg)

**FIGURE 2.3** Phases of Cybercrime.

Cybercrime continues to evolve along with the Internet, now including Wi-Fi, cryptocurrency, leading to the crime of Cryptojacking, social media, and the Internet of Things (IoT).

Now, let us understand these phases in more detail.

### [Phase I](#contents.xhtml#re_h-2-6)

Phase I dates from the late 70s, with the first computer worm, the “Creeper.” Between the 1970s and 1980s we saw the expansion of the ARPANET (Advanced Research Projects Agency Network), an early network initially funded by the US Department of Defense, and its metamorphosis into the fledgling Internet.

Phase I can be summarized as *You can build it, but I can break it.* It features direct attacks against systems, with the goal of bringing them down or causing damage. In this phase budding criminals are becoming almost gleefully aware of their ability to cause damage within this new environment. Some tools of this period include malicious code, Trojans (a type of malware disguised as a legitimate piece of software), advanced worms, and viruses that replicate and crash systems or damage files.

When the Creeper worm appeared on the ARPANET,^([^(57)](#fn57))

One of the most important innovations of this time was the development and use of e-mail. Earlier, emails were designed to deliver messages and files directly to printers. One of the first email systems, created by Tom Van Vleck and Noel Morris in 1965 at The Massachusetts Institute of Technology, was called the Compatible Time-Sharing System (CTSS).

Ray Tomlinson is credited with inventing the e-mail system as we know it today. While working with ARPANET, Tomlinson chose the symbol **@** to designate a particular user and its host, and to differentiate between one computer and another: [name-of-the-user@name-of-the-computer](http://name-of-the-user@name-of-the-computer).^([^(58)](#fn58))

Once computers became part of our daily lives, more incidents began to follow. In 1971, at General Motor’s Oshawa (Canada) factory, thieves hacked into the system and created false purchase requisitions; they then placed purchase orders and invoices in the accounting system to make matters appear legitimate. In 1973, a teller at New York’s Union Dime Bank used the bank’s computer to embezzle $1.5 million.^([^(59)](#fn59))

The term *Hacking* originated in the 1960s at MIT. It was originally a positive term and described the use of a modification to a product or procedure to correct a problem. Students learned to modify computer code to control a program in new ways, demonstrating that they were worthy of calling themselves Hackers. The term was used for amusement and recognition, not for illegal activity.

Phase I is also characterized by a new character – a curious, brilliant, and solitary individual in search of thrill and adventure, seeking to show off his abilities (*I'm better than you, I can hack anything*). In the 1980s, hackers joined hacking groups such as the Chaos Computer Club, Legions of Doom, and NuPrometheus League.^([^(60)](#fn60))

The romantic veneration of computers is perfectly displayed in the 1983 movie *War Games*, in which a young hacker finds his way into a U.S. military supercomputer and comes close to starting a ‘global thermonuclear war’. The movie was released during the time when people believed computers were magic and hackers were geniuses**,** and while a classic representation of this period, it remains popular to this day.

In 1984, U.S. Congress passed the first hacking-related legislation; the Computer Fraud and Abuse Act (CFAA). It was enacted as an amendment to existing computer fraud law (18 U.S.C. § 1030). However, the first person to face prosecution for cybercrime in the United states was Ian Murphy (“Captain Zap”) in 1981. Murphy hacked into AT&T’s computers and changed their internal clocks to charge less during peak times. He received 1,000 hours of community service and 2.5 years of probation.^([^(61)](#fn61))

In 1986, in an attack chronicled by author and investigator Cliff Stoll in “The Cuckoo’s Egg”, German hacker Markus Hess hacked into the Lawrence Berkeley Laboratory computer network^([^(62)](#fn62))

In 1988, Robert Morris, a Cornell University student, embedded his *Morris worm* in the University’s UNIX system. A worm is a standalone malware program that works by multiplying itself and spreading from one computer to another. The *Morris worm* multiplied itself thousands of times, moving from computer to computer across a huge network of computers from many universities, and eventually brought the system to a crashing halt. This worm destroyed more than 6,000 computers and resulted in $98 million in damages. Although still a student, Robert Morris was prosecuted and convicted of violating 18 U.S. Code § 1030 **(**fraud and related activity in connection with computers). The *Morris worm* is known as the first Internet worm.

### [Phase II](#contents.xhtml#re_h-2-7)

Phase II dates from the beginning of the 1990s to the year 2000. With the advancement of web browsers in the 1990s, it became easier to send viruses through Internet connections. These viruses caused the computers to run slowly or allowed annoying pop-up ads to appear.

In 1991 the *Michelangelo virus* appeared.^([^(63)](#fn63))

The next important virus, the *Melissa Virus*,^([^(64)](#fn64))

### [Phase III](#contents.xhtml#re_h-2-8)

Phase III arose in the early 2000s, after the ARPANET and the National Science Foundation’s NSFNet were transformed into a larger network, becoming the Internet ([Figure 2.4](#c2.xhtml#f2.4)). After establishing the Internet as their main channel of communication and illegal e-commerce, cybercriminals began targeting big data. During this phase, cybercrime became a for-profit enterprise. We define this phase by the proliferation of monetary crimes, including identity and credit card theft, phishing, Domain Name System (DNS) attacks, botnets, and use of ransomware and spyware. Cybercriminals evaded justice worldwide by using secure software and proxy servers to conceal their locations and communications, thus remaining anonymous. When social media was born and users flooded it with their personal information, theft of personal data became the crime of the new millennium, with cybercriminals accessing bank accounts, setting up fraudulent credit cards, and engaging in other forms of financial fraud.^([^(65)](#fn65))

![FIGURE 2.4 A map of the ARPANET in December 1970. Courtesy of DARPA.](images/fig2.4.jpg)

**FIGURE 2.4** A map of the ARPANET in December 1970. Courtesy of DARPA.

The number and types of online attacks grew exponentially. Large denial-of-service (DDoS) attacks occurred, including attacks at Amazon, AOL, CNN, eBay, Yahoo, and numerous others. The *ILOVEYOU* virus^([^(66)](#fn66))

In 2001, the *Klez* worm infected its host with a symbiotic virus, Elkern.cav, through an e-mail.^([^(67)](#fn67))

In response to the attacks of September 11, 2001, Congress enacted the 2001 USA PATRIOT Act,^([^(68)](#fn68))

The changes in the USA PATRIOT Act appeared logical and necessary, given the circumstances. The law relaxes restrictions on how much personal information about citizens and non-citizens the government can acquire. Additionally, it authorizes the federal government to improve surveillance procedures, provides for increased monitoring of financial transactions, extends permission for wiretapping, and gives government the power to request electronic communications, as well as the ability to relax search warrant requirements for suspected terrorists. This law remains a subject of contention, as it was intended to deal with a temporary state of emergency, and yet remains in effect twenty years later.

During this time, websites like MySpace and LinkedIn gained fame. YouTube first appeared in 2005, devising new ways for people to communicate and share videos. In 2006, Facebook and Twitter became available to users across the world. This period was characterized by the miniaturization of technology, and the rapid spread of mobile devices (smartphones and tablets).

In 2003, the *Sobig* worm was introduced, infecting millions of Internet and Windows PC users by e-mail.^([^(69)](#fn69))

Trojan horse malware obtained its name from Homer’s novel, The Iliad. When the Greeks tried to conquer the city of Troy, they had difficulty getting into the fortified city. The Greeks deceived the Trojans by giving them a giant wooden horse and pretending to sail away after the Trojans dragged the wooden horse into their city. During the night, Greek soldiers hidden inside the horse crawled out and opened the gates for the rest of the Greek army, after which they captured the city. Similarly, a Trojan horse is a type of malware (malicious software) that masquerades as genuine but contains a hidden destructive element.

When you receive an email and click an innocent looking attachment, you may unknowingly install a program that will infect files throughout your computer or network. That attachment is called a Trojan horse. Mostly, the Trojan horse stays hidden until a specific action is taken, such as accessing an online banking website or paying a bill online. At that point, the Trojan activates a malicious code and carries out its instructions, stealing passwords or transferring money. The Trojan horse may be scripted to delete itself after completing the task.

*Mydoom*, one of the most damaging viruses or worms, appeared in 2004.^([^(70)](#fn70))

Another devastating worm was the *Sober* email worm and its variants. The *Sober* worm is a family of computer worms. They are generally independent programs, and do not need human interaction to replicate across networks. The worm may arrive in an email, fake webpage, fake pop-up ad, or fake advertisement, and will contain subject lines such as, sex, love, and even computer virus warnings. “Upon execution, *Sober* copies itself to one of several files in the Windows system folder, as an .exe file, with a name that is constructed from the following strings: sys, host, dir, explorer, win, run, log, 32, disc, crypt, data, diag, spool,service,smss32.”^([^(71)](#fn71))

Three notable technological advancements became so widespread in this period that they changed how people interact with each other. These technologies are the Apple iPhone***,*** first introduced in 2007, and the Android Operating System (OS), introduced in 2008. The third development is Cloud Computing**,** although John McCarthy first introduced a much more basic version of this technology in the 1960s.^([^(72)](#fn72))

In 2006, Amazon introduced its Web Service AWS, and other cloud*\-*computing providers, such as Google, IBM and Microsoft followed. Cloud Computing is the distribution of computing services such as database, storage, applications, and analytics, over the Internet. Cloud computing provides business and individuals around the world flexibility, savings in cost, time, and resources, enabling less reliance on traditional data centers and support teams. However, a great concern with cloud computing has been the issue of security and data privacy. Depending on the cloud computing model used, data may no longer belong completely to a business or individual. The cloud service provider stores the user’s data on its own servers and has full access to the data, confidential or not. Additionally, physical storage of the data often spans multiple servers in different countries, making it easier for cyber criminals to manipulate the connection to the cloud or attack the data centers.

An example in April 2019 involved the Facebook data bridge that was posted publicly on Amazon cloud servers. Five hundred and forty million records of Facebook user data were publicly exposed. According to UpGuard,^([^(73)](#fn73))

Named after Zeus, the Greek king of the gods, the *Zeus* virus, was identified in 2007. Like other Trojan malware, it targets Microsoft Windows, and cybercriminals use it to steal online financial transactions. *Zeus* creates a botnet, and gathers massive amounts of information including passwords, configuration files, and online credentials. Botnets or “bots” are internet-based computing devices that have been infected with malware and programmed remotely for fraudulent purposes.

Additionally, the *Zeus* virus corrupts computers, while it communicates with and controls servers. *Zeus* infected over 3.6 million computers in the United States.^([^(74)](#fn74))

In 2009, the Health Information Technology for Economic and Clinical Health Act (HITECH), steered healthcare providers in the United States toward an expansion of secure Electronic Medical Records (EMR). Once personal medical information was online, cybercriminals began targeting these healthcare records. They realized that while data stolen from financial institutions becomes useless once the breach is uncovered and passwords are changed, medical histories cannot change and last for a lifetime.

In 2010, the *Stuxnet* worm appeared. *Stuxnet* was a Cyber-warfare tool created by U.S. and Israeli governments to disrupt Iran’s nuclear program.^([^(75)](#fn75))

### [Phase IV](#contents.xhtml#re_h-2-9)

Phase IV begins after 2011 and extends into the present. This phase comprises state-sponsored cyberattacks, espionage, breaches to government privacy and confidentiality, and the manipulation of public opinion through persuasion over social media platforms. Additionally, in this phase we see the rise of fake news, and the death of personal privacy. We now live in the age of surveillance, eerily like George Orwell’s descriptions in his novel, 1984.

The year 2011 was a year of sizable data breaches. Epsilon Data Management, whose clients include Eddie Bauer, Ethan Allen, and TD Ameritrade, lost enormous amounts of data. Also hit were Sony’s PlayStation Network and Qriocity services, drawing the public’s attention to data security, privacy, and the role of governments in preventing such attacks.^([^(76)](#fn76))

In 2013–14, Yahoo experienced the largest security breach in its history, affecting over a billion users.^([^(77)](#fn77))

Another famous example of a state-sponsored attack occurred against Sony Pictures Entertainment (SPE) in 2014. The company detected extensive network intrusions, followed by demands that it refrain from releasing its new action comedy film, ‘The Interview’**.** The film was a satire about Americans sent to North Korea to assassinate its president, Kim Jung Un. Sony claimed that the film was not a political attack but was intended only as entertainment. Sony employees were threatened with physical harm unless they signed a document denouncing the film. Sony did not accede to the demands and released the film as planned. It was later verified that the government of North Korea was responsible for the attack and demands that followed.^([^(78)](#fn78))

In 2015, a hacking group called “The Impact Team” hacked into Ashley Madison’s database and stole personal information from 37 million users. Ashley Madison is a website dedicated to extramarital affairs.^([^(79)](#fn79))

Additionally, cybersecurity attacks continued to affect the healthcare industry. Health insurer Anthem Inc. and Primera Blue Cross suffered massive data breaches. Cyber thieves stole approximately 91 million patient records, including social security numbers, medical data, and financial information.^([^(80)](#fn80))

In 2016, as the U.S. presidential election approached, the country experienced a wave of political cybercrime, characterized by manipulation of social media as well as theft or purchase of personal profiles. In this case, cybercriminals from other countries chose targets to influence based on their political orientation, levels of education, opinions, and other factors that made them persuadable and vulnerable. This type of hacking campaign manipulates social media data and attacks voters without their consent, using social media bots, creating propaganda, and promoting fake news. Since the majority of American adults (62%) get their news on social media, a large number of those who see these stories accept them and believe they are true.^([^(81)](#fn81))

Democratic presidential candidate Hillary Clinton and other Democrats were attacked with ads and persuasive Facebook material containing false information, with the goal of changing votes and creating voting blocs in vulnerable states, ultimately leading to social unrest and unexpected election results, namely the election of Donald Trump, and finally to the possibility of a changed balance of national and international power.

We have seen these hacking campaigns not only in the U.S. election of 2016,^([^(82)](#fn82))

New evidence discovered in 2018 showed that a British political consulting firm, Cambridge Analytica, and other companies harvested personal information in order to alter the outcome and influence voter behavior in both the U.S. presidential election and the U.K.’s Brexit referendum of 2016.^([^(83)](#fn83))

An example of this behavior manipulation occurred in the small Welsh town of Ebbw Vale. According to National Public Radio, the town voted overwhelmingly in favor of Brexit. Using news feeds from Facebook, which later disappeared, and advertisements from Google and YouTube, people were persuaded to believe that immigrant and refugee populations had overwhelmed the city, even though the town actually has one of the lowest rates of immigration in the country. Although the European Union had invested heavily in the town, people came to believe it had done nothing for them. The advertisements and fake news provoked specific human emotions and consequent behavior among people.^([^(84)](#fn84))

The use of psychographic techniques to manipulate behavior emerged as one of the results of corporate greed from Facebook, Twitter, and even Google. Psychographic analysis puts an emphasis on consumer lifestyle. It is used to understand the cognitive processes that affect spending habits, hobbies, opinions, attitudes, interests, and lifestyles, who we buy from, and why we choose to purchase things.

In 2018, the UK’s protection watchdog fined Facebook £500,000 for the role it played in the Cambridge Analytica scandal. Later in 2019, after an investigation of Facebook showed it gave Cambridge Analytica access to 87 million Facebook users’ personal data without their knowledge, the U.S Federal Trade Commission (FTC) fined Google $5 billion. The FTC found that Facebook violated rules against deceptive practices by revealing phone numbers collected during the two-factor (2FA) authentication used for advertising.^([^(85)](#fn85))

Cambridge Analytica gained additional information by using mobile apps to collect data, and by tracking location and contact/address lists. One app used was called “Cruz Crew” and was used by the campaign for the re-election of U.S. Senator Ted Cruz of Texas.^([^(86)](#fn86))

In addition, during Phase IV we continue to experience older forms of cybercrime, including banking malware, bitcoin wallet theft, mobile device hacks, and extortion through ransomware.

With both new and old threats, in Phase IV we see cybercrime grow beyond hacking and identity theft to a more sophisticated and better-organized global threat. Cybercrime now resembles a silent worldwide war. It knows no boundaries and concerns every nation on the planet.

The dissemination of fake news, a critical part of election interference, has been a great source of revenue for social media. This use of disinformation can be stopped only through government supervision, education, and continuous monitoring. As of now, we can only conclude that the word ‘truth’ has lost its meaning. Instead we have “alternative truth or facts.”

We first loved Google and Facebook because they were “free”; we now understand that social media is far from free. We must now think of ourselves as not only users, but also as sources of revenue, with our private information a commodity that can be bought and sold. Social media may have been designed to bring us together, but it now divides us.

Between 2016 and 2017, an encrypting ransomware program called *Petya* and its newer version, *NotPetya*, appeared. Both were intended to encrypt and lock the hard drive of infected computers. File access could be restored only by paying a ransom. The malware usually arrived on the victim’s computer attached to an email. *Petya* could run only if it succeeded in tricking the victim to download its file from a spam email. It targeted the Windows Operating System (OS), infecting the master boot record, encrypting the hard drive’s file system and preventing the computer from booting up. Frequently, cybercriminals demand that the victim make payment to regain access through Bitcoin.^([^(87)](#fn87))

In 2016 we experienced the *Mirai* strain of malware. This type of malware turns IoT devices running on Linux into remotely controlled “bots”.^([^(88)](#fn88))

In 2017, ransomware called *WannaCry* exploited a weakness in Windows computers worldwide. Like *Mirai*, the ransomware was able to encrypt a computer’s files and then lock out users, making it impossible for them to access their own information. At that point, ransom payments in Bitcoin cryptocurrency were required to permit users to access their own information.

*WannaCry* infiltrated the United Kingdom’s National Health Service (NHS) computers, bringing down the entire medical records system. Medical personnel could not register patients, access medical records, or prescribe medication, delaying crucial procedures, and creating chaos for millions of patients and personnel.^([^(89)](#fn89))

The EternalBlue exploit is a code that takes advantage of a software vulnerability, in this case MS Windows OS. It was allegedly stolen from the National Security Agency (NSA) in 2016 and was leaked by a hacker group called the Shadow Brokers. It was then was used in *WannaCry* ransomware.^([^(90)](#fn90))

*WannaCry* and *NotPetya* did not target individuals, but instead attacked critical infrastructures of the largest systems, banks, state agencies, and ministries. These attacks did not come from lone criminals, but instead were designed by intelligence or cyberwarfare agencies.^([^(91)](#fn91))

In 2018, the European Union implemented legislation to combat cybercrime. The General Data Protection Regulation (GDPR) replaced the Data Protection Directive 95/46/EC,^([^(92)](#fn92))

In 2018, Marriott International announced that hackers had breached its Starwood reservation system and had stolen the information of 500 million of its customers worldwide.^([^(93)](#fn93))

In 2019, Facebook, the subject of numerous cybersecurity concerns in the past, suffered another breach. Because unsecured Facebook personal databases were insufficiently protected by a cybersecurity firm called Upguard, more than 540 million records from Facebook users were exposed publicly on Amazon’s cloud computing service.

In 2019, the US Federal Emergency Management Agency (FEMA) announced in a management alert that the confidential personal information of 2.3 million disaster victims of the 2017 California wildfires and hurricanes Harvey, Irma, and Maria had been exposed.^([^(94)](#fn94))

In 2019, we saw growth in Artificial Intelligence (AI) and Machine Learning (ML) algorithms that have revolutionized the creation of believable audios and videos called ‘deepfakes.’ This technology provides the ability to trade one person’s face for another in a video clip or image. Deepfake videos can make anyone do or say anything, and they are not easy to detect. The impact of this powerful technology can range from harmless parody to bullying and extortion of victims, and have enabled the creation of X-rated videos used in political attacks in major election campaigns. It becomes increasingly difficult to spot these fakes and persuade others that they are not credible. Thus, the power of Artificial Intelligence provides another weapon to the cybercriminal.

## [2.4 Cybercrime Categories](#contents.xhtml#re_h-2-10)

### [The Three Cybercrime Categories](#contents.xhtml#re_h-2-11)

Cybercrime may be organized into three categories: cybercrime against government, cybercrime committed against individuals, and cybercrime against property or a corporation. Each category has different goals and requires different methods to achieve these goals.

*   **Cybercrime against government:** Cybercrime against a government is an attack against a state or nation’s sovereignty and is an attempt to limit its power. This act of terrorism is also called cyberwarfare.
    
    ![](images/inline2.1.jpg)
    *   Cybercrime against a government includes hacking into government, military, or defense contractors’ websites, attacks against critical infrastructure, distribution of malware, denial-of-service (DoS and DDoS) attacks, and ransomware attacks. Additionally, it includes manipulation of social media platforms and the distribution of propaganda to influence people into the adoption of certain beliefs and attitudes.
    *   Examples include Russian manipulation of social media platforms in the United States and Europe (U.S. presidential election of 2016,^([^(95)](#fn95))
    *   State-sponsored intellectual property theft and cyber-enabled espionage evading U.S. laws. The use of copyrights, patents, or trade secrets, and trademarks without permission.
    *   Examples include Chinese hackers acting on behalf of China’s Ministry of State Security (MSS) to target aviation companies in Europe and U.S. aerospace companies, banking and finance, telecommunications, consumer electronics, medical equipment, and government agencies.^([^(96)](#fn96))
*   **Cybercrime against corporations or against property:** This type of cybercrime is characterized by unauthorized computer intrusion into the private information of any corporation or any property.
    
    ![](images/inline2.2.jpg)
    *   This includes unauthorized transfer, theft, or possession of data, use of a computer or network without permission, computer or network vandalism, and attacks using malicious software such as spyware, ransomware, malware, and key logger software.
*   **Cybercrime committed against a person:** This category involves a computer-related crime that targets an individual.
    
    ![](images/inline2.3.jpg)
    
    *   This includes the use of malware, ransomware, hacking, spamming, phishing, identity theft, and online scams. It also includes extortion, cyberbullying, cyberstalking, cyber harassment through distribution of hateful or illegal information on the internet or social media, online libel or slander, sexting, and distribution of child pornography and other pornographic material ([Figure 2.5](#c2.xhtml#f2.5)).
    
    ![FIGURE 2.5 Cybercrime categories.](images/fig2.5.jpg)
    
    **FIGURE 2.5** Cybercrime categories.
    

Cybercriminals favor the most efficient methods, and those requiring the least effort. To understand this, let us look at the Crime-as-a-Service (CaaS) model. This criminal marketplace is located on the Dark Web, offering cybercriminals on-demand services such as password cracking, cloud cracking, distributed denial-of-service, and malware.^([^(97)](#fn97))

CaaS provides services and products for anyone, including the non tech-savvy, to buy and use. A 2018 Internet Organized Crime Threat Assessment by Europol reports that cybercriminals and state sponsored actors all use the CaaS model.^([^(98)](#fn98))

The increasing presence of worldwide high-speed Internet makes people more likely to experience cybercrime as victims. The attackers may be from an organized crime group, a corporation engaged in espionage, participants in hacktivism, cyber warfare or cyberterrorism, or criminals looking for financial gain. While conventional crime is a social and economic occurrence, cybercrime is a business, and seeks financial success and quick profit. Thus, cybercrime encompasses economic enticements and methodically selected targets. Cybercriminals generate substantial revenues by selling, obstructing access, or holding data to ransom through the dark web. It fills needs, evolves, and adapts. You may be a victim of cybercrime without ever being aware that your data is being sold to a third party to meet that entity’s goals.

Cybercrime is an inevitable consequence of our data-centric society. Proliferation of cybercrime is associated with the rapid expansion of the Internet, growth of broadband networks, and awareness of the ways in which our unprotected data may be used.

## [2.5 The Future of Cybercrime](#contents.xhtml#re_h-2-12)

### [The Making of the Cybercriminal](#contents.xhtml#re_h-2-13)

Like many of us, cybercriminals often belong to online forums, which facilitate peer-to-peer communication and the buying and selling of hacking tools and services. These activities take place in the Deep Web and the Dark Web.

The Surface Web (Visible Web or Indexed Web), which we know and use every day, does not contain all the content available online. Familiar Search engines like Google and Bing, can only retrieve content in the Surface Web.

Access to the Surface Web requires a direct query, or keywords. But it is exceedingly difficult to find information on the Deep Web since most of its contents are not indexed and will not be recognized by search engines.

The Deep Web is larger than the Surface Web, and is growing exponentially.^([^(99)](#fn99))

The Dark Web is a portion of the Deep Web and contains content and sites that are purposely concealed and encrypted. It contains illegal activities such as child pornography, sensitive information, money laundering, copyright infringement, identity theft, illegal sales of weapons and other kinds of illegal sales. The Dark Web is accessed only by using specialized software like The Onion Router (TOR) or the Invisible Internet Project (I2P). The user must use encrypting software that masks his IP address, and makes him hard to identify. The most publicized site related to Dark Web is the Silk Road, an online black-market drug store selling everything from weed to heroin^([^(100)](#fn100))

![FIGURE 2.6 The Surface Web, Deep Web, and Dark Web.](images/fig2.6.jpg)

**FIGURE 2.6** The Surface Web, Deep Web, and Dark Web.

Essentially, the Dark Web is an illicit marketplace providing services to terrorists, contract killers, human organ black market sellers, and other criminals. It flourishes because of its borderless nature. Its anonymity and speed serve illegal lucrative businesses around the world.

Small businesses are especially vulnerable to the Dark Web, since it provides data they cannot afford to buy; the full-scale Information Technology (IT) teams and secure networks of larger organizations are out of reach for them. These small businesses are also susceptible to the threat of Ransomware.^([^(101)](#fn101))

In general, cybercriminals prefer to hack smaller targets with smaller financial payouts rather than attack large enterprises. They use both simple and cutting-edge technologies to carry out their attacks and constantly seek new methods and techniques.

#### [Cybercrime and the Internet of Things (IoT)](#contents.xhtml#re_h-2-14)

The IoT encompasses millions of computer-based devices that transmit data over the internet autonomously. These include smart home devices and automation products like smart thermostats, smart bulbs, smart TVs, and wearable sensors like heart rate and respiratory rate monitors. Due to technological advances, cheap data storage, and fast internet connections, the Internet of Things (IoT) is everywhere.

Protecting the devices comprising the IoT is a security nightmare. In 2018, The FBI warned that cyber criminals are now targeting IoT devices, looking to exploit their vulnerability and use them as a pathway to other attacks.^([^(102)](#fn102))

The *Mirai* malware attack in 2016 targeted IoT devices, demonstrating the risks these devices faced.^([^(103)](#fn103))

5G is the next generation of mobile broadband that will ultimately replace current 4G LTE connections. 5G has been developed with three major improvements: superior speed, lesser latency (the time it takes for data to go back and forth, and the ability to connect more IoT devices at once.^([^(104)](#fn104))

IoT devices make our lives better, more comfortable, and healthier, utilizing real-time monitoring, medical assistance, tracking and alerts. Consequently, cybercriminals will have access to more and more personal and medical information. Many IoT devices have being manufactured using unsecured communications protocols and open source codes, allowing anyone to use or modify a code or a program. Additionally, manufacturers often use and share code from a single source across devices and multiple brands. As a result, many IoT devices have hard coded backdoor passwords built into them, meaning that anyone can type in the default password and gain access. In some cases, the password can be found on the internet (YouTube) or hacking forums.

Cybercriminals perform these attacks remotely and anonymously. Thus, the ability to impose ransomware thousands of miles away to owners of countless IoT devices is possible. Cybercriminals are constantly looking for ways to gain control of them via password cracking and exploiting additional vulnerabilities.

#### [Cybercrime: Machine Learning and Artificial Intelligence](#contents.xhtml#re_h-2-15)

However, despite the threats already discussed, Machine Learning (ML) and Artificial Intelligence (AI) may be beneficial in the fight against cyber-attacks. ML, a subdivision of AI, enables a computer to learn from experience and behave with a semblance of human-like intellect. This goal is still largely in the future. ML can improve cyber security by spotting abnormal activity patterns in an attack much faster than a human. Using deception as an automated response, AI can send decoys that deceive cyber-attackers, while still adapting to new situations, learning from them, and preventing future attacks. AI technologies can help analysts cope with the potential threats coming from IoT and other new technologies.

Nevertheless, Newton’s third law reminds us that for every action, there is an equal and opposite reaction.^([^(105)](#fn105))

Furthermore, AI can help cybercriminals analyze large volumes of data, create personalized emails or messages, and target specific people for propaganda and psychological warfare.

Google’s TensorFlow^([^(106)](#fn106))

Machine Learning and Artificial Intelligence can be beneficial, but are also a major threat.

#### [Online Child Sexual Abuse and Exploitation (CSAE)](#contents.xhtml#re_h-2-16)

Besides financial rewards, cybercriminals are enticed by cyberbullying, pedophilia, and sexual exploitation, and goals that are political and ideological. The internet has exponentially increased the production, distribution, and possession of child pornography images and child sexual abuse material (CSAM). The United States has addressed online child pornography with the Child Pornography Prevention Act of 1996 (CPPA)^([^(107)](#fn107))

Many consider child sexual abuse and exploitation to be the most shocking aspect of cybercrime. Although this type of abuse occurred prior to the internet, its existence enables new methods and means of exploitation. The growing number of children who can access the internet and social media allows cybercriminals to connect with them as well as with adults.

Technologies like encryption enable offenders to hide their identity and avoid law enforcement. Faster internet speeds, lack of physical boundaries, cloud services around the world, and data encryption make detection exceedingly difficult. Since young social media users link self-esteem to ‘likes’ and ‘dislikes’ the promise of thousands of followers if they carry out offenders’ requests is a powerful incentive. This allows criminals to use persuasion, temptation, or coercive methods to control the behavior of minors. According to the Internet Organized Crime Threat Assessment by Europol (IOCTA 2018),^([^(108)](#fn108))

Another form of CSAE is live streaming. This tool does not require storage of pornographic material and presents a limited forensic trail. Additionally, forensic investigations are very tricky when they involve crossing international borders and jurisdictions.

#### [Cost of Cybercrime](#contents.xhtml#re_h-2-17)

According to *The Economist*, now that over 50% of the world population has access to the internet, the second half of the internet revolution has begun. “Most new users are in the emerging world; some 726 million people came online in the past three years alone. China is still growing fast. But much of the rise is coming from poorer places, notably India and Africa.”^([^(109)](#fn109))

What is the financial cost of cybercrime? In 2014, cybercrime cost almost $500 billion; by 2018, the cost rose to $600 billion.^([^(110)](#fn110))

A 2018 RAND Corporation report estimates that global cybercrime “has direct gross domestic product (GDP) costs of $275 billion to $6.6 trillion, and total GDP costs (direct plus systemic) of $799 billion to $22.5 trillion, representing 1.1 to 32.4 percent of GDP.”^([^(111)](#fn111))

#### [The Role of Cryptocurrency in Cybercrime](#contents.xhtml#re_h-2-18)

Cryptocurrency is an electronic monetary system or digital currency that uses cryptographic technology, permitting instantaneous and borderless transactions. The best-known cryptocurrency is Bitcoin, but there are many others. Financial institutions and governments have no jurisdiction or control over digital currency. Cryptocurrency uses public and private cryptography keys for privacy, security, and anonymity. Cryptocurrency crimes cannot be predicted or punished properly due to user anonymity and lack of oversight by government and financial regulators.

Cryptocurrency crimes include theft of money from financial exchanges, software that tracks secret keys for transactions, called electronic wallets, suspicious services and cryptocurrency Ponzi schemes. In addition, hackers can take over personal computers and other devices, or can infect a computer with crypto mining malware to stealthily mine cryptocurrencies.^([^(112)](#fn112))

Cybercriminals have been buying and selling cryptocurrencies anonymously at peer-to-peer markets like Dream Market, The Wall Street Market and AlphaBay. Cryptocurrency laundering occurs when an offender uses electronic money, video game currency and digital payment systems to convert illegally obtained funds to clean funds. These currencies have become the preferred tools criminals use for money laundering for the following reasons:

*   **Anonymity, security and privacy:** (no real name required for transactions; criminals can remain unknown)
*   **Lack of universal regulations:** (regulation of cryptocurrency varies around the world; little or no oversight by government regulators)
*   **No financial institutions or government control:** (not governed by any central authority and not monitored)
*   **Tax evasion**
*   **Transportation:** (no detection across international borders, no monitoring from banking institutions)
*   **Speed:** (quick processing of cryptocurrency into cash)

The growing criminal use of cryptocurrency is creating problems for the global financial system and governments ([Figure 2.7](#c2.xhtml#f2.7)). Criminals hide their money trails and confuse law enforcement agencies by converting stolen income into video game currency or virtual goods. Virtual goods include gaming merchandise like weapons for a specific game, clothing, or other items that a player needs. The criminals then transform these items into cryptocurrencies or property purchases like Bitcoin Real Estate. Some of the most popular video games for cryptocurrency laundering are Minecraft, FIFA, Final Fantasy, Star Wars Online, and Warcraft. Virtual goods can be purchased at online games sites, cell phone apps, and games on social media. According to the Cipher Trace Cryptocurrency Anti-Money Laundering Report, crime in the cryptocurrency sector in 2018 reached $1.7 billion USD. In the first quarter of 2019, theft of cryptocurrencies from exchanges and infrastructure frauds came to more than $356 million USD.^([^(113)](#fn113))

![FIGURE 2.7 Cybercrime and Money Laundering.](images/fig2.7.jpg)

**FIGURE 2.7** Cybercrime and Money Laundering.

### [State-Sponsored Cyberwarfare and Industrial Espionage](#contents.xhtml#re_h-2-19)

The present phase of cybercrime (Phase IV) is characterized by state-sponsored cyber warfare, particularly attacks on Western nations.^([^(114)](#fn114))

State-sponsored hackers target countries and their citizens by using ransomware, data theft, critical infrastructure attacks (electricity, gas, and water supply systems) and social media manipulation with trolls, bots, and fake news.

This cyber warfare is an operation with specific objectives, undertaken by one nation attacking another. Special military units are dedicated to cyber warfare, such as the Chinese “PLA Unit 61398” or Russia’s “Information Countermeasures” or IPb (informatsionnoye protivoborstvo). In addition, intelligence agencies around the world pay hackers to keep the breach secret. As a result, cyberwarfare actors receive funding, technical support, and equipment from a country’s intelligence or military agencies to execute the attack. The operation consists of psychological warfare, containing propaganda messages and espionage.

Cyberwarfare continues to be an effective weapon in political conflicts around the world. The 2015 attack on Ukraine’s power grid,^([^(115)](#fn115))

The usual suspects in cyber attacks on Western countries are China, Iran, North Korea, and Russia. We know that Russia interfered with the American presidential election in 2016, and that North Korea and China have both been accused of cyber espionage.^([^(116)](#fn116))

## [2.6 Conclusion](#contents.xhtml#re_h-2-20)

Cybercrime is persistent and will not stop any time soon. Motivations for cybercrime include:

*   **Cybercrime as a business:** Financial motives are appealing and are frequently easy to achieve. The increased number of unsuspected new users, the growth of Cybercrime-as-a-Service and the vast amount of data give cybercriminals access to power and wealth.
*   **Hard to prosecute cybercriminals:** Jurisdiction is the biggest barrier in the prosecution of cybercriminals. When the cybercriminal committing a crime is located outside of the jurisdiction, the likelihood of being apprehended is low.
*   **Politically motivated:** Hacktivists can carry out cyber attacks and hate crimes, spreading propaganda, making political statements and protests, destruction, and retaliatory actions.
*   **Script kiddies**^([^(117)](#fn117))
*   **Cyberwarfare and industrial espionage:** Goals include sabotage, controlling critical infrastructure, developing biases, influencing behavior, and creating political unrest.

Today, we are all experiencing the most dangerous type of cybercrime, with corporations and social media platforms selling our private information, and foreign powers manipulating data to influence public perception. Data, targeted emails, and Facebook posts containing lies, can manipulate recipients maliciously, and can only be described as weapons. Unfortunately, most people do not recognize or understand this threat. Most people can be manipulated and made to believe just about anything. Western democracies have been disrupted by lies, manipulation, and corporate greed.

As cybercrime has increased it has gone far beyond identity theft or a worm in a computer. It has evolved and is now a pandemic that threatens our way of life.

## [2.7 Key Words](#contents.xhtml#re_h-2-21)

 
| Cybercrime: || Viruses |
| --- | --- |
| evolution, motivations and phases, || Worms |
| categories, || Internet of Things (IoT) |
| Hacking, || Cybercrime |
| Cybercrime weapons: Crime-as-a-Service (CaaS) || Machine Learning and Artificial Intelligence |
| State-Sponsored Cyberwarfare and Industrial Espionage || Online Child Sexual Abuse and Exploitation |
| Cyberbullying or Cyber || Cost of Cybercrime |
| Harassment || Role of Cryptocurrency in Cybercrime |
| Denial of service (DoS) ||   |
| Fraud and financial crime || Cybercrime and Money |
| Identity theft || Laundering |
| Malware || Surface Web |
| Phishing || Deep Web & Dark Web |
| Ransomware || Deepfake, Fake news |
| Spam ||   |

# [Chapter 3 Understanding the U.S. Legal System](#contents.xhtml#re_c3)

DOI: [10.4324/9780429318726-3](https://doi.org/10.4324/9780429318726-3)

## [Objectives](#contents.xhtml#re_h-3-1)

After completing this chapter, the student will be able to:

*   Understand the main barriers to prosecuting cybercriminals.
*   Understand the legal system in the United States.
*   Distinguish among types of laws.

## [3.1 Introduction](#contents.xhtml#re_h-3-2)

Gathering information for a criminal case is a laborious and rarely accurate process. As people produce more and more searchable data, our understanding of how and why crimes are committed has changed.

Smartphones can log our daily routines, and by giving them permission to track our every move they can pinpoint our exact location. Apps record our psychographic information (personality, values, attitudes, interests, and lifestyles), and other apps use this information to reveal our preferences and political views. As more Internet of Things (IoT) devices and their apps become networked, information about the people who own them will grow significantly. To track a criminal’s movements, conversations, and behavior, we can by-pass a smartphone’s encryption and security and access its metadata.

In response, privacy laws are changing around the world, since previous laws were written during the coin-operated public telephone era. Crime scene investigation in the past was about fingerprints; today it is about our digital footprints. Smartphones, cloud computing, jurisdiction, and IoT devices are making things ever more complex.

The four main barriers to prosecuting cybercriminals are: *Jurisdiction over prosecution*, *Anonymity*, *Difficulty of gathering digital legal evidence*, and *the fact that most cybercrimes are not reported* ([Figure 3.1](#c3.xhtml#f3.1)).

![FIGURE 3.1 Barriers to prosecuting cybercriminals.](images/fig3.1.jpg)

**FIGURE 3.1** Barriers to prosecuting cybercriminals.

### [I. Jurisdiction and Extradition](#contents.xhtml#re_h-3-3)

Jurisdiction over cybercrime and prosecution of the cybercriminal is incredibly challenging, involving multiple countries and regions around the world, and the difficulty of providing the court with authority to exercise jurisdiction over these matters.

![](images/inline3.1.jpg)

Law enforcement bureaus around the world have dedicated special divisions to combating cybercrime. But where does the crime occur – in the country where the cybercriminal operates, or in the country where the victim resides? Unfortunately, it is difficult if not impossible to successfully prosecute cybercriminals when they reside outside of the country and are therefore outside the legal jurisdiction of a court.

Can the accused criminal be brought to the country where the victim lives? Extradition is a process that occurs when a state or nation sends an accused or convicted individual to another jurisdiction for prosecution.^([^(118)](#fn118))

In addition, laws differ from state to state and nation to nation. A criminal act that violates a law in one place may not be illegal in another. Law enforcement agencies can only enforce the law within their jurisdiction. The police department in New York has no authority to arrest someone in Florida, and the Federal Bureau of Investigation can’t arrest someone in France, with infrequent exceptions.

Similarly, the laws of extradition vary from nation to nation. According to international law, a nation has no responsibility to turn over a criminal to the requesting body or nation unless both nations have signed a treaty. In some cases, nations grant extradition without a treaty; in other cases, even with a treaty, extradition is a time-consuming process, often taking years.^([^(119)](#fn119))

### [II. Online Anonymity](#contents.xhtml#re_h-3-4)

Online anonymity is a complex topic. Some argue that anonymity is a sign of free speech and expression, and is a right belonging to every citizen, according to the First Amendment of the U.S. Constitution. Second, some believe that no website should ever be permitted to track their online behavior, citing the right to anonymity and privacy.

To protect themselves, many people, both criminals and law-abiding citizens, use Virtual Private Networks (VPNs). These allow the user to create a secure connection to another network over the Internet, thereby reducing their digital footprint and providing a greater degree of anonymity. However, there are financial costs associated with VPNs, and some will sacrifice their anonymity and privacy for convenience and less expense.

Finally, anonymity is precious to cybercriminals, allowing their illegal efforts to thrive.^([^(120)](#fn120))

### [III. Digital Evidence](#contents.xhtml#re_h-3-5)

Digital evidence is volatile and fragile. Improper handling of this evidence can taint or misplace it. Inexperienced forensic investigators may further exacerbate these difficulties. Digital evidence is more complex than physical evidence because it is not easy to touch, see, or photograph, and any improper handling can make the evidence inadmissible in court. Keeping the integrity of digital evidence and maintaining its chain of custody (the chronological documentation of ownership) is always critical.

The forensic investigator must obtain possession of the evidence with a proper warrant. In some cases, the owner of a computer must voluntarily provide access to the data; in other cases, a proper subpoena must be in place. In child pornography, it can be very difficult to prove which individual downloaded the illegal material. Likewise, as hacking attacks have become more common, a defendant can claim that someone else installed illegal material on their computer without their permission or knowledge. Another difficulty may be the reliability of the evidence, and whether the tools and processes used by the forensic investigator meet the standards for admissible evidence. It is not unheard of for innocent persons to be convicted because of false digital evidence.

Computer forensics investigation is still in its infancy and requires broad universal scientific standards and tools. The enormous amount of data saved in every computing device, along with what may have been stored in the cloud, presents significant challenges. For example, if the cloud that hosts certain data has servers in several different countries, more than one country may have concurrent jurisdiction over the data.

### [IV. Most Cybercrimes Are not Reported](#contents.xhtml#re_h-3-6)

Most cybercrimes against individuals are not reported because of *humiliation*, and the perception that *law enforcement won’t be able to help*, especially if the cybercriminal is in a different country. Unfortunately, law enforcement agencies around the globe are rarely sure how many cybercrimes have been committed, particularly when they don’t have the weapons to pursue the cybercriminals and stop the crime.

![](images/inline3.2.jpg)

Corporations also report cybercrime infrequently, unless required by law to report a cybercrime involving personal or medical information under the Health Insurance Portability and Accountability Act of 1996 (HIPAA) in the United States, or the Personal Information Protection and Electronic Documents Act (PIPEDA) in Canada. Companies in the EU are under the General Data Protection Regulation (EU) 2016/679 (GDPR), are ahead of most of the world in these matters, and are legally obliged to notify the Information Commissioner’s Office (ICO) of any personal data breach.

If not obligated, companies will usually not report a cybercrime, preferring to handle it internally. Why? The answer involves the time and expense involved, and the probability of further disruption of business, but also the damage to the reputation and perceived vulnerability of the company. When companies are attacked and ransom is demanded, the perception is that a criminal investigation is unlikely to help recover money or data, or to prevent future incidents. In many cases companies choose to pay the ransom. Of course, paying a ransom does not guarantee that data will be returned, or a promised decryption key will be delivered. And, since the cybercriminals now possess the stolen data, they may turn and sell them after payment has been made.

## [3.2 A Brief Overview of the Legal System in the United States](#contents.xhtml#re_h-3-7)

According to Aristotle’s *Politics (350 B.C.E.)* man, when perfected, is the best of animals, but, when separated from law and justice, he is the worst of all.^([^(121)](#fn121))

![FIGURE 3.2 A basic guide to the main sources of law in the United States.](images/fig3.2.jpg)

**FIGURE 3.2** A basic guide to the main sources of law in the United States.

In the United States the main categories of law are *Constitutional, Statutory and Agency Regulations, Judicial Decisions or Case law,* and *Administrative law*.

### [I. The Constitution](#contents.xhtml#re_h-3-8)

The U.S. Constitution,^([^(122)](#fn122))

In addition to the Constitution, each of the 50 states has its own constitution. The U.S. Constitution specifies the powers and duties of the government and guarantees specific rights to the people. It is considered a living document, since it can evolve and be amended over time.

The Constitution is separated into three sections; Preamble, Articles I through VII, and 27 Amendments. The first section, the Preamble, describes the intent and purpose of the Constitution ([Figure 3.3](#c3.xhtml#f3.3)).

![FIGURE 3.3 The Constitution of the United States (1791). Photograph from the National Archives and Records Administration (NARA).](images/fig3.3.jpg)

**FIGURE 3.3** The Constitution of the United States (1791). Photograph from the National Archives and Records Administration (NARA).

> We the People of the United States, in Order to form a more perfect Union, establish Justice, insure domestic Tranquility, provide for the common defense, promote the general Welfare, and secure the Blessings of Liberty to ourselves and our Posterity, do ordain and establish this Constitution for the United States of America.^([^(123)](#fn123))

The second section consists of seven Articles. They determine how the government is organized and how the Constitution may be revised. The final section lists the 27 Amendments to the Constitution. The first 10 amendments are known collectively as the Bill of Rights**.** It is the federal courts that interpret and evaluate the constitutionality of both federal and state laws.

> This Constitution, and the Laws of the United States which shall be made in Pursuance thereof; and all Treaties made, or which shall be made, under the Authority of the United States, shall be the supreme Law of the Land; and the Judges in every State shall be bound thereby, any Thing in the Constitution or Laws of any State to the Contrary notwithstanding.^([^(124)](#fn124))

![FIGURE 3.4 The U.S. Const. Art. VI, Clause 2. Photograph from the National Archives and Records Administration (NARA).](images/fig3.4.jpg)

**FIGURE 3.4** The U.S. Const. Art. VI, Clause 2. Photograph from the National Archives and Records Administration (NARA).

### [II. Statutory or Statute Law](#contents.xhtml#re_h-3-9)

Statutory or Statute Law consists of laws ratified by a legislative body. Because the Supremacy clause in Article VI of the constitution mandates that federal law is the highest form of law in the judicial system, a statute from any state cannot supersede federal law. When a bill is passed by the Congress and signed by the President, it becomes a Public Law (Pub.L.). When there is a conflict between state and federal laws, judges are required to follow federal law.

Most laws passed by Congress are public laws. The first full version of public and private laws, also known as *slip laws***,** consists of the entire bill as it was passed by both legislative houses and signed by the President.

Public laws influence issues that affect the general population or society. Because identical versions of public laws must pass each legislative chamber and be signed by the President, the process of negotiation between the Senate and the House of Representatives can lead to public laws that address disparate subject matters.

Private laws**,** on the other hand, influence the rights and responsibilities of specifically identified individuals, families, businesses, or small groups. For example, if the government wants to grant citizenship to an individual who would be ineligible based on applicable immigration law, that measure would be passed as a private law. See, e.g., Private Law 112-1 (Dec. 28, 2012).^([^(125)](#fn125))

When a Public law is enacted, the legislature assigns it a specific number. This number includes the session of Congress in which it was passed. For example, Pub. L. 116-7 is the seventh law enacted during the 116th Congress. They are collected and codified in the Office of the Law Revision Counsel of the United States House of Representatives (OLRC).^([^(126)](#fn126))

The U.S. Code contains the federal laws of the United States arranged into *54 broad titles*, according to subject matter.^([^(127)](#fn127))

For example, **18 U.S. Code § 1030 (a)(3)** may be understood as follows:

*   Title **18 of the U.S. Code** is the principal criminal code of the federal government for crime and criminal procedures.
*   In Title 18, Chapter 47 covers Fraud and false statements (18 USC Ch. 47: FRAUD AND FALSE STATEMENTS),^([^(128)](#fn128))
*   **§ 1030** is the section covering Fraud and related activity in connection with computers. This refers to the Computer Fraud and Abuse Act (CFAA), which outlaws conduct that victimizes computer systems.
*   Paragraph (a)(3) condemns unauthorized intrusion (“hacking”) into federal government computers.

The section sign **§** is a typographical symbol that refers to a reference in a particular section of a document in the legal code. It is also called the *double S* or the *sectional symbol or sign.* In Latin this is known as *signum sectionis*, meaning section symbol ([Figure 3.5](#c3.xhtml#f3.5)).

![FIGURE 3.5 Understanding a Statute Citation.](images/fig3.5.jpg)

**FIGURE 3.5** Understanding a Statute Citation.

When Congress passes laws, it can codify standards or delegate the codification of standards, indicating which federal agencies implement, manage, and evaluate statutorily-authorized programs. The U.S. Code system (U.S.C.), described above, is a codification system for federal laws, while the Code of Federal Regulations (C.F.R.) codifies permanent rules issued by the departments and agencies of the federal government. The CFR is also split by subject matter. It contains *50 titles* that represent wide-ranging areas and subjects of federal regulation.^([^(129)](#fn129))

### [III. Administrative Laws (Agency Regulations) and Ordinance Law](#contents.xhtml#re_h-3-10)

Administrative laws are also known as Agency Regulations. Ordinance Laws are considered local. Administrative Regulations are crafted by administrative agencies of federal and state governments. Administrative law is supposed to be enacted by “experts” in a certain field rather than elected representatives. Federal administrative agencies ratify, enforce, and sometimes even judge these violations. For example, the Food and Drug Administration (FDA), an agency within the U.S. Department of Health and Human Services (HHS), is authorized to pursue both civil and criminal actions, during which they can seize and regulate foods, human and veterinary drugs, vaccines, medical devices intended for human use, radiation-emitting electronic products, cosmetics, dietary supplements, and tobacco products. The FDA does not regulate meat, poultry, and egg products, which are regulated by the U.S. Department of Agriculture (USDA). The USDA can authorize both civil and criminal remedies for violations. Administrative agencies interpret laws and apply their own guidelines and standards to enforce them.

An *Ordinance* is a law passed by the governing body of a municipality like a city or county. These governing bodies include city and county councils, boards of supervisors, and county commissions. Ordinances govern matters that do not conflict with state or federal laws. Some examples of ordinance law are safety, and city zoning and building regulations, which regulate construction and repair of damaged buildings.

Finally, chief executives (the President and the Governors) can issue executive orders that have the effect of law.

### [IV. Judicial Decisions or Precedents or Case Law](#contents.xhtml#re_h-3-11)

This type of law originates from English *Common Law*, where precedents and authority are set by previous court rulings. Case law is created when judges follow the judicial decisions made by court rulings in a prior case. Case law is used by lower courts and judges to identify which law applies to a dispute, to establish criminal procedure, or to create a criminal defense for a crime. In 49 states, laws are largely derived from English Common Law, but in Louisiana, laws are based on the French Civil Code.

In the United States, laws are ratified, explained, and enforced by the federal, state, and local levels of government. The hierarchy of the laws of the United States is:

*   U.S. Constitution
*   Laws enacted by U.S Congress
*   Agency regulations by federal agencies
*   State Constitutions
*   Laws ratified by a State Legislation
*   Rules and regulations by State Agencies
*   Ordinances (city or county)
*   Rules and regulations by Local or City agencies.

### [3.2.1 The Courts System](#contents.xhtml#re_h-3-12)

The Judicial system is classified by a hierarchical structure at both state and federal levels. federal and state governments, along with U.S. territories, have separate court systems. For the most part, each has *District* courts**,** *Appeals* courts**,** and *Supreme* courts, in addition to various courts at local levels, for example traffic court.

![](images/inline3.3.jpg)

Federal jurisdiction consists of U.S. District Courts and U.S. Courts of Appeals or Circuit Courts, which are the first level of appeal, and finally the U.S. Supreme Court, the final level of appeal. Although Article III of the U.S. Constitution requires the establishment of District Courts, these were established pursuant to the Judiciary Act of 1789. U.S. District Courts handle civil and criminal trials within the federal court system. These 94 district or trial courts are organized in 12 regional circuits.

The U.S Appeals Court consists of 13 appellate courts. These courts oversee civil and criminal cases inside clear geographic or subject areas. Federal Courts function differently than State courts.

Federal courts hear only cases authorized by the U.S. Constitution or federal statutes. The federal government can prosecute criminal offenses only in federal courts, and the States must bring criminal prosecutions only in State courts. In addition, according to the Fifth Amendment to the U.S. Constitution, the legal term *Double Jeopardy* means that a defendant cannot be prosecuted twice for the same or similar charges.

> No person shall be held to answer for a capital, or otherwise infamous crime, unless on a presentment or indictment of a Grand Jury, except in cases arising in the land or naval forces, or in the Militia, when in actual service in time of War or public danger; nor shall any person be subject for the same offence to be twice put in jeopardy of life or limb; nor shall be compelled in any criminal case to be a witness against himself, nor be deprived of life, liberty, or property, without due process of law; nor shall private property be taken for public use, without just compensation. (U.S. Const. amend. V (1791); see [Figure 3.6).](#c3.xhtml#f3.6)

![FIGURE 3.6 The U.S. Const. amend. V (1791). Photograph from the National Archives and Records Administration (NARA).](images/fig3.6.jpg)

**FIGURE 3.6** The U.S. Const. amend. V (1791). Photograph from the National Archives and Records Administration (NARA).

Nonetheless, Double Jeopardy is not reciprocal between federal and state governments. The federal government can bring its own prosecution if the defendant violated both state and federal laws; if a state brings charges and does not win a conviction, the federal government may file charges against the defendant if the act is also illegal under federal law. Furthermore, double jeopardy applies only to criminal cases, not civil cases. In the Supreme Court case *Gamble v. United States*, 139 S. Ct. 1960; 204 L. Ed. 2d 322, 587 U. S. \_\_\_\_ (2019), the court held that under the Dual-Sovereignty Doctrine, both state and federal courts may prosecute an individual without violating Double Jeopardy. Thus, a state may prosecute a defendant under state law even though the federal government has prosecuted the defendant for the same conduct under federal law. Justice Alito wrote in the majority opinion that “Under this ‘dual-sovereignty’ doctrine, a State may prosecute a defendant under State law even if the Federal Government has prosecuted him for the same conduct under a Federal statute. Or, the reverse may happen, as it did here.”^([^(130)](#fn130))

The Supreme Court has the discretion to choose the cases it will hear, and not all cases are heard. When most of the justices vote to hear a case, this is called *granting certiorari*, often condensed to *cert***.**

The Supreme Court hears appeals from the U.S. Courts of Appeals or Circuit Courts, as well as U.S. military courts and State Supreme Courts on decisions involving the U.S. Constitution or federal laws and regulations. Because the U.S. Supreme Court is the highest court in the federal court system, once the Supreme Court hands down a decision it is final. The Supreme Court’s decision is considered a binding precedent on all lower courts.

Supreme Court justices and justices of the lower federal courts are appointed by the President and must be confirmed by the U.S. Senate. They usually hold their positions for life. According to U.S. Const. art. III, § 1, “The Judges, both of the supreme and inferior Courts, shall hold their Offices during good Behaviour.” [Figure 3.7](#c3.xhtml#f3.7) displays the three-part structure of the federal court system.

![FIGURE 3.7 The three-part structure of the federal court system.](images/fig3.7.jpg)

**FIGURE 3.7** The three-part structure of the federal court system.

For most states, the judicial system consists of State Trial courts, State Appellate courts, and State Supreme courts. Cases begin in the Trial courts, and the plaintiff and defendant present evidence to prove the facts in a case. A jury of citizens sworn to listen to the facts and make decisions, brings in the verdict.

The trial courts and federal district courts are the only courts that use the Jury system. Although there are codified rules governing the admissibility of evidence, District court judges, can determine what evidence may be used. These courts follow constitutional and legal precedents set by higher courts like Appeals and Supreme courts.

If a defendant considers the verdict unfair, the case may be appealed, and it is sent to the appropriate Appellate court, usually called the Appeals court. This court hears and reviews legal cases that have already been heard in a lower court. In Appellate court, the lawyers argue before a judge or a panel of judges, focusing on legal and policy principles.

Each State in the United States plus the District of Columbia has at least one Supreme Court. Oklahoma and Texas each have two Supreme Courts, one for civil and one for criminal appeals. While the State Supreme Courts hear appeals on legal issues from lower state courts, the U.S. federal courts may overrule a state Supreme Court decision if it is a ruling on a question of federal law.

## [3.3 Types of Laws](#contents.xhtml#re_h-3-13)

Major areas of the law include Bankruptcy, Business or Corporate, Civil Rights, Cyber, Entertainment, Environmental Law, Family, Health, Intellectual Property, International, Labor or Employment Law, Maritime, Real Estate, and Tax Law.

The three types of law that concern cybercriminals are Administrative, Civil, and Criminal laws. These laws are administered during legal proceedings.

A legal proceeding is a procedure or legal action in a court of law or arbitration panel instituted in order to enforce the law. In a proceeding, the participants present evidence based on an argument that supports their claims on how to interpret the law.

### [3.3.1 Administrative Law](#contents.xhtml#re_h-3-14)

Earlier in the chapter we defined Administrative law as powers, or regulations created and enforced by administrative agencies of federal, state, and local levels of government. Administrative law is also comprised of less binding guidance that is supposed to help industry participants understand and implement the governing regulations.

The U.S. Constitution refers to the three branches of government as: Legislative, Executive, and Judicial according to “U.S. Const. art. I”, “U.S. Const. art. II”, and “U.S. Const. art. III”. Administrative agencies are not referred to in the U.S. Constitution, but unofficially, have been called the fourth branch of government. They are officially part of the Executive branch, which is why their department heads are appointed by the President.

Executive Orders are enforceable to the extent they act within an administrative sphere. Other important groups referred to in this manner include the press, advocacy groups, and institutions that are perceived to have influence in the three branches of government. While the free press is called the fourth estate, it is incorrect to call it the fourth branch of government – instead it is an outside entity designed to limit the power of government.

Federal agencies are responsible for protecting the public and ensuring compliance with civil rights, privacy, security, and safety. For example, the Clean Air Act of 1963, 42 U.S.C. § 7401, is administered by Environmental Protection Agency (EPA). The agency has the power to enforce, inspect, investigate complaints, hold hearings, and issue penalties for violations without prior judicial process. This is called non-judicial enforcement. These actions are enforced in coordination with state and local governments.

Certain agencies are authorized to pursue legal action for violations of rules, regulations, or statutes. For example, the Securities and Exchange Commission (SEC) and Drug Enforcement Administration (DEA), which is part of the Justice Department (DOJ), both have the authority to begin civil or criminal litigation against a person or business. The table below lists some of the federal agencies in the United States ([Table 3.1)](#c3.xhtml#t3.1).

 **TABLE 3.1** Major Federal Agencies in the United States 

 
| Major Federal Agencies  |
| --- |
| Agriculture Department || Interior Department |
| --- | --- |
| Arms Control || International Development Agency |
| Central Intelligence Agency (CIA) || International Trade Commission (USITC) |
| Civil Rights Commission || Justice Department (DOJ) |
| Commerce Department || Labor Department |
| Commodity Futures Trading || National Aeronautics and Space Administration (NASA) |
| Consumer Products Safety || National Archives |
| Census Bureau || National Foundation of Arts & Humanities (NEH) |
| Defense Department || National Labor Relations Board (NLRB) |
| Defense Nuclear Safety Board || National Science Foundation (NSF) |
| Education Department || National Transportation Safety Board (NTSB) |
| Energy Department || Nuclear Regulatory Commission (NRC) |
| Environmental Protection Agency (EPA) || Occupational Safety & Health (OSH) |
| Equal Employment Opportunity || Office of Government Ethics (OGE) |
| Federal Communications Commission (FCC) || Office of Personnel Management (OPM) |
| Federal Election Commission (FEC) || Peace Corps |
| Federal Emergency Management Agency (FEMA) || Postal Service (USPS) |
| Federal Labor Relations (FLRA) || Securities and Exchange (SEC) |
| Federal Maritime Commission (FMC) || Small Business Administration |
| Federal Mine Safety || Social Security Administration |
| Federal Trade Commission (FTC) || State Department |
| Food and Drug Administration (FDA) || Trade & Development Agency (USTDA) |
| Health & Human Services (HHS) || Transportation Department |
| Homeland Security || Treasury Department |
| Housing and Urban Development (HUD) || Veteran's Affairs (VA) |

### [3.3.2 Civil Law](#contents.xhtml#re_h-3-15)

Civil law covers disagreements between two or more private individuals, an organization, a company, or two private parties (*person vs person*). In a civil trial, the party making a claim of wrongdoing is called the *plaintiff***.** The accused party is called the *defendant*, and the process of settling or resolving a dispute is called *litigation*. In both civil and criminal trials, an individual may be sued for the same act. An example is found in the notorious O.J. Simpson case, which involved a criminal trial for murder and a civil trial for wrongful death.

A *tort* is a Civil wrong, meaning an injury that causes a plaintiff to suffer loss or harm and permits a lawsuit seeking monetary compensation. The goal of a *tort suit* (civil lawsuit) is to compensate the plaintiff for any injuries.

> Wrong; injury; the opposite of right, So called, according to Lord Coke, because it is wrested, or crooked, being contrary to that which is right and straight.^([^(131)](#fn131))

### [3.3.3 Criminal Law](#contents.xhtml#re_h-3-16)

Criminal law deals with individuals who commit criminal wrongs, violating one or more of society’s laws. These laws keep the public safe and deter criminal conduct. In criminal cases, it is the government or the state, not another person, that brings charges against a person or persons. In a criminal case, the state is represented by a *prosecutor* or *district attorney*, and the *defendant* by a *criminal defense lawyer***.** A victim of a crime may file a complaint and report a crime to the police, but only the government or the state can bring criminal charges. Criminal offenses are divided into two categories based on the severity of the offense: *felonies*, severe crimes such as murder, rape, burglary, kidnapping, and arson, and *misdemeanors*, less severe crimes punishable by a fine and/or imprisonment. [Figure 3.8](#c3.xhtml#f3.8) illustrates the U.S. legal process, including international laws and treaties. [Table 3.2](#c3.xhtml#t3.2) provides brief definitions for legal terms used in this chapter.

![](images/inline3.4.jpg)![FIGURE 3.8 The legal process in the United States including international laws and treaties.](images/fig3.8.jpg)

**FIGURE 3.8** The legal process in the United States including international laws and treaties.

 **TABLE 3.2** Glossary of the Legal Terms 

 
| Glossary  |
| --- |
| Admissible || Evidence that may be considered in civil and criminal cases. |
| --- | --- |
| Affidavit || A sworn statement (written or printed) prepared under oath. |
| Burdens of Proof civil cases || The burden of proof in a civil case is “preponderance of the evidence,” meaning the plaintiff must prove the case with most – at least 51% – of the evidence. |
| Burdens of Proof criminal cases || The burden of proof for a prosecutor to successfully prove a criminal case is “beyond a reasonable doubt.” The defendant is by law assumed innocent until the prosecution proves his or her guilt. If the prosecution fails to prove guilt, the defendant goes free. |
| Class action lawsuit or class suit || Lawsuit to address the injuries of a group of people instead of an individual. |
| Common Law || Originating from the English Common Law, in accordance with custom and legal precedents and authority set by previous court ruling. |
| Circumstantial evidence || Circumstantial evidence is evidence gleaned not from direct observation but by inference. For example, finding one’s fingerprints at the scene of a crime is circumstantial evidence that one was present. |
| Digital or Electronic evidence || Digital information that may be used as evidence in a lawsuit or trial, such as e-mails, pictures, videos, browser history, files stored on a computer hard drive, file fragments or data items stored in memory, and information transmitted over a network, like data found in cloud storage. |
| Probable cause || Probable cause is enough evidence for the government to arrest a suspect or press charges. |
| Subpoena || A written summons to make an individual to testify, often before a court or in other proceedings. If an individual does not comply, he or she may be held in civil or criminal contempt. |
| Search Warrant || A legal document issued by a judge or magistrate allowing law enforcement or other officials to enter and search a location. The Fourth Amendment of the U.S. Constitution restricts the government against unreasonable searches and seizures without a warrant. |
| Testimony || Testimony is information provided under oath in a hearing or other official procedure. |
| Writ Certiorari or Cert || When a party is not satisfied with a decision by a lower court, the party requests that the U.S. Supreme Court hear the case by petition for *Writ of Certiorari.* |

## [3.4 Conclusion](#contents.xhtml#re_h-3-17)

Cybercrime is continually on the rise, and governments around the world have enacted cybersecurity-related legislation to safeguard privacy, enhance security, and protect the rights of citizens. Before we can understand the complexity of this legislation, we must have a basic understanding of the organization and workings of the U.S. Judicial System. Learning the basics of law can help us identify which legislation is pertinent to a particular cybercrime.

Citizens and businesses can be more proactive about protecting their rights and their data if they understand how laws are structured and know how to take action against cybercrime.

## [3.5 Key Words](#contents.xhtml#re_h-3-18)

 
| Administrative law || Jurisdiction |
| --- | --- |
| Agency Regulations || Legal system (Supreme, Courts of Appeal or Circuit Courts, District Courts) |
| Anonymity ||  |
| Burdens of Proof ||  |
| Case law || Misdemeanor |
| Circumstantial evidence || Ordinance |
| Civil law || Plaintiff |
| Common Law || Probable cause |
| Courts system || Prosecutor |
| Criminal law Extradition || Search Warrant |
| Defendant || Subpoena |
| Digital evidence || Tort |
| Double Jeopardy || U.S. Constitution |
| Felony ||  |

# [Chapter 4 Laws, Standards, and Regulations Affecting Cybercrime](#contents.xhtml#re_c4)

DOI: [10.4324/9780429318726-4](https://doi.org/10.4324/9780429318726-4)

## [Objectives](#contents.xhtml#re_h-4-1)

After completing this chapter, the student will be able to:

*   Define cyber law.
*   Understand anti-hacking laws.
*   Understand data security laws in critical infrastructure, financial institutions, and healthcare.
*   Understand the National Institute of Standards and Technology (NIST) Cybersecurity Framework.
*   Understand public and private sector partnerships laws.
*   Understand surveillance laws and privacy law.

## [4.1 Introduction](#contents.xhtml#re_h-4-2)

Cyber law, also called information technology law, or Internet law, pertains to laws involving technology related to the Internet and includes computers and networks. Cyber law is a newer area of the legal system. It pulls from many areas of traditional law and provides legal protection for individuals using the Internet.

This type of law is wide reaching, encompassing cyberbullying and cyberstalking, access to the Internet, intellectual property infringement, consumer protection, financial crimes, freedom of expression, online privacy, jurisdiction, and First and Fourth Amendment rights.

Cybersecurity is one of the fastest-growing challenges across the globe and is becoming increasingly important. Furthermore, cybersecurity has enormous implications for government security, economic prosperity, and public safety. Cyber laws have been enacted by every nation. In the United States, the federal government and individual states are improving cybersecurity through legislation, better security measures and security practices, increasing fines for computer crimes, and addressing the most serious cyber risks to critical infrastructure.

### [4.1.1 Current Legislative Framework in the United States](#contents.xhtml#re_h-4-3)

Like other countries, the United States does not have a single piece of national legislation but instead has many statutes and regulations enacted by federal agencies, called Federal Regulations (CFR), that address various aspects of cybersecurity.

Additionally, the U.S. Constitution provides privacy protection through the First Amendment, which ensures the freedoms of Religion, Speech, Press, Assembly, and Petition—“U.S. Const. Amend. I (1791)”—and the Fourth Amendment, with its provisions against Search and Seizure—“U.S. Const. Amend. IV (1791).”

It is impossible within the scope of this chapter to outline all federal, state, and local laws related to cyberspace. Accordingly, this chapter will outline the most important cyberlaws and highlight the importance of federal agencies in creating them.

Furthermore, some laws in this chapter may overlap with others, and some laws will address different issues that arise from the same events. In some cases, we will return to laws we have discussed before when they address different aspects of cybercrime.

The chapter is organized into six major categories. Each outlines the most important legislation in that category, as well as the agencies responsible for enforcing the laws and for issuing criminal charges or penalties. Case studies will clarify how these laws make us safer.

1.  I. **Anti-hacking (unauthorized computer access) laws** 
    *   Computer Fraud and Abuse Act (CFAA) (18 U.S.C. § 1030)
    *   The Economic Espionage Act of 1996 (EEA) (18 U.S.C. § 1831 et seq.)
    *   The Digital Millennium Copyright Act (DMCA)
2.  II. **Data security laws and regulations in private sector entities** 
    *   National Institute of Standards and Technology (NIST); Cybersecurity Framework for private sector organizations
    *   Laws Dealing with Healthcare: The Health Insurance Portability and Accountability Act (HIPAA), and Health Information Technology for Economic and Clinical Health Act (HITECH)
    *   Federal Trade Commission (FTC) and Section 5
    *   Laws Affecting Financial Institutions (The Gramm–Leach–Bliley Act of 1999 (GLBA), Red Flags Rule)
    *   Laws Affecting Utilities (The Federal Energy Regulatory Commission (FERC), and Nuclear Regulatory Commission (NRC))
3.  III. **Cybersecurity in public and private sector entities partnerships** 
    *   Cybersecurity Information Sharing Act of 2015 (CISA), designed to increase the sharing of cybersecurity threats between the federal and private sector entities to protect privacy and civil liberties
    *   The Cybersecurity and Infrastructure Security Agency (CISA), The National Cybersecurity and Critical Infrastructure Protection Act of 2014 (NCPA), and the Cybersecurity Enhancement Act of 2014 (CEA)
4.  IV. **Cybersecurity requirements for federal government contractors** 
    *   Federal Information Security Modernization Act of 2014 (FISMA)
    *   NIST Information Security Controls for Government Agencies and Contractors
5.  V. **Most important Internet surveillance laws in the United States** 
    *   The Fourth Amendment
    *   USA PATRIOT Act and Freedom Act
    *   Electronic Communication Privacy Act (ECPA) of 1986
    *   Communication Assistant for Law Enforcement Act of 1994 (CALEA)
    *   All Writs Act
6.  VI. **Key privacy laws in the United States** 
    *   Privacy Act of 1974
    *   Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003 (CAN-SPAM Act). Unsolicited commercial e-mails “spam,” false or misleading header information, misleading subject lines, and commercial email that can be identified as an advertisement
    *   18 U.S.C. § 1037. Fraud and Related Activity in Connection with Electronic Mail
    *   18 U.S.C. § 1029. Fraud and Related Activity in Connection with Access Devices
    *   18 U.S.C. § 1028. Fraud and Related Activity in Connection with Identification Documents, Authentication Features, and Information 
    *   Children’s Online Privacy Protection Act of 1998 (COPPA)
    *   Video Privacy Protection Act (VPPA) of 1988
    *   Why the United States began taking privacy seriously (California’s Privacy Law and Illinois Biometric Information Privacy Act)

State and local governments have enacted laws to protect their citizens from concerns over surveillance and the right to privacy when using mobile devices and the Internet of Things (IoTs).^([^(132)](#fn132))

It is important to note how differently nations and states view privacy and surveillance. For example, when the USA PATRIOT Act: Preserving Life and Liberty^([^(133)](#fn133))

Internationally, one of the most important laws on privacy and data protection is the European Union’s General Data Protection Regulation (GDPR).^([^(134)](#fn134))

In contrast, Australia passed a controversial law that has been viewed as a repression of freedom. The Telecommunications and Other Legislation Amendment Act of 2018^([^(135)](#fn135))

Some nations recognize their responsibility to protect data and will introduce or modify cyber laws to protect individuals’ personal information. Other nations have quite a different approach, pushing back against encryption protocols that could protect their citizens against terrorist threats and crime. It is important to understand that security relies on this cryptography to keep information secure. People depend on secure communication for shopping online, managing their bank accounts, or using technology for personal or business communications.

It is worth noting that state governments like California have enacted their own privacy laws to protect consumers and give them more control over their data. One of the first of its kind, the California Consumer Privacy Act (CCPA)^([^(136)](#fn136))

Cybersecurity laws and regulations are designed to protect individuals’ privacy rights and systems and information from cyberattacks. The following are the six categories of U.S. law associated with cyberspace in either federal or private sectors. Additionally, at the end of the chapter, [Tables 4.5](#c4.xhtml#t4.5) and [4.6](#c4.xhtml#t4.5) summarize the most important federal laws concerning cybercrime in the United States.

## [4.2 Anti-Hacking Laws](#contents.xhtml#re_h-4-4)

Anti-hacking laws enable the government to bring criminal charges against individuals who hack computer systems without consent or lawful authorization. Criminal sentences can result in a prison sentence of 1 year for accessing a computer and obtaining information, up to 10 years for obtaining national security information, and/or a fine (see [Table 4.1](#c4.xhtml#t4.1)). Even though penalties are mostly for criminal offenses, they may also include causes of action for civil suits in addition to criminal prosecution. Most computer hacking charges are prosecuted under the Computer Fraud and Abuse Act (18 U.S.C. § 1030).^([^(137)](#fn137))

 **TABLE 4.1** Summary of CFAA Convictions 

 
| CFAA Section  || Offense || Sentence  
(First Conviction)  
 || Maximum Sentence  
(For Second Conviction)  
 |
| --- | --- | --- | --- |
| **(a)(1)** || Obtaining National Security Information || 10 years || 20 years |
| --- | --- | --- | --- |
| **(a)(2)** || Accessing a Computer and Obtaining Information || 1 or 5 years || 10 years |
| **(a)(3)** || Trespassing in a Government Computer || 1 year || 10 years |
| **(a)(4)** || Accessing a Computer to Defraud and Obtain Value || 5 years || 10 years |
| **(a)(5)(A)** || Intentionally Damaging by Knowing Transmission || 1 or 10 years || 20 years |
| **(a)(5)(B)** || Recklessly Damaging by Intentional Access || 1 or 5 years || 20 years |
| **(a)(5)(C)** || Negligently Causing Damage and Loss by Intentional Access || 1 year || 10 years |
| **(a)(6)** || Trafficking in Passwords || 1 year || 10 years |
| **(a)(7)** || Extortion Involving Computers || 5 years || 10 years |
| Adapted from Prosecuting Computer Crimes, published by the Department of Justice. |
| --- |
| Source: Prosecuting Computer Crimes. Department of Justice. Retrieved from [https://www.justice.gov/sites/default/files/criminal-ccips/legacy/2015/01/14/ccmanual.pdf](https://www.justice.gov) |

### [4.2.1 The Federal Computer Fraud and Abuse Act](#contents.xhtml#re_h-4-5)

In the United States, the Computer Fraud and Abuse Act is the principal federal anti-hacking statute that prohibits unauthorized access to computers and networks. The Act provides both criminal and civil penalties. In the early 1980s, the release of the movie *WarGames* brought panic and concern to the public about computer-related crimes.^([^(138)](#fn138))

This was the first anti-hacking law put in place to address computer crime.

The CFAA was originally intended to address federal computer-related offenses and to protect government computer systems and financial institutions. The Act expanded with amendments in 1988, 1989, 1990, 1994, 1996, and 2001; it was expanded again by the USA PATRIOT Act 2002 and expanded once more in 2008 to include nearly any computer in the United States. The CFAA makes it a felony to deliberately access a computer without authorization. The CFAA’s prosecutions were all criminal; however, this was expanded in the 1994 amendment to include civil lawsuits as well, punishing unauthorized computer access, spreading spam, destroying computer data, password trafficking, seizure of property, and impounding the stolen information and equipment used in the attack.

In addition, the Act makes it an offense to access financial records or credit histories stored in a financial institution or to intrude into a governmental computer system. Furthermore, the Act limits federal jurisdiction to cases with a compelling federal interest, “where computers of the federal government or certain financial institutions are involved or where the crime itself is interstate in nature.”^([^(139)](#fn139))

The Act is amended as 18 U.S.C. § 1030 and was first enacted by Congress in 1986 to combat computer crime. The Act is located at Title 18, Crimes and Criminal Procedure § 1030, Fraud and Related Activity in Connection with Computers of the United States Code (unannotated).

The following is a brief summary of the seven paragraphs of subsection 1030(a).

*   **Hacking and cyber espionage**: The Federal Bureau of Investigation shall have primary authority to investigate offenses for any cases involving espionage, foreign counterintelligence, information protected against unauthorized disclosure for reasons of national defense or foreign relations, or restricted data, as defined in section 11y of the Atomic Energy Act of 1954 (42 U.S.C. 2014(y)), (a)(1). See Appendix A.
*   **Hacking to acquire information**: Hacking by means of such conduct as to having obtained information to certain governmental or financial records of a financial institution, credit, or information from any protected computer, (a)(2).
*   **Hacking in federal government’s computer**: Hacking in a governmental computer (nonpublic computer of a department or agency of the United States), (a)(3).
*   **Hacking to commit computer fraud**: Knowingly and with intent to committing fraud and obtain anything of value, unless the object of the fraud and the thing obtained consists only of the use of the computer, and the value of such use is not more than $5,000 in any 1-year period, (a)(4).
*   **Hacking to commit damage and loss**: Damage and loss of a governmental computer or knowingly causing the transmission of a program, code, or command, and as a result of such conduct, intentionally causing damage without authorization to a protected computer (for example, worm, computer virus, Trojan horse, time bomb, a denial-of-service attack, and other forms of cyberattack, cybercrime, or cyberterrorism), (a)(5).
*   **Password trafficking**: Password trafficking for a governmental computer or affecting interstate or foreign commerce. Knowingly and with intent to defraud trafficking in computer passwords or through which a computer may be accessed, (a)(6).
*   **Hacking and threads**: Threatening with intent to extort from any person any money or other thing of value, transmitting in interstate or foreign commerce any communication containing any demand or request for money or other things of value in relation to damage to a protected computer, where such damage was caused to facilitate the extortion, (a)(7).

#### [4.2.1.1 Key Terms and Major Cases to Understand CFAA](#contents.xhtml#re_h-4-6)

##### 4.2.1.1.1 Terms

*   First, the term “Without Authorization” in 18 U.S.C. §§ 1030(a)(3), (a)(5)(B), and (a)(5)(C) means an individual who does not have authorization to access a computer system. This term is differentiated from the crime “Exceed Authorized Access,” described below. An example is the case of the *United States v. Ivanov.*^([^(140)](#fn140))
*   Second, the term “Exceed Authorized Access” in 18 U.S.C. §§ 1030(a)(1), (a)(2), and (a)(4). This term means “to access a computer with authorization and to use such access to obtain or alter information in the computer that the accessor is not entitled so to obtain or alter.”^([^(141)](#fn141))

On the other hand, numerous civil cases have taken place where the defendants lost their authorization to access computer systems when they breached a duty of loyalty and good faith (*accessing the computer for an improper purpose*). Examples include the *United States v. Nosal*^([^(142)](#fn142))

##### 4.2.1.1.2 Significant Cases

1.  When the law went into effect in 1986, the first person convicted was Robert Morris in the case the *United States v. Morris*.^([^(143)](#fn143))
2.  The *United States v. Nosal*^([^(144)](#fn144))
    
    > (4) knowingly and with intent to defraud, accessing a protected computer without authorization, or exceeding authorized access, and by means of such conduct furthering the intended fraud and obtaining anything of value, unless the object of the fraud and the thing obtained consists only of the use of the computer and the value of such use is not more than $5,000 in any 1-year period.^([^(145)](#fn145))
    
      
    David Nosal filed a motion to dismiss, arguing that the CFAA is used to prosecute hackers, not individuals who accessed a computer with authorization and then afterward misused that information. Furthermore, he argued that his co-conspirators had permission to access KFI’s computers and could not have acted “without authorization”; nor could they have “exceeded authorized access.”^([^(146)](#fn146))
    
3.  In *Int’l Airport Ctrs., LLC v. Citrin*, the defendant Jacob Citrin was employed by the plaintiffs. He decided to quit the company and go into business for himself, in breach of his employment contract. Before returning the company’s computer, he erased all files by loading a program, designed to write over the files and prevent their recovery. The court concluded that Citrin violated 1030(a)(5)(B) and ruled that he had breached his duty of loyalty to the company and had exceeded authorized access. Later, the district court dismissed the plaintiff’s suit for failure to state a claim.
4.  In the *United States v. Drew*^([^(147)](#fn147))
5.  Another interesting case is the *United States v. John*.^([^(148)](#fn148))
6.  In the case *United States v. Rodriguez*,^([^(149)](#fn149))

These cases describe the wide range of readings by the courts of 18 U.S.C. 1030 in the understanding of “Without Authorization” and “Exceeded Authorized Access.” The courts are divided as to whether an individual can be found guilty of violating the CFAA simply by misusing the information to which the individual had proper access. Eventually, the U.S. Supreme Court will have to resolve the issue, as the federal courts continue to apply different definitions.

The CFAA has been used in the United States as the primary hacking law. In addition to criminal proceedings, the law allows hacking victims to bring civil lawsuits against perpetrators in certain conditions. Furthermore, many states have additional computer crime laws, and most address unauthorized access or computer hacking. The CFAA has been criticized for harsh punishment in minor offenses, unclear description of punishments, and neither deterring foreign criminals nor effectively protecting the United States against emerging cybercrime.

#### [4.2.1.2 Limitations of the CFAA](#contents.xhtml#re_h-4-9)

The CFAA Act fails to describe which offenses to prohibit, specifically regarding the terms “without authorization,” “exceeding authorized access,” and “unauthorized damage to a computer.” The courts should not be debating over whether a matter was authorized or not. Also, compensation should be restricted to real damage to data or to the methodology of accessing the computer system. Harmless or senseless examples of employees deleting emails or backing up databases when data redundancy is available should not be considered. Criminalizing acts like editing a document or shutting down a computer system without permission should not be prosecuted. The civil cases under CFAA are potentially serious crimes. The Act has become a convenient way to impose intellectual property litigation penalties by bringing a claim of theft of trade secrets. Corporations can take legal action against former employees for deleting, copying, or transferring files before or after they have left their jobs. Nevertheless, the Department of Justice has never criminally prosecuted companies for espionage, violation, or data theft. Additionally, defendants face harsh sentences of up to 20 years, depending on what part of the CFAA they violate, at times for offenses with few real damages or merits. [Table 4.1](#c4.xhtml#t4.1) demonstrates the CFAA’s convictions.

One example was an outrageous indictment for computer fraud, in the case of the *United States of America v. Aaron Swartz*.^([^(150)](#fn150))

[Table 4.1](#c4.xhtml#t4.1) displays the penalties of the CFAA Act.

*For a complete text of the CFAA and the additional amendments see Appendix A.*

### [4.2.2 Computer Hacking Laws from Individual States](#contents.xhtml#re_h-4-10)

So far, in the federal courts, most individuals accused of hacking are charged under the CFAA. In addition, all 50 states have their own computer crime laws, and most address unauthorized access to computer-based information systems or computer intrusion.

It is important to acknowledge the significance of state law. State hacking laws differ widely. Certain states prohibit unauthorized access, computer trespass, and the use of viruses and malware by addressing specific cybercrimes like Denial-of-Service (DoS), Phishing, Ransomware, and Spyware. Florida categorizes DoS as a felony in the first degree,^([^(151)](#fn151))

### [4.2.3 The Economic Espionage Act of 1996 (EEA)](#contents.xhtml#re_h-4-11)

The EEA Act,^([^(152)](#fn152))

Theft of trade secrets extends from electronic storage to actual theft. Additionally, section 1836^([^(153)](#fn153))

The Economic Espionage Act was passed in 1996 and provided punishment for foreign and corporate espionage. It was amended in 2016. The Act now allows companies to bring civil litigation for trade secrets theft;^([^(154)](#fn154))

#### [4.2.3.1 Important Cases](#contents.xhtml#re_h-4-12)

1.  Notable cases include *U.S. v. Liew*. Walter Liew^([^(155)](#fn155))

DuPont had identified titanium dioxide (TiO[2]) as a “trade secret,” and according to the Act

> (A) the owner thereof has taken reasonable measures to keep such information secret; and (B) the information derives independent economic value, actual or potential, from not being generally known to, and not being readily ascertainable through proper means by another person who can obtain economic value from the disclosure or use of the information.^([^(156)](#fn156))

2.  The case of *United States of America v. Wang Dong, Sun Kailiang, Wen Xinyu, Huang Zhenyu, Gu Chunhui*^([^(157)](#fn157))

### [4.2.4 The Digital Millennium Copyright Act](#contents.xhtml#re_h-4-13)

The DMCA emphasizes anti-circumvention laws and aims to prevent copyright infringement by punishing unauthorized users who evade or hack into copyrighted technology or software. The word “circumvention” means lack of authorization or hacking into access controls or technological protection measures (TPM), like a burglar attempting to pick a locked door.![](images/inline4.2.jpg)

On October 28, 1998, President Clinton signed into law the Digital Millennium Copyright Act.^([^(158)](#fn158))

*   **Title I**: “WIPO Copyright and Performances and Phonograms Treaties Implementation Act of 1998.” This title implements the WIPO Copyright Treaty.
*   **Title II**: “Online Copyright Infringement Liability Limitation Act.” This title creates a so-called *safe harbor* regarding the liability of online service providers (OSPs) for copyright infringement.
*   **Title III**: “Computer Maintenance Competition Assurance Act.” This title creates an exemption for making temporary, limited copies of a computer program for purposes of maintenance or repair.
*   **Title IV**: “Covers six miscellaneous provisions.” These provisions relate to the functions of the Copyright Office. It clarifies the duties of the Copyright Office, ephemeral copy for broadcasters, provisions to facilitate distance education, provisions to assist libraries with keeping and making recordings, “webcasting” of sound recordings on the Internet, and provisions of collective bargaining agreements for the transfer of movie rights.
*   **Title V**: “Vessel Hull Design Protection Act.” Protection for vessel hulls design.

Among the sections, Title II, known as the Online Copyright Infringement Liability Limitation Act, is codified as Section 512, Title 17, of the United States Code (17 U.S.C. § 512). The law protects online service providers and websites from liability for copyright infringements in certain cases. More specifically, the law contains safe-harbor provisions for service providers. The safe harbor protects them from copyright infringements, until the copyright owner establishes notice for the prompt removal of content (notice and takedown). The DMCA offers safe harbor only to OSP; individuals or subscribers may still be held liable. Lack of knowledge of the law will not exempt the user from legal consequences. Furthermore, the OSP is obligated to provide all users access to information for dealing with copyright infringement notifications and to inform users concerning violations of copyright or other intellectual property laws.

Section 107 of the Copyright Act (17 U.S.C. § 107) offers the right to use copyrighted content or work without the permission of the owner in certain conditions. This is called Fair Use. The legally permissible purposes for which the copyrighted content can be used include: News Reporting, Commentary, Research, Criticism, Scholarship, and Teaching. According to § 107,

> In determining whether the use made of a work in any particular case is a fair use the factors to be considered shall include: the purpose and character of the use, including whether such use is of a commercial nature or is for nonprofit educational purposes; the nature of the copyrighted work; the amount and substantiality of the portion used in relation to the copyrighted work as a whole; and the effect of the use upon the potential market for or value of the copyrighted work.^([^(159)](#fn159))

The purpose of Fair Use is to promote commentary, discussion, creativity, criticism, innovation, research, scholarship, and teaching.

Cybersecurity legislation involves section 1201 of the DMCA. This section was created to accomplish the aims of the WIPO Copyright Treaty and criminalizes those who “circumvent technological measures used to prevent unauthorized access to copyrighted works, including copyrighted books, movies, video games, and computer software.”^([^(160)](#fn160))

*   § 1201(a)(1) “No person shall circumvent a technological measure that effectively controls access to a work protected under this title.” This section forbids technological measures to encrypt a work, or to avoid, evade, remove, deactivate, or impair, without the authority of the copyright owner. For instance, it forbids avoiding access controls by decrypting encrypted Blu-ray/DVD disks and playing them on an unauthorized device or evading password access to music streaming services. Other examples include password cracking or evading authentication codes in video game systems to prevent playing pirated games.
*   § 1201(a)(2) “No person shall manufacture, import, offer to the public, provide, or otherwise traffic in any technology, product, service, device, or component that was designed to evade a lawful control.”^([^(161)](#fn161))
*   § 1201(b)(1) “No person shall manufacture, import, offer to the public, provide, or otherwise traffic in any technology, product, service, device, component, or part thereof, that—”.^([^(162)](#fn162))

![FIGURE 4.1 The 17 U.S.C. § 1201 statutory structure.](images/fig4.1.jpg)

**FIGURE 4.1** The 17 U.S.C. § 1201 statutory structure.

#### [4.2.4.1 Penalties for 17 U.S.C. § 1201](#contents.xhtml#re_h-4-14)

A civil suit in a federal court can be brought by an individual injured by a violation of sections 1201 or 1202.

Section § 1201 refers to

> 1.  (a) False Copyright Management Information.—No person shall knowingly and with the intent to induce, enable, facilitate, or conceal infringement— 
>     1.  1\. provide copyright management information that is false, or
>     2.  2\. distribute or import for distribution copyright management information that is false.
> 2.  (b) Removal or Alteration of Copyright Management Information.—No person shall, without the authority of the copyright owner or the law— 
>     1.  1\. intentionally remove or alter any copyright management information,
>     2.  2\. distribute or import for distribution copyright management information, knowing that the copyright management information has been removed or altered without authority of the copyright owner or the law, or
>     3.  3\. distribute, import for distribution, or publicly perform works, copies of works, or phonorecords, knowing that copyright management information has been removed or altered without authority of the copyright owner or the law.^([^(163)](#fn163))

Section 1203^([^(164)](#fn164))

> 1.  (a) In General.—Any person who violates section 1201 or 1202 willfully and for purposes of commercial advantage or private financial gain— 
>     1.  1\. shall be fined not more than $500,000 or imprisoned for not more than 5 years, or both, for the first offense; and
>     2.  2\. shall be fined not more than $1,000,000 or imprisoned for not more than 10 years, or both, for any subsequent offense.
> 2.  (b) Limitation for Nonprofit Library, Archives, or Educational Institution.—Subsection (a) shall not apply to a nonprofit library, archives, or educational institution.
> 3.  (c) Statute of Limitations.—No criminal proceeding shall be brought under this section unless such proceeding is commenced within 5 years after the cause of action arose.^([^(165)](#fn165))

#### [4.2.4.2 Important Cases](#contents.xhtml#re_h-4-15)

1.  In the case of *Friedman v. Live Nation Merchandise*,^([^(166)](#fn166))
    
    > Because there was sufficient evidence in the record to allow a reasonable jury to conclude that Live Nation willfully infringed Friedman’s copyrights and knowingly removed CMI from the images it used, we reverse the district court’s grant of summary judgment to Live Nation on those issues. We affirm the district court’s ruling as to statutory damages.^([^(167)](#fn167))
    
2.  Another interesting case is *Craigslist, Inc. v. Naturemarket*^([^(168)](#fn168))
3.  *MDY Industries, Inc. LLC v. Blizzard Entertainment*^([^(169)](#fn169))
    
    > We conclude that for a licensee’s violation of a contract to constitute copyright infringement, there must be a nexus between the condition and the licensor’s exclusive rights of copyright. Here, WoW players do not commit copyright infringement by using Glider in violation of its Terms of Use. MDY is thus not liable for secondary copyright infringement, which requires the existence of direct copyright infringement.^([^(170)](#fn170))
    

In conclusion, the court upheld the judgment that MDY Industries violated the provisions of the DMCA against section 1201(a)(2) that prohibits the circumvention of technological measures but not for related copyright infringement. This case shows the importance of contract drafting in a business relationship.

*For a complete text of section 1201, see Appendix B.*

## [4.3 Data Security Laws and Regulations in the Private Sector Entities](#contents.xhtml#re_h-4-16)

This section emphasizes the importance of partnerships between public and private sectors in terms of data security and privacy through the cooperation of federal agencies and departments working collaboratively with the private sector ([Figure 4.2](#c4.xhtml#f4.2)).

![FIGURE 4.2 The importance and intersection between public and private sector partnerships.](images/fig4.2.jpg)

**FIGURE 4.2** The importance and intersection between public and private sector partnerships.

The private sector consists of organizations that generate profits for their stakeholders and are not controlled by the government. In a public–private partnership, a government agency and private sector company may collaborate to deliver services or business ventures to the public. Since government agencies regularly collect and store citizens’ personal information, the government must agree to protect the privacy of its citizens when dealing with the private sector. As a result, the federal government, along with many states, has passed data security laws and regulations that apply to private entities involved in government business ([Figure 4.3](#c4.xhtml#f4.3)). *Failure to comply can lead to criminal and civil investigations, huge fines and penalties, sanctions, and class-action lawsuits.*

### [4.3.1 The National Institute of Standards and Technology Cybersecurity Framework](#contents.xhtml#re_h-4-17)

The National Institute of Standards and Technology is an agency of the U.S. Department of Commerce. It was founded in 1901 to set official standards for weights and measures and to serve as the national physical laboratory for the United States. From 1901 to 1988 it was known as the National Bureau of Standards (NBS) and the National Metrological Institute (NMI). In 1988, its name was changed to the National Institute of Standards and Technology ([Figure 4.4](#c4.xhtml#f4.4)).^([^(171)](#fn171))

![FIGURE 4.3 Regulations. Courtesy of Shutterstock.](images/fig4.3.jpg)

**FIGURE 4.3** Regulations. Courtesy of Shutterstock.

![FIGURE 4.4 NIST logo.](images/fig4.4.jpg)

**FIGURE 4.4** NIST logo.

The NIST Framework for Improving Critical Infrastructure Cybersecurity or the Cybersecurity Framework offers a voluntary policy framework of computer security for the private sector in the United States. While the use of the framework has been voluntary for the private sector, it has been mandated for all U.S. federal agencies by Presidents Obama and Donald Trump by executive order.^([^(172)](#fn172))

![FIGURE 4.5 Evolution of the Cybersecurity Framework. Adopted from NIST. ¶ Source: The National Institute of Standards and Technology (NIST), History and Creation of the Framework. Retrieved from https://www.nist.gov/cyberframework/online-learning/history-and-creation-framework; Barrett, Matthew P. “Framework for improving critical infrastructure cybersecurity.” National Institute of Standards and Technology, Gaithersburg, MD, USA, Tech. Rep (2018).](images/fig4.5.jpg)

**FIGURE 4.5** Evolution of the Cybersecurity Framework. Adopted from NIST.^([^(173)](#fn173)) ¶  
*Source:* The National Institute of Standards and Technology (NIST), History and Creation of the Framework. Retrieved from [https://www.nist.gov/cyberframework/online-learning/history-and-creation-framework;](https://www.nist.gov) Barrett, Matthew P. “Framework for improving critical infrastructure cybersecurity.” National Institute of Standards and Technology, Gaithersburg, MD, USA, Tech. Rep (2018).

In 2014, after an executive order, NIST released version 1.0 of the Framework for Improving Critical Infrastructure Cybersecurity. Congress approved the role of NIST’s Framework in the Cybersecurity Enhancement Act of 2014^([^(174)](#fn174))

1.  I. The **Core** comprises three parts: Functions, Categories, and Subcategories. The five functions, also shown in [Table 4.2](#c4.xhtml#t4.2), are: 
    
    *   Identify—Develop the organizational understanding to manage cybersecurity risk to systems, assets, data, and capabilities.
    *   Protect—Develop and implement the appropriate safeguards to ensure delivery of critical infrastructure services.
    *   Detect—Develop and implement the appropriate activities to identify the occurrence of a cybersecurity event.
    *   Respond—Develop and implement the appropriate activities to take action regarding a detected cybersecurity event.
    *   Recover—Develop and implement the appropriate activities to maintain plans for resilience and to restore any capabilities or services that were impaired due to a cybersecurity event.^([^(175)](#fn175))
    
     **TABLE 4.2** The Core 
    
     
    | Function *   II. The **Implementation Tiers** describe how an organization assesses, evaluates, and manages the cybersecurity risk as defined in the framework. The four tiers show progress from Partial (Tier 1) to Risk Informed (Tier 2) Repeatable (Tier 3), and finally Adaptive (Tier 4).
    *   III. In the **Profiles** an organization may conduct a self-assessment and identify and improve cybersecurity outcomes based on business needs.
    
    ### [4.3.2 Laws Dealing with Healthcare](#contents.xhtml#re_h-4-18)
    
    #### [4.3.2.1 The Health Insurance Portability and Accountability Act (HIPAA)](#contents.xhtml#re_h-4-19)
    
    HIPAA is a federal law that requires the formation of national standards to protect patients’ privacy, confidentiality, and security of health information ([Figure 4.6](#c4.xhtml#f4.6)). Specifically, the law protects patients’ medical information from disclosure without the patient’s knowledge and permission. The law (Pub. L. 104–191)^([^(176)](#fn176))
    
    ![FIGURE 4.6 HIPAA logo.](images/fig4.6.jpg)
    
    **FIGURE 4.6** HIPAA logo.
    
    The *Privacy Rule* protects “individually identifiable health information”^([^(177)](#fn177))
    
    The *Security Rule* concentrates on the technical safeguards—“technology and the policy and procedures for its use that protect electronic protected health information and control access to it”^([^(178)](#fn178))
    
    1.  I. **Health care provider**: doctors, clinics, psychologists, dentists, nursing home pharmacists.
    2.  II. **A health plan**: health insurance companies, health maintenance organization (HMO), company health plans, government-sponsored programs like Medicare and Medicaid, and veterans’ health care programs.
    3.  III. **A health care clearinghouse**: “public or private entity, including a billing service, repricing company, or community health information system, which processes non-standard data or transactions received from one entity into standard transactions or data elements, or vice versa.”^([^(179)](#fn179))
        
        > The “covered entities” are defined in the HIPAA rules as “(a) Except as otherwise provided, the standards, requirements, and implementation specifications adopted under this subchapter apply to the following entities: (1) a health plan, (2) a health care clearinghouse, (3) a health care provider who transmits any health information in electronic form in connection with a transaction covered by this subchapter. (b) Where provided, the standards, requirements, and implementation specifications adopted under this subchapter apply to a business associate.”^([^(180)](#fn180))
        
    
    “Business Associates” are individuals or organizations who come in contact with or may disclose Protected Health Information (PHI). Examples include accountants, billing company services, cloud storage, email services, healthcare app developers, legal services, IT contractors, and web hosting services. In addition, HIPAA requires a contract or a “Business Associate Agreement” with companies or individuals to safeguard the PHI it receives or creates on behalf of the *covered entity*.
    
    “Business Associates” are defined as (i) a health information organization, e-prescribing gateway, or other “person that provides data transmission services with respect to protected health information to a covered entity and that requires access on a routine basis to such protected health information. (ii) A person that offers a personal health record to one or more individuals on behalf of a covered entity. (iii) A subcontractor that creates, receives, maintains, or transmits protected health information on behalf of the business associate.”^([^(181)](#fn181))
    
    #### [4.3.2.2 Penalties for Violating HIPAA Rule](#contents.xhtml#re_h-4-20)
    
    Violations under HIPAA are very costly. The penalties are based on the level of negligence and can be both civil and criminal. Also, penalties may be imposed on a person or covered entity. For example, under section 13410(D) of the HITECH Act, when a covered entity or person did not know of a violation, “and by exercising reasonable diligence would not have known,”^([^(182)](#fn182))
    
    *For HIPAA Act sections: § 164.308 Administrative safeguards, § 164.310 Physical safeguards, § 164.312 Technical safeguards, and § 164.314 Organizational requirements see Appendix C.*
    
    ### [4.3.3 Health Information Technology for Economic and Clinical Health Act](#contents.xhtml#re_h-4-21)
    
    The HITECH Act^([^(183)](#fn183))
    
    *For HITECH Act, § 13410 Improved Enforcement, see Appendix D.*
    
    ### [4.3.4 Protecting Consumers’ Privacy Rights with FTC’s Section 5: Federal Trade Commission Act](#contents.xhtml#re_h-4-22)
    
    The Federal Trade Commission is a U.S. federal agency responsible for protecting consumers from unfair business practices and for improving competition across the economy ([Figure 4.7](#c4.xhtml#f4.7)). The FTC Act of 1914 founded the Commission and was signed into law by President Woodrow Wilson.^([^(184)](#fn184))
    
    ![FIGURE 4.7 Federal Trade Commission logo.](images/fig4.7.jpg)
    
    **FIGURE 4.7** Federal Trade Commission logo.
    
    The FTC has extensive authority to enforce a variety of laws covering privacy and data security. These include the Truth in Lending Act (TILA),^([^(185)](#fn185))
    
    #### [4.3.4.1 Important FTC Cases](#contents.xhtml#re_h-4-23)
    
    The FTC has charged offenders who have violated section 5 of the FTC Act. Additionally, it imposes other federal laws regarding consumers’ privacy and security.
    
    1.  *Google LLC and YouTube, LLC* (Civil Action Number:1:19-cv-02642). In 2019, the FTC and the New York Attorney General’s office claimed that Google and YouTube collected personal information from children under 13 years without parental consent. Specifically, YouTube’s video sharing service violated the law by using cookies to track children’s personal information without parental consent. As a result, Google and its subsidiary YouTube agreed to pay a $170 million civil penalty to settle the allegations.
    2.  In another case, CVS Pharmacy (FTC File No. 072 3119) (C-2459), one of the largest pharmacies in the United States, was charged with failing to take appropriate security measures to protect sensitive financial and medical information for its customers and employees.
    
    > CVS pharmacies around the country threw confidential information into the garbage, including pill bottles with patient information, orders with social security numbers, credit card numbers, and driver’s license numbers. HHS opened its own investigation into CVS’s disposal of health information protected by HIPAA. As a result, the company agreed to pay $2.25 million to settle the matter with HHS.
    
    Most cases settle with FTC without the expense and publicity of a trial. One example is the $5 billion penalty imposed on Facebook for violating consumers’ privacy, the largest privacy or data security penalty imposed worldwide.
    
    > “Despite repeated promises to its billions of users worldwide that they could control how their personal information is shared, Facebook undermined consumers’ choices,” said FTC Chairman Joe Simons. “The magnitude of the $5 billion penalty and sweeping conduct relief are unprecedented in the history of the FTC. The relief is designed not only to punish future violations but, more importantly, to change Facebook’s entire privacy culture to decrease the likelihood of continued violations. The Commission takes consumer privacy seriously and will enforce FTC orders to the fullest extent of the law.”^([^(186)](#fn186))
    
    The FTC has extraordinary powers; Congress has given it unparalleled investigative and prosecutory power. It can investigate any business practice in the name of consumer protection.
    
    *For FTC’s § 5 see Appendix E.*
    
    ### [4.3.5 Laws Affecting Financial Institutions](#contents.xhtml#re_h-4-24)
    
    ### [4.3.5.1 The Gramm-Leach-Bliley Act of 1999 (GLBA)](#contents.xhtml#re_h-4-25)
    
    The growth of mobile technology and the digital transformation of financial institutions have produced major concerns about privacy and misuse of data. Each financial institution retains information about its customers: names, addresses, email addresses, motor vehicle license numbers, passport numbers, financial data, and social security numbers. Penalties for not protecting this data carry hefty consequences including loss of coverage from the Federal Deposit Insurance Corporation (FDIC), resulting at the end of the financial firm’s business.
    
    ![](images/inline4.3.jpg)
    
    The Gramm–Leach–Bliley Act^([^(187)](#fn187))
    
    The most significant section of the GLBA is the Safeguards Rule, stating that any financial institution must protect the consumer information they collect. In addition to having measures in place to keep customer information secure, Gramm–Leach–Bliley requires federal regulating agencies to adopt administrative, technical, and physical safeguards for the instructions that they regulate.
    
    > TITLE V—PRIVACY Subtitle A—Disclosure of Nonpublic Personal Information
    > 
    > 15 USC 6801. SEC. 501. PROTECTION OF NONPUBLIC PERSONAL INFORMATION.
    > 
    > 1.  (a) PRIVACY OBLIGATION POLICY. It is the policy of the Congress that each financial institution has an affirmative and continuing obligation to respect the privacy of its customers and to protect the security and confidentiality of those customers’ nonpublic personal information.
    > 2.  (b) FINANCIAL INSTITUTIONS SAFEGUARDS. In furtherance of the policy in subsection (a), each agency or authority described in section 505(a) shall establish appropriate standards for the financial institutions subject to their jurisdiction relating to administrative, technical, and physical safeguards 
    >     1.  1\. to insure the security and confidentiality of customer records and information;
    >     2.  2\. to protect against any anticipated threats or hazards to the security or integrity of such records; and
    >     3.  3\. to protect against unauthorized access to or use of such records or information which could result in substantial harm or inconvenience to any customer.^([^(188)](#fn188))
    
    The law refers to the term “non-public personal information” in § 6809(4) and defines it as personally identifiable information of a financial nature provided by a consumer to a financial institution, resulting from a transaction or service performed for the consumer, or otherwise obtained by a financial institution.
    
    > (4) NONPUBLIC PERSONAL INFORMATION. (A) The term “nonpublic personal information” means personally identifiable financial information
    > 
    > 1.  (i) provided by a consumer to a financial institution;
    > 2.  (ii) resulting from any transaction with the consumer or any service performed for the consumer; or
    > 3.  (iii) otherwise obtained by the financial institution.”^([^(189)](#fn189))
    
    Some examples of “nonpublic personal information” include: contact information, consumer account number and application information, consumer report information gained by the financial institution such as employee’s credit worthiness, credit standing, credit capacity, social security number, and Internet cookie information.
    
    ![](images/inline4.4.jpg)
    
    Under the Safeguards Rule, the financial institutions must develop, implement, and maintain a comprehensive information security plan to protect the confidentiality of the client’s data. Furthermore, the financial institution must assign an employee to ensure the security and confidentiality of consumer information, “to protect against any anticipated threats or hazards to the security or integrity of such records.”^([^(190)](#fn190))
    
    ##### 4.3.5.1.1 Enforcement and Penalties for Violating the GLBA
    
    The *Securities and Exchange Commission (SEC)* is an independent U.S. Federal Agency in charge of protecting investors; maintaining fair, orderly, and efficient markets; and facilitating capital formation ([Figure 4.8](#c4.xhtml#f4.8)). The SEC adopted Regulation S-P § 248.30, covering procedures to safeguard customer records and information and the disposal of consumer report information, in accordance with the GLBA Safeguard Rules requirements.^([^(191)](#fn191))
    
    ![FIGURE 4.8 The Securities and Exchange Commission (SEC) logo.](images/fig4.8.jpg)
    
    **FIGURE 4.8** The Securities and Exchange Commission (SEC) logo.
    
    In addition to the SEC, the FTC aggressively enforces the Safeguard Rules. The agency monitors Title V, subtitle A, of GLBA,^([^(192)](#fn192))
    
    > SEC. 505. ENFORCEMENT. (a) IN GENERAL.—This subtitle and the regulations prescribed thereunder shall be enforced by the Federal functional regulators, the State insurance authorities, and the Federal Trade Commission with respect to financial institutions and other persons subject to their jurisdiction under applicable law.^([^(193)](#fn193))
    
    The enforcement and penalties for violations include monetary damages, forfeiture, and imprisonment. In some cases, these could exceed $1 million and the likelihood of losing FDIC insurance, resulting at the end of the financial firm’s business.
    
    #### [4.3.5.2 Red Flags Rule](#contents.xhtml#re_h-4-27)
    
    The Fair and Accurate Credit Transactions Act (FACT)^([^(194)](#fn194))
    
    *For part 681—Identity Theft Rules see Appendix F.*
    
    ### [4.3.6 Laws Affecting Utilities](#contents.xhtml#re_h-4-28)
    
    #### [4.3.6.1 The Federal Energy Regulatory Commission](#contents.xhtml#re_h-4-29)
    
    Under the Energy Policy Act of 2005^([^(195)](#fn195))
    
    ![FIGURE 4.9 The Federal Energy Regulatory Commission (FERC) logo.](images/fig4.9.jpg)
    
    **FIGURE 4.9** The Federal Energy Regulatory Commission (FERC) logo.
    
    One of the biggest threats to electric utilities and power companies is the growing danger of cyberattacks and their effect on the operations and security of the U.S. Electric Power Grid. The electric grid depends on the Industrial Control System (ICS). The grid’s ICS network sensors monitor important components. A common ICS network system is the Supervisory Control and Data Acquisition (SCADA), which collects information from remote stations.^([^(196)](#fn196))
    
    Besides direct cyberattacks by hackers, other threats exist from infected IoT devices connected to the same network as an electric grid. Hackers can take control of a great number of infected IoT devices and launch denial-of-service or other cyberattacks on an electric grid. Additionally, hackers can spread malware, using IoTs to damage these systems on the network, causing interruptions of electrical system operation or manipulation of information. These kinds of attacks could potentially transpire in U.S. electric grids as well. As a result, in 2017, the president issued Executive Order (EO) 13800 on “Strengthening the Cybersecurity of Federal Networks and Critical Infrastructure.”^([^(197)](#fn197))
    
    The Federal Energy Regulatory Commission has adopted cybersecurity framework standards for critical infrastructu\\re protection (CIP).^([^(198)](#fn198))
    
    **TABLE 4.3** Several North American Electric Reliability Corporation (NERC) Critical Infrastructure Protection Standards
    
      
    | Standards || Title || Description |
    | --- | --- | --- |
    | CIP-001 || Sabotage Reporting || Report sabotage to the appropriate governmental agencies |
    | --- | --- | --- |
    | CIP-002 || Critical Cyber Asset Identification || Identify and protect Bulk Electric System (BES) against compromise |
    | CIP-003 || Security Management Controls || Use consistent security management controls to protect BES Cyber Systems against compromise |
    | CIP-004 || Cyber Security Personnel and Training || Require personnel risk assessment training and security awareness in BES Cyber Systems |
    | CIP-006 || Physical Security of BES Cyber Systems || Stipulate a security plan to protect BES Cyber Systems against compromise |
    | CIP-007 || Cyber Security System Security Management || Select technical, operational, and procedural requirements to support BES Cyber Systems against compromise |
    | CIP-009 || Cyber Security Recovery Plans for BES Cyber Systems || Specify recovery plan requirements for the continued stability, operability, and reliability of the BES |
    | CIP-010 || Cyber Security Configuration Change Management and Vulnerability Assessments || Develop changes to prevent and detect unauthorized changes to BES Cyber Systems. |
    
    ### [4.3.6.2 Nuclear Regulatory Commission](#contents.xhtml#re_h-4-30)
    
    The *Nuclear Regulatory Commission* is an independent agency regulating and licensing the nuclear power plants in the United States ([Figure 4.10](#c4.xhtml#f4.10)). More specifically, the Code of Federal Regulations, 10 C.F.R. § 73.54 protects digital computer and communication systems and networks from cyberattack.^([^(199)](#fn199))
    
    ![FIGURE 4.10 The Nuclear Regulatory Commission (NRC) logo.](images/fig4.10.jpg)
    
    **FIGURE 4.10** The Nuclear Regulatory Commission (NRC) logo.
    
    ## [4.4 Public and Private Sector Entities Partnerships in Cyberspace](#contents.xhtml#re_h-4-31)
    
    A public and private collaboration is necessary to address some of the biggest challenges in cybersecurity. As escalating cyberattacks continue to affect governments and private entities, the federal government can act as a central repository and distributor of cyberintelligence and guidelines. The federal government must provide cybersecurity tools to safeguard both public and private information. Organizations outside the federal government should play a leading role in public–private partnerships to train employees, improve technology, identify and rectify vulnerabilities, and exchange information.
    
    ![](images/inline4.5.jpg)
    
    *For a complete 6 U.S.C. § 1501—Domestic Security [Chapter 6](#c6.xhtml#c6)—Cybersecurity Subchapter I—Cybersecurity Information Sharing Sec. 1501—Definitions see Appendix G.*
    
    ### [4.4.1 Cybersecurity Information Sharing Act of 2015 (CISA)](#contents.xhtml#re_h-4-32)
    
    On December 18, 2015, President Obama signed the Consolidated Appropriations Act^([^(200)](#fn200))
    
    > The term “cyber threat indicator” means information that is necessary to describe or identify—
    > 
    > 1.  (A) malicious reconnaissance, including anomalous patterns of communications that appear to be transmitted for the purpose of gathering technical information related to a cybersecurity threat or security vulnerability;
    > 2.  (B) a method of defeating a security control or exploitation of a security vulnerability;
    > 3.  (C) a security vulnerability, including anomalous activity that appears to indicate the existence of a security vulnerability;
    > 4.  (D) a method of causing a user with legitimate access to an information system or information that is stored on, processed by, or transiting an information system to unwittingly enable the defeat of a security control or exploitation of a security vulnerability;
    > 5.  (E) malicious cyber command and control;
    > 6.  (F) the actual or potential harm caused by an incident, including a description of the information exfiltrated because of a particular cybersecurity threat.
    > 7.  (G) any other attribute of a cybersecurity threat, if disclosure of such attribute is not otherwise prohibited by law; or
    > 8.  (H) any combination thereof.^([^(201)](#fn201))
    
    ### [4.4.2 The Cybersecurity and Infrastructure Security Agency](#contents.xhtml#re_h-4-33)
    
    A new Act was signed into law on November 16, 2018, by President Donald Trump. Named the Cybersecurity and Infrastructure Security Agency ([Figure 4.11](#c4.xhtml#f4.11)), it became the nation’s risk advisor.^([^(202)](#fn202))
    
    ![FIGURE 4.11 The Cybersecurity and Infrastructure Security Agency (CISA) logo.](images/fig4.11.jpg)
    
    **FIGURE 4.11** The Cybersecurity and Infrastructure Security Agency (CISA) logo.
    
    ### [4.4.3 The National Cybersecurity and Critical Infrastructure Protection Act of 2014 (NCPA)](#contents.xhtml#re_h-4-34)
    
    The National Cybersecurity and Critical Infrastructure Protection Act of 2014^([^(203)](#fn203))
    
    *   **Title I**—Securing the Nation against Cyber Attack 
        *   designates the 16 critical infrastructure sectors.
        *   creates the National Cybersecurity and Communications Integration Center (NCCIC) as a federal civilian information sharing organization.
        *   promotes ongoing multidirectional sharing of information.
        *   reports cyber incidents, threats, and vulnerabilities impacting federal civilian information systems and critical infrastructure systems.
    *   **Title II**—Public–Private Collaboration on Cybersecurity. 
        *   directs NIST to develop a voluntary cybersecurity framework.
        *   forbids NIST from requiring the use of specific solutions, products, services, or manufacturing or design techniques.
    
    ### [4.4.4 Cybersecurity Enhancement Act of 2014 (CEA)](#contents.xhtml#re_h-4-35)
    
    The Cybersecurity Enhancement Act of 2014 (CEA)^([^(204)](#fn204))
    
    *   **Title I**: Public–Private Collaboration on Cybersecurity (Sec. 101) 
        *   strengthens, facilitates, and supports the development of the cybersecurity framework for critical infrastructure organizations by NIST.
    *   **Title II**: Cybersecurity Research and Development (Sec. 201) 
        *   directs the National Science Foundation (NSF) to support cybersecurity research; allows research and development grants for secure fundamental protocols, software engineering, monitoring, detection, mitigation, and rapid recovery methods; and secure wireless networks, mobile devices, and cloud infrastructure.
    *   **Title III**: Education and Workforce Development (Sec. 301) 
        *   The NSF should continue the federal cyber scholarship for cybersecurity programs in the public sector workforce.
    *   **Title IV**: Cybersecurity Awareness and Preparedness (Sec. 401) 
        *   distributes technical standards and identify best practices by individuals, businesses, and educational institutions
    *   **Title V**: Advancement of Cybersecurity Technical Standards (Sec. 502) 
        *   NIST to coordinate federal agencies in the development of international technical standards related to information system security.
    
    ## [4.5 Cybersecurity Requirements for Federal Government Contractors](#contents.xhtml#re_h-4-36)
    
    The U.S. federal government has been a frequent target of cybersecurity attacks. Fortunately, Congress has recognized the importance of information security inside the federal government and has enacted laws to ensure information security controls and to regulate how contractors handle personal data. In addition, federal agencies have strengthened cybersecurity regulations and standards, especially after the massive leak caused by National Security Agency’s contractor Edward Snowden.^([^(205)](#fn205))
    
    ![](images/inline4.6.jpg)
    
    ### [4.5.1 Federal Information Security Modernization Act of 2014](#contents.xhtml#re_h-4-37)
    
    On December 17, 2002, President George W. Bush signed into law the **E-Government Act**.^([^(206)](#fn206))
    
    In 2014, the Federal Information Security Management Act of 2002 (FISMA) was replaced by the Federal Information Security Modernization Act of 2014 (FISMA) or FISMA 2014.^([^(207)](#fn207))
    
    *   The law defines “national security system” as any information system or telecommunications system used or operated by an agency or by a contractor of an agency or other organization on behalf of an agency (44 U.S.C. § 3552).
    *   The law requires federal agencies to have information security and privacy policies and guidelines (44 U.S.C. § 3553).
    *   The OMB monitors agency implementation of the information security policies and guidelines (§ 3553).
    *   The director of OMB is required to notify Congress of major security incidents within 7 days (44 U.S.C. § 3554, § 3558).
    *   The OMB is responsible for assembling meetings with senior agency officials to help ensure the implementation of information security policies and practices and for collaborating to develop cybersecurity policies and cybersecurity programs and to coordinate government response to cyberattacks (44 U.S.C. § 3553).
    *   The law establishes a Federal Chief Information Security Officer for OMB and the Cyber and National Security Unit (44 U.S.C. § 3553).
    *   Under FISMA, DHS takes the lead in federal cybersecurity and coordinates federal government-wide cybersecurity efforts (44 U.S.C. § 3556).
    *   NIST is responsible for creating standards for information systems, in coordination with OMB and other federal agencies (44 U.S.C. § 3553).
    *   The head of each federal agency provides information on security protections and implementation of information security policies and practices for national security systems (44 U.S.C. § 3554).
    *   The director of the OMB shall ensure that data breach notification policies and guidelines are updated periodically (44 U.S.C. § 3558).
    
    ### [4.5.2 NIST Information Security Controls for Government Agencies and Contractors](#contents.xhtml#re_h-4-38)
    
    As the federal government depends heavily upon contractors for products and services, these contractors are particularly susceptible to cyberattacks. As a result, FISMA 2014 assigned NIST to provide standards and guidance to aid agencies and contractors in meeting legal requirements.^([^(208)](#fn208))
    
    ## [4.6 Most Important Internet Surveillance Laws in the United States](#contents.xhtml#re_h-4-39)
    
    The arrival of the Internet, the exponential growth in the number of mobile devices along with the advent of the Internet of Things, and biometric technologies, all mean that the job of protecting personal privacy has changed. The Fourth Amendment provides protection from unreasonable searches and seizures and has been used to defend wiretaps and other forms of surveillance. Following are the laws that limit the surveillance of government and private entities in the United States.
    
    ![](images/inline4.7.jpg)
    
    ### [4.6.1 All Writs Act](#contents.xhtml#re_h-4-40)
    
    The All Writs Act^([^(209)](#fn209))
    
    1.  (a) The Supreme Court and all courts established by Act of Congress may issue all writs necessary or appropriate in aid of their respective jurisdictions and agreeable to the usages and principles of law.
    2.  (b) An alternative writ or rule nisi may be issued by a justice or judge of a court which has jurisdiction (§ 1651(a)(b)).
    
    #### [4.6.1.1 Significant Case](#contents.xhtml#re_h-4-41)
    
    Nevertheless, in 1977, in the case of the *United States v. New York Telephone Co.*^([^(210)](#fn210))
    
    In other cases, the federal government had used the All Writs Act to access encrypted cell phones like Apple’s iPhone. In a Brooklyn drug case, federal law enforcement requested Apple’s help in unlocking an iPhone. A federal judge ruled that Apple had complied with 70 All Writs Act orders without objection, but in this case the All Writs Act did not require Apple to assist law enforcement in unlocking the iPhone.^([^(211)](#fn211))
    
    > the relief the government seeks is unavailable because Congress has considered legislation that would achieve the same result but has not adopted it. In addition, applicable case law requires me to consider three factors in deciding whether to issue an order under the \[All Writs Act\]: the closeness of Apple’s relationship to the underlying criminal conduct and government investigation; the burden the requested order would impose on Apple; and the necessity of imposing such a burden on Apple. As explained below, after reviewing the facts in the record and the parties’ arguments, I conclude that none of those factors justifies imposing on Apple the obligation to assist the government's investigation against its will. I therefore deny the motion. … Ultimately, the question to be answered in this matter, and in others like it across the country, is not whether the government should be able to force Apple to help it unlock a specific device; it is instead whether the All Writs Act resolves that issue and many others like it yet to come. For the reasons set forth above, I conclude that it does not. (James Orenstein, U.S. Magistrate Judge, February 29, 2016)^([^(212)](#fn212))
    
    ### [4.6.2 Fourth Amendment](#contents.xhtml#re_h-4-42)
    
    The Fourth Amendment to the Constitution is the basis for the individual’s right to privacy ([Figure 4.12](#c4.xhtml#f4.12)). But, as technology advances, upholding the right to privacy has become a challenge for the legal system in the United States. When there is an imperative government interest, individual privacy rights are diminished. Then again, because the Fourth Amendment is an important constitutional right, this area is ripe for litigation. The Amendment prevents the government from exercising its authority against unreasonable search and seizure of the property of U.S. citizens. Under the Fourth Amendment, *a warrant is required to be issued by a judge based on probable cause*. The Amendment states that:
    
    ![FIGURE 4.12 The Bill of Rights. The first 10 amendments to the Constitution, including the Fourth Amendment, comprise the Bill of Rights. Courtesy of The National Archives.](images/fig4.12.jpg)
    
    **FIGURE 4.12** The Bill of Rights. The first 10 amendments to the Constitution, including the Fourth Amendment, comprise the Bill of Rights. Courtesy of The National Archives.
    
    > The right of the people to be secure in their persons, houses, papers, and effects, against unreasonable searches and seizures, shall not be violated, and no Warrants shall issue, but upon probable cause, supported by Oath or affirmation, and particularly describing the place to be searched, and the persons or things to be seized.^([^(213)](#fn213))
    
    This following is a brief overview of the Fourth Amendment.
    
    #### [4.6.2.1 Search and Seizure](#contents.xhtml#re_h-4-43)
    
    The Fourth Amendment limits search and seizure by the government and protects people’s right to privacy from unreasonable intrusions without a warrant issued by a judge, with only a few exceptions. It is important to recognize that the Fourth Amendment limits only governmental entities and not the private sector under the Fourteenth Amendment’s *State Action Doctrine* that differentiates between governmental entities and private sector independence. ^([^(214)](#fn214))
    
    #### [4.6.2.2 Exceptions to the Search Warrant Rule](#contents.xhtml#re_h-4-44)
    
    Exceptions to the Fourth Amendment require urgent circumstances:
    
    *   **Exigent circumstances**: In case of an emergency like a life-and-death situation, law enforcement personnel can enter a premise without a warrant. In the Supreme Court case of *Missouri v. McNeely*, the court decided “A variety of circumstances may give rise to an exigency sufficient to justify a warrantless search, including law enforcement’s need to provide emergency assistance.”^([^(215)](#fn215))
    *   **Search and seizure incidental to a lawful arrest**: When a police officer observes an individual committing a crime, the officer may search without a warrant. In the Supreme Court case of *Riley v. California*^([^(216)](#fn216))
    *   A *consent* is required for law enforcement to search without a warrant. A parent can provide consent for a search of a child’s bedroom when no rent is paid by the child, but not a landlord, or a hotel manager. The Supreme Court case of *Illinois v. Rodriguez*^([^(217)](#fn217))
    *   *In plain view* occurs when a police officer observes illegal evidence in plain view, for example when a police officer sees contraband in a car during a traffic stop. In *Horton v. California*, “the Fourth Amendment does not prohibit the warrantless seizure of evidence in plain view, even though the discovery of the evidence was inadvertent.”^([^(218)](#fn218))
    *   Another exception to the warrant is the *caretaker function*. If a box has been given to the police, the police have the right to open it without a search warrant.
    *   *Impounded vehicles* may be searched without a search warrant as well. The Supreme Court case of *South Dakota v. Opperman* states that “when vehicles are impounded, police routinely follow caretaking procedures by securing and inventorying the cars' contents.” ^([^(219)](#fn219))
    *   The *border search exception* is a doctrine that permits the government, specifically U.S. Customs and Border Protection and DHS to conduct warrantless searches at international borders. See also the cases *United States v. Villamonte-Marquez*^([^(220)](#fn220))
    
    #### [4.6.2.3 Electronic Surveillance: Private vs Public](#contents.xhtml#re_h-4-45)
    
    ##### 4.6.2.3.1 Noteworthy Cases
    
    1.  In the case of the *United States V. Richardson*,^([^(221)](#fn221))
        
        > AOL’s actions did not equate to governmental conduct triggering constitutional protection. The Fourth Amendment does not protect against searches, no matter how unreasonable, conducted “by private individuals acting in a private capacity.”^([^(222)](#fn222))
        
    2.  In the area of electronic surveillance (wiretaps), the landmark case of *Katz v. United States*^([^(223)](#fn223))
    
    > The petitioner has strenuously argued that the booth was a “constitutionally protected area.” The Government has maintained with equal vigor that it was not. But this effort to decide whether a given “area,” viewed in the abstract, is “constitutionally protected” deflects attention from the problem presented by this case. For the Fourth Amendment protects people, not places. What a person knowingly exposes to the public, even in his own home or office, is not a subject of Fourth Amendment protection.^([^(224)](#fn224))
    
    ![FIGURE 4.13 The Phone Booth. Courtesy of Shutterstock.](images/fig4.13.jpg)
    
    **FIGURE 4.13** The Phone Booth. Courtesy of Shutterstock.
    
    Since we now rarely see a phone booth, another landmark case concerning cell phone location information, in relation to the Fourth Amendment, was decided by the U.S. Supreme Court.
    
    3.  In the case of *Carpenter v. United States*,^([^(225)](#fn225))
    
    #### [4.6.2.4 Exclusionary Rule and the Good Faith Exception](#contents.xhtml#re_h-4-47)
    
    The exclusionary rule prohibits law enforcement from using evidence obtained illegally in violation of the Fourth Amendment. An exception to this rule is the “good faith exception.” When a police officer is acting lawfully and it is later found that the officer made a mistake in conducting a search, the evidence is admissible.^([^(226)](#fn226))
    
    #### [4.6.2.5 The USA PATRIOT Act and the Fourth Amendment](#contents.xhtml#re_h-4-48)
    
    After the September 11, 2001, attacks and the enactment of the USA PATRIOT Act of 2001,^([^(227)](#fn227))
    
    With the first version of the PATRIOT Act, law enforcement agencies could conduct covert surveillance on U.S citizens and obtain evidence of crime without proving probable cause under § 213, Title II—Enhanced Surveillance. The law gave leeway to “authorities for delaying notice of execution of a warrant.”^([^(228)](#fn228))
    
    In 2015, after the USA PATRIOT Act expired, a new version was enacted, the Uniting and Strengthening America by Fulfilling Rights and Ensuring Effective Discipline over Monitoring Act of 2015 or the USA Freedom Act.^([^(229)](#fn229))
    
    ### [4.6.3 Electronic Communication Privacy Act of 1986](#contents.xhtml#re_h-4-49)
    
    In addition to the Fourth Amendment, the Electronic Communication Privacy Act^([^(230)](#fn230))
    
    > Interception and disclosure of wire, oral, or electronic communications prohibited. Manufacture, distribution, possession, and advertising of wire, oral, or electronic communication intercepting devices prohibited. (§ 2511)^([^(231)](#fn231))
    
    While the ECPA had revised and updated the original Federal Wiretap Act of 1968, the core of the law has not changed. The ECPA has been amended by the Communications Assistance to Law Enforcement Act (CALEA),^([^(232)](#fn232))
    
    *   18 U.S. Code CHAPTER 119—WIRE AND ELECTRONIC COMMUNICATIONS INTERCEPTION AND INTERCEPTION OF ORAL COMMUNICATIONS (also called Wiretap Act) (18 U.S.C. §§ 2510-23) 
        *   Except as otherwise specifically provided in this chapter any person who 
            *   (a) intentionally intercepts, endeavors to intercept, or procures any other person to intercept or endeavor to intercept, any wire, oral, or electronic communication;
            *   (b) intentionally uses, endeavors to use, or procures any other person to use or endeavor to use any electronic, mechanical, or other device to intercept any oral communication when— 
                *   – (i) such device is affixed to, or otherwise transmits a signal through, a wire, cable, or other like connection used in wire communication; or
                *   – (ii) such device transmits communications by radio or interferes with the transmission of such communication” (**§** 2510 (1)(a)(b).
        *   Prohibits interception and disclosure of wire, oral, or electronic communications (§ 2511).
        *   Prohibits the use of illegally obtained communications as evidence (§ 2515).
        *   Provides access for Federal and State government to obtain authorized wiretapping (§§ 2516-2518).
        *   A warrant needed for interception of communications for up to 30 days by demonstrating probable cause for individual “committing, has committed, or is about to commit a particular offense” (listed at § 2516 and § 2518).
    *   18 U.S. Code CHAPTER 121—STORED WIRE AND ELECTRONIC COMMUNICATIONS AND TRANSACTIONAL RECORDS ACCESS (also called Stored Communications Act (SCA) (§§ 2701-13).^([^(233)](#fn233)) 
        *   The SCA criminalizes “intentional accesses without authorization of a facility through which an electronic communication service is provided; or  
            intentionally exceeding an authorization to access that facility” § 2701(a)(1)(2).
        *   Protects the privacy for data files stored by Internet Service Provider (ISP), and telephone companies, such as subscriber name, billing and records information, and IP addresses or “any person or entity the contents of any communication” (§ 2702).
        *   The SCA protects “electronic communication services” and “remote computing services” (§ 2702). The term “electronic communication service” means any service which provides to users thereof the ability to send or receive wire or electronic communications” (§ 2510) and the term “remote computing service” means the provision to the public of computer storage or processing services by means of an electronic communications system” (§ 2711 (2)).
        *   ISPs are not allowed to share content data such as spoken words of a conversation, actual text of the message, and e-mails. Content data are defined as “contents” when used with respect to any wire, oral, or electronic communication, includes any information concerning the substance, purport, or meaning of that communication” (§ 2510).
        *   An exception is when ISP permitted to share non-content information, such as telephone numbers, email addresses used, websites visited, logs of account usage, mail header information minus the subject line, and lists of outgoing email addresses (§ 2702 (c)(6)).
    *   18 U.S. Code CHAPTER 206—PEN REGISTERS AND TRAP AND TRACE DEVICES (§§ 3121-3127) (also called pen register).^([^(234)](#fn234)) 
        *   The pen register prohibits government entities/law enforcement, to install trap and trace devices without obtaining a warrant. “No person may install or use a pen register or a trap and trace device without first obtaining a court order under section 3123” (§ 3121(a)).
    
    ### [4.6.4 Communication Assistant for Law Enforcement Act of 1994 (CALEA)](#contents.xhtml#re_h-4-50)
    
    The Communication Assistant for Law Enforcement Act^([^(235)](#fn235))
    
    ![](images/inline4.8.jpg)
    
    1.  Design of features and systems configurations. This subchapter does not authorize any law enforcement agency or office 
        1.  (A) to require any specific design of equipment, facilities, services, features, or system configurations to be adopted by any provider of a wire or electronic communication service, any manufacturer of telecommunications equipment, or any provider of telecommunications support services.
        2.  (B) to prohibit the adoption of any equipment, facility, service, or feature by any provider of a wire or electronic communication service, any manufacturer of telecommunications equipment, or any provider of telecommunications support services.” § 1002(b)(1)
    2.  Encryption. A telecommunications carrier shall not be responsible for decrypting, or ensuring the government’s ability to decrypt, any communication encrypted by a subscriber or customer, unless the encryption was provided by the carrier and the carrier possesses the information necessary to decrypt the communication. § 1002(b)(3)^([^(236)](#fn236))
    
    ## [4.7 Key Privacy Laws in the United States](#contents.xhtml#re_h-4-51)
    
    The exponential growth and use of new technologies such as tracking by global positioning system (GPS), the use of social media over the Internet, and the use of biometric authentication, all make privacy less important. Are discount coupons that collect behavioral information and online habits and information about what we do online worth our privacy? Cyberspace and the progression of technology have not killed privacy but have altered how it is being managed and handled. It certainly requires more effort to protect our privacy than ever before. The following is the key legislation that safeguards our privacy ([Figure 4.14](#c4.xhtml#f4.14)).
    
    ![FIGURE 4.14 Privacy Laws. Courtesy of Shutterstock.](images/fig4.14.jpg)
    
    **FIGURE 4.14** Privacy Laws. Courtesy of Shutterstock.
    
    ### [4.7.1 Privacy Act of 1974](#contents.xhtml#re_h-4-52)
    
    The Privacy Act of 1974^([^(237)](#fn237))
    
    ![](images/inline4.9.jpg)
    
    ### [4.7.2 Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003 (CAN-SPAM Act)](#contents.xhtml#re_h-4-53)
    
    The CAN-SPAM Act^([^(238)](#fn238))
    
    *   Prohibition of false or misleading transmission information (§ 7704 (a)(1))
    *   Prohibition of deceptive subject headings (§ 7704 (a)(2))
    *   Inclusion of identifier, opt-out, and physical address in commercial electronic mail (§ 7704 (a)(5))
    *   In this subsection, the term “sexually oriented material” means any material that depicts sexually explicit conduct as that term is defined in section 2256 of title 18—unless the depiction constitutes a small and insignificant part of the whole, the remainder of which is not primarily devoted to sexual matters (§ 7704 (d)(4))
    *   Exclusive enforcement by FTC ((§ 7705 (c))
    
    ### [4.7.3 18 U.S.C. § 1037 Fraud and Related Activity in Connection with Electronic Mail](#contents.xhtml#re_h-4-54)
    
    SEC. 4. PROHIBITION AGAINST PREDATORY AND ABUSIVE COMMERCIAL E-MAIL of the CAN-SPAM Act, § 1037^([^(239)](#fn239))
    
    ![](images/inline4.10.jpg)
    
    1.  (a) In General.—Whoever, in or affecting interstate or foreign commerce, knowingly— 
        1.  1\. accesses a protected computer without authorization, and intentionally initiates the transmission of multiple commercial electronic mail messages from or through such computer,
        2.  2\. uses a protected computer to relay or retransmit multiple commercial electronic mail messages, with the intent to deceive or mislead recipients, or any Internet access service, as to the origin of such messages,
        3.  3\. materially falsifies header information in multiple commercial electronic mail messages and intentionally initiates the transmission of such messages,
        4.  4\. registers, using information that materially falsifies the identity of the actual registrant, for five or more electronic mail accounts or online user accounts or two or more domain names, and intentionally initiates the transmission of multiple commercial electronic mail messages from any combination of such accounts or domain names, or
        5.  5\. falsely represents oneself to be the registrant or the legitimate successor in interest to the registrant of 5 or more Internet Protocol addresses, and intentionally initiates the transmission of multiple commercial electronic mail messages from such addresses, or conspires to do so, shall be punished as provided in subsection (b). (§ 1037)
    
    According to § 1037(b)(1)(2), offenders will be punished with a fine and/or jail sentence for not fewer than 3 and up to 5 years. As mentioned earlier, in § 1037, the law prohibits sending sexually explicit emails without a warning label. The law is codified at 15 U.S.C. § 7704(d)^([^(240)](#fn240))
    
    *For a complete U.S.C. § 1037 see Appendix H.*
    
    ### [4.7.4 18 U.S.C. § 1029 Fraud and Related Activity in Connection with Access Devices](#contents.xhtml#re_h-4-55)
    
    Unauthorized access to a network where data resides compromises the privacy of individuals; such cases commonly involve violations of identity theft statutes. Our credit card information is widely available, and it is quite easy for criminals to commit credit card fraud. Part of the Violent Crime Control and Law Enforcement Act of 1994,^([^(241)](#fn241))
    
    1.  (a) Whoever— 
        1.  1\. knowingly and with intent to defraud produces, uses, or traffics in one or more counterfeit access devices;
        2.  2\. knowingly and with intent to defraud traffics in or uses one or more unauthorized access devices during any one-year period, and by such conduct obtains anything of value aggregating $1,000 or more during that period;
        3.  3\. knowingly and with intent to defraud possesses fifteen or more devices which are counterfeit or unauthorized access devices;
        4.  4\. knowingly, and with intent to defraud, produces, traffics in, has control or custody of, or possesses device-making equipment;
        5.  5\. knowingly and with intent to defraud effects transactions, with 1 or more access devices issued to another person or persons, to receive payment or any other thing of value during any one-year period the aggregate value of which is equal to or greater than $1,000;
        6.  6\. without the authorization of the issuer of the access device, knowingly and with intent to defraud solicits a person for the purpose of— 
            1.  (A) offering an access device; or
            2.  (B) selling information regarding or an application to obtain an access device;
        7.  7\. knowingly and with intent to defraud uses, produces, traffics in, has control or custody of, or possesses a telecommunications instrument that has been modified or altered to obtain unauthorized use of telecommunications services;
        8.  8\. knowingly and with intent to defraud uses, produces, traffics in, has control or custody of, or possesses a scanning receiver;
        9.  9\. knowingly uses, produces, traffics in, has control or custody of, or possesses hardware or software, knowing it has been configured to insert or modify telecommunication identifying information associated with or contained in a telecommunications instrument so that such instrument may be used to obtain telecommunications service without authorization; or
        10.  10\. without the authorization of the credit card system member or its agent, knowingly and with intent to defraud causes or arranges for another person to present to the member or its agent, for payment, 1 or more evidences or records of transactions made by an access device;  
             Shall, if the offense affects interstate or foreign commerce, be punished as provided in subsection (c) of this section. (§ 1029)
    
    ### [4.7.5 18 U.S. Code §1028 Fraud and Related Activity in Connection with Identification Documents, Authentication Features, and Information](#contents.xhtml#re_h-4-56)
    
    Numerous federal laws apply to identity theft, including section 1028(a)(7), enacted as part of the Identity Theft and Assumption Deterrence Act of 1998,^([^(242)](#fn242))
    
    Title 18, United States Code, section 1028 criminalizes identity theft involving fraudulent identification documents or the unlawful use of identification information. The law made identity theft a federal crime and can impose punishments of up to 15 years imprisonment and a maximum fine of $250,000. The law allows for the identity theft victim to seek restitution if there is a conviction. In addition, the law establishes the FTC^([^(243)](#fn243))
    
    *   Whoever, in a circumstance described in subsection (c) of this section— 
        7.  knowingly transfers, possesses, or uses, without lawful authority, a means of identification of another person with the intent to commit, to aid or abet, or in connection with any unlawful activity that constitutes a violation of Federal law, or that constitutes a felony under any applicable State or local law; or
        8.  knowingly traffics in false or actual authentication features for use in false identification documents, document-making implements, or means of identification; 
            1.  Shall be punished as provided in subsection (b) of this section.
    
    ### [4.7.6 Children’s Online Privacy Protection Act of 1998](#contents.xhtml#re_h-4-57)
    
    The Children’s Online Privacy Protection Act of 1998^([^(244)](#fn244))
    
    ![](images/inline4.11.jpg)
    
    More specifically, the law applies to any online services and operators of commercial websites including mobile apps, Internet-connected toys, or any devices that collect, use, or disclose personal information from minors under 13 years old. According to the FTC, personal information is listed in [Table 4.4](#c4.xhtml#t4.4).^([^(245)](#fn245))
    
    **TABLE 4.4** Personal Information 
    
      
    | Personal information means individually identifiable information |
    | --- |
    | (1) A first and last name |
    | --- |
    | (2) A home or other physical address including street name and name of a city or town |
    | (3) Online contact information as defined in this section |
    | (4) A screen or username where it functions in the same manner as online contact information, as defined in this section |
    | (5) A telephone number |
    | (6) A Social Security number |
    | (7) A persistent identifier that can be used to recognize a user over time and across different Web sites or online services. Such persistent identifier includes, but is not limited to, a customer number held in a cookie, an Internet Protocol (IP) address, a processor or device serial number, or unique device identifier |
    | (8) A photograph, video, or audio file where such file contains a child’s image or voice |
    | (9) Geolocation information sufficient to identify street name and name of a city or town |
    | (10) Information concerning the child or the parents of that child that the operator collects online from the child and combines with an identifier described in this definition |
    | Adopted from 16 C.F. R. § 312.2 |
    
    Additionally, the law applies to operators of general audience websites or online services that have “actual knowledge of collecting, using, or disclosing personal information from children” (§ 312.4). Any online services and websites covered under COPPA law must provide notice and “verifiable parental consent” before collecting, using, or disclosing personal information from children.
    
    > (a) General principles of notice. It shall be the obligation of the operator to provide notice and obtain verifiable parental consent prior to collecting, using, or disclosing personal information from children. Such notice must be clearly and understandably written, complete, and must contain no unrelated, confusing, or contradictory materials. (§ 312.4 Notice)
    
    The online services and websites “must make reasonable efforts to obtain verifiable parental consent,” and “reasonably calculated, in light of available technology, to ensure that the person providing consent is the child’s parent.”^([^(246)](#fn246))
    
    *   Providing a consent form to be signed by the parent and returned to the operator by postal mail, facsimile, or electronic scan;
    *   Requiring a parent, in connection with a monetary transaction, to use a credit card, debit card, or other online payment system that provides notification of each discrete transaction to the primary account holder;
    *   Having a parent call a toll-free telephone number staffed by trained personnel;
    *   Having a parent connect to trained personnel via video-conference;
    *   Verifying a parent’s identity by checking a form of government-issued identification against databases of such information, where the parent's identification is deleted by the operator after such verification is complete. (§ 312.b (b))
    
    It is worth noting that under § 312.10 “Data retention and deletion requirements,” the FTC has designated the “Safe Harbor Certification program” that the industry may request approval of self-regulatory guidelines. The program ensures best practices for the collection, use, and disclosure of personal information from minors as consistent with COPPA law.
    
    > In general. Industry groups or other persons may apply to the Commission for approval of self-regulatory program guidelines (“safe harbor programs”). The application shall be filed with the Commission’s Office of the Secretary. The Commission will publish in the Federal Register a document seeking public comment on the application. The Commission shall issue a written determination within 180 days of the filing of the application. (§ 312.11 Safe harbor programs)
    
    ### [4.7.7 Video Privacy Protection Act (VPPA) of 1988](#contents.xhtml#re_h-4-58)
    
    The Video Privacy Protection Act of 1988^([^(247)](#fn247))
    
    ![](images/inline4.12.jpg)
    
    > (4) the term “video tape service provider” means any person engaged in the business, in or affecting interstate or foreign commerce, of rental, sale, or delivery of prerecorded video cassette tapes or similar audiovisual materials, or any person or other entity to whom a disclosure is made under subparagraph (D) or (E) of subsection (b)(2), but only with respect to the information contained in the disclosure. (§ 2710(4)
    
    As a result, the law includes not only “video rental stores or video tape service providers” but any video streaming from the web. The following are the most significant provisions of the law:
    
    *   Unlawful on the disclosure of personally identifiable rental information without written consent.
    *   Law enforcement requires a valid warrant or court order.
    *   If any personal, identifiable information concerning any consumer is disclosed, the provider shall be liable.
    *   Civil remedies, not less than $2500.
    *   When an account is terminated the “video rental stores or video tape service provider” should destroy rental records in no longer than 1 year.
    *   The states are free to enact broader protections for individuals’ records. The Act does not preempt state law (§ 2710).
    
    ### [4.7.8 When the United States Began Taking Privacy Seriously](#contents.xhtml#re_h-4-59)
    
    As we have pointed out, the United States does not have a single form of national legislation but instead has numerous enacted statutes and regulations addressing various aspects of cybersecurity. States sometimes take initiative from the federal government and implement new privacy laws to protect residents’ rights. As a result, two states enacted specially important legislation protecting the individual’s privacy. The first is the California Consumer Privacy Act of 2018 (CCPA),^([^(248)](#fn248))
    
    California’s CCPA was enacted in 2018 and is the most significant consumer data protection law in the United States. The law offers residents of California the right to know what data companies collect about them and gives them the right to request that the business delete their personal information. Examples of personal information include *name*, *alias*, *postal address*, *unique identifier*, *Internet protocol address (IP)*, *email address*, *social security number*, *driver’s license number*, *passport number*, and *characteristics such as race*, *gender*, *disability*, and others protected by federal and state antidiscrimination laws. In addition to the personal information the law protects commercial information, such as *records of property*, *products or services provided, obtained, or considered, or other purchasing or consumer histories or tendencies*; *biometric data*; *Internet or other electronic network activity information, including browsing history, search history, and information regarding a consumer’s interaction with a website, application, or advertisement*.
    
    In synopsis, the law provides the following rights, the right to know, right to access, right to deletion, right of opt-out, right to equal service and price, and right to opt-in for consumers under the age of 16.
    
    The second state law that has had a profound impact concerning privacy is the Illinois Biometric Information Privacy Act (BIPA).^([^(249)](#fn249))
    
    [Tables 4.5](#c4.xhtml#f4.5) and [4.6](#c4.xhtml#f4.6) summarize the most significant Federal laws concerning Cybercrime in the United States.
    
    ## [4.8 Conclusion](#contents.xhtml#re_h-4-60)
    
    Cybercrime is a major concern for the U.S government and the private sector. The growth of computing devices and e-commerce affects everyone. Data breaches have become commonplace. The U.S. cyber and privacy rights laws are perhaps the oldest and most effective in the world. Nevertheless, they need to be modernized and equal in effectiveness to California’s CCPA and the Illinois Biometric Information Privacy Act. A mixture of federal, state, and local legislation, along with responsible individual and best practices, is the best solution to preventing cyberattacks.
    
    **TABLE 4.5** A Brief Summary of Major Unlawful Contact Concerning Cybercrime
    
      
    | Unlawful Violations || Federal Legislation |
    | --- | --- |
    | Accessing a Computer without Authorization || 18 U.S.C. § 1030 |
    | --- | --- |
    | A Denial-of-Service (DoS) Attack || 18 U.S.C. § 1030, 18 U.S.C. § 1362 |
    | Child Pornography || 18 U.S.C. §§ 2251, 2252, 18 U.S.C. § 2423, 18 U.S.C. § 1466 |
    | Children’s Online Privacy Protection || 15 U.S.C. §§ 6501-06, 16 C.F. R. § 312 |
    | Credit Card Fraud || 18 U.S.C. § 1030, 18 U.S.C. § 1029, 15 U.S.C. § 1644, 18 U.S.C. § 1343 |
    | Cyberstalking || 18 U.S.C. § 2261 |
    | Disclosure of Private Information || 18 U.S.C. § 2511 |
    | Electronic Harassment || 47 U.S.C. § 223 |
    | Electronic Threats || 18 U.S.C. § 875, 18 U.S.C. § 1951, 47 U.S.C. § 223 |
    | Espionage || 18 U.S.C. § 1030, 18 U.S.C. § 793, 18 U.S.C. § 798 |
    | Extortion || 18 U.S.C. § 1030, 18 U.S.C. § 875, 18 U.S.C. § 1951 |
    | Internet Fraud || 18 U.S.C. § 1030, 18 U.S.C. § 1028, 18 U.S.C. § 1343,18 U.S.C. §§ 1956, 1957, 18 U.S.C. § 1001, 15 U.S.C. § 45, 15 U.S.C. § 52, 15 U.S.C. § 6821 |
    | Interception of Electronic Communications || 18 U.S.C. § 2511, 18 U.S.C. § 2701, 18 U.S.C. § 1030 |
    | Interfering with Government Communication Systems || 18 U.S.C. § 1030, 18 U.S.C. § 1362 |
    | Password Fraud || 18 U.S.C. § 1030, 18 U.S.C. § 1029, 18 U.S.C. § 1343 |
    | Intellectual Property Theft/Piracy || 17 U.S.C. §§ 1201-1205, 18 U.S.C. § 545, 18 U.S.C. §§ 1831, 1832, 18 U.S.C. § 2318, 17 U.S.C. § 506, 18 U.S.C. § 2319, 18 U.S.C. § 2320, 47 U.S.C. § 553, 18 U.S.C. § 1343 |
    | Substitution/Redirection of a Website || 18 U.S.C. § 1030 |
    | Spam || 18 U.S.C. § 1037 |
    | Spoofing Email Address || 18 U.S.C. § 1037 |
    | Transmission of Program, Information, Code, or Command || 18 U.S.C. § 1030 |
    | Trade Secrets/Economic Espionage || 18 U.S.C. § 1831, 18 U.S.C. § 1832, 18 U.S.C. § 1905, 18 U.S.C. §§ 2314, 2315 |
    | Use Misleading Domain Name || 18 U.S.C. § 225 |
    | Video Privacy Protection from the Web || 18 U.S.C § 2710 |
    
     **TABLE 4.6** Federal Legislation with Titles 
    
     
    | Federal Legislation with Titles  |
    | --- |
    | **18 U.S.C. § 1030—**The Computer Fraud and Abuse Act (CFAA) || **8 U.S.C. 1957—**Engaging in monetary transactions in property derived from specified unlawful activity |
    | --- | --- |
    | **18 U.S.C. § 1362—**Communication lines, stations, or systems || **18 U.S.C. § 1001—**Statements or entries generally |
    | **18 U.S.C. § 2251—**Sexual exploitation of children, **§ 2252—**Certain activities relating to material involving the sexual exploitation of minors || **15 U.S.C. § 45—**Unfair methods of competition unlawful; prevention by Commission |
    | **18 U.S.C § 2710—**Wrongful disclosure of video tape rental or sale records || **15 U.S.C. § 52—**Dissemination of false advertisements |
    | **18 U.S.C. § 2423—**Transportation of minors || **15 U.S.C. § 6821—**Privacy protection for customer information of financial institutions |
    | **18 U.S.C. § 1466—**Engaging in the business of selling or transferring obscene matter || **18 U.S.C. § 2511—**Interception and disclosure of wire, oral, or electronic communications prohibited |
    | **15 U.S.C. § 6501–§ 6506—**Children’s Online Privacy Protection Rule (COPPA) || **18 U.S.C. § 2701—**Unlawful access to stored communications, **§ 1201—**Savings clause |
    | **16 C.F. R. § 312—**Children’s Online Privacy Protection Rule Safe Harbor Proposed Self-Regulatory Guidelines || **17 U.S.C. § 1205—**Circumvention of copyright protection systems |
    | **18 U.S.C. § 1029—**Fraud and related activity in connection with access devices || **18 U.S.C. § 545—**Smuggling goods into the United States |
    | **15 U.S.C. § 1644—**Fraudulent use of credit cards; penalties || **18 U.S.C. § 1831—**Economic espionage |
    | **18 U.S.C. § 1343—**Fraud by wire, radio, or television || **18 U.S.C. 1832—**Theft of trade secrets |
    | **18 U.S.C. § 2261—**Interstate domestic violence || **18 U.S.C. § 2318—**Trafficking in counterfeit labels, illicit labels, or counterfeit documentation or packaging |
    | **18 U.S.C. § 2315—**Sale or receipt of stolen goods, securities, moneys, or fraudulent state tax stamps || **17 U.S.C. § 506—**Criminal offenses (if the infringement was committed) |
    | **47 U.S.C. § 223—**Obscene or harassing telephone calls in the District of Columbia or in interstate or foreign communications || **18 U.S.C. § 2319—**Criminal infringement of a copyright |
    | **18 U.S.C. § 875—**Interstate communications || **18 U.S.C. § 2320—**Trafficking in counterfeit goods or services |
    | **18 U.S.C. § 1951—**Interference with commerce by threats or violence || **47 U.S.C. § 553—**Unauthorized reception of cable service |
    | **18 U.S.C. § 793—**Gathering, transmitting, or losing defense information || **18 U.S.C. § 1037—**Fraud and related activity in connection with electronic mail |
    | **18 U.S.C. § 798—**Disclosure of classified information || **18 U.S.C. § 1905—**Disclosure of confidential information generally |
    | **18 U.S.C. § 1028—**Fraud and related activity in connection with identification documents, authentication features, and information || **18 U.S.C. § 2314—**Transportation of stolen goods, securities, moneys, fraudulent state tax stamps, or articles used in counterfeiting |
    | **18 U.S.C. § 1956—**Laundering of monetary instruments || **18 U.S.C. § 225—**Continuing financial crimes enterprise |
    
    ## [4.9 Key Words](#contents.xhtml#re_h-4-61)
    
     
    | Anti-Hacking Laws || Financial Institutions |
    | --- | --- |
    | Authorized Access || Healthcare |
    | Business Associate Agreement || Infringement Liability |
    | Business Associates || Intellectual Property |
    | Commission || Meaningful Use |
    | Consumer Fraud || Online Privacy |
    | Consent || Password Trafficking |
    | Copyright || Public |
    | Covered Entities || Private Sector |
    | Cybersecurity Framework || Plain View |
    | Cyber Laws || Protection |
    | Electric Utilities || Red Flags Rule |
    | Economic Espionage || Telemarketing |
    | Exceed Authorized Access || Safe Harbor |
    | Exigent Circumstances || Search and Seizure |
    | Fair Use || Warrant |
    | Federal Government ||  |
    
    # [Chapter 5 The Networking Environment](#contents.xhtml#re_c5)
    
    DOI: [10.4324/9780429318726-5](https://doi.org/10.4324/9780429318726-5)
    
    ## [Objectives](#contents.xhtml#re_h-5-1)
    
    After completing this chapter, the student will be able to:
    
    *   Understand computer networking, its history, and evolution
    *   Identify the advantages and disadvantages of computer networking
    *   Understand essential computer network components and terminology
    *   Understand different types of networking
    *   Understand the Open Systems Interconnection (OSI) and Transmission Control Protocol/Internet Protocol (TPC/IP) Models
    
    *Matthew types* [www.linkedin.com](http://www.linkedin.com) *into the address bar of his browser and searches for “Jobs in Computer Security.” The browser looks for a Domain Name System (DNS) record to find the IP address of* [www.linkedin.com](http://www.linkedin.com)*. Instantly, he receives a response, and the site appears.*
    
    *But what happens behind the scenes?*
    
    *   Domain Name System (DNS) Search
    *   Network communication using Transmission Control Protocol (TCP) 
        *   Browser sends a Hypertext Transfer Protocol Secure (HTTPS) request
        *   Server sends back HTTPS response
        *   Server acknowledges and sends back the requested Hypertext Markup Language (HTML) file
    *   Browser renders HTML
    *   Browser sends additional requests (GET request) for additional components
    *   Matthew receives requested information
    
    First, the browser checks for a Domain Name System (DNS) record to find the corresponding IP address of [www.linkedin.com](http://www.linkedin.com). Every Web page on the Internet has a unique IP address assigned to it. While the Uniform Resource Locator (URL) is a reference to a specific website, the DNS is the “phonebook” of the Internet and contains a list of every URL and its IP addresses. To find [www.linkedin.com](http://www.linkedin.com), the browser checks four caches, the Browser cache, Computer Operating System (OS) cache, Router cache, and Internet service provider (ISP) DNS cache. A cache can be hardware or software. It stores data so that future requests for that data can be found more quickly.
    
    If the IP address is not found, the DNS server starts a new DNS query to find the IP address of [www.linkedin.com](http://www.linkedin.com). As soon as the browser locates the right IP address, it tells the server that has found the IP address for [www.linkedin.com](http://www.linkedin.com) and wants to transfer the information.
    
    How does it do that? There are several types of network protocols, but the TCP is the most common protocol used to establish and maintain network communication. The browser sends a Hypertext Transfer Protocol (HTTP) request. HTTP is a protocol that runs on top of TCP. TCP transfers data packets between Matthew’s computer, the client, and the server. This connection is known as a three-way handshake: 1-SYN or a request from the server is sent to synchronize devices; 2-SYN/ACK or the client (Matthew) hears the request; and 3-ACK or the request is acknowledged. This establishes the connection between the network and the devices. After the TCP/IP connection is established, the data can be delivered to Matthew’s computer.
    
    The browser receives a HTML file that needs to be understood and displayed. First, it renders the HTML, and then it checks the HTML tags and sends out a GET method request for additional components on the Web page, like an image or a graph. Now Matthew can see the result of “Jobs in Computer Security” appearing on his browser.
    
    All these events take place while Matthew blinks. In this chapter you will learn to understand each of these steps and appreciate the network devices and processes that make them possible.
    
    The term “computer network” refers to two or more interconnected computing devices or machines that can communicate with each other. The fundamental goal of *computer networking* is simple—to securely share information and resources. It is the execution that is not simple at all.
    
    ## [5.1 Introduction to Computer Networking](#contents.xhtml#re_h-5-2)
    
    Over the centuries, some human inventions have provided transformative changes in our lives. Inventions such as the wheel, compass, concrete, steel, gunpowder, and nails have extended the boundaries of civilization and human knowledge and have moved innovation forward.
    
    The end of the 18th century brought the age of the steam engine,^([^(250)](#fn250))
    
    The 20th century brought us automation, information gathering and processing, the Internet, and mobile phones.^([^(251)](#fn251))
    
    The Internet is an enormous global network of networks that can connect every computing device to its vast resources and to every other computer on the planet. In the 1960s, the Advanced Research Projects Agency (ARPA), part of the Department of Defense, funded a proposed network project called the Advanced Research Projects Agency Network (ARPANET), through the Association for Computing Machinery (ACM).
    
    In 1969, the experimental ARPANET was constructed ([Figure 5.1](#c5.xhtml#f5.1)). Only universities with ties to the Department of Defense were considered for this project. The new network connected the Universities of California Los Angeles (UCLA) and California at Santa Barbara (UCSB), the Stanford Research Institute (SRI), and the University of Utah (UTAH) through the Internet Message Processor (IMP)^([^(252)](#fn252))
    
    ![FIGURE 5.1 A map of the ARPANET in December 1970. Courtesy of DARPA.](images/fig5.1.jpg)
    
    **FIGURE 5.1** A map of the ARPANET in December 1970. Courtesy of DARPA.
    
    ![FIGURE 5.2 The first routers, known as Interface Message Processors or IMPs. Courtesy of DARPA.](images/fig5.2.jpg)
    
    **FIGURE 5.2** The first routers, known as Interface Message Processors or IMPs. Courtesy of DARPA.
    
    ![FIGURE 5.3 The first rough conceptual design of ARPANET in 1969 with four nodes. Adopted from DARPA.](images/fig5.3.jpg)
    
    **FIGURE 5.3** The first rough conceptual design of ARPANET in 1969 with four nodes. Adopted from DARPA.
    
    However, it is worth noting that Bolt Beranek and Newman (BBN) Inc. was awarded the contract to build the ARPANET. Consequently, BBN created Telenet Communications Corp. to commercialize the packet switching technology. Telenet received a Federal Communications Commission (FCC) license in 1974. In 1975, Telenet launched the first commercial packet switching with network service that cost $0.60 per kilo packet with no distance restrictions and $0.90–2.40 per hour for computer terminals dialing into the local Telenet node. The company expanded its network globally and played a vital role in generating the standard for commercial packet networks.^([^(253)](#fn253))
    
    Most institutions with computer science programs were part of CSNET. In 1983, TCP/IP became the official protocol for ARPANET. The term “protocol” will be explained shortly.
    
    In 1983, the ARPANET split into two separate networks, the MILNET for military installations and the ARPANET for civilian use (mainly dedicated to research). In 1986, the National Science Foundation (NSF) sponsored the development of the National Science Foundation Network (NSFNET), which promoted advanced research in networking.^([^(254)](#fn254))
    
    In 1989, while working for the European Organization for Nuclear Research (CERN), Tim Berners-Lee invented the World Wide Web (WWW). The idea was the creation of a service that merged HTML, URL, and HTTP so that all computers could understand each other in an easy-to-use global information system.^([^(255)](#fn255))
    
    In 1990, the ARPANET was replaced by NSFNET. In 1995, the network became largely commercial and grew exponentially.^([^(256)](#fn256))
    
    ### [5.1.1 Protocols](#contents.xhtml#re_h-5-3)
    
    A protocol is a digital language and set of specifications and procedures followed throughout the network so that computers in different locations can share information and resources, making the network viable. Networks can connect many different types of computers and share resources that reside on widely different types of servers. Without a viable protocol, no network can function.
    
    During the early years of the ARPANET the Network Working Group (NWG) was formed to monitor and oversee the network’s technical aspects. The NWG was instrumental in the development of the ARPANET and set the stage for the development of the Network Control Protocol (NCP) and later the Transmission Control Protocol/Internet Protocol (TCP/IP), the most widely used communications protocol to this day. In 1970, the NWG, under the supervision of Steve Crocker, completed the host-to-host protocol called the NCP. Between 1970 and 1972 the NCP was implemented on the ARPANET, enabling network users to develop applications. Besides Crocker, Vinton G. Cerf, one of the co-founders of TCP/IP, had been involved in NCP design and development.^([^(257)](#fn257))
    
    In1974, Vinton G. Cerf and Robert E. Kahn published a paper called “A Protocol for Packet Network Intercommunication Researchers,” which recognized the significance of network intercommunication involving different types of computers, flow control, end-to-end error checking, and topologies.^([^(258)](#fn258))
    
    Later in the 1970s, the government decided to split TCP into two protocols. In 1981, UC Berkeley, working under a contract with DARPA, expanded TCP/IP to include error correction, segmentation, and reassembly. As a result, in 1981, the government eliminated the NCP and adopted TCP/IP as the official protocol for the ARPANET.^([^(259)](#fn259))
    
    ![FIGURE 5.4 A timeline of key network and computer events.](images/fig5.4.jpg)
    
    **FIGURE 5.4** A timeline of key network and computer events.
    
    ### [5.1.2 The World Wide Web and the Internet](#contents.xhtml#re_h-5-4)
    
    The Internet and the World Wide Web (WWW) are not the same. The Internet is a global network of networks that are structured to connect each other, whereas the Web is a service that runs on top of this infrastructure. Imagine our lives today without it!
    
    In the past, the computer center was a room in the basement of a company from which all computer operations were run. With the introduction of networking and the ability to connect to resources and businesses around the world, the old room became outdated and was replaced by enterprise-wide data centers in various locations, with servers connected to the network. Now, these enterprise data centers have been overtaken by cloud computing, virtualization, mobile devices, and the Internet of Things (IoTs), all using edge computing paradigms and fog standards that bring their applications closer to the user. These are discussed more fully in [Chapter 7](#c7.xhtml#c7).
    
    The connection into a network by any device occurs either *wired* or *wirelessly*. In a wired connection, we physically connect a computer into a router using Ethernet cables ([Figure 5.5](#c5.xhtml#f5.5)). In a wireless connection the computer is connected to the network via a radio signal. The Institute of Electrical and Electronics Engineers (IEEE) has defined the standard for wireless communications with Wi-Fi-enabled devices as IEEE 802.11, and for Ethernet wired standard connections as IEEE 802.3.
    
    ![FIGURE 5.5 Ethernet cables. Courtesy of Shutterstock.](images/fig5.5.jpg)
    
    **FIGURE 5.5** Ethernet cables. Courtesy of Shutterstock.
    
    ### [5.1.3 Advantages and Disadvantages](#contents.xhtml#re_h-5-5)
    
    Some of the advantages of *computer networking* are the following:
    
    *   **Central data storage**: data is shared between computing devices/users, and users can access data remotely.
    *   **Cost benefits of shared resources**: when multiple users share resources, such as printers, scanners, copiers, and applications, the business saves money. In addition, by storing data in one centralized database and by sharing peripherals and Internet access, redundancy is reduced, and efficiency is increased.
    *   **Centralized protection and monitoring**
    *   **Ability to access information at a very fast speed**
    *   **Network backup reliability**: ensures that data is backed up onto multiple servers.
    *   **Security**: through authentication that validates the identity of an authorized user, thereby preventing theft or unauthorized accessing of data.
    
    In addition to these advantages, networks have disadvantages as well. Some are:
    
    *   **Cost** of network management and maintenance, including expensive hardware and applications, uninterruptible power supply (UPS), fire suppression equipment, air conditioning, stable temperature maintenance, humidity control, air filtration for dust and other airborne particles, and the training of personnel to run the data center.
    *   **Virus and malware**: Infections can quickly spread on a network system, and repair is time consuming and may interrupt the flow of business.
    
    ### [5.1.4 Essential Computer Network Components and Terminology](#contents.xhtml#re_h-5-6)
    
    A computer network requires different components, which must work together properly. These components are the building blocks of the network and provide the resources to perform its tasks. In addition, the network provides methods and techniques to prevent and monitor unauthorized access, called data breaches.
    
    The most basic form of networking is *peer-to-peer (P2P).* The P2P network is created when two or more computing devices share resources like storage devices, files, and printers without using a server. All computing devices can function as both a client and server ([Figure 5.6](#c5.xhtml#f5.6)).
    
    ![FIGURE 5.6 A peer-to-peer (P2P) network.](images/fig5.6.jpg)
    
    **FIGURE 5.6** A peer-to-peer (P2P) network.
    
    What is a server? The term refers to a piece of hardware or software used to provide resources for other computers or devices, called “clients.”
    
    In networking, a “node” refers to any addressable device, redistribution point, connection point, or communication endpoint that is connected to a network. A node can create, process, recognize, receive, transmit, or store data and requires a unique address for identification to be part of a network. Examples of nodes include computers, network bridges, IoT devices, modems, printers, routers, and switches.^([^(260)](#fn260))
    
    ![FIGURE 5.7 A network with two clients and a server.](images/fig5.7.jpg)
    
    **FIGURE 5.7** A network with two clients and a server.
    
    ![FIGURE 5.8 The client-server communication.](images/fig5.8.jpg)
    
    **FIGURE 5.8** The client-server communication.
    
    In a corporate setting, a network will include a client computer for every employee connected to a server. The client sends and receives requests. A server provides resources to the client such as access to the Internet and to connections like printers, files, programs, and external processing power. Communication occurs when the client sends a message to the server over the network and then waits for a reply. When the server receives the request, it will process it and send back a reply.
    
    The purpose of networking is back-and-forth communication. A network allows computing devices to exchange packets of data safely and securely. To be able to comprehend complex network interactions, we need to understand in detail all the devices that comprise it. All *network devices*, also called *network hardware*, are physical devices that can communicate and interact over the network. *Network software* refers to the application program that runs the network, helping administrators deploy, manage, and/or monitor it. *Network architecture* signifies the way network devices and services are configured and structured. Below are the most important key networking terms, devices, and concepts.
    
    *Access Point (AP)* or *Wireless Access Point (WAP*) is a networking device that contains a radio transmitter and a receiver signal, enabling other computing devices to connect to the network and communicate with each other ([Figure 5.9](#c5.xhtml#f5.9)). An access point can connect routers, switches, and hubs via Ethernet cables or Wi-Fi signals. It can provide a solution to a networking problem, for example, when we want to enable Wi-Fi access to a specific area and we are not within range of the router. The solution is to install an access point and run an Ethernet cable from it to the server. This small, wired connection allows the wireless network to broadcast in a designated area. Access Points operate at Layer 2–Data Link of the OSI model. We will discuss the OSI model later in this chapter.
    
    ![FIGURE 5.9 A ceiling access point Wi-Fi. Courtesy of Shutterstock.](images/fig5.9.jpg)
    
    **FIGURE 5.9** A ceiling access point Wi-Fi. Courtesy of Shutterstock.
    
    *Address Resolution Protocol (ARP)* is a network protocol that finds the Media Access Control (MAC) address of a device from an IP address. [Figures 5.10](#c5.xhtml#f5.10) to [5.12](#c5.xhtml#f5.12) describe the ARP process.
    
    ![FIGURE 5.10 Address Resolution Protocol (ARP)—Step 1 translates IP addresses to MAC addresses.](images/fig5.10.jpg)
    
    **FIGURE 5.10** Address Resolution Protocol (ARP)—Step 1 translates IP addresses to MAC addresses.
    
    ![FIGURE 5.11 Address Resolution Protocol (ARP)—Step 2.](images/fig5.11.jpg)
    
    **FIGURE 5.11** Address Resolution Protocol (ARP)—Step 2.
    
    ![FIGURE 5.12 Address Resolution Protocol (ARP)—Step 3 translates MAC addresses to IP addresses.](images/fig5.12.jpg)
    
    **FIGURE 5.12** Address Resolution Protocol (ARP)—Step 3 translates MAC addresses to IP addresses.
    
    A *bridge* is a network device that connects two or more networks or segments. The bridge is responsible for regulating incoming traffic by inspecting it and deciding whether to forward it or to filter it (block it), thereby reducing unnecessary traffic. A bridge can also store MAC addresses.
    
    *Data packets* are units of data sent over a TCP/IP network, with the goal of transmitting data efficiently and reliably. When we send something over the Internet, the data is divided into small pieces (using the specific size in bytes) to ensure each part is transmitted successfully and to accommodate various bandwidths. By breaking the data into parts, the data packets can evade network congestion caused by simultaneous transfers and can be rerouted via less congested paths. When an email leaves a computing device, the network splits it into data packets. When the packets reach their destination, they are reconstructed and put into the sequence as a single file. Think about it as mailing a jigsaw puzzle. It doesn’t matter which route each mosaic piece is mailed to, as long as all mosaic pieces arrive at the destination and the recipient can combine the shapes into a picture. The reverse happens when we receive an email or a Webpage. We will discuss data packets further in relation to the OSI model.
    
    A packet contains both delivery information and the actual data of the sender. The precise synthesis of a packet differs between protocols, but a typical packet contains three sections, the *header*, the *payload*, and the *trailer* or *footer.* For example, in Internet Protocol version 6 (IPv6), the first section of each data packet is the *IPv6 header*. IPv6 will be described later in the chapter. The main components of an IPv6 header are the following.^([^(261)](#fn261))
    
    **Version** indicates the version of the IP. The header size is 4 bits.
    
    **Traffic class** designates the class or priority settings of IPv6 packet. Its size is 8 bits.
    
    *   **Flow label**: specifies that packets belong to a specific sequence. Examples include real-time data such as voice and video. The size is 20 bits.
    *   **Payload length**: defines the length of the IPv6 payload in octets. An octet is a unit measuring digital information and consists of 8 bits. The size is 16 bits.
    *   **Next header**: indicates the type of the first extension header or the Protocol Data Unit (PDU). This could be TCP, User Datagram Protocol (UDP), or others. The size is 8 bits.
    *   **Hop limit**: designates the maximum number of links that the IPv6 packet can travel before the packet is released. The size is 8 bits.
    *   **Source address**: the originating IPv6 host address. The size is 128 bits.
    *   **Destination of IPv6 address**: stores the destination host. The size is 128 bits.
    
    The *payload* delivers the actual data to its destination, and the *trailer* encompasses information about the destination of the packet.
    
    *Dynamic Host Configuration Protocol (DHCP)* is the client or server that is responsible for assigning dynamic IP addresses to client computers and other related configuration information.
    
    *Domain Name System (DNS)* is a directory of the IP addresses of the entire Internet. The DNS translates domain names, which people can remember, or maps host names into IP addresses. In other words, the DNS allows people to use words in place of an IP address when searching. For example, when we type [www.CISCO.com](http://www.CISCO.com) into a browser, the browser asks the DNS to find the IP address. The DNS will return the IP address for CISCO’s domain name (72.163.4.185), and the browser will connect to the IP address. The user can find an IP address or a website by typing C:\\> nslookup at the command prompt in Windows or at a terminal in Linux. Another way to find an IP address is with ARIN WHOIS IP Address Database Search^([^(262)](#fn262))
    
    **TABLE 5.1** Example of DNS Names and Corresponding IP Addresses
    
      
    | **Name**:**Address**: || microsoft.com131.107.0.89 |
    | --- | --- |
    | **Name**:**Addresses**: || CISCO.com2001:420:1101:1::18572.163.4.185 |
    
    In addition to translating domain names into IP addresses, the DNS has anti-spam defenses, including routing security like the Resource Public Key Infrastructure (RPKI) that safeguards the Internet’s routing infrastructure and firewalls.^([^(263)](#fn263))
    
    Another standard created for the same purpose as SPF is the Domain Keys Identified Mail (DKIM).^([^(264)](#fn264))
    
    Cybercriminals use phishing attacks, to create fake but real-looking websites, tricking users into clicking links in the sites and then giving out personal information. These fake domains impersonate legitimate websites but have entirely different IP addresses.
    
    The DNS is essential because it protects users and businesses from phishing attacks. Therefore, the communication between the user’s computer and the DNS system is vital to direct the correct IP address assigned to a domain name. Usually the Internet Service Provider (ISP) automatically assigns its own default DNS server, but this can change the system’s DNS settings to other free and secure services such as Google Public DNS,^([^(265)](#fn265))
    
    *Gateway* or *Protocol Converters* are network devices (nodes) that can be employed as software, hardware, or a combination of both to connect two dissimilar networks. The gateway is an entry or exit point between networks. The gateway takes data from one network, interprets it, and transfers it to another network. Gateways are usually complex, and since they are found at the edges of a network, they are integrated into routers, firewalls, servers, or other devices that enable traffic to flow in and out of the network. Without gateways we would not be able to communicate with devices, nodes, or networks outside of our own network.
    
    A *hub* connects computing devices and serves as a connection point within a private network or Local Area Network (LAN) by broadcasting packets of data to other connected computing devices ([Figure 5.13](#c5.xhtml#f5.13)). Because the data packets will stay within the local network, the hub does not perform filtering or routing. The drawback of using multiple hubs in a private network is that there may be a *collision* when two or more devices send data at the same time. Another weakness is that when the available bandwidth is split among connected devices, the speed will slow. Hubs operate at Layer 1—Physical layer of the OSI model. Bandwidth is defined as the maximum rate of data transmitted across a network path per unit of time and measured in bits per second.
    
    ![FIGURE 5.13 A hub broadcasts data to all connected hosts.](images/fig5.13.jpg)
    
    **FIGURE 5.13** A hub broadcasts data to all connected hosts.
    
    *Internet Protocol address (IP address)* is a unique identifier assigned to every single computing device on a TCP/IP network. The IP address has two primary functions: it identifies the host’s or network interface identification and location addressing. When a computing device sends data to another device, the data headers contain information about the sending device’s IP address along with the destination device’s IP address. The IP address is like a physical home address for the computer that determines where the mail should be delivered. In 1982, when TCP/IP became the official protocol for ARPANET, IP addresses first emerged. As mentioned earlier, the first version of modern TCP was written in 1973 by Cerf and Kahn.
    
    The first and second Internet Protocols, IPv1and IPv2, were never defined; IPv3 and IPv5 were experimental. Internet Protocol 4, IPv4, was the first version that was used publicly and carried a theoretical limit of 4.3 billion (2^(32)) addresses. So far, IPv4 is the most popular version ever deployed. But, as the Internet grew exponentially, IPv4 ran out of IP addresses, especially after the emergence of mobile and IoT devices. As a result, in 1998, the Internet Engineering Task Force (IETF) created IPv6 to solve this problem.^([^(266)](#fn266))
    
    The organization that is responsible for allocating and maintaining global IP addresses is the Internet Assigned Numbers Authority (IANA).^([^(267)](#fn267))
    
    ![FIGURE 5.14 Map of Regional Internet Registry (RIR RIR). The map was adapted from IANA.](images/fig5.14.jpg)
    
    **FIGURE 5.14** Map of Regional Internet Registry (RIR RIR). The map was adapted from IANA.
    
     **TABLE 5.2** The Regional Internet Registries (RIR) 
    
     
    | Registry  || Area |
    | --- | --- |
    | **AFRINIC** || Africa Region |
    | --- | --- |
    | **APNIC** || Asia/Pacific Region |
    | **ARIN** || Canada, USA, and some Caribbean Islands |
    | **LACNIC** || Latin America and some Caribbean Islands |
    | **RIPE NCC** || Europe, the Middle East, and Central Asia |
    | The table was adapted from IANA. |
    | --- |
    
    *   **IPv4**, first deployed in 1983, uses a 32-bit address and can handle 4,294,967,296 (2^(32)) unique addresses. It is still the most widely used IP version.^([^(268)](#fn268))
    *   **IPv6** uses a 128-bit address, theoretically delivering 2^(128) unique addresses. It offers about 340 trillion trillion trillion combinations, called undecillion, or sextillion or dodekillion and is equal to 10^(36). As opposed to IPv4, which is written in dotted decimal notation, IPv6 is written using hexadecimal notation. An example of an IP address provided by IPv6 for the Microsoft Corporation in Redmond, Washington, United States is 2a01:111: f400:5254::2.
    
    ### [5.1.5 Basic Anatomy of IPv6](#contents.xhtml#re_h-5-7)
    
    IPv6 splits the address into two 64-bit segments, and consists of eight sets of 16-bit hexadecimal values or blocks, separated by colons (:).
    
    For example, if we convert hex 2001 to binary the result is 0010 0000 0000 0001, and if we convert hex 1234 to binary the result is 0001 0010 0011 0100. For more information on hex and binary, see [Chapter 1](#c1.xhtml#c1). The figure below demonstrates the IPv6 structure in hexadecimal. The left four values or blocks indicate the network ID, which is administratively assigned. The right four values or blocks indicate the host or interface ID and are configured manually or automatically (e.g. DHCPv6 or randomly generated numbers). If you think of each value or block as an address, the street is on the network side, left, and the house number is on the right. [Figure 5.15](#c5.xhtml#f5.15) represents one of many different configurations of IPv6 address.
    
    ![FIGURE 5.15 IPv6 structure.](images/fig5.15.jpg)
    
    **FIGURE 5.15** IPv6 structure.
    
    More specifically, the network ID side is split into two smaller parts, the 48-bit *routing prefix* and the 16-bit *Subnet ID (s*ee figure). The *routing prefix* contains the global network addresses and is assigned by ARIN or the ISP. This part is used for routing over the internet. The second part, the *subnet*, is created by the customer on an internal network and is controlled by the network administrator. A *subnet* or *a subnetwork* is a segment of a larger network structure, or a network inside a network. *Subnetting* is been used by administrators to make networks more efficient by allowing traffic to travel shorter distances. The final part, the *Interface ID*, is the unique identifier for a host or a node connected to the network. ^([^(269)](#fn269))
    
    The first two blocks of IPv6 show which block the IP came from. The numbers above the block number indicate ARIN’s specific IPv6 allocation block.^([^(270)](#fn270))
    
    Since the IPv6 specification is exceptionally long, the protocol allows us to shorten the address by omitting leading zeros. For example, in block 5, the hex 0054 can become 54.
    
    If we have consecutive zeros in contiguous blocks, as in blocks 6&7, we can omit them and substitute a double colon **(: :).** Then, the IPv6 looks like this: **2001:0:1234:5678:54::FEFC.**
    
    In the IP world, there are two types of IP addresses: *static and dynamic*. The *static IP* does not change until the device is retired. This type of IP is assigned by the Internet Service Provider (ISP) or by a network administrator.
    
    *   A *static IP* address is assigned to important external computing devices, a server (web server, email server, printer shared within the network) or websites that need to use the IP address so other devices can connect to it quickly. Another example is a Virtual Private Network (VPN). Because Virtual Private Networks (VPN) trust specific IPs, the static IP address provides an easier way to locate the device, more easily set it up, and get better support through the DNS server. This makes it easier to work remotely using VPN and provides better reliability when communicating using Voice over Internet Protocol (VoIP) and video conferencing. However, along with these advantages, the most significant disadvantage of the *static IP* is lessened security. Cybercriminals like hackers know the location of each server on the Internet and the static IP makes it easier to attack since it cannot be disguised. Another disadvantage is that ISPs usually charge more for *static IP* addresses.
    *   The *dynamic IP* is subject to change and is assigned by Dynamic Host Configuration Protocol (DHCP) servers. Some of its advantages include better security. It is harder for hackers to find the location and target networked equipment they are looking for, since the address may have changed. Also, the *dynamic IP* is easier to set up with automatic configuration by the DHCP server. The DHCP automatically assigns computing devices with unlimited IP addresses and is constantly reusing them. The use of *dynamic IP* addresses is less expensive than static IPs. For example, in homes or offices, the ISP’s DHCP server could assign a *dynamic IP* address to a router or other computing devices. When they are disconnected, that IP address may then be assigned to another device. To prevent a conflict when two devices try to use the same *dynamic IP* address, the network or the router automatically removes the old IP and assigns another one. Examples of dynamic address apps include Hulu, DirecTV, and SlingTV.
    
    By default, an ISP or cable company will assign a *dynamic* IP address, unless the user requests a *static* IP. Also, within a network, computing devices are assigned *dynamic* IPs by default. To switch an IP address, the user will need to go to the router's interface, locate the device, and then change the IP address manually. Typically, a network administrator or the ISP can assign a *static* IP. Additionally, an IP can be classified as either a *public* or a *private* IP address. A *public* IP address can be either *static or dynamic* and is accessible to everyone on the Internet. It is unique for each device and is provided by ISPs as soon as the computing device is connected to the Internet gateway.
    
    When the ISP assigns an IP address to a gateway, the gateway permits multiple devices to access the Internet through a single *public IP* address through a process called Network Address Translation (NAT). The NAT limits the number of *public IPs* that an organization must use by translating a *public IP* to *private IP* for security and cost-effective purposes. From a security perspective, NAT enhances security by hiding the internal network from the outside world. NAT is a process in which one or multiple *private IPs* are translated (mapped) into one or multiple *public or global* IP addresses and vice versa. NAT was introduced due to the need for more IPv4 addresses and the vast amount of IT devices.
    
    A *private IP* address is used locally only, for example in a LAN, and is never routed outside of the network. The Internet Assigned Numbers Authority (IANA) reserves IP address ranges for use on private networks.
    
    IPv6 also includes a *type* and a *scope* for interfacing. The three major *types* are *Unicast*, *Multicast*, and *Anycast*.^([^(271)](#fn271))
    
    *   *Unicast addresses* locate a single interface or a node on a network. Once a packet goes to a *unicast* address, the traffic goes from one sender to one receiver or to a specified destination.
    *   *Multicast addresses* locate a set of interfaces or nodes in the network. As soon as a packet goes to a multicast address, the traffic is transported to all interfaces or nodes in the group or within the same physical medium.
    *   *Anycast* addresses locate a set of interfaces or nodes on different physical media. Once the packet goes to an anycast address, it is transported to the closest member of the group or nearest interface or node in the group but not to all interfaces.
    
    An IPv6 address has a specific *scop*e that classifies the topological area for an interface (see [Figure 5.16](#c5.xhtml#f5.16)). These scopes are the *global unicast addresses* and are universally routable across the Internet, with the Prefix always set to binary 001. *Unique local unicast addresses* are for local communication and are routable only inside an internal network and are not routed on the Internet. An example of a unique local unicast address might be an inter-site VPN, a virtual private network across existing Internet connections. The prefix is always set to hex FD or binary 1111 110. Finally, *link local unicast addresses* are used for communication among two IPv6 devices on the same link and are not routed on the Internet, meaning packets cannot move outside the link or to joined networks. This address always starts with hex FE80 or binary 1111 1110 1000 0000.^([^(272)](#fn272))
    
    ![FIGURE 5.16 The scope of IPv6 address.](images/fig5.16.jpg)
    
    **FIGURE 5.16** The scope of IPv6 address.
    
    *Protocols* are a set of specifications and procedures used by systems to communicate with each other. Important protocols are the TCP and HTTPS.
    
    A *port* is a number used to identify a communication endpoint on a network. More specifically, it is a programming docking point to which information flows. [Table 5.3](#c5.xhtml#t5.2). demonstrates the most common protocols used on the internet with their *port* numbers.^([^(273)](#fn273))
    
    **TABLE 5.3** Common Protocols Used on the Internet with Their Port Numbers
    
      
    | Port # || Protocol Name || Purpose |
    | --- | --- | --- |
    | 67 & 68 || DHCP—Dynamic Host Configuration Protocol || Automatically assigns dynamic configuration of IP addresses to clients (client/server protocol). |
    | --- | --- | --- |
    | 53 || DNS—Domain Name System || A standard protocol that translates host names into IP addresses. This naming scheme governs how computers exchange data on the Internet. |
    | 20 & 21 || FTP—File Transfer Protocol || A network protocol used for the transfer of files between a client and a server on a network. |
    | 80 || HTTP—Hyper Text Transfer Protocol || An application protocol for displaying and distributing Web pages. Its main goal is to send data between the web browser and a website. |
    | 443 || HTTPS—Hyper Text Transfer Protocol Secure || An encrypted version of HTTP protocol with SSL/TLS used in communication. The main goal is to increase the security of data transfer. This secure protocol ensures: *authenticity*—being on the real website, *confidentiality*—the connection is encrypted, *integrity*—ensures that data has not been tampered or modified between the client (visitor) and the server (website). |
    | 1 || ICMP—Internet Control Message Protocol || This protocol is for error testing, reporting, and querying for connectivity issues. |
    | 119 || NNTP—Network News Transfer Protocol || An application protocol for distributing, inquiring, retrieving, posting, and transferring newsgroup articles (USENET) from both client/server and server/server. |
    | 110 || POP3—Post Office Protocol version 3 || Protocol for retrieving email from a server. |
    | 22 || SFTP—Secure File Transfer Protocol || Secure file transfer. |
    | 25 || SMTP—Simple Mail Transfer Protocol || Email is sent using this protocol. |
    | 22 || SSH—Secure Shell || A protocol for secure remote access to a remote computer or a server. A secure (encrypted) method for file transferring. Is intended to execute commands like login remotely. |
    | 443 || SSL—Secure Socket Layer || Like the TLC, creates an encrypted HTTPS connection between two computers over the Internet. Intended for data transmission. |
    | 23 || Telnet || This client–server protocol for remote access or login via text-based inputs and outputs (command-line utility). This is an insecure connection. |
    | 443 || TLC—Transport Layer Security protocol || An encryption protocol that provides confidentiality and integrity between two computers over the Internet. |
    
    *Protocol Data Unit (PDU)* is a term describing the names for data packets as they travel in different layers of the OSI model ([Figure 5.17](#c5.xhtml#f5.17)). When a *PDU* arrives at the *Transport Layer*, it is called a *TCP segment* or a *UDP datagram* (most applications use the TCP protocol); when the unit travels into the *Network Layer* it is called a *packet*, and when it moves into the *Data Link Layer* it is called a *frame*. We will discuss segments, packets, and frames along with the OSI model later in this chapter.
    
    ![FIGURE 5.17 The Protocol Data Unit (PDU) at the different layers of the OSI model.](images/fig5.17.jpg)
    
    **FIGURE 5.17** The Protocol Data Unit (PDU) at the different layers of the OSI model.
    
    *Media Access Control Address* or *Physical Address* is a unique, 48-bit, identification number allocated to every computing device’s Network Interface Card (NIC) by the manufacturer. The MAC address does not change; it is hard coded into the NIC or stored in Read Only Memory (ROM). The uniqueness of MAC addresses is registered by the IEEE, which assigns blocks of MAC addresses for a fee to manufacturers. Nonetheless, the address can be configured using manufacturer-supplied software.^([^(274)](#fn274))
    
    MAC addresses consist of 12-digit hexadecimal numbers, 48 bits or 6 bytes. The first 3 bytes (24 bits or 2^(24)) represent the Organizationally Unique Identifier (OUI) or manufacturer’s code assigned by the IEEE. The following 3 bytes (24 bits or 2^(24)) identify the NIC from its manufacturer.^([^(275)](#fn275))
    
    ![FIGURE 5.18 The MAC address structure.](images/fig5.18.jpg)
    
    **FIGURE 5.18** The MAC address structure.
    
    *Network Address Translation (NAT)* allows network devices like routers to connect private IP networks to the Internet by replacing the private IP with a public IP address. The NAT acts as a “receptionist or a dispatcher” between the Internet (public IPs) and local network (private IPs). With this method, only a single IP address is needed to connect an entire group of local computing devices to the Internet.^([^(276)](#fn276))
    
    The *Network Interface Card*, also known as *Network Interface Controller* or *Network Adapter*, is a piece of computer hardware that permits a computing device to connect to a network via wired or wireless connections. A NIC card’s address is the MAC address of the device.
    
    ### [5.1.6 Using Network Utilities](#contents.xhtml#re_h-5-8)
    
    *Network Utilities* are software tools that analyze, diagnose, and configure many aspects of computer networking and begin working on solutions. Some of the most common open source utilities include:
    
    *   **Angry IP Scanner**: a cross-platform network scanner.^([^(277)](#fn277))
    *   **CISCO Packet Tracer**: network simulation, used to test network environments before implementation. It may work across different platforms.
    *   **iPerf3**: network problem solving, performance measurement, and tuning (Microsoft Windows, MacOS, Linux).^([^(278)](#fn278))
    *   **Netstat** or **Network statistics**: delivers basic statistics on network activities on most operating systems.^([^(279)](#fn279))
    *   **Nmap**: network scanner and monitor for unauthorized devices and open ports (supports cross-platform).^([^(280)](#fn280))
    *   **PuTTY**: used to access and configure network devices (Microsoft Windows, MacOS, Linux).^([^(281)](#fn281))
    *   **Wireshark**: collects and interprets network traffic (supported cross-platform).^([^(282)](#fn282))
    
    Additionally, some of the key network utilities included with the common operating systems (OS) are the following:
    
    *   **arp**
    *   The *arp* utility command is used to display and modify the Address Resolution Protocol (ARP) cache and to list the IP and MAC addresses for any devices. The command *arp-a* displays the MAC addresses.  
          To use this command, in Windows, go to Search, and type **cmd** to get the command prompt screen; then type the command **arp**.  
          In Unix or Linux, go to the *Terminal app* and type **arp**.
    
    *   **ipconfig**
    *   The *internet protocol configuration* is a utility that is used to display information on TCP/IP configuration and information on how to set or display the IP address and netmask of a network interface. Once we type **ipconfig** in the command prompt screen, the operating system will return a signal containing IPv4 and IPv6 addresses, subnets, and default gateways which are connections to the Internet. This command can also verify if the computer has the right IP configuration.  
          To use *ipconfig*, in Windows, go to Search, and type **cmd** to get the command prompt screen; then type the command. Entering **ipconfig/all** command will get the full TCP/IP configuration; **ipconfig/flushdns** empties the DNS cache with name resolution issues. As mentioned earlier, the DNS server converts domain names into numerical addresses. Depending upon the operating system or browser, the DNS temporarily stores information about previous DNS searches. We use this command to “flush the DNS” in order to hide search behavior/history, uncover security reasons such as manipulation and DNS spoofing, and solve technical problems like incorrect or old IPs and updated IP information. Linux has replaced **ifconfig** with ip. For example, **ip-4 a** is to see IPv4 information and **ip-6** is to see IPv6 information.^([^(283)](#fn283))
    *   You can also use the **ifconfig** command to see all network-connected devices, including their IP and MAC addresses.
    *   **ping** 
        *   This command is used for confirming network connectivity with TCP/IP and local computers. The command also provides reports on any packet loss. You can use *ping* at the Windows **cmd** prompt, and at the *Terminal app* on Unix or Linux.
    *   **netstat**  
          This command displays information about incoming and outgoing activity in the network connection. *Netstat* will display all active TCP/IP connections and can be used with Windows, Terminal app, Unix, or Linux.
    *   **tracert** 
        
        *   This command is like ping, but *tracert* delivers more detail on packet routes that went through to the destination and also measures transit delays, including “hops,” switches, routers, and DNS information.
        
          
          To use tracert, at the Windows cmd**,** enter **tracert**; on Unix or Linux use the Terminal app command and enter **traceroute.**  
          *Repeater* is a network device that receives and regenerates the signal over the same network. A repeater does not understand frames or packets or headers and cannot perform intelligent routing but only regenerates and reproduces the signal. The repeater operates at the Layer 1—Physical Layer of the OSI model.
    
    *Routers* are virtual or physical network devices that function as dispatchers by forwarding data packets between different IP networks. Additionally, a router evaluates data packets and chooses the best routes on which to send them.
    
    *Servers* are computer hardware or software that accept and respond to requests made by a client over a network. The client creates the request and sends it to the server, the server then returns the requested information to the client. A server runs on a remote computing device, providing services to the clients, and a client is a program that runs on the local computing device that requests services from a server ([Figure 5.19](#c5.xhtml#f5.19)). 
    
    ![FIGURE 5.19 The client-server model.](images/fig5.19.jpg)
    
    **FIGURE 5.19** The client-server model.
    
    *Standards* are sets of rules for components and systems manufacturers that define how to communicate in different settings. For example, Ethernet-based networks are defined by IEEE 802.3 standards, issued by the IEEE, and Bluetooth devices are defined by Bluetooth Low Energy 5.1, which is a wireless technology standard for exchanging data over short distances.
    
    *Switches* are multiport devices that connect computing devices in a network and act like controllers. Switches vary from *hubs* because they handle data packets differently, by performing error checking and by not forwarding data packets that have errors. Therefore, switches improve efficiency and performance. Additionally, a *switch* is a device in the data link layer or layer two of the seven-layer OSI model (see OSI model) that allows devices on a network to communicate with each other as well as with other networks. Switches operate at Layer 2—Data Link of the OSI model ([Figure 5.20](#c5.xhtml#f5.20)).
    
    ![FIGURE 5.20 The Network Switch.](images/fig5.20.jpg)
    
    **FIGURE 5.20** The Network Switch.
    
    *Virtualization in computing* or *VM* is the technology of creating software-based or virtual services like operating systems and servers by distributing capabilities and enabling a single machine to act like multiple simulated devices. *Virtualization* is a cost-saving method. A *hypervisor* is the software that creates and manages virtual machines ([Figure 5.21](#c5.xhtml#f5.21)). 
    
    ## [5.2 Types of Networks](#contents.xhtml#re_h-5-9)
    
    To be able to meet evolving demands and needs, different types of networks have been designed.
    
    The most common types of networks ([Figure 5.21](#c5.xhtml#f5.21)) are the following:
    
    ![FIGURE 5.21 A Typical Network.](images/fig5.21.jpg)
    
    **FIGURE 5.21** A Typical Network.
    
    *   **CAN (Campus Area Network)**: As the name indicates, this type of network is designed for educational institutions like campuses, colleges, schools, and universities. A CAN network is larger than a LAN and smaller than a Wide Area Network (WAN) ([Figure 5.22](#c5.xhtml#f5.22)).
    *   **PAN (Personal Area Network)**: It is a short-range network that serves one person as the name indicates. For example, using an app on a mobile device like a wrist fitness tracker, heart rate monitor, or pedometer with a Bluetooth device is a PAN. When a person connects any two devices such as a mobile phone and a computing device or shares emails, photos, text messages, and more, this is also done within a Personal Area Network ([Figure 5.23](#c5.xhtml#f5.23)). 
    *   **LAN**: It is a medium-range network that spans an area inside a single room, building or group of buildings, office, factory, or school, allowing the sharing of data, files, and resources. A LAN might connect all the computers in a school or a building and could contain both wired and wireless devices ([Figure 5.24](#c5.xhtml#f5.24)).
    *   **MAN (Metropolitan Area Network)**: It is a long-range network that provides communications over a larger area than a LAN and a smaller area than a WAN. Examples include citywide networks; governmental bodies typically own and administer MANs ([Figure 5.25](#c5.xhtml#f5.25)).
    *   **WAN (Wide Area Network)**: It is the largest area communications network. It can span a large geographic area and can connect multiple networks in a country, from region to region or throughout the world. The largest WAN is the Internet, connecting millions of networks around the globe. WAN connectivity can be accomplished by leased fiber lines and satellite links.
    *   **WLAN (Wireless Local Area Network)**: It is like a traditional LAN, but instead of Ethernet cable it uses high-frequency radio waves to connect and communicate wirelessly ([Figure 5.26](#c5.xhtml#f5.26)).
    *   **Virtual Local Area Network (VLAN)**: It is a logical instead of physical connection of different nodes in one or more LANs. Additionally, the LANs are configured to communicate as if they are physically connected.^([^(284)](#fn284))
    *   **VPN (Virtual Private Network)**: It is a point-to-point secure network connection for traffic in transit across the Internet. Significantly, a VPN establishes some privacy by encrypting a personal tunnel and encircling the user’s identity. More specifically, it directs the user’s traffic through a VPN server and masks the user’s IP original address, acting as a middleman. As a result, the mixture of routing to a VPN server, masking of IP address, and the private tunnel encryption makes snooping more difficult for cybercriminals, the government, and ISPs ([Figure 5.27](#c5.xhtml#f5.27)).
    
    ![FIGURE 5.22 A CAN.](images/fig5.22.jpg)
    
    **FIGURE 5.22** A CAN.
    
    ![FIGURE 5.23 A PAN.](images/fig5.23.jpg)
    
    **FIGURE 5.23** A PAN.
    
    ![FIGURE 5.24 A LAN.](images/fig5.24.jpg)
    
    **FIGURE 5.24** A LAN.
    
    ![FIGURE 5.25 A MAN.](images/fig5.25.jpg)
    
    **FIGURE 5.25** A MAN.
    
    ![FIGURE 5.26 A WLAN.](images/fig5.26.jpg)
    
    **FIGURE 5.26** A WLAN.
    
    ![FIGURE 5.27 A Virtual Private Network.](images/fig5.27.jpg)
    
    **FIGURE 5.27** A Virtual Private Network.
    
    ## [5.3 Network Topology](#contents.xhtml#re_h-5-10)
    
    *Network topology* shows the layout of the network and how its nodes and links are structured to forward, receive, send, and store data. Network topology consists of two categories: *physical*, which contains the devices, maintenance, and wires; and *logical*, which describes the way the network transmits and how data flows.
    
    The correct topology improves performance by assigning resources efficiently across the network and helps in finding errors. The following are the most common types of network topology.
    
    *   A *bus network topology* or *line topology* is when all network nodes and computing devices are connected to a central continuous cable in a single direction. More specifically, the data moves in one direction and follows the route of the central cable. Bus network topology features a simple layout and is a cost-effective method for smaller networks. However, this topology may be vulnerable, since the network is based on one central cable, and if the cable fails the entire network will go down ([Figure 5.28](#c5.xhtml#f5.28)).
    *   A ***mesh topology*** is used when network nodes and computing devices have multiple paths or have overlapped connections. There are two types of mesh topology, *full mesh topology*, in which every node is connected to every other node in a network (see [Figure 5.29](#c5.xhtml#f5.29)), and *partial mesh topology* ([Figure 5.30](#c5.xhtml#f5.30)), where only selected nodes are connected to each other, and others are connected to only one or two devices in the network (see [Figure 5.30](#c5.xhtml#f5.30)). Mesh topology provides reliability and robustness, because it offers redundancy to avoid failure; one link cannot cause a break in the network or in the transmission of data or affect other links. Nonetheless, full mesh topology can be expensive due to the cost of cabling. It is also time consuming and labor intensive to implement. Partial mesh, on the other hand, offers fewer redundancies and is less expensive to implement.
    *   A *point-to-point topology* is the simplest communication connection between two nodes directly connected to each other. Examples include a connection between two computers ([Figure 5.31](#c5.xhtml#f5.31)), a connection between two routers ([Figure 5.32](#c5.xhtml#f5.32)), and a connection between two segments ([Figure 5.33](#c5.xhtml#f5.33)).
    *   A *ring topology* is a configuration where all network nodes and computing devices are connected in a ring or circle ([Figure 5.34](#c5.xhtml#f5.34)). Data can travel either direction, and each node has only two neighbors. This topology is characterized by efficiency in transmitting data without errors and without collision in the network and is easy to troubleshoot. A possible disadvantage is that when we take the ring network down to reconfigure devices or troubleshoot, the entire network is offline. Another disadvantage in this topology is that computer devices share bandwidth, which means there is more traffic on the network, and more delays.
    *   A *star network topology* is configured when all network nodes and computing devices are connected to a central switch that manages data transmission ([Figure 5.35](#c5.xhtml#f5.35)). Data flows from any node through a central hub, which works as a repeater, preventing data loss. The star is the most popular topology, providing higher data transfer speed, easy installation, and management from a single location. A major disadvantage is that when the central switch fails, the entire network cannot function. Also, the cost of installation is higher for the star topology than for other network topologies.
    
    ![FIGURE 5.28 A bus network topology connects all network nodes and computing devices to a central continuous cable in a single direction.](images/fig5.28.jpg)
    
    **FIGURE 5.28** A bus network topology connects all network nodes and computing devices to a central continuous cable in a single direction.
    
    ![FIGURE 5.29 A full mesh topology.](images/fig5.29.jpg)
    
    **FIGURE 5.29** A full mesh topology.
    
    ![FIGURE 5.30 In partial mesh topology, only selected nodes are connected to each other.](images/fig5.30.jpg)
    
    **FIGURE 5.30** In partial mesh topology, only selected nodes are connected to each other.
    
    ![FIGURE 5.31 A point-to-point connection between two computers.](images/fig5.31.jpg)
    
    **FIGURE 5.31** A point-to-point connection between two computers.
    
    ![FIGURE 5.32 A point-to-point connection between two routers.](images/fig5.32.jpg)
    
    **FIGURE 5.32** A point-to-point connection between two routers.
    
    ![FIGURE 5.33 A point-to-point connection between two networks.](images/fig5.33.jpg)
    
    **FIGURE 5.33** A point-to-point connection between two networks.
    
    ![FIGURE 5.34 A ring topology connects computing devices in a ring or a circle configuration.](images/fig5.34.jpg)
    
    **FIGURE 5.34** A ring topology connects computing devices in a ring or a circle configuration.
    
    ![FIGURE 5.35 A star network topology connecting all network nodes and computing devices with a central switch.](images/fig5.35.jpg)
    
    **FIGURE 5.35** A star network topology connecting all network nodes and computing devices with a central switch.
    
    Additional network topologies include the Hybrid and Tree topologies. Since every network topology or configuration is designed for a different purpose, decisions are made by looking at the overall network size, the objectives of the network, and, of course, the budget.
    
    ## [5.4 The Open Systems Interconnection (OSI) Model](#contents.xhtml#re_h-5-11)
    
    The *Open Systems Interconnection (OSI)* is a reference or conceptual model that describes the functions and specified protocols and standards of each conceptual layer, tier, or stratum of a network communication. It was created in 1984, when the International Organization for Standardization (ISO) and the International Telegraph and Telephone Consultative Committee, known in France as the Comité Consultatif International Téléphonique et Télégraphique (CCITT), merged their ideas and procedures to shape the OSI Reference Model.^([^(285)](#fn285))
    
    Besides its educational usages, the OSI helps network administrators troubleshoot a problem within a specific layer, and it helps vendors and manufacturers assist customers in recognizing in which layer their product works. Also, it helps programmers as they develop an application to know where in the model the application will work. The ITU Telecommunication Standardization Sector (ITU-T) provides the OSI standards as recommendations X.200 standards.^([^(286)](#fn286))
    
    *The OSI model is not meant to be an exact science, but it does define the network framework and should be viewed as a guideline; often it does not match the real world exactly* (see [Figure 5.37](#c5.xhtml#f5.37)). We will describe the layers starting with the user interface and move down to the physical connections.
    
    *   **Layer 7—Application** is the interface between the user and the network. This layer is closest to the end user, allowing access to network services like email, Directory Services, Web browsers, video conferencing applications like Zoom and Skype, file transfer, and more. The hands-on work of the user is done in Layer 7.
    *   **Layer 6—Presentation** handles the *syntax*, which is the structure, format, or organization of data, and *semantics*, the “meaning” of the data, of the information being transmitted by the network*.* This layer specifies and handles the presentation of data by translating and changing the native data representations to the transfer syntax. Examples include encryption by transforming the original information to another form or ciphertext, and decryption by transforming the message to its original form or to plain text. This layer also provides data compression to reduce the size of the data and code conversion, including ASCII, Unicode, EBCDIC, TIFF, GIF, PICT, JPEG, MPEG, MIDI, DOCX, HTML, MP3, AVI, and others. The protocols used in this layer are Network Data Representation (NDR) and Lightweight Presentation Protocol (LPP).
    *   **Layer 5—Session** coordinates the mechanisms that organize and structure communication between application processes. Simply put, when two machines need to talk to each other, a session is established to synchronize which machine has the right to transmit or to re-synchronize in case of an error. The *Session layer* is involved in coordinating, setting up, managing, and ending sessions between applications.
    *   **Layer 4—Transport** delivers end-to-end reliable communication over the network. More specifically, this layer receives data from the upper layers (5–7), at which point the data is broken into smaller pieces called *segments* and is passed to the Network layer. The *Transport layer* also ensures that the *segments* correctly reach their destination. Examples of protocols used in Layer 4 are the TCP and User Datagram Protocol (UDP). See [Figure 5.41](#c5.xhtml#f5.41).
    *   **Layer 3—Network** is responsible for transferring and routing *packets* through different routers between sub-networks. In this layer, the *segments* are further processed and form *packets*. A *segment* is inside a *packet* and consists of control information such as the source and destination of an IP address, version of IP used, headers, trailer and data payload (size of the data, defined in octets), and more ([Figure 5.36](#c5.xhtml#f5.36)). This layer is responsible for *packet* forwarding, including routing/switching the packets through different routers, and through error and congestion control. For example, if we would like to connect to a server in Germany, the router at this layer will find the most efficient way to reach the server. Examples of protocols used are IP, NAT, and ICMP. Next, the *packets* are forward to the *Data Link layer*.
    *   **Layer 2—Data Link** coordinates node-to-node data transfers, detects and corrects transmitting errors, forms *packets* into *frames*, and synchronizes the frames. A *frame* is a collection of bits. MAC addresses are part of the frames because frames use MAC addresses, rather than IP addresses. 
    
    ![FIGURE 5.36 Segment, packet and a frame.](images/fig5.36.jpg)
    
    **FIGURE 5.36** Segment, packet and a frame.
    
    ![FIGURE 5.37 The open systems interconnection (OSI) conceptual model.](images/fig5.37.jpg)
    
    **FIGURE 5.37** The open systems interconnection (OSI) conceptual model.
    
    The *Data Link layer* accepts packets from the Network layer and adds headers and trailers, making them into frames. Next, the data link layer sends them to the *Physical layer*. In order to fulfill these tasks, the Physical layer is split into two sublayers. The first is the upper sublayer known as the Logical Link Control (LLC) sublayer, which provides data transfer by communicating with the Network layer and is responsible for frame synchronization, flow and error control, and multiplexing (transmission of multiple data simultaneously over a shared link). The lower sublayer, known as the MAC sublayer, is responsible for communicating with the *Physical layer*. The protocols used in this layer are the Serial Line Internet Protocol (SLIP), Point-to-Point Protocol (PPP), Address Resolution Protocol (ARP) Automatic Repeat ReQuest (ARQ), Asynchronous Transfer Mode (ATM), Integrated Services Digital Network (ISDN), and IEEE 802.3.
    
    **Layer 1—Physical** represents the mechanical and electrical interfaces, a setup of physical connections between devices such as Ethernet cables, optical fiber or radio signals, NIC cards, procedures, and functions of the network. In addition, the *Physical layer* receives *frames* from the *Data Link layer*, converts them into a signal, and transmits them over local media. The protocols used in this layer are Bluetooth, IEEE 802.3, Digital Subscriber Line (DSL), synchronous digital hierarchy (SDH), Request for Comments (RFCs), and varieties of 802.11.
    
    These seven layers consist of two major groups and have different levels of significance ([Figure 5.37](#c5.xhtml#f5.37)). Layers 1–4 (Physical, Data Link, Network, and Transport) are the *lower layers* and perform the processes for data transfer around the network. The primary goal of the *lower layers* is formatting, encoding, and transmission of data, using both hardware and software.
    
    Layers 5–7 (Session, Presentation, and Application) comprise the *upper layers* and signify the application component or application-level data. Their primary goal is to interact with the user interface and run applications to fulfill the user’s requests.
    
    ## [5.5 The Internet Protocol Suite (TPC/IP)](#contents.xhtml#re_h-5-12)
    
    The TCP/IP protocol suite is a large family of protocols that are named after TCP and IP. TCP/IP enables the Internet to work by helping computers talk to each other from anywhere on the Internet. Its procedures are consistent and stable, and they are used reliably. The TPC/IP model emerged from the ARPANET.
    
    As mentioned earlier, TCP/IP was invented in 1974 by Drs. Vinton G. Cerf and Robert E. Kahn.^([^(287)](#fn287))
    
    The TCP/IP model contains four layers and constitutes a simplified version of the OSI model. The OSI and TCP/IP models are the two most widely used networking models for Internet communications. TCP/IP encompasses multiple processes that are required for sending and receiving data; these processes must be sent using the same interface, the IP layer. The data is then directed to the transport layer and is managed there by either TCP or UDP. As a result, TCP/IP can perform multiplexing by mixing multiple signals into one signal or session or into several applications, using the same IP address to communicate with the network.
    
    Examining the layers, we can see that TCP/IP is essentially a shorter version of the OSI model, consisting of four instead of seven layers. The four layers are:
    
    *   **Application Layer** (corresponding to layers 5–7 in OSI): This layer is responsible for the user interface, allowing users to access its services. Examples of these services include the web browser, email client, and file transfer clients. Like the *Application layer* of the OSI model, the following are protocols used by this layer: 
        *   Dynamic Host Configuration Protocol (DHCP)
        *   Domain Name System (DNS)
        *   File Transfer Protocol (FTP)
        *   Hypertext Transfer Protocol (HTTP)
        *   Multipurpose Internet Mail Extensions (MIME)
        *   Post Office Protocol (POP)
        *   Real-Time Streaming Protocol (RTSP)
        *   Secure Hypertext Transfer Protocol (SHTTP)
        *   Simple Mail Transfer Protocol (SMTP)
        *   Secure Shell Protocol (SSH)
        *   Telnet Remote Protocol (Telnet)
        *   Trivial File transfer Protocol (TFTP)
        *   Transport Layer Security Protocol (TLS)
        *   Universe Resource Locator (URL)
    *   **Host-to-Host Layer** (layer 4 in OSI): This layer corresponds to the *Transport layer* of the OSI model, providing flow control, segmentation, data transmission, reliability, error control, and end-to-end data integrity. This layer uses the following protocols: 
        *   Transmission Control Protocol
        *   User Datagram Protocol (UDP)
        *   Datagram Congestion Control Protocol (DCCP)
        *   Stream Control Transmission Protocol (SCTP)
    
    The standard protocols used by the *Host-to-Host layer* to provide transfer data and ensure functionality between end systems are the User Datagram Protocol (UDP) and TCP. Both protocols move data between the Application layer and the *Internet layer.* More specifically, the TCP protocol provides a reliable service and connection by ensuring that data packets are resubmitted in case of error.
    
    Unlike TCP, which is a connection-oriented protocol, UDP provides unreliable connectionless services. UDP provides fast transmission and leaves reliability to be controlled by the Application layer. Both TCP and UDP divide data into packets, including the IP addresses of the sender and receiver, along with several configurations, the trailer that indicates the end of the packet and the actual application data. The main difference between the two protocols is how the data packets are transported. [Table 5.4](#c5.xhtml#t5.3) provides a brief summary of key characteristics of each protocol.
    
    **TABLE 5.4** A Brief Summary of Key Characteristics of TCP and UDP Protocols
    
      
    | TCP || UDP |
    | --- | --- |
    | Reliable protocol || Unreliable datagram protocol |
    | --- | --- |
    | Lower speed || Higher speed |
    | Connection-oriented protocol || Connectionless |
    | Error detection and correction || No error detection and correction |
    | Congestion control || No congestion control |
    | Acknowledge segments || Only via checksum |
    | Segment retransition and flow control || No retransition and flow control |
    
    ### [5.5.1 TCP](#contents.xhtml#re_h-5-13)
    
    The TCP is a reliable host-to-host, connection-based protocol. Connection-based protocol means that before any data can be transmitted, a reliable connection between hosts must be achieved and acknowledged. Its speed is slower than UDP, but it is more reliable, with fewer errors occurring. All packets sent are traced so no data is lost or corrupted during transit. TCP, unlike UDP, requires the recipient and the sender to communicate and establish a connection, acknowledging that packets have been received. If packets are not acknowledged by the recipient, they are sent again. Consequently, this back-and-forth communication makes TCP slower than UDP. TCP guarantees delivery of data packets to *port* 4321 just as they were sent. As defined earlier, a port is a physical interface or an endpoint that identifies a transaction over a network by the host and the service. See [Table 5.3](#c5.xhtml#t5.3).
    
    Because TCP is connection-oriented, only when the connection has been established and checked can it be verified that a message has been received. If the message has not been received the TCP sends it again. Only when the connection is established can the user’s data be sent from either direction. This connection is called a “handshake.”
    
    TCP uses a *three-way handshake*. The three parts of the handshake are **SYN** for Synchronize; **SYN-ACK**, for Synchronize Acknowledgment; and **ACL** for Acknowledgment, respectively. [Figure 5.38](#c5.xhtml#f5.38) demonstrates the *handshake* process.
    
    ![FIGURE 5.38 TCP uses a three-way handshake.](images/fig5.38.jpg)
    
    **FIGURE 5.38** TCP uses a three-way handshake.
    
    When two hosts want to send information back and forth, they can negotiate the parameters of the connection before requesting the connection be set up or before transmitting data. To start a TCP session, the host sends a **SYN** packet to the server. This is a request to synchronize the devices. The server receives the **SYN** and responds with a **SYN-ACK** packet. This means that the SYN request has been received and acknowledged. Finally, the host receives the server’s **SYN-ACK** and sends an ACK packet and the TCP socket connection is established. The *three-way handshake* is a process which is used to describe client (host A) and server (host B) communications on a TCP/IP network. This is a standard method for computing devices to communicate regardless of the brand.
    
    The essential function of this protocol is to provide host-to-host or end-to-end communication services between an application program and the IP. Another important role for TCP is to handle and detect errors and request retransmission of out-of-order delivery packets. When the network is congested, IP packets can be misplaced, duplicated, or arrive out of order. The protocol can detect these problems and request retransmission of misplaced packets, or it can sort the out-of-order queue and reduce the congestion. As soon as the protocol reassembles the packet data in the correct order, it transmits the packet to the application program. Additionally, TCP can identify duplicate messages and will reject them. Finally, TCP uses *flow control mechanisms* to slow data transfer and avoid senders sending data too fast for the TCP receiver. All these features make TCP an end-to-end reliable transport protocol.
    
    ### [5.5.2 UDP](#contents.xhtml#re_h-5-14)
    
    The User Datagram Protocol (UDP) is a faster communication protocol than TCP, but it is unreliable. UDP is a transport layer protocol defined by RFC 768.^([^(288)](#fn288))
    
    Both protocols are built on top of the Internet Protocol (IP), and both send data across the Internet from one IP address to another. TCP allows applications to exchange data with the lowest amount of overhead. UDP, however, instead provides unreliable datagram connectionless services and cares about fast transmission, leaving reliability to be controlled by the Application layer. The word “unreliable” means that the protocol does not have a method for confirming that data packets have reached their destination correctly. Another important distinction between TCP and UDP is that UDP does not provide any communication security. For security protection against eavesdropping, message forgery, and tampering, additional protocols are required.
    
    In summary, UDP does not offer reliable delivery and extra security overhead, offering no acknowledgment that packets have been received. This speeds up connections and reduces latency. With UDP, when one computing device sends packets of data to another, delivery cannot be guaranteed, a kind of “send it and forget it” technique. UDP is faster than TCP because it eliminates functions like error checking and recovery services. UDP chooses speed over integrity, and data received may not exactly match the data sent. UDP is faster and TCP is more reliable. UDP is used for streaming games, live broadcasts, and videos. [Figure 5.39](#c5.xhtml#f5.39) demonstrates the UDP protocol.
    
    ![FIGURE 5.39 The User Datagram Protocol (RFC 768).](images/fig5.39.jpg)
    
    **FIGURE 5.39** The User Datagram Protocol (RFC 768).
    
    *   **Internet Layer**: This layer provides the same services as OSI’s Network layer. The layer routes packets, or datagrams, from a source to a destination host and defines addressing of the host by identifying on which network the device resides. The IP uses the TCP/IP transmission method. The main task of this layer is to send packets, regardless of the route they use to arrive at the *destination.* The protocols used are: 
        *   IP-Internet Protocol (IPv4/IPv6)
        *   Internet Control Message Protocol (ICMP)
        *   Internet Group Management Protocol (IGMP)
        *   IPsec (Internet Protocol Security)
    *   **Network Access or Network Interface** (Layers 1–2): This layer is responsible for physical connections to the network, providing a blend of the OSI model’s *Data link* and *Physical layers.* The Network layer includes Ethernet and optical, or wireless, radio wave technology, such as cellular and Wi-Fi standards that work along with the NIC card on a computer device. This allows the computer to access the network infrastructure and send data to other devices. The main responsibility for this layer is to transmit information over the same network between devices. The following protocols are used in this layer. 
        *   Address Resolution Protocol (ARP)
        *   Reverse Address Resolution Protocol (RARP)
        *   Serial Line Internet Protocol (SLIP)
        *   Ethernet (IEEE)
        *   Point-to-Point Protocol (PPP)
    
    [Figure 5.40](#c5.xhtml#f5.40) demonstrates the OSI and the TCP/IP models.
    
    ![FIGURE 5.40 The OSI and the TCP/IP models.](images/fig5.40.jpg)
    
    **FIGURE 5.40** The OSI and the TCP/IP models.
    
    ## [5.6 How Everything Works Together on the Internet: A Review](#contents.xhtml#re_h-5-15)
    
    *   On a network, every single computing device can connect to the network or to another device with a wired or wireless connection. All these devices share data and resources.
    *   Every computing device has two unique identifiers, the IP address and the MAC Address or Physical Address. The IP address identifies a computing device globally on the Internet, and the MAC address identifies the device on the local network. Therefore, both addresses are needed to transfer a data packet from the source to the destination. Think of it like sending a postal letter to California. The *data packet* is the actual letter. The envelope resembles the *IP header* that contains the information required to *route* data on the Internet and reach the destination. *Routing* is when a networked computer decides how to send the data packets. Like the postal service, the letter goes from a substation to another substation, until it reaches its destination. Inside the envelope is the actual letter which is called the *payload*. The IP address is like the zip code, and the addresses with the recipient’s name, street name, street address, and house number are the MAC address.
    *   When we use a search engine, the computer sends a request for the information to the network and attaches the device’s IP address to the request.
    *   The search engine now knows where to send the request. Hence, it responds—and with ads as well.
    *   When a computer sends a request and receives an answer, a rule or a protocol manages the communication between all devices that are involved. The TCP/IP protocol suite is a large family of protocols. It defines the communications standards and procedures between devices and governs how data should route and interconnect in a network or Internet.
    *   To be able to connect to a computer network, a device must use either a wired or a wireless connection. If a wired Ethernet connection is required, IEEE 802.3 is the signaling standard that is used. The wireless standard that defines wireless communications is IEEE 802.11 and IEEE 802.16.^([^(289)](#fn289))
    *   One of many examples of network types is a surveillance network, with cameras installed throughout a city to monitor congestion and accidents, detect automatic incidents, issue traffic tickets to drivers who run red lights, and monitor closures and crowd flow.
    *   Another example is a peer-to-peer or device-to-device network that establishes connections between mobile devices and IoTs, using a *mesh network* design to allow communication using extend wireless communication such as Bluetooth or Wi-Fi. Each node communicates with the other, and if one module cannot relay information to another, the network will try a different route. The mesh network is often used to enable communication in areas with poor connectivity, like disaster zones, or when the area is without Internet connection or is in a remote location.
    *   The *switch* connects computing devices and manages node-to-node communication inside a network, using packet switching, to receive and forward data, ensuring that the packets reach their ultimate destination.
    *   Protocols define the format of these communications and set out how they are sent and received.
    *   An *access point* connects the computing devices via a radio transmitter and a receiver signal, without the use of cables.
    *   The *routers*, virtual or physical, act like dispatchers, forwarding data packets between different IP networks and determining the best route for them to reach their destination. Additionally, *routers* protect information from outside security threats by enabling firewalls and acting like a fence between the Internet and computer devices, blocking any information requests from the Internet.
    *   The computer architecture describes the functionality, the physical and logical framework, and how devices are organized in a computing network.
    
    [Figure 5.41](#c5.xhtml#f5.41) illustrates a typical LAN Network.
    
    ![FIGURE 5.41 A typical LAN connected to the Internet.](images/fig5.41.jpg)
    
    **FIGURE 5.41** A typical LAN connected to the Internet.
    
    ## [5.7 Conclusion](#contents.xhtml#re_h-5-16)
    
    Network connectivity has been in a constant state of evolution, with improved virtualization of servers and data centers, the adoption of multi-cloud systems, and the improvement of networking through AI and machine learning. Machine learning will continue to improve troubleshooting by collecting relevant data, correlating them, and then being able to identify a network or application problem. Additionally, machine learning will improve network security by creating a real-time database of security threats, behavior, and detection.
    
    A final technology gaining momentum is the Software-Defined Wide Area Network (SD-WAN) that simplifies and centralizes the operation of a WAN. SD-WANs improve performance by virtualizing the WAN with centralized controls and intelligent management software, providing the network with cost-effective solutions to its problems.
    
    In wireless networking, 5G wireless network technology, Wi-Fi 6 and Mesh networking will soon change how we access the Internet. An autonomous, fast, and intelligent network is the next evolutionary revolution in technology yet to come.
    
    ## [5.8 Key Words](#contents.xhtml#re_h-5-17)
    
     
    | Access Point || Network Interface Card (NIC) |
    | --- | --- |
    | APRA || Network Software |
    | ARPANET || Network Topology |
    | Assigned Names and Numbers (ICANN) || Node |
    |  || Open Systems Interconnection (OSI) |
    | Bridge || Personal Area Network (PAN) |
    | Campus Area Network (CAN) || Payload |
    | Client || Private or Public IP Address |
    | Defense Advanced Research Projects Agency (DARPA) || Protocol  
    Protocol Data Unit (PDU) |
    | Domain Name System (DNS) || Ports |
    | Dynamic IP || Repeater |
    | Dynamic Host Configuration Protocol (DHCP) || Routers  
    Segment |
    | Electrical and Electronics Engineers (IEEE) || Server  
    Standards |
    | Frame || Static IP |
    | Gateway || Switch |
    | Host || Transmission Control Protocol/Internet Protocol (TPC/IP) |
    | Internet Assigned Numbers Authority (IANA) || User Datagram Protocol (UDP)  
    Transmission Control Protocol (TCP) |
    | Internet ||  |
    | Internet Protocol (IP) || Virtualization |
    | Local Area Network (LAN) || Virtual Local Area Network (VLAN) |
    | Metropolitan Area Network (MAN) ||  |
    | Media Access Control (MAC) Addresses || Virtual Private Network (VPN)  
    Wide Area Network (WAN) |
    | MILNET || Wireless Local Area Network (WLAN) |
    | Network ||  |
    | Network Address Translation (NAT) || Wired |
    | Network Architecture || World Wide Web (WWW) |
    
    # [Chapter 6 Computer Security Technology and Principles](#contents.xhtml#re_c6)
    
    DOI: [10.4324/9780429318726-6](https://doi.org/10.4324/9780429318726-6)
    
    ## [Objectives](#contents.xhtml#re_h-6-1)
    
    After completing this chapter, the student will be able to:
    
    *   Understand computer security technology, its history, and evolution
    *   Understand the CIA Triad Model and NIST’s Standards for Security Categorization of Federal Information and Information Systems (FIPS 199)
    *   Recognize the significance of identification, authentication, and authorization in computer security
    *   Understand different types of cyberattacks
    *   Recognize computer security prevention mechanisms
    *   Understand modern encryption methodology
    
    ## [6.1 Introduction](#contents.xhtml#re_h-6-3)
    
    *For every type of cyberattack, there is a defense mechanism. For every defense mechanism, there is a new and unknown cyberattack.*
    
    Imagine that you sent a personal email to a close friend. How would you feel if this email were intercepted and the content posted on social media for everyone to see? To prevent this, we use s*ecurity* measures that permit access to authorized users and detect and deny access to potential intruders or cybercriminals. This chapter will provide an overview of computer security technology and principles, including terminology, types of cyberattacks, and basic encryption.
    
    Ancient civilizations invented various clever ways to hide information and messages from adversaries. Two well-known techniques for keeping information confidential are *steganography* and *cryptography*. The first term, *steganography*, means *covered writing* and derives from the Greek word *steganós* (στεγανός), meaning *covered*, and *graphy* (γραφή), *writing*.^([^(290)](#fn290))
    
    In *steganography*, information is *concealed* or *hidden from view*, and no means are used to change the structure of the information. In *cryptography*, information is encrypted by encoding or *changing the information structure*.
    
    The Greek historian Herodotus (c.486–425 B.C.),^([^(291)](#fn291))
    
    ![FIGURE 6.1 Fragment from Herodotus Histories Book VIII. Photograph from Papyrus Oxyrhynchus 2099.](images/fig6.1.jpg)
    
    **FIGURE 6.1** Fragment from Herodotus Histories Book VIII. Photograph from Papyrus Oxyrhynchus 2099.
    
    *Cryptography* began thousands of years ago, protecting secrets by applying a code to encrypt and then decrypt a message. A parallel technique, called *cryptanalysis*, was invented to breach or break the adversary’s code. According to the book *The Art of War* by the ancient Chinese military strategist Sun Tsu (c. 5th century B.C.), “Knowledge of the enemy’s dispositions can only be obtained from other men. Hence the use of spies, of whom there are five classes: (1) Local spies; (2) inward spies; (3) converted spies; (4) doomed spies; (5) surviving spies.”^([^(292)](#fn292))
    
    Ancient civilizations invented ingenious ways to encrypt or decrypt secret messages. The algorithm or process of implementing both encryption and decryption is called *cipher* or *cypher.* Some examples include evidence of concealed information found in clay tablets as early as 1500 B.C. in Mesopotamia.^([^(293)](#fn293))
    
    Ancient Greeks also used a wooden baton or *scytale* (σκυτάλη) to send cipher messages during military conflicts ([Figure 6.2](#c6.xhtml#f6.2)). Spartans used a belt containing a strip of parchment that contained a written message. When the messenger, wearing the belt, arrived at his destination, the receiver decrypted the message, by wrapping the parchment strip around a *scytale* of the same diameter.^([^(294)](#fn294))
    
    ![FIGURE 6.2 A scytale. Photograph from Free Software Foundation](images/fig6.2.jpg)
    
    **FIGURE 6.2** A scytale. Photograph from Free Software Foundation
    
    **TABLE 6.1** Polybius Square
    
      
    |  || 1 || 2 || 3 || 4 || 5 |
    | --- | --- | --- | --- | --- | --- |
    | 1 || A || B || C || D || E |
    | --- | --- | --- | --- | --- | --- |
    | 2 || F || G || H || I/J || K |
    | 3 || L || M || N || O || P |
    | 4 || Q || R || S || T || U |
    | 5 || V || W || X || Y || Z |
    
    Julius Caesar, on the other hand, used a method called the Caesar cipher or Caesar code, that moved each letter a fixed number of places.^([^(295)](#fn295))
    
     **TABLE 6.2** The Caesar Cipher with Three Shifted Places 
    
     
    | Plain Alphabet  |
    | --- |
    | A || B || C || D || E || F || G || H || I || J || K || L || M |
    | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
    | X || Y || Z || A || B || C || D || E || F || G || H || I || J ||  |
    |  || M || N || O || P || Q || R || S || T || U || V || W || X || Y || Z |
    | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
    | J || K || L || M || N || O || P || Q || R || S || T || U || V || W |
    | Caesar Cipher |
    
    During World War II, the Germans developed and used numerous mechanical and electromechanical machines for encrypting communication. Their best-known cipher machines are the *Enigma* ([Figure 6.3](#c6.xhtml#f6.3)), built by the Chiffriermaschinen Aktiengesellschaft (Cipher Machines Corporation), and the *SZ-40/SZ-42*, built by Standard Elektrik Lorenz ([Figure 6.4](#c6.xhtml#f6.4)). The British gave these encrypting machines the codename FISH Machines.^([^(296)](#fn296))
    
    ![FIGURE 6.3 Enigma machine. Courtesy of Shutterstock](images/fig6.3.jpg)
    
    **FIGURE 6.3** Enigma machine. Courtesy of Shutterstock
    
    ![FIGURE 6.4 Lorenz-SZ42 machine.](images/fig6.4.jpg)
    
    **FIGURE 6.4** Lorenz-SZ42 machine.
    
    Different terminologies have been used to describe computer security*.* All the terms relate to the protection of Internet-connected computing.
    
    The most important subcategories of computer security include:
    
    *   *Application security* is a general term for securing applications. It includes security features within applications and measures often used for finding, fixing, and preventing security vulnerabilities against cyberthreats. Examples include email, Directory Services, Web browsers, video conferencing applications like Zoom and Skype, and file transfers.  
          Application security concentrates on keeping applications and computing devices secure from SQL injection, DoS attacks, data breaches, and more. For additional information on the OSI model and the application layer, see [Chapter 5](#c5.xhtml#c5).
    *   *Cybersecurity* refers to protection from criminal activity facilitated by the Internet. It also relates to the protection of Internet-connected devices, computer programs, networks, and data from cybercriminals. In other words, cybersecurity protects physical security, which consists of sites, equipment, infrastructure, etc., and logical security, which consists of software safeguards such as user passwords, access, and authentication of Information and Communications Technology (ICT). Additionally, cybersecurity includes neglected and non-intentional incidents that compromise the confidentiality, integrity, and availability of computing systems and data*.*
    *   *Network security* involves the use of countermeasures to protect the networking infrastructure, both software and hardware, from intruders.
    *   *Information security*, or *InfoSec*, refers to safeguarding data in storage, in transit, and while being used.
    
    According to 44 U.S.C. 3542—Definitions^([^(297)](#fn297))
    
    > (1) The term “information security” means protecting information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction to provide—
    > 
    > 1.  (A) *Integrity*, which means guarding against improper information modification or destruction, and includes ensuring information nonrepudiation and authenticity. Integrity safeguards that data and systems are authentic, neither modified nor corrupted.
    > 2.  (B) *Confidentiality*, which means preserving authorized restrictions on access and disclosure, including means for protecting personal privacy and proprietary information. Confidentiality ensures that only authorized users can access or modify data and systems and includes methods for protecting privacy. A loss of confidentiality occurs when unauthorized access or security breach occurs.
    > 3.  (C) *Availability*, which means ensuring timely and reliable access to and use of information. Availability ensures accessibility and reliability by authorized users.
    
    These three concepts are commonly known as the *CIA Triad Model*, which has been used in information security to direct policies of keeping and protecting confidential and sensitive data. The National Institute of Standards and Technology (NIST)^([^(298)](#fn298))
    
    ![FIGURE 6.5 The CIA Triad model.](images/fig6.5.jpg)
    
    **FIGURE 6.5** The CIA Triad model.
    
    Vulnerability in any of these areas of security can vary, and it has been necessary to categorize the levels of threat they pose. Therefore, the NIST’s Standards for Security Categorization of Federal Information and Information Systems (FIPS 199) has defined the levels of potential impact for Confidentiality, Integrity, and Availability as Low, Moderate, and High.
    
    The potential impact is **LOW** if—
    
    *   The loss of confidentiality, integrity, or availability could be expected to have a **limilted** adverse effect on organizational operations, organizational assets, or individuals.  
          A limited adverse effect means that, for example, the loss of confidentiality, integrity, or availability might: (i) cause a degradation in mission capability to an extent and duration that the organization is able to perform its primary functions, but the effectiveness of the functions is noticeably reduced; (ii) result in minor damage to organizational assets; (iii) result in minor financial loss; or (iv) result in minor harm to individuals.
    
    *   The potential impact is **MODERATE** if— 
        *   The loss of confidentiality, integrity, or availability could be expected to have a **serious** adverse effect on organizational operations, organizational assets, or individuals.  
            A serious adverse effect means that, for example, the loss of confidentiality, integrity, or availability might: (i) cause a significant degradation in mission capability to an extent and duration that the organization is able to perform its primary functions, but the effectiveness of the functions is significantly reduced; (ii) result in significant damage to organizational assets; (iii) result in significant financial loss; or (iv) result in significant harm to individuals that does not involve loss of life or serious life threatening injuries.
    *   The potential impact is **HIGH** if— 
        *   The loss of confidentiality, integrity, or availability could be expected to have a severe or catastrophic adverse effect on organizational operations, organizational assets, or individuals.  
            A **severe or catastrophic** adverse effect means that, for example, the loss of confidentiality, integrity, or availability might: (i) cause a severe degradation in or loss of mission capability to an extent and duration that the organization is not able to perform one or more of its primary functions; (ii) result in major damage to organizational assets; (iii) result in major financial loss; or (iv) result in severe or catastrophic harm to individuals involving loss of life or serious life threatening injuries. ^([^(299)](#fn299))
    
    Table 6.3 demonstrates the levels of potential impact according to FIPS 199.
    
    **TABLE 6.3** Levels of Potential Impact According to FIPS 199 (Adapted from FIPS 199)
    
      
    |  || Low || Moderate || High |
    | --- | --- | --- | --- |
    | Impact on operations, assets, and individuals. || **Limited** || **Serious** || **Catastrophic** |
    | --- | --- | --- | --- |
    | Impact of the loss of confidentiality, integrity, or availability. || Temporary disruption or reduction of services; small financial loss; minor damage to assets; minor harm to individuals. || Significant service disruption while performing the primary function; significant financial loss; significant damage to assets; significant harm to individuals other than physical injuries or loss of life. || Significant service disruption compromising primary function; major financial loss; major damage to assets; severe harm or injury to individuals, including or loss of life. |
    
    The FIPS 199 levels of impact also include an additional component under integrity called *authenticity*, which means “guarding against improper information modification or destruction and includes ensuring information non-repudiation and authenticity.”^([^(300)](#fn300))
    
    In this chapter we will use *Computer Security* as an umbrella term*.* We define *Computer Security* as the methodology intended to protect computing systems and networks, including hardware, software, and data from unauthorized intruders.
    
    ## [6.2 Understanding Security Terminology](#contents.xhtml#re_h-6-4)
    
    The world of computer security is constantly changing. Attacks occur daily and continue to evolve. Computer security consists of sets of protocols and best practices showing organizations and individuals how to prevent and monitor unauthorized access. To understand these practices, we will need to understand basic security terminology first. Following are some of the most important terms associated with computer security:
    
    *   *Access control*—is a system that permits, restricts, and monitors requests for access to a wide range of hardware and software, including access to computer systems and network resources, information processing services, and entry or exit points to facilities.
    *   *Antivirus software or antivirus protection*—is a program that prevents, detects, monitors, and removes malicious software from a computing system, device, or network.
    *   *Behavioral analytics*—in enterprise security, behavioral analytics software senses abnormal network behavior such as patterns of unusual data transfer. Behavior analytics software detects intrusions that elude firewalls and antivirus software.
    *   *Biometrics*—are unique physical or behavioral characteristics that either identify (*who are you?*) *or* verify (*prove that it is you … are you who you claim to be?*) the user. Physical or physiological characteristics can consist of DNA, facial patterns, fingerprints, hand geometry, a person’s vein patterns, and iris pattern recognition. Behavioral characteristics can include handwriting patterns, voice recognition, typing or keystroke patterns, and signature analysis.
    *   *Cloud security*—is the safeguarding of cloud-based computing systems, including applications, cloud access, data, and infrastructures, using controls, policies, and systems. The goal of cloud security is to reduce threats and protect users when they are accessing data and applications in the cloud.
    *   *Crime-as-a-Service (CaaS)*—an on-demand marketplace found on the Dark Web, where one can purchase cybercrime services and attack tools like exploit kits, ransomware, worms, and phishing tools.
    *   *Software-as-a-Service (SaaS)*—describes the current method of licensing popular software. Instead of purchasing and installing the software from disks, the software is now cloud-based, and we license and download our copies. Examples include Microsoft Office 365, Google Apps, Dropbox, Cisco WebEx, GoToMeeting, and Adobe Photoshop, InDesign, and Acrobat.
    *   *Cyberwarfare*—a nation-state-sponsored cyberattack on another nation-state to harm, alter, destroy, or steal information; to disseminate lies and misinformation; or to conduct espionage and sabotage a computer network. Examples include the distribution of malware that destroys files and social media attacks that distribute false information, manipulating people rather than technology. Another example is the Advanced Persistent Threat (APT) that hacked the U.S. government agencies in late 2020 using a supply chain of SolarWinds Orion products. The hack was classified by the Cybersecurity and Infrastructure Security Agency (CISA) as AA20-352A.^([^(301)](#fn301))
    *   *Data Breach*—access to a computer system or network resulting in the disclosure of information. It may transpire *intentionally* or *unintentionally*. When the breach follows hackers gaining unauthorized access, it is *intentional*; when caused by an employee’s negligence, such as accidental loss of computing devices, stolen or unattended sensitive documents, the breach is *unintentional.*
    *   *Exploit*—refers to a program or a code written to attack or take advantage of a vulnerability and break into a computer system or a network.
    *   *Hacker*—is an individual accessing a computer device or a computer system without the user’s knowledge and authorization. Not all hackers are bad. In assessing the hacker, the essential factor is whether a law, for example the Computer Fraud and Abuse Act (18 U.S.C. §1030), is being broken. Hackers are classified into the following types:
        
        *   *Black-hat hackers* are cybercriminals who break into or gain unauthorized access to a computer system with malicious intentions. The primary motivations are financial gain, cyber espionage, and competition between hackers.
        *   *White-hat hackers* or *ethical hackers* are the “good guys of hacking,” who utilize the same techniques as black-hat hackers but access systems with permission to identify security vulnerabilities and exploits. Companies hire white-hat hackers to perform penetration testing and find security vulnerabilities before cybercriminals do, performing security audits and checking for security gaps. Professional certifications are offered for ethical hacking. See Appendix I for information on hacking and other certifications.
        *   *Gray-hat hackers* are somewhere between black and white hat and do not have criminal motives. They will identify security vulnerabilities and exploits in computing systems without permission from the owner. After the defect is found the gray-hat hacker will inform the owner of the system and demand a small fee to repair the vulnerability, mentioning that otherwise the hack might be published. The motive is mostly personal enjoyment ([Figure 6.6](#c6.xhtml#f6.6)).
        *   *Script kiddies* or *amateurs* are individuals who use tools and follow instructions that are easily found online. Assumed to be juveniles who lack the ability to write complex programs or exploits, their main objectives are to impress friends, curiosity, enjoyment of a challenge, or an attempt to enter a professional hacking group.
        *   *Hacktivists* are individual hackers driven by an ideology or are politically inspired.
        
        ![FIGURE 6.6 Black-hat, gray-hat, and white-hat hackers. Courtesy of Shutterstock](images/fig6.6.jpg)
        
        **FIGURE 6.6** Black-hat, gray-hat, and white-hat hackers. Courtesy of Shutterstock
        
    *   *Intrusion Detection System (IDS)*—is a hardware or a software application installed on the network that detects, logs, and screens for malicious attacks and intrusions based on security policies or rule violations on the network. The IDS identifies possible incidents, compares anomalies to normal activities, and recognizes deviations.
    *   *Intrusion Prevention System (IPS)*—is a hardware or a software application that detects and blocks intrusions on the network by examining network traffic flows and attempts to prevent any exploit from reaching its destination. More specifically, the IPS is designed to block threats, analyze, and stop data packets from being delivered based on a predefined set of security rules and policies.
    *   *Protocols*—are a digital language and set of specifications used by systems to communicate with each another. Important protocols are the Transmission Control Protocol (TCP) and Hypertext Transfer Protocol Secure (HTTPS). Each protocol uses precise rules and has an exact purpose on a specific port (see [Chapter 5](#c5.xhtml#c5)). Some of the most common security protocols include: 
        *   Secure Sockets Layer (SSL) and Transport Layer Security (TLS), protocols for encrypting and securing communications over a network. The SSL has been replaced by the TLC but is still commonly used.
        *   The Secure Shell (SSH) protocol provides secure remote login from one computer to another via an unsecured network (SSH client connecting to the SSH server).
        *   The Hypertext Transfer Protocol Secure (HTTPS) sends data between a Web browser and a website. HTTPS is encrypted using TLS in order to increase the security of data transfer.
        *   The Pretty Good Privacy (PGP) is an encryption protocol that allows a receiver to authenticate the identity of a sender who has sent the message and verifies that it was not altered in transit. The PGP uses a combination of symmetric and asymmetric encryption and has been used in encrypting and decrypting texts, emails, files, and other messages.
    *   *Security Audit*—is an impartial assessment and examination of an organization’s information security systems. The Security Audit should include the following: 
        *   Review of regulations, operational procedures, and practices.
        *   Assessment of infrastructure such as security architecture, evaluation of internal and external vulnerabilities, and assessment of security configuration.
        *   Audit of specific applications such as penetration testing and source code reviews.
        *   Assessment of physical security, including the protection of facilities, personnel, equipment, property, alarms and access controls, and surveillance cameras that display sensitive areas such as data centers.
    *   *Security Threat*—refers to a possibility or an action that can compromise computing systems.
    *   *Spam—*any unwelcome electronic messages sent in bulk. Spam may be an advertising campaign or a malicious worm or virus with a primary mission to infect.\\
    *   *Virtual Private Network (VPN)*—is a point-to-point secure network connection for traffic across the Internet. Significantly, a VPN is built on top of existing physical networks and establishes some privacy by encrypting a personal secure tunnel, which encircles the user’s identity. As a result, the combination of routing traffic to a VPN server, masking of IP address, and the private tunnel encryption makes intrusion and interference more difficult for cybercriminals, the government, and ISPs.
    *   *Why Is a VPN Necessary?*—When we open a Web page on the Internet, data flows from our modem to our Internet Service Provider (ISP), and then across the Internet until it finds its destination Web server. The server replies with data that comes back via the same route. All these data require IP addresses. As a result, every network *logs* our IP address and the address that has been requested. The Web server then connects and collects data about us and about our destination. These sites are often not secure, and hackers can easily steal data. In addition, some countries allow ISPs to sell or to provide consumer data to their governments.
    *   *How Does a VPN Work?*—The VPN enables a computer user to create an encrypted private connection over public networks (Internet) and disguises the actual IP address and location. The IP address communicating with the Web server will no longer display the user’s IP address but instead will display the IP address of the VPN service. The VPN server assigns a new IP address and transmits data through encrypted tunnels.
    *   The VPN application first encrypts data and then sends it to the VPN server via a secure connection. Next, the VPN server decrypts the data and sends it over the Internet, waiting for a reply. The VPN is like a bridge or a middleman between a user’s computing device, like a cellphone, tablet or home network, and the Internet. Each message is encrypted before being sent and then decrypted by the VPN server when it is received. The VPN creates a safe and encrypted connection over a less secure Internet. Some of the most common VPN protocols are IPsec—Internet Protocol Security, IKEv2—Internet Key Exchange version 2, Secure Socket Tunneling Protocol (SSTP), SSL/TLS—Transport Security Layer (TLS) and its predecessor secure socket layer, and L2TP/IPSec—Layer 2 Tunnel Protocol. [Figure 6.7](#c6.xhtml#f6.7) demonstrates a typical VPN connection.
    *   *Vulnerability*—refers to a security flaw or weakness in a computing system or software that can be exploited by hackers. They may attempt to gain unauthorized access by forcing computing systems to act in unintended ways, run the hacker’s codes, install malware, and destroy, modify, or steal sensitive data.
    
    ![FIGURE 6.7 A typical VPN connection.](images/fig6.7.jpg)
    
    **FIGURE 6.7** A typical VPN connection.
    
    ## [6.3 Types of Cyberattacks](#contents.xhtml#re_h-6-5)
    
    The interconnected world makes our lives easier but also makes us vulnerable to cybersecurity attacks. These attacks infect our computing systems with malicious code, modify data, and threaten our civil liberties by exposing our personal information. Starting in the 1970s with John Draper’s hack of a phone system, cybercriminals have continued to become more sophisticated and rarely get caught (see [Chapter 2](#c2.xhtml#c2)).
    
    Cybercrime today is a large-scale sophisticated enterprise that adjusts the business model to meet customer’s demands. In some cases, cybercriminals or hackers for hire are connected to governments or other large organizations, penetrating computer systems or networks around the world. An example is the APT attack associated with nation-state criminal organizations.
    
    In computer security, cyberattacks are classified as *Active* and *Passive*.^([^(302)](#fn302))
    
    ![FIGURE 6.8 Active and passive attacks.](images/fig6.8.jpg)
    
    **FIGURE 6.8** Active and passive attacks.
    
    Example of *Activ*e attacks include exploits, DoS, DDoS, malware, phishing, and brute-force attacks like password cracking, viruses, and worms. *Passive* attacks consist of system surveillance like keystroke loggers that record every keystroke, malware that can eavesdrop on emails, and other communications like voice recordings and metadata analysis.
    
    Attacks may occur from inside an organization’s network or from an outside source like a hacker. [Figure 6.8](#c6.xhtml#f6.8) shows active and passive attacks.
    
    A *cyberattack* is an intentional exploitation and malicious action that targets computing systems, networks, and personal computing devices. Cybercriminals use a broad range of techniques to cause maximum disruption and increase their profit.
    
    The *attack vector* in cybersecurity refers to methods used to gain unauthorized access or to penetrate the targeted computing system.
    
    A database that provides references and descriptions of officially known security vulnerabilities and exposures is called the Common Vulnerabilities and Exposures (CVE).^([^(303)](#fn303))
    
    The main reasons that cybercriminals or hackers access unauthorized computing systems are *Cyberwarfare*, *Disgruntled employees*, *Revenge*, *Nuisance*, *Espionage*, *Financial gain*, *Fun*, *Hacking enthusiasts*, *Intellectual challenge*, *Hacktivism*, *Malicious competition among businesses*, *Slow network performance (DoS attacks)*, and *ransom.*
    
    [Figure 6.9](#c6.xhtml#f6.9) demonstrates the various motivations of a cyberattack.
    
    ![FIGURE 6.9 Various motivations of cyberattacks.](images/fig6.9.jpg)
    
    **FIGURE 6.9** Various motivations of cyberattacks.
    
    What are these attacks like? Following are some of the most common types of cyberattacks.
    
    ### [6.3.1 Adware](#contents.xhtml#re_h-6-6)
    
    *Adware*, or advertising-supported software, is considered undesirable software, intended to force the user to view or click on an advertisement on the screen. Adware is a *Potentially Unwanted Program (PUP)*, meaning that it is a minor threat and is below the classification of malware. This unwanted software is often placed within a Web browser to generate revenue for its developer or in a user interface as a third-party sponsor that urges the user to install it. Adware exists in all computing device platforms and is usually safe, legitimate, and not malicious. However, cybercriminals could take advantage of the adware developers and might use it as a gateway for malware infection.^([^(304)](#fn304))
    
    ### [6.3.2 Denial-of-Service Attacks](#contents.xhtml#re_h-6-7)
    
    *Denial of service (DoS)* is an attack that occurs when a hacker makes computer resources inaccessible to its users. There are a variety of ways to begin the attack when the aim is to overload the network. The two common methods of DoS attacks are flooding network services by using up resources and crashing network services. One way to execute a DoS attack is to develop a small virus whose only purpose is to launch a flood of messages against the target. Additionally, an attacker can compromise the availability of a system by creating an error or buffer overflow (e.g. ping of death). Any attack against the availability of a service is categorized as a denial-of-service attack.
    
    DoS uses only a single computing device to carry out the attack. [Figure 6.10](#c6.xhtml#f6.10) demonstrates a DoS attack.
    
    ![FIGURE 6.10 A DoS attack.](images/fig6.10.jpg)
    
    **FIGURE 6.10** A DoS attack.
    
    *Denial-of-service attacks* come in various forms and can be classified as *Application Layer Attacks* (measured in requests per second), *Protocol Attacks* (measured in packets per second), and *Volumetric or Volume-based Attacks* (measured in bits per second)*.*^([^(305)](#fn305))
    
    [Figure 6.11](#c6.xhtml#f6.11) explains the three types of denial-of-service attacks with examples for each category.
    
    ![FIGURE 6.11 Types of denial-of-service attacks.](images/fig6.11.jpg)
    
    **FIGURE 6.11** Types of denial-of-service attacks.
    
    Denial-of-service attacks do not need a specific program like malware to run but instead take advantage of the security vulnerabilities of the network’s communication applications.
    
    The goal of a DoS attack is not to infiltrate computing systems, servers, or networks to gain confidential information but to cut users off from a resource by overwhelming them with requests. Since every computer device has an operational limit, the cybercriminal sends numerous requests to the target server, overloading it with traffic it cannot handle. The computing system eventually makes the service unavailable to legitimate users. Following are some common DoS attacks:
    
    *   An *Internet Control Message Protocol (ICMP)* or *ping flood* attack. This type of attack happens when a hacker sends ICMP echo requests or pings with the purpose of flooding a computing system.^([^(306)](#fn306))
    *   A *SYN flood* happens when the attacker exploits weaknesses in the TCP connection sequence, by not supporting the three-way handshake. Every connection establishing using TCP requires a three-way handshake, and this is the foundation for every connection. In a normal connection the three-way handshake occurs between a client and server. First the client sends an SYN packet and the server replies with acknowledgment, such as SYN-ACK. The server sends back an acknowledgment ACK packet followed by the data. The handshake is completed (see [Figure 6.12](#c6.xhtml#f6.12)).  
          The attacker, on the other hand, sends a synchronized (SYN) packet to begin the handshake. The server responds with the acknowledgment (SYN-ACK), but the attacker does not reply with an acknowledgment ACK packet. As a result, the three-way handshake is not completed and leaves the connected port of the server inaccessible for further requests (see [Figure 6.13](#c6.xhtml#f6.13)). The attacker will continue sending more and more requests to prevent anyone else from connecting to the server or network. Defense against SYN flood includes a Software-Defined Networking (SDN) paradigm,^([^(307)](#fn307))
    *   A *Smurf attack* is a denial-of-service attack that exploits weaknesses of the Internet Protocol (IP) and ICMP by using a source code called “smurf.” A hacker uses this source code to broadcast numerous ICMP packets, by making requests with a spoofed IP address.  
          The hacker first creates a spoofed (fake) network packet that has its source address set to the real IP address of the server that he wants to target. Next, the hacker sends an ICMP echo request (ping) to an IP broadcast address of the router, asking a network device or a node to send a reply. Each device responds to the spoofed address with pinged reply packets, resulting in flooding of the targeted IP address and the setting up of an infinite loop since the target and the receiver are the same. Thus, the targeted network is flooded with a large volume of pings from the attacker.^([^(308)](#fn308))
    *   *Buffer overflow* occurs when a hacker modifies a computer’s memory or overflows the buffer’s limit, overwriting memory locations to control program execution and inserting malicious code into the memory of a program.^([^(309)](#fn309))
    *   The hacker’s goal is to insert malicious code in a memory location that the system will execute. The buffer is a *temporary storage area*, like RAM, in which data is held in a computing device. To mitigate a buffer overflow attack, an Address Space Layout Randomization (ASLR) has been used as a successful defense.^([^(310)](#fn310))
    *   The *Ping of Death*: This attack is like a *Smurf* attack. It occurs when a hacker manipulates an IP protocol by sending large packets with the maximum value allowed in the IP header to a target. When the targeted computing device tries to reassemble these large packets, the packets overload the network resources, causing the buffer to overflow, slowing the network, or crashing the operating system. This causes a denial of service for legitimate packets.^([^(311)](#fn311))
    
    ![FIGURE 6.12 The three-way handshake.](images/fig6.12.jpg)
    
    **FIGURE 6.12** The three-way handshake.
    
    ![FIGURE 6.13 The SYN flood attack. The three-way handshake is not completed.](images/fig6.13.jpg)
    
    **FIGURE 6.13** The SYN flood attack. The three-way handshake is not completed.
    
    *Distributed denial-of-service (DDoS)* attacks are more advanced. They occur when multiple computing systems coordinate a synchronized attack. A hacker exploits security vulnerability to take control of multiple computers and turns them into botnets or bots (zombie computers). The hacker then uses the bots to attack other computers or networks. The botnets can be made up of a single handful of bots or thousands of them, located around the world. These infected computers are managed through a command-and-control server. DDoS attacks provide an opportunity for hackers to gain access to numerous compromised computing devices. [Figure 6.14](#c6.xhtml#f6.14) demonstrates a typical DDoS attack.
    
    ![FIGURE 6.14 A DDoS attack.](images/fig6.14.jpg)
    
    **FIGURE 6.14** A DDoS attack.
    
    In addition to the above DoS attacks that can be utilized by a DDoS as well, the most common DDoS attacks are:
    
    *   The *User Datagram Protocol (UDP) Flood* is like the *ping flood***.** The attacker floods the targeted network with UDP packets. Since the UDP protocol is connectionless it does not require any link to be established between the source and destination before data transfer occurs. The goal of this kind of attack is to flood random ports on a remote host with data. Because there is no established connection, the target computer is unable to find an application-sending data and tells the sender that the destination is unreachable. This process consumes host resources, which can ultimately result in denial of services. To defend against UDP floods, firewalls that block malicious UDP packets along with the use of IP routing technology have been used to prevent an attacker from overwhelming a computing system.^([^(312)](#fn312))
    *   A *Slowloris attack* occurs when an attacker overwhelms a targeted server by sending numerous HTTP requests until the server cannot make any more connections. The attacker is using a legitimate HTTP request. As a result, the server is forced to keep existing connections open indefinitely. To keep the connections open and alive, the attacker periodically sends partial requests (HTTP headers) to the server saying, “Hey server I’m still here.” Therefore, these unfinished requests exhaust bandwidth and affect the server’s ability to respond to additional traffic requests.^([^(313)](#fn313))
    *   *Zero-Day DDoS attacks* or *0-day* is used as a blanket term to refer to all unknown new DDoS attacks that exploit vulnerabilities that have not yet been discovered. Since these types of attacks are not understood, they are exceptionally destructive since the targets have no defense. In other words, a new attack can be called a vector’s zero-days.^([^(314)](#fn314))
    
    ![FIGURE 6.15 A normal HTTP request.](images/fig6.15.jpg)
    
    **FIGURE 6.15** A normal HTTP request.
    
    ![FIGURE 6.16 A Slowloris attack with unfinished simultaneous HTTP request.](images/fig6.16.jpg)
    
    **FIGURE 6.16** A Slowloris attack with unfinished simultaneous HTTP request.
    
    #### [6.3.2.1 Notable DDoS Attacks](#contents.xhtml#re_h-6-8)
    
    *   The 2020 Amazon Web Services massive DDoS attack. The attack lasted 3 days and peaked at 2.3 terabytes per second.^([^(315)](#fn315))
    *   The 2018 DDoS attack on GitHub, a platform for hosting software development. GitHub got hit by1.35 Tb per second traffic at once.^([^(316)](#fn316))
    *   In 2016, the Mirai strain of malware infected the Internet of Things (IoT) running on Linux, turning the devices into remotely controlled bots that created DDoS attacks.^([^(317)](#fn317))
    *   In 2013, *spamhaus.org*, an anti-spam organization, suffered a DDoS attack with an estimated size of more than 300 Gb per second of attack traffic.^([^(318)](#fn318))
    
    #### [6.3.2.2 DoS Attacking Tools](#contents.xhtml#re_h-6-9)
    
    Some of the most common and free DoS attack tools are the following:
    
    *   *DoSHTTP*, an easy-to-use and powerful DoS tool that generates HTTP flooding
    *   *High Orbit Ion Cannon (HOIC)*, intended to attack more than one URL at the same time using HTTP (Hypertext Transfer Protocol)
    *   *HTTP Unbearable Load King (HULK)*, a DoS attack tool that generates a unique demand for every request to the Web server
    *   *Layer 7 DDoS Simulator (DDOSIM)*, a DoS attacking tool that mimics several zombie hosts with full TCP connections
    *   *Low Orbit Ion Cannon (LOIC)*, an open-source network stress testing and DoS attack application
    *   *R-U-Dead-Yet*, an HTTP POST DoS attack tool
    *   *Tor’s Hammer*, an attacking tool for slow-rate attacks using HTTP POST requests
    *   *XOIC*, a DoS attack application for any server with an IP address
    
    ### [6.3.3 Malware](#contents.xhtml#re_h-6-10)
    
    Malware is short for “malicious software” and consists of computer viruses, worms, Trojan horses, ransomware, spyware, and other types of destructive software or code. Malware impairs or infiltrates a computing device or system to execute specific damage, without the user’s knowledge. Java Scripts are commonly used for placing malware on a victim’s computing device.^([^(319)](#fn319))
    
    *   *Virus* is a type of malicious code or a program that replicates and spreads from one computer to another after initial execution. A computer virus requires a *host program* and *user action*. Typically, a virus is attached to a computer program, file, or document. For example, a malicious macro infection can be attached to a Word or PDF file. For this code to infect a computing device, the user must run the infected program, and then the executing code can pass the virus to the device.
    *   A *Trojan horse* is named after the famous wooden horse that tricked the Trojans and allowed the ancient Greeks to conquer the city of Troy. Trojan horses are scripts or computer programs camouflaged as legitimate software. Instead, they are delivery vehicles for a variety of threats. For example, when a user innocently downloads a utility, game, or movie from a website considered safe and runs it or opens an attachment containing the infected file, the following may occur:
    *   A backdoor may open, providing hackers with unauthorized remote access.
    *   An exploit occurs that takes advantage of a weakness of the software or hardware.
    *   Harmful software is installed, or files are deleted.  
          Some examples of Trojans are the *Zeus* or *Zbot Trojan* malware that hacked the U.S. Department of Transportation;^([^(320)](#fn320))
    *   A *ransomware* attack occurs when a hacker uses malicious software, usually malware or phishing spam, to extort victims by locking and encrypting their data until the victim pays a ransom in cryptocurrency. Even after payment the data may not be made available.  
          A ransomware report alert was issued by the CISA, the FBI, and the HHS (U.S. Department of Health and Human Services).^([^(321)](#fn321))
    *   Ransomware frequently indicates the end of a lengthy cyberattack chain or cyber kill chain. The attacker has usually spent many days or weeks laying the groundwork for ransomware in the victim’s network.  
          When using ransomware, the attacker first encrypts the victim’s files so they are unusable and then blackmails the victim to pay for the decryption key. When ransomware occurs in a corporation, the attackers threaten to reveal sensitive data to shareholders, the media, and competitors unless payment is made. Some of the signs a computing system may have been infected by ransomware attacks include: 
        
        *   Unusual malware warning reports
        *   Infrequent warning reports from hacking tools such as network scanners
        *   Unusual phishing attacks
        
          
        To defend against ransomware attacks, the following preventive measures should be considered: 
        *   Perform frequent updates and patches to the operating systems and applications
        *   Educate users about phishing attacks in circulation and use an anti-phishing testing system and spam filters
        *   Use a strong password and the system should require two-factor or multi-factor authentication
        *   Disable all remote services such as Remote Desktop Protocol (RDP)
        *   Backup data regularly and keep the backup copy *offline*, in a *cold backup*, where the database is offline, or *off-site*, and where the data is processed externally
        *   Disable the autoplay function and file sharing
        *   Monitor the network for suspicious network behavior
        *   Download only from trusted sites and think twice before clicking
        *   File a report with the FBI^([^(322)](#fn322))
    *   *Spyware* is a type of malicious software that invades a computing device to gather information. It does not self-replicate, evades detection, and runs undetected in the background of a computing device. More specifically, it records passwords, login credentials, and credit card information, forwarding the information and providing access to its spyware author.
    *   A *Worm* is an executable malicious program capable of replicating and distributing itself. In contrast to a virus, a worm does not require user activity to be activated. Usually, worms transmit malware like ransomware.
    
    ### [6.3.4 Phishing](#contents.xhtml#re_h-6-11)
    
    Phishing is a deceitful attempt to gather personal information such as usernames, passwords, and credit card information by using deceptive emails masked as legitimate. For example, a user may receive an email from a financial institution, asking for “missing” information. The email looks genuine, and all the user needs to do is click and answer the questions. But, when the user clicks on the link, the hacker installs malware which spreads to the user’s network within seconds. Then several different types of attacks may occur:
    
    *   *Deceptive Phishing* is one of the most widely used phishing scams. The goal is to mislead the user into revealing personal confidential information by imitating a legitimate source. The phishing email usually gives the impression of urgency—that the user needs to act fast. Following are two phishing email examples. 
        *   *I have tried to email this account many times but have received no response. If you receive this email,*  
            *Contact me as soon as possible for more details.*  
            *Sincerely,*  
            *Benjamin Ezeife*  
                Your   account   is   on   hold    
        *   *Hi Dear, we’re having some trouble with your current billing information. We’ll try again. But in the meantime, you may want to update your payment.*  
                UPDATE   ACCOUNT   NOW      
            *Need help? We are here if you need it. Visit the Help Center or contact us now. Your friends at Netflix*
    *   *Spear Phishing* is when an attacker targets specific individuals or groups within an organization or business. The attacker usually needs to gather information on the target to compile a convincing phishing email. Often intended to steal data, an attacker may also intend to install malware on a targeted individual’s computer. This technique targets individuals by email, social media, instant messaging (IM), and more. Frequently, a spear phishing technique contains an email and attachment. Social media sites are ideal hunting grounds for phishing attacks.
    *   *Vishing* is a voice phishing technique that uses verbal scams to deceive users into sharing confidential information. It flourishes when a cybercriminal has some information about the victim and uses this knowledge to create a sense of urgency to get the user to perform some type of action.
    *   *Smishing* is a mixture of texting and phishing that uses text messages instead of emails. The *smishing* technique lures users into sharing private information or clicking a malicious link and activating a code ([Figure 6.17](#c6.xhtml#f6.17)).
    *   *Pharming* is a combination of two words “phishing” and “farming.” The hacker directs an Internet user to a fake website instead of a legitimate one. The hacker may install malware on a user’s computer that changes the computer’s host file in order to direct traffic to a malicious website instead. Another way to “pharm” is when a hacker may “poison” the DNS server, causing numerous users to visit the fake website. This method exploits Internet browsing. Since a Domain Name System (DNS) server converts domain names like [www.google.com](http://www.google.com) into IP addresses, the *pharming* method targets the DNS server and replaces the IP address with a malicious one. When a user visits a website with the replaced IP address, a DNS cache forms, and the user will be sent to the malicious site on each visit. Both the DNS cache and the DNS server can be corrupted by the pharming technique. To protect against pharming, users should avoid suspicious websites and use only secure Web connections with Hypertext Transfer Protocol Secure (HTTPS) in the web address. In addition, they must utilize a password manager that stores the official website’s direct link, employ strong passwords, enable two-factor authentication on websites, use a VPN, remember to install updates on a regular basis, and use a trusted ISP.
    *   *Social engineering* happens when a cybercriminal tricks victims into revealing confidential information, such as usernames and passwords. For example, a cybercriminal could pose as an IT support technician and then trick the victim into providing login credentials.
    
    ![FIGURE 6.17 Example of smishing technique.](images/fig6.17.jpg)
    
    **FIGURE 6.17** Example of smishing technique.
    
    ### [6.3.5 Spoofing](#contents.xhtml#re_h-6-12)
    
    Spoofing refers to a deceptive method that tricks the user by hiding a malicious origin as a legitimate source. Examples of some of the common spoofing attacks include:
    
    *   *Address Resolution Protocol (ARP) spoofing* or *ARP poisoning* is a man-in-the-middle (MITM) attack. A hacker infiltrates a Local Area Network (LAN) by intercepting communication between network devices. The hacker changes the Media Access Control (MAC) address on the device and thereafter attacks the LAN by modifying the target with a falsified ARP request using a spoofing tool, like *Arpspoof* or *Driftnet*. The hacker can then view all the information passing between the devices and can collect all the traffic via port monitoring. To be able to achieve this type of spoofing attack, the hacker must have access to the network.
    *   *DNS spoofing or DNS cache poisoning* occurs when cybercriminals alter the DNS record of URLs and then redirect online traffic to a falsified website by changing its IP address. Then, they harvest personal information or infect the computer with malware. The DNS is the “phonebook” of the Internet and contains a list of URLs and their IP addresses. Once hacked, a tremendous volume of traffic can be misdirected.
    *   *Email spoofing* occurs when a cybercriminal creates and sends email messages from a forged sender’s email address and makes the recipient believe that the email was sent from a legitimate source. Email spoofing is the most widely used method to execute phishing attacks.^([^(323)](#fn323))
    *   *IP spoofing* occurs when hackers modify an IP packet by falsifying its source address. This attack is often used to set up DDoS attacks. The IP spoofing attack has become less common since ISPs have started performing egress filtering and packet filtering to detect and discard spoofed IP packets. Now, it is quite difficult to spoof an IP address outside of a LAN connection. Nevertheless, in cloud computing, hackers use IP spoofing techniques to launch DDoS attacks and masquerade the source’s identity.^([^(324)](#fn324))
    *   *MAC spoofing* changes the factory-assigned MAC, the physical address of a computing device’s network interface controller (NIC), also known as a network interface card. If a hacker can exploit backdoor vulnerabilities in the device’s drivers and modify the MAC address, he is seen as an authorized user. Then, the hacker presents himself at the default gateway and copies all the data without being detected. With these data, the hacker has detailed knowledge about the applications in use and destination host IP addresses. Additionally, the hacker can deny services on a wireless network, inject packets, send frames to all the wireless users using a broadcast address, and manipulate any packet field.^([^(325)](#fn325))
    *   *Website spoofing* occurs when a cybercriminal creates a fake replica of a real website like that of a bank or a university, and when a user logs into the fraudulent website, the hacker obtains the user’s credentials. Nevertheless, this type of spoofing first requires a phishing email that baits the user into clicking on a malicious link.
    
    ### [6.3.6 Structured Query Language (SQL) Injection or (SQLI)](#contents.xhtml#re_h-6-13)
    
    Structured Query Language, or SQL, is a programming language used with databases to query the database for specific information. An SQL query is basically a request for data. Examples include data retrieval, updates, and data removal. To query a database, a Web page is usually designed that accepts a specific type of identification, like username and password. When a user enters the information, it is checked for authentication. If correct, the user is granted entry. If not, access to the database is denied.
    
    SQL injection is a type of cyberattack where hackers “inject” malicious SQL code to manipulate the database and gain access to information illicitly. In other words, the hacker exploits software vulnerability by adding malicious SQL code to Web applications. Since most Web pages have no way of refusing authenticated requests, once authenticated, the hacker can enter a malicious code in the SQL code that changes the query. As a result, the hacker breaks into the database and steals, alters, or destroys data.
    
    ### [6.3.7 Wi-Fi Hacking](#contents.xhtml#re_h-6-14)
    
    A Wi-Fi connection offers a seamless wireless connection to the Internet. As a result, hackers target Wi-Fi connections and attempt to exploit their vulnerabilities, particularly targeting Wi-Fi in home networks. Once the hacker gains access to the network, he will either target the network itself or go after its connected devices. The hacker will usually focus on the link with the vulnerabilities that are easiest to exploit. Most wireless networks are vulnerable since there is no physical connection to deal with. Established wireless security protocols are frequently exploited to gain unauthorized access to Wi-Fi networks. For example, the security protocol Wired Equivalent Privacy (WEP), introduced in 1999, is the least secure, and the Wi-Fi Protected Access (WPA) protocol also has security vulnerabilities.^([^(326)](#fn326))
    
    Some of the most common Wi-Fi attacks are the following:
    
    *   *Cracking attacks* occur when a hacker uses different password-cracking techniques to break into a Wi-Fi network and gain access. Some of these include: 
        *   *Brute-force attacks*, meaning the hacker uses every possible combination of letters in a series of password-cracking attempts, struggling by trial and error to “force” its way until the correct password is found. For example, the simplest cipher is the Caesar cipher that can easily be cracked using a brute-force attack. Since the Caesar cipher has only 26 possible keys, by using brute force we can easily try all 26 possible key combinations.
        *   *Dictionary attacks* are like *brute-force attacks* but use passwords from a list containing words from the dictionary that many people like to use for their password. The hacker may try words like “password,” “attack,” or “profanity” or credentials stolen from a third-party resource with information about the target’s name, birthday month, etc.
        *   *Phishing*, as discussed earlier, is a dishonest attempt to gather personal information, including usernames and passwords.
        *   *Rainbow table* is a password-cracking technique that uses the rainbow hash table. This table is used in cryptography to encrypt and store important values like passwords using pre-computed hash values for every possible combination of characters. The passwords in almost all online services and computer systems are stored as hashes. We will discuss the hash value further in the chapter.
    *   *Jamming Wi-Fi signals* occurs when a hacker blocks a signal, using an illegal jamming device, for the purpose of creating noise and denying users access to a wireless point. According to the Federal Communications Commission (FCC), jamming critical communications like 911 and other emergency calls poses serious risks to public safety.  
          “It is unlawful to advertise, sell, distribute, import, or otherwise market jamming devices to consumers in the United States.”^([^(327)](#fn327))
    *   A *Wi-Fi de-authentication attack* occurs when a hacker targets a communication when it is traveling between the Wi-Fi Access Point and the device. This is actually a type of denial-of-service (DoS) attack. The goal is to send fake de-authentication packets to wireless users to capture their handshake and other data. These packets may spoof the user’s IP address.^([^(328)](#fn328))
    *   *Wi-Fi protected setup (WPS) attack*. The WPS standard uses a Personal Identification Number, which is an 8-digit pin, or a push button to connect to the router. This standard was created by Cisco and was designed to simplify connectivity between a wireless device and a router.^([^(329)](#fn329))
    *   WPA consists of a family of Wi-Fi security certifications or security technologies developed by the Wi-Fi Alliance to secure wireless computer networks.^([^(330)](#fn330))
    *   *Public Wi-Fi security issues*. Free Wi-Fi can be found in public places such as airports, coffee shops, malls, restaurants, and hotels. Most Wi-Fi hotspots are convenient but are often not secure. The hotspots are becoming more widespread because people want to use their devices 24/7, but the risks are considerable.
    
    Some of the risks of using these free hot spots include:
    
    *   *Man-in-the-Middle (MITM) attacks*, a type of cyber eavesdropping that occurs when data sent from point A to point B is intercepted by an attacker. The attacker then interjects himself into the communication process and accesses the victim’s computing system to monitor the online activity. Sometimes, the hacker can intercept login credentials and steal credit card information, alter the contents of the messages, or mimic the user. Every time we connect to a public Wi-Fi hotspot, we should assume that everything is being watched.
    *   *Unsecured Wi-Fi connections* can be used by hackers to distribute malware. If the user allows file sharing when using an unsecure Wi-Fi connection, the hacker can easily plant malware on the victim’s computer.
    *   In some cases, a hacker may create a rogue hotspot and name it with a well-known store or location, hope to trick users into signing on with their devices.
    
    How can users remain safe?
    
    Some preventive measures when using a public Wi-Fi connection are:
    
    *   Set up a VPN, which can provide protection against man-in-the-middle attacks.
    *   Use a strong password along with two-factor authentication (2FA), requiring an additional step to log into an account, like a passcode text to a mobile phone or a physical key inserted into a computer*.*
    *   Disable the auto-connect functionality for Wi-Fi.
    *   Visit the safest websites using Hypertext Transfer Protocol Secure (HTTPS).
    *   Beware of phishing scams when using a public Wi-Fi connection.
    
    [Figure 6.18](#c6.xhtml#f6.18) demonstrates the evolution of the most significant cyberattacks from the early 2000s until the present. From early 2000 to 2004 we’ve seen mainly worms; from 2005 to 2012 we’ve seen the rise of modern malware, and from 2013 to the present we’ve experienced ransomware and APT attacks associated with nation-state criminal organizations. These nation-state actors target government and commercial networks containing sensitive data, such as research for COVID-19 vaccines, and critical infrastructure.
    
    ![FIGURE 6.18 The evolution of the most important attacks.](images/fig6.18.jpg)
    
    **FIGURE 6.18** The evolution of the most important attacks.
    
    ## [6.4 Prevention Mechanisms](#contents.xhtml#re_h-6-15)
    
    ### [6.4.1 If You Connect It, Protect It](#contents.xhtml#re_h-6-16)
    
    A *firewall* is a piece of hardware, sometimes a standalone system or part of a router, or software application, or a combination of both, that screens incoming and outcoming traffic to or from a network, according to a defined set of rules.
    
    Along with firewalls, other systems such as *IDS* and *IPS* are part of the network security environment.
    
    *   The firewall is the first line of defense, like a fence between a trusted internal network, called the subnet, and the unsafe Internet. The firewall makes sure only specific types of traffic are allowed into and out of a network.
    *   The IDS system detects the attack, identifies it using a database of attack types, registers the attack, and sends an alert to an IT administrator if it is malicious.
    *   The IPS inspects traffic flowing in the network, looking for anything suspicious, and prevents or blocks a connection that is suspect, provides alerts, and cleans up malicious network traffic to keep it from getting to the rest of the network. Like the IDS, the IPS resides between the firewall and the rest of the network.
    
    > The best example of the difference between security gates in IDS and IPS is that an IDS security gate works like a patrol car within the borders of its neighborhood, monitoring activities and looking for abnormal situations. An IPS security gate operates like a security guard at the gate, allowing and denying access based on credentials and a predefined rule set, or policy. No matter how strong the security at the gate is, the patrols continue to operate in a system that provides its own checks.^([^(331)](#fn331))
    
    The separation between a computing device on an internal network and the Internet, or the outside world, is referred to as the *Demilitarized Zone (DMZ)* or *perimeter network*. This area sits between the internal network and external network. The Internet cannot establish connections directly to the internal network, but it can establish connections with the DMZ. If you think of network security as an onion, the DMZ is the peel, or the first layer of the onion.
    
    There are several ways to implement a DMZ in a network. One way is to use the *single firewall model* ([Figure 6.19](#c6.xhtml#f6.19)), which requires three network interfaces (devices) or a three-legged firewall. In this case the DMZ will be positioned inside of this firewall. The first network interface, considered Untrusted, is connected to the external public Internet connection. The second interface, considered trusted, is connected to the internal network or LAN. The third interface is connected directly to the DMZ. Normally, inside the DMZ you will find the email server, File Transfer Protocol (FTP) server, DNS server, Web server, domain controller, database servers, and HTTPS traffic.
    
    ![FIGURE 6.19 The single firewall model.](images/fig6.19.jpg)
    
    **FIGURE 6.19** The single firewall model.
    
    The *dual firewall model* utilizes two separate firewalls. One faces the Internet, called the *front-end firewall*, and the other faces the trusted internal network, or subnet, and is called the *back-end firewall*. The *front-end firewall* is configured to allow only traffic destined for the DMZ. The *back-end firewall* is responsible for regulating network traffic on the trusted internal network or traffic from the DMZ to the internal network.
    
    Cloud computing has changed the role of the DMZ by allowing secure access between the local or on-premises network and cloud-based networks through the use of a VPN service to connect the networks. Most companies use cloud service providers and deploy SaaS applications. DMZs are an important part of network security restricting remote access and guard against unauthorized access to internal servers. [Figure 6.20](#c6.xhtml#f6.20) demonstrates the dual firewall model.
    
    ![FIGURE 6.20 The dual firewall model.](images/fig6.20.jpg)
    
    **FIGURE 6.20** The dual firewall model.
    
    How does the firewall perform its job of monitoring services and blocking malicious or unwanted traffic? What does it block?
    
    A firewall does the following:
    
    *   On the device interface, the firewall filters source and destination ports, including OSI model, Layer 2 traffic.
    *   Regarding packet headers, the firewall filters traffic on the source and destination IP addresses, including OSI model, Layer 3 routed interface IPv4 and IPv6 interfaces. It provides different levels of protection based on parameters within the packet header information, including protocols such as TCP, UDP, and ICMP.
    *   The firewall rejects or accepts network traffic packet by packet, with or without notification, to the sender.
    *   The firewall records packet information.
    *   The firewall enforces security policies such as the setting of alarms, filtering rules and modifying packets, and detects, blocks, and rejects malicious requests when hackers scan public IP addresses for open ports.
    
    On most operating systems the server includes a built-in firewall along with its wireless routers. For example, a firewall is built into Mac OS. It is found under System Preferences, Security & Privacy, Firewall. A firewall is included on Linux and on the Windows OS, where it is called Windows Defender. Additional firewall solutions for personal use are available from security companies such as Bitdefender, Kaspersky, Norton, and McAfee, and from ISPs. On an enterprise-level, network firewalls must be able to secure more complex networks such as cloud environments, data center deployments, and remote sites. Some of the leading companies providing enterprise-level firewalls are Barracuda Networks, Check Point, Cisco systems, Juniper, Palo Alto Networks, and SonicWall. [Figure 6.21](#c6.xhtml#f6.21) displays a typical firewall setup on a network.
    
    ![FIGURE 6.21 A typical firewall setup on a network.](images/fig6.21.jpg)
    
    **FIGURE 6.21** A typical firewall setup on a network.
    
    ### [6.4.2 Types of Firewalls](#contents.xhtml#re_h-6-17)
    
    Firewalls use predetermined rules to analyze incoming traffic at entry points known as ports. Ports are communication endpoints that determine how external devices exchange information and communicate on a network. Some predetermine rules include how to handle trusted IP addresses, protocols, port numbers, and destination IP addresses. Additionally, there are other firewall types based on the method of operation and varying levels of security. Some of the most common firewall types include the following:
    
    *   *Packet-filtering firewalls* are the most basic type, inspecting inbound packets arriving from the network router. Only packets that match the firewall’s criteria are allowed in. Packet filtering operates at the network layer (OSI model, Layer 3), and the firewall inspects the port number, protocol, source, destination, and IP address. Packet firewalls can be either *stateless* or *stateful*. *Stateless* firewalls employ older firewall technology and analyze individual packets based on static information like source and destination. This method is not preferred by security professionals because it does not address vulnerabilities such as those leading to DDoS attacks. *Stateful* firewalls, on the other hand, are more secure and are a significant improvement, because they continuously monitor the network and the active connections. They can recognize the context of incoming traffic and data packets and can detect whether the packet is a part of an abnormal stream as in a DoS attack. Additionally, the *stateful* firewall, by default, permits connections or access from a trusted network to external servers and denies connections from outside to inside servers. However, overall, the packet-filtering firewall is not considered very secure. Its disadvantages are that it only offers basic protection, and it neither examines the packet nor compares it to the previous packet. Furthermore, it does not support user authentication of connections and is therefore vulnerable.
    *   *Proxy firewalls*, or *application-level firewalls*, or *gateway firewalls*, inspect the application and the server-side of the application. They monitor traffic at the application layer, using protocols like DNS, FTP, HTTP, and HTTPS, where traffic moves from one network to another and where the application connects. This type of firewall spots malicious traffic at layers 3, 4, 5, and 7 of the OSI model. A proxy firewall provides detailed log reports and analysis, filters application data, authenticates individuals, not devices, and prevents buffer overflow attempts, DoS attacks, unauthorized access, and spoofing attacks.
    *   A *Network Address Translation (NAT) firewall* allows network devices like routers to connect private IP networks to the Internet by replacing the private IP with a public IP address. The NAT acts as “receptionist or a dispatcher” between the public Internet and local network by remapping an IP address space into another one. The NAT firewall was developed to improve network security by filtering all incoming traffic, identifying threats and malicious actions, and blocking them. The firewall operates on a router to protect the local network’s devices as they connect with outside traffic on the Internet. First, the firewall allows Internet traffic to pass into the local network upon request by a device. Every incoming packet must have been requested by a device. Second, when a device is connected to the Internet, the router assigns it an external public IP address. When a device is connected to the router in the local network, the device is given a private IP address and the firewall does not allow the device to directly communicate with the Internet. Every device sends a request to a Web server by sending data packets. The packets include the sender and receiver’s IP addresses, port numbers, and what kind of information is requested. The NAT changes the data packet’s public IP to private IP to hide or masquerade the IP addresses of any devices from outside the local network behind a single global address.
    *   The *next-generation firewall (NGFW)* is one of the most popular firewalls. It provides advanced inspection threat beyond what is offered by traditional *stateful* firewall detection, featuring excellent application awareness and control, and the ability to block malware, prevent intrusion, recognize cloud-based threat intelligence, and prevent other security applications from entering a network.
    *   *Virtual firewalls* or *Cloud-based firewalls* or *Firewall-as-a-Service* refer to a virtual appliance located in a private cloud that monitors traffic on physical and virtual networks with cost-efficient solutions. This type of firewall provides the same protection in an off-network connection.
    *   A *Web application firewall* (WAF) is a type of firewall that blocks, filters, and protects data traveling in and out of Web services by analyzing each HTTP and HTTPS request at the application layer.
    
    ## [6.5 Identification, Authentication, and Authorization](#contents.xhtml#re_h-6-18)
    
    In computer security it is important to comprehend the difference among these three terms, Identification, Authentication, and Authorization
    
    **Identification** indicates the user’s or the thing’s identity, for example, a username.
    
    **Authentication**, from the Greek word “αὐθεντικός” authentikos, meaning “real” or “legitimate,” is the method that confirms the user’s identity and provides access to a computer system, for example, checking the accuracy of a password. Password authentication is the most common method of confirming a user’s identity, but passwords have many weaknesses and are susceptible to phishing attacks and password-cracking techniques. Because complicated passwords are hard to remember, users tend to choose convenience over security, hence the “12345” password. In addition to the password checking method, other common authentications include:
    
    *   Multi-factor authentication (MFA), sometimes referred to as two-factor authentication (2FA), which means requiring two or more ways to identify a user. For example, users can receive one-time passwords (OTP), requiring a code that is often received via email, text, or from a mobile app like the Google Authenticator. For additional security, a biometric authentication like a fingerprint, face recognition, IRIS scan, or voice recognition can be used. Another security measure is the use of a hardware-based security key based on the FIDO U2F standard.^([^(332)](#fn332))
    *   Users can authenticate with the following authentication factors: 
        *   Something the user knows, such as a password, a PIN, or answers to a set of questions.
        *   Something the user has, such as a smart card or a hardware-based security key.
        *   Something the user is or does such as biometric characteristics.
    *   Biometric authentication includes physiological, including fingerprints, face recognition, palm vein scan, iris scan, retinal pattern, and DNA, and behavioral, including voice pitch, typing patterns, and signature.
    *   Token-based authentication requires a unique generated encrypted code, or token, to verify the user’s identity. The token can be sent to a mobile app or a small hardware device. An example of a token is the RSA SecurID token offered in RSA SecurID two-factor authentication.
    
    *Authorization* happens when a user is provided with certain privileges or permissions to access computer systems or resources such as databases, files, services, computer programs, and applications. Authorization access is based on the level of assigned permissions given to the user, as defined by certain conditions.
    
    An *authentication protocol* is a set of rules that exchanges authentication data between two or more entities, allowing them to operate securely with minimal effort. A simple example of Point-to-Point Protocol (PPP) authentication protocol goes like this:
    
    > *Bob sends Alice his password in a packet. Alice checks Bob’s received password against the one saved in her database. If the password is correct, she sends a packet with an acknowledgment of successful authentication; if not, Bob is denied.*
    
    Common authentication protocols include PPP, Extensible Authentication Protocol (EAP), Kerberos, Challenge-handshake authentication protocol (CHAP), Password Authentication Protocol (PAP), Secure Shell protocol (SSH), and Shiva Password Authentication Protocol (SPAP).
    
    ## [6.6 Modern Encryption](#contents.xhtml#re_h-6-19)
    
    As we discussed earlier, cryptographic techniques have been used for thousands of years for secure communication. The need for people to exchange data easily and securely became more important with the introduction of computers. Encryption is one of the most effective ways to protect data by scrambling data into secret codes, called ciphers, as they travel across the Internet.
    
    Complex encryption algorithms have been developed that are hard to break. The summary below describes a general understanding of modern encryption methods that can protect *data at rest* *,* *data in transit* *,* and *data in use*. It can also keep data safe from lost and stolen computers. However, encryption can also be used by cybercriminals to encrypt data after a ransomware attack, making it almost impossible to retrieve and use. Encryption can be good or evil, protecting us or used as a weapon against us.
    
    ### [6.6.1 Symmetric Encryption or Secret Key Cryptography (SKC)](#contents.xhtml#re_h-6-20)
    
    Symmetric encryption method, also referred to as symmetric key cryptography, secret key, or shared secret, is a method that uses the same key to both encrypt and then decrypt a message. A simple example of symmetric encryption is the Caesar cipher, described earlier, which shifts each letter a fixed number of places. Another example occurred in 1586 when Blaise de Vigenère used an entire word as the shift key.^([^(333)](#fn333))
    
    Since the device uses only one key for both encryption and decryption, symmetric encryption may be vulnerable. Another drawback to symmetric encryption is that all parties must exchange the key (key sharing), to encrypt and decrypt data, and this is not always convenient. To solve this problem, another type of encryption, asymmetric encryption, creates a pair of keys, one public and one secret. The following is a simple example of symmetric encryption.
    
    *Bob and Alice need the same secret key for decryption and encryption. Bob and Alice must first exchange the secret key so that they can communicate privately. When Bob and Alice would like to store private information, they always store it in an encrypted form, using their secret key. If the server or cloud is compromised by someone else, no one can read their messages because the data is encrypted.*
    
    In other words, a cryptographic algorithm converts data into an unreadable form like *qJ4#j!UFO&Cps3#6@tc#Rb50*. Returning it to its original form by decrypting it requires a key or a password.
    
    A symmetric key cipher can be Block Cipher or Stream Cipher. Block Cipher is used to encrypt blocks of data, frequently 64 or 128 bits. For example, the cipher may encrypt a 64-bit block and will return the blocks of cipher text in the same size.^([^(334)](#fn334))
    
    ![FIGURE 6.22 The length of the AES encryption.](images/fig6.22.jpg)
    
    **FIGURE 6.22** The length of the AES encryption.
    
    *   Data Encryption Standard (DES) (uses 56-bit key length)
    *   Advance Encryption Standards (AES) (uses 128-bit, 192-bit, or 256-bit keys)
    *   Blowfish (key lengths vary from 32 to 448-bits length)
    *   RC4 (Rivest Cipher 4) (key can be any length up to 2048 bits)
    *   RC5 (Rivest Cipher 5) key size up to 2040 bits)
    *   RC6 (Rivest Cipher 6) (key sizes of 128, 192, and 256 bits up to 2040 bits)
    *   3DES (uses key length 56, 112, or 168 bits)
    *   IDEA (International Data Encryption Algorithm) (encrypts 64-bit blocks using 128-bit key) and ChaCha20 (Google has replaced RC4 with ChaCha20 stream cipher) algorithms. ^([^(335)](#fn335))
    *   Another stream cipher the Salsa20, which is related to ChaCha20, takes a 256-bit key. So far, researchers have not found any vulnerabilities in ChaCha20 algorithm.^([^(336)](#fn336))
    
    The key lengths indicate the number of bits in a solution used by a cryptographic algorithm. We can’t cover all the different types of encryption algorithms, but we will look at the most common.
    
    In 1970s, IBM developed its DES, which was the first major symmetric algorithm developed for computers in the United States.^([^(337)](#fn337))
    
    The AES is one of the most widely used symmetric encryption ciphers. It uses 128-bit, 192-bit, or 256-bit keys. [Figure 6.22](#c6.xhtml#f6.22) demonstrates the length of its encryption.
    
    If a computer tries 2^(40) (1,099,511,627,7760) solutions per day, it will take approximately about 848 sextillion years to brute-force the solution to a 128-bit key.
    
    The IDEA was developed in 1991. It works with 64-bit block of data and uses a 128-bit key.^([^(338)](#fn338))
    
    ![FIGURE 6.23 Symmetric encryption.](images/fig6.23.jpg)
    
    **FIGURE 6.23** Symmetric encryption.
    
    ### [6.6.2 Asymmetric Encryption or Public Key Cryptography or Asymmetric Cryptography](#contents.xhtml#re_h-6-21)
    
    We have used cipher systems or symmetric encryption for thousands of years. In 1976, a revolutionary paper by Whitfield Diffie and Martin Hellman titled “New Directions in Cryptography” proposed a major change.^([^(339)](#fn339))
    
    This type of encryption uses two mathematically different but connected cryptographic keys. Instead of a single key as in symmetric encryption, the public key encryption system uses a pair of keys. One key is public, and the other is a private or secret key. The public key may be accessed by anyone, and the private key only by the owner.
    
    The sender encrypts a message using the receiver’s public key; however, the receiver can only decrypt this encrypted message with his or her private key. One key will not reveal the other.
    
    The keys are linked mathematically so that anything encrypted with key “A” can only be decrypted with key “B.”
    
    *   A sender can use a recipient’s public key to encrypt the message; then, only the recipient can decrypt using his or her private key.
    *   Or, the message can be encrypted using both the sender’s private key and the recipient’s public key.
    *   If the sender encrypts a message with his private key, it can be decrypted by anyone that has the matching public key.
    *   A recipient with the sender’s public key can verify that it was the sender who created the message. This is called a digital signature. In other words, the sender and the recipient only need to exchange public keys, which can be done over open communication lines. Because the public key is available to everyone, other parties can use it to encrypt messages. As a result, every user must generate a pair of public and private keys. The mathematics behind the asymmetric encryption is extraordinarily complex and beyond the scope of this chapter.
    
    The public and private keys are associated with each other via a mathematical relationship. It is not feasible to calculate the private key from the public key because the mathematical relationship cannot work backward. In comparison with symmetric encryption, asymmetric encryption is much slower but offers better security because of the two different keys. [Figure 6.24](#c6.xhtml#f6.24) demonstrates the Asymmetric Encryption or Public Key Cryptography (PKC).
    
    ![FIGURE 6.24 The asymmetric encryption or public key cryptography (PKC).](images/fig6.24.jpg)
    
    **FIGURE 6.24** The asymmetric encryption or public key cryptography (PKC).
    
    *Bob and Alice have their own separate public keys, which they share with the world, including their friend Eve, and their own private keys which they keep to themselves. Bob encrypts a secret message (a love letter) with Alice’s public key. Even though Eve knows that Bob used Alice's public key, she cannot decrypt the message and read the secret love letter. Only Alice, using her private key, can decrypt the message. Eve would need both keys to decrypt the encrypted data. The private key is kept safe on the user’s computer. The public key, on the other hand, is exchanged on the Internet (* [*Figure 6.25*](#c6.xhtml#f6.25) *).*
    
    ![FIGURE 6.25 The asymmetric encryption Bob, Eve, and Alice.](images/fig6.25.jpg)
    
    **FIGURE 6.25** The asymmetric encryption Bob, Eve, and Alice.
    
    There are different public key encryption schemes that use widely differing mathematical algorithms from the ones used with Symmetric Cryptography. The following are mathematical algorithms used in asymmetric cryptography:
    
    *   The Rivest, Shamir, Adleman (RSA) Algorithm
    *   The Diffie Hellman Algorithm
    *   The ElGamal Cryptosystem
    *   The Elliptical Wave Theory Algorithm
    *   The Digital Signature Algorithm (DSA)
    *   The Elliptic-Curve cryptography (ECC)
    
    Table 6.4 compares symmetric and asymmetric encryption.
    
    **TABLE 6.4** Symmetric vs Asymmetric Encryption
    
      
    | Symmetric Encryption || Asymmetric Encryption |
    | --- | --- |
    | Algorithms exampleChaCha20
    
    *   RC4
    *   AES
    *   DES
    *   3DES
    
     || Algorithms examplesDSA
    
    *   RSA
    *   Diffie Hellman^([^(340)](#fn340))
    *   ECC
    *   El Gamal
    
     |
    | --- | --- |
    | Complexity
    
    *   Involves one key to encrypt and then decrypt the message.
    *   Uses a simpler encryption method compared to asymmetric encryption because only one key is utilized.
    *   Faster operation compared to asymmetric encryption.
    
     || ComplexitySlower operation but offers better security because two keys are used.
    
    *   Uses two different mathematically connected cryptographic keys, the public key, and the private or secret key.
    *   Sender and receiver do not share the secret key. The public key is known to all. Private key is known only to the receiver.
    *   Uses a complex mathematical process.
    
     |
    | Usage examplesPretty Good Privacy (PGP) uses asymmetric encryption data.
    
    *   Banking sector (credit card information).
    *   Data at rest (storage encryption).
    *   SSL/TLS and SSH protocols use both symmetric/asymmetric encryptions and hashing algorithms.
    
     || Usage examples
    
    *   Digital signatures (provides authentication of a source sending a message).
    *   Blockchain uses asymmetric encryption to authenticate the authorized transactions in cryptocurrency.
    *   SSL/TLS, SSH, PGP protocols.
    
     |
    
    As a result of the strengths and weaknesses of symmetric and asymmetric encryption, they have been employed in different ways. *Typically, symmetric encryption safeguards the message, and asymmetric encryption is used to send the symmetric key securely.*
    
    ### [6.6.3 Digital Certificates and Certificate Authority](#contents.xhtml#re_h-6-22)
    
    At this point we should mention that in cryptography, *public key certificates* are widely distributed by the *Certificate Authority (CA).* The CA consists of trusted third parties that validate the identities of an entity by issuing *digital certificates* like email addresses, and websites, to individual users. Think of these digital certificates as passports or electronic ID cards that establish the identity of an ID holder. Essentially, the public key certificate certifies ownership of the public key.
    
    To be able to generate a new digital certificate, the applicant or owner needs to generate a *Certificate Signing Request (CSR)*, along with a pair of private and public keys on the computing system where the certificate will be installed. This request provides information about the applicant. Then, the CA verifies the information, and issues, or “signs,” the certificate, that now contains a public key and the identity of the applicant. The matching private key is kept secret by the user. In other words, the CA confirms that the public key enclosed in the certificate belongs to the owner of the computing system in the certificate.
    
    In summary, digital certificate technology is based on public key cryptography, where every entity has two keys, public and private, that work only when they are used together and act as keys to a user’s encryption scheme. A digital certificate links the public and private key with its owner and allows a user to verify to whom a certificate has been issued. Also, the Certificate Authority makes sure that the owner is not claiming a false identity. The user keeps the private key in a secure location and does not share it, while the public key is sent to every user with whom the user wants to communicate. The most common international framework for digital certificates is defined by the X.509^([^(341)](#fn341))
    
    *   Issuer’s distinguished name
    *   Subject; contains owner’s information
    *   Public key; contains the actual public key
    *   Certificate; serial number of the certificate
    *   Digital signature of the issuer
    *   Validity period; when issued and date of expiration
    
    Some certificate providers are Comodo, IdenTrust, GeoTrus, Network Solutions, RapidSSL, Symantec, Thawte, DigiCert, GoDaddy, GlobalSign, and Trustwave.
    
    *The Certificate Authority can verify a bank’s website. Therefore, when we connect to the website, we can be sure that it is the real website and not a fraud. The digital certificate for the bank’s website is issued by the same Certificate Authority. A public key from the user’s browser encrypts data, such as deposits and withdrawals, and sends them to the bank’s website. The private key from the bank’s website decrypts the data sent by the browser.*
    
    ### [6.6.4 Hash Functions or Hashing Algorithms](#contents.xhtml#re_h-6-23)
    
    The hash algorithm converts data or a message of any length to a fixed length.^([^(342)](#fn342))
    
    The purpose of hash functions is data integrity. A hash algorithm (H) accepts a variable length of data (M) as input and produces a fixed-length output hash value (h). h = H(M). When we change any bit or bits of (M) this results in a change to the hash code.^([^(343)](#fn343))
    
    To be able to find the solution to a hash message, one must guess it by trying a brute-force attack, where the attacker inputs random passwords to see if they match, or by use of a rainbow table of matched hashes.^([^(344)](#fn344))
    
    *Bob creates a hash algorithm into an authentication tag. Alice runs the same computation and checks its result against the tag. If they match, the message is authenticated, if not the packet is discarded.*
    
    In a university, each student is assigned a unique number that can be used to retrieve information. That number may be kept safe by hashing it. Hashing is used for the authentication of passwords, digital signatures, which authenticate the identity of the sender and ensure message integrity, Message Authentication Codes (MAC), tags attached to confirm the authenticity of a message, and biometrics. For example, a typical password in a computer might be stored as “0d7006cd055e94cf614587e1d.”
    
    The hash function is easy to compute for any given message, but it is impossible to then calculate the original input. In contrast to cryptography, a hash algorithm is a one-way mechanism. It is not reversible.
    
    [Figure 6.26](#c6.xhtml#f6.26) demonstrates a hash function that takes a variable-length input and generates a fixed-length output. [Figure 6.27a](#c6.xhtml#f6.27) and [b](#c6.xhtml#f6.27) shows the difference between encryption and hashing algorithm.
    
    ![FIGURE 6.26 The hashing algorithm.](images/fig6.26.jpg)
    
    **FIGURE 6.26** The hashing algorithm.
    
    ![Figure 6.27a and b The difference between encryption and hashing algorithm.](images/fig6.27.jpg)
    
    *Figure 6.27a and b* The difference between encryption and hashing algorithm.
    
    #### [What Does “Salting” a Hashtag Mean?](#contents.xhtml#re_h-6-24)
    
    In hashing, the term “Salt” describes a unique use of random characters added to a one-way function. Salting uses the additional input to safeguard password hashes against dictionary attacks. A new salt is randomly generated for each password and increases the computational power of hashed passwords. In other words, the Salt and the password are concatenated and processed, making a password hash output unique and much less vulnerable to attack. For example, if Bob and Alice use the same password, such as *123456*, both would share the same hash. Consequently, the hacker can predict the password that maps to that hash value by using the dictionary and brute-force attacks. If the password is known, the hacker can access all the accounts that use the hash. With Salt added before the hashing process, the passwords are unique and can better safeguard passwords in storage.
    
    *   If we take the most common password, *123456*, by applying the Secure Hash Algorithm (SHA-256),^([^(345)](#fn345))
    *   b59936bb842a7bcccc54004091069467d78b85b7372e0f843c2b346c186daa14
    *   When Salt is added *A1ndQngn2m3* to the password *123456*, and we hash it then, the salted input becomes :*123456A1ndQngn2m3*. As a result, the hash algorithm will be something like this  
          70c1e0b744121ea8197422639cfee796282696f1b1070165186b1e446abada94
    
    The length of the hash depends on the hashing algorithm. Some common hashing algorithms include:
    
    *   *Message Digest Algorithm 5 (MD5)* was introduced in 1992 and creates 128-bit outputs. The MD5 algorithm has been shown to have weaknesses which make it easy to break. Although a hash function is designed to work only in one direction, MD5 is easy to reverse.^([^(346)](#fn346))
    *   *Secure Hash Algorithm (SHA)* family 
        *   SHA-1 was designed by the National Security Agency (NSA) in 1993 and creates 160-bit hash values.
        *   SHA-2 creates hash values with 224-bit, 256-bit, 384-bit, or 512-bits. It was designed by the NSA in 2001 and is recommended for secure hashing.^([^(347)](#fn347))
        *   SHA-3 is the latest version of SHA family and was developed by the NSA in 2012. It is designed to protect against brute-force attacks.^([^(348)](#fn348))
    
    ## [6.7 Conclusion](#contents.xhtml#re_h-6-25)
    
    As more smart devices connect to the Internet, cybercrime will continue to evolve transnationally. The threats posed by the different forms of cybercrime will increasingly dominate our lives. As we create barriers to their crimes, hackers will continue to become more sophisticated and will always develop new techniques and tools.
    
    Lack of information security, knowledge, and training lead to errors in the mishandling of sensitive data and hacking attacks. Electronic health records (EHRs) and sensitive payment information from credit cards continue to be used for fraud or sold on the Dark Web for profit. Our expectations of privacy continue to suffer.
    
    But then, for any type of cyberattack, there is, hopefully, a defense that we must learn and use.
    
    So far, we humans have been the weakest link in cybersecurity. With IoT and other devices proliferating, the future of cybersecurity relies on a combination of machine learning, artificial intelligence (AI), and savvy people to detect security threats and malicious activities and secure computing devices and networks. Ultimately, understanding and influencing human behavior will help create a better approach to cybersecurity.
    
    ## [6.8 Key Words](#contents.xhtml#re_h-6-26)
    
     
    | Access Control || Exploit |
    | --- | --- |
    | Active Attacks || Firewall |
    | Advanced Encryption Standards || FIPS 199 |
    | (AES) || Hacker |
    | Adware || Hash Functions |
    | Antivirus Software || Integrity |
    | Application Security || Information Security |
    | Authorization || Intrusion Detection System (IDS) |
    | Authentication || Intrusion Prevention System (IPS) |
    | Asymmetric Encryption || Malware |
    | Behavioral Analytics || Network Security |
    | Biometrics || Passive Attacks |
    | Caesar cipher || Phishing |
    | CIA Triad Model || Protocols |
    | Cloud Security || Security Audit |
    | Crime-as-a-Service (CaaS) || Security Threat |
    | Cryptography || Software-as-a-Service (SaaS) |
    | Confidentiality || Spam |
    | Cybersecurity || Spoofing |
    | Cyberwarfare || SQL Injection |
    | Data Breach || Steganography |
    | Demilitarized Zone (DMZ) || Symmetric Encryption |
    | Denial of service (DoS) || Virtual Private Network (VPN) |
    | Digital Certificates and Certificate || Vulnerability |
    | Authority (CA) || Wi-Fi Hacking |
    
    # [Chapter 7 Internet of Things (IoTs)](#contents.xhtml#re_c7)
    
    DOI: [10.4324/9780429318726-7](https://doi.org/10.4324/9780429318726-7)
    
    ## [Objectives](#contents.xhtml#re_h-7-1)
    
    After completing this chapter, the student will be able to:
    
    *   Understand the Internet of Things (IoTs) and the four different lead stages
    *   Understand real-world applications
    *   Understand industrial IoT and its relation to manufacturing
    *   Illustrate IoT architecture
    *   Explain different types of IoT protocols and standards
    *   Describe the IoT ecosystem—bandwidth, interoperability, power usage, and range
    *   Understand the importance of security in IoT devices
    
    *The Neuwirth family is returning from a weekend visiting relatives in a neighboring state. As they reach a point about an hour from home, they want to make the house ready for their arrival. Using their phone, they set the thermostat in the downstairs and bedrooms to 70 degrees; turn on the lights in the family room and kitchen; notify their pet sitter that they will be stopping by to pick up Roddy, their golden retriever; and turn on the oven, setting it to 350 degrees so they can pop in a prepared casserole as soon as they arrive.*
    
    *Sara Taffley, a second grader, has had Type 1 diabetes since the age of 3. She wears an insulin delivery pump to make sure that her glucose level does not go out of bounds. At 10 o’clock one morning, her mother receives an alert on her smartphone that Sara’s glucose has exceeded 200 mg/dl and she has just received 30 units of insulin to bring it down. Sara’s pediatrician has received the same alert, as has the nurse’s office in her school. Sara’s mother leaves work and heads to Sara’s school. By the time she arrives, Sara is resting comfortably in the nurse’s office, and her doctor has already checked in with the school. Sara’s glucose is now 99 mg/dl, a normal reading.*
    
    ## [7.1 The Internet of Things—An Introduction](#contents.xhtml#re_h-7-2)
    
    Like the *Industrial Revolution*, which began around 1760^([^(349)](#fn349))
    
    The phrase “Internet of Things” was coined by Kevin Ashton in 1999.^([^(350)](#fn350))
    
    A few years later, a book^([^(351)](#fn351))
    
    Modern computing began after World War II when the aftermath of the war and the space program of the 1960s brought considerable changes to computing technologies. Despite their massive costs, computers were expected to have long-term benefits for governments and big corporations. Their early adoption can be considered the *first stage* of modern computing. The *second stage* followed the introduction of microcomputers and the development of the personal computer (PC) in the early 1980s.
    
    Over time, the cost of computers fell and became affordable for consumers. As computers became smaller and lighter, the transition to laptops and ultimately to mobile devices began. This is considered the *third stage.* The *fourth stage* is the gradual evolution of IoTs and the steady trend toward Internet-connected devices. This stage includes not only the development of IoTs but the computerization of everything in our lives ([Figure 7.1](#c7.xhtml#f7.1)).
    
    ![FIGURE 7.1 The four stages of modern computing adoption.](images/fig7.1.jpg)
    
    **FIGURE 7.1** The four stages of modern computing adoption.
    
    The recent advances in wireless communications, 5G mobile broadband and the architectural integration of cloud computing, have led to a greater proliferation of IoT devices. Previous researchers have defined IoTs in several ways; there is no concise agreement on a definition.^([^(352)](#fn352))
    
    We will define the *Internet of Things* as *intelligent network-connected devices or systems, embedded in the physical environment, to improve the lives of people with minimal or no human intervention.*
    
    IoTs connect the physical world and the digital or virtual world to enhance the quality of life for humans with minimal or no human intervention.
    
    These devices or systems cleverly integrate networking, Information and Communications Technology (ICT), machine learning, edge, fog and cloud computing, and the delivery of products and services. IoTs provide efficiency, enhanced safety, and convenience for humans, completing tasks remotely and with little or no effort. The next generation of mobile networks, 5G, will enable the creation of a new wave of IoTs with higher bandwidth, greater reliability, and very high speed (up to 10 Gbps), which translates to low latency (the time needed for data to travel between two points). As IoTs need to communicate, 5G mobile broadband will offer an enormous amount of new bandwidth connection and will be able to support a vast diversity of devices and services. According to the tech analyst company IDC, the total number of connected IoT devices will be 41.6 billion by 2025 and will generate 79.4 zettabytes (ZB) of data.^([^(353)](#fn353))
    
    IoTs connect the physical with the digital world. Any tangible and visible physical object can be converted into an IoT device by connecting the device to the Internet and making it able to store, process, and transmit information. Additionally, the device must be able to communicate with the network independently or be controlled remotely.
    
    Examples of IoT devices include lightbulbs that can be controlled by a phone app, motion sensors, smart thermostats, smart locks, smart light switches, smoke alarms, doorbells, virtual assistants, and speakers like Amazon Echo and Google Home. Furthermore, an IoT can be installed in a child’s toy. Medical IoTs and implants monitor and control conditions such as diabetes, hearing loss, and heart rate. IoTs can be embedded in airplanes, collecting and transmitting data about the engine’s operation, airframes, and other aspects of operations.
    
    However, it is critically important to understand that while IoT devices have numerous benefits, they also pose security concerns, and since they are connected to the Internet they can be hacked and misused.
    
    This chapter outlines IoT applications, architecture, protocols, and standards, as well as bandwidth, interoperability, range, and security.
    
    ## [7.2 A Summary of IoT Applications](#contents.xhtml#re_h-7-3)
    
    The advantages of IoTs, along with the data they produce, have significantly impacted our lives. A physician thousands of miles away can monitor a patient’s vital organs, or a city can monitor its trash collection and assess the reliability of its roads and bridges. The possibilities are endless.
    
    [Figure 7.2](#c7.xhtml#f7.2) summarizes IoT applications in our lives.
    
    ![FIGURE 7.2 The range of IoT applications.](images/fig7.2.jpg)
    
    **FIGURE 7.2** The range of IoT applications.
    
    ### [7.2.1 Automotive Sector](#contents.xhtml#re_h-7-4)
    
    In the automotive industry, sensors collect enormous amounts of data that are processed, conceptualized into a visual format and streamed to the cloud. The data can be accessed from any device via the Internet. These sensory data are vital components of the automotive IoT environment. For example, an automotive fleet operator managing 25 or more vehicles for government or business can easily use these data to monitor parameters like driver behavior, vehicle maintenance, on-board diagnostics, fuel monitoring, and delivery delays. In addition, many vehicles we drive feature Internet connectivity. These connected vehicles can share their Internet access with a range of devices within and outside the vehicle.
    
    The Vehicular ad hoc Network (VANET) helps vehicles communicate with each other and their surrounding environment via wireless connectivity. Communication paths include vehicle-to-vehicle (V2V), vehicle-to-infrastructure (V2I), vehicle-to-sensor on-board (V2S), and vehicle-to-Internet (V2I).^([^(354)](#fn354))
    
    These features are evolving rapidly. Many new vehicles come with software platforms that offer mobile devices integration, in-car voice assistants, navigation systems, remote-control parking features, or sensors that allow parents to monitor and control teen drivers.
    
    Eventually, the increase of IoT devices in the automotive industry will lead to the autonomous vehicle, the car that drives itself. Since a range of sensors and algorithms will be needed to ensure the motorist’s safety, developing these applications is currently the greatest challenge to the auto industry. We are scratching only the surface of how we interact with our vehicles.
    
    ### [7.2.2 Energy Sector](#contents.xhtml#re_h-7-5)
    
    The energy sector is also undergoing a massive transformation as it becomes more energy efficient. IoT-enabled sensors and devices provide intelligence and detailed data analytics to energy companies and consumers. They track smart energy from generation to transmission and distribution. Smart devices monitor and manage equipment, measure vibration and temperature, monitor wear, and improve maintenance schedules. All these functions are performed remotely, without human intervention, and significantly improve worker safety, reduce costs, and enable virtual troubleshooting before equipment fails.
    
    With the installation of smart meters and smart thermostats consumers become more informed about their energy consumption. A consumer can remotely control a thermostat via a phone app. A smart meter provides accurate energy bills, and other smart devices measure the power consumption of each appliance and device.
    
    Furthermore, IoT devices can transform the energy grid into a smart grid by helping to distribute changes in electricity supply, demand, and distribution. Thanks to IoTs, the energy industry is smarter, more efficient, and more reliable.
    
    ### [7.2.3 Healthcare Sector](#contents.xhtml#re_h-7-6)
    
    In the healthcare sector, IoT devices have been revolutionizing the diagnosis, treatment, and management of patient care. These devices open up a world of possibilities for telemedicine and education paradigms for patients, providing data to help patients and healthcare professionals gain a deeper understanding of the human body. In addition, the devices have been shown to improve outcomes and reduce costs.^([^(355)](#fn355))
    
    Examples of current IoT healthcare devices include automated insulin delivery pumps^([^(356)](#fn356))
    
    In addition to remote patient monitoring devices, hospital medical equipment is becoming smarter. Examples include defibrillators, electrocardiograms (EKG or ECG), glucose monitoring, smart hospital beds that contain sensors and automatically adjust pressure and can provide patient monitoring, smart thermometers, ultrasound technology, nebulizers, and other monitoring equipment. One example is diabetic management system for children, where a sensor collects data from the child’s body (diet, insulin intake, physical activity) and then transmits the data to a Web-centric disease management hub for further instructions or advice from a medical professional.^([^(357)](#fn357))
    
    While these devices can make our lives better, they are not without challenges. Their enormous bandwidth consumption, along with concerns about data security of sensitive patient information, is concerning.
    
    Nevertheless, we will continue to witness these intelligent devices connecting to the Internet, analyzing data in real time, and extracting meaningful information that will improve healthcare delivery and disease control around the world.
    
    ### [7.2.4 Manufacturing Sector](#contents.xhtml#re_h-7-7)
    
    In the manufacturing sector, IoT devices add intelligence to industrial manufacturing and are poised to transform equipment, processing, and management. Industrial IoT devices, along with 5G mobile broadband, will improve productivity and product quality and will reduce the maintenance of manufacturing technologies through real-time data analytics. This developing trend toward automation, smart factories, real-time data analysis, and network connectivity is called the *Fourth Industrial Revolution or Industry 4.0.*^([^(358)](#fn358))
    
    Historically, near the end of the 18th century, the *First Industrial Revolution* was characterized by the steam engine, powered by coal. The *Second Industrial Revolution* began in the late 19th century with the discovery of oil, and early innovations in manufacturing, such as Henry Ford’s assembly line for the mass production of automobiles, and the work of Frederick Winslow Taylor, the father of scientific management.^([^(359)](#fn359))
    
    As we continue to move into the 21st century, interconnected IoT devices have been transforming the traditional manufacturing landscape with real-time connectivity, replacing traditional manufacturing processes. Examples include 3D printers, which can print just about anything, smart home devices, autonomous vehicles, logistics management, automation, and robotics machinery.
    
    *Industry 4.0* has transformed the world’s economic outlook and will continue to innovate and effect change. According to Rifkin (2014) the “zero marginal cost society,” along with real-time connectivity, will have a major impact on the current economic system as we know it, and IoT devices are spearheading this endeavor^([^(360)](#fn360))
    
    ![FIGURE 7.3 The four phases of the industrial revolution.](images/fig7.3.jpg)
    
    **FIGURE 7.3** The four phases of the industrial revolution.
    
    Thus, industrial IoT devices embedded within cloud-based machine learning capabilities will improve decision making and productivity and will enable the further development of smart products and smart services.
    
    ### [7.2.5 Retail Sector](#contents.xhtml#re_h-7-8)
    
    In the retail sector, IoT devices will help customers make more informed decisions and will help retailers redefine the customer experience. An example of a smart store is *Amazon Go*, in which shopping occurs without the need to stop and check out with a cashier. Other examples include the ability to search for products, compare prices, provide feedback, and receive coupons for a relevant product while customers are still in the store. The smart store uses these technologies to improve the customer experience by understanding their shopping behavior and offering a level of personalized marketing.
    
    Retailers, on the other hand, will be able to grow sales by obtaining and analyzing real-time customer data and identifying each customer’s gender, age, education level, eating behavior, habits, and taste preferences. These retailers will be able to identify loyal customers, predict their behavior, and deliver the products and services they desire. They will use heatmap analysis to track customers’ actual time spent in specific locations of the store. In addition, stores will monitor inventory levels in real time by using RFID and shelf-sensors to track inventory levels and monitor maintenance equipment before problems arise.^([^(361)](#fn361))
    
    IoT algorithms, not people, will calculate and influence every stage of the customer’s shopping experience in the smart store of the future.
    
    ### [7.2.6 Smart Structures (Buildings, Roads, and Bridges Sector)](#contents.xhtml#re_h-7-9)
    
    Any structure that communicates wirelessly, or one that is wired and sends and receives autonomous responses, is considered a smart structure. IoT devices that collect data in smart structures are proliferating.^([^(362)](#fn362))
    
    The primary motivation behind these smart building innovations is to reduce costs and improve sustainability and energy efficiency.
    
    In the field of structural design technology, including roads, bridges, and tunnels, IoT devices serve as an early detection system. Sensors monitor structural cracks, vibrations, temperature, and acceleration and, when applied to machine learning models, can predict defects or quality deviations, ultimately saving lives.
    
    ### [7.2.7 Smart Homes](#contents.xhtml#re_h-7-10)
    
    Smart home automation, or the smart home ecosystem, refers to all Internet-connected and integrated devices in our homes, such as appliances, smart light bulbs and switches, smart climate control systems, entertainment systems, and security systems like smart door locks, motion detectors, and security cameras. All these devices can be controlled through one home automation system, offered by tech companies such as Amazon, Apple, Google, and Logitech.
    
    Smart home IoT devices can be remotely monitored anytime and from anywhere using the home network and a voice or remote-control command or by an IoT-enabled application from any computing device. The development of easy-to-use apps along with the success of smartphones and tablets has helped to extend the use of IoT devices throughout the world. If smartphones and tablets are constantly connected to the Internet, then IoT devices may always be controlled and monitored. All current home electronic devices have built-in IoT-enabled technology, and so will those of the future, as this trend is still at the beginning of its journey within *Industry 4.0.*
    
    ### [7.2.8 Transportation Sector](#contents.xhtml#re_h-7-11)
    
    One of the basic functions of daily living in both urban and rural environments is transportation. We all try to get from point A to point B faster, safer, and cheaper. The transportation sector consists of many different types of businesses that transport people and goods. Examples include airlines, railroads, marine, freight, public transportation, and the transportation infrastructure. IoT devices provide solutions to their challenges through systems integration and centralized data gathering systems. Hence, this underlying technology creates a smart environment that allows people and business to use data in meaningful ways such as:
    
    *   Improved travel with better communication
    *   Enhanced safety, including sensors to maintain train speeds, the condition of aircraft parts, and roadway safety for trucks and cars
    *   Environmental effects to reduce energy use, congestion control, including traffic patterns, control of traffic lights, monitoring CO[2] emissions, location and speed control applications on buses and taxis, streetlights that automatically adjust to changing light conditions, pothole location, and communication of accurate weather conditions
    *   Vehicle-tracking systems, enabling monitoring with GPS tracking and analysis, provision of fleet information, including maintenance, advanced engine diagnostics, the ability to reduce fuel costs and promote better fuel efficiency, and information and security about a vehicle’s exact location.
    *   For maritime applications, IoT devices help by streamlining data operations across a fleet, tracking individual vessels, monitoring equipment and machinery in real time, forecasting maintenance needs, improving planning, reduction of fuel consumption, and safeguarding passengers and crews
    
    *Industry 4.0* is emerging in almost every conceivable industry or sector as each industry incorporates IoT devices to keep pace with competitors and future-proof the business. The underlying technology offers major advantages in automation, real-time data collection, and analysis but comes with security risks and challenges. As IoT devices continue to grow, security risks and privacy issues continue to loom.
    
    ## [7.3 IoT Components, Data Processing Architectures, and Protocols](#contents.xhtml#re_h-7-12)
    
    ### [7.3.1 Basic Components and Data Processing](#contents.xhtml#re_h-7-13)
    
    IoT devices consist of a collection of various technologies that work together seamlessly. Basic IoT hardware includes a *sensor***,** an *actuator***,** a *transceiver*, and a *power supply*.^([^(363)](#fn363))
    
    *   The sensor captures physical characteristics. It first processes them into electrical signals and then interprets them to provide readable information. An excellent example is the microphone. The microphone converts air vibrations (sound waves) into electrical energy (audio signals).^([^(364)](#fn364))
    *   An actuator converts electrical signals into action. An actuator turns an electric signal into a motion, for example turning a furnace on or off.  
        ![](images/inline7.2.jpg)
    *   A processor processes and stores data within an application, on a server or in the cloud.  
        ![](images/inline7.3.jpg)
    *   A wireless communication transceiver provides communication through wireless links, allowing people to monitor or configure IoT devices and enabling interaction between the owner and the device.  
        ![](images/inline7.4.jpg)
    *   A power supply may be either alternating current (AC) or direct current (DC). All IoTs require power. The power supply must be reliable, affordable, efficient, and space-saving.  
        ![](images/inline7.5.jpg)
    
    The sensors and actuators are the devices that interact with the physical world. A sensor wirelessly collects and transmits data to the control center after processing. In general, the control center decides, based on the software, to send a command to an actuator in response to the data collected. Data processing and storage can be performed on the edge of the network, in the cloud servers or on the device itself. Cloud computing provides centralization of computing resources, including storage, easy access to data and cost savings. Data processing capability is limited by the resources available, size, energy, power, and computational capability.^([^(365)](#fn365))
    
    ![FIGURE 7.4 An example of how an IoT system works.](images/fig7.4.jpg)
    
    **FIGURE 7.4** An example of how an IoT system works.
    
    ### [7.3.2 Big Data in IoT](#contents.xhtml#re_h-7-14)
    
    The increasing number of IoT devices and the vast amount of data being generated, along with the increasing use of processing power, together create delays and performance issues, especially when the centralized cloud computing model is used.^([^(366)](#fn366))
    
    Data processing happens on the *edge* of the network or nearer to the source of the data. The *edge computing paradigm* allows processing in real time at a location closer to the user, resulting in shorter response time and more efficient processing.^([^(367)](#fn367))
    
    > It works on both downstream data on behalf of cloud services and upstream data on behalf of IoT services. An edge device is any computing or networking resource residing between data sources and cloud-based datacenters.^([^(368)](#fn368))
    
    In addition to edge computing, a standard introduced by Cisco, called *fog computing*, defines how edge computing should work.^([^(369)](#fn369))
    
    In contrast, in edge computing, the data processing occurs on internal LAN devices like access points, switches, routers, and other devices near the sensors. “Within the network, IoT data are collected, processed, and stored at the **Fog/edge** node, also referred as the IoT gateway through which the fog interacts with the Cloud.”^([^(370)](#fn370))
    
    In retrospect, edge computing and the fog standard remove the workload from the network and bring it closer to the IoT devices, using machine learning, and a cloud computing backend.
    
    To understand latency better, a security camera system with artificial intelligence (AI)–driven analysis and resolution of 2288 × 1712 over the cloud will create latency when transferring massive amounts of video data back and forth between the cloud servers and the device. However, if the security camera system can perform most of the data processing itself and then send information to the cloud servers for archiving, it takes less time, reducing latency and lowering the cost of data transfer. In addition, outage reduction and sporadic connectivity work better with edge computing paradigms since this paradigm does not rely only on cloud servers for processing.
    
    Another example requires us to look at the autonomous vehicles of the future, which will contain numerous sensors and will therefore require massive bandwidth and continuous real-time processing. Edge computing paradigms can analyze data faster from numerous sensors in real time and will be able to make better immediate decisions. The future success of IoTs is about making them smarter, faster, and more secure. [Figure 7.5](#c7.xhtml#f7.5) delineates edge and fog processing paradigms in relation to cloud computing.
    
    ![FIGURE 7.5 The edge and fog processing paradigms.](images/fig7.5.jpg)
    
    **FIGURE 7.5** The edge and fog processing paradigms.
    
    ### [7.3.3 Architectures](#contents.xhtml#re_h-7-15)
    
    Although the IoT network comprises many interdependent components, its primary purpose is to provide a complete solution and work flawlessly. All components of an IoT system must be integrated and must follow rules that define the interface between hardware and software. Like any computing device, IoT architecture contains a set of rules or building blocks describing how each part functions, organizes, and integrates with the other parts. There is no standard IoT architecture model. Researchers, however, have proposed different architecture models. The most common are the *three-* and the *five-layer* architecture (see [Figure 7.7](#c7.xhtml#f7.7)).^([^(371)](#fn371))
    
    The basic three-layer architecture consists of the following:
    
    *   The *perception layer* is the physical layer, where the collection, transfer, and sending of data about the physical environment are accomplished, using sensors, networks-sensors and actuators, tags, near field communication (NFC), and radio-frequency identification.
    *   In the *network layer*, IoT devices connect to other smart devices and network devices such as gateways, wireless access points, servers, routers, switches, hubs, and repeaters. This layer is responsible for transmitting and processing data from the sensors, using gateway controls (physical devices or software that connects to cloud servers), Wi-Fi, Ethernet, cellular, and wide area networks ([Figure 7.6](#c7.xhtml#f7.6)).
    *   The *application layer* is where the data is delivered to the IoT user. We have seen this described in all the sectors we have discussed.
    
    ![FIGURE 7.6 The IoT connectivity.](images/fig7.6.jpg)
    
    **FIGURE 7.6** The IoT connectivity.
    
    The three-layer architecture has been expanded to contain three additional layers: the *transport layer*, the *processing layer*, and the *business layer* (see [Figure 7.7](#c7.xhtml#f7.7)).
    
    ![FIGURE 7.7 The three- and five-layer IoT architectures.](images/fig7.7.jpg)
    
    **FIGURE 7.7** The three- and five-layer IoT architectures.
    
    *   The *transport layer* resembles the network layer, which is responsible for transmitting the data from the sensors of the perception layer to the processing layer across the network.
    *   The *processing layer* or *middleware layer* is responsible for aggregating data, data storage (cloud computing and databases), processing data received from the transport layer,^([^(372)](#fn372))
    *   The *business layer* functions as the manager of the IoT system. This layer is responsible for operating the applications, user privacy, and managing how data is created, stored, and used.
    
    In addition to three- and five-layer architecture, a real-time business architecture solution is needed to authorize devices to improve the management of IoT devices. The *management component* of the IoT ecosystem is based on IoT device modeling, configuration, controlling data flow, and security controls. As IoT devices become more powerful, dealing with huge amounts of data along with *edge* and *fog paradigms*, Cisco IoT and Azure IoT suite architecture has developed a pre-integrated reference model called Cisco Edge. It works with the Microsoft Azure IoT Hub solution and includes software, hardware, security, and cloud services for enterprise IoTs.^([^(373)](#fn373))
    
    ### [7.3.4 Protocols and Standards](#contents.xhtml#re_h-7-16)
    
    A *protocol* is a procedure or set of rules used by systems to communicate with one another. Well-known examples include Transmission Control Protocol (TCP) and Hypertext Transfer Protocol Secure (HTTPS).
    
    A *standard*, in this context, is a set of rules followed by systems manufacturers that define how devices communicate in different settings. For example, Ethernet-based networks are defined by IEEE 802.3 standards, issued by the Institute of Electrical and Electronics Engineers (IEEE), and Bluetooth devices are defined by Bluetooth Low Energy 5.1, which is a wireless technology standard for exchanging data over short distances,
    
    *   *Protocols and standards define how IoT devices are managed and how data are transmitted via networks.*
    
    Standards and protocols are developed by different regulatory organizations and industrial bodies. Among the best known are the recommendations for IoT device manufacturers by the Internet Engineering Task Force (IETF), the Institute of Electrical and Electronics Engineers, the Organization for the Advancement of Structured Information Standards (OASIS), the International Telecommunication Union (ITU), and the NIST’s (National Institute of Standards and Technology) (NISTIR 8259).
    
    While it is not possible to present all protocols and standards, this section will present some of the most frequently used.
    
    To explain how the parts of the IoT interconnect, we will look at the Open Systems Interconnection Model (OSI) and its short version, called the Transmission Control Protocol/Internet Protocol (TCP/IP) model. TCP/IP has been around for a long time. It was developed in the 1970s and adopted as the protocol standard for the ARPANET (predecessor to the Internet) in 1983.
    
    TCP/IP contains four layers and constitutes a simplified version of the OSI model. Both models have been discussed in detail in [Chapter 5](#c5.xhtml#c5). The OSI and TCP/IP models are the two most widely used networking models in Internet communications, including for IoT devices.
    
    In general, networking protocols can be understood best when grouped into layers, where each layer describes a different function. See [Table 7.1](#c7.xhtml#t7.1).
    
     **TABLE 7.1** OSI and TCP/IP Models 
    
     
    | OSI Model  || TCP/IP Model |
    | --- | --- |
    | **(7) Application layer** || Application layer |
    | --- | --- |
    | **(6) Presentation layer** |
    | **(5) Session layer** |
    | **(4) Transport layer** || Transport layer |
    | **(3) Network layer** || Internet layer |
    | **(2) Data link layer** || Network access layer |
    | **(1) Physical layer** |
    
    Both the OSI and TCP/IP models will help us understand how the parts of the IoT ecosystem work together. In [Figure 7.1](#c7.xhtml#f7.1) we see that the TCP/IP model condenses the seven-layer OSI model into four layers. TCP/IP is actually a simpler version of OSI, and IoT networking protocols map more closely to TCP/IP levels than to OSI levels.^([^(374)](#fn374))
    
    1.  I. **Application layer** (**layers 5–7 in OSI)**: In this layer the user employs the interface given by the IoT to interact with the IoT device or other application. Protocols used in this layer: 
        *   **AMQP**: Advanced Message Queuing Protocol is used to pass messages between applications, called Message Exchange and Communication. AMQP is dependable over a distance or over poor networks. AMQP is similar to MQTT, Message Queuing Telemetry Transport, and follows the publish/subscribe (pub/sub) protocol of communication, which is standardized by OASIS.^([^(375)](#fn375))
        *   **CoAP**: Constrained Application Protocol is a machine-to-machine (M2M) protocol and, like Hypertext Transfer Protocol (HTTP), works between a client and a server with a minimum number of resources, making it perfect for IoT devices. Also, CoAP provides simplicity since it runs over the User Datagram Protocol (UDP) but offers less reliability.^([^(376)](#fn376))
        *   **DDS**: Data Distribution Service is a machine-to-machine (M2M) communication protocol that provides low-latency (faster) data connectivity and reliability. It also follows the pub/sub protocol for real-time and embedded systems. DDS was designed by the Object Management Group (OMG)^([^(377)](#fn377))
        *   **MQTT**: Message Queuing Telemetry Transport is standardized by OASIS^([^(378)](#fn378))
    2.  II. **Transport layer (layer 4 in OSI)**: This layer enables host-to-host data communication between layers. Examples of transport protocols are TCP and UDP. Both transport protocols work on top of the IP (Internet Protocol) to send bits of data known as packets from an IoT device to different routers. 
        *   **DTLS**: Datagram Transport Layer Security is a communications protocol that provides excellent security. This protocol has been used by CoAP (Constrained Application Protocol) and IPsec (Internet Protocol Security) for authentication, integrity, and encryption between two communication points across the IP network.^([^(379)](#fn379))
        *   **UDP**: User Datagram Protocol is a faster communication protocol, but it is less reliable. This protocol works similarly to TCP by dividing data into smaller units called datagrams or packets. Both protocols are built on top of the IP, and both send data across the Internet from one IP address to another. UDP, unlike TCP, does not guarantee delivery and has less overhead, offering no acknowledgment that packets have been received. This speeds the connection and reduces latency but reduces reliability. When using this protocol, a computing device sends packets of data to another device without guaranteeing delivery; this is a “send it and forget it” method. UDP is faster than TCP, because it eliminates functions like error checking and recovery services. It chooses speed over integrity, and data received may not exactly match the data sent. UDP is faster and TCP is more reliable. UDP is used for streaming games, live broadcasts, and video.
        *   **TCP** is a much more reliable host-to-host connection-based protocol. Its speed is slower than UDP, but TCP’s greater reliability guarantees fewer errors. The packets sent are traced so no data is lost or corrupted during transit. TCP, unlike UDP, requires the recipient and the sender to communicate and establish a connection, acknowledging that packets have been received. If packets are not acknowledged by the recipient, they are sent again. Consequently, this back-and-forth communication makes TCP slower than UDP.
    3.  III. **Internet layer (layer 3 in OSI)**: In this layer routers transport packets of data between the source host and the destination host. The IoT device communicates with the router using logical IP addressing to deliver packets of information between different networks. Following are some of the protocols the routers use: 
        *   **IPv4**: Internet Protocol uses a 32-bit address and can handle 4,294,967,296 (2^(32)) unique addresses. Because IPv4 is currently running out of addresses the protocol is switching to IPv6.
        *   **Ipv6**: Internet Protocol uses a 128-bit address, theoretically delivering 2^(128) unique addresses.
        *   **RPL**: Routing Protocol for Low-Power and Lossy Networks is for wireless networks and IoT devices with low power consumption. It is a simple and interoperable networking protocol and is resource-constrained.^([^(380)](#fn380))
        *   **6LoWPAN**: Low Power Wireless Personal Area Networks standard makes it possible for IoT devices to transmit IPv6 packets over wireless networks.^([^(381)](#fn381))
    4.  IV. **Network access layer (layers 1-2 in OSI)**: This layer oversees how an IoT device is physically connected to the network through Ethernet wired cables or wireless radio wave technology, using Wi-Fi standards. In addition to this connection, the IoT device is connected to a Media Access Control (MAC) and its protocols. The MAC address is a unique identification number allocated for every device and is used to connect the device to the network. This address is burnt into every device’s hardware by the manufacturer. Some of the protocols in this layer include the following: 
        *   *Bluetooth* is a low-energy, short-range wireless communication protocol that has become a central wireless technology for resource-constrained devices such as battery-operated sensors and actuators in the IoT ecosystem. Bluetooth was originally conceived as a wireless alternative by the Bluetooth Special Interest Group and uses the 2.4 GHz industrial, scientific, and medical (ISM) spectrum band (2,400 to 2,483.5 MHz). It has a range of 100 meters.^([^(382)](#fn382))
        *   *Cellular technology* enables mobile communication and addresses low-power IoT communication. For instance, the Low Power Wide Area Network (LPWAN) uses existing cellular technology for broad utilization of low-power IoT devices like wireless sensors and actuators. Cellular technology includes the fourth-generation cellular wireless (4G LTE) long-term evolution, and the emerging fifth-generation cellular wireless (5G). The LTE-advance (LTE-A) is designed specifically for IoT communication in cellular networks.^([^(383)](#fn383))
        *   *Dash7* is a wireless communication protocol for wireless sensors, actuators, and messaging applications. The protocol was developed by the DASH7 alliance and is based on ISO/IEC 18000-7.^([^(384)](#fn384))
        *   *Ethernet* IEEE 802.3 is an entire family of standards and protocols that defines wired connectivity in Local Area Networks (LAN) and includes standards for wiring, signaling, connectors, protocol rules, and more. More precisely, it defines the physical layer and the MAC address (hardware addresses) of the data link layer for wired Ethernet networks.^([^(385)](#fn385))
        *   *NFC* is a collection of short-range wireless communication protocols, using electromagnetic fields that enable communication with other devices and wireless transfer of data.^([^(386)](#fn386))
        *   *RFID* is a wireless technology that uses radio-frequency waves to read electronic tags from a distance.^([^(387)](#fn387))
        *   *Wi-Fi IEEE 802.11* is a wireless networking protocol, based on the IEEE wireless communication standard 802.11. The Wi-Fi alliance is responsible for certifying Wi-Fi products, including some of the newest standards such as 802.11ax Wi-Fi 6, 802.11ac Wi-Fi 5, and 802.11n Wi-Fi 4.^([^(388)](#fn388))
        *   *ZigBee* is a low-power, low-data-rate, close proximity (i.e., Personal Area Network) wireless communication protocol based on the IEEE 802.15 standard.^([^(389)](#fn389))
    
    [Figure 7.8](#c7.xhtml#f7.8) demonstrates the TCP/IP model and examples of IoT protocols and standards. [Figure 7.9](#c7.xhtml#f7.9) shows the data from an IoT flow between a sender and a receiver. Both figures provide a good reference point showing how IoTs establish network communication.
    
    ![FIGURE 7.8 TCP/IP model, protocols, and standards used by IoTs.](images/fig7.8.jpg)
    
    **FIGURE 7.8** TCP/IP model, protocols, and standards used by IoTs.
    
    ![FIGURE 7.9 Data flow between a sender and a receiver.](images/fig7.9.jpg)
    
    **FIGURE 7.9** Data flow between a sender and a receiver.
    
    ## [7.4 Network Consideration for IoT Devices](#contents.xhtml#re_h-7-17)
    
    In addition to protocols and standards, an IoT ecosystem requires *bandwidth*, *interoperability*, *power usage*, and *range* for successful deployment.
    
    1.  I. **Bandwidth**
    
    Bandwidth defines the maximum rate of data transmitted across a network path per unit of time. “In physical layer communications, the term bandwidth relates to the spectral width of electromagnetic signals or the propagation characteristics of communication systems.”^([^(390)](#fn390))
    
    1.  II. **Interoperability**
    
    Interoperability refers to the ability of IoT devices to work and interact well with other existing devices, such as equipment and systems utilizing standards and protocols. With the great number of different IoT ecosystems that can be connected, poor interoperability can cause serious issues. The adoption of standards and protocols by manufacturers has been a long-established approach to providing good interoperability.
    
    1.  III. **Power usage**
    
    Every IoT device requires power to process and transmit data. Additionally, most of these devices are small, contain limited battery power, and are “always connected” and transmitting data. “Data rate and payload of protocol affect directly on power consumption. High data rate and long data size of protocol lead to low power consumption.”^([^(391)](#fn391))
    
    1.  IV. **Range of networks**
    
    Different types of networks can transfer IoT data from one system to another. Following are the types of networks over which data is usually transmitted by IoT devices. See [Figure 7.9](#c7.xhtml#f7.9) for the different types of network connectivity.
    
    *   **PAN (Personal Area Network)** is a short-range network, found, for example, when using an app on a mobile device over a Bluetooth device (wrist fitness trackers, heart rate monitors, and pedometers).
    *   **LAN (Local Area Network)** is a medium-range network that spans a small area inside a single room, building or group of buildings, factory, or school. Examples include smart home products such as smart thermostats, surveillance equipment, and IoT devices integrated within an Electronic Health Record (EHR) to monitor a patient’s health.
    *   **MAN (Metropolitan Area Network)** is long-range network that provides communications over a larger area than a LAN. Examples include citywide networks, where IoT sensors can tell the sanitation department when the trash reaches a certain level, or on college campuses, where sensors can collect data about temperature, humidity, and air quality in the classrooms.
    *   **WAN (Wide Area Network)** is the widest communications network that can span a large geographic area and can connect multiple networks in a country or throughout the world. Multiple sensors within different countries can monitor water quality over the entire water supply. The best-known example of a WAN is the Internet, connecting multiple networks around the globe. [Figure 7.10](#c7.xhtml#f7.10) delineates the different types of networks transferring IoT data from one system to another.
    
    ![FIGURE 7.10 The different types of network connectivity for IoTs.](images/fig7.10.jpg)
    
    **FIGURE 7.10** The different types of network connectivity for IoTs.
    
    ## [7.5 Security](#contents.xhtml#re_h-7-18)
    
    Since the inception of IoT devices, their security has a great challenge to IoT ecosystems. Security vulnerabilities continue to hound manufacturers and users in every layer of IoT architecture. One of the most infamous IoT security attacks occurred in 2016. An IoT botnet malware called Mirai took advantage of unprotected IoT devices by using default usernames and passwords to log in and infect the IoT devices with malware. It then used the IoTs to issue massive distributed denial-of-service (DDoS) attacks.^([^(392)](#fn392))
    
    Because everything can be connected to the Internet in today’s digital world, privacy and security are critical. IoT devices provide hackers with new targets and more importantly can become part of a “botnet” army that delivers DDoS attacks. Examples of bad actions caused by the exploitation of IoT weaknesses include taking control of a smart home by unlocking the doors, hacking surveillance cameras, taking control of wearable devices, gathering personal data and tracking the users, hacking medical IoT devices and threatening a patient’s safety, or even shutting down a car while it is in motion.
    
    Besides the invasion of our privacy, IoT devices cause additional harm as they interact with our physical world. Cyberattacks caused by IoTs can compromise sensitive data through industrial espionage and eavesdropping, ruin equipment, and even endanger life and property.
    
    The wide variety of IoT applications using different IoT frameworks, the many manufacturers that fail to implement adequate security measures, along with the lack of computing and battery power, makes it very difficult to implement a universal security solution.^([^(393)](#fn393))
    
    *   **Device limitations**: IoT devices generally have short battery lifetimes and limitations in memory and processing power. As a result, they cannot handle all the requirements for advanced cryptography algorithms that would protect them from security threats.^([^(394)](#fn394))
    *   **Physical attacks, network attacks, software, and encryption attacks**: 
        *   Physical attack performed in the proximity of the IoT device (i.e., attacker is close enough to the device to analyze electrical signals such as electromagnetic waves emitted) and can gather sensitive information.^([^(395)](#fn395))
        *   Network attacks occur when an attacker accesses, manipulates, or intercepts an IoT network system remotely and causes damage (a DoS attack, malware, breach, man-in-the-middle attack (MITM), routing information or traffic attack, RFID Spoofing).^([^(396)](#fn396))
        *   Software attacks, including phishing attacks, malware, virus, worms, Trojan horse, spyware, and adware.^([^(397)](#fn397))
        *   Encryption attacks: These occur when an attacker tries to break the encryption scheme and obtain the private key to the device. These types of attacks include cryptanalysis attacks, side channel attacks, MITM attacks, sleep deprivation attacks, eavesdropping, and interference.^([^(398)](#fn398))
    *   **The lack of security by IoT device manufactures**: Manufacturers are profit driven and rush to produce the latest IoT device, often ignoring the lack of appropriate legislation and other security considerations such as insecure software or firmware. In addition, security software updates have often been largely ignored by device manufacturers. Finally, since IoT devices can be embedded in toys, manufacturers may have violated the Federal Trade Commission’s Children’s Online Privacy Protection Rule (COPPA).^([^(399)](#fn399))
    *   **The lack of security awareness by the user**: When it comes to IoT devices, users focus on their advantages and lack the technical knowledge to detect and be aware of security threats.^([^(400)](#fn400))
    
    Understanding the significance of these security risks, the National Institute of Standards and Technology (NIST) published a set of voluntary rules (NISTIR 8228—Considerations for Managing IoT Cybersecurity and Privacy Risks)^([^(401)](#fn401))
    
    *   Protect device security
    *   Protect data security
    *   Protect individuals’ privacy
    
    ## [7.6 Conclusion](#contents.xhtml#re_h-7-19)
    
    IoT devices signify the next giant leap of computing, using the power of the Internet. The combination of IoT and AI is immensely powerful. But IoTs, like other new technologies, need to mature and overcome their security hurdles. The necessity of safeguarding data security and individuals represents a great challenge. We are aware of this challenge and must always remain skeptical and suspicious about anything new that is connected to the Internet. Although firms like Microsoft have developed security applications like Azure Sphere to protect IoT devices, it will take time to earn the knowledge and trust of end users. Like each new technology, IoTs promise enormous benefits and have the potential to bring lasting changes to the world. Time will tell.
    
    ## [7.7 Key Words](#contents.xhtml#re_h-7-20)
    
     
    | Actuators || Interoperability |
    | --- | --- |
    | Automotive Sector || National Institute of Standards and Technology (NIST) |
    | Bandwidth ||  |
    | Cellular Technology || LAN (Local Area Network) |
    | Edge and Fog processing Paradigms || LTE-Advance |
    | Energy Sector || MAN (Metropolitan Area Network) |
    | Fifth-Generation Cellular Wireless (5G) || Manufacturing Sector |
    |  || Open Systems Interconnection Model (OSI) |
    | Fourth-Generation Cellular Wireless (4G LTE) || PAN (Personal Area Network) |
    | Healthcare Sector || Power Usage |
    | Industrial Revolution || Power Supply |
    | Industry 4.0 || Protocols and Standards |
    | IoT Applications  
    IoT Architectures || Radio-Frequency Identification (RFID) |
    | Internet of Things (IoT) || Range |
    | IoT Security || Retail Sector |
    | Sensor  
    Smart Home Automation || Transmission Control Protocol/Internet Protocol (TCP/IP) Model |
    | Smart Structures || WAN (Wide Area Network) |
    | Transceiver || Wireless Communication |
    | Transportation Sector || Transceiver |
    
    # [Chapter 8 Mobile Devices](#contents.xhtml#re_c8)
    
    ## [The Smartphone](#contents.xhtml#re_c8)
    
    DOI: [10.4324/9780429318726-8](https://doi.org/10.4324/9780429318726-8)
    
    ## [Objectives](#contents.xhtml#re_h-8-1)
    
    After completing this chapter, the student will be able to:
    
    *   Understand the historical significance of mobile phone technology.
    *   Recognize the device’s main components and architecture.
    *   Understand how cellular networks function.
    *   Understand the main components, operating systems, applications, and architecture of smartphones.
    *   Understand tracking of mobile devices.
    *   Recognize threats to mobile security.
    
    ## [8.1 Introduction](#contents.xhtml#re_h-8-3)
    
    Smartphones and tablets have transformed our lives. The ability to contact just about anyone sits in the palm of your hand; information that took time to find is now available in a single click. Thousands of free apps help us get the best from our technologies without needing great expertise. Typing is no longer needed – launch the speech recognition app when you send a message, and just speak into your phone – thumbs are no longer required!
    
    *The term mobile devices refers to all handheld computing devices like e-readers, cellphones, tablets etc., that are portable and support transmission of high-quality multimedia data, such as data, voice, and video via wireless transmission and without a physical network connection.*
    
    These devices are typically characterized by Wi-Fi and Cellular connectivity, a small rechargeable battery, usually Lithium-ion or Li-ion, a touchscreen interface, a virtual assistant such as Siri or Alexa, and the capacity to download applications or apps.
    
    This chapter will discuss mobile devices, and their functionality, basic components, architecture, cell network structure, and security.
    
    There was a time not long ago, when people who were not at home had to find a phone booth to make a simple phone call ([Figure 8.1](#c8.xhtml#f8.1)). The smartphone has forever changed our lives. The indispensable smartphone can do just about everything and has become the *Swiss army knife* for all modern society’s needs. It has replaced many things we used to depend on, like alarm clocks, answering machines, calculators, camcorders, cameras, flashlights, GPS devices, landlines, payphones, maps, music players, pagers, watches, address books, and more.
    
    ![FIGURE 8.1 The disappearance of phone booths. Courtesy of Shutterstock.](images/fig8.1.jpg)
    
    **FIGURE 8.1** The disappearance of phone booths. Courtesy of Shutterstock.
    
    ## [8.2 A Brief History and Significant Milestones of Mobile Phones](#contents.xhtml#re_h-8-4)
    
    The mobile radio has actually been around since the 1800s, when *Heinrich Hertz* proved the possibility of sending and receiving radio waves, based on *James Clerk Maxwell's* electromagnetic theory of light. Additionally, *Guglielmo Marconi* established a radio link between a land base and a boat in 1901.^([^(402)](#fn402))
    
    In the 1970s, mobile phones were used in vehicles and trains but were not handheld devices. In 1973, Motorola introduced the first *portable radio telephone* the Motorola DynaTAC, DYNamic Adaptive Total Area Coverage^([^(403)](#fn403))
    
    ![FIGURE 8.2 Motorola’s DynaTAC 8000X. Courtesy of Shutterstock.](images/fig8.2.jpg)
    
    **FIGURE 8.2** Motorola’s DynaTAC 8000X. Courtesy of Shutterstock.
    
    In the United States, the first analog automated cellular network was launched in 1983. Called the Advanced Mobile Phone System (AMPS), it was the first-generation mobile standard that decided how mobile devices communicate with the base station, using distinct frequencies for each conversation. This standard was developed by Bell Labs, an AT&T subsidiary.^([^(404)](#fn404))
    
    In the 1990s, the *second generation (2G)* of cellular communication emerged with two systems. First was the European Global System for Mobile communication (GSM) that was made mandatory by the European Union, and second was the U.S. developed Code Division Multiple Access (CDMA) standard. The 2G cellular network varied from 1G because it utilized digital transmission. Thus, generation 2G allowed the expansion of capacity and enabled widespread use of cellphones around the globe.
    
    As the demand for faster wireless data transfer grew, 2G was not capable of handling such growth. As a result, the *third generation (3G)* promised a more capable digital cellular network. The 3G communication network appeared in the early 2000s and offered access to multimedia and widespread use of the Internet on cell phones. 3G uses a network of phone towers to transfer signals to and from the cell phone, ensuring a stable and fast connection. Originally, 3G’s air data rate was measured between 384 kbit/s coverage and 2 Mbps indoor/microcell coverage. Afterward, the technology progressed into high-speed mobile broadband network coverage, called 3.5G, 3G+ and turbo 3G, delivering faster download speeds, and allowing for data transfer speeds up to 14 Mbps.^([^(405)](#fn405))
    
    In 2007, Apple introduced the iPhone. This was the first mobile phone using a multi-touch interface and signified the beginning of a new era in multimedia.
    
    The two global standards for cellular communication were the GSM and CDMA. Both are 2G communication standards. GSM had captured almost two-fifths of the international market.^([^(406)](#fn406))
    
    To send the call, the voice is first converted from analogue sound waves to data (digital) and transmitted by the cellular network. The subscriber identity module (SIM) card contains the user’s mobile information, including the personal number assigned to the mobile user. One of the advantages for GSM users is that the SIM card can be moved to another mobile phone, easily unlocking and transferring the device to another network. However, when using CDMA, the SIM card works only with mobile devices from the company with the same system.
    
    In contrast, CDMA developed in the United States has been categorized as a *code division* system, and is built on a spread-spectrum signaling, resulting in spreading the user’s signal within the time-frequency domain. This means that many users can send information instantaneously over a single channel or can share a band of frequencies.^([^(407)](#fn407))
    
    The arrival of the iPhone in 2007 put the mobile Internet into everyone’s hands ([Figure 8.3](#c8.xhtml#f8.3)). Its multimedia capabilities and mobile Internet access made 3G a “slow” network. As a result, the *fourth generation (4G)* cellular network, launched in 2010 by Telia Sonera in Finland, promised to support 100 Mbps peak rates and 1 Gbps in low mobility to mobile users.^([^(408)](#fn408))
    
    ![FIGURE 8.3 The first-generation iPhone. Courtesy of Shutterstock.](images/fig8.3.jpg)
    
    **FIGURE 8.3** The first-generation iPhone. Courtesy of Shutterstock.
    
    Different technologies and standards have been used with 4G such as Long-Term Evolution (LTE), Worldwide Interoperability for Microwave Access (WIMAX), Multiple Input Multiple Output (MIMO), Mobile Broadband Wireless Access (MBWA), and Orthogonal Frequency Division Multiplexing (OFDM). Of these, the most significant 4G standard for wireless data transmission is the LTE. The LTE standard was deployed in 2009 and was developed by the 3rd Generation Partnership Project, 3GPP. It established a significant path towards advanced international mobile telephony (IMT Advanced).^([^(409)](#fn409))
    
    4G continues to evolve, using LTE-Advanced and LTE-Advanced Pro, as we move towards *fifth generation (5G)* cellular network technology. 5G mobile networks promise faster speeds than 4G, increased bandwidth, better coverage, less latency, and are expected to offer speeds higher than 1Gbps by using CDMA.^([^(410)](#fn410))
    
    ![FIGURE 8.4 The Evolution of Wireless Mobile Systems.](images/fig8.4.jpg)
    
    **FIGURE 8.4** The Evolution of Wireless Mobile Systems.
    
    ## [8.3 Components, Operating Systems (OS), Applications and Architecture](#contents.xhtml#re_h-8-5)
    
    Like any computing device, a mobile phone consists of both hardware and software components. The components work together and form a complex mobile ecosystem. Most of us do not realize the complexity of the engineering processes that take place when we purchase a smartphone or a tablet. Without thinking, we make phone calls, send text messages, access the Internet, look at videos, play music, take multiple pictures, and play games. None of these activities would be possible without the evolution of computer hardware like Global Positioning Systems (GPS), graphic cards, System-on-Chip (SOC), sensors, wireless networking, and many more elements.
    
    *Mobile device are small portable computers that offer many of the same possibilities as standard computers but, provide a different user experience in a compact, portable environment.*
    
    ### [8.3.1 Main Components](#contents.xhtml#re_h-8-6)
    
    Due to widespread adoption of these devices and their potential security risks and vulnerabilities, it is important to recognize the basic layers of hardware and software they contain and understand how they communicate and function. Additionally, it is important to understand the miniaturization that has gone into the development of mobile technology, such as the camera technology and image sensors, along with the System-on-Chip (SOC), which is an integrated circuit fitted into a single chip. The following are some of the major hardware components of the mobile phone:
    
    *   **An antenna**: made of a metallic element, usually copper, that communicates with mobile points using radio frequencies. It is used by the mobile phone for data broadcast, sending its electrical signal via radio waves, in both directions. A typical mobile phone has more than one type of antenna. Examples include the cellular antenna, Wi-Fi and Bluetooth antenna, wireless charging antenna, GPS antenna, and the Near-Field Communication (NFC) antenna.
    *   **Battery**: the primary source that supplies power to a mobile phone, usually lithium-ion or (Li-ion). Unfortunately, battery technology, has not advanced as fast as other parts of mobile phone technology.
    *   **Camera**: has evolved and become more sophisticated, with astonishing results. The smartphone camera uses a CMOS image sensor and has a digital zoom feature, which is a software effect that crops the image and mimics the optical zoom. To provide a clear image, the camera must be able to use a great number of pixels; otherwise, the image will be less than satisfactory.
    *   **Microphone**: converts sound pressure waves from speech into electrical signals. The *Speaker* does the direct opposite, converting electrical signals into sound waves.
    *   **Mobile phone circuit board or printed circuit board (PCB)**: one of the main components and considered the “brain” of the mobile phone because it manages all parts of the mobile ecosystem. The PCB contains computer chips, flash memory, Read Only Memory (ROM), and more. These circuit boards are constructed of precious metals such as gold, silver, and palladium, which prompt people to recycle their old mobile phones.^([^(411)](#fn411))
    *   **Smartphone display**: the selling point for every mobile phone since the iPhone of 2007. The display has evolved from a miniature gray screen displaying numbers to a high-resolution touchscreen. The smartphone’s display comes in a variety of sizes and resolutions. Where there is a *touchscreen* it will work as both an input and output device. When the finger touches the display, grid wires under the screen produce electrical charges, and the device recognizes the area as a tap (input).  
        The two most common types of displays are:
    *   **Liquid crystal display (LCD) or IPS (in-plane switching) technology**: Its variations display panels shining a bright white backlight behind the screen that passes through polarizing filters and liquid crystals. Depending on the voltage the crystals control the light-like shutters and adjust the angle of polarized light. In front of the crystals layer there is a matrix of picture elements or pixels. Each pixel consists of three separate subpixels (Red, Green, and Blue) and produces the picture on the screen.^([^(412)](#fn412))
    *   **Light-emitting diode (LED)**, including Active-Matrix Organic Light-Emitting (AMOLED) and Organic Light Emitting Diode (OLED). Here, the pixels use light-emitting diodes and are self-luminous. That means the display is slimmer and lighter than LCD screens, featuring better energy efficiency, true black state, faster response time, flexible displays, and a wider color range than LCD.^([^(413)](#fn413))
    *   **Sensors**: devices that detect changes according to certain rules, convert these changes into electrical signals, and interpret them to provide readable information. Examples of mobile device sensors are: 
        *   **Accelerometer**: senses the orientation of the mobile device and its movements. Measures instantaneous acceleration or deceleration.
        *   **Gyroscope**: senses the displacement changes of the device.
        *   **Magnetic field sensor**: measures magnetic field for direction concerning mapping and navigation.
        *   **Light sensor**: adjust the screen brightness based on the light conditions or by the necessity to preserve battery life.
        *   **Proximity sensor**: senses the orientation of nearby objects.
    *   **System-on-chip (SOC)**: a processing system package or a building block that integrates several computer hardware elements into a single silicon chip such as Camera and Image signal processor, Central Processing Unit (CPU), Flash Storage, Graphics Processing Unit (GPU), Modems (4G LTE, 5G, Wi-Fi, and Bluetooth), mobile Random Access Memory (RAM), video encoder & decoder and more.^([^(414)](#fn414))
    
    ### [8.3.2 Operating Systems (OS) and Applications (apps)](#contents.xhtml#re_h-8-7)
    
    The mobile operating system is designed to run on mobile devices, including phones, tablets, 2-in-1 computers (tablet + laptop), and other devices. The OS is usually pre-installed and can be initiated by a power button. When the power button is pushed, firmware, the BIOS, begins the boot process. Self-testing begins, followed by debugging and/or modifying, along with additional device initialization codes before the OS loads into the device.
    
    The mobile OS is responsible for its operation, including administration, maintenance, and management of hardware and software resources, including the processor and memory. Also, the OS runs applications and manages cellular and wireless network connectivity, including Bluetooth and Wi-Fi, GPS navigation, and multimedia functions. The most popular mobile Operating Systems are Android OS and Apple’s iOS.
    
    *   Android OS is the most widely used mobile operating system in the world and is an open source OS. It is based on a modified version of the Linux kernel and was developed by Google.^([^(415)](#fn415))
    *   iPhone OS or iOS is the second most popular operating system and was developed by Apple. The iOS is based on a Unix-like operating system and contains several elements of the Mac OS X operating system. The iOS is only available for Apple devices.^([^(416)](#fn416))
    
    Running above the mobile OS is a series of applications or apps. Initially, the apps were intended to incentivize productivity, like calendar and e-mail apps. As the popularity of mobile devices increased, the demand for apps rapidly expanded into “there's an app for everything and everyone.” These application programs or apps are specialized software, that easily enable mobile users to perform a specific task*.* An *Application Program Interface (API)* is a feature of the OS that permits apps to request services and can interact with and acquire data from one another. Examples of APIs that enable shared content between third-party apps are the LinkedIn’s API, Facebook’s API, Twitter API, Google Maps, and YouTube. A good example is Facebook’s API. Facebook’s API allows users to sign in, enable social media users, and post content from the Facebook app. It also allows developers to access users’ profile identities and get data from Facebook platforms to manage ads and perform other tasks. Users often do not understand the extent of their data that Facebook can use. Facebook’s Graph API, a list of specific tags or data about a specific object, was used by Cambridge Analytica to collect Facebook users’ personal information, access their social lives, and use them as targets in political campaigns like the 2016 U.S. presidential election, and UK’s Brexit referendum campaign.
    
    On a positive note, APIs integrate application components into existing architecture and help businesses to collaborate with customers, harvesting data from old infrastructures with cloud-based apps and sharing the data with them.
    
    To be able to develop an application, developers are using one-stop solution software called *Software Development Kit (SDK)*, a collection of tools, APIs, guidelines, libraries, programs, and other utilities, that help developers create an application for a specific platform. Companies that offer SDK kits include Google, Facebook, and Microsoft.
    
    ### [8.3.3 Platform Architectures](#contents.xhtml#re_h-8-8)
    
    The two most widely deployed mobile operating systems are Google’s Android OS and Apple’s iOS. Android is the most deployed smartphone OS to the end-user.^([^(417)](#fn417))
    
    **Android** is an open-source OS developed by Google, Open Handset Alliance, and other companies. To be able to use the Android OS, mobile device manufacturers must meet the requirements specified by the Compatibility Definition Document (CDD) and get permission from Google. The Android OS consists of seven main layers.^([^(418)](#fn418))
    
    *   **Linux kernel layer**: at the bottom of the stack and considered the heart of the Android ecosystem, it is responsible for the smooth functioning of the system. This layer interfaces between the device hardware and the upper layer of the Android application software stack. It manages core system services like virtual memory, interfacing to peripheral hardware, networking, and a vast array of device drivers like Bluetooth, camera, display, memory, power management, memory management, and keypad.^([^(419)](#fn419))
    *   **Hardware abstraction layer (HAL)**: provides an interface for specific hardware components. It consists of multiple modules, for example, the camera or the Bluetooth module.^([^(420)](#fn420))
    *   **Android runtime (ART)**: is the software layer between the Android OS and the applications. It provides an execution environment for running apps written in Kotlin, the programming language for Java Virtual Machine, and other Java language apps. Additionally, ART’s predecessor Dalvik should work when running with ART. ART also manages memory and provides a set of core libraries for developers to use when developing apps in the Java language.^([^(421)](#fn421))
    *   **Native C/C++ libraries**: provide standard Java libraries for android apps that support general-purpose tasks like networking and databases. Examples include the SQLite library, which is used to store and share data, the Webkit library, used for browsing the web, the Secure Sockets Layer (SSL) library, which is used for secure communications, and the Audio manager library, which controls the audio subsystem. In addition to these standard libraries, Java-based libraries are designed for Android developers.^([^(422)](#fn422))
    *   **Java API framework**: provides the building blocks to create Android apps by simplifying the reuse of core, modular system components and services. It also manages the application resources and user interface, including:^([^(423)](#fn423)) 
        *   Activity Manager, which manages the lifecycle of an app and provides common navigation like the back button.
        *   Content, which enables apps to access/share/publish data from other apps. For example, contacts app.
        *   Notification Manager, which enables apps to display custom alerts.
        *   Resource Manager, which provides access to non-code resources like color strings, graphics, and the user interface layout.
        *   View System, which builds an app’s user interface, including buttons, lists, text boxes, and web browser.
    *   **System application layer**: provides core apps and third-party apps for email, SMS messaging, calendars, Internet browsing, contacts, and more. The third-party apps can become users’ default apps except for the system’s Settings app).^([^(424)](#fn424))
    *   **Hardware and power management**: components built into the system. Every component has a specific interface design for user interaction.
    
    [Figure 8.5](#c8.xhtml#f8.5) demonstrates the major components of the Android platform.
    
    ![FIGURE 8.5 The Android Platform.](images/fig8.5.jpg)
    
    **FIGURE 8.5** The Android Platform.
    
    **Apple’s iOS** is based on the NeXTSTEP operating system. NeXTSTEP was created by Steve Jobs’ company, NeXT, after he left Apple. When Jobs returned to Apple, NeXTSTEP became the basis of macOS and iOS. NeXTSTEP was based on Unix and was created using the Carnegie Mellon Mach kernel.^([^(425)](#fn425))
    
    ![FIGURE 8.6 The iOS Architecture.](images/fig8.6.jpg)
    
    **FIGURE 8.6** The iOS Architecture.
    
    *   **Core OS layer**: Contains lower-level features that most other technologies depend on, like the XNU kernel, which is part of the Darwin OS for use in macOS and iOS operating systems and is the foundation for the entire iOS. The XNU includes the Berkeley Software Distribution (BSD), which provides a portable OS interface and also comprises the file manager, local authentication, security services of the entire system, system utilities, and a Bluetooth framework.^([^(426)](#fn426))
    *   **Core service layer**: Contains important frameworks such as Address book framework, used with the database, Cloud Kit framework to move data between apps and the iCloud, Core telephony framework to handle telephone lines, Core location to provide location information to apps, and Core motion for accelerometer-based data, Social framework to interface social media accounts, and Health kit to control user’s health-related information.^([^(427)](#fn427))
    *   **Media service layer:** Contains graphics, audio and video, video frameworks such as core graphics framework for vector drawings, image 2D rendering, animation, game kit, AV kid, text, and image technology to manage the user interface.
    *   **Cocoa touch layer**: Contains the user interface of iOS, such as touch-based inputs, notifications, multitasking, cut, copy, paste, Game Kit Framework, MapKit framework, and more.^([^(428)](#fn428))
    *   **Hardware power management**: Contains components built into the system.
    
    ## [8.4 The Cellular Network](#contents.xhtml#re_h-8-9)
    
    The mobile phone converts audio and data into radio waves and transmits them from the phone's antenna to the nearest cell tower, cellular base station, or cellphone mast. These radio waves are used for cellular communications in a relatively higher frequency because they travel only short distances between the device and the cell towers^([^(429)](#fn429))
    
    ![FIGURE 8.7 A Cell Tower. Courtesy of Shutterstock.](images/fig8.7.jpg)
    
    **FIGURE 8.7** A Cell Tower. Courtesy of Shutterstock.
    
    Mobile devices rely on cellular or mobile networks. Cellular technology is based on dividing a geographical area into hexagonal cells. The hexagon is preferred because it covers an entire area without overlapping, and the shape reasonably approximates the circular radiation pattern of an omni-directional cell tower antenna.^([^(430)](#fn430))
    
    ![FIGURE 8.8 The Hexagonal Cellular Network.](images/fig8.8.jpg)
    
    **FIGURE 8.8** The Hexagonal Cellular Network.
    
    Cell towers have different traffic densities depending on the number of mobile devices served. For example, during the weekends, cell towers have significantly higher traffic density where people congregate around museums, amusement parks, and shopping centers. Higher traffic occurs near the airports and along highways, compared to rural areas which typically have lower traffic density. Comprehending the traffic density patterns of cellular networks assists with the planning, network capacity, and performance that affect users’ satisfaction.^([^(431)](#fn431))
    
    In remote areas, *microwave links* are often used because fiber-optic cables may be impractical or expensive to install. Microwave links are used for point-to-point communication since they have small wavelengths, are cost-effective, easily deployable, and have limited bandwidth compared to fiber optics.^([^(432)](#fn432))
    
    It is important to point out that with the arrival of 5G cellular systems, traditional cells will be replaced by *Small Cells* that require low power and can be positioned approximately every 250 meters throughout cities. This method will prevent signals from being dropped and provide more effective use of the spectrum^([^(433)](#fn433))
    
    ![FIGURE 8.9 Multiple Cellular Antennas (3G, 4G, and 5G). Courtesy of Shutterstock.](images/fig8.9.jpg)
    
    **FIGURE 8.9** Multiple Cellular Antennas (3G, 4G, and 5G). Courtesy of Shutterstock.
    
    With the exponential growth in demand for *high bandwidth* applications, along with new and old cellular systems being used, more antennas are needed to support more frequencies. The new cellular systems will require greater infrastructure. In the past, cell towers housed 3–4 antennas per tower, now we see dozens of antennas on each tower. With 5G networking, a cell tower can support approximately a hundred ports, so that many more antennas can fit on a single array.^([^(434)](#fn434))
    
    *The goal of a cellular network is to communicate seamlessly from one mobile device to another through linked cell towers.* Mobile phones have unique key identifications to identify the phone's owner and cellular service provider. Following are the most common key identifiers.
    
    *   **Electronic serial number (ESN):** is a unique 32-bit binary number embedded by the manufacturer on a mobile phone. The ESN cannot be easily changed by the user; it requires special facilities for alteration.^([^(435)](#fn435))
    *   **Mobile identification number (MIN):** is a 34-bit binary number assigned by the wireless provider within a wireless carrier's network. The binary number consists of MIN1 (24 bits) and MIN2 (10 bits), simply known as MIN. The CDMA standard uses the International Mobile Station Identity (IMSI). The IMSI is usually stored on a Subscriber Identity Module (SIM). In addition, the IMSI includes the Mobile Network Code (MNC) and the Mobile Subscription Identification Number (MSIN).^([^(436)](#fn436))
    *   **Mobile directory number (MDN):** is the 10-digit cell phone number that we all use. When a number is moved from one wireless service provider to another, the MDN is transferred to a new service provider and another MIN is assigned to identify the new mobile phone on the new carrier. Users can request keeping their MDN, and it is often possible to do so.
    *   **Mobile equipment identifier (MEID):** is a globally unique number identifying a mobile device in the CDMA. Similarly, the **Mobile Equipment Identifier (IMEI)** in GSM phones with hexadecimal digits is embedded in the device not in the SIM cards.^([^(437)](#fn437))
    
    ### [8.4.1 What Happens When a Mobile Phone Is Turned On?](#contents.xhtml#re_h-8-10)
    
    When we turn on the mobile phone, it listens for a signal and searches for the nearest cell tower approximately every seven seconds.^([^(438)](#fn438))
    
    As stated earlier, Radiofrequency (RF) is a type of electromagnetic radiation that has been used to transmit signals containing information in the form of radio waves. The mobile phone uses its antenna to transmit electromagnetic waves, also referred to as Radiofrequency signals, to the nearest cell tower. The cell tower converts the RF signal into light pulses through the Base Transceiver System (BTS) and the Base Station Controller (BSC) and then transmits it over a fiber optic cable into the destination cell tower via the Mobile Telephone Switching Office (MTSO).^([^(439)](#fn439))
    
    The Mobile Telephone Switching Office (MTSO), also known as the Mobile Switching Center (MSC),^([^(440)](#fn440))
    
    ![FIGURE 8.10 The Cellular Network.](images/fig8.10.jpg)
    
    **FIGURE 8.10** The Cellular Network.
    
    As was stated earlier, the SIM card is an important component of any mobile phone. This portable memory chip holds subscriber’s information that can be read by the mobile device, as well as cellular network information used for authentication and user identification. The most important pieces of information contained in a SIM card are:
    
    *   The Integrated Circuit Card ID (ICCID), which consists of 19–20 digits and is a global unique serial number that identifies the SIM card itself and is usually printed on the card,
    *   The International Mobile Subscriber Identity *(*IMSI*)*, which identifies the subscriber’s cellular network,
    *   The authentication key (Ki), a 128-bit secret key for authentication assigned by the cellular provider,
    *   The Local Area Identity (LAI), a unique number that identifies a mobile network,
    *   Short Message Service Center (SMSC), that manages SMS operations like storing, forwarding, routing, converting, and delivering text messages,
    *   The SPN Service Provider Name.^([^(441)](#fn441))
    
    ### [8.4.2 The Cell Tower or Cellular Base Station](#contents.xhtml#re_h-8-11)
    
    It is important to note the significance of the cell tower, or cellular base station. The transmission of RF signals over fiber optic cables is a technology using intense modulation of a light source with the RF signal.^([^(442)](#fn442))
    
    The mobile phone communicates by constantly sending and receiving radio signals to and from an antenna located in the nearest cell tower. When the signal from the mobile phone goes to the cell tower it is called an *uplink*, while the signal coming from a cell tower is called a *downlink*. Each cell tower consists of the following components:
    
    *   **The base transceiver system (BTS)**: Consists of radio equipment (transmitter and receiver = transceiver), that handles transmission and reception of the signals. The BTS sends and receives signals by providing radio coverage for a cell or a sector.^([^(443)](#fn443))
    *   **The base station controller (BSC**): is a network component that manages and controls several cell towers or base stations from cell-to-cell. In addition, it provides the interface from cell towers to the Mobile Switching Center (MSC) via microwave or fiber optic links.^([^(444)](#fn444))
    *   **Backup batteries** provide an uninterrupted power supply in the event of an outage.
    *   **A generator** provides standby power.
    
    ### [8.4.3 Mobile Device Tracking Location: Cell Towers, GPS, and Indoor Localization](#contents.xhtml#re_h-8-12)
    
    There are numerous ways to trace a mobile phone's location, including applications like Android’s *Find My Device,* which is built into the smartphone through Google Play or third-party apps like *Prey Anti-Theft*. This app permits the collection of data including pictures from the camera using GPS coordinates and the Media Access Control (MAC) address.
    
    In addition to the Android mobile phone, this app is available to other devices such as laptops, tablets, iOS, Chromebooks, Windows, and Linux. Apple’s *Find My iPhone* app comes pre-installed on every iOS device that can use a map to locate the device.![](images/inline8.6.jpg)
    
    Besides these apps, other methods such as Cell Towers, GPS, and Wi-Fi-based localizations are available if the device is neither turned off nor switched to airplane mode.
    
    First, Cell Tower Triangulation uses multiple cell towers to locate the device. When the mobile device’s signal is picked up by three or more cell towers, an overlap is enabled. The cell towers estimate the location of the cell phone based on its distance from the three towers, using angles of radio signals and/or time to find the distance.^([^(445)](#fn445))
    
    *   **Angle of arrival (AOA)** estimates the mobile device’s location by measuring the arrival angles of radio signals between the device and the cell towers, using basic trigonometry. A minimum of two angles are required. This technique uses the device location at the intersection of lines shaped by the arrival angles of the radio signals ([Figure 8.11](#c8.xhtml#f8.11)). This is known as triangulation^([^(446)](#fn446))
    *   **Time of arrival (ToA)** uses an estimation of the distance or distances of the travel time of a signal between a mobile device and several cell towers to determine the position coordinates of the device. This technique uses the transmission time between the device and cell tower directly to find the distance of the device from the tower.^([^(447)](#fn447))
    *   **Time difference of arrival (TDoA)** Like ToA, this method uses multiple cell towers to locate the mobile device. The TDoA measures the amount of time it takes for the radio signal from cell towers to reach and return to the tower from the cell phone ([Figure 8.13](#c8.xhtml#f8.13)). The measurement is defined as a hyperbola, instead of a circle and measures pairs of transmission paths between the device and the cell towers.^([^(448)](#fn448))
    
    ![FIGURE 8.11 Measuring the angles Φ determine the location of a mobile device.](images/fig8.11.jpg)
    
    **FIGURE 8.11** Measuring the angles Φ determine the location of a mobile device.
    
    ![FIGURE 8.12 Mobile Cell Towers Triangulation. Courtesy of Shutterstock.](images/fig8.12.jpg)
    
    **FIGURE 8.12** Mobile Cell Towers Triangulation. Courtesy of Shutterstock.
    
    ![FIGURE 8.13 The time difference of arrival (TDoA) measurement.](images/fig8.13.jpg)
    
    **FIGURE 8.13** The time difference of arrival (TDoA) measurement.
    
    The second method uses the *Global Positioning System (GPS)*, a satellite-based navigation system consisting of 24 satellites orbiting the earth^([^(449)](#fn449))
    
    ![FIGURE 8.14 A GPS satellite. Courtesy of Shutterstock.](images/fig8.14.jpg)
    
    **FIGURE 8.14** A GPS satellite. Courtesy of Shutterstock.
    
    In addition to the above methods, indoor techniques may be used to locate devices in an environment when other methods like GPS lack precision. This is called indoor localization and some of the techniques that can be used along with AOA, ToA and TDoA are
    
    *   **Bluetooth** and its latest version called Bluetooth Low Energy (BLE), which enables devices like iBeacon to provide proximity detection and indoor localization.^([^(450)](#fn450))
    *   **Received signal strength indicator (RSSI)** that can be used to estimate the distance between transmission and reception.^([^(451)](#fn451))
    *   **Wi-Fi-based localization** finds the position of the Wi-Fi enabled device based on the Wi-Fi hotspots and other wireless access points.^([^(452)](#fn452))
    
    ## [8.5 Security](#contents.xhtml#re_h-8-13)
    
    Because mobile phones have so changed the fabric of our life it is frightening to think how much these devices know about us. For cybercriminals, mobile phones offer a gateway to everything they might want to know about a person, along with paths into their businesses and other organizations. From our phones they can obtain financial information, personal and private data such as e-mails, pictures, messages, personal and business contact lists, and passwords. As a result, security threats are on the rise, especially in corporations.
    
    Safeguarding the security of mobile devices is ever more complex. Almost all employees routinely access corporate data either from a mobile device or a personal smartphone. This increases the likelihood of sensitive information getting into the wrong hands. The security risks involved in the use of mobile devices may involve either *physical or executable security* ([Figure 8.15](#c8.xhtml#f8.15)).
    
    ![FIGURE 8.15 Physical and Executable Security.](images/fig8.15.jpg)
    
    **FIGURE 8.15** Physical and Executable Security.
    
    ### [8.5.1 Physical Security](#contents.xhtml#re_h-8-14)
    
    Physical security, such as theft or loss of the device is one of the greatest threats. Since the devices are easy to carry, they are stolen or lost more frequently than laptop computers. The Cellular Telecommunications and Internet Association (CTIA), which represents the U.S. wireless communications industry, has announced an agreement between major smartphone manufacturers and all of the leading U.S. wireless carriers to enable smartphones with "kill-switch" functionality on phones sold in the United States after July 2015 that can temporarily disable the device. This potentially solves the theft problem, but it is up to the user to enable this "kill-switch" (the human element). As in many so many other security-related issues, the human element is the weakest link.
    
    CTIA has created an online tool that allows anyone to check if a phone has been registered as lost or stolen. All a person needs to perform the check is the IMEI number of the device.^([^(453)](#fn453))
    
    1.  I. Delete or render inaccessible all information on the smartphone relating to the account holder
    2.  II. Render the smartphone inoperable on the network of any provider of commercial mobile service or commercial mobile data service globally
    3.  III. Prevent the smartphone from being reactivated or reprogrammed without a passcode or similar authorization to an unauthorized factory reset
    4.  IV. Restore personal information from the smartphone onto a compatible or interoperable device.^([^(454)](#fn454))
    
    Furthermore, the act orders the Federal Communications Commission (FCC) to establish a framework to deter and prevent theft and protect consumers. It prohibits service providers from charging fees for making available such functions as the initial prompt and the ability to opt out. The legislation requires manufacturers such as Google and Apple to include tracking and remote protection software such as Find My iPhone and Find My Device to track the device’s last known location and turn on the Activation Lock.
    
    The Global System for Mobile Communications (GSMA) represents the interests of mobile operators worldwide and maintains an International Mobile Equipment Identity Database for mobile devices.^([^(455)](#fn455))
    
    ### [8.5.2 Executable Security](#contents.xhtml#re_h-8-15)
    
    Mobile devices, like other computing devices, are vulnerable to intrusion, intentional intrusion such as hacking, or intrusion through malware that is currently distributed around the Internet. The most common executable security threats ([Figure 8.16](#c8.xhtml#f8.16)) are the following:
    
    ![FIGURE 8.16 Some of the Main Executable Security Threats.](images/fig8.16.jpg)
    
    **FIGURE 8.16** Some of the Main Executable Security Threats.
    
    *   **Malicious text messages**
    
    *Pegasus* was discovered when a political activist received SMS messages that contained malicious links. Instead of clicking on the links, the activist forwarded them to the security labs Citizen Lab and LooKout for examination. If the activist had clicked on the links, his iPhone would have become infected and remotely jailbroken.^([^(456)](#fn456))
    
    The NSO group, an Israeli surveillance technology company, has developed spyware and other capabilities not intended for the average hacker. According to the company, it provides *authorized governments with technology that helps them combat terror and crime.*^([^(457)](#fn457))
    
    Two-factor authentication (2FA) codes from SMS adds an additional layer of security that involves not only a username and a password, but also requires an additional layer of authentication, a code that usually comes on an SMS or via e-mail. However, a simple SMS received can still infect a mobile device even if it is protected by 2FA authentication.
    
    In fact, 2FA authentication raises the level of danger associated with infected SMS. For example, Google’s 2FA authentication sends a 6-digit code via text message when a user attempts to log in. First, the SMS steals the user’s personal information by intercepting SMS messages, then a desktop component phishes the user’s computer and tricks the user into installing smartphone malware to prevent 2FA authentication.^([^(458)](#fn458))
    
    *   **Malware**
    
    The term Malware stands for malicious software. The term is used to describe an intrusive software that impairs a computing device without the user’s knowledge. Malware consists of computer viruses, worms, Trojan horses, and spyware. According to a McAfee Mobile Threat Report Q1, 2020, mobile malware has increased the number of attacks on mobile devices, using a wide variety of backdoors that disguise the attacks, making it difficult to identify and remove.^([^(459)](#fn459))
    
    *   **Phishing attack**
    
    An additional way to launch malware in a mobile device is through a phishing attack. Phishing refers to attacks that attempt to steal personal or sensitive information, such as usernames, passwords, credit card information, and whatever else is stored on the device’s SIM card. Mobile device operating systems and their browsers are not equipped with a security suite that can detect the difference between a fake link and a real link. When an unsuspecting user enters his passwords and credit card information, the phishing attack begins.^([^(460)](#fn460))
    
    *   **SIM-jacking or SIM swapping**
    
    SIM-jacking is when cybercriminals obtain personal information from social media, data breaches or by conning mobile phone users. Then, the hacker uses this information to convince network providers to transfer their numbers to new SIM cards. Once the SIM swap is complete, messages containing codes can be intercepted, and impostors can take over an email, social media, or mobile banking account. The SIM-jacking attacks in the recent past have led to several high-profile thefts of cryptocurrency.^([^(461)](#fn461))
    
    *   **Spyware**
    
    Spyware is a type of malicious program that gathers personal information from a device, such as its location or text message history, during a designated time. An example is the hidden spyware in a legitimate South Korean transit app that allowed hackers into the developer’s Google Play account.^([^(462)](#fn462))
    
    *   **Unsecured Wi-Fi**
    
    One of the major technologies that mobile devices rely on is Wi-Fi technology; we all regularly connect our devices to the nearest Wi-Fi network. Free or public Wi-Fi nodes, or “hotspots,” have been a convenient way for users to enjoy free access to the Internet. Unfortunately, unsecured free access allows hackers to use sniffing apps to intercept and gather data. In addition, mobile devices transmit search requests, looking for nearby networks, and these requests contain the device’s unique MAC address. A hacker can then simply display these requests.^([^(463)](#fn463))
    
    Another way that hackers can fool unsuspecting users is called Network Spoofing, where the attack offers the user what looks like a real Wi-Fi network. Usually set up in a high-traffic public location, the hacker provides access points and might name it, for example, “Free Coffeehouse Wi-Fi Access” to encourage users to connect.
    
    ## [8.6 Conclusion](#contents.xhtml#re_h-8-16)
    
    Mobile devices have come a long way from the brick phone of 40 years ago. They make our lives more efficient, easier, and more enjoyable. They can help us shop, take photos, search the web, identify faces, provide entertainment, replace a credit card, do our banking, and function as a personal assistant. The microprocessor inside today’s mobile phone is more powerful than the computer used to send Neil Armstrong to the moon in 1969. Even a modern toaster has more processing power than the Apollo Guidance Computer^([^(464)](#fn464))
    
    ![FIGURE 8.17 The Apollo Guidance and Navigation System. Photograph courtesy Smithsonian Institute.](images/fig8.17.jpg)
    
    **FIGURE 8.17** The Apollo Guidance and Navigation System. Photograph courtesy Smithsonian Institute.
    
    ![FIGURE 8.18 On July 20, 1969, America’s Apollo 11 landed on the moon, c1969. Photograph from National Aeronautics and Space Administration (NASA).](images/fig8.18.jpg)
    
    **FIGURE 8.18** On July 20, 1969, America’s Apollo 11 landed on the moon, c1969. Photograph from National Aeronautics and Space Administration (NASA).
    
    ![FIGURE 8.19 These computers were used during NASA’s Project Mercury, 1952–1968. Photograph from National Aeronautics and Space Administration (NASA).](images/fig8.19.jpg)
    
    **FIGURE 8.19** These computers were used during NASA’s Project Mercury, 1952–1968. Photograph from National Aeronautics and Space Administration (NASA).
    
    These small devices will continue to reinvent themselves. They are amazing, but do we rely on and trust them too much?
    
    Nonetheless, mobile phones will become more flexible, will have a longer battery life, and will become more environmentally friendly. They will not begin to lose their central place in our lives until something else replaces them.
    
    ## [8.7 Key Words](#contents.xhtml#re_h-8-17)
    
     
    | Angle of Arrival (AOA)  
    Android || Code Division Multiple Access (CDMA) |
    | --- | --- |
    | Antenna || Display |
    | architecture || Electronic Serial Number (ESN) |
    | Apple’s iOS || Executable security |
    | Android Runtime (ART) || Fifth Generation (5G) |
    | Applications (apps) || First Generation (1G) |
    | Application Program Interface (API) || Fourth Generation (4G) |
    | Base Station Controller (BSC)  
    Base Transceiver system (BTS) || Global System for Mobile Communication (GSM) |
    | Bluetooth || Hexagonal Cellular Network |
    | Cellular || Hardware Abstraction Layer (HAL) |
    | Cellular System Identification number (SID) || Hardware  
    Java API Framework |
    | Cell Tower Triangulation || Long Term Evolution (LTE) |
    | Cocoa Touch downlink || Linux kernel Layer |
    | Global Positioning System (GPS) || Malicious Text Messages |
    | Malware || Phishing Attack |
    | Man-in-the-Middle attack || Physical Security |
    | Media Access Control (MAC) || Radiofrequency (RF) |
    | Media Service Layer || Security |
    | Microphone || Sensors |
    | Microwave Access (WIMAX) || Second Generation (2G) |
    | Microwave links || SIM Swapping |
    | Mobile Directory Number (MDN) || Smartphone |
    | Mobile Equipment Identifier (MEID) || Spyware  
    System Application Layer |
    | Mobile devices || Software Development Kit (SDK) |
    | Mobile Identification Number (MIN) || Speaker  
    System-on-Chip (SOC) |
    | Mobile Switching Center (MSC) || Subscriber Identity Module (SIM) |
    | Mobile Telephone Switching Office (MTSO) || Third Generation (3G)  
    Time of Arrival (ToA) |
    | Native C/C++ Libraries || Time Difference of Arrival (TDoA) |
    | Network Identification (NID) || Unsecured Wi-Fi |
    | Power Management || Uplink |
    | Printed Circuit Board (PCB) || Wi-Fi Based Localization. |
    | Operating Systems (OS) ||  |
    
    # [Appendix A](#contents.xhtml#re_appendixA)
    
    ## [A Complete Text of the Computer Fraud and Abuse Act (CFAA) 18 U.S.C. § 1030.](#contents.xhtml#re_appendixA)^([^(465)](#fn465)) 
    
    ## Fraud and Related Activity in Connection with Computers
    
    1.  a) Whoever—
    2.  (1) having knowingly accessed a computer without authorization or exceeding,
    3.  (2) and by means of such conduct having obtained information that has been determined by the United States Government pursuant to an Executive order or statute to require protection against unauthorized disclosure for reasons of national defense or foreign relations, or any restricted data, as defined in paragraph y. of section 11 of the Atomic Energy Act of 1954, with reason to believe that such information so obtained could be used to the injury of the United States, or to the advantage of any foreign nation willfully communicates, delivers, transmits, or causes to be communicated, delivered, or transmitted, or attempts to communicate, deliver, transmit or cause to be communicated, delivered, or transmitted the same to any person not entitled to receive it, or willfully retains the same and fails to deliver it to the officer or employee of the United States entitled to receive it;
    4.  (2) intentionally accesses a computer without authorization or exceeds authorized access, and thereby obtains— 
        1.  (A) information contained in a financial record of a financial institution, or of a card issuer as defined in section 1602(n) of title 15, or contained in a file of a consumer reporting agency on a consumer, as such terms are defined in the Fair Credit Reporting Act (15 U.S.C. 1681 et seq.);
        2.  (B) information from any department or agency of the United States; or
        3.  (C) information from any protected computer;
    5.  (3) intentionally, without authorization to access any nonpublic computer of a department or agency of the United States, accesses such a computer of that department or agency that is exclusively for the use of the Government of the United States or, in the case of a computer not exclusively for such use, is used by or for the Government of the United States and such conduct affects that use by or for the Government of the United States;
    6.  (4) knowingly and with intent to defraud, accesses a protected computer without authorization, or exceeds authorized access, and by means of such conduct furthers the intended fraud and obtains anything of value, unless the object of the fraud and the thing obtained consists only of the use of the computer and the value of such use is not more than $5,000 in any 1-year period;
    7.  (5) 
        1.  (A) knowingly causes the transmission of a program, information, code, or command, and as a result of such conduct, intentionally causes damage without authorization, to a protected computer;
        2.  (B) intentionally accesses a protected computer without authorization, and as a result of such conduct, recklessly causes damage; or
        3.  (C) intentionally accesses a protected computer without authorization, and as a result of such conduct, causes damage and loss.
    8.  (6) knowingly and with intent to defraud traffics (as defined in section 1029) in any password or similar information through which a computer may be accessed without authorization, if— 
        1.  (A) such trafficking affects interstate or foreign commerce; or
        2.  (B) such computer is used by or for the Government of the United States;
    9.  (7) with intent to extort from any person any money or other thing of value, transmits in interstate or foreign commerce any communication containing any— 
        
        1.  (A) threat to cause damage to a protected computer;
        2.  (B) threat to obtain information from a protected computer without authorization or in excess of authorization or to impair the confidentiality of information obtained from a protected computer without authorization or by exceeding authorized access; or
        3.  (C) demand or request for money or other thing of value in relation to damage to a protected computer, where such damage was caused to facilitate the extortion;
        
          
        shall be punished as provided in subsection (c) of this section.
    10.  b) Whoever conspires to commit or attempts to commit an offense under subsection (a) of this section shall be punished as provided in subsection (c) of this section.
    11.  c) The punishment for an offense under subsection (a) or (b) of this section is— 
         1.  1.  (A) a fine under this title or imprisonment for not more than ten years, or both, in the case of an offense under subsection (a)(1) of this section which does not occur after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph; and
             2.  (B) a fine under this title or imprisonment for not more than twenty years, or both, in the case of an offense under subsection (a)(1) of this section which occurs after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph;
         2.  1.  (A) except as provided in subparagraph (B), a fine under this title or imprisonment for not more than one year, or both, in the case of an offense under subsection (a)(2), (a)(3), or (a)(6) of this section which does not occur after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph;
             2.  (B) a fine under this title or imprisonment for not more than 5 years, or both, in the case of an offense under subsection (a)(2), or an attempt to commit an offense punishable under this subparagraph, if— 
                 1.  (i) the offense was committed for purposes of commercial advantage or private financial gain;
                 2.  (ii) the offense was committed in furtherance of any criminal or tortious act in violation of the Constitution or laws of the United States or of any State; or
                 3.  (iii) the value of the information obtained exceeds $5,000; and
             3.  (C) a fine under this title or imprisonment for not more than ten years, or both, in the case of an offense under subsection (a)(2), (a)(3) or (a)(6) of this section which occurs after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph;
         3.  1.  (A) a fine under this title or imprisonment for not more than five years, or both, in the case of an offense under subsection (a)(4) or (a)(7) of this section which does not occur after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph; and
             2.  (B) a fine under this title or imprisonment for not more than ten years, or both, in the case of an offense under subsection (a)(4), or (a)(7) of this section which occurs after a conviction for another offense under this section, or an attempt to commit an offense punishable under this subparagraph;
         4.  1.  (A) except as provided in subparagraphs (E) and (F), a fine under this title, imprisonment for not more than 5 years, or both, in the case of— 
                 1.  (i) an offense under subsection (a)(5)(B), which does not occur after a conviction for another offense under this section, if the offense caused (or, in the case of an attempted offense, would, if completed, have caused)— 
                     1.  (I) loss to 1 or more persons during any 1-year period (and, for purposes of an investigation, prosecution, or other proceeding brought by the United States only, loss resulting from a related course of conduct affecting 1 or more other protected computers) aggregating at least $5,000 in value;
                     2.  (II) the modification or impairment, or potential modification or impairment, of the medical examination, diagnosis, treatment, or care of 1 or more individuals;
                     3.  (III) physical injury to any person;
                     4.  (IV) a threat to public health or safety;
                     5.  (V) damage affecting a computer used by or for an entity of the United States Government in furtherance of the administration of justice, national defense, or national security; or
                     6.  (VI) damage affecting 10 or more protected computers during any 1-year period; or
                 2.  (ii) an attempt to commit an offense punishable under this subparagraph;
             2.  (B) except as provided in subparagraphs (E) and (F), a fine under this title, imprisonment for not more than 10 years, or both, in the case of— 
                 1.  (i) an offense under subsection (a)(5)(A), which does not occur after a conviction for another offense under this section, if the offense caused (or, in the case of an attempted offense, would, if completed, have caused) a harm provided in subclauses (I) through (VI) of subparagraph (A)(i); or
                 2.  (ii) an attempt to commit an offense punishable under this subparagraph;
             3.  (C) except as provided in subparagraphs (E) and (F), a fine under this title, imprisonment for not more than 20 years, or both, in the case of— 
                 1.  (i) an offense or an attempt to commit an offense under subparagraphs (A) or (B) of subsection (a)(5) that occurs after a conviction for another offense under this section; or
                 2.  (ii) an attempt to commit an offense punishable under this subparagraph;
             4.  (D) a fine under this title, imprisonment for not more than 10 years, or both, in the case of— 
                 1.  (i) an offense or an attempt to commit an offense under subsection (a)(5)(C) that occurs after a conviction for another offense under this section; or
                 2.  (ii) an attempt to commit an offense punishable under this subparagraph;
             5.  (E) if the offender attempts to cause or knowingly or recklessly causes serious bodily injury from conduct in violation of subsection (a)(5)(A), a fine under this title, imprisonment for not more than 20 years, or both;
             6.  (F) if the offender attempts to cause or knowingly or recklessly causes death from conduct in violation of subsection (a)(5)(A), a fine under this title, imprisonment for any term of years or for life, or both; or
             7.  (G) a fine under this title, imprisonment for not more than 1 year, or both, for— 
                 1.  (i) any other offense under subsection (a)(5); or
                 2.  (ii) an attempt to commit an offense punishable under this subparagraph. 
                     1.  The United States Secret Service shall, in addition to any other agency having such authority, have the authority to investigate offenses under this section.
                     2.  The Federal Bureau of Investigation shall have primary authority to investigate offenses under subsection (a)(1) for any cases involving espionage, foreign counterintelligence, information protected against unauthorized disclosure for reasons of national defense or foreign relations, or Restricted Data (as that term is defined in section 11y of the Atomic Energy Act of 1954 (42 U.S.C. 2014(y)), except for offenses affecting the duties of the United States Secret Service pursuant to section 3056(a) of this title.
                     3.  Such authority shall be exercised in accordance with an agreement which shall be entered into by the Secretary of the Treasury and the Attorney General.
    12.  d) As used in this section— 
         1.  (1) the term “computer” means an electronic, magnetic, optical, electrochemical, or other high speed data processing device performing logical, arithmetic, or storage functions, and includes any data storage facility or communications facility directly related to or operating in conjunction with such device, but such term does not include an automated typewriter or typesetter, a portable hand held calculator, or other similar device;
         2.  (2) the term “protected computer” means a computer— 
             1.  (A) exclusively for the use of a financial institution or the United States Government, or, in the case of a computer not exclusively for such use, used by or for a financial institution or the United States Government and the conduct constituting the offense affects that use by or for the financial institution or the Government; or
             2.  (B) which is used in or affecting interstate or foreign commerce or communication, including a computer located outside the United States that is used in a manner that affects interstate or foreign commerce or communication of the United States;
         3.  (3) the term “State” includes the District of Columbia, the Commonwealth of Puerto Rico, and any other commonwealth, possession or territory of the United States;
         4.  (4) the term “financial institution” means— 
             1.  (A) an institution, with deposits insured by the Federal Deposit Insurance Corporation;
             2.  (B) the Federal Reserve or a member of the Federal Reserve including any Federal Reserve Bank;
             3.  (C) a credit union with accounts insured by the National Credit Union Administration;
             4.  (D) a member of the Federal home loan bank system and any home loan bank;
             5.  (E) any institution of the Farm Credit System under the Farm Credit Act of 1971;
             6.  (F) a broker-dealer registered with the Securities and Exchange Commission pursuant to section 15 of the Securities Exchange Act of 1934;
             7.  (G) the Securities Investor Protection Corporation;
             8.  (H) a branch or agency of a foreign bank (as such terms are defined in paragraphs (1) and (3) of section 1(b) of the International Banking Act of 1978); and
             9.  (I) an organization operating under section 25 or section 25(a)⁴  of the Federal Reserve Act;
         5.  (5) the term “financial record” means information derived from any record held by a financial institution pertaining to a customer's relationship with the financial institution;
         6.  (6) the term “exceeds authorized access” means to access a computer with authorization and to use such access to obtain or alter information in the computer that the accesser is not entitled so to obtain or alter;
         7.  (7) the term “department of the United States” means the legislative or judicial branch of the Government or one of the executive departments enumerated in section 101 of title 5;
         8.  (8) the term “damage” means any impairment to the integrity or availability of data, a program, a system, or information;
         9.  (9) the term “government entity” includes the Government of the United States, any State or political subdivision of the United States, any foreign country, and any state, province, municipality, or other political subdivision of a foreign country;
         10.  (10) the term “conviction” shall include a conviction under the law of any State for a crime punishable by imprisonment for more than 1 year, an element of which is unauthorized access, or exceeding authorized access, to a computer;
         11.  (11) the term “loss” means any reasonable cost to any victim, including the cost of responding to an offense, conducting a damage assessment, and restoring the data, program, system, or information to its condition prior to the offense, and any revenue lost, cost incurred, or other consequential damages incurred because of interruption of service; and
         12.  (12) the term “person” means any individual, firm, corporation, educational institution, financial institution, governmental entity, or legal or other entity.
    13.  e) This section does not prohibit any lawfully authorized investigative, protective, or intelligence activity of a law enforcement agency of the United States, a State, or a political subdivision of a State, or of an intelligence agency of the United States.
    14.  f) Any person who suffers damage or loss by reason of a violation of this section may maintain a civil action against the violator to obtain compensatory damages and injunctive relief or other equitable relief. A civil action for a violation of this section may be brought only if the conduct involves 1 of the factors set forth in subclauses ⁵  (I), (II), (III), (IV), or (V) of subsection (c)(4)(A)(i). Damages for a violation involving only conduct described in subsection (c)(4)(A)(i)(I) are limited to economic damages. No action may be brought under this subsection unless such action is begun within 2 years of the date of the act complained of or the date of the discovery of the damage. No action may be brought under this subsection for the negligent design or manufacture of computer hardware, computer software, or firmware.
    15.  g) The Attorney General and the Secretary of the Treasury shall report to the Congress annually, during the first 3 years following the date of the enactment of this subsection, concerning investigations and prosecutions under subsection (a)(5).
    16.  h) 
         1.  (1) The court, in imposing sentence on any person convicted of a violation of this section, or convicted of conspiracy to violate this section, shall order, in addition to any other sentence imposed and irrespective of any provision of State law, that such person forfeit to the United States— 
             1.  (B) such person's interest in any personal property that was used or intended to be used to commit or to facilitate the commission of such violation; and
             2.  (C) any property, real or personal, constituting or derived from, any proceeds that such person obtained, directly or indirectly, as a result of such violation.
         2.  (2) The criminal forfeiture of property under this subsection, any seizure and disposition thereof, and any judicial proceeding in relation thereto, shall be governed by the provisions of section 413 of the Comprehensive Drug Abuse Prevention and Control Act of 1970 (21 U.S.C. 853), except subsection (d) of that section.
    17.  i) For purposes of subsection (i), the following shall be subject to forfeiture to the United States and no property right shall exist in them: 
         1.  (1) Any personal property used or intended to be used to commit or to facilitate the commission of any violation of this section, or a conspiracy to violate this section.
         2.  (2) Any property, real or personal, which constitutes or is derived from proceeds traceable to any violation of this section, or a conspiracy to violate this section
    
    ## Amendments
    
    **2008**—Subsec. (a)(2)(C). Pub. L. 110–326, §203, struck out “if the conduct involved an interstate or foreign communication” after “computer”.
    
    Subsec. (a)(5). Pub. L. 110–326, §204(a)(1), redesignated cls. (i) to (iii) of subpar. (A) as subpars. (A) to (C), respectively, substituted “damage and loss.” for “damage; and” in subpar. (C), and struck out former subpar. (B) which read as follows:
    
    “(B) by conduct described in clause (i), (ii), or (iii) of subparagraph (A), caused (or, in the case of an attempted offense, would, if completed, have caused)—
    
    “(i) loss to 1 or more persons during any 1-year period (and, for purposes of an investigation, prosecution, or other proceeding brought by the United States only, loss resulting from a related course of conduct affecting 1 or more other protected computers) aggregating at least $5,000 in value;
    
    “(ii) the modification or impairment, or potential modification or impairment, of the medical examination, diagnosis, treatment, or care of 1 or more individuals;
    
    “(iii) physical injury to any person;
    
    “(iv) a threat to public health or safety; or
    
    “(v) damage affecting a computer system used by or for a government entity in furtherance of the administration of justice, national defense, or national security;”.
    
    Subsec. (a)(7). Pub. L. 110–326, §205, amended par. (7) generally. Prior to amendment, par. (7) read as follows: “with intent to extort from any person any money or other thing of value, transmits in interstate or foreign commerce any communication containing any threat to cause damage to a protected computer;”.
    
    Subsec. (b). Pub. L. 110–326, §206, inserted “conspires to commit or” after “Whoever”.
    
    Subsec. (c)(2)(A). Pub. L. 110–326, §204(a)(2)(A), struck out “(a)(5)(A)(iii),” after “(a)(3),”.
    
    Subsec. (c)(3)(B). Pub. L. 110–326, §204(a)(2)(B), struck out “(a)(5)(A)(iii),” after “(a)(4),”.
    
    Subsec. (c)(4). Pub. L. 110–326, §204(a)(2)(C), amended par. (4) generally. Prior to amendment, par. (4) related to fines and imprisonment for intentionally or recklessly causing damage to a protected computer without authorization.
    
    Subsec. (c)(5). Pub. L. 110–326, §204(a)(2)(D), struck out par. (5) which related to fine or imprisonment for knowingly or recklessly causing or attempting to cause serious bodily injury or death from certain conduct damaging a protected computer.
    
    Subsec. (e)(2)(B). Pub. L. 110–326, §207, inserted “or affecting” after “which is used in”.
    
    Subsec. (g). Pub. L. 110–326, §204(a)(3)(B), in the third sentence, substituted “subsection (c)(4)(A)(i)(I)” for “subsection (a)(5)(B)(i)”.
    
    Pub. L. 110–326, §204(a)(3)(A), which directed substitution of “in subclauses (I), (II), (III), (IV), or (V) of subsection (c)(4)(A)(i)” for “in clauses (i), (ii), (iii), (iv), or (v) of subsection (a)(5)(B)” in the second sentence, was executed by making the substitution for “in clause (i), (ii), (iii), (iv), or (v) of subsection (a)(5)(B)” to reflect the probable intent of Congress.
    
    Subsecs. (i), (j). Pub. L. 110–326, §208, added subsecs. (i) and (j).
    
    **2002**—Subsec. (a)(5)(B). Pub. L. 107–273, §4005(a)(3), realigned margins.
    
    Subsec. (c)(2)(B). Pub. L. 107–273, §4002(b)(1), realigned margins.
    
    Subsec. (c)(2)(B)(iii). Pub. L. 107–273, §4002(b)(12)(A), inserted “and” at end.
    
    Subsec. (c)(3)(B). Pub. L. 107–273, §4005(d)(3), inserted comma after “(a)(4)”.
    
    Subsec. (c)(4)(A), (C). Pub. L. 107–296, §225(g)(2), inserted “except as provided in paragraph (5),” before “a fine under this title”.
    
    Subsec. (c)(5). Pub. L. 107–296, §225(g)(1), (3), (4), added par. (5).
    
    Subsec. (e)(4)(I). Pub. L. 107–273, §4002(b)(12)(B), substituted semicolon for period at end.
    
    **2001**—Subsec. (a)(5)(A). Pub. L. 107–56, §814(a)(1)–(3), designated existing provisions as cl. (i), redesignated subpars. (B) and (C) as cls. (ii) and (iii), respectively, of subpar. (A), and inserted “and” at end of cl. (iii).
    
    Subsec. (a)(5)(B). Pub. L. 107–56, §814(a)(4), added subpar. (B). Former subpar. (B) redesignated cl. (ii) of subpar. (A).
    
    Subsec. (a)(5)(C). Pub. L. 107–56, §814(a)(2), redesignated subpar. (C) as cl. (iii) of subpar. (A).
    
    Subsec. (a)(7). Pub. L. 107–56, §814(b), struck out “, firm, association, educational institution, financial institution, government entity, or other legal entity,” before “any money or other thing of value”.
    
    Subsec. (c)(2)(A). Pub. L. 107–56, §814(c)(1)(A), inserted “except as provided in subparagraph (B),” before “a fine”, substituted “(a)(5)(A)(iii)” for “(a)(5)(C)”, and struck out “and” at end.
    
    Subsec. (c)(2)(B). Pub. L. 107–56, §814(c)(1)(B), inserted “or an attempt to commit an offense punishable under this subparagraph,” after “subsection (a)(2),” in introductory provisions.
    
    Subsec. (c)(2)(C). Pub. L. 107–56, §814(c)(1)(C), struck out “and” at end.
    
    Subsec. (c)(3). Pub. L. 107–56, §814(c)(2), struck out “, (a)(5)(A), (a)(5)(B),” after “subsection (a)(4)” in subpars. (A) and (B) and substituted “(a)(5)(A)(iii)” for “(a)(5)(C)” in subpar. (B).
    
    Subsec. (c)(4). Pub. L. 107–56, §814(c)(3), added par. (4).
    
    Subsec. (d). Pub. L. 107–56, §506(a), amended subsec. (d) generally. Prior to amendment, subsec. (d) read as follows: “The United States Secret Service shall, in addition to any other agency having such authority, have the authority to investigate offenses under subsections (a)(2)(A), (a)(2)(B), (a)(3), (a)(4), (a)(5), and (a)(6) of this section. Such authority of the United States Secret Service shall be exercised in accordance with an agreement which shall be entered into by the Secretary of the Treasury and the Attorney General.”
    
    Subsec. (e)(2)(B). Pub. L. 107–56, §814(d)(1), inserted “, including a computer located outside the United States that is used in a manner that affects interstate or foreign commerce or communication of the United States” before semicolon.
    
    Subsec. (e)(7). Pub. L. 107–56, §814(d)(2), struck out “and” at end.
    
    Subsec. (e)(8). Pub. L. 107–56, §814(d)(3), added par. (8) and struck out former par. (8) which read as follows: “the term ‘damage’ means any impairment to the integrity or availability of data, a program, a system, or information, that—
    
    “(A) causes loss aggregating at least $5,000 in value during any 1-year period to one or more individuals;
    
    “(B) modifies or impairs, or potentially modifies or impairs, the medical examination, diagnosis, treatment, or care of one or more individuals;
    
    “(C) causes physical injury to any person; or
    
    “(D) threatens public health or safety; and”.
    
    Subsec. (e)(10) to (12). Pub. L. 107–56, §814(d)(4), (5), added pars. (10) to (12).
    
    Subsec. (g). Pub. L. 107–56, §814(e), substituted “A civil action for a violation of this section may be brought only if the conduct involves 1 of the factors set forth in clause (i), (ii), (iii), (iv), or (v) of subsection (a)(5)(B). Damages for a violation involving only conduct described in subsection (a)(5)(B)(i) are limited to economic damages.” for “Damages for violations involving damage as defined in subsection (e)(8)(A) are limited to economic damages.” and inserted at end “No action may be brought under this subsection for the negligent design or manufacture of computer hardware, computer software, or firmware.”
    
    **1996**—Subsec. (a)(1). Pub. L. 104–294, §201(1)(A), substituted “having knowingly accessed” for “knowingly accesses”, “exceeding authorized access” for “exceeds authorized access”, “such conduct having obtained information” for “such conduct obtains information”, and “could be used to the injury of the United States” for “is to be used to the injury of the United States”, struck out “the intent or” before “reason to believe”, and inserted before semicolon at end “willfully communicates, delivers, transmits, or causes to be communicated, delivered, or transmitted, or attempts to communicate, deliver, transmit or cause to be communicated, delivered, or transmitted the same to any person not entitled to receive it, or willfully retains the same and fails to deliver it to the officer or employee of the United States entitled to receive it”.
    
    Subsec. (a)(2). Pub. L. 104–294, §201(1)(B), inserted dash after “thereby obtains”, redesignated remainder of par. (2) as subpar. (A), and added subpars. (B) and (C).
    
    Subsec. (a)(3). Pub. L. 104–294, §201(1)(C), inserted “nonpublic” before “computer of a department or agency”, struck out “adversely” after “and such conduct”, and substituted “that use by or for the Government of the United States” for “the use of the Government's operation of such computer”.
    
    Subsec. (a)(4). Pub. L. 104–294, §201(1)(D), substituted “protected computer” for “Federal interest computer” and inserted “and the value of such use is not more than $5,000 in any 1-year period” before semicolon at end.
    
    Subsec. (a)(5). Pub. L. 104–294, §201(1)(E), inserted par. (5) and struck out former par. (5) which related to fraud in connection with computers in causing transmission of program, information, code, or command to a computer or computer system in interstate or foreign commerce which damages such system, program, information, or code, or causes a withholding or denial of use of hardware or software, or transmits viruses which causes damage in excess of $1,000 or more during any one-year period, or modifies or impairs medical examination, diagnosis, treatment or care of individuals.
    
    Subsec. (a)(5)(B)(ii)(II)(bb). Pub. L. 104–294, §604(b)(36)(A), which directed insertion of “or” at end of subsec., could not be executed because no subsec. (a)(5)(B)(ii)(II)(bb) existed subsequent to amendment by Pub. L. 104–294, §201(1)(E). See above.
    
    Subsec. (a)(7). Pub. L. 104–294, §201(1)(F), added par. (7).
    
    Subsec. (c)(1). Pub. L. 104–294, §201(2)(A), substituted “under this section” for “under such subsection” in subpars. (A) and (B).
    
    Subsec. (c)(1)(B). Pub. L. 104–294, §604(b)(36)(B), struck out “and” after semicolon at end.
    
    Subsec. (c)(2)(A). Pub. L. 104–294, §201(2)(B)(i), inserted “, (a)(5)(C),” after “(a)(3)” and substituted “under this section” for “under such subsection”.
    
    Subsec. (c)(2)(B). Pub. L. 104–294, §201(2)(B)(iii), added subpar. (B). Former subpar. (B) redesignated (C).
    
    Subsec. (c)(2)(C). Pub. L. 104–294, §201(2)(B)(iv), substituted “under this section” for “under such subsection” and inserted “and” at end.
    
    Pub. L. 104–294, §201(2)(B)(ii), redesignated subpar. (B) as (C).
    
    Subsec. (c)(3)(A). Pub. L. 104–294, §201(2)(C)(i), substituted “(a)(4), (a)(5)(A), (a)(5)(B), or (a)(7)” for “(a)(4) or (a)(5)(A)” and “under this section” for “under such subsection”.
    
    Subsec. (c)(3)(B). Pub. L. 104–294, §201(2)(C)(ii), substituted “(a)(4), (a)(5)(A), (a)(5)(B), (a)(5)(C), or (a)(7)” for “(a)(4) or (a)(5)” and “under this section” for “under such subsection”.
    
    Subsec. (c)(4). Pub. L. 104–294, §201(2)(D), struck out par. (4) which read as follows: “a fine under this title or imprisonment for not more than 1 year, or both, in the case of an offense under subsection (a)(5)(B).”
    
    Subsec. (d). Pub. L. 104–294, §201(3), inserted “subsections (a)(2)(A), (a)(2)(B), (a)(3), (a)(4), (a)(5), and (a)(6) of” before “this section” in first sentence.
    
    Subsec. (e)(2). Pub. L. 104–294, §201(4)(A)(i), substituted “protected” for “Federal interest” in introductory provisions.
    
    Subsec. (e)(2)(A). Pub. L. 104–294, §201(4)(A)(ii), substituted “that use by or for the financial institution or the Government” for “the use of the financial institution's operation or the Government's operation of such computer”.
    
    Subsec. (e)(2)(B). Pub. L. 104–294, §201(4)(A)(iii), added subpar. (B) and struck out former subpar. (B) which read as follows: “which is one of two or more computers used in committing the offense, not all of which are located in the same State;”.
    
    Subsec. (e)(8), (9). Pub. L. 104–294, §201(4)(B)–(D), added pars. (8) and (9).
    
    Subsec. (g). Pub. L. 104–294, §604(b)(36)(C), substituted “violation of this section” for “violation of the section”.
    
    Pub. L. 104–294, §201(5), struck out “, other than a violation of subsection (a)(5)(B),” before “may maintain a civil action” and substituted “involving damage as defined in subsection (e)(8)(A)” for “of any subsection other than subsection (a)(5)(A)(ii)(II)(bb) or (a)(5)(B)(ii)(II)(bb)”.
    
    Subsec. (h). Pub. L. 104–294, §604(b)(36)(D), substituted “subsection (a)(5)” for “section 1030(a)(5) of title 18, United States Code” before period at end.
    
    **1994**—Subsec. (a)(3). Pub. L. 103–322, §290001(f), inserted “adversely” before “affects the use of the Government's”.
    
    Subsec. (a)(5). Pub. L. 103–322, §290001(b), amended par. (5) generally. Prior to amendment, par. (5) read as follows: “intentionally accesses a Federal interest computer without authorization, and by means of one or more instances of such conduct alters, damages, or destroys information in any such Federal interest computer, or prevents authorized use of any such computer or information, and thereby—
    
    “(A) causes loss to one or more others of a value aggregating $1,000 or more during any one year period; or
    
    “(B) modifies or impairs, or potentially modifies or impairs, the medical examination, medical diagnosis, medical treatment, or medical care of one or more individuals; or”.
    
    Subsec. (c)(3)(A). Pub. L. 103–322, §290001(c)(2), inserted “(A)” after “(a)(5)”.
    
    Subsec. (c)(4). Pub. L. 103–322, §290001(c)(1), (3), (4), added par. (4).
    
    Subsec. (g). Pub. L. 103–322, §290001(d), added subsec. (g).
    
    Subsec. (h). Pub. L. 103–322, §290001(e), added subsec. (h).
    
    **1990**—Subsec. (a)(1). Pub. L. 101–647, §3533, substituted “paragraph y” for “paragraph r”.
    
    Subsec. (e)(3). Pub. L. 101–647, §1205(e), inserted “commonwealth,” before “possession or territory of the United States”.
    
    Subsec. (e)(4)(G). Pub. L. 101–647, §2597(j)(2), which directed substitution of a semicolon for a period at end of subpar. (G), could not be executed because it ended with a semicolon.
    
    Subsec. (e)(4)(H), (I). Pub. L. 101–647, §2597(j), added subpars. (H) and (I).
    
    **1989**—Subsec. (e)(4)(A). Pub. L. 101–73, §962(a)(5)(A), substituted “an institution,” for “a bank”.
    
    Subsec. (e)(4)(C) to (H). Pub. L. 101–73, §962(a)(5)(B), (C), redesignated subpars. (D) to (H) as (C) to (G), respectively, and struck out former subpar. (C) which read as follows: “an institution with accounts insured by the Federal Savings and Loan Insurance Corporation;”.
    
    **1988**—Subsec. (a)(2). Pub. L. 100–690 inserted a comma after “financial institution” and struck out the comma that followed a comma after “title 15”.
    
    **1986**—Subsec. (a). Pub. L. 99–474, §2(b)(2), struck out last sentence which read as follows: “It is not an offense under paragraph (2) or (3) of this subsection in the case of a person having accessed a computer with authorization and using the opportunity such access provides for purposes to which such access does not extend, if the using of such opportunity consists only of the use of the computer.”
    
    Subsec. (a)(1). Pub. L. 99–474, §2(c), substituted “or exceeds authorized access” for “, or having accessed a computer with authorization, uses the opportunity such access provides for purposes to which such authorization does not extend”.
    
    Subsec. (a)(2). Pub. L. 99–474, §2(a), (c), substituted “intentionally” for “knowingly”, substituted “or exceeds authorized access” for “, or having accessed a computer with authorization, uses the opportunity such access provides for purposes to which such authorization does not extend”, struck out “as such terms are defined in the Right to Financial Privacy Act of 1978 (12 U.S.C. 3401 et seq.),” after “financial institution,”, inserted “or of a card issuer as defined in section 1602(n) of title 15,” and struck out “or” appearing at end.
    
    Subsec. (a)(3). Pub. L. 99–474, §2(b)(1), amended par. (3) generally. Prior to amendment, par. (3) read as follows: “knowingly accesses a computer without authorization, or having accessed a computer with authorization, uses the opportunity such access provides for purposes to which such authorization does not extend, and by means of such conduct knowingly uses, modifies, destroys, or discloses information in, or prevents authorized use of, such computer, if such computer is operated for or on behalf of the Government of the United States and such conduct affects such operation;”.
    
    Subsec. (a)(4) to (6). Pub. L. 99–474, §2(d), added pars. (4) to (6).
    
    Subsec. (b). Pub. L. 99–474, §2(e), struck out par. (1) designation and par. (2) which provided a penalty for persons conspiring to commit an offense under subsec. (a).
    
    Subsec. (c). Pub. L. 99–474, §2(f)(9), substituted “(b)” for “(b)(1)” in introductory text.
    
    Subsec. (c)(1)(A). Pub. L. 99–474, §2(f)(1), substituted “under this title” for “of not more than the greater of $10,000 or twice the value obtained by the offense”.
    
    Subsec. (c)(1)(B). Pub. L. 99–474, §2(f)(2), substituted “under this title” for “of not more than the greater of $100,000 or twice the value obtained by the offense”.
    
    Subsec. (c)(2)(A). Pub. L. 99–474, §2(f)(3), (4), substituted “under this title” for “of not more than the greater of $5,000 or twice the value obtained or loss created by the offense” and inserted reference to subsec. (a)(6).
    
    Subsec. (c)(2)(B). Pub. L. 99–474, §2(f)(3), (5)–(7), substituted “under this title” for “of not more than the greater of $10,000 or twice the value obtained or loss created by the offense”, “not more than” for “not than”, inserted reference to subsec. (a)(6), and substituted “; and” for the period at end of subpar. (B).
    
    Subsec. (c)(3). Pub. L. 99–474, §2(f)(8), added par. (3).
    
    Subsec. (e). Pub. L. 99–474, §2(g), substituted a dash for the comma after “As used in this section”, realigned remaining portion of subsection, inserted “(1)” before “the term”, substituted a semicolon for the period at the end, and added pars. (2) to (7).
    
    Subsec. (f). Pub. L. 99–474, §2(h), added subsec. (f).
    
    ## Effective Date of 2002 Amendment
    
    Amendment by Pub. L. 107–296 effective 60 days after Nov. 25, 2002, see section 4 of Pub. L. 107–296, set out as an Effective Date note under section 101 of Title 6, Domestic Security.
    
    ## Transfer of Functions
    
    For transfer of the functions, personnel, assets, and obligations of the United States Secret Service, including the functions of the Secretary of the Treasury relating thereto, to the Secretary of Homeland Security, and for treatment of related references, see sections 381, 551(d), 552(d), and 557 of Title 6, Domestic Security, and the Department of Homeland Security Reorganization Plan of November 25, 2002, as modified, set out as a note under section 542 of Title 6.
    
    ## Reports to Congress
    
    Section 2103 of Pub. L. 98–473 directed Attorney General to report to Congress annually, during first three years following Oct. 12, 1984, concerning prosecutions under this section.
    
    # [Appendix B](#contents.xhtml#re_appendixB)
    
    ## [17 U.S.C. § 1201 Circumvention of Copyright Protection Systems](#contents.xhtml#re_appendixB)^([^(466)](#fn466)) 
    
     
    
     
    
    1.  (A) Violations Regarding Circumvention of Technological Measures.—(1)(A) No person shall circumvent a technological measure that effectively controls access to a work protected under this title. The prohibition contained in the preceding sentence shall take effect at the end of the 2-year period beginning on the date of the enactment of this chapter.
    2.  (B) The prohibition contained in subparagraph (A) shall not apply to persons who are users of a copyrighted work which is in a particular class of works, if such persons are, or are likely to be in the succeeding 3-year period, adversely affected by virtue of such prohibition in their ability to make noninfringing uses of that particular class of works under this title, as determined under subparagraph (C).
    3.  (C) During the 2-year period described in subparagraph (A), and during each succeeding 3-year period, the Librarian of Congress, upon the recommendation of the Register of Copyrights, who shall consult with the Assistant Secretary for Communications and Information of the Department of Commerce and report and comment on his or her views in making such recommendation, shall make the determination in a rulemaking proceeding for purposes of subparagraph (B) of whether persons who are users of a copyrighted work are, or are likely to be in the succeeding 3-year period, adversely affected by the prohibition under subparagraph (A) in their ability to make noninfringing uses under this title of a particular class of copyrighted works. In conducting such rulemaking, the Librarian shall examine— 
        1.  (i) the availability for use of copyrighted works;
        2.  (ii) the availability for use of works for nonprofit archival, preservation, and educational purposes;
        3.  (iii) the impact that the prohibition on the circumvention of technological measures applied to copyrighted works has on criticism, comment, news reporting, teaching, scholarship, or research;
        4.  (iv) the effect of circumvention of technological measures on the market for or value of copyrighted works; and
        5.  (v) such other factors as the Librarian considers appropriate.
    4.  (D) The Librarian shall publish any class of copyrighted works for which the Librarian has determined, pursuant to the rulemaking conducted under subparagraph (C), that noninfringing uses by persons who are users of a copyrighted work are, or are likely to be, adversely affected, and the prohibition contained in subparagraph (A) shall not apply to such users with respect to such class of works for the ensuing 3-year period.
    5.  (E) Neither the exception under subparagraph (B) from the applicability of the prohibition contained in subparagraph (A), nor any determination made in a rulemaking conducted under subparagraph (C), may be used as a defense in any action to enforce any provision of this title other than this paragraph. 
        2.  No person shall manufacture, import, offer to the public, provide, or otherwise traffic in any technology, product, service, device, component, or part thereof, that— 
            1.  (A) is primarily designed or produced for the purpose of circumventing a technological measure that effectively controls access to a work protected under this title;
            2.  (B) has only limited commercially significant purpose or use other than to circumvent a technological measure that effectively controls access to a work protected under this title; or
            3.  (C) is marketed by that person or another acting in concert with that person with that person’s knowledge for use in circumventing a technological measure that effectively controls access to a work protected under this title.
        3.  As used in this subsection— 
            1.  (A) to “circumvent a technological measure” means to descramble a scrambled work, to decrypt an encrypted work, or otherwise to avoid, bypass, remove, deactivate, or impair a technological measure, without the authority of the copyright owner; and
            2.  (B) a technological measure “effectively controls access to a work” if the measure, in the ordinary course of its operation, requires the application of information, or a process or a treatment, with the authority of the copyright owner, to gain access to the work.
    6.  (b) Additional Violations.—(1) No person shall manufacture, import, offer to the public, provide, or otherwise traffic in any technology, product, service, device, component, or part thereof, that— 
        
        1.  (A) is primarily designed or produced for the purpose of circumventing protection afforded by a technological measure that effectively protects a right of a copyright owner under this title in a work or a portion thereof;
        2.  (B) has only limited commercially significant purpose or use other than to circumvent protection afforded by a technological measure that effectively protects a right of a copyright owner under this title in a work or a portion thereof; or
        3.  (C) is marketed by that person or another acting in concert with that person with that person’s knowledge for use in circumventing protection afforded by a technological measure that effectively protects a right of a copyright owner under this title in a work or a portion thereof.
        
        2.  As used in this subsection— 
            1.  (A) to “circumvent protection afforded by a technological measure” means avoiding, bypassing, removing, deactivating, or otherwise impairing a technological measure; and
            2.  (B) a technological measure “effectively protects a right of a copyright owner under this title” if the measure, in the ordinary course of its operation, prevents, restricts, or otherwise limits the exercise of a right of a copyright owner under this title.
    7.  (c) Other Rights, Etc., Not Affected.—(1) Nothing in this section shall affect rights, remedies, limitations, or defenses to copyright infringement, including fair use, under this title. 
        1.  (2) Nothing in this section shall enlarge or diminish vicarious or contributory liability for copyright infringement in connection with any technology, product, service, device, component, or part thereof.
        2.  (3) Nothing in this section shall require that the design of, or design and selection of parts and components for, a consumer electronics, telecommunications, or computing product provide for a response to any particular technological measure, so long as such part or component, or the product in which such part or component is integrated, does not otherwise fall within the prohibitions of subsection (a)(2) or (b)(1).
        3.  (4) Nothing in this section shall enlarge or diminish any rights of free speech or the press for activities using consumer electronics, telecommunications, or computing products.
    8.  (d) Exemption for Nonprofit Libraries, Archives, and Educational Institutions.—(1) A nonprofit library, archives, or educational institution which gains access to a commercially exploited copyrighted work solely in order to make a good faith determination of whether to acquire a copy of that work for the sole purpose of engaging in conduct permitted under this title shall not be in violation of subsection (a)(1)(A). A copy of a work to which access has been gained under this paragraph— 
        
        1.  (A) may not be retained longer than necessary to make such good faith determination; and
        2.  (B) may not be used for any other purpose.
        
        1.  (2) The exemption made available under paragraph (1) shall only apply with respect to a work when an identical copy of that work is not reasonably available in another form.
        2.  (3) A nonprofit library, archives, or educational institution that willfully for the purpose of commercial advantage or financial gain violates paragraph (1)— 
            1.  (A) shall, for the first offense, be subject to the civil remedies under section 1203; and
            2.  (B) shall, for repeated or subsequent offenses, in addition to the civil remedies under section 1203, forfeit the exemption provided under paragraph (1).
        3.  (4) This subsection may not be used as a defense to a claim under subsection (a)(2) or (b), nor may this subsection permit a nonprofit library, archives, or educational institution to manufacture, import, offer to the public, provide, or otherwise traffic in any technology, product, service, component, or part thereof, which circumvents a technological measure.
        4.  (5) In order for a library or archives to qualify for the exemption under this subsection, the collections of that library or archives shall be— 
            1.  (A) open to the public; or
            2.  (B) available not only to researchers affiliated with the library or archives or with the institution of which it is a part, but also to other persons doing research in a specialized field.
    9.  (e) Law Enforcement, Intelligence, and Other Government Activities.—This section does not prohibit any lawfully authorized investigative, protective, information security, or intelligence activity of an officer, agent, or employee of the United States, a State, or a political subdivision of a State, or a person acting pursuant to a contract with the United States, a State, or a political subdivision of a State. For purposes of this subsection, the term “information security” means activities carried out in order to identify and address the vulnerabilities of a government computer, computer system, or computer network. (f) Reverse Engineering.—(1) Notwithstanding the provisions of subsection (a)(1)(A), a person who has lawfully obtained the right to use a copy of a computer program may circumvent a technological measure that effectively controls access to a particular portion of that program for the sole purpose of identifying and analyzing those elements of the program that are necessary to achieve interoperability of an independently created computer program with other programs, and that have not previously been readily available to the person engaging in the circumvention, to the extent any such acts of identification and analysis do not constitute infringement under this title. 
        1.  (2) Notwithstanding the provisions of subsections (a)(2) and (b), a person may develop and employ technological means to circumvent a technological measure, or to circumvent protection afforded by a technological measure, in order to enable the identification and analysis under paragraph (1), or for the purpose of enabling interoperability of an independently created computer program with other programs, if such means are necessary to achieve such interoperability, to the extent that doing so does not constitute infringement under this title.
        2.  (3) The information acquired through the acts permitted under paragraph (1), and the means permitted under paragraph (2), may be made available to others if the person referred to in paragraph (1) or (2), as the case may be, provides such information or means solely for the purpose of enabling interoperability of an independently created computer program with other programs, and to the extent that doing so does not constitute infringement under this title or violate applicable law other than this section.
        3.  (4) For purposes of this subsection, the term “interoperability” means the ability of computer programs to exchange information, and of such programs mutually to use the information which has been exchanged.
    10.  (g) Encryption Research.— 
         1.  Definitions.—For purposes of this subsection— 
             1.  (A) the term “encryption research” means activities necessary to identify and analyze flaws and vulnerabilities of encryption technologies applied to copyrighted works, if these activities are conducted to advance the state of knowledge in the field of encryption technology or to assist in the development of encryption products; and
             2.  (B) the term “encryption technology” means the scrambling and descrambling of information using mathematical formulas or algorithms.
         2.  Permissible acts of encryption research.—Notwithstanding the provisions of subsection (a)(1)(A), it is not a violation of that subsection for a person to circumvent a technological measure as applied to a copy, phonorecord, performance, or display of a published work in the course of an act of good faith encryption research if— 
             1.  (A) the person lawfully obtained the encrypted copy, phonorecord, performance, or display of the published work;
             2.  (B) such act is necessary to conduct such encryption research;
             3.  (C) the person made a good faith effort to obtain authorization before the circumvention; and
             4.  (D) such act does not constitute infringement under this title or a violation of applicable law other than this section, including section 1030 of title 18 and those provisions of title 18 amended by the Computer Fraud and Abuse Act of 1986.
         3.  Factors in determining exemption.—In determining whether a person qualifies for the exemption under paragraph (2), the factors to be considered shall include— 
             1.  (A) whether the information derived from the encryption research was disseminated, and if so, whether it was disseminated in a manner reasonably calculated to advance the state of knowledge or development of encryption technology, versus whether it was disseminated in a manner that facilitates infringement under this title or a violation of applicable law other than this section, including a violation of privacy or breach of security;
             2.  (B) whether the person is engaged in a legitimate course of study, is employed, or is appropriately trained or experienced, in the field of encryption technology; and
             3.  (C) whether the person provides the copyright owner of the work to which the technological measure is applied with notice of the findings and documentation of the research, and the time when such notice is provided.
         4.  Use of technological means for research activities.—Notwithstanding the provisions of subsection (a)(2), it is not a violation of that subsection for a person to— 
             1.  (A) develop and employ technological means to circumvent a technological measure for the sole purpose of that person performing the acts of good faith encryption research described in paragraph (2); and
             2.  (B) provide the technological means to another person with whom he or she is working collaboratively for the purpose of conducting the acts of good faith encryption research described in paragraph (2) or for the purpose of having that other person verify his or her acts of good faith encryption research described in paragraph (2).
         5.  Report to Congress.—Not later than 1 year after the date of the enactment of this chapter, the Register of Copyrights and the Assistant Secretary for Communications and Information of the Department of Commerce shall jointly report to the Congress on the effect this subsection has had on— 
             1.  (A) encryption research and the development of encryption technology;
             2.  (B) the adequacy and effectiveness of technological measures designed to protect copyrighted works; and
             3.  (C) protection of copyright owners against the unauthorized access to their encrypted copyrighted works.
    
    The report shall include legislative recommendations, if any.
    
    1.  (h) Exceptions Regarding Minors.—In applying subsection (a) to a component or part, the court may consider the necessity for its intended and actual incorporation in a technology, product, service, or device, which— 
        1.  (4) does not itself violate the provisions of this title; and
        2.  (5) has the sole purpose to prevent the access of minors to material on the Internet.
    2.  (i) Protection of Personally Identifying Information.— 
        1.  (1) Circumvention permitted.—Notwithstanding the provisions of subsection (a)(1)(A), it is not a violation of that subsection for a person to circumvent a technological measure that effectively controls access to a work protected under this title, if— 
            1.  (A) the technological measure, or the work it protects, contains the capability of collecting or disseminating personally identifying information reflecting the online activities of a natural person who seeks to gain access to the work protected;
            2.  (B) in the normal course of its operation, the technological measure, or the work it protects, collects or disseminates personally identifying information about the person who seeks to gain access to the work protected, without providing conspicuous notice of such collection or dissemination to such person, and without providing such person with the capability to prevent or restrict such collection or dissemination;
            3.  (C) the act of circumvention has the sole effect of identifying and disabling the capability described in subparagraph (A), and has no other effect on the ability of any person to gain access to any work; and
            4.  (D) the act of circumvention is carried out solely for the purpose of preventing the collection or dissemination of personally identifying information about a natural person who seeks to gain access to the work protected, and is not in violation of any other law.
        2.  (2) Inapplicability to certain technological measures.—
    
    This subsection does not apply to a technological measure, or a work it protects, that does not collect or disseminate personally identifying information and that is disclosed to a user as not having or using such capability.
    
    1.  (j) Security Testing.— 
        1.  (6) Definition.—For purposes of this subsection, the term “security testing” means accessing a computer, computer system, or computer network, solely for the purpose of good faith testing, investigating, or correcting, a security flaw or vulnerability, with the authorization of the owner or operator of such computer, computer system, or computer network.
        2.  (7) Permissible acts of security testing.—Notwithstanding the provisions of subsection (a)(1)(A), it is not a violation of that subsection for a person to engage in an act of security testing, if such act does not constitute infringement under this title or a violation of applicable law other than this section, including section 1030 of title 18 and those provisions of title 18 amended by the Computer Fraud and Abuse Act of 1986.
        3.  (8) Factors in determining exemption.—In determining whether a person qualifies for the exemption under paragraph (2), the factors to be considered shall include— 
            1.  (A) whether the information derived from the security testing was used solely to promote the security of the owner or operator of such computer, computer system or computer network, or shared directly with the developer of such computer, computer system, or computer network; and
            2.  (B) whether the information derived from the security testing was used or maintained in a manner that does not facilitate infringement under this title or a violation of applicable law other than this section, including a violation of privacy or breach of security.
        4.  (9) Use of technological means for security testing.—Notwithstanding the provisions of subsection (a)(2), it is not a violation of that subsection for a person to develop, produce, distribute or employ technological means for the sole purpose of performing the acts of security testing described in subsection (2), provided such technological means does not otherwise violate section (a)(2).
    2.  (k) Certain Analog Devices and Certain Technological Measures.— 
        1.  Certain analog devices.— 
            1.  (A) Effective 18 months after the date of the enactment of this chapter, no person shall manufacture, import, offer to the public, provide or otherwise traffic in any— 
                1.  (ii) VHS format analog video cassette recorder unless such recorder conforms to the automatic gain control copy control technology;
                2.  (iii) 8mm format analog video cassette camcorder unless such camcorder conforms to the automatic gain control technology;
                3.  (iv) Beta format analog video cassette recorder, unless such recorder conforms to the automatic gain control copy control technology, except that this requirement shall not apply until there are 1,000 Beta format analog video cassette recorders sold in the United States in any one calendar year after the date of the enactment of this chapter;
                4.  (v) 8mm format analog video cassette recorder that is not an analog video cassette camcorder, unless such recorder conforms to the automatic gain control copy control technology, except that this requirement shall not apply until there are 20,000 such recorders sold in the United States in any one calendar year after the date of the enactment of this chapter; or
                5.  (vi) analog video cassette recorder that records using an NTSC format video input and that is not otherwise covered under clauses (i) through (iv), unless such device conforms to the automatic gain control copy control technology.
            2.  (B) Effective on the date of the enactment of this chapter, no person shall manufacture, import, offer to the public, provide or otherwise traffic in— 
                1.  (vii) any VHS format analog video cassette recorder or any 8mm format analog video cassette recorder if the design of the model of such recorder has been modified after such date of enactment so that a model of recorder that previously conformed to the automatic gain control copy control technology no longer conforms to such technology; or
                2.  (viii) any VHS format analog video cassette recorder, or any 8mm format analog video cassette recorder that is not an 8mm analog video cassette camcorder, if the design of the model of such recorder has been modified after such date of enactment so that a model of recorder that previously conformed to the four-line colorstripe copy control technology no longer conforms to such technology.
    
    Manufacturers that have not previously manufactured or sold a VHS format analog video cassette recorder, or an 8mm format analog cassette recorder, shall be required to conform to the four-line colorstripe copy control technology in the initial model of any such recorder manufactured after the date of the enactment of this chapter, and thereafter to continue conforming to the four-line colorstripe copy control technology. For purposes of this subparagraph, an analog video cassette recorder “conforms to” the four-line colorstripe copy control technology if it records a signal that, when played back by the playback function of that recorder in the normal viewing mode, exhibits, on a reference display device, a display containing distracting visible lines through portions of the viewable picture.
    
    2.  Certain encoding restrictions.—No person shall apply the automatic gain control copy control technology or colorstripe copy control technology to prevent or limit consumer copying except such copying— 
        1.  (A) of a single transmission, or specified group of transmissions, of live events or of audiovisual works for which a member of the public has exercised choice in selecting the transmissions, including the content of the transmissions or the time of receipt of such transmissions, or both, and as to which such member is charged a separate fee for each such transmission or specified group of transmissions;
        2.  (B) from a copy of a transmission of a live event or an audiovisual work if such transmission is provided by a channel or service where payment is made by a member of the public for such channel or service in the form of a subscription fee that entitles the member of the public to receive all of the programming contained in such channel or service;
        3.  (C) from a physical medium containing one or more prerecorded audiovisual works; or
        4.  (D) from a copy of a transmission described in subparagraph (A) or from a copy made from a physical medium described in subparagraph (C).
    
    In the event that a transmission meets both the conditions set forth in subparagraph (A) and those set forth in subparagraph (B), the transmission shall be treated as a transmission described in subparagraph (A).
    
    3.  Inapplicability.—This subsection shall not— 
        1.  (A) require any analog video cassette camcorder to conform to the automatic gain control copy control technology with respect to any video signal received through a camera lens;
        2.  (B) apply to the manufacture, importation, offer for sale, provision of, or other trafficking in, any professional analog video cassette recorder; or
        3.  (C) apply to the offer for sale or provision of, or other trafficking in, any previously owned analog video cassette recorder, if such recorder was legally manufactured and sold when new and not subsequently modified in violation of paragraph (1)(B).
    4.  Definitions.—For purposes of this subsection: 
        1.  (A) An “analog video cassette recorder” means a device that records, or a device that includes a function that records, on electromagnetic tape in an analog format the electronic impulses produced by the video and audio portions of a television program, motion picture, or other form of audiovisual work.
        2.  (B) An “analog video cassette camcorder” means an analog video cassette recorder that contains a recording function that operates through a camera lens and through a video input that may be connected with a television or other video playback device.
        3.  (C) An analog video cassette recorder “conforms” to the automatic gain control copy control technology if it— 
            1.  (ix) detects one or more of the elements of such technology and does not record the motion picture or transmission protected by such technology; or
            2.  (x) records a signal that, when played back, exhibits a meaningfully distorted or degraded display.
        4.  (D) The term “professional analog video cassette recorder” means an analog video cassette recorder that is designed, manufactured, marketed, and intended for use by a person who regularly employs such a device for a lawful business or industrial use, including making, performing, displaying, distributing, or transmitting copies of motion pictures on a commercial scale.
        5.  (E) The terms “VHS format,” “8mm format,” “Beta format,” “automatic gain control copy control technology,” “colorstripe copy control technology,” “four-line version of the colorstripe copy control technology,” and “NTSC” have the meanings that are commonly understood in the consumer electronics and motion picture industries as of the date of the enactment of this chapter.
    5.  Violations.—Any violation of paragraph (1) of this subsection shall be treated as a violation of subsection (b)(1) of this section. Any violation of paragraph (2) of this subsection shall be deemed an “act of circumvention” for the purposes of section 1203(c)(3)(A) of this chapter.
    
    ## 1202\. Integrity of Copyright Management Information**³**
    
    1.  (b) False Copyright Management Information.—No person shall knowingly and with the intent to induce, enable, facilitate, or conceal infringement— 
        1.  (1) provide copyright management information that is false, or
        2.  (2) distribute or import for distribution copyright management information that is false.
    2.  (c) Removal or Alteration of Copyright Management Information.—  
        No person shall, without the authority of the copyright owner or the law— 
        1.  (1) intentionally remove or alter any copyright management information,
        2.  (2) distribute or import for distribution copyright management information knowing that the copyright management information has been removed or altered without authority of the copyright owner or the law, or
        3.  (3) distribute, import for distribution, or publicly perform works, copies of works, or phonorecords, knowing that copyright management information has been removed or altered without authority of the copyright owner or the law, knowing, or, with respect to civil remedies under section 1203, having reasonable grounds to know, that it will induce, enable, facilitate, or conceal an infringement of any right under this title.
    3.  (d) Definition.—As used in this section, the term “copyright management information” means any of the following information conveyed in connection with copies or phonorecords of a work or performances or displays of a work, including in digital form, except that such term does not include any personally identifying information about a user of a work or of a copy, phonorecord, performance, or display of a work: 
        1.  (1) The title and other information identifying the work, including the information set forth on a notice of copyright.
        2.  (2) The name of, and other identifying information about, the author of a work.
        3.  (3) The name of, and other identifying information about, the copyright owner of the work, including the information set forth in a notice of copyright.
        4.  (4) With the exception of public performances of works by radio and television broadcast stations, the name of, and other identifying information about, a performer whose performance is fixed in a work other than an audiovisual work.
        5.  (5) With the exception of public performances of works by radio and television broadcast stations, in the case of an audiovisual work, the name of, and other identifying information about, a writer, performer, or director who is credited in the audiovisual work.
        6.  (6) Terms and conditions for use of the work.
        7.  (7) Identifying numbers or symbols referring to such information or links to such information.
        8.  (8) Such other information as the Register of Copyrights may prescribe by regulation, except that the Register of Copyrights may not require the provision of any information concerning the user of a copyrighted work.
    4.  (e) Law Enforcement, Intelligence, and Other Government Activities.—This section does not prohibit any lawfully authorized investigative, protective, information security, or intelligence activity of an officer, agent, or employee of the United States, a State, or a political subdivision of a State, or a person acting pursuant to a contract with the United States, a State, or a political subdivision of a State. For purposes of this subsection, the term “information security” means activities carried out in order to identify and address the vulnerabilities of a government computer, computer system, or computer network.
    5.  (f) Limitations on Liability.— 
        1.  Analog transmissions.—In the case of an analog transmission, a person who is making transmissions in its capacity as a broadcast station, or as a cable system, or someone who provides programming to such station or system, shall not be liable for a violation of subsection (b) if— 
            1.  (A) avoiding the activity that constitutes such violation is not technically feasible or would create an undue financial hardship on such person; and
            2.  (B) such person did not intend, by engaging in such activity, to induce, enable, facilitate, or conceal infringement of a right under this title.
        2.  Digital transmissions.— 
            1.  (A) If a digital transmission standard for the placement of copyright management information for a category of works is set in a voluntary, consensus standard-setting process involving a representative cross-section of broadcast stations or cable systems and copyright owners of a category of works that are intended for public performance by such stations or systems, a person identified in paragraph (1) shall not be liable for a violation of subsection (b) with respect to the particular copyright management information addressed by such standard if— 
                1.  (xi) the placement of such information by someone other than such person is not in accordance with such standard; and
                2.  (xii) the activity that constitutes such violation is not intended to induce, enable, facilitate, or conceal infringement of a right under this title.
            2.  (B) Until a digital transmission standard has been set pursuant to subparagraph (A) with respect to the placement of copyright management information for a category of works, a person identified in paragraph (1) shall not be liable for a violation of subsection (b) with respect to such copyright management information, if the activity that constitutes such violation is not intended to induce, enable, facilitate, or conceal infringement of a right under this title, and if— 
                1.  (i) the transmission of such information by such person would result in a perceptible visual or aural degradation of the digital signal; or
                2.  (ii) the transmission of such information by such person would conflict with— 
                    1.  (I) an applicable government regulation relating to transmission of information in a digital signal;
                    2.  (II) an applicable industry-wide standard relating to the transmission of information in a digital signal that was adopted by a voluntary consensus standards body prior to the effective date of this chapter; or
                    3.  (III) an applicable industry-wide standard relating to the transmission of information in a digital signal that was adopted in a voluntary, consensus standards-setting process open to participation by a representative cross-section of broadcast stations or cable systems and copyright owners of a category of works that are intended for public performance by such stations or systems.
        3.  Definitions.—As used in this subsection— 
            1.  (A) the term “broadcast station” has the meaning given that term in section 3 of the Communications Act of 1934 (47 U .S .C . 153); and
            2.  (B) the term “cable system” has the meaning given that term in section 602 of the Communications Act of 1934 (47 U .S .C . 522).
    
    ## 1203\. Civil Remedies**⁴**
    
    1.  (g) Civil Actions.—Any person injured by a violation of section 1201 or 1202 may bring a civil action in an appropriate United States district court for such violation.
    2.  (h) Powers of the Court.—In an action brought under subsection (a), the court— 
        1.  (1) may grant temporary and permanent injunctions on such terms as it deems reasonable to prevent or restrain a violation, but in no event shall impose a prior restraint on free speech or the press protected under the 1st amendment to the Constitution;
        2.  (2) at any time while an action is pending, may order the impounding, on such terms as it deems reasonable, of any device or product that is in the custody or control of the alleged violator and that the court has reasonable cause to believe was involved in a violation;
        3.  (3) may award damages under subsection (c);
        4.  (4) in its discretion may allow the recovery of costs by or against any party other than the United States or an officer thereof;
        5.  (5) in its discretion may award reasonable attorney’s fees to the prevailing party; and
        6.  (6) may, as part of a final judgment or decree finding a violation, order the remedial modification or the destruction of any device or product involved in the violation that is in the custody or control of the violator or has been impounded under paragraph (2).
    3.  (i) Award of Damages.— 
        1.  (1) In general.—Except as otherwise provided in this title, a person committing a violation of section 1201 or 1202 is liable for either— 
            1.  (A) the actual damages and any additional profits of the violator, as provided in paragraph (2), or
            2.  (B) statutory damages, as provided in paragraph (3).
        2.  (2) Actual damages.—The court shall award to the complaining party the actual damages suffered by the party as a result of the violation, and any profits of the violator that are attributable to the violation and are not taken into account in computing the actual damages, if the complaining party elects such damages at any time before final judgment is entered.
        3.  (3) Statutory damages.—(A) At any time before final judgment is entered, a complaining party may elect to recover an award of statutory damages for each violation of section 1201 in the sum of not less than $200 or more than $2,500 per act of circumvention, device, product, component, offer, or performance of service, as the court considers just.  
            (B) At any time before final judgment is entered, a complaining party may elect to recover an award of statutory damages for each violation of section 1202 in the sum of not less than $2,500 or more than $25,000.
        4.  (4) Repeated violations.—In any case in which the injured party sustains the burden of proving, and the court finds, that a person has violated section 1201 or 1202 within three years after a final judgment was entered against the person for another such violation, the court may increase the award of damages up to triple the amount that would otherwise be awarded, as the court considers just.
        5.  (5) Innocent violations.— 
            
            1.  (A) In general.—The court in its discretion may reduce or remit the total award of damages in any case in which the violator sustains the burden of proving, and the court finds, that the violator was not aware and had no reason to believe that its acts constituted a violation.
            2.  (B) Nonprofit library, archives, educational institutions, or public broadcasting entities.—
            
            1.  (xiii) Definition.—In this subparagraph, the term “public broadcasting entity” has the meaning given such term under section 118(f).
            2.  (xiv) In general.—In the case of a nonprofit library, archives, educational institution, or public broadcasting entity, the court shall remit damages in any case in which the library, archives, educational institution, or public broadcasting entity sustains the burden of proving, and the court finds, that the library, archives, educational institution, or public broadcasting entity was not aware and had no reason to believe that its acts constituted a violation.
    
    ## 1204\. Criminal Offenses and Penalties**⁵**
    
    1.  (j) In General.—Any person who violates section 1201 or 1202 willfully and for purposes of commercial advantage or private financial gain— 
        1.  (1) shall be fined not more than $500,000 or imprisoned for not more than 5 years, or both, for the first offense; and
        2.  (2) shall be fined not more than $1,000,000 or imprisoned for not more than 10 years, or both, for any subsequent offense.
    2.  (k) Limitation for Nonprofit Library, Archives, Educational Institution, or Public Broadcasting Entity.—Subsection (a) shall not apply to a nonprofit library, archives, educational institution, or public broadcasting entity (as defined under section 118(f)).
    3.  (l) Statute of Limitations.—No criminal proceeding shall be brought under this section unless such proceeding is commenced within five years after the cause of action arose.
    
    ## 1205\. Savings Clause
    
    Nothing in this chapter abrogates, diminishes, or weakens the provisions of, nor provides any defense or element of mitigation in a criminal prosecution or civil action under, any Federal or State law that prevents the violation of the privacy of an individual in connection with the individual’s use of the Internet.
    
    # [Appendix C](#contents.xhtml#re_appendixC)
    
    ## [HIPAA §164.308 Administrative Safeguards](#contents.xhtml#re_appendixC)^([^(467)](#fn467)) 
    
     
    
     
    
    1.  (a) A covered entity or business associate must, in accordance with §164.306: 
        1.  (1) Standard: Security management process. Implement policies and procedures to prevent, detect, contain, and correct security violations.  
            (ii) Implementation specifications: 
            1.  (A) Risk analysis (Required). Conduct an accurate and thorough assessment of the potential risks and vulnerabilities to the confidentiality, integrity, and availability of electronic protected health information held by the covered entity or business associate.
            2.  (B) Risk management (Required). Implement security measures sufficient to reduce risks and vulnerabilities to a reasonable and appropriate level to comply with §164.306(a).
            3.  (C) Sanction policy (Required). Apply appropriate sanctions against workforce members who fail to comply with the security policies and procedures of the covered entity or business associate.
            4.  (D) Information system activity review (Required). Implement procedures to regularly review records of information system activity, such as audit logs, access reports, and security incident tracking reports.
        2.  (2) Standard: Assigned security responsibility. Identify the security official who is responsible for the development and implementation of the policies and procedures required by this subpart for the covered entity or business associate.
        3.  (3) Standard: Workforce security. Implement policies and procedures to ensure that all members of its workforce have appropriate access to electronic protected health information, as provided under paragraph (a)(4) of this section, and to prevent those workforce members who do not have access under paragraph (a)(4) of this section from obtaining access to electronic protected health information.  
            (ii) Implementation specifications: 
            1.  (A) Authorization and/or supervision (Addressable). Implement procedures for the authorization and/or supervision of workforce members who work with electronic protected health information or in locations where it might be accessed.
            2.  (B) Workforce clearance procedure (Addressable). Implement procedures to determine that the access of a workforce member to electronic protected health information is appropriate.
            3.  (C) Termination procedures (Addressable). Implement procedures for terminating access to electronic protected health information when the employment of, or other arrangement with, a workforce member ends or as required by determinations made as specified in paragraph (a)(3)(ii)(B) of this section.
        4.  (4) Standard: Information access management. Implement policies and procedures for authorizing access to electronic protected health information that are consistent with the applicable requirements of subpart E of this part.  
            (ii) Implementation specifications: 
            1.  (A) Isolating health care clearinghouse functions (Required). If a health care clearinghouse is part of a larger organization, the clearinghouse must implement policies and procedures that protect the electronic protected health information of the clearinghouse from unauthorized access by the larger organization.
            2.  (B) Access authorization (Addressable). Implement policies and procedures for granting access to electronic protected health information, for example, through access to a workstation, transaction, program, process, or other mechanism.
            3.  (C) Access establishment and modification (Addressable). Implement policies and procedures that, based upon the covered entity's or the business associate's access authorization policies, establish, document, review, and modify a user's right of access to a workstation, transaction, program, or process.
        5.  (5) Standard: Security awareness and training. Implement a security awareness and training program for all members of its workforce (including management).  
            (ii) Implementation specifications. Implement: 
            1.  (A) Security reminders (Addressable). Periodic security updates.
            2.  (B) Protection from malicious software (Addressable). Procedures for guarding against, detecting, and reporting malicious software.
            3.  (C) Log-in monitoring (Addressable). Procedures for monitoring log-in attempts and reporting discrepancies.
            4.  (D) Password management (Addressable). Procedures for creating, changing, and safeguarding passwords.
        6.  (6) Standard: Security incident procedures. Implement policies and procedures to address security incidents.  
            (ii) Implementation specification: Response and reporting (Required). Identify and respond to suspected or known security incidents; mitigate, to the extent practicable, harmful effects of security incidents that are known to the covered entity or business associate; and document security incidents and their outcomes.
        7.  (7) Standard: Contingency plan. Establish (and implement as needed) policies and procedures for responding to an emergency or other occurrence (for example, fire, vandalism, system failure, and natural disaster) that damages systems that contain electronic protected health information.  
            (ii) Implementation specifications: 
            1.  (A) Data backup plan (Required). Establish and implement procedures to create and maintain retrievable exact copies of electronic protected health information.
            2.  (B) Disaster recovery plan (Required). Establish (and implement as needed) procedures to restore any loss of data.
            3.  (C) Emergency mode operation plan (Required). Establish (and implement as needed) procedures to enable continuation of critical business processes for protection of the security of electronic protected health information while operating in emergency mode.
            4.  (D) Testing and revision procedures (Addressable). Implement procedures for periodic testing and revision of contingency plans.
            5.  (E) Applications and data criticality analysis (Addressable). Assess the relative criticality of specific applications and data in support of other contingency plan components.
        8.  (8) Standard: Evaluation. Perform a periodic technical and nontechnical evaluation, based initially upon the standards implemented under this rule and, subsequently, in response to environmental or operational changes affecting the security of electronic protected health information, that establishes the extent to which a covered entity's or business associate's security policies and procedures meet the requirements of this subpart.
    2.  (b) (1) Business associate contracts and other arrangements. A covered entity may permit a business associate to create, receive, maintain, or transmit electronic protected health information on the covered entity's behalf only if the covered entity obtains satisfactory assurances, in accordance with §164.314(a), that the business associate will appropriately safeguard the information. A covered entity is not required to obtain such satisfactory assurances from a business associate that is a subcontractor. 
        1.  (2) A business associate may permit a business associate that is a subcontractor to create, receive, maintain, or transmit electronic protected health information on its behalf only if the business associate obtains satisfactory assurances, in accordance with §164.314(a), that the subcontractor will appropriately safeguard the information.
        2.  (3) Implementation specifications: Written contract or other arrangement (Required). Document the satisfactory assurances required by paragraph (b)(1) or (b)(2) of this section through a written contract or other arrangement with the business associate that meets the applicable requirements of §164.314(a).
    
    ## HIPAA §164.310 Physical Safeguards^([^(468)](#fn468)) 
    
    A covered entity or business associate must, in accordance with §164.306:
    
    1.  Standard: Facility access controls. Implement policies and procedures to limit physical access to its electronic information systems and the facility or facilities in which they are housed, while ensuring that properly authorized access is allowed.  
        (2) Implementation specifications: 
        1.  (i) Contingency operations (Addressable). Establish (and implement as needed) procedures that allow facility access in support of restoration of lost data under the disaster recovery plan and emergency mode operations plan in the event of an emergency.
        2.  (ii) Facility security plan (Addressable). Implement policies and procedures to safeguard the facility and the equipment therein from unauthorized physical access, tampering, and theft.
        3.  (iii) Access control and validation procedures (Addressable). Implement procedures to control and validate a person's access to facilities based on their role or function, including visitor control, and control of access to software programs for testing and revision.
        4.  (iv) Maintenance records (Addressable). Implement policies and procedures to document repairs and modifications to the physical components of a facility which are related to security (for example, hardware, walls, doors, and locks).
    2.  Standard: Workstation use. Implement policies and procedures that specify the proper functions to be performed, the manner in which those functions are to be performed, and the physical attributes of the surroundings of a specific workstation or class of workstation that can access electronic protected health information.
    3.  Standard: Workstation security. Implement physical safeguards for all workstations that access electronic protected health information, to restrict access to authorized users.
    4.  Standard: Device and media controls. Implement policies and procedures that govern the receipt and removal of hardware and electronic media that contain electronic protected health information into and out of a facility, and the movement of these items within the facility.  
        (2) Implementation specifications: 
        1.  (i) Disposal (Required). Implement policies and procedures to address the final disposition of electronic protected health information, and/or the hardware or electronic media on which it is stored.
        2.  (ii) Media re-use (Required). Implement procedures for removal of electronic protected health information from electronic media before the media are made available for re-use.
        3.  (iii) Accountability (Addressable). Maintain a record of the movements of hardware and electronic media and any person responsible therefore.
        4.  (iv) Data backup and storage (Addressable). Create a retrievable, exact copy of electronic protected health information, when needed, before movement of equipment.
    
    ## HIPAA §164.312 Technical Safeguards^([^(469)](#fn469)) 
    
    A covered entity or business associate must, in accordance with §164.306:
    
    1.  Standard: Access control. Implement technical policies and procedures for electronic information systems that maintain electronic protected health information to allow access only to those persons or software programs that have been granted access rights as specified in §164.308(a)(4).
    2.  Implementation specifications: 
        1.  (i) Unique user identification (Required). Assign a unique name and/or number for identifying and tracking user identity.
        2.  (ii) Emergency access procedure (Required). Establish (and implement as needed) procedures for obtaining necessary electronic protected health information during an emergency.
        3.  (iii) Automatic logoff (Addressable). Implement electronic procedures that terminate an electronic session after a predetermined time of inactivity.
        4.  (iv) Encryption and decryption (Addressable). Implement a mechanism to encrypt and decrypt electronic protected health information.
    3.  Standard: Audit controls. Implement hardware, software, and/or procedural mechanisms that record and examine activity in information systems that contain or use electronic protected health information.
    4.  Standard: Integrity. Implement policies and procedures to protect electronic protected health information from improper alteration or destruction.  
        (2) Implementation specification: Mechanism to authenticate electronic protected health information (Addressable). Implement electronic mechanisms to corroborate that electronic protected health information has not been altered or destroyed in an unauthorized manner.
    5.  Standard: Person or entity authentication. Implement procedures to verify that a person or entity seeking access to electronic protected health information is the one claimed.
    6.  Standard: Transmission security. Implement technical security measures to guard against unauthorized access to electronic protected health information that is being transmitted over an electronic communications network.  
        (2) Implementation specifications: 
        1.  (i) Integrity controls (Addressable). Implement security measures to ensure that electronically transmitted electronic protected health information is not improperly modified without detection until disposed of.
        2.  (ii) Encryption (Addressable). Implement a mechanism to encrypt electronic protected health information whenever deemed appropriate.
    
    ## HIPAA §164.314 Organizational Requirements^([^(470)](#fn470)) 
    
    1.  Standard: Business associate contracts or other arrangements. The contract or other arrangement required by §164.308(b)(3) must meet the requirements of paragraph (a)(2)(i), (a)(2)(ii), or (a)(2)(iii) of this section, as applicable.  
        (2) Implementation specifications (Required). 
        1.  (i) Business associate contracts. The contract must provide that the business associate will-- 
            1.  (A) Comply with the applicable requirements of this subpart;
            2.  (B) In accordance with §164.308(b)(2), ensure that any subcontractors that create, receive, maintain, or transmit electronic protected health information on behalf of the business associate agree to comply with the applicable requirements of this subpart by entering into a contract or other arrangement that complies with this section; and
            3.  (C) Report to the covered entity any security incident of which it becomes aware, including breaches of unsecured protected health information as required by § 164.410.
        2.  (ii) Other arrangements. The covered entity is in compliance with paragraph (a)(1) of this section if it has another arrangement in place that meets the requirements of §164.504(e)(3).
        3.  (iii) Business associate contracts with subcontractors. The requirements of paragraphs (a)(2)(i) and (a)(2)(ii) of this section apply to the contract or other arrangement between a business associate and a subcontractor required by §164.308(b)(4) in the same manner as such requirements apply to contracts or other arrangements between a covered entity and business associate.
    2.  Standard: Requirements for group health plans. Except when the only electronic protected health information disclosed to a plan sponsor is disclosed pursuant to §164.504(f)(1)(ii) or (iii), or as authorized under §164.508, a group health plan must ensure that its plan documents provide that the plan sponsor will reasonably and appropriately safeguard electronic protected health information created, received, maintained, or transmitted to or by the plan sponsor on behalf of the group health plan.  
        (2) Implementation specifications (Required). The plan documents of the group health plan must be amended to incorporate provisions to require the plan sponsor to— 
        1.  (i) Implement administrative, physical, and technical safeguards that reasonably and appropriately protect the confidentiality, integrity, and availability of the electronic protected health information that it creates, receives, maintains, or transmits on behalf of the group health plan;
        2.  (ii) Ensure that the adequate separation required by §164.504(f)(2)(iii) is supported by reasonable and appropriate security measures;
        3.  (iii) Ensure that any agent to whom it provides this information agrees to implement reasonable and appropriate security measures to protect the information; and
        4.  (iv) Report to the group health plan any security incident of which it becomes aware.
    
    # [Appendix D](#contents.xhtml#re_appendixD)
    
    Sec. 13410. Improved Enforcement^([^(471)](#fn471))
    
    1.  (a) IN GENERAL.—
    2.  (1) NONCOMPLIANCE DUE TO WILLFUL NEGLECT.—Section 1176 of the Social Security Act (42 U.S.C. 1320d–5) is amended— 
        1.  (A) in subsection (b)(1), by striking “the act constitutes an offense punishable under section 1177” and inserting “a penalty has been imposed under section 1177 with respect to such act”; and
        2.  (B) by adding at the end the following new subsection:
        3.  (C) “(c) NONCOMPLIANCE DUE TO WILLFUL NEGLECT.— 
            1.  (1) IN GENERAL.—A violation of a provision of this part due to willful neglect is a violation for which the Secretary is required to impose a penalty under subsection (a)(1).
            2.  (2) REQUIRED INVESTIGATION.—For purposes of paragraph (1), the Secretary shall formally investigate any complaint of a violation of a provision of this part if a preliminary investigation of the facts of the complaint indicate such a possible violation due to willful neglect.”
        4.  (2) ENFORCEMENT UNDER SOCIAL SECURITY ACT.—Any violation by a covered entity under thus subtitle is subject to enforcement and penalties under section 1176 and 1177 of the Social Security Act.
    3.  (b) EFFECTIVE DATE; REGULATIONS.— 
        1.  (1) The amendments made by subsection (a) shall apply to penalties imposed on or after the date that is 24 months after the date of the enactment of this title.
        2.  (2) Not later than 18 months after the date of the enactment of this title, the Secretary of Health and Human Services shall promulgate regulations to implement such amendments.
    4.  (c) DISTRIBUTION OF CERTAIN CIVIL MONETARY PENALTIES COLLECTED.— 
        1.  (1) IN GENERAL.— Subject to the regulation promulgated pursuant to paragraph (3), any civil monetary penalty or monetary settlement collected with respect to an offense punishable under this subtitle or section 1176 of the Social Security Act (42 U.S.C. 1320d–5) insofar as such section relates to privacy or security shall be transferred to the Office for Civil Rights of the Department of Health and Human Services to be used for purposes of enforcing the provisions of this subtitle and subparts C and E of part 164 of title 45, Code of Federal Regulations, as such provisions are in effect as of the date of enactment of this Act.
        2.  (2) GAO REPORT.— Not later than 18 months after the date of the enactment of this title, the Comptroller General shall submit to the Secretary a report including recommendations for a methodology under which an individual who is harmed by an act that constitutes an offense referred to in paragraph (1) may receive a percentage of any civil monetary penalty or monetary settlement collected with respect to such offense.
        3.  (3) ESTABLISHMENT OF METHODOLOGY TO DISTRIBUTE PERCENTAGE OF CMPS COLLECTED TO HARMED INDIVIDUALS.— Not later than 3 years after the date of the enactment of this title, the Secretary shall establish by regulation and based on the recommendations submitted under paragraph (2), a methodology under which an individual who is harmed by an act that constitutes an offense referred to in paragraph (1) may receive a percentage of any civil monetary penalty or monetary settlement collected with respect to such offense.
        4.  (4) APPLICATION OF METHODOLOGY.—The methodology under paragraph (3) shall be applied with respect to civil monetary penalties or monetary settlements imposed on or after the effective date of the regulation.
    5.  (d) TIERED INCREASE IN AMOUNT OF CIVIL MONETARY PENALTIES.— 
        1.  (1) IN GENERAL.—Section 1176(a)(1) of the Social Security Act (42 U.S.C. 1320d–5(a)(1)) is amended by striking “who violates a provision of this part a penalty of not more than” and all that follows and inserting the following: “who violates a provision of this part—  
            “(A) in the case of a violation of such provision in which it is established that the person did not know (and by exercising reasonable diligence would not have known) that such person violated such provision, a penalty for each such violation of an amount that is at least the amount described in paragraph (3)(A) but not to exceed the amount described in paragraph (3)(D);  
            “(B) in the case of a violation of such provision in which it is established that the violation was due to reasonable cause and not to willful neglect, a penalty for each such violation of an amount that is at least the amount described in paragraph (3)(B) but not to exceed the amount described in paragraph (3)(D); and  
            “(C) in the case of a violation of such provision in which it is established that the violation was due to willful neglect— 
            1.  (i) if the violation is corrected as described in subsection (b)(3)(A), a penalty in an amount that is at least the amount described in paragraph (3)(C) but not to exceed the amount described in paragraph (3)(D); and
            2.  (ii) if the violation is not corrected as described in such subsection, a penalty in an amount that is at least the amount described in paragraph (3)(D). In determining the amount of a penalty under this section for a violation, the Secretary shall base such determination on the nature and extent of the violation and the nature and extent of the harm resulting from such violation.”
        2.  (2) TIERS OF PENALTIES DESCRIBED.—Section 1176(a) of such Act (42 U.S.C. 1320d–5(a)) is further amended by adding at the end the following new paragraph:  
            “(3) TIERS OF PENALTIES DESCRIBED.—For purposes of paragraph (1), with respect to a violation by a person of a provision of this part— 
            1.  (A) the amount described in this subparagraph is $100 for each such violation, except that the total amount imposed on the person for all such violations of an identical requirement or prohibition during a calendar year may not exceed $25,000;
            2.  (B) the amount described in this subparagraph is $1,000 for each such violation, except that the total amount imposed on the person for all such violations of an identical requirement or prohibition during a calendar year may not exceed $100,000;
            3.  (C) the amount described in this subparagraph is $10,000 for each such violation, except that the total amount imposed on the person for all such violations of an identical requirement or prohibition during a calendar year may not exceed $250,000; and
            4.  (D) the amount described in this subparagraph is $50,000 for each such violation, except that the total amount imposed on the person for all such violations of an identical requirement or prohibition during a calendar year may not exceed $1,500,000.”
        3.  (3) CONFORMING AMENDMENTS.—Section 1176(b) of such Act (42 U.S.C. 1320d–5(b)) is amended—(A) by striking paragraph (2) and redesignating paragraphs (3) and (4) as paragraphs (2) and (3), respectively; and (B) in paragraph (2), as so redesignated—(i) in subparagraph (A), by striking “in subparagraph (B), a penalty may not be imposed under subsection (a) if” and all that follows through “the failure to comply is corrected” and inserting “in subparagraph (B) or subsection (a)(1)(C), a penalty may not be imposed under subsection (a) if the failure to comply is corrected”; and (ii) in subparagraph (B), by striking “(A)(ii)” and inserting “(A)” each place it appears.
        4.  (4) EFFECTIVE DATE.—The amendments made by this subsection shall apply to violations occurring after the date of the enactment of this title.
    6.  (e) ENFORCEMENT THROUGH STATE ATTORNEYS GENERAL.— 
        1.  (1) IN GENERAL.—Section 1176 of the Social Security Act (42 U.S.C. 1320d–5) is amended by adding at the end the following new subsection:  
            “(d) ENFORCEMENT BY STATE ATTORNEYS GENERAL.— 
            
            1.  a. “(1) CIVIL ACTION.—Except as provided in subsection (b), in any case in which the attorney general of a State has reason to believe that an interest of one or more of the residents of that State has been or is threatened or adversely affected by any person who violates a provision of this part, the attorney general of the State, as parens patriae, may bring a civil action on behalf of such residents of the State in a district court of the United States of appropriate jurisdiction—
            
            1.  (A) to enjoin further such violation by the defendant; or
            2.  (B) to obtain damages on behalf of such residents of the State, in an amount equal to the amount determined under paragraph (2).
            
              
            “(2) STATUTORY DAMAGES.— 
            
            1.  a. “(A) IN GENERAL.—For purposes of paragraph (1)(B), the amount determined under this paragraph is the amount calculated by multiplying the number of violations by up to $100. For purposes of the preceding sentence, in the case of a continuing violation, the number of violations shall be determined consistent with the HIPAA privacy regulations (as defined in section 1180(b)(3)) for violations of subsection (a).
            2.  b. “(B) LIMITATION.—The total amount of damages imposed on the person for all violations of an identical requirement or prohibition during a calendar year may not exceed $25,000.
            3.  c. “(C) REDUCTION OF DAMAGES.—In assessing damages under subparagraph (A), the court may consider the factors the Secretary may consider in determining the amount of a civil money penalty under subsection (a) under the HIPAA privacy regulations.
            4.  d. “(3) ATTORNEY FEES.—In the case of any successful action under paragraph (1), the court, in its discretion, may award the costs of the action and reasonable attorney fees to the State.
            5.  e. “(4) NOTICE TO SECRETARY.—The State shall serve prior written notice of any action under paragraph (1) upon the Secretary and provide the Secretary with a copy of its complaint, except in any case in which such prior notice is not feasible, in which case the State shall serve such notice immediately upon instituting such action. The Secretary shall have the right—
            
            1.  (A) to intervene in the action;
            2.  (B) upon so intervening, to be heard on all matters arising therein; and
            3.  (C) to file petitions for appeal.
            
              
            “(5) CONSTRUCTION.—For purposes of bringing any civil action under paragraph (1), nothing in this section shall be construed to prevent an attorney general of a State from exercising the powers conferred on the attorney general by the laws of that State.  
            “(6) VENUE; SERVICE OF PROCESS.— 
            
            1.  (A) VENUE.—Any action brought under paragraph (1) may be brought in the district court of the United States that meets applicable requirements relating to venue under section 1391 of title 28, United States Code.
            2.  (B) SERVICE OF PROCESS.—In an action brought under paragraph (1), process may be served in any district in which the defendant— 
                1.  (i) is an inhabitant; or”(ii) maintains a physical place of business.
            
              
            “(7) LIMITATION ON STATE ACTION WHILE FEDERAL ACTION IS PENDING.—If the Secretary has instituted an action against a person under subsection (a) with respect to a specific violation of this part, no State attorney general may bring an action under this subsection against the person with respect to such violation during the pendency of that action.  
            “(8) APPLICATION OF CMP STATUTE OF LIMITATION.—A civil action may not be instituted with respect to a violation of this part unless an action to impose a civil money penalty may be instituted under subsection (a) with respect to such violation consistent with the second sentence of section 1128A(c)(1).” 
            1.  (1) CONFORMING AMENDMENTS.—Subsection (b) of such section, as amended by subsection (d)(3), is amended—  
                (A) in paragraph (1), by striking “A penalty may not be imposed under subsection (a)” and inserting “No penalty may be imposed under subsection (a) and no damages obtained under subsection (d)”;  
                (B) in paragraph (2)(A)— 
                
                1.  (i) after “subsection (a)(1)(C),”, by striking “a penalty may not be imposed under subsection (a)” and inserting “no penalty may be imposed under subsection (a) and no damages obtained under subsection (d)”; and
                2.  (ii) in clause (ii), by inserting “or damages” after “the penalty”;
                
                  
                (C) in paragraph (2)(B)(i), by striking “The period” and inserting “With respect to the imposition of a penalty by the Secretary under subsection (a), the period”; and (D) in paragraph (3), by inserting “and any damages under subsection (d)” after “any penalty under subsection (a).”
            2.  (2) EFFECTIVE DATE.—The amendments made by this subsection shall apply to violations occurring after the date of the enactment of this Act.
    7.  (f) ALLOWING CONTINUED USE OF CORRECTIVE ACTION.—Such section is further amended by adding at the end the following new subsection: “(e) ALLOWING CONTINUED USE OF CORRECTIVE ACTION.—Nothing in this section shall be construed as preventing the Office for Civil Rights of the Department of Health and Human Services from continuing, in its discretion, to use corrective action without a penalty in cases where the person did not know (and by exercising reasonable diligence would not have known) of the violation involved.”
    
    # [Appendix E](#contents.xhtml#re_appendixE)
    
    ## [15 U.S.C.](#contents.xhtml#re_appendixE)
    
    Title 15 – COMMERCE AND TRADE
    
    [CHAPTER 2](#c2.xhtml#c2) – FEDERAL TRADE COMMISSION; PROMOTION OF EXPORT TRADE AND PREVENTION OF UNFAIR METHODS OF COMPETITION
    
    SUBCHAPTER I – FEDERAL TRADE COMMISSION
    
    Sec. 45 – Unfair methods of competition unlawful; prevention by Commission
    
    From the U.S. Government Publishing Office, [www.gpo.gov](http://www.gpo.gov)
    
    §45. Unfair methods of competition unlawful; prevention by Commission^([^(472)](#fn472))
    
    1.  (a) **Declaration of unlawfulness; power to prohibit unfair practices; inapplicability to foreign trade** 
        
        1.  (1) Unfair methods of competition in or affecting commerce, and unfair or deceptive acts or practices in or affecting commerce, are hereby declared unlawful.
        2.  (2) The Commission is hereby empowered and directed to prevent persons, partnerships, or corporations, except banks, savings and loan institutions described in section 57a(f)(3) of this title, Federal credit unions described in section 57a(f)(4) of this title, common carriers subject to the Acts to regulate commerce, air carriers and foreign air carriers subject to part A of subtitle VII of title 49, and persons, partnerships, or corporations insofar as they are subject to the Packers and Stockyards Act, 1921, as amended \[7 U.S.C. 181 et seq.\], except as provided in section 406(b) of said Act \[7 U.S.C. 227(b)\], from using unfair methods of competition in or affecting commerce and unfair or deceptive acts or practices in or affecting commerce.
        3.  (3) This subsection shall not apply to unfair methods of competition involving commerce with foreign nations (other than import commerce) unless— 
            1.  (A) such methods of competition have a direct, substantial, and reasonably foreseeable effect— 
                1.  (i) on commerce which is not commerce with foreign nations, or on import commerce with foreign nations; or
                2.  (ii) on export commerce with foreign nations, of a person engaged in such commerce in the United States; and
            2.  (B) such effect gives rise to a claim under the provisions of this subsection, other than this paragraph.
        
          
        If this subsection applies to such methods of competition only because of the operation of subparagraph (A)(ii), this subsection shall apply to such conduct only for injury to export business in the United States.
    2.  (4)(A) For purposes of subsection (a), the term “unfair or deceptive acts or practices” includes such acts or practices involving foreign commerce that— 
        
        1.  (i) cause or are likely to cause reasonably foreseeable injury within the United States; or
        2.  (ii) involve material conduct occurring within the United States.
        
          
        (B) All remedies available to the Commission with respect to unfair and deceptive acts or practices shall be available for acts and practices described in this paragraph, including restitution to domestic or foreign victims.
    3.  (b) **Proceeding by Commission; modifying and setting aside orders**  
        Whenever the Commission shall have reason to believe that any such person, partnership, or corporation has been or is using any unfair method of competition or unfair or deceptive act or practice in or affecting commerce, and if it shall appear to the Commission that a proceeding by it in respect thereof would be to the interest of the public, it shall issue and serve upon such person, partnership, or corporation a complaint stating its charges in that respect and containing a notice of a hearing upon a day and at a place therein fixed at least thirty days after the service of said complaint. The person, partnership, or corporation so complained of shall have the right to appear at the place and time so fixed and show cause why an order should not be entered by the Commission requiring such person, partnership, or corporation to cease and desist from the violation of the law so charged in said complaint. Any person, partnership, or corporation may make application, and upon good cause shown may be allowed by the Commission to intervene and appear in said proceeding by counsel or in person. The testimony in any such proceeding shall be reduced to writing and filed in the office of the Commission. If upon such hearing the Commission shall be of the opinion that the method of competition or the act or practice in question is prohibited by this subchapter, it shall make a report in writing in which it shall state its findings as to the facts and shall issue and cause to be served on such person, partnership, or corporation an order requiring such person, partnership, or corporation to cease and desist from using such method of competition or such act or practice. Until the expiration of the time allowed for filing a petition for review, if no such petition has been duly filed within such time, or, if a petition for review has been filed within such time then until the record in the proceeding has been filed in a court of appeals of the United States, as hereinafter provided, the Commission may at any time, upon such notice and in such manner as it shall deem proper, modify or set aside, in whole or in part, any report or any order made or issued by it under this section. After the expiration of the time allowed for filing a petition for review, if no such petition has been duly filed within such time, the Commission may at any time, after notice and opportunity for hearing, reopen and alter, modify, or set aside, in whole or in part any report or order made or issued by it under this section, whenever in the opinion of the Commission conditions of fact or of law have so changed as to require such action or if the public interest shall so require, except that (1) the said person, partnership, or corporation may, within sixty days after service upon him or it of said report or order entered after such a reopening, obtain a review thereof in the appropriate court of appeals of the United States, in the manner provided in subsection (c) of this section; and (2) in the case of an order, the Commission shall reopen any such order to consider whether such order (including any affirmative relief provision contained in such order) should be altered, modified, or set aside, in whole or in part, if the person, partnership, or corporation involved files a request with the Commission which makes a satisfactory showing that changed conditions of law or fact require such order to be altered, modified, or set aside, in whole or in part. The Commission shall determine whether to alter, modify, or set aside any order of the Commission in response to a request made by a person, partnership, or corporation under paragraph ¹  (2) not later than 120 days after the date of the filing of such request.
    4.  (c) **Review of order; rehearing**  
        Any person, partnership, or corporation required by an order of the Commission to cease and desist from using any method of competition or act or practice may obtain a review of such order in the court of appeals of the United States, within any circuit where the method of competition or the act or practice in question was used or where such person, partnership, or corporation resides or carries on business, by filing in the court, within sixty days from the date of the service of such order, a written petition praying that the order of the Commission be set aside. A copy of such petition shall be forthwith transmitted by the clerk of the court to the Commission, and thereupon the Commission shall file in the court the record in the proceeding, as provided in section 2112 of title 28. Upon such filing of the petition the court shall have jurisdiction of the proceeding and of the question determined therein concurrently with the Commission until the filing of the record and shall have power to make and enter a decree affirming, modifying, or setting aside the order of the Commission, and enforcing the same to the extent that such order is affirmed and to issue such writs as are ancillary to its jurisdiction or are necessary in its judgement to prevent injury to the public or to competitors pendente lite. The findings of the Commission as to the facts, if supported by evidence, shall be conclusive. To the extent that the order of the Commission is affirmed, the court shall thereupon issue its own order commanding obedience to the terms of such order of the Commission. If either party shall apply to the court for leave to adduce additional evidence, and shall show to the satisfaction of the court that such additional evidence is material and that there were reasonable grounds for the failure to adduce such evidence in the proceeding before the Commission, the court may order such additional evidence to be taken before the Commission and to be adduced upon the hearing in such manner and upon such terms and conditions as to the court may seem proper. The Commission may modify its findings as to the facts, or make new findings, by reason of the additional evidence so taken, and it shall file such modified or new findings, which, if supported by evidence, shall be conclusive, and its recommendation, if any, for the modification or setting aside of its original order, with the return of such additional evidence. The judgment and decree of the court shall be final, except that the same shall be subject to review by the Supreme Court upon certiorari, as provided in section 1254 of title 28.
    5.  (d) **Jurisdiction of court**  
        Upon the filing of the record with it the jurisdiction of the court of appeals of the United States to affirm, enforce, modify, or set aside orders of the Commission shall be exclusive.
    6.  (e) **Exemption from liability**  
        No order of the Commission or judgement of court to enforce the same shall in anywise relieve or absolve any person, partnership, or corporation from any liability under the Antitrust Acts.
    7.  (f) **Service of complaints, orders and other processes; return**  
        Complaints, orders, and other processes of the Commission under this section may be served by anyone duly authorized by the Commission, either (a) by delivering a copy thereof to the person to be served, or to a member of the partnership to be served, or the president, secretary, or other executive officer or a director of the corporation to be served; or (b) by leaving a copy thereof at the residence or the principal office or place of business of such person, partnership, or corporation; or (c) by mailing a copy thereof by registered mail or by certified mail addressed to such person, partnership, or corporation at his or its residence or principal office or place of business. The verified return by the person so serving said complaint, order, or other process setting forth the manner of said service shall be proof of the same, and the return post office receipt for said complaint, order, or other process mailed by registered mail or by certified mail as aforesaid shall be proof of the service of the same.
    8.  (g) **Finality of order**  
        An order of the Commission to cease and desist shall become final— 
        1.  (1) Upon the expiration of the time allowed for filing a petition for review, if no such petition has been duly filed within such time; but the Commission may thereafter modify or set aside its order to the extent provided in the last sentence of subsection (b).
        2.  (2) Except as to any order provision subject to paragraph (4), upon the sixtieth day after such order is served, if a petition for review has been duly filed; except that any such order may be stayed, in whole or in part and subject to such conditions as may be appropriate, by— 
            1.  (A) the Commission;
            2.  (B) an appropriate court of appeals of the United States, if (i) a petition for review of such order is pending in such court, and (ii) an application for such a stay was previously submitted to the Commission and the Commission, within the 30-day period beginning on the date the application was received by the Commission, either denied the application or did not grant or deny the application; or
            3.  (C) the Supreme Court, if an applicable petition for certiorari is pending.
        3.  (3) For purposes of subsection (m)(1)(B) of this section and of section 57b(a)(2) of this title, if a petition for review of the order of the Commission has been filed— 
            1.  (A) upon the expiration of the time allowed for filing a petition for certiorari, if the order of the Commission has been affirmed or the petition for review has been dismissed by the court of appeals and no petition for certiorari has been duly filed;
            2.  (B) upon the denial of a petition for certiorari, if the order of the Commission has been affirmed or the petition for review has been dismissed by the court of appeals; or
            3.  (C) upon the expiration of 30 days from the date of issuance of a mandate of the Supreme Court directing that the order of the Commission be affirmed or the petition for review be dismissed.
        4.  (4) In the case of an order provision requiring a person, partnership, or corporation to divest itself of stock, other share capital, or assets, if a petition for review of such order of the Commission has been filed— 
            1.  (A) upon the expiration of the time allowed for filing a petition for certiorari, if the order of the Commission has been affirmed or the petition for review has been dismissed by the court of appeals and no petition for certiorari has been duly filed;
            2.  (B) upon the denial of a petition for certiorari, if the order of the Commission has been affirmed or the petition for review has been dismissed by the court of appeals; or
            3.  (C) upon the expiration of 30 days from the date of issuance of a mandate of the Supreme Court directing that the order of the Commission be affirmed or the petition for review be dismissed.
    9.  (h) **Modification or setting aside of order by Supreme Court**  
        If the Supreme Court directs that the order of the Commission be modified or set aside, the order of the Commission rendered in accordance with the mandate of the Supreme Court shall become final upon the expiration of thirty days from the time it was rendered, unless within such thirty days either party has instituted proceedings to have such order corrected to accord with the mandate, in which event the order of the Commission shall become final when so corrected.
    10.  (i) **Modification or setting aside of order by Court of Appeals**  
         If the order of the Commission is modified or set aside by the court of appeals, and if (1) the time allowed for filing a petition for certiorari has expired and no such petition has been duly filed, or (2) the petition for certiorari has been denied, or (3) the decision of the court has been affirmed by the Supreme Court, then the order of the Commission rendered in accordance with the mandate of the court of appeals shall become final on the expiration of thirty days from the time such order of the Commission was rendered, unless within such thirty days either party has instituted proceedings to have such order corrected so that it will accord with the mandate, in which event the order of the Commission shall become final when so corrected.
    11.  (j) **Rehearing upon order or remand**  
         If the Supreme Court orders a rehearing; or if the case is remanded by the court of appeals to the Commission for a rehearing, and if (1) the time allowed for filing a petition for certiorari has expired, and no such petition has been duly filed, or (2) the petition for certiorari has been denied, or (3) the decision of the court has been affirmed by the Supreme Court, then the order of the Commission rendered upon such rehearing shall become final in the same manner as though no prior order of the Commission had been rendered.
    12.  (k) **“Mandate” defined**  
         As used in this section the term “mandate”, in case a mandate has been recalled prior to the expiration of thirty days from the date of issuance thereof, means the final mandate.
    13.  (l) **Penalty for violation of order; injunctions and other appropriate equitable relief**  
         Any person, partnership, or corporation who violates an order of the Commission after it has become final, and while such order is in effect, shall forfeit and pay to the United States a civil penalty of not more than $10,000 for each violation, which shall accrue to the United States and may be recovered in a civil action brought by the Attorney General of the United States. Each separate violation of such an order shall be a separate offense, except that in a case of a violation through continuing failure to obey or neglect to obey a final order of the Commission, each day of continuance of such failure or neglect shall be deemed a separate offense. In such actions, the United States district courts are empowered to grant mandatory injunctions and such other and further equitable relief as they deem appropriate in the enforcement of such final orders of the Commission.
    14.  (m) **Civil actions for recovery of penalties for knowing violations of rules and cease and desist orders respecting unfair or deceptive acts or practices; jurisdiction; maximum amount of penalties; continuing violations; de novo determinations; compromise or settlement procedure** 
         1.  (1)(A) The Commission may commence a civil action to recover a civil penalty in a district court of the United States against any person, partnership, or corporation which violates any rule under this subchapter respecting unfair or deceptive acts or practices (other than an interpretive rule or a rule violation of which the Commission has provided is not an unfair or deceptive act or practice in violation of subsection (a)(1) of this section) with actual knowledge or knowledge fairly implied on the basis of objective circumstances that such act is unfair or deceptive and is prohibited by such rule. In such action, such person, partnership, or corporation shall be liable for a civil penalty of not more than $10,000 for each violation.  
             (B) If the Commission determines in a proceeding under subsection (b) of this section that any act or practice is unfair or deceptive, and issues a final cease and desist order, other than a consent order, with respect to such act or practice, then the Commission may commence a civil action to obtain a civil penalty in a district court of the United States against any person, partnership, or corporation which engages in such act or practice—
         2.  (1) after such cease and desist order becomes final (whether or not such person, partnership, or corporation was subject to such cease and desist order), and
         3.  (2) with actual knowledge that such act or practice is unfair or deceptive and is unlawful under subsection (a)(1) of this section.  
             In such action, such person, partnership, or corporation shall be liable for a civil penalty of not more than $10,000 for each violation.  
             (C) In the case of a violation through continuing failure to comply with a rule or with subsection (a)(1) of this section, each day of continuance of such failure shall be treated as a separate violation, for purposes of subparagraphs (A) and (B). In determining the amount of such a civil penalty, the court shall take into account the degree of culpability, any history of prior such conduct, ability to pay, effect on ability to continue to do business, and such other matters as justice may require. 
             1.  (2) If the cease and desist order establishing that the act or practice is unfair or deceptive was not issued against the defendant in a civil penalty action under paragraph (1)(B) the issues of fact in such action against such defendant shall be tried de novo. Upon request of any party to such an action against such defendant, the court shall also review the determination of law made by the Commission in the proceeding under subsection (b) of this section that the act or practice which was the subject of such proceeding constituted an unfair or deceptive act or practice in violation of subsection (a) of this section.
             2.  (3) The Commission may compromise or settle any action for a civil penalty if such compromise or settlement is accompanied by a public statement of its reasons and is approved by the court.
    15.  (n) **Standard of proof; public policy considerations**  
         The Commission shall have no authority under this section or section 57a of this title to declare unlawful an act or practice on the grounds that such act or practice is unfair unless the act or practice causes or is likely to cause substantial injury to consumers which is not reasonably avoidable by consumers themselves and not outweighed by countervailing benefits to consumers or to competition. In determining whether an act or practice is unfair, the Commission may consider established public policies as evidence to be considered with all other evidence. Such public policy considerations may not serve as a primary basis for such determination.
    
    # [Appendix F](#contents.xhtml#re_appendixF)
    
    **PART 681—IDENTITY THEFT RULES**
    
    **Appendix A to Part 681—Interagency Guidelines on Identity Theft Detection, Prevention, and Mitigation**^([^(473)](#fn473))
    
    **Alerts, Notifications or Warnings from a Consumer Reporting Agency**
    
    1.  A fraud or active duty alert is included with a consumer report.
    2.  A consumer reporting agency provides a notice of credit freeze in response to a request for a consumer report.
    3.  A consumer reporting agency provides a notice of address discrepancy, as defined in §641.1(b) of this part.
    4.  A consumer report indicates a pattern of activity that is inconsistent with the history and usual pattern of activity of an applicant or customer, such as: 
        1.  a. A recent and significant increase in the volume of inquiries;
        2.  b. An unusual number of recently established credit relationships;
        3.  c. A material change in the use of credit, especially with respect to recently established credit relationships; or
        4.  d. An account that was closed for cause or identified for abuse of account privileges by a financial institution or creditor.
    
    **Suspicious documents**
    
    5.  Documents provided for identification appear to have been altered or forged.
    6.  The photograph or physical description on the identification is not consistent with the appearance of the applicant or customer presenting the identification.
    7.  Other information on the identification is not consistent with information provided by the person opening a new covered account or customer presenting the identification.
    8.  Other information on the identification is not consistent with readily accessible information that is on file with the financial institution or creditor, such as a signature card or a recent check.
    9.  An application appears to have been altered or forged, or gives the appearance of having been destroyed and reassembled.
    
    **Suspicious personal identifying information**
    
    10.  Personal identifying information provided is inconsistent when compared against external information sources used by the financial institution or creditor. For example: 
         1.  a. The address does not match any address in the consumer report; or
         2.  b. The Social Security Number (SSN) has not been issued, or is listed on the Social Security Administration's Death Master File.
    11.  Personal identifying information provided by the customer is not consistent with other personal identifying information provided by the customer. For example, there is a lack of correlation between the SSN range and date of birth.
    12.  Personal identifying information provided is associated with known fraudulent activity as indicated by internal or third-party sources used by the financial institution or creditor. For example: 
         1.  a. The address on an application is the same as the address provided on a fraudulent application; or
         2.  b. The phone number on an application is the same as the number provided on a fraudulent application.
    13.  Personal identifying information provided is of a type commonly associated with fraudulent activity as indicated by internal or third-party sources used by the financial institution or creditor. For example: 
         1.  a. The address on an application is fictitious, a mail drop, or a prison; or
         2.  b. The phone number is invalid, or is associated with a pager or answering service.
    14.  The SSN provided is the same as that submitted by other persons opening an account or other customers.
    15.  The address or telephone number provided is the same as or similar to the address or telephone number submitted by an unusually large number of other persons opening accounts or by other customers.
    16.  The person opening the covered account or the customer fails to provide all required personal identifying information on an application or in response to notification that the application is incomplete.
    17.  Personal identifying information provided is not consistent with personal identifying information that is on file with the financial institution or creditor.
    18.  For financial institutions and creditors that use challenge questions, the person opening the covered account or the customer cannot provide authenticating information beyond that which generally would be available from a wallet or consumer report.
    
    **Unusual use of, or suspicious activity related to, the covered account**
    
    19.  Shortly following the notice of a change of address for a covered account, the institution or creditor receives a request for a new, additional, or replacement card or a cell phone, or for the addition of authorized users on the account.
    20.  A new revolving credit account is used in a manner commonly associated with known patterns of fraud. For example: 
         1.  a. The majority of available credit is used for cash advances or merchandise that is easily convertible to cash (e.g., electronics equipment or jewelry); or
         2.  b. The customer fails to make the first payment or makes an initial payment but no subsequent payments.
    21.  A covered account is used in a manner that is not consistent with established patterns of activity on the account. There is, for example: 
         1.  a. Nonpayment when there is no history of late or missed payments;
         2.  b. A material increase in the use of available credit;
         3.  c. A material change in purchasing or spending patterns;
         4.  d. A material change in electronic fund transfer patterns in connection with a deposit account; or
         5.  e. A material change in telephone call patterns in connection with a cellular phone account.
    22.  A covered account that has been inactive for a reasonably lengthy period of time is used (taking into consideration the type of account, the expected pattern of usage and other relevant factors).
    23.  Mail sent to the customer is returned repeatedly as undeliverable although transactions continue to be conducted in connection with the customer's covered account.
    24.  The financial institution or creditor is notified that the customer is not receiving paper account statements.
    25.  The financial institution or creditor is notified of unauthorized charges or transactions in connection with a customer's covered account.
    
    *Notice from Customers, Victims of Identity Theft, Law Enforcement Authorities, or Other Persons Regarding Possible Identity Theft in Connection With Covered Accounts Held by the Financial Institution or Creditor*
    
    26.  The financial institution or creditor is notified by a customer, a victim of identity theft, a law enforcement authority, or any other person that it has opened a fraudulent account for a person engaged in identity theft.
    
    # [Appendix G](#contents.xhtml#re_appendixG)
    
    **6 U.S.C.**
    
    United States Code
    
    **Title 6 – DOMESTIC SECURITY**
    
    **[CHAPTER 6](#c6.xhtml#c6) – CYBERSECURITY**
    
    **SUBCHAPTER I – CYBERSECURITY INFORMATION SHARING**
    
    Sec. 1501 – Definitions
    
    From the U.S. Government Publishing Office, [www.gpo.gov](http://www.gpo.gov)
    
    §1501. Definitions^([^(474)](#fn474))
    
    In this subchapter:
    
    1.  **Agency**
    
    The term “agency” has the meaning given the term in section 3502 of title 44.
    
    2.  **Antitrust laws**
    
    The term “antitrust laws”—
    
    1.  (A) has the meaning given the term in section 12 of title 15;
    2.  (B) includes section 45 of title 15 to the extent that section 45 of title 15 applies to unfair methods of competition; and
    3.  (C) includes any State antitrust law, but only to the extent that such law is consistent with the law referred to in subparagraph (A) or the law referred to in subparagraph (B).
    
    3.  **Appropriate federal entities**
    
    The term “appropriate Federal entities” means the following:
    
    1.  (A) The Department of Commerce.
    2.  (B) The Department of Defense.
    3.  (C) The Department of Energy.
    4.  (D) The Department of Homeland Security.
    5.  (E) The Department of Justice.
    6.  (F) The Department of the Treasury.
    7.  (G) The Office of the Director of National Intelligence.
    
    4.  **Cybersecurity purpose**
    
    The term “cybersecurity purpose” means the purpose of protecting an information system or information that is stored on, processed by, or transiting an information system from a cybersecurity threat or security vulnerability.
    
    5.  **Cybersecurity threat** 
        1.  (A) **In general**  
            Except as provided in subparagraph (B), the term “cybersecurity threat” means an action, not protected by the First Amendment to the Constitution of the United States, on or through an information system that may result in an unauthorized effort to adversely impact the security, availability, confidentiality, or integrity of an information system or information that is stored on, processed by, or transiting an information system.
        2.  (B) **Exclusion**  
            The term “cybersecurity threat” does not include any action that solely involves a violation of a consumer term of service or a consumer licensing agreement.
    
    6.  **Cyber threat indicator**
    
    The term “cyber threat indicator” means information that is necessary to describe or identify—
    
    1.  (A) malicious reconnaissance, including anomalous patterns of communications that appear to be transmitted for the purpose of gathering technical information related to a cybersecurity threat or security vulnerability;
    2.  (B) a method of defeating a security control or exploitation of a security vulnerability;
    3.  (C) a security vulnerability, including anomalous activity that appears to indicate the existence of a security vulnerability;
    4.  (D) a method of causing a user with legitimate access to an information system or information that is stored on, processed by, or transiting an information system to unwittingly enable the defeat of a security control or exploitation of a security vulnerability;
    5.  (E) malicious cyber command and control;
    6.  (F) the actual or potential harm caused by an incident, including a description of the information exfiltrated as a result of a particular cybersecurity threat;
    7.  (G) any other attribute of a cybersecurity threat, if disclosure of such attribute is not otherwise prohibited by law; or
    8.  (H) any combination thereof.
    
    7.  **Defensive measure** 
        1.  (A) **In general**  
            Except as provided in subparagraph (B), the term “defensive measure” means an action, device, procedure, signature, technique, or other measure applied to an information system or information that is stored on, processed by, or transiting an information system that detects, prevents, or mitigates a known or suspected cybersecurity threat or security vulnerability.
        2.  (B) **Exclusion**  
            The term “defensive measure” does not include a measure that destroys, renders unusable, provides unauthorized access to, or substantially harms an information system or information stored on, processed by, or transiting such information system not owned by— 
            1.  (i) the private entity operating the measure; or
            2.  (ii) another entity or Federal entity that is authorized to provide consent and has provided consent to that private entity for operation of such measure.
    
    8.  **Federal entity**
    
    The term “Federal entity” means a department or agency of the United States or any component of such department or agency.
    
    **(9) Information system**
    
    The term “information system”—
    
    1.  (A) has the meaning given the term in section 3502 of title 44; and
    2.  (B) includes industrial control systems, such as supervisory control and data acquisition systems, distributed control systems, and programmable logic controllers.
    
    10.  **Local government**
    
    The term “local government” means any borough, city, county, parish, town, township, village, or other political subdivision of a State.
    
    11.  **Malicious cyber command and control**
    
    The term “malicious cyber command and control” means a method for unauthorized remote identification of, access to, or use of, an information system or information that is stored on, processed by, or transiting an information system.
    
    12.  **Malicious reconnaissance**
    
    The term “malicious reconnaissance” means a method for actively probing or passively monitoring an information system for the purpose of discerning security vulnerabilities of the information system, if such method is associated with a known or suspected cybersecurity threat.
    
    13.  **Monitor**
    
    The term “monitor” means to acquire, identify, or scan, or to possess, information that is stored on, processed by, or transiting an information system.
    
    14.  **Non-Federal entity** 
         1.  (A) **In general**  
             Except as otherwise provided in this paragraph, the term “non-Federal entity” means any private entity, non-Federal government agency or department, or State, tribal, or local government (including a political subdivision, department, or component thereof).
         2.  (B) **Inclusions**  
             The term “non-Federal entity” includes a government agency or department of the District of Columbia, the Commonwealth of Puerto Rico, the United States Virgin Islands, Guam, American Samoa, the Northern Mariana Islands, and any other territory or possession of the United States.
         3.  (C) **Exclusion**  
             The term “non-Federal entity” does not include a foreign power as defined in section 1801 of title 50.
    15.  **Private entity** 
         1.  **(A) In general**  
             Except as otherwise provided in this paragraph, the term “private entity” means any person or private group, organization, proprietorship, partnership, trust, cooperative, corporation, or other commercial or nonprofit entity, including an officer, employee, or agent thereof.
         2.  **(B) Inclusion**  
             The term “private entity” includes a State, tribal, or local government performing utility services, such as electric, natural gas, or water services.
         3.  **(C) Exclusion**  
             The term “private entity” does not include a foreign power as defined in section 1801 of title 50.
    
    16.  **Security control**
    
    The term “security control” means the management, operational, and technical controls used to protect against an unauthorized effort to adversely affect the confidentiality, integrity, and availability of an information system or its information.
    
    17.  **Security vulnerability**
    
    The term “security vulnerability” means any attribute of hardware, software, process, or procedure that could enable or facilitate the defeat of a security control.
    
    18.  **Tribal**
    
    The term “tribal” has the meaning given the term “Indian tribe” in section 450b of title 25.
    
    (Pub. L. 114–113, div. N, title I, §102, Dec. 18, 2015, 129 Stat. 2936.)
    
    ## Short Title
    
    Pub. L. 114–113, div. N, §1(a), Dec. 18, 2015, 129 Stat. 2935, provided that: “This division \[enacting this chapter and sections 149 and 151 of this title, amending sections 131, 148, 149, and 150 of this title, section 1029 of Title 18, Crimes and Criminal Procedure, and sections 3553 and 3554 of Title 44, Public Printing and Documents, enacting provisions set out as notes under this section and sections 101, 131, and 151 of this title and section 301 of Title 5, Government Organization and Employees\] may be cited as the 'Cybersecurity Act of 2015'.”
    
    Pub. L. 114–113, div. N, title I, §101, Dec. 18, 2015, 129 Stat. 2936, provided that: “This title \[enacting this subchapter\] may be cited as the 'Cybersecurity Information Sharing Act of 2015'.”
    
    Pub. L. 114–113, div. N, title II, §221, Dec. 18, 2015, 129 Stat. 2963, provided that: “This subtitle \[subtitle B (§§221–229) of title II of div. N of Pub. L. 114–113, enacting subchapter II of this chapter and sections 149 and 151 of this title, amending sections 148, 149, and 150 of this title and sections 3553 and 3554 of Title 44, Public Printing and Documents, and enacting provisions set out as a note under section 151 of this title\] may be cited as the 'Federal Cybersecurity Enhancement Act of 2015'.”
    
    # [Appendix H](#contents.xhtml#re_appendixH)
    
    **18 U.S.C.**
    
    United States Code, 2011 Edition
    
    **Title 18 – CRIMES AND CRIMINAL PROCEDURE**
    
    **PART I – CRIMES**
    
    **CHAPTER 47 – FRAUD AND FALSE STATEMENTS**
    
    Sec. 1037 – Fraud and related activity in connection with electronic mail
    
    From the U.S. Government Publishing Office, [www.gpo.gov](http://www.gpo.gov)
    
    **§1037. Fraud and Related Activity in Connection with Electronic Mail**
    
    1.  (a) In General.—Whoever, in or affecting interstate or foreign commerce, knowingly— 
        
        1.  (1) accesses a protected computer without authorization, and intentionally initiates the transmission of multiple commercial electronic mail messages from or through such computer,
        2.  (2) uses a protected computer to relay or retransmit multiple commercial electronic mail messages, with the intent to deceive or mislead recipients, or any Internet access service, as to the origin of such messages,
        3.  (3) materially falsifies header information in multiple commercial electronic mail messages and intentionally initiates the transmission of such messages,
        4.  (4) registers, using information that materially falsifies the identity of the actual registrant, for five or more electronic mail accounts or online user accounts or two or more domain names, and intentionally initiates the transmission of multiple commercial electronic mail messages from any combination of such accounts or domain names, or
        5.  (5) falsely represents oneself to be the registrant or the legitimate successor in interest to the registrant of 5 or more Internet Protocol addresses, and intentionally initiates the transmission of multiple commercial electronic mail messages from such addresses, or conspires to do so, shall be punished as provided in subsection (b). 
            1.  (b) Penalties.—The punishment for an offense under subsection (a) is— 
                1.  (1) a fine under this title, imprisonment for not more than 5 years, or both, if— 
                    1.  (A) the offense is committed in furtherance of any felony under the laws of the United States or of any State; or
                    2.  (B) the defendant has previously been convicted under this section or section 1030, or under the law of any State for conduct involving the transmission of multiple commercial electronic mail messages or unauthorized access to a computer system;
                2.  (2) a fine under this title, imprisonment for not more than 3 years, or both, if— 
                    1.  (A) the offense is an offense under subsection (a)(1);
                    2.  (B) the offense is an offense under subsection (a)(4) and involved 20 or more falsified electronic mail or online user account registrations, or 10 or more falsified domain name registrations;
                    3.  (C) the volume of electronic mail messages transmitted in furtherance of the offense exceeded 2,500 during any 24-hour period, 25,000 during any 30-day period, or 250,000 during any 1-year period;
                    4.  (D) the offense caused loss to one or more persons aggregating $5,000 or more in value during any 1-year period;
                    5.  (E) as a result of the offense any individual committing the offense obtained anything of value aggregating $5,000 or more during any 1-year period; or
                    6.  (F) the offense was undertaken by the defendant in concert with three or more other persons with respect to whom the defendant occupied a position of organizer or leader; and
                3.  (3) a fine under this title or imprisonment for not more than 1 year, or both, in any other case.
        
        1.  (c) Forfeiture.— 
            1.  (1) In general.—The court, in imposing sentence on a person who is convicted of an offense under this section, shall order that the defendant forfeit to the United States— 
                1.  (A) any property, real or personal, constituting or traceable to gross proceeds obtained from such offense; and
                2.  (B) any equipment, software, or other technology used or intended to be used to commit or to facilitate the commission of such offense.
            2.  (2) Procedures.—The procedures set forth in section 413 of the Controlled Substances Act (21 U.S.C. 853), other than subsection (d) of that section, and in Rule 32.2 of the Federal Rules of Criminal Procedure, shall apply to all stages of a criminal forfeiture proceeding under this section.
        2.  (d) Definitions.—In this section: 
            1.  (1) Loss.—The term “loss” has the meaning given that term in section 1030(e) of this title.
            2.  (2) Materially.—For purposes of paragraphs (3) and (4) of subsection (a), header information or registration information is materially falsified if it is altered or concealed in a manner that would impair the ability of a recipient of the message, an Internet access service processing the message on behalf of a recipient, a person alleging a violation of this section, or a law enforcement agency to identify, locate, or respond to a person who initiated the electronic mail message or to investigate the alleged violation.
            3.  (3) Multiple.—The term “multiple” means more than 100 electronic mail messages during a 24-hour period, more than 1,000 electronic mail messages during a 30-day period, or more than 10,000 electronic mail messages during a 1-year period.
            4.  (4) Other terms.—Any other term has the meaning given that term by section 3 of the CAN-SPAM Act of 2003.
    
    (Added Pub. L. 108–187, §4(a)(1), Dec. 16, 2003, 117 Stat. 2703.)
    
    ## References
    
    The Federal Rules of Criminal Procedure, referred to in subsec. (c)(2), are set out in the Appendix to this title.
    
    Section 3 of the CAN-SPAM Act of 2003, referred to in subsec. (d)(4), is classified to section 7702 of Title 15, Commerce and Trade.
    
    ## Effective Date
    
    Section effective Jan. 1, 2004, see section 16 of Pub. L. 108–187, set out as a note under section 7701 of Title 15, Commerce and Trade.
    
    # [Appendix I](#contents.xhtml#re_appendixI)
    
    ## [Valuable IT and Management Certifications](#contents.xhtml#re_appendixI)
    
    1.  I. **Entry-Level IT Certifications** 
        *   Cisco Certifications^([^(475)](#fn475))
        *   Cisco Certified Technician (CCT)
        *   Cisco Certified Network Associate (CCNA)
        *   CompTIA Certifications^([^(476)](#fn476))
        *   CompTIA IT Fundamentals (ITF+)
        *   Comp TIA A+
        *   CompTIA Network+
        *   CompTIA Security+
        *   Microsoft Certifications^([^(477)](#fn477))
        *   Microsoft 365 Fundamentals
        *   Microsoft Technology Associate (MTA)
        *   Systems Security Certified Practitioner (SSCP)^([^(478)](#fn478))
    2.  II. **Intermediate and Advance I T Certifications** 
        *   Amazon Web Services (AWS) Certified Solutions Architect^([^(479)](#fn479))
        *   Certified Ethical Hacker (CEH)^([^(480)](#fn480))
        *   Certified Information Systems Security Professional (CISSP)^([^(481)](#fn481))
        *   Cisco Certification
        *   Cisco Certified Network Professional (CCNP) ^([^(482)](#fn482))
        *   Cisco Expert-level Certifications (CCIE)^([^(483)](#fn483))
        *   Cisco Certified Design Expert (CCDE)^([^(484)](#fn484))
        *   Citrix Certifications^([^(485)](#fn485))
        *   Citrix Certified Associate – Virtualization (CCA-V)
        *   CCA-N: Citrix Certified Associate – Networking
        *   Global Information Assurance Certifications (GIAC)^([^(486)](#fn486))
        *   Google Certified Professional Cloud Architect^([^(487)](#fn487))
        *   IBM Professional Certifications^([^(488)](#fn488))
        *   Information Systems Audit and Control Association (ISACA) Certifications^([^(489)](#fn489))
        *   Certified Information Systems Auditor (CISA)
        *   Certified Information Security Manager (CISM)
        *   Certified in Risk and Information Systems Control (CRISC)
        *   Certified in the Governance of Enterprise IT (CGEIT)
        *   Juniper Certifications^([^(490)](#fn490))
        *   Linux Certifications^([^(491)](#fn491))
        *   Microsoft Certifications^([^(492)](#fn492))
        *   Microsoft certified solutions expert (MCSE)
        *   Microsoft certified solutions developer (MCSD)
        *   Microsoft Certifications
        *   Microsoft Certified: Azure Fundamentals^([^(493)](#fn493))
        *   Microsoft Certified: Azure Administrator Associate^([^(494)](#fn494))
        *   Microsoft SQL Server certifications
        *   Oracle Certified Professional^([^(495)](#fn495))
    3.  III. **Management Certifications** 
        *   Project Management Professional (PMP)^([^(496)](#fn496))
        *   Certified ScrumMaster (CSM)^([^(497)](#fn497))
        *   Agile Certifications^([^(498)](#fn498))
    
    # [Index](#contents.xhtml#re_index)
    
    *   1-SYN, [172](#c5.xhtml#p172)
    *   2-SYN/ACK, [172](#c5.xhtml#p172)
    *   3-ACK, [172](#c5.xhtml#p172)
    *   6 U.S.C., [405](#appendixG.xhtml#p405)–[409](#appendixG.xhtml#p409)
    *   10 C.F.R. § [73](#c2.xhtml#p73).[54](#c2.xhtml#p54), [140](#c4.xhtml#p140)
    *   15 U.S.C., [391](#appendixE.xhtml#p391)–[399](#appendixE.xhtml#p399)
    *   17 U.S.C. § 1201, [122](#c4.xhtml#p122)
    *   17 U.S.C. § 1201 Circumvention of copyright protection systems, [359](#appendixB.xhtml#p359)–[370](#appendixB.xhtml#p370)
    *   18 U.S.C., [411](#appendixH.xhtml#p411)–[413](#appendixH.xhtml#p413)
    *   18 U.S.C. § 1029, [160](#c4.xhtml#p160)–[161](#c4.xhtml#p161)
    *   18 U.S.C. 1030, [115](#c4.xhtml#p115)
    *   18 U.S.C. § 1030, [109](#c4.xhtml#p109)
    *   18 U.S.C. § 1037, [159](#c4.xhtml#p159)–[160](#c4.xhtml#p160)
    *   18 U.S.C. § 1831, [117](#c4.xhtml#p117)
    *   18 U.S. Code § 1028, [161](#c4.xhtml#p161)
    *   18 U.S.C.S. § 1030(a)(4), [113](#c4.xhtml#p113)
    *   § 1201(a)(1), [121](#c4.xhtml#p121)
    *   § 1201(a)(2), [121](#c4.xhtml#p121)
    *   § 1201(b)(1), [121](#c4.xhtml#p121)
    *   1202 Integrity of copyright management information, [370](#appendixB.xhtml#p370)–[373](#appendixB.xhtml#p373)
    *   1203 Civil remedies, [373](#appendixB.xhtml#p373)–[375](#appendixB.xhtml#p375)
    *   1204 Criminal offenses and penalties, [375](#appendixB.xhtml#p375)
    *   1205 Savings clause, [375](#appendixB.xhtml#p375)
    *   2018 RAND Corporation, [81](#c2.xhtml#p81)
    *   A
    *   AA20-352A, [231](#c6.xhtml#p231)
    *   Abacus, [30](#c1.xhtml#p30)
    *   ABC, see [Atanasoff-Berry Computer](#index.xhtml#see109)
    *   Accelerometer, [315](#c8.xhtml#p315)
    *   Access control, [230](#c6.xhtml#p230)
    *   Access point, [217](#c5.xhtml#p217)
    *   Acknowledgment (ACL), [212](#c5.xhtml#p212)
    *   Active attack, [235](#c6.xhtml#p235)
    *   Actual damages, [374](#appendixB.xhtml#p374)
    *   Actuator, [286](#c7.xhtml#p286)
    *   Address Resolution Protocol (ARP), [182](#c5.xhtml#p182)–[183](#c5.xhtml#p183), [194](#c5.xhtml#p194), [250](#c6.xhtml#p250)
    *   Address Space Layout Randomization (ASLR), [242](#c6.xhtml#p242)
    *   Administrative law, [95](#c3.xhtml#p95), [99](#c3.xhtml#p99)
    *   Advanced Message Queuing Protocol (AMQP), [294](#c7.xhtml#p294)
    *   Advanced Mobile Phone System (AMPS), [309](#c8.xhtml#p309)
    *   Advanced Persistent Threat (APT), [231](#c6.xhtml#p231)
    *   Advanced Research Projects Agency Network (ARPANET), [38](#c1.xhtml#p38), [39](#c1.xhtml#p39), [60](#c2.xhtml#p60)–[61](#c2.xhtml#p61), [63](#c2.xhtml#p63), [173](#c5.xhtml#p173)–[175](#c5.xhtml#p175), [210](#c5.xhtml#p210)
    *   Adware, [237](#c6.xhtml#p237)
    *   Affidavit, [103](#c3.xhtml#p103)
    *   Agency, [405](#appendixG.xhtml#p405)
    *   AI, see [Artificial Intelligence](#index.xhtml#see104)
    *   All Writs Act, [147](#c4.xhtml#p147)
    *   Amateurs, [84](#c2.xhtml#p84)
    *   Amazon, [44](#c1.xhtml#p44), [66](#c2.xhtml#p66)
    *   Amazon Go, [284](#c7.xhtml#p284)
    *   American Standard Code for Information Interchange (ASCII), [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   America Online (AOL), [151](#c4.xhtml#p151)
    *   AMPS, see [Advanced Mobile Phone System](#index.xhtml#see40)
    *   AMQP, see [Advanced Message Queuing Protocol](#index.xhtml#see39)
    *   Analog transmissions, [371](#appendixB.xhtml#p371)
    *   Analog video cassette camcorder, [369](#appendixB.xhtml#p369)
    *   Analog video cassette recorder, [369](#appendixB.xhtml#p369)
    *   Analytical Engine, [33](#c1.xhtml#p33)
    *   AND-gate, [17](#c1.xhtml#p17)
    *   Android, [317](#c8.xhtml#p317)
    *   Android.database, [319](#c8.xhtml#p319)
    *   Android.opengl, [319](#c8.xhtml#p319)
    *   Android Operating System, [65](#c2.xhtml#p65), [316](#c8.xhtml#p316)
    *   Android runtime (ART), [318](#c8.xhtml#p318)
    *   Android.text, [319](#c8.xhtml#p319)
    *   Android.webkit, [318](#c8.xhtml#p318)
    *   Angle of arrival (AOA), [329](#c8.xhtml#p329)
    *   Angry IP scanner, [195](#c5.xhtml#p195)
    *   ANN, see [Artificial neural network](#index.xhtml#see105)
    *   Antenna, [314](#c8.xhtml#p314)
    *   Anti-hacking laws, [106](#c4.xhtml#p106)
    *   Computer Hacking Laws, [117](#c4.xhtml#p117)
    *   Digital Millennium Copyright Act (DMCA), [119](#c4.xhtml#p119)–[125](#c4.xhtml#p125)
    *   Economic Espionage Act of 1996 (EEA), [117](#c4.xhtml#p117)
    *   Federal Computer Fraud and Abuse Act, [109](#c4.xhtml#p109)–[117](#c4.xhtml#p117)
    *   Antikythera Mechanism, [31](#c1.xhtml#p31)
    *   Antitrust laws, [405](#appendixG.xhtml#p405)
    *   Antivirus software/antivirus protection, [230](#c6.xhtml#p230)
    *   Anycast addresses, [191](#c5.xhtml#p191)
    *   AOA, see [Angle of arrival](#index.xhtml#see67)
    *   AOL, see [America Online](#index.xhtml#see52)
    *   API, see [Application Program Interface](#index.xhtml#see92)
    *   Appeals court, [98](#c3.xhtml#p98)
    *   Apple, [44](#c1.xhtml#p44)
    *   Apple computers, [39](#c1.xhtml#p39), [194](#c5.xhtml#p194)
    *   Apple II, [39](#c1.xhtml#p39), [40](#c1.xhtml#p40)
    *   Apple iPhone, [65](#c2.xhtml#p65)
    *   Apple’s iOS, [319](#c8.xhtml#p319)
    *   Application layer, [207](#c5.xhtml#p207), [211](#c5.xhtml#p211), [291](#c7.xhtml#p291), [294](#c7.xhtml#p294)
    *   Application layer attacks, [238](#c6.xhtml#p238)
    *   Application-level firewalls, [260](#c6.xhtml#p260)
    *   Application Program Interface (API), [317](#c8.xhtml#p317)
    *   Applications (apps), [316](#c8.xhtml#p316)
    *   Application security, [226](#c6.xhtml#p226)
    *   Appropriate federal entities, [406](#appendixG.xhtml#p406)
    *   APT, see [Advanced Persistent Threat](#index.xhtml#see41)
    *   Aristotle, [3](#c1.xhtml#p3)
    *   arp, [196](#c5.xhtml#p196)
    *   ARP, see [Address Resolution Protocol](#index.xhtml#see36)
    *   ARPANET, see [Advanced Research Projects Agency Network](#index.xhtml#see42)
    *   Arpspoof, [250](#c6.xhtml#p250)
    *   ART, see [Android runtime](#index.xhtml#see64)
    *   Article VI, [93](#c3.xhtml#p93)
    *   Artificial Intelligence (AI), [45](#c1.xhtml#p45), [73](#c2.xhtml#p73)
    *   Artificial neural network (ANN), [46](#c1.xhtml#p46)
    *   ASCII, see [American Standard Code for Information Interchange](#index.xhtml#see51)
    *   ASLR, see [Address Space Layout Randomization](#index.xhtml#see37)
    *   Asymmetric encryption, [266](#c6.xhtml#p266)–[269](#c6.xhtml#p269)
    *   Atanasoff-Berry Computer (ABC), [34](#c1.xhtml#p34)
    *   Atbash ciphers, [223](#c6.xhtml#p223)
    *   Atomic Energy Act of 1954 (42 U.S.C. 2014(y)), [348](#appendixA.xhtml#p348)
    *   section [11](#c1.xhtml#p11), [343](#appendixA.xhtml#p343)
    *   Attack vector, [235](#c6.xhtml#p235)
    *   Authentication Centre (AC), [326](#c8.xhtml#p326)
    *   Authentication key (Ki), [328](#c8.xhtml#p328)
    *   Authentication protocol, [262](#c6.xhtml#p262)
    *   Authenticity, [229](#c6.xhtml#p229)
    *   Authorization, [262](#c6.xhtml#p262)
    *   Automotive sector, [279](#c7.xhtml#p279)–[280](#c7.xhtml#p280)
    *   Availability, [226](#c6.xhtml#p226)
    *   B
    *   Babbage, Charles, [33](#c1.xhtml#p33)
    *   Back-end firewall, [257](#c6.xhtml#p257)
    *   Backup batteries, [329](#c8.xhtml#p329)
    *   Bandwidth, [299](#c7.xhtml#p299)–[300](#c7.xhtml#p300)
    *   Base station controller (BSC), [328](#c8.xhtml#p328)
    *   Base transceiver system (BTS), [328](#c8.xhtml#p328)
    *   Battery, [314](#c8.xhtml#p314)
    *   Behavioral analytics, [230](#c6.xhtml#p230)
    *   Berkeley Software Distribution (BSD), [320](#c8.xhtml#p320)
    *   Big data, IoT, [288](#c7.xhtml#p288)–[290](#c7.xhtml#p290)
    *   Bill of Rights, [149](#c4.xhtml#p149)
    *   Binary
    *   data, [4](#c1.xhtml#p4)–[9](#c1.xhtml#p9)
    *   to decimal conversion, [9](#c1.xhtml#p9)
    *   to hexadecimal conversion, [13](#c1.xhtml#p13)–[14](#c1.xhtml#p14)
    *   Biometric authentication, [261](#c6.xhtml#p261)
    *   Biometrics, [230](#c6.xhtml#p230)
    *   BIPA, see [Illinois Biometric Information Privacy Act](#index.xhtml#see643)
    *   Bit
    *   colors, [27](#c1.xhtml#p27)
    *   possible patterns, [6](#c1.xhtml#p6), [7](#c1.xhtml#p7)
    *   Black-hat hackers, [231](#c6.xhtml#p231), [232](#c6.xhtml#p232)
    *   BLE, see [Bluetooth Low Energy](#index.xhtml#see147)
    *   Block Cipher, [264](#c6.xhtml#p264)
    *   Bluetooth, [297](#c7.xhtml#p297), [331](#c8.xhtml#p331)
    *   Bluetooth Low Energy (BLE), [331](#c8.xhtml#p331)
    *   Boolean algebra, [15](#c1.xhtml#p15)–[16](#c1.xhtml#p16)
    *   Botnets, [66](#c2.xhtml#p66)
    *   Brick, [310](#c8.xhtml#p310)
    *   Bridge, [182](#c5.xhtml#p182)
    *   Broadcast station, [372](#appendixB.xhtml#p372)
    *   Brute-force attacks, [252](#c6.xhtml#p252)
    *   BSD, see [Berkeley Software Distribution](#index.xhtml#see130)
    *   Buffer overflow, [242](#c6.xhtml#p242)
    *   Burdens of proof, [103](#c3.xhtml#p103)
    *   Business Associates, [130](#c4.xhtml#p130), [131](#c4.xhtml#p131)
    *   Business layer, [291](#c7.xhtml#p291)
    *   Bus network topology, [202](#c5.xhtml#p202), [203](#c5.xhtml#p203)
    *   C
    *   CA, see [Certificate authority](#index.xhtml#see189)
    *   CaaS, see [Crime-as-a-Service](#index.xhtml#see319)
    *   Cable system, [372](#appendixB.xhtml#p372)
    *   Cache memory, [21](#c1.xhtml#p21)
    *   Caesar cipher/Caesar code, [224](#c6.xhtml#p224), [263](#c6.xhtml#p263)
    *   with three shifted places, [225](#c6.xhtml#p225)
    *   CALEA, see [Communication Assistant for Law Enforcement Act of 1994](#index.xhtml#see227)
    *   California Consumer Privacy Act of 2018 (CCPA), [73](#c2.xhtml#p73), [109](#c4.xhtml#p109), [165](#c4.xhtml#p165)
    *   Camera, [314](#c8.xhtml#p314)
    *   Campus Area Network (CAN), [199](#c5.xhtml#p199)
    *   CAN, see [Campus Area Network](#index.xhtml#see170)
    *   CAN-SPAM Act, see [Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003](#index.xhtml#see301)
    *   CAPTCHA, [124](#c4.xhtml#p124)
    *   Carnegie Mellon Mach kernel, [320](#c8.xhtml#p320)
    *    Carpenter v. United States, [152](#c4.xhtml#p152)
    *   Cascading Style Sheets (CSS), [12](#c1.xhtml#p12)
    *   Case law, [96](#c3.xhtml#p96)
    *   CCPA, see [California Consumer Privacy Act of 2018](#index.xhtml#see168)
    *   CDD, see [Compatibility Definition Document](#index.xhtml#see228)
    *   CDMA, see [Code Division Multiple Access](#index.xhtml#see217)
    *   CEA, see [Cybersecurity Enhancement Act of 2014](#index.xhtml#see375)
    *   Cell towers, [322](#c8.xhtml#p322), [328](#c8.xhtml#p328)
    *   Cellular technology, [297](#c7.xhtml#p297)
    *   Cellular Telecommunications and Internet Association (CTIA), [333](#c8.xhtml#p333)
    *   Central data storage, [178](#c5.xhtml#p178)
    *   Central processing unit (CPU), [2](#c1.xhtml#p2), [19](#c1.xhtml#p19)
    *   architecture, [19](#c1.xhtml#p19)
    *   registers, [21](#c1.xhtml#p21)
    *   Certificate authority (CA), [269](#c6.xhtml#p269)–[270](#c6.xhtml#p270)
    *   Certificate Signing Request (CSR), [269](#c6.xhtml#p269)
    *   CFAA, see [Computer Fraud and Abuse Act](#index.xhtml#see264)
    *   CFR, see [Code of Federal Regulations](#index.xhtml#see219)
    *   Child Pornography Prevention Act of 1996 (CPPA), [80](#c2.xhtml#p80)
    *   Children’s Online Privacy Protection Act of 1998 (COPPA), [133](#c4.xhtml#p133), [162](#c4.xhtml#p162)–[164](#c4.xhtml#p164)
    *   Child Sexual Abuse and Exploitation (CSAE), [80](#c2.xhtml#p80)
    *   Child sexual abuse material (CSAM), [80](#c2.xhtml#p80)
    *   CIA Triad Model, [227](#c6.xhtml#p227)
    *   Cipher/cypher, [223](#c6.xhtml#p223)
    *   Ciphertext, [264](#c6.xhtml#p264)
    *   Cipher Trace Cryptocurrency Anti-Money Laundering Report, [82](#c2.xhtml#p82)
    *   Circumstantial evidence, [103](#c3.xhtml#p103)
    *   CISA, see [Cybersecurity Information Sharing Act of 2015](#index.xhtml#see376); [Cybersecurity Infrastructure Security Agency](#index.xhtml#see377)
    *   CISCO packet tracer, [195](#c5.xhtml#p195)
    *   Cisco systems, [45](#c1.xhtml#p45)
    *   Civil law, [100](#c3.xhtml#p100)
    *   Class action lawsuit, [103](#c3.xhtml#p103)
    *   Clean Air Act of 1963, [99](#c3.xhtml#p99)
    *   Clients, [179](#c5.xhtml#p179)
    *   Client server communication, [180](#c5.xhtml#p180)
    *   Client-server model, [197](#c5.xhtml#p197)
    *   Cloud-based firewalls, [261](#c6.xhtml#p261)
    *   Cloud computing, [65](#c2.xhtml#p65)
    *   Cloud security, [230](#c6.xhtml#p230)
    *   CMYK (Cyan, Magenta, Yellow, Black), [28](#c1.xhtml#p28)
    *   CoAP, see [Constrained Application Protocol](#index.xhtml#see300)
    *   Cocoa touch layer, [322](#c8.xhtml#p322)
    *   Code Division Multiple Access (CDMA), [310](#c8.xhtml#p310)
    *   Code division system, [311](#c8.xhtml#p311)
    *   Code of Federal Regulations (CFR), [94](#c3.xhtml#p94)
    *   COE, see [Council of Europe](#index.xhtml#see310)
    *   Collision, [186](#c5.xhtml#p186)
    *   Color
    *   depth, [25](#c1.xhtml#p25)–[26](#c1.xhtml#p26)
    *   models, [27](#c1.xhtml#p27)
    *   Common Law, [103](#c3.xhtml#p103)
    *   Common Vulnerabilities and Exposures (CVE), [235](#c6.xhtml#p235)
    *   Communication Assistant for Law Enforcement Act of 1994 (CALEA), [156](#c4.xhtml#p156)
    *   Compatibility Definition Document (CDD), [317](#c8.xhtml#p317)
    *   Compatible Time-Sharing System (CTSS), [60](#c2.xhtml#p60)
    *   Comprehensive Drug Abuse Prevention and Control Act of 1970 (21 U.S.C. 853), section [413](#appendixH.xhtml#p413), [351](#appendixA.xhtml#p351)
    *   Compression
    *   lossless compression, [23](#c1.xhtml#p23)–[24](#c1.xhtml#p24)
    *   lossy compression, [22](#c1.xhtml#p22)–[23](#c1.xhtml#p23)
    *   Computer, [348](#appendixA.xhtml#p348)
    *   Computer concepts
    *   compression
    *   lossless compression, [23](#c1.xhtml#p23)–[24](#c1.xhtml#p24)
    *   lossy compression, [22](#c1.xhtml#p22)–[23](#c1.xhtml#p23)
    *   computing devices, [30](#c1.xhtml#p30)–[47](#c1.xhtml#p47)
    *   conventional computer systems, [1](#c1.xhtml#p1)–[2](#c1.xhtml#p2)
    *   input, [2](#c1.xhtml#p2), [5](#c1.xhtml#p5)
    *   American Standard Code for Information Interchange (ASCII), [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   binary data, [4](#c1.xhtml#p4)–[9](#c1.xhtml#p9)
    *   binary to decimal conversion, [9](#c1.xhtml#p9)
    *   binary to hexadecimal conversion, [13](#c1.xhtml#p13)–[14](#c1.xhtml#p14)
    *   decimal to binary conversion, [9](#c1.xhtml#p9)
    *   Extended Binary Coded Decimal Interchange Code (EBCDIC), [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   hexadecimal, [11](#c1.xhtml#p11)–[12](#c1.xhtml#p12)
    *   hexadecimal to binary conversion, [13](#c1.xhtml#p13)
    *   UNICODE, [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   output
    *   color depth, [25](#c1.xhtml#p25)–[26](#c1.xhtml#p26)
    *   color models, [27](#c1.xhtml#p27)
    *   pixels, [24](#c1.xhtml#p24)
    *   screen resolution, [28](#c1.xhtml#p28)
    *   processing
    *   Boolean algebra, [15](#c1.xhtml#p15)
    *   logic gates, [15](#c1.xhtml#p15)–[19](#c1.xhtml#p19)
    *   processor types, [19](#c1.xhtml#p19)–[20](#c1.xhtml#p20)
    *   truth tables, [17](#c1.xhtml#p17)–[18](#c1.xhtml#p18)
    *   quantum computing, [29](#c1.xhtml#p29)–[30](#c1.xhtml#p30)
    *   storage, [20](#c1.xhtml#p20)–[21](#c1.xhtml#p21)
    *   Computer data conversion, [9](#c1.xhtml#p9), [10](#c1.xhtml#p10)
    *   Computer Fraud and Abuse Act (CFAA), [94](#c3.xhtml#p94), [343](#appendixA.xhtml#p343)–[357](#appendixA.xhtml#p357)
    *   Computer Hacking Laws, [117](#c4.xhtml#p117)–[118](#c4.xhtml#p118)
    *   Computer Maintenance Competition Assurance Act, [120](#c4.xhtml#p120)
    *   Computer network components and terminology, [179](#c5.xhtml#p179)–[188](#c5.xhtml#p188)
    *   Computer networking, [173](#c5.xhtml#p173)–[174](#c5.xhtml#p174)
    *   advantages and disadvantages, [178](#c5.xhtml#p178)–[179](#c5.xhtml#p179)
    *   computer network components and terminology, [179](#c5.xhtml#p179)–[188](#c5.xhtml#p188)
    *   internet, [176](#c5.xhtml#p176)–[177](#c5.xhtml#p177)
    *   IPv6 anatomy, [188](#c5.xhtml#p188)–[195](#c5.xhtml#p195)
    *   network utilities, [195](#c5.xhtml#p195)–[196](#c5.xhtml#p196)
    *   protocol, [175](#c5.xhtml#p175)–[176](#c5.xhtml#p176)
    *   World Wide Web (WWW), [176](#c5.xhtml#p176)–[177](#c5.xhtml#p177)
    *   Computer security technology
    *   authentication, [261](#c6.xhtml#p261)
    *   authorization, [261](#c6.xhtml#p261)
    *   cyberattack types, [235](#c6.xhtml#p235)–[236](#c6.xhtml#p236)
    *   adware, [237](#c6.xhtml#p237)–[238](#c6.xhtml#p238)
    *   denial-of-service attacks, [238](#c6.xhtml#p238)–[245](#c6.xhtml#p245)
    *   malware, [246](#c6.xhtml#p246)–[248](#c6.xhtml#p248)
    *   phishing, [248](#c6.xhtml#p248)–[250](#c6.xhtml#p250)
    *   spoofing, [250](#c6.xhtml#p250)–[251](#c6.xhtml#p251)
    *   Structured Query Language Injection, [251](#c6.xhtml#p251)–[252](#c6.xhtml#p252)
    *   Wi-Fi hacking, [252](#c6.xhtml#p252)–[256](#c6.xhtml#p256)
    *   identification, [261](#c6.xhtml#p261)
    *   modern encryption, [262](#c6.xhtml#p262)
    *   asymmetric encryption, [266](#c6.xhtml#p266)–[269](#c6.xhtml#p269)
    *   certificate authority, [269](#c6.xhtml#p269)–[270](#c6.xhtml#p270)
    *   digital certificates, [269](#c6.xhtml#p269)–[270](#c6.xhtml#p270)
    *   hash functions, [270](#c6.xhtml#p270)–[273](#c6.xhtml#p273)
    *   symmetric encryption, [263](#c6.xhtml#p263)–[266](#c6.xhtml#p266)
    *   prevention mechanisms, [256](#c6.xhtml#p256)–[259](#c6.xhtml#p259)
    *   firewall types, [259](#c6.xhtml#p259)–[261](#c6.xhtml#p261)
    *   understanding security terminology, [230](#c6.xhtml#p230)–[235](#c6.xhtml#p235)
    *   Computing devices, [30](#c1.xhtml#p30)–[47](#c1.xhtml#p47)
    *   Conficker, [67](#c2.xhtml#p67)
    *   Confidentiality, [226](#c6.xhtml#p226)
    *   Constrained Application Protocol (CoAP), [294](#c7.xhtml#p294)
    *   Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003 (CAN-SPAM Act), [107](#c4.xhtml#p107), [158](#c4.xhtml#p158)–[159](#c4.xhtml#p159)
    *   Conventional computer systems, [1](#c1.xhtml#p1)–[2](#c1.xhtml#p2)
    *   Conviction, [349](#appendixA.xhtml#p349)
    *   COPPA, see [Children’s Online Privacy Protection Act of 1998](#index.xhtml#see194)
    *   Copyright Act (17 U.S.C. § 107), [119](#c4.xhtml#p119)
    *   Copyright management information (CMI), [122](#c4.xhtml#p122), [370](#appendixB.xhtml#p370)
    *   Core, [128](#c4.xhtml#p128), [129](#c4.xhtml#p129)
    *   Core OS layer, [320](#c8.xhtml#p320)
    *   Core service layer, [321](#c8.xhtml#p321)
    *   Council of Europe (COE), [80](#c2.xhtml#p80)
    *   Courts system, [96](#c3.xhtml#p96)–[99](#c3.xhtml#p99)
    *   Covered entities, [130](#c4.xhtml#p130), [131](#c4.xhtml#p131)
    *   Covers six miscellaneous provisions, [120](#c4.xhtml#p120)
    *   CPPA, see [Child Pornography Prevention Act of 1996](#index.xhtml#see193)
    *   CPU, see [Central processing unit](#index.xhtml#see186)
    *   Cracking attacks, [252](#c6.xhtml#p252)
    *    Craigslist, Inc. v. Naturemarket, [124](#c4.xhtml#p124)
    *   Creeper, [60](#c2.xhtml#p60)
    *   Crime-as-a-Service (CaaS), [56](#c2.xhtml#p56), [67](#c2.xhtml#p67), [75](#c2.xhtml#p75), [230](#c6.xhtml#p230)
    *   Criminal law, [100](#c3.xhtml#p100)–[101](#c3.xhtml#p101)
    *   Criminal violation, [123](#c4.xhtml#p123)
    *   Cruz Crew, [70](#c2.xhtml#p70)
    *   Cryptanalysis, [223](#c6.xhtml#p223)
    *   Cryptocurrency, [81](#c2.xhtml#p81)
    *   Cryptography, [222](#c6.xhtml#p222)
    *   CSAE, see [Child Sexual Abuse and Exploitation](#index.xhtml#see195)
    *   CSAM, see [Child sexual abuse material](#index.xhtml#see196)
    *   CSR, see [Certificate Signing Request](#index.xhtml#see190)
    *   CSS, see [Cascading Style Sheets](#index.xhtml#see176)
    *   CTIA, see [Cellular Telecommunications and Internet Association](#index.xhtml#see184)
    *   CTSS, see [Compatible Time-Sharing System](#index.xhtml#see229)
    *   Cultura Colectiva, [66](#c2.xhtml#p66)
    *   CVE, see [Common Vulnerabilities and Exposures](#index.xhtml#see226)
    *   CVS Pharmacy, [133](#c4.xhtml#p133)
    *   Cyberattack, [302](#c7.xhtml#p302)
    *   motivations, [237](#c6.xhtml#p237)
    *   types, [235](#c6.xhtml#p235)–[237](#c6.xhtml#p237)
    *   adware, [237](#c6.xhtml#p237)
    *   denial-of-service attacks, [238](#c6.xhtml#p238)–[245](#c6.xhtml#p245)
    *   malware, [246](#c6.xhtml#p246)–[248](#c6.xhtml#p248)
    *   phishing, [248](#c6.xhtml#p248)–[250](#c6.xhtml#p250)
    *   spoofing, [250](#c6.xhtml#p250)–[251](#c6.xhtml#p251)
    *   Structured Query Language Injection, [251](#c6.xhtml#p251)–[252](#c6.xhtml#p252)
    *   Wi-Fi hacking, [252](#c6.xhtml#p252)–[256](#c6.xhtml#p256)
    *   Cybercrime; see also individual entries 
    *   as business, [84](#c2.xhtml#p84)
    *   categories
    *   against corporations, [74](#c2.xhtml#p74)
    *   against government, [74](#c2.xhtml#p74)
    *   against person, [75](#c2.xhtml#p75)–[76](#c2.xhtml#p76)
    *   Child Sexual Abuse and Exploitation (CSAE), [80](#c2.xhtml#p80)
    *   cost, [81](#c2.xhtml#p81)
    *   cryptocurrency role, [81](#c2.xhtml#p81)
    *   and cybercriminal, [53](#c2.xhtml#p53)–[55](#c2.xhtml#p55)
    *   industrial espionage, [83](#c2.xhtml#p83)–[84](#c2.xhtml#p84)
    *   Internet of Things (IoT), [78](#c2.xhtml#p78)
    *   machine learning (ML), [79](#c2.xhtml#p79)–[80](#c2.xhtml#p80)
    *   making of cybercriminal, [76](#c2.xhtml#p76)–[78](#c2.xhtml#p78)
    *   origin and definition, [55](#c2.xhtml#p55)
    *   phases and evolution of, [58](#c2.xhtml#p58)–[60](#c2.xhtml#p60)
    *   phase I, [60](#c2.xhtml#p60)–[62](#c2.xhtml#p62)
    *   phase II, [62](#c2.xhtml#p62)
    *   phase III, [63](#c2.xhtml#p63)–[67](#c2.xhtml#p67)
    *   phase IV, [67](#c2.xhtml#p67)–[73](#c2.xhtml#p73)
    *   state-sponsored cyberwarfare, [83](#c2.xhtml#p83)–[84](#c2.xhtml#p84)
    *   weapons, [56](#c2.xhtml#p56)
    *   Cyber harassment, [56](#c2.xhtml#p56)
    *   Cyber law, [87](#c3.xhtml#p87)
    *   Cybersecurity, [226](#c6.xhtml#p226)
    *   framework evolution, [127](#c4.xhtml#p127), [128](#c4.xhtml#p128)
    *   in public and private sector, [107](#c4.xhtml#p107)
    *   purpose, [406](#appendixG.xhtml#p406)
    *   requirements for federal government, [107](#c4.xhtml#p107)
    *   threat, [406](#appendixG.xhtml#p406)
    *   Cybersecurity Enhancement Act of 2014 (CEA), [127](#c4.xhtml#p127), [143](#c4.xhtml#p143)
    *   Cybersecurity Information Sharing Act of 2015 (CISA), [107](#c4.xhtml#p107), [141](#c4.xhtml#p141)–[142](#c4.xhtml#p142)
    *   Cybersecurity Infrastructure Security Agency (CISA), [142](#c4.xhtml#p142), [231](#c6.xhtml#p231), [236](#c6.xhtml#p236)
    *   Cyberterrorism, [56](#c2.xhtml#p56)
    *   Cyber threat indicator, [406](#appendixG.xhtml#p406)
    *   Cyberwarfare, [56](#c2.xhtml#p56), [72](#c2.xhtml#p72), [231](#c6.xhtml#p231)
    *   D
    *   Damage, [349](#appendixA.xhtml#p349)
    *   Dark Web, [75](#c2.xhtml#p75), [77](#c2.xhtml#p77)
    *   DARPA, see [Defense Advanced Research Projects Agency](#index.xhtml#see410)
    *   Dash [7](#c1.xhtml#p7), [297](#c7.xhtml#p297)
    *   Data Breach, [231](#c6.xhtml#p231)
    *   Data Distribution Service (DDS), [295](#c7.xhtml#p295)
    *   Data-driven and techno-centric society, see [Cybercrime](#index.xhtml#see345)
    *   Datagram Transport Layer Security (DTLS), [295](#c7.xhtml#p295)
    *   Data Link layer, [192](#c5.xhtml#p192), [208](#c5.xhtml#p208), [210](#c5.xhtml#p210)
    *   Data packets, [182](#c5.xhtml#p182), [216](#c5.xhtml#p216)
    *   Data security laws and regulations, [106](#c4.xhtml#p106), [125](#c4.xhtml#p125)–[126](#c4.xhtml#p126)
    *   Federal Trade Commission Act, [132](#c4.xhtml#p132)–[134](#c4.xhtml#p134)
    *   Health Information Technology, [131](#c4.xhtml#p131)–[132](#c4.xhtml#p132)
    *   laws affecting financial institutions, [134](#c4.xhtml#p134)–[136](#c4.xhtml#p136)
    *   laws affecting utilities, [138](#c4.xhtml#p138)–[140](#c4.xhtml#p140)
    *   laws dealing with healthcare, [128](#c4.xhtml#p128)–[131](#c4.xhtml#p131)
    *   National Institute of Standards and Technology Cybersecurity Framework, [126](#c4.xhtml#p126)–[128](#c4.xhtml#p128)
    *   DDoS, see [Distributed denial-of-service](#index.xhtml#see430)
    *   DDS, see [Data Distribution Service](#index.xhtml#see387)
    *   Decagon, [6](#c1.xhtml#p6)
    *   Deceptive phishing, [248](#c6.xhtml#p248)
    *   Decimal
    *   to binary conversion, [9](#c1.xhtml#p9)
    *    vs. binary system, [9](#c1.xhtml#p9)
    *   Deepfakes, [73](#c2.xhtml#p73)
    *   Deepfake technology, [79](#c2.xhtml#p79)
    *   Deep Web, [76](#c2.xhtml#p76), [77](#c2.xhtml#p77)
    *   Defendant, [100](#c3.xhtml#p100)
    *   Defense Advanced Research Projects Agency (DARPA), [173](#c5.xhtml#p173)–[174](#c5.xhtml#p174)
    *   Defensive measure, [407](#appendixG.xhtml#p407)
    *   Demilitarized Zone (DMZ), [256](#c6.xhtml#p256)
    *   Denial of service (DoS), [56](#c2.xhtml#p56), [117](#c4.xhtml#p117), [138](#c4.xhtml#p138), [238](#c6.xhtml#p238)–[245](#c6.xhtml#p245)
    *   Department of the United States, [349](#appendixA.xhtml#p349)
    *   DHCP, see [Dynamic Host Configuration Protocol](#index.xhtml#see445)
    *   DHS, see [U.S. Department of Homeland Security](#index.xhtml#see1329)
    *   Dialed number recorder (DNR), [147](#c4.xhtml#p147)
    *   Dictionary attacks, [252](#c6.xhtml#p252)
    *   Digital
    *   certificates, [269](#c6.xhtml#p269)–[270](#c6.xhtml#p270)
    *   evidence, [90](#c3.xhtml#p90)
    *   signature, [267](#c6.xhtml#p267)
    *   transmissions, [371](#appendixB.xhtml#p371)–[372](#appendixB.xhtml#p372)
    *   Digital Millennium Copyright Act (DMCA), [119](#c4.xhtml#p119)–[121](#c4.xhtml#p121)
    *   17 U.S.C. § 1201, [122](#c4.xhtml#p122)
    *    Craigslist, Inc. v. Naturemarket, [124](#c4.xhtml#p124)
    *    Friedman v. Live Nation Merchandise, [123](#c4.xhtml#p123)
    *    MDY Industries, Inc. LLC v. Blizzard Entertainment, [124](#c4.xhtml#p124)
    *   DistBelief, [46](#c1.xhtml#p46)
    *   Distributed denial-of-service (DDoS), [56](#c2.xhtml#p56), [242](#c6.xhtml#p242), [302](#c7.xhtml#p302)
    *   DKIM, see [Domain keys identified mail](#index.xhtml#see435)
    *   DMZ, see [Demilitarized Zone](#index.xhtml#see412)
    *   DNR, see [Dialed number recorder](#index.xhtml#see417)
    *   DNS, see [Domain name system](#index.xhtml#see436)
    *   Domain keys identified mail (DKIM), [185](#c5.xhtml#p185)
    *   Domain name system (DNS), [63](#c2.xhtml#p63), [171](#c5.xhtml#p171)–[172](#c5.xhtml#p172), [184](#c5.xhtml#p184)–[185](#c5.xhtml#p185), [211](#c5.xhtml#p211), [249](#c6.xhtml#p249), [250](#c6.xhtml#p250)
    *   spoofing, [250](#c6.xhtml#p250)
    *   DoS, see [Denial of service](#index.xhtml#see413)
    *   DoSHTTP, [245](#c6.xhtml#p245)
    *   Double Jeopardy, [97](#c3.xhtml#p97)
    *   Downlink, [328](#c8.xhtml#p328)
    *   DTLS, see [Datagram Transport Layer Security](#index.xhtml#see389)
    *   Dual firewall model, [257](#c6.xhtml#p257), [258](#c6.xhtml#p258)
    *   DuPont, [118](#c4.xhtml#p118)
    *   Dynamic Host Configuration Protocol (DHCP), [184](#c5.xhtml#p184), [190](#c5.xhtml#p190)
    *   Dynamic IP address, [190](#c5.xhtml#p190)
    *   E
    *   EBCDIC, see [Extended Binary Coded Decimal Interchange Code](#index.xhtml#see488)
    *   ECOA, see [Equal Credit Opportunity Act](#index.xhtml#see479)
    *   Economic espionage, [118](#c4.xhtml#p118)
    *   Economic Espionage Act of 1996 (EEA), [117](#c4.xhtml#p117)
    *   ECPA, see [Electronic Communication Privacy Act of 1986](#index.xhtml#see457)
    *   Edge computing paradigm, [288](#c7.xhtml#p288)
    *   EEA, see [Economic Espionage Act of 1996](#index.xhtml#see451)
    *   E-Government Act, [145](#c4.xhtml#p145)
    *   EHRs, see [Electronic Health Records](#index.xhtml#see460)
    *   Electronic Communication Privacy Act of 1986 (ECPA), [154](#c4.xhtml#p154)–[155](#c4.xhtml#p155)
    *   Electronic computer (Z3), [35](#c1.xhtml#p35)
    *   Electronic evidence, [103](#c3.xhtml#p103)
    *   Electronic Health Records (EHRs), [132](#c4.xhtml#p132)
    *   Electronic Medical Records (EMR), [67](#c2.xhtml#p67)
    *   Electronic serial number (ESN), [325](#c8.xhtml#p325)
    *   Electronic surveillance, [151](#c4.xhtml#p151)–[153](#c4.xhtml#p153)
    *   Electronic wallets, [81](#c2.xhtml#p81)
    *   Electro optical devices, [20](#c1.xhtml#p20)
    *   Email spoofing, [250](#c6.xhtml#p250)
    *   EMR, see [Electronic Medical Records](#index.xhtml#see461)
    *   Encryption
    *   attacks, [303](#c7.xhtml#p303)
    *   research, [364](#appendixB.xhtml#p364)
    *   technology, [364](#appendixB.xhtml#p364)
    *   Energy Policy Act of 2005, [138](#c4.xhtml#p138)
    *   Energy sector, [280](#c7.xhtml#p280)
    *   ENIAC computer, [36](#c1.xhtml#p36)
    *   Enigma machine, [224](#c6.xhtml#p224), [225](#c6.xhtml#p225)
    *   Entry-level IT certifications, [415](#appendixI.xhtml#p415)
    *   Environmental Protection Agency (EPA), [100](#c3.xhtml#p100)
    *   Epsilon Data Management, [67](#c2.xhtml#p67)
    *   Equal Credit Opportunity Act (ECOA), [133](#c4.xhtml#p133)
    *   Espionage, [54](#c2.xhtml#p54)
    *   EternalBlue, [72](#c2.xhtml#p72)
    *   Ethernet (IEEE 802.3), [297](#c7.xhtml#p297)
    *   Ethernet-based networks, [293](#c7.xhtml#p293)
    *   Ethernet cables, [178](#c5.xhtml#p178), [181](#c5.xhtml#p181)
    *   European Union, [70](#c2.xhtml#p70), [72](#c2.xhtml#p72)
    *   Exceeds authorized access, [112](#c4.xhtml#p112), [349](#appendixA.xhtml#p349)
    *   Exploit, [230](#c6.xhtml#p230)
    *   Extended Binary Coded Decimal Interchange Code (EBCDIC), [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   Extradition, [88](#c3.xhtml#p88)–[89](#c3.xhtml#p89)
    *   F
    *   Facebook, [64](#c2.xhtml#p64), [66](#c2.xhtml#p66), [70](#c2.xhtml#p70), [73](#c2.xhtml#p73)
    *   Fair and Accurate Credit Transactions Act (FACT), [137](#c4.xhtml#p137)
    *   Fair Credit Reporting Act (FCRA), [133](#c4.xhtml#p133), [344](#appendixA.xhtml#p344)
    *   Fair Debt Collection Practices Act, [133](#c4.xhtml#p133)
    *   Farm Credit Act of 1971, [349](#appendixA.xhtml#p349)
    *   FCC, see [Federal Communications Commission](#index.xhtml#see500)
    *   FCRA, see [Fair Credit Reporting Act](#index.xhtml#see493)
    *   FDIC, see [Federal Deposit Insurance Corporation](#index.xhtml#see505)
    *   Federal Bureau of Investigation, [111](#c4.xhtml#p111)
    *   Federal Communications Commission (FCC), [174](#c5.xhtml#p174), [253](#c6.xhtml#p253), [309](#c8.xhtml#p309), [334](#c8.xhtml#p334)
    *   Federal Computer Fraud and Abuse Act
    *   cases, [112](#c4.xhtml#p112)–[115](#c4.xhtml#p115)
    *   limitations, [116](#c4.xhtml#p116)–[117](#c4.xhtml#p117)
    *   terms, [112](#c4.xhtml#p112)–[113](#c4.xhtml#p113)
    *   Federal Deposit Insurance Corporation (FDIC), [134](#c4.xhtml#p134)
    *   Federal Energy Regulatory Commission (FERC), [138](#c4.xhtml#p138)–[139](#c4.xhtml#p139)
    *   Federal entity, [407](#appendixG.xhtml#p407)
    *   Federal Government contractors, cybersecurity requirements for, [144](#c4.xhtml#p144)
    *   Federal Information Security Modernization Act of 2014, [145](#c4.xhtml#p145)–[146](#c4.xhtml#p146)
    *   NIST Information Security Controls, [146](#c4.xhtml#p146)
    *   Federal Information and Information Systems (FIPS 199), [228](#c6.xhtml#p228)
    *   potential impact levels, [228](#c6.xhtml#p228)
    *   Federal Information Security Management Act of 2002 (FISMA), [145](#c4.xhtml#p145)
    *   Federal Information Security Modernization Act of 2014, [145](#c4.xhtml#p145)–[146](#c4.xhtml#p146)
    *   Federal Legislation, [168](#c4.xhtml#p168)–[169](#c4.xhtml#p169)
    *   Federal Reserve Act, section 25 or section 25(a), [349](#appendixA.xhtml#p349)
    *   Federal Trade Commission Act, [132](#c4.xhtml#p132)–[134](#c4.xhtml#p134)
    *   Federal Wiretap Act of 1968, [154](#c4.xhtml#p154)
    *   FEMA, see [US Federal Emergency Management Agency](#index.xhtml#see1334)
    *   FERC, see [Federal Energy Regulatory Commission](#index.xhtml#see506)
    *   FIDO, [261](#c6.xhtml#p261)
    *   Fifth-generation cellular wireless (5G), [78](#c2.xhtml#p78)
    *   Financial
    *   gain, [54](#c2.xhtml#p54)
    *   institution, [348](#appendixA.xhtml#p348)–[349](#appendixA.xhtml#p349)
    *   institutions safeguards, [134](#c4.xhtml#p134)–[136](#c4.xhtml#p136)
    *   record, [349](#appendixA.xhtml#p349)
    *   Firewall, [256](#c6.xhtml#p256)
    *   Firewall-as-a-Service, [261](#c6.xhtml#p261)
    *   Firewall types, [259](#c6.xhtml#p259)–[261](#c6.xhtml#p261)
    *   FISMA, see [Federal Information Security Management Act of 2002](#index.xhtml#see513)
    *   5G, see [Fifth-generation cellular wireless](#index.xhtml#see522)
    *   5G mobile networks, [312](#c8.xhtml#p312)
    *   Flow label, [184](#c5.xhtml#p184)
    *   Fog computing, [289](#c7.xhtml#p289)
    *   Food and Drug Administration (FDA), [95](#c3.xhtml#p95)
    *   4G cellular network, [311](#c8.xhtml#p311)
    *   Fourth Amendment, [148](#c4.xhtml#p148)–[149](#c4.xhtml#p149)
    *   electronic surveillance, [151](#c4.xhtml#p151)–[153](#c4.xhtml#p153)
    *   good faith exception, [153](#c4.xhtml#p153)
    *   search and seizure, [149](#c4.xhtml#p149)–[150](#c4.xhtml#p150)
    *   Search Warrant Rule, [150](#c4.xhtml#p150)–[151](#c4.xhtml#p151)
    *   USA PATRIOT Act, [153](#c4.xhtml#p153)–[154](#c4.xhtml#p154)
    *   Frame, [192](#c5.xhtml#p192)
    *   Fraud and financial crime, [56](#c2.xhtml#p56)
    *   Fraud and Related Activity in Connection with Access Devices, [160](#c4.xhtml#p160)–[161](#c4.xhtml#p161)
    *   Fraud and Related Activity in Connection with Electronic Mail, [159](#c4.xhtml#p159)–[160](#c4.xhtml#p160)
    *   Fraud and Related Activity in Connection with Identification Documents, Authentication Features, and Information, [161](#c4.xhtml#p161)–[162](#c4.xhtml#p162)
    *    Friedman v. Live Nation Merchandise, [123](#c4.xhtml#p123)
    *   Front-end firewall, [257](#c6.xhtml#p257), [258](#c6.xhtml#p258)
    *   FTC, see [U.S Federal Trade Commission](#index.xhtml#see1335)
    *   FTC Act of 1914, [132](#c4.xhtml#p132)
    *   Full mesh topology, [203](#c5.xhtml#p203)
    *   G
    *   Gateway firewalls, [260](#c6.xhtml#p260)
    *   GDP, see [Gross domestic product](#index.xhtml#see575)
    *   General Data Protection Regulation (GDPR), [72](#c2.xhtml#p72), [108](#c4.xhtml#p108)
    *   Generator, [329](#c8.xhtml#p329)
    *   GLBA, see [Gramm-Leach-Bliley Act of 1999](#index.xhtml#see568)
    *   Global positioning system (GPS), [43](#c1.xhtml#p43), [331](#c8.xhtml#p331)
    *   Global System for Mobile communication (GSM), [310](#c8.xhtml#p310), [334](#c8.xhtml#p334)
    *   Global unicast addresses, [191](#c5.xhtml#p191)
    *   Good faith exception, [153](#c4.xhtml#p153)
    *   Google, [43](#c1.xhtml#p43), [70](#c2.xhtml#p70)
    *    Google LLC and YouTube, LLC, [133](#c4.xhtml#p133)
    *   Government entity, [349](#appendixA.xhtml#p349)
    *   GPS, see [Global positioning system](#index.xhtml#see560)
    *   Gramm-Leach-Bliley Act of 1999 (GLBA), [134](#c4.xhtml#p134)–[136](#c4.xhtml#p136)
    *   enforcement and penalties for violating, [136](#c4.xhtml#p136)–[137](#c4.xhtml#p137)
    *   Red Flags Rule, [137](#c4.xhtml#p137)
    *   Granting certiorari, [98](#c3.xhtml#p98)
    *   Graphic user interface (GUI), [40](#c1.xhtml#p40), [41](#c1.xhtml#p41)
    *   Gray-hat hackers, [232](#c6.xhtml#p232)
    *   Grayscale representation, [25](#c1.xhtml#p25)
    *   Gross domestic product (GDP), [81](#c2.xhtml#p81)
    *   GSM, see [Global System for Mobile communication](#index.xhtml#see561)
    *   GUI, see [Graphic user interface](#index.xhtml#see572)
    *   Gyroscope, [315](#c8.xhtml#p315)
    *   H
    *   Hacker, [56](#c2.xhtml#p56), [231](#c6.xhtml#p231)–[232](#c6.xhtml#p232)
    *   Hacking, [61](#c2.xhtml#p61)
    *   Hacking and threads, [112](#c4.xhtml#p112)
    *   Hacktivists, [56](#c2.xhtml#p56), [84](#c2.xhtml#p84), [232](#c6.xhtml#p232)
    *   HAL, see [Hardware abstraction layer](#index.xhtml#see586)
    *   Hard Drives (HD), [20](#c1.xhtml#p20), [21](#c1.xhtml#p21)
    *   Hardware abstraction layer (HAL), [318](#c8.xhtml#p318)
    *   Hardware power management, [319](#c8.xhtml#p319), [322](#c8.xhtml#p322)
    *   Hash algorithms, [270](#c6.xhtml#p270)–[273](#c6.xhtml#p273)
    *   HD, see [Hard Drives](#index.xhtml#see585)
    *   Health care clearinghouse, [130](#c4.xhtml#p130)
    *   Health care provider, [130](#c4.xhtml#p130)
    *   Healthcare sector, [281](#c7.xhtml#p281)–[282](#c7.xhtml#p282)
    *   Health Information Technology, [131](#c4.xhtml#p131)–[132](#c4.xhtml#p132)
    *   Health Information Technology for Economic and Clinical Health Act (HITECH), [67](#c2.xhtml#p67), [131](#c4.xhtml#p131)
    *   Health Insurance Portability and Accountability Act (HIPAA), [128](#c4.xhtml#p128)–[131](#c4.xhtml#p131)
    *   logo, [129](#c4.xhtml#p129)
    *   penalties for violating rule, [131](#c4.xhtml#p131)
    *   Privacy Rule, [130](#c4.xhtml#p130)
    *   Security Rule, [130](#c4.xhtml#p130)
    *   Health plan, [130](#c4.xhtml#p130)
    *   Hexadecimal, [11](#c1.xhtml#p11)–[13](#c1.xhtml#p13)
    *   Hexadecimal to binary conversion, [13](#c1.xhtml#p13)
    *   Hexagonal Cellular Network, [323](#c8.xhtml#p323)
    *   High Orbit Ion Cannon (HOIC), [245](#c6.xhtml#p245)
    *   HIPAA, see [Health Insurance Portability and Accountability Act](#index.xhtml#see595)
    *   HIPAA §164.308 Administrative safeguards, [377](#appendixC.xhtml#p377)–[380](#appendixC.xhtml#p380)
    *   HIPAA §164.310 Physical safeguards, [380](#appendixC.xhtml#p380)–[382](#appendixC.xhtml#p382)
    *   HIPAA §164.312 Technical safeguards, [382](#appendixC.xhtml#p382)–[383](#appendixC.xhtml#p383)
    *   HIPAA §164.314 Organizational requirements, [383](#appendixC.xhtml#p383)–[384](#appendixC.xhtml#p384)
    *   Histaeus, [222](#c6.xhtml#p222)
    *   HITECH, see [Health Information Technology for Economic and Clinical Health Act](#index.xhtml#see594)
    *   HLR, see [Home Location Register](#index.xhtml#see615)
    *   HOIC, see [High Orbit Ion Cannon](#index.xhtml#see604)
    *   Homeland Security Act of 2002 (HSA), [143](#c4.xhtml#p143)
    *   Home Location Register (HLR), [326](#c8.xhtml#p326)
    *   Hop limit, [184](#c5.xhtml#p184)
    *    Horton v. California, [150](#c4.xhtml#p150)
    *   Host, [180](#c5.xhtml#p180)
    *   Host-to-host layer, [211](#c5.xhtml#p211)
    *   HSA, see [Homeland Security Act of 2002](#index.xhtml#see614)
    *   HSS, see [U.S. Department of Health and Human Services](#index.xhtml#see1328)
    *   HTML, see [Hyper Text Markup Language](#index.xhtml#see628)
    *   HTTP, see [Hypertext Transfer Protocol](#index.xhtml#see629)
    *   HTTPS, see [Hypertext Transfer Protocol Secure](#index.xhtml#see630)
    *   HTTP Unbearable Load King (HULK), [245](#c6.xhtml#p245)
    *   Hubs, [186](#c5.xhtml#p186), [198](#c5.xhtml#p198)
    *   HULK, see [HTTP Unbearable Load King](#index.xhtml#see625)
    *   Hyper Text Markup Language (HTML), [12](#c1.xhtml#p12)
    *   Hypertext Transfer Protocol (HTTP), [172](#c5.xhtml#p172), [240](#c6.xhtml#p240)
    *   Hypertext Transfer Protocol Secure (HTTPS), [233](#c6.xhtml#p233)
    *   I
    *   I2P, see [Invisible Internet Project](#index.xhtml#see712)
    *   IANA, see [Internet Assigned Numbers Authority](#index.xhtml#see669)
    *   ICANN, see [Internet Corporation for Assigned Names and Numbers](#index.xhtml#see671)
    *   ICCID, see [Integrated Circuit Card ID](#index.xhtml#see658)
    *   ICMP, see [Internet Control Message Protocol](#index.xhtml#see670)
    *   ICS, see [Industrial Control System](#index.xhtml#see648)
    *   Identity theft, [56](#c2.xhtml#p56)
    *   Ideology, [54](#c2.xhtml#p54)
    *   IDS, see [Intrusion Detection System](#index.xhtml#see710)
    *   IETF, see [Internet Engineering Task Force](#index.xhtml#see672)
    *   IFAST, see [International Forum on ANSI-41 Standards Technology](#index.xhtml#see664)
    *   Illinois Biometric Information Privacy Act (BIPA), [166](#c4.xhtml#p166)
    *    Illinois v. Rodriguez, [150](#c4.xhtml#p150)
    *   The Impact Team, [68](#c2.xhtml#p68)
    *   Implementation tiers, [128](#c4.xhtml#p128)
    *   Indoor localization, [331](#c8.xhtml#p331)
    *   Industrial Control System (ICS), [138](#c4.xhtml#p138)
    *   Industrial espionage, [83](#c2.xhtml#p83)–[85](#c2.xhtml#p85)
    *   Industrial revolution phases, [282](#c7.xhtml#p282)–[283](#c7.xhtml#p283)
    *   Industry 4.0, [282](#c7.xhtml#p282), [283](#c7.xhtml#p283), [286](#c7.xhtml#p286)
    *   Information
    *   processing, [3](#c1.xhtml#p3)
    *   security, [363](#appendixB.xhtml#p363), [371](#appendixB.xhtml#p371)
    *   security/InfoSec, [226](#c6.xhtml#p226)
    *   system, [408](#appendixG.xhtml#p408)
    *   Innocent violations, [374](#appendixB.xhtml#p374)–[375](#appendixB.xhtml#p375)
    *   Integrated Circuit Card ID (ICCID), [327](#c8.xhtml#p327)
    *   Integrity, [226](#c6.xhtml#p226)–[227](#c6.xhtml#p227)
    *   Interface ID, [189](#c5.xhtml#p189)
    *   Intermediate and advance IT certifications, [416](#appendixI.xhtml#p416)
    *   International Banking Act of 1978, section 1(b), [349](#appendixA.xhtml#p349)
    *   International Business Machines (IBM) PC, [38](#c1.xhtml#p38), [41](#c1.xhtml#p41)
    *   International Forum on ANSI-41 Standards Technology (IFAST), [326](#c8.xhtml#p326)
    *   International Mobile Equipment Identity Database, [325](#c8.xhtml#p325)
    *   International Mobile Subscriber Identity (IMSI), [325](#c8.xhtml#p325), [328](#c8.xhtml#p328)
    *   International Organization for Standardization (ISO), [206](#c5.xhtml#p206)
    *   Internet, [53](#c2.xhtml#p53)
    *   Internet Assigned Numbers Authority (IANA), [187](#c5.xhtml#p187)
    *   Internet Control Message Protocol (ICMP), [239](#c6.xhtml#p239)
    *   Internet Corporation for Assigned Names and Numbers (ICANN), [187](#c5.xhtml#p187)
    *   Internet Engineering Task Force (IETF), [187](#c5.xhtml#p187)
    *   Internet layer, [215](#c5.xhtml#p215), [296](#c7.xhtml#p296)
    *   Internet of things (IoTs), [78](#c2.xhtml#p78), [87](#c3.xhtml#p87), [276](#c7.xhtml#p276)–[277](#c7.xhtml#p277)
    *   architectures, [290](#c7.xhtml#p290)–[293](#c7.xhtml#p293)
    *   automotive sector, [279](#c7.xhtml#p279)–[280](#c7.xhtml#p280)
    *   basic components, [286](#c7.xhtml#p286)–[288](#c7.xhtml#p288)
    *   big data, [288](#c7.xhtml#p288)–[290](#c7.xhtml#p290)
    *   connectivity, [292](#c7.xhtml#p292)
    *   data processing, [286](#c7.xhtml#p286)–[288](#c7.xhtml#p288)
    *   energy sector, [280](#c7.xhtml#p280)–[281](#c7.xhtml#p281)
    *   gateway, [289](#c7.xhtml#p289)
    *   healthcare sector, [281](#c7.xhtml#p281)–[282](#c7.xhtml#p282)
    *   manufacturing sector, [282](#c7.xhtml#p282)–[284](#c7.xhtml#p284)
    *   network consideration, [299](#c7.xhtml#p299)–[301](#c7.xhtml#p301)
    *   protocols, [293](#c7.xhtml#p293)–[299](#c7.xhtml#p299)
    *   retail sector, [284](#c7.xhtml#p284)
    *   security, [301](#c7.xhtml#p301)–[304](#c7.xhtml#p304)
    *   smart homes, [285](#c7.xhtml#p285)
    *   smart structures, [284](#c7.xhtml#p284)–[285](#c7.xhtml#p285)
    *   standards, [293](#c7.xhtml#p293)–[299](#c7.xhtml#p299)
    *   transportation sector, [286](#c7.xhtml#p286)
    *   Internet Protocol 4 (IPv4), [186](#c5.xhtml#p186), [296](#c7.xhtml#p296)
    *   Internet Protocol 6 (IPv6), [184](#c5.xhtml#p184), [187](#c5.xhtml#p187)–[188](#c5.xhtml#p188), [191](#c5.xhtml#p191), [296](#c7.xhtml#p296)
    *   anatomy, [188](#c5.xhtml#p188)–[195](#c5.xhtml#p195)
    *   Internet Protocol address (IP address), [186](#c5.xhtml#p186)–[190](#c5.xhtml#p190)
    *   Internet protocol suite (TPC/IP), [210](#c5.xhtml#p210)–[212](#c5.xhtml#p212), [215](#c5.xhtml#p215)
    *   transmission control protocol (TCP), [212](#c5.xhtml#p212)–[213](#c5.xhtml#p213)
    *   user datagram protocol (UDP), [213](#c5.xhtml#p213)–[216](#c5.xhtml#p216)
    *   Internet service provider (ISP), [42](#c1.xhtml#p42), [172](#c5.xhtml#p172), [185](#c5.xhtml#p185), [234](#c6.xhtml#p234)
    *   Internet surveillance laws, [107](#c4.xhtml#p107)
    *   Internet Surveillance Laws, United States, [147](#c4.xhtml#p147)
    *   All Writs Act, [147](#c4.xhtml#p147)–[148](#c4.xhtml#p148)
    *   Communication Assistant for Law Enforcement Act of 1994 (CALEA), [156](#c4.xhtml#p156)–[157](#c4.xhtml#p157)
    *   Electronic Communication Privacy Act of 1986 (ECPA), [154](#c4.xhtml#p154)–[156](#c4.xhtml#p156)
    *   Fourth Amendment, [148](#c4.xhtml#p148)–[154](#c4.xhtml#p154)
    *   Interoperability, [300](#c7.xhtml#p300), [364](#appendixB.xhtml#p364)
    *    The Interview, [68](#c2.xhtml#p68)
    *    Int’l Airport Ctrs., LLC v. Citrin, [114](#c4.xhtml#p114)
    *   Intrusion Detection System (IDS), [232](#c6.xhtml#p232)
    *   Intrusion Prevention System (IPS), [232](#c6.xhtml#p232)
    *   Invisible Internet Project (I2P), [77](#c2.xhtml#p77)
    *   IoTs, see [Internet of things](#index.xhtml#see674)
    *   IP address, see [Internet Protocol address](#index.xhtml#see696)
    *   ipconfig, [196](#c5.xhtml#p196)
    *   iPerf [3](#c1.xhtml#p3), [195](#c5.xhtml#p195)
    *   iPhone OS, [316](#c8.xhtml#p316)
    *   IPS, see [Intrusion Prevention System](#index.xhtml#see711)
    *   IP spoofing, [250](#c6.xhtml#p250)–[251](#c6.xhtml#p251)
    *   IPv [4](#c1.xhtml#p4), see Internet Protocol [4](#c1.xhtml#p4)
    *   IPv [6](#c1.xhtml#p6), see Internet Protocol [6](#c1.xhtml#p6)
    *   ISO, see [International Organization for Standardization](#index.xhtml#see667)
    *   ISP, see [Internet service provider](#index.xhtml#see700)
    *   J
    *   Jamming Wi-Fi signals, [253](#c6.xhtml#p253)
    *   Java API framework, [319](#c8.xhtml#p319)
    *   JavaScript, [246](#c6.xhtml#p246)
    *   JSTOR, [116](#c4.xhtml#p116)
    *   Jurisdiction, [88](#c3.xhtml#p88)–[89](#c3.xhtml#p89)
    *   K
    *    Katz v. United States, [151](#c4.xhtml#p151)
    *   Kenbak- [1](#c1.xhtml#p1), [39](#c1.xhtml#p39)
    *   Key Privacy Laws, United States, [107](#c4.xhtml#p107)–[108](#c4.xhtml#p108), [157](#c4.xhtml#p157)
    *   Children’s Online Privacy Protection Act of 1998 (COPPA), [162](#c4.xhtml#p162)–[164](#c4.xhtml#p164)
    *   Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003 (CAN-SPAM Act), [158](#c4.xhtml#p158)–[159](#c4.xhtml#p159)
    *   Fraud and Related Activity in Connection with Access Devices, [160](#c4.xhtml#p160)–[161](#c4.xhtml#p161)
    *   Fraud and Related Activity in Connection with Electronic Mail, [159](#c4.xhtml#p159)–[160](#c4.xhtml#p160)
    *   Fraud and Related Activity in Connection with Identification Documents, Authentication Features, and Information, [161](#c4.xhtml#p161)–[162](#c4.xhtml#p162)
    *   Privacy Act of 1974, [158](#c4.xhtml#p158)
    *   Video Privacy Protection Act (VPPA) of 1988, [164](#c4.xhtml#p164)–[165](#c4.xhtml#p165)
    *   Klez worm, [64](#c2.xhtml#p64)
    *   Korn/Ferry International (KFI), [113](#c4.xhtml#p113), [114](#c4.xhtml#p114)
    *   L
    *   LAN, see [Local Area Network](#index.xhtml#see800)
    *   Large denial-of-service, [63](#c2.xhtml#p63)
    *   Laws, Standards, and Regulations
    *   anti-hacking laws, [106](#c4.xhtml#p106)
    *   Computer Hacking Laws, [117](#c4.xhtml#p117)
    *   Digital Millennium Copyright Act (DMCA), [119](#c4.xhtml#p119)–[125](#c4.xhtml#p125)
    *   Economic Espionage Act of 1996 (EEA), [117](#c4.xhtml#p117)–[119](#c4.xhtml#p119)
    *   Federal Computer Fraud and Abuse Act, [109](#c4.xhtml#p109)–[117](#c4.xhtml#p117)
    *   current legislative framework, United States, [106](#c4.xhtml#p106)–[109](#c4.xhtml#p109)
    *   Data Security Laws and Regulations, [125](#c4.xhtml#p125)–[126](#c4.xhtml#p126)
    *   Federal Trade Commission Act, [132](#c4.xhtml#p132)–[134](#c4.xhtml#p134)
    *   Health Information Technology, [131](#c4.xhtml#p131)–[132](#c4.xhtml#p132)
    *   laws affecting financial institutions, [134](#c4.xhtml#p134)–[137](#c4.xhtml#p137)
    *   laws affecting utilities, [138](#c4.xhtml#p138)–[140](#c4.xhtml#p140)
    *   laws dealing with healthcare, [128](#c4.xhtml#p128)–[131](#c4.xhtml#p131)
    *   Federal Government contractors, cybersecurity requirements for, [144](#c4.xhtml#p144)
    *   Federal Information Security Modernization Act of 2014, [145](#c4.xhtml#p145)–[146](#c4.xhtml#p146)
    *   NIST Information Security Controls, [146](#c4.xhtml#p146)–[147](#c4.xhtml#p147)
    *   Fourth Amendment, [148](#c4.xhtml#p148)–[149](#c4.xhtml#p149)
    *   electronic surveillance, [151](#c4.xhtml#p151)–[153](#c4.xhtml#p153)
    *   good faith exception, [153](#c4.xhtml#p153)
    *   search and seizure, [149](#c4.xhtml#p149)–[150](#c4.xhtml#p150)
    *   Search Warrant Rule, [150](#c4.xhtml#p150)–[151](#c4.xhtml#p151)
    *   USA PATRIOT Act, [153](#c4.xhtml#p153)–[154](#c4.xhtml#p154)
    *   Key Privacy Laws, United States, [157](#c4.xhtml#p157)
    *   Children’s Online Privacy Protection Act of 1998 (COPPA), [162](#c4.xhtml#p162)–[164](#c4.xhtml#p164)
    *   Controlling the Assault of Non-Solicited Pornography and Marketing Act of 2003 (CAN-SPAM Act), [158](#c4.xhtml#p158)–[159](#c4.xhtml#p159)
    *   Fraud and Related Activity in Connection with Access Devices, [160](#c4.xhtml#p160)–[161](#c4.xhtml#p161)
    *   Fraud and Related Activity in Connection with Electronic Mail, [159](#c4.xhtml#p159)–[160](#c4.xhtml#p160)
    *   Fraud and Related Activity in Connection with Identification Documents, Authentication Features, and Information, [161](#c4.xhtml#p161)–[162](#c4.xhtml#p162)
    *   Privacy Act of 1974, [158](#c4.xhtml#p158)
    *   Video Privacy Protection Act (VPPA) of 1988, [164](#c4.xhtml#p164)–[165](#c4.xhtml#p165)
    *   public and private sector entities partnerships, [140](#c4.xhtml#p140)
    *   Cybersecurity and Infrastructure Security Agency, [142](#c4.xhtml#p142)
    *   Cybersecurity Enhancement Act of 2014 (CEA), [143](#c4.xhtml#p143)
    *   Cybersecurity Information Sharing Act of 2015 (CISA), [141](#c4.xhtml#p141)–[142](#c4.xhtml#p142)
    *   National Cybersecurity and Critical Infrastructure Protection Act of 2014 (NCPA), [143](#c4.xhtml#p143)–[144](#c4.xhtml#p144)
    *   Laws affecting utilities
    *   Federal Energy Regulatory Commission (FERC), [138](#c4.xhtml#p138)–[139](#c4.xhtml#p139)
    *   Nuclear Regulatory Commission, [140](#c4.xhtml#p140)
    *   Law types
    *   Administrative law, [99](#c3.xhtml#p99)–[100](#c3.xhtml#p100)
    *   Civil law, [100](#c3.xhtml#p100)
    *   Criminal law, [100](#c3.xhtml#p100)–[102](#c3.xhtml#p102)
    *   Layer 7 DDoS Simulator (DDOSIM), [245](#c6.xhtml#p245)
    *   LCD, see [Liquid crystal display](#index.xhtml#see796)
    *   LED, see [Light-emitting diode](#index.xhtml#see792)
    *   Legislative framework, United States, [106](#c4.xhtml#p106)–[109](#c4.xhtml#p109)
    *   Light-emitting diode (LED), [315](#c8.xhtml#p315)
    *   Light sensor, [315](#c8.xhtml#p315)
    *   Link local unicast addresses, [192](#c5.xhtml#p192)
    *   Linux kernel layer, [318](#c8.xhtml#p318)
    *   Liquid crystal display (LCD), [314](#c8.xhtml#p314)–[315](#c8.xhtml#p315)
    *   LIR, see [Local Internet Registries](#index.xhtml#see802)
    *   Litigation, [100](#c3.xhtml#p100)
    *   Local Area Identity (LAI), [328](#c8.xhtml#p328)
    *   Local Area Network (LAN), [186](#c5.xhtml#p186), [200](#c5.xhtml#p200), [301](#c7.xhtml#p301)
    *   Local government, [408](#appendixG.xhtml#p408)
    *   Local Internet Registries (LIR), [187](#c5.xhtml#p187)
    *   Logic gates, [15](#c1.xhtml#p15), [17](#c1.xhtml#p17)–[19](#c1.xhtml#p19)
    *   LOIC, see [Low Orbit Ion Cannon](#index.xhtml#see810)
    *   Long-Term Evolution (LTE), [311](#c8.xhtml#p311), [312](#c8.xhtml#p312)
    *   LoRa/Bluetooth-enabled Electronic Reade, [282](#c7.xhtml#p282)
    *   Lorenz-SZ-40/SZ-42 machine, [224](#c6.xhtml#p224), [225](#c6.xhtml#p225)
    *   Loss, [349](#appendixA.xhtml#p349)–[350](#appendixA.xhtml#p350), [413](#appendixH.xhtml#p413)
    *   Lossy compression, [22](#c1.xhtml#p22)–[23](#c1.xhtml#p23)
    *   Low Orbit Ion Cannon (LOIC), [245](#c6.xhtml#p245)
    *   Low Power Wide Area Network (LPWAN), [297](#c7.xhtml#p297)
    *   Low Power Wireless Personal Area Networks (6LoWPAN), [296](#c7.xhtml#p296)
    *   LPWAN, see [Low Power Wide Area Network](#index.xhtml#see811)
    *   LTE, see [Long-Term Evolution](#index.xhtml#see805)
    *   LTE-advance (LTE-A), [297](#c7.xhtml#p297)
    *   M
    *   MAC, see [Media access control](#index.xhtml#see835)
    *   Machine learning (ML), [45](#c1.xhtml#p45), [49](#c1.xhtml#p49), [73](#c2.xhtml#p73), [79](#c2.xhtml#p79)–[80](#c2.xhtml#p80)
    *   Machine-to-machine (M2M) protocol, [295](#c7.xhtml#p295)
    *   Macintosh, [40](#c1.xhtml#p40)–[42](#c1.xhtml#p42)
    *   Magnetic field sensor, [315](#c8.xhtml#p315)
    *   Malicious cyber command and control, [407](#appendixG.xhtml#p407)
    *   Malicious reconnaissance, [408](#appendixG.xhtml#p408)
    *   Malicious text messages, [335](#c8.xhtml#p335)
    *   Malware, [56](#c2.xhtml#p56), [246](#c6.xhtml#p246)–[248](#c6.xhtml#p248), [336](#c8.xhtml#p336)
    *   MAN, see [Metropolitan Area Network](#index.xhtml#see846)
    *   Management certifications, [417](#appendixI.xhtml#p417)
    *   Mandate, defined, [397](#appendixE.xhtml#p397)
    *   Man-in-the middle (MITM) attack, [250](#c6.xhtml#p250), [254](#c6.xhtml#p254), [336](#c8.xhtml#p336)
    *   Manufacturing sector, [282](#c7.xhtml#p282)–[284](#c7.xhtml#p284)
    *   Massachusetts Institute of Technology (MIT), [116](#c4.xhtml#p116)
    *   MDY industries, [124](#c4.xhtml#p124)–[125](#c4.xhtml#p125)
    *    MDY Industries, Inc. LLC v. Blizzard Entertainment, [124](#c4.xhtml#p124)
    *   Mechanical bird, see [Pigeon](#index.xhtml#see1055)
    *   Media access control (MAC), [182](#c5.xhtml#p182), [297](#c7.xhtml#p297)
    *   address, [192](#c5.xhtml#p192)–[195](#c5.xhtml#p195)
    *   spoofing, [250](#c6.xhtml#p250)–[252](#c6.xhtml#p252)
    *   Media service layer, [322](#c8.xhtml#p322)–[323](#c8.xhtml#p323)
    *   Melissa virus, [62](#c2.xhtml#p62)
    *   Memory hierarchy, [21](#c1.xhtml#p21), [22](#c1.xhtml#p22)
    *   Mesh network, [217](#c5.xhtml#p217)
    *   Mesh topology, [203](#c5.xhtml#p203)–[204](#c5.xhtml#p204)
    *   Message Digest Algorithm 5 (MD5), [272](#c6.xhtml#p272)
    *   Message Exchange and Communication, [294](#c7.xhtml#p294)
    *   Message Queuing Telemetry Transport (MQTT), [295](#c7.xhtml#p295)
    *   Metropolitan Area Network (MAN), [200](#c5.xhtml#p200), [301](#c7.xhtml#p301)
    *   MFA, see [Multi-factor authentication](#index.xhtml#see880)
    *   Michelangelo virus, [62](#c2.xhtml#p62)
    *   Microchip, [37](#c1.xhtml#p37)
    *   Microphone, [314](#c8.xhtml#p314)
    *   Microprocessors, [18](#c1.xhtml#p18)
    *   Microwave links, [323](#c8.xhtml#p323)–[324](#c8.xhtml#p324)
    *   Mirai malware, [71](#c2.xhtml#p71), [78](#c2.xhtml#p78), [302](#c7.xhtml#p302)
    *   Misdemeanor, [101](#c3.xhtml#p101)
    *    Missouri v. McNeely, [150](#c4.xhtml#p150)
    *   MITRE Corporation, [236](#c6.xhtml#p236)
    *   ML, see [Machine learning](#index.xhtml#see818)
    *   Mobile devices, [307](#c8.xhtml#p307), [313](#c8.xhtml#p313)
    *   Mobile device tracking location, [329](#c8.xhtml#p329)–[332](#c8.xhtml#p332)
    *   Mobile directory number (MDN), [325](#c8.xhtml#p325)
    *   Mobile equipment identifier (MEID), [325](#c8.xhtml#p325)
    *   Mobile identification number (MIN), [225](#c6.xhtml#p225)
    *   Mobile phones
    *   applications (apps), [316](#c8.xhtml#p316)
    *   cellular network, [322](#c8.xhtml#p322)–[332](#c8.xhtml#p332)
    *   components, [313](#c8.xhtml#p313)–[316](#c8.xhtml#p316)
    *   history and milestones, [308](#c8.xhtml#p308)–[313](#c8.xhtml#p313)
    *   operating systems (OS), [316](#c8.xhtml#p316)
    *   platform architectures, [317](#c8.xhtml#p317)–[322](#c8.xhtml#p322)
    *   security, [332](#c8.xhtml#p332)–[333](#c8.xhtml#p333)
    *   executable security, [335](#c8.xhtml#p335)–[338](#c8.xhtml#p338)
    *   physical security, [333](#c8.xhtml#p333)–[335](#c8.xhtml#p335)
    *   Mobile Telephone Switching Office (MTSO), [326](#c8.xhtml#p326)
    *   Modern computing adoption stages, [276](#c7.xhtml#p276), [277](#c7.xhtml#p277)
    *   Monitor, [408](#appendixG.xhtml#p408)
    *   Morris worm, [62](#c2.xhtml#p62), [113](#c4.xhtml#p113)
    *   MQTT, see [Message Queuing Telemetry Transport](#index.xhtml#see845)
    *   MTSO, see [Mobile Telephone Switching Office](#index.xhtml#see873)
    *   Multicast addresses, [191](#c5.xhtml#p191)
    *   Multi-factor authentication (MFA), [261](#c6.xhtml#p261)
    *   Multiple, [413](#appendixH.xhtml#p413)
    *   Mydoom, [65](#c2.xhtml#p65)
    *   N
    *   NASA, see [National Aeronautics and Space Administration](#index.xhtml#see886)
    *   NAT, see [Network Address Translation](#index.xhtml#see933)
    *   National Aeronautics and Space Administration (NASA), [3](#c1.xhtml#p3), [4](#c1.xhtml#p4)
    *   National Bureau of Standards (NBS), [126](#c4.xhtml#p126)
    *   National Conference of State Legislatures (NCSL), [117](#c4.xhtml#p117)
    *   National Cybersecurity and Critical Infrastructure Protection Act of 2014 (NCPA), [143](#c4.xhtml#p143)
    *   National Institute of Standards and Technology (NIST), [127](#c4.xhtml#p127)–[128](#c4.xhtml#p128), [143](#c4.xhtml#p143), [303](#c7.xhtml#p303)
    *   information security controls, [146](#c4.xhtml#p146)
    *   logo, [127](#c4.xhtml#p127)
    *   National Institute of Standards and Technology Cybersecurity Framework, [126](#c4.xhtml#p126)–[128](#c4.xhtml#p128)
    *   National Internet Registries (NIR), [187](#c5.xhtml#p187)
    *   National Metrological Institute (NMI), [126](#c4.xhtml#p126)
    *   National Science Foundation (NSF), [175](#c5.xhtml#p175)
    *   National Science Foundation Network (NSFNET), [63](#c2.xhtml#p63), [174](#c5.xhtml#p174)
    *   National Security Agency (NSA), [72](#c2.xhtml#p72), [273](#c6.xhtml#p273)
    *   Native C/C++ libraries, [318](#c8.xhtml#p318)–[319](#c8.xhtml#p319)
    *   NCPA, see [National Cybersecurity and Critical Infrastructure Protection Act of 2014](#index.xhtml#see889)
    *   Near Field Communication (NFC), [261](#c6.xhtml#p261), [298](#c7.xhtml#p298)
    *   NERC, see [North American Electric Reliability Corporation](#index.xhtml#see983)
    *   netstat, [196](#c5.xhtml#p196)
    *   Network
    *   access layer, [296](#c7.xhtml#p296)–[298](#c7.xhtml#p298)
    *   architecture, [181](#c5.xhtml#p181)
    *   attacks, [302](#c7.xhtml#p302)
    *   hardware, [181](#c5.xhtml#p181)
    *   interface, [215](#c5.xhtml#p215)–[216](#c5.xhtml#p216)
    *   layer, [192](#c5.xhtml#p192), [207](#c5.xhtml#p207), [291](#c7.xhtml#p291)
    *   range, [300](#c7.xhtml#p300)
    *   security, [226](#c6.xhtml#p226)
    *   software, [181](#c5.xhtml#p181)
    *   Spoofing, [338](#c8.xhtml#p338)
    *   statistics, [195](#c5.xhtml#p195)
    *   switch, [198](#c5.xhtml#p198)
    *   topology
    *   bus network topology, [202](#c5.xhtml#p202), [203](#c5.xhtml#p203)
    *   mesh topology, [203](#c5.xhtml#p203)–[204](#c5.xhtml#p204)
    *   point-to-point topology, [204](#c5.xhtml#p204)
    *   ring topology, [204](#c5.xhtml#p204), [205](#c5.xhtml#p205)
    *   star network topology, [204](#c5.xhtml#p204)–[206](#c5.xhtml#p206)
    *   types
    *   Campus Area Network (CAN), [199](#c5.xhtml#p199)
    *   Local Area Network (LAN), [200](#c5.xhtml#p200)
    *   Metropolitan Area Network (MAN), [200](#c5.xhtml#p200)
    *   Personal Area Network (PAN), [199](#c5.xhtml#p199)–[200](#c5.xhtml#p200)
    *   Virtual Local Area Network (VLAN), [201](#c5.xhtml#p201)
    *   Virtual Private Network (VPN), [202](#c5.xhtml#p202)
    *   Wide Area Network (WAN), [200](#c5.xhtml#p200)
    *   Wireless Local Area Network (WLAN), [201](#c5.xhtml#p201)
    *   utilities, [195](#c5.xhtml#p195)–[198](#c5.xhtml#p198)
    *   Network Address Translation (NAT), [190](#c5.xhtml#p190)–[191](#c5.xhtml#p191), [260](#c6.xhtml#p260)
    *   Network Identification (NID), [325](#c8.xhtml#p325)
    *   Networking environment
    *   computer networking, [173](#c5.xhtml#p173)–[175](#c5.xhtml#p175)
    *   advantages and disadvantages, [178](#c5.xhtml#p178)–[179](#c5.xhtml#p179)
    *   computer network components and terminology, [179](#c5.xhtml#p179)–[188](#c5.xhtml#p188)
    *   internet, [176](#c5.xhtml#p176)–[179](#c5.xhtml#p179)
    *   IPv6 anatomy, [188](#c5.xhtml#p188)–[195](#c5.xhtml#p195)
    *   network utilities, [195](#c5.xhtml#p195)–[198](#c5.xhtml#p198)
    *   protocol, [175](#c5.xhtml#p175)–[176](#c5.xhtml#p176)
    *   World Wide Web (WWW), [176](#c5.xhtml#p176)–[179](#c5.xhtml#p179)
    *   internet protocol suite (TPC/IP), [210](#c5.xhtml#p210)–[212](#c5.xhtml#p212), [215](#c5.xhtml#p215)
    *   transmission control protocol (TCP), [212](#c5.xhtml#p212)–[213](#c5.xhtml#p213)
    *   user datagram protocol (UDP), [213](#c5.xhtml#p213)–[216](#c5.xhtml#p216)
    *   network topology
    *   bus network topology, [202](#c5.xhtml#p202), [203](#c5.xhtml#p203)
    *   mesh topology, [203](#c5.xhtml#p203)–[204](#c5.xhtml#p204)
    *   point-to-point topology, [204](#c5.xhtml#p204)
    *   ring topology, [204](#c5.xhtml#p204), [205](#c5.xhtml#p205)
    *   star network topology, [204](#c5.xhtml#p204)–[206](#c5.xhtml#p206)
    *   network types
    *   Campus Area Network (CAN), [199](#c5.xhtml#p199)
    *   Local Area Network (LAN), [200](#c5.xhtml#p200)
    *   Metropolitan Area Network (MAN), [200](#c5.xhtml#p200)
    *   Personal Area Network (PAN), [199](#c5.xhtml#p199)–[200](#c5.xhtml#p200)
    *   Virtual Local Area Network (VLAN), [201](#c5.xhtml#p201)
    *   Virtual Private Network (VPN), [202](#c5.xhtml#p202)
    *   Wide Area Network (WAN), [200](#c5.xhtml#p200)
    *   Wireless Local Area Network (WLAN), [201](#c5.xhtml#p201)
    *   open systems interconnection (OSI) model, [206](#c5.xhtml#p206)–[211](#c5.xhtml#p211)
    *   Network Interface Card (NIC), [192](#c5.xhtml#p192), [195](#c5.xhtml#p195)
    *   Network interface controller (NIC), [251](#c6.xhtml#p251)
    *   Neural networks, [46](#c1.xhtml#p46)
    *   Newton’s third law, [76](#c2.xhtml#p76)
    *   Next-generation firewall (NGFW), [260](#c6.xhtml#p260)–[261](#c6.xhtml#p261)
    *   Next header, [184](#c5.xhtml#p184)
    *   NeXTSTEP operating system, [319](#c8.xhtml#p319)
    *   NFC, see [Near Field Communication](#index.xhtml#see901)
    *   NGFW, see [Next-generation firewall](#index.xhtml#see967)
    *   NIC, see [Network Interface Card](#index.xhtml#see963); [Network interface controller](#index.xhtml#see964)
    *   Nippon Telephone & Telegraph (NTT), [309](#c8.xhtml#p309)
    *   NIR, see [National Internet Registries](#index.xhtml#see894)
    *   NIST, see [National Institute of Standards and Technology](#index.xhtml#see890)
    *   Nmap, [195](#c5.xhtml#p195)
    *   NMT, see [Nordic Mobile Telephone](#index.xhtml#see982)
    *   Node, [180](#c5.xhtml#p180)
    *   Non-Federal entity, [408](#appendixG.xhtml#p408)
    *   Non-public personal information, [135](#c4.xhtml#p135)
    *   Non-Volatile Memory, see Read-only memory
    *   Nordic Mobile Telephone (NMT), [309](#c8.xhtml#p309)
    *   North American Electric Reliability Corporation (NERC), [139](#c4.xhtml#p139)
    *   NOT-gate, [17](#c1.xhtml#p17)
    *   NotPetya, [71](#c2.xhtml#p71), [72](#c2.xhtml#p72)
    *   NRC, see [Nuclear Regulatory Commission](#index.xhtml#see991)
    *   NSA, see [National Security Agency](#index.xhtml#see898)
    *   NSF, see [National Science Foundation](#index.xhtml#see896)
    *   NSFNET, see [National Science Foundation Network](#index.xhtml#see897)
    *   NTT, see [Nippon Telephone & Telegraph](#index.xhtml#see973)
    *   Nuclear Regulatory Commission (NRC), [140](#c4.xhtml#p140)
    *   Nybble, [11](#c1.xhtml#p11)
    *   O
    *   Object Management Group (OMG), [295](#c7.xhtml#p295)
    *   OCR, see [Office for Civil Rights](#index.xhtml#see997)
    *   OFDMA, see [Orthogonal Frequency Division Multiple Access](#index.xhtml#see1011)
    *   Office for Civil Rights (OCR), [130](#c4.xhtml#p130)
    *   Office of Management and Budget (OMB), [145](#c4.xhtml#p145)
    *   Office of the Law Revision Counsel (OLRC), [93](#c3.xhtml#p93)
    *   OMB, see [Office of Management and Budget](#index.xhtml#see998)
    *   OMG, see [Object Management Group](#index.xhtml#see994)
    *   1G analog automated cellular network, [309](#c8.xhtml#p309)
    *   Online anonymity, [89](#c3.xhtml#p89)–[90](#c3.xhtml#p90)
    *   Online Copyright Infringement Liability Limitation Act, [120](#c4.xhtml#p120)
    *   Open systems interconnection (OSI) model, [206](#c5.xhtml#p206)–[211](#c5.xhtml#p211), [215](#c5.xhtml#p215)
    *   Operating systems (OS), [316](#c8.xhtml#p316)
    *   Optical devices, [21](#c1.xhtml#p21)
    *   Ordinance, [95](#c3.xhtml#p95)–[96](#c3.xhtml#p96)
    *   Organizationally Unique Identifier (OUI), [194](#c5.xhtml#p194)
    *   OR-gate, [18](#c1.xhtml#p18)
    *   Orthogonal Frequency Division Multiple Access (OFDMA), [312](#c8.xhtml#p312)
    *   OS, see [Operating systems](#index.xhtml#see1006)
    *   Osborne [1](#c1.xhtml#p1), [40](#c1.xhtml#p40)
    *   OSI, see Open systems interconnection model
    *   OUI, see [Organizationally Unique Identifier](#index.xhtml#see1009)
    *   P
    *   P2P, see [Peer-to-peer](#index.xhtml#see1034)
    *   Packet, [192](#c5.xhtml#p192)
    *   Packet-filtering firewalls, [259](#c6.xhtml#p259)–[260](#c6.xhtml#p260)
    *   Packets, [208](#c5.xhtml#p208)
    *   PAN, see [Personal Area Network](#index.xhtml#see1039)
    *   Part 681—Identity Theft Rules, [401](#appendixF.xhtml#p401)–[404](#appendixF.xhtml#p404)
    *   Partial mesh topology, [203](#c5.xhtml#p203), [204](#c5.xhtml#p204)
    *   Passive attack, [235](#c6.xhtml#p235)
    *   Password
    *   authentication, [261](#c6.xhtml#p261)
    *   trafficking, [112](#c4.xhtml#p112)
    *   Payload, [216](#c5.xhtml#p216)
    *   length, [184](#c5.xhtml#p184)
    *   PCB, see [Printed circuit board](#index.xhtml#see1072)
    *   PDA, see [Personal Digital Assistants](#index.xhtml#see1040)
    *   PDF, see [Portable Document Format](#index.xhtml#see1065)
    *   PDU, see [Protocol Data Unit](#index.xhtml#see1089)
    *   Peer-to-peer (P2P), [143](#c4.xhtml#p143)
    *   Pegasus, [335](#c8.xhtml#p335)
    *   Pen register, [156](#c4.xhtml#p156)
    *   Perception layer, [291](#c7.xhtml#p291)
    *   Person, [350](#appendixA.xhtml#p350)
    *   Personal Area Network (PAN), [199](#c5.xhtml#p199)–[200](#c5.xhtml#p200), [300](#c7.xhtml#p300)
    *   Personal Digital Assistants (PDA), [42](#c1.xhtml#p42)
    *   Petya, [71](#c2.xhtml#p71)
    *   Pew Research Center, [44](#c1.xhtml#p44)
    *   PGP, see [Pretty Good Privacy](#index.xhtml#see1070)
    *   Pharming, [149](#c4.xhtml#p149)–[150](#c4.xhtml#p150)
    *   Phase I, [60](#c2.xhtml#p60)–[62](#c2.xhtml#p62)
    *   Phase II, [62](#c2.xhtml#p62)
    *   Phase III, [63](#c2.xhtml#p63)–[67](#c2.xhtml#p67)
    *   Phase IV, [67](#c2.xhtml#p67)–[73](#c2.xhtml#p73)
    *   PHI, see [Protected Health Information](#index.xhtml#see1085)
    *   Phishing, [56](#c2.xhtml#p56), [248](#c6.xhtml#p248)–[250](#c6.xhtml#p250), [253](#c6.xhtml#p253)
    *   attack, [337](#c8.xhtml#p337)
    *   Physical
    *   attack, [302](#c7.xhtml#p302)
    *   layer, [201](#c5.xhtml#p201)
    *   Pigeon, [32](#c1.xhtml#p32)
    *   ping, [196](#c5.xhtml#p196)
    *   Ping flood attack, [239](#c6.xhtml#p239)
    *   Ping of Death, [242](#c6.xhtml#p242)
    *   Pixels, [24](#c1.xhtml#p24)
    *   Plaintiff, [100](#c3.xhtml#p100)
    *   Point-to-Point Protocol (PPP), [262](#c6.xhtml#p262)
    *   Point-to-point topology, [204](#c5.xhtml#p204)
    *   Polybius Square, [224](#c6.xhtml#p224)
    *   Port, [192](#c5.xhtml#p192)
    *   Portable Document Format (PDF), [246](#c6.xhtml#p246)
    *   Potentially Unwanted Program (PUP), [237](#c6.xhtml#p237)
    *   Power supply, [287](#c7.xhtml#p287)
    *   Power usage, [300](#c7.xhtml#p300)
    *   Presentation layer, [207](#c5.xhtml#p207)
    *   Pretty Good Privacy (PGP), [233](#c6.xhtml#p233)
    *   Prey Anti-Theft, [329](#c8.xhtml#p329)
    *   Printed circuit board (PCB), [314](#c8.xhtml#p314)
    *   Privacy Act of 1974, [158](#c4.xhtml#p158)
    *   Privacy obligation policy, [135](#c4.xhtml#p135)
    *   Private entity, [409](#appendixG.xhtml#p409)
    *   Private IP address, [190](#c5.xhtml#p190)–[191](#c5.xhtml#p191)
    *   Private laws, [93](#c3.xhtml#p93)
    *   Probable cause, [103](#c3.xhtml#p103)
    *   Processing layer, [291](#c7.xhtml#p291)
    *   Professional analog video cassette recorder, [369](#appendixB.xhtml#p369)
    *   Profiles, [128](#c4.xhtml#p128)
    *   Prosecutor, [81](#c2.xhtml#p81)
    *   PROTECT Act of 2003, [80](#c2.xhtml#p80)
    *   Protected computer, [348](#appendixA.xhtml#p348)–[349](#appendixA.xhtml#p349)
    *   Protected Health Information (PHI), [130](#c4.xhtml#p130)–[131](#c4.xhtml#p131)
    *   Protocol, [175](#c5.xhtml#p175)–[176](#c5.xhtml#p176), [192](#c5.xhtml#p192), [232](#c6.xhtml#p232)
    *   attacks, [238](#c6.xhtml#p238)
    *   converters, [185](#c5.xhtml#p185)
    *   Protocol Data Unit (PDU), [192](#c5.xhtml#p192), [194](#c5.xhtml#p194)
    *   Proximity sensor, [315](#c8.xhtml#p315)
    *   Proxy firewalls, [260](#c6.xhtml#p260)
    *   Public and private sector entities partnerships, [140](#c4.xhtml#p140)
    *   Cybersecurity and Infrastructure Security Agency, [142](#c4.xhtml#p142)
    *   Cybersecurity Enhancement Act of 2014 (CEA), [143](#c4.xhtml#p143)–[144](#c4.xhtml#p144)
    *   Cybersecurity Information Sharing Act of 2015 (CISA), [141](#c4.xhtml#p141)–[142](#c4.xhtml#p142)
    *   National Cybersecurity and Critical Infrastructure Protection Act of 2014 (NCPA), [143](#c4.xhtml#p143)
    *   Public IP address, [190](#c5.xhtml#p190)
    *   Public Key Cryptography (PKC), see [Asymmetric encryption](#index.xhtml#see108)
    *   Public laws, [93](#c3.xhtml#p93)
    *   Public–Private Collaboration on Cybersecurity, [143](#c4.xhtml#p143)
    *   Public Wi-Fi security issues, [254](#c6.xhtml#p254)
    *   PUP, see [Potentially Unwanted Program](#index.xhtml#see1066)
    *   PuTTY, [195](#c5.xhtml#p195)
    *   Q
    *   Quantum computing, [29](#c1.xhtml#p29)–[30](#c1.xhtml#p30)
    *   Qubits, [29](#c1.xhtml#p29)
    *   R
    *   Radiofrequency (RF), [326](#c8.xhtml#p326)
    *   Radio-frequency identification (RFID), [276](#c7.xhtml#p276), [297](#c7.xhtml#p297)
    *   Rainbow table, [253](#c6.xhtml#p253)
    *   Random Access Memory (RAM), [21](#c1.xhtml#p21)
    *   Ransomware, [56](#c2.xhtml#p56)
    *   attack, [247](#c6.xhtml#p247)
    *   Read only memory (ROM), [192](#c5.xhtml#p192), [314](#c8.xhtml#p314)
    *   Reaver tool, [253](#c6.xhtml#p253)
    *   Received signal strength indicator (RSSI), [332](#c8.xhtml#p332)
    *   Red Flags Rule, [137](#c4.xhtml#p137)
    *   Regional Internet Registries (RIR), [187](#c5.xhtml#p187)
    *   Remote data storage, [21](#c1.xhtml#p21)
    *   Remote monitoring, [281](#c7.xhtml#p281)
    *   Removable media, [20](#c1.xhtml#p20)
    *   Repeated violations, [374](#appendixB.xhtml#p374)
    *   Repeater, [197](#c5.xhtml#p197)
    *   Retail sector, [284](#c7.xhtml#p284)
    *   RFID, see [Radio-frequency identification](#index.xhtml#see1109)
    *   RGB (Red, Green, and Blue), [25](#c1.xhtml#p25), [26](#c1.xhtml#p26)
    *    Riley v. California, [150](#c4.xhtml#p150)
    *   Ring topology, [204](#c5.xhtml#p204), [205](#c5.xhtml#p205)
    *   RIR, see [Regional Internet Registries](#index.xhtml#see1118)
    *   ROM, see [Read only memory](#index.xhtml#see1114)
    *   Routers, [197](#c5.xhtml#p197), [217](#c5.xhtml#p217)
    *   Routing, [216](#c5.xhtml#p216)
    *   Routing prefix, [188](#c5.xhtml#p188)
    *   Routing Protocol (RPL), [296](#c7.xhtml#p296)
    *   RPL, see [Routing Protocol](#index.xhtml#see1134)
    *   RSSI, see [Received signal strength indicator](#index.xhtml#see1116)
    *   R-U-Dead-Yet, [245](#c6.xhtml#p245)
    *   S
    *   SaaS, see [Software-as-a-Service](#index.xhtml#see1200)
    *   SCA, see [Stored Communications Act](#index.xhtml#see1227)
    *   SCADA, see [Supervisory Control and Data Acquisition](#index.xhtml#see1237)
    *   SC-FDMA, see [Single Carrier Frequency Division Multiple Access](#index.xhtml#see1180)
    *   Screen resolution, [28](#c1.xhtml#p28)
    *   Script kiddies/amateurs, [232](#c6.xhtml#p232)
    *   Scytale, [223](#c6.xhtml#p223)
    *   SDK, see [Software Development Kit](#index.xhtml#see1203)
    *   SD-WAN, see [Software-Defined Wide Area Network](#index.xhtml#see1202)
    *   Search warrant, [103](#c3.xhtml#p103)
    *   SEC, see [Securities and Exchange Commission](#index.xhtml#see1157)
    *   Sec. 13410. Improved enforcement, [385](#appendixD.xhtml#p385)–[390](#appendixD.xhtml#p390)
    *   Secret Key Cryptography (SKC), see [Symmetric encryption method](#index.xhtml#see1240)
    *   Sectional symbol, [94](#c3.xhtml#p94)
    *   Secure Hash Algorithm (SHA), [273](#c6.xhtml#p273)
    *   Secure Shell (SSH) protocol, [233](#c6.xhtml#p233)
    *   Secure Sockets Layer (SSL), [233](#c6.xhtml#p233), [318](#c8.xhtml#p318)
    *   Securing the Nation against Cyber Attack, [143](#c4.xhtml#p143)
    *   Securities and Exchange Commission (SEC), [136](#c4.xhtml#p136), [137](#c4.xhtml#p137)
    *   Securities Exchange Act of 1934
    *   section [15](#c1.xhtml#p15), [349](#appendixA.xhtml#p349)
    *   Security
    *   audit, [233](#c6.xhtml#p233)
    *   control, [409](#appendixG.xhtml#p409)
    *   testing, [366](#appendixB.xhtml#p366)
    *   threat, [233](#c6.xhtml#p233)
    *   vulnerability, [409](#appendixG.xhtml#p409)
    *   Security Act (42 U.S.C. 1320d–5(a)(1))
    *   section 1176(a)(1), [387](#appendixD.xhtml#p387)
    *   Sender policy framework (SPF), [185](#c5.xhtml#p185)
    *   Sensors, [286](#c7.xhtml#p286), [315](#c8.xhtml#p315)
    *   Servers, [180](#c5.xhtml#p180), [197](#c5.xhtml#p197)
    *   Session layer, [207](#c5.xhtml#p207)–[208](#c5.xhtml#p208)
    *   Sexually oriented material, [159](#c4.xhtml#p159)
    *   SHA, see [Secure Hash Algorithm](#index.xhtml#see1153)
    *   Shadow Brokers, [72](#c2.xhtml#p72)
    *   Short Message Service Center (SMSC), [328](#c8.xhtml#p328)
    *   SID, see [System Identification number](#index.xhtml#see1248)
    *   Signum sectionis, [94](#c3.xhtml#p94)
    *   SIM, see Subscriber identity module card
    *   SIM-jacking, [337](#c8.xhtml#p337)
    *   Single Carrier Frequency Division Multiple Access (SC-FDMA), [312](#c8.xhtml#p312)
    *   Single firewall model, [257](#c6.xhtml#p257)
    *   Siphon float, [32](#c1.xhtml#p32)
    *   64-bit processor, [20](#c1.xhtml#p20)
    *   Slip laws, [93](#c3.xhtml#p93)
    *   Slowloris attack, [243](#c6.xhtml#p243)–[244](#c6.xhtml#p244)
    *   Smart home automation, [285](#c7.xhtml#p285)
    *   Smartphone display, [314](#c8.xhtml#p314)
    *   Smart structures, [284](#c7.xhtml#p284)–[285](#c7.xhtml#p285)
    *   Smishing, [249](#c6.xhtml#p249)
    *   SMSC, see [Short Message Service Center](#index.xhtml#see1175)
    *   Smurf attack, [241](#c6.xhtml#p241)–[242](#c6.xhtml#p242)
    *   Sober worm, [65](#c2.xhtml#p65)
    *   Sobig worm, [64](#c2.xhtml#p64)
    *   SOC, see [System-on-chip](#index.xhtml#see1249)
    *   Social engineering, [250](#c6.xhtml#p250)
    *   Social Security Act (42 U.S.C. 1320d–5), section 1176, [303](#c7.xhtml#p303), [385](#appendixD.xhtml#p385)
    *   Social Security Act (42 U.S.C. 1320d–55(b)), section 1176(b), [385](#appendixD.xhtml#p385)
    *   Social Security Administration (SSA), [115](#c4.xhtml#p115)
    *   Social Security Number (SSN), [402](#appendixF.xhtml#p402)
    *   Software-as-a-Service (SaaS), [230](#c6.xhtml#p230)–[231](#c6.xhtml#p231)
    *   Software attacks, [303](#c7.xhtml#p303)
    *   Software-Defined Wide Area Network (SD-WAN), [218](#c5.xhtml#p218)
    *   Software Development Kit (SDK), [317](#c8.xhtml#p317)
    *   Sony Pictures Entertainment (SPE), [68](#c2.xhtml#p68)
    *   Source address, [184](#c5.xhtml#p184)
    *   Spam, [56](#c2.xhtml#p56), [233](#c6.xhtml#p233)
    *   SPE, see [Sony Pictures Entertainment](#index.xhtml#see1204)
    *   Spear phishing, [248](#c6.xhtml#p248)–[249](#c6.xhtml#p249)
    *   SPF, see [Sender policy framework](#index.xhtml#see1168)
    *   Spoofing, [250](#c6.xhtml#p250)–[251](#c6.xhtml#p251)
    *   SpyEye, [66](#c2.xhtml#p66), [75](#c2.xhtml#p75)
    *   Spyware, [248](#c6.xhtml#p248), [336](#c8.xhtml#p336)
    *   SQLI, see [Structured Query Language Injection](#index.xhtml#see1230)
    *   SSH, see Secure Shell protocol
    *   SSL, see [Secure Sockets Layer](#index.xhtml#see1155)
    *   SSN, see [Social Security Number](#index.xhtml#see1199)
    *   Standards, [198](#c5.xhtml#p198)
    *   Star network topology, [204](#c5.xhtml#p204)–[206](#c5.xhtml#p206)
    *   State, [348](#appendixA.xhtml#p348)
    *   Stateful firewalls, [260](#c6.xhtml#p260), [261](#c6.xhtml#p261)
    *   Stateless firewalls, [259](#c6.xhtml#p259)
    *   State-sponsored cyberwarfare, [83](#c2.xhtml#p83)–[84](#c2.xhtml#p84)
    *   Static IP address, [189](#c5.xhtml#p189)
    *   Statute law, [93](#c3.xhtml#p93)–[95](#c3.xhtml#p95)
    *   Statutory damages, [374](#appendixB.xhtml#p374)
    *   Steganography, [222](#c6.xhtml#p222)
    *   Stored Communications Act (SCA), [155](#c4.xhtml#p155)
    *   Stream Cipher, [264](#c6.xhtml#p264)
    *   Structured Query Language (SQL), [251](#c6.xhtml#p251)–[252](#c6.xhtml#p252)
    *   Structured Query Language Injection (SQLI), [251](#c6.xhtml#p251)–[252](#c6.xhtml#p252)
    *   Stuxnet worm, [67](#c2.xhtml#p67)
    *   Subnet, [188](#c5.xhtml#p188), [189](#c5.xhtml#p189)
    *   Subnetting, [189](#c5.xhtml#p189)
    *   Subpoena, [103](#c3.xhtml#p103)
    *   Subscriber identity module (SIM) card, [311](#c8.xhtml#p311)
    *   Superposition, [29](#c1.xhtml#p29)
    *   Supervisory Control and Data Acquisition (SCADA), [138](#c4.xhtml#p138)
    *   Surface Web, [77](#c2.xhtml#p77)
    *   Switches, [197](#c5.xhtml#p197), [217](#c5.xhtml#p217)
    *   Symmetric encryption method, [263](#c6.xhtml#p263)–[266](#c6.xhtml#p266)
    *   Symmetric vs. asymmetric encryption, [269](#c6.xhtml#p269)
    *   SYN, see [Synchronize](#index.xhtml#see1244)
    *   SYN-ACK, see [Synchronize Acknowledgment](#index.xhtml#see1246)
    *   Synchronize (SYN), [212](#c5.xhtml#p212)
    *   flood attack, [240](#c6.xhtml#p240), [241](#c6.xhtml#p241)
    *   Synchronize Acknowledgment (SYN-ACK), [213](#c5.xhtml#p213)
    *   System application layer, [319](#c8.xhtml#p319)
    *   System Identification number (SID), [325](#c8.xhtml#p325)
    *   System-on-chip (SOC), [313](#c8.xhtml#p313), [315](#c8.xhtml#p315)
    *   T
    *   TCP, see [Transmission Control Protocol](#index.xhtml#see1280)
    *   TCP/IP, see Transmission Control Protocol/Internet Protocol model
    *   TDoA, see [Time difference of arrival](#index.xhtml#see1268)
    *   Technological advancements, [48](#c1.xhtml#p48)–[49](#c1.xhtml#p49)
    *   Technological measure, [360](#appendixB.xhtml#p360)
    *   Technological protection measures (TPM), [119](#c4.xhtml#p119)
    *   Technological singularity, [47](#c1.xhtml#p47)
    *   Telecommunications Industry Association (TIA), [326](#c8.xhtml#p326)
    *   Telenet, [174](#c5.xhtml#p174)
    *   TensorFlow, [46](#c1.xhtml#p46), [79](#c2.xhtml#p79)
    *   Testimony, [103](#c3.xhtml#p103)
    *   Theft of trade secrets, [118](#c4.xhtml#p118)
    *   32-Bit processor, [20](#c1.xhtml#p20)
    *   3G communication network, [310](#c8.xhtml#p310)
    *   Three-way handshake, [212](#c5.xhtml#p212), [213](#c5.xhtml#p213)
    *   TIA, see [Telecommunications Industry Association](#index.xhtml#see1258)
    *   TILA, see [Truth in Lending Act](#index.xhtml#see1290)
    *   Time difference of arrival (TDoA), [330](#c8.xhtml#p330)–[331](#c8.xhtml#p331)
    *   Time of arrival (ToA), [330](#c8.xhtml#p330)
    *   TLS, see [Transport Layer Security](#index.xhtml#see1284)
    *   ToA, see [Time of arrival](#index.xhtml#see1269)
    *   Token-based authentication, [262](#c6.xhtml#p262)
    *   Tor’s Hammer, [245](#c6.xhtml#p245)
    *   Tort, [100](#c3.xhtml#p100)
    *   Tort suit, [100](#c3.xhtml#p100)
    *   TPC/IP, see [Internet protocol suite](#index.xhtml#see697)
    *   Traceroute, [197](#c5.xhtml#p197)
    *   tracert, [197](#c5.xhtml#p197)
    *   Transistor, [8](#c1.xhtml#p8), [36](#c1.xhtml#p36)
    *   Transmission Control Protocol (TCP), [65](#c2.xhtml#p65), [172](#c5.xhtml#p172), [212](#c5.xhtml#p212)–[213](#c5.xhtml#p213), [296](#c7.xhtml#p296)
    *   Transmission Control Protocol/Internet Protocol (TCP/IP) model, [293](#c7.xhtml#p293), [299](#c7.xhtml#p299)
    *   Transportation sector, [286](#c7.xhtml#p286)
    *   Transport layer, [192](#c5.xhtml#p192), [208](#c5.xhtml#p208), [291](#c7.xhtml#p291)–[296](#c7.xhtml#p296)
    *   Transport Layer Security (TLS), [233](#c6.xhtml#p233)
    *   Triangulation, [329](#c8.xhtml#p329)
    *   Tribal, [409](#appendixG.xhtml#p409)
    *   Trilateration, [331](#c8.xhtml#p331)
    *   Trojan horse, [65](#c2.xhtml#p65), [246](#c6.xhtml#p246)
    *   Trojans, [60](#c2.xhtml#p60)
    *   Truth in Lending Act (TILA), [132](#c4.xhtml#p132)
    *   Twitter, [64](#c2.xhtml#p64)
    *   2G cellular network, [310](#c8.xhtml#p310)
    *   Two-factor authentication (2FA), [261](#c6.xhtml#p261), [336](#c8.xhtml#p336)
    *   U
    *   UDP, see [User Datagram Protocol](#index.xhtml#see1331)
    *   UI, see [User interface](#index.xhtml#see1333)
    *   Unicast addresses, [191](#c5.xhtml#p191)
    *   UNICODE, [14](#c1.xhtml#p14)–[15](#c1.xhtml#p15)
    *   Uniform resource locator (URL), [172](#c5.xhtml#p172)
    *   Unique local unicast addresses, [192](#c5.xhtml#p192)
    *    United States of America v. Aaron Swartz, [116](#c4.xhtml#p116)
    *    United States of America v. Wang Dong, Sun Kailiang, Wen Xinyu, Huang Zhenyu, Gu Chunhui, [119](#c4.xhtml#p119)
    *    United States v. Drew, [115](#c4.xhtml#p115)
    *    United States v. John, [114](#c4.xhtml#p114)–[115](#c4.xhtml#p115)
    *    United States v. Morris, [113](#c4.xhtml#p113)
    *    United States v. New York Telephone Co., [147](#c4.xhtml#p147)
    *    United States v. Nosal, [113](#c4.xhtml#p113)
    *    United States v. Ramsey, [151](#c4.xhtml#p151)
    *    United States V. Richardson, [151](#c4.xhtml#p151)
    *    United States v. Rodriguez, [115](#c4.xhtml#p115)
    *    United States v. Villamonte-Marquez, [151](#c4.xhtml#p151)
    *   Universal Serial Bus (USB), [8](#c1.xhtml#p8), [43](#c1.xhtml#p43)
    *   Unlawful Violations, [167](#c4.xhtml#p167)
    *   Unsecured Wi-Fi, [337](#c8.xhtml#p337)–[338](#c8.xhtml#p338)
    *   Unsecured Wi-Fi connections, [254](#c6.xhtml#p254)
    *   UpGuard, [66](#c2.xhtml#p66)
    *   Uplink, [328](#c8.xhtml#p328)
    *   URL, see [Uniform resource locator](#index.xhtml#see1299)
    *   USA PATRIOT Act, [64](#c2.xhtml#p64), [153](#c4.xhtml#p153)–[154](#c4.xhtml#p154)
    *   USA PATRIOT Act 2002, [111](#c4.xhtml#p111)
    *   USA PATRIOT Act: Preserving Life and Liberty, [108](#c4.xhtml#p108)
    *   U.S Appeals Court, [97](#c3.xhtml#p97)
    *   USB, see [Universal Serial Bus](#index.xhtml#see1312)
    *   U.S. Code Annotated (USC), [94](#c3.xhtml#p94)
    *   U.S. Constitution, [92](#c3.xhtml#p92)–[93](#c3.xhtml#p93), [96](#c3.xhtml#p96), [99](#c3.xhtml#p99), [106](#c4.xhtml#p106)
    *   U.S. Court of Appeals case for the Ninth Circuit, [113](#c4.xhtml#p113)
    *   U.S. Department of Agriculture (USDA), [95](#c3.xhtml#p95)
    *   U.S. Department of Health and Human Services (HHS), [95](#c3.xhtml#p95)
    *   U.S. Department of Homeland Security (DHS), [236](#c6.xhtml#p236)
    *   U.S. District Courts, [96](#c3.xhtml#p96)
    *   User Datagram Protocol (UDP), [213](#c5.xhtml#p213)–[216](#c5.xhtml#p216), [295](#c7.xhtml#p295)–[296](#c7.xhtml#p296)
    *   User Datagram Protocol Flood, [243](#c6.xhtml#p243)
    *   User interface (UI), [3](#c1.xhtml#p3)
    *   US Federal Emergency Management Agency (FEMA), [73](#c2.xhtml#p73)
    *   U.S Federal Trade Commission (FTC), [70](#c2.xhtml#p70)
    *   U.S. Legal System
    *   Administrative Laws, [95](#c3.xhtml#p95)–[96](#c3.xhtml#p96)
    *   Case law, [96](#c3.xhtml#p96)
    *   courts system, [96](#c3.xhtml#p96)–[99](#c3.xhtml#p99)
    *   digital evidence, [90](#c3.xhtml#p90)
    *   extradition, [88](#c3.xhtml#p88)–[89](#c3.xhtml#p89)
    *   jurisdiction, [88](#c3.xhtml#p88)–[89](#c3.xhtml#p89)
    *   law types
    *   Administrative Law, [99](#c3.xhtml#p99)–[100](#c3.xhtml#p100)
    *   Civil law, [100](#c3.xhtml#p100)
    *   Criminal law, [100](#c3.xhtml#p100)–[102](#c3.xhtml#p102)
    *   legal term, [103](#c3.xhtml#p103)
    *   non reported cybercrimes, [90](#c3.xhtml#p90)–[91](#c3.xhtml#p91)
    *   online anonymity, [89](#c3.xhtml#p89)–[90](#c3.xhtml#p90)
    *   overview of, [91](#c3.xhtml#p91)
    *   Statute Law, [93](#c3.xhtml#p93)–[95](#c3.xhtml#p95)
    *   U.S. Constitution, [92](#c3.xhtml#p92)–[93](#c3.xhtml#p93)
    *    U.S. v. Liew, [118](#c4.xhtml#p118)
    *   V
    *   Vacuum tube, [36](#c1.xhtml#p36)
    *   Vehicular ad hoc Network (VANET), [280](#c7.xhtml#p280)
    *   Vessel Hull Design Protection Act, [120](#c4.xhtml#p120)
    *   Video Privacy Protection Act (VPPA) of 1988, [164](#c4.xhtml#p164)–[165](#c4.xhtml#p165)
    *   Video tape service provider, [165](#c4.xhtml#p165)
    *   Virtual firewalls, [261](#c6.xhtml#p261)
    *   Virtualization, [198](#c5.xhtml#p198)
    *   Virtual Local Area Network (VLAN), [201](#c5.xhtml#p201)–[202](#c5.xhtml#p202)
    *   Virtual memory, [21](#c1.xhtml#p21)
    *   Virtual Private Networks (VPNs), [89](#c3.xhtml#p89), [190](#c5.xhtml#p190), [202](#c5.xhtml#p202), [234](#c6.xhtml#p234)
    *   Virus, [179](#c5.xhtml#p179)
    *   Vishing, [249](#c6.xhtml#p249)
    *   VLAN, see [Virtual Local Area Network](#index.xhtml#see1362)
    *   Voice over Internet Protocol (VoIP), [190](#c5.xhtml#p190)
    *   Volatile memory, see [Random Access Memory (RAM)](#index.xhtml#see1111)
    *   Volumetric/volume-based Attacks, [238](#c6.xhtml#p238)
    *   von Neumann concept, [2](#c1.xhtml#p2)
    *   VPNs, see [Virtual Private Networks](#index.xhtml#see1364)
    *   VPPA, see Video Privacy Protection Act of 1988
    *   Vulnerability, [235](#c6.xhtml#p235)
    *   W
    *   WAN, see [Wide Area Network](#index.xhtml#see1382)
    *   WannaCry, [71](#c2.xhtml#p71), [72](#c2.xhtml#p72)
    *   WAP, see [Wireless Access Point](#index.xhtml#see1396)
    *   Web application firewall (WAF), [261](#c6.xhtml#p261)
    *   Website spoofing, [251](#c6.xhtml#p251)
    *   White-hat/ethical hackers, [231](#c6.xhtml#p231)–[232](#c6.xhtml#p232)
    *   Wide Area Network (WAN), [200](#c5.xhtml#p200), [301](#c7.xhtml#p301)
    *   Wi-Fi
    *   based localization, [332](#c8.xhtml#p332)
    *   de-authentication attack, [253](#c6.xhtml#p253)
    *   hacking, [252](#c6.xhtml#p252)–[256](#c6.xhtml#p256)
    *   Halo, [298](#c7.xhtml#p298)
    *   Wi-Fi IEEE 802.11, [217](#c5.xhtml#p217)
    *   Wi-Fi Protected Access 3 (WPA3), [252](#c6.xhtml#p252)
    *   Wi-Fi Protected Access II (WPA2), [252](#c6.xhtml#p252)
    *   Wi-Fi Protected Access (WPA) protocol, [252](#c6.xhtml#p252)
    *   Wi-Fi protected setup (WPS) attack, [253](#c6.xhtml#p253)–[254](#c6.xhtml#p254)
    *   WIPO Copyright and Performances and Phonograms Treaties Implementation Act of 1998, [120](#c4.xhtml#p120)
    *   WIPO Copyright Treaty, [119](#c4.xhtml#p119)
    *   WIPO Performances and Phonograms Treaty, [119](#c4.xhtml#p119)
    *   Wireless Access Point (WAP), [181](#c5.xhtml#p181)–[182](#c5.xhtml#p182)
    *   Wireless communication transceiver, [287](#c7.xhtml#p287)
    *   Wireless Local Area Network (WLAN), [201](#c5.xhtml#p201)
    *   Wireshark, [195](#c5.xhtml#p195)
    *   Wiretap Act, [154](#c4.xhtml#p154)
    *   WLAN, see [Wireless Local Area Network](#index.xhtml#see1398)
    *   World Intellectual Property Organization (WIPO), [120](#c4.xhtml#p120)
    *   World of Warcraft (WoW), [124](#c4.xhtml#p124)
    *   World Wide Web (WWW), [12](#c1.xhtml#p12), [40](#c1.xhtml#p40), [41](#c1.xhtml#p41), [176](#c5.xhtml#p176)–[178](#c5.xhtml#p178)
    *   Worm, [56](#c2.xhtml#p56), [58](#c2.xhtml#p58)
    *   WPA, see Wi-Fi Protected Access protocol
    *   Writ Certiorari, [103](#c3.xhtml#p103)
    *   WWW, see [World Wide Web](#index.xhtml#see1404)
    *   X
    *   XOIC, [245](#c6.xhtml#p245)
    *   Y
    *   Yahoo, [68](#c2.xhtml#p68)
    *   YouTube, [70](#c2.xhtml#p70)
    *   Z
    *   Zero-Day DDoS attacks, [244](#c6.xhtml#p244)
    *   Zeus virus, [66](#c2.xhtml#p66), [75](#c2.xhtml#p75)
    *   ZigBee, [298](#c7.xhtml#p298)
    
    * * *
    
    1.  [1](#c1.xhtml#re_n-1) Von Neumann, John. “First Draft of a Report on the EDVAC.” *IEEE Annals of the History of Computing* 15, no. 4 (1993): 27–75.[↩](#fnref1)
    2.  [3](#c1.xhtml#re_n-3) Garfinkel, Simson L., and Rachel H. Grunspan. *The computer book: From the abacus to artificial intelligence, 250 milestones in the history of computer science*, 2018, Nueva York: Sterling, 2018.[↩](#fnref2)
    3.  [5](#c1.xhtml#re_n-5) Ben-Ari, Mordechai. *Mathematical logic for computer science*. Springer Science & Business Media, 2012.[↩](#fnref3)
    4.  [6](#c1.xhtml#re_n-6) Simpson, Stephen G. “Logic and mathematics.” *The examined life: Readings from western philosophy from Plato to Kant*, edited by S. Rosen, pp. 577–605, Random House, 2000.[↩](#fnref4)
    5.  [7](#c1.xhtml#re_n-7) Maini, Anil K. *Digital electronics: principles, devices and applications*. John Wiley & Sons, 2007.[↩](#fnref5)
    6.  [9](#c1.xhtml#re_n-9) *Id.* at 7.[↩](#fnref6)
    7.  [11](#c1.xhtml#re_n-11) Boole, George. *The mathematical analysis of logic*. Philosophical Library, 1847.[↩](#fnref7)
    8.  [12](#c1.xhtml#re_n-12) Mahmoodi, Hamid, Saihal Mukhopadhyay, and Kaushik Roy. “High performance and low power domino logic using independent gate control in double-gate SOI MOSFETs.” In *2004 IEEE International SOI Conference (IEEE Cat. No. 04CH37573)*, pp. 67–68. IEEE, 2004.[↩](#fnref8)
    9.  [15](#c1.xhtml#re_n-15) Motoyoshi, Makoto. “Through-silicon via (TSV).” *Proceedings of the IEEE* 97, no. 1 (2009): 43–48.[↩](#fnref9)
    10.  [17](#c1.xhtml#re_n-17) Kodituwakku, S. R., and U. S. Amarasinghe. “Comparison of lossless data compression algorithms for text data.” *Indian Journal of Computer Science and Engineering* 1, no. 4 (2010): 416–425.[↩](#fnref10)
    11.  [18](#c1.xhtml#re_n-18) Pavlidis, Theodosios. *Algorithms for graphics and image processing*. Springer Science & Business Media, 2012.[↩](#fnref11)
    12.  [19](#c1.xhtml#re_n-19) Koenderink, Jan J. *Color for the sciences*. MIT Press, 2010.[↩](#fnref12)
    13.  [20](#c1.xhtml#re_n-20) Hirsch, Robert. *Exploring color photography: From film to pixels*. Routledge, 2014.[↩](#fnref13)
    14.  [23](#c1.xhtml#re_n-23) Mouw, T. “Additive vs. subtractive color models,” Pantone. Last modified April 2018. [https://www.xrite.com/blog/additive-subtractive-color-models](https://www.xrite.com)[↩](#fnref14)
    15.  [25](#c1.xhtml#re_n-25) Feynman, Richard P. *Feynman lectures on computation*. CRC Press, 2018.[↩](#fnref15)
    16.  [26](#c1.xhtml#re_n-26) Boixo, Sergio, Sergei V. Isakov, Vadim N. Smelyanskiy, Ryan Babbush, Nan Ding, Zhang Jiang, Michael J. Bremner, John M. Martinis, and Hartmut Neven. “Characterizing quantum supremacy in near-term devices.” *Nature Physics* 14, no. 6 (2018): 595.[↩](#fnref16)
    17.  [27](#c1.xhtml#re_n-27) Teresi, Dick. *Lost discoveries: The ancient roots of modern science—from the Babylonians to the Maya*. Simon and Schuster, 2002.[↩](#fnref17)
    18.  [29](#c1.xhtml#re_n-29) Seiradakis, J. H., and M. G. Edmunds. “Our current knowledge of the Antikythera Mechanism.” *Nature Astronomy* 2, no. 1 (2018): 35.[↩](#fnref18)
    19.  [30](#c1.xhtml#re_n-30) Yates, David R., Christophe Vaessen, and Morgan Roupret. “From Leonardo to da Vinci: the history of robot‐assisted surgery in urology.” *BJU International* 108, no. 11 (2011): 1708–1713.[↩](#fnref19)
    20.  [32](#c1.xhtml#re_n-32) Ratcliff, Jessica R. “Samuel Morland and his calculating machines c. 1666: the early career of a courtier–inventor in Restoration London.” *The British Journal for the History of Science* 40, no. 2 (2007): 159–179.[↩](#fnref20)
    21.  [33](#c1.xhtml#re_n-33) Randell, Brian, ed. *The origins of digital computers: Selected papers*. Springer, 2013.[↩](#fnref21)
    22.  [35](#c1.xhtml#re_n-35) Burks, Arthur W. “The invention of the universal electronic computer—how the Electronic Computer Revolution began.” *Future Generation Computer Systems* 18, no. 7 (2002): 871–892.[↩](#fnref22)
    23.  [36](#c1.xhtml#re_n-36) Rojas, Raúl, and Ulf Hashagen, eds. *The first computers: History and architectures*. MIT Press, 2002.[↩](#fnref23)
    24.  [37](#c1.xhtml#re_n-37) Rojas, Raúl. “Konrad Zuse’s legacy: the architecture of the Z1 and Z3.” *IEEE Annals of the History of Computing* 19, no. 2 (1997): 5–16.[↩](#fnref24)
    25.  [38](#c1.xhtml#re_n-38) Ceruzzi, Paul E. *A history of modern computing*. MIT Press, 2003.[↩](#fnref25)
    26.  [41](#c1.xhtml#re_n-41) *Id.* at 38.[↩](#fnref26)
    27.  [43](#c1.xhtml#re_n-43) Ayers, John E. *Digital integrated circuits: Analysis and design*. CRC Press, 2018.[↩](#fnref27)
    28.  [44](#c1.xhtml#re_n-44) Kilby, Jack St Clair. “Turning potential into realities: The invention of the integrated circuit (Nobel lecture).” *ChemPhysChem* 2, no. 8–9 (2001): 482–489.[↩](#fnref28)
    29.  [45](#c1.xhtml#re_n-45) *Id.* at 36.[↩](#fnref29)
    30.  [46](#c1.xhtml#re_n-46) Schaller, Robert R. “Moore’s law: Past, present and future.” *IEEE Spectrum* 34, no. 6 (1997): 52–59.[↩](#fnref30)
    31.  [47](#c1.xhtml#re_n-47) Bosworth, Seymour, and Michel E. Kabay, eds. *Computer security handbook*. John Wiley & Sons, 2002.[↩](#fnref31)
    32.  [48](#c1.xhtml#re_n-48) Brown, Bruce C. *The complete guide to e-mail marketing: how to create successful, spam-free campaigns to reach your target audience and increase sales*. Vol. 978, no. 1-60045. Atlantic Publishing Company, 2007.[↩](#fnref32)
    33.  [49](#c1.xhtml#re_n-49) Chesbrough, Henry W., and David J. Teece. “Organizing for innovation.” *The Strategic Management of Intellectual Capital* (2009): 27.[↩](#fnref33)
    34.  [50](#c1.xhtml#re_n-50) Diem, Richard A., and Michael J. Berson, eds. *Technology in retrospect: Social studies in the information age, 19842009*. IAP, 2010.[↩](#fnref34)
    35.  [51](#c1.xhtml#re_n-51) Linzmayer, Owen W. *Apple confidential 2.0: The definitive history of the world’s most colorful company*. No Starch Press, 2004.[↩](#fnref35)
    36.  [52](#c1.xhtml#re_n-52) Mowery, David C., and Timothy Simcoe. “Is the Internet a US invention?—an economic and technological history of computer networking.” *Research Policy* 31, no. 8–9 (2002): 1369–1387.[↩](#fnref36)
    37.  [53](#c1.xhtml#re_n-53) Bank, David. *Breaking windows: how Bill Gates fumbled the future of Microsoft*. Simon & Schuster, 2001.[↩](#fnref37)
    38.  [54](#c1.xhtml#re_n-54) Adelsberger, Heimo H., Betty Collis, and Jan Martin Pawlowski, eds. *Handbook on information technologies for education and training*. Springer Science & Business Media, 2013.[↩](#fnref38)
    39.  [55](#c1.xhtml#re_n-55) Campbell-Kelly, Martin, and Daniel D. Garcia-Swartz. “The history of the internet: The missing narratives.” *Journal of Information Technology* 28, no. 1 (2013): 18–33.[↩](#fnref39)
    40.  [57](#c1.xhtml#re_n-57) McNeff, Jules G. “The global positioning system.” *IEEE Transactions on Microwave theory and techniques* 50, no. 3 (2002): 645–652.[↩](#fnref40)
    41.  [59](#c1.xhtml#re_n-59) Buenstorf, Guido, and Dirk Fornahl. “B2C—bubble to cluster: The dot-com boom, spin-off entrepreneurship, and regional agglomeration.” *Journal of Evolutionary Economics* 19, no. 3 (2009): 349–378.[↩](#fnref41)
    42.  [60](#c1.xhtml#re_n-60) Edosomwan, Simeon, Sitalaskshmi Kalangot Prakasan, Doriane Kouame, Jonelle Watson, and Tom Seymour. “The history of social media and its impact on business.” *Journal of Applied Management and Entrepreneurship* 16, no. 3 (2011): 79–91.[↩](#fnref42)
    43.  [61](#c1.xhtml#re_n-61) Vise, David. “The google story.” *Strategic Direction* 23, no. 10 (2007).[↩](#fnref43)
    44.  [66](#c1.xhtml#re_n-66) Qian, Ling, Zhiguo Luo, Yujian Du, and Leitao Guo. “Cloud computing: An overview.” In *IEEE International Conference on Cloud Computing*, pp. 626–631. Springer, Berlin, Heidelberg, 2009.[↩](#fnref44)
    45.  [73](#c1.xhtml#re_n-73) Mahmud, Redowan, Ramamohanarao Kotagiri, and Rajkumar Buyya. “Fog computing: A taxonomy, survey and future directions.” In *Internet of everything*, pp. 103–130. Springer, Singapore, 2018.[↩](#fnref45)
    46.  [75](#c1.xhtml#re_n-75) Nilsson, Nils J., and Nils Johan Nilsson. *Artificial intelligence: a new synthesis*. Morgan Kaufmann, 1998.[↩](#fnref46)
    47.  [77](#c1.xhtml#re_n-77) McCarthy John. “What is artificial intelligence?” Last revised November 12, 2007. [http://jmc.stanford.edu/articles/whatisai.html](http://jmc.stanford.edu).[↩](#fnref47)
    48.  [78](#c1.xhtml#re_n-78) Abadi, Martín, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, et al. “Tensorflow: Large-scale machine learning on heterogeneous distributed systems.” *arXiv preprint arXiv:1603.04467* (2016).[↩](#fnref48)
    49.  [80](#c1.xhtml#re_n-80) Wu, Stephen Gang, Forrest Sheng Bao, Eric You Xu, Yu-Xuan Wang, Yi-Fan Chang, and Qiao-Liang Xiang. “A leaf recognition algorithm for plant classification using probabilistic neural network.” In *2007 IEEE international symposium on signal processing and information technology*, pp. 11–16. IEEE, 2007.[↩](#fnref49)
    50.  [82](#c1.xhtml#re_n-82) Kurzweil, Ray. *The singularity is near: When humans transcend biology*. Penguin, 2005.[↩](#fnref50)
    51.  [84](#c1.xhtml#re_n-84) Modis, Theodore. “The singularity myth.” *Technological Forecasting & Social Change* 73, no. 2 (2006): 104–112.[↩](#fnref51)
    52.  [1](#c2.xhtml#re_n-1) *The Economist*. The world’s most valuable resource is no longer oil, but data (2017). Retrieved from [https://www.economist.com/news/leaders/21721656-data-economy-demands-new-approach-antitrust-rules-worlds-most-valuable-resource](https://www.economist.com)[↩](#fnref52)
    53.  [2](#c2.xhtml#re_n-2) Bennett, Anthony J. “1992: ‘It’s the Economy, Stupid!’.” *In the race for the White House from Reagan to Clinton*, pp. 123–159. Palgrave Macmillan, New York, 2013.[↩](#fnref53)
    54.  [3](#c2.xhtml#re_n-3) Trautman, Lawrence J. “Is cyberattack the next pearl harbor.” *NCJL & Tech.* 18 (2016): 233.[↩](#fnref54)
    55.  [5](#c2.xhtml#re_n-5) Kirwan, Gráinne, ed. *The psychology of cyber crime: Concepts and principles*. Igi Global, 2011.[↩](#fnref55)
    56.  [7](#c2.xhtml#re_n-7) Bonner, Lance. “Cyber risk: How the 2011 Sony data breach and the need for cyber risk insurance policies should direct the federal response to rising data breaches.” *Washington University Journal of Law & Policy Introduction* 40 (2012): 257.[↩](#fnref56)
    57.  [8](#c2.xhtml#re_n-8) Lukasik, Stephen. “Why the ARPANET was built.” *IEEE Annals of the History of Computing* 33, no. 3 (2010): 4–21.[↩](#fnref57)
    58.  [10](#c2.xhtml#re_n-10) Brown, Bruce C. *The complete guide to e-mail marketing: How to create successful, spam-free campaigns to reach your target audience and increase sales*. Vol. 978, no. 1-60045. Atlantic Publishing Company, 2007.[↩](#fnref58)
    59.  [12](#c2.xhtml#re_n-12) Carroll, John M. *Computer security*. Butterworth-Heinemann, 2014.[↩](#fnref59)
    60.  [13](#c2.xhtml#re_n-13) Corera, Gordon. *Cyberspies: The secret history of surveillance, hacking, and digital espionage*. Pegasus Books, 2016.[↩](#fnref60)
    61.  [14](#c2.xhtml#re_n-14) Brenner, Susan W. “History of computer crime.” In *The history of information security*, pp. 705–721. Elsevier Science BV, 2007.[↩](#fnref61)
    62.  [16](#c2.xhtml#re_n-16) Futter, Andrew. *Hacking the bomb: Cyber threats and nuclear weapons*. Georgetown University Press, 2018.[↩](#fnref62)
    63.  [17](#c2.xhtml#re_n-17) Gragido, Will, Daniel Molina, John Pirc, and Nick Selby. *Blackhatonomics: An inside look at the economics of cybercrime*. Newnes, 2012.[↩](#fnref63)
    64.  [18](#c2.xhtml#re_n-18) Zou, Cliff C., Don Towsley, and Weibo Gong. “Email virus propagation modeling and analysis.” *Department of Electrical and Computer Engineering, University of Massachusetts, Amherst, Technical Report: TR-CSE-03-04* (2003).[↩](#fnref64)
    65.  [20](#c2.xhtml#re_n-20) Hoar, Sean B. “Identity theft: The crime of the new millennium.” *Oregon School of Law* 80 (2001): 1423.[↩](#fnref65)
    66.  [21](#c2.xhtml#re_n-21) Knight, Peter. “ILOVEYOU: Viruses, paranoia, and the environment of risk.” *The Sociological Review* 48, no. 2\_suppl (2000): 17–30.[↩](#fnref66)
    67.  [22](#c2.xhtml#re_n-22) Kienzle, Darrell M., and Matthew C. Elder. “Recent worms: a survey and trends.” In *Proceedings of the 2003 ACM workshop on Rapid malcode*, pp. 1–10. ACM, 2003.[↩](#fnref67)
    68.  [23](#c2.xhtml#re_n-23) USA PATRIOT Act of 2001, Pub. L. No. 107–56. Retrieved from [https://www.congress.gov/107/plaws/publ56/PLAW-107publ56.pdf](https://www.congress.gov)[↩](#fnref68)
    69.  [24](#c2.xhtml#re_n-24) Chen, Thomas M., and J-M. Robert. “Worm epidemics in high-speed networks.” *Computer* 37, no. 6 (2004): 48–53.[↩](#fnref69)
    70.  [25](#c2.xhtml#re_n-25) *Id.* at 24.[↩](#fnref70)
    71.  [26](#c2.xhtml#re_n-26) “Sophos W32/Sober-I.” Last modified January 2005. Retrieved from [https://www.sophos.com/en-us/threat-center/threat-analyses/viruses-and-spyware/W32~Sober-I/detailed-analysis.aspx](https://www.sophos.com)[↩](#fnref71)
    72.  [27](#c2.xhtml#re_n-27) Chen, Yanpei, Vern Paxson, and Randy H. Katz. “What’s new about cloud computing security.” *University of California, Berkeley Report No. UCB/EECS-2010-5*, January 20, no. 2010 (2010): 2010–15.[↩](#fnref72)
    73.  [28](#c2.xhtml#re_n-28) “Losing face: Two more cases of third-party facebook app data exposure.” *UpGuard*. Last modified April 3, 2019. Retrieved from [https://www.upguard.com/breaches/facebook-user-data-leak](https://www.upguard.com)[↩](#fnref73)
    74.  [29](#c2.xhtml#re_n-29) Binsalleeh, Hamad, Thomas Ormerod, Amine Boukhtouta, Prosenjit Sinha, Amr Youssef, Mourad Debbabi, and Lingyu Wang. “On the analysis of the zeus botnet crimeware toolkit.” In *2010 Eighth International Conference on Privacy, Security and Trust*, pp. 31–38. IEEE, 2010.[↩](#fnref74)
    75.  [32](#c2.xhtml#re_n-32) Kenney, Michael. “Cyber-terrorism in a post-stuxnet world.” *Orbis* 59, no. 1 (2015): 111–128.[↩](#fnref75)
    76.  [33](#c2.xhtml#re_n-33) *Id.* at 7.[↩](#fnref76)
    77.  [36](#c2.xhtml#re_n-36) Steinmetz, Kevin F., and Matt R. Nobles, eds. *Technocrime and criminological theory*. Routledge, 2017.[↩](#fnref77)
    78.  [37](#c2.xhtml#re_n-37) Haggard, Stephan, and Jon R. Lindsay. “North Korea and the Sony hack: Exporting instability through cyberspace” (2015).[↩](#fnref78)
    79.  [38](#c2.xhtml#re_n-38) Edwards, Benjamin, Steven Hofmeyr, and Stephanie Forrest. “Hype and heavy tails: A closer look at data breaches.” *Journal of Cybersecurity* 2, no. 1 (2016): 3–14.[↩](#fnref79)
    80.  [39](#c2.xhtml#re_n-39) Khan, Shahidul Islam, and Abu Sayed Md Latiful Hoque. “Digital health data: A comprehensive review of privacy and security risks and some recommendations.” *Computer Science Journal of Moldova* 24, no. 2 (2016).[↩](#fnref80)
    81.  [40](#c2.xhtml#re_n-40) Allcott, Hunt, and Matthew Gentzkow. “Social media and fake news in the 2016 election.” *Journal of Economic Perspectives* 31, no. 2 (2017): 211–36.[↩](#fnref81)
    82.  [41](#c2.xhtml#re_n-41) Persily, Nathaniel. “The 2016 US election: Can democracy survive the internet?.” *Journal of Democracy* 28, no. 2 (2017): 63–76.[↩](#fnref82)
    83.  [44](#c2.xhtml#re_n-44) *Id.* at 41.[↩](#fnref83)
    84.  [50](#c2.xhtml#re_n-50) Raz, Guy. “Carole Cadwalladr: How did social media manipulate our votes and our elections?” *npr News*, July 12, 2019. Retrieved from [https://www.npr.org/templates/transcript/transcript.php?storyId=740771021](https://www.npr.org)[↩](#fnref84)
    85.  [51](#c2.xhtml#re_n-51) “$5b privacy fine against Facebook seen as ‘chump change’” *Naked Security*, July 19, 2019. Retrieved from [https://nakedsecurity.sophos.com/2019/07/16/5b-privacy-fine-against-facebook-seen-as-chump-change/](https://nakedsecurity.sophos.com)[↩](#fnref85)
    86.  [53](#c2.xhtml#re_n-53) Detrow, Scott. “Cruz’s Crew: you play the game, but it’s the cruz campaign that scores.” *Npr News*, November 9, 2015. Retrieved from [https://www.npr.org/2015/11/09/455225893/cruzs-crew-you-play-the-game-but-its-the-cruz-campaign-that-scores](https://www.npr.org)[↩](#fnref86)
    87.  [55](#c2.xhtml#re_n-55) Fayi, Sharifah Yaqoub A. “What Petya/NotPetya ransomware is and what its remidiations are.” In *Information Technology—New Generations*, pp. 93–100. Springer, Cham, 2018.[↩](#fnref87)
    88.  [56](#c2.xhtml#re_n-56) Kambourakis, Georgios, Constantinos Kolias, and Angelos Stavrou. “The mirai botnet and the iot zombie armies.” In *MILCOM 2017–2017 IEEE Military Communications Conference (MILCOM)*, pp. 267–272. IEEE, 2017.[↩](#fnref88)
    89.  [57](#c2.xhtml#re_n-57) Clarke, Rachel, and Taryn Youngstein. “Cyberattack on Britain’s National Health Service—a wake-up call for modern medicine.” *The New England Journal of Medicine* 377, no. 5 (2017): 409–11.[↩](#fnref89)
    90.  [59](#c2.xhtml#re_n-59) Bowden, Mark. “The worm that nearly ate the Internet.” *The New York Times*, June 9, 2019. Retrieved from [https://www.nytimes.com/2019/06/29/opinion/sunday/conficker-worm-ukraine.html](https://www.nytimes.com)[↩](#fnref90)
    91.  [60](#c2.xhtml#re_n-60) Farral, Travis. “Nation-state attacks: Practical defences against advanced adversaries.” *Network Security* 2017, no. 9 (2017): 5–7.[↩](#fnref91)
    92.  [63](#c2.xhtml#re_n-63) “European Commission-Data Protection Directive 95/46/ec.” Last modified June 28, 2018. Retrieved from [https://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=CELEX%3A31995L0046%3Aen%3AHTML](https://eur-lex.europa.eu)[↩](#fnref92)
    93.  [65](#c2.xhtml#re_n-65) Hammouchi, Hicham, Othmane Cherqi, Ghita Mezzour, Mounir Ghogho, and Mohammed El Koutbi. “Digging deeper into data breaches: An exploratory data analysis of hacking breaches over time.” *Procedia Computer Science* 151 (2019): 1004–1009.[↩](#fnref93)
    94.  [66](#c2.xhtml#re_n-66) “Management alert – FEMA did not safeguard disaster survivors’ sensitive personally identifiable information.” Office of Inspector General Department of Homeland Security. Last modified March 15, 2019. Retrieved from [https://www.oig.dhs.gov/sites/default/files/assets/2019-03/OIG-19-32-Mar19.pdf;](https://www.oig.dhs.gov) [https://www.oig.dhs.gov/reports/2019/management-alert-fema-did-not-safeguard-disaster-survivors-sensitive-personally-identifiable-information-redacted/oig-19-32-mar19](https://www.oig.dhs.gov)[↩](#fnref94)
    95.  [67](#c2.xhtml#re_n-67) *Id.* at 41.[↩](#fnref95)
    96.  [69](#c2.xhtml#re_n-69) Inkster, Nigel. *China’s Cyber Power*. Routledge, 2018.[↩](#fnref96)
    97.  [71](#c2.xhtml#re_n-71) Manky, Derek. “Cybercrime as a service: A very modern business.” *Computer Fraud & Security* 2013, no. 6 (2013): 9–13.[↩](#fnref97)
    98.  [72](#c2.xhtml#re_n-72) “Internet Organized Crime Threat Assessment by Europol (IOCTA 2018).” Last modified 2018. Retrieved from [https://www.europol.europa.eu/internet-organised-crime-threat-assessment-2018](https://www.europol.europa.eu)[↩](#fnref98)
    99.  [73](#c2.xhtml#re_n-73) Weimann, Gabriel. “Going dark: Terrorism on the dark web.” *Studies in Conflict & Terrorism* 39, no. 3 (2016): 195–206.[↩](#fnref99)
    100.  [75](#c2.xhtml#re_n-75) Bradbury, Danny. “Unveiling the dark web.” *Network Security* 2014, no. 4 (2014): 14–17.[↩](#fnref100)
    101.  [76](#c2.xhtml#re_n-76) Brewer, Ross. “Ransomware attacks: Detection, prevention and cure.” *Network Security* 2016, no. 9 (2016): 5–9.[↩](#fnref101)
    102.  [77](#c2.xhtml#re_n-77) “The Federal Bureau of Investigation—cyber actors use internet of things devices as proxies for anonymity and pursuit of malicious cyber activities” Last modified August 2, 2018. Retrieved from [https://www.ic3.gov/media/2018/180802.aspx](https://www.ic3.gov)[↩](#fnref102)
    103.  [78](#c2.xhtml#re_n-78) Lindqvist, Ulf, and Peter G. Neumann. “The future of the Internet of Things.” *Communications of the ACM* 60, no. 2 (2017): 26–30.[↩](#fnref103)
    104.  [79](#c2.xhtml#re_n-79) Al-Falahy, Naser, and Omar Y. Alani. “Technologies for 5G networks: Challenges and opportunities.” *IT Professional* 19, no. 1 (2017): 12–20.[↩](#fnref104)
    105.  [80](#c2.xhtml#re_n-80) Hellingman, Cornellis. “Newton’s third law revisited.” *Physics Education* 27, no. 2 (1992): 112.[↩](#fnref105)
    106.  [81](#c2.xhtml#re_n-81) “An end-to-end open source machine learning platform.” Google. Last modified May 2018. Retrieved from [https://www.tensorflow.org/](https://www.tensorflow.org)[↩](#fnref106)
    107.  [82](#c2.xhtml#re_n-82) Child Pornography Prevention Act of 1996. Retrieved from [https://www.congress.gov/bill/104th-congress/house-bill/4123](https://www.congress.gov)[↩](#fnref107)
    108.  [85](#c2.xhtml#re_n-85) *Id.* at 72.[↩](#fnref108)
    109.  [86](#c2.xhtml#re_n-86) “The second half of humanity is joining the internet.” *The Economist*. Last modified June 8, 2019. Retrieved from [https://www.economist.com/leaders/2019/06/08/the-second-half-of-humanity-is-joining-the-internet](https://www.economist.com)[↩](#fnref109)
    110.  [87](#c2.xhtml#re_n-87) Lewis, James. *McAfee report—Economic Impact of Cybercrime—No Slowing Down*. Last modified February, 2018. Retrieved from [https://www.mcafee.com/enterprise/en-us/solutions/lp/economics-cybercrime.html](https://www.mcafee.com)[↩](#fnref110)
    111.  [88](#c2.xhtml#re_n-88) Dreyer Paul, Jones Therese, Klima Kelly, Oberholtzer Jenny, Strong Aaron, Welburn William Jonathan, Winkelman Zev. *Estimating the global cost of cyber risk calculator*. RAND Corporation, 2018. Last modified January 15, 2018. Retrieved from [https://www.rand.org/pubs/tools/TL281.html](https://www.rand.org)[↩](#fnref111)
    112.  [89](#c2.xhtml#re_n-89) *Id.* at 72.[↩](#fnref112)
    113.  [91](#c2.xhtml#re_n-91) CipherTrace. “Cryptocurrency anti-Money laundering report, 2019.” Last modified April 2019. Retrieved from [https://ciphertrace.com/wp-content/uploads/2019/05/ciphertrace-q1-2019-cryptocurrency-anti-money-laundering-report.pdf](https://ciphertrace.com)[↩](#fnref113)
    114.  [93](#c2.xhtml#re_n-93) Lawson, Sean, and Michael K. Middleton. “Cyber Pearl Harbor: Analogy, fear, and the framing of cyber security threats in the United States, 1991–2016.” *First Monday* 24, no. 3 (2019).[↩](#fnref114)
    115.  [94](#c2.xhtml#re_n-94) Kostyuk, Nadiya, and Yuri M. Zhukov. “Invisible digital front: Can cyber attacks shape battlefield events?.” *Journal of Conflict Resolution* 63, no. 2 (2019): 317–347.[↩](#fnref115)
    116.  [97](#c2.xhtml#re_n-97) Hjortdal, Magnus. “China’s use of cyber warfare: Espionage meets strategic deterrence.” *Journal of Strategic Security* 4, no. 2 (2011): 1–24.[↩](#fnref116)
    117.  [99](#c2.xhtml#re_n-99) Shachaf, Pnina, and Noriko Hara. “Beyond vandalism: Wikipedia trolls.” *Journal of Information Science* 36, no. 3 (2010): 357–370.[↩](#fnref117)
    118.  [1](#c3.xhtml#re_n-1) Sadoff, David A. *Bringing international fugitives to justice: Extradition and its alternatives*. Cambridge University Press, 2016.[↩](#fnref118)
    119.  [3](#c3.xhtml#re_n-3) Kofele-Kale, Ndiva. *The international law of responsibility for economic crimes: Holding state officials individually liable for acts of fraudulent enrichment*. Routledge, 2016[↩](#fnref119)
    120.  [5](#c3.xhtml#re_n-5) Jardine, Eric. “The Dark Web dilemma: Tor, anonymity and online policing.” *Global Commission on Internet Governance Paper Series* 21 (2015).[↩](#fnref120)
    121.  [6](#c3.xhtml#re_n-6) Jowett, Benjamin. *Politics by Aristotle (Written 350 B.C.E).* Indo-European Publishing, 2012.[↩](#fnref121)
    122.  [7](#c3.xhtml#re_n-7) “United States Senate,” Constitution of the United States, [https://www.senate.gov/civics/constitution\_item/constitution.htm](https://www.senate.gov)[↩](#fnref122)
    123.  [8](#c3.xhtml#re_n-8) U.S. Constitution, pmbl.[↩](#fnref123)
    124.  [9](#c3.xhtml#re_n-9) U.S. Const. Art. VI, Clause 2.[↩](#fnref124)
    125.  [10](#c3.xhtml#re_n-10) Private Law 112–1—An act for the relief of Sopuruchi Chukwueke. Retrieved from [https://www.congress.gov/112/plaws/pvtl1/PLAW-112pvtl1.pdf](https://www.congress.gov)[↩](#fnref125)
    126.  [11](#c3.xhtml#re_n-11) “Office of the Law Revision Counsel of the United States House of Representatives,” United States Code, last modified August 23, 2019, [http://uscode.house.gov](http://uscode.house.gov).[↩](#fnref126)
    127.  [12](#c3.xhtml#re_n-12) *Id.* at 11.[↩](#fnref127)
    128.  [14](#c3.xhtml#re_n-14) “Office of the Law Revision Counsel of the United States House of Representatives, Title 18/Part I/Chapter 47—Fraud and False Statements, United States Code, last modified August 23, 2019, [https://uscode.house.gov/view.xhtml?path=/prelim@title18/part1/chapter47&edition=prelim](https://uscode.house.gov)[↩](#fnref128)
    129.  [15](#c3.xhtml#re_n-15) Electronic Code of Federal Regulations. Retrieved from [https://www.ecfr.gov/cgi-bin/ECFR?page=browse](https://www.ecfr.gov)[↩](#fnref129)
    130.  [16](#c3.xhtml#re_n-16) “Supreme Court of the United Stated,” *Gamble v. United States*, [https://www.supremecourt.gov/search.aspx?Search=Gamble+v.+United+States&type=Site](https://www.supremecourt.gov) [https://www.supremecourt.gov/opinions/18pdf/17-646\_new2\_1an2.pdf](https://www.supremecourt.gov)[↩](#fnref130)
    131.  [17](#c3.xhtml#re_n-17) Black, Henry Campbell, Bryan A. Garner, Becky R. McDaniel, David W. Schultz, and West Publishing Company. *Black’s Law Dictionary*. Vol. 196. St. Paul, MN: West Group, 1999.[↩](#fnref131)
    132.  [1](#c4.xhtml#re_n-1) Greenwald, Glenn. *No place to hide: Edward Snowden, the NSA, and the US surveillance state*. Macmillan, 2014.[↩](#fnref132)
    133.  [2](#c4.xhtml#re_n-2) USA Patriot Act, The United States Department of Justice. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-107publ56/pdf/PLAW-107publ56.pdf](https://www.govinfo.gov)[↩](#fnref133)
    134.  [3](#c4.xhtml#re_n-3) European Union Law, *Official Journal of the European Union*, Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016, General Data Protection Regulation. Retrieved from [https://eur-lex.europa.eu/eli/reg/2016/679/oj](https://eur-lex.europa.eu)[↩](#fnref134)
    135.  [4](#c4.xhtml#re_n-4) Australian Government, Federal Register of Legislation. [https://www.legislation.gov.au/Details/C2018A00148](https://www.legislation.gov.au)[↩](#fnref135)
    136.  [5](#c4.xhtml#re_n-5) The California Consumer Privacy Act of 2018 (CCPA), California Legislative information. Retrieved from [https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill\_id=201720180AB375https://leginfo.legislature.ca.gov/faces/billCompareClient.xhtml?bill\_id=201720180AB375](https://leginfo.legislature.ca.gov)[↩](#fnref136)
    137.  [6](#c4.xhtml#re_n-6) 18 U.S.C. 1030—Fraud and related activity in connection with computers. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/app/details/USCODE-2010-title18/USCODE-2010-title18-partI-chap47-sec1030/summary](https://www.govinfo.gov)[↩](#fnref137)
    138.  [9](#c4.xhtml#re_n-9) Skibell, Reid. “Cybercrime & (and) Misdemeanors: A Reevaluation of the Computer Fraud and Abuse Act.” *Berkeley Tech. LJ* 18 (2003): 909.[↩](#fnref138)
    139.  [11](#c4.xhtml#re_n-11) Jarrett, H. M., and M. W. Bailie. *Prosecution of computer. Office of Legal Education Executive Office for United States Attorneys*. Retrieved from [https://www.justice.gov/sites/default/files/criminal-ccips/legacy/2015/01/14/ccmanual.pdf](https://www.justice.gov)[↩](#fnref139)
    140.  [13](#c4.xhtml#re_n-13) *United States v. Ivanov*, 175 F. Supp. 2d 367 (D. Conn. 2001).[↩](#fnref140)
    141.  [15](#c4.xhtml#re_n-15) U.S.C. §1030(e)(6).[↩](#fnref141)
    142.  [16](#c4.xhtml#re_n-16) *United States v. Nosal*, 676 F.3d 854 (9th Cir. 2012).[↩](#fnref142)
    143.  [18](#c4.xhtml#re_n-18) *United States v. Morris*, 928 F.2d 504, 505 (2d Cir. 1991).[↩](#fnref143)
    144.  [19](#c4.xhtml#re_n-19) *United States v. Nosal*, 676 F.3d 854 (9th Cir.2012) (en banc).[↩](#fnref144)
    145.  [20](#c4.xhtml#re_n-20) U.S.C. 1030—Fraud and related activity in connection with computers. U.S. Government Publishing Office [https://www.govinfo.gov/content/pkg/USCODE-2010-title18/html/USCODE-2010-title18-partI-chap47-sec1030.htm](https://www.govinfo.gov)[↩](#fnref145)
    146.  [21](#c4.xhtml#re_n-21) *United States v. Nosal*, 676 F.3d 854 (9th Cir.2012) (en banc), Retrieved from [http://cdn.ca9.uscourts.gov/datastore/opinions/2011/04/28/10-10038.pdf](http://cdn.ca9.uscourts.gov)[↩](#fnref146)
    147.  [22](#c4.xhtml#re_n-22) *United States v. Drew*, 259 F.R.D. 449, 461 (C.D.Cal. 2009).[↩](#fnref147)
    148.  [23](#c4.xhtml#re_n-23) *United States v. John*, 597 F.3d 263 (5th Cir. 2010).[↩](#fnref148)
    149.  [25](#c4.xhtml#re_n-25) *United States v. Rodriguez*, 628 F.3d 1258 (11th Cir. 2010).[↩](#fnref149)
    150.  [26](#c4.xhtml#re_n-26) U.S. Attorney’s Office District of Massachusetts. “Alleged hacker charged with stealing over four million documents from MIT network” (July 19, 2011). Press release. Retrieved from [http://www.justice.gov/usao/ma/news/2011/July/SwartzAaronPR.html](http://www.justice.gov)[↩](#fnref150)
    151.  [31](#c4.xhtml#re_n-31) Official Internet site of the Florida Legislature. Florida Statutes Title XLVI. Crimes § 815.01. Retrieved from [http://www.leg.state.fl.us/Statutes/index.cfm?App\_mode=Display\_Statute&URL=0800-0899/0815/Sections/0815.06.html](http://www.leg.state.fl.us)[↩](#fnref151)
    152.  [36](#c4.xhtml#re_n-36) The United States Department of Justice. 18 U.S.C. §1831 (economic espionage) and 18 U.S.C. §1832 (theft of trade secrets). Retrieved from [https://www.justice.gov/jm/criminal-resource-manual-1122-introduction-economic-espionage-act](https://www.justice.gov)[↩](#fnref152)
    153.  [38](#c4.xhtml#re_n-38) 18 U.S.C. §1836.[↩](#fnref153)
    154.  [39](#c4.xhtml#re_n-39) 18 U.S.C. § 1836.[↩](#fnref154)
    155.  [42](#c4.xhtml#re_n-42) *U.S. v. Liew CR 11-00573-1*, 4 JSW (N.D. Cal. Jun. 9, 2014). Retrieved from [http://cdn.ca9.uscourts.gov/datastore/opinions/2017/05/05/14-10367.pdf](http://cdn.ca9.uscourts.gov)[↩](#fnref155)
    156.  [45](#c4.xhtml#re_n-45) Office of the Law Revision Counsel of the United States House of Representatives. United States Code, Retrieved from [https://uscode.house.gov/view.xhtml?req=granuleid:USC-prelim-title18-section1839&num=0&edition=prelim](https://uscode.house.gov)[↩](#fnref156)
    157.  [46](#c4.xhtml#re_n-46) The United States Department of Justice. Retrieved from [https://www.justice.gov/opa/pr/us-charges-five-chinese-military-hackers-cyber-espionage-against-us-corporations-and-labor](https://www.justice.gov)[↩](#fnref157)
    158.  [47](#c4.xhtml#re_n-47) Pub. L. No. 105-304, 112 Stat. 2860 (Oct. 28, 1998).[↩](#fnref158)
    159.  [50](#c4.xhtml#re_n-50) Office of the Law Revision Counsel of the United States House of Representatives. United States Code. Retrieved from [https://uscode.house.gov/view.xhtml?req=granuleid:USC-prelim-title17-section107&num=0&edition=prelim](https://uscode.house.gov)[↩](#fnref159)
    160.  [51](#c4.xhtml#re_n-51) 17 U.S.C. § 1201.[↩](#fnref160)
    161.  [52](#c4.xhtml#re_n-52) U.S. Congress. H. Rept. No. 105-551-WIPO Copyright Treaties Implementation and On-Line Copyright Infringement Liability Limitation. Retrieved from [https://www.congress.gov/congressional-report/105th-congress/house-report/551/1](https://www.congress.gov)[↩](#fnref161)
    162.  [53](#c4.xhtml#re_n-53) U.S.C. § 1201 (b) (1).[↩](#fnref162)
    163.  [54](#c4.xhtml#re_n-54) U.S.C. § 1202.  
            United States Code. 17 U.S.C. § 1202—Integrity of copyright management information. U.S. Government Publishing Office. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/app/details/USCODE-2016-title17/USCODE-2016-title17-chap12-sec1202](https://www.govinfo.gov)[↩](#fnref163)
    164.  [55](#c4.xhtml#re_n-55) 17 U.S.C. § 1203—Civil remedies.[↩](#fnref164)
    165.  [57](#c4.xhtml#re_n-57) United States Code. 17 U.S.C. § 1204—Criminal offenses and penalties. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/app/details/USCODE-1998-title17/USCODE-1998-title17-chap12-sec1204](https://www.govinfo.gov)[↩](#fnref165)
    166.  [58](#c4.xhtml#re_n-58) *Friedman v. Live Nation Merch., Inc*., No. 14-55302 (9th Cir. Aug.18, 2016). United States Court of Appeals for the Ninth Circuit. Retrieved from [https://cdn.ca9.uscourts.gov/datastore/opinions/2016/08/18/14-55302.pdf](https://cdn.ca9.uscourts.gov)[↩](#fnref166)
    167.  [59](#c4.xhtml#re_n-59) *Id.* at 58.[↩](#fnref167)
    168.  [60](#c4.xhtml#re_n-60) *Craigslist, Inc. v. Naturemarket, Inc.*, 694 F. Supp. 2d 1039, 1048–49 (N.D. Cal. 2010).[↩](#fnref168)
    169.  [62](#c4.xhtml#re_n-62) *MDY Industries, Inc. LLC v. Blizzard Entertainment*, 629 F.3d 928 (9th Cir. 2010).[↩](#fnref169)
    170.  [64](#c4.xhtml#re_n-64) United States Court of Appeals for the Ninth Circuit. *MDY Industries, Inc. LLC v. Blizzard Entertainment*, 629 F.3d 928 (9th Cir. 2010). Retrieved from [http://cdn.ca9.uscourts.gov/datastore/opinions/2011/02/17/09-15932.pdf](http://cdn.ca9.uscourts.gov)[↩](#fnref170)
    171.  [65](#c4.xhtml#re_n-65) NIST Timeline. Retrieved from [https://www.nist.gov/timeline#event-774241](https://www.nist.gov)[↩](#fnref171)
    172.  [67](#c4.xhtml#re_n-67) Presidential Executive Order on Improving Critical Infrastructure (February 12, 2013) [https://obamawhitehouse.archives.gov/the-press-office/2013/02/12/executive-order-improving-critical-infrastructure-cybersecurity](https://obamawhitehouse.archives.gov)[↩](#fnref172)
    173.  [71](#c4.xhtml#re_n-71)[↩](#fnref173)
    174.  [73](#c4.xhtml#re_n-73) U.S. Congress Cybersecurity Enhancement Act of 2014. Retrieved from [https://www.congress.gov/bill/113th-congress/senate-bill/1353/text](https://www.congress.gov)[↩](#fnref174)
    175.  [74](#c4.xhtml#re_n-74) Framework for Improving Critical Infrastructure Cybersecurity. Version 1.1 National Institute of Standards and Technology. April 16, 2018. Retrieved from [https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf](https://nvlpubs.nist.gov)[↩](#fnref175)
    176.  [75](#c4.xhtml#re_n-75) U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-104publ191/pdf/PLAW-104publ191.pdf](https://www.govinfo.gov)[↩](#fnref176)
    177.  [79](#c4.xhtml#re_n-79) *Id.* at 76.[↩](#fnref177)
    178.  [80](#c4.xhtml#re_n-80) 45 C.F.R. § 164.304.[↩](#fnref178)
    179.  [81](#c4.xhtml#re_n-81) Health and Human Services. Health Information Privacy Cover. Covered Entities and Business Associates. Retrieved from [https://www.hhs.gov/hipaa/for-professionals/covered-entities/index.html](https://www.hhs.gov)[↩](#fnref179)
    180.  [82](#c4.xhtml#re_n-82) CFR § 160.103.[↩](#fnref180)
    181.  [83](#c4.xhtml#re_n-83) *Id*. at 80.[↩](#fnref181)
    182.  [84](#c4.xhtml#re_n-84) The American Recovery and Reinvestment Act of 2009. TITLE XIII—The Health Information Technology for Economic and Clinical Health (HITECH) Act. SEC. 13410. Improved Enforcement. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-111publ5/pdf/PLAW-111publ5.pdf](https://www.govinfo.gov)[↩](#fnref182)
    183.  [85](#c4.xhtml#re_n-85) *Id.*at 82.[↩](#fnref183)
    184.  [87](#c4.xhtml#re_n-87) Hoofnagle, Chris Jay. Federal Trade Commission privacy law and policy. Cambridge University Press, 2016.[↩](#fnref184)
    185.  [91](#c4.xhtml#re_n-91) 15 U.S.C. §§ 1601-1667f. Retrieved from [https://uscode.house.gov/view.xhtml?req=granuleid%3AUSC-prelim-title15-chapter41-subchapter1&edition=prelim](https://uscode.house.gov)[↩](#fnref185)
    186.  [98](#c4.xhtml#re_n-98) The Federal Trade Commission. FTC Imposes $5 Billion Penalty and Sweeping New Privacy Restrictions on Facebook. Retrieved from [https://www.ftc.gov/news-events/press-releases/2019/07/ftc-imposes-5-billion-penalty-sweeping-new-privacy-restrictions](https://www.ftc.gov)[↩](#fnref186)
    187.  [99](#c4.xhtml#re_n-99) Public Law 106–102—Nov. 12, 1999. The Gramm-Leach-Bliley Act. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-106publ102/pdf/PLAW-106publ102.pdf](https://www.govinfo.gov)[↩](#fnref187)
    188.  [100](#c4.xhtml#re_n-100) U.S.C. § 6801(a)(b).[↩](#fnref188)
    189.  [101](#c4.xhtml#re_n-101) U.S.C. § 6809(4).[↩](#fnref189)
    190.  [102](#c4.xhtml#re_n-102) *Id.* at 98.[↩](#fnref190)
    191.  [104](#c4.xhtml#re_n-104) 17 C.F.R. §248.30.[↩](#fnref191)
    192.  [105](#c4.xhtml#re_n-105) 15 U.S.C. § 6801 et seq.[↩](#fnref192)
    193.  [106](#c4.xhtml#re_n-106) 15 U.S.C. § 6805.[↩](#fnref193)
    194.  [107](#c4.xhtml#re_n-107) U.S. Congress. H.R.2622—Fair and Accurate Credit Transactions Act of 2003, Public Law No: 108–159 (12/04/2003). Retrieved from [https://www.congress.gov/bill/108th-congress/house-bill/2622/text](https://www.congress.gov)[↩](#fnref194)
    195.  [110](#c4.xhtml#re_n-110) Pub.L.109-58; EPACT05-Energy Policy Act of 2005. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-109publ58/html/PLAW-109publ58.htm](https://www.govinfo.gov)[↩](#fnref195)
    196.  [113](#c4.xhtml#re_n-113) Congressional Research Service, Electric Grid Cybersecurity (R45312). Updated September 4, 2018. Retrieved from [https://crsreports.congress.gov](https://crsreports.congress.gov)[↩](#fnref196)
    197.  [116](#c4.xhtml#re_n-116) Presidential Executive Order on Strengthening the Cybersecurity of Federal Networks and Critical Infrastructure. Retrieved from [https://www.whitehouse.gov/presidential-actions/presidential-executive-order-strengthening-cybersecurity-federal-networks-critical-infrastructure/](https://www.whitehouse.gov)[↩](#fnref197)
    198.  [117](#c4.xhtml#re_n-117) North American Electric Reliability Corporation (NERC), CIP Standards. Retrieved from [https://www.nerc.com/pa/Stand/Pages/CIPStandards.aspx](https://www.nerc.com)[↩](#fnref198)
    199.  [119](#c4.xhtml#re_n-119) 10 C.F.R. §73.54—Protection of digital computer and communication systems and networks. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/CFR-2012-title10-vol2/pdf/CFR-2012-title10-vol2-sec73-54.pdf](https://www.govinfo.gov)[↩](#fnref199)
    200.  [123](#c4.xhtml#re_n-123) Pub. L. 114-113 Consolidated Appropriations Act 2016. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-114publ113/html/PLAW-114publ113.htm](https://www.govinfo.gov)[↩](#fnref200)
    201.  [126](#c4.xhtml#re_n-126) *Id.*at 122.[↩](#fnref201)
    202.  [127](#c4.xhtml#re_n-127) Cybersecurity and Infrastructure Security Agency (CISA). Retrieved from [https://www.cisa.gov/](https://www.cisa.gov)[↩](#fnref202)
    203.  [130](#c4.xhtml#re_n-130) U.S. Congress, National Cybersecurity and Critical Infrastructure Protection Act of 2014. Retrieved from [https://www.congress.gov/bill/113th-congress/house-bill/3696](https://www.congress.gov)[↩](#fnref203)
    204.  [132](#c4.xhtml#re_n-132) *Id.* at 71.[↩](#fnref204)
    205.  [134](#c4.xhtml#re_n-134) *Id.* at 1.[↩](#fnref205)
    206.  [135](#c4.xhtml#re_n-135) Pub. L. 107-347 E-Government Act of 2002. U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/CRPT-107hrpt787/html/CRPT-107hrpt787-pt1.htm](https://www.govinfo.gov)[↩](#fnref206)
    207.  [137](#c4.xhtml#re_n-137) U.S Congress, Federal Information Security Modernization Act of 2014 (FISMA). Retrieved from [https://www.congress.gov/113/plaws/publ283/PLAW-113publ283.pdf](https://www.congress.gov) or U.S. Government Publishing Office. Retrieved from [https://www.govinfo.gov/content/pkg/CRPT-113srpt256/html/CRPT-113srpt256.htm](https://www.govinfo.gov)[↩](#fnref207)
    208.  [139](#c4.xhtml#re_n-139) NIST, Computer Security Resource Center. Publication search. Retrieved from [https://csrc.nist.gov/publications/fips](https://csrc.nist.gov)[↩](#fnref208)
    209.  [143](#c4.xhtml#re_n-143) 28 U.S.C. § 1651.[↩](#fnref209)
    210.  [144](#c4.xhtml#re_n-144) *United States v. New York Telephone Co.*, 434 U.S. 159 (1977).[↩](#fnref210)
    211.  [145](#c4.xhtml#re_n-145) United States District Courteastern District of New York, No. 15-MC-1902 (JO) (E. D. N. Y. Feb. 29, 2016). Retrieved from [https://img.nyed.uscourts.gov/files/opinions/Order%2015mc1902.pdf](https://img.nyed.uscourts.gov)[↩](#fnref211)
    212.  [146](#c4.xhtml#re_n-146) *Id.* at 143.[↩](#fnref212)
    213.  [147](#c4.xhtml#re_n-147) U.S. Const. Amend. IV.[↩](#fnref213)
    214.  [148](#c4.xhtml#re_n-148) U.S. Const. Amend. XIV, sec. 1.[↩](#fnref214)
    215.  [149](#c4.xhtml#re_n-149) *Missouri v. McNeely*, 569 U.S. 141 (2013). Retrieved from [https://www.supremecourt.gov/opinions/12pdf/11-1425\_cb8e.pdf](https://www.supremecourt.gov)[↩](#fnref215)
    216.  [150](#c4.xhtml#re_n-150) *Riley v. California*, 573 U.S. 373 (2014). Retrieved from [https://www.supremecourt.gov/opinions/13pdf/13-132\_8l9c.pdf](https://www.supremecourt.gov)[↩](#fnref216)
    217.  [151](#c4.xhtml#re_n-151) *Illinois v. Rodriguez* 497 U.S. 177 (1990). Retrieved from [https://cdn.loc.gov/service/ll/usrep/usrep497/usrep497177/usrep497177.pdf](https://cdn.loc.gov)[↩](#fnref217)
    218.  [152](#c4.xhtml#re_n-152) *Horton v. California*, 496 U.S. 128 (1990). Retrieved from [https://cdn.loc.gov/service/ll/usrep/usrep496/usrep496128/usrep496128.pdf](https://cdn.loc.gov)[↩](#fnref218)
    219.  [153](#c4.xhtml#re_n-153) *Dakota v. Opperman*, 428 U.S. 364 (1976). Retrieved from[https://cdn.loc.gov/service/ll/usrep/usrep428/usrep428364/usrep428364.pdf](https://cdn.loc.gov)[↩](#fnref219)
    220.  [154](#c4.xhtml#re_n-154) *United States v. Villamonte-Marquez*, 462 U.S. 579, 585 (1983).[↩](#fnref220)
    221.  [156](#c4.xhtml#re_n-156) *United States V. Richardson*, 607 F. 3d 357 (4th Cir. 2010).[↩](#fnref221)
    222.  [158](#c4.xhtml#re_n-158) *Id.* at 154.[↩](#fnref222)
    223.  [159](#c4.xhtml#re_n-159) *Katz v. United States*, 389 U.S. 347 (1967). Retrieved from [https://cdn.loc.gov/service/ll/usrep/usrep389/usrep389347/usrep389347.pdf](https://cdn.loc.gov)[↩](#fnref223)
    224.  [160](#c4.xhtml#re_n-160) *Id.* at 157.[↩](#fnref224)
    225.  [161](#c4.xhtml#re_n-161) *Carpenter v. United States*, No. 16-402, 585 U.S. \_\_\_\_ (2018). Retrieved from [https://www.supremecourt.gov/opinions/17pdf/16-402\_h315.pdf](https://www.supremecourt.gov)[↩](#fnref225)
    226.  [163](#c4.xhtml#re_n-163) *Mapp v. Ohio*, 367 U.S. 643 (1961).[↩](#fnref226)
    227.  [164](#c4.xhtml#re_n-164) U.S. Congress, House, Uniting and Strengthening America by Providing Appropriate Tools Required to Intercept and Obstruct Terrorism (USA PATRIOT ACT) Act of 2001, HR 3162, 107th. Retrieved from [https://www.congress.gov/bill/107th-congress/house-bill/3162/text](https://www.congress.gov)[↩](#fnref227)
    228.  [165](#c4.xhtml#re_n-165) *Id.* at 162.[↩](#fnref228)
    229.  [167](#c4.xhtml#re_n-167) U.S. Congress, House, Uniting and Strengthening America by Fulfilling Rights and Ensuring Effective Discipline Over Monitoring Act of 2015 (USA Freedom Act of 2015), H. Rept. 114-109. Retrieved from [https://www.congress.gov/114/plaws/publ23/PLAW-114publ23.pdf](https://www.congress.gov)[↩](#fnref229)
    230.  [168](#c4.xhtml#re_n-168) Electronic Communications Privacy Act of 1986 (ECPA), 18 U.S.C. §§ 2510-2523. Retrieved from [https://uscode.house.gov/view.xhtml?path=/prelim@title18/part1/chapter119&edition=prelim](https://uscode.house.gov)[↩](#fnref230)
    231.  [169](#c4.xhtml#re_n-169) *Id.* at 166.[↩](#fnref231)
    232.  [170](#c4.xhtml#re_n-170) U.S. Congress, H.R. 4922—Communications Assistance for Law Enforcement Act 103rd Congress (1993–1994). Retrieved from [https://www.congress.gov/bill/103rd-congress/house-bill/4922/text](https://www.congress.gov)[↩](#fnref232)
    233.  [172](#c4.xhtml#re_n-172) U.S. Codes, 18 USC Ch. 121: Stored wire and electronic communications and transactional records access. Retrieved from [https://uscode.house.gov/view.xhtml?path=/prelim@title18/part1/chapter121&edition=prelim](https://uscode.house.gov)[↩](#fnref233)
    234.  [173](#c4.xhtml#re_n-173) USC Ch. 206: Pen registers and trap and trace devices. Retrieved from [https://uscode.house.gov/view.xhtml?path=/prelim@title18/part2/chapter206&edition=prelim](https://uscode.house.gov)[↩](#fnref234)
    235.  [174](#c4.xhtml#re_n-174) 47 U.S.C §§1001-10.[↩](#fnref235)
    236.  [175](#c4.xhtml#re_n-175) U.S.C. 1002—Assistance capability requirements. Retrieved from [https://www.govinfo.gov/content/pkg/USCODE-2018-title47/pdf/USCODE-2018-title47-chap9-subchapI-sec1002.pdf](https://www.govinfo.gov)[↩](#fnref236)
    237.  [176](#c4.xhtml#re_n-176) 5 U.S.C. § 552a.[↩](#fnref237)
    238.  [180](#c4.xhtml#re_n-180) 15 U.S.C §§ 7701-7713. Retrieved from [https://uscode.house.gov/view.xhtml?req=granuleid%3AUSC-prelim-title15-chapter103&edition=prelim](https://uscode.house.gov)[↩](#fnref238)
    239.  [181](#c4.xhtml#re_n-181) 18 U.S. Code § 1037. Retrieved from [https://www.govinfo.gov/content/pkg/USCODE-2011-title18/html/USCODE-2011-title18-partI-chap47-sec1037.htm](https://www.govinfo.gov)[↩](#fnref239)
    240.  [182](#c4.xhtml#re_n-182) 15 U.S.C. 7704—Other protections for users of commercial electronic mail. Retrieved from [https://www.govinfo.gov/content/pkg/USCODE-2011-title15/pdf/USCODE-2011-title15-chap103-sec7704.pdf](https://www.govinfo.gov)[↩](#fnref240)
    241.  [183](#c4.xhtml#re_n-183) Violent Crime Control and Law Enforcement Act of 1994, Pub. L. No. 103-322, § 250007, 108 Stat. 1796. Retrieved from [https://www.govinfo.gov/content/pkg/STATUTE-108/pdf/STATUTE-108-Pg1796.pdf](https://www.govinfo.gov).[↩](#fnref241)
    242.  [184](#c4.xhtml#re_n-184) U.S Congress H.R. 3601—Identity Theft and Assumption Deterrence Act of 1998. Retrieved from [https://www.congress.gov/bill/105th-congress/house-bill/3601/text](https://www.congress.gov)[↩](#fnref242)
    243.  [186](#c4.xhtml#re_n-186) Federal Trade Commission, Identity Theft and Assumption Deterrence Act. Retrieved from [https://www.ftc.gov/node/119459](https://www.ftc.gov)[↩](#fnref243)
    244.  [187](#c4.xhtml#re_n-187) 15 U.S.C. §§ 6501–06.[↩](#fnref244)
    245.  [189](#c4.xhtml#re_n-189) 16 C.F.R. § 312.2.[↩](#fnref245)
    246.  [190](#c4.xhtml#re_n-190) 16 C.F.R. § 312.5.[↩](#fnref246)
    247.  [191](#c4.xhtml#re_n-191) 18 U.S.C § 2710.[↩](#fnref247)
    248.  [193](#c4.xhtml#re_n-193) *Id.* at 5.[↩](#fnref248)
    249.  [195](#c4.xhtml#re_n-195) Illinois General Assembly, Illinois Biometric Information Privacy Act. Retrieved from [http://www.ilga.gov/legislation/ilcs/ilcs3.asp?ActID=3004&ChapterID=57](http://www.ilga.gov)[↩](#fnref249)
    250.  [1](#c5.xhtml#re_n-1) Deane, Phyllis M., and Phyllis M. Deane. *The first industrial revolution*. Cambridge University Press, 1979.[↩](#fnref250)
    251.  [3](#c5.xhtml#re_n-3) Morrar, Rabeh, Husam Arman, and Saeed Mousa. “The fourth industrial revolution (Industry 4.0): A social innovation perspective.” *Technology Innovation Management Review* 7, no. 11 (2017): 12–20.[↩](#fnref251)
    252.  [4](#c5.xhtml#re_n-4) Forouzan, Behrouz A. *TCP/IP protocol suite*. McGraw-Hill, Inc., 2002.[↩](#fnref252)
    253.  [6](#c5.xhtml#re_n-6) Mathison, Stuart L., Lawrence G. Roberts, and Philip M. Walker. “The history of telenet and the commercialization of packet switching in the US.” *IEEE Communications Magazine* 50, no. 5 (2012): 28–45.[↩](#fnref253)
    254.  [7](#c5.xhtml#re_n-7) *Id.* at 4.[↩](#fnref254)
    255.  [8](#c5.xhtml#re_n-8) Where the Web was born, European Organization for Nuclear Research (CERN). Retrieved from [https://home.cern/science/computing/birth-web/short-history-web](https://home.cern)[↩](#fnref255)
    256.  [9](#c5.xhtml#re_n-9) National Science Foundation. A Brief History of NSF and the Internet. Retrieved from [https://www.nsf.gov/news/news\_summ.jsp?cntn\_id=103050](https://www.nsf.gov)[↩](#fnref256)
    257.  [10](#c5.xhtml#re_n-10) Leiner, Barry M., Vinton G. Cerf, David D. Clark, Robert E. Kahn, Leonard Kleinrock, Daniel C. Lynch, Jon Postel, Lawrence G. Roberts, and Stephen S. Wolff. “The past and future history of the Internet.” *Communications of the ACM* 40, no. 2 (1997): 102–108.[↩](#fnref257)
    258.  [11](#c5.xhtml#re_n-11) Cerf, V., and R. Icahn. “A protocol for packet network intercommunication.” *IEEE Transactions on Communications* 22, no. 5 (May 1974): 637–648. doi: [10.1109/TCOM.1974.1092259](http://doi.org/10.1109/TCOM.1974.1092259).[↩](#fnref258)
    259.  [13](#c5.xhtml#re_n-13) *Id.* at 4.[↩](#fnref259)
    260.  [15](#c5.xhtml#re_n-15) The Internet Engineering Task Force (IETF). Retrieved from [https://tools.ietf.org/html/rfc2460#section-2](https://tools.ietf.org)[↩](#fnref260)
    261.  [16](#c5.xhtml#re_n-16) CISCO SYSTEMS. IPv6 Extension Headers Review and Considerations. [https://www.cisco.com/en/US/technologies/tk648/tk872/technologies\_white\_paper0900aecd8054d37d.html](https://www.cisco.com)[↩](#fnref261)
    262.  [17](#c5.xhtml#re_n-17) ARIN WHOIS IP Address Database Search. Retrieved from [http://itools.com/tool/arin-whois-domain-search](http://itools.com)[↩](#fnref262)
    263.  [18](#c5.xhtml#re_n-18) Klein, Amit, Haya Shulman, and Michael Waidner. “Internet-wide study of dns cache injections.” In *IEEE INFOCOM 2017—IEEE Conference on Computer Communications*, pp. 1–9. IEEE, 2017.[↩](#fnref263)
    264.  [20](#c5.xhtml#re_n-20) DomainKeys Identified Mail (DKIM). Retrieved from [http://www.dkim.org/](http://www.dkim.org))[↩](#fnref264)
    265.  [21](#c5.xhtml#re_n-21) Google Public DNS. Retrieved from [https://developers.google.com/speed/public-dns/docs/using](https://developers.google.com)[↩](#fnref265)
    266.  [24](#c5.xhtml#re_n-24) The Internet Engineering Task Force. IPv6 is an Internet Standard. Retrieved from [https://ietf.org/blog/ipv6-internet-standard/](https://ietf.org) and [https://www.ietf.org/rfc/rfc2460.txt](https://www.ietf.org)[↩](#fnref266)
    267.  [25](#c5.xhtml#re_n-25) Internet Assigned Numbers Authority (IANA). Retrieved by [https://www.iana.org/about](https://www.iana.org)[↩](#fnref267)
    268.  [28](#c5.xhtml#re_n-28) *Id.* at 27.[↩](#fnref268)
    269.  [29](#c5.xhtml#re_n-29) The American Registry for Internet Numbers (ARIN). Retrieved from [https://www.arin.net/resources/guide/ipv6/first\_request/](https://www.arin.net)[↩](#fnref269)
    270.  [30](#c5.xhtml#re_n-30) IP Address Blocks ARIN Issues From. Retrieved from [https://www.arin.net/reference/research/statistics/ip\_blocks/](https://www.arin.net)[↩](#fnref270)
    271.  [32](#c5.xhtml#re_n-32) CISCO Systems, IPv6 Deployment Guide for Cisco Collaboration Systems Release. Retrieved from [https://www.cisco.com/c/en/us/td/docs/voice\_ip\_comm/uc\_system/IPv6/vtgs\_b\_ipv6-deployment-guide-for-cisco/vtgs\_b\_ipv6-deployment-guide-for-cisco\_chapter\_01.html](https://www.cisco.com)[↩](#fnref271)
    272.  [34](#c5.xhtml#re_n-34) ORACLE, System Administration Guide: IP Services. Retrieved from [https://docs.oracle.com/cd/E23823\_01/html/816-4554/ipv6-overview-10.html](https://docs.oracle.com)[↩](#fnref272)
    273.  [35](#c5.xhtml#re_n-35) IANA. Assigned Internet Protocol Numbers. Retrieved from [https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xml](https://www.iana.org)[↩](#fnref273)
    274.  [36](#c5.xhtml#re_n-36) Martin, Jeremy, Travis Mayberry, Collin Donahue, Lucas Foppe, Lamont Brown, Chadwick Riggins, Erik C. Rye, and Dane Brown. “A study of MAC address randomization in mobile devices and when it fails.” *Proceedings on Privacy Enhancing Technologies* 2017, no. 4 (2017): 365–383.[↩](#fnref274)
    275.  [40](#c5.xhtml#re_n-40) *Id.* at 39.[↩](#fnref275)
    276.  [41](#c5.xhtml#re_n-41) CISCO Systems. Network Address Translation (NAT). Retrieved from [https://www.cisco.com/c/en/us/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html](https://www.cisco.com)[↩](#fnref276)
    277.  [42](#c5.xhtml#re_n-42) Angry IP Scanner. Retrieved from [https://angryip.org/](https://angryip.org)[↩](#fnref277)
    278.  [43](#c5.xhtml#re_n-43) iPerf3. Retrieved from [https://iperf.fr/](https://iperf.fr)[↩](#fnref278)
    279.  [44](#c5.xhtml#re_n-44) Netstat. Retrieved from [https://netstatagent.com/download/](https://netstatagent.com)[↩](#fnref279)
    280.  [45](#c5.xhtml#re_n-45) Nmap. Retrieved from [https://nmap.org/](https://nmap.org)[↩](#fnref280)
    281.  [46](#c5.xhtml#re_n-46) PuTTY. Retrieved from [https://www.puttygen.com/download-putty](https://www.puttygen.com)[↩](#fnref281)
    282.  [47](#c5.xhtml#re_n-47) Wireshark. Retrieved from [https://www.wireshark.org/](https://www.wireshark.org)[↩](#fnref282)
    283.  [48](#c5.xhtml#re_n-48) Replacing ifconfig with ip. Retrieved from [https://www.linux.com/training-tutorials/replacing-ifconfig-ip/](https://www.linux.com)[↩](#fnref283)
    284.  [49](#c5.xhtml#re_n-49) CISCO Systems, Understanding and Configuring VLANs. Received from [https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst4500/12-2/25ew/configuration/guide/conf/vlans.html](https://www.cisco.com)[↩](#fnref284)
    285.  [50](#c5.xhtml#re_n-50) Russell, Andrew L. *Open standards and the digital age*. Cambridge University Press, 2014.[↩](#fnref285)
    286.  [51](#c5.xhtml#re_n-51) The ITU Telecommunication Standardization Sector (ITU-T). Recommendation X.200. Retrieved from [https://www.itu.int/rec/T-REC-X.200/en](https://www.itu.int)[↩](#fnref286)
    287.  [52](#c5.xhtml#re_n-52) *Id.* at 12.[↩](#fnref287)
    288.  [55](#c5.xhtml#re_n-55) User Datagram Protocol. Retrieved from [https://tools.ietf.org/html/rfc768](https://tools.ietf.org)[↩](#fnref288)
    289.  [56](#c5.xhtml#re_n-56) IEEE GET Program. Retrieved from [https://standards.ieee.org/products-services/ieee-get-program.html](https://standards.ieee.org)[↩](#fnref289)
    290.  [1](#c6.xhtml#re_n-1) Morkel, Tayana, Jan H. P. Eloff, and Martin S. Olivier. “An overview of image steganography.” In *ISSA*, vol. 1, no. 2. 2005.[↩](#fnref290)
    291.  [2](#c6.xhtml#re_n-2) Luce, Torrey James. *The Greek historians*. Psychology Press, 1997.[↩](#fnref291)
    292.  [5](#c6.xhtml#re_n-5) Tzu, Sun, Sun Tzu, Wu Sun, and Sun Cu Vu. *The art of war*. Vol. 361. Oxford University Press, 1971.[↩](#fnref292)
    293.  [6](#c6.xhtml#re_n-6) Kahn, David. *The Codebreakers: The comprehensive history of secret communication from ancient times to the internet*. Simon and Schuster, 1996.[↩](#fnref293)
    294.  [9](#c6.xhtml#re_n-9) *Id.* at 7.[↩](#fnref294)
    295.  [11](#c6.xhtml#re_n-11) Id. at 7.[↩](#fnref295)
    296.  [12](#c6.xhtml#re_n-12) Id. at 6.[↩](#fnref296)
    297.  [13](#c6.xhtml#re_n-13) United States Code, 2006 Edition, Supplement 5, Title 44—Public Printing and Documents. 44 U.S.C. 3542—Definitions. Retrieved from [https://www.govinfo.gov/app/details/USCODE-2011-title44/USCODE-2011-title44-chap35-subchapIII-sec3542](https://www.govinfo.gov)[↩](#fnref297)
    298.  [14](#c6.xhtml#re_n-14) NIST, Small business information security: The fundamentals. Retrieved from [https://csrc.nist.gov/publications/detail/nistir/7621/rev-1/final](https://csrc.nist.gov)[↩](#fnref298)
    299.  [15](#c6.xhtml#re_n-15) The National Institute of Standards and Technology, Federal Information Processing Standards (FIPS) Publication 199, Standards for Security Categorization of Federal Information and Information Systems. Retrieved from [https://www.nist.gov/privacy-framework/fips-199](https://www.nist.gov)[↩](#fnref299)
    300.  [16](#c6.xhtml#re_n-16) *Id.* at 15.[↩](#fnref300)
    301.  [18](#c6.xhtml#re_n-18) The Cybersecurity and Infrastructure Security Agency (CISA), Advanced Persistent Threat Compromise of Government Agencies, Critical Infrastructure, and Private Sector Organizations. Retrieved from [https://us-cert.cisa.gov/ncas/alerts/aa20-352a](https://us-cert.cisa.gov)[↩](#fnref301)
    302.  [19](#c6.xhtml#re_n-19) Stallings, William, and Lawrie Brown. *Computer security: principles and practice*, fourth edition. Pearson Education, 2017.[↩](#fnref302)
    303.  [20](#c6.xhtml#re_n-20) Common Vulnerabilities and Exposures (CVE). Retrieved from [https://cve.mitre.org/](https://cve.mitre.org)[↩](#fnref303)
    304.  [22](#c6.xhtml#re_n-22) Gao, Jun, Li Li, Pingfan Kong, Tegawendé F. Bissyandé, and Jacques Klein. “Should you consider adware as malware in your study?” In *2019 IEEE 26th International Conference on Software Analysis, Evolution and Reengineering (SANER)*, pp. 604–608. IEEE, 2019.[↩](#fnref304)
    305.  [23](#c6.xhtml#re_n-23) Gupta, B. B., and Omkar P. Badve. “Taxonomy of DoS and DDoS attacks and desirable defense mechanism in a cloud computing environment.” *Neural Computing and Applications* 28, no. 12 (2017): 3655–3682.[↩](#fnref305)
    306.  [24](#c6.xhtml#re_n-24) Khalaf, Bashar Ahmed, S. A. Mostafa, Aida Mustapha, Azizan Ismaila, M. A. Mahmoud, Mohammed Ahmed Jubaira, and M. H. Hassan. “A simulation study of syn flood attack in cloud computing environment.” *REVISTA AUS* 26, no. 1 (2019): 1–19.[↩](#fnref306)
    307.  [25](#c6.xhtml#re_n-25) Sahoo, Kshira Sagar, Sanjaya Kumar Panda, Sampa Sahoo, Bibhudatta Sahoo, and Ratnakar Dash. “Toward secure software-defined networks against distributed denial of service attack.” *The Journal of Supercomputing* 75, no. 8 (2019): 4829–4874.[↩](#fnref307)
    308.  [27](#c6.xhtml#re_n-27) *Id.* at 25.[↩](#fnref308)
    309.  [29](#c6.xhtml#re_n-29) Nicula, Ștefan, and Răzvan Daniel Zota. “Exploiting stack-based buffer overflow using modern day techniques.” *Procedia Computer Science* 160 (2019): 9–14.[↩](#fnref309)
    310.  [30](#c6.xhtml#re_n-30) Seo, Jaebaek, Byoungyoung Lee, Seong Min Kim, Ming-Wei Shih, Insik Shin, Dongsu Han, and Taesoo Kim. “SGX-shield: Enabling address space layout randomization for SGX programs.” In *NDSS*. 2017.[↩](#fnref310)
    311.  [31](#c6.xhtml#re_n-31) *Id.* at 23.[↩](#fnref311)
    312.  [32](#c6.xhtml#re_n-32) Gillman, David, Yin Lin, Bruce Maggs, and Ramesh K. Sitaraman. “Protecting websites from attack with secure delivery networks.” *Computer* 48, no. 4 (2015): 26–34.[↩](#fnref312)
    313.  [34](#c6.xhtml#re_n-34) Cambiaso, Enrico, Gianluca Papaleo, Giovanni Chiola, and Maurizio Aiello. “Slow DoS attacks: Definition and categorisation.” *International Journal of Trust Management in Computing and Communications* 1, no. 3–4 (2013): 300–319.[↩](#fnref313)
    314.  [37](#c6.xhtml#re_n-37) Sun, Xiaoyan, Jun Dai, Peng Liu, Anoop Singhal, and John Yen. “Using Bayesian networks for probabilistic identification of zero-day attack paths.” *IEEE Transactions on Information Forensics and Security* 13, no. 10 (2018): 2506–2521.[↩](#fnref314)
    315.  [38](#c6.xhtml#re_n-38) AWS Shield Threat Landscape Report—Q1 2020. Retrieved from [https://aws-shield-tlr.s3.amazonaws.com/2020-Q1\_AWS\_Shield\_TLR.pdf](https://aws-shield-tlr.s3.amazonaws.com)[↩](#fnref315)
    316.  [39](#c6.xhtml#re_n-39) Hameed, Sufian, and Usman Ali. “HADEC: hadoop-based live DDoS detection framework.” *EURASIP Journal on Information Security* 2018, no. 1 (2018): 1–19.[↩](#fnref316)
    317.  [40](#c6.xhtml#re_n-40) Kambourakis, Georgios, Constantinos Kolias, and Angelos Stavrou. “The mirai botnet and the iot zombie armies.” In *MILCOM 2017–2017 IEEE Military Communications Conference (MILCOM)*, pp. 267–272. IEEE, 2017.[↩](#fnref317)
    318.  [42](#c6.xhtml#re_n-42) Wong, FuiFui, and Cheng Xiang Tan. “A survey of trends in massive DDoS attacks and cloud-based mitigations.” *International Journal of Network Security & Its Applications* 6, no. 3 (2014): 57.[↩](#fnref318)
    319.  [43](#c6.xhtml#re_n-43) Fass, Aurore, Michael Backes, and Ben Stock. “Hidenoseek: Camouflaging malicious javascript in benign asts.” In *Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security*, pp. 1899–1913. 2019.[↩](#fnref319)
    320.  [44](#c6.xhtml#re_n-44) Mane, Yogita Deepak. “Detect and deactivate P2P Zeus bot.” In 2017 8th International Conference on Computing, Communication and Networking Technologies (ICCCNT), pp. 1–7. IEEE, 2017.[↩](#fnref320)
    321.  [47](#c6.xhtml#re_n-47) CISA Ransomware Report Alert, Ransomware Activity Targeting the Healthcare and Public Health Sector (AA20-302A). Retrieved from [https://us-cert.cisa.gov/ncas/alerts/aa20-302a](https://us-cert.cisa.gov)[↩](#fnref321)
    322.  [48](#c6.xhtml#re_n-48) FBI Internet Crime Complaint Center. Retrieved from [https://www.ic3.gov/](https://www.ic3.gov)[↩](#fnref322)
    323.  [49](#c6.xhtml#re_n-49) Iyer, R. Padmavathi, Pradeep K. Atrey, Gaurav Varshney, and Manoj Misra. “Email spoofing detection using volatile memory forensics.” In *2017 IEEE Conference on Communications and Network Security (CNS)*, pp. 619–625. IEEE, 2017.[↩](#fnref323)
    324.  [50](#c6.xhtml#re_n-50) Agrawal, Neha, and Shashikala Tapaswi. “A lightweight approach to detect the low/high rate IP spoofed cloud DDoS attacks.” In *2017 IEEE 7th International Symposium on Cloud and Service Computing (SC2)*, pp. 118–123. IEEE, 2017.[↩](#fnref324)
    325.  [52](#c6.xhtml#re_n-52) Alotaibi, Bandar, and Khaled Elleithy. “A new mac address spoofing detection technique based on random forests.” *Sensors* 16, no. 3 (2016): 281.[↩](#fnref325)
    326.  [53](#c6.xhtml#re_n-53) Nikolov, Linko G. “Wireless network vulnerabilities estimation.” *Security & Future* 2, no. 2 (2018): 80–82.[↩](#fnref326)
    327.  [56](#c6.xhtml#re_n-56) Federal Communications Commission (FCC), Jammer Enforcement. Retrieved from [https://www.fcc.gov/general/jammer-enforcement](https://www.fcc.gov)[↩](#fnref327)
    328.  [58](#c6.xhtml#re_n-58) Noman, Haitham Ameen, Shahidan M. Abdullah, and Haydar Imad Mohammed. “An automated approach to detect deauthentication and disassociation dos attacks on wireless 802.11 networks.” *International Journal of Computer Science Issues (IJCSI)* 12, no. 4 (2015): 107.[↩](#fnref328)
    329.  [60](#c6.xhtml#re_n-60) CISCO Systems, Wi-Fi Protected Setup (WPS) Enrollment Configuration on the WAP121 and WAP321 Access Points. [https://www.cisco.com/c/en/us/support/docs/smb/wireless/cisco-small-business-300-series-wireless-access-points/smb2485-wi-fi-protected-setup-wps-enrollment-configuration-on-the-wa.html](https://www.cisco.com)[↩](#fnref329)
    330.  [63](#c6.xhtml#re_n-63) Wi-Fi Alliance introduces Wi-Fi Certified WPA3 security. Retrieved from [https://www.wi-fi.org/news-events/newsroom/wi-fi-alliance-introduces-wi-fi-certified-wpa3-security](https://www.wi-fi.org)[↩](#fnref330)
    331.  [65](#c6.xhtml#re_n-65) Ashoor, Asmaa Shaker, and Sharad Gore. “Difference between intrusion detection system (IDS) and intrusion prevention system (IPS).” In *International Conference on Network Security and Applications*, pp. 497–501. Springer, 2011.[↩](#fnref331)
    332.  [66](#c6.xhtml#re_n-66) FIDO Alliance. Retrieved from Alliance [https://fidoalliance.org/](https://fidoalliance.org)[↩](#fnref332)
    333.  [67](#c6.xhtml#re_n-67) Traina, P., M. Gramegna, Alessio Avella, A. Cavanna, D. Carpentras, I. P. Degiovanni, G. Brida, and M. Genovese. “Review on recent groundbreaking experiments on quantum communication with orthogonal states.” *Quantum Matter* 2, no. 3 (2013): 153–166.[↩](#fnref333)
    334.  [68](#c6.xhtml#re_n-68) Cruz, Bryan F., Keinaz N. Domingo, Froilan E. De Guzman, Jhinia B. Cotiangco, and Christopher B. Hilario. “Expanded 128-bit data encryption standard.” *International Journal of Computer Science and Mobile Computing* 68, no. 8 (2017): 133–142.[↩](#fnref334)
    335.  [71](#c6.xhtml#re_n-71) Abdullaziz, Osamah Ibrahiem, Li-Chun Wang, and Yu-Jia Chen. “HiAuth: Hidden authentication for protecting software defined networks.” *IEEE Transactions on Network and Service Management* 16, no. 2 (2019): 618–631.[↩](#fnref335)
    336.  [73](#c6.xhtml#re_n-73) McLaren, Peter, William J. Buchanan, Gordon Russell, and Zhiyuan Tan. “Deriving ChaCha20 key streams from targeted memory analysis.” *Journal of Information Security and Applications* 48 (2019): 102372.[↩](#fnref336)
    337.  [74](#c6.xhtml#re_n-74) Coppersmith, Don. “The Data Encryption Standard (DES) and its strength against attacks.” *IBM Journal of Research and Development* 38, no. 3 (1994): 243–250.[↩](#fnref337)
    338.  [76](#c6.xhtml#re_n-76) Abdullah, Dahlan, Robbi Rahim, Andysah Putera Utama Siahaan, Ananda Faridhatul Ulva, Zahratul Fitri, M. Malahayati, and H. Harun. “Super-encryption cryptography with IDEA and WAKE algorithm.” *Journal of Physics: Conference Series* 1019, no. 1 (2018): 012039.[↩](#fnref338)
    339.  [77](#c6.xhtml#re_n-77) Diffie, Whitfield, and Martin Hellman. “New directions in cryptography.” *IEEE transactions on Information Theory* 22, no. 6 (1976): 644–654.[↩](#fnref339)
    340.  [79](#c6.xhtml#re_n-79) ITU Telecommunication Standardization. X.509: Information technology—Open Systems Interconnection—The Directory: Public-key and attribute certificate frameworks. Retrieved from [https://www.itu.int/rec/T-REC-X.509](https://www.itu.int)[↩](#fnref340)
    341.  [80](#c6.xhtml#re_n-80) ITU Telecommunication Standardization. X.509: Information technology—Open Systems Interconnection—The Directory: Public-key and attribute certificate frameworks. Retrieved from [https://www.itu.int/rec/T-REC-X.509](https://www.itu.int)[↩](#fnref341)
    342.  [81](#c6.xhtml#re_n-81) Dang, Quynh. *Recommendation for applications using approved hash algorithms*. U.S. Department of Commerce, National Institute of Standards and Technology, 2008.[↩](#fnref342)
    343.  [82](#c6.xhtml#re_n-82) Stallings, William, Lawrie Brown, Michael D. Bauer, and Arup Kumar Bhattacharjee. *Computer security: Principles and practice*. Pearson Education, 2012.[↩](#fnref343)
    344.  [83](#c6.xhtml#re_n-83) Harnik, Danny, Joe Kilian, Moni Naor, Omer Reingold, and Alon Rosen. “On robust combiners for oblivious transfer and other primitives.” In *Annual International Conference on the Theory and Applications of Cryptographic Techniques*, pp. 96–113. Springer, 2005.[↩](#fnref344)
    345.  [84](#c6.xhtml#re_n-84) SHA-256 hash calculator. Retrieved from [https://xorbin.com/tools/sha256-hash-calculator](https://xorbin.com)[↩](#fnref345)
    346.  [85](#c6.xhtml#re_n-85) Cilardo, Alessandro, and Nicola Mazzocca. “Exploiting vulnerabilities in cryptographic hash functions based on reconfigurable hardware.” *IEEE Transactions on Information Forensics and Security* 8, no. 5 (2013): 810–820.[↩](#fnref346)
    347.  [86](#c6.xhtml#re_n-86) Guo, Jian, San Ling, Christian Rechberger, and Huaxiong Wang. “Advanced meet-in-the-middle preimage attacks: First results on full Tiger, and improved results on MD4 and SHA-2.” In *International Conference on the Theory and Application of Cryptology and Information Security*, pp. 56–75. Springer, 2010.[↩](#fnref347)
    348.  [88](#c6.xhtml#re_n-88) Kelsey, John, Shu-jen Chang, and Ray Perlner. *SHA-3 derived functions: cSHAKE, KMAC, TupleHash, and ParallelHash*. No. NIST Special Publication (SP) 800-185 (Draft). National Institute of Standards and Technology, 2016.[↩](#fnref348)
    349.  [1](#c7.xhtml#re_n-1) Deane, Phyllis M., and Phyllis M. Deane. *The first industrial revolution*. Cambridge University Press, 1979.[↩](#fnref349)
    350.  [2](#c7.xhtml#re_n-2) Ashton, Kevin. “That ‘internet of things’ thing.” *RFID Journal* 22, no. 7 (2009): 97–114.[↩](#fnref350)
    351.  [4](#c7.xhtml#re_n-4) Gershenfeld, Neil A., and Neil Gershenfeld. *When things start to think*. Macmillan, 2000.[↩](#fnref351)
    352.  [5](#c7.xhtml#re_n-5) Vermesan, Ovidiu, Peter Friess, Patrick Guillemin, Sergio Gusmeroli, Harald Sundmaeker, Alessandro Bassi, Ignacio Soler Jubert, et al. “Internet of things strategic research roadmap.” *Internet of Things—Global Technological and Societal Trends* 1, no. 2011 (2011): 9–52.[↩](#fnref352)
    353.  [7](#c7.xhtml#re_n-7) International Data Corporation (IDC). “The growth in connected IoT devices is expected to generate 79.4ZB of data in 2025, according to a new IDC forecast.” Retrieved from [https://www.idc.com/getdoc.jsp?containerId=prUS45213219](https://www.idc.com) (Accessed January 18, 2019).[↩](#fnref353)
    354.  [9](#c7.xhtml#re_n-9) Lu, Ning, Nan Cheng, Ning Zhang, Xuemin Shen, and Jon W. Mark. “Connected vehicles: Solutions and challenges.” *IEEE Internet of Things Journal* 1, no. 4 (2014): 289–299.[↩](#fnref354)
    355.  [11](#c7.xhtml#re_n-11) Alam, Muhammad Mahtab, Hassan Malik, Muhidul Islam Khan, Tamas Pardy, Alar Kuusik, and Yannick Le Moullec. “A survey on the roles of communication technologies in IoT-based personalized healthcare applications.” *IEEE Access* 6 (2018): 36611–36631.[↩](#fnref355)
    356.  [12](#c7.xhtml#re_n-12) Obaidat, M., S. O., J. Holst, A. Al H., J. B, “A Comprehensive and systematic survey on the Internet of things: Security and privacy challenges, security frameworks, enabling technologies, threats, vulnerabilities and countermeasures”, *Computers—IoT: Security, Privacy and Best Practices*. Multidisciplinary Digital Publishing Institute (MDPI)-Basel, Switzerland. 2020/5/30. Obaidat, Muath A., Suhaib Obeidat, Jennifer Holst, Abdullah Al Hayajneh, and Joseph Brown. “A Comprehensive and Systematic Survey on the Internet of Things: Security and Privacy Challenges, Security Frameworks, Enabling Technologies, Threats, Vulnerabilities and Countermeasures.” *Computers* 9, no. 2 (2020): 44.[↩](#fnref356)
    357.  [13](#c7.xhtml#re_n-13) Al-Taee, Majid A., Waleed Al-Nuaimy, Zahra J. Muhsin, and Ali Al-Ataby. “"Robot assistant in management of diabetes in children based on the Internet of things.” *IEEE Internet of Things Journal* 4, no. 2 (2016): 437–445.[↩](#fnref357)
    358.  [15](#c7.xhtml#re_n-15) Lu, Yang. “Industry 4.0: A survey on technologies, applications and open research issues.” *Journal of Industrial Information Integration* 6 (2017): 1–10.[↩](#fnref358)
    359.  [17](#c7.xhtml#re_n-17) Kanigel, Robert. “The one best way: Frederick Winslow Taylor and the enigma of efficiency.” *MIT Press Books* 1 (2005).[↩](#fnref359)
    360.  [19](#c7.xhtml#re_n-19) Rifkin, Jeremy. *The zero marginal cost society: The internet of things, the collaborative commons, and the eclipse of capitalism*. St. Martin’s Press, 2014.[↩](#fnref360)
    361.  [20](#c7.xhtml#re_n-20) Khodjaeva, Matluba, Muath Obaidat, and Douglas Salane. “Mitigating threats and vulnerabilities of RFID in IoT through outsourcing computations for public key cryptography.” In *Security, privacy and trust in the IoT environment*, pp. 39-60. Springer, Cham, 2019.[↩](#fnref361)
    362.  [21](#c7.xhtml#re_n-21) Zhang, Xiangyu, Rajendra Adhikari, Manisa Pipattanasomporn, Murat Kuzlu, and Saifur Rahman. “Deploying IoT devices to make buildings smart: Performance evaluation and deployment experience.” In *2016 IEEE 3rd World Forum on Internet of Things (WF-IoT)*, pp. 530–535. IEEE, 2016.[↩](#fnref362)
    363.  [23](#c7.xhtml#re_n-23) Sethi, Pallavi, and Smruti R. Sarangi. “Internet of things: architectures, protocols, and applications.” *Journal of Electrical and Computer Engineering* 2017 (2017).[↩](#fnref363)
    364.  [24](#c7.xhtml#re_n-24) Sultana, Ayesha, Md Mehebub Alam, Sujoy Kumar Ghosh, Tapas Ranjan Middya, and Dipankar Mandal. “Energy harvesting and self-powered microphone application on multifunctional inorganic-organic hybrid nanogenerator.” *Energy* 166 (2019): 963–971.[↩](#fnref364)
    365.  [25](#c7.xhtml#re_n-25) *Id.* at 23.[↩](#fnref365)
    366.  [26](#c7.xhtml#re_n-26) Yousefpour, Ashkan, Genya Ishigaki, and Jason P. Jue. “Fog computing: Towards minimizing delay in the internet of things.” In *2017 IEEE International Conference on Edge Computing (EDGE)*, pp. 17–24. IEEE, 2017.[↩](#fnref366)
    367.  [28](#c7.xhtml#re_n-28) Shi, Weisong, and Schahram Dustdar. “The promise of edge computing.” *Computer* 49, no. 5 (2016): 78–81.[↩](#fnref367)
    368.  [29](#c7.xhtml#re_n-29) *Id.* at 28.[↩](#fnref368)
    369.  [30](#c7.xhtml#re_n-30) David Linthicum. *Edge computing vs. fog computing: Definitions and enterprise uses*. Retrieved from [https://www.cisco.com/c/en/us/solutions/enterprise-networks/edge-computing.html](https://www.cisco.com)[↩](#fnref369)
    370.  [32](#c7.xhtml#re_n-32) Pramanik, Pijush Kanti Dutta, Prasenjit Choudhury, S. K. Shandilya, S. A. Chun, S. Shandilya, and E. Weippl. “IoT data processing: the different archetypes and their security & privacy assessments.” *Internet of Things (IoT) Security: Fundamentals, Techniques and Applications* (2018): 37–54.[↩](#fnref370)
    371.  [33](#c7.xhtml#re_n-33) *Id.* at 23.[↩](#fnref371)
    372.  [37](#c7.xhtml#re_n-37) Ashraf, Q. M. and M.H. Habaebi. Autonomic schemes for threat mitigation in Internet of Things. *The Journal of Network and Computer Applications* 49 (2015): 112–127. doi: [10.1016/j.jnca.2014.11.011](http://doi.org/10.1016/j.jnca.2014.11.011)[↩](#fnref372)
    373.  [38](#c7.xhtml#re_n-38) Bakhshi, Zeinab, Ali Balador, and Jawad Mustafa. “Industrial IoT security threats and concerns by considering Cisco and Microsoft IoT reference models.” In *2018 IEEE Wireless Communications and Networking Conference Workshops (WCNCW)*, pp. 173–178. IEEE, 2018.[↩](#fnref373)
    374.  [39](#c7.xhtml#re_n-39) Irons-Mclean, Rik, Anthony Sabella, Marcelo Yannuzzi, “IoT and Security Standards and Best Practices,” January 14, 2019, CISCO. Retrieved from [https://www.ciscopress.com/articles/article.asp?p=2923211&seqNum=6](https://www.ciscopress.com)[↩](#fnref374)
    375.  [40](#c7.xhtml#re_n-40) Advancement of Structured Information Standards (OASIS). AMQP v1.0. Retrieved from [https://docs.oasis-open.org/amqp/core/v1.0/os/amqp-core-complete-v1.0-os.pdf](https://docs.oasis-open.org)[↩](#fnref375)
    376.  [42](#c7.xhtml#re_n-42) Naik, Nitin. “Choice of effective messaging protocols for IoT systems: MQTT, CoAP, AMQP and HTTP.” In *2017 IEEE International Systems Engineering Symposium (ISSE)*, pp. 1–7. IEEE, 2017.[↩](#fnref376)
    377.  [43](#c7.xhtml#re_n-43) Object Management Group (OMG), Data Distribution Service (DDS). Retrieved from [https://www.omg.org/omg-dds-portal/](https://www.omg.org)[↩](#fnref377)
    378.  [44](#c7.xhtml#re_n-44) Advancement of Structured Information Standards (OASIS), MQTT Version 3.1.1 Plus Errata 01. Retrieved from [https://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html](https://docs.oasis-open.org)[↩](#fnref378)
    379.  [47](#c7.xhtml#re_n-47) *Id.* at 42.[↩](#fnref379)
    380.  [48](#c7.xhtml#re_n-48) Kim, Hyung-Sin, Jeonggil Ko, David E. Culler, and Jeongyeup Paek. “Challenging the IPv6 routing protocol for low-power and lossy networks (RPL): A survey.” *IEEE Communications Surveys & Tutorials* 19, no. 4 (2017): 2502–2525.[↩](#fnref380)
    381.  [50](#c7.xhtml#re_n-50) Qiu, Yue, and Maode Ma. “A mutual authentication and key establishment scheme for m2m communication in 6lowpan networks.” *IEEE Transactions on Industrial Informatics* 12, no. 6 (2016): 2074–2085.[↩](#fnref381)
    382.  [52](#c7.xhtml#re_n-52) Bluetooth SIG. Bluetooth Core Specification. Retrieved from [https://www.bluetooth.com/specifications/bluetooth-core-specification/](https://www.bluetooth.com)[↩](#fnref382)
    383.  [54](#c7.xhtml#re_n-54) Elsaadany, Mahmoud, Abdelmohsen Ali, and Walaa Hamouda. “Cellular LTE-A technologies for the future Internet-of-Things: Physical layer features and challenges.” *IEEE Communications Surveys & Tutorials* 19, no. 4 (2017): 2544–2572.[↩](#fnref383)
    384.  [55](#c7.xhtml#re_n-55) The DASH7 Alliance Protocol (D7A). Retrieved from [https://dash7-alliance.org/](https://dash7-alliance.org)[↩](#fnref384)
    385.  [56](#c7.xhtml#re_n-56) Law, David, Dan Dove, John D'Ambrosia, Marek Hajduczenia, Mark Laubach, and Steve Carlson. “Evolution of Ethernet standards in the IEEE 802.3 working group.” *IEEE Communications Magazine* 51, no. 8 (2013): 88–96.[↩](#fnref385)
    386.  [58](#c7.xhtml#re_n-58) Al-Sarawi, Shadi, Mohammed Anbar, Kamal Alieyan, and Mahmood Alzubaidi. “Internet of Things (IoT) communication protocols.” In *2017 8th International Conference on Information Technology (ICIT)*, pp. 685–690. IEEE, 2017.[↩](#fnref386)
    387.  [60](#c7.xhtml#re_n-60) Nath, Badri, Franklin Reynolds, and Roy Want. “RFID technology and applications.” *IEEE Pervasive Computing* 5, no. 1 (2006): 22–24.[↩](#fnref387)
    388.  [61](#c7.xhtml#re_n-61) Wi-Fi Alliance, Wi-Fi generations. Retrieved from [https://www.wi-fi.org/discover-wi-fi](https://www.wi-fi.org)[↩](#fnref388)
    389.  [63](#c7.xhtml#re_n-63) Porkodi, R., and V. Bhuvaneswari. “The internet of things (IoT) applications and communication enabling technology standards: An overview.” In *2014 International Conference on Intelligent Computing Applications*, pp. 324–329. IEEE, 2014.[↩](#fnref389)
    390.  [65](#c7.xhtml#re_n-65) Prasad, Ravi, Constantinos Dovrolis, Margaret Murray, and K. C. Claffy. “Bandwidth estimation: metrics, measurement techniques, and tools.” *IEEE Network* 17, no. 6 (2003): 27–35.[↩](#fnref390)
    391.  [67](#c7.xhtml#re_n-67) Mahmoud, Mahmoud S., and Auday AH Mohamad. “A study of efficient power consumption wireless communication techniques/modules for internet of things (IoT) applications.” *Advances in Internet of Things* 6 (2016): 19–29.[↩](#fnref391)
    392.  [68](#c7.xhtml#re_n-68) Kambourakis, Georgios, Constantinos Kolias, and Angelos Stavrou. “The mirai botnet and the IoT zombie armies.” In *MILCOM 2017–2017 IEEE Military Communications Conference (MILCOM)*, pp. 267–272. IEEE, 2017.[↩](#fnref392)
    393.  [70](#c7.xhtml#re_n-70) Yang, Yuchen, Longfei Wu, Guisheng Yin, Lijie Li, and Hongbin Zhao. “A survey on security and privacy issues in Internet-of-Things.” *IEEE Internet of Things Journal* 4, no. 5 (2017): 1250–1258.[↩](#fnref393)
    394.  [71](#c7.xhtml#re_n-71) *Id.* at 70.[↩](#fnref394)
    395.  [74](#c7.xhtml#re_n-74) Andrea, Ioannis, Chrysostomos Chrysostomou, and George Hadjichristofi. “Internet of Things: Security vulnerabilities and challenges.” In *2015 IEEE Symposium on Computers and Communication (ISCC)*, pp. 180–187. IEEE, 2015.[↩](#fnref395)
    396.  [75](#c7.xhtml#re_n-75) *Id.* at 70.[↩](#fnref396)
    397.  [76](#c7.xhtml#re_n-76) Deogirikar, Jyoti, and Amarsinh Vidhate. “Security attacks in IoT: A survey.” In *2017 International Conference on I-SMAC (IoT in Social, Mobile, Analytics and Cloud) (I-SMAC)*, pp. 32–37. IEEE, 2017.[↩](#fnref397)
    398.  [77](#c7.xhtml#re_n-77) *Id.* at 74.[↩](#fnref398)
    399.  [80](#c7.xhtml#re_n-80) Chu, Gordon, Noah Apthorpe, and Nick Feamster. “Security and privacy analyses of Internet of Things children’s toys.” *IEEE Internet of Things Journal* 6, no. 1 (2018): 978–985.[↩](#fnref399)
    400.  [81](#c7.xhtml#re_n-81) McDermott, Christopher D., John P. Isaacs, and Andrei V. Petrovski. “Evaluating awareness and perception of botnet activity within consumer internet-of-things (IoT) networks.” In *Informatics*, vol. 6, no. 1, p. 8. Multidisciplinary Digital Publishing Institute, 2019.[↩](#fnref400)
    401.  [82](#c7.xhtml#re_n-82) NISTIR 8228—Considerations for Managing Internet of Things (IoT) Cybersecurity and Privacy Risks. Retrieved from [https://nvlpubs.nist.gov/nistpubs/ir/2019/NIST.IR.8228.pdf](https://nvlpubs.nist.gov)[↩](#fnref401)
    402.  [1](#c8.xhtml#re_n-1) Nassa, Vinay Kumar. “Wireless communications: Past, present and future.” *Dronacharya Research Journal* 50, July–Dec., 2011.[↩](#fnref402)
    403.  [2](#c8.xhtml#re_n-2) “Motorola Milestones,” last modified September 2018. Retrieved from [https://www.motorola.com/us/about/motorola-history-milestones](https://www.motorola.com)[↩](#fnref403)
    404.  [6](#c8.xhtml#re_n-6) *Id.* at 5.[↩](#fnref404)
    405.  [8](#c8.xhtml#re_n-8) Miao, Guowang, Jens Zander, Ki Won Sung, and Slimane Ben Slimane. *Fundamentals of mobile data networks*. Cambridge University Press, 2016.[↩](#fnref405)
    406.  [9](#c8.xhtml#re_n-9) Steinbock, Dan. *The mobile revolution: The making of mobile services worldwide*. Kogan Page Publishers, 2005.[↩](#fnref406)
    407.  [12](#c8.xhtml#re_n-12) Torrieri, Don. *Principles of spread-spectrum communication systems*. Vol. 1. Heidelberg: Springer, 2005.[↩](#fnref407)
    408.  [15](#c8.xhtml#re_n-15) Ezhilarasan, E., and M. Dinakaran. “A review on mobile technologies: 3G, 4G and 5G.” In *2017 Second International Conference on Recent Trends and Challenges in Computational Models (ICRTCCM)*, pp. 369–373. IEEE, 2017.[↩](#fnref408)
    409.  [17](#c8.xhtml#re_n-17) Astély, David, Erik Dahlman, Anders Furuskär, Ylva Jading, Magnus Lindström, and Stefan Parkvall. “LTE: The evolution of mobile broadband.” *IEEE Communications* 47, no. 4 (2009): 44–51.[↩](#fnref409)
    410.  [19](#c8.xhtml#re_n-19) Fagbohun, O. “Comparative studies on 3G, 4G and 5G wireless technology.” *IOSR Journal of Electronics and Communication Engineering* 9, no. 3 (2014): 88–94.[↩](#fnref410)
    411.  [22](#c8.xhtml#re_n-22) Kim, Yumi, Hyunhee Seo, and Yul Roh. “Metal recovery from the mobile phone waste by chemical and biological treatments.” *Minerals* 8, no. 1 (2018): 8.[↩](#fnref411)
    412.  [23](#c8.xhtml#re_n-23) Tsai, Pei-Shan, Chia-Kai Liang, Tai-Hsiang Huang, and Homer H. Chen. “Image enhancement for backlight-scaled TFT-LCD displays.” *IEEE Transactions on Circuits and Systems for Video Technology* 19, no. 4 (2009): 574–583.[↩](#fnref412)
    413.  [25](#c8.xhtml#re_n-25) *Id.* at 24.[↩](#fnref413)
    414.  [26](#c8.xhtml#re_n-26) Hwang, L. James, and Reno L. Sanchez. “Method and system for resource allocation in FPGA-based system-on-chip (SoC).” U.S. Patent 7,058,921, issued June 6, 2006.[↩](#fnref414)
    415.  [28](#c8.xhtml#re_n-28) Alshahrani, Hani, Harrison Mansourt, Seaver Thorn, Ali Alshehri, Abdulrahman Alzahrani, and Huirong Fu. “DDefender: Android application threat detection using static and dynamic analysis.” In *2018 IEEE International Conference on Consumer Electronics (ICCE)*, pp. 1–6. IEEE, 2018.[↩](#fnref415)
    416.  [29](#c8.xhtml#re_n-29) Novac, Ovidiu Constantin, Mihaela Novac, Cornelia Gordan, Tamas Berczes, and Gyöngyi Bujdosó. “Comparative study of Google Android, Apple iOS and Microsoft Windows phone mobile operating systems.” In *2017 14th International Conference on Engineering of Modern Electric Systems (EMES)*, pp. 154–159. IEEE, 2017.[↩](#fnref416)
    417.  [30](#c8.xhtml#re_n-30) Mayrhofer, René, Jeffrey Vander Stoep, Chad Brubaker, and Nick Kralevich. “The Android platform security model.” *arXiv preprint* arXiv:1904.05572 (2019).[↩](#fnref417)
    418.  [33](#c8.xhtml#re_n-33) Ahvanooey, Milad Taleby, Qianmu Li, Mahdi Rabbani, and Ahmed Raza Rajput. “A survey on smartphones security: software vulnerabilities, malware, and attacks.” *arXiv preprint* arXiv:2001.09406 (2020).[↩](#fnref418)
    419.  [35](#c8.xhtml#re_n-35) *Id.* at 33.[↩](#fnref419)
    420.  [36](#c8.xhtml#re_n-36) Bhat, Parnika, and Kamlesh Dutta. “A survey on various threats and current state of security in android platform.” *ACM Computing Surveys (CSUR)* 52, no. 1 (2019): 1–35.[↩](#fnref420)
    421.  [37](#c8.xhtml#re_n-37) Li, Bodong, Yuanyuan Zhang, Juanru Li, Wenbo Yang, and Dawu Gu. “AppSpear: automating the hidden-code extraction and reassembling of packed android malware.” *Journal of Systems and Software* 140 (2018): 3–16.[↩](#fnref421)
    422.  [39](#c8.xhtml#re_n-39) Meier, Reto, and Ian Lake. *Professional android*. John Wiley & Sons, 2018.[↩](#fnref422)
    423.  [42](#c8.xhtml#re_n-42) Android Architecture. Retrieved from [https://developer.android.com/guide/platform](https://developer.android.com)[↩](#fnref423)
    424.  [43](#c8.xhtml#re_n-43) *Id.* at 42.[↩](#fnref424)
    425.  [44](#c8.xhtml#re_n-44) Kostakis, Vasilis, and Stelios Stavroulakis. “The parody of the commons.” *P2P E INOVAÇÃO* 2, no. 2 (2016): 28–51.[↩](#fnref425)
    426.  [48](#c8.xhtml#re_n-48) *Id.* at 29.[↩](#fnref426)
    427.  [49](#c8.xhtml#re_n-49) Junxiang, Gao, and Huang Yu. “Design of mobile learning system for courses of computer science and technology.” In *Journal of Physics: Conference Series*, vol. 1237, no. 5, p. 052002. IOP Publishing, 2019.[↩](#fnref427)
    428.  [50](#c8.xhtml#re_n-50) Mohamed, Ibtisam, and Dhiren Patel. “Android vs iOS security: A comparative study.” In *2015 12th International Conference on Information Technology—New Generations*, pp. 725–730. IEEE, 2015.[↩](#fnref428)
    429.  [51](#c8.xhtml#re_n-51) Gralla, Preston. *How wireless works*. Que, 2002.[↩](#fnref429)
    430.  [52](#c8.xhtml#re_n-52) Mozaffari, Mohammad, Ali Taleb Zadeh Kasgari, Walid Saad, Mehdi Bennis, and Mérouane Debbah. “Beyond 5G with UAVs: Foundations of a 3D wireless cellular network.” *IEEE Transactions on Wireless Communications* 18, no. 1 (2018): 357–372.[↩](#fnref430)
    431.  [53](#c8.xhtml#re_n-53) Kim, Heeyoung, Rong Duan, Sungil Kim, Jaehwan Lee, and Guang‐Qin Ma. “Spatial cluster detection in mobility networks: A copula approach.” *Journal of the Royal Statistical Society: Series C (Applied Statistics)* 68, no. 1 (2019): 99–120.[↩](#fnref431)
    432.  [54](#c8.xhtml#re_n-54) Rao, R. Srinivasa. *Microwave engineering*. PHI Learning Pvt. Ltd., 2015.[↩](#fnref432)
    433.  [56](#c8.xhtml#re_n-56) Nordrum, Amy, and Kristen Clark. “Everything you need to know about 5G.” *IEEE Spectrum* 27 (2017).[↩](#fnref433)
    434.  [57](#c8.xhtml#re_n-57) *Id.* at 56.[↩](#fnref434)
    435.  [58](#c8.xhtml#re_n-58) Yacoub, Michel Daoud. *Wireless technology: Protocols, standards, and techniques*. CRC Press, 2017.[↩](#fnref435)
    436.  [60](#c8.xhtml#re_n-60) *Id.* at 58.[↩](#fnref436)
    437.  [61](#c8.xhtml#re_n-61) Bojinov, Hristo, Yan Michalevsky, Gabi Nakibly, and Dan Boneh. “Mobile device identification via sensor fingerprinting.” *arXiv preprint* arXiv:1408.1416 (2014).[↩](#fnref437)
    438.  [62](#c8.xhtml#re_n-62) McLaughlin, Kevin. “The Fourth Amendment and cell phone location tracking: Where are we.” *Hastings Communications and Entertainment Law Journal*29 (2006): 421.[↩](#fnref438)
    439.  [67](#c8.xhtml#re_n-67) Dat, Pham Tien, Atsushi Kanno, and Tetsuya Kawanishi. “Radio-on-radio-over-fiber: efficient fronthauling for small cells and moving cells.” *IEEE Wireless Communications* 22, no. 5 (2015): 67–75.[↩](#fnref439)
    440.  [69](#c8.xhtml#re_n-69) Djordjevic, Ivan B. *Advanced optical and wireless communications systems*. Heidelberg: Springer, 2018.[↩](#fnref440)
    441.  [70](#c8.xhtml#re_n-70) Anwar, Nuril, Imam Riadi, and Ahmad Luthfi. “Forensic SIM card cloning using authentication algorithm.” *International Journal of Electronics and Information Engineering* 4, no. 2 (2016): 71–81.[↩](#fnref441)
    442.  [72](#c8.xhtml#re_n-72) Caytan, Olivier, Laurens Bogaert, Haolin Li, Joris Van Kerrebrouck, Sam Lemey, Guy Torfs, Johan Bauwelinck et al. “Passive opto-antenna as downlink remote antenna unit for radio frequency over fiber.” *Journal of Lightwave Technology* 36, no. 19 (2018): 4445–4459.[↩](#fnref442)
    443.  [74](#c8.xhtml#re_n-74) *Id.* at 58.[↩](#fnref443)
    444.  [75](#c8.xhtml#re_n-75) *Id.* at 58.[↩](#fnref444)
    445.  [76](#c8.xhtml#re_n-76) Sattarian, Mahbubeh, Javad Rezazadeh, Reza Farahbakhsh, and Alireza Bagheri. “Indoor navigation systems based on data mining techniques in internet of things: A survey.” *Wireless Networks* 25, no. 3 (2019): 1385–1402.[↩](#fnref445)
    446.  [77](#c8.xhtml#re_n-77) Laoudias, Christos, Adriano Moreira, Sunwoo Kim, Sangwoo Lee, Lauri Wirola, and Carlo Fischione. “A survey of enabling technologies for network localization, tracking, and navigation.” *IEEE Communications Surveys & Tutorials* 20, no. 4 (2018): 3607–3644.[↩](#fnref446)
    447.  [78](#c8.xhtml#re_n-78) *Id.* at 77.[↩](#fnref447)
    448.  [79](#c8.xhtml#re_n-79) Salari, Soheil, Francois Chan, Yiu-Tong Chan, and William Read. “TDOA estimation with compressive sensing measurements and hadamard Matrix.” *IEEE Transactions on Aerospace and Electronic Systems* 54, no. 6 (2018): 3137–3142.[↩](#fnref448)
    449.  [80](#c8.xhtml#re_n-80) Doshi, Pankti, Pooja Jain, and Abhishek Shakwala. “Location based services and integration of google maps in android.” *International Journal of Engineering and Computer Science* 3, no. 3 (2014).[↩](#fnref449)
    450.  [84](#c8.xhtml#re_n-84) Zafari, Faheem, Athanasios Gkelias, and Kin K. Leung. “A survey of indoor localization systems and technologies.” *IEEE Communications Surveys & Tutorials* 21, no. 3 (2019): 2568–2599.[↩](#fnref450)
    451.  [85](#c8.xhtml#re_n-85) *Id.* at 84.[↩](#fnref451)
    452.  [86](#c8.xhtml#re_n-86) Kulshrestha, Tarun, Divya Saxena, Rajdeep Niyogi, Vaskar Raychoudhury, and Manoj Misra. “SmartITS: Smartphone-based identification and tracking using seamless indoor-outdoor localization.” *Journal of Network and Computer Applications* 98 (2017): 97–113.[↩](#fnref452)
    453.  [87](#c8.xhtml#re_n-87) CTIA’s Stolen Phone Checker. Retrieved from [https://stolenphonechecker.org/spc/](https://stolenphonechecker.org)[↩](#fnref453)
    454.  [88](#c8.xhtml#re_n-88) Smartphone Theft Prevention Act of 2015. Retrieved from [https://www.congress.gov/bill/114th-congress/senate-bill/1076/text](https://www.congress.gov)[↩](#fnref454)
    455.  [89](#c8.xhtml#re_n-89) IMEI Database. Retrieved from [https://www.gsma.com/aboutus/workinggroups/terminal-steering-group/imei-database](https://www.gsma.com)[↩](#fnref455)
    456.  [91](#c8.xhtml#re_n-91) Marczak, Bill, and John Scott-Railton. “The million dollar dissident: NSO group’s iPhone zero-days used against a UAE human rights defender.” *Citizen Lab* 24 (2016).[↩](#fnref456)
    457.  [92](#c8.xhtml#re_n-92) Brewster, T. *Forbes.* Everything we know about NSO group: The professional spies who hacked iPhones with a single text. (2016, August 25). Retrieved from [https://www.forbes.com/sites/thomasbrewster/2016/08/25/everything-we-know-about-nso-group-the-professional-spies-who-hacked-iphones-with-a-single-text/#547864c33997](https://www.forbes.com)[↩](#fnref457)
    458.  [93](#c8.xhtml#re_n-93) Felt, Adrienne Porter, Matthew Finifter, Erika Chin, Steve Hanna, and David Wagner. “A survey of mobile malware in the wild.” In *Proceedings of the 1st ACM Workshop on Security and Privacy in Smartphones and Mobile Devices*, pp. 3–14. 2011.[↩](#fnref458)
    459.  [94](#c8.xhtml#re_n-94) McAfee Mobile Threat Report Q1, 2020. Retrieved from [https://www.mcafee.com/content/dam/consumer/en-us/docs/2020-Mobile-Threat-Report.pdf](https://www.mcafee.com)[↩](#fnref459)
    460.  [96](#c8.xhtml#re_n-96) *Id.* at 93.[↩](#fnref460)
    461.  [98](#c8.xhtml#re_n-98) *Id.* at 95.[↩](#fnref461)
    462.  [100](#c8.xhtml#re_n-100) *Id.* at 94.[↩](#fnref462)
    463.  [101](#c8.xhtml#re_n-101) Vanhoef, M., Matte, C., Cunche, M., Cardoso, L. S., & Piessens, F. Why MAC address randomization is not enough: An analysis of Wi-Fi network discovery mechanisms. In *Proceedings of the 11th ACM on Asia Conference on Computer and Communications Security* (pp. 413–424). ACM, May 2016.[↩](#fnref463)
    464.  [105](#c8.xhtml#re_n-105) Chace, Calum. *Artificial intelligence and the two singularities*. CRC Press, 2018.[↩](#fnref464)
    465.  [1](#appendixA.xhtml#re_n-1) 18 U.S.C. 1030 - Fraud and related activity in connection with computers, Retrieved from [https://www.govinfo.gov/content/pkg/USCODE-2010-title18/html/USCODE-2010-title18-partI-chap47-sec1030.htm](https://www.govinfo.gov)[↩](#fnref465)
    466.  [1](#appendixB.xhtml#re_n-1) The WIPO Copyright and Performances and Phonograms Treaties Implementation Act of 1998 added chapter 12, titled “Copyright Protection and Management Systems,” to title 17. Pub. L. No. 105-304, 112 Stat. 2860, 2863. The WIPO Copyright and Performances and Phonograms Treaties Implementation Act of 1998 is title I of the Digital Millennium Copyright Act. Pub. L. No. 105-304, 112 Stat. 2860. Retrieved from [https://www.copyright.gov/title17/92chap12.html](https://www.copyright.gov)[↩](#fnref466)
    467.  [1](#appendixC.xhtml#re_n-1) 45 C.F.R. § 164.208[↩](#fnref467)
    468.  [2](#appendixC.xhtml#re_n-2) 45 C.F.R. § 164.310[↩](#fnref468)
    469.  [3](#appendixC.xhtml#re_n-3) 45 C.F.R. § 164.312[↩](#fnref469)
    470.  [4](#appendixC.xhtml#re_n-4) 45 C.F.R. §164.314[↩](#fnref470)
    471.  [1](#appendixD.xhtml#re_n-1) The American Recovery and Reinvestment Act of 2009. TITLE XIII—The Health Information Technology for Economic and Clinical Health (HITECH) Act. SEC. 13410. Improved Enforcement. Retrieved from [https://www.govinfo.gov/content/pkg/PLAW-111publ5/pdf/PLAW-111publ5.pdf](https://www.govinfo.gov)[↩](#fnref471)
    472.  [1](#appendixE.xhtml#re_n-1) 15 U.S.C. 45 – Unfair methods of competition unlawful; prevention by Commission. Retrieved from [https://www.govinfo.gov/app/details/USCODE-2011-title15/USCODE-2011-title15-chap2-subchapI-sec45](https://www.govinfo.gov)[↩](#fnref472)
    473.  [1](#appendixF.xhtml#re_n-1) 16 C.F.R. §681.1 PART 681—IDENTITY THEFT RULES, Electronic Code of Federal Regulations, e-CFR data is current as of December 31, 2019. Retrieve from [https://www.ecfr.gov/cgi-bin/text-idx?SID=fddfe88d36b1e7881a1b76f4e8437d65&mc=true&node=pt16.1.681&rgn=div5#ap16.1.681\_12.a](https://www.ecfr.gov)[↩](#fnref473)
    474.  [1](#appendixG.xhtml#re_n-1) 6 U.S.C. 1501 – Definitions. Retrieved from [https://www.govinfo.gov/app/details/USCODE-2018-title6/USCODE-2018-title6-chap6-subchapI-sec1501](https://www.govinfo.gov)[↩](#fnref474)
    475.  [1](#appendixI.xhtml#re_n-1) [https://www.cisco.com/c/en/us/training-events/training-certifications/certifications.html](https://www.cisco.com)[↩](#fnref475)
    476.  [2](#appendixI.xhtml#re_n-2) [https://www.comptia.org/certifications](https://www.comptia.org)[↩](#fnref476)
    477.  [3](#appendixI.xhtml#re_n-3) [https://docs.microsoft.com/en-us/learn/certifications/](https://docs.microsoft.com)[↩](#fnref477)
    478.  [4](#appendixI.xhtml#re_n-4) [https://www.isc2.org/Certifications/SSCP](https://www.isc2.org)[↩](#fnref478)
    479.  [5](#appendixI.xhtml#re_n-5) [https://aws.amazon.com/certification/certified-solutions-architect-associate/](https://aws.amazon.com)[↩](#fnref479)
    480.  [6](#appendixI.xhtml#re_n-6) [https://cert.eccouncil.org/certified-ethical-hacker.html](https://cert.eccouncil.org)[↩](#fnref480)
    481.  [7](#appendixI.xhtml#re_n-7) [https://www.isc2.org/Certifications/CISSP](https://www.isc2.org)[↩](#fnref481)
    482.  [8](#appendixI.xhtml#re_n-8) [https://www.cisco.com/c/en/us/training-events/training-certifications/certifications/professional.html](https://www.cisco.com)[↩](#fnref482)
    483.  [9](#appendixI.xhtml#re_n-9) [https://www.cisco.com/c/en/us/training-events/training-certifications/certifications/expert.html](https://www.cisco.com)[↩](#fnref483)
    484.  [10](#appendixI.xhtml#re_n-10) [https://www.cisco.com/c/en/us/training-events/training-certifications/certifications/expert/ccde.html](https://www.cisco.com)[↩](#fnref484)
    485.  [11](#appendixI.xhtml#re_n-11) [https://training.citrix.com/learning/landing-badges/digital-workspace](https://training.citrix.com)[↩](#fnref485)
    486.  [12](#appendixI.xhtml#re_n-12) [https://www.giac.org/](https://www.giac.org)[↩](#fnref486)
    487.  [13](#appendixI.xhtml#re_n-13) [https://cloud.google.com/certification#certification\_paths](https://cloud.google.com)[↩](#fnref487)
    488.  [14](#appendixI.xhtml#re_n-14) [https://www.ibm.com/certify](https://www.ibm.com)[↩](#fnref488)
    489.  [15](#appendixI.xhtml#re_n-15) [https://www.isaca.org/credentialing](https://www.isaca.org)[↩](#fnref489)
    490.  [16](#appendixI.xhtml#re_n-16) [https://www.juniper.net/us/en/training/certification/](https://www.juniper.net)[↩](#fnref490)
    491.  [17](#appendixI.xhtml#re_n-17) [https://www.lpi.org/our-certifications/summary-of-certifications](https://www.lpi.org)[↩](#fnref491)
    492.  [18](#appendixI.xhtml#re_n-18) [https://docs.microsoft.com/en-us/learn/certifications/browse/?resource\_type=certification](https://docs.microsoft.com)[↩](#fnref492)
    493.  [19](#appendixI.xhtml#re_n-19) [https://docs.microsoft.com/en-us/learn/certifications/azure-fundamentals](https://docs.microsoft.com)[↩](#fnref493)
    494.  [20](#appendixI.xhtml#re_n-20) [https://docs.microsoft.com/en-us/learn/certifications/azure-administrator](https://docs.microsoft.com)[↩](#fnref494)
    495.  [21](#appendixI.xhtml#re_n-21) [https://education.oracle.com/certification](https://education.oracle.com)[↩](#fnref495)
    496.  [22](#appendixI.xhtml#re_n-22) [https://www.pmi.org/certifications/project-management-pmp](https://www.pmi.org)[↩](#fnref496)
    497.  [23](#appendixI.xhtml#re_n-23) [https://www.scrumalliance.org/get-certified/scrum-master-track/certified-scrummaster](https://www.scrumalliance.org)[↩](#fnref497)
    498.  [24](#appendixI.xhtml#re_n-24) [https://www.pmi.org/certifications/agile-certifications](https://www.pmi.org)[↩](#fnref498)
    
     |
    | --- |