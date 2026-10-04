

• `Border Gateway Protocol (BGP)`，它在两个模型中都在传输层之上运行，提供独立实体（自治系统）之间的路由（可达性）。这是否使其成为应用层协议？同时，该协议正在提供网络层运行所需的路由信息。这是否使其成为网络层协议？

• `IPsec` 向 Internet 协议（`IP`）头部添加信息，并规定了在网络上传输的信息的加密。由于 `IP` 是网络层，而 `IPsec`（某种程度上）在 `IP` 之上运行，这是否使 `IPsec` 成为传输协议？或者，由于 `IPsec` 与 `IP` 并行运行，它是网络层协议？

争论这些类型的问题可以在技术会议或标准会议上提供很多娱乐；然而，它们也指出了这些模型定义方式中存在一定程度的模糊性。这种模糊性来自于这些模型中形式与功能的精心混合；它们描述的是信息包含的位置、谁使用信息、对信息做了什么，还是为解决通过网络传输信息中的特定问题而需要满足的特定目标？答案是——以上所有。或者也许，*视情况而定*。

这导致了以下观察：任何数据承载协议实际上只能提供四种功能：传输、多路复用、差错校正和流量控制。如果这些听起来很熟悉，那应该是的——因为这些正是我们在 [Chapter 2](#ch02.xhtml#ch02) “[Data Transport Problems and Solutions](#ch02.xhtml#ch02)” 中对人类语言的调查中发现的同样的四种功能。

在这四种功能中存在两种自然分组：传输和多路复用，差错和流量控制。因此大多数协议都属于做以下两件事之一：

• 协议提供传输，包括从一种数据格式到另一种数据格式的某种形式的转换；以及多路复用，协议保持来自不同主机和应用程序的数据分离的能力。

• 协议提供差错控制，要么通过纠正小错误的能力，要么通过重传丢失或损坏的数据；以及流量控制，它防止由于网络交付数据的能力与应用程序生成数据的能力不匹配而导致不必要的丢包。

从这个角度来看，`Ethernet` 提供传输服务和流量控制，因此它是一个集中于单个链路、端口到端口（或隧道端点到隧道端点）内的混合体。`IP` 是一种多跳协议（跨越一个以上物理链路的协议）提供传输服务，而 `TCP` 是一种使用 `IP` 传输机制的多跳协议，并提供差错校正和流量控制。[Figure 3-4](#ch03.xhtml#ch03fig04) 说明了迭代模型。

![Image](graphics/03fig04.jpg)

**Figure 3-4** *The RINA Model*

模型的每一层都有相同的两种功能之一，只是范围不同。该模型在网络协议工作中并未广泛流行，但它比七层或四层模型提供了对网络协议动态和操作的更简单视图，并且增加了范围的概念，这在考虑网络操作时至关重要。信息的范围是网络稳定性和弹性的基础。

### Connection Oriented and Connectionless

迭代模型也再次将面向连接和无连接网络协议的概念带入了白天。

面向连接的协议在发送第一个数据位之前，先建立端到端连接，包括传输有意义数据所需的所有状态。状态可能包括诸如服务质量要求、流量通过网络的路径、将发送和接收数据的特定应用程序、可以发送数据的速率以及其他信息。一旦连接建立，数据就可以以非常小的开销传输。

另一方面，无连接服务将传输数据所需的数据与数据本身结合，在单个数据包（或协议数据单元）中携带两者。无连接协议只是将携带数据通过网络所需的状态分散到可能需要数据的每个设备，而面向连接的模型将状态限制在只需要了解特定数据包流的设备上。结果是，无连接网络中单个设备或链路故障可以通过将流量转移到另一条可能路径来修复，而不是重新做建立状态以继续从源到目的传输流量的所有工作。

大多数现代网络都是用无连接传输模型与面向连接的服务质量、差错控制和流量控制模型组合构建的。这种组合并不总是理想的；例如，服务质量通常沿特定路径配置以匹配应遵循这些路径的特定流。将服务质量视为比正在管理的实际流量流更面向连接的做法会导致网络理想状态与各种可能故障模式之间出现强烈的脱节。

### Final Thoughts

了解多个模型，以及它们如何应用于各种网络协议，可以帮助你快速理解以前未遇到过的协议并诊断运营网络中的问题。了解协议模型的历史可以帮助你理解为什么特定协议被设计成那样，特别是协议设计者认为需要解决的问题，以及该协议最初设计时周围的协议。不同类型的模型以不同的方式抽象一组协议；了解多个模型，以及如何将一组协议适配到每个模型中，可以帮助你以不同的方式而不是单一方式理解协议操作，就像在绘画中看到一个花瓶与在三维展示中看到它大不相同。

特别重要的是无连接和面向连接协议的两个概念。这两个概念将是理解流量控制、错误管理以及许多其他协议操作的基础。

下一章将把这些模型应用于较低层的传输协议。

### Further Reading

Cerf, Vinton G., and Edward Cain. “The DoD Internet Architecture Model.” *Computer Networks* 7 (1983): 307–18.

Day, J. *Patterns in Network Architecture: A Return to Fundamentals*. Indianapolis, IN: Pearson Education, 2007.

Grasa, Eduard. “Design Principles of the Recursive InterNetwork Architecture.” In *3rd FIArch Workshop*. Brussels, 2011. [http://www.future-internet.eu/fileadmin/documents/fiarch23may2011/06-Grasa_DesignPrinciplesOTheRecursiveInterNetworkArchitecture.pdf](http://www.future-internet.eu/fileadmin/documents/fiarch23may2011/06-Grasa_DesignPrinciplesOTheRecursiveInterNetworkArchitecture.pdf).

Maathuis, I., and W. A. Smit. “The Battle between Standards: TCP/IP Vs OSI Victory through Path Dependency or by Quality?” In *Standardization and Innovation in Information Technology, 2003. The 3rd Conference on*, 161–76, 2003. doi:10.1109/SIIT.2003.1251205.

Padlipsky, Michael A. *The Elements of Networking Style and Other Essays and Animadversions on the Art of Intercomputer Networking*. Prentice-Hall, 1985.

Russell, Andrew L. “OSI: The Internet That Wasn’t.” Professional Organization. *IEEE Spectrum*, September 27, 2016. [https://spectrum.ieee.org/tech-history/cyberspace/osi-the-internet-that-wasnt](https://spectrum.ieee.org/tech-history/cyberspace/osi-the-internet-that-wasnt).

White, Russ, and Denise Donohue. *The Art of Network Architecture: Business-Driven Design*. 1st edition. Indianapolis, IN: Cisco Press, 2014.

### Review Questions

