Once the syscalls are renamed, the entire binary will make more sense; from there, you can apply the same reversing process as used in Windows environments. One of the most important pieces of information is the IP or domain the malware is trying to reach. Let’s see how that looks in IoT (since it is Linux-based, there’s really no difference).

We put a breakpoint at 0x4065C4, and thanks to the syscall renaming, you know it corresponds to the “connect” function call (see Figure 25-26). Because of that, you can also now identify the parameters by looking at the definition:

![](bbox=[0.34, 0.24, 0.77, 0.39])

![](bbox=[0.34, 0.41, 0.77, 0.56])

![](bbox=[0.12, 0.57, 0.88, 0.65])

Figure 25-26 Displaying the sockadddr structure in IDA Pro

```
int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen);
```

Because you know that the second parameter passed via register A1 holds a sockaddr structure, you can ask IDA to show you the memory content of that register by right-clicking Memory Windows (lower-left window) and selecting “Synchronize with” -> A1, as displayed in the aforementioned figure. By looking at the sockaddr_in structure definition in the following code, you can see that the first parameter is the length of the structure, which is optional and is not being used in this case. You can also see that the second parameter is the sin_family, which has the number in memory equal to 00 02 (big-endian), corresponding to AF_INET. Then follows the port content, 00 35, which is the hexadecimal representation of 53 (domain port). Finally, you see the IP address, which corresponds to 08 08 08 08, a public domain IP address.