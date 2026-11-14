

识别、保护和捍卫您的 *事物* 以及您的朋友、家人和客户的事物。

## 进一步阅读

- “利用 PLC 编程信息区分面向互联网的设备” https://www.hsdl.org/?abstract&did=757013
- 由 BullGuard 提供的物联网扫描仪 https://iotscanner.bullguard.com/
- NIST 特别出版物 800-82，修订版 2，“工业控制系统 (ICS) 安全指南” http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-82r2.pdf
- “定量评估与可视化工业系统攻击面” https://www.cl.cam.ac.uk/~fms27/papers/2011-Leverett-industrial.pdf

## 参考文献

- 1. X. Xu, “服务创新中的物联网,” *The Amfiteatru Economic Journal*, 4(6, 2012年11月): 698–719.
- 2. M. Swan, “传感器狂热！物联网、可穿戴计算、客观度量与量化自我 2.0,” *Journal of Sensor and Actuator Networks*, 1(3, 2012年11月8日): 217–253.
- 3. D. Evans, “物联网：互联网下一进化如何改变一切 [互联网],” Cisco, 2011年4月, https://www.cisco.com/c/dam/en_us/about/ac79/docs/innov/IoT_IBSG_0411FINAL
- 4. *The Economist*, “物联网（将被黑客攻击）,” 2014年7月12日, https://www.economist.com/news/leaders/21606829-hooking-up-gadgets-web-promises-huge-benefits-security-must-not-be.
- 5. A. Harper, “消费者安全意识对物联网采用的影响：一项相关性研究,” 博士论文, Capella University, 2016, https://pqdtopen.proquest.com/doc/1853097232.html?FMT=ABS.
- 6. D. Bandyopadhyay, J. Sen, “物联网：技术与标准化中的应用与挑战,” *Wireless Personal Communications*, 58(1, 2011年5月): 49–69.
- 7. Harper, “消费者安全意识对物联网采用的影响.”
- 8. Z. Chen, F. Xia, T. Huang, F. Bu, and H. Wang, “物联网定位方法,” *The Journal of Supercomputing*, 63(3, 2013年3月): 657–674.
- 9. H. Jayakumar, K. Lee, W. Lee, A. Raha, Y. Kim, and V. Raghunathan, “为物联网供电,” 收录于《2014年低功耗电子与设计国际研讨会论文集》, ACM, 2014, 375–380, http://doi.acm.org/10.1145/2627369.2631644.
- 10. Zigbee, Wikipedia, 2017, https://en.wikipedia.org/w/index.php?title=Zigbee&oldid=809655996.
- 11. Harper, “消费者安全意识对物联网采用的影响.”
- 12. H. Jayakumar, 等人, “为物联网供电.”
- 13. J. Sarto, “用于传感器网络的 ZigBee 与 6LoWPAN 对比,” LSR, https://www.lsr.com/white-papers/zigbee-vs-6lowpan-for-sensor-networks.
- 14. S. Schneider, “理解物联网背后的协议,” Electronic Design, 2013年10月9日, www.electronicdesign.com/iot/understanding-protocols-behind-internet-things.
- 15. J. Matherly, Shodan完全指南：收集。分析。可视化。让互联网情报为你所用, Lean Publishing, 2017.
- 16. V. Pasknel, “使用 MQTT 黑客攻击物联网,” Morphus Labs, 2017年7月19日, https://morphuslabs.com/hacking-the-iot-with-mqtt-8edaf0d07b9b.
- 17. Pasknel, “使用 MQTT 黑客攻击物联网.”
- 18. Pasknel, “使用 MQTT 黑客攻击物联网.”
- 19. Mirai（恶意软件）, Wikipedia, 2017, https://en.wikipedia.org/w/index.php?title=Mirai_(malware)&oldid=807940975.
- 20. S. M. Kerner, “DDoS攻击正朝1太比特纪录迈进,” eWEEK, 2016年9月25日, www.eweek.com/security/ddos-attacks-heading-toward-1-terabit-record.
- 21. Mirai（恶意软件）, Wikipedia.
- 22. Kerner, “DDoS攻击正朝1太比特纪录迈进.”
- 23. C. Farivar, “计算机科学学生认罪创建 Mirai 僵尸网络,” Mirai | Tim’s Tablet Web Site, 2017年10月13日, http://tablets.yourfree.wordpress.com/?tag=mirai.
- 24. B. Krebs, “新 Mirai 蠕虫让90万德国用户离线,” Krebs on Security, 2016年11月16日, https://krebsonsecurity.com/2016/11/new-mirai-worm-knocks-900k-germans-offline/.
- 25. M. Mimoso, “Mirai僵尸网络数量自源代码发布以来翻了一倍多,” 2016年10月19日, https://threatpost.com/mirai-bots-more-than-double-since-source-code-release/121368/.
- 26. T. Fox-Brewster, “大量 IoT 摄像头存在可被黑客攻击的漏洞——下一次网络危机即将来临,” Forbes, 2017年10月23日, https://www.forbes.com/sites/thomasbrewster/2017/10/23/reaper-botnet-hacking-iot-cctv-iot-cctv-cameras/.

