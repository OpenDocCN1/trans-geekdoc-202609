![](bbox=[0.133, 0.083, 0.253, 0.163])

NOTE The best recommendations during this type of effort are to perform static analysis via a disassembler like IDA Pro or radare2 and to use dynamic debugging with a tool like IDA Pro, Immunity Debugger (OllyDBG fork), or GDB.

This lab presents two approaches to debugging IoT malware: the quick approach via the QEMU stand-alone version, and the full system emulation via the QEMU system option. We will also discuss pros and cons of each approach.

# Emulating the Binary

The fast way to start debugging an IoT malware sample is by emulating the binary only and not the entire system. This has some limitations, due to the restricted environment, and because network communication and system checks might fail, but it’s definitely a great and fast start to get into the malware details.

To get this running, log into your Ubuntu VM (running VirtualBox in this case), copy the malware binary to the system (via SSH or drag and drop), and execute these commands in order:

```
$ mkdir ~/GH5
$ cd ~/GH5
$ copy ~/okiru.mips ~/GH5/
$ cp `which qemu-mips` .
$ chroot ./qemu-mips -g 12345 ./okiru.mips
```

Figure 25-18 shows that our instance has been started with QEMU, and thanks to the -g option, we have also spawned a GDBServer that has stopped the binary execution at the entry point and is waiting for a debugger to attach to it at TCP port 12345.

![](bbox=[0.16, 0.645, 0.84, 0.855])

Figure 25-18 Launching a stand-alone emulation with QEMU