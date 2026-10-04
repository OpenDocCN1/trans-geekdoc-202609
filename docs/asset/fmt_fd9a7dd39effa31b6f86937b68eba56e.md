
下一步是人工智能（AI），人们可能熟悉的是图灵测试，该测试由艾兰·图灵（Alan Turing, 1950）著名地提出。通过测试的早期尝试包括 `ELIZA`，这是 MIT 在 1964 年至 1966 年间创建的一个聊天机器人（Agassi & Wiezenbaum, 1976）。从那以后，尤其是近年来，机器学习和人工智能大幅增长。2018 年，Google 展示了其基于语音的 AI 助手，它可以用来给美发店打电话、与员工交谈并预约发型，而对方并没有意识到正在与机器对话。此类问题很重要，但关于 AI 以及如何在本文范围之外证明它的挑战性讨论超出了本书的范围。尽管如此，机器学习在网络安全方面有一些有趣的应用。Dutta、Joyce 和 Brewer (2018) 探索了如何利用聊天机器人帮助网络安全从业人员做出决策以及如何应对事件。这背后的逻辑是，网络事件可能是高压力情况，网络安全专业人员必须在短时间内处理并采取大量信息。攻击者试图让目标做出快速、冲动的决策（认知吝啬者/cognitive miser），而不是仔细考虑可用信息并做出理性决策（天真科学家/naive scientist）。这样聊天机器人可以在决策过程中产生一些缓冲，并帮助网络安全专业人员区分关键点以及如何做出适当决策。人工智能的收益不仅限于网络安全专业人员。有人认为，`ChatGPT` 这样的 AI 软件通过承担某些黑客的技术方面使网络犯罪“民主化”，从而降低了参与门槛（Munchester, 2022）。正如本书所述，黑客行为本身并非犯罪活动。然而，担心 AI 工具可能让人们在不完全了解自己所做什么的情况下无意中参与非法活动是合理的。此外，AI 可用于创建深度伪造（deepfakes）。这些是 AI 生成的虚假图像和视频，但通常看起来非常逼真。一些著名的深度伪造视频案例包括前美国总统巴拉克·奥巴马描述唐纳德·特朗普为“彻头彻尾的混蛋”，或者《游戏之王》中的琼·雪为其被认为糟糕的向粉丝道歉（Sample, 2020）。在《不要相信任何人：深入深度伪造世界》（Trust No One: Inside the World of Deepfakes）中，Grothaus (2021) 强调了深度伪造带来的风险，概述了一个人们日益难以区分虚构与现实的世界。

# 新兴技术与未来方向

网络攻击者利用深度伪造（deepfakes）进行各种活动无疑具有巨大的潜力，包括制造虚假新闻、生成钓鱼邮件，并通过利用语音聊天机器人等技术实施其他直到目前为止需要人类攻击者才能完成的社会工程形式。这些问题促使 Guitton (2020) 等研究人员将人工智能识别为一种新兴且可能重大的网络安全风险。

目前已发现具体的案例，证明了机器学习和人工智能可以被攻击者利用。例如，Baki、Verma、Mukherjee 和 Gawali (2017) 演示了这些技术在电子邮件伪装中的作用。这指的是攻击者获取电子邮件账户的访问权限（例如在第3章中讨论的涉及 Anonymous 和 HBGary 的事件），然后利用该账户内的邮件来学习该账户所有者的写作风格。攻击者还可以获取有关目标联系人的信息，以及之前对话发生的背景情况。这使得攻击者能够发送伪装成目标的新邮件，用于多种目的，包括进行通信、造成扰乱和不和谐、发送钓鱼邮件以及传播恶意软件。这种攻击完全可以通过人工努力完成，但这项任务可以通过人工智能在规模得多的水平上完成。换句话说，人工智能可能扫描目标所有的电子邮件和其他电子通信内容（如社交媒体帖子），并快速生成一封以目标风格编写的虚假邮件。Baki 等人 (2017) 测试了伪装邮件，发现参与者区分真伪伪装邮件的能力接近其真实能力水平。此类研究凸显了个人和组织在尝试安全地使用计算机系统时所面临的不断演变的挑战。结合深度伪造等人工智能赋能的技术，攻击者手中拥有了越来越多的工具，用来寻找他们的目标。

