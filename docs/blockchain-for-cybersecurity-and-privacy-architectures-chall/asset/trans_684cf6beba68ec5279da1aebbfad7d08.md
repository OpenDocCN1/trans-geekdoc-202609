

# 内部审计与IT审计系列

# 用于网络安全与隐私的区块链：架构、挑战与应用

![](img/816c34830872ca25a809f80557c76d27_0_0.png)

编辑：
Yassine Maleh • Mohammad Shojafar
Mamoun Alazab • Immed Romdhani

![](img/816c34830872ca25a809f80557c76d27_0_1.png)

## 用于网络安全与隐私的区块链

## 内部审计与IT审计系列

系列编辑：Dan Swanson, Dan Swanson and Associates, Ltd., Winnipeg, Manitoba, Canada.

**《内部审计与IT审计》**出版面向审计高管以及内部及IT从业人员面临的关键主题的前沿书籍。关键主题包括审计领导力、网络安全、战略风险管理、审计各种IT活动和流程、审计管理以及运营审计。

**CISA 考试准备完全指南**
Richard E. Cascarino

**用于网络安全与隐私的区块链：** 架构、挑战与应用
编辑：Yassine Maleh, Mohammad Shojafar, Mamoun Alazab, Immed Romdhani

**网络安全知识体系：** ACM/IEEE/AIS/IFIP 网络安全完整课程的建议
Daniel Shoemaker, Anne Kohnke, Ken Sigler

**公司治理：** 审计师、董事会、投资者和会计师的实用指南
Vasant Raval

**审计价值因子**
Daniel Samson

**城市物联网系统管理**
Chuck Benson

**使用 CAATT 进行欺诈审计：** 审计师和法务会计师检测组织欺诈手册
Shaun Aghili

**如何构建具有网络韧性的组织**
Dan Shoemaker, Anne Kohnke, Ken Sigler

**审计师核心要义：** 成功的100个概念、技巧、工具和技术
Herman Murdock

**项目管理能力评估：** 执行基于 ISO 33000 的项目管理能力评估
Peter T. Davis, Barry D. Lewis

**物联网、为物物联网以及通过物联网**
Abhik Chaudhury

**供应链风险管理：** 确保安全采购原则以保障可信的技术产品
Ken Sigler, Dan Shoemaker, Anne Kohnke

**为什么 CISO 会失败：** 安全管理中缺失的环节以及如何修复
Barak Engel

有关本丛的更多信息，请访问：
https://www.crcpress.com/Internal-Audit-and-IT-Audit/bookseries/CRCINTAUDITA

## 用于网络安全与隐私的区块链
### 架构、挑战与应用

编辑：
Yassine Maleh
Mohammad Shojafar
Mamoun Alazab
Imed Romdhani

![](img/816c34830872ca25a809f80557c76d27_3_0.png)

第一版出版于2020年

由 CRC Press 出版
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

以及 CRC Press 出版
2 Park Square, Milton Park, Abington, Oxon, OX14 4RN

© 2020 Taylor & Francis Group, LLC

CRC Press 是 Taylor & Francis Group, LLC 的旗下品牌

我们已尽力发布可靠的数据和信息，但作者和出版者不承担追踪本书中再版的所有材料版权持有者的责任，也不承担所有材料的有效性或其使用的后果。作者和出版者已尝试追踪版权持有者，如果未获得以这种形式出版的许可，将向版权持有者道歉。如有任何版权材料未注明，请写信告知我们，以便我们在未来的任何重印中予以修正。

除美国版权法允许外，未经出版者许可，本书的任何部分不得以电子、机械或其他（无论现在已知还是以后发明的）形式重印、复制、传输或利用，包括复印、微缩和录制，或在存储或检索系统中。

如需许可复印或电子化使用本作品中的材料，请访问 www.crc.com 或联系许可中心 (CCC), 222 Rosewood Drive, Denver, MA 01923, 9750-8400。对于 CCC 上未提供的作品，请联系 mpbookspermissions@tandf.co.uk

商标声明：产品或运营名称可能是商标或注册商标，仅用于识别和扩展，无侵权意图。

## 图书目录出版数据

Males, Yasseh, 1988-编辑。
书名：用于网络安全与隐私的区块链：架构、挑战与应用 / Yasseh Males, Mohammad Shojafar, Mohammad Alazab, 和 Imed Romhani 编辑。
描述：第一版。 | Boca Raton, FL : CRC Press, 2020. | 系列：内部审计与IT | 包含参考文献和索引。
标识符：LCCN 2020009460 | ISBN 9780367343101 (平装) | ISBN 9780367437588 (精装) | ISBN 9780429324932 (电子书)
主题：LCSH: 区块链（数据库） | 计算机安全。
分类号：LC QA76.9.B56 2020 | DDC 005.8/3--dc23nLC 记录可用 https://lccn.org/2020009460

ISBN: 9780367437588 (hbk)
ISBN: 9780367433101 (pbk)
ISBN: 9780429324932 (ebk)

使用 Times 字体排版
由 Lumina Datamat Limited 提供

> 本书献给我爱的母亲 Fatima。

Yassine Maleh

![](img/816c34830872ca25a809f80557c76d27_6_0.png)

## 目录

前言 ................................................................................................ xi
序言 ................................................................................................ xiii
编辑者 ................................................................................................ xv
贡献者 ...................................................................... xix

## 第一部分 用于网络安全的区块链：架构与挑战

- 第 1 章 区块链威胁与漏洞分类法................................ 3
Ayman Alkhalifah, Alex Ng, A. S. M. Kayes, Jabed Chowdury, Mamoun Alazab, 以及 Paul A. Watters

- 第 2 章 分布式账技术的对比研究：区块链与哈希图................................29
Ariba Aslam Zahoor, Muhammad Mubashir Khan, 以及 Junaid Arshad

- 第 3 章 区块链设计实验室练习................................................57
Hongmei Chi, Bertony Bornel, 以及 Angela R. Martin

- 第 4 章 区块链安全及未来应用场景75

- 第 5 章 通向安全物联网：区块链解决方案、挑战与开放问题........85
Ranesh Kumar Naha, Sudheer Kumar Battulla, Khizahr Hameed, Md Anwar Kaium Patry, Saurabh Garg, 以及 Byeong Kang

## 第二部分 用于物联网安全与隐私的区块链

- 第 6 章 链：一种面向物联网的可扩展业务框架................117
Alireza Mokhtari Golpayegani, Mani Zarei, 以及 Alireza Souri

- 第 7 章 基于区块链的内容中心网络物联网中的信任与安全...............................141
Mohamed Labbi, Yassine Chahid, Nabil Kannouf, 以及 Mohamed Benabdallah

- 第 8 章 用于汽车网络的区块链安全...........................................................159
Anis Herbadji, Hadjer Goumidi, Yasmine Harbi, Khadidja Medani, 以及 Zibouda Aliouat

## 第三部分 用于医疗健康安全与隐私的区块链

- 第 9 章 当医疗服务遇上区块链技术...............................201
Gokay Saldamli, Pavan H. Ramesh, Karthika M. S. Nair, Roopashree Munegowda, Jeevan Venkataramana, 以及 Lo'ai A. Tawalbeh

- 第 10 章 用于医疗健康的区块链安全数据共享框架...............................................219
Raza Nowrozy, A. S. M. Keyes, Paul A. Watters, ...（略）

- 第 11 章 使用复合非同质化代币的药品防伪冒供应链系统...........................243
Ahmad Sghier Omar 和 Otman Basir

