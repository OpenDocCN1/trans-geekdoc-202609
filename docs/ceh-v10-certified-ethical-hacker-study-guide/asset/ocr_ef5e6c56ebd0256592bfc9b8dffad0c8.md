```
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=3 win=29200 rtt=7.5 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=4 win=29200 rtt=7.3 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=5 win=29200 rtt=3.0 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=6 win=29200 rtt=2.8 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=7 win=29200 rtt=2.7 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=8 win=29200 rtt=2.5 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=9 win=29200 rtt=2.4 ms
len=46 ip=192.168.86.1 ttl=64 DF id=0 sport=80 flags=SA seq=10 win=29200 rtt=2.2 ms
```

hping will provide you with all of the flags that are set in the response. This includes the SYN and ACK flags as well as the don’t fragment bit, indicated by the DF in the response. You can see a lot of other details as well, including the IP identification number, the relative sequence number, and the window size as provided by the target host. In the case of a port where there is no listener, you won’t get a message indicating that the host is unreachable or that the message timed out, as you would with a standard ping program. Instead, you will get the same response back that you got from an open port. Instead of showing SA for flags, meaning that the SYN and ACK flags were set, you will see RA, meaning the RST and ACK flags. The remote system reset the port, telling us that there is no application there. You will still get all of the other information, including the round-trip time, which will tell you how quick the target system is to respond to these messages, which will be a factor of network and operating system responsiveness.

![](bbox=[0.145, 0.51, 0.23, 0.56])

Raw sockets provide programmers with the ability to bypass the network stack. When a programmer uses raw sockets, the program is expected to handle all the things the network stack does, meaning all the values in the headers should be set. Raw sockets provide the programmer with complete control over what the packet will end up looking like. None of it has to be considered legal from the standpoint of the protocols, if you aren’t expecting responses back. This is not to say that you will always get a response, though. You could completely mangle the message to the target host. As one example, take a look at the command line below. The offset for the TCP headers is being set incorrectly, which means the target network stack is being pointed to the wrong place. Also, the SYN and FIN flags are both set, as well as the ACK and PSH flags. This is a flag combination that makes no sense. The source port is being set to 15, which would require administrative privileges to do, as do most things in hping, considering it is generally using something called raw sockets.

# hping with Bad Flags Set

```
root@quiche:~# hping3 -0 8 -s 15 -F -S -P -A -t 3 -p 80 192.168.86.1
HPING 192.168.86.1 (eth0 192.168.86.1): SAFP set, 40 headers + 0 data bytes
^C
--- 192.168.86.1 hping statistic ---
```