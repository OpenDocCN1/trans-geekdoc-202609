

维持网络的正常运行。然而，在其他场景中，实时性要求可能没有那么严格，允许在较长时间内进行分析。识别应用场景的实时性要求对于设计NDT系统的硬件和软件以确保其有效使用至关重要。

## 3.5.4 标准化

不同网络制造商通过异构技术实现的协议、功能和服务的多样性，是建立统一NDT系统的重大挑战。更甚的是，当旨在将它们应用于不同场景，并跨不同层面在技术层面进行标准化时（Hu et al. 2021, Zhou et al. 2022）。因此，有必要提出一个具有明确定义的组件和功能的统一NDT架构，以便根据为不同应用场景采用的方法进行后续调整。之后，可以通过采用现有技术或不采用现有技术，来识别和定义架构不同层之间的接口（Zhou et al. 2022）。

## 3.5.5 NDT系统的可扩展性

网络的规模以及为建模这些环境所需的数据量，可能会在确保网络可扩展性方面造成多种问题。大量网络数据有助于实现更准确的网络模型。然而，这些数据的获取、建模和大规模存储是在可扩展性背景下出现的问题（Almasan, Ferriol-Galmés and Paillisse, et al. 2022a, Almasan, Ferriol-Galmés and Suárez-Varela, et al. 2022b, Zhou et al. 2022）。这些问题在总体上是由采用NDT导致的容量过度使用所引起的高通信成本和大规模数据存储造成的（Zhou et al. 2022）。因此，需要采用高效的数据采集工具和压缩技术，以最大限度地减少在网络上传输的数据及其占用的空间。此外，当NDT系统用于随着时间的推移而增长的网络环境时，其在准确性或执行时间方面的性能会下降，这表明所选择的技术方法可能并不最合适（Almasan, Ferriol-Galmés and Suárez-Varela, et al. 2022b）。例如，当基于神经网络的NDT模型执行时间过长，使其在生产环境中的采用变得不可行时，采用替代方法（例如，基于数学抽象的方法，如仿真或分析模型）可能更合适。这是另一个应指导根据NDT将被应用的场景选择合适技术方法的因素。

## 3.6 结论

本章考察了将DT范式应用于计算机网络领域（即NDT）的情况。NDT系统在真实网络环境与虚拟孪生环境之间保持持续同步，确保现实世界中的操作基于对虚拟环境中实时数据的分析来执行。近年来，工业界和学术界已提出多种实际实现。然而，许多实现并未完整实现NDT的关键特征，这使得定义和分类NDT方法变得复杂。我们观察到，自互联网诞生之初起就已采用网络仿真方法，此后即可将其归类为一种NDT，即网络数字模型。我们还能够识别出，只有通过基于意图的网络自动化和闭环自动化处理全生命周期网络管理的工业工具，才能在今天有效地在其完整设计中被归类为NDT，主要原因是它们在物理环境和虚拟环境之间保持双向通信。

我们强调，除了在物理世界和虚拟世界之间保持双向通信外，进一步的挑战今天也具有重要意义，例如为实现目标应用场景的关键目标而维持软件和硬件要求的困难。使用NDT所期望的具体结果很可能最终将指导技术方法的选择。例如，根据要建模的网络规模，抽象程度更高的方法可能会被证明更高效。然而，需要不同方法的新实际实现，以确保模型的成熟度并从生产环境中收集足够的数据。迄今为止，仍缺乏对NDT的统一定义、参考架构和通用实现产物（例如，开放数据模型、API、标准接口等），这可能会损害NDT系统未来的互操作性。

## 参考文献

