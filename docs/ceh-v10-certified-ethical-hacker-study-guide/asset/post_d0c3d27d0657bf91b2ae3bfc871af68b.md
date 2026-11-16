
FIGURE 9.7 Packet analysis

![](img/421171b17a0c0dfae0aacde15d9831c1_370_0.png)

Wireshark will take care of calculations that will make life easier for you. When a TCP connection starts up, sequence numbers are generated, and to prevent spoofing TCP connections, the initial sequence number should be random. A sequence number is 4 bytes, so they are large numbers. Sequence numbers increment based on the number of bytes that are transmitted. If you were to try to do this addition yourself, you would be spending some time tracking sequence numbers and acknowledgment numbers. Instead of that, to make it easier, Wireshark provides you with a relative sequence number. The first sequence number is 1 according to Wireshark. The relative sequence number then increments as you would normally expect. Figure 9.8 shows the TCP headers with a relative sequence number.

FIGURE 9.8 Relative sequence numbers

![](img/421171b17a0c0dfae0aacde15d9831c1_370_1.png)

Packets (or frames) that belong to a particular conversation can be spread through a packet capture. You may find it difficult to move from one packet in the conversation to another, especially if there are a lot of frames that pass by in between. Wireshark allows you to follow a stream. This can be done from a context menu that comes up when you right-click on a frame that belongs to the conversation. If you select Follow TCP Stream, for example, Wireshark will create a display filter for you, only showing the frames that belong to that conversation. In addition, Wireshark will extract the data from the payload, presenting it to you. With an HTTP conversation, for example, you will see the text of the HTTP messages between the client and the server. Figure 9.9 shows the dialog box that comes up showing the text of an HTTP conversation. The client messages are colored with a pink background and red text, while the server messages are in blue with a lilac or light purple background. At the bottom, you will see it says Save And Show Data As and ASCII is selected. There are other options, including raw, C arrays, and YAML.

FIGURE 9.9 Follow TCP Stream dialog box

![](img/421171b17a0c0dfae0aacde15d9831c1_371_0.png)

Wireshark also has substantial capabilities to present statistics from the packet capture. There is a Statistics menu that has a lot of options. One of them is Protocol Hierarchy. This shows every protocol identified in the capture in a hierarchy based on how the protocols are related. For example, as shown in Figure 9.10, everything is a frame and all of these frames are Ethernet. Out of all of the Ethernet frames, everything in this particular capture is an IP packet. From there, 5.5 percent are UDP datagrams. SSDP, MDNS, and DNS are all protocols that make use of UDP as a Transport layer protocol. The majority of the packets captured are TCP segments. Most of those are SSL, though in reality they are all TLS, which is the successor protocol to SSL.

FIGURE 9.10 Protocol Hierarchy statistics

![](img/421171b17a0c0dfae0aacde15d9831c1_372_0.png)

Another entry in the statistics menu to look at is the Conversations view. This shows all of the conversations between endpoints in the packet capture. Every layer of the capture has different sets of conversations, since layer 2 conversations are different than IP address conversations. Any IP conversation that passes out of the local network has a layer 2 conversation with the local gateway. This means you may likely have fewer Ethernet conversations than you do IP conversations. Additionally, your TCP conversations will be different from your IP conversations. You may have multiple sets of ports between two IP addresses. This may be especially true if your local browser sets up multiple connections to a web server to issue requests for images, HTML pages, and other resources that go into the rendering of a page. Figure 9.11 shows the Conversations statistics from a packet capture.

One last feature to look at is in the Analyze menu. Wireshark does perform analysis on frames and packets as it gets them. We looked at some of these earlier by looking at the list of frames and looking at colors. Additionally, when we looked at the protocol decode, you could see errors in cases where the information identified by Wireshark is in square brackets. You don't have to skim all the way through the packet capture file to find the errors one at a time. Instead, if you go to the Analyze menu, you can select Expert Information and this will show you all of the frames that Wireshark has identified as problematic. In Figure 9.12, you can see all of the expert information by category. You see the errors, warnings, notes, and chat. If you were to open each of these entries, you would get a list of frames. Clicking on one of these entries takes you to that frame in the capture so you can see its details.

FIGURE 9.11 Conversations statistics

![](img/421171b17a0c0dfae0aacde15d9831c1_373_0.png)

FIGURE 9.12 Expert Information

