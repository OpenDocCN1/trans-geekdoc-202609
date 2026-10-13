

*   **[SCAN2007]** [M. Scannapieco](#ch14.xhtml#Cref14_7), I. Figotin, E. Bertino, A. Elmagarmid, “Privacy Preserving Schema and Data Matching, *Proceedings of 2007 ACM SIGMOD International Conference on Management of Data, Beijing China*, 653–664.

*   **[THUR1998]** [B. Thuraisingham](#ch14.xhtml#Cref14_8), Data Mining: Technologies, Techniques, Tools and Trends, CRC Press, 1998.

*   **[THUR2002a]** [B. Thuraisingham](#ch14.xhtml#Cref14_9), Data Mining, National Security, Privacy and Civil Liberties, SIGKDD Explorations, Volume 4, # 2, 2002, 1–5.

*   **[THUR2002b]** [B. Thuraisingham](#ch14.xhtml#Cref14_10), Data Mining for Counter-Terrorism, Presented at the White House Office of Science and Technology Policy, Washington DC, February 2002.

*   **[THUR2002c]** [B. Thuraisingham](#ch14.xhtml#Cref14_11), Data Mining for Counter-Terrorism, Presented at the Database Program panel at Stanford University, Palo Alto, March 2002.

*   **[THUR2002d]** [B. Thuraisingham](#ch14.xhtml#Cref14_12), Data Mining for Counter-Terrorism, Panel at the IFIP 113 Conference on Data and Applications Security, University of Cambridge, England, July 2002.

*   **[THUR2002e]** [B. Thuraisingham](#ch14.xhtml#Cref14_13), Data Mining for Counter-Terrorism, Presented at the United Nations, September 2002 (also at the White House Office of Technology and Policy, 2002).

*   **[THUR2003]** [B. Thuraisingham](#ch14.xhtml#Cref14_14), Web Data Mining with Applications to Counter-terrorism and Business Intelligence, CRC Press, 2003.

*   **[THUR2005]** [B. Thuraisingham](#ch14.xhtml#Cref14_15), Privacy-Preserving Data Mining: Development and Directions, Journal of Database Management, Volume 16, # 1, 2005, 75–87.

*   **[THUR2015]** [B. Thuraisingham](#ch14.xhtml#Cref14_16), Keeping Better Tabs on Suspicious Persons (NY Times Opinion Column), January 13, 2015. [https://www.nytimes.com/roomfordebate/2015/01/12/when-known-jihadists-come-home/keeping-better-tabs-on-suspicious-persons](https://www.nytimes.com)

*   **[THUR2018]** [B. M. Thuraisingham](#ch14.xhtml#Cref14_17), M. Kantarcioglu, E. Bertino, J. Z. Bakdash, M. Fernández, Towards a Privacy-Aware Quantified Self Data Management Framework, SACMAT, Indianapolis, Indiana, 2018, 173–184.

*   **[THUR2020a]** [B. Thuraisingham](#ch14.xhtml#Cref14_18), Data Science, COVID-19, Privacy and Civil Liberties, *Proceedings IEEE BigCyber*, December 2020.

*   **[THUR2020b]** [B. Thuraisingham](#ch14.xhtml#Cref14_19), Can AI be for Good in the Midst of Cyber Attacks and Privacy Violations? A Position Paper, ACM CODASPY, 2020, 1–4.

*   **[ULUS2014]** [H. Ulusoy](#ch14.xhtml#Cref14_20), M. Kantarcioglu, E. Pattuk, K. W. Hamlen, Vigiles: Fine-Grained Access Control for MapReduce Systems, 2014 *IEEE International Congress on Big Data (BigData Congress)*, Anchorage, Alaska, pp. 40–47

*   **[UN]** [United Nations](#ch14.xhtml#Cref14_21), AI for Good, [https://aiforgood.itu.int/](https://aiforgood.itu.int)

# 第三部分 结语

DOI: [10.1201/9781003081845-23](https://doi.org/10.1201/9781003081845-23)

在[第三部分](#part_03.xhtml#part3)中，我们讨论了安全和隐私感知的数据科学。部分未来方向包括以下内容。在对抗性支持向量机学习方面（[第10章](#ch10.xhtml#chapter10)），该工作的一个未来方向是将成本敏感度量添加到学习模型中。另一个方向是将单一学习模型扩展为集成模型，其中每个基学习器处理不同的一组攻击。我们还希望纳入对其他对抗性机器学习技术以及不同类型攻击的研究。此外，我们还希望考虑其他的博弈论模型。在对抗性相关向量机学习方面（[第11章](#ch11.xhtml#chapter11)），未解决的问题是发现一种高效的方法来同时更新核函数和学习参数。该解决方案将有助于在样本空间中找到针对最坏情况攻击的最优学习模型。与对抗性支持向量机学习类似，另一个方向是考虑不同类型的攻击。

在隐私保护数据挖掘方面（[第12章](#ch12.xhtml#chapter12)），一个未来方向是构建可用于对扰动数据集进行分类的分类器。正如我们之前提到的，利用概率作为加权，配合随机噪声数据 R 的更好界限，是一种需要进一步研究的方法。此外，随着新型机器学习技术的开发，如基于深度学习的方法，我们需要探索针对这些方法的隐私保护机器学习。在隐私感知的基于策略的数据管理框架方面（[第13章](#ch13.xhtml#chapter13)），下一步是进行框架的详细设计和实现。我们还必须设计形式化框架，以便无论实施何种解决方案，都能指定和推理策略。我们还需要将用户的行为方面纳入考量。我们需要为诸如智能交通系统之类的应用调整该框架。

最后，在[第14章](#ch14.xhtml#chapter14)中，我们讨论了数据科学在 COVID-19 相关应用中的应用，并讨论了可能发生的隐私侵犯。我们还讨论了由美国公民自由联盟等组织提出的各种框架。

# 第四部分 访问控制与数据科学

# 第四部分 导言

DOI: [10.1201/9781003081845-25](https://doi.org/10.1201/9781003081845-25)

[第四部分](#part_04.xhtml#part4)由五章组成，描述了访问控制与数据科学。特别是，将讨论我们开发的一些实验系统。

[第15章](#ch15.xhtml#chapter15)描述了一个基于大数据访问控制的安全云查询处理系统。[第16章](#ch16.xhtml#chapter16)描述了我们开发的一个运行在云中的基于策略的信息共享系统。我们的信息共享策略植根于访问控制策略。[第17章](#ch17.xhtml#chapter17)讨论了一个基于社交媒体数据语义 Web 的访问控制框架，我们将社交媒体数据视为大数据的一种形式。[第18章](#ch18.xhtml#chapter18)描述了我们基于语义 Web 大数据的访问控制开发的推理控制器。最后，[第19章](#ch19.xhtml#chapter19)讨论了我们的一些工作如何应用于智能交通系统等应用。

# 15 基于大数据系统访问控制的安全云查询处理

DOI: [10.1201/9781003081845-26](https://doi.org/10.1201/9781003081845-26)

## 15.1 介绍

正如[第4章](#ch04.xhtml#chapter4)所述，云计算是信息技术和数据处理领域的一个新兴范式。企业利用云计算服务外包数据维护，这可以带来显著的经济效益。企业在“云”中远程存储和访问数据。随着云计算的普及，服务提供商面临着日益增长的挑战。他们必须在提供高效信息检索的同时维护海量异构数据。因此，云计算解决方案的关键重点是可扩展性和查询效率。换句话说，云计算是大数据管理和分析的关键技术。

