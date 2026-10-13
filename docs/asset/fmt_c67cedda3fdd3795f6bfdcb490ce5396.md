
*   **第 3 层** – 将文件恢复到各自的系统后，AI 再次搜索任何恶意代码或入迹象。
*   **第 4 层** – 抗体 AI 使用淋巴 AI 和上一次入侵的黑匣子备份，训练淋巴 AI 识别另一种威胁，从而实现自我学习。
*   **第 5 层** – AI 向其所在工作单位的网络安全部门提供 IRS 日志和淋巴 AI 日志。
*   **第 6 层** – 用户解除锁定状态，恢复工作。
*   **第 7 层** – 随着用户工作，AI 在整个系统中执行最后一次搜索，以检查该代码片段是否存在。

领域 1 成功执行且无任何差错后，整个网络将进入固定时间段的维护期，响应机制转入最关键的步骤——领域 2。

*   **事后响应机制 – 领域 2**
    *   **第 1 层** – 抗体 AI 将数据库的所有密码和集体信息备份到数据库内的随机位置，以确保没有人能找到其位置，甚至包括管理员。
    *   **第 2 层** – AI 剥离旧的加密函数密钥，并生成一个新的随机密钥。
    *   **第 3 层** – 此新密钥将用于加密存储在随机位置的所有密码，并存储到相应用户的密码字段中。
    *   **第 4 层** – 最后一步是让用户再次登录以检查是否有加密错误，如果有错误，可使用随机文件夹中指定的备份密码进入并修改。

加载完事后响应机制的领域 2 后，整个网络将恢复正常，并采用新的加密，该加密因入侵而异且无法被检测到，甚至管理员也无法检测。随后维护期随一条信息警报结束：“感谢您的等待：抗体 AI 现已更改密码加密。为检查您的密码是否正确加密，请尝试登录您的软件。若遇到任何错误，请联系您的管理员”，如图 8 所示，抗体 AI 完成其工作。这就是抗体 AI 连同其其他部分（如淋巴 AI 和协议）运作的工作流程。

| 图 8. ARM 领域 2 完成时 AI 的信息消息 |
| :--- |
| ![Figure979-8-3693-1642-9.ch004.f08](img/ch004.f08.png) |

## 4. 系统架构

| 图 9. 抗体 AI 及其内部所有组件的系统架构 |
| :--- |
| ![Figure979-8-3693-1642-9.ch004.f09](img/ch004.f09.png) |

图 9 展示了抗体 AI 的架构。用户部分指使用软件或网络的用户，包含少数合法用户和少数黑客/键盘记录器。网络部分描绘了用户系统所在的网络，数据库表示存储所有关键数据的位置。抗体 AI 由以下部分组成：

*   **淋巴 AI**
*   **协议**

### 4.1 淋巴 AI

抗体 AI 的这一部分负责利用数据集进行集体训练并生成“安全点”，供抗体 AI 及其协议使用。由于抗体 AI 是基于 LLM/生成式 AI 的神经网络，为了准确行动，它必须接受少量简单的输入。基于这一唯一原因，抗体 AI 内嵌了一个较小的 AI 模型，专门用于将原始数据（即日志和其他用户输入）直接转换为处理后的输出点。这些点决定系统是安全的还是正在发生入侵。淋巴 AI 的这些输出随后被发送给主 AI——抗体 AI，后者结合自身的处理方法将这些点转换为可用格式，以检测系统是否被攻破。图 10 展示了淋巴 AI 的工作原理及输出返回过程。

| 图 10. 淋巴 AI 的工作原理及输出返回 |
| :--- |
| ![Figure979-8-3693-1642-9.ch004.f10](img/ch004.f10.png) |

### 4.2 协议

协议在抗体 AI 中发挥着主要作用。为执行如此庞大的流程，AI 有时会变得随机化，并在试图防护或遏制入侵时混淆。为避免这种情况并为用户标记流程，该 AI 拥有若干协议以保护网络及其自身。

部分先前解释过的协议如下：

*   **安全协议 (SP)** – 一旦 AI 识别出入侵可能性，即触发这些协议。
*   **锁定协议 (LP)** – 一旦 IRS 接收到触发消息，即触发这些协议，用于保护同一网络内的其他用户。
*   **事后响应机制领域 (ARMS)** – 一旦 IRS 完成对入侵者或黑客的处理工作，即触发这些协议。这是负责抗体 AI 动态密钥更改的主要算法。

## 5. 影响准确性的参数

本项目包含两个具有不同参数和不同工作流程的 AI，因此每个 AI 都有几个显著的参数优先级和对其准确性的影响。分类如下：

### 5.1 影响淋巴 AI 的参数

#### Lymph AI：抗体 AI 的第一层

我们直接提供给抗体 AI 的每一个输入（即 SUND 输入）首先进入 **Lymph AI（淋巴 AI）**。Lymph AI 通过选择性公式法和数据集训练法接收这些输入并生成输出。该输出称为 **“安全点”**。这些安全点被传递给抗体 AI，后者仅接受源自 Lymph AI 的输入。随后，安全点被转换为抗体 AI 用于不同目的的各种参数形式：**PBP（潜在违规百分比）** 和 **触发标志**。

