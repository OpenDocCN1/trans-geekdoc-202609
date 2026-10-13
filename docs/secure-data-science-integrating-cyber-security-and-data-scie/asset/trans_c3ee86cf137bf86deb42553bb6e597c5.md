
*   \[PIRO1996\] [P. Pirolli](#ch03.xhtml#Cref3_17), J. Pitkow, R. Rao, Silk from a Sow's Ear: Extracting Usable Structures from the Web, *Proceedings of 1996 Conference on Human Factors in Computing Systems (CHI-96)*, Vancouver, British Columbia, Canada, 1996, pp. 118–125.

*   \[THUR1998\] [B. Thuraisingham](#ch03.xhtml#Cref3_18), Data Mining: Technologies, Techniques, Tools and Trends, CRC Press, 1998.

*   \[THUR2002\] [B. Thuraisingham](#ch03.xhtml#Cref3_19), Data Mining, National Security, Privacy and Civil Liberties, SIGKDD Explorations, New York, NY, Volume 4, #2, December 2002.

*   \[THUR2003\] [B. Thuraisingham](#ch03.xhtml#Cref3_20), Web Data Mining Technologies and Their Applications in Business Intelligence and Counter-terrorism, CRC Press, 2003.

*   \[THUR2004\] [B. Thuraisingham](#ch03.xhtml#Cref3_21), Managing Threats to Web Databases and Cyber Systems, Issues, Solutions and Challenges, Kluwer (Editors: and V. Kumar, J. Srivastava, Al. Lazarevic), 2004.

*   \[THUR2005\] [B. Thuraisingham](#ch03.xhtml#Cref3_22), Database and Applications Security, CRC Press, 2005.

*   \[THUR2016\] [B. Thuraisingham](#ch03.xhtml#Cref3_23), S. Abrol, R. Heatherly, M. Kantarcioglu, V. Khadilkar, L. Khan, Analyzing and Securing Social Networks, CRC Press, 2016.

*   \[THUR2017\] [B. Thuraisingham](#ch03.xhtml#Cref3_24), P. Praveen, M. M. Masud, L. Khan, Big Data Analytics with Applications in Insider Threat Detection, CRC Press, 2017.

*   \[VAPN1995\] [V.N. Vapnik](#ch03.xhtml#Cref3_25), The Nature of Statistical Learning Theory, Springer, 1995.

*   \[VAPN1998\] [V.N. Vapnik](#ch03.xhtml#Cref3_26), Statistical Learning Theory, Wiley, 1998.

*   \[VAPN1999\] [V.N. Vapnik](#ch03.xhtml#Cref3_27), The Nature of Statistical Learning Theory, Springer-Verlag, 1999.

*   \[YANG2001\] [Q. Yang](#ch03.xhtml#Cref3_28), H. Zhang, T. Li, Mining Web Logs for Prediction Models in WWW Caching and Prefetching, *The 7th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining KDD*, ACM, San Francisco, CA, August 26–29, 2001, pp. 473–478.

# 4 大数据、云、语义 Web 和社交网络技术

DOI: [10.1201/9781003081845-6](https://doi.org/10.1201/9781003081845-6)

## 4.1 简介

[第 2 章](#ch02.xhtml#chapter2)和[第 3 章](#ch03.xhtml#chapter3)讨论了数据安全和隐私、用于网络安全的数据挖掘以及针对数据挖掘的攻击等概念。这些支撑技术是本书讨论概念的基础技术之一。例如，[第 II 部分](#part_02.xhtml#part2)描述了用于网络安全的数据科学，而[第 III 部分](#part_03.xhtml#part3)描述了安全和隐私感知的数据科学。除了数据安全和隐私以及数据挖掘和安全之外，大数据技术、云和语义 Web 也是我们在安全数据科学工作中利用的一些基础技术。本章讨论这些基础技术。

十多年来，涌现出许多大数据管理和分析系统。此外，各种云服务提供商也实施了大数据解决方案。另外，大数据系统的基础设施/平台也已开发完成。大数据系统中值得注意的包括 MongoDB、Google 的 BigQuery 和 Apache HIVE。大数据解决方案由包括 Amazon、IBM、Google 和 Microsoft 在内的云提供商开发。此外，还基于 Apache 的 Hadoop、Spark 和 Storm 等产品开发了基础设施/平台。

选择要讨论的产品是一项艰巨的任务。这是因为几乎每个数据库供应商以及云计算供应商连同分析工具供应商现在都在将其产品作为大数据解决方案进行推销。当我们将所有供应商提供的产品结合起来，并包括开源产品时，则有数百种产品可供讨论。因此，我们选择了最熟悉的产品，通过在我们讲授的课程中讨论这些产品和/或在实验中使用它们。换句话说，我们仅选择了最熟悉并在工作中研究过的服务提供商、产品和框架。描述所有的服务提供商、产品和框架超出了本书的范围。此外，我们在本书中不为任何产品背书。

我们利用云平台管理和分析大型数据集。我们将在全书中看到，云计算是管理大型数据集的核心。云计算已成为面向服务计算的强大计算范式。许多计算服务正被外包给云。此类基于云的服务可用于托管各种网络安全应用，如内部威胁检测和身份管理。Google 现已推出 MapReduce 框架，用于在通用硬件上处理大量数据。Apache 的 Hadoop 分布式文件系统 (HDFS) 正成为云计算的优越软件组件，并与 MapReduce 等集成部件相结合 \[[DEAN2004](#ch04.xhtml#ref4_25), [GHEM2003](#ch04.xhtml#ref4_29), [HDFS](#ch04.xhtml#ref4_33)\]。HP 的 Open Cirrus Testbed 等云正在利用 HDFS。这反过来又导致了许多拥有海量数据需要共享和管理的社交网络站点的出现。例如，我们可能想要对多年的股票市场数据进行统计分析以揭示模式，或基于数年的天气和相关数据构建可靠的天气模型。为了处理分布在许多站点（即节点）上的此类海量数据，需要可扩展的硬件和软件组件。云计算模型应运而生，旨在应对 Web 连接设备的爆炸式增长，并处理海量数据。其特征是大规模可扩展性和新的互联网驱动经济。

另一个用于各种应用的概念是语义 Web 的概念。语义 Web 本质上是一组用于生成机器可理解网页的技术的集合。这些技术也可用于表示任何类型的数据，包括大数据的模式和恶意软件数据。我们基于语义 Web 技术表示的数据进行了一些分析和安全调查。特别是，我们使用语义 Web 技术表示社交网络，随后应用我们的分析技术提取有用的关系。我们还研究了使用语义 Web 技术表示的社交网络的安全性和隐私。

本章的组织结构如下。[第 4.2 节](#ch04.xhtml#sec4_2)讨论大数据管理和分析工具。[第 4.3 节](#ch04.xhtml#sec4_3)讨论云计算概念。[第 4.4 节](#ch04.xhtml#sec4_4)讨论语义 Web 概念。[第 4.4 节](#ch04.xhtml#sec4_4)讨论分析和保护社交网络。[第 4.6 节](#ch04.xhtml#sec4_6)结束本章。[图 4.1](#ch04.xhtml#fig4_1a)说明了本章讨论的概念。本章讨论的工具和技术的更多细节见于 \[[THUR2007](#ch04.xhtml#ref4_64)\], \[[THUR2013](#ch04.xhtml#ref4_65)\], 和 \[[THUR2017](#ch04.xhtml#ref4_68)\]。

![图 4.1 大数据、云计算和语义 Web 技术。](images/fig4_1.jpg)

[图 4.1 大数据、云计算和语义 Web 技术。](#ch04.xhtml#Ffig4_1)

## 4.2 大数据管理和分析工具及技术

我们讨论各类大数据管理和分析工具，包括基础设施工具和大数据管理及分析工具。所讨论的工具如[图 4.2](#ch04.xhtml#fig4_2a)所示 \[[THUS2010](#ch04.xhtml#ref4_69)\]。

![图 4.2 大数据工具。](images/fig4_2.jpg)
