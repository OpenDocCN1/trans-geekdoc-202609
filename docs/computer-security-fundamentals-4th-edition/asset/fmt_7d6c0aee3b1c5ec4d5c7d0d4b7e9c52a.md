
The type of cable used in connecting computers is also often referred to as unshielded twisted-pair (UTP) cable. In UTP, the wires in the cable are in pairs, twisted together without additional shielding. As you can see in `[Table 2.1](#ch02.xhtml#ch02tab01)`, each subsequent category of cable is somewhat faster and more robust than the last. It should be noted that although Cat 4 can be used for networks, it almost never is used for that purpose, as it is simply slower, less reliable, and an older technology. You will usually see Cat 5 cable and, increasingly, Cat 6. You should note that we are focusing on UTP because that is what is found most often. There are other types of cable, such as shielded twisted-pair (STP), but they are not nearly as common as UTP.

FYI: Cable Speed

Category 6 cable is for Gigabit Ethernet and has become quite common. In fact, some networks are now using Cat 7. Cat 5 cable works at speeds of up to 100Mbps, whereas Cat 6 works at 1000Mbps. Cat 6 is widely available and has been for several years. However, for Cat 6 to truly function properly, you need hubs/switches and NICs that also transmit at gigabit speeds; thus, the spread of gigabit Ethernet has been much slower than many analysts expected. We will discuss hubs, switches, NICs, and other hardware in more detail later in this chapter.

As shown in `[Table 2.1](#ch02.xhtml#ch02tab01)`, a key specification is speed, measured in Mbps, or megabits per second (though gigabits per second, or Gbps, speeds are becoming more common). You are probably already aware that ultimately everything in a computer is stored in a binary format—namely, in the form of a 1 or a 0. These units are called `bits`. It takes 8 bits, which equals 1 byte, to represent a single character such as a letter, number, or carriage return. Remember that the data specification for each cable is the maximum that the cable can handle. A Cat 5 cable can transmit up to 100 mega (million) bits per second. This is known as the `bandwidth` of the cable. If multiple users are on a network, all sending data, that traffic uses up bandwidth rather quickly. Any pictures transmitted also use a lot of bandwidth. Simple scanned-in photos can easily reach 2 megabytes (2 million bytes, or 16 million bits) or much larger. And streaming media, such as video, is perhaps the most demanding in terms of bandwidth.

If you simply want to connect 2 computers, you can have the cable go directly from one computer to the other. You would have to use a crossover cable, but you could connect 2 computers directly. But what do you do if you want to connect more than 2 computers? What if you have 100 computers that you need to connect on a network? There are three devices that can help you to accomplish this task: the hub, the switch, and the router. These each use Cat 5 or Cat 6 cable with RJ-45 connectors and are explained in the following sections.

##### The Hub

The simplest connection device is the `[hub](#glossary.xhtml#gloss46)`. A hub is a small box-shaped electronic device into which you can plug network cables. It will have 4 or more (commonly up to 24) RJ-45 jacks, each called a `port`. A hub can connect as many computers as it has ports. (For example, an 8-port hub can connect eight computers.) You can also connect one hub to another; this strategy is referred to as “stacking” hubs. Hubs are quite inexpensive and simple to set up: Just plug in the cable. However, hubs have a downside. If you send a packet (a unit of data transmission) from one computer to another, a copy of that packet is actually sent out from every port on the hub. All these copies leads to a lot of unnecessary network traffic. This occurs because the hub, being a very simple device, has no way of knowing where a packet is supposed to go. Therefore, it simply sends copies of the packet out all of its ports. While you may go to your favorite electronics store and buy something called a “hub,” true hubs no longer exist. What you are really getting is a switch, which we will discuss later in this section.

##### The Repeater

A `repeater` is a device used to boost signal. Basically if your cable needs to go further than the maximum length (which is 100 meters for UTP), then you need a repeater. There are two types of repeaters: amplifiers and signals. Amplifier repeaters simply boost the entire signal they receive, including any noise. Signal repeaters regenerate the signal, and thus don’t rebroadcast noise.

##### The Switch

A `switch` is basically an intelligent hub; it works and looks exactly like a hub, with one significant difference. When a switch receives a packet, it sends that packet only out the port for the computer to which it needs to go. A switch is essentially a hub that is able to determine where a packet is being sent. It makes this determination based on the MAC (Media Access Control) address, found in the Ethernet header of the packet. More details on MAC addresses and packet headers will be provided later in this chapter.

##### The Router

Finally, if you wish to connect two or more networks, you use a `[router](#glossary.xhtml#gloss68)`. A router is similar in concept to a hub or switch, as it relays packets; but it is far more sophisticated. To begin with, a router directs traffic based on the IP address found in the IP header of a packet. You can program most routers and control how they relay packets. Most routers have interfaces that allow you to configure them. More robust routers also offer more programming possibilities. The specifics of how you program a router are different from vendor to vendor, and there are entire books written on just programming routers. It is not possible to cover specific router programming techniques in this book; however, you should be aware that most routers are programmable, allowing you to change how they route traffic. Also, unlike when using a hub or switch, the two networks connected by a router are still separate networks.

#### Faster Connection Speeds

So far we have looked at the connections between computers on a local network, but there are faster connection methods. In fact, your Internet service provider or the company for which you work probably has a much faster connection to the Internet. `[Table 2.2](#ch02.xhtml#ch02tab02)` summarizes the most common high-speed connection types and their speeds.

**Table 2.2** Internet Connection Types 

| Connection Type || Speed || Details |
| --- | --- | --- |
| DS0 || 64Kbps || Standard phone line. |
| --- | --- | --- |
| ISDN || 128Kbps || 2 DS0 lines working together to provide a high-speed data connection. |
| T1 || 1.54Mbps || 24 DS0 lines working as one, where 23 of the lines carry data, and 1 carries information about the other lines. This type of connection has become common for schools and businesses. |
| T3 || 43.2Mbps || 672 DS0 lines working together; the equivalent of 28 T1 lines. |
| OC3 || 155Mbps || All OC lines are optical and do not use traditional phone lines. OC3 lines are quite fast and very expensive. They are often found at telecommunications companies. |
| OC12 || 622Mbps || The equivalent of 336 T1 lines, or 8064 phone lines. |
| OC48 || 2.5Gbps || The equivalent of 4 OC12 lines. |

It is common to find T1 connection lines in many locations. A cable modem can sometimes achieve speeds comparable to that of a T1 line. Note that cable connections are not included in `[Table 2.2](#ch02.xhtml#ch02tab02)` simply because their actual speeds vary greatly, depending on a variety of circumstances, including how many people in the immediate vicinity are using the same cable modem provider. You are not likely to encounter OC lines unless you work in telecommunications.

#### Wireless
