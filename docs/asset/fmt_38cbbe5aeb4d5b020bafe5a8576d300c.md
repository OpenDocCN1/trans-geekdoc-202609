
### 提示

OWASP XSS 过滤器规避备 Cheat 表（[`www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet`](https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet)）包含了数十个额外的规避技术示例。你可以在我的 GitHub 仓库中访问大量的 XSS 规避技术向量，地址为 [https://github.com/The-Art-of-Hacking/h4cker/blob/master/web_application_testing/xss_vectors.md](https://github.com/The-Art-of-Hacking/h4cker/blob/master/web_application_testing/xss_vectors.md)。

#### XSS 缓解

以下是防止 XSS 的通用规则：

- 对内容进行 HTML 编码。
- 绝不在允许的位置插入不可信数据。
- 对 HTML 属性进行属性编码。
- 对 JavaScript 数据进行 JavaScript 转义。
- 对 CSS 属性进行 CSS 转义。
- 对 URL 参数进行 URL 编码。
- 使用库清理 HTML。
- 通过遵循 OWASP 防止基于 DOM 的 XSS：[`cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet`](https://cheatsheetseries.owasp.org/cheatsheets/DOM_based_XSS_Prevention_Cheat_Sheet)。
- 使用 `HttpOnly` Cookie 标记。
- 实施内容安全策略（CSP）。
- 使用 `X-XSS-Protection` 响应头。

现代浏览器已经提供了 XSS 控制。

### 提示

列出多种 XSS 缓解措施的最佳资源之一是 OWASP 跨站脚本防护备 Cheat 表，地址为 [cheatsheetseries.owasp.org/X_ss_Prevention_Cheat_Sheet](https://cheatsheetseries.owasp.org/cheatsheets/X_ss_Prevention_Cheat_Sheet)。

## 理解跨站请求伪造 (CSRF/XSRF) 和服务端请求伪造攻击

跨站请求伪造（简称 **CSRF** 或 **XSRF**）攻击发生在受信任的用户发送未经授权的命令时。CSRF 攻击与 XSS 攻击不同，因为它利用了应用程序对用户浏览器的信任。

### 注意

CSRF 漏洞也被称为 *单点击攻击* 或 *会话劫持*。

CSRF 攻击通常影响依赖用户身份的应用程序（或网站）。攻击者可以欺骗用户向目标网站发送 HTTP 请求。CSRF 攻击的一个示例是通过浏览器保存的 Cookie 应用程序身份验证的用户，无意中向信任该用户的网站发送 HTTP 请求，从而触发了非想要的操作。

图 6-21 展示了使用 DVWA 进行 CSRF 攻击的示例。

![FIGURE 6-21 CSRF Example](img/06fig21.jpg)

**FIGURE 6-21** CSRF Example

在图 6-21 中，Web 表单要求用户更改密码。如果你仔细查看图 6-21 中的 URL，你会发现它包含了参数 `password_new=test&password_conf=test&Change=Change#`。用户在 Web 表单中输入密码后，密码不仅会显示在 URL 中，而且由于应用程序允许这样做，攻击者可以轻松地向任何用户发送一个构造的链接来更改其密码，如下所示：

点击此处查看代码图像

```
http://192.168.78.8:66/vulnerabilities/csrf/?password_new=newpasswd&password_conf=newpasswd&Change=Change#
```

如果用户点击此链接，其密码将被更改为 `newpasswd`。

## 注意

CSRF 的缓解和防御是在服务器端实现的。以下链接处的论文描述了防止或缓解 CSRF 漏洞的几种技术：[`seclab.stanford.edu/websec/csrf/csrf.pdf`](https://seclab.stanford.edu/websec/csrf/csrf.pdf)。

## 理解点击劫持 (Clickjacking)

点击劫持涉及使用多个透明或不透明层，诱导用户点击其并非想要导航或点击页面上的 Web 按钮或链接。点击劫持攻击通常被称为 UI 还原（UI redress attacks）。用户的击键也可以通过点击劫持技术被劫持。攻击者可以通过 CSS 样式表、iframe 和文本框的组合发起点击劫持攻击，欺骗用户在不可见的框架中输入信息或点击链接，该框架可以从攻击者创建的站点。

根据 OWASP，这些是防止和缓解点击劫持的两种常用技术：

* 向正确的内容安全策略 (CSP) 框架祖发送指令响应头，指示浏览器不允许来自其他域的框架。（这取代了旧的 `X-Frame-Options` HTTP 头。）
* 在应用程序中使用防御性代码确保当前帧是顶层窗口。

## 注意

OWASP 点击劫持防御作弊表（OWASP Clickjacking Defense Cheat Sheet）提供了有关如何防御点击劫持攻击的更多细节。可以通过以下地址访问作弊表：[`www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet`](https://www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet)。

## 利用安全配置错误

攻击者可以利用安全配置错误，包括目录遍历漏洞和 Cookie 操纵。

### 利用目录遍历漏洞

目录遍历漏洞（通常被称为路径遍历）允许攻击者访问存储在 Web 根文件夹之外的文件和目录。

## 注意

目录遍历有许多名称，包括“点点斜”（dot-dot-slash）、`目录爬爬`（directory climbing）和 `回溯`（backtracking）。

通过操纵引用带有点点斜（`../`）序列及其变体的文件的变量，或者通过使用绝对文件路径访问漏洞系统上的文件，可以利用路径遍历漏洞。

图 6-22 显示了目录遍历的一个示例。

```
http://192.168.78.8:66/vulnerabilities/csrf/?password_new=newpasswd&password_conf=newpasswd&Change=Change#
```