#### 5.1.1 影响 Lymph AI 的输入参数

##### 5.1.1.1 IP 地址

被扫描计算机的 `IP Address` 决定了我们试图访问的系统。它充当计算机的 ID，标识我们从哪台计算机获取数据。这是 Lymph AI 的 **主键**。它不用于计算“安全点”的公式中，但对于 AI 检测入侵仍然很重要。

如果检测到入侵，Lymph AI 会连同受影响电脑的 IP 或攻击者的 IP 一起发送安全点。这些 IP 作为 **封锁协议** 的参数。

##### 5.1.1.2 IP 的网络 Ping 值

IP（或系统）的 `Network Ping` 用于确定网络流量，这对于分析暴力破解或僵尸网络尝试至关重要。该参数以 **毫秒** 为单位，并作为 Lymph AI 内部的基础检测参数。

它充当 **安全点的基础值参数**。当设置较高时（即网络 Ping 增加），安全点会显著下降，但不会超过 **20 点**。

##### 5.1.1.3 IP 的软件代码使用情况

软件代码使用情况通过监控选定应用程序或操作系统的内存消耗，检测软件内运行的恶意代码。通过远程登录操作系统，我们检测目标 IP 的内存和 RAM 使用情况。如果使用率超过特定阈值，我们断定该软件正在运行恶意代码（例如自动密钥生成器或暴力破解代码）或已死机。该参数在 Lymph AI 中具有 **最低优先级**。

##### 5.1.1.4 SQL 注入检测

SQL 注入检测是 Lymph AI 最简单但也最关键的参数。它检测文本字段中的 SQL 注入标签，立即将其默认值（`False`）切换为 `True`，并大幅降低“安全点”，因为任何被检测到的标签都表明可能存在入侵。通过简单的文本框输入搜索或验证脚本标记进行检测，表明有系统试图渗透并访问数据库。

此检测具有 **巨大的安全点下降值**。当 Lymph AI 接收到 `SQL Injection = True` 时，输出安全点会大幅下降，尽管其 **警报等级** 在系统层面上保持较低。

### 5.2 影响抗体 AI 的参数

抗体 AI 没有自己的参数；它使用由 Lymph AI 输出的参数。这些参数触发协议和 IRS（事件响应系统）。具体如下：

#### 5.2.1 安全点

Lymph AI 的主要输出生成安全点，它是衍生出两个额外参数的基础。这些参数在网络系统发生违规或违规尝试时发挥着至关重要的作用。安全点被严格组合到定义的限制内，从而产生抗体 AI 功能中使用的两个新参数。这种系统性关系强化了整体安全架构，提供了强大的防御机制。

安全点还为 **GPT AI（即抗体 AI）** 简化了 AI 输入，使其能够扫描即将到来的输入并判断是否存在违规条件，而无需处理所有原始参数。

#### 5.2.2 潜在违规百分比 (PBP)

由于违规检测不适应纯数字点数，安全点被处理为一个百分比变量：**潜在违规百分比 (PBP)**。该参数允许管理员和用户实时验证入侵可能性。它是一个为用户和网络安全专家显示而优化的半原始参数。

该百分比决定 **威胁等级**，并指示激活哪些 **安全协议** 和 **封锁协议系列**。然而，由于百分比对于 AI 违规检测仍非最优，它们被进一步处理为最终参数：**触发标志**。

#### 5.2.3 触发标志

**触发标志** 是从 **潜在违规百分比** 衍生出的布尔参数：

- 如果 `Breaching Percentage < 50%` → `Trigger Flag = False`
- 如果 `Breaching Percentage > 50%` → `Trigger Flag = True`

这简化了 **OpenAI API** 的输入处理，无需复杂的函数检查即可实现对入侵的轻松检测和响应。

这些参数检测违规并触发抗体 AI 协议。**图 11** 展示了抗体 AI 及其组件的 UML 图。

| 图 11. 抗体 AI 及其内部所有组件的 UML 图 |
| --- |
| ![Figure979-8-3693-1642-9.ch004.f11](img/ch004.f11.png) |

## 6. 未来研究方向

抗体 AI 连同 Lymph AI，是一系列计划项目中的首个装置。虽然检测对安全至关重要，但它仅是一个展示——指出问题而非完全解决问题。

我们的未来计划涉及一个 **终极 AI 集合**（或单一主控 AI），控制大量工具以解决网络大众媒体的所有问题。计算机时代的未来是人工智能的诞生。我们的主控 AI 计划价值高昂，利用 AI 实现：

- 侦察
- 故障排除
- 检测
- 预防
- 响应攻击
- 攻击分类
- 对攻击者实施反击
- 在系统内执行修复措施
- 协同恢复并保护重要文件
- 以及通过 **大语言模型 (LLMs)** 实现的更多功能。

