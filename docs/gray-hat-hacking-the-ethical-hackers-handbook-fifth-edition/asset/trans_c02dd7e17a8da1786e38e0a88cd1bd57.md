

3. 在 IDA 工具栏中，选择 Labeless | 设置。在显示的对话框中（如图 4-8 所示），更改以下选项：

![](img/5f597c6a70133069118d9e804ace3775_132_0.png)

图 4-8 Labeless 配置设置窗口

- a. 在“远程模块基址”字段中输入上一步找到的模块基址。
- b. 在“同步标签”部分，选择除“函数名作为注释”以外的所有选项。这更多是个人偏好，但如果将函数名直接注释在反汇编代码中，而不是写成注释，通常更容易阅读反汇编。
- c. 启用“重命名时自动同步”选项。
- d. 单击“测试连接”按钮，确保 IDA 与调试后端之间的连接正常工作。

4. 在 IDA 工具栏的 Labeless 下，运行“立即同步标签”选项或使用 ALT-SHIFT-R 热键，将 IDA 的所有注释应用到调试后端。

名称传播到调试后端后，调试器的反汇编列表将与 IDA 的非常相似，并且 IDA 中的所有后续重命名都会自动传播到调试器视图。以下是在应用 IDA 名称后 x64dbg 中的反汇编列表：

```
00007FF6E96F23F8 | 48 83 EC 28 | sub rsp,28
00007FF6E96F23FC | E8 0F 05 00 00 | call <x64dbg.__security_init_cookie>
00007FF6E96F2401 | 48 83 C4 28 | add rsp,28
00007FF6E96F2405 | E9 02 00 00 00 | jmp <x64dbg.__tmainCRTStartup>
```

## 实验 4-2：将调试器内存区域导入 IDA

处理加壳程序或内存注入恶意软件时，Labeless 另一个有用的功能是能够将内存段从调试器导回 IDA。Labeless 支持两种主要工作流来结合静态分析和动态分析：

- 从 IDA 的静态分析会话开始，分析人员希望通过使用调试器进行动态执行，来加深对目标应用程序特定内部工作原理的理解。
- 从动态分析开始，分析人员希望利用 IDA 注释来丰富调试体验，并将额外的运行时解码/解密代码导入 IDA。

虽然第一种工作流已讨论过，但第二种也不应被忽视。在分析混淆或内存注入恶意软件时，能够以更持久的方式（例如 IDA 数据库）保留执行状态和内存非常有用。

Labeless 有两个内存导入选项：

- 全部擦除并导入 此选项会从当前 IDB 中删除所有段，并从调试器导入选定的内存页。
- 保留现有并导入 与前一个选项不同，此选项会保持当前 IDB 不变，仅从调试器导入其他内存页。

第二种导入选项解决了更常见的场景：使用来自调试器的其他内存页扩展当前数据库。当你从 IDA 工具栏中选择 Labeless | IDADump | 保留现有 菜单选项并导入时，将出现一个“选择要转储的内存”窗口，列出调试进程中的所有映射内存页。要导入内存，你可以从列表中选择一个或多个内存区域，或定义所需的虚拟地址范围。

通过高效地结合静态和动态分析工具，并利用各自的优势，分析人员可以同时获得两者的好处，而不必牺牲易用性。

## 总结

高度活跃的逆向工程社区不断发展用于分析各种文件格式以实现不同分析目标的工具和技术。有时，有趣的工具和研究可能会被遗漏，并在这个活跃的社区中不公平地被忽视。本章介绍了一些相对较新的工具和插件，如果有机会使用，可能会显著提高你的分析信心和速度。

## 延伸阅读

- BinCrowd IDA 插件 code.google.com/p/zyanmics/source/checkout?repo=bincrowd-plugin
- BinNavi www.zyanmics.com/binnavi.html
- CollabREate IDA 插件 sourceforge.net/projects/collabreate/
- CrowdDetox IDA 插件 github.com/CrowdStrike/CrowdDetox
- CrowdRE IDA 插件 www.crowdstrike.com/crowdre/downloads/
- funcap IDA 插件 github.com/deresz/funcap
- Hexrays_tools IDA 插件 www.hex-rays.com/contests/2013/hexrays_tools.zip
- HexRaysCodeXplorer IDA 插件 github.com/REhints/HexRaysCodeXplorer
- IDA 插件竞赛 www.hex-rays.com/contests/index.shtml
- IDA Pro FindCrypt www.hexblog.com/?p=27
- IDA Pro FindCrypt2 www.hexblog.com/?p=28
- IDA Sync 插件 www.openrce.org/downloads/details/2
- IDA Toolbag 插件 thunkers.net/~deft/code/toolbag/
- IDA2Sql 插件 wiki.github.com/zyanmics/ida2sql-plugin-ida
- IDAScope 插件 bitbucket.org/daniel_plohmann/simplifire.idascope/
- Optimice IDA 插件 code.google.com/p/optimice/
- PatchDiff2 IDA 插件 code.google.com/p/patchdiff2/

## 参考文献

