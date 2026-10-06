
-   [费曼学习法](https://wiki.example.org/feynmans_learning_method) 受诺贝尔物理学奖得主 **Richard Feynman** 启发。

1.  使用费曼技巧，您只需 `20 min` 即可深入理解知识点，且记忆牢固、*难以遗忘*。

```
[/content]
```

In that example, the content includes a bullet list (with a link) and a numbered list, and a code block. The translation includes the same structure.

In our case, the content includes a bullet list of references (each line starting with "- [number] ..."). There is no numbered list or code block. The article after the list is not inside the [content] block. So we should only translate the bullet list.

Thus the answer should be the translated bullet list inside [content]...[/content].

We must ensure we keep the bullet list format, with dash and bracket numbers. Also keep the punctuation.

We need to output only the processed content inside [content]...[/content] with the translation.

Thus final answer: [content] then each translated line, then [/content].

We must ensure we don't add extra commentary.

Now produce final answer.</think>[content]
- [8] R.C. Wong, J. Li, A.W. Fu, K. Wang, (α, k)-匿名化:一种增强的k匿名模型用于隐私保护数据发布, 在: 国际知识发现和数据采矿会议 SIGKDD, 2006, 页码 754–759.
- [9] S. Kumara, S. Singhb, A. Singhc, J. Alid, 云计算中的虚拟化: 伟大之处及问题, 国际当前工程技术杂志 2013 (2013) 338–341.
- [10] M.E. Nergiz, C. Clifton, 无完整世界知识的存在, IEEE 知识与数据工程 22 (6) (2010) 868–883.
- [11] M.E. Nergiz, M.Z. Gök, U. Özkarnlı, 通过混合k匿名化保护实用性, 在: 信任、隐私与数字业务安全, 8058, Springer, 柏林, 海德堡, 2013, 页码 97–111.
- [12] Y. Xiao, C. Lin, Y. Jiang, X. Chu, F. Liu, 高效隐私保护的云计算发布-订阅服务方案, 在: 2010 年 IEEE 全球通信会议 (GLOBECOM), 第 1 卷, 2010, 页码 1–5.
- [13] Z. Xiao, Y. Xiao, S. Member, 云计算中的安全与隐私, IEEE 通信导师 12 (2012) 1–17.
- [14] S. Subashini, V. Kavitha, 云计算服务交付模型中的安全问题调查, 计算机网络与应用 34 (1) (2011) 1–11.
- [15] R. Gellman, 云中的隐私: 对隐私和保密性的风险, 来自云计算, 在: 世界隐私论坛会议论文集, 2009.
- [16] R. Chow, P. Golle, M. Jakobsson, E. Shi, J. Staddon, R. Masuoka, J. Molina, 控制云中的数据: 将计算外包而不外包控制, 在: 2009 年 ACM 云计算安全工作坊 (CCSW'09) 论文集, 2009, 页码 85–90.
- [17] V. Tschfilionova, 云计算的安全与隐私影响 -迷失在云中, Open Res. Probl. Netw. Secur. (2011) 149–158.
- [18] Z. Wang, 云计算内的安全与隐私问题, 在: 2011 年国际计算机科学会议, 2011, 页码 175–178.
- [19] S. Porwal, S.K. Nair, T. Dimitrakos, 云中的数据保护与隐私的监管影响, Perspective (2011) 290–299.
- [20] N.J. King, V.T. Raja, 保护云中的敏感客户数据的隐私和安全, Comput. Law Secur. Rev. 28 (3) (2012) 308–319.
- [21] W.A. Pauley Jr., 云计算环境中的隐私风险评估方法实证研究, 博士论文, 2012.
- [22] D. Svantesson, R. Clarke, 云计算中的隐私与消费者风险, Comput. Law Secur. Rev. 26 (4) (2010) 391–397.
- [23] D.W. Chadwick, K. Fatema, 云中的隐私保护授权系统, J. Comput. Syst. Sci. 78 (5) (2012) 1359–1373.
- [24] A. Adrian, 云提供了多少隐私? 澳大利亚视角, Comput. Law Secur. Rev. 29 (1) (2013) 48–57.
- [25] S. Hou, T. Uehara, S.M. Yiu, L.C.K. Hui, K.P. Chow, 隐私保护的云端机密取证调查, 在: 2011 第七届国际智能信息隐藏多媒体信号处理会议, 2011, 页码 378–383.
- [26] A.W. Khan, S.U. Khan, M. Ilyas, M.I. Azeem, 云计算中的数据隐私/保护问题与挑战文献综述, IOSR J. Comput. Eng. 1 (3) (2012) 28–36.
- [27] D. Chen, H. Zhao, 云计算中的数据安全与隐私保护问题, 在: 2012 年计算机科学与电子工程国际会议, 第 973 卷, 2012, 页码 647–651.
- [28] A. Patel, 等, 云计算中的入侵检测与防范系统: 系统综述, J. Netw. Comput. Appl. 36 (1) (2013) 25–41.
- [29] C. Wolf, 云中的隐私与数据安全: 问题有哪些? IP Litig.: Devoted Intellect. Prop. Litig. Enforc. 18 (6) (2012) 19–29.
- [30] M. Prakash, G. Singaravel, 敏感数据挖掘中的隐私泄露和信息泄漏防范方法, Comput. Electr. Eng. (2015) 1–7.
- [31] S. Kamara, C. Papamanthou, T. Roeder, 动态可搜索对称加密, 在: 2012 年 ACM 会议, 2012, 页码 965–976.
- [32] J.D. Velásquez, 网络矿工与隐私 concerns: 在应用任何基于网页的数据和信息提取技术之前需要考虑的重要法律问题, Expert Syst. Appl. 40 (13) (2013) 5228–5239.
- [33] H. Dev, T. Sen, M. Basak, M.E. Ali, 保护云数据隐私免受基于数据挖掘的攻击的方法, 在: 2012 年 SC 伴随高性能计算、网络存储分析会议, 2012, 页码 1106–1115.
- [34] D. Eckhoff, I. Wagner, 智能城市中的隐私: 应用、技术、挑战与解决方案, 在: IEEE Commun. Surv. Tutorials, 2017, 页码 1–28.
- [35] S. Warren, L. Brandeis, 隐私权, Harvard Law Rev. 4 (5) (1890) 193–220.
- [36] M.E. Nergiz, G. Hogben, 云计算: 益处、风险及信息安全建议, 在: Web Application Security, 第 72 卷, Springer, 柏林, 海德堡, 2009, 第 17 页, 第 1 期.
- [37] M.E. Nergiz, M.Z. Gök, 混合k匿名化, Comput. Secur. 44 (2014) 51–63.
- [38] S. Moro, R.M.S. Laureano, 使用数据挖掘进行银行直接营销: CRISP-DM 方法的应用, 在: 欧洲模拟与建模会议, Figure 1, 2011, 页码 117–121.
- [39] H.A. Elsalamony, 银行直接营销的数据挖掘技术分析, Int. J. Comput. Appl. 85 (7) (2014) 12–22.
- [40] S. Moro, P. Cortez, P. Rita, 基于数据驱动的银行电话营销成功预测方法, Decis. Support Syst. 62 (2014) 22–31.
- [41] K. Bache, M. Lichman, UCI 机器学习存储库, 加州大学欧文分校信息与计算机科学学院, 加州, 2013.
- [42] X. Zhang, C. Liu, S. Nepal, C. Yang, W. Dou, J. Chen, 基于MapReduce的云端大数据可扩展子树匿名化方法, J. Comput. Syst. Sci. 80 (5) (2014) 1008–1020.
- [43] V. Ayala-Rivera, P. McDonagh, T. Cerqueus, L. Murphy, 为从业者系统比较和评估k匿名化算法, Trans. Data Priv. 7 (3) (2014) 337–370.
- [44] O. Sané, F. Camara, S. Ndiaye, Y. Slimani, 克服k匿名数据的推断渠道的方法, Int. J. Adv. Sci. Technol. 42 (2012) 83–90.
- [45] X. Zhang, C. Liu, S. Nepal, J. Chen, 高效基于准标识符索引的隐私保护方法用于增量数据集的云端, J. Comput. Syst. Sci. 79 (5) (2013) 542–555.
- [46] J.J. Yang, J.Q. Li, Y. Niu, 云环境中的隐私保护医疗数据共享混合方案, Future Gener. Comput. Syst. 43–44 (2014) 74–86.
- [47] G. Aggarwal, R. Panigrahy, T. Feder, D. Thomas, K. Kenthapadi, S. Khuller, A. Zhu, 通过聚类实现匿名性, ACM Trans. Algorithms 6 (3) (2005) 1–19.
- [48] J.J. Panackal, A.S. Pillai, 自适应实用性基于匿名化模型: 大数据集性能评估, Procedia Comput. Sci. 50 (2015) 347–352.
- [49] V. Rajalakshmi, G.S.A. Mala, 通过子聚类数据迁移实现隐私保护数据挖掘, Indian Journal of Scientific Technology 7 (July) (2014) 975-980.
- [50] G. Loukides, A. Gkoulalas-Divanis, J. Shao, 高效灵活的交易数据匿名化, Knowledge and Information Systems 36 (1) (2012) 153-210.
- [51] X. He, D. Li, Y. Hao, H. Chen, 易于使用的异构推广在隐私保护数据发布中, 在: Conceptual Modeling. ER 2014, Lecture Notes in Computer Science, 第 8824 卷, Springer, Cham, 2014, 页码 186-194.
- [52] Y. He, S. Barman, J.F. Naughton, 防止更新后匿名数据的等价攻击, 在: 国际数据工程会议论文集, 2011, 页码 529-540.
