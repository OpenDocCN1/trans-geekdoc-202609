
as bash, telnetd, ls, cp, and such, a smaller monolithic program called busybox is typically used. Busybox 14 provides the functionality within a single executable by using the first argument as the desired program. Although I’d like to say that unused services are removed to reduce the attack surface, they are likely only removed to save space.

Although most devices do not intentionally provide console access to the user, many do have a serial port for console access on the board. As soon as you have access to the root file system, either via the console or by extracting the image from storage, you will want to look for the versions of applications and libraries, world-writable directories, any persistent storage, and the initialization process. The initialization process for Linux, found in /etc/inittab and /etc/init.d/rcS, will give you an idea of how the applications are started on boot.

## Summary

In this chapter, we briefly discussed the differences between different CPU packages (microcontroller, microprocessor, and SoC), several serial interfaces of interest, JTAG, and embedded software. In our discussion of serial interfaces, you were introduced to the JTAGulator in an example of discovering UART (serial) ports. JTAGulator can also be used to discover JTAG debug ports and potentially several other interfaces. We also briefly discussed different software use cases, including bootloaders, no OS, an RTOS, and a general OS. At this point, you should have a common vocabulary for embedded systems and a few areas of concern when attempting to gain a further understanding.

## For Further Reading

- ARM:
  - https://developer.arm.com/products/architecture/a-profile
  - https://www.arm.com/products/processors/cortex-a?tab=Resources
  - https://developer.arm.com/products/architecture/r-profile
  - https://www.arm.com/products/processors/cortex-r?tab=Resources
  - https://developer.arm.com/products/architecture/m-profile
  - https://www.arm.com/products/processors/cortex-m?tab=Resources

- Bus Pirate http://dangerousprototypes.com/docs/Bus_Pirate

- Embedded Linux https://www.elinux.org/Main_Page

- Firmware extraction and reconstruction https://www.j-michel.org/blog/2013/09/16/firmware-extraction-and-reconstruction

- Firmware security information https://github.com/advanced-threat-research/firmware-security-training

- Free RTOS https://www.freertos.org/

- I2C https://learn.sparkfun.com/tutorials/i2c

- JTAG:
  - http://blog.senr.io/blog/jtag-explained
  - https://developer.arm.com/docs/dui0499/latest/arm-dstream-target-interface-connections/signal-descriptions/serial-wire-debug

- JTAGulator www.grandideastudio.com/jtagulator/

- MT-7621A:
  - https://www.mediatek.com/products/homeNetworking/mt7621n-a
  - https://wikidevi.com/wiki/MediaTek_MT7621

- OpenOCD http://openocd.org/

- Reverse-engineering VxWorks firmware www.devttys0.com/2011/07/reverse-engineering-vxworks-firmware-wrt54gv8/

- SPI https://www.maximintegrated.com/en/app-notes/index.mvp/id/3947

- Understanding ARM HW debug options https://elinux.org/images/7/7f/Manderson5.pdf

- VxWorks https://www.windriver.com/products/vxworks/

## References

- 1. OR Gate, Wikipedia, https://en.wikipedia.org/wiki/OR_gate.
- 2. “ARM Architecture Profiles,” ARM Developer, http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0471i/BCFDF FGA.html.
- 3. “Completion of Sale of MIPS,” Imagination, October 25, 2017, https://www.imgtec.com/news/press-release/completion-of-sale-of-mips/.
- 4. “Serial Peripheral Interface (SPI),” Sparkfun, https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi.
- 5. “Serial Peripheral Interface Bus, SPI Standards,” Wikipedia, https://en.wikipedia.org/wiki/Serial_Peripheral_Interface_Bus#Standards.
- 6. “SPI,” https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi.
- 7. “I2C—What's That?,” Wikipedia, I2C, https://www.i2c-bus.org/.
- 8. Joint Test Action Group, Wikipedia, https://en.wikipedia.org/wiki/JTAG.
- 9. “JTAG Pinouts,” JTAG Test, www.jtagtest.com/pinouts/.
- 10. “JTAG Pin Descriptions,” ARM DS-5 DSTREAM System and Interface Design Reference Guide Version 5, https://developer.arm.com/docs/dui0499/latest/arm-dstream-target-interface-connections/the-arm-jtag-20-connector-pinouts-and-interface-signals/arm-jtag-20-interface-signals.
- 11. “Structure of the SWJ-DP” (JTAG/SWD Coexist as SWJ-DP), ARM Developer, http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.ddi0314h/Chdjjbcb.html.
- 12. “10-Way Connector Pinouts” (SWD/JTAG 10 Pin), ARM Developer, http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.ddi0314h/Chdhbiad.html.
- 13. “20-Way Connector Pinouts Including Trace” (SWD/JTAG 20 Pin), ARM Developer, http://infocenter.arm.com/help/topic/com.arm.doc.ddi0314h/Chdfccbi.html.
- 14. “BusyBox: The Swiss Army Knife of Embedded Linux,” BusyBox, https://busybox.net/about.html.

