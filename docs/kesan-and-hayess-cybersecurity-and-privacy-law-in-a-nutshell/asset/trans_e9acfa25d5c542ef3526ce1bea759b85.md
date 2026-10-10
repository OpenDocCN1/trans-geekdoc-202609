

# 第 2 章

## 网络安全技术与行为体

本章将介绍与网络安全相关的技术。虽然精通技术的律师日益增多，但大多数律师并没有技术背景。有些律师能够自己组装和维修电脑，但这种专业知识并非理解和领会网络安全相关法律问题的必要条件。然而，掌握一些概念和术语的知识很重要，这也是我们准备本章作为面向律师的技术入门指南的原因。

### I. 安全故事会

因为律师习惯于详细的假设情境，我们决定以这种熟悉的形式介绍网络安全事件的常见要素。下面是一个故事，它将提供本章全文将反复引用的人物和示例。与真实个人或公司的任何相似之处纯属巧合。

Carrie 是 Compbiz 公司的 CEO，该公司是软件解决方案行业的领导者。Carrie 和她的员工都很谨慎，但就像任何软件一样，Bug 偶尔也会进入成品。

Sam 是一家计算机安全公司的 CEO。他的公司 Securesoft 已成为安全解决方案行业的领导者。Securesoft 的业务活动涵盖了安全领域的全谱系。Securesoft 设有专门部门，分别专注于发现软件漏洞、防止计算机病毒传播、开发新的加密技术以及检测入侵。

Robert 是在线零售商 Retailco 的 CEO。Retailco 同时使用 Compbiz 和 Securesoft 的产品。

因为没有黑客的网络安全故事是不完整的，所以我们设定了三位：Wilma、George 和 Brian。Wilma 受雇于 Securesoft，解决网络安全问题是她工作的一部分。George 是一名系统管理员，从事自由安全工作，有时会将产品漏洞信息出售给相关公司，通常以“漏洞赏金”的形式。Brian 是一名程序员，通过入侵其他系统、窃取信息并在黑市出售来补贴收入。这三人分别代表网络安全评论中常提到的白帽、灰帽和黑帽黑客类别。

在最新版本中，Compbiz 的旗舰产品增加了一项新功能，允许用户在远程编辑数据库时拥有更多控制权。这对 Retailco 来说是一大优势，因为它使问题能够快速修复，而无需等待程序员到办公室。不幸的是，其中一行代码存在缺陷，可能允许未经授权的用户夺取数据库的控制权。

George 和 Brian 大约在同一时间发现了该缺陷。George 联系 Compbiz 告知该缺陷，并表示希望在几个月后的一个安全会议上演示该缺陷，给 Compbiz 足够的时间来修补漏洞。与此同时，Brian 编写了利用该缺陷的恶意软件，并开始琢磨如何利用它从公司数据库窃取信用卡号等信息。等到 Brian 的攻击代码准备就绪时，Compbiz 已为软件 2.1 版本的用户修补了该缺陷。不幸的是，Retailco 尚未更新其系统，因此仍在使用 2.0 版本。

Brian 部署了一个包含利用该安全缺陷的恶意代码的网站。得益于他早先使用的一个病毒，他已经控制了数千台计算机，将它们变成了僵尸网络，以便大规模执行他的指令。他利用其中一个僵尸网络向大量电子邮件地址（包括数百个 Retailco.com 地址）发送钓鱼邮件。该邮件声称与纳税申报信息有关，但点击邮件中的链接会将用户带到 Brian 的恶意网站。Retailco 的行政助理 Andrew 收到钓鱼邮件并点击了链接。因为 Andrew 使用的是 Compbiz 产品的 2.0 版本，他的电脑被感染了。Brian 在查看钓鱼活动结果时发现了这一点，并利用 Andrew 的受感染机器访问了 Retailco 的客户数据库。Brian 设法下载了 3,000 个客户档案，其中包括未加密的信用卡信息，随后触发了 Retailco 的 Securesoft 品牌入侵检测警报。

Brian 迅速带着信息潜逃，留下 Retailco 应对后果。他在黑市上出售信用卡号列表。大多数被盗信用卡由 BigBank 发行，该银行为客户提供欺诈保护。大多数信用卡在被使用前就已注销，但 BigBank 仍需支付 100,000 美元的欺诈性消费，并额外支付 10,000 美元重新发行所有受影响的卡片。

作为律师，上述任何行为体都可能成为您的客户。作为 CEO，Carrie、Sam 和 Robert 都很可能被要求解释或为其公司的行为辩护。Retailco 可能会被 BigBank 或其客户起诉。Compbiz 可能需要关于其产品潜在法律责任的建议。Compbiz 还可能寻求禁令阻止 George 发布其研究结果，或者指控 Securesoft 在违规事件后的调查中未能履行承诺。如果 Retailco 客户的信息泄露，他们可能会订阅信用监控服务。

上述例子是相对简单的例子之一。黑客可以以保护较弱的分包商为目标，以获取对大型组织的访问权限。Target 公司遭遇的即是这种情况，黑客通过第三方制冷承包商进入了 Target 的系统。此外，黑客还可能危及关键基础设施（如大容量电力系统），甚至以飞机、汽车和医疗设备为目标，这些都构成了重大风险。

### II. 计算机与软件

卡尔·萨根曾睿智地观察道：“如果你想从头做一个苹果派，你必须先发明宇宙。”许多人将这句话理解为指万物皆建立在早期创新之上。没有任何事物存在于真空中。面包师对烹饪科学的理解越深，就越能调整配方以获得最佳结果。本章讲的就是网络安全语境下的这种理解。任何人都能照着食谱做菜。改进则需要对食谱为何奏效有相当不错的理解。

## 参考文献

[3] Gary D. Brown & Andrew O. Metcalf, *Easier Said Than Done: Legal Reviews of Cyber Weapons*, 7 J. Nat’l Security L. & Pol’y 115, 126 (2014). Available at: https://www.westlaw.com/Document/Ib47b2062945711e38578f7ccc38dcbee/View/FullText.html?transitionType=Default&contextData=(sc.Default)&VR=3.0&RS=da3.0&fragmentIdentifier=co_pp_sp_186241_126

[4] Ponemon Institute, *2015 Cost of Data Breach Study*.

[5] Ponemon Institute, *2018 Cost of Data Breach Study*.

[6] *F.T.C. v. Wyndham Worldwide Corp.*, 799 F.3d 236 (3d Cir. 2015). Available at: https://www.westlaw.com/Document/I70e296b14a8d11e5a807ad48145ed9f1/View/FullText.html?transitionType=Default&contextData=(sc.Default)&VR=3.0&RS=da3.0

[7] Stipulated Order for Injunction, *F.T.C. v. Wyndham Worldwide Corp.*, Dec. 11, 2015. Available at: https://www.westlaw.com/Document/I70e296b14a8d11e5a807ad48145ed9f1/View/FullText.html?transitionType=Default&contextData=(sc.Default)&VR=3.0&RS=da3.0

