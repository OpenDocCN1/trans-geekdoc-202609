
# 自测

A: 在这种情况下，你应该在每个位置都设置一个 `GC` 服务器并且可能设置站点。

快速答案键在自测问题之后。有关本章以及本书其他章节中自测问题的完整问题、答案和解释，请参阅自测附录。

## 使用全局编录和 GC 服务器

1. 你正在自己的 DC 上工作，想要运行 `Schema snap-in`。你点击 `Start` 并选择 `Run`。你输入 `MMC` 并按 `Enter`。当你去添加管理单元时，你没有看到它列为可以添加的一项。为什么？
A. 你所在的 DC 不是 `GC` 服务器，因此 `Schema Admin snap-in` 在该 DC 上不可用。
B. 你不是 `Schema Admins` 组的成员，因此无法安装管理单元。
C. 你登录的 DC 不担任 `Schema Master` 角色，因此管理单元将无法运行。
D. `schmmgmt.dll` 文件尚未注册。

2. 你刚刚完成了一个包含三个 DC 的林的设置。服务器 `DC1` 是林根 DC。服务器 `DC2` 和 `DC3` 也将作为 DC 使用。你想将 `GC` 责任分配给 `DC2`。现在如何确定哪个 DC 正在作为 `GC` 服务器提供服务？（多选）
A. 你可以在 `Active Directory Sites and Services` 管理工具中查看每个 Server 对象的属性，以确定服务器是否为 `GC` 服务器。
B. 你知道 `DC1` 是 `GC`，因为在林中首先设置的 DC 会自动承担 `GC` 角色。
C. 你可以在 `Active Directory Sites and Services` 中每个 Server 对象下的 `NTDS Settings` 的属性中查看。
D. 你知道 `DC3` 是 `GC` 服务器，因为第三个 DC 在被添加到域时，会从林根服务器接管 `GC` 角色。

3. 你有一个新属性需要添加到 `GC`。你已打开 `Schema Admin snap-in`。你如何确保一个属性包含在 `GC` 中？
A. 展开 Attributes 部分，右键单击你想要包含的属性并选择 Properties。在 General 选项卡上，确保选中 Replicate this attribute to the `GC`。
B. 展开 Attributes 部分，右键单击你想要包含的属性并选择 Properties。在 General 选项卡上，确保选中 Allow this attribute to be shown in advanced view。
C. 展开 Attributes 部分，右键单击你想要包含的属性并选择 Properties。在 General 选项卡上，确保选中 Index this attribute for containerized searches in the Active Directory。
D. 展开 Attributes 部分，右键单击你想要包含的属性并选择 Properties。在 General 选项卡上，确保选中 Index this attribute in the Active Directory。

4. 你最近将新员工设为名为 `Enterprise Admins` 的 `Universal Group` 的成员。该新员工位于分支办公室。当用户注销然后重新登录时，他注意到他无法访问某些管理工具。你最近将用户添加到 `Universal Group`，并且你在分支办公室和主办公室之间有一条 56 K 链路。你的 `GC` 服务器位于主办公室。可能是什么问题？（多选）
A. 你不能将用户添加到 `Universal Group`s，只能添加到 Global 和 Domain Local 组。
B. 你已打开 `Universal Group` 缓存，并且缓存信息自今天早上以来尚未刷新。
C. `GC` 数据在 `WAN` 链路上的传输失败。
D. `GC` 复制不支持 56 K 链路。

5. 你有一个主办公室和一个卫星办公室的网络。你的网络的功能级别为 `Windows 2000 Native`。卫星办公室有一个 DC。主办公室有一个 DC 和一个 `GC` 服务器。你遇到了主办公室和卫星办公室之间链路的问题。你担心用户将无法在卫星办公室登录域，因为他们无法访问 `GC`。令你惊讶的是，他们仍然能够登录到域。这是为什么？
A. 分支办公室的 DC 可能设置为缓存 `Universal Group` 信息，从而允许客户端仍然登录。
B. `GC` 对于登录不是必需的，仅在登录后搜索目录时才需要。
C. 卫星办公室的 DC 正在担任 `Schema Master` 角色并且可以在没有 `GC` 服务器的情况下进行身份验证。
D. 用户正在本地登录并且未对域进行身份验证。

6. 你有多个属于 `Default-First-Site-Name` 站点的地点。这些地点位于佛罗里达、俄勒冈和爱荷华。你已在每个地点部署了 `GC` 服务器。在监控你的网络时，你注意到地点之间有大量复制流量。你如何补救复制流量的数量以及该流量的处理方式？
A. 实施使用 `Subnet objects`
B. 实施使用 `Object classes`
C. 实施使用站点
D. 实施使用 `site connectors`

## 使用 Active Directory Schema

7. 你正在使用 `Schema Admin snap-in` 并且无法进行任何更改。你在林根域中创建了一个等同于网络管理员的账户但无法修改架构。为什么？
A. 你必须是 `Enterprise Admin` 组的成员才能修改架构。
B. 你必须是 `Schema Admin` 组的成员才能修改架构。
C. 你必须在林中的每个域中都是 `Domain Admins` 成员才能修改架构。
D. 只有在林创建期间的初始 `Administrator` 账户才能修改架构。

8. 你是一名网络管理员，想要修改与其中一个用户账户关联的一个属性。你如何做到这一点？
A. 打开 `Active Directory Users and Computers` 并更改为高级视图。这将允许你修改需要更改的用户账户中属性的属性。
B. 打开 `Active Directory Sites and Services`。打开包含该属性的站点的属性并进行修改。
C. 打开 Schema Snap-in，展开 `Objects`，并选择 `User object` 以修改关联的属性。
D. 打开 Schema Snap-in，展开 `Attributes`，并找到你想要修改的属性。

9. 你正在向另一名网络管理员解释各种属性。你正在展示一个 `User` 账户的属性，你的新网络管理员问关于各种属性的 Other 按钮是什么意思。你告诉她什么？
A. 这些属性是多值属性。
B. 这些属性是单值属性。
C. 这些属性实际上是 `Object classes`。
D. 这些属性是索引属性。

10. 作为网络管理员，你负责确保各种属性为查询的最佳性能而被索引。你如何使一个属性被索引？
A. 使用 `Schema snap-in`，右键单击你想要索引的属性并选择 Properties。选择 Index this attribute in the Active Directory。
B. 使用 `Schema snap-in`，右键单击你想要索引的属性并选择 Properties。选择 Replicate this attribute to the `GC`。
C. 使用 `Schema snap-in`，右键单击你想要索引的属性并选择 Properties。选择 Allow this attribute to be shown in advanced view。
D. 使用 `Schema snap-in`，右键单击你想要索引的属性并选择 Properties。选择 Attribute is Active。

11. 你正在处理 Schema 对象并且需要一个必须由第三方提供的组件。哪个组件由第三方提供以便遵循标准？
A. `LDAP name`
B. `Common name`
C. `OID`
D. `Object GUID`

12. 你在设置架构中的新类时犯了一个错误。你想要纠正这个错误，以便为该类拥有适当的名字和配置。你如何做到这一点？
A. 你必须停用添加时带有错误的那种类，然后重命名它。然后你可以创建一个具有适当名称和配置的新类。
