

eBay 对规划极其重视。他们识别出要解决的问题，创建并启用了跨职能团队，并成功执行了多年战略。即使你的公司不像 eBay 那样规模庞大或没有他们的资源，你仍然可以从他们的例子中学到前期制定战略的重要性。

但是，请确保不要试图一次性完成所有事情。如果你试图同时解决所有业务问题，那么你将一个都解决不了。从小处着手，然后随着时间的推移迭代和扩展解决方案。你选择首先解决的问题将为你其余的人工智能之旅奠定基础。

* * *

[14](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-5.xhtml#footnote-016-backlink) “Walmart Drops Bossa Nova Inventory Robotics Program - Highlights Retail Robotics Challenges & Opportunities.” Robotics Business Review, 17 Nov. 2020, www.roboticsbusinessreview.com/opinion/walmart-drops-bossa-nova-inventory-robotics-program-highlights-retail-robotics-challenges-opportunities/.

[15](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-5.xhtml#footnote-015-backlink) Strickler, Jordan. “Blue River Technology Uses Facebook AI For Weed Control.” Forbes, Forbes Magazine, 7 Aug. 2020, www.forbes.com/sites/jordanstrickler/2020/08/07/facebook-ai-is-getting-into-agriculture/.

[16](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-5.xhtml#footnote-014-backlink) Simonite, Tom. “Why John Deere Just Spent $305 Million on a Lettuce-Farming Robot.” Wired, Conde Nast, 7 Sept. 2017, www.wired.com/story/why-john-deere-just-spent-dollar305-million-on-a-lettuce-farming-robot.

[17](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-5.xhtml#footnote-013-backlink) “Brain Tumor: Statistics.” Cancer.Net, 12 Feb. 2020, [`https://www.cancer.net/cancer-types/brain-tumor/statistics`](https://www.cancer.net/cancer-types/brain-tumor/statistics).

# Chapter 3

## 3\. Picking the Goldilocks Problem

“除了看起来像一群莽撞的业余爱好者之外，试图将人工智能方法强行应用于不适合的场景的领导者，通常最终会得到在生产环境中维护成本过高的解决方案。相反，找到一个好的问题来解决，让最好的解决方案胜出。如果你可以不使用人工智能来完成，那就更好了。机器学习/人工智能适用于其他方法无法满足你所需性能的场景。”

—Cassie Kozyrkov, Google, Inc. 首席决策科学家[18](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-6.xhtml#footnote-021)

将人工智能融入你的业务并不一定意味着要利用机器学习一次性解决所有问题。事实上，不应该这样做。更重要的是选择一个正确的问题作为起点，并通过其解决方案建立势头。这就是所谓的识别“金发姑娘问题”。

在软件公司 Autodesk® 开始处理人工智能之前，其技术支持服务明显是传统的。当数百万依赖 AutoCAD LT® 软件来创建技术设计和模型的工程师和建筑师需要帮助时，他们的选择是拨打热线或通过电子邮件发送帮助请求。这形成了一个需要手动管理的长队列。平均支持案例需要超过一天才能解决。因此，当 Autodesk 决定引入人工智能时，他们将目光集中在一个突出的问题上：通过缩短案例解决时间来改善客户体验。他们没有构建一个模型来帮助自动化联系中心的所有咨询（这些咨询涵盖了数十种用例和问题），而是专注于解决一个占据了大量进入支持工单的单一问题：密码重置。[19](#Alyssa-Simpson-Rochwerger_Real-World-AI_PRODUCTION_v101-6.xhtml#footnote-020)

这种专注——识别一个具有业务重要性的狭窄问题——对其成功至关重要。

决定哪些入站咨询是关于重置密码的，是自然语言处理的一个好任务，因为人们通常以几种相似的方式之一描述问题：“我需要帮助登录。”“我想重置我的密码。”Autodesk 拥有大量历史数据——电子邮件和语音录音——用户在其中请求他们解决这个问题。密码重置请求每月代表数千个咨询。如果 Autodesk 能够自动化该过程，他们将显著释放联系中心资源，以更快地解决其他客户问题。

最重要的是，提出这些请求的客户往往会感到沮丧，因为像重置密码这样简单的事情竟然需要一天半才能解决。这些是高度技术性的用户，无法访问他们工作所需的主要工具之一。糟糕的客户体验正在给公司造成损失。

在确定了这个具体目标后，Autodesk 构建了一个模型来识别哪些入站工单是密码重置请求。如果他们能在咨询发送后立即自动识别这些请求，他们就可以将该客户路由到一个能够重置客户密码而无需另一个人工介入的用户界面。该团队不仅需要构建一个自然语言处理模型来检测密码重置咨询。他们还需要连接多个内部系统，以验证请求重置的人是否有权这样做。最终，他们能够大幅减少解决密码重置请求的平均时间——从 1.5 天缩短到 10-15 分钟。

这个解决方案是一个极好的概念验证。此外，负责确定哪些入站请求是关于密码重置的自然语言处理模型，在开始增加价值时不需要完美。即使在开始时，该模型只成功识别了 70% 的入站密码重置请求，这仍然对缩短客户解决时间的底线做出了有意义的贡献。随着时间的推移，模型得到了改进并扩展了其功能。Autodesk 构建了模型来识别 60 个不同的用例，从激活码请求到地址更改、合同问题、技术问题等。这 60 个用例同样容易解决和自动化，释放了他们的客服人员去帮助客户处理更复杂的问题，并将平均案例解决时间从 1.5 天降至 5.4 分钟。

根据 Autodesk 当时的运营副总裁 Gregg Spratto 的话，“该解决方案识别问题上下文的能力，使 Autodesk 能够以快 99% 的速度解决客户咨询。”这直接转化为成本节约和更好的客户体验，并导致整个组织对人工智能进行更大规模的投资。

Autodesk 通过选择一个可管理且有价值的首要问题来解决，为自己奠定了成功的基础。他们的问题范围狭窄，但具有明显且可衡量的业务影响。他们没有在一开始就试图解决最终自动化的所有 60 个用例；团队专注于解决一个问题，快速且出色地解决了它，并证明了其业务价值。同时，他们为即将到来的所有解决方案构建了原型。也许更重要的是，团队不仅仅是构建一个模型然后把它扔给别人。

如果你能解决你攻克的第一个问题并证明人工智能可以产生的影响，你将更容易获得支持和资源来解决接下来的 10 个问题。你可能会识别出各种潜在的绝佳首要问题。选择一个在规模和影响之间达到最佳平衡且具有可管理机器学习组件的问题，是你为自己奠定成功基础所能做的最重要的事情。

那么这个金发姑娘问题的特征是什么？

## Start Small

