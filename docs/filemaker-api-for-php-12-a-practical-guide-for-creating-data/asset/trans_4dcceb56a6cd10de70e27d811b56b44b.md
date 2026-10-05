

## 在 OS X 上为你的网站绑定 SSL 证书。

在 OS X 服务器上为网站绑定 SSL 证书与 Windows 非常相似，尽管步骤要少得多。

- 1. 打开服务器管理（Server Admin）。从服务器列表中点击你的 Web 服务器。然后点击证书（Certificates）图标。
- 2. 点击加 + 按钮创建证书身份（Certificate Identity）。

![](img/5a2c5fda68d42e5d65f51850276e49ec_260_0.png)

图 7-80：创建一个新的证书身份。

- 3. 输入你网站的域名。
- 4. 选择身份类型为自签名根（Self Signed Root）。别担心，当你从证书颁发机构安装签名证书时，它会自动更改。
- 5. 选择证书类型为 SSL 服务器（SSL Server）。

## 证书助手

## 创建你的证书

请在下方指定某些证书信息。

| 名称 | formulationspro.com |
|---|---|
| 身份类型 | 自签名根 (Self Signed Root) |
| 证书类型 | SSL 服务器 (SSL Server) |
| | 让我覆盖默认值（例如：扩展、目标钥匙串等） |

 了解更多...

继续

图 7-81：为你的证书输入信息。

- 6. 点击“继续”。然后点击下一个“继续”按钮以创建临时的自签名证书。
- 7. 点击操作图标并生成证书签名请求 (CSR)。这将在你的桌面上创建一个文本文件 (.csr)。该文件将被你发送给你的证书颁发机构（CA）和/或复制/粘贴到你的网站上。每个 CA 接收文件的方式略有不同。CA 将向你返回一个签名证书，你将在接下来的步骤中放置它。

![](img/5a2c5fda68d42e5d65f51850276e49ec_261_0.png)

| 名称 | 过期 |
|---|---|
| formulationspro.com | 2013/2/28 |
| formulationspro.com | 2013/7/11 |

图 7-82：生成发送给证书颁发机构 (CA) 的证书签名请求 (CSR)。

- 8. 当你收到签名证书后，在列表中选择自签名证书。然后点击操作图标并选择用签名或更新的证书替换证书（Replace Certificate with Signed or Renewed Certificate）。

## 服务器管理: mailserver1.local: 证书

证书身份由公共证书和私钥组成。这些证书身份可以用于保护你的网络通信：

| 名称 | 到期 |
| --- | --- |
| formulationspro | 2013/8/9 |
| formulationspro2012 | 2012/2/28 |
| | 2013/7/11 |

生成证书签名请求 (CSR)
用签名或更新的证书替换证书
自签名证书
过期：2015年8月9日 星期五 上午 8:59:12 PT
此证书不受信任

formulationspro
美国 US
formulationspro
1
SHA-1 带 RSA 加密 | 1 2 840 113549 1 1 5 |
none

图 7-83：用来自 CA 的签名证书替换自签名证书。

- 9. 窗口将打开。将新的签名证书拖入窗口。然后选择“替换证书”。

服务器管理: mailserver1.local: 证书

添加一个与现有 "formulationsspro" 证书使用相同密钥的包含签名或更新证书的文件。要获取签名或更新的证书，请向你的证书颁发机构发送证书签名请求 (CSR)。

在此处拖入包含你私钥的文件。

图 7-84：将签名证书拖入窗口。

- 10. 要为你的网站安装证书，请从服务器中选择 Web 服务（Web service）。然后选择站点（Sites）图标。选择你想应用证书的网站。然后选择“安全”（Security）选项卡。
- 11. 勾选启用安全套层 (SSL)。
- 12. 从证书弹出菜单中选择你刚刚安装的证书。
- 13. 点击保存（Save）按钮为站点启用 SSL。

## 服务器管理: mailserver1.local | Web

| 概览 | 日志 | 站点 | Smartsgo |
|---|---|---|------|
| 已启用 | 主机名 | IP 地址 | 端口 |
| ✓ | mail.formulationspro.com | 192.168.1.7 | 8080 |

![](img/5a2c5fda68d42e5d65f51850276e49ec_263_0.png)

图 7-85：为你的网站安装签名 SSL 证书。

## 重配置 FileMaker Server

此时，如果你在浏览器中打开默认网页（Windows 上的 iisestart.html 或 Mac 上的 index.html），你的 Web 服务器在 http 和 https 上都运行得非常出色。然而，你会很快发现，如果你尝试从数据库访问动态 PHP 页面，一切都无法运行且 Web 发布引擎会崩溃。糟糕了！FileMaker 有一些晦涩的文档（技术文章 #7619）介绍如何配合 SSL 证书使用 cURL。别担心，这项工作不需要了解任何关于 cURL 的知识。执行以下任务以启用 cURL 库：

- 1. 打开位于以下路径的 FileMaker API 文件：
/FileMaker Server/Web Publishing/publishing-engine/php/FileMaker/conf/filemaker-api

- 2. 取消以下代码的注释：

```
$_FM_CONFIG['cURLOptions'] = array(CURLOPT_SSL_VERIFYPEER => false)
```

