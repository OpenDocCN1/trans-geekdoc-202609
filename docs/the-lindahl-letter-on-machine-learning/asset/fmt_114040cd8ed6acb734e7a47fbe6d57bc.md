
# 机器学习部署路径的分歧

在机器学习领域，存在一个分岔路口：如何评估机器学习用例的价值，这在一定程度上将用例分为了两类。

## 开箱即用的云 API 方案

您有大量开箱即用的选项，只需基于云 API 端点提供的模型进行少量配置和设置即可使用。当然，您需要建立连接并建立商业关系，但总体而言，这是大规模入门机器学习领域最简单的方式。这些解决方案并非高度定制化的部署，并且从一开始就包含了一定的按交易计费成本。

## 自建模型部署方案

或者，您可以构建并提供自己的模型，而不必求助于基于云的 API 机器学习解决方案。这意味着开箱即用且可扩展的解决方案与需要一定程度的初始和持续投资的高度定制化部署之间存在天然冲突。

## 参考文献

[1] *Big Data, Data Mining, and Machine Learning: Value Creation for Business Leaders and Practitioners* by Jared Dean (2014)

[2] “When Not to Use Machine Learning or AI” (Towards Data Science) by Cassie Kozyrkov, who also shares some great content on decision-making here: https://decision.substack.com/

[3] See “Substack Week 11: What is machine learning scale? The where and the when of machine learning usage” and “Substack Week 16: Ongoing machine learning cloud costs.”

[4] “Cloud API Market to Reach $1.78 Billion by 2026” (Wired Release)

---

# Substack Week 10: 面向小样本 GPT-2 的模型可扩展性

**发布日期：2021 年 4 月 2 日**

您可能已经听说过生成式预训练转换器模型，或在过去一年的新闻文章中读到过它。它在发布时引起了相当大的轰动。让我们深入探讨，从一个问题开始：“什么是 GPT-2 甚至 GPT-3？” 让我们先了解一些关于小样本学习究竟包含什么的基础知识，随后再研究它如何与 GPT-2 相关联。

您可能知道，小样本学习是一种方法，它获取一个构建完善且定义明确的模型，仅使用少量训练数据通过尝试几次来实现有利的结果 [1]。基本上，您是基于少量数据进行预测。网上有更好的表述方式并已免费分享，您稍微搜索一下就能找到，但我认为这为探讨主题的第二部分奠定了基础。

我对 OpenAI 的 GPT-2 和 GPT-3 模型项目都非常感兴趣 [2]。它们是以预测性语言建模为目标设置的 GPT 模型。这是一套非常有趣的技术，基于其在实践中所承诺的潜力，吸引了我的注意力以及许多其他人的关注 [3]。目前 GPT-3 的提供方式是，您可以通过 API 部署以功能性方式调用模型，并能获得非常有趣的结果。您只需给它一个提示或一小段文本，它就准备好输出内容。人们担心 GPT-3 可能会创造出近乎无尽的内容流，变得如此普遍以至于挤占所有其他相关内容。这可能是首次通过泛滥内容流发起的“拒绝内容攻击”。它可能创建独特的内容，以至于过滤和拦截方法难以轻易遏制。

完全基于调用 GPT-2 或 GPT-3 生成式语言模型的机器学习工作流部署，目前可能尚未达到生产就绪状态。模型可能会输出一些奇怪而有趣的东西，除非这正是您想要的用例，否则它可能还没准备好输出帮助台类型的文档或可直接面向客户的内容。考虑到模型偶尔会产生的惊人结果，那可能是一个非常糟糕的计划。

您可以访问 OpenAI 网站，深入了解他们试图用语言模型做什么。大型语言模型的影响才刚刚开始从研究演示转向商业实现 [4]。人们正在谈论它们，用例在理论上开始堆积，但在实践中尚未完全落地。如果这些内容还不够您消费，也许可以去了解一下 BERT [5]。

## 2020 年 6 月，我深度研究了 GPT-2

https://github.com/nelslindahlx/NLP/blob/master/Yet_another_working_GPT2_corpus_example.ipynb

十个月后，您仍然可以通过该链接在 Google Colab 上运行那个 GPT-2 笔记本。我刚检查过，代码仍然有效。它设置为运行 1,000 个训练步骤，这在您的 Colab 实例上需要一些时间。如果您想让它运行得更快，可以减少训练步数，但这可能会使输出变得更“狂野”。仅在我的写作语料库上稍作训练，它就会吐出与我极有可能产出的内容相似的东西。它肯定在仅仅几轮学习中就掌握了我对写作过程抱怨的总体形式和结构。这正是该模型如此有趣的原因。

## 参考文献

[1] Here is a Medium post that I enjoyed on the subject: https://medium.com/quick-code/understanding-few-shot-learning-in-machine-learning-bede251a0f67

[2] https://github.com/openai/gpt-2 or https://openai.com/blog/better-language-models/

[3] https://dailynous.com/2020/07/30/philosophers-gpt-3/#chalmers

[4] https://openai.com/blog/better-language-models/ or read the full technical paper here https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf

[5] https://towardsdatascience.com/bert-explained-state-of-the-art-language-model-for-nlp-f8b21a9b6270

---

# Substack Week 11: 什么是机器学习规模？机器学习使用的地点与时机

**发布日期：2021 年 4 月 9 日**

本周的主题正是我为今年演讲季准备的演示文稿的核心。无论您觉得它是否引人入胜，都请将其视为我对深入理解这一主题极感兴趣的证明。我投入了时间研究它，并认为值得在正式演讲中与他人分享。

当您坐下来思考机器学习时，大量的炒作扑面而来，而少许真相藏身其中。某个业务驱动的用例将存在于某个工作流中。在该工作流中，某种可定义且可重复的任务将受益于机器学习，以推动某个拐点。也许是一个简单的推荐引擎，又或许您需要弄清照片或文本块中的内容以触发某种动作。一次或几次执行可能只是一个有趣的小概念验证（POC）来设置和执行。但要解决细节，使其一次又一次地在成百上千万次执行中运行，则完全是另一码事。

大规模执行机器学习模型——无论是通过调用 API 还是托管模型——都将暴露边缘情况和意外后果。这必然会发生。您认为非常契合且将以高准确度执行的事物，将面临现实世界的挑战，问题随之而来。您必须为此做好准备，拥有一种有计划的方法，将事物控制在预先规划的容差范围内。这就是您如何确保 ROI 路径行之有效，而不是让一个严重的性能问题击垮您整个财务用例。人们开始真正谈论在现实世界机器学习案例中扩展的重要性 [1]。

## 参考文献

[1] People are really starting to talk about the importance of scaling in real-world machine learning examples.
