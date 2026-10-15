
身份管理活动。
聊天机器人的对话预期。
处理意外且经常敏感的信息。

### 21.6.4 基于实体的隐私保护

提供“实体”对于个性化聊天机器人至关重要，同时还有“意图”和“话语”。实体对应于特定领域中使用的术语。在客户端/应用端，一个名为隐私保护聊天模块（PPCM）的模块实现了基于实体的方法。理解原始聊天机器人材料以及聊天机器人平台所采用的底层 NLP 策略对于 PPCM 设计是必要的。为了解决用户的聊天隐私问题，采用了基于过滤和转换的隐私保护方法的组合。PPCM 使用的文本提取方法与聊天机器人的 NLP 引擎相同。然后查询会被过滤或删除，以使其不会提交到后端 NLP 引擎，然后用户会收到适当的通知。为了使聊天机器人 NLP 引擎将转换后问题的用户情感分类为“中性”，PPCM 必须将原始用户查询修改为语义相同但更“中性”的响应。

### 21.6.5 可搜索加密

使用一种称为可搜索加密（SE）的方法，可以在允许服务器端搜索（云）的同时保护敏感数据（Jayati, 2022）。服务器可以使用 SE 在不泄露任何明文数据的情况下搜索加密数据。可搜索对称加密（SSE）和带关键字搜索的公钥加密（PEKS）是 SE 的两个主要子领域。SE 由以下多项式时间随机算法组成，如图 21.6 所示。

深度学习医疗聊天机器人的架构以及安全性如下所示，见图 21.7。

