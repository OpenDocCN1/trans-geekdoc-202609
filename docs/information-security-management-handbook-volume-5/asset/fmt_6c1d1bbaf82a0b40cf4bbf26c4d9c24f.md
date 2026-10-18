
| 4 CIF || 704 × 576 || 704 × 480 |

| D1 || 720 × 576 || 720 × 480 |

Video is also categorized into live video and prerecorded video. Live video is clearly delay sensitive and quality of service (QoS) is very important in maintaining the integrity of live video streams. In most cases, transport is typically UDP (best effort). Recorded video is not adversely affected by delay and reviews of the recorded video streams can be scheduled or ad hoc. Typically, transport is TCP based and the location of recording devices is of importance to understand where the information should be retrieved.

*Performance and Storage Considerations*: When addressing video performance, parameters such as resolution and frame rate have a direct impact on both bandwidth and storage requirements. For instance, if we consider a video capture practice like dual-streaming, where live viewing locally and remotely need to be facilitated, one would be best served by using high resolution and frame rates for local live viewing, while remote viewing can be adjusted to lower frame rates depending on available bandwidth. Also, especially for storage of captured video streams, the two leading methods are as follows.

![](OEBPS/images/box.jpg) *Centrally Located*: Centralized storage is typically deployed in a single environmentally controlled facility with close proximity to personnel who provide the technical support and management of the surveillance and storage systems. Often, these centralized storage models provide the advantage of potentially reducing operational costs due to only having a single location where the video is stored. However, in order to pass on video to other locations, or collect video from multiple locations in a central storage facility, there is likely more video (data) flowing across WAN links.

![](OEBPS/images/box.jpg) *Distributed Storage*: A distributed model for the storage of video surveillance streams positions storage to be located where events are happening, and within close proximity to local surveillance teams who can monitor and react to events in real time. Scalability can be achieved by using multiple smaller systems and there is not a single point of failure. Distributed storage also reduces the bandwidth requirements on the LAN and WAN links, however there are downsides like economies of scale—the cost per hour of storage with multiple smaller systems may be higher. Also, overall operational costs can be higher due to the required maintenance of more devices.

**Multicast:** Just for a quick recap:

![](OEBPS/images/box.jpg) *Unicast*: Communications between one source address and one destination host address.

![](OEBPS/images/box.jpg) *Broadcast*: Communication from one host address, typically to all hosts on a network segment or broadcast destination.

![](OEBPS/images/box.jpg) *Multicast*: Communications where one host sends one copy of each packet being sent to a special address that is then used by several hosts interested in receiving this information. The receiving hosts are members of a designated multicast group and can join or leave the group dynamically, be members of one or multiple groups, and can be located anywhere on the network.

Multicast is often desirable for IP video surveillance applications, since increased efficiencies can be realized. For instance, lower CPU utilization is often observed since senders and receivers only receive requested data. Obviously, network utilization is optimal when compared to replicating multiple streams. However, the nature of multicast relies on UDP, rather than TCP, for transport, thus drops can occur and are often expected since there is not a built-in receipt mechanism, or congestion avoidance.

*Quality of Service and Network Design Principles*: QoS is a critical technology that must be employed to maintain the integrity and efficacy of IP video surveillance. QoS when employed in IP networks allows a systems administrator to prioritize and protect video surveillance traffic from all other types of traffic that traverse the network. Also, proper deployment of QoS prevents degradation of service events like packet loss, latency, and jitter, which represent the effects of mismanaged traffic congestion and will often result in poor video quality and sometimes a complete loss of video. Let’s consider some of the impacts of these congestion events as they pertain to IP video surveillance.

![](OEBPS/images/box.jpg) *Packet Loss*: Video surveillance decoders may be able to tolerate some degree of packet loss, but the quality of the image will degrade. However, since surveillance video is often required to reconstruct critical information, there is not a specific amount of packet loss that can be deemed as “acceptable.” IP video surveillance packet loss may represent itself as shown in [Figure 33.3](#9781466508507_epub_c33_r1.htm#fig_33.3).

![](OEBPS/images/fig_33.3.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 33.3 Examples of video surveillance packet loss.**

![](OEBPS/images/box.jpg) *Latency*: This measure of delay represents the time required to encode, transmit, buffer, and decode the video. This delay sensitivity can be more critical for Pan/Tilt/Zoom (PTZ) cameras due to their movement. A popular best-practice metric is to optimize total end-to-end delay to less than 500 ms, with encoding and decoding best done under 250 ms, leaving 1–50 ms for LAN transport and 100–150 ms for WAN transport.

![](OEBPS/images/box.jpg) *Jitter*: Represented as delay variation, accounts for differences in the end-to-end delay for IP packets for a given video surveillance stream. Packets can over- or under-run the available buffer space, affecting the quality of playback. This effect can cause additional frames to be stored in the decoder’s buffer, potentially reordering the frame sequence and introducing latency, and can result in dropped packets. Jitter is often recommended to be kept under 10 ms whenever possible.

QoS implementation for IP video surveillance traffic requires classification, marking, queuing, and scheduling provisions. The access layer defines the edge of the network, or the ingress point, where traffic must be classified and marked for further treatment in the architecture. The edge devices may be able to rely on configurable Differentiated Services Code Point (DiffServ Code Point, or DSCP) markings that originate from the end devices themselves, i.e., video surveillance cameras. Access layer switches are then configured to trust these markings and preserve them upon ingress.

When looking at the actual classification and markings, the preferred methods for marking packets are Class of Service (CoS) marking, which is performed at Layer 2 of the OSI model, and DiffServ Code Point (DSCP) marking, which is conducted at Layer 3. Let us briefly examine CoS marking at Layer 2 ([Figure 33.4](#9781466508507_epub_c33_r1.htm#fig_33.4)).

![](OEBPS/images/fig_33.4.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 33.4 Class of service marking.**

An Ethernet frame can be marked at Layer 2 (trunked) with their relative importance by setting the 802.1p User Priority bits of the 802.1Q header. Since only 3 bits are available for 802.1p marking, 8 classes of service can be marked 0–7.

If we now examine a DSCP marking at Layer 3, we see where several key pieces of information are coded into the packet ([Figure 33.5](#9781466508507_epub_c33_r1.htm#fig_33.5)).

![](OEBPS/images/fig_33.5.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 33.5 IP Precedence and DiffServ Code Points.**

Here we see information written into the Type of Service (ToS) byte. The three most significant bits of the ToS byte are called IP Precedence (IPP). The six most significant bits of the ToS byte are called the DSCP, with the remaining two bits left for flow control. IPP values define eight levels of marking, which some find too restrictive and much prefer the 6-bit/64-value DSCP model.
