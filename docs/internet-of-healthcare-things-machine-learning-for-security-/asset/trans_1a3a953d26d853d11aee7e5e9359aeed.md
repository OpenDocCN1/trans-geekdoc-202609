

# 104 医疗健康物联网

## 5.4 在 IoHT 数据集上进行主题建模

健康监测是政府和非政府组织面临的挑战性问题之一。在大范围内实施公共健康监测需要大量的人力物物资源。数字平台和数字资源为开发健康监测系统提供了解决方案。数字解决方案具有成本效益且资源利用率高。数据分析是解决方案解决方案，可用于开发公共健康监测系统。面向所有人的数字健康监测平台是政府提供低成本、人人享医疗解决方案的热门议程之一。技术促进了数字解决方案以及个人健康记录的低成本存储。这些信息可用于监测、教育和决策 [2, 10]。

主题建模算法通过词汇分析从给定文档中发现主题结构。执行主题建模不需要对文本进行标注和标记。在主题建模中，源自狄利克雷文本的是词汇分布的表示。本研究应用了狄利克雷分配（LDA）一种概率主题建模算法，来寻找与医疗健康物联网相关的主题。使用 LDA 模型发现相似的观测值，并将 IoHTs 数据集中提出的词汇分组为主题 [4]。选择来自各种来源的新闻数据作为信息源执行主题建模，以将文本归类为潜在主题。对数据集进行预处理，以删除超链接等不需要的信息。删除停用词并使用词形还原法将变形词转换为词根形式。将预处理后的文本传递给 LDA 模型，对给定文本应用词袋模型（bag of words）方法以派生词向量。给定文本的潜在主题概率分布表示 [12, 16]。

IoHT 数据集上的主题建模
执行医疗保健 初创市场 nascom 创新支持医疗专家 西门子
主题 #1: 物联网 iot 健康 方式 启动 数字 业务 卡
主题 #2: 物联网 iot 医疗 健康 影响 监测 远程 患者
主题 #3: 健康 iot 十亿 市场 行业 全球 人工智能 互联网 合作
主题 #4: 物 健康 技术 业务 
主题 #5: covid 设备 健康 安全 社会 规则
主题 #6: 设备 健康 智能 使用 新 基于
主题 #7: 物联网 健康 covid 大疫情 冠状病毒 电信 未来
主题 #8: 健康 智能 安全 年度 网络 技术 百比 最后 组织 泄露
主题 #9: 物联网 健康 iot 全球 顶尖 市场 需求 

图 5.5 在 IoHT 数据集上进行主题建模。

# IOHT 趋势与公众情感分析 105

**表 5.2** 从 LDA 主题模型输出派出的可能的抽象主题标签。

| 可能的主题标签 | LDA主题模型输出 |
| --- | --- |
| 医疗健康初创企业 | Topic #0: thing healthcare internet startup market Nasscom innovation support healthineers siemens |
| 数字 IoHTs 业务 | Topic #1: internet thing IOT healthcare launch digital business risk care |
| IoHTs 对医疗和家庭的影响 | Topic #2: thing internet medical IOT healthcare home impact monitoring patient |
| IoT 健康与人工智能 | Topic #3: healthcare IOT billion market industry global artificial intelligence CIO |
| IoHTs 的未来与冠状病毒 | Topic #4: internet IOT hospital future help life coronavirus business make |
| IoT 设备在新冠19 中的角色 | Topic #5: covid device post help security play societal role |
| IoT 设备与健康 | Topic #6: internet device healthcare smart care use IoT based |
| IoHTs 与新冠19 大流行 | Topic #7: internet thing healthcare covid IoT news coronavirus telecom future |
| 医疗安全 | Topic #8: healthcare market security cyber percent last organization breach |
| 全球市场中的 IoHTs 技术 | Topic #9: thing internet healthcare IoT technology top player market news |

IoHTs 数据集通过 LDA 主题建模输入并如图 5.5 所示。这些主题显示了与 IoHTs 相关新闻的趋势。最热门的主题与医疗、初创企业、创新、医院和新冠19有关。表 5.2 列出了可能的抽象主题，这些主题派生自 LDA 模型的结果。这些抽象主题代表了潜在的主题标签。表 5.3 列出了 LDA 主题模型输出及相应的可能主题标签。最热门的是医疗健康物联网初创企业、数字 IoHTs 业务、IoHTs 对医疗和家庭的影响、IoT 健康与人工智能、IoHT 未来与冠状病毒、IoT 设备在新冠19 中的角色、IoT 设备与健康、IoHTs 与新冠19 大流行、医疗安全

# 106 医疗健康物联网

在新冠肺炎期间在 IoHT 数据集上进行主题建模
主题 #0: 健康 物 iot 行业 智能 连结 转型 生命
主题 #1: iot 最佳 方法 案例 使用 应用 健康 增长 业务
主题 #2: 互联网 iot 云 家 揭示 市场 业务
主题 #3: iot 物 covid 健康 电信 世界 银行 关键 社会
主题 #4: iot covid 大流行 新 世界 领先 电信 医疗 健康
主题 #5: 互联网 服务 物 风险 cio 设备 增长 帮助 医疗
主题 #6: iot 未来 技术 主要 预测 十亿 设备 医疗 速度
主题 #7: 健康 安全 市场 无 互联网 冠状病毒 医疗
主题 #8: iot 互联网 健康 帮助 冠状病毒 生命 智能 十亿
主题 #9: 物 健康 健康 iot 未来 初创企业 创新 支持 医疗专家

图 5.6 在新冠肺炎期间在 IoHT 数据集上进行主题建模。

表 5.3 新冠肺炎期间从 LDA 主题模型派出的可能的抽象主题标签。

| 可能的主题标签 | 新冠肺炎期间的 LDA 主题模型输出 |
| --- | --- |
| IoHTs 与人工智能 | Topic #0: healthcare thing iot industry intelligence artificial connected transforming life |
| IoHTs 业务 | Topic #1: iot best approach case use apply healthcare grow business |
| 新冠19 中的 IoT 业务 | Topic #2: internet iot cloud make home unveils market business |
| IoT 与新冠19 | Topic #3: iot thing covid healthcare telecoms banking crucial society |
| IoHTs 与大流行 | Topic #4: iot covid pandemic new world lead telecom medical health |
| IoT 服务与医疗行业 | Topic #5: internet service thing risk cio device growth help medical |
| IoT 未来技术 | Topic #6: iot future technology major prediction billion device medical speed |
| 新冠19 中的安全 IoT | Topic #7: healthcare security market nothing internet coronavirus medical |
| IoHTs 在冠状病毒中帮助生命 | Topic #8: iot internet healthcare help coronavirus life smart billion |
| IoHTs 的未来初创企业 | Topic #9: thing internet healthcare iot future startup innovation support healthineers |

# IOHT 趋势与公众情感分析 107

以及全球市场中的技术。IoHTs 和新冠19 在与 IoHTs 的新新闻中被高度讨论。主题“IoHT 未来与冠状病毒”、“IoT 设备复原新冠19”以及“IoHTs 与新冠19 大流行”显示，在流行病期间，IoHTs 发挥了重要作用。“医疗安全”主题显示 IoHTs 的安全性是全球范围内的一个重要议题和需求。

LDA 主题建模被应用于新冠肺炎期间的 IoHT 数据集。新闻数据集收集自 2020 年 3 月到 2020 年 11 月，用于分析 IoHTs 之间的相关性。图 5.6 显示了新冠肺炎期间 IoHT 数据集上 LDA 主题建模的输出。主题派生自 LDA 模型。表 5.3 列出的可能标签派自 LDA 模型输出。主题“新冠19 中的 IoT 业务”、“IoT”、“IoHTs 与大流行”、“IoT 服务与医疗行业”以及“IoHTs 在冠状病毒中帮助生命”显示 IoHTs 是全球热门话题，且在新冠19 大流行期间获得了了重要性。

## 5.5 在 IoHTs 数据集上进行情感分析

情感分析在自然语言处理（NLP）领域被称为意见挖掘。它用于研究给定文本中的主观信息。基于词汇和情感的 VADER（价值感知情感推理词典）、Text Blob 和深度学习 LSTM 模型已用于许多领域的情感取向分析。VADER 是一种为情感分析设计的基于规则的情感分析工具。情感推理词典（VADER）是一种基于词典和规则的情感分析工具，用于分析文本信息中表达的情感 [2, 7]。它通过定性和定量方法强调情感强度，适用于分析来自微博客平台的短文本 [5]。对 IoHTs 的情感取向及其应用进行情感分析，以了解用户如何应对最新进展。最近的疫情对我们现有的医疗基础设施产生了巨大影响，这些基础设施不足以应对传染或其他疾病的突然激增。数字健康基础设施是需要的

