
为了处理这些情况，DBMS 必须维护事务日志。例如，假设银行系统的设计是每处理一笔交易就在日志（电子版、纸质版或两者兼有）中生成一条消息。如果发生系统故障，系统可以通过恢复数据库的备份副本，并从日志中重新处理所有后续交易，从而获得准确的账户余额。

## 元素完整性

数据库**元素**的**完整性**是指其正确性或准确性。归根结底，授权用户负责在数据库中录入正确的数据。然而，用户和程序在收集数据、计算结果和录入数值时会犯错误。因此，DBMS 有时会采取特殊措施，帮助在错误发生时捕获错误，并在错误插入后进行纠正。

**数据库实现了数据库本身、其结构及其各个元素的完整性。**

这种纠正措施可以通过三种方式实施：字段检查、访问控制和变更日志。

首先，DBMS 可以应用**字段检查**，即测试某位置数值是否适当的活动。某字段可能被要求必须为数字、大写字母或一组可接受字符中的某一个。该检查确保数值落在指定范围内，或不大于其他两个字段数值之和。这些检查可在数据录入时防止简单错误。（侧边栏 7-1 演示了元素完整性的重要性。）

### 侧边栏 7-1 元素完整性故障导致网络瘫痪

Crocker 和 Bernstein [CRO89] 研究了当时称为 ARPANET（即当今互联网的前身）的灾难性故障。有几次故障源于用于指导网络流量的路由表问题。

1971 年的一次错误被称为“黑洞”。硬件故障导致某节点宣称它是通往网络中所有其他节点的最佳路径。该节点将此声明发送给其他节点，错误的通告很快在整个网络中传播开来。该节点立即成为了网络的“黑洞”，因为所有流量都被路由到它那里，却永远无法到达真正的目的地。

ARPANET 使用的是简单的表，而非功能齐全的数据库管理系统，因此在新值被安装到分布式路由表之前，没有对其进行检查。如果有一个数据库，完整性检查软件本可以检查新分发值中的错误，并为人工审核发出标记。

第二种完整性措施由**访问控制**提供。为了理解原因，请设想没有数据库的情况。数据文件可能包含来自多个来源的数据，冗余数据可能存储在多个不同的地方。例如，学生的邮寄地址可能存储在校园内许多不同的文件中：教务处用于正式通信，餐饮服务处用于食堂特权，书店用于购物，财务援助处用于核算。实际上，学生甚至可能不知道每个独立办公室都存档了该地址。如果学生从一个住所搬到另一个住所，每个独立文件都需要更正。

没有数据库，你可以想象数据完整性面临的风险。首先，在某一时刻，一些数据文件可能显示旧地址（尚未更新），而另一些文件同时显示新地址（已更新）。其次，总有人可能录错数据字段，再次导致文件包含错误信息。第三，学生可能甚至不知道某些文件的存在，因此不知道通知文件所有者更新地址信息。数据库解决了这些问题。它们支持在一个中心源头收集和控制这些数据，确保学生和用户拥有正确的地址。

然而，集中化说起来容易做起来难。谁拥有这个共享的中心文件？谁被授权更新哪些元素？如果两个人应用了相互冲突的修改怎么办？如果修改按错误的顺序应用怎么办？如何检测重复记录？发现重复记录时采取什么行动？这些是必须由数据库管理员解决的策略问题。侧边栏 7-2 描述了如何在管理程序配置时解决这些问题；管理数据库变更也需要类似的正式流程。

### 侧边栏 7-2 配置管理与访问控制

软件工程师在管理大型计算机系统配置时必须解决访问控制问题。主要系统的代码及其随时间变化的修改实际上构成了一个数据库。在许多情况下，多个程序员同时对系统进行更改；配置管理数据库必须帮助确保存储的是正确且最新的更改。

版本和发布的激增可以通过三种主要方式加以控制。[PFL10a]

- **分离文件**：可以为每个不同的版本或发布保留单独的文件。例如，版本 1 适用于将所有数据存储在主存储器中的机器，版本 2 适用于必须将部分数据存放到磁盘的机器。假设公共功能在两个版本中相同，位于组件 `C[1]` 到 `C[k]` 中，但内存管理由组件 `M[1]` 负责版本 1，组件 `M[2]` 负责版本 2。如果要向内存管理例程添加新功能，保持两个版本都处于最新和正确状态可能很困难；从用户角度来看，结果必须相同。

