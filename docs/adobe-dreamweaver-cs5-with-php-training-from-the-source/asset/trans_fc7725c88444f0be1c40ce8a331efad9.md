
如果不想购买 MAMP 的商业版本，你可以手动编辑 hosts 文件和 Apache 配置文件。 hosts 文件是隐藏文件，但可以在 BBEdit 或 TextWrangler 中轻松编辑（参考本课前文“编辑 php.ini”侧边栏）。

![Image](graphics/tip.jpg)`TIP:`

Mac OS X 预装的 Apache 使用不同的设置。如果你使用的是预装版本，请按照 [http://foundationphp.com/tutorials/vhosts_leopard.php](http://foundationphp.com/tutorials/vhosts_leopard.php) 的说明进行操作。该指南最初针对 Mac OS X 10.5，但同样适用于 10.6。

**1.** 在 BBEdit 或 TextWrangler 中，选择 **File > Open Hidden**。

**2.** 在打开对话框中，将 **Enable** 设置为 **Everything** 或 **All Files**。如果有显示隐藏文件的选项，请确保已选中。

**3.** 选择 **Macintosh HD:private:etc:hosts**，点击 **Open** 打开 hosts 文件。

**4.** 在文件底部的新行上，列出每个虚拟主机的 IP 地址和对应的名称。

`127.0.0.1  phpcs5`

输入 `127.0.0.1`（循环回退 IP，表示本机）后跟一个或多个空格，再输入虚拟主机名称。输入时会出现提示文件拥有者为 “root”，点击 **Unlock** 确认编辑。

**5.** 保存并关闭 hosts 文件。由于它是系统文件，系统会要求输入 Mac 管理员密码以确认更改。

**6.** 接下来需要编辑的文件是 Apache 配置文件 **httpd.conf**。该文件不隐藏，直接选择 **File > Open**，然后定位到 `Applications:MAMP:conf:apache:httpd.conf`。

**7.** 向文件底部滚动，找到以下行：

`# NameVirtualHost \*`

删除行首的 `#` 号。

**8.** 由于虚拟主机替换了原有配置，需要为 **localhost** 和每个要添加的虚拟主机创建一个虚拟主机块。在文件底部添加以下代码：

`<VirtualHost \*>`

  `DocumentRoot /Applications/MAMP/htdocs`

   `ServerName localhost`

`</VirtualHost>`

`<VirtualHost \*>`

   `DocumentRoot /Users/your_name/Sites/phpcs5`

  `ServerName phpcs5`

`</VirtualHost>`

对于每个虚拟主机，`DocumentRoot` 的值是站点所在文件夹的路径，`ServerName` 是虚拟主机的名称。示例假设虚拟主机名称为 “phpcs5”，文件夹位于个人 **Sites** 目录下的 “phpcs5” 文件夹中（将 `your_name` 替换为你的 Mac 用户名）。若文件夹名称包含空格，请用双引号包裹路径。

**9.** 保存并关闭 **httpd.conf**。重启 Apache 后，仍可访问 [http://localhost](http://localhost)。存放在 **phpcs5** 文件夹中的文件可通过 [http://phpcs5](http://phpcs5) 访问。

### Setting Up a PHP Site in Dreamweaver CS5

Dreamweaver 基于在本地计算机上创建网站的精确副本。因此，在进行其他操作之前，需要先向程序提供一些基本的站点信息。Dreamweaver CS5 已简化了此过程。只需为站点命名并指定本地存储文件的位置即可开始。其余设置可在需要时再处理。但对于 PHP 站点，建议同步定义测试服务器。

理论上，你可以将 PHP 文件存放在计算机的任何位置，Dreamweaver 在使用 **Live View** 或 **Preview in Browser** 时会将文件复制到测试服务器。这样会产生两份相同的文件副本，建议将项目文件存放在测试服务器的文档根目录中。同时，还需告诉 Dreamweaver 测试服务器的 URL。

上述信息取决于是否为本书练习创建了虚拟主机。

#### 使用虚拟主机

如果已创建虚拟主机，请将文件存放在为 **phpcs5** 虚拟主机选择的服务器根目录文件夹中。

URL 为 **[http://phpcs5/](http://phpcs5/)**。

#### 使用服务器根目录的子文件夹

如果未创建虚拟主机，则本地站点文件夹和测试服务器文件夹为服务器根目录的子文件夹：

- **XAMPP**: `C:\\xampp\\htdocs\\phpcs5`
- **WampServer**: `C:\\wamp\\www\\phpcs5`
- **Easyphp**: `C:\\EasyPHP\\www\\phpcs5`
- **独立的 Windows Apache 安装**: `C:\\Program Files\\Apache Software Foundation\\Apache2.2\\htdocs\\phpcs5`（64 位 Windows 需在 Program Files 后加 (x86)）
- **IIS**: `C:\\inetpub\\wwwroot\\phpcs5`
- **MAMP**: `Macintosh HD:Applications:MAMP:htdocs:phpcs5`
- **Mac OS X 预装 Apache**: `Macintosh HD:Library:WebServer:Documents:phpcs5`

URL 为 **[http://localhost/phpcs5/](http://localhost/phpcs5/)**。

#### 创建站点定义

使用以下步骤为本书的 PHP 站点设置站点定义：

**1.** 在 Dreamweaver CS5 中，选择 **Site > New Site** 打开 **Site Setup** 对话框。

![Image](graphics/fig02_06.jpg)

如果之前使用过旧版 Dreamweaver，会发现 **Basic** 与 **Advanced** 标签页已被移除（Mac 系统中为按钮）。

**2.** 在 **Site Name** 文本框中输入站点名称，例如 **PHP CS5**。此名称在 Dreamweaver 内部用于识别 **Files** 面板中的站点，建议具描述性并可包含空格。

**3.** 点击 **Browse for folder** 图标，在弹出的文件夹选择对话框中选定用于存放站点文件的本地文件夹。

此时可以直接点击 **OK**，但最好同步设置测试服务器。

**4.** 在左侧列表中点击 **Servers**，打开服务器面板，用于定义站点连接的服务器。

![Image](graphics/fig02_07.jpg)

**5.** 点击面板底部的 **plus (+)** 按钮，打开另一个对话框以定义测试服务器的设置。

![Image](graphics/fig02_08.jpg)

**6.** 在 **Server Name** 文本框中输入描述性的服务器名称，例如 **Testing Server**。

**7.** 点击 **Connect using** 下拉菜单，选择 **Local/Network** 以便于本地测试服务器，仅保留 **Server Folder** 与 **Web URL** 两个字段。

**8.** 在 **Server Folder** 文本框中，选择步骤 3 中使用的相同文件夹。

**9.** 在 **Web URL** 文本框中输入本地测试服务器的 URL，确保以斜杠结尾。

下图展示了为名为 “phpcs5” 的虚拟主机（位于 `C:\\vhosts\\phpcs5`）配置的设置示例。根据所使用的环境使用相应的值。

![Image](graphics/fig02_09.jpg)

**10.** 点击对话框顶部的 **Advanced** 按钮，展开远程服务器与测试服务器的独立设置区域。

**11.** 在 **Testing Server** 部分底部的 **Server Model** 菜单中，选择 **PHP MySQL**。

![Image](graphics/fig02_10.jpg)

点击 **Save**。

**12.** 测试服务器应出现在 **Servers** 面板中。确保 **Remote** 框未被选中，而 **Testing** 框已选中。此时底部的按钮会变为活动状态，可用于添加、删除、编辑或复制服务器。

![Image](graphics/fig02_11.jpg)

**13.** 点击 **Save** 关闭 **Site Setup** 对话框。

#### 设置多个服务器

