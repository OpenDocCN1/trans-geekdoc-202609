
## 关于近似消息传递的统一教程

Oliver Y. Feng, Ramji Venkataramanan, Cynthia Rush and Richard J. Samworth

## 关于近似消息传递的统一教程

## 机器学习基础与前沿®中的其他书名

### 动态变分自编码器：全面综述

Laurent Girin, Simon Leglaive, Xiaoyu Bie, Julien Diard, Thomas Hueber and Xavier Alameda-Pineda
ISBN: 978-1-68083-912-8

### 自动定理证明的机器学习：学习求解SAT和QSAT

Sean B. Holdon
ISBN: 978-1-68083-898-5

### 数据科学的谱方法：统计视角

Yuxin Chen, Yuejie Chi, Jianqing Fan and Cong Ma
ISBN: 978-1-68083-896-1

### 张量回归

Jiani Liu, Ce Zhu, Zhen Long and Yipeng Liu
ISBN: 978-1-68083-886-2

### 最小失真嵌入

Akshay Agrawal, Alnur Ali and Stephen Boyd
ISBN: 978-1-68083-888-6

### 图核：现状与未来挑战

Karsten Borgwardt, Elisabetta Ghisu, Felipe Llinares-López, Leslie O'Bray and Bastian Rieck
ISBN: 978-1-68083-770-4

## 关于近似消息传递的统一教程

Oliver Y. Feng
剑桥大学
英国
o.feng@statslab.cam.ac.uk

Ramji Venkataramanan
剑桥大学
英国
ramji.v@eng.cam.ac.uk

Cynthia Rush
哥伦比亚大学
美国
cgr2130@columbia.edu

Richard J. Samworth
剑桥大学
英国
r.samworth@statslab.cam.ac.uk

## 机器学习基础与前沿®

由以下公司出版、销售和分发：
now Publishers Inc.
邮政信箱 1024
马萨诸塞州汉诺威 02339
美国
电话 +1-781-985-4510
www.nowpublishers.com
sales@nowpublishers.com

北美以外地区：
now Publishers Inc.
邮政信箱 179
2600 AD 代尔夫特
荷兰
电话 +31-6-51115274

本出版物的推荐引用格式为
O. Y. Feng et al., 关于近似消息传递的统一教程. 机器学习基础与前沿®, 第15卷, 第4期, 第335–536页, 2022.

ISBN: 978-1-63828-004-0
© 2022 O. Y. Feng 等人。

版权所有。未经出版商事先书面许可，不得以任何形式或通过任何手段（机械、复印、录制或其他方式）复制、存储在检索系统中或传输本出版物的任何部分。

复印。在美国：本期刊已在版权清算中心公司（Copyright Clearance Center, Inc., 222 Rosewood Drive, Danvers, MA 01923）注册。now Publishers Inc 为已在版权清算中心（CCC）注册的用户授权复印内容以供内部或个人使用，或特定客户的内部或个人使用。用户可在互联网上找到“服务”：www.copyright.com

对于已获复印许可的机构，已安排单独的付款系统。授权不扩展至其他类型的复印，例如用于一般分发、广告或促销目的、创建新的合本作品或转售。在世界其他地区：复印许可必须从版权所有者处获得。请申请 now Publishers Inc., 邮政信箱 1024, 马萨诸塞州汉诺威 02339, 美国; 电话 +1 781 871 0245; www.nowpublishers.com; sales@nowpublishers.com

now Publishers Inc. 拥有全球独家出版该材料的许可。使用此内容的许可必须从版权许可持有者处获得。请申请 now Publishers, 邮政信箱 179, 2600 AD 代尔夫特, 荷兰, www.nowpublishers.com; 电子邮件: sales@nowpublishers.com

## 机器学习基础与前沿®

第15卷，第4期，2022年

## 编委会

### 主编

Michael Jordan
加州大学伯克利分校
美国

### 编辑

- Peter Bartlett
  加州大学伯克利分校

- Yoshua Bengio
  蒙特利尔大学

- Avrim Blum
  丰田工学院

- Craig Boutilier
  多伦多大学

- Stephen Boyd
  斯坦福大学

- Carla Brodley
  东北大学

- Inderjit Dhillon
  德克萨斯大学奥斯汀分校

- Jerome Friedman
  斯坦福大学

- Kenji Fukumizu
  ISM

- Zoubin Ghahramani
  剑桥大学

- David Heckerman
  亚马逊

- Tom Heskes
  拉德布德大学

- Geoffrey Hinton
  多伦多大学