```php
<?php
 * FileMaker API 配置。
 * 所有设置都放入 $FM_CONFIG 数组中以保持全局命名空间。
 * 默认字符编码 ('UTF-8' 或 'ISO-8859-1')。
 * $FM_CONFIG['charset'] = 'UTF-8';
 * 提供翻译的默认语言区域：'en'
 * $FM_CONFIG['locale'] = 'en';
 * 日志级别，如果提供了对象：
 * $FM_CONFIG['loglevel'] = 'FILEMAKER_ERR';
 * 默认主机规格 (hostspec)，例如，使用 http://localhost:80/127.0.0.1/ 可能会导致性能损失。不要在此字符串中包含 /php/xml。
 * $FM_CONFIG['hostspec'] = '192.168.0.20:4043';
 * 指定任何额外的 cURL 证书等 - 在数组中使用 curl 选项作为键和值：
 * $FM_CONFIG['curloptions'] = array(CURLOPT_SSL_VERIFYPEER => false);
 * 用于表示记录的 PHP 类：
 * $FM_CONFIG['recordclass'] = 'FileMaker_Record';
 *
 * 在 Record 数据上进行预验证 (PHP)？
 * $FM_CONFIG['validate'] = false;
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_264_0.png)

- 3. 通过打开 FileMaker Server控制台 (http://localhost:1600) 来编辑 Web 发布部署。按照向导安装服务器部署。

## 部署助手

## 部署进度

证书身份由公共证书和私钥组成。这些证书身份可以用于保护你的网络通信：

| 名称 | 过期 |
| --- | --- |
| formulationspro | 2013/8/9 |
| formulationspro2012 | 2012/2/28 |
| | 2013/7/11 |

生成证书签名请求 (CSR)
用签名或更新的证书替换证书
自签名证书
过期：2015年8月9日 星期五 上午 8:59:12 PT
此证书不受信任

formulationspro
美国 US
formulationspro
1
SHA-1 带 RSA 加密 | 1 2 840 113549 1 1 5 |
none

图 7-83：用来自 CA 的签名证书替换自签名证书。

- 9. 窗口将打开。将新的签名证书拖入窗口。然后选择“替换证书”。

服务器管理: mailserver1.local: 证书

添加一个与现有 "formulationsspro" 证书使用相同密钥的包含签名或更新证书的文件。要获取签名或更新的证书，请向你的证书颁发机构发送证书签名请求 (CSR)。

在此处拖入包含你私钥的文件。

图 7-84：将签名证书拖入窗口。

- 10. 要为你的网站安装证书，请从服务器中选择 Web 服务（Web service）。然后选择站点（Sites）图标。选择你想应用证书的网站。然后选择“安全”（Security）选项卡。
- 11. 勾选启用安全套层 (SSL)。
- 12. 从证书弹出菜单中选择你刚刚安装的证书。
- 13. 点击保存（Save）按钮为站点启用 SSL。

服务器管理: mailserver1.local | Web

| 概览 | 日志 | 站点 | Smartsgo |
|---|---|---|------|
| 已启用 | 主机名 | IP 地址 | 端口 |
| ✓ | mail.formulationspro.com | 192.168.1.7 | 8080 |

![](img/5a2c5fda68d42e5d65f51850276e49ec_263_0.png)

图 7-85：为你的网站安装签名 SSL 证书。

## 重配置 FileMaker Server

此时，如果你在浏览器中打开默认网页（Windows 上的 iisestart.html 或 Mac 上的 index.html），你的 Web 服务器在 http 和 https 上都运行得非常出色。然而，你会很快发现，如果你尝试从数据库访问动态 PHP 页面，一切都无法运行且 Web 发布引擎会崩溃。糟糕了！FileMaker 有一些晦涩的文档（技术文章 #7619）介绍如何配合 SSL 证书使用 cURL。别担心，这项工作不需要了解任何关于 cURL 的知识。执行以下任务以启用 cURL 库：

- 1. 打开位于以下路径的 FileMaker API 文件：
/FileMaker Server/Web Publishing/publishing-engine/php/FileMaker/conf/filemaker-api

- 2. 取消以下代码的注释：

```
$_FM_CONFIG['cURLOptions'] = array(CURLOPT_SSL_VERIFYPEER => false)
```

## 部署助手

## 部署进度

证书身份由公共证书和私钥组成。这些证书身份可以用于保护你的网络通信：

| 名称 | 过期 |
| --- | --- |
| formulationspro | 2013/8/9 |
| formulationspro2012 | 2012/2/28 |
| | 2013/7/11 |

生成证书签名请求 (CSR)
用签名或更新的证书替换证书
自签名证书
过期：2015年8月9日 星期五 上午 8:59:12 PT
此证书不受信任

formulationspro
美国 US
formulationspro
1
SHA-1 带 RSA 加密 | 1 2 840 113549 1 1 5 |
none

图 7-83：用来自 CA 的签名证书替换自签名证书。

- 9. 窗口将打开。将新的签名证书拖入窗口。然后选择“替换证书”。

服务器管理: mailserver1.local: 证书 

添加一个与现有 "formulationsspro" 证书使用相同密钥的包含签名或更新证书的文件。要获取签名或更新的证书，请向你的证书颁发机构发送证书签名请求 (CSR)。

在此处拖入包含你私钥的文件。

图 7-84：将签名证书拖入窗口。

- 10. 要为你的网站安装证书，请从服务器中选择 Web 服务（Web service）。然后选择站点（Sites）图标。选择你想应用证书的网站。然后选择“安全”（Security）选项卡。
- 11. 勾选启用安全套层 (SSL)。
- 12. 从证书弹出菜单中选择你刚刚安装的证书。
- 13. 点击保存（Save）按钮为站点启用 SSL。

## 部署助手

## 部署进度

请指定要用于 Web 发布的协议、主机名和端口信息。点击重试（Retry）测试你的设置。

## 服务器测试结果

## 服务器测试失败

证书身份由公共证书和私钥组成。这些证书身份可以用于保护你的：

