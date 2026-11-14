
to identify, protect, and defend your *things* and those of your friends, family, and clients.

## For Further Reading

- “Distinguishing Internet-Facing Devices using PLC Programming Information” https://www.hsdl.org/?abstract&did=757013
- Internet of Things Scanner by BullGuard https://iotscanner.bullguard.com/
- NIST Special Publication 800-82, Revision 2, “Guide to Industrial Control Systems (ICS) Security” http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-82r2.pdf
- “Quantitatively Assessing and Visualizing Industrial System Attack Surfaces” https://www.cl.cam.ac.uk/~fms27/papers/2011-Leverett-industrial.pdf

## References

- 1. X. Xu, “Internet of Things in Service Innovation,” *The Amfiteatru Economic Journal*, 4(6, November 2012): 698–719.
- 2. M. Swan, “Sensor Mania! The Internet of Things, Wearable Computing, Objective Metrics, and the Quantified Self 2.0,” *Journal of Sensor and Actuator Networks*, 1(3, November 8, 2012): 217–253.
- 3. D. Evans, “The Internet of Things How the Next Evolution of the Internet Is Changing Everything [Internet],” Cisco, April 2011, https://www.cisco.com/c/dam/en_us/about/ac79/docs/innov/IoT_IBSG_0411FINAL
- 4. *The Economist*, “The Internet of Things (to Be Hacked),” July 12, 2014, https://www.economist.com/news/leaders/21606829-hooking-up-gadgets-web-promises-huge-benefits-security-must-not-be.
- 5. A. Harper, “The Impact of Consumer Security Awareness on Adopting the Internet of Things: A Correlational Study,” Dissertation, Capella University, 2016, https://pqdtopen.proquest.com/doc/1853097232.html?FMT=ABS.
- 6. D. Bandyopadhyay, J. Sen, “Internet of Things: Applications and Challenges in Technology and Standardization,” *Wireless Personal Communications*, 58(1, May 2011): 49–69.
- 7. Harper, “The Impact of Consumer Security Awareness on Adopting the Internet of Things.”
- 8. Z. Chen, F. Xia, T. Huang, F. Bu, and H. Wang, “A Localization Method for the Internet of Things,” *The Journal of Supercomputing*, 63(3, March 2013): 657–674.
- 9. H. Jayakumar, K. Lee, W. Lee, A. Raha, Y. Kim, and V. Raghunathan, “Powering the Internet of Things,” in *Proceedings of the 2014 International Symposium on Low Power Electronics and Design*, ACM, 2014, 375–380, http://doi.acm.org/10.1145/2627369.2631644.
- 10. Zigbee, Wikipedia, 2017, https://en.wikipedia.org/w/index.php?title=Zigbee&oldid=809655996.
- 11. Harper, “The Impact of Consumer Security Awareness on Adopting the Internet of Things.”
- 12. H. Jayakumar, et al., “Powering the Internet of Things.”
- 13. J. Sarto, “ZigBee VS 6LoWPAN for Sensor Networks,” LSR, https://www.lsr.com/white-papers/zigbee-vs-6lowpan-for-sensor-networks.
- 14. S. Schneider, “Understanding the Protocols Behind the Internet of Things,” Electronic Design, October 9, 2013, www.electronicdesign.com/iot/understanding-protocols-behind-internet-things.
- 15. J. Matherly, Complete Guide to Shodan: Collect. Analyze. Visualize. Make Internet Intelligence Work for You, Lean Publishing, 2017.
- 16. V. Pasknel, “Hacking the IoT with MQTT,” Morphus Labs, July 19, 2017, https://morphuslabs.com/hacking-the-iot-with-mqtt-8edaf0d07b9b.
- 17. Pasknel, “Hacking the IoT with MQTT.”
- 18. Pasknel, “Hacking the IoT with MQTT.”
- 19. Mirai (malware), Wikipedia, 2017, https://en.wikipedia.org/w/index.php?title=Mirai_(malware)&oldid=807940975.
- 20. S. M. Kerner, “DDoS Attacks Heading Toward 1-Terabit Record,” eWEEK, September 25, 2016, www.eweek.com/security/ddos-attacks-heading-toward-1-terabit-record.
- 21. Mirai (malware), Wikipedia.
- 22. Kerner, “DDoS Attacks Heading Toward 1-Terabit Record.”
- 23. C. Farivar, “Computer Science Student Pleads Guilty to Creating Mirai Botnet,” Mirai | Tim’s Tablet Web Site, October 13, 2017, http://tablets.yourfree.wordpress.com/?tag=mirai.
- 24. B. Krebs, “New Mirai Worm Knocks 900K Germans Offline,” Krebs on Security, November 16, 2016, https://krebsonsecurity.com/2016/11/new-mirai-worm-knocks-900k-germans-offline/.
- 25. M. Mimoso, “Mirai Bots More Than Double Since Source Code Release,” October 19, 2016, https://threatpost.com/mirai-bots-more-than-double-since-source-code-release/121368/.
- 26. T. Fox-Brewster, “A Massive Number of IoT Cameras Are Hackable—And Now the Next Web Crisis Looms,” Forbes, October 23, 2017, https://www.forbes.com/sites/thomasbrewster/2017/10/23/reaper-botnet-hacking-iot-cctv-iot-cctv-cameras/.

