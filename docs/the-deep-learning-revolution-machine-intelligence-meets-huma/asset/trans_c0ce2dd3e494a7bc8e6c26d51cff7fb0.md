

**图灵机** 是艾伦·图灵（Alan Turing，1937年）发明的假设性计算机，作为数学计算的简单模型。图灵机由一个可以前后移动的“纸带”、一个具有“状态”的“读写头”（该状态可改变其下方活动单元的属性）以及一组指令组成，指令规定读写头应如何修改活动单元并移动纸带。每一步中，机器可能修改活动单元的属性并改变读写头的状态。之后，它将纸带移动一个单位。

## 附注

## 前言

- 1. 严格来说，神经网络是一种生物实体，而机器学习中使用的模型是人工神经网络——ANNies。不过，在本书中，除非另有说明，“神经网络”指人工神经网络。

- 2. Conor Dougherty， “谷歌‘登月计划船长’Astro Teller谈如何在谷歌X盈利，”《纽约时报》，2015年2月6日，https://bits.blogs.nytimes.com/2015/02/16/googles-captain-of-moonshots-on-making-profits-at-google-x。深度学习使运行数据中心的能源成本降低了15%，每年节省数亿美元。

- 3. 虽然1943年Watson的那句引语从未得到证实，但它反映了当时几乎普遍未能想象计算机未来的情况。

## 第1章

- 1. “哦，多么勇敢的新世界，竟有这般人！”——莎士比亚《暴风雨》中米兰达的台词（5.1.182–183［牛津标准版莎士比亚］）。

- 2. Bill Vlasic， “通用汽车希望驾驶未来自动驾驶汽车，”《纽约时报》，2017年6月4日，https://www.nytimes.com/2017/06/04/business/general-motors-self-driving-cars-mary-barra.html。

- 3. “全速前进：当100%的汽车都实现自动驾驶时，”《纽约时报杂志》，2017年11月8日。https://www.nytimes.com/interactive/2017/11/08/magazine/tech-design-autonomous-future-cars-100-percent-augmented-reality-policing.html?hp&action=click&pgtype=Homepage&clickSource=story-heading&module=second-column-region&region=top-news&WT.nav=top-news/。

- 4. Christopher Ingraham， “通勤中浪费的惊人人类潜能，”《华盛顿邮报》，2016年2月24日，https://www.washingtonpost.com/news/wonk/wp/2016/02/25/how-much-of-your-life-youre-wasting-on-your-commute/?utm_term=497dfd1b5d9c。

- 5. Patcharinee Tientrakool、Ya-Chi Ho 和 N. F. Maxemchuk， “利用车辆对车辆通信和传感器进行避碰带来的高速公路容量效益，”IEEE车辆技术会议，旧金山，2011年9月5–8日。

- 6. “谷歌Waymo在无人驾驶汽车竞赛中取得里程碑，”《金融时报》，2017年12月10日。https://www.ft.com/content/dc281ed2-c425-11e7-b2bb-322b2cb39656/。

- 7. B. A. Golomb， “当它发生时我们能否识别出来？”收录于Brockman，J.（编），《思考会思考的机器》（纽约：Harper Perennial，2015年），第533–535页。

- 8. Pierre Delforge， “美国的数据中心消耗并浪费日益增长的能源，”自然资源保护委员会议论文，2015年2月6日。https://www.nrdc.org/resources/americas-data-centers-consuming-and-wasting-growing-amounts-energy/。

- 9. W. Brian Arthur， “技术正在将经济带向何方？”麦肯锡季刊，2017年10月。https://www.mckinsey.com/business-functions/mckinsey-analytics/our-insights/Where-is-technology-taking-the-economy/。

- 10. Gideon Lewis-Kraus， “人工智能的大觉醒，”《纽约时报杂志》，2016年12月14日。https://www.nytimes.com/2016/12/14/magazine/the-great-ai-awakening.html。

- 11. 亚历山大·谢尔盖耶维奇·普希金，《叶甫盖尼·奥涅金：一部诗体小说》，第2版，弗拉基米尔·纳博科夫译（普林斯顿：普林斯顿大学出版社，1991年）。

- 12. 关于这一领域的早期探索，请参见Andrej Karpathy的 《循环神经网络的惊人效能》，Andrej Karpathy博客，2015年5月21日发布。http://karpathy.github.io/2015/05/21/rnn-effectiveness/。

- 13. G. Hinton、L. Deng、G. E. Dahl、A. Mohamed、N. Jaitly、A. Senior 等人， “语音识别中声学建模的深度神经网络，”IEEE信号处理杂志 29，第6期（2012年）：82–97页。

- 14. W. Xiong、J. Droppo、X. Huang、F. Seide、M. Seltzer、A. Stolcke 等人， “实现对话式语音识别的人类水平性能，”微软研究院技术报告 MSR-TR-2016-71，2017年2月修订。https://arxiv.org/pdf/1610.05256.pdf。

- 15. A. Esteva、B. Kuprel、R. A. Novoa、J. Ko J、S. M. Swetter、H. M. Blau 和 S. Thrun， “利用深度神经网络进行皮肤科医生水平的皮肤癌分类，”《自然》 542，第7639期（2017年）：115–118页。

- 16. Siddhartha Mukherjee， “人工智能对医生：当诊断实现自动化时会发生什么？”《纽约客》，2017年4月3日。http://www.newyorker.com/magazine/2017/04/03/ai-versus-md/。

- 17. Dayong Wang、Aditya Khosla、Rishab Gargeya、Humayun Irshad 和 Andrew H. Beck，*利用深度学习识别转移性乳腺癌*，arXiv:1606.05718。他们使用的指标称为信号检测理论下的曲线下面积，对假阴性和假阳性均敏感。https://arxiv.org/abs/1606.05718/。

