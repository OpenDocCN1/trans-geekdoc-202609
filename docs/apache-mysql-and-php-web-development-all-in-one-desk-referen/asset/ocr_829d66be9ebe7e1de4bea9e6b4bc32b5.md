```
*mangle
COMMIT

*nat
COMMIT
# DEFAULT ALL CHAINS TO DROP ON FALLTHROUGH
#:INPUT DROP [0:0]
#:FORWARD DROP [0:0]
#:OUTPUT DROP [0:0]
# PASS ALL FROM LOCALHOST
[0:0] -A INPUT -i lo -j ACCEPT
[0:0] -A OUTPUT -o lo -j ACCEPT
# PASS ICMP TYPE 3 PACKETS, INPUT AND OUTPUT
[0:0] -A INPUT -p icmp --icmp-type 3 -j ACCEPT
[0:0] -A OUTPUT -p icmp --icmp-type 3 -j ACCEPT
# PASS NFS: 2049, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 2049 -j ACCEPT
[0:0] -A INPUT -p udp -m udp --dport 2049 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 2049 -j ACCEPT
[0:0] -A OUTPUT -p udp -m udp --sport 2049 -j ACCEPT
# PASS MOUNTD AT 33333, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 33333 -j ACCEPT
[0:0] -A INPUT -p udp -m udp --dport 33333 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 33333 -j ACCEPT
[0:0] -A OUTPUT -p udp -m udp --sport 33333 -j ACCEPT
# PASS HTTP AT 80, INPUT AND OUTPUT, TCP AND UDP
[0:0] -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
[0:0] -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT
[0:0] -A OUTPUT -p tcp -m tcp --sport 80 -j ACCEPT
COMMIT
```

Figure 1-5: Example iptables configuration.

# Playing Games: IP Masquerade

Network Address Translation (NAT) is used to hide a group host address behind a single public address. Typically NAT is used to allow multiple private hosts to use a single public IP address to access the Internet. Everyone on the private network sharing the single public IP is effectively “masked” — hence the moniker Masquerade — from the Internet. The individual host can use a private IP address (192.168.1.22, for example) and use NAT to access public networks with a different IP address that is routable on the Internet. The advantage to this configuration is that an organization with many internal hosts needs only a single publicly known IP address for all of its resources.

To use IP Masquerade, you need a build that already supports it, or you may need to recompile your kernel to use IP Masquerade. Most current Linux releases support IP Masquerade. To check your system, you can run this command:

```
uname -a
```

The results reveal the kernel version your system is using. To use IP Masquerade, you need kernel version 2.0.x or greater. On the Red Hat distribution, within the /etc/rc.d/rc.local script is an entry that loads the