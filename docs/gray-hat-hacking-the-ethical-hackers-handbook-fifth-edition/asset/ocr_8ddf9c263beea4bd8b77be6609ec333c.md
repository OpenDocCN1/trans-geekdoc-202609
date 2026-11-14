# Index of /~aurel32/qemu

| Name | Last modified | Size | Description |
| :--- | :--- | :--- | :--- |
| Parent Directory | | - | |
| amd64/ | 2014-01-06 18:29 | - | |
| armel/ | 2014-01-06 18:29 | - | |
| armhf/ | 2014-01-06 18:29 | - | |
| i386/ | 2014-01-06 18:29 | - | |
| kfreebsd-amd64/ | 2014-01-06 18:29 | - | |
| kfreebsd-i386/ | 2014-01-06 18:29 | - | |
| mips/ | 2015-03-15 19:07 | - | |
| mipsel/ | 2014-06-22 09:55 | - | |
| powerpc/ | 2014-01-06 18:29 | - | |
| sh4/ | 2014-01-06 18:29 | - | |
| sparc/ | 2014-01-06 18:29 | - | |

Figure 25-12 QEMU VMs repository

Download all the wheezy release binaries from the “armel” directory into your Ubuntu-VM. Also, make sure you configure the Ubuntu-VM in bridge mode.

![](bbox=[0.13, 0.56, 0.25, 0.64])

**NOTE** The main difference between armel and armhf is the supported ARM versions: armel supports older versions and is very useful when dealing with legacy systems.

Now fire up the ARM system by executing the following command:

```
qemu-system-arm -M versatilepb -kernel vmlinuz-3.2.0-4-versatile -initrd initrd.img-3.2.0-4-versatile -hda debian_wheezy_armel_standard.qcow2 -append "root=/dev/sda1" -monitor stdio -vnc 192.168.1.200:1 -redir tcp:6666::22
```

The monitor option provides a QEMU shell to interact with QEMU-Guest, which is useful to shut down the machine in case something goes wrong. We also add the vnc option, providing the IP address of the Ubuntu-VM to spawn a VNC Server instance on port 5901 by default. A VNC client will be needed to access it; no credentials are required, although those can be set via the QEMU shell. This is useful to watch the booting process and detect any problems during this phase. Finally, the redir option is used to connect to