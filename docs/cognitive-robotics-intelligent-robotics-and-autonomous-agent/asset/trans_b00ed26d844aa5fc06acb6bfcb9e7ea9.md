

大多数机器人平台都是原型机，可靠性有限。在仿真中开发软件可以在不担心损坏机器人或环境的情况下测试研究算法。最近，深度学习研究表明，可以使用在仿真中生成的数据来训练算法，并在现实世界中部署，取得令人印象深刻的结果。这已被证明在感知方面效果良好，通过数据增强和逼真渲染相结合来解决六维物体姿态估计问题（Tremblay et al. 2018），在强化学习方面，则可以解决使用灵巧手进行手中物体操作问题（Andrychowicz et al. 2020）。这项研究推动了仿真工具的发展，这些工具能够以很高的准确性复现物理环境，包括精巧的逼真效果。

过去曾有专门为认知机器人研究量身定制平台的努力。一个著名的例子是 iCub，这是一款专门针对认知机器人社区开发的人形机器人。其他平台并非怀着这一目标设计，但由于广泛采用而成为事实标准（例如，Aibo、NAO 和 Pepper，已在前文提及，还有来自 Rethink Robotics 的 Baxter [Fitzgerald 2013] 和来自 Franka Emika GmbH 的 Panda [2020]）。本章的目标是识别和描述社区最常用的机器人平台和仿真工具，重点介绍它们在支持研究活动方面的优缺点。

## 7.2 方法论

在撰写本章时，我们试图了解认知机器人社区中使用哪些平台。我们通过查看认知机器人领域的两大主要科学期刊进行了详细研究：IEEE 认知发展系统汇刊（TCDS）和 Springer 社会机器人国际期刊（IJSR）。我们检查了2016–2019年期间在这些期刊上发表的所有论文，记录了每篇论文所采用的机器人平台和软件仿真器（如果有）。这项文献调查的目标是识别社区内使用的平台和软件仿真器。值得注意的是，我们决定专注于期刊，而不是包括会议在内的更广泛的场所，因为这使我们能够检查更长时间跨度的出版物，并接触到更成熟的工作。

结果在表 7.1 中针对硬件平台进行了总结，表 7.2 针对仿真器进行了总结。在表 7.1 中，我们报告了每个平台在考虑期间在 TCDS 或 IJSR 中发表论文的次数。由于无法列出所有机器人平台，我们将所有在少数论文中发现的平台（不超过两次）归类为“其他”。

总共我们分析了337篇论文，其中找到了62个不同的硬件平台和13个软件框架的引用。第一个观察结果是社区的高度分散：除少数例外外，大多数机器人平台只出现一次。这表明其他团队不使用这些平台，并且该领域的大多数研究都是使用仅在特定研究组内部使用的定制原型机进行的。然而，这项调查也使我们能够明确识别出社区内使用的一些平台：NAO 机器人使用最频繁（47篇论文），其次是 iCub（16篇）、Pepper 和 Robovie（7篇）、Pioneer 3-Dx/3-AT（6篇）、Baxter（5篇），

**表 7.1 文献调查：硬件平台结果**

| | TCDS 2019 | TCDS 2018 | TCDS 2017 | TCDS 2016 | IJSR 2019 | IJSR 2018 | IJSR 2017 | IJSR 2016 | 总计 |
|---|---|---|---|---|---|---|---|---|---|
| 其他 | 10 | 9 | 3 | 4 | | 10 | 16 | 10 | 62 |
| NAO | 3 | 5 | 3 | 2 | 4 | 14 | 9 | 7 | 47 |
| iCub | | 6 | 2 | 6 | | | 2 | | 16 |
| Pepper | 1 | | | | 3 | | 3 | | 7 |
| Robovie 系列 | | | | | | 3 | 2 | 2 | 7 |
| Pioneer 3-Dx/3-AT | 2 | 1 | 2 | | | 1 | | | 6 |
| Baxter | 1 | 2 | | 1 | | | 1 | | 5 |
| Kuka LBR iiwa | | | | 1 | 1 | | 1 | | 3 |

注：我们报告了 TCDS 和 IJSR 中每年每个平台发表的论文数量。最后一列报告了所有年份的总和。我们只列出在超过两篇论文中发现的平台。总共我们发现了67个不同的平台。

**表 7.2 文献调查：仿真框架**

