

ASP用户可以测试整个登录应用程序。打开 register.asp，并创建个人资料。然后使用用户名和密码登录。一如既往，也尝试破坏应用程序。注册两次相同的名字。尝试使用错误密码登录。尝试输入电话号码而不是电子邮件地址。等等。

ColdFusion用户在测试应用程序之前有一个快速的任务要做：他们需要创建 application.cfm 文件，该文件控制Web应用程序框架。ASP用户不必担心创建 global.asa 文件——即使没有它，ASP也能很好地处理会话管理。

PHP用户也可能有他们自己的快速任务。取决于你的配置，会话管理可能未正确设置。此问题通常出现在Windows PHP用户中，而不会出现在Macintosh PHP用户中。有关详细信息，请参见本课后面部分“确保已启用会话管理（仅限Windows PHP用户）”部分。

## 创建 APPLICATION.CFM（仅限COLDFUSION）

“登录用户”服务行为的功能之一是，当用户成功登录时创建会话变量。问题是，会话作用域默认处于非活动状态，这意味着登录页面将无法工作。您需要在ColdFusion Web应用程序框架中激活会话管理。这样做只需创建一个新文件（Application.cfm），并输入一行代码。

- 1) 在代码视图中创建一个新页面。删除页面上的所有代码，包括任何HTML、XML或其他标记或代码。

Application.cfm 不是常规Web页面，因此开始时不应在其中包含任何代码。

- 2) 在第一行中，键入以下代码：

```
<cfapplication sessionmanagement="yes" setclientcookies="yes" name="newland_tours" sessiontimeout="#CreateTimeSpan(0, 0, 20, 0)#"/>
```

<cfapplication> 标签可有效创建应用程序并启用Web应用程序框架。它有多个属性，其中许多是可选的。一个必需的属性是 name，即您想为应用程序指定的任意名称。此处使用的其他属性用于启用会话管理、启用Cookie设置以及创建会话超时。

您会注意到，sessiontimeout 属性中不是指定一段简单的时间，而是一个函数 CreateTimeSpan()。该函数采用四个参数，分别代表天数、小时数、分钟数和秒数。因此，sessiontimeout 设置为20分钟。换句话说，如果用户处于非活动状态，或离开网站去浏览其他页面超过20分钟，则与该用户关联的所有会话变量都将被清除。从实际角度来看，这意味着用户将需要重新登录。

![](img/43fd0127a958864ab2d93e28efe683e7_407_0.png)

- 3) 保存、关闭并上传 Application.cfm。

此时，您可以测试在本课中添加的注册和登录功能。如前所述，尝试输入您能想到的每种变体来破坏应用程序。

## 确保已启用会话管理（仅限Windows PHP用户）

使用默认设置安装PHP时，会话管理处于启用状态。当PHP开始使用会话时，它会将事务信息存储在文本文件中。安装PHP时，此文本文件也应已设置，或者至少应该如此。不幸的是，Windows上某些PHP版本的默认设置使用错误的路径来查找该文本文件。结果是会出现一些看不见的错误。

![](img/43fd0127a958864ab2d93e28efe683e7_407_1.png)

如果在测试 login.php 时看不到此错误，则可以跳至“限制对页面的访问”部分。

仔细查看错误时，您会发现它试图打开一个路径极不可能的文件，类似于 /tmp\sess_sess_6002c7a1f3cba0838a2d56d8e659b615, 0_RDWR)。使此路径如此不同寻常的是，它以正斜杠 (/) 开头，而所有Windows路径都使用反斜杠 (\)。这很可能是一个源于PHP的Unix起源的错误；Unix（包括Mac OS X）中的路径都使用正斜杠。更糟的是，它正在查找的文件夹（tmp）不存在！

修复此问题相对容易，只需两步：

- 修改指定PHP应使用哪个路径映射到会话目录的 .ini 文件
- 创建 .ini 文件实际指向的目录。

- 1) 导航到 C:\windows\php.ini。双击以在记事本中打开它。

