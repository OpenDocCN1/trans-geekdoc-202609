
要安装带 MySQL 支持的 PHP 5 for Windows，您需要下载一个包含 PHP 所需所有文件的 Zip 文件， 以下步骤说明如何在 Windows 上安装 PHP：

- 1. **将你的 Web 浏览器指向** www.php.net.
- 2. **点击下载。**
- 3. **前往 Windows Binaries 部分。** 点击最新版本 PHP（截至本文撰写时为 5.0.0）的 Zip 包下载链接。
  一个对话框打开。
- 4. **点击镜像网站的链接以从中下载文件，并选择离您最近的站点。**
  一个对话框打开。
- 5. **选择保存文件的选项。**
  一个对话框打开，让您可以选择文件保存的位置。
- 6. **导航到您希望文件下载到的位置。** 这应是一个临时位置，例如下载目录。然后点击保存。
  下载完成后，您会在下载位置看到一个包含所需所有文件的文件。该文件名为 php，后跟版本号和 win32.zip。对于当前版本，文件名为 php5.0.0-Win32.zip。
- 7. **将 .zip 文件中的文件解压到您希望安装 PHP 的目录中，例如 c:\php。**
  如果您双击 .zip 文件，它应该会在计算机上用于解压 .zip 文件的软件中打开，例如 WinZip 或 PKZIP。选择提取菜单项并选择要将文件解压到的目录。C:\php 是一个不错的安装选择，因为许多配置文件假定 PHP 安装在那里，因此默认设置更有可能正确。
  最好不要将 PHP 安装在路径中包含空格的目录中，例如 Program Files/PHP 中。它有时会导致问题。
  您现在拥有一个包含多个子目录的目录，其中包含您所需的文件。
- 8. **将 MySQL 所需的文件复制到 PHP 主目录。**
  该文件位于 PHP 安装目录中的 ext 子目录中。根据您使用的 MySQL 版本复制以下文件之一：

![](img/d82df0828cfbc6d6be1e9a991861f3b7_424_0.png)

