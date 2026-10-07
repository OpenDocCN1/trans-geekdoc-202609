
```filemaker
Duplicate Record/Request
Set Variable [ $PK; Value:php_demo::RecordID ]
```

复制原始记录的门户（portal）记录。然后将外键更改为新的主键。

```filemaker
Go to Record/Request/Page [ Previous ]
Go to Related Record [ From table: "related_data"; Using layout: "Related Data php" 
(related_data) ] Show only related records
```

我喜欢在复制记录时从最后记录开始。这让你更容易判断何时已复制了所有记录，因为当你跳过用新键值更新了外键之后的记录时，集合中就不有剩余记录了。

```filemaker
Go to Record/Request/Page [ Last ]
```

遍历所有记录，为每个记录创建副本并更改外键。

```filemaker
Loop
Duplicate Record/Request
Set Field [ related_data::$PK ]
Omit Record
Omit Record
Exit Loop If [ Get(FoundCount) = 0 ]
End Loop
```

提交记录以确保它们在网页上显示。

```filemaker
Commit Records/Requests [ Skip data entry ]
```

# 编辑脚本 'PHP Duplicate Record' (php_demo)

视图：按类别查看所有

脚本名称：`PHP Duplicate Record`

- 允许用户取消 [ On ] - 不支持的脚本步骤。如果此处包含，FM 允许用户取消。

*(注：OCR 文本包含一些乱码；根据提供的文本：)*

- 允许用户取消 [0]

- 设置变量 (`$User`, On) - 如果 FileMaker 返回错误框未显示或将产生

- 设置错误捕获 (0)

- `GetRecord($RecordID)` 由 PHP 脚本。

- 设置变量 (`$RecordID`, `GetScriptParameter()`)

- 转布局 ('Demo php', `php_demo`)

- 结束循环

- 设置字段 (`php_demo.RecordID`, `$RecordID`)

- 执行查找

- 如果错误 - 未找到记录。

- 如果 (`GetLastError() > 0`)

- 退出循环

- 结束

- 复制记录并存储新记录的 PK，以便可以传递给 `related_data` 的外键。

- 复制记录/请求

- 设置变量 (`$Value`, `$RecordID`)

- 转到列表 (List, `$PK`)

- 转到相关记录 来自表: "Related_data" 使用布局: "Related Data php" (`related_data`) 仅显示相关记录

- 转到相关记录 来自表: "Related_data" 使用布局: "Related Data php" (`related_data_`) 复制原始记录的门户记录，为每个记录创建一个副本并更改外键。

- 循环

- 复制记录/请求

- 设置字段 (`related_data.FK`, `$PK`)

- 跳过记录

- 退出循环 如果 (`GetFoundCount = 0`)

- 结束循环

- 提交记录。

- 提交记录/对话 (跳过数据输入，!)

- 控制

- 执行脚本

- 暂停/恢复脚本

- 退出脚本

- 否则

- 如果

- 结束如果

- 循环

- 退出循环

- 允许用户取消

- 设置错误捕获

- 设置变量

- 安装/脚本

- 导航

- 转布局

- 转到相关记录

- 转到门户行

- 转字段

- 转到上一个字段

- 错误消息

- 进入查找模式

- 撤销/重做

- 剪切

- 粘贴

- 清空

- 设置选择

- 设置活动

- 执行查找/替换

- 按名称设置字段

- 设置下一个序列值

- 插入计算结果

- 插入最后有效的

- 插入索引

- 插入当前日期

脚本步骤选项

- 显示兼容性

- 客户端

- 使用完全权限运行脚本

图 7-77：PHP 记录脚本。

# 课程 32：安装并配置 SSL 与 FileMaker 使用

**目标**：在本课程中，你将学习如何在 Windows 或 OS X 上为 FileMaker 安装并配置 SSL。虽然没有示例文件，但知道如何配置 SSL 是重要的。

**难度**：简单

**示例文件**：无

**页面**：无

**步骤**：

![](img/5a2c5fda68d42e5d65f51850276e49ec_258_0.png)

1. 打开 IIS。

2. 在连接窗口中点击你的服务器。

3. 点击安全部分的“证书”。

4. 在操作窗口中点击“创建证书请求”。

![](img/5a2c5fda68d42e5d65f51850276e49ec_258_1.png)

图 7-78：准备证书请求

5. 按照向导创建证书，也称为 CSR。

   a. 组织：使用注册域名的业务。

   b. 组织单位：使用公司的部门。

   c. 通用名称：输入计划使用的完整域名或 URL，例如 `formulationspro.com`。你也可以使用通配符域名如 `*.formulationspro.com`。但这通常需要付费。

   d. 国家：使用你国家的两位 ISO 代码，美国使用 `US`。

   e. 州/省：使用你所在州的全称，例如 `California`。

   f. 城市/位置：使用你所在城市的全称，例如 `San Diego`。

6. 点击下一步

7. 在加密服务提供商窗口中，选择长度为 2048 位的 Microsoft RSA 加密提供商。

8. 输入你想保存的路径（例如桌面文件夹）并点击完成。

9. 将证书发送给你的证书颁发机构（CA）。你购买 SSL 证书的公司（例如 Verisign, Go Daddy 等）。某些公司可能要求你请求并复制/粘贴内容到他们的 Web 服务器提交。