大数据、机器学习和人工智能也被用于理解和定位黑客。正如 Lima 和 Keegan (2020) 所指出的，在线黑客论坛和社交媒体账户产生了大量文本，还有关于黑客信息以及已发现的安全漏洞的共享。这些数据量远超任何人类在防止攻击的极短窗口内能够以现实方式进行监控和审查。此外，从理论上讲，大数据和机器学习方法可以用于识别计划进行攻击的个人或群体。此外，该方法还可以用于更好地理解黑客群体内部的结构和流程。Lippmann 等人 (2016) 在其对社交媒体和 Reddit 帖子的研究中尝试了这一点。他们的分析支持了 Benjamin、Zhang、Nunamaker 和 Chen (2016) 的早期研究，他们认为黑客社区内部往往存在领导者和有影响力的人物。这与黑客群体自身的声称形成对比——此类群体通常会说他们没有领导者（Olson, 2012）。最近，Marin、Shakarian 和 Shakarian (2018) 证明机器学习可以用于识别暗网论坛上的黑客。然而，Lima 和 Keegan (2020) 指出了在使用大数据和机器学习识别和预测黑客行为时面临的若干挑战。首先，黑客词汇频繁变化（如第3章中讨论的），不同论坛之间使用的表达方式存在差异。其次，缺乏“真值”（ground truth）数据集。在人工智能的背景下，真值指的是分配给训练机器学习模型的数据集中的标签，用于将新输入连接起来并验证其性能（Levowitz, Levina, & Lifshitz-Assaf, 2021）。换句话说，真值是通过直接观察和证据验证的已知真实、准确的信息。获取真值在许多领域都是一项挑战，但在涉及黑客时可能尤为困难。毕竟，这是一个往往倾向于掩盖身份和动机的群体。这并不是局限于机器学习的问题。例如，媒体对网络犯罪和战争的报道也面临着挑战（Lee, 2015），特别是在验证事件是否发生，以及如果发生了，究竟发生了什么方面。情报机构和其他政府机构也可能在防御性和进攻网络安全领域使用人工智能，但并不意外的是，关于此类实践的信息有限。

## 参考文献

- Adderij, J., & Kelley, K. (2018). Big Data in Psychology: A Framework for Research Advancement. American Psychologist, 73(7), 899–917. doi:10.1037/amp0000190
- Agassi, J., & Wiezenbaum, J. (1976). Computer Power and Human Reason: From Judgment to Calculation. Technology and Culture, 17, 813. doi:10.2307/3103715
- Baki, S., Verma, R., Mukherjee, A., & Gnanali, O. (2017). Scaling and Effectiveness of Email Attacks: Exploiting Natural Language Generation. Paper presented at the Proceedings of the 2017 ACM on Asia Conference on Computer and Communications Security, Abu Dubai, United Arab Emirates. https://doi.org/10.1145/3052973.3053033
- Bartoletti, M., Pes, B., & Serusi, S. (2018). Data mining for detecting Bitcoin schemes. Paper presented at the Crypto Valley Conference on Blockchain Technology (CVCT), Zug, Switzerland, jun 20–22.
- Benlouzid, B. (2019). To predict and manage. Data & Society, 6.
- Benjamin, V., Zhang, B., Nunamaker, J., & Chen, H. (2016). Examining participation in hacker communities. Journal of Information Systems, 33(2), 482–510. doi:10.1177/0742221
- Browning, O. (2023). What is generative AI? Scientific American, 7.
- De Viga, A., Astakhova, L., & Herselman, M. (2020). Defining organisational culture. Computers & Human Behavior, 92
- Liu, Z., Tong, W., & Su, Y. (2020). Interaction effects of eye, word frequency, and probability to saccade length in Chinese reading. PeerJ, 8, e860, doi:10.7717/peerj.8860
- Guitton, M. (2020). AI as an emergent and potentially major cybersecurity risk. Cyber Security.
- Lee, D. E. (2015). The challenge of reporting on cyberattack.
- Li, X.-S., Fan, Z.-n., Ren, Y.-Y., & Yang, R. (2021). Classification of Eye Movement and Its Application in Driving Based on a Refined Process and Machine Learning. IEEE ACCESS, doi:10.1109/ACCESS.2021.31596
- Lima, A., & Keenan, B. (2020). Challenges of using learning algorithms for security: a study of threat-classification models applied to social media data.
- Lippmann, R. P., Campbell, M. W., Wells-Fahy, D. J., Mensch, A. C., Zeno, G. M., & Campbell, J. P. (2016). Finding Meaningful Discussions in Social Media.
- Marin, E., Shakarian, J., & Shakarian, P. (2018). Mining key-hackers on darkweb forums. Paper presented at the 18th International Conference on Data Intelligence and Security (ICDIS).

## 新兴技术与未来方向

Masling, J. M. (1966). 受试者与心理学者的相关行为及其对心理数据的影响。内布拉斯动机座讨会，14, 67–103。

Muncaster, P. (2022). 专家警告 `ChatGPT` 可能使网络犯罪民主。检索自 https://www.infsecurity-magazine.com/news/experts-warn-chatgpt-democratize/

Nam, Y., Hong, U., Chung, H., & Noh, S. R. (2022). 反映网络晕症的眼动模式：来自虚拟现实游戏不同模式的证据。Psychol Behav Soc Net, 255(2), 135–139. doi:10.1089/cyber.2021.0167

Norman, K. L. (2017). 心理学：人机交互导论（第二版）。剑桥与纽约：剑桥大学出版社。

Nurse, J. R. C., Erola, A., Gibson-Robinson, T., Goldsmith, M., & Creece, S. (2016). 用于刻画和度量在线人格特性的分析。Security Informatics, 5(1), 3, doi:10.1186/s13638-016-0028-1

Olson, P. (2012). 我们是匿名。纽约：Back Bay Books。

