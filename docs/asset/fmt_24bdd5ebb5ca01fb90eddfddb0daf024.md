
当 Web 应用程序向 Web 服务器发送数据请求时，数据库服务器会验证 Web 应用程序是否有权检索数据，如果有，数据库服务器会发送数据。然而，这涉及多个步骤。例如，数据库管理系统首先检索并解密数据，并以 Web 应用程序可以读取的方式对其进行格式化。然后，数据库服务器在传输前使用传输加密算法对数据进行加密。这确保了传输中的数据是安全的。

- [Web 应用服务器](https://example.org)接收加密格式的数据，对其进行解密后将数据发送至 Web 应用。Web 应用在使用数据以授权交易时，会将数据存储在临时内存缓冲区中。当 Web 应用不再需要该数据时，会采取措施清除内存缓冲区，确保所有残留的敏感数据均被彻底从内存中移除。

### 处理信息和资产

管理敏感数据的关键目标是防止数据泄露。数据泄露是任何未经授权的实体能够查看或访问敏感数据的事件。如果关注新闻，你大概经常会看到数据泄露的报道。如 2017 年的 Equifax 事故等大规模泄露事件经常登上主流新闻。Equifax 报告称，攻击者窃取了包括社会安全号码、姓名、地址以及出生日期在内的约 1.43 亿美国人个人数据。

然而，即使你可能从未听说小规模数据泄露，它们也在持续发生，2017 年平均每周就有超过 25 起报告的数据泄露。下面的章节列出组织内部人员为降低数据泄露风险而遵循的基本步骤。

#### 标记敏感数据和资产

标记（也称为标签）敏感信息，可让用户轻松辨识数据的分类级别。标记最重要的作用是指示数据的分类。例如，标记为“绝密”的信息让任何看到标签的人都能明确知道该信息属于绝密级别。当用户了解数据的价值后，更有可能根据分类采取相应的控制和保护措施。标记既包括实体标记也包括电子标记。

实体标签指示存储在介质或系统上处理的数据的安全分类。例如，若备份磁带包含机密数据，贴在磁带上的实体标签即表明该磁带存储机密数据。

同样，若计算机处理敏感信息，该计算机会标记其处理的最高分类信息。处理机密、绝密及绝密以上数据的计算机应标记为处理“绝密”数据。实体标签在系统或介质的全生命周期内保持存在。

标记还包括使用数字标记或标签。常见做法是将分类作为文档的页眉/页脚或作为水印嵌入，这些方式在打印件上也会显示。即使用户在打印时加入页眉页脚，大多数组织仍要求将印有敏感文档的纸张放入标有分类的文件夹或封面页中。页眉不限于文件，备份磁带通常也包含页眉信息，分类可写入该页眉中。

页眉、页脚和水印的另一优势是数据防泄漏（DLP）系统能够识别包含敏感信息的文档，并应用相应的安全控制。部分 DLP 系统在检测到文档包含敏感信息时，会在文档中添加元数据标签，这些标签提供对文档内容的洞察，帮助 DLP 系统正确处理文档。

同样，部分组织规定电脑桌面背景必须使用特定样式。例如，处理专有数据的系统可能拥有黑色桌面背景，上面用白色文字写有 `Proprietary`，并配有宽阔的橙色边框。背景还可能包含“本机处理专有数据”等声明，以及提醒用户保护数据的责任提示。

在许多安全环境中，人员也会为非机密介质和设备使用标签，以防止遗漏标记的错误。例如，若一卷存储敏感数据的备份磁带未标记，用户可能误以为其仅包含非机密数据。若组织同时标记非机密数据，则未标记的介质会更加显眼，用户在查看未标记磁带时会产生怀疑。

组织通常会制定介质降级的程序。例如，若备份磁带包含机密信息，管理员可能希望将其降级为非机密。组织会确定可信的程序，彻底清除磁带上所有可用数据。清除后，管理员可对磁带进行降级并更换标签。

然而，许多组织完全禁止介质降级。例如，数据政策可能禁止对包含绝密数据的备份磁带进行降级。相反，政策可能要求在磁带生命周期结束时销毁该磁带。同样，系统降级也很少见。换言之，若系统曾处理过绝密数据，很少会将其降级并重新标记为非机密系统。无论如何，必须制定经批准的程序，确保降级操作正确完成。

#### 处理敏感信息和资产

处理指的是在其全生命周期内安全传输介质的过程。根据数据的价值和分类，人员会采用不同的处理方式，显而易见，分类最高的信息需要更严格的保护。虽然这看似常识，但人们仍会犯错。许多时候，人们对敏感信息的处理变得麻木，保护措施松懈。

例如，2011 年英国国防部因回应信息自由请求，意外在网络上公开了核潜艇的机密信息及其他敏感信息。他们使用图像编辑软件对机密数据进行黑条处理，但任何试图复制该数据的人都能复制所有文字，包括已黑条的内容。

另一种常见情况是备份磁带的控制权丧失。备份磁带应获得与被备份数据同等级别的保护。即使用户在备份磁带上存储机密信息，该磁带也应被视为机密信息进行保护。然而，仍有许多情况未遵循此原则。例如，TD Bank 在 2012 年丢失两卷备份磁带，导致超过 26 万条客户记录数据泄露。与多数数据泄露一样，细节的披露耗时较长。TD Bank 在磁带丢失六个月后才向客户报告此事故。两年后，即 2014 年 10 月，TD Bank 最终同意支付 85 万美元并改进其做法。

更近期，AWS Simple Storage Service（S3）中存储的数据权限配置不当，导致数十 TB 的数据被公开。AWS S3 是云端存储服务，美国政府的 Outpost 计划公开收集社交媒体及其他网页数据。网络爬虫和监控社交媒体并不新鲜，但这些数据存放在名为 CENTCOM 的公开档案中，且未启用加密或权限限制。

- [Policies and procedures](https://example.org)需要制定以确保人们了解如何处理敏感数据。这始于确保系统和介质已适当标记。此外，正如雷根总统在讨论与苏联关系时所说的：“信任，但要验证。”第 17 章“预防和应对事件”讨论了日志记录、监控和审计的重要性。这些控制措施在重大损失发生前验证了敏感信息的适当处理。如果发生损失，调查人员使用审计日志帮助发现问题所在。因人员未正确处理数据而导致的任何事件应迅速调查，并采取行动防止再次发生。

#### 存储敏感数据

敏感数据应存储方式确保免受任何类型损失的保护。最明显的保护措施是加密。`AES 256` 提供强加密，且有众多应用程序可用于使用 `AES 256` 加密数据。此外，许多操作系统具备在文件级和磁盘级别加密数据的内置功能。

如果敏感数据存储在便携式磁盘驱动器或备份磁带等物理介质上，人员应遵循基本的物理安全措施，防止因盗窃导致的损失。这包括将这些设备存放在上锁的保险箱或金库中，或放置在包含多种额外物理安全控制的安全房间内。例如，服务器室包含防止未经授权访问的物理安全措施，因此在服务器室内上锁的柜子中存储便携介质可提供强有力的保护。

此外，应使用环境控制措施保护介质。这包括温度和湿度控制，如暖通空调（HVAC）系统。

这里有一个常被终端用户忽视的点：任何敏感数据的价值远高于存储该数据的介质的价值。换言之，购买高质量介质在数据长期存储（如备份磁带）时更具成本效益。同样，购买带内置加密功能的高质量 USB 闪存盘也是值得的投资。部分这些 USB 闪存盘采用指纹生物认证机制，提供了增强保护。

#### 消除敏感数据

当组织不再需要敏感数据时，人员应对其进行销毁。正确销毁可确保数据不落入错误之手导致未经授权披露。高度机密数据的销毁步骤与较低级别数据不同。组织的安全政策或数据政策应规定根据数据分类可接受的销毁方法。例如，组织可能要求对存储高度机密数据的介质进行彻底销毁，但允许人员使用软件工具覆盖低级别数据文件。

`NIST SP 800-88r1`，“介质清除指南”，提供了不同清除方法的详细信息。清除、清除和销毁等方法确保数据无法通过任何手段恢复。当处置计算机时，清除工作包括确保所有非易失性存储器已被移除或销毁；系统的任何光盘（CD/DVD）未存储在任何驱动器中；内部驱动器（硬盘和固态硬盘（SSD））已被清除、移除或销毁。清除可指介质的销毁，或使用可信方法在不销毁介质的情况下清除机密数据。

#### 消除数据残留

`数据残留` 是指数据在介质被 supposedly 擦除后仍然保留的现象。通常指硬盘上的残留磁通。使用系统工具删除数据通常会在介质上保留大量数据，且广泛可用的工具可轻松恢复已删除数据。即使使用高级工具覆盖介质，原始数据的痕迹仍可能以不易察觉的磁场形式残留。这类现象类似于长时间显示相同数据的电视或计算机显示器上可能残留的幽灵影像。取证专家和攻击者拥有工具，可在数据被 supposedly 覆盖后仍检索该数据。

消除数据残留的一种方法是使用消磁器。消磁器产生强磁场，可重新对传统硬盘、磁带和软盘驱动器等磁性介质的磁场进行实时对齐。使用电力的消磁器可可靠地重写磁场，从而消除数据残留。但它们仅对磁性介质有效。

相比之下，SSD 使用集成电路而非磁性介质。因此，对 SSD 进行消磁操作无法消除数据。即便采用其他方法清除 SSD 数据，残留数据往往仍然存在。在一篇题为《可靠擦除闪存固态硬盘数据的方法》（可查看 [www.usenix.org/legacy/event/fast11/tech/full_papers/Wei.pdf](http://www.usenix.org/legacy/event/fast11/tech/full_papers/Wei.pdf)）的研究论文中，作者发现传统的单个文件清除方法对 SSD 无效。

部分 SSD 包含内置擦除命令以清除整个磁盘，但遗憾的是，这些命令在不同厂商的部分 SSD 上效果不佳。鉴于这些风险，销毁 SSD 的最佳方法是物理销毁。美国国家安全局（NSA）要求使用经批准的 `disintegrator` 销毁 SSD，该设备可将 SSD 粉碎至 2 毫米（mm）或更小尺寸。许多组织销售多种经 NSA 批准的信息销毁和清除解决方案，这些方案被政府机构和私营企业广泛使用。

另一种保护 SSD 的方法是确保所有存储数据均已加密。若清除方法未能彻底清除所有数据残留，剩余数据将无法阅读。

以下列表包含一些与数据销毁相关的常见术语：

**Erasing** `Erasing` 介质仅是针对文件、文件集合或整个介质执行删除操作。在大多数情况下，删除或移除过程仅移除数据的目录或链接。实际数据仍保留在驱动器上。当新文件写入介质时，系统最终会覆盖已删除数据，但根据驱动器大小、剩余空闲空间及其他因素，数据可能在数月内才被覆盖。任何人都可使用广泛可得的恢复工具检索该数据。

**Clearing** `Clearing`，即 `overwriting`，是为重用介质并确保数据无法通过传统恢复工具恢复的过程。当介质被清除时，非机密数据会被写入介质的所有可寻址位置。一种方法是在整个介质上写入单一字符或特定位元模式。更彻底的方法是在整个介质上写入字符及其补码，随后写入随机位元，并分三次操作完成，如 `Figure 5.2` 所示。尽管这听起来像原始数据已永久丢失，但通过高级实验室或取证技术仍可能检索部分原始数据。此外，某些数据存储类型对清除技术不敏感。例如，硬盘的备用扇区、标记为“bad”的扇区以及许多现代 SSD 的区域可能未被清除，仍可能保留数据。

![FIGURE 5.2 Clearing a hard drive ](img/c05f002.jpg)

**FIGURE 5.2** Clearing a hard drive

**Purging** `Purging` is a more intense form of clearing that prepares media for reuse in less secure environments. It provides a level of assurance that the original data is not recoverable using any known methods. A purging process will repeat the clearing process multiple times and may combine it with another method such as degaussing to completely remove the data. Even though purging is intended to remove all data remnants, it isn’t always trusted. For example, the U.S. government doesn’t consider any purging method acceptable to purge top secret data. Media labeled top secret will always remain top secret until it is destroyed.

**Degaussing** A degausser creates a strong magnetic field that erases data on some media in a process called `degaussing`. Technicians commonly use degaussing methods to remove data from magnetic tapes with the goal of returning the tape to its original state. It is possible to degauss hard disks, but we don’t recommend it. Degaussing a hard disk will normally destroy the electronics used to access the data. However, you won’t have any assurance that all of the data on the disk has actually been destroyed. Someone could open the drive in a clean room and install the platters on a different drive to read the data. Degaussing does not affect optical CDs, DVDs, or SSDs.

**Destruction** Destruction is the final stage in the lifecycle of media and is the most secure method of sanitizing media. When destroying media it’s important to ensure that the media cannot be reused or repaired and that data cannot be extracted from the destroyed media. Methods of destruction include incineration, crushing, shredding, disintegration, and dissolving using caustic or acidic chemicals. Some organizations remove the platters in highly classified disk drives and destroy them separately.

`Declassification` involves any process that purges media or a system in preparation for reuse in an unclassified environment. Sanitization methods can be used to prepare media for declassification, but often the efforts required to securely declassify media are significantly greater than the cost of new media for a less secure environment. Additionally, even though purged data is not recoverable using any known methods, there is a remote possibility that an unknown method is available. Instead of taking the risk, many organizations choose not to declassify any media and instead destroy it when it is no longer needed.

#### Ensuring Appropriate Asset Retention

Retention requirements apply to data or records, media holding sensitive data, systems that process sensitive data, and personnel who have access to sensitive data. Record retention and media retention is the most important element of asset retention.
