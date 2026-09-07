![](images/cover.jpg)

MATLAB® is a trademark of The MathWorks, Inc. and is used with permission. The MathWorks does not warrant the accuracy of the text or exercises in this book. This book’s use or discussion of MATLAB® software or related products does not constitute endorsement or sponsorship by The MathWorks of a particular pedagogical approach or particular use of the MATLAB® software.

First edition published 2020

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2020 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

International Standard Book Number-13: 978-1-138-54352-2 (Hardback)

International Standard Book Number-13: 978-1-351-00666-8 (eBook)

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact mpkbookspermissions@tandf.co.uk

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks, and are used only for identification and explanation without intent to infringe.

# [Authors](#toc.xhtml#fm1a)

**Dr. Shrirang Ambaji Kulkarni** is a prolific learner, author, and faculty member with 18-plus years of experience in the field of Computer Science and Engineering. He is currently working as an Associate Professor at the National Institute of Engineering in the Department of Computer Science and Engineering, Mysore, India.

**Dr. Varadraj P. Gurupur** is an distinguished faculty member and researcher in the field of Health Informatics. He has authored many research articles in reputed journals. He is currently working as an Associate Professor at the University of Central Florida in the Department of Health Informatics, Florida, USA.

**Dr. Steven Lawrence Fernandes** is a high-profile researcher in the field of Image Processing. He is currently working as Post-Doctoral Fellow at the University of Central Florida in the Department of Computer Science and Engineering, Florida, USA.

# [Chapter **1**](#toc.xhtml#ch-01)

# [Introduction](#toc.xhtml#ch-01)

In the last three decades, technology has changed the way we live our lives. This happens to be a universally accepted truth. In this book, we attempt to illustrate the use of a new technology that has changed the world of communication, computing and computing education. Interestingly, the name of this technology coincides with that of a famous dessert named Raspberry Pie. Raspberry *Pi* is a single board computer developed in the United Kingdom. Incidentally, the organization that started this is known as the Raspberry Pi Foundation. This was first launched in the year 2012.

By the year 2015, Raspberry Pi had gained wide-scale popularity. One of the key features of this technology was its size and adaptability. In some strange ways, Raspberry Pi was the panacea the world of technology was dreaming of. To build on this idea of a tiny computer, one must consider the fact that more than a decade ago you would have computer programs running on desktops wired to electromechanical systems that would use them. The advent of the Raspberry Pi enables the community of technology developers to innovate handheld devices than can encompass the power of regular computers. Our intention in writing this book is twofold: a) we want to provide a basic understanding of how a Raspberry Pi can be used for simple applications, and b) we want to provide fundamental information on how a Raspberry Pi can be used to advance innovations in machine learning and image recognition.

While providing fundamental information on Raspberry Pi, we will help students comprehend the necessary information required to develop applications and devices. These devices and applications can have a wide range of applications such as networking devices, using devices and applications related to privacy and security, creating medical applications and developing sensors. The authors believe that this range of applications will help the scientific community adapt Raspberry Pi for use in some of their projects and thereby enhance its usability.

Additionally, the authors are attempting to present information on how Raspberry Pi can successfully implement machine learning and image processing. The information presented in this book will help the community of researchers synthesize new scientific methods, algorithms, devices and other forms of technology into a wide range of application domains. The authors envision Raspberry Pi advancing the development of science and technology across various user domains such as medicine, security, communication, and the military. Last but not least, it is our attempt to have this book used as study material for courses teaching students about using Raspberry Pi. It is our understanding that Raspberry Pi can be used extensively in healthcare information systems.