- KGEN(1^k) 输出一对公私钥：(A_pub, A_priv)。
- SENC(A_pub, w, m) 在实体 w 和公钥 A_pub 下输出聊天消息 m 的可搜索加密 s_w。
- DOOR(A_priv, w) 输出允许按实体 w 搜索的陷门 t_w。
- TEST(A_pub, s_w, t_w') 如果 w = w' 则输出消息 m。

图 21.6 SE 的多项式随机算法

![](img/a2fc2296b12812e9151e817bff1de16d_452_0.png)

图 21.7 具有安全性的深度学习聊天机器人框架

## 21.7 问题与未来研究趋势

每项技术都有优点和缺点。聊天机器人也是如此。它们并不总是完美运行。以下是它们带来的危险列表。

### 21.7.1 部分检查与评估

许多医疗专业人士认为聊天机器人可以帮助自我诊断轻微疾病。该技术尚未先进到足以完全取代医生就诊。它们无法判断一个人是更随意还是更严肃地说话。此外，它们在每次互动中保持相同的语气方面存在困难。

### 21.7.2 不可靠的解释

如果 AI 聊天机器人无法理解确切情况，患者可能会遭受严重伤害甚至死亡。选择错误药物的后果可能十分灾难性。即使 AI 聊天机器人服务的使用并不常见，患者也经常因医疗保健系统的缺陷而受苦。

### 21.7.3 数据泄露与用户隐私

并非所有终端用户都觉得向机器人提供其私人信息是安全的。AI 也需要训练，这涉及随着新场景出现而获取新数据。此类数据可能被黑客攻击，导致隐私泄露。这目前是手头最重要的一个问题之一。

### 21.7.4 缺乏人际互动

无论自动化速度有多快，人际互动的沉浸式乐趣始终优于机器人对话。一个人总能参与多个信息线程，提供最终更有益于患者的切题评论。

### 21.7.5 缺乏真诚情感与责任

同理心是沟通中至关重要的一部分，对于担心自己健康的人来说经常是必要的。当护理人员在医疗保健系统中表现出同理心时，患者会感觉更好，并且更愿意配合治疗。目前医疗保健中 AI 采用的是基于原则的方法，然而，支撑医患关系的基础信任的缺失仍然存在。

## 21.8 研究范围

现有的监管模式是为固定的医疗保健解决方案设计的，而 AI 则灵活且随时间演变。该领域的远见立法无疑会给法律团队带来更大的合规压力，但它也会带来急需的清晰度，降低合规企业的法律诉讼风险，并为 SaMD 制造商提供他们开发和充分利用医疗保健行业 AI 所需的保障。

未来的研究在三个关键领域尤其有帮助：诊断、医院外的患者参与以及心理健康。旨在不仅主动吸引而且吸引其护理中患者的聊天机器人提出了技术是否能进一步吸引患者以改善结果的问题。寻求心理健康咨询的人可以使用医疗保健对话聊天机器人作为讨论其情绪的论坛。如果患者的需要得到满足并且可以自动化，则可以避免医疗专家介入接管。

开发医疗保险聊天机器人可以产生巨大影响。没有人愿意处理保险公司、索赔或医疗费用。值得庆幸的是，医疗保健 AI 聊天机器人可以帮助完成这些任务。医疗保健聊天机器人能够验证当前保障范围、协助索赔申请并监控索赔进度。医疗 AI 系统还可以帮助医生处理计费问题和预授权程序。

## 参考文献

Abhinav, V., Krisstina, R., Vivek, E., & Yukti, S. (July 2021). Regulating AI in public health: Systems challenges and perspectives, ORF. Occasional Paper, 261.

Adamopoulou, E., & Moussiades, L. (2020a). An overview of chatbot technology. In Maglogiannis, I., Iliadis, L., Pimenidis, E. (Eds.), Artificial Intelligence Applications and Innovations. AIAI 2020. IFIP Advances in Information and Communication Technology, Vol. 584. Springer, Cham. doi: 10.1007/978-3-030-49186-4_31.

Adamopoulou, E., & Moussiades, L. (2020b). Chatbots: History, technology, and applications. Machine Learning with Applications, 2, 100006.

Ahmad, N. A., Che, M. H., Zainal, A., Abd Rauf, M. F., & Adnan, Z. (2018). Review of chatbots design techniques. International Journal of Computer and Applications, 181(8), 7–10.

Athota, L., Shukla, V. K., Pandey, N., & Rana, A. (2020). Chatbot for healthcare system using artificial intelligence. In 8th International Conference on Reliability, Infocom Technologies and Optimization (Trends and Future Directions) (ICRITO), 2020, pp. 619–622. doi: 10.1109/ICRITO48877.2020.9197833.

Ayanouz, S., Abdelhakim, B. A., & Benhmed, M. (2020, March). A smart chatbot architecture based NLP and machine learning for health care assistance. In Proceedings of the 3rd International Conference on Networking Information Systems & Security, 756, pp. 1–6.

Bagwan, F., Phalnikar, R., & Desai, S. (2021). Artificially intelligent health chatbot using deep learning. In 2nd International Conference for Emerging Technology (INCET), 2021, pp. 1–5. doi: 10.1109/INCET51464.2021.9456195.

Bhagwat, S., Bhagwat, V. A., & Gaikwad, V. (2019). Deep learning for chatbots, scholar works, link: “Deep learning for chatbots” by Vyas Ajay Bhagwat (sjsu.edu).

Bhattad, H., & Atkar, M. G. (2021). Review on different types of Chatbots. International Research Journal of Modernization in Engineering Technology and Science (IRJMETS), 3(5), 1347–1349.

Bhirud, N., Tataale, S., Randive, S., & Nahar, S. (2019). A literature review on chatbots in healthcare domain. International Journal of Scientific and Technology Research, 8(7), 225–231.

Cahn, J. (2017). Chatbot: Architecture, design and development, Senior Thesis, Department of Computer and Information Science, University of Pennsylvania.

Chopde, A., & Agrawal, M. (2022, June 19). Chatbot using deep learning. Available at SSRN: doi: 10.2139/ssrn.4140506.

Chuan, C. H., & Morgan, S. (2020). Creating and evaluating chatbots as eligibility assistants for clinical trials: An active deep learning approach towards user-centered classification. ACM Transactions on Computing for Healthcare, 2(1), 1–19.

Csaky, R. (2019). Deep learning based chatbot models. arXiv Preprint ArXiv:1908.08835.

Davenport, T., & Kalakota, R. (2019, June). The potential for artificial intelligence in healthcare. Future Healthcare Journal, 6(2), 94–98. doi: 10.7861/futurehosp.6-2-94; PMID: 31363513; PMCID: PMC6616181.

Dolianiti, F., Tsoupouroglou, I., Antoniou, P., Konstantinidis, S., Anastasiades, S., & Bamidis, P. (2020, October). Chatbots in healthcare curricula: The case of a conversational virtual patient. In International Conference on Brain Function Assessment in Learning. Springer, Cham, pp. 137–147.

Fadhil, A., & Schiavo, G. (2019). Designing for health chatbots. arXiv Preprint ArXiv:1902.09022.

Hasal, M., Nowaková, J., Ahmed Saghair, K., Abdulla, H., Snášel, V., & Ogiela, L. (2021). Chatbots: Security, privacy, data protection, and social aspects. Concurrency and Computation: Practice and Experience, 33(19), e6426.

Heinz-Uwe, D., & Dirk, T.W. (2021, November). Artificial Intelligence is forcing healthcare regulators to catch up and reimagine the regulation rule book. https://www.ey.com/en_lv/law/how-the-challenge-of-regulating-ai-in-healthcare-is-escalating.
