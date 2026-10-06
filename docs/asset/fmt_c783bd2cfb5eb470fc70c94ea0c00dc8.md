
虽然“仇恨言论”和“攻击性语言”在理论术语上有所不同，但许多研究和技术倾向于混淆完全不同类型的内容。仇恨言论对应攻击性语言，但并非所有的攻击性内容都一定对应仇恨言论。例如，`n**`、`b**ch` 和 `h**e` 等词用于日常对话、说唱歌曲和电影中。这些词虽然具有攻击性，但不能被归类为仇恨言论的元素。将仇恨言论与攻击性语言或反之视为单一实体，可能会导致仇恨言论检测工具和分类器产生误报，整体结果可能不准确。因此，通过引入能够定性区分 HSOL 的算法来开发和校准现有及新系统是至关重要的。

### 9.6.2 数据驱动系统中的隐含偏见

数据驱动系统由于其自动工作机制且缺乏人工检查和平衡，容易受到大量固有偏差的影响。深度学习数据驱动系统中的一些隐含偏见包括：

- **采样/选择偏差** – 当可用数据的样本量不充足时，它不能被认为是整个人群的真实代表。结果是，可能会对其产生误读。
- **过拟合/欠拟合偏差** – 向系统输入大量数据会导致从噪声和无用数据条中学习，这就是过拟合。相反，当向系统输入的数据较少时，无法获得准确的结果。这种情况被称为欠拟合。
- **测量偏差** – 当向系统输入具有定量不准确的数据时，就会测量偏差，即与测量和评估相关的误差。
- **回忆偏差** – 也称为假性偏差，这种偏差由于对主观信息的错误和不一致标记。
- **排除偏差** – 在数据输入系统之前，需要经过预处理阶段。这包括删除不必要的链接、URL、名称、空值等。然而，有时有用信息也会被过滤掉并排除在之外。这可能导致被排除的数据代表性不足。
- **种族偏差** – 当数据偏向特定人群（如某个种族或社区）时，就会发生种族或人口统计偏差。此类数据偏于识别特定人群，可能无法有效识别其他人群或种族。

深度学习工具也存在固有偏见，没有单一系统可以 100% 准确地识别 HSOL。当这些偏见随着时间的推移而放大时，它们不仅反映输出中，还会反映社会。

### 9.6.3 数据集和嵌入中的偏见

广义来说，偏见定义为对个人、群体、想法或事物的偏爱或反对——特别是以不公平的方式。深度学习模型的词嵌入和数据集是基于通用语言数据的，这些数据可能包含性别偏见、歧视性内容、个人观点等。因此，这些偏见可能会微妙或直白地出现在嵌入和数据集中。这种偏见可能会忽略某些 HSOL 内容，从而获得的结果可能无法反映真实情况。

# 用于仇恨言论和攻击性语言检测的深度学习

每一分钟，过滤仇恨和攻击性内容的任务都变得繁琐。现有的识别和分类深度学习系统无法跟上海量的推文、帖子和博客。因此，在恶意内容的生成与其检测之间存在巨大的延迟，这极可能给个人和整个社会带来困扰。近期，Meta 和 Twitter 等社交媒体巨头经常因未投入资金开发全面且快速的 HSOL（仇恨言论和攻击性语言）检测工具而饱受谴责。

## 9.6.6 隐私侵犯的潜在来源

从 Twitter 和 YouTube 等社交网络网站提取测试数据涉及隐私问题。这些数据在未获得内容创建者许可的情况下被收集和使用，因此可能构成侵犯隐私。此外，收集的原始、未处理的数据包含与用户相关的信息，如用户名、个人资料和帖子 URL 等。这些数据极其敏感，极易被未经授权的人员滥用。在使用这些数据开发数据集和深度学习之前，解决隐私问题并建立确保个人信息完整性的协议至关重要。

## 9.6.7 法律与意识形态挑战

最后，仇恨言论的检测和删除一直处于法律审查之下。尽管印度宪法及后续若干法律允许政府根据某些理由限制基本言论自由，但这些限制受到了某些团体的批评，认为其是对言论和表达自由的侵犯。将内容分类为仇恨言论和非仇恨言论也存在争议，因为社交媒体网站被指责以仇恨言论的名义抑制某些观点，同时允许同样包含针对性内容的反向观点。

