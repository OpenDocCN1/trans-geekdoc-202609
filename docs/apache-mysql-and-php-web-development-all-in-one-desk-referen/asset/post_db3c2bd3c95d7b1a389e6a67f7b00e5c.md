
Here are a couple handy ways to help you determine if you need a particular service or program:

- Visit the home page of your Linux distribution and search for the program.
- Search for “man program/service” using a search engine like Yahoo! or Google. The manual (man) pages typically reveal a wealth of information about the program/service and its usage.

## Protection with Firewalls

Although many third-party security products, including firewalls, are available for Linux, several handy features are included with the operating system out of the box. Having a firewall on your Linux system is exceptionally important if the system is outside any other firewalls. For example, if the resources for setting up a secure LAN are not available, the Linux server you build needs a local firewall installed if it is connected to the Internet. Even if you’re using a secure LAN configuration, an additional, local firewall adds an extra line of defense to stave off intruders if they compromise one of your existing routers.

## Ipchains

Ipchains is a long-standing firewalling mechanism that is available on most Linux distributions that use kernel version 2.2.x. To get started, you need to enable ipchains. If your system is using the IP address 10.50.4.55 with the mask 255.255.255.0 (internally), you need to run the following commands with root privileges:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
ipchains -A forward -j MASQ -s 10.50.4.0/24 -d 0.0.0.0/0
```

The first command enables ip_forwarding, and the second entry configures the server with which network to grant Internet access. If you want to load the ipchains service at startup, you need to place the two preceding commands into the etc/rc.d/rc.local file. After you have the firewall running, you can use the ipchains -L command to see the configured IP filtering rules. Of course to start with, there is not much to see. The output of this command looks something like Figure 1-4.

```
ipchains -A input -p icmp -i eth0 -j REJECT
```

Here's a closer look at the components of this example:

- The `ipchains -A input` portion indicates that you're appending (A) a new rule to the ipchains `input` chain. In place of -A, you can use -L to see the current ipchains rules and -D to delete a rule from a chain.
- The option -p specifies that you're going to set a rule for a protocol.
- icmp is the type (used with the -p option), and in this case, that is all ICMP traffic.
- eth0 is the network interface to apply the rule to.
- The -j REJECT option specifies that the ICMP traffic should be rejected at the interface. The result is that any inbound ICMP traffic on the eth0 interface is summarily rejected.

See Book I, Chapter 3, for information about products that make ipchains and other firewall configuration easier. This chapter only touches on the capabilities of the ipchains tool. If you're interested in finding out more about ipchains, visit `www.rt.com/man/ipchains.8.html` or type "man ipchains" on your Linux server to see the almost overwhelming number of ipchains run-time options.

![](img/3f967ab8a8fddc723173059f56621648_46_0.png)

Figure 1-4: Example ipchains rules configuration.

## Iptables

Another option for implementing a firewall on your Linux system is through the use of iptables. They are similar in function (they both control network access); however, iptables has several advantages over ipchains. The advantages are noteworthy enough that if you are using a 2.4.x or newer kernel version (any build of Red Hat newer than 7.1, for example) you should use iptables. Below are some of the ways in which iptables differs from ipchains.

- Iptables, unlike ipchains, uses a single chain to process filtered packets. Because of this, iptables allows you to exert finer control over the kinds of filtering options you choose. For example, a packet forwarded by an ipchains host must traverse the input, forward, and output chains to make it to its destination. An iptables host must only check the packet against the output filter. If the host is using iptables, a conflicting rule on the input chain won't stop the forwarding of the packet.
- The iptables host processes inbound packets using only the inbound rules, and outbound packets using only the outbound rules. If you want to specify the network interface to be used with a particular rule, you must use the appropriate option in your configuration. The `-i` option must be used with the inbound or forward chains and the `-o` option must be used with the outbound chains. Remember that the inbound interface will not use outbound rules and the outbound interface will not use inbound rules. If you mix your options, the rule will not have the intended effect.
- Unlike ipchains, you must specify the source or destination port after the protocol declaration (ICMP, TCP, or UDP). In ipchains the order was not all that important, however with iptables the rules will fail to operate as expected if the proper order is not used.

As you might expect, the configuration file (typically located in /etc/sysconfig/iptables) has changed considerably as well. The overall arrangement is a bit cleaner and if you use comments, it is fairly straightforward to understand what is going on in the configuration. In Figure 1-5, the configuration first sets a rule that allows the local host (running iptables) to pass any traffic to or from *localhost*. The next entry allows the passage of ICMP type 3 traffic. Type 3 “Destination Unreachable” messages are used when systems that forward data to another host cannot find the targeted host. Next, there are mounted and NFS connections allowed. These would probably be essential if you needed to connect to your system over a network to send data (to upload Web page content for example), but if you are working locally on the machine, these could be eliminated. The mount entry in this example only works if you go to the NFS configuration file /etc/rc.d/init.d/nfs and assign the mount service to a single port (33333 in this case). By default, the port is picked during system startup and varies between 32000 and 42000. Finally, the configuration file allows the passing of http traffic on port 80. If you need to use https as well, you could duplicate this last entry and change the destination port (dport) and source port (sport) values to 443.

In Figure 1-4, note that three chains are in place by default.

I strongly recommended that you become familiar with the syntax and use of ipchains and iptables before you use either in a production environment. It’s easy to overlook something and leave your system exposed. Make a plan for the kinds of traffic you need to allow in and out of your server and for the services and ports that need to be blocked. With a clear plan, your results will be much better. To find additional information about ipchains configurations, check out www.linux.org/docs/ldp/howto/IPCHAINS-HOWTO.html. If you will be working with iptables, there is a great source of general information and configuration examples located at www.jollycom.ca/iptables-tutorial/iptables-tutorial.html.

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

## Playing Games: IP Masquerade

Network Address Translation (NAT) is used to hide a group host address behind a single public address. Typically NAT is used to allow multiple private hosts to use a single public IP address to access the Internet. Everyone on the private network sharing the single public IP is effectively “masked” — hence the moniker Masquerade — from the Internet. The individual host can use a private IP address (192.168.1.22, for example) and use NAT to access public networks with a different IP address that is routable on the Internet. The advantage to this configuration is that an organization with many internal hosts needs only a single publicly known IP address for all of its resources.

To use IP Masquerade, you need a build that already supports it, or you may need to recompile your kernel to use IP Masquerade. Most current Linux releases support IP Masquerade. To check your system, you can run this command:

```
uname -a
```

The results reveal the kernel version your system is using. To use IP Masquerade, you need kernel version 2.0.x or greater. On the Red Hat distribution, within the /etc/rc.d/rc.local script is an entry that loads the
