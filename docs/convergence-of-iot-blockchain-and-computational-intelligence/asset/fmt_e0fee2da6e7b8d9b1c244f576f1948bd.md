
### 表 3.4 安全问题规范

[表 3.4](#chapter3.xhtml#tbl3_4) 规定了安全问题。在所有 IoT 基础设施中，应实施各种技术以确保所有连接的安全。SoC 是组织具有集中功能的设施。该安全团队负责安全相关问题。安全供应商从根源提供安全保障。为解决分层安全模型，硬件隔离在处理器和缓存中定义了完整的 SoC。如果硬件具有允许不同操作系统的管理程序，则 SoC 位于虚拟机 (VM) 上。软件可通过系统内存管理单元 (MMU) 在出现漏洞时进行隔离。用户空间隔离在 Linux 操作系统的内核中完成。加密数据以变量和文本字符串的形式存储在内存中。为保护数据，开发人员执行网络测试、渗透测试和配置防火墙。发送和接收数据需要数据认证。在网络路由时应实施加密操作。核心处理器设计有加密引擎，并支持加密和解密。它以高速率提供数据安全。

#### 表 3.4 数据安全问题

| 数据状态 | 问题 | 硬件平台提供的安全性 | 软件平台提供的安全性 |
| :--- | :--- | :--- | :--- |
| 静态数据 | 信任根 | SoC (安全运营中心) | 是 |
| | 信任链 | 引导加载程序经过验证和认证 | 操作系统经过验证和认证 |
| 使用中数据 | 硬件强制隔离 | 实现多个 SoC | 不适用 |
| | 软件强制分离 | 嵌入式管理程序上的 SoC | 支持虚拟化的多核 SoC |
| | 用户空间隔离 | 不适用 | 基于应用程序的数据内存隔离 |
| | 信息或数据混淆 | 配置防火墙、网络压力测试和网络渗透分析 | 不适用 |
| 运动中数据 | 设备劫持 | 不适用 | 带加密引擎的 SoC |

## 3.4 结论

本章探讨了七层 IoT 框架，这是一种现代且广泛使用的技术。传感器通过事物层的标准化硬件组件传输感知数据。为传输数据，连接层包含在事物层之上。网络层选择用于通信的正确协议并存储在集中式数据存储中。存储的信息可能是非结构化的；数据摄取层支持非结构化数据的传输。通过数据处理层执行数据挖掘和报告。用户可以通过自定义移动应用程序或基于 Web 的应用程序访问应用程序。这由应用层技术支持。第 7 层业务层由 IoT 环境控制，便于客户进行决策。该层负责向客户交付优质产品。IoT 通过利用多种技术促进行业转型，已成为市场的一部分。技术因众多进步而持续演进；然而，了解当前可用技术的特性和认知至关重要。由于企业在很大程度上由 IoT 驱动，某些技术的缺陷可在未来得到解决。

## 参考文献

*   Ahmed, S. H.; Rani, S. A hybrid approach, Smart Street use case and future aspects for internet of things in smart cities. Future Generation Computer Systems. 2018, 79, 941–951.
*   [Aman, A. H. M](#chapter3.xhtml#b3ref3_2).; Yadegaridehkordi, E.; Attarbashi, Z. S.; Hassan, R.; Park, Y. J. A survey on trend and classification of internet of things reviews. IEEE Access. 2020, 8, 111763–111782.
*   [Ande, R](#chapter3.xhtml#b3ref3_3).; Adebisi, B.; Hammoudeh, M.; Saleem, J. Internet of things: Evolution and technologies from a security perspective. Sustainable Cities and Society. 2020, 54, 101728.
*   [Astill, J](#chapter3.xhtml#b3ref3_4).; Dara, R. A.; Fraser, E. D.; Roberts, B.; Sharif, S. Smart poultry management: Smart sensors, big data, and the internet of things. Computers and Electronics in Agriculture. 2020, 170, 105291.
*   [Bera, S](#chapter3.xhtml#b3ref3_5).; Misra, S.; Vasilakos, A. V. Software-defined networking for internet of things: A survey. IEEE Internet of Things Journal. 2017, 4(6), 1994–2008.
*   [Glaroudis, D](#chapter3.xhtml#b3ref3_6).; Iossifides, A.; Chatzimisios, P. Survey, comparison and research challenges of IoT application protocols for smart farming. Computer Networks. 2020, 168, 107037.
*   [HaddadPajouh, H](#chapter3.xhtml#b3ref3_7).; Khayami, R.; Dehghantanha, A.; Choo, K. K. R.; Parizi, R. M. AI4SAFE-IoT: An AI-powered secure architecture for edge layer of internet of things. Neural Computing and Applications. 2020, 32(20), 16119–16133.
*   [Kamilaris, A](#chapter3.xhtml#b3ref3_8).; Kartakoullis, A.; Prenafeta-Boldú, F. X. A review on the practice of big data analysis in agriculture. Computers and Electronics in Agriculture. 2017, 143, 23–37.
*   [Karthiprem, S](#chapter3.xhtml#b3ref3_9).; Selvarajan, S.; Sankar, M. S. Recognizing the moving vehicle while driving on Indian roads. International Journal of Applied Engineering Research. 2016, 10(20), 41471–41477.
*   [Mishra, B](#chapter3.xhtml#b3ref3_10).; Jena, D.; Somula, R.; Sankar, S. Secure key storage and access delegation through cloud storage. International Journal of Knowledge and Systems Science (IJKSS). 2020, 11(4), 45–64.
*   [Nazini, H](#chapter3.xhtml#b3ref3_11).; Sasikala, T. Simulating aircraft landing and takeoff scheduling in distributed framework environment using Hadoop file system. Cluster Computing. 2019, 22(6), 13463–13471.
*   [Osanaiye, O](#chapter3.xhtml#b3ref3_12).; Chen, S.; Yan, Z.; Lu, R.; Choo, K. K. R.; Dlodlo, M. From cloud to fog computing: A review and a conceptual live VM migration framework. IEEE Access. 2017, 5, 8284–8300.
*   [Perez, S](#chapter3.xhtml#b3ref3_13).; Hernández-Ramos, J. L.; Raza, S.; Skarmeta, A. Application layer key establishment for end-to-end security in IoT. IEEE Internet of Things Journal. 2019, 7(3), 2117–2128.
*   Revathi, T. K.; Sathiyabhama, B.; Sankar, S. A deep learning based approach for diagnosing coronary inflammation with multi-scale coronary response dynamic balloon tracking (MSCAR-DBT) based artery segmentation in coronary computed tomography angiography (CCTA). Annals of the Romanian Society for Cell Biology. 2021a, 25(6), 4936–4948.
*   [Samanta, S](#chapter3.xhtml#b3ref3_15).; Panda, M.; Ramasubbareddy, S.; Sankar, S.; Burgos, D. Spatial-resolution independent object detection framework for aerial imagery. CMC- Computers Materials and Continua. 2021, 68(2), 1937–1948.
*   [Sankar, S](#chapter3.xhtml#b3ref3_16).; Ramasubbareddy, S.; Chen, F.; Gandomi, A. H. Energy-Efficient Cluster-Based Routing Protocol in Internet of Things Using Swarm Intelligence. In 2020 IEEE Symposium Series on Computational Intelligence (SSCI). 2020a, December, 219–224.
*   [Sankar, S](#chapter3.xhtml#b3ref3_17).; Somula, R.; Kumar, R. L.; Srinivasan, P.; Jayanthi, M. A. Trust-aware routing framework for internet of things. International Journal of Knowledge and Systems Science (IJKSS). 2021, 12(1), 48–59.
*   [Sankar, S](#chapter3.xhtml#b3ref3_18).; Srinivasan, P. Internet of things (IoT): A survey on empowering technologies, research opportunities and applications. International Journal of Pharmacy and Technology. 2016, 8(4), 26117–26141.
*   [Sankar, S](#chapter3.xhtml#b3ref3_19).; Srinivasan, P. Composite metric based energy efficient routing protocol for internet of things. International Journal of Intelligent Engineering and Systems. 2017, 10(5), 278–286.
