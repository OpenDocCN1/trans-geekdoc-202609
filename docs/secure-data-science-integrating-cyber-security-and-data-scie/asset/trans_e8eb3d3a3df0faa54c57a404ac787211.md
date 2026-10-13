
我们首先考虑管理员策略，该策略规定对象的所有者有权为该对象指定访问控制策略。根据前几节介绍的本体定义的相应 SWRL 规则如下：

```
Owns(?grantor, ?targetObject) ⇒ AdminAll(?grantor, ?targetObject)
```

对上述规则的求值结果是为每一对用户及其拥有的相应资源生成一个不同的对象属性 `AdminAll` 实例。值得注意的是，这种授权是根据对 SAKB 进行建模的本体进行传播的。因此，由于框架利用了第 17.5.1 节介绍的本体，上述授权也会传播到 `AdminRead` 和 `AdminWrite`。

社交网络中另一个有意义的管理员策略是：如果用户在照片中被标记，则她有权为该照片的读取权限指定访问控制策略。这可以通过以下 SWRL 安全规则进行编码：

```
Photo(?targetObject) ∧ photoOf(?grantor, ?targetObject) ⇒ AdminRead(?grantor, ?targetObject)
```

上述规则是有趣的例子，强调了在所提出的框架中，可以轻松指定管理员策略，而在非基于语义的访问控制机制中实现这些策略将需要复杂的策略管理。确实，为 OSN 提供对用户和资源之间关系（例如建模所有权或标记关系）进行建模的本体，使得 SA 能够通过简单地对所需关系类型提出条件来指定管理员策略。相反，在传统访问控制机制中强制执行这些管理员策略将需要实现复杂的策略管理功能，因为这将要求首先确定用户和资源之间所有可能的关系，然后为所有这些关系指定管理员授权。而在所提出的框架中，这项任务由推理器执行。

[表 17.1](#ch17.xhtml#table17_1a) 展示了一些 SWRL 安全规则的示例。第一条安全规则编码了一条过滤策略，规定 Bob 的孩子不能访问视频。一旦对该规则进行求值，就会为 Bob 的每个孩子和视频资源创建一个禁止实例。相反，第二条安全规则对应 Bob 陈述的一条访问控制策略，将对其照片的读取访问限制为仅限其直接朋友，而第三条规则编码了一条访问控制策略，规定 Alice 被标记的照片可以被她的直接朋友访问。最后，第四条规则规定如果一个人拥有一张照片，那么他们朋友的朋友（一种间接关系）可以查看该照片。

### 表 17.1 SWRL 安全规则示例

| # | SWRL 规则 |
|---|---|
| (1) | `Video(?targetObject) ∧ ParentOf(Bob, ?controlled) ⇒ PRead(?controlled, ?targetObject)` |
| (2) | `Owner(Bob, ?targetObject) ∧ Photo(?targetObject) ∧ Friend(Bob, ?targetSubject) ⇒ Read(?targetSubject, ?targetObject)` |
| (3) | `Photo(?targetObject) ∧ photoOf(Alice, ?targetObject) ∧ Friend(Alice, ?targetSubject) ⇒ Read(?targetSubject, ?targetObject)` |
| (4) | `Photo(?targetObject) ∧ Owns(?owner, ?targetObject) ∧ Friend(?owner, ?targetSubject1) ∧ Friend(?targetSubject1, ?targetSubject2) ⇒ Read(?targetSubject2, ?targetObject)` |

## 17.6 安全规则执行

### 17.6.1 我们的方法

我们的框架的作用类似于传统的访问控制机制，其中 `reference monitor`（参考监视器）通过查找授予或拒绝请求的授权来评估请求。在所提出的框架中利用这一原则意味着通过查询 SAKB 本体来检索授权/禁止。因此，例如，要验证用户 `u` 是否有权为对象 `o` 的读取权限指定访问控制策略，有必要验证实例 `AdminRead(u, o)` 是否在本体中，即执行实例检查。这意味着在评估任何可能的请求之前，必须先评估所有编码安全策略的 SWRL 规则，从而推断出所有访问控制/管理员授权以及所有禁止。因此，在策略执行之前，需要执行一个称为 `policy refinement`（策略细化）的初步阶段。该阶段旨在通过执行所有编码安全策略的 SWRL 规则，用推断出的授权/禁止来填充 SAKB。

一旦推断出授权/禁止，就可以进行安全策略执行。特别是，访问控制和过滤策略在提交 `access request`（访问请求）时进行评估，而管理员策略在提交 `admin request`（管理员请求）时进行评估。在下文中，我们将展示这两种请求评估，说明相应策略是如何执行的。

### 17.6.2 管理员请求评估

管理员请求包含两部分信息：`grantor`（授予者）的名称，即提交管理员请求的用户；以及授予者想要指定的访问控制或过滤策略，编码为 SWRL 规则，即 `submitted SWRL`（提交的 SWRL）。仅当 SAKB 中存在针对授予者的管理员授权时，提交的 SWRL 才能被插入系统。例如，如果提交的规则要求为 `targetObject` 的读取权限指定访问控制策略，则必须存在 `<grantor, targetObject>: Read` 的实例。请注意，关于权限和 `targetObject` 的信息可以直接从提交的 SWRL 中检索。因此，要决定上述请求是否可以被授权，一种可能的方法是查询 SAKB 以检索相应的管理员授权（如果有）。如果存在实例，则可以评估提交的 SWRL，否则框架将拒绝授予者的管理员请求。另一种方法是通过在其主体中添加条件来重写提交的 SWRL，以验证 SAKB 中是否存在授权指定该规则的管理员授权。以下示例将阐明这一基本思想。

假设系统收到以下管理员请求：`{Bob, SWRL[1]}`，其中 `SWRL[1]` 如下：

```
SWRL[1]: Owns(Bob, ?targetObject) ^ Photo(?targetObject) ^ Friend(Bob, ?targetSubject) ⇒ Read(?targetSubject, ?targetObject)
```

为了确定管理员请求的结果，框架必须验证 SAKB 中 `<Bob, targetObject>: AdminRead` 实例的存在性。可以通过简单地修改 `SWRL[1]` 将此检查合并到其主体中，如下所示：

```
New_SWRL[1]: AdminRead(Bob, ?targetObject) ^ Owns(Bob, ?targetObject) ^ Photo(?targetObject) ^ Friend(Bob, ?targetSubject) ⇒ Read(?targetSubject, ?targetObject)
```

然后对 `New_SWRL[1]` 进行求值，其结果是只有当 Bob 根据管理员策略被授权指定这些授权时，读取访问控制授权才会被插入 SAKB。

如果管理员请求提交的是过滤策略，为了决定授予者是否有权指定该策略，需要在 `Prohibitions` 类（即过滤策略要求禁止的动作对应的子类）中进行搜索，寻找一个实例，其 `Grantor` 属性等于授予者，`Controlled` 和 `TargetObject` 属性分别等于提交的 SWRL 规则头部指定的受控者和 `TargetObject`。在这种情况下，我们也可以采用基于 SWRL 重写的方法。
