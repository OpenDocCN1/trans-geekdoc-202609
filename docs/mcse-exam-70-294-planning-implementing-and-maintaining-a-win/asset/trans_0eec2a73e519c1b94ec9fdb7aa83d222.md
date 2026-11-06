
## 信任密码同步

☑ D. 信任会定期自动更改其密码。对目录进行权威还原（而不仅仅是某些部分）可能会还原信任使用的旧密码。然后就会不同步并导致信任失败。如果没有有效的信任来允许跨域身份验证，用户只能访问其本地域中的资源。

![错误](images/wrong.png) 答案 A 不正确，因为 Managers 组存在于 BOOC 域中，而还原是在 BST 域中进行的，因此该组仍然存在。如果删除或替换信任的密码，信任本身仍然存在；因此，答案 B 不正确。Managers 组不在还原发生所在的 BST 域中。此外，一旦对象被分配了其 SID，就不存在旧 SID 这种说法。对象可以重命名，但 SID 保持不变；因此，答案 C 不正确。

## 9. 使用 [图 7.48](#B9781931836944500180_1.xhtml#f0050) 中的图表，确定可以包含在连接到 FS2 的磁带设备的日常备份例程中的数据。

A. 网络 1：DC1 上的 AD；FS1

![图 7.48 备份域](images/B9781931836944500180/a01-09-9781931836944.jpg)

图 7.48 备份域

6. 网络 2：FS2；IIS

7. 网络 3：Email；FS3；FS4

B. 网络 1：FS1

8. 网络 2：DC2 上的 AD；FS2；IIS

9. 网络 3：Email；FS3；FS4

C. 网络 1：FS1

10. 网络 2：FS2；IIS

11. 网络 3：DC3 上的 AD；Email；FS3；FS4

D. 网络 1：FS1

12. 网络 2：FS2；IIS

13. 网络 3：Email；FS3；FS4

