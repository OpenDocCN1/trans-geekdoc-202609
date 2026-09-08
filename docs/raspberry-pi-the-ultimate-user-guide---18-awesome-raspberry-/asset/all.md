   

 

 

 

 

 

Raspberry Pi:

The Ultimate User Guide - 18 Awesome Raspberry Pi Projects, Tips And Tricks For Absolute Beginners!

  
Table of contents

 

[Introduction](#part0000_split_002.html#_Toc436896387)

[Chapter 1 – First things First: Starting Off with Linux](#part0000_split_003.html#_Toc436896388)

[Chapter 2 – PI Photo Use](#part0000_split_004.html#_Toc436896389)

[Chapter 3 – Raspberry Pi Loves to Game](#part0000_split_007.html#_Toc436896390)

[Chapter 4 – Helpful Tips with Your Pi](#part0000_split_008.html#_Toc436896391)

[Chapter 5 – Tricks of the Trade](#part0000_split_009.html#_Toc436896392)

[Chapter 6 – Something to Get your Juices Flowing](#part0000_split_010.html#_Toc436896393)

[Conclusion](#part0000_split_011.html#_Toc436896394)

# Introduction

 

The Raspberry Pi is nothing short of a truly amazing powerhouse that gives you nearly limitless possibilities, and it’s not even all that expensive. Usually it can be purchased for somewhere between $30-40 USD for the base unit. 

Then you can add onto it just about anything you would find in any electronical device or gadget to create your own D-I-Y version of just about any out of the box item that would run you far more in terms of cost. 

The cost you end up paying for products straight of the box isn’t just monetary either, you actually give up a lot of control when you go with something already completely manufactured. 

When you start working with your Raspberry Pi and learning more and more coding the process opens up all sorts of avenues for you to create devices that are going to run exactly the way you want them to, when and how you want them to. 

Along with taking back control, many of the devices you can build can help you completely eliminate having to pay some of the monthly subscription fees that are associated with simple services. 

In one of the latter chapters you will see an example of using the Raspberry Pi to build your own personal Cloud drive that you can access anywhere you wish. No more having to pay for ridiculous storage fees that never give you anything concrete. 

This way you actually have control over how much space you have and at the end of the day you maintain complete ownership over all of the files. They are stored in your home. Not on some far away distant server. 

While the Raspberry Pi is great for teaching or learning different techniques to build your own devices, it really can stand on its own as a chip that can be used for serious projects that are anything but novice. 

For the sake of having to start somewhere, we’ll take a look at 18 different projects that, while they vary in purpose and range of skill level, they are still in the beginner category. 

But don’t worry, that doesn’t mean these beginner projects are going to be boring or useless. 

While some of the more advanced projects out there use the Raspberry Pi as a video game emulator to play retro games, or to build your own tablet using 3d printed materials and the aid of a Raspberry Pi, the individuals making those sort of projects had to start somewhere. That somewhere is starting off with a Linux operating system for most people. 

Currently there are other operating systems that you can run with the Raspberry Pi, but the most common and popular system you will find other programmers using is hands-down Linux. Linux is the programmer’s OS. 

If you find that it is a bit over your head, stick with it for a while. Learning code is a complete language all by itself. Thankfully there are all sorts of inside tips to writing code (some that we will actually cover a little later) that can make the transition from not speaking any code at all, to writing your own working programs. 

You may be wondering about your IOS or your Windows affiliation. Don’t worry there are new ways for utilizing both of these systems continually being unveiled by both companies. 

But for the most part, considering that Linux is open source, which runs parallel to the sub-culture behind creating many of the things you will be using your Raspberry Pi for, it remains to be one of the best OS to use. 

So that is where we will start. Then we will cover a few projects in depth, look over some great tips and tricks that you can use and in the end give you some more fuel for the fire to get your gears turning and your juices flowing. May the force be with you in all of your creations. 

 

# Chapter 1 – First things First: Starting Off with Linux 

 

When you bring your new Raspberry Pi home your mind may already be swimming with all sorts of possibilities on what you want to build and for good reason considering this chips versatility, but the first thing you are going to need is a decent operating system. 

The Raspberry Pi runs all of its software off of an SD card. If your chip came with one already, great. If not, then you will obviously need to get one. The general rule of thumb with memory is that more really is better. Just don’t go below 4GB. 

With your SD card in hand you are ready to go ahead and format it, download Linux, and begin to get the ball rolling. So easy huh? Actually, if you are new to Linux, you will soon discover that when you go to download this open source operating system that there are loads of different distributors. 

This is because people can make their own tweaks to the software and redistribute as is the standard for working with open source software. 

For the sake of your Raspberry Pi there are a few Linux distributions that were created specifically for the Raspberry Pi, and that work exceptionally well. One of the top number one distributors of Linux for the Pi is known as “Raspbian”. 

Raspbian actually offers special features for the Pi to help make it easier for you to do things like gaming. 

The Raspbian version comes with IDLE which is a python based programmer’s development tool, and also Scratch. If you are doing anything with gaming on down the road with with Pi explorations, this extra software is going to be as valuable as a game controller.

 The software is also packed with all sorts of extra little tools that give you aid in GPS tracking, GUI configuration, and even some extra hacking tools. 

Along with being made specifically for Raspberry Pi, Raspbian has become the standard for many of the different projects that you encounter, including the ones that we will discuss. 

This doesn’t mean that you have to go with Raspbian, you can go rogue all you want. But seriously, it’s probably best to save your creative juices for what you are going to actually use your Pi for. 

Once you’ve downloaded your Linux version from the internet onto your SD card you can go ahead and begin the process of testing it out on your Pi. 

The process requires a little bit of configuration but it really isn’t anything that causes too much of a headache. 

First, put the card into your Pi chip, hook your chip up to either a TV or monitor, and be sure to use some sort of power supply. 

You’ll also need a mouse and a keyboard. These can all be plugged right into the chip or you could use your home computer or a laptop to do all of these things for you. 

The configuration is sort of one deal gig. After the first time is over, it will all be set up the way you want it and you won’t really ever need to go to through this process again. 

On the configuration menu be sure to use all of your SD card’s available memory. This is not a default setting, so you will need to configure this. Also, you will want to be sure to configure it for full screen by disabling ‘OverScan’. 

Be sure to set your time zone. You also want to decide if you want the system to boot up in a windowing environment or not. Most people do. All you need to do is go to ‘Boot Behavior’ on the configuration menu and tell it to start desktop on boot. 

Now that you have your system configured you can Reboot your Pi to make sure it starts up the way you want, for many of us that was right in the desktop environment. 

Now you are ready to set your Pi up to the internet. Not only are some of the projects you will do overtime internet-dependent, you will want the ability to use the full range of your Pi chip. Internet setup can be done using either an Ethernet cable or a Wi-Fi adapter. The setup is super simple. 

For Ethernet you should pretty much be able to plug and play. You do need to make sure that the router on your home network is set up for Dynamic Host Configuration Protocol (DHCP). Odds are you are already in this mode which lets you log onto your network from any device that is able to see it. 

If you decide to go for Wi-Fi, the adapter that you get doesn’t have to be anything necessarily special or expensive. 

Nearly every model will work with the Pi, but you do need to take into consideration the large amount of power that running a Wi-Fi requires. Some of them may even need an external power source. 

The easiest way to run the configuration on your wireless adapter is to use the windowing environment where there is already an icon conveniently included in your version of Linux, at least if you went with Raspbian. 

The setup is typical of any wireless network setup and will require that you enter your password so be sure and have that handy. 

You will also be able to view your unique IP address for your Pi chip. You may want to write this down and store it somewhere for future reference. 

At this point you have the best of the basics down. You have installed an operating system and you have got your chip setup and ready for the internet. Now let’s take a look at some great projects that you can build. 

# Chapter 2 – PI Photo Use

 

Unlike your average boxed laptop or home computer, the Raspberry Pi is perfect for projects where you need the continual aid of a computer without the risk of it turning off. 

The Pi is great for building all sorts of sensors, video monitoring, and just about any passive monitoring configuration that needs a device dedicated solely to that one purpose. Now you can build your own home security system without the need to shell out a lot of money, no need to hire an outside company either. 

 

## Home Security Setup

 

To set up your basic home motion sensor detector you can purchase a PIR Motion Sensor made specifically for Raspberry Pi projects. Adafruit makes a great, low-cost model that offers coverage for up to 7 meters and minimal soldering of the header pins. 

You will also need to have some sort of speaker, Piezo makes a nice speaker that will be plenty loud if someone or thing sets off your alarm. You should also have an SD card for the setup and you will need a resistor, go with a 100-ohm model. 

To attach the parts, you can either use a breadboard to run the negative/positive rails, sensor, and speaker to your Raspberry Pi, or you can choose to wire them all directly into the Pi. 

The breadboard makes it so you don’t have to get involved with all of the soldering while you are building your prototype. Then if you decide you want to make things more permanent to your Pi, you can dive in and solder away. 

In terms of programming the code is relatively simple. 

Here is an example of some code script that you can use:

 
| 1 2 3 4 5 6 7 8 9101112131415161718192021222324252627 || import RPi.GPIO as GPIOimport time pir\_sensor = 11piezo = 7 GPIO.setmode(GPIO.BOARD) GPIO.setup(piezo,GPIO.OUT) GPIO.setup(pir\_sensor, GPIO.IN) current\_state = 0try:    while True:        time.sleep(0.1)        current\_state = GPIO.input(pir\_sensor)        if current\_state == 1:            print("GPIO pin %s is %s" % (pir\_sensor, current\_state))            GPIO.output(piezo,True)            time.sleep(1)            GPIO.output(piezo,False)            time.sleep(5)except KeyboardInterrupt:    passfinally:    GPIO.cleanup()  |
| --- | --- |

Use this to get your coding going. If for some reason it doesn’t work be sure to check your wiring. Also, feel free to toy around with different numerical settings in the code to adjust your different sleep and timer settings on the motion detector. 

You can also further develop this setup by adding a webcam and a wireless adapter so that your home security system actually sends you a notification via email including a snapshot of a trigger along with a link to the live fee of the webcam. 

Now you can have your complete remote viewing system in place in case something happens while you are out of your home. You even set the sensor up so that it only covers just the area of your desktop so that anybody that may be going beyond their boundaries is caught red-handed. 

It’s portable, no monthly service fee to handle the monitoring, and you built it yourself. It doesn’t get much better thn that in terms of home monitoring. 

If you ever wanted to you could even program it to call into the proper authorities with a pre-recorded message. Though, with a few wrong calls your apt to lose some respect. 

 

## Make Your Own Time Lapse Video

 

Have you ever seen those wonderful time lapse photos or videos and thought of making your own, only to realize that the costs of some of the equipment are well beyond your means? Well, Raspberry Pi is to the rescue again. 

To do this you pretty much only need to install a camera through the ribbon cable attachment. 

Your camera can be as basic or advanced as you like, but the good thing is that you drastically save on costs by building this all yourself. Once you have a camera set up the coding is as simple as setting the shutter release to go off on a variety of intervals. 

You pick the times you want it to go off and voilà, you have yourself a series of photos that you can then use to go ahead and create your own time-lapse videos. 

You can also use this same sort of setup to make great animations where the lapse in shutter release is set far enough apart to allow you to make the changes in your design necessary to generate the animation effect. 

 

 

# Chapter 3 – Raspberry Pi Loves to Game

 

One of the most popular uses off the Raspberry Pi is to make gaming emulators. The wide array of emulators that are being made today with the Raspberry Pi run the gambit of everything from actual arcade stick and button emulators to emulators that use Xbox controllers to plug directly into an HDMI monitor or television. 

You really can get as advanced as you want when it comes to building your emulator, the best thing about is that you can now play all of those old games that used to when you were a kid, and if you happen to be part of a younger generation, now you can see what all the hype is about with truly retro games. 

To keep things simple, you can start by purchasing a USB controller or joystick so that you don’t have to build your own right away. 

This way you can focus on getting your Raspberry Pi setup and running with the emulator of your choice. 

The setup is best done by using a program from RetroPie that you download and then install on your SD card for the Pi. Once you have the software on the card plug in your Pi chip and start up the device. 

The basic setup involves enabling SSH and then boosting your overlook. These are both options that you will see in the configuration of the program upon booting up and expanding the file. 

When you are done you will want to follow the prompts and reboot the system. Lastly you need to make sure that your Raspberry Pi has added ROMS. To do this you need to go into your network configuration and find your Raspberry device. 

When you open it up you will find the location to store your ROMS. You can also choose to go out and download actual FTP software to help you if you are unable to add it under your network settings. 

In terms of choosing which games you want to play there are as many different available (and free) emulators as there are gaming platforms. Nearly every different system has their own. 

For example, UAE4II gives you games for the wonderfully retro Commodore family, go to RetroArch to find an assortment of old Neo Geo, Intellivision, Nintendo, and original PlayStation 1 games. 

As this may be your first time using an emulator you will find that each emulator has a variety of settings that will need to be tinkered with until you find the right timing on your gameplay. 

You may experience certain lag where suddenly the screen will freeze up and perhaps completely miss your play, you simply need to adjust frame refresh rate or possibly even disconnect and reconnect to the server to boost your game play. 

Don’t simply give up if the game play doesn’t seem to be holding up to all the applause you’ve heard from emulator retro-gameplay. The hype is there for a reason, it’s a great way to play old games. Keep tweaking away until you get the right settings for you. 

There is not standard that is going to run on everybody’s game play across all devices and servers. Some people formulate all sorts of equations that are designed to help you calculate the exact numbers you need for your configuration. 

Instead of wasting your time with all the math, just start plugging different figures in until it works. You aren’t going to break the device or crash the server. 

Think of it like moving around the old rabbit ears on the television. If you don’t know what that saying means you may want to ask your folks. 

If video games aren’t quite your thing, but you still want to explore some of the joy that can be had with some simple programming and a great chip like the Raspberry Pi, look at what some of the awesome programmers have already done with setting up MIDI to work with their Christmas lights. 

The setup is simple in terms of arranging the MIDI player with the Raspberry Pi. The programming corresponds to controlling each strand of lights with a given note. 

You basically set it up to turn the switch on and off your note is either on or off.  Super basic programming with loads of opportunity to get highly detailed in terms of the way you place your lighting and how many notes you program the device to respond to. 

# Chapter 4 – Helpful Tips with Your Pi

 

Along your creative journey with your Raspberry Pi you are going to want to know some of these useful tips that will make working with your device even more of a cinch. 

If you are highly familiar with Linux and the different coding and scripting, then odds are you won’t need as many of these tips, but then again you probably wouldn’t be reading any of this if you are already well-versed in code and script. 

When you are writing out script there is actually a command that functions similarly to the autofill feature in search bars and on your cell phone’s messaging service. 

Only, this one is made specifically for coding. How great is that? When you are typing out prompts you can just type the first few letters and tap on the tab key. 

If the shell can figure out exactly what you are aiming for it goes ahead and gives it to you, but even better it gives you a rundown of all the other prompts that you could be aiming for. 

Definitely great regardless of your level of code writing. The less you have to memorize the better. 

You can also jump around your commands by simply pressing ctrl+E for the end, or ctrl+A for the beginning of the command. 

This is just like jumping to the beginning or ending of a word document by pressing ctrl+home or ctrl+end. 

If you haven’t ever worked with code up until now, those long strings of coding can get longer than the checkout lines on Black Friday. 

As your building your work you might want to take a screenshot just like you would on your pc or mac. 

The difference is you need to a little bit of ‘scrotting’ (you know, running the sudo apt-get install scot command), in order to get the digital content of the screen converted over into a PNG that can then be opened wherever you wish. 

You will encounter, if you haven’t already, a prompt that comes up when you are coding that says you have to be the ‘superuser’ in order to execute it. This horrible command is frustrating to say the least. You are the ‘superuser’! 

 

Thankfully there is the nice little tip that can get you out of that jamb anytime it happens to pop up. All you need to do is type “sudo !!” and then Pi will easily go ahead and follow through with executing your prompt just as if it were root. If you ever hear people referring to this command they call it ‘sudo bang bang’. 

# Chapter 5 – Tricks of the Trade

 

There are always tricks out there for every device to help you get more out of it, and you know for sure that a device made for hackers, designers, and programmers is going to have its fair amount of them. 

The interesting thing is that Raspberry Pi almost had a sixth sense in knowing that people were going to push it’s potential beyond the standard device’s limits. 

One of the first things you can do is completely overclock your Pi. It was actually made to do this. Well, not necessarily ‘made’ to do it, but you can do it without actually voiding your warranty. Try overclocking your PC and you can kiss that warranty goodbye. 

Another trick you can do anytime you are away from your Pi and need to gain access is simply to grab ahold of your IP address (remember you wrote it down earlier?) and then take that information to connect it. 

If you are using Windows you should use “PuTTY”, and on any other system is simply “ssh pi@\[your IP\]. Next thing you know you are up and running and able to connect to your device from anywhere you need. 

Recently Windows (sorry Linux fans) opened up the ability to use Windows 10 as an operating system to pair your Pi with different software applications. 

This opens up a whole new slew of possibilities for using your device with a wide assortment of universal applications. 

Even if you avoid windows like the plague, this may be time to put on your hazmat suit and gear up for pushing your creativity and utilities to brand new horizons. Now you can use Visual Studio. And yes, you can even build your own and use others apps straight out of the PC now. 

A simple trick to also help you out on your Raspberry Pi endeavors isn’t anything super huge or wildly hidden, in fact it’s complete common sense (a thing most of us happen to lack from time to time). 

You may have realized by now that the SD card is your home for storage in terms of all the programming and purpose of what you are actually running the Raspberry Pi for. 

You can imagine over time that you are going to build up quite a catalogue of SD cards. Instead of having to continually put them into your reader to figure out what is on them here’s a trick: label them. 

In all seriousness, this is not to suggest that you aren’t organized or that you don’t know how to label things, but it happens to the best of us, and the little extra moment of labeling will save a lot of frustration down the end, especially if you have 20 cards to leaf through. 

If you want to save yourself another extra step in terms of organization, instead of labeling the cards with what is actually on them, label them alpha-numerically. 

Then you can create a separate document, or grab some good old-fashioned pen and paper and make a list of all the coordinating software and script contained on each card. 

This way if you ever wipe the card clean to rebuild it you can just change your database, without needing to worry about relabeling. 

 

 

# Chapter 6 – Something to Get your Juices Flowing

 

You know you have a world of infinite potential in front of you with your new Raspberry Pi, but knowing what to do with it can be a bit daunting when you are new to the games. 

Especially considering that for so many years you may have been consumed by thinking inside of the box, the store bought one that is. Now you are in a wide open field limited only by your imagination. 

Here are some ideas to get your juices flowing and hopefully set you on the course to building something truly unique with your own design in mind. Who knows you could be on to the coolest invention since the toaster. 

You can build your own jukebox. One up this by setting up your music to stream from an online streaming service. Build your box with an AirPlay receiver and suddenly you can broadcast it around on an FM channel. Who needs Sirius now?

Just because it’s small doesn’t mean it’s limited. Many programmers are using the Raspberry Pi to set up their very own fully functioning computer. 

This sort of project is definitely not for the impatient or person with shallow pockets.

It can require a lot of processor which is going to cost some money, but if you want to have full control over everything in your computer, why not take the bull by the horns and build your own from the ground up? 

Speaking of building from the ground up, why not go ahead and construct your own personal web server. 

Now you can take it anywhere you go. It’s an in-depth complicated process but if you are serious about your own security and ability to retain your access wherever you go, this sort of project is going to be right up your alley. 

Cloud service is everywhere now. Unfortunately, you give up a lot of control by using hosted services, as well as a certain monthly fee if you want any sort of serious professional level of storage. 

Why not go ahead and build your own personal cloud storage? You have to invest in buying the actual storage, but at least it’s a one-time purchase and the actual storage is yours to own, forever. 

Build your own home arcade studio. Build your own powered and framed digital wall art gallery. Build your own digital musical equipment. 

You can do just about anything, and one of those things happens to be hacking. We haven’t covered hacking for a couple of different reasons. 

One is that even though the Raspberry Pi chip is great at hacking software, that sort of knowledge in the wrong hands can truly be used for destructive and self-serving ends. 

If we knew everyone would use it for the greater good of all of humanity it would be great. Hacking can definitely be used for good though, and many hackers have found Raspberry Pi perfect for its extreme portability. 

You can essentially set up so that you have an encased computer with a touch screen display the size of the palm of your hand that can access a computer anywhere you go. 

Perfect for helping people on the go, also perfect for getting into places where you truly don’t belong. If you are going to use your Raspberry Pi for snooping around don’t be surprised at what sort of trouble you can get into. Both personally and legally. 

# Conclusion

 

Learning some coding isn’t going to hurt you, but there are tons of people out there that have already done all the coding and embedded it into links available for free. 

The Raspberry Pi community is great for helping each other out when in programming need. This could all be due to the fact that there is something amazing and inherent to the process of going against the big-company, multi-zillionaire corporations, and building your own devices. 

The grassroots sort of, D-I-Y community that constitutes a large portion of the Pi ecosphere is hands-down an inclusive group that aims to help others fine-tune all of the little bugs until your Pi project works the way you want it to. You may find that some individuals are more secretive about their projects. 

Maybe they too are wanting to be a self-made zillionaire someday off of their inventions, but for the most part the whole culture surrounding Pi, is a community build on sharing and bypassing the commodity of knowledge. Or at least those seeking to capitalize off of their code. 

Hopefully now you have at least got your OS all geared up on your Pi and a few projects to start working on right away. When in doubt just stick to using a breadboard that way you can make any changes easier. 

It also jus helps you move a little quicker in terms of building, which can be great when you are first starting out. 

Also if you are working on a project like the Synced Holiday Lights mentioned earlier you are probably going to end up putting all of your electronics in some sort of casing. 

In the case of the lights, you end up with a lot of wires. Using a breadboard while you are working on where everything will go, will make it easier to switch things around a bit if you need to in order to get them to suit your case.