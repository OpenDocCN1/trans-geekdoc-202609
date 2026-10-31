
# 现场安全评估

## 初步停车场和周边观察

通过这种个人直接接触可能看不到的是，他们的评估在驶入停车场时就开始了：该地点是否设置了预期的适当物理屏障，例如混凝土或坚固的路障来保护软性入口？建筑物前方是否有大面积水域作为物理屏障？可以看到多少个出口？室外摄像头在哪里，它们是否覆盖所有入口和出口？是否有足够高度的门禁和围栏以阻止翻越者？保安或接待员在进入时是否坚持查看政府签发的有效身份证件？是否努力将我们的身份证件与面部进行匹配？大厅的摄像头覆盖是否足够？他们是否有访客 Wi-Fi，进入有多容易？

## 陪同与工作区评估

分析员接受过礼貌的训练，但在被护送到任何会议室时，他们接受过环顾四周并进一步评估的训练：办公桌是否没有信息残留，是否有任何工作站未上锁？是否有任何维修门被撑开“因为这样油漆工进出更方便”，或消防门明显敞开而警报未响？许多员工因“一直都是这样”或“没人说过什么”之类的借口而忽略自己工作场所的这些问题。这是一个信号，表明对于物理安全人员而言，安全本身至关重要。

## 接待员作为物理安全控制

例如，在大多数前台，接待员的关键角色是作为物理安全控制，并且是分析员评估的一部分：在接近其工作站时，接待员是否在注意并准备迎接你？他们是否要求查看身份证件并进行面部比对？不幸的是，许多担任此角色的人没有意识到他们对物理安全的重要性。许多社会工程攻击都针对这一脆弱角色。声称包裹投递或紧急家庭问题是黑客操纵未经训练的接待员以允许未经授权进入的常见方式。

## 评估介绍声明

介绍完成后并说明议程后，KC 的安全评估员接受过训练，通过以下声明向供应商保证安全评估的目的：

> KC Enterprises 将其供应商视为合作伙伴，这并非设计成“抓包”游戏或让公司内任何人难堪。这项评估是我们与合作伙伴尽职调查计划的一部分，以确保我们的安全满足客户和员工的期望。

这些 `exact` 词语是该团队培训的一部分。在与供应商互动时，预计他们会用自己的话传达这一点。同样预期的是，其精神会被贯彻，无论他们如何向第三方定义它。

## 调查流程和领域覆盖

根据供应商安排专家的方式，领域将按该顺序进行覆盖。这些评估的调查表不会与第三方共享，主要是因为这是一次对话。在审阅 KC 现场调查表时，它首先关注领域层级，并依靠经验丰富且受过训练的 KC 员工在讨论发展过程中深入细节。它在介绍时经常以模拟对话的方式向供应商描述：

| `KC Analyst:` | | `“Do you have an access management policy?”`重点是从顶层领域开始；在这种情况下，是访问管理。KC 对访问管理有一些安全标准，但它并不规定第三方如何编写政策。 |
| --- | --- | --- |
| `Vendor SME:` | | `“Yes, let me bring it up on the projector.”`现场评估的一个优势是，受控访问文档（如政策或工件）即使他们原本不愿分享也可以展示。这种方法允许对第三方的整体安全态势进行全面了解，而不仅仅是单个控制措施。 |
| `KC Analyst:` | | `“Show me the version control section.”`查看版本控制有几个目的。大多数政策或标准文件都需要更新周期和审批。通常要求每年审查和更新一次。如果分析员注意到间隔超过一年，这可能表明供应商没有关注政策。不关注政策是一个很好的指标，表明他们可能没有遵循政策。 |
| `KC Analyst:` | | `“I notice that it has not been updated per the control statement at least annually. Is there a plan to review and update soon?”` |
| `Vendor SME:` | | `“Not sure, I will need to check with the document owner and get back to you.”`分析员在调查表中记录了这一点以及政策过时需要审查。这可能会引发另一场对话。 |
| `KC Analyst:` | | `“Great, thanks. Please turn to the section on password complexity requirements.”`现在分析员通过查看供应商的政策或流程文件中是如何规定的来深入验证具体控制措施。当文档在投影仪上电子翻页到密码复杂度部分时，分析员记录了要求。 |
| `KC Analyst:` | | `“I see that the password complexity rules are at least eight characters, with one uppercase, one lowercase, and a special character. Please show me this in production, either a screenshot of your group policy for the domain, or any other way that would demonstrate that it is enforced.”` |
| `Vendor SME:` | | `“Sure, here is a screenshot, dated yesterday, of our domain group policy showing the complexity rules.”` |
| `KC Analyst:` | | `“Is this the only domain internally used for access management?”` |
| `Vendor SME:` | | `“No, we've got our cloud deployment in Azure that has a separate domain controller and a one‐way trust from internal corporate DC to Azure DC.”` |
| `KC Analyst:` | | `“We will do more cloud security later in that domain, but do you have available the same type of screenshot for the domain policy in Azure?”` |
| `Vendor SME:` | | `“No, that's owned by the cloud security team, when they come in to do the cloud security section they can show you that.”` |

再次，对确认云实例中的组策略进行了后续记录，分析员随后继续进行访问管理中的其他部分，如特权账户管理等。每个领域的开展方式都相同：分析员查看顶层政策或标准，然后找到供应商的具体安全控制措施并进行物理验证。

### 现场问卷

现场问卷是一份重要文件，由于其规模，你可以在 `www.wiley.com/go/cybersecurityand3prisk` 找到并下载。以下是主要部分的摘要。

### 数据确认
本部分与您的供应商确认他们提供的服务、数据量和类型，如果连接处于活动状态，则确保其上的数据正确。如果存在差异，它会指示分析员与供应商经理交谈，以确保其记录准确或揭示是否存在需要澄清的误解。

### 安全计划
这是一项以网络安全为重点的现场评估。为了使供应商在自身网络安全方面取得成功，他们必须拥有记录在案的安全政策和计划。供应商必须出示一份安全政策文件，说明信息安全在供应商处如何运行。它应提供以下方面的答案：

#### 访问控制
本部分的问题集中在该领域内的几个关键领域。首先，审查的是访问控制的顶层政策。此外，必须有网络访问的政策。