## Dissecting Embedded Devices

This chapter provides a high-level view of embedded devices with the intention of providing a vocabulary for and high-level understanding of potential areas of concern. Embedded devices are electrical or electro-mechanical devices that meet a specific need or have a limited function. A few examples of embedded devices include security systems, network routers/switches, cameras, garage door openers, smart thermostats, controllable light bulbs, and mobile phones. As our devices gain remote connectivity for our convenience, they also provide more opportunity for an attacker to enter our lives through our networks.

Much of the discussion in this chapter revolves around integrated circuits (ICs). An IC is a collection of electrical components within a small package, often referred to as a _chip_. A simple example is the quad 2-input OR<sup>1</sup> gate IC, where four 2-input OR circuits are implemented inside a single chip. In our case, the ICs will be much more complex and contain the entire multiple-computing elements inside a single IC. Also, note that this chapter assumes you are familiar with a multimeter and the basic concepts of electrical circuits, such as voltage, current, resistance, and ground.

In this chapter, we discuss the following topics:

- CPU
- Serial interfaces
- Debug interfaces
- Software

### CPU

Unlike the desktop systems that most people are familiar with, the embedded world uses many different processing architectures based on embedded functionality, required complexity of the system, price, power consumption, performance, and other considerations. Because embedded systems generally have much more defined functionality, they tend to lend themselves to more quantifiable performance requirements. As a result, a blend of software and hardware requirements are used to determine the appropriate microprocessor, microcontroller, or system on chip (SoC).

### Microprocessor

Microprocessors do not include memory or program storage internal to the chip. Microprocessor-based designs can utilize a large amount of memory and storage and can run sophisticated operating systems such as Linux. The common PC is an example of a device utilizing a microprocessor-based design.

### Microcontrollers

Common to the embedded world is the microcontroller. The microcontroller generally has a CPU core (or cores), memory, storage, and I/O ports, all within a single chip. The microcontroller is well suited to highly embedded designs that perform simple or well-defined lower-performance applications. Due to the simplicity of the applications and hardware, the software on the microcontroller is typically written in a lower language such as assembly or C and does not include an operating system (OS). Applications for a microcontroller include an electronic door lock and a TV remote.

Depending on the specific microcontroller, protections may be implemented in hardware to help secure the applications. Examples are read protections for the program storage and disabling the on-chip debugging interface from becoming active. Although these protections provide a layer of protection, there are no guarantees that the protections cannot be bypassed.

### System on Chip (SoC)

The SoC is one or more microprocessor cores or microcontrollers with a wide variety of integrated hardware features within a single IC. For example, the SoC for a phone may contain a Graphics Processing Unit (GPU), sound processor, Memory Management Unit (MMU), cellular, and network controller. The main benefit of the SoC is reduced cost due to fewer chips and smaller-size applications. These are typically used in a more custom fashion. Whereas the microcontroller stores the program internally and provides limited memory, the SoC typically utilizes external storage and memory.

### Common Processor Architectures

Although there are many microcontroller architectures, such as Intel 8051, Freescale (Motorola) 68HC11, and Microchip PIC, two architectures show up much more in Internet-connected devices: ARM and MIPS. Knowing the processor architecture is important when using tools such as disassemblers, build tools, and debuggers. Identification of the processor architecture can typically be done by visually inspecting the board and locating the processor.

ARM is a licensed architecture that is used by many microprocessor, microcontroller, and SoC manufacturers such as Texas Instruments, Apple, Samsung, and more. The ARM cores are licensed in multiple profiles based on the intended applications. ARM cores come in both 32- and 64-bit architectures and can be configured as either big or little endian. Table 23-1 illustrates the profiles and applications that would typically use them.