```
ext\php_mysql.dll   (for MySQL 4.0 or earlier)
ext\php_mysqli.dll  (for MySQL 4.1 or later)
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_425_0.png)

![](img/d82df0828cfbc6d6be1e9a991861f3b7_425_1.png)

将这两个文件复制到主 PHP 目录，例如 `c:\php`。

另一个名为 `libmysql.dll` 的文件也是 MySQL 支持所必需的。该文件应已位于主 PHP 目录中。如果不在那里，您需要找到它并复制到那里。如果它不在您的 PHP 目录中，它通常随 MySQL 一起安装，因此请在 MySQL 安装的目录中找到它，也许在 bin 子目录中，例如 `c:\mysql\bin`。

偶尔 PHP 需要找不到的 DLL 文件。当这种情况发生时，运行 PHP 程序时 PHP 会显示错误消息，称找不到特定的 DLL。您通常可以在 `ext` 子目录中找到该 DLL 并将其复制到主 PHP 目录。

- 9. **配置您的 Web 服务器。**
  下一节提供配置 Web 服务器的说明。
- 10. **配置 PHP。**
  请遵循本章后面部分中的说明。

## 配置 PHP 的 Web 服务器

您的 Web 服务器需要配置为识别 PHP 脚本并运行它们。请按照您 Web 服务器部分的步骤操作：

### 配置 Apache

您必须在 PHP 能够正常运行之前编辑名为 `httpd.conf` 的 Apache 配置文件。要为 PHP 配置 Apache，请按照以下步骤操作：

- 1. **打开 httpd.conf 进行编辑。**
  您可能可以通过选择 开始→程序→Apache HTTPD Server→Configure Apache Server→Edit Configuration 来编辑它。
  如果 Edit Configuration 不在您的开始菜单上，请在硬盘上找到 `httpd.conf` 文件，通常在 Apache 安装目录的 `conf` 子目录中（例如，`c:\program files\Apache group\Apache\conf`）。使用编辑器打开此文件，例如记事本或 WordPad。
- 2. **为 PHP 安装的目录设置一个别名。**
  `ScriptAlias` 语句用于为 PHP 安装的目录设置名称。在 `httpd.conf` 文件中查找 `ScriptAlias` 语句。您可能会看到一些用于其他软件的语句。如果没有 PHP 的，请添加以下内容：

```
ScriptAlias /php/ "c:/php/"
```

### 配置 IIS

要配置 IIS 与 PHP 协同工作，请按照以下步骤操作：

- 1. **进入 IIS 管理控制台。**
  您应该可以通过选择 开始→程序→管理工具→Internet Services Manager 或 开始→设置→控制面板→管理工具→Internet Services Manager 进入。
- 2. **右键单击您的网站（例如 Default Web Site）。**
- 3. **选择属性。**
- 4. **选择主目录选项卡。**
- 5. **点击配置按钮。**
- 6. **选择 App Mappings 选项卡。**
- 7. **点击添加。**
- 8. **在可执行文件框中，输入 PHP 解释器的路径：例如，输入 c:\php\php-cgi.exe。**
- 9. **在扩展名框中，输入 .php。**
  这将是与 PHP 脚本关联的扩展名。
- 10. **选择脚本引擎复选框。**
- 11. **点击确定。**
  如果您希望除 .php 之外的任何其他扩展名，例如 .phtml，也由 PHP 处理，请重复步骤 6–10。

### 配置 PHP

PHP 使用名为 php.ini 的文件中的设置来控制其某些行为。PHP 在启动时查找 php.ini 并使用找到的设置。如果 PHP 找不到该文件，它将使用一组默认设置。

除非在安装期间更改，否则 php.ini 文件的默认位置如下之一：

- ✔ **Windows：** 系统目录，根据 Windows 版本而定，如下所示：
  - Windows 98/Me/XP: `windows`
  - Windows NT/2000: `winnt`
- ✔ **Unix/Linux/Mac：** `/usr/local/lib`

![](img/d82df0828cfbc6d6be1e9a991861f3b7_428_0.png)

如果在安装期间未安装 php.ini 文件，您现在需要安装它。PHP 发行版中包含一个具有默认设置、名为 php.ini-dist 的配置文件。将此文件复制到适当的位置，例如上面提到的默认位置，并将其名称更改为 php.ini。

如果您已安装了 PHP 的早期版本（例如 PHP 4.3），请在用 PHP 5 的 php.ini 文件覆盖它之前备份 php.ini 文件的副本。然后您可以查看当前使用的设置并更改新 php.ini 文件中的设置以匹配当前设置。

要配置 PHP，请按照以下步骤操作。

- 1. **打开 php.ini 文件进行编辑。**
- 2. **激活 mysql 或 mysqli 支持。**
- 3. **仅当您使用 PHP 与 IIS Web 服务器时，关闭强制重定向。找到以下行：**
- 4. **保存 php.ini 文件。**
- 5. **在新设置生效之前，您可能需要重新启动 Apache 服务器。**

查找扩展列表。找到 mysql（如果您使用的是 MySQL 4.0 或更早版本）或 mysqli（如果您使用的是 MySQL 4.1 或更高版本）的行，如下所示：

```
;extension=php_mysql.dll
;extension=php_mysqli.dll
```

注意行开头的分号（;）。要激活扩展，请删除分号。如果扩展行不在您的 php.ini 文件中，请添加它。

```
;cgi.force_redirect = 1
```

您需要删除分号以使设置生效，并将 1 改为 0。更改后，该行如下所示：

```
cgi.force_redirect = 0
```

总体而言，其余默认设置允许 PHP 正常运行，但您可能需要出于特定原因编辑其中一些设置。我在全书中讨论 php.ini 文件中的设置，当讨论可能需要更改设置的话题时。例如，PHP 错误处理操作可以通过 php.ini 文件中的设置来更改。错误处理的可能设置及其影响在第 4 章中讨论。
