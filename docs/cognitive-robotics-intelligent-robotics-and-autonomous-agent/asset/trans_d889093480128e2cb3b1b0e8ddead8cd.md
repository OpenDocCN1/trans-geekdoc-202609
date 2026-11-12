
环境包括 Gazebo、CoppeliaSim（原名 V-REP）、Webots 和 SIGVerse。这些环境还支持以自定义插件系统的形式加载针对特定实验的代码，或提供通过中间件接口或 API（例如 ROS/ROS2 或 YARP）公开模拟机器人功能的支持。（由于机器人中间件（如 ROS）的深入讨论超出了本章范围，我们将读者引向 Kortenkamp, Simmons 和 Brugali [2016] 以及 Magyar, Kriszán 和 Sincák [2015]。）

对于物理引擎和模拟环境，有必要区分两种不同的用例。在第一种用例中，用户手动启动模拟，就像启动真实机器人一样，随后其执行以实时继续。在第二种用例中，用户自动同时运行多个模拟，或长时间运行多个模拟——例如，用于训练学习算法。这些用例回应了用户的不同需求，一个环境可以针对其中一种用例进行优化，以提供更多便利。

另一个重要方面是模拟器公开的用于控制机器人的 API。在某些情况下，API 的设计旨在复制真实机器人的接口。这样避免了在从模拟器切换到真实机器人时重写控制软件的需要（从而证明它是真实机器人的数字孪生体）。例如，iCub 人形机器人模拟器（Tikhanoff et al. 2008; Hoffman et al. 2014）采用了这种方法。

图 7.3 展示了从直接使用物理引擎库功能构建的模拟器，到能够采用光线追踪渲染再现逼真场景的成熟模拟环境等模拟器示例。在下一节中，我们将讨论在调查中发现的一些物理引擎和模拟环境，以及一些我们认为基于 2020 年初机器人领域的当前趋势而重要的环境。

## 7.4.2 可用模拟器

机器人社区广泛使用的常见开源物理引擎包括 Open Dynamic Engine（ODE；Smith 2020）、Bullet（2020）和 DART（2020）。除 DART 外，这些工具最初是为计算机游戏开发的，随后改编为可与机器人协同工作。如今，这两个领域几乎已经融合，同时提供准确的物理模拟和光线追踪渲染。机器人学习社区广泛使用的一种流行闭源物理引擎是 MuJoCo（Roboti LLC 2020）。出于性能原因，物理引擎使用 C 和 C++ 等低级语言开发，尽管它们通常提供与 Python 等其他语言的绑定。绝大多数开源和商业模拟环境都与上述至少一个物理引擎进行接口。

构建机器人模拟器的最初尝试直接依赖于物理引擎库提供的功能。在这方面的一个著名示例是 iCub ODE 模拟器（Tikhanoff et al. 2008），它使用 ODE API 构建了 iCub 机器人的完整模拟，包括所有关节、头部的惯性传感器、摄像头和面部表情。iCub ODE 模拟器还为位置、速度和扭矩控制提供软件接口。它还允许加载物理对象，可以直接从配置文件或使用 YARP 中间件的其他软件模块加载。iCub ODE 模拟器已用于传感器运动学习实验（Tommasino

![](img/3dbcfad67b8516752e436bc9e574de5a_144_0.png)

图 7.3 模拟器示例：（a）iCub ODE 模拟器；（b）使用 Gazebo 进行模拟的示例；（c）Isaac Sim。来源：Tikhanoff et al. 2008；（Hoffman et al. 2014；NVIDIA Corporation 2020）。这些示例展示了模拟环境的演变过程，从使用物理引擎库功能编程的自定义模拟器，到允许从描述文件和物体 3D 模型加载复杂场景、具有高保真渲染的成熟环境。

et al. 2019）、工具可负担性（Mar, Tikhanoff, and Natale 2017）、面对面交互期间情感状态的估计（Boccignone et al. 2018）、语言发展计算模型的研究（Štěpánová et al. 2018）、认知技能的协调（Hwang and Tani 2018）以及利他行为（Baraglia, Nagai, and Asada 2016）。

