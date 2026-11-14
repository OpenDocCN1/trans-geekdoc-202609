QEMU-Guest via SSH from Ubuntu-VM. This is done via port redirection because by default QEMU-Guest is configured as a NAT device and is not reachable directly.
Therefore, we need to connect to local port 6666 on the Ubuntu-VM, which will be
redirected to the QEMU-Guest machine on port 22 (SSH). Here's the command to use:

```
ssh -p 6666 root@localhost
```

The default username and password for the machine are both “root.” Figure 25-13 shows
that the ARMEL system has started and we are already logged into the system.

![](bbox=[0.116, 0.247, 0.883, 0.565])

Figure 25-13 Watching the boot process via a VNC client

Now it’s time to install all the tools needed during our malware analysis:

+   * GDBServer Allows us to perform remote debugging
+   * Tcpdump Allows us to capture network traffic
+   * Strace Allows us to record syscalls during malware execution

Before going any further, it is important to update the system by running the following
command:

```
root@debian-armel:~# apt-get update
```

Note that those pre-built images always throw the following error:

```
W: There is no public key available for the following key IDs: 9D6D8F6BC857C906
W: There is no public key available for the following key IDs: 7638D0442B90D010
W: There is no public key available for the following key IDs: 7638D0442B90D010
```

In order to fix this, execute the following command:

```
root@debian-armel:~# apt-get install debian-keyring debian-archive-keyring
```