## 嵌入式设备剖析

本章对嵌入式设备提供了高层次的视图，旨在提供相关词汇以及对潜在关注领域的高层次理解。嵌入式设备是满足特定需求或具有有限功能的电气或机电设备。嵌入式设备的示例包括安防系统、网络路由器/交换机、摄像头、车库门开启器、智能恒温器、可控灯泡和手机。随着我们的设备为了便利性而获得远程连接功能，它们也为攻击者通过我们的网络进入我们的生活提供了更多机会。

本章大部分讨论都围绕集成电路（IC）展开。IC 是指封装在小型外壳内的电气元件集合，通常称为 _芯片_。一个简单的示例是四路双输入 OR<sup>1</sup> 门 IC，其中四个双输入 OR 电路被实现在单个芯片内。在我们的情况中，IC 将复杂得多，并在单个 IC 内包含整个多计算元件。另请注意，本章假设您熟悉万用表以及电气电路的基本概念，例如电压、电流、电阻和接地。

本章将讨论以下主题：

- CPU
- 串行接口
- 调试接口
- 软件

### CPU

与大多数人熟悉的台式机系统不同，嵌入式世界基于嵌入式功能、系统所需复杂性、价格、功耗、性能和其他考虑因素，使用许多不同的处理架构。由于嵌入式系统通常具有更明确的功能，它们往往更适合更可量化的性能要求。因此，会使用一系列软件和硬件要求来确定合适的微处理器、微控制器或片上系统（SoC）。

### 微处理器

微处理器不包含芯片内部的内存或程序存储。基于微处理器的设计可以利用大量内存和存储，并可以运行诸如 Linux 之类的复杂操作系统。普通 PC 是利用基于微处理器设计的设备的示例。

### 微控制器

微控制器在嵌入式世界中很常见。微控制器通常在单个芯片内集成 CPU 核心（或多个核心）、内存、存储和 I/O 端口。微控制器非常适合执行简单或明确定义的低性能应用的高度嵌入式设计。由于应用程序和硬件的简单性，微控制器上的软件通常使用汇编或 C 等低级语言编写，并且不包含操作系统（OS）。微控制器的应用示例包括电子门锁和电视遥控器。

根据特定微控制器，可以在硬件中实现保护机制以帮助保护应用程序。示例包括对程序存储的读取保护以及禁用片上调试接口激活。虽然这些保护提供了一层防护，但无法保证这些保护不会被绕过。

### 片上系统 (SoC)

片上系统（SoC）是在单个 IC 内集成一个或多个微处理器内核或微控制器以及各种集成硬件特性的系统。例如，手机的 SoC 可能包含图形处理单元（GPU）、声音处理器、内存管理单元（MMU）、蜂窝网络控制器和网络控制器。SoC 的主要优势是由于芯片更少、应用尺寸更小而降低成本。这些通常以更定制化的方式使用。与微控制器将程序存储在内部并提供有限内存不同，SoC 通常利用外部存储和内存。

### 常见处理器架构

尽管存在许多微控制器架构，例如 Intel 8051、Freescale (Motorola) 68HC11 和 Microchip PIC，但 ARM 和 MIPS 两种架构在联网设备中出现得多得多。在使用反汇编器、构建工具和调试器等工具时，了解处理器架构非常重要。处理器架构通常可以通过目视检查电路板并定位处理器来识别。

ARM 是一种授权架构，被德州仪器（Texas Instruments）、Apple、三星（Samsung）等众多微处理器、微控制器和 SoC 制造商使用。ARM 内核根据预期应用程序以多个配置文件（profile）进行授权。ARM 内核既有 32 位也有 64 位架构，并可配置为大端或小端字节序。表 23-1 说明了通常使用这些配置文件及其应用。

