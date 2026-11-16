
you could take. When you start up Wireshark, you will get a home screen, as seen in Figure 9.5. From here, you could just click the shark fin in the toolbar to start up a capture on the default, or primary, interface.

### FIGURE 9.5 Wireshark home screen

![](img/421171b17a0c0dfae0aacde15d9831c1_366_0.png)

If you want to be able to capture from a non-default interface, you would just select one of the interfaces in the list on the home screen. Just double-clicking would start the capture. If you are unsure, you could take a look at the mini graph. This shows interfaces where there is traffic and the amount of traffic over time. It probably isn’t worth capturing traffic from any interface that isn’t showing traffic coming across it.

Wireshark also supports filtering. You can set up a filter at the time of capture, as you can see in Figure 9.5 right where it says “Capture ...Using this Filter.” There is an edit box there where you could enter a filter, which would restrict what Wireshark captures. Once you have captured, you could also use a display filter. This keeps all the frames intact but displays only the ones that match the filter you put in. Wireshark helpfully provides you with hints as you go. Figure 9.6 shows a window with suggestions based on what you have typed. This makes it easier to create a filter that will work.

### FIGURE 9.6 Capture filter in Wireshark

![](img/421171b17a0c0dfae0aacde15d9831c1_366_1.png)

Figure 9.6 shows the capture filter, but Wireshark will also provide help if you are building a display filter. It also helpfully colors the edit box as you go. Once you have valid filter syntax entered, the box turns green. As soon as you start typing, until you have valid filter syntax, the box will be red. When it comes to the display filter, you can filter on any field of any protocol Wireshark understands. You may be looking for all packets where the IP TTL is 13, for instance. You can get very granular with the filtering in Wireshark. It makes life a lot easier if you are looking through hundreds of thousands of frames that have been captured.

## Berkeley Packet Filter (BPF)

The packet-capturing tools we have looked at so far all can use Berkeley Packet Filter (BPF). BPF is an interface to the Data Link layer of a system. BPF is used across many systems and applications, including tcpdump, tshark, and Wireshark. Writing BPF consists of a number of primitives like host, ether, net, and proto. You can use modifiers like src or dst with each of these primitives. This means you could filter based on src host or dst host, as examples. You could also filter based on IPv4 or IPv6 by using the modifiers ip and ip6. When you append a filter to a tcpdump command line, tcpdump will capture and display only packets that pass through the filter.

As an example, the tcpdump examples in the preceding paragraph were actually captured on a Linux system (where I had a simple prompt, to be completely honest) that I was SSH’d into. When you are connected to a system over SSH and you run a packet capture, the vast majority of packets would be SSH packets. Any traffic you really cared about would get lost in the SSH traffic. Think about it for a second. You run tcpdump and tcpdump sends a message to you indicating it is running. tcpdump captures one packet and displays it. In order to display it, there are SSH packets containing the text of the display going to you. This thing is captured and the capture is sent to you. And so on, and so on. In order to capture something useful and not just all SSH packets, the actual command run to capture packets would be tcpdump not port 22.

Here you can see the output of tcpdump without any filters, where tcpdump was run through an SSH session. This is a very small sample. You’ll see that SSH and DNS requests are the messages that are sent, because every packet captured has to have IP addresses resolved to a hostname before it is displayed. You can just cycle through this loop for ages. In the second or two it took to kill the capture, over 4,000 packets were captured.

### Running tcpdump without filters

```
root@quiche:~# tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
18:32:07.835797 IP quiche.lan.ssh > yazpistachio.lan.64631: Flags [P.], seq 3616191731:3616191919, ack 453098787, win 315, options [nop,nop,TS val 16893480 ecr 1259709774], length 188
18:32:07.836406 IP quiche.lan.60511 > testwifi.here.domain: 58726+ PTR? 26.86.168.192.in-addr.arpa. (44)
18:32:07.838352 IP testwifi.here.domain > quiche.lan.60511: 58726* 1/0/0 PTR yazpistachio.lan. (100)
18:32:07.838530 IP quiche.lan.60657 > testwifi.here.domain: 4670+ PTR? 57.86.168.192.in-addr.arpa. (44)
18:32:07.840275 IP testwifi.here.domain > quiche.lan.60657: 4670* 1/0/0 PTR quiche.lan. (94)
18:32:07.840505 IP quiche.lan.ssh > yazpistachio.lan.64631: Flags [P.], seq 188:408, ack 1, win 315, options [nop,nop,TS val 16893485 ecr 1259709774], length 220
```