Orne, M. T. (1962). 论心理实验的社会心理学：参考需求特征及其意义 [美国心理协会 doi:10.1037/h004422]。 检索

Sample, I. (2020). 什么是深度伪造——你如何识别它们？ 检索自 https://www.theguardian.com/technology/2020/jan/13/what-are-deepfakes-and-how-can-you-spot-them

Shang, T., Lu, H., Wu, P., & Wei, Y. (2021). 熟悉与不熟悉司机对高速隧道出口出口标志的眼动评估。Int J Environ Res Public Health, 18(13), doi:10.3390/ijerph181336280

Turing, A. M. (1950). 计算机器与智能。Mind, 49, 433–460。

Vasek, M., Liu, X, Li, Y, Xu, Y, Xia, M., . . Wang, J. (2022). 分析比特币庞局计划生态系统。金融加密货币研讨会论文。

Zhang, D., Liu, X., Xu, L., Li, Y, Xu, Y, Xia, M., . . (2022). 使用判别性眼动特征对抑郁症与对照组进行有效区分。Journal of Affective Disorders, 307, 237–243. doi:10.1016/j.jad.2022.03.077

## 结论与建议

### 网络安全中的机遇与挑战

人类是复杂的。技术通过提供以前所未实现的通信方式，为预测行为增加了进一步的不确定性。这创造了新的机会和挑战，其程度尚未被完全理解。解决这个问题的一种方法可能是考虑 Suler (2004) 提出的根本问题——互联网是增强了还是了？互联网提供的自由和匿名性是允许我们更开放地表达自我，还是让我们变成了一个不同的人？这涉及到将网络犯罪分类为“网络赋能型”或“网络依赖型”。网络赋能型犯罪涉及个人利用技术实施在离线也可以实施的犯罪，而网络依赖型犯罪则是只能通过使用技术才能实施的犯罪。黑客属于后者，但关于它是否真的是一种新行为仍存有争议。像 Jenny Radcliffe (Radcliffe, 2023) 等工程师的故事清楚表明，在互联网广泛普及之前，他们已经在进入某些场所方面掌握了高超技能。计算机系统和互联网提供了新的探索空间。

来自网络犯罪内部和外部的心理学研究可以为人们在使用社会技术系统时为何表现出特定的行为，以及如何改变有害行为提供一些见解。如果说心理学研究能解决所有与网络犯罪相关的问题就过于乐观了，但我们认为，在预防网络犯罪中更多利用心理学方法具有重大益处。这将有助于转变“人类是网络安全中最薄弱环节”的观点，而这并不是与人们接触以理解和改变行为的有效方式。增加心理学在网络安全中的作用也可能有助于对社会工程学风险产生更多关注和理解。伦理社会工程工程师提供了关于如何减轻或防止此类犯罪行为的见解，但到目前，这些理解很大程度上来自媒体来源和个人陈述。我们呼吁开展更多实证研究，与社会工程人员合作，以开发改进网络安全实践的证据基础。我们认为学术研究是一个遵循这一调查方向的有力立场，因为我们遵循严格的标准，并且在心理学等学科中调查受访者可能犹豫的行为方面具有经验。

网络犯罪分子使用的动机和技术是多样化的，并与他们的自我认同感有关。黑客是“在母亲地下室工作的青少年”的刻板印象是不准确的，而且对于分析攻击者是没有效率的。互联网的本质和数字技术演进的速度使我们对此类假设保持谨慎。这就是为什么需要理解数字技术的独特特征，以及它们如何影响网络安全中的行为和决策。行为改变和预防不仅需要考虑网络犯罪的目标，还需要考虑发起者。对计算系统的新奇以及对测试可能界限的渴望似乎是许多参与黑客活动的人的起点，但这些特征本身并不是负面特征。鼓励这些个人从事网络安全领域的合法职业，可以为社会抵御网络安全威胁提供所需的资源和技能。

在线环境也为行为和预防策略提供了独特的机遇。例如，监控员工在工作场所对计算机系统使用情况，这提供了提供个性化、实时行为改变干预的机会。然而，这些可能性也引发了关于如何使用此类信息的争论，以及个人是否会因为成为网络犯罪受害者而受到不公正的处罚。书中反复出现的一个主题是，许多网络攻击的执行异常地简单，以及社会工程人员和其他攻击者为了确保系统安全而使用的复杂的心理操纵。此外，可以认为网络安全行为改变和预防策略没有充分利用心理学文献提供的证据基础。这并不意味着在其他领域成功的行为改变和预防策略同样适用于网络安全——互联网的本质和数字技术演进的速度使我们对此类假设保持谨慎。这就是为什么需要理解数字技术的独特特征，以及它们如何影响网络安全中的行为和决策。行为改变和预防不仅需要考虑网络犯罪的目标，还需要考虑发起者。对计算系统的新奇以及对测试可能界限的渴望似乎是许多参与黑客活动的人的起点，但这些特征本身并不是负面特征。鼓励这些个人从事网络安全领域的合法职业，可以为社会抵御网络安全威胁提供所需的资源和技能。
