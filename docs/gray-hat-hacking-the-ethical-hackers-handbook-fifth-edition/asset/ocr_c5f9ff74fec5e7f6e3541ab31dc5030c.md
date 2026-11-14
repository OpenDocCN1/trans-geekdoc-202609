# Setting Up the Threat Lab

Traditional malware runs in Windows environments, and tools like sandboxes and virtual machines already support these systems transparently. However, when dealing with IoT malware, two different architectures are put into place that are far from being supported transparently. These two architectures are ARM and MIPS, and in this section, we discuss multiple options for emulating those environments in what we’ll call our “threat lab.” As a quick overview, here are the different ways to get a system up and running for the ARM and MIPS architectures:

+   - Use a QEMU (short for “Quick Emulator”). QEMU is an open source machine emulator and virtualizer. This is the most common way to emulate the ARM and MIPS architectures, and it’s very convenient for malware analysis because snapshots can be used to avoid permanent changes in the hard disk.
+   - Use a development platform such as BeagleBone or Raspberry Pi. Although not recommended for malware analysis, sometimes you need to run the malware in a real environment. The good news is that these boards can always be reimaged if needed.
+   - Use a sandbox such as the Cuckoo sandbox. Cuckoo can be customized to run ARM and MIPS because, behind the scenes, it uses QEMU for the emulation part. However, the results are still limited and far from the details you can obtain in Linux environments, especially in terms of process execution indicators. Also the Volatility plug-in is not supported. Still, it’s worth mentioning the effort done by the team at https://linux.huntingmalware.com/, who were able to make Cuckoo available.

In the next section, we use emulation through QEMU because it is the most stable and mature platform for emulation.

# ARM and MIPS Overview

Before we start playing with ARM and MIPS, let’s quickly look at what these architectures are and how they work. ARM and MIPS are reduced instruction set computers (RISCs) whose instruction set architectures (ISAs) have sets of attributes that allow them to have lower cycles per instruction (CPI) and low operating voltages. This reduces energy consumption, allowing these architectures to run on small devices (so-called embedded devices) like a wristband with Wi-Fi capabilities or a finger ring with Bluetooth connectivity. This architecture is different from the complex instruction set computing (CISC) used by x86 processors found in the Windows and macOS X laptops used on a daily basis. These RISC architectures support 32-bit and 64-bit versions.

ARM offers a 16-bit-long instruction set called Thumb that is basically a compressed representation of the 32-bit instruction set, decompressed in real time, allowing for code size reduction that directly impacts application performance.

Although both architectures are commonly used in game consoles, like those from Nintendo and PlayStation, and in network equipment such as routers and residential