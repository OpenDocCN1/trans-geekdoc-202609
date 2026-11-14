
### For Further Reading

### References

## Chapter 16 Next-Generation Web Application Exploitation

### The Evolution of Cross-Site Scripting (XSS)
### Setting Up the Environment
- Lab 16-1: XSS Refresher
- Lab 16-2: XSS Evasion from Internet Wisdom
- Lab 16-3: Changing Application Logic with XSS
- Lab 16-4: Using the DOM for XSS

### Framework Vulnerabilities
### Setting Up the Environment
- Lab 16-5: Exploiting CVE-2017-5638
- Lab 16-6: Exploiting CVE-2017-9805

### Padding Oracle Attacks
- Lab 16-7: Changing Data with the Padding Oracle Attack

### Summary
### For Further Reading
### References

## Chapter 17 Next-Generation Patch Exploitation

### Introduction to Binary Diffing
### Application Diffing
### Patch Diffing

### Binary Diffing Tools
- BinDiff
- turbodiff
- Lab 17-1: Our First Diff

### Patch Management Process
### Microsoft Patch Tuesday

### Obtaining and Extracting Microsoft Patches
- Lab 17-2: Diffing MS17-010

### Patch Diffing for Exploitation
### DLL Side-Loading Bugs
- Lab 17-3: Diffing MS16-009

### Summary
### For Further Reading
### References

## Part IV Advanced Malware Analysis

## Chapter 18 Dissecting Mobile Malware

### The Android Platform
- Android Application Package
- Application Manifest
- Analyzing DEX
- Java Decompilation
- DEX Decompilation
- DEX Disassembling
- Example 18-1: Running APK in Emulator
- Malware Analysis

### The iOS Platform
- iOS Security
- iOS Applications
- Summary
- For Further Reading
- References

## Chapter 19 Dissecting Ransomware

### The Beginnings of Ransomware
### Options for Paying the Ransom
### Dissecting Ransomlock
- Example 19-1: Dynamic Analysis
- Example 19-2: Static Analysis
### WannaCry
- Example 19-3: Analyzing WannaCry Ransomware
### Summary
### For Further Reading

## Chapter 20 ATM Malware

### ATM Overview
### XFS Overview
### XFS Architecture
### XFS Manager
### ATM Malware Analysis
### Types of ATM Malware
### Techniques for Installing Malware on ATMs
### Techniques for Dissecting the Malware
### ATM Malware Countermeasures
### Summary
### For Further Reading
### References

## Chapter 21 Deception: Next-Generation Honeypots

### Brief History of Deception
### Honeypots as a Form of Deception
### Deployment Considerations
### Setting Up a Virtual Machine
### Open Source Honeypots
- Lab 21-1: Dionaea
- Lab 21-2: ConPot
- Lab 21-3: Cowrie
- Lab 21-4: T-Pot
### Commercial Alternative: TrapX
### Summary
### For Further Reading
### References

## Part V Internet of Things

## Chapter 22 Internet of Things to Be Hacked

### Internet of Things (IoT)
### Types of Connected Things
### Wireless Protocols
### Communication Protocols
### Security Concerns
### Shodan IoT Search Engine
### Web Interface
### Shodan Command-Line Interface
- Lab 22-1: Using the Shodan Command Line
### Shodan API
- Lab 22-2: Testing the Shodan API
- Lab 22-3: Playing with MQTT
### Implications of This Unauthenticated Access to MQTT
### IoT Worms: It Was a Matter of Time
- Lab 22-4: Mirai Lives
### Prevention
### Summary
### For Further Reading
### References

## Chapter 23 Dissecting Embedded Devices

### CPU
### Microprocessor
### Microcontrollers
### System on Chip (SoC)
### Common Processor Architectures
### Serial Interfaces
### UART
### SPI
### I²C
### Debug Interfaces
### JTAG
### SWD (Serial Wire Debug)
### Software
### Bootloader
### No Operating System
### Real-Time Operating System
### General Operating System
### Summary
### For Further Reading
### References

## Chapter 24 Exploiting Embedded Devices

### Static Analysis of Vulnerabilities in Embedded Devices
- Lab 24-1: Analyzing the Update Package
- Lab 24-2: Performing Vulnerability Analysis

### Dynamic Analysis with Hardware

### The Test Environment Setup
- Ettercap

### Dynamic Analysis with Emulation

### FIRMADYNE
- Lab 24-3: Setting Up FIRMADYNE
- Lab 24-4: Emulating Firmware
- Lab 24-5: Exploiting Firmware

### Summary
### Further Reading
### References

## Chapter 25 Fighting IoT Malware

### Physical Access to the Device

### RS-232 Overview