简单而微妙的动机往往执行得更快、更容易。该方案围绕主 AI 或大脑 AI 展开，控制其他所有 AI 的组件或其他工具（如我们的抗体 AI），以进行检测；作为额外收益，主 AI 通过原始输入因素训练其他 AI，并增加了可能性，例如立即在软件中发现病毒代码、创建新防火墙、检测通过 Shell 或批处理可执行文件进行的远程访问等，从而使我们的工作环境和系统免受所有可能的恶意软件入侵和黑客攻击。

如果该领域的 AI 领域获得更多丰富的升级，我们将利用这一 AI 和其他 AI 的集合，创建项目的更大组成部分、用于此特定密码学目的的 AGI 模型和 AGI 仿真模型，并将其应用于所有基础设施和业务系统，以有效提高安全性。

## 7. 结论

本章解释了通过集成 OpenAI API 和其他算法，利用 AI 进行动态加密密钥交换和入侵检测。本章使用 OpenAI API 和其他机器学习算法创建了一个终极的基于 AI 的 IDS，它以四种不同的日志作为输入，通过另一个 AI 处理后输出少量参数，如“安全点”。这些标志尝试检查 AI 监控下的任何系统中是否存在入侵或违规，一旦检测到违规，它会使用其安全协议调用行动、锁定协议以隔离并保护未受影响的系统。最后，事后响应机制部门清理损害并动态随机更改加密。我们希望这些信息能作为进一步研究的关键，鼓励个人在这个无尽的知识领域中探索和发展这一概念。科学探索的协作性质依赖于研究人员的集体努力，我们渴望本文能为该领域正在进行的集体知识智慧做出贡献。

## 参考文献

Bailey, M., Oberheide, J., Andersen, J., Mao, Z. M., Jahanian, F., & Nazario, J. (2007). Automated classification and analysis of internet malware. In International Workshop on Recent Advances in Intrusion Detection. Springer. doi:[10.1007/978-3-540-74320-0_10](https://doi.org/10.1007/978-3-540-74320-0_10)

BilgeL.KirdaE.KrügelC.BalduzziM. (2011). EXPOSURE: Finding Malicious Domains Using Passive DNS Analysis. Network and Distributed System Security Symposium.

CanaliD.RobertsonW.KirdaE.KruegelC.VignaG. (2011). A Large-Scale Analysis of the Security of Embedded Firmwares. Proceedings of the 18th Annual Network and Distributed System Security Symposium.

CovaM.KruegelC.VignaG. (2010, April). Detection and analysis of drive-by-download attacks and malicious JavaScript code. In Proceedings of the 19th international conference on World wide web (pp. 281-290). ACM. doi:[10.1145/1772690.1772720](https://doi.org/10.1145/1772690.1772720)

Gala, Y., Vanjari, N., Doshi, D., & Radhanpurwala, I. (2023). AI based Techniques for Network-based Intrusion Detection System: A Review. 2023 10th International Conference on Computing for Sustainable Global Development (INDIACom), 1544-1551.

GonzálezG. G.CasasP.FernándezA. (2023, July). Fake it till you Detect it: Continual Anomaly Detection in Multivariate Time-Series using Generative AI. In 2023 IEEE European Symposium on Security and Privacy Workshops (EuroS&PW) (pp. 558-566). IEEE. doi:[10.1109/EuroSPW59978.2023.00068](https://doi.org/10.1109/EuroSPW59978.2023.00068)

GrierC.BallardL.CaballeroJ.ChachraN.DietrichC. J.LevchenkoK.MavrommatisP.McCoyD.NappaA.PitsillidisA.ProvosN.RafiqueM. Z.RajabM. A.RossowC.ThomasK.PaxsonV.SavageS.VoelkerG. M. (2012). Manufacturing compromise: the emergence of exploit-as-a-service. Proceedings of the 2012 ACM conference on Computer and communications security. doi:[10.1145/2382196.2382283](https://doi.org/10.1145/2382196.2382283)

HolzT.GoreckiC.RieckK.FreilingF. C. (2009). Measuring and Detecting Fast-Flux Service Networks. Proceedings of the 14th European Conference on Research in Computer Security.

Joshi, N., Sheth, T., Shah, V., Gupta, J., & Mujawar, S. (2022). A Detailed Evaluation of SQL Injection Attacks, Detection and Prevention Techniques. 2022 5th International Conference on Advances in Science and Technology (ICAST), 352-357. doi:[10.1109/ICAST55766.2022.10039662](https://doi.org/10.1109/ICAST55766.2022.10039662)

Kandhro, I. A., Alanazi, S. M., Ali, F., Kehar, A., Fatima, K., Uddin, M., & Karuppayah, S. (2023). Detection of Real-Time Malicious Intrusions and Attacks in IoT Empowered Cybersecurity Infrastructures. IEEE Access : Practical Innovations, Open Solutions, 11, 9136–9148. doi:[10.1109/ACCESS.2023.3238664](https://doi.org/10.1109/ACCESS.2023.3238664)
