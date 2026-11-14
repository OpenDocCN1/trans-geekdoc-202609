Now, execute the update command again and it should work. Finally, the necessary tools are installed as follows:

```
root@debian-armel:~# apt-get install gdb tcpdump strace
```

Now that all the tools needed are installed, you are ready to run the malware. However, that is outside the scope of this exercise. See Lab 25-2 for those details. Note that you can follow exactly the same process to run other architectures such as MIPS through QEMU. You just need to download the proper files from the repository.

# Dynamic Analysis of IoT Malware

As mentioned earlier, multiple options are available to execute Windows-based malware in a monitored environment to extract indicators dynamically. Solutions such as Cuckoo Sandbox and Payload Security are two examples. However, when it comes to dynamic analysis on ARM or MIPS, there is still no solid solution—at least one that’s freely available. Therefore, we need to create our own environments. Lab 25-2 details the steps to follow to replicate an IoT malware known as Satori and extract network- and host-based indicators.

# Lab 25-2: IoT Malware Dynamic Analysis

Before starting this lab, note that we will be using real malware found in the wild. Therefore, you are highly encouraged to run it in a virtual environment, totally segregated from your corporate or home network. It is also recommended that you make sure any inbound communications started from the guest VM to the host machine are rejected.

Sample MD5 to be used during this Lab = ad52832a507cede6521e11556f7cbb95

Fire up your armel emulated machine via QEMU, as previously described in Lab 25-1, but this time with a significant change: you need to add the option -snapshot to the command line to prevent the malware from causing permanent damage on the guest’s hard disk. With this option, the next time you reboot the machine, any modifications made by the malware will be gone, which perfectly fits our need during malware analysis. We do not want to reuse an infected host multiple times; it must be a fresh start for each iteration. You can monitor the booting process via VNC access. Once the login prompt appears, copy the malware (470.arm) to QEMU via the following scp command:

```
scp -P 6666 470.arm root@localhost:
```

In case you forgot, the credentials are root/root. Once the file is copied successfully, log into the ARM machine and make sure the file is there. Then change the permissions to 755 and get ready for execution!

You will need another shell in order to run tcpdump to capture network traffic. You can start the network traffic capture with the following command:

```
# tcpdump -i eth0 -n host 10.0.2.15 and tcp or udp and not port 23 -w 2_15.pcap
```