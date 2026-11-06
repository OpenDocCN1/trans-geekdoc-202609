
## DFS 拓扑修复步骤

1. 使用 `DFS MMC snap-in` 或 `dfsutil.exe` 实用程序检查 DFS 拓扑。第一步是准备一份 DFS 根列表，其中根路径、根复制服务器名称或链接目标服务器名称因重命名域而需要修复。后续步骤描述了何时需要修复每个拓扑组件。请注意，`DFSutil.exe` 实用程序只能修复基于域的 DFS 根拓扑，而不能修复独立的 DFS 根。

2. 检查您的 DFS 拓扑中是否存在任何基于域的 DFS 根路径。当域名更改时，它们需要在拓扑中进行更改。例如，如果域 `zoo.net` 的名称更改为 `naturepre-serve.net`，那么名为 `\\zoo.net\\public` 的基于域的 DFS 根就需要更改为 `\\naturepreserve.nef\\public`。请记住，如果根路径使用域的 NetBIOS 名称，并且域的 NetBIOS 名称未更改，则无需修复。

3. 在域重命名过程中，任何基于域的 DFS 根复制主机名或链接目标主机名如果指定为完全限定 DNS 名称，则需要在 DFS 拓扑中进行更改。例如，由于域名更改，名为 `guppy.zoo.net` 的 DFS 复制服务器的 DNS 主机名可能会更改为 `guppy.naturepreserve.net`。同样，DFS 链接可能需要从 `\\poodle.zoo.net\\good places to bury a bone` 更改为 `\\poodle.naturepre-serve.net\\bones`。同样，NetBIOS 名称只有在重命名过程中被指示更改时才会更改。

4. 在控制站上，打开命令提示符并更改到 `RenameTools` 目录。对于需要修复前面描述的任何拓扑组件的每个 DFS 根，键入以下命令（整个命令必须在一行中键入）：`DFSutil /RenameFtRoot /Root:DFSRootPath /OldDomain:OldName/ NewDomain:NewName /Verbose`。请注意：
   - `DFSRootPath` 是要操作的 DFS 根；例如，`\\naturep-reserve.net\\public`。
   - `OldName` 是要在 DFS 根的拓扑中替换的确切旧名称。
   - `NewName` 是要在拓扑中替换旧名称的确切新名称。

5. 再次检查您已修复的 DFS 拓扑，以确认它反映了重命名的域。

6. 两次重新启动所有 DFS 根复制服务器以刷新 DFS 服务拓扑信息。

7. 对每个重命名的域重复步骤 1 到 6。您可以按顺序输入命令。

## 第 12 步：修复组策略对象和链接

