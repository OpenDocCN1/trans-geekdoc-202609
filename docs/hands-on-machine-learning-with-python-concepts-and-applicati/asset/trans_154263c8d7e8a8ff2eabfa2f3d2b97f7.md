

# 使用 Python 进行机器学习实战

## 概念与应用

**John Anderson & Peter Morgan**

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00001.jpeg)

## 如何联系我们

如果您在本书中发现任何损坏、编辑问题或其他问题，请立即通过电子邮件通知我们的客户服务：

[contact@aisciences.net](mailto:contact@aisciences.net)

我们的目标是为您在计算机科学学科的技术学习提供高质量的书籍。

非常感谢您购买本书。

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00002.jpeg)

## 目录

- [作者简介](#part0000_split_006.html#_Toc521008051)
- [AI Sciences 出版社序言](#part0000_split_007.html#_Toc521008052)
- [前言](#part0000_split_009.html#_Toc521008053)
  - [为什么要读这本书](#part0000_split_009.html#_Toc521008054)
  - [适合读者](#part0000_split_009.html#_Toc521008055)
  - [学习内容概览](#part0000_split_009.html#_Toc521008056)
- [安装与设置](#part0000_split_011.html#_Toc521008057)
  - [下载 Anaconda](#part0000_split_011.html#_Toc521008058)
  - [运行 Jupyter Notebook](#part0000_split_011.html#_Toc521008059)
- [Python 快速入门](#part0000_split_012.html#_Toc521008060)
  - [字符串、列表、函数及更多](#part0000_split_012.html#_Toc521008061)
  - [Jupyter Notebook](#part0000_split_012.html#_Toc521008062)
  - [Numpy, Pandas, Scipy, Matplotlib, Scikit-learn](#part0000_split_012.html#_Toc521008063)
    - [数值计算库 (Numpy)](#part0000_split_012.html#_Toc521008064)
    - [Pandas](#part0000_split_012.html#_Toc521008065)
    - [科学计算库 (Scipy)](#part0000_split_012.html#_Toc521008066)
    - [Matplotlib](#part0000_split_012.html#_Toc521008067)
    - [Scikit-Learn](#part0000_split_012.html#_Toc521008068)
  - [关于 Google TensorFlow](#part0000_split_012.html#_Toc521008069)
- [您的第一个机器学习项目](#part0000_split_013.html#_Toc521008070)
  - [泰坦尼克号生存预测](#part0000_split_013.html#_Toc521008071)
  - [启示与可能性](#part0000_split_013.html#_Toc521008072)
  - [通用工作流程](#part0000_split_013.html#_Toc521008073)
- [通用机器学习概念](#part0000_split_014.html#_Toc521008074)
  - [什么是机器学习](#part0000_split_014.html#_Toc521008075)
  - [监督学习](#part0000_split_014.html#_Toc521008076)
  - [无监督学习](#part0000_split_014.html#_Toc521008077)
  - [半监督学习算法](#part0000_split_014.html#_Toc521008078)
  - [强化学习算法](#part0000_split_014.html#_Toc521008079)
  - [深度学习](#part0000_split_014.html#_Toc521008080)
  - [过拟合与欠拟合](#part0000_split_014.html#_Toc521008081)
  - [正确性](#part0000_split_014.html#_Toc521008082)
  - [偏差-方差权衡](#part0000_split_014.html#_Toc521008083)
  - [特征提取与选择](#part0000_split_014.html#_Toc521008084)
  - [为什么机器学习如此流行](#part0000_split_014.html#_Toc521008085)
- [回归](#part0000_split_015.html#_Toc521008086)
  - [简单与多元线性回归](#part0000_split_015.html#_Toc521008087)
  - [逻辑回归](#part0000_split_015.html#_Toc521008088)
  - [广义线性模型](#part0000_split_015.html#_Toc521008089)
  - [回归示例：预测波士顿房价](#part0000_split_015.html#_Toc521008090)
  - [分析步骤](#part0000_split_015.html#_Toc521008091)
  - [导入库：](#part0000_split_015.html#_Toc521008092)
  - [如何预测与预报](#part0000_split_015.html#_Toc521008093)
- [K-近邻算法](#part0000_split_016.html#_Toc521008094)
  - [K 近邻算法简介](#part0000_split_016.html#_Toc521008095)
  - [如何创建和测试 K 近邻分类器](#part0000_split_016.html#_Toc521008096)
  - [另一个应用](#part0000_split_016.html#_Toc521008097)
  - [计算相似度](#part0000_split_016.html#_Toc521008098)
  - [定位邻居](#part0000_split_016.html#_Toc521008099)
  - [生成响应](#part0000_split_016.html#_Toc521008100)
  - [评估准确率](#part0000_split_016.html#_Toc521008101)
  - [维度灾难](#part0000_split_016.html#_Toc521008102)
- [朴素贝叶斯](#part0000_split_017.html#_Toc521008103)
  - [朴素贝叶斯的应用](#part0000_split_017.html#_Toc521008104)
  - [如何在 Python 中使用朴素贝叶斯构建基础模型](#part0000_split_017.html#_Toc521008105)
- [决策树与随机森林](#part0000_split_018.html#_Toc521008106)
  - [划分的熵](#part0000_split_018.html#_Toc521008107)
  - [创建决策树](#part0000_split_018.html#_Toc521008108)
  - [随机森林](#part0000_split_018.html#_Toc521008109)
- [神经网络](#part0000_split_019.html#_Toc521008110)
  - [感知机](#part0000_split_019.html#_Toc521008111)
  - [反向传播](#part0000_split_019.html#_Toc521008112)
  - [如何使用 TensorFlow 运行神经网络](#part0000_split_019.html#_Toc521008113)
  - [如何获取数据](#part0000_split_019.html#_Toc521008114)
  - [如何训练和测试数据](#part0000_split_019.html#_Toc521008115)
- [聚类](#part0000_split_020.html#_Toc521008116)
  - [聚类简介](#part0000_split_020.html#_Toc521008117)
  - [聚类示例](#part0000_split_020.html#_Toc521008118)
  - [使用 Scikit-Learn 运行 K-means](#part0000_split_020.html#_Toc521008119)
  - [模型实现](#part0000_split_020.html#_Toc521008120)
  - [自底向上的层次聚类](#part0000_split_020.html#_Toc521008121)
  - [K-means 聚类](#part0000_split_020.html#_Toc521008122)
- [网络分析](#part0000_split_021.html#_Toc521008123)
  - [介数中心性](#part0000_split_021.html#_Toc521008124)
  - [特征向量中心性](#part0000_split_021.html#_Toc521008125)
- [推荐系统](#part0000_split_021.html#_Toc521008126)
- [分类](#part0000_split_022.html#_Toc521008127)
  - [多分类](#part0000_split_022.html#_Toc521008128)
  - [流行分类算法](#part0000_split_022.html#_Toc521008129)
- [支持向量机](#part0000_split_023.html#_Toc521008130)
  - [如何创建和测试支持向量机 (SVM) 分类器](#part0000_split_023.html#_Toc521008131)
- [使用 TensorFlow 进行深度学习](#part0000_split_024.html#_Toc521008132)
  - [深度学习与其他机器学习方法的对比](#part0000_split_024.html#_Toc521008133)
  - [深度学习的应用](#part0000_split_024.html#_Toc521008134)
  - [Python 深度学习框架](#part0000_split_024.html#_Toc521008135)
  - [安装 TensorFlow](#part0000_split_024.html#_Toc521008136)
    - [在 Windows 上安装 TensorFlow](#part0000_split_024.html#_Toc521008137)
    - [在 Linux 上安装 TensorFlow](#part0000_split_024.html#_Toc521008138)
    - [在 macOS 上安装 TensorFlow](#part0000_split_024.html#_Toc521008139)
  - [如何创建神经网络模型](#part0000_split_024.html#_Toc521008140)
- [深度学习案例研究](#part0000_split_025.html#_Toc521008141)
  - [银行客户流失建模](#part0000_split_025.html#_Toc521008142)
  - [情感分析](#part0000_split_025.html#_Toc521008143)
- [致谢！](#part0000_split_026.html#_Toc521008144)
- [来源与参考文献](#part0000_split_027.html#_Toc521008145)
  - [软件、库与编程语言](#part0000_split_027.html#_Toc521008146)
  - [数据集](#part0000_split_027.html#_Toc521008147)
  - [在线书籍、教程及其他参考资料](#part0000_split_027.html#_Toc521008148)
- [致谢！](#part0000_split_028.html#_Toc521008149)

---

© 2018 AI Sciences 版权所有

保留所有权利。

首次印刷，2018

Davies Company 编辑

Pixels Studio 电子书转换与封面设计

AI Sciences LLC 出版

ISBN-13: 978-1724731968

ISBN-10: 1724731963

未经作者直接书面许可，本书内容不得复制、复印或传播。

