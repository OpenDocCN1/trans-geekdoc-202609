
3. 在`Add Assignments`格中，选择要分配给该角色的用户或组。

使用基于角色的访问控制技术的最佳实践是将角色分配给专门创建的组，然后将用户添加到该组中。移除用户的权限只需将其账户从特定组中移除。这比按资源逐个移除特定用户的权限要简单得多。

## 技能 1.2：使用 Azure AD 管理安全访问

本目标涉及通过使用 Azure Active Directory 保护 Azure 资源访问可以采取的步骤。本目标涉及配置特权身份管理、条件访问策略、实施 Azure AD 身份保护、管理无密码身份以及执行访问审查。本节涵盖以下主题：

### 配置 Azure AD 特权身份管理 (PIM)

Azure AD 特权身份管理 (PIM) 允许你让角色分配变为临时的并取决于批准，而不是像手动将成员添加到角色那样使其成为永久性的。PIM 需要 Azure AD P2，且在配置之前必须启用它。要配置用于 PIM 的 Azure AD 管理员角色，请执行以下步骤：

1. 在 Azure AD 管理中心中，选择`Roles And Administrators`。

2. 选择你想要添加用户的角色。这将打开角色的属性页面。

3. 在`Role Properties`页面上，点击`Manage In PIM`。角色将打开，任何永久分配给该角色的成员将列出且状态为`Permanent`（永久），如图 1-22 所示。

![FIGURE 1-22 Members of the Password Administrators role](img/01fig22.jpg)

**图 1-22** 密码管理员角色的成员

4. 选择你想要从`Permanent`（永久）转换为`Eligible`（符合）的用户。符合的用户可以请求该角色的权限，但该用户将不会拥有该权限。
