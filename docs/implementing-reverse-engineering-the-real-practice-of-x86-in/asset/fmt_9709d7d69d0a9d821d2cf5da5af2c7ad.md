
![](images/cover.jpg)
![image](images/cover.jpg)

# Implementing Reverse Engineering

![](images/line.jpg)

## The Real Practice of x86 Internals, Code Calling Conventions, Ransomware Decryption, Application Cracking, Assembly Language, and Proven Cybersecurity Open Source Tools

![](images/line.jpg)

## Jitender Narula

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

**FIRST EDITION 2022**

**Copyright © BPB Publications, India**

**ISBN: 978-93-91030-377**

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![](images/logo1.jpg)

[www.bpbonline.com](http://www.bpbonline.com/)

## Dedicated to
*My parents*
*Always seen God in them*

## About the Author
**Jitender Narula** is an experienced Cyber Security Specialist currently associated with International Institute of Cyber Security (**[www.iicybersecurity.com](http://www.iicybersecurity.com)**) having over 18 years of industry experience. He has many years of cyber security experience with governments and corporate world. In India, he has worked with government entities like Delhi Police, ICAI (Institute of Chartered Accountants of India), Delhi University and other private organizations.
He has worked on the projects of AT&T, Citrix, Google, Conexant, IPolicy Networks (Tech Mahindra now), Narus (a wholly owned subsidiary of The Boeing Company) and HFCL. Apart from this, he has conducted training programs for various corporate and government officials in India and Mexico.
He has published articles, research information and interviews in the area of cyber security for Information Security Newspaper (**[www.securitynewspaper.com](http://www.securitynewspaper.com)**), Noticias de seguridad informática (**noticiasseguridad.com**), Cibertip - Noticias de Hacking (**[www.cibertip.com](http://www.cibertip.com)**), Exploit One (**[www.exploitone.com](http://www.exploitone.com)**), iicybersecurity blog (**[https://www.iicybersecurity.com/blog-eng.html](https://www.iicybersecurity.com/blog-eng.html)**) and also contributed to the Vishvas News, which is part of Dainik Jagran (Indian language daily newspaper).

## About the Reviewer
**Sanil Nadkarni** is CISO /CRO/DPO in an MNC. He has worked for organizations and clients such as Microsoft, Symantec, MphasiS, Capita, SLK and has supported International Banks and Financial Organizations.
He is an international speaker, author and trainer. Sanil has published over 100 articles online and also for various magazines.
His certifications include CFE, CISSP, CISA, CISM, Security+, ISO 27001 LA, ISO 22301 LA, A+, N+, MCP, MCSA, CCNA, SCSA, ISO 10012 (GDPR), RHCE, CEH,CBCP, ISO 31000 Risk and Microsoft Azure Architect.
Sanil has received honors and awards such as CISO TOP 100 Award, Dynamic CISO Award, Top 100 CIO award and many more.
He has published a book on Fundamentals on Information Security which is available on Amazon.

## Acknowledgement
First and foremost, praises and thanks to my Dad, Mom and God for showering blessings throughout my work to complete the book successfully.
I would like to express my deep and sincere gratitude to Atul Narula, my colleague at International Institute of Cyber Security, Mexico for helping with the review process of this book. I am extremely grateful for what he has offered me. I would also like to thank him for his friendship, empathy and great sense of humor.
I am extremely grateful to my parents (Ramesh Narula and Mohini Narula) for their love, prayers, care and sacrifices for educating and preparing me for my future. I am very much thankful to my wife and son for their love, understanding, prayers and continuing support to complete this book. Also, I would like to express my thanks to Dr. Shilpi Sahi and Om Narula for their support and motivation throughout this process of writing. Once again, I would like to thank my family for putting up with me while I was spending many nights writing—I could have never completed this book without their support.
Finally, I would like to thanks BPB Publications for giving me the opportunity to write my first book for them.

## Preface
Reverse Engineering (RE) is an art of understanding any program code when no source code is available. This book provides step-by-step explanation of the essential concepts and practical examples to understand and implement Reverse Engineering. It will enable the readers to understand the application code flow to identify vulnerabilities and bugs in the application.
This book is for the readers who want to start learning Reverse Engineering from basics in a step-by-step manner. The book is divided into three parts:
1. Exploring Reverse Engineering
2. Reverse Engineering Applications
3. Real World Examples with Solutions
The first part Exploring Reverse Engineering starts with the basic concepts of Computing System and Data Building Blocks of the Computing System. This part also enlists open-source tools required for RE applications and the programming instructions of RE. The second part Reverse Engineering Applications walks us through the different applications/programs to understand the implementation of RE. This part covers various practicals, which give the users a hands-on experience. All the applications/programs mentioned in this part are aligned in a systematic manner; from reverse engineering of basic C/C++ programs to complex C/C++ programs. In the third part Real World Examples and Solutions of this book, RE of well-known Windows application along with different exercises are demonstrated in a step-by-step manner. Over the 18 chapters in this book, you will learn the following:

### PART 1: Exploring Reverse Engineering
In this part, the readers will understand the impact of RE on industry, building blocks of x86 computing system and the role of each in the overall functioning of x86 system.
**[Chapter 1](#c01.xhtml)** talks about the impact of RE on IT industry and how it originated as an area.
**[Chapter 2](#c02.xhtml)** talks about the building blocks of a computing system and the role of each building block in the overall functioning of the system. This chapter is important in order to understand the core concept behind the working of x86 computing systems.
**[Chapter 3](#c03.xhtml)** focuses on the open-source tools used in RE and how these tools are used for debugging and analysis. These tools will be used in all illustrations shown in this book.
**[Chapter 4](#c04.xhtml)** explains about the major assembly instructions used and also about how different instructions are segmented in various sections for easy understanding along with examples.
**[Chapter 5](#c05.xhtml)** helps us understand the different calling conventions along with practical illustrations.

### PART 2: Reverse Engineering Applications
This is where the strategic way of learning RE applications/programs is explained with different illustrations. Every case is the outcome of research explained in a very simplified and step-by-step manner.
