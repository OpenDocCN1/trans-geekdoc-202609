

你已识别出潜在的“金矿”——产品中可能适合 AI 解决方案的数据丰富型问题。现在是时候为工作选择合适的工具了。可以将本部分视为你的 AI 工具箱，其中包含可应用于解决特定类型挑战的不同功能。就像木匠不会用锤子锯木板一样，你需要了解每种 AI/ML 技术的优势，以选择最合适的一种。

请记住，这并非要成为技术专家。而是要了解不同 AI/ML 方法的 `capabilities`，以便与工程团队进行有根据的对话，并做出战略性产品决策。

## 了解你的 AI/ML 工具箱：关键功能

以下是你可能会遇到的核心 AI/ML 功能的分解，以及它们如何应用于产品问题的示例：

### 分类：将事物归类

**它是什么：** 将数据分类到预定义的组或类别中。可以将其视为将邮件分类到不同的垃圾桶中。

**何时使用：** 任何时候你需要自动分类信息、标记数据，或在一组预定义选项之间做出决策。

**示例：** 

* **垃圾邮件过滤：** 将电子邮件分类为“垃圾邮件”或“非垃圾邮件”（`supervised learning` 的经典示例），如 [图 8-1](#c08.xhtml#c08-fig-0001) 所示。
* **客户支持工单路由：** 自动分类收到的支持工单（例如，“技术问题”、“账单问题”、“功能请求”），并将其路由到相应的团队。
* **文档类型识别：** 自动识别用户上传的文档类型（例如，发票、合同、简历、报告）。
* **图像标记：** 自动使用相关关键词标记图像（例如，“猫”、“狗”、“汽车”）。

![Figure 8-1: An illustration of a spam filter, a classic example of an AI classification model. The model analyzes an incoming email and automatically categorizes it as either 'spam' or 'not spam' based on learned patterns.](images/c08f001.png)

**Figure 8-1:** An illustration of a spam filter, a classic example of an AI classification model. The model analyzes an incoming email and automatically categorizes it as either 'spam' or 'not spam' based on learned patterns.

### 聚类：发现隐藏的群组

**它是什么：** 将相似的数据点分组在一起，*没有* 预定义的类别。就像是在你的数据中发现自然分组。

**何时使用：** 当你想要了解数据的底层结构、发现隐藏的细分市场，或识别异常时。

**示例：** 

* **客户细分：** 根据客户的行为、人口统计或购买模式，将客户群划分为不同的组，*不* 预先定义这些组，如 [图 8-2](#c08.xhtml#c08-fig-0002) 所示。这允许更有针对性的营销和个性化体验。（这是 `unsupervised learning` 的典型示例。）
* **识别用户角色：** 根据用户与产品的交互发现不同类型的用户，即使你之前没有明确定义这些角色。
* **分组相似产品：** 在电子商务环境中，根据产品的功能、描述或客户评论将产品分组，即使它们不属于同一预定义类别。

![Figure 8-2: An illustration of customer segmentation, a common application of unsupervised learning. The model identifies hidden patterns in user data to automatically group customers into distinct segments, enabling more targeted product strategies and personalized experiences.](images/c08f002.png)

**Figure 8-2:** An illustration of customer segmentation, a common application of unsupervised learning. The model identifies hidden patterns in user data to automatically group customers into distinct segments, enabling more targeted product strategies and personalized experiences.

### 生成：创造新事物

**它是什么：** 使用 AI，特别是大型语言模型（LLM），创建新内容，例如文本、图像、音频，甚至代码。为此，这些模型首先将大量信息分解为称为 token 的较小片段——例如单词或单词的一部分。通过学习这些 token 之间的统计关系，模型随后可以生成新的、原创的内容。[Figure 8-3](#c08.xhtml#c08-fig-0003) 说明了处理文本的这一初始步骤。这是 AI 从分析转向创造的地方。

**何时使用：** 当你需要自动化内容创建、大规模个性化内容，或为用户提供创意协助时。

**示例：** 

* **生成营销文案：** 创建广告标题、电子邮件主题行或产品描述的变体。
* **总结文本：** 将长文章、文档或客户支持对话浓缩为简洁的摘要。
* **创建个性化电子邮件回复：** 根据电子邮件内容起草对客户询问的回复。
* **生成代码片段：** 通过基于所需功能的自然语言描述生成代码，帮助开发人员。
* **创建图像变体：** 基于现有图像或文本描述。

![Figure 8-3: A simplified view of how LLMs process text. Input text is first broken down into smaller units called “tokens” and then converted into numerical “embeddings” before being used by the model to generate new content.](images/c08f003.png)

**Figure 8-3:** A simplified view of how LLMs process text. Input text is first broken down into smaller units called “tokens” and then converted into numerical “embeddings” before being used by the model to generate new content.

### 推荐：引导选择

**它是什么：** 根据用户的过去行为、偏好或相似用户的行为，向用户推荐相关项目或内容。这种常见的方法，称为协同过滤，如 [Figure 8-4](#c08.xhtml#c08-fig-0004) 所示。

**何时使用：** 当你想要提高参与度、促进销售，或帮助用户发现新内容或功能时。

**示例：** 

* **产品推荐：** 根据用户的过去购买或浏览历史，推荐用户可能感兴趣的产品（例如亚马逊的“购买此商品的客户还购买了……”功能）。
* **内容推荐：** 根据用户的过去消费模式推荐文章、视频或音乐（例如 Netflix 或 Spotify）。
* **功能推荐：** 根据用户的当前任务或工作流程，推荐用户可能发现有帮助的产品功能。

![Figure 8-4: Collaborative filtering is a method used in recommendation systems that predicts a user's preferences by analyzing the preferences of other users with similar tastes.](images/c08f004.png)

**Figure 8-4:** Collaborative filtering is a method used in recommendation systems that predicts a user's preferences by analyzing the preferences of other users with similar tastes.

### 异常检测：发现异常

**它是什么：** 识别与常态显著偏离的数据点。就像是发现离群值或例外情况，如 [Figure 8-5](#c08.xhtml#c08-fig-0005) 所示。

**何时使用：** 当你需要检测欺诈、识别系统错误，或标记异常行为时。

**示例：** 

* **欺诈交易检测：** 识别可能表明信用卡交易欺诈的异常消费模式。

