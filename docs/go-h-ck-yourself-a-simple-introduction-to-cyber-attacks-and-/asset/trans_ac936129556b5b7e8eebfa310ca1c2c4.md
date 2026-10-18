

A *反射式 XSS 攻击*利用那些直接将用户输入显示或*反射*回网页上的页面，例如要求输入姓名和地址的订单表单，然后将其显示给你以确认输入正确。攻击者使用反射式跨站脚本将恶意 HTML 或 JavaScript 代码注入未受保护的 Web 应用程序。让我们来试试！

1.  在 Windows 10 虚拟机上的 DVWA 中，单击左侧的 **XSS reflected** 打开漏洞：反射式跨站脚本（XSS）网页。

    此页面旨在在单词 *Hello* 之后显示你在 What’s your name? 文本字段中输入的内容。例如，如果你输入姓名 `Bryson`，页面将响应 `Hello Bryson`。

2.  不要输入你的姓名，而是将上一节中的 HTML/JavaScript 命令输入到姓名文本字段中，如 [图 8-6](#c08.xhtml#figure8-6) 所示：

    ```
    <script>alert("You've been hacked!");</script>
    ```

    ![Figure 8-6: Attacking the reflected XSS page by entering HTML and JavaScript into the text box](image_fi/502000c08/f08006.png)

    Figure 8-6: Attacking the reflected XSS page by entering HTML and JavaScript into the text box

3.  单击 **Submit**，网页将重新加载，并弹出消息 “You’ve been hacked!”，如 [图 8-7](#c08.xhtml#figure8-7) 所示。

    ![Figure 8-7: The vulnerable web page pops up a message saying we’ve been hacked!](image_fi/502000c08/f08007.png)

    Figure 8-7: The vulnerable web page pops up a message saying we’ve been hacked!

通过将一行 HTML 和 JavaScript 组合并将其输入到 DVWA 中未受保护的文本框，我们将代码注入了网页。恶意攻击者可以使用相同的技术说服用户他们的计算机确实正受到攻击，并让他们拨打免费电话寻求“技术支持”。在这种常见的诈骗中，犯罪分子租用呼叫中心来获取受害者的信用卡信息，并向他们收取虚假计算机服务的费用。

#### 存储式跨站脚本

大多数网站使用数据库来存储用户输入或经常变化的信息，例如产品信息或客户数据。如果攻击者将恶意代码注入与数据库关联的 Web 表单，该恶意代码将存储在数据库中，并成为网页的永久部分。这种攻击称为 *存储式 XSS 攻击*，可确保每次有人查看受影响的网页时，恶意代码都会运行。相比之下，我们的反射式 XSS 攻击并未永久更改网页，因为我们注入的代码未保存到数据库中。我们现在来尝试一次存储式 XSS 攻击。

1.  单击左侧 DVWA 菜单中的 **XSS stored**。你将看到一个类似留言本的应用程序，允许用户将姓名和简短消息保存到页面。

2.  不要用你的姓名和一条友好的消息来签署留言本，只需输入你的姓名。然后，在 Message 文本框中，输入我们要存储在此页面数据库中的 XSS 攻击代码，`<script>alert("You've been hacked!");</script>`，如 [图 8-8](#c08.xhtml#figure8-8) 所示。

    ![Figure 8-8: Storing our malicious script in the XSS stored page in DVWA](image_fi/502000c08/f08008.png)

    Figure 8-8: Storing our malicious script in the XSS stored page in DVWA

3.  单击 **Sign Guestbook**，你将看到弹出警报，如 [图 8-9](#c08.xhtml#figure8-9) 所示。

    ![Figure 8-9: Our JavaScript alert will tell every visitor, “You’ve been hacked!”](image_fi/502000c08/f08009.png)

    Figure 8-9: Our JavaScript alert will tell every visitor, “You’ve been hacked!”

与反射式攻击不同，每次有人访问存储式跨站脚本（XSS）留言本页面时，此警报都会弹出。你已使用数据库驱动的网页在 DVWA 网站中永久存储了恶意脚本。

不过，JavaScript 可以做的远不止弹出警报消息。让我们更改浏览器的 `window.location` 以将用户重定向到完全不同的网站：

1.  再次加载 XSS stored 网页，并单击 **OK** 关闭警报消息弹出窗口。

2.  这次，在正常输入姓名后，将以下代码输入到 Message 文本框中，如 [图 8-10](#c08.xhtml#figure8-10) 所示：

    ```
    <script>window.location.href="https://www.nostarch.com/go-hck-yourself";</script>
    ```

    ![Figure 8-10: Entering a more malicious script that will redirect the user to a completely different web page](image_fi/502000c08/f08010alt.png)

    Figure 8-10: Entering a more malicious script that will redirect the user to a completely different web page

3.  单击 **Sign Guestbook**，你将看到我们之前注入的警报弹出窗口。但一旦关闭警报，你将被带到 [https://www.nostarch.com/go-hck-yourself/](https://www.nostarch.com/go-hck-yourself/)。你无法返回 DVWA XSS stored 页面，因为每次重新加载页面时，它都会重定向到 *Go H\*ck Yourself* 网页。

我们已永久劫持 XSS stored 页面，因此每位访问者都将被重定向到本书的网站，而不是原页面。攻击者可以对雇主网站、你喜爱的在线游戏或社交媒体应用，甚至当地政府网站上的未受保护 Web 应用程序做同样的事情，甚至更糟。要恢复网站的原始功能，网站管理员需要访问数据库并完全删除存储的 XSS 代码。

要在 DVWA 中重置数据库以删除我们输入的恶意代码，请单击左侧 DVWA 菜单中的 **Setup**，如 [图 8-11](#c08.xhtml#figure8-11) 所示。然后单击 **Create / Reset Database**，DVWA 将把数据库重置为原始状态。

 ![Figure 8-11: Clearing your stored XSS hacks](image_fi/502000c08/f08011.png)

Figure 8-11: Clearing your stored XSS hacks

### 对数据库发起 SQL 注入攻击

将恶意代码注入 *到* 网站中很可怕，但黑客如何从网站中窃取敏感数据？在本节中，你将学习 Web 黑客如何使用结构化查询语言（SQL）注入攻击直接从网站数据库窃取信息。SQL 是访问大多数数据库所使用的语言，而 *SQL 注入* *(SQLi)* 是指将恶意 SQL 代码插入 Web 应用程序，以诱骗应用程序的数据库泄露私密信息。

数据库包含 *表*，表看起来像带有列和行的电子表格。列用于不同的 *字段* 或信息片段，例如名、姓、用户名、密码、电子邮件地址等。行用于单个 *记录*。例如，用户表中的每个用户都会占据单独的一行。

当我们访问数据库时，我们使用 SQL *查询*，例如：

```
SELECT password FROM users WHERE username='Bryson'
```

此查询请求从 `users` 表中 `username` 字段为 `Bryson` 的行或行中获取 `password` 字段。我们可以稍微修改查询以请求 *所有* 用户的密码：

```
SELECT password FROM users WHERE username='Bryson' OR 1='1'
```

通过向查询添加 `OR` 条件，我们要求数据库从 `users` 表中选择所有密码。在每一行中，SQL 都会询问 `username` 是否等于 `'Bryson'`，或者该行中 `1` 是否等于 `'1'`。如果任一条件为真，SQL 将返回该行的密码。因为其中一个条件 *始终* 为真（1 始终等于 1），数据库将返回 `users` 表中的 *每个* 密码。

让我们将一些 SQL 查询注入 DVWA，以从网站数据库窃取信息。

1.  在 Windows 10 虚拟机的 Edge 浏览器中，确保 DVWA Script Security 设置为低（如第 95 页的 [图 8-5](#c08.xhtml#figure8-5) 所示）。

2.  单击左侧 DVWA 菜单中的 **SQL Injection**。你将看到一个用户查找页面，如 [图 8-12](#c08.xhtml#figure8-12) 所示。