## Exploiting Embedded Devices

This chapter covers the topic of exploiting embedded devices. This topic is becoming increasingly important with the emergence of the Internet of Things (IoT), as covered in previous chapters. From elevators to cars, toasters, and everything “smart,” embedded devices are becoming ubiquitous, and the security vulnerabilities and threats are becoming innumerable. As Bruce Schneier has observed, it is like the Wild West of the 1990s all over again; everywhere we look, there are vulnerabilities in these embedded devices. Schneier explains that this is because of many factors, including the limited resources of the devices themselves and the limited resources of the manufacturers in the low-margin field of producing embedded devices.¹ Hopefully, more ethical hackers will rise to meet this challenge and make a dent in the tide of vulnerabilities of embedded devices. To that end, in this chapter, we discuss the following topics:

- Static analysis of vulnerabilities in embedded devices
- Dynamic analysis with hardware
- Dynamic analysis with emulation

## Static Analysis of Vulnerabilities in Embedded Devices

Static analysis of vulnerabilities involves looking for vulnerabilities by inspecting the update packages, file systems, and binaries of the system without having to power up the device being evaluated. In fact, in most cases, the attacker doesn’t need to have the device to do most of the static analysis. In this section, you are exposed to some tools and techniques for conducting static analysis on an embedded device.

## Lab 24-1: Analyzing the Update Package

In most cases, the update packages for the device can be downloaded from the vendor site. Currently, most updates are not encrypted and therefore can potentially be deconstructed with various tools such as unzip, binwalk, and Firmware Mod Kit. For instruction purposes, we will look at a Linux-based system since you are most likely familiar with these systems.

In Linux-based embedded systems, the update packages often contain a new copy of all the essential files and directories required to operate the system. The required directories and files are referred to as the root file system (RFS). If an attacker can gain access to the RFS, they will have the initialization routines, web server source code, any binaries that are required to run the system, and possibly some binaries that provide the attacker with an advantage when attempting to exploit the system. For example, if a system uses Busybox and includes the telnetd server, an attacker might be able to leverage the Telnet server to provide remote access to the system. Specifically, the telnetd server included in Busybox provides an argument that allows it to be invoked without authentication and bind to any program (/usr/sbin/telnetd -l /bin/sh).

As an example, we will investigate an older version of the D-Link DAP-1320 wireless range extender’s firmware update (version 1.1 of the A hardware). This update was chosen because it is an older update that has been patched, and the vulnerability disclosure (www.kb.cert.org/vuls/id/184100) was reported by several of the authors.

![](img/5f597c6a70133069118d9e804ace3775_660_0.png)

The first step is to create the environment for deconstructing the firmware. In our case, we will use the Firmware Mod Kit. The base host system for our analysis is Kali Linux 2017.1. In order to install the Firmware Mod Kit, the prerequisites must first be installed using the package manager apt-get ①. Once the prerequisites are met, the install only requires cloning the project from GitHub ②. The first time extract-firmware.sh is run, it compiles the necessary tools and results in a lot of output (the first run has been omitted in the example). We then attempt to extract the firmware ③, and if the package and content types are known by the tool, they will be extracted for further analysis. From the output, we can see that the tool has found both an MIPS Linux kernel image ④ and a squashfs file system ⑤, and they have been successfully extracted to the fmk directory ⑥. By browsing the extraction, we identify it to be the rootfs ⑦ and verify that the binaries are compiled for MIPS ⑧.
