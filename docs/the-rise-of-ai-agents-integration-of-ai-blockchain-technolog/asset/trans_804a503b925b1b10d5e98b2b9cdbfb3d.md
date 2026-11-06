
![cover-image](graphics/9780135352939.jpg)

# 人工智能代理的崛起
## 人工智能、区块链技术与量子计算的融合
### Petar Radanliev

## 早期发布读者须知

使用早期发布电子书，您可以在作者撰写时获得书籍的最早形式——作者的原始未编辑内容，从而在这些标题正式发布之前很久就能利用这些技术。

如果您对我们如何改进本书的内容和/或示例有任何建议，或如果您注意到该书中缺少材料，请联系 Pearson，邮箱为 [PearsonITAcademics@pearson.com](mailto:PearsonITAcademics@pearson.com)

![Images](graphics/pub.jpg)

Boston • Columbus • Indianapolis • New York • San Francisco • Amsterdam • Cape Town

Dubai • London • Madrid • Milan • Munich • Paris • Montreal • Toronto • Delhi • Mexico City

São Paulo • Sydney • Hong Kong • Seoul • Singapore • Taipei • Tokyo

制造商和销售商用来区分其产品的许多名称均已申请商标。在本书中出现这些名称且出版商已知有商标声明的情况下，这些名称均以首字母大写或全部大写形式印刷。

作者和出版商在本书的准备工作中已尽最大努力，但不对任何明示或暗示的保证承担责任，也不承担因错误或遗漏而产生的责任。对于因使用本信息或程序而产生的或与之相关的附带或后果性损害概不负责。

有关批量购买本书或特殊销售机会（可能包括电子版本；定制封面设计；以及针对您业务、培训目标、营销重点或品牌利益的特定内容）的信息，请联系我们的企业销售部门，邮箱 [corpsales@pearsoned.com](mailto:corpsales@pearsoned.com) 或电话 (800) 382-3419。

如有政府销售咨询，请联系 [governmentsales@pearsoned.com](mailto:governmentsales@pearsoned.com)。

有关美国境外销售的问题，请联系 [intlcs@pearson.com](mailto:intlcs@pearson.com)。

访问我们的网站：[informit.com/aw](http://informit.com/aw)

图书馆国会控制号：

版权所有 © 2025 Pearson Education, Inc.

保留所有权利。美国印刷。本出版物受版权保护，未经出版商许可，不得以任何形式或任何手段进行禁止的复制、存储在检索系统或传输，包括电子、机械、影印、录音等。如需了解许可信息、申请表格以及 Pearson Education 全球权利与许可部门的相应联系人，请访问 [www.pearsoned.com/permissions/](http://www.pearsoned.com/permissions/)。

ISBN-13: 978-0-13535-294-6  
ISBN-10:

ITP 产品管理总监
Brett Bartow

执行编辑
James Manly

管理编辑
Sandra Schroeder

开发编辑
Christopher A. Cleveland

高级项目编辑
校对编辑
技术编辑
Omar Santos

编辑助理
Cindy Teeters

书籍设计师
封面设计师
排版
索引员
审校
内页设计师
封面设计师
排版员
图形

基于 Q Learning 类型强化学习的 AI 代理与量子计算的整合代表着迈向通用人工智能（AGI）和技术奇点的一次潜在飞跃，技术奇点是指 AI 超越人类智能、从根本上改变社会并成为地球上最高形式的智能的临界点。诸如 Grover 和 Shor 的量子算法将指数级增强 AI 在优化和密码分析方面的能力，加速 AGI 的演进。这种巨大的新力量不会容易控制，这引发了重大的安全问题，特别是在密码韧性方面。最快的解决方案在于后量子密码学，如基于格和基于哈希的密码学，它确保即使是量子驱动的 AI 也无法破坏数据完整性。但这还不够，我们可以预期会发生入侵。我们需要能够审计网络攻击。区块链技术通过其去中心化和不可篡改的账本，为记录交易和 AI 决策提供了一个透明、不可篡改的账本，从而提供问责制并防止 AGI 被滥用。通过解决这些挑战，我们可以在降低奇点相关风险的同时利用 AGI 的好处。 - *博士 Petar Radanliev, 牛津大学, 2024年8月*

## 目录

### [第一部分：先进技术的基础（1页书籍部分分隔符）](#part01.html#part01)
#### [第1章，人工智能代理、区块链和量子计算简介（19页，1幅线图）](#ch01.html#ch01)
#### [第2章，人工智能向人工智能代理的推进（22页，2张屏幕截图，2幅线图）](#ch02.html#ch02)
#### [第3章，人工智能代理和区块链技术的数字信任（26页，3幅线图）](#ch03.html#ch03)
#### [第4章，量子计算与人工智能代理（35页，3幅线图）](#ch04.html#ch04)

### [第二部分：增强应用的融合（1页书籍部分分隔符）](#part02.html#part02)
#### [第5章，去中心化人工智能代理（32页，1幅线图）](#ch05.html#ch05)
#### [第6章，量子人工智能代理（43页，8幅线图）](#ch06.html#ch06)
#### [第7章，区块链、量子与人工智能代理（46页，7幅线图）](#ch07.html#ch07)

### [第三部分：对社会和伦理的影响（1页书籍部分分隔符）](#part03.html#part03)
#### [第8章，人工智能代理的伦理（31页，4幅线图）](#ch08.html#ch08)
#### [第9章，塑造人工智能代理未来发展的法律框架和全球标准（32页，0幅图）](#ch09.html#ch09)
#### [第10章，社会影响与自主人工智能系统的兴起（57页，0幅图）](#ch10.html#ch10)
#### [附录：测试你的技能答案（待定 – 由第1-10章中包含的答案构建）](#appa.html#appa)

## 目录

### [第一部分：先进技术的基础（1页书籍部分分隔符）](#part01.html#part01)
#### [第1章。人工智能代理、区块链和量子计算简介](#ch01.html#ch01)
##### [虚构故事（第1部分）：Jovan 的故事](#ch01.html#ch01lev1sec1)
##### [人工智能代理的基础](#ch01.html#ch01lev1sec2)
##### [塑造人工智能代理发展的技术创新：AI/ML、区块链和量子计算](#ch01.html#ch01lev1sec3)
##### [融合](#ch01.html#ch01lev1sec4)
##### [摘要](#ch01.html#ch01lev1sec5)
##### [参考文献](#ch01.html#ch01lev1sec6)
##### [测试你的技能](#ch01.html#ch01lev1sec7)
##### [多项选择题](#ch01.html#ch01lev1sec8)

#### [第2章。人工智能向人工智能代理的推进](#ch02.html#ch02)
##### [神经网络与深度学习的兴起](#ch02.html#ch02lev1sec1)
##### [强化学习：通过交互学习](#ch02.html#ch02lev1sec2)
##### [Q学习：一种离策略 RL 算法](#ch02.html#ch02lev1sec3)
##### [神经图灵机：连接 AI 与记忆](#ch02.html#ch02lev1sec4)
##### [未来方向](#ch02.html#ch02lev1sec5)
##### [摘要](#ch02.html#ch02lev1sec6)
##### [参考文献](#ch02.html#ch02lev1sec7)
##### [测试你的技能](#ch02.html#ch02lev1sec8)
##### [多项选择题](#ch02.html#ch02lev1sec9)

#### [第3章。人工智能代理和区块链技术的数字信任](#ch03.html#ch03)
##### [区块链作为分布式账本的本质](#ch03.html#ch03lev1sec1)
##### [以太坊与区块链生态系统的演进](#ch03.html#ch03lev1sec2)
