
## 问答

**Q:** 服务器必须以何种模式启动才能执行 `Active Directory` 数据库的脱机碎片整理？

**A:** `Directory Services Restore Mode` 是一种特殊的启动模式，它不会初始化 `Active Directory` 数据库。因为它未被加载，所以可以对其执行低级操作；例如，移动和脱机碎片整理操作。

**Q:** 在性能控制台中，我应该监视 `Active Directory` 目录服务的哪个主要对象？

**A:** `NTDS` 对象是 Microsoft 为监视 `Active Directory` 提供的首要对象。它包含可用于监视目录服务的各个计数器。

**Q:** 我可以使用什么从命令行备份 `Active Directory`？

**A:** 可以使用 `Ntbackup` 命令结合 `systemstate` 选项从命令行备份活动目录。

**Q:** 在 `Windows Server 2003` 中，`Active Directory` 可能有哪些三种恢复类型？

**A:** Microsoft 在 `Windows Server 2003` 中新增了一种恢复类型，即 `primary restore`。在 `Windows 2000` 中受支持的 `normal`（以前称为非权威） 和 `authoritative restore` 类型也仍然可用。

**Q:** 我可以在 `Ntdsutil` 中使用哪些命令来验证 `Active Directory` 数据库的一致性？

**A:** 您可以使用 `integrity` 和 `semantic` 数据库分析命令来验证数据库的一致性。

**Q:** 我怀疑我的 `Active Directory` 数据库存在问题。我应该在 `Ntdsutil` 中运行修复选项吗？

**A:** 此选项不再存在于随 `Windows Server 2003` 提供的 `Ntdsutil` 版本中。它必须手动运行，使用带有 `/p` 开关的 `esentutl.exe` 命令，您应仅在高级支持人员的指导下或在 Microsoft 技术支持的指导下运行此命令。它仅用于在尝试了所有其他方法后作为最后的手段使用。使用此工具很可能会导致 `Active Directory` 数据丢失。

## 自测

快速答案键在自测题之后。有关本章以及本书其他章节中自测题的完整问题、答案和解释，请参阅自测附录。

### 了解 Active Directory 可用性问题

1. 您的主管询问您 `Active Directory` 如何知道哪些事务已提交到数据库。您解释说，这是在一个名为的文件中跟踪的：

A. `Edb.log`
B. `Ntds.dit`
C. `Edb.chk`
D. `Edb00001.log`

2. 您正在学习 `Windows Server 2003 Resource Kit`：为部署贵公司的新基础设施做准备。您了解到对 `Active Directory` 数据库的更新基于事务。以下哪些是事务的组成部分？（多选。）

A. 已由管理员或复制过程更改的现有 `Active Directory` 数据
B. 已由管理员或复制过程更改的新 `Active Directory` 数据
C. 描述对象的全部未更改信息
D. `Metadata`

3. 您向主管解释系统状态数据的重要性。您告诉她，其中包含的信息取决于底层操作系统中安装的组件。以下哪些您告诉她始终是 `Windows Server 2003` DC 上系统状态数据的一部分？（多选。）

A. 证书数据库
B. The `Registry`
C. The `Active Director)` 数据库
D. 元数据库
E. `SYSVOL`

4. 您正试图向同事解释 `Active Directory` 删除过程。尽管您尽了最大努力，他似乎无法理解垃圾回收过程的概念。您重申以下哪些关键点？（多选。）

A. 默认情况下，垃圾回收过程每 12 小时运行一次。
B. 数据库的脱机碎片整理会在垃圾回收过程结束时自动运行。
C. 垃圾回收过程会从 `Active Directory` 数据库中删除所有过期对象。
D. 垃圾回收过程会从 `Active Directory` 数据库中删除所有已封存对象。

### 执行 Active Directory 维护任务

5. 您的 `Windows Server 2003` DC 在包含数据库和日志文件的分区上磁盘空间不足。以下哪些步骤最能在此之前解决该情况，避免关键故障和额外的性能下降？（多选。）

A. 您可以使用 `NTFS` 压缩压缩数据库文件。
B. 您可以安装额外的硬盘。
C. 您可以使用 Windows 资源管理器移动 `Active Directory` 数据库和日志文件，然后重新启动服务器。
D. 您可以使用 `Ntdstuil` 实用程序移动 `Active Directory` 数据库和日志文件

6. 您最近开始了一份网络管理员的新工作。在审查您负责的服务器时，您注意到其中一个 DC 上的 `Active Directory` 无法启动。进一步调查显示，`Active Directory` 找不到日志文件的位置。您验证日志文件位于 `D:\\ADLogs` 目录中。以下哪些操作最适合解决此问题？

A. 您可以删除日志文件，以便自动重新创建它们。
B. 您可以启动到 `Directory Services Restore Mode` 并在 `Ntdsutil` 实用程序中使用 `set path logs` 命令。
C. 您可以启动到 `Directory Services Restore Mode` 并在 `Ntdsutil` 实用程序中使用 `move logs to` 命令。
D. 您可以直接修改 `Registry` 以便指向新位置。

7. 您已被提升为网络工程师，并正在培训帮助台人员晋升到您之前的网络管理员角色。您强调每天监控日志文件以尽早发现 `Active Directory` 问题的重要性。您指定以下哪些日志对新管理员来说很重要？（多选。）

A. The `System event log`
B. The `Application event log`
C. The `Directory Service event log`
D. The `File Replication Service event log`
E. The `DNS Server event log`

8. 您工作的网络工程师担心监控太多性能计数器的影响。她要求您将监控限制为核心目录服务性能对象及其计数器。以下哪些将允许您进行监控？

A. `DS Search sub-operations/sec`
B. `DRA inbound and outbound counters`
C. `Context Switches/sec`
D. `% DPC Time`

### 备份和还原 Active Directory

9. 您刚刚接手一份新工作，并正在审查备份日志。在您其中一个新 DC 上，日志显示 `Active Directory` 数据库备份失败。它还显示操作系统的几个关键组件，例如 `Registry`，甚至未被选中进行备份。以下哪种是最好的选择，以确保这些关键系统组件得到备份？

A. 验证是否启用了 `Volume Shadow Copy`
B. 选择备份 `system state data`
C. 启用完整系统备份
D. 验证驱动器上是否有足够的可用空间来保存影子副本

10. 您的同事一直在尝试编写系统状态数据自动还原脚本，但未成功。他向您寻求帮助。您告诉他什么？

A. 使用 `Ntbackup` 编写还原脚本需要宏。
B. A `CMD` 文件必须用于编写还原脚本。
C. A `BAT` 文件必须用于编写还原脚本时。
D. 使用 `Ntbackup` 实用程序编写还原脚本是不可能的。

11. 周末，一场龙卷风袭击了贵公司堪萨斯州的办公室。您到达时发现没有运行的 DC。该办公室在贵公司的林中拥有自己的域。重复硬件预计两天后到达，异地备份磁带明天应该到达。您将对该设施的三个 DC 使用以下哪些还原方法？（多选。）

A. `Primary`
B. `Normal`
