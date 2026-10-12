

## 2.1.4 CIA 三要素与 McCumber 立方体的对比

McCumber 的信息安全模型或立方体确实具有相同的三个特征：机密性、完整性和可用性。然而，其完整模型包含三个维度，上述三个特征仅代表一个名为安全特征或目标的维度。另外两个维度是信息状态和安全防护措施。根据该模型，信息处于三种状态：存储、处理和传输。安全措施也主要分为三类：策略、教育和技术（图 2.1）。

![Figure 2.1 McCumber’s Cube of information security. (Data from McCumber, J., Information systems security: A comprehensive model, in: Proceedings of the 14th National Computer Security Conference, NIST, Baltimore, MD, 1991.)](images/pg35_1.jpg)

**图 2.1** McCumber 信息安全立方体。（数据来源：McCumber, J., Information systems security: A comprehensive model, in: *Proceedings of the 14th National Computer Security Conference*, NIST, Baltimore, MD, 1991。）

## 2.2 Parker 六要素

Donn B. Parker 提出了一个包含六个基本安全要素的模型，通常称为 *Parkerian Hexad*。除了经典 CIA 列表中的三个属性外，效用、真实性和占有是 Parker 新增的建议。他主要认为这三个 CIA 属性在定义和实践解释方面不够全面和精确，因此不足以涵盖所有可能性。因此，这三个新属性分别包含了在传统 CIA 属性解释中未被考虑的安全顾虑。

### 2.2.1 占有

Parker 详细阐述了信息的占有或对其的控制权不同于信息的机密性，因为即使控制信息的人没有查看它，对信息的未授权占有仍然是一个安全问题。在这种情况下，信息的机密性本身并未受损，但对占有权的侵犯日后可能导致机密性问题。因此，Parker 认为有必要将占有作为一个安全属性纳入其中，以避免信息控制权有意、无意或恶意地落入未授权实体手中的情况。计算机网络上的通信实际上是一个完美的例子，因为在大多数情况下物理网络是公开可访问的，这意味着如果不采取适当措施，任何人都可以控制正在进行的通信。

![Figure 2.2 Parker’s new fundamental conceptual information security model. (Data from D. Parker, Our excessively simplistic information security model and how to fix it, ISSA J., 8 (7): 12-21, July, 2010.)](images/pg37_1.jpg)

**图 2.2** Parker 的新基础概念信息安全模型。（数据来源：D. Parker, Our excessively simplistic information security model and how to fix it, *ISSA J*., 8 (7): 12-21, July, 2010。）

### 2.2.2 真实性

信息的真实性被定义为信息来源的有效性或对信息来源的确认。因此，该特征描述了信息的来源是否与接收者预期或假设的相同。Parker 解释说，真实性不同于完整性，因为后者关乎信息内容的可靠性和状况。有时，授权来源可能会生成不正确的信息或为测试目的而违背完整性的信息，从而不违背真实性。另一方面，恶意来源可能冒充他人，从而复制一份正确的信息，例如以自己的名义发布软件，但实际上是由不同实体开发的。Parker 进一步主张，缓解这两个问题所需的措施也是不同的。

### 2.2.3 效用

Parker 建议的最后一个增强项是效用，他将其定义为数据或信息的有用性。Parker 认为*可用性*一词仅限于信息的可用性，这并不总能保证信息也有用。例如，如果信息以加密形式交付，但接收者丢失了解密密钥，该信息仍然是可用的，但其效用为零。

### 2.2.4 CIA 三要素与 Parker 六要素的对比

CIA 三要素与 Parker 六要素的区别主要在于对所用术语的解释不同。毫无疑问，Parker 提到的顾虑并非不重要或不存在；然而，专业人士随着时间的推移已将这些扩展解释融合到了三个 CIA 属性中。

## 2.3 信息保障模型

Maconachy 等人提出的模型。

很难确定*认证*和*不可否认性*这两个术语的起源，因为它们大致在同一时期出现在多个来源中。例如，我们在 Parker 的六要素中看到了*真实性*。Maconachy 等人自己在。

![Figure 2.3 Information assurance model. (Data from Maconachy, W. et al., A model for information assurance: An integrated approach, in: Proceedings of the IEEE Workshop on Information Assurance and Security, U.S. Military Academy, New York, 2001.)](images/pg38_1.jpg)

**图 2.3** 信息保障模型。（数据来源：Maconachy, W. et al., A model for information assurance: An integrated approach, in: *Proceedings of the IEEE Workshop on Information Assurance and Security*, U.S. Military Academy, New York, 2001。）

### 2.3.1 认证

该模型中的认证是指验证 Parker 模型中*真实性*的一项服务。因此，它是用于验证信息发起者有效性的过程或措施。该术语在该模型中仅指措施，不包含特征；然而，NIST 在中提供的定义。

### 2.3.2 不可否认性