10. 他们通常会通过你的服务器向你发送文件。然后点击操作窗口中的“完成证书链接”并按照向导安装证书。

![](img/5a2c5fda68d42e5d65f51850276e49ec_259_0.png)

11. 在连接窗口中选择你的站点。

12. 在操作窗口中点击“绑定”。你的常规 HTTP（端口 80）绑定应该是活动状态的。

13. 编辑端口 80 绑定，并将主机名更改为你的网站（例如 `formulationspro.com`）。这将告诉 IIS 监听任何使用该域名网站文件夹的请求。

14. 现在点击“添加”以安装 SSL 绑定。选择类型为主机，端口为 443。你应该能够从绑定的弹出菜单中选择你新安装的证书。

15. 完成后保存，你的网站现在应该已启用 SSL（即 https）。

## 在 OS X 上为你的网站绑定 SSL 证书。

在 OS X 服务器上为网站绑定 SSL 证书与 Windows 非常相似，尽管步骤要少得多。

- 1. 打开服务器管理（Server Admin）。从服务器列表中点击你的 Web 服务器。然后点击证书（Certificates）图标。

- 2. 点击加 + 按钮创建证书身份（Certificate Identity）。

![](img/5a2c5fda68d42e5d65f51850276e49ec_260_0.png)

图 7-80：创建一个新的证书身份。

- 3. 输入你网站的域名。

- 4. 选择身份类型为自签名根（Self Signed Root）。别担心，当你从证书颁发机构安装签名证书时，它会自动更改。

- 5. 选择证书类型为 SSL 服务器（SSL Server）。

### 证书助手

### 创建你的证书

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

- 7. 点击操作图标并生成证书签名请求 (CSR)。这将在你的桌面上创建一个文本文件 (`.csr`)。该文件将被你发送给你的证书颁发机构（CA）和/或复制/粘贴到你的网站上。每个 CA 接收文件的方式略有不同。CA 将向你返回一个签名证书，你将在接下来的步骤中放置它。

![](img/5a2c5fda68d42e5d65f51850276e49ec_261_0.png)

| 名称 | 过期 |

|---|---|

| formulationspro.com | 2013/2/28 |

| formulationspro.com | 2013/7/11 |

图 7-82：生成发送给证书颁发机构 (CA) 的证书签名请求 (CSR)。

- 8. 当你收到签名证书后，在列表中选择自签名证书。然后点击操作图标并选择用签名或更新的证书替换证书（Replace Certificate with Signed or Renewed Certificate）。

### 服务器管理: mailserver1.local: 证书

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

### 服务器管理: mailserver1.local | Web

| 概览 | 日志 | 站点 | Smartsgo |

|---|---|---|------|

| 已启用 | 主机名 | IP 地址 | 端口 |

| ✓ | mail.formulationspro.com | 192.168.1.7 | 8080 |

![](img/5a2c5fda68d42e5d65f51850276e49ec_263_0.png)

图 7-85：为你的网站安装签名 SSL 证书。

## 重配置 FileMaker Server

此时，如果你在浏览器中打开默认网页（Windows 上的 `iisestart.html` 或 Mac 上的 `index.html`），你的 Web 服务器在 http 和 https 上都运行得非常出色。然而，你会很快发现，如果你尝试从数据库访问动态 PHP 页面，一切都无法运行且 Web 发布引擎会崩溃。糟糕了！FileMaker 有一些晦涩的文档（技术文章 #7619）介绍如何配合 SSL 证书使用 cURL。别担心，这项工作不需要了解任何关于 cURL 的知识。执行以下任务以启用 cURL 库：

- 1. 打开位于以下路径的 FileMaker API 文件：

`/FileMaker Server/Web Publishing/publishing-engine/php/FileMaker/conf/filemaker-api`

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

- 3. 通过打开 FileMaker Server控制台 (`http://localhost:1600`) 来编辑 Web 发布部署。按照向导安装服务器部署。

### 部署助手

### 部署进度

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

此时，如果你在浏览器中打开默认网页（Windows 上的 `iisestart.html` 或 Mac 上的 `index.html`），你的 Web 服务器在 http 和 https 上都运行得非常出色。然而，你会很快发现，如果你尝试从数据库访问动态 PHP 页面，一切都无法运行且 Web 发布引擎会崩溃。糟糕了！FileMaker 有一些晦涩的文档（技术文章 #7619）介绍如何配合 SSL 证书使用 cURL。别担心，这项工作不需要了解任何关于 cURL 的知识。执行以下任务以启用 cURL 库：

- 1. 打开位于以下路径的 FileMaker API 文件：

`/FileMaker Server/Web Publishing/publishing-engine/php/FileMaker/conf/filemaker-api`

- 2. 取消以下代码的注释：

```
$_FM_CONFIG['cURLOptions'] = array(CURLOPT_SSL_VERIFYPEER => false)
```

### 部署助手

### 部署进度

证书身份由公共证书和私钥组成。这些证书身份可以用于保护你的网络通信：

| 名称 | 过期 |

| --- | --- |

| formulationspro | 2013/8/9 |
