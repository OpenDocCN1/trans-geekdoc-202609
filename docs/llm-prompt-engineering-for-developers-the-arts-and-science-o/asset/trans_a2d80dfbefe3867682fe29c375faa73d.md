

虽然归纳学习强调广泛的适用性，但转导学习则针对手头的数据进行优化。了解何时使用每种方法对于各种机器学习应用至关重要。

简而言之，归纳学习推理从观察到的训练案例出发，并寻求推广到未见的场景；而转导学习推理则从一个特定的观察案例移动到另一个特定但尚未见过的案例，而不改变当前的基本任务。

从心理学中做一个类比，Perkins 和 Salomon (1989) 提出的“Hugging”（拥抱/强化类似情境）43，强调学习情境与未来应用之间的相似性，可以类比为归纳学习；而“Bridging”（架桥/情境迁移），这是教学中使用的另一种技术，它将具体的知识实例与新情境联系起来，反映了转导学习的原理。

下表总结了归纳学习与转导学习之间的区别：

| 方面 | 归纳学习 | 转导学习 |
| :------- | :------------------- | :--------------------- |
| 遇到的数据 | 在模型训练期间仅遇到训练数据。 | 在模型训练期间同时遇到训练和测试数据集。 |
| 预测模型 | 构建一个可应用于未见数据的预测模型。 | 不为未见数据构建独立的预测模型。 |
| 新数据处理 | 当引入新数据时，已建立的模型可以快速预测，无需重新训练。 | 新数据需要从头重新运行算法、重新训练，然后进行预测。 |
| **模型的目的** | 旨在创建一个通用模型，能够预测数据空间中的任何新点。 | 构建一个针对其遇到的特定训练和测试数据点定制的模型。 |
| **流数据效率** | 可以以最小的计算开销快速标记新的数据点。 | 如果不断引入新的数据点，可能会变得计算密集。 |

## 11.5 - 迁移学习、微调和提示工程

提示工程和迁移学习服务于不同的目的，但它们都是用于提高机器学习模型性能和实用性的方法论，特别是在 OpenAI GPT 系列等模型的背景下。

微调是迁移学习的一种，涉及将预训练模型适应于新的自定义任务。这是自然语言处理（NLP）领域的一种常见做法，通常用于提高语言模型的性能。

那么，提示工程和微调之间有什么关系呢？

当你想要微调像 OpenAI GPT 这样的模型时，你需要提供一组训练示例，每个示例都包含一个输入（“提示”）及其对应的输出（“补全”）。这与使用基础模型有明显不同，在使用基础模型时，你可能在单个提示中输入详细的指令或多个示例。

当你希望模型执行特定任务时，这非常有用。例如，你可能希望微调一个模型来理解你的客户支持工单，并根据你的知识库或之前对类似工单的回复自动响应。

### 11.6 - 使用提示数据集进行微调：一个实用示例

为了简单起见，我们将使用 OpenAI 的基础模型之一，并将其微调以执行一个简单的任务：回答 FAQ 中的问题。

为了微调模型，正如之前所述，我们需要一组训练示例，每个示例都包含一个输入（“提示”）及其对应的输出（“补全”）。以下是 OpenAI 文档的建议：

- 每个提示应以一个固定的分隔符结尾，以便通知模型提示结束且补全开始。一个通常效果良好的简单分隔符是 `\n\n###\n\n`。分隔符不应出现在任何提示的其他位置。
- 由于 OpenAI 的分词方式（对大多数单词进行分词时会附带前导空格），每个补全应以一个空格开始。
- 每个补全应以一个固定的停止序列结尾，以便通知模型补全结束。停止序列可以是 `\n, ###,` 或任何其他未在任何补全中出现的标记。

假设你有一个名为 SkillUp Academy 的电子学习平台，并且你有以下 FAQ 页面。

Q. 什么是 SkillUp Academy？
A. SkillUp Academy 是一个在线学习平台，提供跨多个学科的多种课程，使学习者能够以自己的节奏从世界任何地方获得知识和技能。

Q. 我如何注册？
A. 只需点击我们主页上的“注册”按钮，提供你的详细信息，即可开始！

Q. 我如何支付课程费用？
A. 我们接受通过 PayPal 和 Stripe 进行的付款。

Q. 我对课程不满意。我可以退款吗？
A. 是的，我们提供 30 天退款保证。如果你在此期间内不满意，可以申请退款。请参阅我们的退款政策以了解详情。

