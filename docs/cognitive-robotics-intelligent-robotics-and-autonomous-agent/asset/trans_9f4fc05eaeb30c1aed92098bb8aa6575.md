

当没有可抓取的对象时，才会执行该动作，这由抓取检测算法决定。

## 16.6 结论

带有臂操纵器的机器人正从工厂车间转向人们日常生活领域，例如家庭服务和医疗护理。实现这些目标的一种可能方案是，使机器人能够从人类行为中学习操纵技能。本章研究了多种在各种传感器数据中将人类适应技能转移到机器人的有效方法——例如，脑电图（EEG）、身体运动信号、视觉信号等生理信号。提出了 PbD 方法，通过模仿人类导师来提高机器人学习人类运动技能的效率。我们将 DMP 与 GMM 相结合，使机器人能够从运动传感器捕获的一组示范中学习，以提供友好的人机交互。此外，我们介绍了深度学习在机器人操纵方面应用的一些最新进展。未来工作包括以更智能的方式教导机器人，使机器人能够使用位置、刚度和力信息从人类那里学习更灵巧的技能。

## 致谢

我们谨感谢郭锟林、刘阳和朱成之在本章撰写期间作出的巨大贡献。

## 进一步阅读与资源

- *介绍机器人操纵基本理论和数学基础的经典著作*：Murray, R. M., Z. Li, and S. S. Sastry. 1994. *机器人操纵数学导论*. Boca Raton: CRC Press.

- *机器人学系统手册，含机器人操纵专题章节*：Siciliano, Bruno, and Oussama Khatib, eds. 2016. *机器人学施普林格手册*. Berlin: Springer.

- *介绍机器人操纵先进技术的近期全面著作，含生物启发式机器人操纵和视觉伺服控制专题章节*：Yang, C., H. Ma, and M. Fu. 2016. *现代机器人应用先进技术*. Singapore: Springer.

- 生理信号增强操纵: https://www.youtube.com/watch?v=rvHluEVSyZw.

- 基于 sEMG 的人机技能转移: https://www.youtube.com/watch?v=CCKy88QTkGY.

## 参考文献

- Asada, Haruhiko, and J.-J. E. Slotine. 1986. *机器人分析与控制*. Hoboken, NJ: John Wiley and Sons.

- Atkeson, Christopher G., Andrew W. Moore, and Stefan Schaal. 1997. "面向控制的局部加权学习". *人工智能评论* 11:75–113.

- Berscheid, Lars, Pascal Meißner, and Torsten Kröger. 2019. "杂乱环境中移动物体以供抓取的机器人学习". ArXiv 预印本: 1907.11035.

- Billard, Aude, Sylvain Calinon, Ruediger Dillmann, and Stefan Schaal. 2008. "通过演示进行机器人编程". In 机器人学施普林格手册, edited by Bruno Siciliano and Oussama Khatib, 1371–1394. Berlin: Springer.

- Billard, Aude, and Danica Kragic. 2019. "机器人操纵的趋势与挑战". Science 364 (6446): eaat8414.

- Calinon, Sylvain. 2018. "基于任务参数化生成模型的机器人学习". In 机器人研究, 111–126. Cham, Switzerland: Springer.

- Calinon, Sylvain, Florent Guenter, and Aude Billard. 2007. "关于人形机器人中任务的学习、表示与泛化". IEEE 系统、人与控制论汇刊，部分 B（控制论） 37 (2): 286–298.

- Calinon, Sylvain, Zhibin Li, Tohid Alizadeh, Nikos G. Tsagarakis, and Darwin G. Caldwell. 2012. "人形技能获取的统计动态系统". In 2012 第 12 届 IEEE-RAS 人形机器人国际会议, 323–329. New York: IEEE.

- Chen, Yiwen, Chenguang Yang, and Ying Feng. 2020. "基于变分自编码器的机器人强化学习". In 第 11 届建模、识别与控制国际会议论文集, 675–684. Springer, Singapore.

- Chu, Fu-Jen, and Patricio A. Vela. 2018. "深度抓取：使用深度神经网络进行抓取检测与定位". ArXiv 预印本: 1802.00520.

- Chu, Fu-Jen, Ruinian Xu, and Patricio A. Vela. 2018. "现实世界多目标多抓取检测". IEEE 机器人与自动化期刊 3 (4): 3355–3362.

