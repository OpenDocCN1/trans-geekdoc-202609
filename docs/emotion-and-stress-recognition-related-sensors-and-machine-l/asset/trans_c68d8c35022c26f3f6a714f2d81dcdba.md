

## 模型损失

![](img/601340ca744b738277eef45ff127492a_434_0.png)

(a) VGG16

## 模型损失

![](img/601340ca744b738277eef45ff127492a_434_1.png)

(b) Xception

## 模型损失

![](img/601340ca744b738277eef45ff127492a_434_2.png)

(c) Inception V3

## 模型损失

![](img/601340ca744b738277eef45ff127492a_434_3.png)

(d) InceptionResNetV2

图 5. 各网络损失函数随轮数（epochs）的演化情况。

## 模型准确率

![](img/601340ca744b738277eef45ff127492a_434_4.png)

(a) VGG16

## 模型准确率

![](img/601340ca744b738277eef45ff127492a_434_5.png)

(b) Xception

## 模型准确率

![](img/601340ca744b738277eef45ff127492a_434_6.png)

(c) Inception V3

## 模型准确率

![](img/601340ca744b738277eef45ff127492a_434_7.png)

(d) InceptionResNetV2

图 6. 各网络准确率函数随轮数（epochs）的演化情况。

## 训练归一化最佳

![](img/601340ca744b738277eef45ff127492a_435_0.png)

图 7. InceptionResNetV2 网络训练集的混淆矩阵。

图 8 显示了相对于每个测试网络的验证集混淆矩阵。

![](img/601340ca744b738277eef45ff127492a_435_1.png)

![](img/601340ca744b738277eef45ff127492a_435_2.png)

(a) VGG16

(b) Xception

![](img/601340ca744b738277eef45ff127492a_435_3.png)

![](img/601340ca744b738277eef45ff127492a_435_4.png)

(c) Inception V3

(d) InceptionResNetV2

图 8 经过归一化处理的训练网络混淆矩阵。

## 表 3. 在共 221 张图像中三个错误类别中中性脸部分类错误的图像数量。

| 图像数量 | 快乐 | 惊讶 | 愤怒 |
| :--- | :--- | :--- | :--- |
| | 11 | 7 | 4 |

实验在全脸图像上进行了重复，以研究嘴部的贡献；生成的混淆矩阵如图 9 所示。结果可以总结为以下几点：

- 性能最佳的网络与基于嘴部的表情识别（ER）网络相同，即 InceptionResNetV2。
- 愤怒是最难分类的情绪。
- 性能提升仅为 5%，准确率为 84.4%，证明了嘴部对表情识别具有持续的贡献。![](img/601340ca744b738277eef45ff127492a_436_0.png)

在这项工作中，我们通过对四种不同的卷积神经网络（CNN）使用迁移学习进行对比分析，展示了基于嘴部的表情识别方法的整合结果。如第 5 节所述，我们获得 InceptionResNetV2 在验证集上的准确率为 79.5%。与全脸相比，结果显示损失仅为 5%，我们认为这种损失被我们方法的优势所抵消。此外，关注较小区域需要更少的计算能力。将我们的方法直接应用于医疗管理和临床患者的自动监督，该系统可以在没有人工帮助的情况下（例如夜间或病房期间）通过表情识别来支持患者。我们的方法可以轻松扩展到之前描述的情景，例如对抑郁状态或自闭症患者的早期识别。

**作者贡献**：作者对本工作贡献相等。所有作者均已阅读并同意发表的版本。

**资助**：本研究部分由意大利研究部的 PRIN 拨款（2017-PRXX））以及数学和计算机科学部门资助。

**致谢**：感谢 Google 提供的 Cloud 基础设施用于计算。感谢丹佛大学为本研究提供的数据库支持。

**利益冲突**：作者声明无冲突。

## 参考文献