You can combine different filter primitives. For example, you can see in the following code listing how you would capture TCP packets that either came from or were going to the host 192.168.86.1. With complex filters and also for clarity, you can use parentheses to isolate one of the parameters. You’ll notice the backslashes that are used here to make sure the Linux shell doesn’t try to interpret them, and they are passed as parentheses to tcpdump.

### Complex filters with BPF

```
root@quiche:~# tcpdump tcp and \(host 192.168.86.1\)
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
18:41:33.287262 IP quiche.lan.43790 > testwifi.here.http: Flags [S],
 seq 674275431, win 29200, options [mss 1460,sackOK,TS val 2412954967
ecr 0,nop,wscale 7], length 0
18:41:33.288206 IP testwifi.here.http > quiche.lan.43790: Flags [S.],
 seq 239316039, ack 674275432, win 28960, options [mss 1460,sackOK,TS val
 235265600 ecr 2412954967,nop,nop,wscale 7], length 0
18:41:33.288269 IP quiche.lan.43790 > testwifi.here.http: Flags [.], ack 1,
 win 229, options [nop,nop,TS val 2412954968 ecr 235265600], length 0
18:41:37.111956 IP quiche.lan.43790 > testwifi.here.http: Flags [F.], seq 1,
 ack 1, win 229, options [nop,nop,TS val 2412958792 ecr 235265600], length 0
18:41:37.113495 IP testwifi.here.http > quiche.lan.43790: Flags [F.], seq 1,
 ack 2, win 227, options [nop,nop,TS val 235265982 ecr 2412958792], length 0
18:41:37.113515 IP quiche.lan.43790 > testwifi.here.http: Flags [.], ack 2,
 win 229, options [nop,nop,TS val 2412958793 ecr 235265982], length 0
```

Keep in mind that when you are using BPF on the command line with tcpdump, you are using a capture filter. This means that you won’t see anything that doesn’t pass the filter. If you are writing your capture to a file, you won’t have anything that doesn’t pass the filter. If you are expecting to perform analysis on the captured file later on, you should make sure you won’t need those packets later. Think carefully about the filters you use before applying them to capture.

## Port Mirroring/Spanning

Back when everything used simple hubs, which were just electrical repeaters with no intelligence, getting traffic from everywhere on the network was easy. Then came switches. These are devices that improve the performance and security of a network by doing filtering at layer 2 at the network device. A switch knows which systems are connected to it at which port. When a frame comes in with a destination MAC address, the switch can look up the port where MAC address is and send the frame out that port to the destination system.
This way, other systems on the network never see that frame pass their network interface. This makes capturing packets more difficult if you are looking for traffic that isn’t passing your network interface.

One way to get around that is to have access to the switch. This would allow you to configure the switch to mirror ports. It means any traffic that passes through one port would be mirrored to another port. You may be able to mirror multiple ports to a single port, which would let you monitor traffic to and from multiple systems. If you could only monitor a single port, you could consider mirroring the port that led to a gateway/routing device. This means you are seeing traffic entering and exiting the network, which could potentially give you more access to sensitive information than if you were to just monitor a single endpoint.

On Cisco devices, the feature used for configuring port mirroring is referred to as Switched Port Analyzer (SPAN). When you set up port mirroring, you are configuring a SPAN port. As a result, you may hear the process referred to as port spanning. Other switch vendors may use other terminology for this process.

One consideration when you are mirroring ports is the idea of oversubscription. If you have five 1g switch ports and you are mirroring them out to a single 1g port, you have the possibility of oversubscribing the receiving port. This means you could easily drop packets you were trying to capture and the packets would be basically random, depending on when you have too much data coming in to be able to send out.

## Packet Analysis

Ultimately, packet analysis is probably a big part of why you are capturing the packets to begin with. Once you have the packets, you will want to take a closer look at them, including filtering, following communication streams, and maybe even looking at the statistics and other visualizations from the packet capture. This is another area where Wireshark really excels and can help you a lot. As noted earlier, Wireshark really understands protocols, which means it can not only decode the protocol, it can also tell you places where there may be protocol violations. There are a number of other places where Wireshark can make reading through a packet capture significantly easier.

Wireshark is very good at determining information that isn’t directly provided. It will color frames where it identifies problems in the frame list based on rule sets. These rule sets may be changed and added to. The default rules color frames with errors to have black backgrounds with red text. Once you open the packet in the window below the frame list, you can get the details about the error. Anywhere you see square brackets [] in Wireshark, you are looking at data provided by Wireshark that it has calculated or inferred from the messages it has received. As an example, Figure 9.7 shows the details of a frame where there were errors. You’ll see places where Wireshark provides information in square brackets to help you out.