- Chu, Jun-Uk, Inhyuk Moon, and Mu-Seong Mun. 2006. "基于线性-非线性特征投影的多功能义肢手实时肌电图模式识别系统". IEEE 生物医学工程汇刊 53 (11): 2232–2239.

- Collura, Thomas F. 1993. "脑电图仪器与技术的历史与演变". 临床神经生理学杂志 10 (4): 476–504.

- Dautenhahn, Kerstin, and Chrystopher L. Nehaniv. 2002. "基于代理的模仿视角". In 动物与人工制品中的模仿, 1–40. Cambridge, MA: MIT Press.

- Dempster, Arthur P., Nan M. Laird, and Donald B. Rubin. 1977. "通过 EM 算法从不完全数据中获得最大似然". 皇家统计学会杂志：B 系列（方法论） 39 (1): 1–22.

- Folgieri, Raffaella, and Roberto Zampolini. 2015. "音乐与游戏中情感参与的 BCI 前景". 娱乐计算机 12 (1): 1–10.

- Fujimoto, Scott, Herke van Hoof, and David Meger. 2018. "解决 Actor-Critic 方法中的函数逼近误差". ArXiv 预印本: 1802.09477.

- Geng, Tao, John Q. Gan, and Huosheng Hu. 2010. "用于移动机器人控制的自主节奏在线脑机接口". 先进机电系统国际期刊 2 (1–2): 28–35.

- Guler, Inan, and Elif Derya Ubeyli. 2007. "EEG 信号分类的多类支持向量机". IEEE 生物医学信息技术汇刊 11 (2): 117–126.

- Hermens, Hermie J., Bart Freriks, Catherine Disselhorst-Klug, and Günter Rau. 2000. "SEMG 传感器及传感器放置程序建议的制定". 肌电图与运动学杂志 10 (5): 361–374.

- Hu, Jianbing, Zining Yang, Zhiyang Wang, Xinyu Wu, and Yongsheng Ou. 2015. "基于极端学习机的稳定动态系统神经学习". In 2015 IEEE 信息与自动化国际会议, 306–311. New York: IEEE.

- Jang, Eric, Coline Devin, Vincent Vanhoucke, and Sergey Levine. 2018. "Grasp2vec：从自监督抓取中学习物体表示". ArXiv 预印本: 1811.06964.

- Jiang, Yiming, Yang Chenguang, Na Jing, Li Guang, Li Yanan, and Zhong Junpei. 2017. "基于神经网络的学习与控制及其在机器人中的应用简要综述". 复杂性 2017:1895897.

- Kalashnikov, Dmitry, Alex Irpan, Peter Pastor, Julian Ibarz, Alexander Herzog, Eric Jang, Deirdre Quillen, et al. 2018. "Qt-Opt：面向视觉机器人操纵的可扩展深度强化学习". ArXiv 预印本: 1806.10293.

- Khansari-Zadeh, S. Mohammad, and Aude Billard. 2011. "使用高斯混合模型学习稳定非线性动态系统". IEEE 机器人汇刊 27 (5): 943–957.

- Khezri, Mahdi, and Mehran Jahed. 2007. "表面肌电图信号实时智能模式识别算法". 生物医学工程在线 6 (1): 1–12.

- Kosmyna, Nataliya, Franck Tarpin-Bernard, Nicolas Bonnefond, and Bertrand Rivet. 2016. "现实智能家居环境中 BCI 控制的可行性". 人类神经科学前沿 10:416.

- Kumar, Sulabh, and Christopher Kanan. 2017. "使用深度卷积神经网络的机器人抓取检测". In 2017 IEEE/RSJ 智能机器人与系统国际会议论文集, 769–776. New York: IEEE.

- Lee, Michelle A., Yuke Zhu, Krishnan Srinivasan, Parth Shah, Silvio Savarese, Li Fei-Fei, Animesh Garg, and Jeannette Bohg. 2019. "理解视觉与触觉：面向丰富接触任务的多模态表示自监督学习". In 2019 机器人与自动化国际会议, 8943–8950. New York: IEEE.

- Levine, Sergey, Peter Pastor, Alex Krizhevsky, Julian Ibarz, and Deirdre Quillen. 2018. "使用深度学习和大规模数据采集学习机器人抓取的手眼协调". 机器人学研究国际期刊 37 (4–5): 421–436.