每个重命名域中的 GPO 和 GPO 引用需要使用 `gpfixup.exe` 命令行工具进行修复，如 [练习 4.28](#B9781931836944500106_2.xhtml#b0155) 所示。这些 GPO 及其链接仍在其属性中嵌入旧的域名，在修复之前将无法正常运行。托管软件部署也受损，因为基于组策略的软件安装和维护数据（例如软件分发点网络路径）也可能基于域名。`Gpfixup.exe` 也会为您修复这些问题，并且需要在每个重命名的域中运行一次。此外，由于 GPO 不能引用应用程序目录分区，因此不需要对它们进行修复。此步骤完成了核心域重命名过程；但是，根据您的配置，如“域重命名后采取的步骤”部分所示，可能需要许多其他步骤。

### 练习 4.28 修复 GPO 和链接

1. 打开命令提示符。单击 开始 | 所有程序 | 附件 | 命令提示符。

2. 更改到 `RenameTools` 目录。

3. 在一行中键入此整个命令：`gpfixup /olddns:OldDomainDnsName /newdns:NewDomainDNSName /oldnb:OldDomainNetBIOSName /newnb:NewDomainNetBIOSName/dc:DcDnsName 2>&1 > gpfixup.log`。在这种情况下：
   - `OldDomainDnsName` 是重命名域的旧 DNS 名称。
   - `NewDomainDnsName` 是重命名域的新 DNS 名称。
   - `OldDomainNetBIOSName` 是重命名域的旧 NetBIOS 名称。
   - `NewDomainNetBIOSName` 是重命名域的新 NetBIOS 名称。
   - `DcDnsName` 是重命名域中 DC 的 DNS 主机名，最好是 PDC 模拟器。选择一个在步骤 8 中 `dclist.xml` 状态文件中以最终 Done 状态成功完成重命名操作的 DC。

![b04-35-9781931836944](images/B9781931836944500106/b04-35-9781931836944.jpg)注意
命令行参数 `/oldnb` 和 `/newnb` 只有在域的 NetBIOS 名称更改时才需要；否则，这些参数可以从 `Gpfixup` 的命令行中省略。此外，重定向的输出——状态和错误——都保存到文件 `gpfixup.log` 中，可以定期显示以监控命令的进度。

4. 要强制将组策略修复更改复制到重命名域中的其余 DC，请键入 `repadmin /syncall /d /e/P /q DcDnsName NewDomainDN` 然后按 Enter，在这种情况下：
   - `DcDnsName` 是 `gpfixup` 命令的目标 DC 的 DNS 主机名。
   - `NewDomainDN` 是对应于重命名域的新 DNS 名称的 DN。

![b04-02-9781931836944](images/B9781931836944500106/b04-02-9781931836944.jpg)注意
请记住，重命名域中 DC 的 DNS 主机名在域名更改时不会自动更改。除非您在此阶段手动将其更改为新名称，否则请使用旧名称。

5. 对每个重命名的域重复此过程中的步骤 3 和 4。您可以按顺序执行。对于两个域，执行两次 `gpfixup` 和两次 `repadmin`。对每个重命名的域不要运行超过一次 `gpfixup`，并且不要对重命名的应用程序目录分区运行它。

![b04-25-9781931836944](images/B9781931836944500106/b04-25-9781931836944.jpg)注意
GPO/链接修复过程不会修复跨域 GPO 链接。如果您的林中有这些链接，它们必须手动修复。这意味着中断并重新建立每个链接。它也不会修复外部域的软件分发点的网络路径。

## 域重命名后采取的步骤

按照本节中的说明操作，以确保所有依赖于准确域名的功能都已得到解决。主要关注点之一是您的企业 CA。

### 验证证书安全性

如果您使用企业证书，请在域重命名完成后执行以下所有过程。您的企业 CA 可以配置为同时使用 LDAP 和 HTTP URL 指向您的 CRL。在继续之前确定您的证书属性。

![b04-26-9781931836944](images/B9781931836944500106/b04-26-9781931836944.jpg)注意
如果您的企业证书中只有 LDAP URL，则在重命名域时所有先前颁发的证书将停止工作。更正 LDAP CDP 和 AIA 指针的唯一可用解决方法是续订整个 CA 层次结构并重新颁发所有最终实体证书。这将在您解决这些问题之前导致 PKI 中断。

### 域重命名后为 CDP 和 AIA 扩展准备 URL

为了确保域重命名后旧的企业证书正常运行，请创建 `CNAME` DNS 记录，将旧的 HTTP 服务器名称重定向到服务器的新 DNS 名称，如 [练习 4.29](#B9781931836944500106_2.xhtml#b0170) 所示。这是指服务于您 CA 的 CRL 的主机。通过此重定向，旧证书中的 HTTP URL 将继续有效。这是为了使客户端机器能够获取 CRL 和 CA 证书以供验证。

### 练习 4.29 配置重定向别名条目的 DNS

1. 单击 开始 | 管理工具 | DNS。

2. 展开 DNS 服务器条目。

3. 右键单击旧 DNS 区域。

4. 选择 新别名 (`CNAME`)。

5. 在 别名名称 框中，键入 HTTP 服务器的原始 FQDN。

6. 在 目标主机 的完全限定域名 框中，键入 HTTP 服务器的新 FQDN，然后单击 确定。