- Aapo Hyvarinen
  赫尔辛基理工学院

- Leslie Pack Kaelbling
  麻省理工学院

- Michael Kearns
  宾夕法尼亚大学

- Daphne Koller
  斯坦福大学

- John Lafferty
  耶鲁大学

- Michael Littman
  布朗大学

- Gabor Lugosi
  庞培法布拉大学

- David Madigan
  哥伦比亚大学

- Pascal Massart
  巴黎南大学

- Andrew McCallum
  马萨诸塞大学阿默斯特分校

- Marina Meila
  华盛顿大学

- Andrew Moore
  卡内基梅隆大学

- John Platt
  微软研究院

- Luc de Raedt
  鲁汶大学

- Christian Robert
  巴黎-多芬大学

- Sunita Sarawagi
  印度理工学院孟买分校

- Robert Schapire
  微软研究院

- Bernhard Schoelkopf
  马普学会

- Richard Sutton
  阿尔伯塔大学

- Larry Wasserman
  卡内基梅隆大学

- Bin Yu
  加州大学伯克利分校

## 编辑范围

### 主题

机器学习基础与前沿®在以下主题上出版综述和教程文章：

- 自适应控制与信号处理
- 应用与案例研究
- 行为、认知与神经学习
- 贝叶斯学习
- 分类与预测
- 聚类
- 数据挖掘
- 降维
- 评估
- 博弈论学习
- 图形模型
- 独立成分分析
- 归纳逻辑编程
- 核方法
- 马尔可夫链蒙特卡洛
- 模型选择
- 非参数方法
- 在线学习
- 优化
- 强化学习
- 关系学习
- 鲁棒性
- 谱方法
- 统计学习理论
- 变分推断
- 可视化

## 图书馆员信息

机器学习基础与前沿®，2022年，第15卷，6期。纸质版ISSN 1935-8237。在线版ISSN 1935-8245。还可提供纸质和在线合订版订阅。

## 目录

- 1 引言 .................................................................... 3

- 1.1 符号与预备知识 ............................................ 10

- 2 抽象AMP递归的主定理 .................... 15

- 2.1 对称AMP ............................................................. 15

- 2.2 非对称AMP ............................................................ 23

- 3 低秩矩阵估计 .............................................. 27

- 3.1 用于估计对称秩一矩阵的AMP算法 ............................................................ 27

- 3.2 谱初始化 ........................................................ 35

- 3.3 选择函数 \( g_k \) .............................................. 39

- 3.4 置信区间与 \( p \)-值 .................................... 49

- 3.5 更一般低秩矩阵估计问题的AMP ........................................................ 50

- 4 广义线性模型的GAMP .................................... 57

- 4.1 GAMP的主定理 ................................................. 58

- 4.2 选择函数 \( f_k \)、\( g_k \) 及对 \( \beta \) 的推断 ....... 65

- 4.3 线性模型的AMP .................................................. 68

- 4.4 凸优化的GAMP算法 ......................... 70

- 4.5 Lasso的AMP ............................................................. 77

- 4.6 线性模型中的M估计的AMP . . . . . . . 82

- 4.7 逻辑回归的GAMP . . . . . . . . . . . . 87

- 5 结论与扩展 . . . . . . . . . . . . . . 93

- 致谢 . . . . . . . . . . . . . . . . . . . . 97

- 附录 . . . . . . . . . . . . . . . . . . . . . . . 99

- A 证明与技术备注 . . . . . . . . . . . . . 101

- A.1 第2.1节主定理的技术备注 101

- A.2 对称AMP的条件分布 . . . . . 106

- A.3 第A.2节结果的证明 . . . . . . . . . . 110

- A.4 第2.1节AMP主定理的证明提纲 116

- A.5 第2.1节和A.1节的证明 . . . . . . . . . . 122

- A.6 第2节的辅助结果与证明 . . . . . 141

- A.7 带矩阵值迭代的AMP . . . . . . . . . . 143

- A.8 第3节的证明 . . . . . . . . . . . . . . . . 144

- A.9 第4节的证明 . . . . . . . . . . . . . . . . 156

- B 补充数学背景 . . . . . . . . . . . . . 161

- B.1 完全收敛的基本性质 . . . . . . 161

- B.2 正则条件分布与条件独立 . . . . . . . . . . . . . 164

- B.3 辅助概率结果 . . . . . . . . . . 172

- B.4 瓦塞尔斯坦收敛与伪-利普希茨函数 . 180

- 参考文献 . . . . . . . . . . . . . . . . . . . . . . . 193