![](img/421171b17a0c0dfae0aacde15d9831c1_373_1.png)

One element of packet capture that we haven’t spent any time on is the time stamp. Packets don’t contain time stamps, so just looking at most frames or packets won’t give you the time the frame passed through the network. When you look at the time column in Wireshark, you will find a relative time. This is relative to the start of the capture. That may not be very useful to you. Helpfully, packet capture files will include the time of the start of the capture in the metadata. This means you can change the time shown in Wireshark to be absolute time. This assumes the time and the time zone in the capturing file were correct, since it does rely on the configuration of the capturing system.

## Spoofing Attacks

You may not have to be stuck with only capturing packets that are destined to your system or ones that you can get to you by reconfiguring the switch. There are other ways to get messages to you. This can be done by using different types of spoofing attacks. A spoofing attack is where you pretend to be a system you aren’t. You can approach this from different layers, starting at layer 2. You can also spoof at a higher layer, using DNS to get systems to send traffic to systems you want. Spoofing attacks allow you to sit in the middle of a conversation between two endpoints.

This brings up an issue you need to keep in mind. If you are running spoofing attacks, it means at least one end of the conversation is potentially not getting to the appropriate endpoint. If everything doesn’t look right, someone is going to start suspecting something. This means you need to make sure you are doing something to make the conversation whole. If someone gets suspicious that something is wrong, they may start looking for causes, which may mean you could be identified and caught. Presumably, if you are running a spoofing attack, you don’t want to be identified and caught. As always, you need to make sure you are using these powers for good and not for evil.

## ARP Spoofing

The Address Resolution Protocol (ARP) has two stages. The first is the request, where a system knows an IP address but doesn’t know the corresponding MAC address. It sends an ARP request out asking for the system with the IP address to respond with its MAC address. The response is the system replying, indicating its MAC address to the requestor. There is nothing to authenticate that request, though. In theory, anyone could respond to that request with their MAC address to get the requesting system to send the message to the attacker’s/spoofer’s address. We could make it even easier by simply not waiting for the request to begin with and just sending the reply.

In order to be efficient, systems will take any ARP responses, even if they didn’t ask, and cache the mapping. This keeps them from having to ask for the MAC address should they ever need it. This is a feature we can take advantage of. We could just send out ARP responses, mapping whatever IP address on the network we want to our MAC address. This would get all systems on the local network sending messages to us, as our address is in their ARP cache. The process of just sending out ARP responses without a corresponding ARP request is called gratuitous ARP, meaning it's an ARP message that wasn't asked for.

One of the problems we have is the length of time ARP entries are cached for. On Linux systems, the default cache length is 60 seconds. You can check it from an entry in the /proc pseudo filesystem, as you can see in the following code listing. You could also change the behavior by replacing the 60 with another value. On Windows systems, the cache time is different. Microsoft opted to follow RFC4861, which applies to IPv6, for the IPv4 implementation. Starting with Windows Vista, Microsoft has a base time of 30,000 milliseconds, which is multiplied by a random value between .5 and 1.5 to get the cache duration. This means it's different from one system to another and also from one boot to another.

### ARP cache duration on Linux

```
cat /proc/sys/net/ipv4/neigh/default/gc_stale_time
60
```

Because the cache can time out quickly, we have to keep sending out our gratuitous ARP responses. Obviously, this is something better done programmatically rather than manually. This is especially true since there is another problem. When we redirect messages to our system, we really need to forward them back out onto the network with the correct MAC address in the destination field. Otherwise, conversations don't happen. A TCP connection never completes because the SYN or the SYN/ACK never reaches the appropriate destination system. Instead, it is sent to our system where it dead-ends unless we do something. This requires turning on forwarding so that the message we are hijacking can be forwarded back out the same interface to get to its intended destination.

There are a few programs that can be used to handle ARP spoofing. One of them, arpspoof, has been around for a long time now. It was written by Dug Song, who also wrote a program called fragroute, which is useful in its own way. Using arpspoof, we can inject ourselves in between two systems on the network. We can tell arpspoof which two IP addresses we want to pretend to be. It takes care of the rest for us. In the following code listing, you can see a run of arpspoof where I've selected the default gateway on my network to be the one I spoof. This means I get messages that are destined for the default gateway, so anything that's going off-net gets sent to the system running arpspoof. You'll see the gratuitous ARP responses being sent. They get sent out every few seconds to ensure that no ARP cache entries age out.