In this book, the authors present a transformative interdisciplinary perspective of Raspberry Pi usage. This idea is based on the philosophy of transformative transdisciplinary perspective presented by the founding fathers of Society for Design and Process Science \[[1](#chapter01.xhtml#ref1_1)\]. This philosophy is based on bringing about a positive transformative change to one domain by making changes or improvements in another. This philosophy is applicable to Raspberry Pi because rapid improvements in Raspberry Pi and its applicability will facilitate and create a rostrum for improvements in all the domains in which this device can be used. One example will be the implementation of machine learning algorithms that can aid image processing. In this book, the authors have dwelled on some of the fundamental programming concepts that are needed for image analysis and machine learning. This is another very important reason this book is needed for its targeted audience.

While we engage ourselves in recognizing the importance of the Raspberry Pi, it is also important to note that Raspberry Pi has competitors or alternatives available in the market. A brief summary of these alternatives is listed in [Table 1.1](#chapter01.xhtml#table1_1).

Table  1.1  A List of Raspberry Pi Alternatives Available as of 2019 \[[2](#chapter01.xhtml#ref1_2)\]

| Raspberry Pi Model || Brief Description |
| --- | --- |
| Odroid XU4 || Compatible with a few prominent versions of Linux operating system and comparable to Raspberry Pi 3 |
| --- | --- |
| UDOO Bolt || Works well with desktop applications |
| ASUS Tinker Board || Works with versions of Linux operating system and Chrome |
| LattePanda Alpha || Unlike many alternatives; supports windows 10 and uses an Intel Core M3 processor |
| Banana Pi M64 || Works with a wider range of operating systems |
| RockPro 64 || A powerful 64 bit CPU |
| BeagleBone Black || Developed by Texas Instruments in collaboration with Newark element 14 |
| Libre Computer AML-S905X-CC Le Potato || Suitable for image processing |
| MinnowBoard Turbot || Its small size and affordability make it a viable competitor for the Raspberry Pi. |
| Odroid H2 || Suitable for game streaming and video applications |
| Arduino || Useful for applications involving robotics |

This book is divided into five chapters. The first chapter provides some introductory material on Raspberry Pi and a brief introduction to the authors. The second chapter explains different types of Raspberry Pis and provides the reader with important information on the slots and other necessary elements of the Raspberry Pi. An explanation on these elements or parts is essential from a usability perspective. It also provides instructions on installing the operating system Raspbian \[[3](#chapter01.xhtml#ref1_3)\] on Raspberry Pi. Additionally, it provides some information on peripheral devices and the ways in which they can be used with the Raspberry Pi.

The importance of using Raspbian dwells in the idea that installing and using this operating system is a necessary step in the synthesis of systems and applications. Raspbian is a freely available operating system for the Raspberry Pi. It is important to note that Raspbian is not affiliated with the Raspberry Pi Foundation. Raspbian is a community-funded development effort as was the case in the early days of the Linux operating system. Interestingly, Raspbian is a Linux distribution built with the Linux operating system. Raspbian was first released in the year 2012.

The third chapter explains the elements of Python programming \[[4](#chapter01.xhtml#ref1_4)\] that are essential with respect to using Raspberry Pi. Here the authors dwell on esoteric programming details that are needed for successful Raspberry Pi application. These details include matrix operations, Cholesky decomposition and modifying data frames. It is important to note that data manipulation and analysis have become critical in today’s world of artificial intelligence and big data. Raspberry Pi provides the much-needed hardware for manipulating big data. The authors understand this need and provide some basic information on the development of systems for data manipulation using the Raspberry Pi. [Chapter 3](#chapter03.xhtml) contains necessary program snippets with illustrations of expected outcomes. One of the critical objectives of this illustration is to help the reader with machine learning application development using the Raspberry Pi. These applications can be applied to smart phones, wearable devices, farming devices and other IoT applications.

[Chapter 4](#chapter04.xhtml) dwells on details with respect to programming machine-learning systems. The authors explore required approaches for splitting data sets into test and training sets essential for machine learning algorithm implementations. We use health informatics examples to explain how machine learning can be implemented using the Raspberry Pi. This chapter provides the reader with necessary information on synthesizing expert systems, developing knowledge banks and performing knowledge curation.

Machine learning implementation is explained with several examples, programing snippets and figures associated with the outcome of their implementation. Implementation of machine learning is important in many domains including health informatics, where machine learning has been extensively used to predict healthcare outcomes and diagnoses and for genetics and bioinformatics. Machine learning and big data analytics have been helpful in predicting the early onset of diseases. Additionally, the possibility of the development of a disease or disorder later in life can be predicted with the application of bioinformatics based on the information derived from human genomes. The integration of Raspberry Pi into portable biomedical devices enhances the possibility of computation.

Finally, [chapter 5](#chapter05.xhtml) deals with image processing using the Raspberry Pi. Here the authors provide many program snippets and associated outputs, thereby delineating details that are necessary for the reader to use the device to perform image-processing algorithms. In recent times, it has been observed that image processing and machine learning associate well. Thus, the authors provide information on machine learning and image processing in this book. With the advent of the Raspberry Pi, the size of the computational device for image processing is reduced while at the same time it improved the available computability. This aids the development and synthesis of real-time sensors in need of advanced processing.

The authors have extensive experience in research and development of science and technology. Dr. Shrirang Kulkarni has a Doctoral degree in Computer Engineering; he started his career in research by exploring and developing technologies for ad hoc wireless networks. He further identified other areas of science and technology in which his fundamental approaches could be used, thereby expanding on the transdisciplinary and transformative nature of his research. He now works on research projects that involve using the Raspberry Pi for developing machine learning techniques for healthcare. Additionally, Dr. Kulkarni has written several books that have attained national attention in India. It is also important to mention that he has been involved in teaching engineering students for the last 18 years.

Dr. Steven Fernandes is a well-accomplished researcher in the area of Internet of Things (IoT), machine learning, image processing and the design and development of intelligent systems. He has published more than 40 articles in reputable journals. Additionally, he has served as a guest editor for several special issues. Dr. Fernandes has been involved in teaching engineering students in India and the United States for about a decade.

Finally, Dr. Varadraj Prabhu Gurupur is currently serving as an Associate Professor with the Department of Health Management and Informatics at the University of Central Florida. Dr. Gurupur has more than 100 publications, including a book, chapters, journal articles, abstracts, conference papers and published reviews. He has worked on several projects funded by agencies such as the National Science Foundation and the National Institutes of Health. He has been actively involved with the Institute of Electrical and Electronic Engineers for over a decade. Additionally, he has been honored with several national, regional and state level awards in the United States for his accomplishments in the area of Health Informatics. Dr. Gurupur received his Master’s in Computer Science in the year 2005 and Doctor of Philosophy in Computer engineering in 2010 from the University of Alabama at Birmingham.

## REFERENCES

\[1\]    Society for Design and Process Science Official Website \[Online\]. Available: [www.sdpsnet.org/sdps/](http://www.sdpsnet.org). Accessed: 09/24/2019.

\[2\]    Electromaker \[Online\]. Available: [www.electromaker.io/blog/article/10-best-raspberry-pi-alternatives](http://www.electromaker.io). Accessed: 09/24/2019.

\[3\]    Raspbian \[Online\]. Available: [www.raspbian.org/RaspbianImages](http://www.raspbian.org)

\[4\]    S.A. Kulkarni, *Problem Solving and Python Programming*, YesDee Publishers, Chennai, India, 2017.

# [Chapter **2**](#toc.xhtml#ch-02)

# [Raspberry Pi Unraveled](#toc.xhtml#ch-02)

## 2.0 Raspberry Pi

Raspberry Pi is an Advanced RISC Machines (ARM)-processed, credit-card sized computer. It was developed by the Raspberry Pi Foundation in the United Kingdom (UK).

ARM stands for Advanced RISC Machines. The company specializes in building processors based on Reduced Instruction Set Computers (RISC) architecture. RISC machines emphasize the use of registers and smaller instructions and thus can achieve higher speeds with the ability to execute millions of instructions per second. The smaller size of ARM processors’ low power consumption makes them most suitable for miniaturized devices like the Raspberry Pi.

The latest model (Raspberry Pi 3 B+) uses 1.2 GHz ARM Cortex – A53 Broadcom BCM 2837 Processor. The significant difference is the quad-core ARM Cortex A53 (ARMv8) cluster, which works at 1.2 GHz, making it 50% faster than the Raspberry Pi 2 model.

## 2.1 TimeLine of Raspberry Pi Models

A brief timeline of various base Raspberry Pi models released to date follows.

 
| Year: 2012Model: Raspberry Pi Model BSize: 85.60 mm × 56.5 mmCPU: ARM1176JZF-S; 32 bitGPU: Broadcom VideoCore IV @ 250 MHzSpeed: 700Mhz Single-Core CPURAM: 512MB RAM || Year: 2013Model: Raspberry Pi Model ASize: 85.60 mm × 56.5 mmCPU: ARM1176JZF-S 32 bitGPU: Broadcom VideoCore IV @ 250 MHzSpeed: 700Mhz Single-Core CPURAM: 256 MB RAM |
| --- | --- |

 
| Year: 2014Model: Raspberry Pi Compute modelSize: 67.6 mm × 30 mmCPU: ARM1176JZF-S 32 bitGPU: Broadcom VideoCore IV @ 250 MHzSpeed: 700Mhz Single-Core CPURAM: 512 MB RAM || Year: 2015Model: Raspberry Pi ZeroSize: 65 mm × 30 mm × 5 mmCPU: ARM1176JZF-S 32 bitGPU: Broadcom VideoCore IV @ 250 MHzSpeed: 1 GHz Single-Core CPURAM: 512 MB RAM |
| --- | --- |

 
| **Latest Raspberry Pi Model** |
| --- |
| Year: 2018Model: **Raspberry Pi 3 Model B+**Size: 85mm x 56mm x 17mm.CPU: Cortex-A53 (ARMv8) 64-bitGPU: Dual Core VideoCore IV GPU@400 MHzSpeed: 1.4GHz 64-bit quad-core ARM Cortex A53 CPURAM: 1GB RAM |

## 2.2 Components of a Raspberry Pi Model 3

A brief component layout of Raspberry Pi Model 3 is illustrated in [Figure 2.1](#chapter02.xhtml#fig2_1). The model we considered in this book is Raspberry Pi 3 V 1.2

![Figure  2.1  Raspberry Pi Model 3.](images/fig2_1.jpg)

Figure  2.1  Raspberry Pi Model 3.

### 2.2.1 General Purpose Input-Output Pins (GPIO) Pins

There are 40 general purpose input-output pins (GPIO) pins on the Raspberry Pi board as illustrated in [Figure 2.2](#chapter02.xhtml#fig2_2). These pins help the Raspberry Pi connect to the real world. With the help of these pins, the Raspberry Pi can help you control physical devices like motors, extension boards and LEDs.

![Figure  2.2  GPIO Pins.](images/fig2_2.jpg)

Figure  2.2  GPIO Pins.

The pins on the left side of the board are numbered using odd numbers from 1 to 39; the right side uses even numbers from 2 to 40. The GPIO pins are numbered in two nomenclatures. One is the GPIO numbering and the other is the physical numbering. The GPIO numbering refers to the Broadcom numbering on System on Chip, whereas the physical numbering refers to the 40 pins specified on the Raspberry Pi Board.

### 2.2.2 Broadcom BCM283 7 64bit ARMv7 Quad Core Processor

At the center of the Raspberry Pi is an ARMv7 Quad Core Processor with 1GB of RAM, which works at 1.2 GHz. The miniature size of the processor is noticeable. The Quad-Core nature of the processor at the rate of 1.2 Ghz makes it 50% faster than the Raspberry Pi 2. Coupled with GPU, the Raspberry Pi can work wonders in number-crunching situations.

### 2.2.3 Micro USB Slot

The Micro USB power connector supplies power to the Raspberry Pi board. This is illustrated in [Figure 2.3](#chapter02.xhtml#fig2_3).

![Figure  2.3  Micro USB Slot.](images/fig2_3.jpg)

Figure  2.3  Micro USB Slot.

The Raspberry Pi board is powered by 5v DC supply. To turn the Raspberry Pi on/off you need to turn this power supply on/off.

### 2.2.4 High Definition Multimedia Interface (HDMI) Port

The Raspberry Pi provides a high definition multimedia interface (HDMI) output port. This is illustrated in [Figure 2.4](#chapter02.xhtml#fig2_4).

![Figure  2.4  HDMI Port.](images/fig2_4.jpg)

Figure  2.4  HDMI Port.

The HDMI port allows the Raspberry Pi to connect to a monitor. For monitors that support only o video graphics array (VGA) you need an HDMI to VGA connector cable. With the support from GPU, the Raspberry Pi can support 1080p video and that could be truly outputted from an HDMI port.

### 2.2.5 Audio Jack

For listening to sound, the Raspberry Pi provides a 3.5 mm audio jack. This is illustrated in [Figure 2.5](#chapter02.xhtml#fig2_5). You can plug earphones into this audio jack.

![Figure  2.5  Audio Jack/Port.](images/fig2_5.jpg)

Figure  2.5  Audio Jack/Port.

### 2.2.6 Universal Serial Bus (USB) Ports

The Raspberry Pi 3 model provides four universal serial bus (USB) ports. This is illustrated in [Figure 2.6](#chapter02.xhtml#fig2_6).

![Figure  2.6  USB Ports.](images/fig2_6.jpg)

Figure  2.6  USB Ports.

The USB ports allow for the connection of a mouse and a keyboard. However, connecting devices indirectly to the Raspberry Pi through a USB hub minimizes the power drawn.

### 2.2.7 Ethernet Socket

The Raspberry Pi provides an Ethernet socket. This is illustrated in [Figure 2.7](#chapter02.xhtml#fig2_7).

![Figure  2.7  Ethernet Port.](images/fig2_7.jpg)

Figure  2.7  Ethernet Port.

The Ethernet cable, with its RJ-45 connector, allows a router to be connected to the Raspberry Pi. Thus, a router with dynamic host configuration protocol will allow your Raspberry Pi to connect to the Internet. However, Raspberry Pi also supports built-in Wi-Fi and Bluetooth connectivity.

### 2.2.8 Micro-SD Card Slot

Raspberry Pi provides an onboard micro-SD card slot. This is illustrated in [Figure 2.8](#chapter02.xhtml#fig2_8).

![Figure  2.8  SD Card Port.](images/fig2_8.jpg)

Figure  2.8  SD Card Port.

For the Raspberry to boot through its operating system, it needs the operating system to reside on the SD card. This is essential, as Raspberry Pi does not have a hard-drive like in a laptop or desktop.

## 2.3 Raspbian Operating System

The soul of a computer system is its operating system. The preferred operating system for Raspberry Pi is Raspbian. Raspbian is based on Debian, which is a Linux-based operating system highly customized for Raspberry Pi hardware. The popular versions of Raspberry Pi are Wheezy, which is based on Debian 7, Jessie, which is based on Debian 8, and Stretch, based on Debian 9. The operating system considered in this book is Jessie.

The Jessie version of Raspberry Pi focused on making the desktop more comfortable for end users. The LibreOffice suite was included in the Jessie version. This helps users write documents, prepare PowerPoints and work with Excel spreadsheets and databases. All of these are compatible with Microsoft Windows. The Jessie version comes bundled with BlueJ, a Java development environment for beginners, and Scratch, a programming language for beginners. The graphical user interface provided for Raspbian is the Lightweight Desktop Environment or LXDE.

### 2.3.1 Operating Systems Available for Raspberry Pi

Let us discuss some of the operating systems available for Raspberry Pi, shown in [Table 2.1](#chapter02.xhtml#table2_1).

Table  2.1  Operating System supporting Raspberry Pi

 
| **Raspbian** |
| --- |
| 

*   Raspberry Pi Foundation recommended OS
*   A very user friendly desktop environment
*   Comes with a lot of pre-installed software

 |
| **LibreELEC** |
| 

*   Designed to support Kodi-powered media center
*   Can be paired with the KODI Remote App
*   Can build a small home theater

 |
| **Windows 10 IoT Core** |
| 

*   Provides integration with Visual Studio
*   Supports both ARM and X86 architectures
*   Supports development of connected devices

 |
| **RISC OS** |
| 

*   Performance is key and is emphasized by the designers
*   Comes with an archived file, which is unto 4MB, a very small size
*   Provides better drag-and-drop options

 |

## 2.4 To Connect Raspberry Pi 3 to Monitor

*   **Step 1:** Connect a monitor to Raspberry Pi via HDMI and a keyboard and mouse via a USB.
*   **Step 2:** Install an Operating System. 
    *   **Step 2.1:** Use new out-of-box software (NOOBs) available at ([https://www.raspberrypi.org/downloads/](https://www.raspberrypi.org)).
    *   **Step 2.2:** Extract the NOOBs downloaded.
    *   **Step 2.3:** The downloaded NOOBS file must be copied into a formatted SD card. (SDHC card >2GB and ≤ = 32 GB follows FAT 32). NOOBs will install Raspbian on the SD card at the initial boot.
*   **Step 3: raspi-config** 
    *   **$ sudo raspi-config**

You will see the following screen ([Figure 2.9](#chapter02.xhtml#fig2_9)). Choose the interfacing options.

![Figure  2.9  Choosing Interfacing Options.](images/fig2_9.jpg)

Figure  2.9  Choosing Interfacing Options.

Press Enter to move into an option and arrow keys to move up/down. Tab to select the options like <finish>.

*   **Step 3.1:** Change the user password. The default login is **pi** and password is **raspberry**.
*   **Step 3.2:** Enable boot to Desktop.
*   **Step 3.3:** Internationalization options 
    *   **Step 3.3.1:** Change-locale: select a language.
    *   **Step 3.3.2:** Change time zone.
    *   **Step 3.3.3**: Change keyboard layout. QWERTY is the default.

Post successful configuration; the Raspberry Pi environment will look as shown in [Figure 2.10](#chapter02.xhtml#fig2_10).

![Figure  2.10  Raspberry Pi Desktop.](images/fig2_10.jpg)

Figure  2.10  Raspberry Pi Desktop.

## 2.5 Applications of IoT

According to Gartner\[[1](#chapter02.xhtml#ref2_1)\], by 2020 there will be around 2.6 billion connected devices. This clearly indicates a potential host of applications.

1.  **Smart Home:** The Smart Home is the most potent application for IoT. You can control air conditioners, refrigerators, microwave ovens, lighting and entertainment systems through IoT-based control systems.
2.  **Wearable devices:** Monitoring human health parameters like heartbeat, blood pressure and other vitals is possible through wearable IoT devices. The constraint on these devices is that they must be small and energy efficient.
3.  **Farming:** Farmers are at times challenged to monitor crops and livestock at remote farm areas. Now this is possible through IoT. Also, detecting diseases of crops and water usage can be controlled through IoT devices.
4.  **Industrial IoT:** It has been now realized that IoT has a host of applications across different industries like manufacturing, oil and gas and energy. IoT helps industries in the automation and optimization of resources.

## Exercises

1.  Show how to make a headless Raspberry Pi installation.
2.  Explain why Secure Shell (SSH) is disabled from Raspberry Pi 3 onwards.
3.  What type of file system is preferred on the SD card used for uploading the Raspberry Pi operating system?
4.  Discuss the various operating systems available for Raspberry Pi along with their advantages and disadvantages.
5.  Write a note on the most recent industrial applications of Raspberry Pi as Industrial IoT.

## Reference

\[1\]    Gartner, [https://www.gartner.com/en/newsroom/press-releases/2019-08-29-gartner-says-5-8-billion-enterprise-and-automotive-io](https://www.gartner.com), 2019.

# [Chapter **3**](#toc.xhtml#ch-03)

# [Python and Its Libraries for Machine Learning](#toc.xhtml#ch-03)

## 3.1 Introduction

Python is one of the most popular languages for Machine Learning. One of the dominant reasons for the popularity of Python is its rich support of libraries (see [Table 3.1](#chapter03.xhtml#table3_1)).

Table  3.1  Libraries for Python

| Python Library || Usage |
| --- | --- |
| NumPy || Mathematical applications |
| --- | --- |
| SciPy || Scientifics Computing |
| Pandas || Data Analysis |
| Matplotib || Data Visualization |
| Scikit-learn || Machine Learning |

## 3.2 Python

### 3.2.1 What Is Python?

*   Python was proposed by Guido van Rossum in the late 1980s.
*   It is a simple but powerful high-level programming language.
*   It supports procedural and object-oriented concepts.
*   Python code is interpreted rather than compiled.

## 3.3 A Typical Python Program

![Figure  3.1  A Typical Python Program.](images/fig3_1.jpg)

Figure  3.1  A Typical Python Program.

![Figure  3.2  Output of a Typical Python Program.](images/fig3_2.jpg)

Figure  3.2  Output of a Typical Python Program.

Thus, we now see a typical Python program, which computes the square root of every element of a given matrix. A Python program typically begins with an import statement. The import statement includes Python modules that provide a programmer with various library functions. In the mentioned program we have used library functions like map(), split() and sqrt(). Python follows strict rules for code indentation. The inner for loop is indented a few more spaces than the outer for loop is.

## 3.4 Python Keywords

Keywords are reserved words and cannot be used as names for identifiers or programmer-defined variables. The keywords are listed in the **keyword** module and can be printed as seen in [Figure 3.3](#chapter03.xhtml#fig3_3).

![Figure  3.3  Python Code to Display Keyword List.](images/fig3_3.jpg)

Figure  3.3  Python Code to Display Keyword List.

## 3.5 Python Variable

*   A python variable must begin with a letter (a – z, A – B) or underscore (\_) followed by letters, numbers or underscore.
*   Python variables are case sensitive.

| **mean** || ![](images/inline3_1.jpg) || valid variable |
| --- | --- | --- |
| **1\_mean** || ![](images/inline3_2.jpg) || invalid variable |
| **mean\_new@** || ![](images/inline3_3.jpg) || invalid variable |
| **\_new\_mean** || ![](images/inline3_4.jpg) || valid variable |

## 3.6 Comments in Python

Python provides two types of comments. This is as shown as comments.py in [Figure 3.4](#chapter03.xhtml#fig3_4).

![Figure  3.4  Python Program to Demonstrate Comments.](images/fig3_4.jpg)

Figure  3.4  Python Program to Demonstrate Comments.

![Figure  3.5  Output of comments.py.](images/fig3_5.jpg)

Figure  3.5  Output of comments.py.

In [Figure 3.5](#chapter03.xhtml#fig3_5), we observe that comments are ignored by the Python interpreter.

## 3.7 Python Data Types

Variables in Python are typeless. Python supports dynamic typing, and the variable type is decided at runtime Python data types can be categorized as shown in [Table 3.2](#chapter03.xhtml#table3_2).

Table  3.2  Python data types

| Python Data Types  |
| --- |
| Numeric || intlongfloatcomplexbool |
| --- | --- |
| Sequence || strlisttuple |
| Sets || setfrozen set |
| Mapping || dict |

To determine the data type of the variable use the **type()** function in Python. **Python program: datatype.py** as illustrated in [Figure 3.6](#chapter03.xhtml#fig3_6).

![Figure  3.6  Python Program to Demonstrate Different Data Types.](images/fig3_6.jpg)

Figure  3.6  Python Program to Demonstrate Different Data Types.

![Figure  3.7  Output of datatype.py.](images/fig3_7.jpg)

Figure  3.7  Output of datatype.py.

## 3.8 Python Operator Precedence

The Python operator and precedence are given in [Table 3.3](#chapter03.xhtml#fig3_3).

Table  3.3  Python Operator Precedence and Associativity

| **Operator**  || **Highest**![](images/inline3_5.jpg)Lowest || **Associativity** |
| --- | --- | --- |
| \*\* || Right-to-left |
| ~ + − || Left-to-right |
| \* / % // || Left-to-right |
| \+ − || Left-to-right |
| \>> << || Left-to-right |
| & || Left-to-right |
| ^ | || Left-to-right |
| <= < > >= || Left-to-right |
| <> == != || Left-to-right |
| \= %= /= //= −= += \*= \*\*= || Right-to-left |
| is is not || Left-to-right |
| In not in || Left-to-right |
| not or and || Left-to-right |

### 3.8.1 Evaluate the Following Python Expression

*   2 + 3 \* 4//5 − 17
*   **Step 1:** (3\*4) = 12
*   **Step 2:** 12//5 = 2 (Integer division)
*   **Step 3**: 2 + 2 = 4
*   **Step 4:** 4−17 = −13
*   **Ans = −13**

### 3.8.2 Evaluate the Following Python Expression

*   **2\*\*3+4//7−6\*9**
*   **Step 1:** (2\*\*3) = 8
*   **Step 2:** 4//7 = 0 (Integer division)
*   **Step 3**: 6 \* 9 = 54
*   **Step 4:** 8 + 0 = 8
*   **Step 5:** 8−54 = −46
*   **Ans = −** 46

## 3.9 Conditional Constructs in Python

Conditional constructs are used in Python to take action based on certain conditions. The conditions can involve comparison expressions or arithmetic expressions, and their outcome is either True or False.

Structure of IF-ELSE Statement in Python

if condition1:

      statement 1

elif condition2:

      statement 2

else:

      statement 3

**Example:** Consider the following description

0–1: baby

1–2: toddler

2–12: child

13–17: teenager (14 = early teens)

18 +: adult

**Python program**:if\_elif\_stmt.py is illustrated in [Figure 3.8](#chapter03.xhtml#fig3_8).

![Figure  3.8  Python Program to Demonstrate if elif Statements.](images/fig3_8.jpg)

Figure  3.8  Python Program to Demonstrate if elif Statements.

![Figure  3.9  Output of Python Program if\_elif\_stmt.py.](images/fig3_9.jpg)

Figure  3.9  Output of Python Program if\_elif\_stmt.py.

## 3.10 Ternary Operator in Python

The syntax for Python’s ternary operator is as follows.

**a if test else b**

![Figure  3.10  Python Program to Demonstrate Use of Ternary Operator.](images/fig3_10.jpg)

Figure  3.10  Python Program to Demonstrate Use of Ternary Operator.

![Figure  3.11  Output of Python Program to Demonstrate Ternary Operator.](images/fig3_11.jpg)

Figure  3.11  Output of Python Program to Demonstrate Ternary Operator.

## 3.11 Looping Constructs in Python

At times when certain statements are to be executed repeatedly, loops are useful. Thus, the statements are executed continuously until some conditions are met.

### 3.11.1 While Loop

A while loop is an entry-controlled loop. Thus, the loop is entered only if the entry condition is satisfied. There may be a counter that keeps count of the number of time the loop is executed and finally when a certain threshold is reached, the loop terminates. The syntax is as follows

while expression:

     statement

The while loop iterates as long as the condition is True. The Statement can be a single statement or block of statements.

Example: Python program while\_loop.py as seen in [Figure 3.12](#chapter03.xhtml#fig3_12).

![Figure  3.12  Python Program to Demonstrate while loop.](images/fig3_12.jpg)

Figure  3.12  Python Program to Demonstrate while loop.

![Figure  3.13  Output of while\_loop.py.](images/fig3_13.jpg)

Figure  3.13  Output of while\_loop.py.

### 3.11.2 For Loop

The for loop in Python iterates over a given range of values. The syntax of the for loop is as follows

for item in sequence:

     print item

Example: Python program – for\_loop.py as illustrated in [Figure 3.14](#chapter03.xhtml#fig3_14).

![Figure  3.14  Python Program to Demonstrate for\_loop.py.](images/fig3_14.jpg)

Figure  3.14  Python Program to Demonstrate for\_loop.py.

![Figure  3.15  Output of Python Program for\_loop.py.](images/fig3_15.jpg)

Figure  3.15  Output of Python Program for\_loop.py.

To perform a similar iteration using the for loop in the reverse manner, consider the program for\_loop\_reverse.py.

![Figure  3.16  Python Program to Demonstrate for loop in the Reverse Manner.](images/fig3_16.jpg)

Figure  3.16  Python Program to Demonstrate for loop in the Reverse Manner.

![Figure  3.17  Output of Python Program for\_loop\_reverse.py.](images/fig3_17.jpg)

Figure  3.17  Output of Python Program for\_loop\_reverse.py.

### 3.11.3 Else in Combination with While and For Loop

The else condition with while loop activates when the while entry condition become False. For example, consider the Python program illustrated in [Figure 3.18](#chapter03.xhtml#fig3_18).

![Figure  3.18  Python Program to Demonstrate else in Combination with while loop.](images/fig3_18.jpg)

Figure  3.18  Python Program to Demonstrate else in Combination with while loop.

![Figure  3.19  Output of Python Program for else with while loop.](images/fig3_19.jpg)

Figure  3.19  Output of Python Program for else with while loop.

The else statement is clubbed with the for loop in the case in which the for loop has been exhausted by iterating with all elements in the sequence. For example, consider the Python program illustrated in [Figure 3.20](#chapter03.xhtml#fig3_20).

![Figure  3.20  Python Program to Demonstrate else in Combination with for loop.](images/fig3_20.jpg)

Figure  3.20  Python Program to Demonstrate else in Combination with for loop.

![Figure  3.21  Output of Python Program for Else with for loop.](images/fig3_21.jpg)

Figure  3.21  Output of Python Program for Else with for loop.

## 3.12 Strings in Python

Strings are contiguous set of characters enclosed by double quotes in Python.

Example: “Hello”

     “Raju”

The concatenation of two strings is performed with the “+” operator. Example a = “Good” and b = “Morning”. Then a+ b will give Good Morning.

The operator “in” returns True if the given character is in the string. The operator “not in” returns True if the given character is not in the given string. Example G in Good returns True and G not in Morning returns True.

### 3.12.1 String Built-in Methods

Following are some of the commonly used string methods

1.  **len(string)** returns the length of the string.  
    Example: len(“morning”)  
    Output: 7
2.  **lower()** converts uppercase letters into lowercase.  
    Example: str= “HELLO”  
           print str.lower()  
    Output: hello
3.  **find()** finds whether the string is there in a string or in a substring of the string.  
    find(sub, start = 0, end = len(string))  
    Example: str= “morning”  
          str.find("r",0,len(str))  
    Output: 2
4.  **replace()** replaces the old string with a new string and returns the updated string.  
    replace(old, new, max\_occurrence)  
    Example: str="Good Morning"  
            str.replace("Morning", "Evening",1)  
    Output: 'Good Evening'
5.  **split()** method provides a way to split a string into small substrings separated by a delimiter. The output is a list.  
    Example: str="Winning is everything"  
            str.split()  
    Output: \['Winning', 'is', 'everything'\]

## 3.13 List in Python

A list is comma-delimited values enclosed in square brackets. Example lst = \['a', 'b', 'c', 'd'\]. The Python program list\_op.py illustrates in [Figure 3.22](#chapter03.xhtml#fig3_22) an example of list.

![Figure  3.22  Python Program to Demonstrate an Example of list.](images/fig3_22.jpg)

Figure  3.22  Python Program to Demonstrate an Example of list.

![Figure  3.23  Output of Python Program list\_op.py.](images/fig3_23.jpg)

Figure  3.23  Output of Python Program list\_op.py.

### 3.13.1 List Methods

*   **len(list)** gives the length of the list.  
    lst=\['a', 'b', 'c', 'd'\]  
    len(lst)  
    Output: 4
*   **list.reverse()** reverses the elements of the list.  
    lst=\['a', 'b', 'c', 'd'\]  
    lst.reverse()  
    lst=\['d', 'c', 'b', 'a'\]
*   **list.sort()** sorts the elements of the list in ascending order.  
    lst=\['d', 'c', 'b', 'a'\]  
    lst.sort()  
    lst= \['a', 'b', 'c', 'd'\]

## 3.14 Tuples in Python

Tuples are sequences similar to lists except that they are immutable (i.e., they cannot be changed and they use parentheses). Example tup=('a', 'b', 'c', 'd')

*   **len(tuple)** gives the length of the tuple.  
    tup=('a', 'b', 'c', 'd')  
    len(tup)  
    4
*   **max(tuple)** returns the max value in a tuple.  
    tup=(1,2,3,4)  
    max(tup)  
    4
*   **min(tuple)** returns the min value of the tuple.  
    tup=(1,2,3,4)  
    min(tup)  
    1

## 3.15 Dictionaries in Python

Dictionaries are key value pairs separated by “:” and enclosed in curly braces. Example dict ={'a': 'apple', 'b': 'ball', 'c': 'cat', 'd': 'dog', 'e': 'elephant'}

### 3.15.1 Methods on Dictionaries

*   **dict.items()** returns dictionary as key/value pairs.  
    print dict.items()  
    \[('a', 'apple'), ('c', 'cat'), ('b', 'ball'), ('e', 'elephant'), ('d', 'dog')\]
*   **dict.keys()** returns the dictionary’s keys only.  
    print dict.keys()  
    \['a', 'c', 'b', 'e', 'd'\]
*   **dict.values()** returns the dictionary’s values only.  
    print dict.values()  
    \['apple', 'cat', 'ball', 'elephant', 'dog'\]

## 3.16 Python Functions

A user-defined function in Python is defined with the def keyword. A function can accept parameters and return a value.

![Figure  3.24  Python Program to Demonstrate a Function That Can Accept and Return a Value.](images/fig3_24.jpg)

Figure  3.24  Python Program to Demonstrate a Function That Can Accept and Return a Value.

![Figure  3.25  Output of Python Function Program.](images/fig3_25.jpg)

Figure  3.25  Output of Python Function Program.

## 3.17 NumPy Introduction

NumPy is an abbreviation that stands for numerical python. It is a fundamental python package useful for performing data analysis and supporting machine-learning algorithms. As datasets for machine learning algorithms come from a variety of sources and follow different formats, it becomes quite challenging to process the same. These datasets may include images, text or sound clips. These data sources for processing are visualized as numerical arrays. Thus, NumPy as a python package supports huge capabilities for array processing. NumPy also provides the following functionalities:

*   ndarray, which supports high-dimensional arrays with superior performance capabilities.
*   Mathematical functions to support operations on entire arrays as a single unit.

It provides support for linear algebra operations and allows Python code to interact with C and C++.

How to use NumPy

The convention is to use NumPy with the command as illustrated in [Figure 3.26](#chapter03.xhtml#fig3_26).

![Figure  3.26  Usage of NumPy module.](images/fig3_26.jpg)

Figure  3.26  Usage of NumPy module.

If you see the above screen, the execution of **import numpy as np** resulted in the interpreter prompt ⋙; this means that the NumPy package is installed correctly.

## 3.18 NumPy Operations

### 3.18.1 Creating an Array from a Python List

The first step is to build a Python list. Let us consider lst=\[10, 20, 30, 40, 50\]. To convert the list to an array we have to use the function np.array() and pass the argument to the list (i.e., lst). This is visualized in [Figure 3.27](#chapter03.xhtml#fig3_27).

![Figure  3.27  Python Command Code to Create an Array from Python List.](images/fig3_27.jpg)

Figure  3.27  Python Command Code to Create an Array from Python List.

NumPy requires that all array elements be of the same type. If the elements do not match, the lower type will be converted or promoted to a higher type.

![Figure  3.28  Python Command Code to Show Type Conversion When Creating an Array from Python List.](images/fig3_28.jpg)

Figure  3.28  Python Command Code to Show Type Conversion When Creating an Array from Python List.

Some of the basic datatypes supported by NumPy are illustrated in [Table 3.4](#chapter03.xhtml#table3_4).

Table  3.4  NumPy data types

| DataType || Description |
| --- | --- |
| bool\_ || Boolean True or False |
| --- | --- |
| int32 || Supports Integers on 32 bit machines |
| int64 || Supports Integers on 64 bit machines |
| uint32 || Supports unsigned integer (0 to 4,294,967,295) |
| Uint64 || Supports unsigned integer(0 to 18,446,744,073,709,551,615) |
| float32 || Single precision floating point value |
| float64 || Double precision floating point value |
| intc || Equivalent to int32 or int64 |
| floatc || Equivalent to float64 |
| complex64 || Supports complex number where both real and imaginary parts are 32-bit floats. |
| Complex128 || Supports complex number where both real and imaginary parts are 64-bit floats. |

Suppose we want to create a list of integers to float64: we can use the keyword dtype= 'float64'. This is executed as illustrated in [Figure 3.29](#chapter03.xhtml#fig3_29).

![Figure  3.29  Python Command Code to Convert a List of Integers to an Array of Double Precision Floating Point Values of Type float64.](images/fig3_29.jpg)

Figure  3.29  Python Command Code to Convert a List of Integers to an Array of Double Precision Floating Point Values of Type float64.

Here we observe that a list of integers is converted into an array of double-precision floating-point values of type float64.

### 3.18.2 Creating Arrays with NumPy

To create a single dimensional array of 20 elements filled with 0s, we use the following command

 *n**p*.*z**e**r**o**s*(20,*d**t**y**p**e*^′*i**n**t*64^′) <img src="images/inline-math3\_6.jpg" alt=""/> . This is visualized in [Figure 3.30](#chapter03.xhtml#fig3_30).

![Figure  3.30  Python Command Code to Create a Single Dimensional Array of 20 Elements Filled with 0s.](images/fig3_30.jpg)

Figure  3.30  Python Command Code to Create a Single Dimensional Array of 20 Elements Filled with 0s.

Now let us create a single dimensional array with values filled from 0 to 9. We can accomplish this with the command np.arange(0,10,1). Here 0 is the starting element, 10 is the max range and 1 is the step function. This is illustrated in [Figure 3.31](#chapter03.xhtml#fig3_31).

![Figure  3.31  Python Command Code to Create a Single Dimensional Array with Values Filled from 0 to 9.](images/fig3_31.jpg)

Figure  3.31  Python Command Code to Create a Single Dimensional Array with Values Filled from 0 to 9.

We have not specified dtype, and it generates values of integer types.

To generate floating-point values, we may as well specify dtype = 'float64'. Thus, we get the following

![Figure  3.32  Python Command Code to Create a Single Dimensional Array with Floating Point Values Filled from 0 to 9.](images/fig3_32.jpg)

Figure  3.32  Python Command Code to Create a Single Dimensional Array with Floating Point Values Filled from 0 to 9.

To generate random floating-point values between 0 and 4 and for a 2-Dimensional matrix of the range 4 x 4, we can use the following command.

  
*n**p*.*r**a**n**d**o**m*.*r**a**n**d**o**m*((4,4)) \* 4 + 0  
<graphic xlink:href="unmath3\_1.tif"/>

The random.random() command returns floating-point values between 0 to 1. However, as we have defined that we want values between 0 and 4, our lower bound remains the same (i.e., 0). To get the upper bound we need to multiply by 4, the value required in our case. Also, the lower bound can be specified by adding the same, which can be safely ignored in our case as the lower bound is 0. Thus, the command to generate random floating-point values between 0 and 4 and for a 2-dimensional matrix of the range 4 x 4 can be rewritten as

  
*n**p*.*r**a**n**d**o**m*.*r**a**n**d**o**m*((4,4)) \* 4  
<graphic xlink:href="unmath3\_2.tif"/>

Both of these commands accomplish our requirement. This is illustrated in [Figure 3.33](#chapter03.xhtml#fig3_33).

![Figure  3.33  Python Command Code to Create 2-dimensional 4 x 4 Matrix of Random Floating Point Values.](images/fig3_33.jpg)

Figure  3.33  Python Command Code to Create 2-dimensional 4 x 4 Matrix of Random Floating Point Values.

Suppose we want to generate a 2-dimensional array of random values in the range 2 to 4. We can use the following command

  
*n**p*.*r**a**n**d**o**m*.*r**a**n**d**o**m*((4,4)) \* 4 + 2  
<graphic xlink:href="unmath3\_3.tif"/>

![Figure  3.34  Python Command Code to Create 2-dimensional 4 x 4 Matrix of Random Floating Point Values between 0 and 4.](images/fig3_34.jpg)

Figure  3.34  Python Command Code to Create 2-dimensional 4 x 4 Matrix of Random Floating Point Values between 0 and 4.

Here we observe that adding 2 provides us with the lower bound.

Now suppose we want to create a 2-dimensional array of dimensions 3 x 3 filled with 1s of Integer64 type; we need to use the following command

  
*n**p*.*o**n**e**s*((3,3), *d**t**y**p**e*\= ^′*i**n**t*64^′)  
<graphic xlink:href="unmath3\_4.tif"/>

This is illustrated as in [Figure 3.35](#chapter03.xhtml#fig3_35).

![Figure  3.35  Python Command Code to Create a 2-dimensional Array of Dimensions 3 x 3 Filled with 1s of Integer64 type.](images/fig3_35.jpg)

Figure  3.35  Python Command Code to Create a 2-dimensional Array of Dimensions 3 x 3 Filled with 1s of Integer64 type.

### 3.18.3 Basic NumPy Operations

*   Array Attributes: In most data-processing applications, the developers need to be aware of the array attributes. The attributes and their descriptions are illustrated in [Table 3.5](#chapter03.xhtml#fig3_5).

Table  3.5  NumPy Array Attributes

| Attribute || Description |
| --- | --- |
| ndim || Specifies the number of dimensions |
| --- | --- |
| shape || Specifies the size of each dimension |
| size || Specifies the total size of the array |
| dtype || Specifies the datatype of the array elements |

Consider a 2-dimensional array with dimensions 3 x 3 as follows

  
$$\\begin{matrix} 1 & 2 & 3 \\\\ 4 & 5 & 6 \\\\ 7 & 8 & 9 \\\\ \\end{matrix}$$  
<graphic xlink:href="unmath3\_5.tif"/>

Now using NumPy we create the above array and print its attributes.

![Figure  3.36  Python Command Code to Create a 2-Dimensional Array of Dimensions 3 X 3 and Print Its Attributes.](images/fig3_36.jpg)

Figure  3.36  Python Command Code to Create a 2-Dimensional Array of Dimensions 3 X 3 and Print Its Attributes.

The method reshape() is used to build a matrix of 3 x 3 with elements 1 to 9. The method reshape() will be discussed more elaborately in the following sections.

*   **Array indexing**

The array index in Python starts from 0. Thus if we have to get the 5^(th) element of the array we need to say array\_name\[4\]. This is illustrated in the [Figure 3.37](#chapter03.xhtml#fig3_37).

![Figure  3.37  Python Command Code to Access Array Elements.](images/fig3_37.jpg)

Figure  3.37  Python Command Code to Access Array Elements.

To access a multi-dimensional array we need to have a comma separated tuple of indices to access the array. Example array\_name\[2\]\[1\] will return the value of the element at the third row and second column. This is illustrated with the example in [Figure 3.38](#chapter03.xhtml#fig3_38).

![Figure  3.38  Python Command Code to Access Multi-dimensional Array Elements.](images/fig3_38.jpg)

Figure  3.38  Python Command Code to Access Multi-dimensional Array Elements.

*   **Working with subarrays.**

To get a subarray from an array we use the slicing operations similar to Python lists.

The syntax is array\_name\[intial\_value, final\_value, step\_value\]

**1-Dimensional array**

Let us consider a 1-Dimensional array with values 0, 1, 2, 3, 4, 5, 6.

| Index || 0 || 1 || 2 || 3 || 4 || 5 || 6 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Values || 0 || 1 || 2 || 3 || 4 || 5 || 6 |

To get the first three values, we need to execute the statement a\[:3\]. This says values that are at index 0, index 1 and index 2. To get the last three values we need to execute the Python statement a\[4:\]. This says all values that are after index 4. This is illustrated as in [Figure 3.39](#chapter03.xhtml#fig3_39).

![Figure  3.39  Python Command Code to Get Subarray from Array.](images/fig3_39.jpg)

Figure  3.39  Python Command Code to Get Subarray from Array.

In [Figure 3.39](#chapter03.xhtml#fig3_39) we see that to get the middle values of an array a we splice it with the following range a\[2:5\] (i.e., all value greater than index 2 means starting from value 3, and up to index 5 means up to value 4).

**2-dimensional array**

In case of 2-dimensional arrays, the multiple splices are separated by commas.

For example, if we have a 2-D array of dimensions 3 x 3 as follows

  
$$\\begin{matrix} 1 \\\\ 4 \\\\ 7 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 2 \\\\ 5 \\\\ 8 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 3 \\\\ 6 \\\\ 9 \\\\ \\end{matrix}$$  
<graphic xlink:href="unmath3\_6.tif"/>

Now using NumPy, we want to get the values of the single column  $\\begin{matrix} 2 \\\\ 5 \\\\ 8 \\\\ \\end{matrix}\\;$ <img src="images/inline-math3\_7.jpg" alt=""/>  we need to execute the following statements

  
*a*\[:3,1:2\]  
<graphic xlink:href="unmath3\_7.tif"/>

This is illustrated in [Figure 3.40](#chapter03.xhtml#fig3_40).

![Figure  3.40  Python Command Code to Get Subarray from 2-D Array.](images/fig3_40.jpg)

Figure  3.40  Python Command Code to Get Subarray from 2-D Array.

Thus, we fetch 3 rows from array **a** for columns that start at index 1 and are less than index 2 (i.e., the entire column at index 1).

**Note:** The subarrays created by NumPy are treated as views. Thus, if the subarray elements are modified, they are reflected back in the original array. This is illustrated in [Figure 3.41](#chapter03.xhtml#fig3_41).

![Figure  3.41  Python Command Code to Get Subarray from 2-D Array.](images/fig3_41.jpg)

Figure  3.41  Python Command Code to Get Subarray from 2-D Array.

Here we modify 2 row 3rd element and assign it with a value 10. This is reflected back in the array **a** when we print out the same.

*   **Copying an array**

We can make another copy of an array with the copy() function. This is illustrated in [Figure 3.42](#chapter03.xhtml#fig3_42).

![Figure  3.42  Python Command Code to Copy an Array.](images/fig3_42.jpg)

Figure  3.42  Python Command Code to Copy an Array.

*   **Array reshaping**

At times, we need to change the shape of an array (i.e., from a row-vector to a column-vector). This is illustrated in the example shown in [Figure 3.43](#chapter03.xhtml#fig3_43).

![Figure  3.43  Python Command Code to Change the Shape of an Array.](images/fig3_43.jpg)

Figure  3.43  Python Command Code to Change the Shape of an Array.

*   **Array Concatenation**

It is possible to club two arrays into a single one through the concatenation process. The first routine we consider is np.concatenate(). This is illustrated in [Figure 3.44](#chapter03.xhtml#fig3_44).

Axis in NumPy are with respect to multi-dimensional arrays. For example, a 2-dimensional array has two axes. If axis=0, that means a straight axis running downwards across the rows. Alternatively, if axis=1, that means a straight axis running horizontally across the columns.

Let us consider the concatenation of two 1-dimensional arrays. This is illustrated in [Figure 3.44](#chapter03.xhtml#fig3_44).

![Figure  3.44  Python Command Code to Concatenate Two 1-dimensional Arrays.](images/fig3_44.jpg)

Figure  3.44  Python Command Code to Concatenate Two 1-dimensional Arrays.

The concatenation operation of multi-dimensional arrays is based on the axis. If the axis=0 it means the concatenation will be done vertically, and if the axis=1, it means the concatenation will be done horizontally. This is illustrated with the examples in [Figures 3.45](#chapter03.xhtml#fig3_45) and [3.46](#chapter03.xhtml#fig3_46).

![Figure  3.45  Python Command Code to Concatenate Multi-dimensional Array Vertically.](images/fig3_45.jpg)

Figure  3.45  Python Command Code to Concatenate Multi-dimensional Array Vertically.

![Figure  3.46  Python Command Code to Concatenate Multi-dimensional Array Horizontally.](images/fig3_46.jpg)

Figure  3.46  Python Command Code to Concatenate Multi-dimensional Array Horizontally.

If the arrays are of different dimensions and you want to concatenate them, then you can use vstack() vertical stack or hstack() horizontal stack routines. This is illustrated in the example below.

![Figure  3.47  Python Command Code to Concatenate Arrays of Different Dimensions.](images/fig3_47.jpg)

Figure  3.47  Python Command Code to Concatenate Arrays of Different Dimensions.

*   **Splitting Arrays**

Sometimes we need to split an array into different arrays. This is accomplished with the split() function. If the split of the array is going to be into arrays of unequal sizes, then you need to give the split points. This is illustrated in [Figure 3.48](#chapter03.xhtml#fig3_48).

![Figure  3.48  Python Command Code to Split Arrays of Unequal Sizes.](images/fig3_48.jpg)

Figure  3.48  Python Command Code to Split Arrays of Unequal Sizes.

 

  
*a*1, *a*2, *a*3 = *n**p*.*s**p**l**i**t*(*a*,\[3,7\])  
<graphic xlink:href="unmath3\_8.tif"/>

Here the split for the first array is 0 to 2, for the second array 3 to 6 and for the third array it is 7 to 9. This we have accomplished with the split points\[3,7\].

However, there is another way of splitting an array to unequal sizes. This is accomplished with the routine array\_split() and is illustrated in [Figure 3.49](#chapter03.xhtml#fig3_49).

![Figure  3.49  Python Command Code to Split Arrays of Unequal Sizes with Array\_Split().](images/fig3_49.jpg)

Figure  3.49  Python Command Code to Split Arrays of Unequal Sizes with Array\_Split().

## 3.19 Pandas Introduction

Pandas is one of the essential Python libraries you need to study as a productive data scientist. In brief, Pandas builds upon the capabilities of NumPy arrays into labeled rows and columns.

Pandas can be visualized as the sum of NumPy array capabilities with the power of spreadsheets and relational databases.

A small subset of Pandas applications includes

*   Converting a NumPy array, Python list or dictionary into a Pandas dataframe object.
*   Opening a locally stored csv file.
*   Helping to open a remote csv file through a URL.

### 3.19.1 Exploring Pandas

To check whether Pandas has been installed properly, you can type the command illustrated in [Figure 3.50](#chapter03.xhtml#fig3_50).

![Figure  3.50  Python Command Code to Check Whether Pandas Is Installed Properly.](images/fig3_50.jpg)

Figure  3.50  Python Command Code to Check Whether Pandas Is Installed Properly.

If you get the interpreter prompt without any errors, that means Pandas has been installed properly.

The two preliminary data structures of Pandas you need to study are Series and DataFrame.

![Figure  3.51  Python Command Code to Demonstrate Use of Pandas Series Object.](images/fig3_51.jpg)

Figure  3.51  Python Command Code to Demonstrate Use of Pandas Series Object.

In Pandas official documentation, a Series is described as a homogeneously typed structure. Let us consider the example illustrated in [Figure 3.52](#chapter03.xhtml#fig3_52).

![Figure  3.52  Python Command Code to Demonstrate Use of Pandas Series Object for Upcast.](images/fig3_52.jpg)

Figure  3.52  Python Command Code to Demonstrate Use of Pandas Series Object for Upcast.

Here we observe that the Series object allowed us to insert a string 'a'. Thus, the presence of int and string has resulted in an upcast of the type object. If the array contains integers and floats, the array type will be upcasted to float. This is visualized with the help of the example as illustrated in [Figure 3.53](#chapter03.xhtml#fig3_53).

![Figure  3.53  Python Command Code to Demonstrate Use of Pandas Series Object for Upcast from Integers to Floats.](images/fig3_53.jpg)

Figure  3.53  Python Command Code to Demonstrate Use of Pandas Series Object for Upcast from Integers to Floats.

Here we observe that the series object contained integers and floats and has been upcasted to floats.

**Note:** Although the Series object will permit non-homogeneous elements, certain Pandas functions may not work correctly.

Since for the above series object we did not specify an index, it by default took an index from 0 to N-1 where N is the number of elements in the Series object.

Subarray can be obtained by splicing the Series object in Pandas like NumPy. This is illustrated in [Figure 3.54](#chapter03.xhtml#fig3_54).

![Figure  3.54  Python Command Code to Generate Sub-array Using Splicing of Series Object.](images/fig3_54.jpg)

Figure  3.54  Python Command Code to Generate Sub-array Using Splicing of Series Object.

In the case of a series object in Pandas, we can access index using strings and not restrict ourselves to integers like NumPy. This is illustrated in the example in [Figure 3.55](#chapter03.xhtml#fig3_55).

![Figure  3.55  Python Command Code to Acess Series Object Index Using Strings.](images/fig3_55.jpg)

Figure  3.55  Python Command Code to Acess Series Object Index Using Strings.

The Pandas Series object could be visualized as a Python dictionary. Here the corresponding keys and their values are mapped together. This is illustrated in [Figure 3.56](#chapter03.xhtml#fig3_56).

![Figure  3.56  Python Command Code to Implement Series Object as Dictionary.](images/fig3_56.jpg)

Figure  3.56  Python Command Code to Implement Series Object as Dictionary.

Here, the indices are the keys of the dictionary in the sorted form.

### 3.19.2 DataFrame Object

A DataFrame is a tabular structure like a spreadsheet in which each column represents different values. It can also be visualized as a collection of 1-dimensional Series objects.

Thus a DataFrame can be thought of as a page in a spreadsheet. This is illustrated in [Table 3.4](#chapter03.xhtml#table3_4).

Let us try to depict a state, its capital and the capital’s population.

Table  3.4  Table of a state, capital and population

| State || Capital || Population |
| --- | --- | --- |
| Alabama || Montgomery || 198,232 |
| --- | --- | --- |
| Florida || Tallahassee || 193,078 |
| Louisiana || Baton Rouge || 226,505 |
| Massachusetts || Boston || 687,584 |
| Virginia || Richmond || 230,254 |

![Figure  3.57  Python Command Code to Demonstrate Dataframe as a Tabular Structure.](images/fig3_57.jpg)

Figure  3.57  Python Command Code to Demonstrate Dataframe as a Tabular Structure.

As we have not specified the row indexes, it has taken the index values from 0 to 4. We can access the DataFrame object by specifying the column name or by getting the data from a specific row.

Example: dataf\['state'\]

To get specific row data we can use the following

dataf.ix\[1\]

Here ix stands for indexing field. This is illustrated in [Figure 3.58](#chapter03.xhtml#fig3_58).

![Figure  3.58  Python Command Code to Access Dataframe Object.](images/fig3_58.jpg)

Figure  3.58  Python Command Code to Access Dataframe Object.

The datatype of the columns of a DataFrame object are of the same type. We can get the data types of all columns by specifying

*   dataframeobject.dtypes
*   We can also get the datatype of a specific column by writing
*   dataframeobject\['column\_name'\].dtype

![Figure  3.59  Python Command Code to Access Dataframe Object.](images/fig3_59.jpg)

Figure  3.59  Python Command Code to Access Dataframe Object.

As a Pandas DataFrame object contains many records, it is sometime useful to check a limited number of sample records from the top or the bottom. Pandas provides functions like head() and tail() to accomplish the same.

This is illustrated with the in [Figure 3.60](#chapter03.xhtml#fig3_60).

![Figure  3.60  Python Command Code to Create Dataframe Object Dict\_Info.](images/fig3_60.jpg)

Figure  3.60  Python Command Code to Create Dataframe Object Dict\_Info.

To view the available indexes and column names, we can use Pandas capabilities like

*   **dataobjectname.index**
*   **dataobjectname.columns**

This is illustrated in [Figure 3.61](#chapter03.xhtml#fig3_61).

![Figure  3.61  Python Command Code to View Available Indexes and Column Names in a Dataframe Object dict\_info.](images/fig3_61.jpg)

Figure  3.61  Python Command Code to View Available Indexes and Column Names in a Dataframe Object dict\_info.

#### 3.19.2.1 DataFrame Column Functions

There are times when you would want to extract some column-level functions; under such circumstances, you could make use of Column Functions

*   mean(): the mean of the specified column values
*   unique(): the unique values of a column
*   sum(): sum of the values of the specified column
*   max(): highest value of the specified column
*   min(): lowest value of the specified column
*   idxmin(): the index of the lowest value
*   idxmax(): the index of the highest value
*   count(): the number of non-null values in a specified column
*   describe(): the statistical summary
*   This is illustrated in [Figure 3.62](#chapter03.xhtml#fig3_62).

![Figure  3.62  Python Command Code to View Available Indexes and Column Names in a Dataframe Object dict\_info.](images/fig3_62.jpg)

Figure  3.62  Python Command Code to View Available Indexes and Column Names in a Dataframe Object dict\_info.

#### 3.19.2.2 Pandas Functionalities for DataFrame Information

Pandas provides functionalities where we can extract information about the DataFrame like shape, columns and the index used.

The syntax is

*   dataframeobject.shape: the number of rows and columns in the DataFrame object
*   dataframeobject.columns: the columns specified in the DataFrame object
*   Dataframeobject.index: details of the row index including the range
*   This is illustrated in [Figure 3.63](#chapter03.xhtml#fig3_63).

![Figure  3.63  Python Command Code to Demonstrate Column Level Functions.](images/fig3_63.jpg)

Figure  3.63  Python Command Code to Demonstrate Column Level Functions.

#### 3.19.2.3 Pandas Functions to Remove Rows and Columns in a DataFrame

Pandas provides the drop function to remove the rows and columns in a DataFrame object.

First, consider an example in which you want to drop specific rows from a DataFrame. As we have not specified row names, the values would be from 0 to N-1. Thus, if we want to drop row0 and row1, we execute the following statement:

*   dataframeobject.drop(\[0,1\])
*   If we had to drop a column, we would specify
*   dataframeobject.drop('column\_name',axis=1)
*   This is illustrated in [Figure 3.64](#chapter03.xhtml#fig3_64).

![Figure  3.64  Python Command Code to Demonstrate Dataframe Information.](images/fig3_64.jpg)

Figure  3.64  Python Command Code to Demonstrate Dataframe Information.

#### 3.19.2.4 Modifying a DataFrame

To modify a DataFrame by adding a column, we can execute the following statement

  
*d**a**t**a**f**r**a**m**e**o**b**j**e**c**t*\[^′*c**o**l**u**m**n*\_*n**a**m**e*^′\] = 0  
<graphic xlink:href="unmath3\_9.tif"/>

This will create a specified column and initialize its values to 0.

If you want to change the column names of a DataFrame object, you can execute the following statement.

  
Dataframeobject\[′column\_name1^′, ′column\_name2′,^′column\_name3′, ′column\_name4′\]  
<graphic xlink:href="unmath3\_10.tif"/>

Thus, the DataFrameObjects columns will be changed as specified by column\_name1, column\_name2, column\_name3 and column\_name4.

This is illustrated in [Figure 3.65](#chapter03.xhtml#fig3_65) and [Figure 3.66](#chapter03.xhtml#fig3_66).

![Figure  3.65  Python Command Code to Modify DataFrame Information by Adding a Column.](images/fig3_65.jpg)

Figure  3.65  Python Command Code to Modify DataFrame Information by Adding a Column.

![Figure  3.66  Python Command Code to Modify DataFrame Information by Changing Column Names.](images/fig3_66.jpg)

Figure  3.66  Python Command Code to Modify DataFrame Information by Changing Column Names.

## 3.20 Pandas Functionalities to Read Data from Files

Let us first consider how to read data from a CSV file. CSV stands for comma separated values. It stores data that is delimited by commas; CSV files can be imported or exported to popular spreadsheets like Excel and officeorg.

Let us consider a simple CSV file called as **state.csv**

*   Step 1: In Python Shell say File -> NewFile.
*   Step 2: Paste your CSV content.
*   Step 3: Save the file (i.e., give **filename.csv** and choose type as **all files)**.
*   **Note:** Our created file is in the same folder in which Python can access files.

![Figure  3.67  Snapshot of state.csv File.](images/fig3_67.jpg)

Figure  3.67  Snapshot of state.csv File.

To access this file using Pandas:

![Figure  3.68  Python Command Code to Access the csv File state.csv.](images/fig3_68.jpg)

Figure  3.68  Python Command Code to Access the csv File state.csv.

## 3.21 Pandas Missing Data (Data Cleaning)

Sometimes we come across missing values in a Pandas Series or DataFrame object. Pandas represents the missing value by NaN. It is useful to convert this NaN to the value 0 sometimes.

As an example, we have created a 1-dimensional array with a Series object as seen in [Figure 3.69](#chapter03.xhtml#fig3_69).

![Figure  3.69  Python Command Code to Create a 1-dimensional Array with a Series Object.](images/fig3_69.jpg)

Figure  3.69  Python Command Code to Create a 1-dimensional Array with a Series Object.

The first step would be to check the presence of missing data we can use the **isnull()** function. The usage of isnull() is illustrated in [Figure 3.70](#chapter03.xhtml#fig3_70).

![Figure  3.70  Python Command Code to Check the Presence of Missing Data in the Series Object.](images/fig3_70.jpg)

Figure  3.70  Python Command Code to Check the Presence of Missing Data in the Series Object.

Here we observe that row index 2 and row index 5 indicate True; that means there are values of NaN.

To remove these type of NaN values, we could use dropna() function, which drops rows or columns that have NaN values.

![Figure  3.71  Python Command Code to Remove NaN Values from a DataFrame Object.](images/fig3_71.jpg)

Figure  3.71  Python Command Code to Remove NaN Values from a DataFrame Object.

Here, column index 3 and column index 2 have NaN. Thus, when we delete column-wise, setting axis=1; only 2 columns are retained (i.e., column index 0 and column index 1, which do not have any NaN values).

The disadvantage of this method is that useful information associated with rows/columns having NaN values is lost.

To overcome this, we can replace NaN values with a value 0 or we can forward fill or backward fill the data.

![Figure  3.72  Python Command Code to Replace NaN Values with a Value 0.](images/fig3_72.jpg)

Figure  3.72  Python Command Code to Replace NaN Values with a Value 0.

The forward filling and backward filling of data are illustrated in [Figure 3.73](#chapter03.xhtml#fig3_73).

![Figure  3.73  Python Command Code for Forward Filling and Backward Filling of Data.](images/fig3_73.jpg)

Figure  3.73  Python Command Code for Forward Filling and Backward Filling of Data.

## 3.22 SciPy Introduction

SciPy is Python’s library that helps scientists and engineers perform scientific computing. It provides supports toward the development of such applications as

*   Optimization
*   Integration
*   Image Processing
*   Statistics

### 3.22.1 Exploring SciPy

The first step is to check whether SciPy is installed properly.

![Figure  3.74  Python Command Code to Check Whether SciPy Is Installed Properly.](images/fig3_74.jpg)

Figure  3.74  Python Command Code to Check Whether SciPy Is Installed Properly.

If we get the command interpreter prompt without any error, which means SciPy has been installed properly.

### 3.22.2 Sparse Matrix

If a matrix contains a large number of zeros, we can call such matrix a sparse matrix.

Example

  
$$\\begin{matrix} 1 \\\\ 0 \\\\ 0 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 0 \\\\ 0 \\\\ 0 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 0 \\\\ 3 \\\\ 0 \\\\ \\end{matrix}$$  
<graphic xlink:href="unmath3\_11.tif"/>

In the above matrix there are 2 non-zero values, and the other 7 values are zero.

The formula to compute sparsity is

  
*N**u**m**b**e**r* *o**f* *z**e**r**o* *e**l**e**m**e**n**t**s*​/​*T**o**t**a**l* *n**u**m**b**e**r* *o**f* *e**l**e**m**e**n**t**s*  
<graphic xlink:href="unmath3\_12.tif"/>

Thus, the percentage of sparsity is (7/9)\*100 = 77.78%, and the percentage of density is (2/9)\*100 = 22.22%.

Common Sparse Row is often used to represent a sparse matrix in machine-learning applications. Here, three 1-dimensional matrices are used for non-zero values. This is illustrated with the example as illustrated in [Figure 3.75](#chapter03.xhtml#fig3_75) and [Figure 3.76](#chapter03.xhtml#fig3_76).

![Figure  3.75  Python Program to Demonstrate a Sparse Matrix.](images/fig3_75.jpg)

Figure  3.75  Python Program to Demonstrate a Sparse Matrix.

![Figure  3.76  Output of Python Program to Demonstrate a Sparse Matrix.](images/fig3_76.jpg)

Figure  3.76  Output of Python Program to Demonstrate a Sparse Matrix.

The following example demonstrates how to compute sparsity and density for a given matrix. This is illustrated in [Figure 3.77](#chapter03.xhtml#fig3_77) and [Figure 3.78](#chapter03.xhtml#fig3_78).

![Figure  3.77  Python Program to Compute Sparsity and Density for a Given Matrix.](images/fig3_77.jpg)

Figure  3.77  Python Program to Compute Sparsity and Density for a Given Matrix.

![Figure  3.78  Output of Python Program to Compute Sparsity and Density for a Given Matrix.](images/fig3_78.jpg)

Figure  3.78  Output of Python Program to Compute Sparsity and Density for a Given Matrix.

### 3.22.3 Inverse of a Matrix

The module that supports Linear Algebra in SciPy is linalg. Let us compute the inverse of matrix using SciPy

  
$$\\begin{matrix} 1 \\\\ 0 \\\\ 5 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 2 \\\\ 1 \\\\ 6 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 3 \\\\ 5 \\\\ 0 \\\\ \\end{matrix}$$  
<graphic xlink:href="unmath3\_13.tif"/>

The inverse of the above matrix is

 

  
$$\\begin{matrix} {- 6} \\\\ 5 \\\\ {- 1} \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 3.6 \\\\ {- 3} \\\\ 0.8 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 1.4 \\\\ {- 1} \\\\ 0.2 \\\\ \\end{matrix}$$  
<graphic xlink:href="unmath3\_14.tif"/>

![Figure  3.79  Python Program to Compute Inverse of Matrix.](images/fig3_79.jpg)

Figure  3.79  Python Program to Compute Inverse of Matrix.

![Figure  3.80  Output of Python Program to Compute Inverse of Matrix.](images/fig3_80.jpg)

Figure  3.80  Output of Python Program to Compute Inverse of Matrix.

### 3.22.4 Cholesky Decomposition

The **Cholesky decomposition** or **Cholesky factorization** is a decomposition of a Hermitian, positive-definite matrix into the product of a lower triangular matrix and its conjugate transpose.

![Figure  3.81  Python Program to Compute Cholesky Decomposition.](images/fig3_81.jpg)

Figure  3.81  Python Program to Compute Cholesky Decomposition.

![Figure  3.82  Output of Python Program to Compute Cholesky Decomposition.](images/fig3_82.jpg)

Figure  3.82  Output of Python Program to Compute Cholesky Decomposition.

### 3.22.5 Application to Visualize Student Study Hours Using SciPy

Suppose a student studies a fixed number of hours per day. His hours of study may vary. The data is given by a csv file, as illustrated in [Figure 3.83](#chapter03.xhtml#fig3_83).

![Figure  3.83  Snapshot of student.csv File.](images/fig3_83.jpg)

Figure  3.83  Snapshot of student.csv File.

SciPy genfromtxt can be used to read data from a text file; in this case, it is a CSV file. Python’s slice operator is used to split columns into x and y. Then we use Matplotlib functions to plot the study pattern. This is illustrated in [Figure 3.84](#chapter03.xhtml#fig3_84).

![Figure  3.84  Python Matplotlib Code to Plot Student Study Pattern.](images/fig3_84.jpg)

Figure  3.84  Python Matplotlib Code to Plot Student Study Pattern.

The output plot is as follows and is illustrated in [Figure 3.85](#chapter03.xhtml#fig3_85).

![Figure  3.85  Output of Python Matplotlib Code to Plot Student Study Pattern.](images/fig3_85.jpg)

Figure  3.85  Output of Python Matplotlib Code to Plot Student Study Pattern.

The line graph shows the student’s study pattern in terms of hours for 12 days.

## 3.23 Matplotlib Introduction

Matplotlib is a 2-D plotting package available for Python programmers. For data analysts and machine-intelligence algorithm designers, plotting data characterization and outputs in terms of graphs is essential. These things are taken care of by Matplotlib, which is a huge library.

![Figure  3.86  Python Command Code to Test Whether Matplotlib Is Properly Installed.](images/fig3_86.jpg)

Figure  3.86  Python Command Code to Test Whether Matplotlib Is Properly Installed.

If importing Matplotlib and its module pyplot as a plt returns the command interpreter prompt, that means that Matplotlib has been installed properly.

### 3.23.1 Exploring Matplotlib

The basic types of plots in Matplotlib are line plots, scatterplots and histograms. Let us first consider line plots.

Line plots plot lines co-relating x with corresponding y values. The example in [Figure 3.87](#chapter03.xhtml#fig3_87) illustrates a line plot.

![Figure  3.87  Python Matplotlib Code to Plot a Line Plot.](images/fig3_87.jpg)

Figure  3.87  Python Matplotlib Code to Plot a Line Plot.

The method plot() takes x and y coordinates for plotting. The show() method is used to display the plot in a new window. As we do not want the toolbars to be displayed, we are making use of a statement **plt.rcParams\['toolbarv'\] = 'None'.** To change the default rc settings of a Matplotlib, we have a dictionary type variable matplotlib.rcParams, in which all of the default settings are available. Thus in our case we have disabled the toolbar by setting it to none.

![Figure  3.88  Output of Python Matplotlib Code to Plot a Line Plot.](images/fig3_88.jpg)

Figure  3.88  Output of Python Matplotlib Code to Plot a Line Plot.

Our next step would be to give a name to the x-axis and y-axis, give a title to the graph, set the limits to the x-axis and y-axis and change the line color.

![Figure  3.89  Python Matplotlib Code to Plot a Named Line Plot with Axis Labels.](images/fig3_89.jpg)

Figure  3.89  Python Matplotlib Code to Plot a Named Line Plot with Axis Labels.

![Figure  3.90  Output of Python Matplotlib Code to Plot a Named Line Plot with Axis Labels.](images/fig3_90.jpg)

Figure  3.90  Output of Python Matplotlib Code to Plot a Named Line Plot with Axis Labels.

Next, we plot multiline graphs with legends giving information about the plots.

![Figure  3.91  Python Matplotlib Code to Plot Multiline Graphs with Legends.](images/fig3_91.jpg)

Figure  3.91  Python Matplotlib Code to Plot Multiline Graphs with Legends.

The plt.legend() method will help us to position the legend. We can specify label parameter to the legends we describe.

![Figure  3.92  Output of Python Matplotlib Code to Plot Multiline Graphs with Legends.](images/fig3_92.jpg)

Figure  3.92  Output of Python Matplotlib Code to Plot Multiline Graphs with Legends.

Now we apply Matplotlib to draw a scatter plot. This is illustrated in [Figure 3.93](#chapter03.xhtml#fig3_93).

![Figure  3.93  Python Matplotlib Code to Plot Scatter Plot.](images/fig3_93.jpg)

Figure  3.93  Python Matplotlib Code to Plot Scatter Plot.

Here we use the plt.scatter() method, and we use the parameter c to assign the color.

![Figure  3.94  Output of Python Matplotlib Code to Plot Scatter Plot.](images/fig3_94.jpg)

Figure  3.94  Output of Python Matplotlib Code to Plot Scatter Plot.

Now we try to plot a histogram using Matplotlib. This is illustrated in [Figure 3.95](#chapter03.xhtml#fig3_95).

![Figure  3.95  Python Matplotlib Code to Plot a Histogram.](images/fig3_95.jpg)

Figure  3.95  Python Matplotlib Code to Plot a Histogram.

Here we use plt.hist() method. The opacity is set with the alpha parameter, histtype is bar and the edge color is set to black. The output is illustrated in [Figure 3.96](#chapter03.xhtml#fig3_96).

![Figure  3.96  Output of Python Matplotlib Code to Plot a Histogram.](images/fig3_96.jpg)

Figure  3.96  Output of Python Matplotlib Code to Plot a Histogram.

## Exercise

Answer the following briefly

1.  Is Python a compiled or interpreted programming language?
2.  Is there any char datatype in Python?
3.  What is the role of + operator in Python?
4.  Explain the role of else with respect to while and for loop.
5.  Which sorting algorithm does Python’s sort() function follow?
6.  Are tuples in Python mutable?
7.  Can Python list store heterogeneous data?
8.  Can a Python dictionary have multiple keys for a given value?
9.  How do you create an array using NumPy?
10.  Is a Pandas series 1-dimensional or 2-dimensional array?
11.  Can a Pandas DataFrame’s rows and columns be labeled?
12.  What does CSV stand for on a file?
13.  How do you get the number of rows and columns in a CSV file?
14.  What useful functions does the SciPy library provide?
15.  For what purpose are density plots used?
16.  What is a scatter plot used for?
17.  Which Python library you would use to plot graphs?

## Solve the following

1.  Write a Python program that accepts a multiline sentence and gives the frequency of occurrence of the top 10 words. Stop words should not be counted.
2.  Write a Python program to initialize a NumPy array with values 10, 20, 30, 40 and 50 and compute the mean.
3.  Write a Python program to demonstrate the time consumed by operations on a Python List versus similar operations performed on a NumPy array.
4.  Write a Python program using the Pandas library to read the state.csv as given in [Figure 3.97](#chapter03.xhtml#fig3_97) and generate its summary statistics.
    
    ![Figure  3.97  Snapshot of state.csv file.](images/fig3_97.jpg)
    
    Figure  3.97  Snapshot of state.csv file.
    
5.  Write a Python program using the SciPy library to compute the determinant of an array 
    
      
    $$\\begin{matrix} 1 \\\\ 4 \\\\ 7 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 2 \\\\ 5 \\\\ 8 \\\\ \\end{matrix}\\;\\;\\;\\;\\begin{matrix} 3 \\\\ 6 \\\\ 9 \\\\ \\end{matrix}$$  
    <graphic xlink:href="unmath3\_16.tif"/>
    
6.  Write a Python program using Matplotlib and considering a suitable example to plot a 3-dimensional line graph.

# [Chapter **4**](#toc.xhtml#ch-04)

# [Machine Learning](#toc.xhtml#ch-04)

## 4.0 What Is Meant by Machine Learning?

In machine learning, algorithms attempt to learn without explicit instructions and human interventions and only through experiences.

## 4.1 Categories of Machine Learning

Machine learning algorithms are classified as

*   Supervised
*   Unsupervised
*   Reinforcement Learning

### 4.1.1 Supervised Learning

Supervised algorithms learn from labeled data. In supervised learning, there are sets of defined inputs and outputs; through multiple iterations, supervised learning algorithms come up with a function that helps to correctly conclude an output for a given set of inputs that were not part of training data.

### 4.1.2 Unsupervised Learning

Unsupervised algorithms work with unlabeled data. Here the algorithms are provided only with data, and they try to find the interesting patterns in this data. Unsupervised learning tries to find the commonalities in the data; for a new sample, it tries to find the presence or absence of the discovered commonalities.

### 4.1.3 Reinforcement Learning

In reinforcement learning, we have agents that interact with an environment to maximize its rewards. It is like learning with a critic. For correct decisions, the agent is rewarded; for wrong decisions, the agent is penalized. Thus, the goal for an agent would be to maximize rewards and reach the goal state.

The machine learning algorithms of supervised, unsupervised and reinforcement learning are illustrated in [Figure 4.1](#chapter04.xhtml#fig4_1)

![Figure  4.1  Categories of Machine Learning Algorithms.](images/fig4_1.jpg)

Figure  4.1  Categories of Machine Learning Algorithms.

In this book, we discuss the classification of Supervised Machine Learning algorithms.

## 4.2 Classification in Machine Learning

In classification, we try to predict categorical values. The labels for these categorical values come up with a finite set of classes.

Examples:

*   Given an image, predict cat or dog.
*   Given an email, predict spam or real.

In binary classification, we have only two classes for prediction, usually with values 0 and 1.

In multi classification, we have more than two classes for prediction (e.g., cat, dog or deer).

In this chapter, we apply the following algorithms for classification problems

1.  Logistic Regression
2.  Naïve Bayes
3.  Neural Network
4.  Support Vector Machine
5.  Random Forest
6.  K N N
7.  Linear Discriminate Analysis (LDA)

### 4.2.1 Metrics for Classification

The following metrics have been used to evaluate the supervised algorithms as mentioned section 4.2.

#### 4.2.1.1 K-Fold Cross-Validation

Cross-validation is an important technique used to validate the performance of a given model. Cross-validation involves keeping a sample of the dataset for testing and training the model on the remaining part of the dataset.

The value k determines the number of groups into which data can be split. We have set the value of k to 10. Thus, it is called 10-fold cross-validation.

A value of k equaling 10 is the most popular value for validating the accuracy of models.

#### 4.2.1.2 Confusion Matrix

A confusion matrix (sometimes known as an error matrix) allows us to analyze the performance of a machine-learning algorithm in a matrix format. Rows represent the predicted class, while columns represent the actual class.

The confusion matrix layout is as depicted in Figure 4.2

**Figure 4.2** Confusion Matrix Layout. 

|  || Actual Values |
| --- | --- |
| Predicted Values ||  || Positive (Yes) || Negative (No) |
| --- | --- | --- | --- |
| Positive (Yes) || TP || FP |
| Negative (No) || FN || TN |

*   TP stands for True Positive: the prediction is yes, and it is true.
*   TN stands for True Negative: the prediction is no, and it is false.
*   FN stands for False Negative: the prediction is no, and it is true.
*   FP stands for False Positive: the prediction is yes, and it is false.

**Accuracy** determines the correctness of the confusion matrix; it is given in [Equation 4.1](#chapter04.xhtml#math4_1)

  
$$accuracy = \\frac{\\left( {TP + TN} \\right)}{total},$$  
<graphic xlink:href="math4\_1.tif"/>

(4.1)

where the total is the row sum of the Predicted or the column sum of the Actuals.

**Precision** gives the correctness of Prediction when it is Yes and is given in [Equation 4.2](#chapter04.xhtml#math4_2)

  
$$precision = \\frac{\\left( {TP} \\right)}{Predicted\\; Yes},$$  
<graphic xlink:href="math4\_2.tif"/>

(4.2)

where Predicted Yes is the row sum of Predicted Yes values.

**Recall** is the capacity of the model to find data points of interest and is given in [Equation 4.3](#chapter04.xhtml#math4_3)

 

  
$$recall = \\frac{TP}{\\left( {TP + FN} \\right)}.$$  
<graphic xlink:href="math4\_3.tif"/>

(4.3)

## 4.3 Regression

In regression, we try to predict continuous valued output. Machine learning algorithms that predict continuous valued outputs are

*   Linear Regression
*   Multiple Linear Regression
*   Support Vector Machine (applied for both regression and classification)

## 4.4 Scikit-Learn

Scikit-learn is a library for Python Programming language that supports machine learning. It supports machine-learning features like classification, regression and clustering along with APIs to support popular algorithms like

1.  Linear Regression
2.  Logistic Regression
3.  Naive Bayes
4.  Neural Network
5.  Support Vector Machine
6.  Random Forest
7.  K N N
8.  LDA

### 4.4.1 Dataset

We have analyzed the heart disease data set from University of California, Irvine. For our classification tests, we used only 14 attributes, listed in [Table 4.1](#chapter04.xhtml#table4_1).

Table  4.1  Description of heart disease dataset attributes

 
| Sl\_No || Attribute Name || Attribute Name and Description |
| --- | --- | --- |
| 1 || age || Age in years |
| --- | --- | --- |
| 2 || sex || Sex (1 = male; 0 = female) |
| 3 || cp || Chest pain type

*   Value 1: typical angina
*   Value 2: atypical angina
*   Value 3: non-anginal pain
*   Value 4: asymptomatic

 |
| 4 || trestbps || resting blood pressure (in mm Hg on admission to the hospital) |
| 5 || chol || serum cholesterol in mg/dl |
| 6 || fbs || (fasting blood sugar > 120 mg/dl) (1 = true; 0 = false) |
| 7 || restecg || resting electrocardiographic results

*   Value 0: normal
*   Value 1: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV)
*   Value 2: showing probable or definite left ventricular hypertrophy by Estes’ criteria

 |
| 8 || thalach || maximum heart rate achieved |
| 9 || exang || exercise induced angina (1 = yes; 0 = no) |
| 10 || oldpeak || ST depression induced by exercise relative to rest |
| 11 || slope || the slope of the peak exercise ST segment

*   Value 1: upsloping
*   Value 2: flat
*   Value 3: downsloping

 |
| 12 || ca || number of major vessels (0–3) colored by fluoroscopy |
| 13 || thal || 3 = normal; 6 = fixed defect; 7 = reversible defect |
| 14 || num || diagnosis of heart disease (angiographic disease status)

*   Value 0: < 50% diameter narrowing
*   Value 1: > 50% diameter narrowing
*   (in any major vessel: attributes 59 through 68 are vessels)

 |

The snapshot of the heart disease csv file is illustrated in [Figure 4.3](#chapter04.xhtml#fig4_11)

![Figure  4.3  Snapshot heart.csv file.](images/fig4_3.jpg)

Figure  4.3  Snapshot heart.csv file.

#### 4.4.1.1 Analysis of the Dataset

**Check how many rows and columns are in the dataset.**

**Python program: Datashape.py**

![Figure  4.4  Python Program Datashape.py to Analyze heart.csv.](images/fig4_4.jpg)

Figure  4.4  Python Program Datashape.py to Analyze heart.csv.

**Output**

![Figure  4.5  Output of Python Program Datashape.py.](images/fig4_5.jpg)

Figure  4.5  Output of Python Program Datashape.py.

We observe from the output that the heart disease dataset considered for classification has 303 rows and 14 columns. It is very important to know the attributes of all data, as illustrated in the Python program seen in [Figure 4.6](#chapter04.xhtml#fig4_6) and its output illustrated in [Figure 4.7](#chapter04.xhtml#fig4_7).

**Python program: Datatype.py**

![Figure  4.6  Python Program to Print the Datatype of Each Attribute.](images/fig4_6.jpg)

Figure  4.6  Python Program to Print the Datatype of Each Attribute.

**Output**

![Figure  4.7  Output of Python Program to Print the Datatype of Each Attribute.](images/fig4_7.jpg)

Figure  4.7  Output of Python Program to Print the Datatype of Each Attribute.

#### 4.4.1.2 Correlation

Correlation indicates the relatedness among variables. It generally speaks about what one variable knows about the other. The performance of machine learning, like linear and logistic regression, will be affected if they have highly correlated data.

#### 4.4.1.3 Pearson Correlation

Pearson correlation is a measure of the linear relationship between two variables (A and B). A value of 1 indicates positive correlation, -1 indicates negative correlation and 0 indicates no linear correlation. The Pearson correlation is as given in [Equation 4.4](#chapter04.xhtml#math4_4)

  
$$P\_{A,B} = \\frac{Cov\\left( {A,B} \\right)}{\\sigma A\\;\\sigma B},$$  
<graphic xlink:href="math4\_4.tif"/>

(4.4)

where  *C**o**v* <img src="images/inline-math4\_1.jpg" alt=""/>  is the covariance,

 *σ**A* <img src="images/inline-math4\_2.jpg" alt=""/>  is the standard deviation of *A* and

 *σ**B* <img src="images/inline-math4\_3.jpg" alt=""/>  is the standard deviation of *B*.

##### Python program: Pcovdata.py

![Figure  4.8  Python Program Pcovdata.py to Generate Covariance Matrix.](images/fig4_8.jpg)

Figure  4.8  Python Program Pcovdata.py to Generate Covariance Matrix.

![Figure  4.9  Output of Python Program Pcovdata.py to Generate Covariance Matrix.](images/fig4_9.jpg)

Figure  4.9  Output of Python Program Pcovdata.py to Generate Covariance Matrix.

The matrix displays positive covariance, as you can see in the diagonal line from left top to right bottom.

### 4.4.2 Check whether Scikit-learn is properly installed

Run the statement on the idle editor in Python as illustrated in [Figure 4.10](#chapter04.xhtml#fig4_10).

![Figure  4.10  Python Program to Check Whether Scikit-learn Is Properly Installed.](images/fig4_10.jpg)

Figure  4.10  Python Program to Check Whether Scikit-learn Is Properly Installed.

If we get the interpreter prompt without any error that means Scikit-learn has been installed properly.

### 4.4.3 Procedure for Loading the Data

The given dataset is available as csv file.

*from pandas import read\_csv*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak', 'ca','thal','target'\]*

*data = read\_csv(filename, names=names)*

The **read\_csv()** function helps you to load a CSV file into a Pandas DataFrame.

### 4.4.4 Splitting Data into Training and Testing

This is the procedure:

*from sklearn.model\_selection import train\_test\_split*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

The train\_test\_split()function is used to split the data into training and testing subsets. The percentage of split in the function is 80/20 (i.e., 80% for training and 20% for testing).

The random\_state is set to an integer that will act as a seed for the random number generator during the split.

### 4.4.5 Building the Models for Supervised Learning

*   **Logistic Regression**  
    *from sklearn.linear\_model import LogisticRegression*  
    *reg = LogisticRegression()*  
    Here reg is an object of the class LogisticRegression()
*   **Naive Bayes**  
    *from sklearn.naive\_bayes import GaussianNB*  
    *nbmodel = GaussianNB()*  
    Here nbmodel is an object of the class LogisticRegression()
*   **Neural Network MLP**  
    *from sklearn.neural\_network import MLPClassifier*  
    *mlp = MLPClassifier(hidden\_layer\_sizes=(30, 30, 30), max\_iter=1000)*  
    where *hidden\_layer\_sizes=(30, 30, 30)* defines the layers of the Neural Network  
    *max\_iter=1000* defines the iterations for training over the dataset.
*   **Support Vector Machine (SVM)**  
    *from sklearn.svm import SVC*  
    *svmodel=SVC(kernel='linear',probability=True)*  
    where *kernel='linear' means* it will be a Linear SVC model and is useful in a dataset that has a high number of features.  
    *probability=*True. If you want to generate predicted probabilities, Probability must be set to True.
*   **Random Forest**  
    *from sklearn.ensemble import RandomForestClassifier*  
    *clf = RandomForestClassifier()*  
    where clf means a classifier is an object of the class RandomForestClassifier.
*   **K Neighbors**  
    *from sklearn.neighbors import KNeighborsClassifier*  
    *knclf = KNeighborsClassifier(n\_neighbors=5)*  
    where n\_neighbors are the number of neighbors set to 5.
*   **Linear Discriminant Analysis (LDA)**  
    *from sklearn.discriminant\_analysis import LinearDiscriminantAnalysis*  
    *ldac = LinearDiscriminantAnalysis()*  
    where ldac means a classifier is an object of the class LDA.

### 4.4.6 Model Fitting, Scaling and Prediction in Supervised Learning

Model fitting is equivalent to training the model with the training data. Let us see how various models are trained. For a classification, you can classify the test data with the predict method

*   **Logistic Regression**  
    *reg.fit(X\_train, y\_train)*  
    *y\_pred = reg.predict(X\_test)*  
    Here, the *reg.fit(X\_train, y\_train)* is used to train the classifier model; prediction for new data instances is done with the *reg.predict(X\_test)* method.
*   **Naive Bayes**  
    The training and prediction are similar to that in logistic regression.  
    r=nbmodel.fit(X\_train, y\_train)  
    y\_pred = nbmodel.predict(X\_test)
*   **Neural Network MLP**  
    If your data has different scales, it is helpful to normalize and rescale the data. Feature scaling is done only on the training data; the test data is kept as close to reality as possible as seen in *scaler.fit(X\_train).*  
    *from sklearn.neural\_network import MLPClassifier*  
    *scaler = StandardScaler()*  
    *scaler.fit(X\_train)*  
    *X\_train = scaler.transform(X\_train)*  
    *X\_test = scaler.transform(X\_test)*  
    *r=mlp.fit(X\_train, y\_train)*  
    *y\_pred = mlp.predict(X\_test)*  
    The transform function is used to compute the mean and standard deviation on the training set so that you can apply it to the testing set.
*   **Support Vector Machine (SVM)**  
    The training of the SVM classifier is done with the fit() function for the training data; the prediction of the trained classifier is done with the predict() function for the testing data.  
    *r=svmodel.fit(X\_train, y\_train)*  
    *y\_pred = svmodel.predict(X\_test)*
*   **Random Forest**  
    *from sklearn.ensemble import RandomForestClassifier*  
    *stdc = StandardScaler()*  
    *X\_train = stdc.fit\_transform(X\_train)*  
    *X\_test = stdc.transform(X\_test)*  
    *r=clf.fit(X\_train, y\_train)*  
    *y\_pred = clf.predict(X\_test)*  
    The Standard Scaler is applied for the Random Forest feature scaling of training data and is further transformed. Once it is done, the model classifier is trained on the training data and tested for predictions on the predict() function.
*   **K Neighbors**  
    *from sklearn.preprocessing import StandardScaler*  
    *ksc = StandardScaler()*  
    *ksc.fit(X\_train)*  
    *X\_train = ksc.transform(X\_train)*  
    *X\_test = ksc.transform(X\_test)*  
    *r=knclf.fit(X\_train, y\_train)*  
    *y\_pred = knclf.predict(X\_test)*  
    The Standard Scaler is applied for the K Nearest Neighbor feature scaling of training data and is further transformed. Once it is done, the model classifier is trained on the training data and tested for predictions on the predict() function.
*   **Linear Discriminant Analysis (LDA)**  
    *from sklearn.preprocessing import StandardScaler*  
    *lsc = StandardScaler()*  
    *lsc.fit(X\_train)*  
    *X\_train = lsc.transform(X\_train)*  
    *X\_test = lsc.transform(X\_test)*  
    *r = ldac.fit\_transform(X\_train, y\_train)*  
    *y\_pred = ldac.predict(X\_test)*  
    The Standard Scaler is applied for LDA and the feature scaling of its training data that is further transformed. Once it is done, the model classifier is trained on the training data and tested for predictions on the predict() function.

### 4.4.7 K-Fold Classification Accuracy with Scikit-learn.

*from sklearn.model\_selection import KFold*

*num\_folds = 10*

*kfold = KFold(n\_splits=10, random\_state=7)*

*results = cross\_val\_score(reg, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100,"%")*

In our experimentation, we have used 10-fold K Cross Validation. Here 1 fold is used for validation whereas 10−1 = 9 folds are used for training; this is repeated for all combinations. Compute the cross validation scores with the function *cross\_val\_score().*Finally, compute the accuracy as the mean of results.

### 4.4.8 Confusion Matrix Implementation with Sckit-learn.

A confusion matrix provides insights into the classification algorithm. The Scikit code is

*from sklearn import metrics*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

Consider the following confusion matrix generated Logistic Regression example

*   \[\[22 5\]
*   \[4 30\]\]

The diagonal elements show the classifications for each class. Thus, for class 0 we have 22 correct predictions and for class 1 we have 30 accurate predictions.

The off diagonal shows the wrong classifications.

Thus, accuracy is correctly classified/all classified = (52/61)\* 100 = 85.2459.

### 4.4.9 ROC Curve

The ROC curve is used to balance between True Positives and False positives. The code to plot ROC is

*y\_pred\_prob = reg.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Logistic Regression')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

The prediction of probabilities is done with the reg.predict\_proba() function. We restrict it to only positive outcomes. We compute the Area Under Curve(AUC) and Receiver Operating Characteristic curve (RUC) with the functions *metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*metrics.roc\_curve(y\_test, y\_pred\_prob)* and plot the same.

If AUC is 0, the outcome is bad; if AUC is 1, the outcome is good.

## 4.5 Logistic Regression

Logistic regression is also a supervised learning technique. It is more suitable as a classification technique rather than as a regression technique. Logistic regression is more often applied to discrete classes. Examples of discrete classes are male/female, cat/dog and pass/fail. Logistic regression models its output as a logistic sigmoid function, which maps to the discrete classes.

The mathematical modeling of logistic regression is as follows in Equation 4.5.

  
$$\\begin{matrix} y\_{d} & {= \\log\\left( {p\\!/\\!{1 - p}} \\right)} \\\\ & {= \\ \\gamma\_{0} + \\ \\gamma\_{1} \\ast \\ x\_{1\\ } + \\ \\gamma\_{2} \\ast \\ x\_{2\\ } + - - - - - - - \\ \\gamma\_{n} \\ast \\ x\_{m},} \\\\ \\end{matrix}$$  
<graphic xlink:href="math4\_5.tif"/>

(4.5)

where p is the probability that  *y*[*d*] = 1 <img src="images/inline-math4\_4.jpg" alt=""/>  given the values of the vector of the input features x

 *γ*[0], *γ*[1], *γ*[2] −  −  −  −  −  − − *γ*[*n*] <img src="images/inline-math4\_5.jpg" alt=""/>  are estimated through the maximum likelihood function.

 *x*[1 ], *x*[2 ],  −  −  −  −  −  − − *x*[*m* ] <img src="images/inline-math4\_6.jpg" alt=""/>  are vectors of the input features.

 *γ*[*n*] <img src="images/inline-math4\_7.jpg" alt=""/>  is known as the vector of coefficients.

### 4.5.1 Logistic Regression Sigmoid Function

The sigmoid function used in logistic regression is shown in [Figure 4.11](#chapter04.xhtml#fig4_11).

![Figure  4.11  Sigmoid Curve.](images/fig4_11.jpg)

Figure  4.11  Sigmoid Curve.

The sigmoid function maps any real value to a value between 0 and 1. The sigmoid function is given by the [Equation 4.6](#chapter04.xhtml#math4_6).

  
$$S(y) = \\frac{1}{1 + e^{- y}},$$  
<graphic xlink:href="math4\_6.tif"/>

(4.6)

where  *S*(*y*) <img src="images/inline-math4\_8.jpg" alt=""/>  is a value between 0 and 1.

 *y* <img src="images/inline-math4\_9.jpg" alt=""/>  is the input to the function.

 *e* <img src="images/inline-math4\_10.jpg" alt=""/>  is the base to the natural log.

### 4.5.2 Types of Logistic Regression

*   **Binary logistic regression:** This type of logistic regression models two outcomes only (e.g., pass and fail).
*   **Multinomial logistic regression:** This type of logistic regression models three or more outcomes without any ordering (e.g., cats, dogs and sheep).
*   **Ordinal logistic regression:** This type of logistic regression models three or more outcomes with ordering (e.g., product ratings from 1 to 5).

#### To apply logistic regression, the dataset should ideally support the following properties

*   The independent variables need to be independent of each other.
*   Proper and meaningful variables need to be considered for modeling logistic regression.
*   Logistic regression usually requires large sample sizes.

**Note:** If logistic regression has fewer parameters, there is less chance of overfitting. Overfitting analysis corresponds to a particular set of data and may fail for additional data.

#### Python Program: Logisticregrr.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.linear\_model import LogisticRegression*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*data = read\_csv(filename, names=names)*

*types = data.dtypes*

*array = data.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

*num\_folds = 10*

*kfold = KFold(n\_splits=10, random\_state=7)*

*reg = LogisticRegression()*

*results = cross\_val\_score(reg, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100,"%")*

*reg.fit(X\_train, y\_train)*

*y\_pred = reg.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = reg.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Logistic Regression')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.12  Output of Python Program Logisticregrr.py.](images/fig4_12.jpg)

Figure  4.12  Output of Python Program Logisticregrr.py.

![Figure  4.13  ROC Curve of Logistic Regression.](images/fig4_13.jpg)

Figure  4.13  ROC Curve of Logistic Regression.

## 4.6 Naive Bayes

Naive Bayes is a supervised learning technique. It is a probabilistic classifier based on the Bayes theorem. It represents a classification technique that relies on the independence of the predictors (independent variables).

The term Naive implies that the occurrence of certain feature is independent of other features. The term Bayes tells that the basis of Naive Bayes is the Bayes theorem. Bayes Theorem gives the conditional probability of event X given event Y has occurred, as specified in Equation 4.7.

  
$$P\\left( {X|Y} \\right) = \\ \\frac{P(Y|X).P\\left( X \\right)}{P\\left( Y \\right)},$$  
<graphic xlink:href="math4\_7.tif"/>

(4.7)

where

 *P*(*X*|*Y*) <img src="images/inline-math4\_11.jpg" alt=""/>  is the conditional probability of X given Y.

 *P*(*Y*|*X*) <img src="images/inline-math4\_12.jpg" alt=""/>  is the conditional probability of Y given X.

 *P*(*X*) <img src="images/inline-math4\_13.jpg" alt=""/>  is the Probability of event X.

 *P*(*Y*) <img src="images/inline-math4\_14.jpg" alt=""/>  is the Probability of event Y.

The best feature of Naive Bayes is that it can handle an arbitrary number of independent variables regardless of whether they are independent or continuous.

From a set of variables  *X* = {*x*1, *x*2,−−−−−−*x**n*} <img src="images/inline-math4\_15.jpg" alt=""/>  we want to get the posterior probability for the event *Cj* among the set of outcomes  *C* = {*c*1, *c*2,−−−−−−−*c**n*} <img src="images/inline-math4\_16.jpg" alt=""/> . Here in more generic terms X is the set of predictors, and C is the categorical levels present in the dependent variables.

The final posterior probability is as given [Equation 4.8](#chapter04.xhtml#math4_8).

  
$$p\\left( {C\_{j\\ }|\\ X} \\right) \\propto p\\ \\left( C\_{j\\ } \\right)\\prod\\limits\_{k}^{n}p\\left( {x\_{n\\ }|\\ C\_{j\\ }} \\right).\\ $$  
<graphic xlink:href="math4\_8.tif"/>

(4.8)

### 4.6.1 Advantages of Naive Bayes

*   It builds the model quickly and makes quick decisions.
*   It can handle both continuous and discrete data.
*   It is highly scalable with respect to the number of predictors and data points.
*   Medical Diagnosis
*   Weather Prediction
*   News Classification

### 4.6.2 Naive Bayes Applications

*   Medical Diagnosis
*   Weather Prediction
*   News Classification

#### Python Program: NaiveBayes.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.naive\_bayes import GaussianNB*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*nbmodel = GaussianNB()*

*results = cross\_val\_score(nbmodel, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*r=nbmodel.fit(X\_train, y\_train)*

*y\_pred = nbmodel.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = r.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Naive Bayes')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.14  Python Program NaiveBayes.py to Implement Naive Bayes.](images/fig4_14.jpg)

Figure  4.14  Python Program NaiveBayes.py to Implement Naive Bayes.

![Figure  4.15  ROC Curve of Naive Bayes.](images/fig4_15.jpg)

Figure  4.15  ROC Curve of Naive Bayes.

## 4.7 Neural Network MLP

Neural network or commonly known as Artificial Neural Network is a system for processing information inspired from biological neural networks. It is made up of numerous processing elements known as neurons that interact with one another to solve a problem.

Neural Networks are classified into 3 categories

*   Multi-Layer Perceptron (MLP)
*   Convolutional Neural Networks
*   Recurrent Neural Network

In our discussion, we consider the MLP classifier, composed of at least three layers of neurons. This is illustrated in [Figure 4.16](#chapter04.xhtml#fig4_16).

![Figure  4.16  Three Layer Multi-layer Perceptron.](images/fig4_16.jpg)

Figure  4.16  Three Layer Multi-layer Perceptron.

LPs are fully connected. Each layer connects to another layer with some weight  *w*[*i**j*] <img src="images/inline-math4\_17.jpg" alt=""/> . A neural network works in two phases.

*   Feed forward
*   Backpropagation

In the feed forward phase, the following steps are executed.

1.  The values in the inputs are multiplied by weights. They are further added with bias.
2.  Hidden layer neurons have an activation function like sigmoid or relu. These are applied to the values received from the input layers.
3.  The processed values are then given to the output layers. These are the actual outputs of the algorithm.

The outputs generated may need not be accurate. Thus, the backpropagation phase is initiated.

In the backpropagation phase, the following steps are executed.

1.  The error is calculated by computing the difference between the output and the input. This difference is known as a loss and the corresponding function as the loss function. An example of the loss function is a mean squared error.
2.  A partial derivative of the error function known as the gradient descent is computed. If the slope of the error function is positive, then weights can be reduced or the weights can be increased. This exercise reduces the overall error, and its corresponding function is called the optimization function.

MLPs are suitable for classification problems in which the inputs are assigned a class or label.

### 4.7.1 Application of MLPs

*   Time Series Predictions
*   Image Processing
*   Character Recognition

#### Python program: MLP.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.neural\_network import MLPClassifier*

*from sklearn.model\_selection import train\_test\_split*

*from matplotlib import pyplot as plt*

*from sklearn import metrics*

*from sklearn.preprocessing import StandardScaler*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

*scaler = StandardScaler()*

*scaler.fit(X\_train)*

*X\_train = scaler.transform(X\_train)*

*X\_test = scaler.transform(X\_test)*

*mlp = MLPClassifier(hidden\_layer\_sizes=(30, 30, 30), max\_iter=1000)*

*r=mlp.fit(X\_train, y\_train)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*results = cross\_val\_score(mlp, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*y\_pred = mlp.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = r.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Neural Network')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.17  Python Program MLP.py to Implement Neural Network Multi-layer Perceptron.](images/fig4_17.jpg)

Figure  4.17  Python Program MLP.py to Implement Neural Network Multi-layer Perceptron.

![Figure  4.18  ROC Curve of Neural Network Multi-layer Perceptron.](images/fig4_18.jpg)

Figure  4.18  ROC Curve of Neural Network Multi-layer Perceptron.

## 4.8 Support Vector Machine

SVM is a supervised learning technique that helps in the classification and regression analysis of data. SVM strives to find a hyperplane that divides the data into corresponding classes. At the simplest level, a hyperplane is a straight line that divides the data into corresponding classes.

Support vectors are the data points nearest a hyperplane. The distance from the nearest data point to the hyperplane is known as a margin, and the goal is to have a wider margin for optimal classification.

The transformation of non-separable data points to transferable data points is possible through kernel functions.

In our discussion, let us consider the Linear SVM.

To get the maximum margin separation, the following Equations 4.9 and 4.10 need to be computed.

  
*W*^(*T*)*X*[*i*] + *b* >  + 1   
<graphic xlink:href="math4\_9.tif"/>

(4.9)

  
*W*^(*T*)*X*[*i*] + *b* <  − 1.   
<graphic xlink:href="math4\_10.tif"/>

(4.10)

Here Equation 4.9 is considered for all positive cases. Equation 4.10 is considered for negative cases.

  ∥ *W*∥² <img src="images/inline-math4\_18.jpg" alt=""/>  is required to be as small as possible.

The separator is then defined as a set of points for the [Equation 4.11](#chapter04.xhtml#math4_11)

  
*W*.*x* + *b* = 0.   
<graphic xlink:href="math4\_11.tif"/>

(4.11)

### 4.8.1 Advantages of Support Vector Machines (SVM)

*   They work well in high-dimensional spaces.
*   SVM is capable of avoiding problems due to bias and overfitting.

### 4.8.2 Limitations of Support Vector Machines (SVM)

*   They have performance issues when working with larger data sets.
*   SVM is impacted with the presence of noise in the datasets.

### 4.8.3 Applications of SVM

*   Image Classification
*   Text Categorization
*   Bioinformatics

#### Python program: svm.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.svm import SVC*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*svmodel=SVC(kernel='linear',probability=True)*

*r=svmodel.fit(X\_train, y\_train)*

*results = cross\_val\_score(svmodel, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*y\_pred = svmodel.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = r.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Support Vector Machine')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.19  Python Program svm.py to Implement Support Vector Machine.](images/fig4_19.jpg)

Figure  4.19  Python Program svm.py to Implement Support Vector Machine.

**ROC Curve**

![Figure  4.20  ROC Curve of Support Vector Machine.](images/fig4_20.jpg)

Figure  4.20  ROC Curve of Support Vector Machine.

## 4.9 Random Forest

Random forest falls under the category of supervised learning. Random forest builds multiple trees and merges them for an accurate decision. Thus, random forest is involved in building multiple decision trees.

### 4.9.1 Decision Tree

A Decision Tree follows a top-down approach in which the root nodes begin the process of binary splits with some criteria for the reduction in entropy. Here entropy is the measure of unpredictability in the data.

The root node N is the dataset with different class or labels of data. It is split into left and right subsets. The goal of these subsets is to have purity of class. If this is achieved at the corresponding node whose entropy is 0, only one kind of label is left. Otherwise, the process of splitting continues to determine the remaining labels.

Consider the dataset in [Table 4.2](#chapter04.xhtml#table4_2)

Table  4.2  Mobile phone dataset

| Color || Price || label |
| --- | --- | --- |
| Gold || 5000 || iPhone |
| --- | --- | --- |
| Blue || 5000 || Samsung |
| Black || 3000 || Nokia |
| Gold || 5000 || iPhone |
| Blue || 5000 || Samsung |
| Black || 3000 || Nokia |

A simple decision process for illustrative purpose is shown in [Figure 4.21](#chapter04.xhtml#fig4_21).

![Figure  4.21  Decision Tree Process in Random Forest.](images/fig4_21.jpg)

Figure  4.21  Decision Tree Process in Random Forest.

### 4.9.2 Advantages of Random Forest

*   The problem of overfitting is reduced.
*   It has the capability to produce accurate predictions for large datasets.
*   It has the ability to consider missing data.

### 4.9.3 Limitations of Random Forest

*   Trees are sensitive to data changes in the training data.
*   A large number of trees can slow down the algorithm.

#### Python program: RandomForest.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.preprocessing import StandardScaler*

*from sklearn.ensemble import RandomForestClassifier*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, Y, test\_size = 0.2, random\_state = 0)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*stdc = StandardScaler()*

*X\_train = stdc.fit\_transform(X\_train)*

*X\_test = stdc.transform(X\_test)*

*clf = RandomForestClassifier()*

*r=clf.fit(X\_train, y\_train)*

*results = cross\_val\_score(clf, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*y\_pred = clf.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = r.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Random Forest')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.22  Python Program RandomForest.py to Implement Random Forest.](images/fig4_22.jpg)

Figure  4.22  Python Program RandomForest.py to Implement Random Forest.

![Figure  4.23  ROC Curve of Random Forest.](images/fig4_23.jpg)

Figure  4.23  ROC Curve of Random Forest.

## 4.10 K Neighbors

K Neighbors (also known as K Nearest Neighbors (KNN)) is a supervised learning algorithm. In this type of instance-based learning, the training observations are retained as the part of the model. It is known as competition-based learning because it uses competition between data instances for prediction. It is also called lazy learning because the decision to build a model is pushed until the time for prediction. When KNN is referred as non-parametric, it means that it makes no assumptions of the underlying data distributions.

K nearest neighbors are employed perform classification. Euclidean distance formula is used to measure the distance as in [Equation 4.12](#chapter04.xhtml#math4_12)

  
$$d\\left( {a,b} \\right) = \\sum\\limits\_{i = 1}^{n}\\left( {b\_{i} - a\_{i}} \\right)^{2}.$$  
<graphic xlink:href="math4\_12.tif"/>

(4.12)

The Euclidean distance between the two points provides the length of the path connecting them.

KNN believes that samples with similar inputs belong to the same class as illustrated in [Figure 4.24(a)](#chapter04.xhtml#fig4_24) and [Figure 4.24(b)](#chapter04.xhtml#fig4_24).

![Figure  4.24  a  K= 1 in KNN.](images/fig4_24a.jpg)

Figure  4.24  a  K= 1 in KNN.

![Figure  4.24  b  K= 3 in KNN.](images/fig4_24b.jpg)

Figure  4.24  b  K= 3 in KNN.

Here ? is the new sample and + and – stand for training data samples

The value of k determines the closest neighbors to consider. When K=1, the label of the new sample will be that of the 1 closest neighbor. When K=3 a voting by majority is considered. Suppose if two labels are X and one label is Y. Then, per the majority system, the new label will be X. In a tie, then a tie-breaker rule (e.g., closest neighbor label or random label) is chosen.

### 4.10.1 Advantages of KNN

*   KNN is relatively fast for small training data sets.
*   It makes no assumption of data and works well for non-linear data.
*   It can be applied for both classification and regression.

### 4.10.2 Limitations of KNN

*   KNN is computationally expensive because it retains the training data.
*   It is sensitive for larger datasets.

#### Python program: kneighbor.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.neighbors import KNeighborsClassifier*

*from sklearn.preprocessing import StandardScaler*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X,Y,test\_size=0.2,random\_state=0)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*ksc = StandardScaler()*

*ksc.fit(X\_train)*

*X\_train = ksc.transform(X\_train)*

*X\_test = ksc.transform(X\_test)*

*knclf = KNeighborsClassifier(n\_neighbors=5)*

*r=knclf.fit(X\_train, y\_train)*

*results = cross\_val\_score(knclf, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*y\_pred = knclf.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print("The Confusion Matrix is: ")*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = r.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('K Nearest Neighbor')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

*plt.show()*

**Output**

![Figure  4.25  Python Program kneighbor.py to Implement K Neighbors.](images/fig4_25.jpg)

Figure  4.25  Python Program kneighbor.py to Implement K Neighbors.

![Figure  4.26  ROC Curve of K Neighbors.](images/fig4_26.jpg)

Figure  4.26  ROC Curve of K Neighbors.

## 4.11 Linear Discriminant Analysis (LDA)

Linear Discriminant Analysis (LDA) is a supervised learning technique. It is used as a dimensionality reduction technique. LDA as a classification technique was developed by R. A. Fisher.

LDA tries to achieve

*   Making the distance between the two clusters large.
*   Making the intra-cluster distance small.

Select “W” to maximize the ratio of between-class scatter and the within-class scatter.

The between class scatter matrix is defined in [Equation 4.13](#chapter04.xhtml#math4_13)

  
$$S\_{B} = \\ \\sum\\limits\_{i = 1}^{c}N\_{i}\\left( {\\mu\_{i} - \\mu} \\right)\\left( {\\mu\_{i} - \\mu} \\right)^{T},$$  
<graphic xlink:href="math4\_13.tif"/>

(4.13)

where  *μ*[*i*] <img src="images/inline-math4\_19.jpg" alt=""/>  is the mean of the class  *X*[*i*] <img src="images/inline-math4\_20.jpg" alt=""/> 

 *N*[*i*] <img src="images/inline-math4\_21.jpg" alt=""/>  is the number of samples in class

 *X*[*i*] <img src="images/inline-math4\_22.jpg" alt=""/>   *μ* <img src="images/inline-math4\_23.jpg" alt=""/>  is the overall mean of the data

*c* is the overall number of classes.

The within-class scatter matrix is

  
$$S\_{W} = \\;\\sum\\limits\_{i = 1}^{c}.\\sum\\limits\_{x\_{k} \\in x\_{i}}{\\left( {x\_{k} - \\mu\_{i}} \\right){\\left( {x\_{k} - u\_{i}} \\right)^{T},}}$$  
<graphic xlink:href="math4\_14.tif"/>

(4.14)

here  *x*[*k*] <img src="images/inline-math4\_24.jpg" alt=""/>  is the subset of the sample class  *X*[*i*] <img src="images/inline-math4\_25.jpg" alt=""/> 

The generalized eigenvalue problem of the matrix is given in [Equation 4.15](#chapter04.xhtml#math4_15)

  
*S*[*w*]^( − 1)*S*[*B*].  
<graphic xlink:href="math4\_15.tif"/>

(4.15)

Equation 4.15 is solved to compute *w* Eigenvectors that maximize [Equation 4.16](#chapter04.xhtml#math4_16)

  
$$w = {arg\\; max}\\left| \\frac{W^{T}S\_{B}W}{W^{T}S\_{W}W} \\right|.$$  
<graphic xlink:href="math4\_16.tif"/>

(4.16)

Sort the eigenvectors by decreasing eigenvalues and choose the *k* eigenvectors with the largest eigenvalues to form a transformation matrix. Use the transformation matrix to convert the original data set to lower dimension space.

### 4.11.1 Advantages of LDA

*   LDA is simple and mathematically robust.
*   It produces results with accuracy comparable with more complex models.

### 4.11.2 Limitations of LDA

*   LDA is sensitive to overfitting.
*   It is not well suited to non-linear problems.

#### Python program: LDA.py

*from pandas import read\_csv*

*from sklearn.model\_selection import KFold*

*from sklearn.discriminant\_analysis import LinearDiscriminantAnalysis*

*from sklearn.preprocessing import StandardScaler*

*from sklearn.model\_selection import cross\_val\_score*

*from sklearn.model\_selection import train\_test\_split*

*from sklearn import metrics*

*from matplotlib import pyplot as plt*

*filename = 'heart.csv'*

*names = \['age','sex','cp','trestbps','chol','fbs','restecg','thalach','exang','oldpeak','slope','ca','thal','target'\]*

*dataframe = read\_csv(filename, names=names)*

*array = dataframe.values*

*X = array\[:,0:13\]*

*Y = array\[:,13\]*

*X\_train, X\_test, y\_train, y\_test = train\_test\_split(X,Y,test\_size=0.2,random\_state=0)*

*kfold = KFold(n\_splits=10, random\_state=7)*

*lsc = StandardScaler()*

*lsc.fit(X\_train)*

*X\_train = lsc.transform(X\_train)*

*X\_test = lsc.transform(X\_test)*

*ldac = LinearDiscriminantAnalysis()*

*r = ldac.fit\_transform(X\_train, y\_train)*

*results = cross\_val\_score(ldac, X, Y, cv=kfold)*

*print("K-Fold Classification Accuracy:",results.mean()\*100)*

*y\_pred = ldac.predict(X\_test)*

*conf\_matrix = metrics.confusion\_matrix(y\_test, y\_pred)*

*print("The Confusion Matrix is: ")*

*print(conf\_matrix)*

*print("Confusion Matrix Accuracy:",metrics.accuracy\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Precision:",metrics.precision\_score(y\_test, y\_pred)\*100,"%")*

*print("Confusion Matrix Recall:",metrics.recall\_score(y\_test, y\_pred)\*100,"%")*

*y\_pred\_prob = ldac.predict\_proba(X\_test)\[::,1\]*

*fp\_rate, tp\_rate, \_ = metrics.roc\_curve(y\_test, y\_pred\_prob)*

*auc\_score = metrics.roc\_auc\_score(y\_test, y\_pred\_prob)*

*plt.rcParams\['toolbar'\] = 'None'*

*plt.title('Linear Discriminant Analysis')*

*plt.xlabel('False Positive Rate')*

*plt.ylabel('True Positive Rate')*

*plt.plot(fp\_rate,tp\_rate,label="data 1, auc="+str(auc\_score))*

*plt.legend(loc=4)*

plt.show()

**Output**

![Figure  4.27  Python Program LDA.py to Implement Linear Discriminant Analysis.](images/fig4_27.jpg)

Figure  4.27  Python Program LDA.py to Implement Linear Discriminant Analysis.

**ROC Curve**

![Figure  4.28  ROC Curve of Linear Discriminant Analysis.](images/fig4_28.jpg)

Figure  4.28  ROC Curve of Linear Discriminant Analysis.

## Exercises

1.  Answer the following briefly. 
    1.  Define Machine Learning.
    2.  Bring out the difference between Supervised and Unsupervised Learning.
    3.  What is meant by Reinforcement Learning?
    4.  What is the difference between classification and regression?
    5.  List the metrics for classification.
    6.  What is a CSV file; which Pandas function do you use to load it?
    7.  What is the advantage of drawing the correlation of data?
    8.  Is it good to use Logistic Regression for classification or as the name suggests for regression?
    9.  Does the Neural Network mimic the function of the human brain? Justify briefly.
    10.  Give the application areas in which Naive Bayes could be applied.
    11.  What is meant by overfitting?
    12.  What is the role of the sigmoid function?
    13.  Can SVMs be applied to regression also?
    14.  Does Random Forest depend on decision trees?
    15.  Is K Nearest Neighbor Supervised or Unsupervised learning?
    16.  Who developed the Linear Discriminant Analysis technique?
2.  Using the Prima Indians diabetes dataset, apply the following supervised machine learning algorithms: 
    *   Logistic Regression
    *   Naïve Bayes
    *   Neural Network
    *   SVM
    *   Random Forest
    *   K N N
    *   LDA

Download Prima Indians diabetes dataset from [http://networkrepository.com/pima-indians-diabetes.php](http://networkrepository.com)

Compare the results of classification metrics of the best performing and worst performing algorithms and justify the reasons for their good and poor performances.

# [Chapter 5](#toc.xhtml#ch-05)

# [Introduction to Image Processing](#toc.xhtml#ch-05)

Image processing is a technique for performing a specific operation to an image, in order to produce an enriched image or to obtain some useful information from it. Digital image processing is rapidly growing in the field of computer science; it plays an important role in science and technology, with applications in the fields of photography, television, remote sensing, robotics, industrial inspection and medical diagnosis.

Image-Processing Applications

*   Computerized Photography (e.g., Photoshop)
*   Fingerprint/face/iris Recognition
*   Space-Image Processing (e.g., interplanetary probe images, Hubble space telescope images)
*   Automatic Character Recognition (e.g., license-plate recognition)
*   Medical/biological Image Processing (e.g., interpretation of X-ray images, blood/cellular microscopic images)
*   Industrial Applications (e.g., product inspection/sorting)

In the following report, image-processing operations will be implemented using the Raspberry Pi. Raspberry Pi is based on python and OpenCV packages.

In this we chapter, we show how to:

*   Load, display and save images on Raspberry Pi.
*   Scale (resize) images.
*   Vary the brightness of images.
*   Perform bitwise operations.
*   Blur and sharpen images.
*   Perform thresholding on images.
*   Perform erosion and dilation.
*   Perform edge detection on images.
*   Perform image segmentation.

## 5.1 Load, Display and Save an Image on Raspberry Pi, Using Python and Open CV

*\# Import Computer Vision package – cv2*

*import cv2*

 

*\# Read the image using imread built-in function*

*image = cv2.imread('image\_1.jpg')*

 

*\# Display original image using imshow built-in function*

*cv2.imshow("Original", image)*

 

*\# Wait until any key is pressed*

*cv2.waitKey(0)*

 

*\# Save the image using imwrite built-in function*

*cv2.imwrite("Saved Image.jpg", image)*

 

**Output:**

![Figure  5.1  Output of Python Program Load, Display and Save an Image on Raspberry Pi.](images/fig5_1.jpg)

Figure  5.1  Output of Python Program Load, Display and Save an Image on Raspberry Pi.

*   The objective of this code is to load, display and save an image. The first step is to import the computer vision package ***cv2***.
*   We can read the image using the built-in function, **cv2.imread**. The **cv2.imread** function takes one parameter within a single inverted quote, which is. the name of the image.
*   We can display the image using the built-in function, **cv2.imshow**. The **cv2.imshow** function requires 2 parameters: the name under which the image is saved and the variable containing the read image.
*   To save the image, we can use the built-in function, **cv2.imwrite**.
*   The built-in function, **cv2.waitkey**, is used to wait until you press any key in the keyboard.

## 5.2 Scaling (Resizing) Images – Cubic, Area and Linear Interpolations

**Python Program: Scaling.py**

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_2.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey()*

*\# cv2.resize(image, output image size, x scale, y scale, interpolation)*

*\# Scaling using cubic interpolation*

*scaling\_cubic = cv2.resize(image, None, fx=.75, fy=.75, interpolation = cv2.INTER\_CUBIC)*

*cv2.imshow('Cubic Interpolated', scaling\_cubic)*

*cv2.waitKey()*

*\# Scaling using area interpolation*

*scaling\_skewed = cv2.resize(image, (600, 300), interpolation = cv2.INTER\_AREA)*

*cv2.imshow('Area Interpolated', scaling\_skewed)*

*cv2.waitKey()*

*scaling\_linear = cv2.resize(image, None, fx=0.5, fy=0.5, interpolation = cv2.INTER\_LINEAR)*

*\# Scaling using linear interpolation*

*cv2.imshow('Linear Interpolated', scaling\_linear)*

*cv2.waitKey()*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.2  Output of Python Program to Display Original Image.](images/fig5_2.jpg)

Figure  5.2  Output of Python Program to Display Original Image.

![Figure  5.3  Output of Python Program to Display Scaling Using Cubic Interpolation.](images/fig5_3.jpg)

Figure  5.3  Output of Python Program to Display Scaling Using Cubic Interpolation.

![Figure  5.4  Output of Python Program Load to Display Scaling Using Area Interpolation.](images/fig5_4.jpg)

Figure  5.4  Output of Python Program Load to Display Scaling Using Area Interpolation.

![Figure  5.5  Output of Python Program Load to Display Scaling Using Linear Interpolation.](images/fig5_5.jpg)

Figure  5.5  Output of Python Program Load to Display Scaling Using Linear Interpolation.

*   This program involves image scaling to resize the image.
*   OpenCV utilizes the function **cv2.resize()** for this purpose. The size of the image can be specified either manually or with the scaling factor. There are different interpolation methods, preferably **cv2.INTER\_AREA** for shrinking the image and **cv2.INTER\_CUBIC** (slow) and **cv2.INTER\_LINEAR** for enlarging the image. The default interpolation method used is **cv2.INTER\_LINEAR** for all resizing purposes.
*   **cv2.resize**(**image, output image size, x scale, y scale, interpolation)**

This function takes five parameters. The first parameter is the name of the image to be resized, the second parameter is the size of the output image, the third and fourth parameters are the scaling factors of the image in both the x- and y-axis and the final parameter specifies the interpolation to be used, namely cubic, area, or linear. The default interpolation is linear. All interpolation methods take the dimensions of the output image and the image’s scaling factor as parameters.

*   **cv2.INTER\_CUBIC** is the command for cubic interpolation, **cv2.INTER\_AREA** for area interpolation and **cv2.INTER\_LINEAR** for linear interpolation.
*   The built-in function **cv2.destroyAllWindow()** closes all windows once any key is pressed.

## 5.3 Varying Brightness of Images Using Add and Subtract Operations

**Python Program: Varying\_Brightness.py**

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_4.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# np.ones returns an array of given shape and type, filled with ones*

*\# np.ones(shape, dtype)*

*matrix = np.ones(image.shape, dtype = "uint8") \* 120*

*\# image.shape: gives takes the shape of original image*

*\# uint8: unsigned integer (0 to 255)*

*\# matrix: contains ones, having same dimension as original image but mutlipied by 120*

*\# Adding matrix to orginal image increases brightness*

*add = cv2.add(image, matrix)*

*cv2.imshow("Added", add)*

*cv2.waitKey(0)*

*\# Subtracting matrix from original image decreases brightness*

*subtract = cv2.subtract(image, matrix)*

*cv2.imshow("Subtracted", subtract)*

*cv2.waitKey(0)*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.6  Output of Python Program to Display Original Image.](images/fig5_6.jpg)

Figure  5.6  Output of Python Program to Display Original Image.

![Figure  5.7  Output of Python Program That Adds Matrix to Original Image to Increase Brightness.](images/fig5_7.jpg)

Figure  5.7  Output of Python Program That Adds Matrix to Original Image to Increase Brightness.

![Figure  5.8  Output of Python Program That Subtracts Matrix to Original Image to Increase Brightness.](images/fig5_8.jpg)

Figure  5.8  Output of Python Program That Subtracts Matrix to Original Image to Increase Brightness.

*   This program varies the brightness of the image, using addition, subtraction and arithmetic operations.
*   The function **np.ones** returns an array consisting entirely of ones, based on the given inputs of shape and type. In this example, we used the data type uint8: unsigned integer (0 to 255). This array matrix consists of ones, having the same dimensions as the original image, multiplied by 120.
*   The built-in function **cv2.add(image, matrix)** is applied to add the array matrix **np.ones** to the original image in order to increase the brightness.
*   The built-in function **cv2.subtract(image, matrix)** subtracts the array matrix **np.ones** from the original image in order to decrease the brightness.

## 5.4 Bitwise Operations – AND, OR, XOR, NOT

**Python Program: Bitwise\_Operations.py**

*import cv2*

*import numpy as np*

*\# np.zeros(shape, dtype)*

*rectangle = np.zeros((200, 200), np.uint8)*

*\# dimension of the rectangle is 200 x 200*

*\# uint8: is an unsigned integer (0 to 255)*

 

*\# Creating rectangle using cv2.rectangle built-in function*

*\# cv2.rectangle(image, (x1,y1), (x2,y2), color, thickness)*

*cv2.rectangle(rectangle, (20, 20), (180, 180), 255, -1)*

*cv2.imshow("Rect", rectangle)*

*cv2.waitKey(0)*

*\# np.zeros(shape, dtype)*

*circle = np.zeros((200, 200), dtype = "uint8")*

*\# dimension of the circle is 200 x 200*

*\# uint8: is an unsigned integer (0 to 255)*

 

*\# Creating circle using cv2.circle built-in function*

*\# cv2.circle(image, centre, radius, color, thickness)*

*cv2.circle(circle, (100, 100), 100, 255, -1)*

*cv2.imshow("Circle", circle)*

*cv2.waitKey(0)*

*\# Performing bitwise AND operation on rectangle, circle*

*\# cv2.bitwise\_and(src1, src2)*

*And = cv2.bitwise\_and(rectangle, circle)*

*\# AND operation*

*\# A B Output*

*\# 0 0 0*

*\# 0 1 0*

*\# 1 0 0*

*\# 1 1 1*

*cv2.imshow("AND", And)*

*cv2.waitKey(0)*

*\# Performing bitwise OR operation on rectangle, circle*

*\# cv2.bitwise\_or(src1, src2)*

*Or = cv2.bitwise\_or(rectangle, circle)*

*\# OR operation*

*\# A B Output*

*\# 0 0 0*

*\# 0 1 1*

*\# 1 0 1*

*\# 1 1 1*

*cv2.imshow("OR", Or)*

*cv2.waitKey(0)*

*\# Performing bitwise XOR operation on rectangle, circle*

*\# cv2.bitwise\_xor(src1, src2)*

*Xor = cv2.bitwise\_xor(rectangle, circle)*

*\# XOR operation*

*\# A B Output*

*\# 0 0 0*

*\# 0 1 1*

*\# 1 0 1*

*\# 1 1 0*

*cv2.imshow("XOR", Xor)*

*cv2.waitKey(0)*

*\# Performing bitwise NOT operation on rectangle*

*\# cv2.bitwise\_not(src1)*

*Not\_rect = cv2.bitwise\_not(rectangle)*

*\# NOT operation*

*\# A Output*

*\# 0 1*

*\# 1 0*

*cv2.imshow("NOT1", Not\_rect)*

*cv2.waitKey(0)*

*\# Performing bitwise NOT operation on circle*

*\# cv2.bitwise\_not(src1)*

*Not\_circ = cv2.bitwise\_not(circle)*

*\# NOT operation*

*\# A Output*

*\# 0 1*

*\# 1 0*

*cv2.imshow("NOT2", Not\_circ)*

*cv2.waitKey(0)*

*cv2.destroyAllWindows()*

 

**Output:**

![Figure  5.9  Output of Python Program to Display Rectangle, Circle, OR and AND Operations.](images/fig5_9.jpg)

Figure  5.9  Output of Python Program to Display Rectangle, Circle, OR and AND Operations.

![Figure  5.10  Output of Python Program to Display NOT, NOT1 and XOR Operations.](images/fig5_10.jpg)

Figure  5.10  Output of Python Program to Display NOT, NOT1 and XOR Operations.

This program performs bit-wise operations and uses the operations AND, OR, XOR and NOT.

*   Initially, two shapes are created: a rectangle and a circle.
*   The function **rectangle = np.zeros((200, 200), np.uint8)** creates an array of zeroes, with dimensions of 200\*200 (any other dimensions may be inputted) and data type np.unit8 (unsingned integer of 8bits).
*   **cv2.rectangle(rectangle, (20, 20), (180, 180), 255, -1):** The rectangle is created using the built-in function **cv2.rectangle.** The first input parameter is the “variable” (in this case, “rectangle”), the next inputs are the coordinates (X1,Y1) and (X2, Y2), followed by the color, which varies from 0 to 255, with 255 returning white and 0 returning black; the final parameter is the thickness.
*   The function **circle = np.zeros((200, 200), dtype = "uint8")** creates an array of zeroes with dimension of 200\*200 and data type unsigned integer of 8 bits.
*   **cv2.circle(circle, (100, 100), 100, 255, -1):** Similarly to the rectangle, the circle is created using the built-in function **cv2.circle**, which has the input parameters “variable name” (in this case, “circle”), “center of the circle location”, “radius”, “color” (0 to 255) and “thickness”.
*   Bitwise operations are performed on the resulting two images, rectangle and circle:
*   The “AND” operation is performed using the built-in function **cv2.bitwise\_and**; the “OR” operation is performed using the built-in function **cv2.bitwise\_or**; the “XOR” operation is performed using the built-in function **cv2.bitwise\_xor**; the “NOT” operation is performed with the built-in function **cv2.bitwise\_not**. All four functions use the input parameters of the two shapes (rectangle and circle).

## 5.5 Blurring and Sharpening Images

**Python Program:Blurring\_Sharpening.py**

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_5.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# Blurring images: Averaging, cv2.blur built-in function*

*\# Averaging: Convolving image with normalized box filter*

*\# Convolution: Mathematical operation on 2 functions which produces third function.*

*\# Normalized box filter having size 3 x 3 would be:*

*\# (1/9) \[\[1, 1, 1\]*,

*#                  \[1, 1, 1\]*,

*#                  \[1, 1, 1\]\]*

*blur = cv2.blur(image,(9,9)) # (9 x 9) filter is used*

*cv2.imshow('Blurred', blur)*

*cv2.waitKey(0)*

*\# Sharpening images: Emphasizes edges in an image*

*kernel = np.array(\[\[-1,-1,-1\]*,

          *\[-1,9,-1\]*,

          *\[-1,-1,-1\]\])*

*\# If we don’t normalize to 1, image will be brighter or darker, respectively*

 

*\# cv2.filter2D is the built-in function used for sharpening images*

*\# cv2.filter2D(image, ddepth, kernel)*

*sharpened = cv2.filter2D(image, -1, kernel)*

*\# ddepth = -1, sharpened images will have same depth as original image*

*cv2.imshow('Sharpened', sharpened)*

*cv2.waitKey(0)*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.11  Output of Python Program to Display Original Image.](images/fig5_11.jpg)

Figure  5.11  Output of Python Program to Display Original Image.

![Figure  5.12  Output of Python Program to Display Blurred Image.](images/fig5_12.jpg)

Figure  5.12  Output of Python Program to Display Blurred Image.

![Figure  5.13  Output of Python Program to Display Sharpened Image.](images/fig5_13.jpg)

Figure  5.13  Output of Python Program to Display Sharpened Image.

*   This program blurs and sharpens the image.
*   The built-in function **cv2.blur** blurs the image, using a concept called averaging. Averaging applies the mathematical process of convolution to the image with a normalized box filter. Convolution is a mathematical operation describing how one function may alter another to produce a third function.
*   For example, if you consider a normalized box filter with dimensions of 4\*4 (i.e., 4 rows and 4 columns, with each element equal to 1), the total value equals 16, so we will multiply it by 1/16. Here we used the read image and a (9\*9) normalized box filter as the input parameters.
*   The built-in function **cv2.filter2D** sharpens the image by emphasizing the edges. There are three input parameters required: first is the read image, second is the depth (if we input a depth of -1, the sharpened image will have the same depth as the original image) and the third variable is the kernel.

## 5.6 Thresholding – Binary Thresholding

**Python Program:Thresholding.py**

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_6.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# cv2.COLOR\_BGR2GRAY: Converts color(RGB) image to gray*

*\# BGR(bytes are reversed)*

*\# cv2.cvtColor: Converts image from one color space to another*

*gray = cv2.cvtColor(image, cv2.COLOR\_BGR2GRAY)*

*\# cv2.threshold built-in function which performs thresholding*

*\# cv2.threshold(image, threshold\_value, max\_value, threshold\_type)*

*ret,threshold = cv2.threshold(gray, 127, 255, cv2.THRESH\_BINARY)*

*cv2.imshow('Binary Thresholding', threshold)*

*cv2.waitKey(0)*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.14  Output of Python Program to Display Original Image.](images/fig5_14.jpg)

Figure  5.14  Output of Python Program to Display Original Image.

![Figure  5.15  Output of Python Program to Display Binary Threshold Image.](images/fig5_15.jpg)

Figure  5.15  Output of Python Program to Display Binary Threshold Image.

*   This program utilizes thresholding to convert a grayscale image into binary.
*   If there is a color image, it must first be converted into grayscale before applying thresholding, so it can be converted to binary.
*   To convert a color image to grayscale, we use the built-in function **cv2.cvtColor(image, cv2.COLOR\_BGR2GRAY)**.
*   “BGR2GRAY”, describes the conversion of the primary colors RGB (red, green, and blue) into gray, stated conversely as BGR (blue, green, red) because the bites are saved in reverse order.
*   The built-in function **cv2.Color** converts from one color space to another, i.e. from color to grayscale.
*   The built-in function **cv2.threshold** applies binary thresholding.
*   ***ret,threshold = cv2.threshold(gray, 127, 255, cv2.THRESH\_BINARY):*** This function converts the image from color to gray, utilizing the variable “gray” that we have saved after the BGR2GRAY conversion. Using the threshold value from 0 to 255 (based on 8 bits), we can modify the image brightness before using the thresholding type, **cv2.THRESH\_BINARY.**

## 5.7 Morphological Operations: Erosion and Dilation

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_7.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# np.ones returns an array, given shape and type, filled with ones*

*\# np.ones(shape, dtype)*

*kernel = np.ones((5,5), dtype = "uint8")*

*\# 5 x 5 is the dimension of the kernel*

*\# uint8: is an unsigned integer (0 to 255)*

 

*\# cv2.erode is the built-in function used for erosion*

*\# cv2.erode(image, kernel, iterations)*

*erosion = cv2.erode(image, kernel, iterations = 1)*

*cv2.imshow("Erosion", erosion)*

*cv2.waitKey(0)*

*\# cv2.dilate is the built-in function used for dilation*

*\# cv2.dilate(image, kernel, iterations)*

*dilation = cv2.dilate(image, kernel, iterations = 1)*

*cv2.imshow("Dilation", dilation)*

*cv2.waitKey(0)*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.16  Output of Python Program to Display Original Image.](images/fig5_16.jpg)

Figure  5.16  Output of Python Program to Display Original Image.

![Figure  5.17  Output of Python Program to Display Eroded Image.](images/fig5_17.jpg)

Figure  5.17  Output of Python Program to Display Eroded Image.

![Figure  5.18  Output of Python Program to Display Dilated Image.](images/fig5_18.jpg)

Figure  5.18  Output of Python Program to Display Dilated Image.

*   This program applies erosion, which removes pixels at the boundaries of objects in an image and dilation, which adds pixels to the boundaries of objects in an image.
*   **np.ones** returns an array of a given shape and type, consisting entirely of ones.
*   **np.ones(shape, dtype)**: Here we use the variable *"*kernel*"* and assign np.ones(5,5), with dimension of 5\*5, with format **np.ones((5,5), dtype = "uint8")**. uint8 is an unsigned integer of 8 bits.
*   With the built-in erosion function, **cv2.erode**, we use **cv2.erode(image, kernel, iterations = 1)** with the input parameters of the image, the kernel and the number of iterations.
*   With the built-in dilation function, cv2.dilate, the format is **cv2.dilate(image, kernel, iterations = 1)**, using the same inputs of image, kernel, and iterations.

## 5.8 Edge Detection Using Canny Edge Detector

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_8.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# cv2.Canny is the built-in function used to detect edges*

*\# cv2.Canny(image, threshold\_1, threshold\_2)*

*canny = cv2.Canny(image, 50, 200)*

*cv2.imshow('Canny Edge Detection', canny)*

*cv2.waitKey(0)*

*cv2. destroyAllWindows()*

**Output:**

![Figure  5.19  Output of Python Program to Display Original Image.](images/fig5_19.jpg)

Figure  5.19  Output of Python Program to Display Original Image.

![Figure  5.20  Output of Python Program to Demonstrate Canny Edge Detection.](images/fig5_20.jpg)

Figure  5.20  Output of Python Program to Demonstrate Canny Edge Detection.

*   This program detects edges within the image.
*   We use canny edge detector, generally considered the most powerful and efficient approach; it is therefore the most commonly used in many real-time applications.
*   We use the built-in function **cv2.Canny(image, 50, 200)**, which requires three input parameters: the image with which we are working, the lower-limit, threshold\_1 and the upper limit, threshold\_2.

## 5.9 Image Segmentation Using Contours

*\# Segmentation: Partitioning images into different regions*

*\# Contours: Lines or curves around the boundary of an object*

*import cv2*

*import numpy as np*

*image = cv2.imread('image\_9.jpg')*

*cv2.imshow("Original", image)*

*cv2.waitKey(0)*

*\# cv2.Canny is the built-in function used to detect edges*

*\# cv2.Canny(image, threshold\_1, threshold\_2)*

*canny = cv2.Canny(image, 50, 200)*

*cv2.imshow("Canny Edge Detection", canny)*

*cv2.waitKey(0)*

*\# cv2.findContours is the built-in function to find contours*

*\# cv2.findContours(canny, contour retrieval mode, contour approximation mode)*

*\# contour retrieval mode: cv2.RETR\_LIST (retrieves all contours)*

*\# contour approximation mode: cv2.CHAIN\_APPROX\_NONE (stores all boundary points)*

*contours,hierarchy=cv2.findContours(canny,cv2.RETR\_LIST,cv2.CHAIN\_APPROX\_NONE)*

*\# cv2.drawContours is the the built-in function to draw contours*

*\# cv2.drawContours(image, contours, index of contours, color, thickness*

*cv2.drawContours(image, contours, -1, (255,0,0), 10)*

*\# index of contours = -1 will draw all the contours*

*cv2.imshow("Contours", image)*

*cv2.waitKey()*

*cv2.destroyAllWindows()*

**Output:**

![Figure  5.21  Output of Python Program to Display Original Image.](images/fig5_21.jpg)

Figure  5.21  Output of Python Program to Display Original Image.

![Figure  5.22  Output of Python Program to Display Image Contours.](images/fig5_22.jpg)

Figure  5.22  Output of Python Program to Display Image Contours.

*   This program performs image segmentation, which partitions the image into different regions, using contours, which are the lines or curves around the boundary of an object.
*   We use canny edge detection to find the contours, with the built-in function. **cv2.findContours**.
*   **cv2.findContours(canny, contour retrieval mode, contour approximation mode):**
*   Contour retrieval mode: **cv2.RETR\_LIST** (retrieves all contours).
*   Contour approximation mode: **cv2.CHAIN\_APPROX\_NONE** (stores all boundary points).
*   **cv2.drawContours** is the built-in function to draw contours.
*   **cv2.drawContours(image, contours, index of contours, color, thickness):** inputting index of contours and a thickness of –1 draws all contours.

# [Bibliography](#toc.xhtml#fm-1)

\[1\].    Derek Molloy, *Exploring Raspberry Pi: Interfacing to the Real World with Embedded Linux*, Wiley Publication,United States, 2016.

\[2\].    Steven Lawrence Fernandes, *Raspberry Pi 3 Cookbook for Python Programmers: Unleash the Potential of Raspberry Pi 3 with Over 100 Recipes*, 3rd Edition, Packt Publications, United Kingdom, 2018.

\[3\].    Leonard Eddison, *Raspberry Pi: A Step by Step Guide for Beginners*, CreateSpace Independent Publishing Platform, 2018.

\[4\].    Claus Fuhrer, Jan Erik Solem and Olivier Verdier, *Scientific Computing with Python 3*, Packt Publications, United Kingdom, 2016.

\[5\].    Shrirang Ambaji Kulkarni, *Problem Solving and Python Programming*, yesdee Publications, India, 2019.

\[6\].    Andreas C. Müller and Sarah Guido, *Introduction to Machine Learning with Python: A Guide for Data Scientists*, 1st Edition, O’Reilly Publication, United States, 2016.

\[7\].    Sebastian Raschka, *Python Machine Learning*, Packt Publications, United Kingdom, 2015.

\[8\].    Peter Harrington, *Machine Learning in Action*, Manning Publication, 2012.

# [Index](#toc.xhtml#ind1)

Page numbers in *italics* refer to Figures, and page numbers in **bold** refer to Tables.

## A

Area interpolation, [128](#chapter05.xhtml#page_128)–[131](#chapter05.xhtml#page_131), [*130*](#chapter05.xhtml#page_130)

ARM (Advanced RISC Machines), [7](#chapter02.xhtml#page_7)

Arrays, *See also* [Matrices](#index1.xhtml#index_128)

attributes, [41](#chapter03.xhtml#page_41)–[42](#chapter03.xhtml#page_42), [**42**](#chapter03.xhtml#page_42), [*42*](#chapter03.xhtml#page_42)

concatenation, [47](#chapter03.xhtml#page_47)–[49](#chapter03.xhtml#page_49), [*47*](#chapter03.xhtml#page_47), [*48*](#chapter03.xhtml#page_48), [*49*](#chapter03.xhtml#page_49)

copying, [46](#chapter03.xhtml#page_46), [*46*](#chapter03.xhtml#page_46)

creating

with 0s, [38](#chapter03.xhtml#page_38)–[39](#chapter03.xhtml#page_39), [*39*](#chapter03.xhtml#page_39)

with 1s of Integar64 type, [41](#chapter03.xhtml#page_41), [*41*](#chapter03.xhtml#page_41)

from a Python list, [37](#chapter03.xhtml#page_37)–[38](#chapter03.xhtml#page_38), [*37*](#chapter03.xhtml#page_37), [*38*](#chapter03.xhtml#page_38)

with random values, [40](#chapter03.xhtml#page_40)–[41](#chapter03.xhtml#page_41), [*40*](#chapter03.xhtml#page_40), [*41*](#chapter03.xhtml#page_41)

with values 0 to, [9](#chapter02.xhtml#page_9), [39](#chapter03.xhtml#page_39), [*39*](#chapter03.xhtml#page_39)

indexing and access, [43](#chapter03.xhtml#page_43), [*43*](#chapter03.xhtml#page_43)

reshaping, [46](#chapter03.xhtml#page_46), [*47*](#chapter03.xhtml#page_47)

splitting, [49](#chapter03.xhtml#page_49)–[50](#chapter03.xhtml#page_50), [*49*](#chapter03.xhtml#page_49), [*50*](#chapter03.xhtml#page_50)

subarrays

1-Dimensional array, [44](#chapter03.xhtml#page_44), [*44*](#chapter03.xhtml#page_44)

2-Dimensional array, [45](#chapter03.xhtml#page_45)–[46](#chapter03.xhtml#page_46), [*45*](#chapter03.xhtml#page_45), [*46*](#chapter03.xhtml#page_46)

Artificial Neural Network *See* [Neural network MLP](#index1.xhtml#index_144)

Audio jack, [10](#chapter02.xhtml#page_10), [*11*](#chapter02.xhtml#page_11)

## B

Big data, [4](#chapter01.xhtml#page_4)

Binary thresholding images, [142](#chapter05.xhtml#page_142)–[144](#chapter05.xhtml#page_144), [*142*](#chapter05.xhtml#page_142), [*143*](#chapter05.xhtml#page_143)

Bitwise operations, [134](#chapter05.xhtml#page_134)–[139](#chapter05.xhtml#page_139), [*137*](#chapter05.xhtml#page_137), [*138*](#chapter05.xhtml#page_138)

BlueJ, [14](#chapter02.xhtml#page_14)

Bluetooth, [12](#chapter02.xhtml#page_12)

Blurring and sharpening images, [139](#chapter05.xhtml#page_139)–[141](#chapter05.xhtml#page_141), [*140*](#chapter05.xhtml#page_140), [*141*](#chapter05.xhtml#page_141)

Brightness adjustment, [131](#chapter05.xhtml#page_131)–[134](#chapter05.xhtml#page_134), [*132*](#chapter05.xhtml#page_132), [*133*](#chapter05.xhtml#page_133)

## C

Canny edge detection (images), [146](#chapter05.xhtml#page_146)–[148](#chapter05.xhtml#page_148), [*147*](#chapter05.xhtml#page_147)

Cholesky decomposition, [70](#chapter03.xhtml#page_70), [*71*](#chapter03.xhtml#page_71)

Classification in machine learning, [82](#chapter04.xhtml#page_82)–[83](#chapter04.xhtml#page_83)

metrics

confusion (error) matrix, [84](#chapter04.xhtml#page_84)–[85](#chapter04.xhtml#page_85), [*84*](#chapter04.xhtml#page_84), [95](#chapter04.xhtml#page_95)

k-fold cross-validation, [83](#chapter04.xhtml#page_83)

models, [91](#chapter04.xhtml#page_91)–[95](#chapter04.xhtml#page_95)

Confusion (error) matrix, [84](#chapter04.xhtml#page_84)–[85](#chapter04.xhtml#page_85), [*84*](#chapter04.xhtml#page_84), [95](#chapter04.xhtml#page_95)

Contours, image segmentation using, [148](#chapter05.xhtml#page_148)–[150](#chapter05.xhtml#page_150), [*149*](#chapter05.xhtml#page_149)

Correlation, [89](#chapter04.xhtml#page_89)

Covariance matrix, [89](#chapter04.xhtml#page_89)–[90](#chapter04.xhtml#page_90), [*89*](#chapter04.xhtml#page_89), [*90*](#chapter04.xhtml#page_90)

Cross-validation *See* [K-fold cross-validation](#index1.xhtml#index_91)

CSV (comma separated value) files, reading

Pandas, [63](#chapter03.xhtml#page_63), [*63*](#chapter03.xhtml#page_63)

Scikit-Learn, [85](#chapter04.xhtml#page_85), [*87*](#chapter04.xhtml#page_87), [91](#chapter04.xhtml#page_91)

SciPy, [71](#chapter03.xhtml#page_71)–[72](#chapter03.xhtml#page_72), [*71*](#chapter03.xhtml#page_71), [*72*](#chapter03.xhtml#page_72)

Cubic interpolation, [128](#chapter05.xhtml#page_128)–[131](#chapter05.xhtml#page_131), [*129*](#chapter05.xhtml#page_129)

## D

Data cleaning, [64](#chapter03.xhtml#page_64)–[66](#chapter03.xhtml#page_66), [*64*](#chapter03.xhtml#page_64), [*65*](#chapter03.xhtml#page_65), [*66*](#chapter03.xhtml#page_66)

Data visualization, *See also* [Matplotlib](#index1.xhtml#index_122)

histograms, [78](#chapter03.xhtml#page_78), [*78*](#chapter03.xhtml#page_78)

line plots, [*72*](#chapter03.xhtml#page_72), [73](#chapter03.xhtml#page_73)–[76](#chapter03.xhtml#page_76), [*73*](#chapter03.xhtml#page_73), [*74*](#chapter03.xhtml#page_74), [*75*](#chapter03.xhtml#page_75), [*76*](#chapter03.xhtml#page_76)

scatter plots, [77](#chapter03.xhtml#page_77), [*77*](#chapter03.xhtml#page_77)

DataFrame object (Pandas)

adding columns, [61](#chapter03.xhtml#page_61), [*62*](#chapter03.xhtml#page_62)

changing column names, [61](#chapter03.xhtml#page_61), [*62*](#chapter03.xhtml#page_62)

Column Functions, [58](#chapter03.xhtml#page_58)–[59](#chapter03.xhtml#page_59), [*59*](#chapter03.xhtml#page_59)

DataFrame information, [59](#chapter03.xhtml#page_59), [*60*](#chapter03.xhtml#page_60)

indexing and access, [55](#chapter03.xhtml#page_55)–[58](#chapter03.xhtml#page_58), [*56*](#chapter03.xhtml#page_56), [*57*](#chapter03.xhtml#page_57), [*58*](#chapter03.xhtml#page_58)

removing rows and columns, [60](#chapter03.xhtml#page_60), [*61*](#chapter03.xhtml#page_61)

as a tabular structure, [55](#chapter03.xhtml#page_55), [**55**](#chapter03.xhtml#page_55), [*55*](#chapter03.xhtml#page_55)

Debian (operating system), [14](#chapter02.xhtml#page_14), *See also* [Raspbian (operating system)](#index1.xhtml#index_220)

Decision trees *See* [Random forest model](#index1.xhtml#index_197)

Dictionaries (Python), [34](#chapter03.xhtml#page_34)–[35](#chapter03.xhtml#page_35), [54](#chapter03.xhtml#page_54), [*54*](#chapter03.xhtml#page_54)

Dilation and erosion of images, [144](#chapter05.xhtml#page_144)–[146](#chapter05.xhtml#page_146), [*145*](#chapter05.xhtml#page_145)

## E

Edge detection of images, [146](#chapter05.xhtml#page_146)–[148](#chapter05.xhtml#page_148), [*147*](#chapter05.xhtml#page_147)

Else in combination with while and for loop, [30](#chapter03.xhtml#page_30)–[31](#chapter03.xhtml#page_31), [*31*](#chapter03.xhtml#page_31)

Erosion and dilation of images, [144](#chapter05.xhtml#page_144)–[146](#chapter05.xhtml#page_146), [*145*](#chapter05.xhtml#page_145)

Error (confusion) matrix, [84](#chapter04.xhtml#page_84)–[85](#chapter04.xhtml#page_85), [*84*](#chapter04.xhtml#page_84), [95](#chapter04.xhtml#page_95)

Ethernet port, [12](#chapter02.xhtml#page_12), [*13*](#chapter02.xhtml#page_13)

## F

Farming and IoT, [17](#chapter02.xhtml#page_17)

For loop, [28](#chapter03.xhtml#page_28)–[29](#chapter03.xhtml#page_29), [*29*](#chapter03.xhtml#page_29), [*30*](#chapter03.xhtml#page_30)

## G

GPIO (general purpose input-output) pins, [8](#chapter02.xhtml#page_8)–[9](#chapter02.xhtml#page_9), [*9*](#chapter02.xhtml#page_9)

## H

HDMI (high definition multimedia interface) port, [10](#chapter02.xhtml#page_10), [*11*](#chapter02.xhtml#page_11)

Histograms, [78](#chapter03.xhtml#page_78), [*78*](#chapter03.xhtml#page_78)

## I

IF-ELSE statements, [25](#chapter03.xhtml#page_25)–[26](#chapter03.xhtml#page_26), [*26*](#chapter03.xhtml#page_26)

Image processing

applications, [125](#chapter05.xhtml#page_125)

bitwise operations, [134](#chapter05.xhtml#page_134)–[139](#chapter05.xhtml#page_139), [*137*](#chapter05.xhtml#page_137), [*138*](#chapter05.xhtml#page_138)

blurring and sharpening, [139](#chapter05.xhtml#page_139)–[141](#chapter05.xhtml#page_141), [*140*](#chapter05.xhtml#page_140), [*141*](#chapter05.xhtml#page_141)

brightness adjustment, [131](#chapter05.xhtml#page_131)–[134](#chapter05.xhtml#page_134), [*132*](#chapter05.xhtml#page_132), [*133*](#chapter05.xhtml#page_133)

edge detection, [146](#chapter05.xhtml#page_146)–[148](#chapter05.xhtml#page_148), [*147*](#chapter05.xhtml#page_147)

erosion and dilation, [144](#chapter05.xhtml#page_144)–[146](#chapter05.xhtml#page_146), [*145*](#chapter05.xhtml#page_145)

load, display and save an image, [126](#chapter05.xhtml#page_126)–[128](#chapter05.xhtml#page_128), [*127*](#chapter05.xhtml#page_127)

scaling, [128](#chapter05.xhtml#page_128)–[131](#chapter05.xhtml#page_131), [*129*](#chapter05.xhtml#page_129), [*130*](#chapter05.xhtml#page_130)

segmentation using contours, [148](#chapter05.xhtml#page_148)–[150](#chapter05.xhtml#page_150), [*149*](#chapter05.xhtml#page_149)

thresholding, [142](#chapter05.xhtml#page_142)–[144](#chapter05.xhtml#page_144), [*142*](#chapter05.xhtml#page_142), [*143*](#chapter05.xhtml#page_143)

Industrial IoT, [17](#chapter02.xhtml#page_17)

Internet of things (IoT), applications, [17](#chapter02.xhtml#page_17)

## K

K nearest neighbors (KNN) model, [115](#chapter04.xhtml#page_115)–[116](#chapter04.xhtml#page_116), [*115*](#chapter04.xhtml#page_115), [*116*](#chapter04.xhtml#page_116)

advantages and limitations, [116](#chapter04.xhtml#page_116)

example, [116](#chapter04.xhtml#page_116)–[118](#chapter04.xhtml#page_118), [*118*](#chapter04.xhtml#page_118)

model building, [92](#chapter04.xhtml#page_92)

model training, [94](#chapter04.xhtml#page_94)

K-fold cross-validation, [83](#chapter04.xhtml#page_83)

Keyboard, connecting to, [12](#chapter02.xhtml#page_12), [14](#chapter02.xhtml#page_14)–[16](#chapter02.xhtml#page_16), [*15*](#chapter02.xhtml#page_15), [*16*](#chapter02.xhtml#page_16)

## L

LibreELEC (operating system), [**15**](#chapter02.xhtml#page_15)

LibreOffice suite, [14](#chapter02.xhtml#page_14)

Linalg module, [69](#chapter03.xhtml#page_69)

Line plots, [*72*](#chapter03.xhtml#page_72), [73](#chapter03.xhtml#page_73)–[76](#chapter03.xhtml#page_76), [*73*](#chapter03.xhtml#page_73), [*74*](#chapter03.xhtml#page_74), [*75*](#chapter03.xhtml#page_75), [*76*](#chapter03.xhtml#page_76)

Linear discriminant analysis (LDA), [119](#chapter04.xhtml#page_119)–[120](#chapter04.xhtml#page_120)

advantages and limitations, [120](#chapter04.xhtml#page_120)

example, [120](#chapter04.xhtml#page_120)–[121](#chapter04.xhtml#page_121), [*121*](#chapter04.xhtml#page_121), [*122*](#chapter04.xhtml#page_122)

model building, [92](#chapter04.xhtml#page_92)

model training, [94](#chapter04.xhtml#page_94)

Linear interpolation, [128](#chapter05.xhtml#page_128)–[131](#chapter05.xhtml#page_131), [*130*](#chapter05.xhtml#page_130)

Lists (Python), [33](#chapter03.xhtml#page_33)–[34](#chapter03.xhtml#page_34), [*33*](#chapter03.xhtml#page_33)

Logistic regression in machine learning, [96](#chapter04.xhtml#page_96)–[97](#chapter04.xhtml#page_97)

example, [98](#chapter04.xhtml#page_98)–[99](#chapter04.xhtml#page_99), [*99*](#chapter04.xhtml#page_99), [*100*](#chapter04.xhtml#page_100)

model building, [91](#chapter04.xhtml#page_91)

model training, [93](#chapter04.xhtml#page_93)

sigmoid function, [97](#chapter04.xhtml#page_97), [*97*](#chapter04.xhtml#page_97)

types, [98](#chapter04.xhtml#page_98)

LXDE (Lightweight Desktop Environment), [14](#chapter02.xhtml#page_14)

## M

Machine learning

categories, [81](#chapter04.xhtml#page_81)–[82](#chapter04.xhtml#page_82), [*82*](#chapter04.xhtml#page_82)

classification *See* [Classification in machine learning](#index1.xhtml#index_30)

k nearest neighbors (KNN) model *See* [K nearest neighbors (KNN) model](#index1.xhtml#index_86)

linear discriminant analysis (LDA) *See* [Linear discriminant analysis (LDA)](#index1.xhtml#index_97)

Naive Bayes model *See* [Naive Bayes model](#index1.xhtml#index_139)

neural network *See* [Neural network MLP](#index1.xhtml#index_144)

random forest model *See* [Random forest model](#index1.xhtml#index_197)

regression *See* [Regression in machine learning](#index1.xhtml#index_221)

Scikit-Learn *See* [Scikit-Learn](#index1.xhtml#index_237)

support vector machine (SVM) *See* [Support vector machine (SVM)](#index1.xhtml#index_283)

Matplotlib

histograms, [78](#chapter03.xhtml#page_78), [*78*](#chapter03.xhtml#page_78)

installation, [73](#chapter03.xhtml#page_73), [*73*](#chapter03.xhtml#page_73)

introduction, [72](#chapter03.xhtml#page_72)–[73](#chapter03.xhtml#page_73)

line plots, [*72*](#chapter03.xhtml#page_72), [73](#chapter03.xhtml#page_73)–[76](#chapter03.xhtml#page_76), [*73*](#chapter03.xhtml#page_73), [*74*](#chapter03.xhtml#page_74), [*75*](#chapter03.xhtml#page_75), [*76*](#chapter03.xhtml#page_76)

scatter plots, [77](#chapter03.xhtml#page_77), [*77*](#chapter03.xhtml#page_77)

Matrices, *See also* [Arrays](#index1.xhtml#index_3)

Cholesky decomposition, [70](#chapter03.xhtml#page_70), [*71*](#chapter03.xhtml#page_71)

confusion (error) matrix, [84](#chapter04.xhtml#page_84)–[85](#chapter04.xhtml#page_85), [*84*](#chapter04.xhtml#page_84), [95](#chapter04.xhtml#page_95)

covariance matrix, [89](#chapter04.xhtml#page_89)–[90](#chapter04.xhtml#page_90), [*89*](#chapter04.xhtml#page_89), [*90*](#chapter04.xhtml#page_90)

inverse, [69](#chapter03.xhtml#page_69)–[70](#chapter03.xhtml#page_70), [*70*](#chapter03.xhtml#page_70)

sparsity and density, [67](#chapter03.xhtml#page_67)–[68](#chapter03.xhtml#page_68), [*68*](#chapter03.xhtml#page_68), [*69*](#chapter03.xhtml#page_69)

Micro USB slot, [10](#chapter02.xhtml#page_10), [*10*](#chapter02.xhtml#page_10)

Micro-SD card slot, [12](#chapter02.xhtml#page_12), [*13*](#chapter02.xhtml#page_13)

MLP (multi-layer perceptron) *See* [Neural network MLP](#index1.xhtml#index_144)

Monitor, connecting to, [10](#chapter02.xhtml#page_10), [14](#chapter02.xhtml#page_14)–[16](#chapter02.xhtml#page_16), [*15*](#chapter02.xhtml#page_15), [*16*](#chapter02.xhtml#page_16)

Mouse, connecting to, [12](#chapter02.xhtml#page_12), [14](#chapter02.xhtml#page_14)–[16](#chapter02.xhtml#page_16), [*15*](#chapter02.xhtml#page_15), [*16*](#chapter02.xhtml#page_16)

## N

Naive Bayes model, [100](#chapter04.xhtml#page_100)–[101](#chapter04.xhtml#page_101)

advantages and applications, [101](#chapter04.xhtml#page_101)

example, [101](#chapter04.xhtml#page_101)–[102](#chapter04.xhtml#page_102), [*103*](#chapter04.xhtml#page_103)

model building, [91](#chapter04.xhtml#page_91)

model training, [93](#chapter04.xhtml#page_93)

Neural network MLP, [103](#chapter04.xhtml#page_103)–[105](#chapter04.xhtml#page_105), [*104*](#chapter04.xhtml#page_104)

applications, [105](#chapter04.xhtml#page_105)

example, [105](#chapter04.xhtml#page_105)–[106](#chapter04.xhtml#page_106), [*107*](#chapter04.xhtml#page_107)

model building, [92](#chapter04.xhtml#page_92)

model training, [93](#chapter04.xhtml#page_93)

NOOBS (new out-of-box software), [14](#chapter02.xhtml#page_14)

NumPy (numerical python)

arrays *See* [Arrays](#index1.xhtml#index_3)

data types, [**38**](#chapter03.xhtml#page_38)

overview and usage, [36](#chapter03.xhtml#page_36), [*36*](#chapter03.xhtml#page_36)

## O

Operating system

installation, [14](#chapter02.xhtml#page_14)

LibreELEC, [**15**](#chapter02.xhtml#page_15)

Raspbian, [3](#chapter01.xhtml#page_3), [14](#chapter02.xhtml#page_14), [**15**](#chapter02.xhtml#page_15)

RISC OS, [**15**](#chapter02.xhtml#page_15)

Windows 10 IoT core, [**15**](#chapter02.xhtml#page_15)

## P

Pandas

data cleaning, [64](#chapter03.xhtml#page_64)–[66](#chapter03.xhtml#page_66), [*64*](#chapter03.xhtml#page_64), [*65*](#chapter03.xhtml#page_65), [*66*](#chapter03.xhtml#page_66)

DataFrame object *See* [DataFrame object (Pandas)](#index1.xhtml#index_50)

installation, [*51*](#chapter03.xhtml#page_51)

reading CSV files, [63](#chapter03.xhtml#page_63), [*63*](#chapter03.xhtml#page_63)

Series object *See* [Series object (Pandas)](#index1.xhtml#index_273)

Pearson correlation, [89](#chapter04.xhtml#page_89)

Peripherals, connecting to, [10](#chapter02.xhtml#page_10), [12](#chapter02.xhtml#page_12), [14](#chapter02.xhtml#page_14)–[16](#chapter02.xhtml#page_16), [*15*](#chapter02.xhtml#page_15), [*16*](#chapter02.xhtml#page_16)

Power supply, [10](#chapter02.xhtml#page_10)

Processor, [9](#chapter02.xhtml#page_9)–[10](#chapter02.xhtml#page_10)

Python, *See also* [Image processing](#index1.xhtml#index_73);, [Machine learning](#index1.xhtml#index_111)

comments, [22](#chapter03.xhtml#page_22), [*22*](#chapter03.xhtml#page_22)

conditional constructs, [25](#chapter03.xhtml#page_25)–[26](#chapter03.xhtml#page_26), [*26*](#chapter03.xhtml#page_26)

data types, [22](#chapter03.xhtml#page_22)–[23](#chapter03.xhtml#page_23), [**23**](#chapter03.xhtml#page_23), [*23*](#chapter03.xhtml#page_23), [*24*](#chapter03.xhtml#page_24)

dictionaries, [34](#chapter03.xhtml#page_34)–[35](#chapter03.xhtml#page_35), [54](#chapter03.xhtml#page_54), [*54*](#chapter03.xhtml#page_54)

keywords, [21](#chapter03.xhtml#page_21), [*21*](#chapter03.xhtml#page_21)

libraries, [**19**](#chapter03.xhtml#page_19)

Matplotlib *See* [Matplotlib](#index1.xhtml#index_122)

NumPy *See* [NumPy (numerical python)](#index1.xhtml#index_150)

Pandas *See* [Pandas](#index1.xhtml#index_160)

Scikit-Learn *See* [Scikit-Learn](#index1.xhtml#index_237)

SciPy *See* [SciPy](#index1.xhtml#index_266)

lists, [33](#chapter03.xhtml#page_33)–[34](#chapter03.xhtml#page_34), [*33*](#chapter03.xhtml#page_33)

looping constructs

else in combination with while and for loop, [30](#chapter03.xhtml#page_30)–[31](#chapter03.xhtml#page_31), [*31*](#chapter03.xhtml#page_31)

for loop, [28](#chapter03.xhtml#page_28)–[29](#chapter03.xhtml#page_29), [*29*](#chapter03.xhtml#page_29), [*30*](#chapter03.xhtml#page_30)

while loop, [27](#chapter03.xhtml#page_27)–[28](#chapter03.xhtml#page_28), [*28*](#chapter03.xhtml#page_28)

operator precedence and associativity, [24](#chapter03.xhtml#page_24)–[25](#chapter03.xhtml#page_25), [**24**](#chapter03.xhtml#page_24)

overview, [19](#chapter03.xhtml#page_19)

reading CSV files *See* [CSV (comma separated value) files, reading](#index1.xhtml#index_40)

strings, [32](#chapter03.xhtml#page_32)–[33](#chapter03.xhtml#page_33)

ternary operator, [27](#chapter03.xhtml#page_27), [*27*](#chapter03.xhtml#page_27)

tuples, [34](#chapter03.xhtml#page_34)

typical program, [*20*](#chapter03.xhtml#page_20), [21](#chapter03.xhtml#page_21)

user-defined functions, [35](#chapter03.xhtml#page_35), [*35*](#chapter03.xhtml#page_35)

variables, [21](#chapter03.xhtml#page_21)

## R

RAM, [8](#chapter02.xhtml#page_8), [9](#chapter02.xhtml#page_9)

Random forest model, [111](#chapter04.xhtml#page_111), [**111**](#chapter04.xhtml#page_111), [*112*](#chapter04.xhtml#page_112)

advantages and limitations, [111](#chapter04.xhtml#page_111)–[112](#chapter04.xhtml#page_112)

example, [112](#chapter04.xhtml#page_112)–[113](#chapter04.xhtml#page_113), [*114*](#chapter04.xhtml#page_114)

model building, [92](#chapter04.xhtml#page_92)

model training, [94](#chapter04.xhtml#page_94)

Raspberry Pi

alternatives/competitors, [**3**](#chapter01.xhtml#page_3)

components

audio jack, [10](#chapter02.xhtml#page_10), [*11*](#chapter02.xhtml#page_11)

Ethernet port, [12](#chapter02.xhtml#page_12), [*13*](#chapter02.xhtml#page_13)

GPIO (general purpose input-output) pins, [8](#chapter02.xhtml#page_8)–[9](#chapter02.xhtml#page_9), [*9*](#chapter02.xhtml#page_9)

HDMI (high definition multimedia interface) port, [10](#chapter02.xhtml#page_10), [*11*](#chapter02.xhtml#page_11)

Micro USB slot, [10](#chapter02.xhtml#page_10), [*10*](#chapter02.xhtml#page_10)

micro-SD card slot, [12](#chapter02.xhtml#page_12), [*13*](#chapter02.xhtml#page_13)

processor, [9](#chapter02.xhtml#page_9)–[10](#chapter02.xhtml#page_10)

RAM, [8](#chapter02.xhtml#page_8), [9](#chapter02.xhtml#page_9)

USB (universal serial bus) ports, [12](#chapter02.xhtml#page_12), [*12*](#chapter02.xhtml#page_12)

GUI, [14](#chapter02.xhtml#page_14)

Model, [3](#chapter01.xhtml#page_3), [7](#chapter02.xhtml#page_7), [8](#chapter02.xhtml#page_8), [*9*](#chapter02.xhtml#page_9)

models (timeline), [7](#chapter02.xhtml#page_7)–[8](#chapter02.xhtml#page_8)

operating system *See* [Operating system](#index1.xhtml#index_154)

philosophy, [2](#chapter01.xhtml#page_2)

power supply, [10](#chapter02.xhtml#page_10)

Raspbian (operating system), [3](#chapter01.xhtml#page_3), [14](#chapter02.xhtml#page_14), [**15**](#chapter02.xhtml#page_15)

Regression in machine learning, [85](#chapter04.xhtml#page_85), *See also* [Logistic regression in machine learning](#index1.xhtml#index_104)

Reinforcement learning, [82](#chapter04.xhtml#page_82), [*82*](#chapter04.xhtml#page_82)

Resizing images *See* [Scaling images](#index1.xhtml#index_235)

RISC (Reduced Instruction Set Computers) architecture, [7](#chapter02.xhtml#page_7)

RISC OS, [**15**](#chapter02.xhtml#page_15)

ROC (Receiver Operating Characteristic) curve, [96](#chapter04.xhtml#page_96)

k nearest neighbors (KNN) model, [*118*](#chapter04.xhtml#page_118)

linear discrminant analysis (LDA), [*122*](#chapter04.xhtml#page_122)

logistic regression, [*100*](#chapter04.xhtml#page_100)

Naive Bayes model, [*103*](#chapter04.xhtml#page_103)

neural network MLP, [*107*](#chapter04.xhtml#page_107)

random forest model, [*114*](#chapter04.xhtml#page_114)

support vector machine (SVM), [*110*](#chapter04.xhtml#page_110)

Router, connecting to, [12](#chapter02.xhtml#page_12)

## S

Scaling images, [128](#chapter05.xhtml#page_128)–[131](#chapter05.xhtml#page_131), [*129*](#chapter05.xhtml#page_129), [*130*](#chapter05.xhtml#page_130)

Scatter plots *See* [Matplotlib: scatter plots](#index1.xhtml#index_122)

Scikit-Learn

confusion (error) matrix implementation, [95](#chapter04.xhtml#page_95)

example dataset, [85](#chapter04.xhtml#page_85), [**86**](#chapter04.xhtml#page_86)

example dataset analysis, [87](#chapter04.xhtml#page_87)–[88](#chapter04.xhtml#page_88), [*87*](#chapter04.xhtml#page_87)

attributes, [**86**](#chapter04.xhtml#page_86), [88](#chapter04.xhtml#page_88)–[89](#chapter04.xhtml#page_89), [*88*](#chapter04.xhtml#page_88)

correlation, [89](#chapter04.xhtml#page_89)

covariance matrix, [89](#chapter04.xhtml#page_89)–[90](#chapter04.xhtml#page_90), [*89*](#chapter04.xhtml#page_89), [*90*](#chapter04.xhtml#page_90)

k nearest neighbors (KNN) model, [116](#chapter04.xhtml#page_116)–[118](#chapter04.xhtml#page_118), [*118*](#chapter04.xhtml#page_118)

linear discriminant analysis (LDA), [120](#chapter04.xhtml#page_120)–[121](#chapter04.xhtml#page_121), [*121*](#chapter04.xhtml#page_121), [*122*](#chapter04.xhtml#page_122)

logistic regression, [98](#chapter04.xhtml#page_98)–[99](#chapter04.xhtml#page_99), [*99*](#chapter04.xhtml#page_99), [*100*](#chapter04.xhtml#page_100)

Naive Bayes model, [101](#chapter04.xhtml#page_101)–[102](#chapter04.xhtml#page_102), [*103*](#chapter04.xhtml#page_103)

neural network MLP, [105](#chapter04.xhtml#page_105)–[106](#chapter04.xhtml#page_106), [*107*](#chapter04.xhtml#page_107)

Pearson correlation, [89](#chapter04.xhtml#page_89)

random forest model, [112](#chapter04.xhtml#page_112)–[113](#chapter04.xhtml#page_113), [*114*](#chapter04.xhtml#page_114)

support vector machine (SVM), [109](#chapter04.xhtml#page_109)–[110](#chapter04.xhtml#page_110), [*110*](#chapter04.xhtml#page_110)

installation, [90](#chapter04.xhtml#page_90)–[91](#chapter04.xhtml#page_91), [*90*](#chapter04.xhtml#page_90)

k-fold classification accuracy, [95](#chapter04.xhtml#page_95)

KNN model *See* [K nearest neighbors (KNN) model](#index1.xhtml#index_86)

LDA *See* [Linear discriminant analysis (LDA)](#index1.xhtml#index_97)

learning model building, [91](#chapter04.xhtml#page_91)

learning model training, [92](#chapter04.xhtml#page_92)–[95](#chapter04.xhtml#page_95)

logistic regression *See* [Logistic regression in machine learning](#index1.xhtml#index_104)

Naive Bayes model *See* [Naive Bayes model](#index1.xhtml#index_139)

neural network *See* [Neural network MLP](#index1.xhtml#index_144)

random forest model *See* [Random forest model](#index1.xhtml#index_197)

reading CSV files, [85](#chapter04.xhtml#page_85), [*87*](#chapter04.xhtml#page_87), [91](#chapter04.xhtml#page_91)

ROC curve *See* [ROC (Receiver Operating Characteristic) curve](#index1.xhtml#index_226)

splitting data into training and testing subsets, [91](#chapter04.xhtml#page_91)

SVM *See* [Support vector machine (SVM)](#index1.xhtml#index_283)

SciPy

installation, [67](#chapter03.xhtml#page_67)

linalg module, [69](#chapter03.xhtml#page_69)

matrices *See* [Matrices](#index1.xhtml#index_128)

reading CSV files, [71](#chapter03.xhtml#page_71)–[72](#chapter03.xhtml#page_72), [*71*](#chapter03.xhtml#page_71), [*72*](#chapter03.xhtml#page_72)

Scratch, [14](#chapter02.xhtml#page_14)

Segmentation of images using contours, [148](#chapter05.xhtml#page_148)–[150](#chapter05.xhtml#page_150), [*149*](#chapter05.xhtml#page_149)

Series object (Pandas), [*51*](#chapter03.xhtml#page_51)

data cleaning, [64](#chapter03.xhtml#page_64)–[66](#chapter03.xhtml#page_66), [*64*](#chapter03.xhtml#page_64), [*65*](#chapter03.xhtml#page_65), [*66*](#chapter03.xhtml#page_66)

indexing and access, [53](#chapter03.xhtml#page_53)–[54](#chapter03.xhtml#page_54), [*54*](#chapter03.xhtml#page_54)

as Python dictionary, [54](#chapter03.xhtml#page_54), [*54*](#chapter03.xhtml#page_54)

subarrays, [53](#chapter03.xhtml#page_53), [*53*](#chapter03.xhtml#page_53)

for upcast, [52](#chapter03.xhtml#page_52), [*52*](#chapter03.xhtml#page_52)

Sharpening and blurring images, [139](#chapter05.xhtml#page_139)–[141](#chapter05.xhtml#page_141), [*140*](#chapter05.xhtml#page_140), [*141*](#chapter05.xhtml#page_141)

Smart homes, [17](#chapter02.xhtml#page_17)

Strings (Python), [32](#chapter03.xhtml#page_32)–[33](#chapter03.xhtml#page_33)

Supervised learning, [81](#chapter04.xhtml#page_81), [*82*](#chapter04.xhtml#page_82), *See also* [Machine learning](#index1.xhtml#index_111)

Support vector machine (SVM), [107](#chapter04.xhtml#page_107)–[108](#chapter04.xhtml#page_108)

applications, [108](#chapter04.xhtml#page_108)

example, [109](#chapter04.xhtml#page_109)–[110](#chapter04.xhtml#page_110), [*110*](#chapter04.xhtml#page_110)

model building, [92](#chapter04.xhtml#page_92)

model training, [93](#chapter04.xhtml#page_93)

## T

Thresholding images, [142](#chapter05.xhtml#page_142)–[144](#chapter05.xhtml#page_144), [*142*](#chapter05.xhtml#page_142), [*143*](#chapter05.xhtml#page_143)

Transformative transdisciplinary perspective, [2](#chapter01.xhtml#page_2)

Tuples (Python), [34](#chapter03.xhtml#page_34)

## U

Unsupervised learning, [81](#chapter04.xhtml#page_81)–[82](#chapter04.xhtml#page_82), [*82*](#chapter04.xhtml#page_82)

USB ports, [12](#chapter02.xhtml#page_12), [*12*](#chapter02.xhtml#page_12)

USB slot, [10](#chapter02.xhtml#page_10), [*10*](#chapter02.xhtml#page_10)

User-defined functions (Python), [35](#chapter03.xhtml#page_35), [*35*](#chapter03.xhtml#page_35)

## W

Wearable devices, [17](#chapter02.xhtml#page_17)

While loop, [27](#chapter03.xhtml#page_27)–[28](#chapter03.xhtml#page_28), [*28*](#chapter03.xhtml#page_28)

Wi-Fi, [12](#chapter02.xhtml#page_12)

Windows 10 IoT core (operating system), [**15**](#chapter02.xhtml#page_15)