此文件包含PHP实现的大部分配置说明。请记住，在Unix世界中，最常见的界面不是对话框或向导，而是文本文件。

- 2) 使用“编辑”>“查找”搜索 session.save_path。查找指定保存目录的路径。

![](img/43fd0127a958864ab2d93e28efe683e7_408_0.png)

请记住，分号后的任何内容都被注释掉了，可能是文档。因此，您发现的第一个 session.save_path 实例很可能是文档的一部分，而不是问题本身。

您需要的实例后面跟着一个路径。您的路径可能与屏幕截图中显示的不同。事实上，这就是问题所在！

```
[Session]
; Handler used to store/retrieve data.
; session.save_handler = files

; Argument passed to save_handler. In the case of files, this is the path
; where data files are stored. Note: Windows users have to change this
; variable in order to use PHP's session functions.
;
; As of PHP 4.0.1, you can define the path as:
;
;     session.save_path = "N;/path"
;
; where N is an integer. Instead of storing all the session files in
; /path, what this will do is use subdirectories N-levels deep, and
; store the session data in those directories. This is useful if you
; or your OS have problems with lots of files in one directory, and is
; a more efficient layout for servers that handle lots of sessions.
;
; NOTE 1: PHP will not create this directory structure automatically.
;         You can use the script in the ext/session dir for that purpose.
; NOTE 2: See the section on garbage collection below if you choose to
;         use subdirectories for session storage
; The file storage module creates files using mode 600 by default.
; You can change this by using
;
;     session.save_path = "N;MODE;/path"
;
; where MODE is the octal representation of the mode. Note that this
; does not overwrite the process's umask.
session.save_path = "C:\\PHP-4.1.2-Win32\\temp"

; whether to use cookies.
; session.use_cookies = 1

; This option enables administrators to make their users invulnerable to
; attacks which involve passing session ids in URLs; defaults to 0.
; session.use_only_cookies = 1
```

- 3) 修改路径，使其符合以下公式：

```
C:\php-[version_number]-Win32\temp\
```

也就是说，键入您看到的完全相同的内容，但将 [version_number] 替换为您的PHP副本的实际版本号。

如果您忘记了PHP副本的版本号，请查看硬盘上的 C:\ 目录。在那里列出的实际上是该文件夹的名称，而不完全是您的版本号，尽管通常版本号是目录名称的一部分。

```
NOTE 1: PHP will not create this directory structure automatically.
NOTE 2: You can use the script in the ext/session dir for that purpose.
        See the section on garbage collection below if you choose to
        use subdirectories for session storage
session.save_path = C:\PHP-4.1.2-Win32\temp\

whether to use cookies.
session.use_cookies = 1
```

- 4) 保存并关闭 php.ini。

您刚刚更新了PHP存储会话信息的位置。

- 5) 使用系统托盘中的Apache图标停止并重新启动Apache。

这将强制 php.ini 重新加载并实际应用新设置。

![](img/43fd0127a958864ab2d93e28efe683e7_409_0.png)

- 6) 在Windows资源管理器中，导航到 C:\php-[version_number]-Win32\ 并验证内部是否有一个名为 temp 的文件夹。
如果该文件夹不存在，请创建一个。

![](img/43fd0127a958864ab2d93e28efe683e7_410_0.png)

## 限制对页面的访问

到现在为止，您应该已经测试了注册和登录页面，并且它们应该按预期工作。唯一的问题是，在您为要阻止访问的页面实现页面限制功能之前，您的注册和登录框架并不十分有用。在此任务中，您将添加服务行为，以防止用户访问页面，除非他们先登录。

- 1) 打开 profiles.asp。

这是用户必须登录才能查看的页面之一。

- 2) 单击页面上的任何位置，插入“限制对页面的访问”服务行为，该行为位于“服务行为”菜单的“用户身份验证”子菜单中。在“基于限制”组中，选择“用户名”、“密码”和“访问级别”。

此对话框不仅让您限制对页面的访问；它还允许您根据用户的访问级别限制对页面的访问。

