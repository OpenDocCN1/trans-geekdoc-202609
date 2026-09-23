   

Arduino

 

Mastering Arduino - The Complete Beginner’s Guide To Arduino

 

Steve Gold

Table Of Contents

 

Book 1

Arduino - Getting Started With Arduino: The Ultimate Beginner’s Guide

 

Book 2

Arduino - Taking The Next Step With Arduino: The Ultimate Beginner’s Guide - Part 2

© Copyright 2017 by Eddington Publishing - All rights reserved.

 

This document is geared towards providing exact and reliable information in regards to the topic and issue covered. The publication is sold with the idea that the publisher is not required to render accounting, officially permitted, or otherwise, qualified services. If advice is necessary, legal or professional, a practiced individual in the profession should be ordered.

\- From a Declaration of Principles which was accepted and approved equally by a Committee of the American Bar Association and a Committee of Publishers and Associations.

In no way is it legal to reproduce, duplicate, or transmit any part of this document in either electronic means or in printed format. Recording of this publication is strictly prohibited and any storage of this document is not allowed unless with written permission from the publisher. All rights reserved.

The information provided herein is stated to be truthful and consistent, in that any liability, in terms of inattention or otherwise, by any usage or abuse of any policies, processes, or directions contained within is the solitary and utter responsibility of the recipient reader. Under no circumstances will any legal responsibility or blame be held against the publisher for any reparation, damages, or monetary loss due to the information herein, either directly or indirectly.

Respective authors own all copyrights not held by the publisher.

The information herein is offered for informational purposes solely, and is universal as so. The presentation of the information is without contract or any type of guarantee assurance.

The trademarks that are used are without any consent, and the publication of the trademark is without permission or backing by the trademark owner. All trademarks and brands within this book are for clarifying purposes only and are the owned by the owners themselves, not affiliated with this document.

Book One Starts Here￼

![Arduino Thumbnail.JPG](images/00001.jpeg)

 

Arduino

 

Getting Started With Arduino: The Ultimate Beginner’s Guide

 

Steve Gold

Introduction

 

If are you fascinated by the simplest of technology, and often wonder about the inner workings of the electronic devices that are so ubiquitous in our daily lives, you are likely to find joy in experimenting and tinkering with Arduino.

 

At the core of everything that comes to life at a flick of a switch – the Christmas tree lights that blink in multiple colors, the apps that open up on a touch screen device, and the microwave oven that heats up your food etc. – is a micro-controller, programmed to perform certain feats when activated. Arduino is an open-source platform that consists of a micro-controller and programming software. Unlike most platforms, Arduino was geared towards non-electricians who want to get creative with electronics, while also being flexible enough to accommodate engineering experts. It is meant to be accessible, low cost and easy to learn, regardless of your previous knowledge in electronics and programming.

 

This guide will not make you an Arduino expert overnight – in fact, nothing can. What you will learn from this book however are the fundamentals of this amazingly versatile platform, and you’ll also have the opportunity to get a firsthand feel for what it can do. You will be guided through the key features of an Arduino circuit board, technical requirements to begin working, how to kick-start your first Arduino, important lingo you’ll need to know in order to get by, and how to proceed further in order to keep building upon what you have learnt.

 

The information here is intended for the absolute beginner in electronics, circuitry and programming. If you have always wanted to learn how to build cool stuff with electronics yet are completely at loss as to how to get started, you now have all the information you’ll need at your fingertips in order to make your entry into the exciting world of Arduino. The rest is up to you!

 