- **增量文件**：将一个版本视为主版本，所有其他版本视为主版本的变体。数据库仅在一个称为增量文件的文件中记录差异。增量文件包含“应用”于主版本以将其转换为替代版本的命令。这种方法节省存储空间，但可能变得难以驾驭。

- **条件编译**：所有版本由单个文件处理，并使用条件语句确定哪些语句在何种条件下适用。在这种情况下，共享代码只出现一次，因此如果发现问题，只需一次修正。但该单个文件中的代码可能非常复杂且难以维护。

## 数据库完整性与访问控制

### 受控访问配置文件

在上述三种情况下，对配置文件的受控访问至关重要。两个修复不同问题的程序员有时需要对同一组件进行更改。如果他们不协调访问，第二个程序员可能会无意中撤销（甚至破坏）第一个程序员的更改，不仅导致初始问题复发，还会引入额外的问题。因此，文件通过多种方式进行控制，包括在一名程序员进行更改时锁定文件，以及由一组称为**配置控制委员会**的人员进行管理，他们确保未经适当检查和测试的更改文件不会被投入生产使用。Shari Lawrence Pfleeger 和 Joanne Atlee 在文献 [[PFL10a]](#bib01.html#bib_485) 中描述了这些技术。

### 变更日志

提供数据库完整性的第三种手段是维护数据库的**变更日志**。变更日志记录了对数据库所做的每一次更改；它同时包含原始值和修改后的值。数据库管理员可以利用此日志撤销任何错误的更改。例如，图书馆罚款可能被错误地记在 Charles W. Robertson 头上，而不是 Charles M. Robertson，导致 Charles W. Robertson 被标记为不具备参加校队运动的资格。发现错误后，数据库管理员从日志中获取 Charles W. 的原始资格值并更正数据库。

#### 可审计性

对于某些应用，管理员可能希望生成对数据库所有访问（读或写）的审计记录。此类记录有助于维护数据库的完整性，或者至少能在事后发现谁在何时影响了什么值。第二个优势（稍后将看到）是用户可以增量式地访问受保护数据；即单次访问不泄露受保护数据，但一组连续的访问放在一起查看就会泄露数据，这很像在侦探小说中发现线索。在这种情况下，审计跟踪可以识别用户已获得哪些线索，以指导是否告知用户更多信息。

正如我们在 第 2 章 中指出的，粒度可能成为审计的障碍。操作系统中被审计的事件是诸如 `open file` 或 `call procedure` 之类的动作；它们很少像 `write record 3` 或 `execute instruction I` 那样具体。为了有助于维护完整性，数据库审计跟踪应包括记录级、字段级甚至元素级的访问。这种细节对于大多数数据库应用来说是难以承受的。

此外，数据库管理系统可能会访问一条记录但不向用户报告数据，例如用户执行 `select` 操作时。例如，宿舍辅导员可能想要所有不及格学生的数量，数据库管理系统报告为 462。为了得到这个数字，系统必须检查所有学生记录并标记成绩不及格的记录，它代表已适当记录在日志中接收数据的辅导员执行了此查找。因此，从某种意义上说，辅导员访问了所有那些学生成绩，尽管从数字 462 中辅导员无法确定任何个别学生的成绩。（在不将接收到的数据传输给用户的情况下访问记录或元素称为**透传问题**。）因此，直接访问的所有记录的日志既可能高估也可能低估用户实际获知的信息。该问题比我们在此描述的更为微妙，我们将在本章后面探讨一些泄露的复杂性。

## 访问控制

数据库通常按用户访问权限进行逻辑分离。例如，所有用户可被授予访问通用数据的权限，但只有人事部门可获取薪资数据，只有市场部门可获取销售数据。数据库之所以有用，是因为它们集中了数据的存储和维护。有限访问既是这种集中化的责任，也是其益处。

数据库管理员指定谁应被允许访问哪些数据，粒度可达视图、关系、字段、记录甚至元素级别。`DBMS` 必须强制执行此策略，授予对所有指定数据的访问权，或在禁止时拒绝访问。此外，访问模式可以有多种。用户或程序可能拥有读取、更改、删除或追加值的权利，添加或删除整个字段或记录，甚至重组整个数据库。

表面上看，数据库的访问控制似乎类似于操作系统或计算系统中任何其他组件的访问控制。然而，数据库问题更为复杂，正如我们在本章中将看到的。操作系统对象（如文件）是无关的项，而记录、字段和元素是相关的。虽然用户通过读取其他文件可能无法确定一个文件的内容，但用户可能仅通过读取其他数据元素就能确定某个数据元素。从其他数据获取数据值的问题称为**推理**，我们将在本章后面深入探讨。

重要的是要注意，你可以通过推理访问数据，而无需直接访问安全对象本身。限制推理可能意味着禁止某些路径以防止可能的推理。然而，为控制推理而限制访问也会限制那些无意进行未授权值访问的用户的查询。此外，尝试检查请求的访问是否存在不可接受的推理可能会实际降低 `DBMS` 的性能。

最后，操作系统对象和数据库对象在大小或粒度上有所不同。操作系统可以轻松控制对文件的访问，正如我们在 第 5 章 中所解释的。然而，包含数百个文件的访问控制列表比包含数百个文件（每个文件可能有一百个字段）的数据库的访问控制列表更容易实现。大小影响处理效率。操作系统通常不会“深入”文件内部以控制对文件内项目的访问。

**数据库管理系统实现自己的访问控制，其粒度比操作系统处理的更细。**

## 用户认证

`DBMS` 可以要求严格的用户认证。例如，`DBMS` 可能坚持要求用户同时通过特定密码和时间段检查。这种认证补充了操作系统执行的认证。通常，`DBMS` 作为应用程序运行在操作系统之上。这种系统设计意味着从 `DBMS` 到操作系统没有可信路径，因此 `DBMS` 必须对接收到的任何数据保持怀疑，包括来自操作系统的用户身份。因此，`DBMS` 被迫执行自己的认证。

## 可用性

`DBMS` 兼具程序和系统的特性。它是一个使用其他硬件和软件资源的程序，但对许多用户来说，它是唯一运行的应用程序。用户往往将 `DBMS` 视为理所当然，将其作为执行特定任务的必备工具。但当系统不可用时——忙于服务其他用户，或因维修升级而停机——用户会非常敏锐地察觉到 `DBMS` 的不可用性。例如，两个用户可能请求同一条记录，`DBMS` 必须进行仲裁；必然有一个用户会被拒绝访问一段时间。或者 `DBMS` 可能会扣留非受保护数据以避免泄露受保护数据，导致请求用户不满。我们将在本章后面更详细地探讨这些问题。这些问题导致对 `DBMS` 有很高的可用性要求。

### 完整性/机密性/可用性

The three aspects of computer security—integrity, confidentiality, and availability—are closely related to database management systems (DBMS). As we have described, integrity applies to each separate element of a database and to the database as a whole. Integrity is also a property of database structure (elements in one table correspond one-to-one with elements in another) and database relationship (records with the same unique identifier, called a key, are related). Thus, integrity is a primary concern in the design of database management systems. We look more closely at integrity issues in the next section.

Confidentiality is likewise a key issue for databases because databases are often used to implement controlled sharing of sensitive data. Access to data can be direct (you request a record and the database provides it) or indirect (you request some records and infer or intuit other data from those results). Controlling direct access uses the access control techniques we described in Chapter 2 and Chapter 5. However, indirect access is more difficult to control, and we examine it in more depth later in this chapter.

Finally, availability is important because it is the basis for the motivation to develop shared access to databases. However, availability conflicts with confidentiality. The last few sections of this chapter explore availability issues in environments where confidentiality is also important.

## 7.3 Reliability and Integrity

Databases integrate data from multiple sources, and users expect the DBMS to provide access to data in a reliable way. When software engineers say that software has **reliability**, they mean that the software runs for very long periods of time without failure. Users certainly expect a DBMS to be reliable because data is usually critical to business or organizational needs. In addition, users entrust data to a DBMS and reasonably expect it to protect the data from loss or corruption. Concern for reliability and integrity is a general security issue, but it is more pronounced in databases.

DBMSs protect against loss or corruption in several ways, which we study in this section. However, the controls we consider are not absolute: no control can prevent an authorized user from inadvertently entering an acceptable but incorrect value.

Concern for database reliability and integrity can be viewed from three dimensions:

*   **Database integrity:** Concern that the database as a whole is protected against damage, such as a disk drive failure or corruption of the master database index. These problems are addressed by operating system integrity controls and recovery procedures.

*   **Element integrity:** Concern that the value of a specific data element is written or changed only by authorized users. Proper access controls protect the database against corruption by unauthorized users.

*   **Element accuracy:** Concern that only correct values are written into a database element. Checks on element values help prevent the insertion of improper values. In addition, constraints can detect incorrect values.

### Operating System Protection Features
