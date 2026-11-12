

![](img/3dbcfad67b8516752e436bc9e574de5a_81_0.png)

图 4.3  
模拟设置（左）源自 von Hofsten（1982）对婴儿（中间和右侧）进行的实验。

婴儿的伸展和抓握行为（图 4.3，中间和右侧）。机器人的训练分为三个阶段实现：1) 前伸展阶段，此时机器人具有简单的预设反射行为、低视觉敏锐度和不成熟的神经系统；2) 粗伸展阶段，此时机器人具有改进的视觉敏锐度和成熟的皮层区域；以及 3) 精细伸展阶段，此时机器人可以获取编码物体相对于手的相对位置的感知信息。

实验分析表明，前伸展阶段内部神经资源的缺乏具有适应性作用（即，将粗伸展阶段的发育过程引向更好的解决方案）和偏差作用（即，代表了探索性运动咿呀学语行为出现的必要条件）。这表明，皮层区域（Martin 2005）在人类中的后期介入可以发挥适应性作用，并且可能为了实现此功能而进化。此外，对训练过程中机器人行为的分析表明，婴儿中观察到的以下现象是自发产生的：1) 前伸展阶段机器人手臂远端自由度（DOFs）的使用减少（冻结）；2) 前伸展阶段的探索性（运动咿呀学语）行为；以及 3) 精细伸展阶段开始时伸展能力的时间性退行。这些质的变化自发出现的事实表明，它们不一定反映其他特定成熟约束的存在。它们可以是通过暂时降低运动空间、感觉空间和相关任务空间的复杂性来运作的一般自结构过程的表现。

与强化学习算法（Sutton and Barto 2018）形成对比，后者是建模试错学习最常见的选择，进化算法则具有优点和缺点。优点包括能够调整机器人的所有特性，包括机器人的形态和神经网络架构，以及在稀疏奖励存在下良好运行的能力。另一方面，强化学习算法通常样本效率更高。

开发新的进化算法，这些算法通过估计局部梯度（Hansen and Ostermeier 2001）并最终依赖随机梯度优化器来变化自适应参数（Salimans et al. 2017），使得使用进化方法更具吸引力。确实，尽管这些梯度上升方法也可以用于包含多个父代的种群，但通常用于由单个父代产生多个后代的种群。后代的评估用于估计局部梯度，进而用于变化父代的参数。这意味着，如同发生学习中一样，适应过程是通过变化单个个体的参数来实现的。

Salimans et al.（2017）表明，现代进化方法是一种可扩展的替代方案，可替代最先进的强化学习算法（Schulman et al. 2015, 2017）。确实，它们可以用于调整具有数百万个参数的神经网络控制器，并实现与强化学习方法相媲美的结果。结果已在最先进的基准问题上收集：Mujoco 控制问题（需要控制铰接式机器人，Todorov, Erez, and Tassa 2012）和 Atari 游戏（需要控制接收控制台图像作为输入的游戏玩家，Bellemare et al. 2013）。

## 4.9 结论

进化机器人学不仅是一种受生物学启发的自动机器人开发方法，也是研究自然系统中开放问题的工具，例如，认知中具身化的作用、符号通信的起源、行为与认知能力之间的关系，以及支持合作行为发展的机制。

尽管主流学科代表甚至该方法的先驱（Matarić and Cliff 1996）最初持怀疑态度，但多年来，来自广泛学科的越来越多研究人员采用了该方法。该方法的丰富性和富有成效性，加上最近方法论进步所带来的新机遇，表明它将在未来继续发挥重要作用。

有兴趣获取进化机器人学实践知识的读者可以访问免费可用的工具，这些工具允许复制标准实验和设计新实验（参见 Auerbach et al. 2014; Massera et al. 2014; Nolfi 2021；另见 https://github.com/snolfi/evorobotpy）。

## 进一步阅读与资源

- 该领域的最新综述：Nolfi, S., J. Bongard, P. Husbands, 和 D. Floreano. 2016. “进化机器人学。”收录于 *Springer 机器人手册*，Bruno Siciliano 和 Oussama Khatib 编，第 1423–1541 页。第 2 版。柏林：Springer Verlag。

- 一篇更详细地说明具身代理中行为与认知的复杂自适应系统性质的文章：Nolfi, S. 2009. “行为与认知作为复杂自适应系统：来自机器人实验的见解。”收录于 *科学哲学手册. 第 10 卷: 复杂系统哲学*，C. Hooker 编。总编辑：Dov M. Gabbay、Paul Thagard 和 John Woods。圣地亚哥：Elsevier。

- 该领域的更详细综述：Nolfi, S., 和 D. Floreano, *进化机器人学：自组织机器的生物学、智能与技术*. Cambridge, MA: MIT Press, 2000。