P.S. As a token of my appreciation, I have included a free gift for you; no catch, no charge. Simply [click here](http://eepurl.com/bMxlLr) for instant access.

© Copyright 2015 by Eddington Publishing - All rights reserved.

 

This document is geared towards providing exact and reliable information in regards to the topic and issue covered. The publication is sold with the idea that the publisher is not required to render accounting, officially permitted, or otherwise, qualified services. If advice is necessary, legal or professional, a practiced individual in the profession should be ordered.

\- From a Declaration of Principles which was accepted and approved equally by a Committee of the American Bar Association and a Committee of Publishers and Associations.

In no way is it legal to reproduce, duplicate, or transmit any part of this document in either electronic means or in printed format. Recording of this publication is strictly prohibited and any storage of this document is not allowed unless with written permission from the publisher. All rights reserved.

The information provided herein is stated to be truthful and consistent, in that any liability, in terms of inattention or otherwise, by any usage or abuse of any policies, processes, or directions contained within is the solitary and utter responsibility of the recipient reader. Under no circumstances will any legal responsibility or blame be held against the publisher for any reparation, damages, or monetary loss due to the information herein, either directly or indirectly.

Respective authors own all copyrights not held by the publisher.

The information herein is offered for informational purposes solely, and is universal as so. The presentation of the information is without contract or any type of guarantee assurance.

The trademarks that are used are without any consent, and the publication of the trademark is without permission or backing by the trademark owner. All trademarks and brands within this book are for clarifying purposes only and are the owned by the owners themselves, not affiliated with this document.

Table of contents

 

Introduction

Chapter 1: Understanding Arduino

Chapter 2: How To Get Started with Arduino

Chapter 3: Taking the first step!

Chapter 4: Arduino Survival Lingo

Chapter 5: Essential Resources & Further Reading

Conclusion

A message from the author, Steve Gold

Chapter 1

 

Understanding Arduino

 

In 2005, the Ivrea Interaction Design Institute in Italy started a project of creating an open-source platform to be used for building various electronic projects, known as Arduino. Originally geared towards students with little to no background in electronics or computer programming, the platform eventually gained worldwide popularity due to its accessibility and beginner-friendly features.

 

Over the years since its inception, Arduino has garnered the attention and enthusiasm of hobbyists, artists, programmers, students and even hackers from all levels of experience. Being an open-source platform, it continues to grow with contributions from a diverse community of users that keep pushing the limits of its capabilities. In fact, Arduino has been the backbone behind thousands of projects and applications, from everyday objects to complex scientific equipment.

 

The Arduino platform consists of two components:

 

1.  The hardware – A physical programmable circuit board, also known as the microcontroller. There are different types of Arduino boards (more on this in Chapter 2).

 

1.  The Software – The Integrated Development Environment (IDE) that runs on the computer, used for writing and uploading programming codes to the physical board.

 

 

Why Go Arduino?

 

Practically anyone can use Arduino. Experts are sure to have fun with building projects and sharing ideas with other users at online communities. For those with no experience with circuits and micro-controller programming, the platform is excellent for learning and experimenting. However, it is recommended that before exploring the wonders of Arduino, you should at least have a firm understanding of these fundamental concepts:

 

1.  The basics of electricity and circuitry

 

1.  Voltage, current, resistance and Ohm’s law

 

1.  Polarity

 

1.  Integrated circuits (ICs)

 

1.  Digital logic

 

1.  Analog versus Digital

 

1.  Basic computer programming

 

 

What makes Arduino a favorite among amateurs and experts alike is that, compared to other platforms and systems, it simplifies the process of working with micro-controllers. For a start, loading new codes to the board can simply be done with a USB cable, unlike previous programmable circuit boards where a separate piece of hardware has to be used. It is also a plus point that Arduino boards are relatively inexpensive compared to other micro-controller platforms, with some pre-assembled modules costing less than $50. If those perks are not enough, here are some more reasons why Arduino is the platform to go for:

 

1.  Cross-platform – Arduino’s IDE runs on Windows, Macintosh OSX, and Linux operating systems, whereas most micro-controller systems are only compatible with Windows.

 

1.  Simple programming environment – The Arduino IDE uses a simplified version of C++, making it easier for beginner to learn how to program, yet flexible enough for advance users to get creative and ambitious with.

 

1.  Open source and extensible hardware – Arduino board plans are published under a Creative Common license, allowing circuit designers to create their own version of the module, extending it and improving upon it.

 

1.  Open source and extensible software – The Arduino IDE is published as open source tools that experienced programmers can expand on, through C++ libraries. You can also learn the AVR-C programming language from Arduino, just as you can also add AVR-C code directly into Arduino programs.

 

1.  Backed by a supportive community – If you are absolutely new to the platform and don’t know where to begin, there is a wealth of information to be found online due to the popularity of Arduino. You will never run out of resources to learn from, and you can even find pre-coded projects to work on right away (See Chapter 5 for Arduino resources).

 

 

What can Arduino do for You?

 

Arduino was designed with the creative and innovative in mind, regardless of experience level. Artists, designers, electricians, engineers, programmers and science enthusiasts can use it to create interactive objects and environments. Among the things Arduino can interact with include motors, speakers, LEDs, GPS units, cameras, TVs, smart-phones and even the internet.

 

With Arduino, one can build low cost scientific instruments, do programming for robotics, build interactive prototypes of architectural designs and create installations for musical instruments to experiment with sound, build new video game hardware – and this is just the tip of the iceberg! So, whether your project entails building a robot, a heating blanket, a festive lighting display or a fortune-telling machine, Arduino can serve as a base for your electronic projects.

Before You Continue...

 

As a token of appreciation, I’ve included a great, surprise for you

 

Claim Your Exclusive Free Gift!

 

For a limited time I’ve included access to a FREE book which is ONLY available to my readers and can’t be found anywhere else. Don’t miss your chance to get it, along with exclusive access to more free books and exclusive discounts in the future! Simply follow the link below for instant access:

 

[\=>Click HERE to learn more! <=](http://eepurl.com/bMxlLr)

 

Enjoy!

Steve Gold

Chapter 2

 

Getting Started with Arduino

 

As the Arduino platform is ever expanding, continuous learning is necessary as there is always something new to discover. What you will learn in this chapter is the bare minimum you need to know in order to get your feet wet. You will be introduced to the basic Arduino components, what you will need and how to set them up. Obviously, you are going to need the two essentials: an Arduino board and the software installed (available free for download on the official Arduino website).

 

 

Anatomy of an Arduino Board

 

Before you start shopping around for hardware, you need to know some basics about Arduino boards and their features. There are several types of Arduino boards available for purchase, each with different capabilities. Although they may differ in look and capabilities, you will find most boards have the majority of these components in common:

 

1.  USB and Barrel Jack – Every board will have a means for it to be connected to a power source. Almost all Arduino boards come with USB connection, since this is how you will be uploading codes onto them. You can also connect to a wall power supply via the barrel jack. 

 

2\. Pins – The boards’ pins are where you construct circuits by connecting wires. There are several types of pins on Arduino boards, each meant for a specific functions. Here is what you will normally find:

 

 

1.  GND: Short for Ground, these pins are used to ground your circuit.

 

1.  5V and 3.3V: These pins supply 5 Volts and 3.3 Volts of power, respectively.

 

1.  Analog: You can identify this row of pins under the ‘Analog In’ label. They are used for reading signals from analog sensors, and convert those signals into digital values.

 

1.  Digital: Across from the analog pins, under the ‘Digital’ label, are the pins to be used for digital input and output. For example, telling when a button is pressed (input), so that an LED lights up (output).

 

1.  PWM: In a lot of Arduino boards, there is the label (PWM~) next to ‘Digital’. It means that the pins can be used as normal digital pins, and also for a type of signal called Pulse-Width Modulation (see the glossary of terms in Chapter 4 for explanation).

 

1.  AREF: A short form for Analog Reference, this is the pin which can be used to set an external voltage as the upper limit for the analog pins (between 0 and 5 Volts), although it is mostly left alone.

 

3\. Reset button – This button is self-explanatory; pushing it will connect the rest pin to ground, and restart any code loaded onto the board. This is useful for testing your programmed codes multiple times. It does not, however, functions to reset everything to a clean slate and wipe away any problems.

 

4\. Power LED Indicator – This is a tiny LED that can be identified with the word ‘ON’ next to it. It will light up when you plug the board into a power source, and if it doesn’t, it means you have to re-check your circuit because something is wrong.

 

5\. Transmit (TX) and Receive (RX) LEDs – Not to be confused with the TX and RX markings by the 0 and 1 digital pins, the LEDs with these markings will give you a visual indication whenever the board is transmitting or receiving data, such as when you load a new program onto the board.

 

6\. Main Integrated Circuit (IC) – This is the black piece with metal legs that is attached to every board. It is basically the brains of an Arduino board. The main IC differs from board to board, though most are from the ATmega line of IC’s by the ATMEL company. It is important to know the IC and board type before loading up a new program from the Arduino IDE. You can usually find this information written on the top side of the IC.

 

7\. Voltage regulator – As its name implies, this component controls the amount of voltage that is allowed into the Arduino board. It functions by turning away extra voltage let into the board. But it has its limits though; it cannot handle anything over 20 Volts. So, a word of caution: DO NOT use a power supply greater than 20 Volts! It will overpower and destroy your Arduino. The recommended voltage for most models is 6 to 12 Volts.

 

 

All in the Family

 

The Arduino board has gone through considerable changes since it was first introduced, in order to meet the various demands and challenges of its users. More than just the 8-bit boards, Arduino have boards built for various applications, from Internet of Things (IoT) applications to wearable items. All of them are, of course, open-source, which further empowers users to build derivatives and customize them to fit specific needs. The following are a few options that are considered most suitable for the Arduino novice:

 

1.  Arduino UNO (R3) – The UNO is often considered to be the definitive Arduino board. It is well-equipped with everything you need to get started, with 14c digital input/output pins – six of which can be used as Pulse Width Modulation (PWM) outputs – six analog inputs, a USB connection, a power jack and many more. Simply connect it to any power source, whether it is a computer with a USB cable, an AC-to-DC adapter or battery, and you are good to get started. Regardless of your Arduino expertise, you can never go wrong with the UNO.

 

1.  Arduino Mega (2560) – The Mega board is a few notches above the UNO; kind of like its big brother. It has an impressive 54 digital input/output pins, of which 14 can be used as PWM outputs, 16 analog inputs, plus everything else you can find on the UNO and also functions the same way. If you have a project that requires a lot of digital input/outputs, such as for a lot of LED lights or buttons, the Mega may be the board for the job.

 

1.  Arduino Leonardo – The Leonardo board offers a cheaper and simpler alternative, as it is the first Arduino development board to use one micro-controller with built-in USB. Because of its direct USB handling, code libraries are available that allows the board to emulate a computer keyboard, mouse and much more.

 

1.  Arduino Mega ADK – This board is basically a specialized version of the Arduino Mega board. It is specifically designed for interfacing with Android smartphones.

 

1.  LilyPad Arduino – Thinking about making a cat-suit that lights up? The LilyPad is the wearable e-textile board you need. Designed by Leah Buechley, engineer and co-author of the book, Sew Electric, the innovative board was created with a large connecting pad and flat back that allows it to be sewn into clothing with conductive thread. And it is even washable!

 

1.  Arduino NG, Diecimila and duemilanove – Collectively known as Legacy Versions of the UNO, these boards are basically the granddaddies of the Arduino. The legacy boards lack some key features of other newer boards. For instance, the Diecimila and NG have a jumper next to the USB port and require manual selection of either USB or battery power. The NG also requires holding down the Reset button for a few seconds before uploading a program. It should be noted, however, the legacy boards are still being tinkered and improved upon by Arduino enthusiasts. They are worth looking into once you gain more knowledge and experience with Arduino.

 

 

Genuino Who?!

 

If you are shopping for Arduino boards outside of America, you may find Genuino boards that look identical. Don’t worry; you are not being duped by an imitation product! Genuino is Arduino’s sister-brand, created by the same team, and used for boards and products sold outside of the US.

 

The Genuino brand certifies the authenticity of boards and products to be in line with Arduino’s philosophy of open-source hardware. The brand has alliances with market-leading manufacturers in Asia, Europe, South America, Canada and Africa, making the Arduino hardware available worldwide.

 

You can think of Genuino boards as the identical twins of Arduino boards that live in foreign countries. All Genuino boards have the similar quality, components and characteristics as their Arduino counterpart. So, depending on which part of the world you live, you may find a Genuino UNO board when looking to buy an Arduino UNO. That’s just fine; you’re still getting the real deal.

 

It should be noted though, that not all Arduino boards – especially lesser known ones – have a Genuino twin.

 

 

Other Stuff You could Use

 

An Arduino board cannot do much on its own, so you will need to hook it up with something. There are plenty of hardware options one can fix onto their Arduino boards that will be overwhelming for the beginner to learn (see Chapter 5 for further reading suggestions). Hence, we will only be introducing you to two handy items that are easy to hook onto an Arduino boards and bringing your projects to life – sensors and shields.

 

There is a lot of fun to be had with sensors. Hook one up to your Arduino board, and add some simple programming code, you can then make your board sense and measure practically anything – light, temperature, physical pressure, distance proximity, barometric pressure and radioactivity. You can also build devices to scan fingerprint, detect motions of animals or people, and signals from remote controls.

 

Additionally, you can do even more with shields, which are pre-built circuit boards that can fit on top of your Arduino boards. With shields, you can program your Arduino to connect to the internet, control LCD screens, control motors and provide cellular communication and lots of other cool stuff, limited only by your knowledge and imagination!

 

 

Set Up the Software

 

Once you have your hardware sorted out, the first thing to do is to install the Arduino IDE. This is the software where you will write the code for the micro-controller and attach the circuit components to make things happen. You can download the software at the official Arduino website: www.arduino.cc.

 

Once downloaded, unzip the folder into a choose a location on your computer hard drive, and then run the Arduino.EXE file to complete the installation. Now, you are ready to get things going with Arduino!

Chapter 3

 

Taking The First Steps!

 

You have an Arduino board and the software; it is time to get down to business! In the sections that follow, you will be guided in a step-by-step process to do a few things; you will test out the Arduino software and board with your first code, and do a simple project of lighting an LED. For the example given, an Arduino UNO (R3) board will be used. However, the instructions can be applied, with minor modifications, to any Arduino board of your choice.

 

Here are the four pieces of equipment you will need to begin your Arduino journey:

 

1.  A computer that runs on Windows (XP or above), Mac, or Linux operating system, with the Arduino IDE installed

 

1.  An Arduino micro-controller (a.k.a. the circuit board)

 

1.  A USB A-to-B cable for connecting your Arduino board to the computer, or one that fits your board of choice (be aware that some boards will require an A-to-Mini-B cable)

 

1.  An LED

 

 

Plug in the Board

 

Arduino boards are powered by either a USB connection to a computer (via the USB jack) or an external power supply (via the barrel jack). You will need to connect the board to a computer in order to program it using the Arduino IDE. Once you are done with the programming and don’t require it to be connected – depending on how you want to use the board for your project – you can then opt for powering it with a wall power supply.

 

To start off, you must connect your Arduino board to a computer using the USB cable. The moment you so that, you may notice the LED with the label ‘ON’ next to it starts blinking furiously; this is the default program stored in the board’s chip. What you will be doing to kick-start your Arduino is overriding this default program, and making the LED blink on and off slowly, at 2-second intervals.

 

 

Install the Drivers

 

This step is required if you are using Windows 7, Vista or XP with an Arduino board for the first time. If you are using another operating system, you can skip this section.

 

1.  After you plug in the board, Windows will start the driver installation process. However, after a few moments, the process will fail.

 

1.  Next you’ll need to click on the Start Menu, and then click to open up the Control Panel.

 

1.  Navigate the Control Panel and go to System and Security. Click on System.

 

1.  Once the System window is up, click to open the Device Manager.

 

1.  Look under Ports (COM & LPT). Here, you should be able to see an open port named Arduino UNO (COMxx). However, if for some reason there is no COM & LPT section, look under Other Devices and search for Unknown Device.

 

1.  Next, Right click on the Arduino UNO (COmxx) or Unknown Device port and choose the Update Driver Software option.

 

1.  Select the Browse my computer for driver software option.

 

1.  Finally, find and select the driver file called arduino.inf, which can be found in the Drivers folder of the Arduino Software download (note: NOT in the FTDI USB Drivers sub-directory). Be aware that if you are using an older version of the IDE (1.0.3 or older), you’ll need to select the Uno driver file named Arduino UNO.inf.

 

1.  From here, Windows will finish up the driver installation.

 

 

Launch and Sketch

 

Once you have the Arduino IDE properly installed, you are now ready to test drive your board with the first program. Before getting into that, there are some things you need to know about writing code for Arduino. The codes are known as sketches, written in C++.

 

Every sketch needs two void type functions that do not return any value, setup() and loop(). The setup() method is run once, just after the Arduino board is powered up and the loop() method is run continuously afterwards. The setup() is where you want to do any initialization steps, and loop() is for codes you want to run over and over again.

 

A basic sketch skeleton should look like this:

 

|  void setup(){ } void loop(){ } |
| --- |

 

 

Now, let’s give your first program a try:

 

1.  Make sure your board is plugged in, and launch the Arduino application

 

1.  Open the Blink example sketch. To do this simply go to: File > Examples > 1.Basics > Blink

 

1.  Select the Arduino board type you’re using by going to: Tools > Board > your board type

 

1.  Choose the serial/COM port that your Arduino is attached to by going to: Tools > Port > COMxx 

 

If you’re not certain which of the serial devices is your Arduino board, have a look at the available ports, then unplug your Arduino and check them again. It should be the one that disappeared after you unplugged your board.

 

 

Upload and Make it Blink!

 

With your Arduino board connected, and the Blink sketch open, press the Upload button. Wait for a few seconds; you should see the RX and TX LEDs of the board flashing as the program is being uploaded. If the upload is successful, you will see the Done Uploading message in the status bar of the Blink sketch. 

 

If the whole process is done correctly, the orange ‘ON’ LED should be blinking slowly. Congratulations! You have successfully programmed your first Arduino.

 

 

But it doesn’t Work!

 

If you followed all the steps above, but you can’t upload the sketch to your Arduino for it to launch, it could be due to problems with one of the processes. Try running through these troubleshooting measures:

 

1.  Make sure you select the right board under the Tools > Board menu. In case you choose to use another board besides the UNO (as in the example), check the IC on the board. For instance, newer Arduino Duemilanove boards come with an ATmega328, while older ones have an ATmega168. So, make sure you select the right option.

 

1.  Check that the proper port is selected in the Tools > Serial Port menu.

 

1.  Check to see if the drivers for your board are properly installed in the Tools > Serial Port menu in the Arduino IDE, with your board connected. There should be an additional item that wasn’t there when your board is not plugged in.

 

 

First Mission: Light an LED!

 

Having successfully activated your Arduino, let’s try doing a little bit more with it. The following is a common learning project suitable for complete beginners in circuitry. For this task, you will need an LED and your Arduino that has already been launched (following the previous instructions).

 

1.  Plug in your board.

 

1.  Open another example sketch: File > Examples > Basics > BareMinimum. This will open a new window with a simple sketch that acts as the framework for your program.  

 

1.  Connect the LED’s anode (the longer pin) to pin 13 on the Arduino board, and the cathode (the shorter pin) to the adjacent GND pin. 

 

1.  Under the setup() section of the sketch, add the code: pinMode(13, OUTPUT);. This is the command that will run once to configure the board and get it ready to do as you program.

 

1.  Add the following under the loop() section: digitalWrite(13, HIGH);. This sets the pin 13 as an output pin with high voltage level (5 Volt).

 

When complete, your sketch should look like this:

 

|  void setup(){pinMode(13, OUTPUT);} void loop(){digitalWrite(13, HIGH);} |
| --- |

 

Hit the Upload button and wait for the Done Uploading message to show in the status bar. Voila! The LED should light up.

Chapter 4

 

Arduino Survival Lingo

 

As you go about adding to your knowledge bank about all things Arduino, you are bound to encounter some frequently used jargon. This mini glossary of terms is by no means extensive, but it does help the beginner understand the terms people often mention when they talk about Arduino, so that you will not be totally at a loss.

 

8-bit – The term refers to a Central Processing Unit (CPU) that processes 8 bits of data as a single unit.

 

Analog – Describes devices or systems that represent changing values as continuously variable physical quantities. As humans, we perceive the world in analog, as everything we see and hear is a continuous transmission of information (data) to our senses. An example of an analog device is a record player, because it reads bumps and groves from a vinyl record as a continuous signal. Analog data is more accurate than digital data, but harder to manipulate and preserve. With Arduino boards, you can use the analog pins to convert analog data to digital values.

 

AVR – When you work with electronics, you will encounter several meanings for this acronym. In Arduino terms, it refers to the platforms environment, which is based on Atmel Atmega micro-controllers. The AVR micro-controller was developed by Atmel Corporation in 1996, by Alf-Egil Bogen and Vegard Wollan. The AVR acronym derives from its developers and stands for Alf-Egil Bogen Vegard Wollan RISC micro-controller. It is also known as Advanced Virtual RISC.

 

C++ – Pronounced as ‘cee plus plus’, it is a general-purpose programming language. You program an Arduino board do stuff with C++, using the Arduino IDE.

 

CPU – Stands for Central Processing Unit and is also commonly referred to as the processor, a CPU is the electronic circuitry within a computer that carries out the instructions of a program.

 

Digital – Information in digital is stored using a series of 1s and 0s, known as binary code. Digital is the opposite of analog. Because digital devices read only 1s and 0s, they can only approximate audio and video signals. Unlike analog, digital data is easier to manipulate and store.

 

Driver – A software that allows a computer to connect and communicate with a hardware or device. Without the right driver, the hardware you connect to a computer will not work properly. Depending on the operating system you are using to work with your Arduino, you may need to install the driver for the board.

 

Environment – In computing jargon, the environment refers to a particular configuration of a hardware platform and the operating system that it runs on.

 

Ground – In electrical engineering, a ground is the reference point in an electrical circuit from which voltages are measured or the common wiring point. The term can also mean the literal earth where electrical circuits are connected to. On the Arduino board, the GND pin serves this purpose.

 

I/O – Short for input/output, which describes a program, operation or device which transfers data to or from a computer, to interact with the outside world. For example, if a button is pressed (input), a light bulb goes on (output).

 

LED – The acronym for Light-Emitting Diode, a two-lead semiconductor light source. LEDs have many advantages over other light sources, including smaller sizes, longer lifespan and lower energy consumption. On the Arduino board, you will notice some LEDs that indicate when the board is powered and codes are uploaded.

 

Micro-controller – A computer present in a single integrated circuit that is programmed to perform specific tasks. Micro-controllers are the brains behind automatically controlled electronic devices, from cell phones and cameras to washing machines and microwave ovens to robots.

 

Open-source – A program whose source code is made freely available to the public for use or modification. Open Source is a certification mark owned by the Open Source Initiative (OSI) that allows software developers to freely share their products with the public, so that it can be improved upon and redistributed. Unlike commercial software, where some sort of redistribution licensing is required, anyone can have a hand in developing and redistributing an open-source project.

 

Sensor – Electronic devices used to measure physical quantities, and then convert them into electronic signals. There are various different kinds of sensors for measuring things in the physical, such as temperature, pressure, distance, noise, motion etc. Sensors are normally components of more complex and sophisticated electronic systems. If you want to built a digital thermometer, for instance, you will need a temperature sensor that will go with your Arduino board.

 

Serial port – A connector that is used to send data to a device connected to a computer, such as modems, printers, and mice. An Arduino board must be connected to the right serial port for codes to be uploaded properly.

 

Sketch – A term used to mean an Arduino program. A chunk of code written to command an Arduino is called a ‘sketch’, rather than just a ‘program’, because the Arduino platform was designed to appeal to artists and creative individuals in addition to engineers. According to the founders, using the term ‘sketch’ would imply a rough idea that can be explored, refined and developed – much like an art or design sketch. As such, it will make using Arduino feel more encouraging and less daunting to those who are not from a tech background.

 

Shield – This is a circuit board that can be attached on top of an Arduino to accomplish a variety of purposes. They are called this because they fit over the top of an Arduino board like a protective shield.

 

IDE (Integrated Development Environment) – The software application that is run to provide you with the tools to program Arduino boards. It includes a source code editor, build automation and debugger. It is an open-source software available for download at the official Arduino website (www.arduino.cc).

 

Pulse-Width Modulation (PWM) – A term describing a type of digital signal that is used in a variety of applications. It is mainly used to control the amount of power supplied to electrical devices.

 

Voltage – The amount of energy between two points of a circuit, measured with the standard unit, Volt (V).

Chapter 5

 

Essential Resources & Further Reading

 

You have learnt the basics of Arduino and – if you have actually been following along with the instructions – got a feel for what the platform can do firsthand. That was just the tip of the iceberg, though; Arduino mastery takes time and dedication to keep building upon what you have learnt. Furthermore, the open-source platform keeps on expanding as more people take to using it. Whatever brought you to Arduino, your journey with this exciting platform has just begun. Here is a list of useful materials, written by some of the most respected authorities on Arduino, to help you move ahead.

 

 

 

For Absolute Beginners

 

 

# Getting Started with Arduino: The Open Source Electronics Prototyping Platform

by Massimo Banzi and Michael Shiloh

ISBN-10: 1449363334 / ISBN-13: 978-1449363338

 

What better way to get more acquainted with Arduino than from one of the creators himself? Massimo Banzi is the platform’s co-founder. This beginner-friendly book is written based on his extensive experience in teaching, using, and building Arduino.

 

 

# Beginning C for Arduino, Second Edition: Learn C Programming for the Arduino Kindle Edition

by Jack Purdum Ph.D.

ISBN-10: 1484209419 / ISBN-13: 978-1484209417 

 

Written for those who have no prior experience with micro-controllers or programming, this guide is ideal for those who are starting their journey into programming. You will get an introduction into C programming language, with a simple demonstration of how it can be used on the Arduino family of micro-controllers. Drawn from the author’s 20-plus years of university teaching, this book is perfect for the complete programming beginner. It is engaging to read and assumes no prior programming or hardware design experience of its readers, making learning enjoyable.

 

 

 

Take Your Skills to the Next Level

 

 

# Programming Arduino Next Steps: Going Further with Sketches

by Simon Monk

ISBN-10: 0071830251 / ISBN-13: 978-0071830256

####  

#### Electronics guru, Simon Monk reveals professional programming secrets for Arduino in this practical guide for those who already have a firm grasp of programming micro-controllers. This book covers the Arduino Uno, Leonardo, and Due boards. Learn advanced ‘sketching’ techniques to take your Arduino to the next level, including programming for the internet, maximizing serial communications, managing memory, performing digital signal processing, and so much more. The book features over 75 example sketches, all available for download.

 

 

# Electronics from the Ground Up: Learn by Hacking, Designing, and Inventing

by Ronald Quan

ISBN-10: 0071837280 / ISBN-13: 978-0071837286

 

Are you fascinated by the complex circuits behind common electronic devices? This book guides you through step-by-step experiments that reveal how electronic circuits function. It also explains components, construction techniques, basic test equipment, circuit analysis, and troubleshooting. By the end of the book, you will not only be armed with the know-how to design customs circuits, but also the ability to hack and modify existing circuits to suit your needs.

 

 

# 30 Arduino Projects for the Evil Genius

by Simon Monk

ISBN-10: 0071817727 / ISBN-13: 978-0071817721

 

Ever want to build a Morse code translator? Pulse rate monitor? A Hypnotizer? How about a keyboard prank? You can unleash your evil genius with this do-it-yourself guide that shows you how to program and build some really fascinating projects with the Arduino Uno and the Arduino Leonardo boards. You will learn from through guides with checklists of required parts for each project, step-by-step instructions with illustrations, and clear explanation of scientific principles behind the projects.

 

 

 

Fun Project Ideas

 

 

# Arduino Workshop: A Hands-On Introduction with 65 Projects

by John Boxall

ISBN-10: 1593274483 / ISBN-13: 860-1200651553

 

Think you’ve already got the hang of Arduino and are ready to try some fun projects? This book will get you started. You will learn the extensive range of Arduino’s input/output add-ons, displays, motors, sensors, indicators, and more. Each project is designed to reinforce what you have learnt, and they increase in complexity as you progress. So, what can you learn to build? A digital thermometer, battery checker, and a GPS logger, to name a few. There are also fun things to learn, like making a binary quiz game and an an electronic dice.

 

 

# Sew Electric Perfect

by Leah Buechley, Kanjun Qiu and Sonja de Boer

ISBN-10: 0989795608 / ISBN-13: 978-0989795609

 

Co-written by the creator of the LilyPad Arduino board, Leah Buechley, this book is a hands-on guide that combines crafting, electronics and programming to create fun projects. Learn to make interactive toys, light-up fashion accessories and many other cool things using the LilyPad Arduino board that can be shared with friends and family. This is also a great material for teachers to introduce practical electronics to young students.

 

 

# Textile Messages: Dispatches From the World of E-Textiles and Education

by Leah Buechley, Kylie Peppler, Michael Eisenberg and Yasmin Kafai

ISBN-10: 143311920X / ISBN-13: 978-1433119200

 

This book is a handy introduction to e-textiles – soft circuit boards that can be used to incorporate electronic elements into clothing and furniture. In the Arduino family, the LilyPad board is an e-textile, and this is a beginner to intermediate guide that can show you how to make the most of your LilyPad. You will be introduced to a collection of tools that enable anyone to learn and create with e-textiles, whether you are an educator, hobbyist or designer.

 

 

# Make: Wearable Electronics: Design, prototype, and wear your own interactive garments

by Kate Hartman

ISBN-10: 1449336515 / ISBN-13: 978-1449336516 

 

For those with interest in computing, and fashion designers who want to build creative projects that fuse both disciplines, this book is a must read. You will be introduced to tools, materials and techniques for making interactive electronic circuits, and embedding them in articles of clothing with step-by-step instructions. Although the book does not specifically feature Arduino projects, it will equip you with knowledge that can be adapted to suit the Arduino platform. So, if you ever wanted to build clothing that changes color to complement your skin tone, a jacket that shows when the next bus is arriving, shoes that dynamically shift your height, and many other cool wearable items, now you can!

#  

 

# Adventures in Arduino

by Becky Stewart

ISBN-10: 1118948475 / ISBN-13: 978-1118948477

 

If you know a kid who shows potential in electrical engineering and programming, give this book to him or her! Written specifically for the budding electrician, ages 11 to 15, this book is an excellent Arduino introductory source.

 

 

 

Online Resources

 

[https://www.arduino.cc/](https://www.arduino.cc/) - The official Arduino website for all your needs and the latest development news regarding the platform. Here is where you can find and join the Arduino forum to get help and share knowledge with other users from all around the world.

 

[http://www.cplusplus.com/](http://www.cplusplus.com/) - A comprehensive online library for all things C++. You can learn about the history, development and the A-to-Zs of the programming language that Arduino runs on. 

 

[http://www.ladyada.net/](http://www.ladyada.net/) - A wonderful resource to learn about electronics and circuitry, with nearly all its content being open-sourced.

Conclusion

 

Congratulations on completing the Arduino basic apprenticeship and successfully navigating your first Arduino project! In this book, I hope I have managed to give you all the information you need to feel confident in your ability to move forward and try some more difficult Arduino projects. Good luck!

 

Don’t forget to scroll down for your FREE GIFTS and for more info on my other books!

A message from the author, Steve Gold

 

To show my appreciation for your support, Id like to offer you a couple of exclusive free gifts:

 

FREE BONUS NUMBER 1!

As a free bonus, I’ve included a preview of one of my other best-selling books directly after this section. Enjoy!

 

FREE BONUS NUMBER 2!

For a limited time I’ve also included access to a FREE book which is ONLY available to my readers and can’t be found anywhere else. Don’t miss your chance to get it, along with exclusive access to more free books and exclusive discounts in the future! Simply follow the link below for instant access:

 

[\=>Click HERE to learn more! <=](http://eepurl.com/bMxlLr)

 

ALSO…

Be sure to check out my other books. Scroll to the back of this book for a list of other books written by me, along with download links.

 

Thank you again for your support.

 

Steve Gold

Book Two Starts Here￼

![Arduino 2 Thumbnail.png](images/00002.jpeg)

 

Arduino

 

Taking The Next Step With Arduino: The Ultimate Beginner’s Guide - Part 2

 

Steve Gold

Table of Contents

 

Introduction

 

Chapter 1: Working with the Arduino IDE

 

The Command Area

Menu Items

The Icons

The Text Area

The Message Window Area

The IDE and the Board

 

Chapter 2: Creating and Saving Your Own Sketches

 

 

Project Planning Stages

How to Write Your Own Sketch

Comments

The Setup Function

The Loop Function

Notes on Saving Your Sketch

Verifying Your Sketch

Getting Your Sketch to the Board and Running It

Changing Sketches

 

Chapter 3: Signals and the System

 

Analog Pins and Digital Pins on Your Board

 

Chapter 4: Incorporating Sensors

 

Sensing Movement

Chasing the Light

How to Detect Motion

Measuring Distance

 

Chapter 5: The Different Types of Outputs

 

Digital Output

Analog Output

Varying the Levels of Light

Getting to Know Your LED

Maximum Pin Current

Practical Applications for LEDs

A Series Resistor

Audio Output

 

Chapter 6: Breadboarding

 

Getting Grounded

When You Need Jumper Wires

 

Chapter 7: Build Your Own Simple Robot

 

Getting the Support in Place

Attaching the Arduino and the Breadboard

Your Robot’s Chariot Awaits

Wire Up Your Servo

Placing the Sensor

I’ve Got the Power

Killing Your Robot

 

Conclusion

 

A message from the author

Introduction

 

So, you know a bit about Arduino already and you want to learn more? You’ve played around with your first board and made the LED blink and you’re now ready for something a little bit more advanced?

 

This book is for someone who already knows something about Arduino and how it works. It is not written for a beginner. It is for someone who wants to know more about creating their own sketches, using the Arduino IDE and getting to grips with the various types of hardware that you can add on.

 

This book goes through all this and a lot more. We will work through this carefully and you will be given practical advice and real world examples that you can draw upon.

 

And, at the end of the it all, you get to build a robot!

 

Will you become an Arduino expert after reading this book? Not quite – to do that would take reading through a few very long books.

 

Will you be able to fake being an expert? With your own home-made robot at your side, what do you think?

 

Will you get the grounding you need to go on and learn more? What you will learn from this book are skills that can be built on at a later stage. With Arduino, once you understand how to connect up the circuits properly and how to program your creations, the sky really is the limit.

 

P.S. As a token of my appreciation, I have included a free gift for you; no catch, no charge. Simply [click here](http://eepurl.com/bMxlLr) for instant access.

© Copyright 2017 by Eddington Publishing - All rights reserved.

 

This document is geared towards providing exact and reliable information in regards to the topic and issue covered. The publication is sold with the idea that the publisher is not required to render accounting, officially permitted, or otherwise, qualified services. If advice is necessary, legal or professional, a practiced individual in the profession should be ordered.

\- From a Declaration of Principles which was accepted and approved equally by a Committee of the American Bar Association and a Committee of Publishers and Associations.

In no way is it legal to reproduce, duplicate, or transmit any part of this document in either electronic means or in printed format. Recording of this publication is strictly prohibited and any storage of this document is not allowed unless with written permission from the publisher. All rights reserved.

The information provided herein is stated to be truthful and consistent, in that any liability, in terms of inattention or otherwise, by any usage or abuse of any policies, processes, or directions contained within is the solitary and utter responsibility of the recipient reader. Under no circumstances will any legal responsibility or blame be held against the publisher for any reparation, damages, or monetary loss due to the information herein, either directly or indirectly.

Respective authors own all copyrights not held by the publisher.

The information herein is offered for informational purposes solely, and is universal as so. The presentation of the information is without contract or any type of guarantee assurance.

The trademarks that are used are without any consent, and the publication of the trademark is without permission or backing by the trademark owner. All trademarks and brands within this book are for clarifying purposes only and are the owned by the owners themselves, not affiliated with this document.

Chapter 1

 

Working with the Arduino IDE

 

Let’s start by seeing what the Arduino IDE is all about. Start by opening up the IDE. It looks like a very basic word processor and is divided up into the following areas:

 

1.  The Command Area

 

1.  The Text Area

 

1.  The Message Window Area

 

 

The Command Area

 

The command area is where you will find the icons, menu items and title bar. The title bar shows what the name of the sketch is and what version of the Arduino IDE you are running.

 

Then you will find your menu items and icons as discussed below.

 

 

Menu Items

 

You work this in much the same way as you would Microsoft Word. Click on any item in the menu to see what options you have.

 

1.  File: In this section you will find the buttons to save sketches, to load them and to print them. You will also be able to find example sketches that you can refer to. You will also be able to set your Preferences here by clicking on the Preferences tab.

 

1.  Edit: Here you will find the normal commands – Search, Copy and Paste, just like in Microsoft Word.

 

1.  Sketch: This includes functionality that allows you to verify your sketch before you take the step of uploading it to the board itself. It also has import options and a way to sort your sketches into folders.

 

1.  Tools: There are a number of different functions included in here. You will need this section to specify the type of Arduino board you have and what USB port you’ll be using.

 

1.  Help: This will enable you to get help using Arduino and the specific IDE version that you have.

 

 

The Icons

 

The icons are under the menu toolbar. There are six in total. You can hover over each of the icons to see the name. These are what the icons are and what they do:

 

1.  Verify: If you click on here, you will be able to tell if the Arduino sketch is actually valid and that it is free of errors in the programming.

 

1.  Upload: If you click on here, you will be able to verify the sketch first and then have it uploaded to the board.

 

1.  New: This will enable you to open a new, blank sketch. It opens in a different window.

 

1.  Save: You can save the sketch that is currently open using this button. You will be asked to name the sketch if you have not already done so.

 

1.  Serial Monitor: This is the button if you want to open a window that can be used to transfer data from the IDE to the Arduino or back again.

 

 

The Text Area

 

This is the area that you will use to create the different sketches. This is the area that you can type in.

 

At the top left-hand corner, you will be able to see what sketch you are working on is. If you haven’t named the sketch yet, the system will default to whatever the date is.

 

You put in your commands here just like you would in a text editor.

 

 

The Message Window Area

 

This is towards the bottom of the screen. Messages that the IDE sends will show up in the area that is blacked out. There are a number of different messages that you will get. This is where the IDE will communicate whether or not a sketch is verified, what the status of the system is, etc.

 

 

The IDE and the Board

 

If you look at the bottom of the screen, next to where the IDE messages are displayed, you will see the type of Arduino board you have and also which port it is connected to.

Before You Continue...

 

As a token of appreciation, I’ve included a great, surprise for you

 

Claim Your Exclusive Free Gift!

 

For a limited time I’ve included access to a FREE book which is ONLY available to my readers and can’t be found anywhere else. Don’t miss your chance to get it, along with exclusive access to more free books and exclusive discounts in the future! Simply follow the link below for instant access:

 

[\=>Click HERE to learn more! <=](http://eepurl.com/bMxlLr)

 

Enjoy!

Steve Gold

Chapter 2

 

Creating and Saving Your Own Sketches

 

Sketches are really just your instructions to your board. Now that you have some understanding of how the board works, you no doubt want to jump right in and get started with writing your own sketches.

 

What you need to remember is that you will need to tell your board what to do, step by step. The board cannot think for itself or fill in the blanks when it comes to codes that have errors or missing information.

 

Fortunately, with a little bit of planning, you can work around this.

 

 

Project Planning Stages

 

1.  Clear objectives: Start by clearing defining what it is that you want to get out of the sketch.

 

1.  Write out the algorithm: This is where you list the instructions that you need in order to make your project a reality. This is a step by step set of instructions from start to finish.

 

1.  Choose what hardware you are using: The hardware will need to be connected to the board and you need to figure out how to do that upfront.

 

1.  Your sketch: Now you can actually get down to writing out the sketch. In this, you will give the Arduino clear and simple instructions on what it must do.

 

1.  Connect everything: Now you can wire in the circuitry and hardware to the board.

 

1.  Test for bugs: Does the project work as it should? If not, what errors can you pick up? Work through everything one step at a time again. It could be a problem with the sketch or the algorithm, it could be a problem with the way it was connected or it might even be a faulty component.

 

 

How to Write Your Own Sketch

 

Creating a basic sketch is easy if you approach it step by step. The sketch will run through each command in the order in which they appear so make sure that your steps are laid out in a logical sequence.

 

To draw a parallel in the real world – deal with writing the sketch the same way you would approach teaching a young child to bring you their jacket. They don’t know anything.

 

You have to explain to them where the jacket is. You have to tell them to fetch the jacket. You have to tell them how long it should take. You have to tell them to hand the jacket over to you, etc.

 

In the same way, you have to tell your board what pins to use and what you have connected to them. You have to tell them what components you have added and what you want them to do.

 

Let’s say, for example, that you want to blink an LED light. You have to tell the system to switch the light on for, how long to leave it on for and then to switch it off.

 

To start off with, make sure that the board is plugged in to the USB port on your computer.

 

Open up the IDE and go to “Tools”. Make sure the correct port has been selected. This is just to confirm that the board is connected properly.

 

Now you can start writing your sketch:

 

 

Comments

 

These are not actually for the board but more as a reminder to yourself. This will come in handy later when you are using a few different sketches. You can write in what the purpose of the sketch is. It doesn’t need to be too involved or complicated – just a reminder of what you created and why.

 

It also helps to update the comments when you make changes – this will help you to keep track of whatever tweaking you have done.

 

It is especially important to update the comments section if you think someone else is going to be making use of your sketch.

 

If what you are writing will fit on one line, type in two forwards slashes immediately before your comment so that the board knows to ignore that text completely.

 

So it could look like:

 

// Clock Sketch by Name created January 2017

 

If your comment won’t fit on one line, put a forward slash and asterisk on the line directly above the comment. When the comment is complete, move to the next line and repeat the slash and asterisk again.

 

So, it could look like:

 

/\*

Clock Sketch by Name Created January 2017

Made to tell the time

\*/

 

Now go to File and click on “Save As”. Choose what you are going to name the sketch and hit the “OK” button.

 

Arduino sketches have the extension .ino appended to them but you don’t have to worry about doing this – it should be done automatically.

 

Once the sketch has been saved, you will be able to call it up again by finding it in the Sketchbook.

 

 

The Language Used by Arduino

 

The language that you will use for coding will be familiar to you if you have done any work with C or C++. That said, you do not need to be an expert programmer to be able to use the code as the system is centered on making things simpler for you.

 

 

Variables

 

It can be useful to think of variables as something like a shopping basket. Each variable has content within it. You can look inside to see what you have in there, and can change out the contents for something else if you like.

 

The variable is essentially what your “shopping basket” is going to be called. The variable is the name of container which holds a specific bit of data that it is possible to change or inspect.

 

Using variables has a couple of different advantages – first off, code becomes easier to understand if you do and it also makes maintaining the code easier.

 

Let’s say you first decide that you want to use the number 2 pin for blinking your LED light. You have two options. Either you could apply the function manually throughout your coding or you could use a variable instead.

 

You would name the variable and then assign a value to it. Then, in the sketch, wherever you need to refer to that particular function and pin, you could use the variable instead.

 

Now, this may seem like you are doing things the long way around but the advantage is that, should you want to move the function to another pin, all you would have to do is to adjust the coding where you have declared the variable. Had you done this the other way around, you would have to go to each line where the code appears and change each manually.

 

You can also be creative when it comes to the name that you give the variable. This will make it a lot easier to remember what the actual function of the variable was. So you could, for example, call your variable, outputPin.

 

 

The Setup Function

 

Your next step, whatever sketch you are creating is to add in the “void setup()” function. Type in void setup () and then follow on the next line with braces and whatever instructions you want to add in.

 

The difference with this function and other functions is that this will only be run once, at system start up or when the system is reset.

 

Close the brackets on the next line.

 

Include this even if you have no particular instructions for the system because the IDE will look for this when verifying the sketch and will return an error if it is not present.

 

So it looks something like:

 

void setup()

{

}

 

 

Control Your Hardware

 

Once the hardware has been connected, you need to tell the Arduino board what to do with it. If your hardware requires an electrical signal, it will need to be connected to a digital pin.

 

You will need to tell that pin what it must do so it will look something like:

 

{

pinMode(2, OUTPUT); // this tells the number 2 pin that it is for output

}

 

What the above example is telling the pin to do is to generate a signal. You can set it up the other way around by replacing the word “input” to the word “output”.

 

The part of the command is the instruction to the board – the semicolon is what tells the board that the command is ended. The text following the forward slashes are notes for your own benefit – you don’t have to add them if you don’t want to.

 

Always save your work as you are going along.

 

 

The Loop Function

 

If you want to make the board do something over and over again, like blink an LED light, you need to add in a loop function. This lets the board know that it must repeat the instruction continuously until it is shut down or reset.

 

This instruction should immediately follow the void setup() command and “pin” command, before you put new commands in.

/\*

LED Blinker

by Name, created January 2017

\*/

void setup()

{

pinMode(2, OUTPUT); // this tells the number 2 pin that it is for output

}

void loop()

{

// Add in your main code:

}

 

Again, save your work.

 

You will then tell the board exactly how often to blink the light, how long to blink it for and how long to pause it for.

 

 

Notes on Saving Your Sketch

 

When you save your sketch, choose a name that is short but meaningful to you. When you hit the save button, the IDE brings up the default save location as the Arduino folder created in your “My Documents”.

 

You can save the sketches elsewhere if you like but only sketches saved in the default location will appear in the Sketchbook menu section. If you save sketches elsewhere, they may not be as easy to track down again at a later stage.

 

Arduino does not allow you to use some characters, like spaces. If you try to use these, it will ignore these completely so do keep that in mind when naming your sketches.

 

The samples that are provided with the software cannot be overwritten. You will need to change the filename in order to save any changes that you have made. This is a good thing because it keeps the samples free of any errors – if your changes don’t work, you can always revert to the originals again.

 

If you do make changes, the system will ask whether or not the changes should be saved when you close the sketch off. It is better not to rely on these system reminders and save your work periodically to prevent data loss.

 

If you are working on a sketch and have changed portions of it, but not saved them yet, you will see the § symbol behind the sketch’s name. As soon as you hit save, this will disappear.

 

If you are tinkering with a sketch and want to be able to go back to previous version, you need to click on the “Save As” and give the amended sketch a different name so that you don’t overwrite the previous version.

 

It does help to also verify the code as you are going along. That way, locating errors becomes a far easier task.

 

If you upload the sketch to your board without saving it, you won’t be able to access it again. The sketches must be saved on your hard drive on your computer if you want to access them again later.

 

 

Verifying Your Sketch

 

All that you are doing here is ensuring that Arduino is able to understand the sketch and is able to follow the commands. Once you have run the “Verify” command, the IDE will tell you whether it is verified or not in the message box.

 

You will get a message stating “Done compiling” and that means that you can upload the sketch to the board. It will give you the amount of memory the sketch needs and the amount of memory the Arduino has.

 

Mistakes happen and basic errors will come up during this stage. Perhaps you forgot to close off the command properly and this prevents the sketch running properly.

 

The system will tell you when that is the case.

 

It will tell you which function has a problem, it will list the area that it believes the error is in, and what the nature of the problem is. It will even highlight what it believes to be the problem area on the sketch itself.

 

 

Getting Your Sketch to the Board and Running It

 

As long as you are sure that your sketch is right, you can upload it to the board. Your board will have to be connected to the USB port to do this.

 

You can upload your sketch by using the “Upload” function. The IDE is going to reverify the sketch before it uploads it.

 

You can check to see that the board’s LED lighting blinks so that you know the computer is transferring the information.

 

Once the upload is finished, as long as everything is correct, your command should be run and you will see if the Arduino acts as you think it should.

 

 

Changing Sketches

 

You might want to tinker with your sketch once you have run it and seen how it actually performs. Again, this is pretty simple because it operates a lot like Microsoft Word.

 

Click on the “Sketch” button, go to the “Sketch Folder” option and click on it. It will bring up a new window with the list of saved sketches.

 

Double-click on the one that you want to change and the system will bring it up in the IDE window. You can then edit it as you like.

 

Save the amended sketch.

Chapter 3

 

Signals and the System

 

Part of Arduino’s charm is that it can make sense of both analog and digital inputs. It is able to interact with you and the world it is in as a result. This can be useful when it comes to things like creating sensors, etc. In this chapter, we will go through some of the useful things you can do with the system in this regard.

 

You do need to have some sort of knowledge about electronics in order to work through this chapter so, if you do not, it will help to read up on the subject more. It can save a lot of heartache and expense to do so.

 

If you are not sure what you are doing and incorrectly connect components or use too much power for the system, you might end up blowing the controller chip.

 

“Getting Started in Electronics”, written by Forrest Mims, is a good place to start off.

 

You need to find out what voltage your controller will run on. This is usually about 5 volts. If you exceed this voltage, you risk frying the chip.

 

For most boards, it is not the end of the world if you do fry the chip because the chips are replaceable but it is better to be safe than sorry.

 

Analog Pins and Digital Pins on Your Board  

We will deal with the standard Arduino board here.

 

We’ll start off with a digital input pin – these are used to determine the presence of voltage on the actual pin or the lack there of. The analog input pins, on the other hand, are designed to determine what the range of voltage actually is.

 

The digitalRead function will be input in the sketch as either “High” or “Low”. Essentially, the former means that voltage is coming in to the pin and the latter means that it is not. So, if you want the pin to measure whether or not there is a current coming from a device connected to it, you must use the digitalRead function.

 

If you want to measure voltage, on the other hand, you would use pinMode instead.

 

Most boards have 14 of these digital pins. The first two, numbers and 1, will have the designations TX and RX. These pins are for the USB serial connection. They should not be used for anything else.

 

If you find that you do not have enough digital pins, you can instead use your analog pins.

 

If the standard board is still not big enough, you can get yourself a mega board. It works in much the same way as the standard one but it has a lot more pins.

 

Analog values are completely different in that they vary on a continuous basis instead of just having two levels – on and off. The volume control on your TV is a good example of this – you can change the volume to any level along its range.

 

A lot of sensors out there give readings based on the differences in voltage. You can use the function, analogRead in order to get the system to give you a value based on the voltage it reads on one of the analog pins. You will be able to tell not only if the pin is on or off but also how much voltage is running through it.

Chapter 4

 

Incorporating Sensors

 

Before we get onto the actual sensors themselves, let’s take a look at setting up a workspace that will work for you. You don’t need a huge space, unless you are working on a particularly large project but you should have a space that you can dedicate to the process.

 

Whether this is a specific desk/ workbench or a whole room in your house will depend on what you plan to build, how much time you will devote to working on Arduino projects and how much space you currently have.

 

One thing to bear in mind is that you will often be working with fiddly bits and pieces and that your projects are going to require a good deal of concentration on your part. Ideally speaking, you want a space where you can leave your work undisturbed to pick up later when you have time again. If you have to stop partway through a project, it can be very annoying to have to tidy everything away and then have to unpack it again when you want to get started again.

Consider the following when deciding where to put your Arduino workspace:

 

1.  A comfortable chair and a place as free of humidity as possible. (The laundry room, therefore, may not be the best idea.

 

1.  A good workbench that is solid and that will provide adequate support for your projects and tools.

 

1.  A good power outlet on hand.

 

1.  Space to set up your laptop or computer.

 

1.  Excellent lighting and good ventilation are essential.

 

1.  Storage space to keep all the parts in – shelves are a good thing to have. You will need various storage items to keep your tools and your parts in. A set of drawers that you would normally use to store hardware like nails, screws, etc. will come in very handy. Try for drawers that have clear fronts or be sure to label the drawers carefully to make your storage system as efficient as possible.

 

1.  A comfortable environment to work in, especially when it comes to longer projects. If you set aside a space in your garage, for example, will it be warm enough to be pleasant to work in during the dead of winter?

 

1.  A distraction-free environment. Can you cut yourself off from the rest of your family? Choosing a high-traffic area in your home is not conducive to the kind of concentration you will need to maintain when building your Arduino projects and writing lines and lines of complicated code.

 

1.  Some background music. It can help to have some background music playing to drown out extraneous noise in the background and to improve your enjoyment of the time spent on the Arduino projects.

 

1.  Access to the internet. You will need to be able to connect to the internet in order to easily be able to access plans, etc. If you have Wi-Fi, make sure that you will get a signal in your chosen workspace.

 

1.  Safety issues also need to be considered. Keep a small first aid kit on hand so that you can treat cuts, burns, etc. quickly and easily.

 

1.  If there are small kids in the house, it is a good idea to be able to keep your work area locked so that they cannot explore it and potentially hurt themselves.

 

1.  An area free of snacks and drinks. It is tempting to want to eat at your work area but, for the most part, it is better to take a break when you need a snack. Spilling food or drinks on the project you are working on can be disastrous.

 

1.  Make it possible to keep everything neat and tidy. That means having enough drawers, etc. so that you can store your parts properly. Having an untidy workspace is not conducive to efficiently working on projects. If you have to waste time searching for components, you are likely to lose your train of thought and will have to take even longer on your projects.

 

 

Tools to Consider

 

There are some basic tools that will make your life a lot easier. Here is a list of the tools to consider getting before you embark on your Arduino projects:

 

1.  A multimeter: This is not always something that you will see listed in your Arduino projects but it is something that will make your experience a lot less frustrating. A multimeter allows you to measure a range of things in an electrical circuit such as current voltage, whether the circuit is complete, etc. With the multimeter, you can test whether or not each of the electronic components is working as it should or not. It is also extremely useful when it comes to troubleshooting when something is not working as it should.

 

1.  Jumper wires and a few breadboards: Again, these are not always strictly necessary and not called for in all projects. A breadboard, however, can make it a lot easier to test out your proposed layout and see if it works without having to go through all the trouble of soldering the wires n place. A breadboard is also useful in keeping your projects neat and tidy and makes it simpler to create the right connections. In addition to the breadboard, you will need jumper wires – these are what make the connections on the breadboard possible. You will need to find solid core jumpers to use with the breadboard and do look for wires that can handle the kind of voltage that your project will be generating.

 

1.  A soldering iron: The breadboard is not suitable for all projects and, in those cases, you will need to be able to solder your components in place. Should you feel that you need to include buttons in your project, for example, you will want to solder the wires for them in place. Even if you are going to incorporate the breadboard into your project permanently, you might still need to solder components into place. Soldering irons are inexpensive and should form part of your toolkit. There is a caution here though – they get extremely hot. Always make sure that you have somewhere safe to support them while they are heating up and always make sure that you switch them off when you are done with them. Keeping a small burn kit in your First Aid kit is essential if you are going to be working with a soldering iron.

 

1.  Something to supply power: The Arduino does have a little bit of a charge and this will be sufficient to charge very small projects. In many cases, you need to have a separate power supply.

 

1.  A set of screwdrivers: You will be working with a range of components of varying sizes and descriptions. You will need a variety of star and flathead screwdrivers.

 

1.  Helping Hands: These are a little clamp that has a couple of alligator clips attached to connect to the board you are working with. They hold the board up and steady so that it is easier to work with. Some have a magnifying glass built into their design as well. These are hardly ever referred to in Arduino projects but are an extremely helpful device.

 

1.  Wire Strippers: These will be used to strip the wires of insulation and to cut different wires. There are tons of options on the market, ranging from cheap to very expensive. Aim for something in the middle – these will be used a lot and will last you a long time. If you choose one of the cheapest pairs, they are bound to be more trouble than they are worth.

 

1.  Needle-Nose pliers: These are a great help when you need to work with fine wires and small objects. Have a couple of different sizes to handle a variety of different projects.

 

1.  Angle Side Cutters: These are useful for those tougher to reach spots and good to cut leads or wire leading to your components.

 

1.  A sharp craft knife and spare blades: There are going to be times when you need to cut through materials that you are using to house your projects in – like cardboard, etc. You need a sharp craft knife to help you in these instances. Always make sure that you have at least one spare blade so that you can replace worn blades immediately. You will know that your blade needs replacing when it starts to drag on the surface that you are cutting or makes uneven cuts. Also keep some Band-aids in your First-Aid box and take care when cutting with the blades. They can be very sharp.

 

1.  A box cutter: A craft knife won’t be able to handle heavier materials so keep a box cutter and replacement blades on hand as well. The same safety precautions need to be applied.

 

1.  A self-healing mat: This will be used in conjunction with the craft knife. It protects your desk or work table and gives you a firm surface to cut on.

 

1.  A permanent marker, pencil and scrap paper: The permanent marker is for when you need to make permanent marks on something. The pencil and scrap paper are so that you can quickly sketch out your new projects – planning them on paper first helps you to think out where you will put everything and helps you to work out what the best design is. These designs don’t have to be draftsman quality but just a rough idea of how the components will fit together before you start on the actual construction. If you would prefer to make precision drawings, graph paper can come in very usefully.

 

 

Sensors and Your Arduino Board

 

Incorporating sensors makes it possible for the Arduino board to measure things in the it’s environment and/ or respond to them. Sensors help make the Arduino boards a lot more useful and this is one of the primary reasons people use the boards in the first place – to make simple machines to measure input.

 

The sensors read the data they are meant to measure and convert this data into an electrical signal that the Arduino is able to read. The sensor itself will determine what data is read and produced - the data produced is only as good as the sensor.

 

A simpler sensor, like a photoresistor, is made of a substance that is designed to respond to changes in the environment.

 

More complex sensors will incorporate a microcontroller into their design.

 

In this chapter, we will deal with using sensors and how you can incorporate them into your Arduino designs.

 

Sensors provide the Arduino board with information in one of the following ways:

 

1.  Digital On/ Off: These tend to be more simple sensors, like tilt sensors. When conditions change, they will switch the pin on/ off. There are no other variables. These will work in conjunction with the digitRead function.

 

1.  Analog: These provide a signal that varies according the conditions that the sensor is experiencing. You could, for example, have a sensor that measures light conditions or sound levels. These will work in conjunction with the analogRead function.

 

1.  Pulse width: These are sensors that can measure things such as distance travelled. You would need to measure the duration of the pulse related and so would need to use the pulsein function.

 

1.  Serial: There are sensors that use a serial protocol to communicate values. These must be connected through the serial port and so you are limited in terms of how many you can add. You can add additional ports for this but that is beyond the scope of this book.

 

An alternative option is to see whether or not you can use a sensor from something that you have at home rather than buying a new one. An old gaming controller can be put to use quite well as it already has sensors incorporated into it. It might even be less expensive than buying the sensors on their own.

 

If you do decide to jerry-rig device, you will have to write a sketch based on a device that produces the same kind of output. Check the specs for the device that you have bought or co-opted by looking at the data sheet. If you have lost the sheet, you will often be able to find more information in this regard online.

 

Data sheets give you a lot more detail than the average user would really need. You want to check the information provided about the output signal and also check what voltage the sensor can take.

 

If, for example, you have a device that can only stand up to 3.3 volts and you connect it to a pin that produces 5 volts, you will damage it.

 

Making sensors useful to you can mean a lot of tweaking. You will need to interpret the data so that it is useful to you, and also make sure that it is put in the right context. You then also need to ensure that there is as little exposure to items that you don’t want measured as possible.

 

These are things that you will learn how to do with time. You could, for example, take an average when it comes to readings instead of relying on just one or two.

 

 

Sensing Movement

 

Tilt sensors tend to be pretty simple in their construction. Basically all it usually is, is a box that has contacts on one of the ends. A ball is placed inside – if the ball makes contact with the contacts, the circuit is closed.

 

If it is tilted away from the contacts, the circuit remains open. You will thus know which way the box has been tilted by determining whether or not the circuit is closed.

 

You will see from the markings which way to orient the sensor.

 

If you want the sensor to be sensitive to the slightest movement, you can orient the box so that the ball is just touching the contacts.

 

If you really only want to know when there has been a major change, you can orient the ball in a position that is straight above, or under the senses. That way the ball will only change place if the whole box is upset.

 

If you want to know whether or not the box has been shaken about, you can look at the length of time that position of the ball stayed the same for. Say, for example, that it stays in the same position for 10 minutes, it is clearly not being shaken. If, on the other hand, it tilts one way and then the other every few minutes, it likely is being shaken.

 

There are a range of different sensors that can be applied in similar contexts. When you want to enter a shop, for example, a pressure pad signals the electronic doors to open.

 

The sketch you write will be pretty simple as this is a basic On/ Off situation.

 

 

Chasing the Light

 

What if what you want is to see when the light levels have changed? Maybe you want to be able to switch the lights on when the room becomes too dark to see in.

 

A simple solution is to connect an LDR or light dependent resistor. This detects changing levels in the light and responds by altering resistance. This can be measured by the board as a change in the levels of voltage.

 

For this to work, the LDR would need to be connected to an analog pin and an LED light would need to be connected as well.

 

Here it is important to know what the device you attach can do because there will never be a case when the voltage is not going to drop. This means that the voltage will never run up to the maximum that the power supply can handle.

 

If you understand this out the outset, you can plan accordingly so that the results given are more accurate.

 

A sketch like this will work for a number of different resistive sensors but you may need to change the resistor value to match the sensor better.

 

The complexity of the sensor required would depend on what you actually want to monitor.

 

 

How to Detect Motion

 

There are many reasons why you might want to build a motion sensor – you could, for example, connect them to security lights so that the lights come on if motion is detected.

 

Many easily obtainable sensors are easy to connect to your board. The key is in identifying the right pins to connect them to. You need to read through the data sheet that came with the sensor in order to find this information.

 

When setting up your motion detectors, the key to getting the kind of results that you want is in positioning the sensor correctly. Take the example of the motion sensor being used to switch on security lights.

 

If the sensor is placed aiming at the wrong level, you will pick up movement from family pets and kids as well and this can be annoying. Position the sensors high enough so that they are effective but also so that they don’t get triggered accidentally.

 

 

Measuring Distance

 

This is a fun application – you are going to measure the distance between the sensor and something else – like the nearest park car or a dog walking towards you.

 

Again, reading the data sheet that comes with your sensor is imperative here. You need to determine what the maximum range for your sensor is.

 

With ultrasonic sensors, the distance is measured by working out how long it has taken for the sound to echo back off the object in question.

 

The ping is sent out when the sensor is activated. (In the code this is where the pin receives voltage for a couple of split-seconds. This triggers the sensor to create a pulse. This pulse is cut off when the return wave is detected.

 

The system then works out how long it took the pulse to travel. It works out the distance by comparing this measurement to the speed of sound.

Chapter 5

 

The Different Types of Outputs

 

It is when it comes to visual outputs that the Arduino really becomes fun to work with. The board can be used in conjunction with a number of different LED devices.

 

Again, with visual output, you will use either digital or analog output.

 

 

Digital Output

 

Any pin that you use for input can be changed to give output instead. Essentially when it comes to digital output, there are two settings – Low or High. So you can choose to have the device on or off. This can be used to switch the lights on or off, for example.

You will need to use the command, pinMode(outputPin), or pinMode(inputPin).

 

 

Analog Output

 

Here you have more range – if you want the lights to be dimmed gradually, for example, you will need to use the analogWrite function. This is accomplished through the use of Pulse Width Modulation – it is not actually an analog signal but it acts in much the same way.

 

Pulse modulation will change up the time that the pulses are off in relation to the time that they are on. If you want a dimmer LED, for example, the pulses run for less time than they are off. If you want a brighter light, on the other hand, the pulses run for longer than the time than they are off.

 

Because we are usually talking about microseconds here, the sensors in our own eyes will not be able to detect that the light is actually pulsing. It will look like a solid light.

 

It is also important here to know that you won’t be able to use all the pins for analog output. On the standard Arduino board, you can only use the pins numbered 3, 5 ,6, 10 and 11. If you have a Mega board, you can use all the pins from number 2 through to number 13.

 

If you try to use other pins with the analogWrite function, your sketch will not work.

 

 

Varying the Levels of Light

 

This is an easy way to create an interactive device. You can choose from single lights, arrays of LEDS and or numeric displays. Displays for graphics and text on LCDs have to be handled differently, though.

 

 

Getting to Know Your LED

 

An LED is a basic diode that has two different leads – the cathode and the anode. When the device is receiving more positive voltage on the anode than what is received on the cathode, light is emitted.

 

You can normally identify the anode by the length of the lead – this will generally be longer on the on the anode lead. The housing for the cathode is normally marked with a flattened area.

 

What color the light is and what voltage it requires will differ depending on how the diode has been made. In addition to the diode, you will need a resistor to prevent the LED from burning out too quickly.

 

As always, it is a good idea to read through the data sheet for the LED device that you have chosen to ensure that you get the one best suited to your particular project. The maximum current that the LED can handle is important, as are the values required in terms of forward voltage. This is especially important so that you can choose the right resistor to use.

 

The pins on your board are able to give a maximum of 40 mA. This will work for your standard LEDs but won’t be enough for ones that run at a higher level of brightness. You will also only be able to run single LEDS off a single pin. If you need to increase the amount of current, a transistor can be added.

 

Multicolor LEDs will have more than one LED in the package. This may mean that you have more sets of leads to work with. The data sheet will be able to give you more details on how these should be connected.

 

There is a limit to what you can do when it comes to LEDS that have their own integrated chips. In these cases, the chip changes the colors and this cannot be overwritten by the Arduino board. If you are using a Pulse Wave Modulation, these are not the best choice because the chip will be constantly rebooted.

 

 

Maximum Pin Current

 

Where you also need to be careful is with LEDs that are able to draw in too much power for your chip. The chip can source a lot more mA of power than it is actually capable of handling. You need to take this into account when working out the maximum ratings.

 

If you are not careful in this insistence, your Arduino chip could get fried.

 

 

Practical Applications for LEDs

 

Arduino couldn’t have made it simpler to switch an LED on or off. You will find that the connection of an LED and running the sketch for it is one of the basic beginner lessons that most books on the subject contain.

 

 

A Series Resistor

 

The current to the LED needs to be controlled to prevent them from burning out. Some LED packages come with built-in resistors.

 

For those that do not, you will need to connect a resistor to each of the leads. In order to choose the right resistor for the job, you will need to know what voltage the pin will provide, what the forward voltage of the LED is and how much current you want the LED to have.

 

 

Audio Output

 

Arduino boards are not really built to produce sound themselves. If they are wired to a speaker though, they can make sounds.

 

It can do this simply by sending out pulses that create vibrations. The vibrations are what causes the sound.

 

The pitch can be altered by change the rate at which the pulses are sent out. A longer pulse will produce a lower frequency sound.

 

The software for the Arduino boards does have a function that enables them to make sounds. You will need to use the timers built into the hardware. The standard boards are not able to run more than one tone simultaneously and you can run into problems when the timer is being used for something else.

 

Knowing this upfront, you can plan your sketch accordingly and schedule functions that need to use the timer at a different time to when you are producing the tone.

 

It must be said, however, that the tones that are produced are of a very limited range and will sound hard and computer-generated. If you want to create actual music, you are going to need to add in external hardware.

 

Arduino is great at controlling the devices that can actually play music. Done this way round, you can recreate all the musical notes that you want.

You can also use Arduino to control an external device that is built to make sound.

Chapter 6

 

Breadboarding

 

Breadboarding is a technique that will take all your projects up a notch or two. You can just plug everything in and just hope for the best, but breadboarding adds that extra touch of organization that makes the design a lot more efficient.

 

A breadboard is kind of like a story board in a movie – you can arrange the pieces of your project on it and see if they work together and make sense. The breadboard looks like a piece of plastic with a lot of holes in it.

 

The breadboard is connected to your Arduino board and, instead of you having to solder the wires onto the pins, you plug them into the breadboard. This completes the circuit and allows you to test out the work you have done.

 

The advantage is that it doesn’t have to be permanent – if you want to change something, all you have to do is to unplug the wires and plug them into their new spots.

 

When you are happy with the work, you can record the layout, disconnect everything, remove the breadboard and solder everything in place or you can leave the breadboard as is.

 

Breadboards are all pretty similar. You can refer to your data sheet to find out more about how yours operates but most will have the following components:

 

1.  Ground bus strip: You can connect this to one of the GND pins on the Arduino. These strips will usually have black or blue markings.

 

1.  Power bus strip: You will connect your power supply here in order to power your strip. There are normally two strips that are not connected. Most power strips will have red markings.

 

1.  Terminal strips: These will be perpendicular in relation to your bus strips.

 

1.  Conductors: These strips are there to show you where the connector wires have been placed. You won’t be able to see the wires, just the conductors.

 

If you want to use the conductor, you will just plug the wire in one of the wires that need to be connected into one of the holes. Then connect the next wire in another of the holes along the same row.

 

Solderless breadboards normally do come with a strip of adhesive on them. This makes it easy to attach and secure to your project.

 

 

Getting Grounded

 

When it comes to electronics, the two vital things that you need to know how to deal with are how to power your project and how to ground it.

 

In an electrical circuit, the power wire controls where the electricity is sourced from and the ground wire controls where it returns to.

 

With the breadboard, this distinction is easy because the power section and the ground section of boards each have their own bus strips. This makes it very easy to power your circuit.

 

All you need to do is to plug the power supply into the relevant strip and the connect your ground bus strip up to your Arduino board’s GND pin.

 

 

When You Need Jumper Wires

 

When using a breadboard, you will usually use wires that are referred to as jumpers. All these are, are wires that are long enough to reach between the various connections.

 

You can easily make your own - bearing in mind that a solid wire is better for this purpose because it has less of a tendency to fray.

 

If you want to, you can buy premade jumpers. These have a connector pin already attached on either end. The advantage of buying the premade ones is that they will fit the holes in a breadboard perfectly and are built to be quite durable.

 

It is advisable, especially when starting out, to get premade jumpers with the connections already in place. You can also get short jumpers that are specially designed to lay flat against the board and are angled accordingly and these are very useful.

Chapter 7

 

Build Your Own Simple Robot

 

Let’s do something fun and cool – after all, that’s really what Arduino is all about. The project detailed below is a simple and made with the Funduino UNO Robotics Kit. The steps are basically the same for making any other robot so you can use a different kit or make up your own kit if you like.

 

 

Getting the Support in Place

 

Start by taking out the battery back. Put it face down, with the cable facing towards you.

 

Lay out the two servos and put them back to back lengthwise, with the shafts facing in opposite directions. Make sure that they are lined up properly.

 

The servos should be laid on top of the battery pack, so that one shaft is on either side of the pack. You need to align them with the edge of the battery pack that has the wire leading out of it and with the wires of the servos hanging clear of the pack.

 

So, if you are looking at it, the servo wires will be at the top edge of the battery pack, with the servos aligned to the same edge. The battery pack wire will be coming out of the right-hand side at the bottom. They will cover around about half of the battery pack and you will have space to put the breadboard next to the servos.

 

When you have the alignment right, secure with double-sided tape.

 

Make sure that the servos are firmly in place

 

Your robot’s chassis is now done.

 

 

Attaching the Arduino and the Breadboard

 

Attaching the breadboard comes next. Fit it in place next to the servos so that it is snugly aligned with them. Tape the breadboard down using adhesive tape.

 

The Arduino goes on next – it is going to be taped down directly on top of the servos. Try, as far as possible, to avoid too much overhang when it comes to the breadboard.

 

 

Your Robot’s Chariot Awaits

 

Now you get to make your robot mobile. Fit the wheels onto the shafts of the servos. It is going to require a bit of elbow grease – they are meant to fit on very snugly.

 

You now need to add a caster so that the breadboard section doesn’t drag on the ground. The caster should fit neatly under the breadboard, ensuring that the robot has enough clearance in front.

 

If the castors are not high enough, you can make yourself a spacer. This is easy to do – all you need is some scrap wood to make up the difference. Then attach the wood to the breadboard and attach the caster to the wood.

 

 

Wire Up Your Servo

 

You will need to find the long break away header. Cut away two of the 3-pin sections. Make sure that the plastic keeping the wires is properly centered. If not, you can gently move the plastic to rectify this.

 

Plug the headers into your breadboard, in the row directly under the halfway point of the board, all the way over to the left-hand side. Place them in the same row but separate them by a hole. You can now connect up the servo wires to the headers. Make sure that the black wires are on the left-hand side when connecting them.

 

Pick up the slack in the cord and fold it neatly. Use a small cable tie to keep the cord neat and out of the way.

 

Now you need will need to use the jumpers to connect the headers to the Arduino and to the rails on the breadboard.

 

Place a jumper that extends from the base of the header that the red wire is connected to, to the red rail on your board.

 

Place a jumper that extends from the base of the header that the black wire is connected to, to the blue rail of the board.

 

You now need to connect the Arduino. You will need longer jumpers to do this. Place a jumper that extends from the base of the header that the white wire is connected to, to the Arduino’s pins 12 and 13.

 

 

Placing the Sensor

 

Take the ultrasonic sensor and put in the center front of your robot. You are going to plug it into the body of your breadboard, not either of the rails.

 

Use jumpers to wire the sensor’s VCC pin. Connect it to the red rail closest to it. This will power the sensor.

 

Use jumpers to connect the sensor’s GND pin to the blue rail of breadboard. This will ground it.

 

The last step is to get a longer jumper and connect the sensor’s Trig to pin 8 on your Arduino and connect the sensor’s Echo to pin 9 on your Arduino.

 

 

I’ve Got the Power

 

It is not a good idea to use the Arduino’s pin to power the servos because they draw too much power. You can overcome this by attaching them directly to a battery pack – you can piggyback them on the same pack that you use for the Arduino or a new pack altogether.

 

The servos will require four AA batteries. To make sure that you attach the cables correctly, you need to put the robot on its side with the power cord from the battery pack at the bottom. In other words, if the robot is facing forward, place it on its right side.

 

Find the spring that is second from the left and attach the red wire to it. Find the last spring on the right and attach the black wire to it.

 

Now take the two wires that you just connected to the battery springs and plug them into the back power rail of your servo.

 

Take one of the black jumpers and connect one end to your Arduino’s GND pin and the other to the breadboard’s back GND rail.

 

Now connect the breadboards GND rails using a jumper. (You are not to do this with the red rails, though.)

 

Get a red jumper and wire it to the 5V pin on your Arduino board. Connect the other end to the breadboard’s front red rail.

 

 

Killing Your Robot

 

If you don’t add a kill switch, your robot is just going to keep on going until the batteries run flat.

 

Get out the push button switch and position it across the gap that defines the center of the breadboard.

 

Connect one half of the switch to the power rail on the front. Connect the other side to the GND rail using a 10kΩ resistor.

 

Connect the side of the switch that has the resistor attached to your Arduino board’s number 2 pin.

 

Now you are going to want to write a sketch that links each of the components and tells Arduino what to do with each.

 

Writing the code to go along with the robot is likely to take longer than actually putting it together.

 

You can download the sketch to run the robot from at [www.foxytronics.com/files/file/36-arduino-maze-solving-robot-code/](http://www.foxytronics.com/files/file/36-arduino-maze-solving-robot-code/) – it was created by Nathan House to work with the Funduino UNO Robotics Kit. If you have used a different kit, you can use this as an example for the kind of coding you will need to do.

Conclusion

 

There we go, all done. I hope you enjoyed this next step in your Arduino journey. I know that this is still only scratching the surface of what you can do with Arduino but you now have some more of the building blocks that you can learn from.

 

Arduino is fun and it was always meant to be. It is there to make it easier to get your wildest ideas from the drawing board stage to a physical prototype.

 

Knowing the basics of Arduino, like how to use, change and write your own sketches makes it possible for you to get your projects to work exactly right.

 

Knowing techniques like breadboarding makes this process a whole lot easier for you.

 

All in all, creating is about exploring, about pushing the limits of what you know and can do. Arduino is a great tool to help you do all those things.

 

Good luck with it!

Don’t forget to scroll down for your FREE GIFTS and for more info on my other books!

A message from the author, Steve Gold

 

To show my appreciation for your support, Id like to offer you a couple of exclusive free gifts:

 

FREE BONUS NUMBER 1!

As a free bonus, I’ve included a preview of one of my other best-selling books directly after this section. Enjoy!

 

FREE BONUS NUMBER 2!

For a limited time I’ve also included access to a FREE book which is ONLY available to my readers and can’t be found anywhere else. Don’t miss your chance to get it, along with exclusive access to more free books and exclusive discounts in the future! Simply follow the link below for instant access:

 

[\=>Click HERE to learn more! <=](http://eepurl.com/bMxlLr)

 

ALSO…

Be sure to check out my other books. Scroll to the back of this book for a list of other books written by me, along with download links.

 

Thank you again for your support.

 

Steve Gold

##### FREE BONUS!: Preview Of “Elon Musk - The Biography of a Modern Day Renaissance Man”!

![Elon Musk - Biography.jpg](images/00003.jpeg)

 

If you enjoyed this book, I have a little bonus for you; a preview of one of my other books “Elon Musk - The Biography of a Modern Day Renaissance Man”. In this book, I take a closer look at exactly who Elon Musk is as well as examining the truly extraordinary accomplishments he has managed to achieve. Enjoy the free sample, and feel free to click on the purchase link below if you would like to learn more about this truly incredible individual!

Introduction

 

When actor Robert Downey Jr. signed on to portray Tony Stark (a.k.a. Iron Man), he suggested to director John Favreau that they meet up with Elon Musk. They have a task of bringing to life a superhero, and Musk is the closest there ever is to Marvel’s genius, billionaire, philanthropist in real life. The meeting was set and some of Musk’s characteristics went into RDJ’s portrayal of Tony Stark on screen, thus creating the memorable character that people come to know and love.

 

In reality, there is far more to Musk’s life and person than can be personified by a fictional character. Sure, he does have a lot in common with Iron Man; he’s a prodigious tech genius and entrepreneur, with the capacity to make seemingly impossible ideas a reality. Like Tony Stark, he dreams, thinks and lives large, but that is where the similarity ends.

 

Unlike his comic book counterpart, Elon Musk was not born into a life of luxury and ease. Despite showing potential for greatness as early as his preteens, his childhood and young adult life was filled with adversaries. To this day, Musk credits his early life struggles in helping him cultivate the indomitable spirit he is known for.

 

Having made his mark in the field of IT, finance, sustainable energy, automotive, aerospace manufacturing and space exploration, it is an understatement to say that Musk has come a long way from his humble beginnings. He founded some of the most pioneering companies – Paypal, Tesla Motors, and SpaceX – and is almost single-handed responsible for each enterprise’s success. Whichever business he decided to dabble in, he brought with him a revolutionary idea which often ends up being a game-changer in the industry. Yet, he is far from done.

 

His brilliant mind never ceased to think up grander innovations, even after numerous repeated successful endeavors. His ample and wild ambitions, it seems, are driven by grand visions of changing the world we live in. His agenda for the future includes filling the roads with more electric cars, powering the world with solar energy, colonizing neighboring planets and enabling people to cover great distances with a futuristic high-speed public transportation system.

 

Most children would imagine of going outer space and travel to different cities in bullet-fast capsule pods, until those fantasies fade away in adulthood. Rarely are there individuals who dare to dream of living those fantasies that appropriately should stay within the realm of fiction. Elon Musk is among the exceptional few.

Chapter 1

 

The Beginnings Of Greatness

 

Almost every success story of high-achieving individuals contain episodes highlighting their extraordinary iron will, critical thinking, propensity for hard work, and an unwavering belief that the impossible is not out of their reach. As one of the most brilliant minds who help shaped the global economy after at the dawn of the information age and tech boom in the late 20^(th) century, it is hardly surprising that Elon Musk displayed such distinctive personality traits at an incredibly young age.

 

Elon Reeve Musk was born in June 28 of 1971, in Pretoria, Gauteng, South Africa. His father is a South African-born British electrical engineer, Errol Musk, and his mother is Canadian-English dietitian, Maye Musk. Elon is the eldest of their three children, followed by brother Kimbal and sister Tosca.

 

Growing up in Pretoria, Elon’s early years were far from a picture perfect childhood. His parents divorced when he was 9 years-old, after which he lived mostly with his demanding and emotionally abusive father. At school, he endured harsh bullying by his peers. In one notable instance, he ended up hospitalized after being pushed down a flight of stairs. Such ordeals led Elon to find solace in the safest company available; his own thoughts and imagination which resided in the deep recesses of his prodigious mind.

 

He would regularly immerse himself in reading as a means of escaping his troubles in the outside world. Encyclopedias and science fiction were among his favorite books; they added to his knowledge bank and encouraged his seemingly wild dreams of futuristic technology which had yet to become a reality. Often times, Elon would be caught daydreaming and lost in his own thoughts, ignoring the world around him in favor of the utopias in his imagination. Along with his innovative thoughts, Elon’s childhood experiences also contributed to him developing a high tolerance for hardship and an extraordinary work ethic; attributes which he is well known for and which have served him well in his life.

 

His aptitude for technological innovations and entrepreneurship was evident when he began teaching himself computer programming at the tender age of 10. When he was just 12, he developed a spaceship shooter video game called, “Blastar", which he sold to a computer magazine for $500. After his first brush with success, Elon and his younger brother, Kimbal, hatched a plan to open an arcade near their school. Unfortunately, their enterprising plan had to be scrapped when their parents refused to provide the legal consent to obtain a business permit.

 

In 1988, after graduating from Pretoria Boys High School at the age of 17, Elon made the momentous decision to leave his hometown for the United States, without the support of his parents. This would be the first step towards his hard-earned success. He was able to obtain Canadian citizenship through his mother a year later, and left South Africa for Montreal, Canada. There, he worked low-paying jobs and was living on the brink of poverty for a year.

 

At the age of 19, he was accepted into Queens University in Kingston, Ontario for undergraduate studies in science. It was during his studies that he met Canadian author, Justine Musk, whom he would marry in 2000 and end up having six sons with. Their marriage lasted for only eight years, and Elon got married for the second time to British actress Talulah Riley. This marriage ended in divorce in 2014.

 

Two years into his studies at Queens, Elon received a scholarship from The University of Pennsylvania (Penn) in America. He relocated to the US in 1992, following his transfer to Penn. In the following year, he earned his Bachelor of Science degree in Physics from Penn's College of Arts and Sciences, and stayed back a year at Penn's Wharton School to complete his studies for a Bachelor of Science degree in Economics.

 

Throughout his college years, alongside his scientific studies, Elon took a keen interest in philosophical and religious literature. It was stated that his all-time favorite book is The Hitchhiker’s Guide to the Galaxy by Douglas Adams. It is through this immersion in both science and personal studies of humanities that Elon found his calling; he had the lofty ambition of wanting to contribute to projects that would change the world for the better.

 

Consequently, his vision and entrepreneurial aspirations began taking shape, specifically in the areas of the internet, renewable energy and space exploration.

 

[Click here to check out the rest of “Elon Musk - The Biography of a Modern Day Renaissance Man” on Amazon.](http://amzn.to/1MBnmB9)

Or go to: [http://amzn.to/1MBnmB9](http://amzn.to/1MBnmB9)

# Check Out My Other Books!

![Elon Musk - Biography-1.jpg](images/00004.jpeg)

[Elon Musk - The Biography Of A Modern Day Renaissance Man](http://amzn.to/1MBnmB9)

![Elon Musk - Lessons.jpg](images/00005.jpeg)

[Elon Musk - The Business & Life Lessons Of A Modern Day Renaissance Man](http://amzn.to/1jpCQl7)

![Warren\_Buffett\_new.jpg](images/00006.jpeg)

[Warren Buffett - The Business And Life Lessons Of An Investment Genius, Magnate And Philanthropist](http://amzn.to/1LPu6kp)

![Steve Jobs Thumbnail.JPG](images/00007.jpeg)

Steve Jobs - The Biography & Lessons Of The Mastermind Behind Apple

![Management - .jpg](images/00008.jpeg)

[Management - Achieve Management Excellence & World Class Leadership Skills In 7 Simple Steps](http://amzn.to/1hFnU09)

 

![Sales\_new.jpg](images/00009.jpeg)

Sales - Easily Sell Anything To Anyone & Achieve Sales Excellence In 7 Simple Steps

![Arduino Thumbnail.JPG](images/00001.jpeg)

 

Arduino - Getting Started With Arduino: The Ultimate Beginner’s Guide

 

(If the links do not work, for whatever reason, you can simply search for these titles on the Amazon to find them. All books available as ebooks or printed books)