## 9.6.8 代码混合语言

代码混合语言是指两种不同语言（无论相关或不相关）的混合。大多数用户在社交媒体平台上结合使用两种或两种以上语言，例如印地语-英语、泰米尔语-英语、印地语-泰米尔语、泰米尔语-马拉雅姆语等。使用包含单语言词库的传统数据集来识别 HSOL，对于生成包含代码混合语言帖子的结果可能并不完全准确。研究人员一直在为不同语言开发代码混合数据集，例如，最近开发了一个针对达罗毗达语言（泰米尔语和马拉雅姆语）的数据集$^{25}$

## 9.7 结论

我们已经看到 HSOL 内容产量的增加对个人及整个社会可能产生不利影响。因此，此类内容的检测变得至关重要。由于生成的数据量巨大，人工筛选不是一个可行的方案，必须采用自动化系统来实现快速识别和准确结果。近期已开发了多种浅层和深度学习模型，其中深度学习方法被证明显著优于浅层检测方法。多系列数据集、嵌入向量和分类器算法已开发并应用于深度学习模型中。然而，固有的偏见和其他若干其他挑战要求我们在现有工具的基础上进行构建，制定出更好的技术，以最大限度地减少结果中的偏差和不准确性。

HSOL 检测深度学习领域的持续研究已提出了现有模型的组合，以及额外的算法和概念。这些组合在受控条件下比传统工具产生了更准确的结果。此类研究需要扩展到包含更大的测试数据集集，以更好地代表整个群体并提供更宏观的图景。

- 1 Kumar, P. N. V. (2016). Growing Cyber Crimes in India: A Survey. 2016 International Conference on Data Mining and Advanced Computing (SAPIENCE). https://doi.org/10.1109/SAPIENCE.2016.768441
- 2 Jacobs, J. B., & Potter, K. (2000). Oxford University Press.
- 3 Davidson, T., Warmsley, D., Macy, M., & Weber, I. (2007). Automated Hate Speech Detection and the Problem of Offensive Language. Proceedings of the International AAAI Conference on Web and Social Media, II(1), 512-515. Retrieved from https://ojs.aaai.org/index.php/WSM/article/14955
- 4 Wang, W., Chen, L., Thurunarayan, K., & Sheth, A. P. (2014). Cursing in English on Twitter. Proceedings of the 17th ACM Conference on Computer Supported Cooperative Work & Social Computing, 415–424. https://cohesolar.libraries.wright.edu/knoesis/590
- 5 Zhang, Z., & Luo, L. (2019). Hate Speech Detection: A Solved Problem? The Challenging Case of Tail on Twitter. Semantic Web, 10(5), 925–945. https://doi.org/10.3233/sw-180338
- 6 Paul, C., & Bora, P. (2021). Detecting Hate Speech Using Deep Learning Techniques. International Journal of Advanced Computer Science and Applications, 12(2). https://doi.org/10.14569/jasc.2021.0120278
- 7 Hate Speech Detection Using Machine Learning – Data Analytics. Retrieved April 26, 2022, from https://vitalflux.com/hate-speech-detection-using-machine-learning/
- 8 Mikolov, T., Chen, Corrado, G., & Dean, J. (2013). Efficient Estimation of Word Representations in Vector Space. CoRR, abs/1301.3781.
- 9 Pennington, R., Manning, C., Pennington, J., Socher, R., & Manning, C. C. (2014). Glove: Global Vectors for Word Representation. In Conference on Natural Language Processing. Citeseer.
- 10 Alatawi, H. S., Alothali, A. M., & Moira, K. M. (2021). Detecting. White Supremist Hate Speech Using Domain Specific Word Embedding With BERT. IEEE Access, 9,10633–10674. https://doi.org/10.1109/access.2021.0120278
- 11 Types of Steps. Retrieved April 26, 2022, from www.analystics.com/types-machine-learning
- 12 Roy, P., Singh, A., Tripathi, A., & Das, T. (2022). Identifying Cyberbullying on Social Networking Platform Using Machine Learning. In Advances in Distributed Computing and Machine Learning (pp. 186–195). Springer.
- 13 Mandl, T., Rocha, S., Majumder, P., Patel, D., Dave, M., & Patel, A. (2019). Overview of HASOC at The 21st Forum for Information Retrieval. https://doi.org/10.18653/v1/n119-1144
- 14 Fanta, A., Djouvas, C., Chatzako, D., Leontidis, I., Blackburn, J., Stringhini, G., Akali, V., & Sirianos, M. (2018). AI Conference on Web and Social Media. Retrieved from www.aaa.org/ocs/index.php/IJCSM/ICWSM/1790
- 15 Zampieri, M, Malmasi, S., Nakov, P., Rosenthal, S., Farra, N., & Kumar, R. (2019). Predicting the Type and Target of Offensive Posts in Social Media. Proceedings of the 2019 Conference of the North. https://doi.org/10.18653/v1/5102
- 16 Deibert, O., Perez, N., Garcia-Pablos, A., & Cuadros, M. (2018). Hate Speech Dataset from White Supremacy Forum. Proceedings of the 2nd Workshop on Abusive Language Online (ALW2). https://doi.org/10.18653/v1/w18-5102
- 17 Tahmasi, N., & Rastagari, E. (2018). A Socio-Contextual Approach in Detection of Cyberbullying on Twitter. ACM Transactions on Social Computing, (1,4), 1–22. https://doi.org/10.1145/3290838
- 18 Bhattacharya, S., Kumar, R., Bhagat, A., Dawer, Y., & Ojha, A. K. (2020). Developing a Multilingual Annotated Corpus of Misogyny and Aggression. preprint arXiv:2003.07428.
- 19 Bohra, A., Vijay, D., Singh, V., Akhtar, S. S., & Shrivastava, M. (2018). A Dataset of Hindi-Mixed Social Media for Hate Speech Detection. Proceedings of the Second Workshop on Computational Modeling of People’s Opinions, Personality, and Emotions in Social Media. https://doi.org/10.18653/v1/w18-1105
- 20 Working of Convolutional Neural Network - Javatoint. Retrieved April 26, 2022, from www.javatoint.com/working-of-convolutional-neural-network-net

