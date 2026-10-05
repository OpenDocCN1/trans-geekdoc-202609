
如果用户点击“复制”（Duplicate）按钮，你将在数据库中运行 PHP 复制记录脚本（Duplicate Record）。没有理由让 PHP 让过程变得过于复杂。将父记录的 ID 传递给数据库并在服务器上运行脚本要简单得多。

```php
else {
  if ($_POST['duplicate'] == 'Duplicate') {
    $layout = 'Demo php';
    $script = 'PHP Duplicate Record';
    $parameter = $_REQUEST['id'];
    $request = $frm->newPerformScriptCommand($layout, $script, $parameter);
    $result = $request->execute();
    $display = '<p>the record was duplicated successfully.</p>';
  }
```

如果用户点击“取消”（Cancel）按钮，你可以更新显示消息。我喜欢包含一个返回列表页的链接。

```php
else {
  $display = '<p>Cancel: The record was not duplicated.</p>';
  $display = '<a href="DuplicateRelatedList.php">Click here to return to the list view</a></p>';
}?
```

使用 $display 变量输出 PHP 代码创建的 html。

```html
<html
<head>
<title>Duplicate Record -> Detail</title>
</head>
<body>
<?php echo $display; ?>
</body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_255_0.png)

图 7-76：DuplicateRelatedDetail.php 文件。

# PHP 复制记录脚本

该脚本的任务是获取网页传递的记录 ID 并找到父记录。一旦找到父记录，它将复制父记录和相关记录。即使对于 FileMaker 客户端编程，这也是一个非常常见的脚本。

首先确保你开启了“允许用户取消”（User Abort）和“设置错误捕获”（Set Error Capture）。

- 允许用户取消 [  ]
- 设置错误捕获 [ On ]

从 PHP 代码传递的脚本参数创建 $RecordID 变量。

```filemaker
Set Variable [ $RecordID; Value:Get(ScriptParameter) ]
```

使用 Demo php 布局查找父记录。

```filemaker
Go to Layout [ "Demo php" (php_demo) ]
Enter Find Mode [ ]
Set Field [ php_demo::RecordID; $RecordID ]
Perform Find [ ]
```

确保捕获错误，并在未找到记录时停止脚本。

```filemaker
If [ Get(LastError) > 0 ]
Halt Script
End If
```

复制记录并存储新记录的记录 ID，以便将其传递给新相关记录的外键。

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

脚本名称：PHP Duplicate Record

- 允许用户取消 [ On ] - 不支持的脚本步骤。如果此处包含，FM 允许用户取消。

*(注：OCR 文本包含一些乱码；根据提供的文本：)*
- 允许用户取消 [0]
- 设置变量 ($User, On) - 如果 FileMaker 返回错误框未显示或将产生
- 设置错误捕获 (0)
- GetRecord($RecordID) 由 PHP 脚本。
- 设置变量 ($RecordID, GetScriptParameter())
- 转布局 ('Demo php', php_demo)
- 结束循环
- 设置字段 (php_demo.RecordID, $RecordID)
- 执行查找
- 如果错误 - 未找到记录。
- 如果 (GetLastError() > 0)
- 退出循环
- 结束
- 复制记录并存储新记录的 PK，以便可以传递给 related_data 的外键。
- 复制记录/请求
- 设置变量 ($Value, $RecordID)
- 转到列表 (List, $PK)
- 转到相关记录 来自表: "Related_data" 使用布局: "Related Data php" (related_data) 仅显示相关记录
- 转到相关记录 来自表: "Related_data" 使用布局: "Related Data php" (related_data_) 复制原始记录的门户记录，为每个记录创建一个副本并更改外键。
- 循环
- 复制记录/请求
- 设置字段 (related_data.FK, $PK)
- 跳过记录
- 退出循环 如果 (GetFoundCount = 0)
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
   c. 通用名称：输入计划使用的完整域名或 URL，例如 formulationspro.com。你也可以使用通配符域名如 *.formulationspro.com。但这通常需要付费。
   d. 国家：使用你国家的两位 ISO 代码，美国使用 US。
   e. 州/省：使用你所在州的全称，例如 California。
   f. 城市/位置：使用你所在城市的全称，例如 San Diego。
6. 点击下一步
7. 在加密服务提供商窗口中，选择长度为 2048 位的 Microsoft RSA 加密提供商。
8. 输入你想保存的路径（例如桌面文件夹）并点击完成。
9. 将证书发送给你的证书颁发机构（CA）。你购买 SSL 证书的公司（例如 Verisign, Go Daddy 等）。某些公司可能要求你请求并复制/粘贴内容到他们的 Web 服务器提交。
10. 他们通常会通过你的服务器向你发送文件。然后点击操作窗口中的“完成证书链接”并按照向导安装证书。

![](img/5a2c5fda68d42e5d65f51850276e49ec_259_0.png)

11. 在连接窗口中选择你的站点。
12. 在操作窗口中点击“绑定”。你的常规 HTTP（端口 80）绑定应该是活动状态的。
13. 编辑端口 80 绑定，并将主机名更改为你的网站（例如 formulationspro.com）。这将告诉 IIS 监听任何使用该域名网站文件夹的请求。
14. 现在点击“添加”以安装 SSL 绑定。选择类型为主机，端口为 443。你应该能够从绑定的弹出菜单中选择你新安装的证书。
15. 完成后保存，你的网站现在应该已启用 SSL（即 https）。
