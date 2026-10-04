
Traditional stateful packet filter policy management is not a realistic option when considering many small packet filters deployed as VNFs. To handle VNF packet filter management, central policy management is used. A single policy leveraging metadata is written.

In this context, metadata refers to less granular ways to group objects. For example, users might be grouped by an object in Microsoft’s Active Directory. Applications might be grouped by name. Hosts might be grouped by DNS suffix. Leveraging meta-data, humans can write policies that say, “Hosts containing ‘web’ as part of their name can perform SQL queries against hosts containing ‘dbase’ as part of their name.”

The central policy manager software analyzes the policy, the metadata, and the hosts filtered by VNF packet filters. The policy manager then compiles and deploys the correct packet filter rules for each VNF stateful packet filter. [Figure 27-6](#ch27.xhtml#ch27fig06) illustrates.

![Image](graphics/27fig06.jpg)

**Figure 27-6** *A Centralized Policy Manager*

This approach removes the burden of granular management from the network operator, shifting it to software. Policy management software makes managing dynamic VNFs possible.

### Intent-Based Networking

An emerging technique being used to handle complex configuration is intent-based networking. Intent-based networking allows for plain language to be used to express a configuration desire. While traditional configuration describes exactly how the network is to behave, intent-based networking describes the hoped-for outcome, but not how the outcome will be achieved.

Intent-based networking is interesting in the context of VNFs because it introduces a layer of abstraction between network state and configuration specifics. The intent engine interprets the generic intent expressed by a human or possibly software, and then sends the specific configuration (or individuated policies) required to convert the intent into network state. [Figure 27-7](#ch27.xhtml#ch27fig07) illustrates.

![Image](graphics/27fig07.jpg)

**Figure 27-7** *Intent-based Networking*

Intent is also a useful tool in enforcing a desired network state. If intent is used to describe the desired network state, and the intent engine can interpret those directives into configuration specifics, then the intent engine can also be leveraged to determine when the network state no longer matches the expressed intent.

Intent is still very new, and proving difficult to implement. Wide variations in network hardware and network operating system software introduce many variables that make implementing intent-based networking a complex programming challenge. Nonetheless, specific intent-based networking implementations have found their way into open source projects such as Open Network Operating System (ONOS) and OpenDaylight. In addition, several commercial variants have been introduced to the market, with others expected to find their way to market soon.

### Benefit

The chief benefit of VNF automation is a decreased time to service. Bringing applications to market quickly is a critical benefit of VNFs, as they allow for a service to be composed and instantiated with a minimum of risk and without human configuration.

Centralized policy management based on metadata and intent-based networking are examples of tooling that enable VNF spin-up time to be reduced.

## Compute Advantages and Architecture

Physical network devices such as switches and routers run on built-for-purpose silicon. Other network devices such as firewalls and load balancers might run on general-purpose CPUs while offloading specific functions to dedicated hardware. Encryption is an example of this, where a load balancer might run most functions on a general-purpose CPU, while mathematically intensive packet encryption is offloaded to dedicated silicon to maintain high throughput levels.

Built-for-purpose silicon chips are called Application-Specific Integrated Circuits (ASICs). ASICs are designed by networking vendors to perform a small number of networking functions and do them quickly. ASICs are limited in function—they are “application specific.” Thus, network devices perform tasks using ASICs to do what they do very well but cannot perform anything beyond what the ASIC was designed for.

In contrast to ASICs, general-purpose processors are found in servers and desktop computers. General-purpose processors are designed to run a wide variety of soft-ware. Intel x86 processors are the most widely known general-purpose processor; network functions that have been virtualized are said to be running on x86.

While ASICs do a small number of things extremely well, x86 processors do a large number of things merely adequately. This is critical to understanding VNFs. When a network function is virtualized to run on x86, performance might be reduced when compared to the same function running on an ASIC.

Discussions about VNFs and performance are commonplace due to two major concerns.

1. VNFs need to function quickly enough to fill the network pipe of the host they run on. Ethernet speeds of 10, 25, 40, and even higher are all interesting to network operators leveraging VNFs.
2. VNFs use the general-purpose x86 CPU in hosts to provide their services. These hosts are also going to be running other workloads the data center requires—web server, database engines, and so on. CPU cycles used for VNFs are not available for those other workloads.

### Improving VNF Throughput

There are two significant means VNF software architects use to gain sufficient throughput from their network services. The first means is software optimization. The second is hardware offload.

Software optimization is related to the peculiarities of the operating system that many virtualized network functions run in, Linux. Linux processes network functions in the Linux kernel. However, the VNF software is going to be running as a user. When the user space program needs access to the network interface hardware to send or receive packets, it will perform a system call to the kernel. A hardware interrupt is performed, and data is copied between kernel and user space. All of this takes time, reducing the maximum amount of throughput the VNF might otherwise achieve.

Software optimization of VNFs seeks to eliminate the back-and-forth between kernel space and user space. Many networking software stacks run completely in Linux user space. To gain access to the network hardware, these user space stacks leverage an open source project called Data Plane Development Kit (DPDK). DPDK provides a means for a networking stack to directly access the networking interface inside a host without having to perform system calls to the kernel. This reduces latency, subsequently increasing throughput.

Hardware offload consists of network interface cards (NICs) with customized silicon designed to offload the x86 CPU from some VNF tasks. NICs with customized silicon are costly compared to less-capable NICs, as well as being specialized for specific environments. These custom NICs run with special drivers, handing off functions from specific VNFs to hardware to accelerating them.

## Considering Tradeoffs

*If you have not found the tradeoffs, you have not looked hard enough*.

This is true in every area of engineering (and life!), including NFV. This chapter has largely considered the case for NFV. What are the tradeoffs? The State/Optimization/Surface (SOS) triad will be useful in evaluating these tradeoffs.

### State
