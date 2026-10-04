

超出 iSLIP 范围，iSLIP 在此仅作为争用管理的方便示例，厂商会根据自身交叉开关结构（crossbar fabric）的硬件能力编写自己的算法。例如，本节仅考虑了输入队列式交叉开关结构，但许多交叉开关结构在交叉开关的出口侧也提供输出队列。

## 内存到物理介质

一旦数据包通过总线传输到出站线路卡，或数据包缓冲区的指针从输入队列移动到输出队列，网络设备仍有工作要做。[Figure 7-11](#ch07.xhtml#ch07fig11) 进行了说明。

![Image](graphics/07fig11.jpg)

**Figure 7-11** *Clocking a Packet Back onto the Wire*

请注意 [Figure 7-11](#ch07.xhtml#ch07fig11) 中显示的环是发送环，而非接收环。[Figure 7-11](#ch07.xhtml#ch07fig11) 中共有四个步骤：

**Step 1.** 数据包被传递到路由器的发送侧以进行转发。这里可能需要进行交换后处理，具体取决于平台和特定功能；这些在该图示中未显示。首先会尝试将数据包直接放置在发送环上，以便进行传输。如果环上已有数据包，或环已满（取决于实现方式），则数据包不会被放置在发送环上。如果数据包被放置在发送环上，则跳过步骤 2（这意味着数据包不会使用任何出站服务质量 \[QoS\] 规则进行处理）。否则，数据包将被放置在输出队列中，等待被转移到发送环。

**Step 2.** 如果数据包无法放置在发送环上，它将被放置在输出队列中以便在稍后时间持有。

**Step 3.** 定期地，发送代码会将数据包从输出队列移动到发送环。从输出队列中取出数据包的顺序将取决于 QoS 配置；有关 QoS 如何在各种情况下应用于队列的更多信息，请参阅 [Chapter 8](#ch08.xhtml#ch08)，“[Quality of Service](#ch08.xhtml#ch08)”。

**Step 4.** 在数据包被移动到发送环之后的一段时间内，发送 PHY 芯片会从数据包缓冲区读取每一位，将其编码为适合出站物理介质类型的格式，并将数据包复制到线路上。

## 关于分组交换的最终思考

分组交换的细节可能看起来陷入琐碎。毕竟，数据包或帧在两个设备之间如何移动是否真的重要？是否真的那么关键去理解串行化和反串行化、等价成本多路径、交叉开关结构争用、发送环等？

从某种意义上说，这些细节对普通网络工程师并不重要。当网络设备正在执行其通过自身移动数据的任务时，交换机为完成该任务所遵循的实际过程都是微不足道的。“它就是能工作。”

然而，交换内部结构通常在很大程度上影响网络设计。例如，考虑端口到端口延迟。在某些高流量网络中，交换机将帧从入口端口移动到出口端口所需的时间会影响整体应用性能。在现代交换机中，端口到端口延迟以单个微秒或数百纳秒来衡量。如果一台交换机在 1 微秒内完成工作，而另一台可以在 400 纳秒内完成，这可能会影响硬件选择。

另一个考虑因素是故障排除。当网络设备似乎没有转发其接收到的所有数据包时，即入口大于出口，会发生什么？网络结构中少量数据包丢失很难追踪。了解网络设备的内部分组交换过程能极大地揭示故障可能发生的位置。

因此，不要将分组交换视为对有志于网络的人来说“过于接近线路”而无关紧要。相反，应拥抱对分组交换的了解，以获得其提供的对整体网络性能的深刻见解。

## 进一步阅读

“1.5. Basics of How Operating Systems Work.” *Operating Systems Study Guide*. Accessed April 22, 2017. [http://faculty.salina.k-state.edu/tim/ossg/Introduction/OSworking.html](http://faculty.salina.k-state.edu/tim/ossg/Introduction/OSworking.html).

Bollapragada, Vijay, Russ White, and Curtis Murphy. *Inside Cisco IOS Software Architecture*. Indianapolis, IN: Cisco Press, 2000.

*BSTJ 18: 1. January 1939: Crossbar Dial Telephone Switching System. (Scudder, F. J.; Reynolds, J. N.)*, 1939. [http://archive.org/details/bstj18-1-76](http://archive.org/details/bstj18-1-76).

“Cisco Nexus 5548P Switch Architecture.” *Cisco*. Accessed July 29, 2017. [http://www.cisco.com/c/en/us/products/collateral/switches/nexus-5548p-switch/white_paper_c11-622479.html](http://www.cisco.com/c/en/us/products/collateral/switches/nexus-5548p-switch/white_paper_c11-622479.html).

“Fast Ethernet | Integrating 100mbps into Existing 10mbps Networks.” *Savvius*. Accessed April 22, 2017. [https://www.savvius.com/resources/compendium/fast_ethernet/overview](https://www.savvius.com/resources/compendium/fast_ethernet/overview).

Heineman, George T., Gary Pollice, and Stanley Selkow. *Algorithms in a Nutshell: A Practical Guide*. 2nd edition. O’Reilly Media, 2016.

Inniss, Daryl, and Roy Rubenstein. *Silicon Photonics: Fueling the Next Information Revolution*. 1st edition. Morgan Kaufmann, 2016.

“Intel Ethernet Switch Family Hash Efficiency.” Intel, April 2009. [https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/ethernet-switch-hash-efficiency-paper.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/ethernet-switch-hash-efficiency-paper.pdf).

“Interrupt.” *Wikipedia*, Accessed February 3, 2017. [https://en.wikipedia.org/w/index.php?title=Interrupt&oldid=763436239](https://en.wikipedia.org/w/index.php?title=Interrupt&oldid=763436239).

Kloth, Axel K. *Advanced Router Architectures*. Boca Raton, FL: CRC Press, 2005.

Konheim, Alan G. *Hashing in Computer Science: Fifty Years of Slicing and Dicing*. 1st edition. Wiley-Interscience, 2011.

Lekkas, Panos. *Network Processors: Architectures, Protocols and Platforms*. 1st edition. New York: McGraw-Hill Education, 2003.

Meiners, Chad R., Alex X. Liu, and Eric Torng. *Hardware Based Packet Classification for High Speed Internet Routers*. 2010 edition. New York: Springer, 2010.

Noubir, Guevara. “Signal Encoding Techniques.” Accessed April 22, 2017. [http://www.ccs.neu.edu/home/noubir/Courses/CS6710/S12/slides/signals-encoding.pdf](http://www.ccs.neu.edu/home/noubir/Courses/CS6710/S12/slides/signals-encoding.pdf).

Stringfield, Nakia, Russ White, and Stacia McKee. *Cisco Express Forwarding*. 1st edition. Indianapolis, IN: Cisco Press, 2007.

Thakur, Dinesh. “Encoding Techniques and Codec.” *Computer Notes*. Accessed April 22, 2017. [http://ecomputernotes.com/computernetworkingnotes/communication-networks/encoding-techniques-and-codec](http://ecomputernotes.com/computernetworkingnotes/communication-networks/encoding-techniques-and-codec).

“Understanding IEEE 802.3ad Link Aggregation—Technical Documentation—Support—Juniper Networks,” March 26, 2013. [https://www.juniper.net/documentation/en_US/junose14.2/topics/concept/802.3ad-link-aggregation-understanding.html](https://www.juniper.net/documentation/en_US/junose14.2/topics/concept/802.3ad-link-aggregation-understanding.html).

## Review Questions

1. What happens if one end of a link is configured as a bundle and the other end is not? Specifically, what happens if one device thinks `STP` is running and the other does not?

2. Why is flow hashing typically used as opposed to round-robin as a forwarding algorithm in `ECMP`?

3. What is the purpose of a multistage fabric? Provide an example.

