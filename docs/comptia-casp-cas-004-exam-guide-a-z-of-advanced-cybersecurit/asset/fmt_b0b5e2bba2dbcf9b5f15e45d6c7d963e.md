
# Reverse Engineering Tools

Reverse engineering may be used to solve a variety of security problems. When a host is breached, reverse engineering techniques may be used to determine the facts of the breach, including how the attacker gained access to the system and the measures taken to breach the system. When used to malware, reverse engineering may also refer to the use of tools to break down malware in order to understand its purpose and how to destroy it; when applied to malware, reverse engineering is done in a sandbox environment to prevent the virus from spreading. Reverse engineering tools are recommended for analyzing *zero-day malware* and sandboxing it, as well as when a host has been hacked and safely isolated and you want to uncover specifics of the breach to be better prepared for the future. The *Infosec Institute* recommends the following as the top reverse engineering tools for cybersecurity professionals:

## Top Reverse Engineering Tools

*   `Apktool`: This third-party tool for reverse engineering can decode resources to the nearly original form and re-create them after making some adjustments.
*   `dex2jar`: This lightweight API is designed to read the Dalvik Executable (`.dex`/`.odex`) format. It is used with Android and Java `.class` files.
*   `diStorm3`: This tool is lightweight, easy to use, and has a fast decomposer library. It disassembles instructions in 16-, 32-, and 64-bit modes. It is also the fastest disassembler library. The source code is very clean, readable, portable, and platform-independent.
*   `edb-debugger`: This is the Linux equivalent of the famous Olly debugger on the Windows platform. One of the main goals of this debugger is modularity.
*   `Jad debugger`: This is the most popular Java decompiler ever written. It is a command-line utility written in C++.
*   `Javasnoop`: This Aspect Security tool allows security testers to test the security of Java applications easily.
*   `OllyDbg`: This is a 32-bit, assembler-level analyzing debugger for Microsoft Windows. Emphasis on binary code analysis makes it useful in cases where the source is unavailable.
*   `Valgrind`: This suite is for debugging and profiling Linux programs.

# Physical Security Tools

As stated earlier in this chapter, without physical security, other forms of security are useless. We end this chapter with several host physical security assessment tools.

## Lock Picks

Lock picks are tools used to test the ability of your physical locks to withstand someone picking them. These are the same tools used by a professional locksmith to open a lock when hired to do so and one of the reasons many organizations have moved away from using physical locks. [Figure 13.23](#c13.xhtml#fig13_23) shows examples of some lock picks; if a facility uses physical locks, the locks should be checked to see if they are susceptible to these tools; it may even be advisable to hire a locksmith to attempt to open them:

![Lock Picks](images/Image28334.jpg)

**Figure 13.23:** Lock Picks

## Locks

Door locks can be either mechanical or electronic. Electric locks, or cipher locks, use a keypad that requires the correct code to open the lock. These are programmable, and organizations that use them should change the codes frequently. Another type of door security system is a proximity authentication device, with which a programmable card is used to deliver an access code to the device either by swiping the card, or in some cases, by just being in the vicinity of the reader. These devices typically contain the following **electronic access control** (`EAC`) components:

*   An electromagnetic lock
*   A credential reader
*   A closed-door sensor

Locks are also used in places other than doors, such as protecting cabinets and securing devices. The types of mechanical locks with which you should be familiar are as follows:

### Warded Locks

This type of lock has a spring-loaded bolt with a notch in it. The lock has wards, or metal projections, inside the lock with which the key will match to enable opening the lock. A warded lock design is shown in [Figure 13.24](#c13.xhtml#fig13_24):

![Warded Lock](images/Image28341.jpg)

**Figure 13.24:** *Warded Lock*

### Tumbler Locks

This type of lock has more moving parts than the warded lock, and the key raises the lock metal piece to the correct height. A tumbler lock design is shown in [Figure 13.25](#c13.xhtml#fig13_25):

![Tumbler Lock](images/Image28351.jpg)

**Figure 13.25:** *Tumbler Lock*

### Combination Locks

This type of lock requires rotating the lock in a pattern that, if correct, lines the tumblers up, opening the lock. A combination lock design is shown in [Figure 13.26](#c13.xhtml#fig13_26):

![Combination Lock](images/Image28359.jpg)

**Figure 13.26:** Combination Lock

In the case of device locks, laptops are the main item that must be protected because they are so easy to steal. Laptops should never be left in the open without being secured to something solid with a cable lock—a vinyl-coated steel cable that connects to the laptop and locks around an object.

## RFID Tools

Malicious individuals use **Radio-frequency identification** (`RFID`) tools to steal the proximity badge information from an unsuspecting employee who physically walks near the concealed device. One example is the `Tastic RFID Thief` by Bishop Fox. Specifically, it targets 125 KHz, low-frequency `RFID` badge systems used for physical security, such as those used in HID Prox and Indala proximity products. Alternatively, it could be used to weaponize a 13.56 MHz, high-frequency `RFID` reader, like those for HID iCLASS access control systems. When `RFID` systems are in use, penetration tests should include testing the vulnerability of systems to the capture of such `RFID` credentials as their capture could lead to serious physical security issues.

## IR Camera

An infrared camera is a camera that forms an image using infrared radiation and can capture images in the dark. These cameras can also detect motion in the area, making them a great choice. When physical security assessments are performed, these devices should be fully tested to ensure that they capture all intrusion attempts.

# Conclusion

This chapter discussed various tools, related to the security assessment of network tools. This chapter presented a brief on the different Host related tools to assess vulnerabilities that might be present on an individual host. Such tools include password crackers, vulnerability scanners, command-line tools, local exploitation tools and frameworks, SCAP tools, file integrity monitoring utilities, log analysis tools, antivirus, and reverse engineering tools. Physical security tools devices to assess the security of an environment, including lock picks, `RFID` tools, and IR cameras were discussed.

In the next chapter, we will discuss *remote access* and *unified collaboration*.

# Chapter 14: Securing Communication and Collaborative Solutions

## Introduction

Increasingly, workers and the organizations for which they work are relying on new methods of communicating and working together that introduce new security concerns. As a CASP candidate, you need to be familiar with these new technologies, understand the security issues they raise, and implement controls that mitigate the security issues. This chapter describes these new methods and technologies, identifies issues, and suggests methods to secure these new workflow processes.

## Structure

In this chapter, we will discuss the following topics:

*   Remote access
*   Unified collaboration

## Objectives

After studying this chapter, you will be able to understand the following:
