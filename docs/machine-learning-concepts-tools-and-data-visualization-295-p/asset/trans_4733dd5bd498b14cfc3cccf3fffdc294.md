

Watson 的技术水平足以分析非结构化数据，例如图片、视频、MRI 数据和患者移动轨迹，这些数据以前是难以分析的。

### Watson 是如何工作的？
在专家的指导下，Watson 收集开发基于语料库知识所需的信息。因此，收集此类语料库的任务是将相关文献引导至 Watson。为了构建语料库，需要人工干预来查看收集的信息，并丢弃过时、评估不佳或与领域相关性较低的信息。

这被称为内容策划（content curation）。为了让 Watson 正确学习，必须有效地执行内容策划。为了学习解释大量信息，需要专家培训。为了获得学习最优性能和搜索模式的能力，Watson 成为专家的伙伴，并通过机器学习进行自我训练。机器学习是人工智能用于实现类人推理的应用，它始于 1984 年 Douglas Lenat 发起的的人工智能项目 CYC。

例如，取“每棵树都是植物”和“植物最终会死亡”这两个陈述。
当被询问树是否死亡时，推理引擎（Inference Engine）可以得出确定结论并正确回答。专家以问/答格式将训练数据上传到 Watson，这些数据被用作验证数据。

图 4-6 显示了人工智能中的基于知识的代理。

![](img/3c3c87d78136583581b0cf0620f5ae66_75_0.png)

图 4-6 人工智能中的基于知识的代理

专家定期审查用户与 Watson 之间的交互，并向系统反馈以提高 Watson 解释信息的能力。这些规则是人工添加的。制定涵盖世界上所有差异知识的规则是不行的。但在 Watson 的情况下，这是通过自然语言处理自动完成的。毕竟，Watson 是在新信息发布时不断更新自身的系统，并通过处理语言来学习新事物。

## 4.3 练习题
Q1. 什么是 AlphaGo？
Q2. 描述作为 AlphaGo 算法实现的蒙特卡洛树搜索 (MCTS)。
Q3. 描述 AlphaGo 工作流 (Pipeline)。
Q4. 描述 IBM 实现的人工智能系统 Watson。

# 第 5 章
## Microsoft Azure Machine Studio

## 5.1 Microsoft Azure Machine Studio 简介
Azure 是微软的一款云计算平台，自 2010 年起投入服务。继 2011 年推出 PaaS 后，又于 2013 年推出了 IaaS 服务。在 Azure 平台提供的 600 多项服务中，本书将重点介绍其中之一：Azure Learning Studio。机器学习有很多开源库和工具，为什么要使用 Azure Learning Studio 呢？答案在于 Azure Learning Studio 解决了以下问题：

- 计算资源缺乏灵活性
- 配置用于学习的基于 GPU 的环境困难
- 学习工具的安装和设置困难
- 实验记录和版本控制困难

图 5-1 显示了 Azure Machine Learning 工作流。用户可以利用 Azure 平台实现云端数据收集和管理，并使用 Machine Learning Studio 轻松创建预测模型和构建 Web 服务。与现有云平台和机器学习工具不同，它提供了一个考虑用户便利性的易访问的 GUI 环境。图 5-2 显示 Azure ML Studio 可以以拖放的形式轻松创建块，这与传统的机器学习工具和库不同。此外，用 R 和 Python 语言编写的脚本可以插入并在块中使用。

## 机器学习：概念、工具和数据可视化
### Azure Machine Learning：基本工作流
从数据构建模型并使机器学习解决方案运行化

| 数据收集与管理 | 机器学习服务 | 嵌入式 ML 模型 |
| :--- | :--- | :--- |
| Blobs 与表格 (Azure Storage) | ML STUDIO | |
| Hadoop (Azure HDInsight) | Web 服务 | |
| 关系型数据 (Azure SQL Database) | 输出可以定期运行并连接数据库的 Web 服务 | 为应用或网站添加智能，或在 BI 工具中提供洞察 |
| 海量数据存储 (Azure Data Lake) | 创建机器学习模型 | |

**图 5-1** Azure Machine Learning 工作流
![](img/3c3c87d78136583581b0cf0620f5ae66_80_0.png)

**图 5-2** Azure Machine Studio 实验画布

得益于其简单的结构，所有技能水平的用户都可以轻松创建和分发预测模型。结果可以可视化。图 5-3 显示了 Azure AI Gallery，用户可以在那里尝试其他用户开发的项目，或将其导入到自己的项目中进行修改。此外，用户可以在 Facebook 或 Twitter 等社交媒体上发布在 Gallery 中共享的项目，以寻求建议。

图 5-4 显示了 Azure Machine Learning 的整体能力。Azure Machine Learning 支持输入、输出和可视化，并准备了数据科学家常用的标准机器学习算法。用户可以开发并部署以下步骤：

Microsoft Azure Machine Learning Studio 65
![](img/3c3c87d78136583581b0cf0620f5ae66_81_0.png)

图 5-3 Azure AI Gallery
![](img/3c3c87d78136583581b0cf0620f5ae66_81_1.png)

图 5-4 Azure Machine Learning Studio 图解
(1) 导入数据：用户可以获取用于模型训练的数据并将其导入 Azure 云进行多种用途。
(2) 数据预处理：用户可以对数据数据的情况进行预处理。
(3) 特征选择：为了训练模型，用户可以提取特征。
(4) 评估：训练后对模型进行评估。
(5) Web 服务部署：训练好的模型可以通过服务发布。

## 5.2 Microsoft Azure Learning Studio 注册
访问 https://studio.azureml.net/ 并点击图 5-5 中框出的“Sign up here”链接。
![](img/3c3c87d78136583581b0cf0620f5ae66_82_0.png)

将弹出一个窗口，如图 5-6 所示。用户可以免费进入 8 小时，但建议使用 Microsoft 账户创建工作区来存储项目和实验数据。

![](img/3c3c87d78136583581b0cf0620f5ae66_83_0.png)

图 5-6 Azure Learning Studio 选择窗口

如果登录成功，你将看到图 5-7 所示的工作区。
![](img/3c3c87d78136583581b0cf0620f5ae66_83_1.png)

图 5-7 Azure Machine Studio 工作区

## 5.3 Microsoft Azure Machine Studio 功能介绍
点击图 5-8 中的“+ NEW”显示工作区功能

![](img/3c3c87d78136583581b0cf0620f5ae66_84_0.png)

点击“+NEW”按钮查看图 5-9 所示的“DATASET”、“MODULE”、“PROJECT”、“EXPERIMENT”和“NOTEBOOK”功能。“DATASET”允许用户将实验数据文件上传到 Azure 云，供个人账户使用。用户还可以通过插入包含 Python 语言编写模块的压缩包 (.zip) 来 Python 脚本模块化。

![](img/3c3c87d78136583581b0cf0620f5ae66_84_1.png)

图 5-10 中的“MODULE”功能可以通过插入包含 R 语言编写脚本的压缩包 (.zip) 来 R 脚本模块化。用户还可以导入并使用微软在 Gallery 中发布的各种 R 语言编写的模块示例。

