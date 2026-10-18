

![Remember](images/remember.png)根据您获取的 PII 类型，您有义务保护它。像 [`https://www.dol.gov/general/ppii`](https://www.dol.gov/general/ppii) 这样的文档指出了其中一些要求。但是，如果您获取了医疗信息，可能需要遵守《健康保险可移植性与责任法案》(HIPAA) 等法律。像 [`https://www.paubox.com/blog/personally-identifiable-information-hipaa-and-pii-compliance/`](https://www.paubox.com/blog/personally-identifiable-information-hipaa-and-pii-compliance/) 这样的网站会告诉您如何处理此类信息以及哪些内容属于 PII。

关键在于，您不能随意获取 PII 并指望每个人都认为这是个好主意。大多数人会对任何侵犯隐私的行为产生负面反应，无论他们是否主动提供了信息。征求许可并保护获取的数据是最佳选择。作为解决方案的一部分，您还必须考虑《加州消费者隐私法案》(CCPA)、《通用数据保护条例》(GDPR) 以及其他要求，这些要求规定在个人请求时模糊或删除 PII（参见 [`https://www.dataguise.com/blog/how-to-obfuscate-delete-personal-information-of-data-subjects`](https://www.dataguise.com/blog/how-to-obfuscate-delete-personal-information-of-data-subjects)）。

## 使用清理技术

很容易将数据清理与数据清洗（在 [第 11 章](#c11.xhtml) 中讨论过的主题）混淆。*数据清理*涉及从数据集中删除个人信息，例如姓名、地址、电话号码、ID 等，以至于在数据集中识别特定个人变得不可能。除了文本和数据集变量外，您还必须考虑每种类型的数据。例如，如果您正在处理照片集，采取措施模糊面部并从图像中移除车牌至关重要。奇怪的是，如果您使用 sanitization 作为关键词进行 Google 搜索，您仍然会得到许多关于清理的链接。将 privacy 作为另一个关键词有助于找到您真正需要的文章类型。即便如此，您可能会发现您不是唯一对该过程感到困惑的人。

删除个人信息对于确保个人隐私以及满足法律要求至关重要。如本章开头所述，未能确保个人隐私将会有后果。您可以应用多种技术来实现这一目标：

*   **删除特征：** 说到姓名，删除特征将保护隐私，但在大多数情况下仍能保持数据完全可用。这是最佳的清理方法。

*   **替换特征：** 您可能需要为数据集中的案例提供一个 ID 来识别案例，而不是用户。这个过程有点棘手，因为您不能在用户的原始个人标识符和新案例标识符之间创建任何关联，后者应该是一个随机的唯一值。

*   **聚合特征：** 通过仔细聚合，您可以创建一个新特征，该特征是几个可个人识别特征的数学聚合。当可以将聚合逆向工程回原始值时，就会出现问题。

*   **自动化清理：** 您可以找到声称可以清理数据的算法，例如位于 [`https://www.researchgate.net/publication/315913699_An_Improved_Data_Sanitization_Algorithm:for_Privacy_Preserving_Medical_Data_Publishing`](https://www.researchgate.net/publication/315913699_An_Improved_Data_Sanitization_Algorithm:for_Privacy_Preserving_Medical_Data_Publishing) 的医疗产品。但是，在没有监督的情况下使用自动化可能会导致意外结果。有人可能能够逆向工程该过程，或者数据在其新形式下可能变得不可用。

## 避免数据推断

在收集数据时，一些用户会拒绝分享可个人识别的信息，例如性别和年龄。一项建议是，当用户的照片或其他信息可用时，推断这些信息。例如，机器学习应用程序可能会尝试使用人名推断性别，或使用面部分析推断年龄。

不幸的是，在特定文化中与某一性别相关的名字，在其他文化中可能被分配给另一性别。人们还可以从像 [`https://www.popsugar.com/family/Gender-Neutral-Baby-Names-34485564`](https://www.popsugar.com/family/Gender-Neutral-Baby-Names-34485564) 这样的网站上选择中性名字，因此基于名字做出假设是个坏主意。一个人也可能认同自己是双性人（参见 [`https://isna.org/faq/what_is_intersex/`](https://isna.org/faq/what_is_intersex/)），而不是男性或女性，以及跨性别者等等（您可以在 [`https://interactadvocates.org/faq/intersex-lgbtqia/`](https://interactadvocates.org/faq/intersex-lgbtqia/) 上阅读更多内容），这可能会影响该人对许多问题的看法。

年龄推断的问题更为深刻。例如，机器学习算法可能会为白化病患者推断出错误的年龄，这可能会影响多达 3000 人中的 1 人，具体取决于数据来自世界的哪个部分（[`https://www.albinism.org/information-bulletin-what-is-albinism/`](https://www.albinism.org/information-bulletin-what-is-albinism/））。如果数据以任何方式偏向白化病患者，您最终可能会得到很多实际上相当年轻的老年人。对于早衰和许多其他可能自然发生的生理变化也是如此。

结论是，基于您认为自己了解的关于某人的信息来假设任何事情是不安全的。推断任何事情都可能导致数据偏差。如果某个特定属性对您的分析至关重要，而该人未提供它，最安全的做法是将该案例从数据集中删除。

## 正确使用概括

当今许多研究领域都试图错误地应用统计和机器学习结果，导致个人在某种程度上受到不公正对待。必须记住，统计适用于群体，而不适用于个人。反之亦然：您不能通过观察群体中的个体来对群体做出概括。位于 [`https://bigthink.com/Mind-Matters/big-idea-statistics-about-groups-tell-you-nothing-about-individuals`](https://bigthink.com/Mind-Matters/big-idea-statistics-about-groups-tell-you-nothing-about-individuals) 的文章在一定程度上讨论了这两种情况。许多数据收集技术的一个问题是，个体被问及关于群体成员身份的尖锐问题，这些问题最终被证明是不真实的，因为

*   个体不了解群体成员身份的含义

*   个体对群体的看法与数据收集者不同

*   群体成员身份是模糊的

*   群体成员身份过于宽泛

*   群体成员身份过于狭窄