- Ahrenholz, Jeff. “CORE网络仿真平台比较.” 2010-Milcom 2010军事通信会议. IEEE, 2010: 166–171.
- Almasan, Paul, et al. “数字孪生网络：机遇与挑战.” 2022a.
- Almasan, Paul, et al. “网络数字孪生：背景、赋能技术与机遇.” IEEE Communications Magazine 60.11 (2022): 22–27.
- Bacon, David F., Alexander Dupuy, Jed Schwartz, and Yechiam Yemini. “NEST：一种网络仿真与原型工具.” USENIX Winter. 1988: 17–78.
- Barricelli, Barbara Rita, Elena Casiraghi, and Daniela Fogli. “数字孪生调查：定义、特征、应用与设计影响.” IEEE Access, 7 (2019): 167653–167671.
- Beckett, Ryan, Gupta Aarthi, Ratul Mahajan, and David Walker. “网络配置验证的一般方法.” 2017 Conference of the ACM Special Interest Group on Data Communication (SIGCOMM’17). New York: Association for Computing Machinery, Inc. 2017. 155–168.
- Chaudhary, Rachna, Shweta Sethi, Rita Keshari, and Goel Saksi. “网络仿真器-3与网络仿真器-2比较研究.” International Journal of Computer Science and Information Technologies, 3 (2012): 3085–3092.
- Cooper, Robert B. “排队论：90分钟教程.” Proceedings of the ACM’81 Conference, 1981: 119–122.
- Dodin, Roman. “Containerlab...以及人们如何使用它.” NLNOG. Amsterdam: Nokia, 2021.
- Dzerkals, Uldis. EVE-NG Professional. EVE-NG LTD, 2022.
- Fantom, Will, Paul Alcock, Ben Summes, Charalampos Rotsos, and Nicholas Race. “测试驱动网络管理的NEAT方式.” NOMS 2022-2022 IEEE/IFIP Network Operations and Management Symposium. Budapest, Hungary: IEEE, 2022: 1–5.
- Ferriol-Galmés, Miquel, et al. “RouteNet-Erlang：用于网络性能评估的图神经网络.” IEEE INFOCOM 2022 - IEEE Conference on Computer Communications, 2022: 2018–2027.
- Ferriol-Galmés, Miquel, Xiangle Cheng, Xiang Shi, Shihan Xiao, Pere Barlet-Ros, and Albert Cabellos-Aparicio. “FlowDT：面向计算机网络的流感知数字孪生.” ICASSP, IEEE International Conference on Acoustics, Speech and Signal Processing - Proceedings. Singapore: IEEE, 2022. 8907–8911.
- Fogel, Ari, et al. “网络配置分析的一般方法.” 12th USENIX Symposium on Networked Systems Design and Implementation (NSDI’15). Oakland, CA: USENIX Association, 2015. 469–483.
- Fuller, Aidan, Zhong Fan, Charles Day, and Chris Barlow. “数字孪生：赋能技术、挑战与开放研究.” IEEE Access 8 (2020): 108952–108971.
- Goto, Yuki, Bryn Ng, Winston K. G. Seah, and Yutaka Takahashi. “基于现实OpenFlow交换机模型的软件定义网络排队分析.” Computer Networks, 164 (2019): 106892.
- Henderson, Thomas R., Mathieu Lacage, and George F. Riley. “使用NS-3仿真器进行网络仿真.” SIGCOMM Demonstration, 14 (2008): 527.
- Hong, Hanshu, et al. “NetGraph：面向数据中心网络的智能运营数字孪生平台.” Proceedings of the ACM SIGCOMM 2021 Workshop on Network-Application Integration (NAI’21). Proceedings of the ACM SIGCOMM 2021 Workshop on Network-Application Integration, 2021: 26–32.
- Hu, Weifei, Tangzhou Zhang, Xiaoyu Deng, Zhenyu Liu, and Jianrong Tan. “数字孪生：其赋能技术、应用与挑战的最新综述.” Journal of Intelligent Manufacturing and Special Equipment, 2021: 1–34.
- Hui, Linbo, Mowei Wang, Liang Zhang, Lu Lu, and Yong Cui. “面向网络的数字孪生：一种数据驱动的性能建模视角.” arXiv preprint arXiv:2206.00310, 2022.

