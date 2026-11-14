
We are basically saying to listen on network interface eth0 and only focus on the IP of the guest machine and only listen to TCP or UDP ports (to avoid ARP or other noisy traffic). Also, because we are dealing with Mirai-based malware, we want to avoid port 23, which is normally used for scanning the Internet and will quickly increase the size of our capture file with the same destination port. It is highly recommended that you avoid doing this on your local network because your IP might be banned by your ISP.

On another terminal, trace the execution of the malware by executing the following command. Probably the most important options are -f for following child processes (very important since Mirai-based malware uses fork to eventually hide from the parent process) and -o for storing the gathered information into a file.

```
#strace -f -q -s 100 -o satori.out ./470.arm
```

Once strace and tcpdump are running, you can always monitor the size of those files and transfer the current captured file at intervals. Depending on the malware, it can be left running for minutes, hours, or even days. For this lab, after 5 minutes you can stop the malware execution (normally by shutting down the machine).

By taking a look at the captured traffic, you can identify the attacker’s host (C2) where the malware is trying to connect, as shown in Figure 25-14.

| Source | Destination | Protocol | Length Info |
| :--- | :--- | :--- | :--- |
| 10.0.2.15 | 8.8.8.8 | DNS | 82 Standard query 0x3730 A network.bigbotpein.com |
| 8.8.8.8 | 10.0.2.15 | DNS | 98 Standard query response 0x3730 A network.bigbotpein.com A 177.67.82.48 |
| 10.0.2.15 | 8.8.8.8 | DNS | 82 Standard query 0x1c48 A network.bigbotpein.com |

Figure 25-14 C2 used by the malware

If you want more details about the actions performed on that site, you can take a look at the satori.out output file, where you can easily identify a telnet connection to the resolved IP 177.67.82.48, as shown in Figure 25-15.

![](img/5f597c6a70133069118d9e804ace3775_701_0.png)

Figure 25-15 Telnet connection with the C2

The duration of this particular capture shows an infinite loop of the malware trying to get a response from the host, which is not available at the time of testing. That’s the normal behavior of Mirai-based malware, waiting to receive the command to be executed.

Feel free to play with the malware or execute other samples following the same approach. You will eventually need a strace output parser for a good-looking report.

## Platform for Architecture-Neutral Dynamic Analysis (PANDA)

PANDA is an open source platform for architecture-neutral dynamic analysis. Although it does not fully support MIPS and is in an early experimental phase, it is definitely a framework to keep an eye on. PANDA is being developed collaboratively among MIT Lincoln Laboratory, New York University (NYU), and Northeastern University. It is built on QEMU for emulation and adds the ability to record and replay malware executions multiple times, going through different plug-ins that allow for syscall monitoring, taint analysis, and so on. It also includes a mechanism to share functionality between plug-ins in order to avoid duplication of efforts. Unfortunately, we did not find a stable version during our ARM malware analysis, so we decided not to prepare a lab. However, be sure to keep an eye on PANDA and give it a try. If it can move into a stable release, it has the potential to be one of the must-have frameworks for IoT dynamic malware analysis.

PANDA can be built from its GitHub repository, which also includes a Docker image to simplify the installation process.

## BeagleBone Black Board

Sometimes the malware won’t run on a virtual machine or is heavily hardware dependent, or perhaps you are just reversing a piece of code of a Car infotainment. For those cases, a real device running an ARM system is highly recommended, and the BeagleBone Black board device is the way to go in this scenario: it cost less than $60 and you can always re-flash the firmware if it gets affected by the malware. This board runs on a Cortex-A8 ARM system, with USB, Ethernet, HDMI, and 2 x 46 pin headers for connectivity.

You just need to download the USB drivers for your computer, set up the SD card for booting, if needed (check the “For Further Reading” section for the Beaglebone Black Getting Started URL), and then just plug your BeagleBone device into your computer via USB, which should automatically assign you an IP in the 192.168.6.x or 192.168.7.x segment. Then you can use an SSH client to log into your ARM system that is waiting for you at the IP 192.168.7.2 or 192.168.6.2.