此类模拟器的主要局限性是可维护性。机器人的变更需要通过修改模拟代码来传播；因此，支持多个机器人或让用户有选项向模拟环境添加新机器人或对象变得困难。使用模拟环境的其他好处，除了改善用户体验之外，还包括用自定义功能扩展模拟的可能性，以及能够直接从图形界面与模拟身体交互的机会。特别是在认知机器人研究中，交互至关重要。出于这些原因，近年来，社区已转向采用模拟环境。

最完整且持久的模拟环境之一是 Gazebo（Koenig and Howard 2004），目前由开源机器人基金会（2014）开发，并作为开源软件分发。Gazebo 的开发者还提出了 SDF（Open Source Robotics Foundation 2019），这是一种 XML 格式，用于描述机器人模型、对象以及机器人部署的环境。随着时间的推移，SDF 扩展到描述表征机器人的所有方面，包括静态对象和动态对象、地形以及照明。Gazebo 支持通常安装在机器人上的所有常见传感器，并允许开发软件插件以扩展其功能。它还支持多种物理引擎，例如 ODE、Bullet、Simbody 和 DART。Gazebo 最初是为 Linux 开发的，最近也扩展了对 Windows 的支持。Gazebo 的主要优势在于其成熟度和庞大的社区：Gazebo 在 DARPA 机器人挑战赛（Defense Advanced Research Projects Agency 2013）期间被广泛用于模拟 ATLAS 人形机器人，目前它是 iCub 机器人全身控制和运动实验的首选模拟器（Hoffman et al. 2014）。它还已集成到人脑计划（Human Brain Project 2018）的神经机器人平台中，用于在模拟的闭环系统中研究大脑模型（例如，参见 Chen et al. 2019）。其他示例包括用于 HRI 研究的移动平台模拟（Truong and Ngo 2017）以及模拟婴儿状人形机器人以探索学习伸手任务的发展性方法（Luo et al. 2018）。

CoppeliaSim（Rohmer, Singh, and Freese 2013），原名 V-REP，是一个与 Gazebo 类似的框架，支持多种物理引擎，包括 Bullet 和 ODE。它是跨平台的，面向 macOS、Linux 和 Windows 分发。它可以免费使用，但仅限于其教育版。

在我们的调查中，我们发现 CoppeliaSim-V-REP 被用于模拟自定义机器人系统，以研究家庭任务（清理桌子；Cruz et al. 2016）的强化学习、多机器人移动架构（Rossi, Staffa, and Rossi 2016），以及 HRI 环境中的 Kuka omnibot（Caccavale and Finzi 2017）。

Webots（Cyberbotics Ltd. 2020）是另一个模拟环境，由瑞士联邦工学院（EPFL）于 1998 年开发，并成为 EPFL 衍生公司 Cyberbotics（Olivier 2004）的商业产品。它最初作为闭源应用程序分发，很可能正因如此，其采用受到了影响，尤其是当 Gazebo 等开源替代方案获得流行时。随着 R2019a 的发布，Webots 现在采用开源许可证分发。Webots 基于 ODE；它提供一个图形界面，简化了环境的设计，并从一组传感器和执行器实现机器人系统的快速原型设计。它是跨平台的，运行在 Windows、Linux 和 macOS 上。在 Pierris and Dahl（2017）中，Webots 被用于模拟一种蝾螈状机器人，以研究一种通过扩展通过示范学习的现有技能来推导新技能的架构。

Choregraphe（Pot et al. 2009）是 Aldebaran 机器人（包括 NAO 和 Pepper）的内置编程应用程序。它允许机器人程序员创建动画、行为和对话。除了这些编程功能之外，它还允许用户在模拟机器人上测试编程的行为，因此，使用 Aldebaran 机器人的研究人员经常使用它。

MATLAB 环境还提供了一个用于机器人控制和模拟的工具箱，称为 MATLAB Robotics System Toolbox（MathWorks 2020），其中包括与 Simulink 和 Simscape Mechanics 集成的仿真工具。此外，MATLAB
