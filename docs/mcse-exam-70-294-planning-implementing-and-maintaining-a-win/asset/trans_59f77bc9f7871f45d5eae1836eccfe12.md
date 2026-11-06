
![wrong](images/wrong.png) 答案 A 不正确，因为这是一个 `UPN`。在 Active Directory 中，每个用户账户在 Active Directory 中都有一个登录名和 `UPN` 后缀。登录名是账户名，而 `UPN` 后缀是用户将登录到的域。答案 B 不正确，因为这是一个 `DNS` 域名。它标识了域，但没有提供足够的信息来访问数据库。答案 D 也不正确，因为它使用 `UNC` 路径来标识文件的位置。虽然 `UNC` 名称可用于访问文件，但它没有使用问题中特别要求的 `URL`。

### 5. 用户名是 JaneD 的用户在 Sales 部门工作。她的账户位于 [syngress.com](http://www.syngress.com) 域中。基于此信息，在 Active Directory 中将使用什么规范名称来标识此对象？
A. `CN = JaneD`
B. `/CN = JaneD /OU = Sales /DC = syngress /DC = com`
C. `OU = Sales`
D. `/syngress.com/Sales/JaneD`
☑ D. 规范名称是显示对象区别名称 (`DN`) 的另一种方式，但格式更易于阅读。`DN` 中使用的信息是反转的，因此它从最高级别开始，然后逐步向下到对象的名称。
![wrong](images/wrong.png) 答案 A 不正确，因为这是相对区别名称 (`RDN`)。`RDN` 是 `DN` 的一部分，用于在父容器中唯一标识对象。由于每个对象必须在目录结构中具有唯一名称，因此 `RDN` 在特定 `OU` 内标识对象。答案 B 不正确，因为它是 `DN`。它由对象的通用名称 (`CN`)、组织单位 (`OU`) 和域组件 (`DC`) 组成。答案 C 不正确，因为这是 `DN` 的组织组件。

## 了解 Active Directory 的工作原理

### 6. 你正在对 Active Directory 中使用的对象类和属性进行更改。在以下哪个 DC 上进行这些更改？
A. `Schema Master`
B. `RID Master`
C. `Infrastructure Master`
D. `PDC Emulator`
☑ A. `Schema Master` 是一个负责对架构进行所有更改的 DC，架构定义了林中使用的对象类和属性。对架构的更新必须在担任 `Schema Master` 角色的 DC 上执行。此 DC 用于写入目录的架构，然后复制到林中的其他 DC。
![wrong](images/wrong.png) 答案 B 不正确，因为 `RID Master` 负责为域中的每个对象创建一个唯一编号。这些编号发放给域中的其他 DC，以便在创建对象时，可以将唯一标识对象的编号序列应用于它。答案 C 不正确，因为 `Infrastructure Master` 负责更新对组成员关系所做的更改。答案 D 不正确，因为 `PDC Emulator` 设计为充当 Windows NT 主 DC 并接收首选密码更改，然后将其复制到域中的其他 DC。

### 7. 你的网络由两个林组成，一个林中有两个域，另一个林中有三个域。基于此信息，以下主角色中有多少个将在林和域中？
A. There will be five `Schema Masters`, `Domain Naming Masters`, `RID Masters`, `PDC Emulators`, and `Infrastructure Masters`.
B. There will be two `Schema Masters`, `Domain Naming Masters`, `RID Masters`, `PDC Emulators`, and `Infrastructure Masters`.
C. There will be five `Schema Masters` and `Domain Naming Masters`, and two `RID Masters`, `PDC Emulators`, and `Infrastructure Masters`.
D. There will be two `Schema Masters` and `Domain Naming Masters`, and five `RID Masters`, `PDC Emulators`, and `Infrastructure Masters`.
☑ D `Schema Master` 和 `Domain Naming Master` 是林范围的主角色，并且在每个林中唯一对应一个 DC。`RID Master`、`PDC Emulator` 和 `Infrastructure Master` 是域范围的主角色，每个域中只有一个。
![wrong](images/wrong.png) 答案 A 不正确，因为每个林中只能有一个 `Schema Master` 和 `Domain Naming Master`。由于有两个林，这意味着网络上会有两个。答案 B 不正确，因为每个域必须有一个 `RID Master`、`PDC Emulator` 和 `Infrastructure Master`。由于有五个域，这意味着网络上有五个。答案 C 不正确，因为网络所需的域范围主角色和林范围主角色的数量是颠倒的。必须有两个 `Schema Masters` 和 `Domain Naming Masters`，以及五个 `RID Masters`、`PDC Emulators` 和 `Infrastructure Masters`。

### 8. 用户最近更改了她的姓氏，你对目录中的用户对象进行了更改以反映这一点。更改前，站点间复制已使用默认计划进行。更改后，做出更改的 DC 与另一站点中的 DC 之间的链路失败。链路恢复还需要一个小时。每个站点有四个 DC。以下哪种情况会发生？
A. Replication between the DCs will occur normally, because at least two connections to each DC are created by the Knowledge Consistency Checker (`KCC`). Because one has failed, the other connection will be used.
B. Replication between the DCs won’t occur. After 15 seconds, a notification of the change will be sent out, and replication partners will then request updated data.
C. Replication will occur normally, because the information won’t be replicated until three hours after the last replication.
D. Another link will be used to replicate the data, based on the information gathered by the topology generator.
☑ C. 场景说明复制使用默认计划进行，并且故障后一个小时链路恢复。默认情况下，站点间复制每 180 分钟（三个小时）发生一次，并且将使用站点链路全天候 24 小时、每周 7 天满足此计划。
![wrong](images/wrong.png) 答案 A 不正确，因为此选项描述的是站点内复制。在站点内复制（复制发生在站点内）中，知识一致性检查器 (`KCC`) 为每个 DC 创建至少两个连接，以便如果一个连接失败，另一个连接可以使用。答案 B 不正确，因为这也描述了站点内复制。默认情况下，当在 DC 上进行更改时，它会等待 15 秒然后向其最近的复制伙伴发送通知。如果它有多个复制伙伴，它将以三秒间隔向每个额外伙伴发送通知。当伙伴收到此通知时，它将向原始 DC 发送请求更新目录信息的请求，然后原始 DC 通过发送更新的数据进行响应。答案 D 不正确，因为默认情况下复制每三小时发生一次。虽然每个站点的站点间拓扑生成器会构建拓扑以将数据发送到其他 DC，但站点内复制将在计划时间发生。站点链路对象的信息用于确定在站点之间传递此数据时使用最佳链路。

## 使用 Active Directory 管理工具

### 9. 你正在使用 Microsoft Management Console (`MMC`) 来管理 Active Directory 中的对象。你决定查看有关 DC 的信息。你将使用以下哪个管理单元来查看此信息？
A. `Active Directory Users and Computers`
B. `Active Directory Domains and Trusts`
C. `Active Directory Sites and Services`
D. `Dcgpofix`
☑ `Active Directory Users and Computers` 控制台是一个 `MMC` 管理单元，允许你管理用户和计算机账户、域控制器对象、组、打印机、`OU`、联系人以及存储在 Active Directory 中的其他对象。在此管理单元中，`Domain Controllers` 容器包含代表驻留在域中的 `Windows 2000` 和 `Windows Server 2003` DC 的对象。