## Reverse Engineering IoT Malware

Reverse engineering is a skill that requires knowledge of assembly, which is the language used by the microprocessors. The goal is to understand how a program works without having the source code. Traditionally, most of the work is done on Intel microprocessors running Windows or Linux operating systems, but with the exponential growth of IoT devices, the need to understand ARM and MIPS architectures is mandatory. This section summarizes the key concepts needed to be able to reverse-engineer malware running on these architectures.

## Crash-Course ARM/MIPS Instruction Set

Before jumping into the IoT malware debugging, you need to understand key concepts that will make your life easier when reversing these type of threats. The good news is that the number of instructions in ARM/MIPS is significantly lower than in the x86 architecture and therefore it won’t be hard for you to get up to speed.

## Calling Convention

As usual, when you’re learning new architectures, understanding the calling convention is mandatory. You need to understand how the parameters are passed to the functions and where you get the response back.

Let’s create some quick ARM code and compile it to see the calling convention in action:

```
unsigned int function ( unsigned int, unsigned int, unsigned int, unsigned int,
unsigned int, unsigned int, unsigned int );
unsigned int mifunction ( void ) {
return(function(0,1,2,3,4,5,6));
}
```

Now we just need to compile it with a cross-compiler:

```
# ./arm-elf-gcc -O2 -c call-arm.c -o call-arm
```

![](img/5f597c6a70133069118d9e804ace3775_703_0.png)

NOTE A VM with cross-compilers and other useful tools like GDB and Objdump for ARM, MIPS, PowerPC, and many other architectures can be found at http://kozos.jp/vmimage/burning-asm.html. Note that this is the Japanese version.

Let’s look at the disassembly by running the following command:

```
# arm-elf-objdump -D call-arm
```

Figure 25-16 shows the calling convention. We will refer to the assembly code based on the line numbers in the left column, starting with 0, 4, 8, c ... all the way to the line 40.

```
Disassembly of section .text:
00000000 <mifunction>:
  0:	e1a0c00d	mov	ip, sp
  4:	e92dd800	push	{fp, ip, lr, pc}
  8:	e3a02002	mov	r2, #2
  c:	e24dd00c	sub	sp, sp, #12
 10:	e24cb004	sub	fp, ip, #4
 14:	e3a0c004	mov	ip, #4
 18:	e3a0e005	mov	lr, #5
 1c:	e58dc000	str	ip, [sp]
 20:	e3a01001	mov	r1, #1
 24:	e08cc002	add	ip, ip, r2
 28:	e3a03003	mov	r3, #3
 2c:	e3a00000	mov	r0, #0
 30:	e58de004	str	lr, [sp, #4]
 34:	e58dc008	str	ip, [sp, #8]
 38:	ebffffff	bl	0 <function>
 3c:	e24bd00c	sub	sp, fp, #12
 40:	e89da800	ldm	sp, {fp, sp, pc}
```

Figure 25-16 ARM calling convention

The numbers 0 to 3 are passed directly to the registers r0 to r3 in the assembly code. Look at the line numbers 2c, 20, 8, and 28 (left side) in Figure 25-16. The parameter with the value 4 is first moved to the register ip at line 14 and then stored in the stack via (stack pointer) register [sp] at line 1c. The same process is used for the parameter with the value 5; it is assigned at line 18 and then stored at [sp, #4] (stack pointer + 4) at line 30. Finally, for the last parameter with the value 6, its value is first calculated at line 24 by adding the current value of “ip = 4” (calculated at line 14), plus the current value of “r2 = 2” (assigned at line 8), for a total of 6. This is finally stored in the stack at offset [sp, #8] (stack pointer + 8) at line 34.

Now let’s do the same, but this time compile with MIPS toolchain (mips-elf-gcc). The result can be seen in Figure 25-17. Again, we will refer to the assembly code based on the line numbers along the left side.