Q. 我在哪里可以找到网站的服务条款？
A. 我们的服务条款可以在我们网站的页脚找到，或者点击此处查看。

Q. 我的个人信息安全吗？
A. 绝对安全。我们优先考虑你的隐私，并采取了严格措施来保护你的数据。在此阅读更多关于我们的隐私政策的详情。

Q. 我可以按自己的节奏学习吗？
A. 是的，我们的课程旨在允许你按自己的方便时间学习。一旦注册，你可以在特定时期内访问课程材料，在此期间你可以按自己的节奏学习。

Q. 我对课程内容有问题。我该如何得到解答？
A. 大多数课程都有讨论论坛，你可以在那里提问、与其他学习者互动，有时还可以得到课程讲师的回复。

Q. 我可以在手机上访问课程吗？
A. 是的，我们的平台对移动设备友好，我们还有专为 Android 和 iOS 提供的专用应用程序。

Q. 我是一名讲师。我如何在你的平台上开设一门课程？
A. 我们始终在寻找知识渊博的讲师。只需前往我们的“成为讲师”页面，了解与我们合作的详细信息。

Q. 完成课程后你们提供证书吗？
A. 是的，一旦你成功完成课程并通过任何必要的评估，你将获得结业证书。

Q. 如果我遇到技术问题该怎么办？
A. 请通过“联系我们”页面联系我们的支持团队，他们很乐意为你提供帮助。

要将 FAQ 用作训练数据集，我们需要将其转换为 OpenAI GPT 可以理解的格式。我们将使用类似于 OpenAI 推荐的格式（JSONL 文档⁴⁴）

```json
{"prompt": "lorem ipsum dolor sit amet.END_PROMPT", "completion": "consectetur adipiscing elit.\n"}
{"prompt": "Vivamus vel lacus quis diam vestibulum scelerisque.END_PROMPT", "completion": "Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.\n"}
...etc
```

在实践中，lorem ipsum 文本将被问题（提示）和答案（补全）替换。`->` 和 `\n` 是我们将使用的分隔符，用于通知模型提示和补全何时结束。

FAQ 数据集看起来将是这样的：

```json
{"prompt": "What is SkillUp Academy->", "completion": " SkillUp Academy is an online learning platform offering a variety of courses across multiple disciplines, enabling learners to gain knowledge and skills at their own pace from anywhere in the world.\n"}
{"prompt": "How do I sign up->", "completion": " Just click on the \"Sign Up\" button on our homepage, provide your details, and get started!\n"}
{"prompt": "How can I pay for a course->", "completion": " We accept payments through PayPal, and Stripe.\n"}
{"prompt": "I am not satisfied with the course. Can I get a refund->", "completion": " Yes, we offer a 30-day money-back guarantee. If you're not satisfied within this period, you can request a refund. Please see our refund policy for details.\n"}
{"prompt": "Where can I find the terms of service for the website->", "completion": " Our terms of service can be found at the footer of our website or by clicking here.\n"}
{"prompt": "Is my personal information secure->", "completion": " Absolutely. We prioritize your privacy and have stringent measures in place to protect your data. Read more in our privacy policy here.\n"}
{"prompt": "Can I learn at my own pace->", "completion": " Yes, our courses are designed to allow you to learn at your convenience. Once you enroll, you'll have access to the course materials for a specific period, during which you can learn at your own pace.\n"}
{"prompt": "I have questions about the course content. How can I get them answered->", "completion": " Most courses have a discussion forum where you can ask questions, engage with fellow learners, and sometimes get responses from the course instructors.\n"}
{"prompt": "Can I access the courses on mobile->", "completion": " Yes, our platform is mobile-friendly, and we also have a dedicated app available for both Android and iOS.\n"}
{"prompt": "I'm an instructor. How can I offer a course on your platform->", "completion": " We're always looking for knowledgeable instructors. Just head to our 'Become an Instructor' page for details on how to collaborate with us.\n"}
{"prompt": "Do you offer certificates upon course completion->", "completion": " Yes, once you successfully complete a course and pass any required assessments, you will receive a certificate of completion.\n"}
{"prompt": "What should I do if I face technical issues->", "completion": " Please reach out to our support team via the 'Contact Us' page, and they'll be happy to assist you.\n"}
```