- 18. Anthony Rechtschaffen 和 Alan Kales 编，*人类受试者睡眠阶段标准化术语、技术与评分系统手册*，美国国立卫生研究院出版物编号204（贝塞斯达，马里兰州：美国国立神经系统疾病与失明研究所，神经信息网络，1968年）。

- 19. 参见 Ian Allison， “前核物理学家Henri Waelbroeck解释机器学习如何缓解高频交易，”*国际商业时报*，2016年3月23日，http://www.ibtimes.co.uk/former-nuclear-physicist-henri-waelbroeck-explains-how-machine-learning-mitigates-high-frequency-1551097/；Bailey McCann， “人工智能投资者：AI基金招手，”*华尔街日报*，2017年11月5日。https://www.wsj.com/articles/the-artificial-intelligent-investor-ai-funds-beckon-1509937622/。

- 20. Sei Chong， “早间议程：艰难的一年中对冲基金负责人仍获高薪，”*纽约时报*，2017年5月16日。https://www.nytimes.com/2017/05/16/business/dealbook/hedge-funds-amazon-bezos.html。

- 21. 国家安全局（NSA）除外，该局雇佣了数千名数学家。Alfred W. Hales，个人通信，2016年5月4日。

- 22. Sarfaz Manzoor， “量化分析师：运营华尔街的数学天才，”*每日电讯报*，2013年7月23日。http://www.telegraph.co.uk/finance/10188335/Quants-the-maths-geniuses-running-Wall-Street.html。

- 23. D. E. Shaw、J. C. Chao、M. P. Eastwood、J. Gagliardo、J. P. Grossman、C. Ho 等人， “Anton：分子动力学模拟专用机器，”*ACM通讯* 51，第7期（2008年）：91–97页。

- 24. D. T. Max、Jim Simons， “数字之王，”*纽约客*，2017年12月18日&25日。https://www.newyorker.com/magazine/2017/12/18/jim-simons-the-numbers-king/。

- 25. 即将推出大电影。

- 26. John von Neumann，引自Jacob Bronowski，*人类的登攀*，纪录片电视系列，第13集（1973年）。

- 27. 参见 M. Moračević、M. Schmid、N. Burch、V. Lisý、D. Morrill、N. Bard 等人， “DeepStack：扑克头对头无限注中专家级人工智能，”*科学* 356，第6337期（2017年）：508–513页。标准差是钟形曲线的半宽。只有16%的样本大于平均值一个标准差。只有万分之三的样本大于平均值四个标准差。

- 28. 让人联想到1983年科幻电影《战争游戏》中的情景。参见 https://en.wikipedia.org/wiki/WarGames。

- 29. 参见 D. Silver、A. Huang、C. J. Maddison、A. Guez、L. Sifre、G. v. d. Driessche 等人， “利用深度神经网络和树搜索掌握围棋游戏，”《自然》 529，第7587期（2016年）：484–489页。

- 30. “我不知道今天该如何开口或说什么，”世石对记者们说，“但我想我得首先表达歉意。我本应展现出更好的结果、更好的结局，以及在对弈内容方面更好的表现，我确实为无法满足许多人的期望而道歉。我感觉有点无力。如果回顾这三场比赛，即使第一局我可以回去重新下一遍，我也觉得自己赢不了，因为我当时误判了AlphaGo的能力。”引自Jordan Novet， “围棋冠军李世石为输给谷歌人工智能道歉，”VentureBeat，2016年3月12日。https://venturebeat.com/2016/03/12/go-board-game-champion-lee-sedol-apologizes-for-losing-to-googles-ai/。

- 31. 勘测者1号于1966年6月2日6时17分36秒UT（EST凌晨1:17:36）在月球表面着陆。着陆点位于Flamsteed环形山以北一个100公里环形山内的平坦地区。

- 32. 柯洁引自Selina Cheng， “青少年围棋冠军对弈谷歌AlphaGo的极度挫败感，”Quartz，2017年5月27日。https://qz.com/993147/the-awful-frustration-of-a-teenage-go-champion-playing-googles-alphago/。

- 33. 柯洁引自Paul Mozur， “谷歌人工智能程序在获胜比赛中让中国围棋大师不安，”《纽约时报》，2017年5月25日。https://www.nytimes.com/2017/05/25/business/google-alphago-defeats-go-ke-jie-again.html。

- 34. Paul Mozur， “北京希望到2030年实现人工智能‘中国制造’，”《纽约时报》，2017年7月20日。https://www.nytimes.com/2017/07/20/business/china-artificial-intelligence.html。

- 35. Silver D.、J. Schrittwieser、K. Simonyan、I. Antonoglou、A. Huang、A. Guez、T. Hubert、L. Baker、M. Lai、A. Bolton、Y. Chen、T. Lillicrap、F. Hui、L. Sifre、G. van den Driessche、T. Graepel 和 D. Hassabis， “无需人类知识即可掌握围棋游戏，”《自然》 550（2017年）：354–359页。

- 36. David Silver、Thomas Hubert、Julian Schrittwieser、Ioannis Antonoglou、Matthew Lai、Arthur Guez、Marc Lanctot、Laurent Sifre、Dharshan Kumaran、Thore Graepel、Timothy Lillicrap、Karen Simonyan、Demis Hassabis，《通过自我对弈与通用强化学习算法掌握国际象棋和将棋》，arXiv:1712.01815（2017年）。

- 37. Harold Gardner，《心智的框架：多元智能理论》，第3版（纽约：Basic Books，2011年）。

- 38. J. R. Flynn， “14个国家的智商大幅提升：智力测试真正衡量的是什么，”《心理学公报》 101，第2期（1987年）：171–191页。