190

社交媒体中的网络犯罪

- 21 什么是门控循环单元 (GRU)？—— 来自 Techopedia 的定义。检索于2022年4月26日，来自 www.techopedia.com/definition/33283/gated-recurrent-unit-gru
- 22 Zhang, Z., Robinson, D., & Tepper, J. (2018). 使用基于卷积-GRU 的深度神经网络在 Twitter 上检测仇恨言论。《The Semantic Web》, 745–760. https://doi.org/10.1007/978-3-319-93417-4_48
- 23 Roy, P. K., Tripathy, A. K., Das, T. K., & Gao, X. Z. (2020). 使用深度卷积神经网络的仇恨言论检测框架。《IEEE Access》， 8, 204951-204962.
- 24 Henderson, P., Sinha, K., Angerald-Gontier, N., Ke, N. R., Fried, G., Lowe, R., & Pineau, J. (2018). 数据驱动对话系统中的伦理挑战。《2018 AAAI/ACM 人工智能、伦理与社会会议集》。https://doi.org/10.1145/3278721.3278777
- 25 Roy, P. K., Bhawal, S., & Subalalitha, C. N. (2022). 使用深度集成框架进行达罗维达语中的仇恨言论和攻击性语言检测。《Computer Speech & Language》，75, 101386.

# 10 用于司法鉴定与网络犯罪的语音处理与分析：系统性述评

Kruthika S. G 和 Trisiladevi C. Nagavi

## 目录

- 10.1 引言 ................................................................................ 192
- 10.2 司法鉴定的语音处理与分析通用模型 ................................ 193
- 10.2.1 声纹识别 ........................................................................ 194
- 10.2.2 语音增强 ............................................................................. 195
- 10.2.3 语音合成 .................................................................................... 196
- 10.3 挑战 .................................................................................................. 198
- 10.4 动机 ................................................................................................. 199
- 10.5 各应用 ......................................................................................... 199
- 10.5.1 社交媒体中的网络安全 .................................................................... 200
- 10.5.1.1 有效的社交媒体网络安全措施 .................................. 200
- 10.5.2 军事 .................................................................................................... 201