- 1. ClassInformer IDA 插件，SourceForge，https://sourceforge.net/projects/classinformer/。
- 2. Angel M. Villegas，“安装插件”，FIRST IDA Pro 集成，FIRST IDA Python 插件，2016，http://first-plugin-ida.readthedocs.io/en/latest/installing.html。
- 3. Volatility，高级内存取证框架，GitHub，www.volatilityfoundation.org/。
- 4. YARA，模式匹配瑞士军刀，GitHub，https://github.com/virustotal/yara。
- 5. Axel Souchet（又名 0vercl0k）和 Duncan Ogilvie（又名 mrexodia），Labeless IDA 插件，GitHub，https://github.com/a1ext/labeless。
- 6. Labeless IDA 插件发行版，GitHub，https://github.com/a1ext/labeless/releases/。

## 第 5 章

## 软件定义无线电

无线设备遍布我们生活的方方面面。虽然这些通过消除电线而为我们提供更大自由的设备，但它们也打开了近距离和远程攻击面。例如，有线且未公开暴露的传感器远比覆盖范围超过建筑物周边的无线传感器更难访问。当然，仅仅能够访问无线信号并不能保证能够实施恶意活动，但这确实敞开了大门。

无线射频（RF）黑客技术是一个过于复杂的主题，无法在一个章节中充分覆盖。我们的目标是使用一个简单的设备，向你介绍经济型软件定义无线电（SDR）、用于 SDR 的开源软件，以及评估和测试使用自定义或半自定义无线协议进行通信的产品的流程。

在本章中，我们将讨论以下主题：

- SDR 入门
- 分析简单 RF 设备的逐步流程（SCRAPE）

### SDR 入门

SDR 是一种使用可修改的软件组件来处理原始数据的无线电，而不是完全依赖于专用 RF 硬件和数字信号处理器。SDR 使用通用处理器（例如运行 Linux 的计算机）的资源来提供信号处理，同时使用通用 RF 硬件来捕获和传输数据。SDR 的优势包括能够在单个（可能可远程更新）固件包中处理各种信号和频率。此外，SDR 在构建新系统原型时为开发人员/研究人员提供了灵活性。

### 购买建议

现在你对 SDR 是什么有了概念，是时候寻找你的新玩具了。SDR 的示例包括 HackRF、bladeRF 和 USRP。这些设备均使用计算机上的 USB 端口，并可与 GNU Radio 等开源软件一起使用。表 5-1 对这三种设备进行了快速比较。

| | HackRF | bladeRF x115 | USRP B200 |
|---|---|---|---|
| 工作频率 | 1 MHz 到 6 GHz | 300 MHz 到 3.8 GHz | 70 MHz 到 6 GHz |
| 带宽 | 20 MHz（6 GHz） | 28 MHz（124 MHz） | 56 MHz |
| 双工 | 半双工 | 全双工 | 全双工 |
| 总线 | USB 2 | USB 3 | USB 3 |
| ADC 分辨率 | 8 bit | 12 bit | 12 bit |
| 每秒采样数 | 20 MSps（每秒百万次采样） | 40 MSps | 61 MSps（122 MSps） |
| 近似成本 | $300 | $650 | $745 |

表 5-1 经济型 SDR 设备比较

工作频率决定无线电可以调谐到哪些频率。例如，蓝牙在 2.4 GHz 到 2.48 GHz 之间运行，具体取决于版本，使用 40 到 80 个信道。FM 调频收音机在 87.8 MHz 到 108 MHz 之间运行，使用 101 个信道。虽然 bladeRF 的工作频率比其他两个设备显著低，但附加板可以有效地将低频降至 60 KHz。（我不知道有任何附加板可以提高 bladeRF 的上限。）HackRF 和 USRP B200 也有可用的附加板，可以有效地降低其低频限制。

带宽是应用程序/设备可以扫描的 RF 频谱量。列出的带宽在各自网站上发布，但可能取决于加载的固件而有所不同。例如，HackRF 固件版本 2017.02.01 现在支持扫频模式，允许设备在完整的 6 GHz 范围内扫频。bladeRF 添加了支持以将其带宽扩展到 124 MHz。增加带宽的一个潜在好处是能够同时监控所有蓝牙信道（80 MHz）。

双工是指两个系统如何相互通信。全双工意味着设备可以同时发送和接收。半双工，你无疑已经猜到了，意味着设备可以发送和接收数据，但不能同时进行。半双工通信的示例包括对讲机和许多计算机 IP 语音应用程序。当双方同时尝试说话时，会发生冲突并且数据会丢失。虽然全双工更灵活，但 SDR 的双工方式不太可能妨碍分析的有效性。

模数转换（ADC）分辨率是指每个采样可以采取的不同电压值的数量。例如，电压范围为 4V 的 8 位 ADC 具有 15.6 mV 或 0.39% 的分辨率。结合采样率，更多的 ADC 分辨率位数会产生对模拟信号更准确的数字表示。

公布的每秒采样数取决于 USB 吞吐量、CPU 和