### RS-232 Pinout

- Exercise 25-1: Troubleshooting a Medical Device’s RS-232 Port

### Setting Up the Threat Lab

### ARM and MIPS Overview

- Lab 25-1: Setting Up Systems with QEMU

### Dynamic Analysis of IoT Malware

- Lab 25-2: IoT Malware Dynamic Analysis

### Platform for Architecture-Neutral Dynamic Analysis (PANDA)

### BeagleBone Black Board

### Reverse Engineering IoT Malware

### Crash-Course ARM/MIPS Instruction Set

- Lab 25-3: IDA Pro Remote Debugging and Reversing

- IoT Malware Reversing Exercise

### Summary
### For Further Reading
### Index

## PREFACE

This book has been developed by and for security professionals who are dedicated to working in an ethical and responsible manner to improve the overall security posture of individuals, corporations, and nations.

## ACKNOWLEDGMENTS

Each of the authors would like to thank the staff at McGraw-Hill Education. In particular, we would like to thank Wendy Rinaldi and Claire Yee. You really went above and beyond, keeping us on track and greatly helping us through the process. Your highest levels of professionalism and tireless dedication to this project were truly noteworthy and bring great credit to your publisher. Thanks.

Allen Harper would like to thank his wonderful wife Corann and beautiful daughters Haley and Madison for their support and understanding as I chased yet another dream.

It is wonderful to see our family and each of us individually grow stronger in Christ each year. Madison and Haley, I love you both dearly and am proud of the young ladies you have become. In addition, I would like to thank the members of my former and current employer. To the friends at Tangible Security, I am thankful for your impact on my life—you made me better. To my brothers and sisters in Christ at Liberty University, I am excited for the years ahead as we labor together and aim to train Champions for Christ!

Daniel Regalado le gustaría agradecer primero a Dios por la bendición de estar vivo, a su esposa Diana por aguantarlo, por siempre motivarlo, por festejar cada uno de sus triunfos como si fueran de ella, por ser tan bella y atlética, te amo! A sus hijos Fercho y Andrick por ser la luz de la casa y su motor de cada dia y finalmente pero no menos importante a la Familia Regalado Arias: Fernando, Adelina, Susana Erwin y Belem, sin ellos, sus triunfos no sabrían igual, los amo! Y a su Papa Fernando, hasta el ultimo dia que respire, viviré con la esperanza de volver a abrazarte. Cape, Cone, Rober, hermandad para siempre!

Branko Spasojevic would like to thank his family—Sanja, Sandra, Ana Marija, Magdalena, Ilinka, Jevrem, Olga, Dragisa, Marija, and Branislav—for all the support and knowledge they passed on.

Another big thanks goes to all my friends and colleagues who make work and play fun. Some people who deserve special mention are Ante Gulam, Antonio, Cedric, Clement, Domagoj, Drazen, Goran, Keith, Luka, Leon, Matko, Santiago, Tory, and everyone in TAG, Zynamics, D&R, and Orca.

Ryan Linn would like to thank Heather for her support, encouragement, and advice as well as his family and friends for their support and for putting up with the long hours and infrequent communication while the book was coming together.

Thanks also go out to Ed Skoudis for pushing me to do awesome things, and to HD, Egypt, Nate, Shawn, and all the other friends and family who have offered code assistance, guidance, and support when I’ve needed it the most.

Stephen Sims would like to thank his wife LeAnne and daughter Audrey for their ongoing support with the time needed to research, write, work, teach, and travel. He would also like to thank his parents, George and Mary, and sister, Lisa, for their support from afar. Finally, a special thanks to all of the brilliant security researchers who contribute so much to the community with publications, lectures, and tools.

Chris Eagle would like to thank his wife Kristen for being the rock that allows him to do all of the things he does. None of it would be possible without her continued support.

Linda Martinez would like to thank her mom and dad for being truly delightful people and always setting a great example to follow. Linda would also like to thank her daughter Elysia for the years of encouragement that allowed her to pursue her passions.

A big thanks to my friends and some of the brightest minds in the industry—Allen, Zack, Rob, Ryan, Bill, and Shon, may she rest in peace.

Michael Baucom would like to thank his wife, Bridget, and daughter, Tiernan, for their sacrifices and support in allowing him to pursue his professional goals.

I’d also like to thank my parents for your love, support, and instilling in me the work ethic that has carried me to this point. Additionally, I’d like to thank the Marine Corps for giving me the courage and confidence to understand that all things are possible. Finally, I’d like to thank my brother in Christ, long-time friend, and colleague, Allen Harper. Nothing can be accomplished without a great team.

We, the authors, would also like to collectively thank Hex-Rays for the generous use of their tool, IDA Pro.