| 仿真器 | 机器人平台 | 支持语言 | 操作系统 | 参考文献 |
|---|---|---|---|---|
| ODE | iCub (5), HOAP-2 (1) | C/C++ | macOS, Linux, Windows | (Smith 2020) |
| Gazebo | NeuroSnake (1), Eddie (1), PKU-HR6 (1) | C++ | macOS, Linux, Windows | (Open Software Robotics Foundation 2014) |
| V-REP | NAO (1), Pioneer (2), Exapod (1) | LUA, C/C++, Python, Java, MATLAB/Octave | macOS, Linux, Windows | (Coppelia Robotics GmbH 2020) |
| Webots | NAO (1), Salamander (1) | C/C++, Python, Java, MATLAB | macOS, Linux, Windows | (Cyberbotics Ltd. 2020) |
| Nextage Blender | Kawada (1) Custom (1) | Python | macOS, Linux, Windows | (Blender Foundation 2020) |
| OpenSim | JacoArm (1) | C++, Python, MATLAB, Java | macOS, Linux (仅 API), Windows | (OpenSim 2020) |
| RobWorkSim | UR3 (1) | C++, Python, Java, LUA | macOS, Linux, Windows | (SDU Robotics 2020) |
| SMILE | Baxter (1) | Java | macOS, Linux, Windows | (SMILE 2020) |
| Stage | iRat (1) | C++ | macOS, Linux | (Stage 2020) |
| FARSA | iCub (1) | C++ | macOS, Linux, Windows | (Farsa Sourceforge 2020) |
| SIGVerse | TurtleBot (1) | C# (Unity) | Windows | (SIGVerse 2020) |
| 3D Studio | Probo (1) | macOS, Linux, Windows | Windows | (Autodesk Inc. 2020) |

注：对于每个仿真框架，我们报告所模拟的机器人名称及其在我们分析的论文中出现的次数。我们还添加了有关支持编程语言和操作系统的一般信息，并提供托管仿真器代码的网页链接。

以及 Kuka LBR iiwa（3次）。这些平台将在本章下一部分中详细介绍。

我们还观察到，令人惊讶的是，社区中并不经常使用软件仿真器，社区大体上更喜欢使用真实机器人进行实验。我们认为这是因为仿真器在认知机器人研究方面仍然相当不成熟，因为它们不能很好地模拟复杂环境，尤其是在与人类交互很重要时。另一种可能性是，最近软件仿真的进展主要由机器人学习社区推动，该社区专注于感知和抓取，并在不同场所（例如，机器人学习国际会议）发表论文。发现使用最频繁的软件框架有：Open Dynamic Engine (ODE；4次)、Gazebo（3次）和 V-REP（4次）。然而，这种观点并不能很好地代表机器人社区对仿真框架开发所赋予的日益增长的重要性。这一情况将会改变，因为在未来几年可能会提供更好的仿真环境，对认知机器人社区产生相应影响。出于这些原因，在 7.4 节中，我们概述了软件仿真器在机器人领域中的使用情况，描述了社区中使用的不同类型的仿真器，以及由不断发展的机器学习领域推动的当前研究趋势。

## 7.3 机器人平台

在本节中，我们根据调查回顾了认知机器人社区中最常用的平台。作为总结，每个平台的详细信息也报告在表 7.3 中。

iCub 是一款在 RobotCub 项目背景下开发的开源人形机器人（图 7.1a）。iCub 拥有 53 个自由度（DOF），并配备了丰富的传感器套件（立体摄像头、麦克风、六轴力矩传感器和全身触觉传感器）。iCub 机器人的成本约为 250,000 欧元。它使用 YARP 中间件和自定义运动控制库进行控制（有关 iCub 软件架构的更多细节请参阅 Natale et al. [2016]）。这些元素允许规划和控制涉及物理交互的复杂 HRI 任务。尽管 iCub 具有板载计算和电池，但它通常从固定基座操作，不允许自主导航。iCub 是一个多功能平台，用于研究机器人学的各个方面，包括传感器运动学习（Hoffmann et al. 2018; Zambelli and Demiris 2017; Giagkos et al. 2017; Çelikkanat et al. 2016）、对象学习和工具使用（Ribes et al. 2016; Mar, Tikhanoff, and Natale 2017）、内在动机和强化学习（Meola et al. 2016; Santucci, Baldassarre, and Mirolli 2016）、HRI（Förster, Saunders, and Nehaniv 2018; Baraglia, Nagai, and Asada 2016; Petit, Fischer, and Demiris 2016）、社会机器人学（Anzalone et al. 2017; Ivaldi et al. 2017）以及人工认知架构（Moulin-Frier et al. 2018）。

Pepper 机器人最初由 Aldebaran 公司开发，后被 Softbank Robotics 收购（图 7.1c）。Pepper 机器人拥有 17 个自由度，并配备了全向轮，用于在室内环境中导航。Pepper 机器人专门为社交、非物理 HRI 任务开发；其