1. Gervasi, O.; Franzoni, V.; Riganelli, M.; Tasso, S. 自动表情识别。Web Intell. 2019, 17–27. [CrossRef]
2. Sagonos, C.; Tsimropoulos, G.; Zafeiriou, S.; Pantic, M. 半自动地标标注方法。2013 IEEE 计算机视觉与模式识别会议论文集，Portland, OR, 6月23–28日，886–993。
3. Kazeni, V.; Sullivan, J. 基于回归树的面部匹配。2014 IEEE 计算机视觉与模式识别会议论文集，Columbus, OH, 6月23–28日，1867–1874。
4. Riganelli, M.; Franzoni, V.; Gervasi, O.; Tasso, S. 使用卷积神经网络的脸部识别工具。计算机科学与应用国际会议论文集，苏黎世，瑞士, 7月3–6日，第1047卷，692–704。
5. Bindi, G.; Franzoni, V.; Gervasi, O.; Perri, D. 改进表情识别的方法。计算机科学与应用国际会议论文集，圣彼得堡，俄罗斯，2019年7月11–14日，1169卷，649–664。
6. Gervasi, O.; Maggi, R.; Frei, M. 通过解释动作预测单词的方法。计算机科学与应用国际会议论文集，北京，2016年7月7日，第9787卷，450–463。
7. Deng, J.; Wang, S.; Reich, R.; Li, K. ImageNet：大规模分层数据库。2009 IEEE 计算机视觉与模式识别会议论文集，Miami, FL, 6月25–29日，248–255。
8. Sagonos, C.; Tsimropoulos, G.; Zafeiriou, S.; Pantic, M. Faces-The-Wild：数据集与结果。Image Vis. 2016, 67, 1.
9. Ekman, P. 基础情绪。Cogn. Sci. Inf. 1982, 21, 529–553. [CrossRef]
10. Plutnik, R.; Franzoni, V.; Valverdú, J. 人机交互中的情感特征。Web智能国际会议论文集，莱比锡，德国，2017年8月23–26日，924–930. [CrossRef]
11. Franzoni, V.; Milani, A.; Valverdú, J. 情感建模中的过拟合。Web智能国际会议，希腊，2017年10月14–16日。
12. Franco, V.; Milani, A.; Verdi, D.; Vallverdu, J. 机器学习：回归。Web Intell. 2019, 17–27.
13. Franco, V.; Milani, A.; Verdi, D.; Vallverdu, J. 增强障碍人士交流的脑机接口。云计算计算国际会议论文集，上海，2016年12月6–12日，327–332。
14. Gervasi, O.; Magni, R.; Marcellari, S. 人脸自动识别。计算机科学与应用论文集，A.M., Taniar, D., Aduhan, B.O., Gervasi, O.; Eds.; Springer International Publishing: Cham,瑞士，2014，8584卷，70–721。
15. Bastiani, E.; Dardi, A.; Aiello, L.; Giacomo, F. 机器人虚拟接口开发。Appl. Intell. 2016, 44–66.
16. Picard, R. 人工计算技术。Hum. Comput. 2003, 53–64.
17. Ciebłek, M.; Dür, Ö.; Üzilli, F. 情感检测的潜力。CEUR工作会议，瓦伦西亚，西班牙，2013年7月17–18日，47–58。
18. Franco, V.; Milani, A. 自疗表情识别。计算机科学与应用——ICISA论文集，Misra, S., Rocha, V., Morgante, B., Stankova, E., Korchkov, V., Torre, C., Rocha, A.M., Taniar, D., Aduhan, B.O., Tarantino, E.; Eds.; Springer International Publishing: Cham,瑞士，2019，1166卷，665–676。
19. Hayes, G.; Ramirez, S.; Marci, G.; Nguyen, D.; Yegayan, M. 交互式视觉分析。Comput. 2014, 16, 663–680.
20. Picard, R.; Vassili, E.; Heasley, J. 生理状态分析。Trans. Anal. Meth. 2017, 25, 1115–1191.
21. Bertola, F.; Patti, V. 回答情感反应。CEUR工作会议，瓦伦西亚，西班牙，2015年7月17–18日。
22. Canosa, A.; Bader, J.; El-Noza, M.S.; Anderson, E. 游戏设计中的情感激发。第4次个性化系统会议（EMPORIA）论文集，波士顿，美国，2015，1–9。
23. Angelov, P.; Xu, X.; Iglesias, I.; Ledanca, S.; Opele, Z.; Remezani, R. 思想识别。Mag. 2017年5月–7。