- Evorobotpy（Nolfi 2021; https://github.com/snolfi/evorobotpy2）是一种简单且文档齐全的工具，可用于执行进化机器人学实验。相关文档（Nolfi 2021, 第 13 章）包括教程和练习。

- Farsa（Massera et al. 2014; https://sourceforge.net/projects/farsa/）是另一种可用于进行进化机器人学实验的软件工具。

## 参考文献

André, Jean-Baptiste, 和 Stefano Nolfi. 2016. “进化机器人学模拟有助于解释为什么互惠在自然界中很稀有。” Scientific Reports 6:32785。

Arbib, Michael A. 1989. 《隐喻大脑：第 2 卷，神经网络及其后》. New York: Wiley。

Auerbach, Joshua, Denis Aydin, Andrea Maesani, Przemyslaw Kornatowski, Titus Cieslewski, Grégoire Heitz, Pradeep Fernando, Ilya Loshchilov, Ludovic Daler, 和 Dario Floreano. 2014. “RoboGen: 通过人工进化进行机器人生成。”收录于《第十四届生命系统合成与模拟国际会议论文集》，H. Sayama, J. Reiffel, S. Risi, R. Doursat, 和 H. Lipson 编。New York: MIT Press。

Auerbach, Joshua E., 和 Joshua C. Bongard. 2012. “关于进化机器人中环境与形态复杂性之间关系的研究。”收录于《第 14 届遗传与进化计算国际会议论文集》，第 521–528 页。ACM Press。

Axelrod, Robert, 和 William Donald Hamilton. 1981. “合作的进化。” Science 211:1390–1396。

Baldassarre, Gianluca, Vito Trianni, Michael Bonani, Francesca Mondada, Marco Dorigo, 和 Stefano Nolfi. 2007. “物理连接机器人群组中的自组织协调运动。” IEEE 系统、人与控制论汇刊 37 (1): 224–239。

Bellemare, Marc G., Yavar Naddaf, Joel Veness, 和 Michael Bowling. 2013. “街机学习环境：通用代理的评估平台。” 人工智能研究杂志 47:253–279。

Bernstein, Nikolai. 1967. 《动作的协调与调节》. Oxford: Pergamon Press。

Berthoz, Alain. 2000. 《大脑的运动感觉》. Cambridge, MA: Harvard University Press。

Bongard, Joshua C. 2011. “机器中的形态变化加速了稳健行为的进化。” 美国国家科学院院刊 108:1234–1239。

Bongard, Josh, Victor Zykov, 和 Hod Lipson. 2006. “通过持续自我建模实现的有弹性机器。” Science 314 (5802): 1118–1121。

Brockman, Greg, Vicki Cheung, Ludwig Pettersson, Jonas Schneider, John Schulman, Jie Tang, 和 Wojciech Zaremba. 2016. “OpenAI Gym.” ArXiv: 1606.01540。

Brunyé, Tad T., Aaron L. Gardony, Amanda Holmes, 和 Holly A. Taylor. 2018. “导航过程中的空间决策动态：交叉口提示决策过程。” 认知研究：原则与意义 8:13。

Camazine, Scott, Jean-Louis Deneubourg, Nigel R. Franks, James Sneyd, Eric Bonabeau, 和 Guy Theraulaz. 2001. 《生物系统中的自组织》. Princeton, NJ: Princeton University Press。

Cangelosi, Angelo, 和 Domenico Parisi. 2002. 《语言进化模拟》. Berlin: Springer Verlag。

Carvalho, João Tyska, 和 Stefano Nolfi. 2016. “认知卸载不仅不会阻碍，反而促进认知发展。” PLoS One 11 (8): e0160679。

Chestnutt, Joel, Manfred Lau, German Cheung, James Kuffner, Jessica Hodgins, 和 Takeo Kanade. 2005. “Honda ASIMO 人形机器人的脚步规划。”收录于《IEEE 机器人与自动化国际会议论文集》。New York: IEEE。

Chiel, Hillel J., 和 Randall D. Beer. 1997. “大脑拥有身体：适应性行为源于神经系统、身体与环境的相互作用。” 神经科学动态 20:553–557。

Clark, Andy. 1998. 《身临其境：重新整合大脑、身体与世界》. Cambridge, MA: MIT Press。

Clark, Andy. 1999. “一种具身认知科学？” 认知科学动态 3:345–351。

Cliff, Dave, 和 Geoffrey F. Miller. 1995. “追踪红皇后：共进化模拟中适应性进度的测量。”收录于《人工生命进展：第三届欧洲人工生命会议论文集》，F. Moran, A. Moreno, J. J. Merelo, 和 P. Chacon 编。Berlin: Springer Verlag。

Collins, Steve, Andy Ruina, Russ Tedrake, 和 Martijn Wisse. 2005. “基于被动动态步行器的高效双足机器人。” Science 307 (5712): 1082–1085。