☑ D. 唯一可能的答案是 D，因为其他三个都不可能。为什么？它们各自将 Active Directory 列为备份到磁带的备份的一部分。系统状态，其中 Active Directory 是其一部分，需要与您正在备份的设备进行直接本地连接。[图 7.48](#B9781931836944500180_1.xhtml#f0050) 中的磁带设备本地连接到 FS2，而 FS2 不是 DC；因此，Active Directory 无法备份。

![错误](images/wrong.png) 答案 A、B 和 C 因与正确答案中所述的相同原因而不可能。在 [图 7.48](#B9781931836944500180_1.xhtml#f0050) 中，Active Directory 无法备份，因为磁带设备未本地连接到任何 DC。

## 10. Brayden 是多站点 Windows Server 2003 域的域管理员。总部位于印第安纳州南本德。正在加利福尼亚州圣何塞远程开设一个新分支。Brayden 需要在新的圣何塞站点放置两个 DC。WAN 链路还需要两周才能开通，但他希望本周就能让 DC 上线并就位，以便他的圣何塞技术人员立即开始在圣何塞设置工作站。在 WAN 安装之前，Brayden 可以做什么来创建这些 DC？

A. 在南本德创建两个 DC，然后将服务器运送到圣何塞。

B. 在南本德创建一个 DC 的备份到 CD 或 DVD 并运送到圣何塞。

C. 在圣何塞创建 DC，然后在 WAN 链路安装后，将它们与南本德的 DC 同步。

D. 什么都不做。Brayden 必须等待 WAN 链路后再创建远程站点的 DC。

☑ A. 要在同一域内创建 DC，您必须有一个可用的现有 DC 进行身份验证，然后进行同步。

![错误](images/wrong.png) 答案 B 是一个不错的选择，只是 DC 还原后需要连接到现有 DC，而在没有 WAN 链路的情况下这是不可用的。答案 C 不正确，因为在没有现有 DC 可用的情况下，您无法在同一域内创建额外的 DC。答案 D 不正确，因为 Brayden 可以做一些事情：将两个 DC 安装在南本德并快递运送到圣何塞。

### 管理操作主控

## 11. James 周一来上班并打开 Active Directory 用户和计算机。他的今天的任务是创建三个新用户并创建一个新组。James 尝试这样做但反复失败。他知道上周末一个 DC 宕机了，但他没有连接到该 DC，并且可以看到 Active Directory 中的所有对象。用户登录也完全正常。无法在 Active Directory 中创建新对象的可能解释是什么？

A. James 未以 Schema Admin 身份登录。

B. 宕机的 DC 上有 Domain Naming FSMO。

C. 宕机的 DC 上有 RID FSMO。

D. 宕机的 DC 上有 Schema FSMO。

E. 宕机的 DC 上有 PDC Emulator。

☑ C. 域中的所有新对象都需要唯一的 SID。RID 保留一组唯一的 SID，以便在创建对象时发放。

![错误](images/wrong.png) 答案 A 不正确，因为 Schema Admins 的成员授予修改架构的权限，与在 Active Directory 中创建新对象无关。James 只需要是 Domain Admin 即可创建新对象。Domain Naming FSMO 管理林中域的名称，而不是域中对象的名称，因此答案 B 不正确。答案 D 不正确，因为 Schema FSMO 仅控制架构的扩展，与在 Active Directory 中创建对象无关。答案 E 不正确，因为 PDC Emulator 控制 Active Directory 向 Windows NT 4 BDC 的复制，是每个域所有密码的主副本，与创建 Active Directory 对象无关。

## 12. Ryan 是 Astronauts Ltd 的域管理员。这是一个包含五个站点的多域树。今天，他必须将一些用户添加到 Marketing 组。他使用 ADUC 打开该组并添加来自 [SD.CA.COM](http://www.SD.CA.COM) 域的用户 Brayden 和 Hannah。来自 [LA.CS.COM](http://www.LA.CS.COM) 域的用户 Rebecca 和 McKay 已是该组的成员。在测试这些用户对 Marketing 部门使用的 Contact 数据库的访问时，Ryan 发现用户 Brayden 和 Hannah 仍然无法访问数据库，而 Rebecca 和 McKay 可以。以下哪一项是在诊断此问题时适用的故障排除步骤？

A. 验证该组是否为分发列表。

B. 验证该组是否为本地组。

C. 验证 RID FSMO 是否在线且可用。

D. 验证 Infrastructure FSMO 是否在线且可用。

☑ D. Infrastructure FSMO 缺失的症状是组创建失败或无法将用户添加到组。Infrastructure FSMO 负责在域之间更新 Active Directory 对象，并且可能是不一致的组成员问题的原因。所有 FSMO 对域的管理都很重要，确保它们在线且可用是一个良好的故障排除步骤。 （注意：Infrastructure FSMO 在此角色中是一个助手，给出足够的时间后，该组可能会赶上并正常工作。）

![错误](images/wrong.png) 答案 A 不正确，因为分发列表无法分配权限，而该组需要权限。答案 B 不正确，因为该组需要是全局组，并且在存在多个域并且希望为域中的其他域分配组权限时使用域中的本地组。答案 C 不正确，因为 RID FSMO 管理新对象创建所需的唯一 SID，而在此场景中，所有对象已存在；因此 RID FSMO 与此问题无关。

## 13. 作为 Sports Agents of America（SAA）的企业管理员，您必须将新收购的机构的域作为 SAA.us 的子域迁移到现有林中。新机构名为 Alternative Sports, Inc。新的 Windows Server 2003 域称为 AS。 [图 7.49](#B9781931836944500180_1.xhtml#f0055) 显示了 SAA.us 的当前域和站点拓扑。为了设置迁移，您首先要创建子域 AS.SAA.us。这反复失败。可能的原因是什么？

A. 位于 Montana 站点的 Domain Naming FSMO 已离线。

B. 位于 Montana 站点的 Schema FSMO 已离线。