- Liang, Hengyue, Xibai Lou, and Changhyun Choi. 2019. "用于滑向墙壁物体抓取的知识诱导深度 Q 网络". ArXiv 预印本: 1910.03781.

- Lillicrap, Timothy P., Jonathan J. Hunt, Alexander Pritzel, Nicolas Heess, Tom Erez, Yuval Tassa, David Silver, and Daan Wierstra. 2015. "使用深度强化学习进行连续控制". ArXiv 预印本: 1509.02971.

- MacQueen, James. 1967. "多元观测分类与分析的若干方法". 第五届伯克利数理统计与概率研讨会论文集 1 (14): 281–297.

- Matas, Jan, Stephen James, and Andrew J. Davison. 2018. "可变形物体操纵的仿真到现实强化学习". ArXiv 预印本: 1806.07851.

- Mnih, Volodymyr, Koray Kavukcuoglu, David Silver, Andrei A. Rusu, Joel Veness, Marc G. Bellemare, Alex Graves, et al. 2015. "通过深度强化学习实现人类水平控制". 自然 518 (7540): 529–533.

- Morrison, Douglas, Peter Corke, and Jürgen Leitner. 2018. "机器人抓取闭环：一种实时生成性抓取合成方法". ArXiv 预印本: 1804.05172.

- Müller-Putz, Gernot R., Reinhold Scherer, Christian Braunneis, and Gert Pfurtscheller. 2005. "基于稳态视觉诱发电位 (SSVEP) 的通信：谐波频率分量的影响". 神经工程杂志 2 (2): 123.

- Mülling, Katharina, Jens Kober, Oliver Kroemer, and Jan Peters. 2013. "在机器人乒乓球中学习选择和泛化击球动作". 机器人学研究国际期刊 32 (3): 263–279.

- Murray, Richard M., Zexiang Li, and S. Shankar Sastry. 1994. 机器人操纵数学导论. Boca Raton: CRC Press.

- Nair, Ashvin V., Vitchyr Pong, Murtaza Dalal, Shikhar Bahl, Steven Lin, and Sergey Levine. 2018. "带有想象目标的视觉强化学习". 神经信息处理系统进展 31 (2018): 9191–9200.

- Osu, Rieko, David W. Franklin, Hiroko Kato, Hiroaki Gomi, Kazuhisa Domen, Toshinori Yoshioka, and Mitsuo Kawato. 2002. "运动学习相关的关节共收缩的短期与长期变化：基于表面肌电图的揭示". 神经生理学杂志 88 (2): 991–1004.

- Peng, Guangzhu, Chenguang Yang, Yiming Jiang, Long Cheng, and Peidong Liang. 2016. "基于人体运动捕捉的 Baxter 机器人遥操作控制". In 2016 IEEE 信息与自动化国际会议, 1026–1031. New York: IEEE.

- Quillen, Deirdre, Eric Jang, Ofi Nachum, Chelsea Finn, Julian Ibarz, and Sergey Levine. 2018. "面向视觉机器人抓取的深度强化学习：非策略方法的模拟比较评估". In 2018 IEEE 机器人与自动化国际会议, 6284–6291. New York: IEEE.

- Ray, G. C., and S. K. Guha. 1983. "表面肌电图与肌肉力之间的关系". 医学与生物工程与计算 21 (5): 579–586.

- Rebsamen, Brice, Etienne Burdet, Cuntai Guan, Haihong Zhang, Chee Leong Teo, Qiang Zeng, Christian Laugier, and Marcelo H. Ang. 2007. "使用思想控制室内轮椅". IEEE 智能系统 22 (2): 18–24.

- Redmon, Joseph, and Anelia Angelova. 2015. "使用卷积神经网络进行实时抓取检测". In 2015 IEEE 机器人与自动化国际会议, 1316–1322. New York: IEEE.

- Redmon, Joseph, Santosh Divvala, Ross Girshick, and Ali Farhadi. 2016. "一次看个够：统一的实时目标检测". In IEEE 计算机视觉与模式识别会议论文集, 779–788. New York: IEEE.

- Rozo, Leonel, Pablo Jiménez, and Carme Torras. 2013. "用于执行基于力的操纵任务的基于演示的机器人学习框架". 智能服务机器人学 6 (1): 33–51.

- Schaal, Stefan. 1999. "模仿学习是通往人形机器人的途径吗？". 认知科学趋势 3 (6): 233–242.

