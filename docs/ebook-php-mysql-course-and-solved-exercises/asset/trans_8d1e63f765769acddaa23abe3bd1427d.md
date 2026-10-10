

# 在 macOS 上下载并安装 XAMPP

在下载页面，你将看到不同版本的 XAMPP。通过点击相应的下载按钮，选择最适合 macOS 的版本。

![Image](images/image-4.png)

下载完成后，打开下载的文件（应位于 Mac 的“下载”文件夹中）。

双击安装文件以开始 XAMPP 安装过程。

按照屏幕上的说明在 Mac 上安装 XAMPP。你可能需要输入管理员密码以授权安装。

![Image](images/image-5.png)

当你点击 XAMPP 图标时，可能会出现一个警告窗口，提示“macOS 无法检查此 App 是否包含恶意软件”。在这种情况下，根据你的 Mac 系统版本，你可能需要修改 Mac 的安全设置才能安装 XAMPP：

*   打开“系统设置”。
*   点击“隐私与安全性”，向下滚动并点击“仍要打开”按钮，以确认你打开或安装该 App 的意图。

![Image](images/image-6.png)

安装完成后，你将看到一个确认窗口。点击“完成”关闭安装程序。

XAMPP 现已安装在你的 Mac 上。要启动服务（Apache、MySQL 等），请从“应用程序”文件夹打开 XAMPP 并运行 `manager-osx` 文件，然后点击相应按钮以激活所需服务。

![Image](images/image-7.png)

服务启动后，你可以通过在浏览器地址栏输入 `localhost` 来访问 XAMPP 管理界面。

这些步骤应能让你成功在 Mac 上下载并安装 XAMPP。

# 在 Windows 上下载并安装 XAMPP

以下是在 Windows 上下载并安装 XAMPP 的步骤：

访问 Apache Friends 官方网站：`https://www.apachefriends.org/fr/download.html`

在下载页面，你将看到不同版本的 XAMPP。通过点击相应的下载按钮，选择最适合 Windows 的版本。

下载完成后，通过双击打开下载的文件。它应位于你通常下载文件的文件夹中。

XAMPP 安装程序将打开。如果 Windows 询问你是否授权更改，请点击“是”。

安装程序将引导你完成安装过程。选择你想要安装的组件（默认全选）并选择安装 XAMPP 的文件夹。

点击“安装”按钮开始安装。等待过程完成。

安装完成后，系统将提示你启动 XAMPP 组件（Apache、MySQL 等）。点击“完成”关闭安装程序。

XAMPP 现已安装在你的电脑上。要启动服务，请从“开始”菜单打开 XAMPP 并点击相应按钮启动 Apache 和 MySQL。

服务启动后，你可以通过在浏览器地址栏输入 `localhost` 来访问 XAMPP 管理界面。

这些步骤应能让你成功在 Windows 电脑上下载并安装 XAMPP。

# 下载并安装文本编辑器

安装 XAMPP 后，我们建议你下载并安装一个文本编辑器，用于编写和编辑代码文件。以下是几款最流行、适合 Web 开发的文本编辑器示例：

**Sublime Text**：Sublime Text 是一款轻量级、高度可定制的文本编辑器，拥有许多对 Web 开发有用的功能，如语法高亮、自动补全和项目管理。

下载链接：`https://www.sublimetext.com/`

**Visual Studio Code**：Visual Studio Code (VS Code) 是由微软开发的源代码编辑器。它具有可扩展性，提供 Git 集成、调试功能以及众多用于 Web 开发的扩展。

下载链接：`https://code.visualstudio.com/`

**Brackets**：Brackets 是由 Adobe 开发的开源文本编辑器。它专为 Web 开发设计，包含实时预览、语法高亮、自动补全和扩展支持等功能。

下载链接：`https://brackets.io/`

你可以选择最适合你 Web 开发需求和偏好的文本编辑器。安装好首选编辑器后，即可开始为 Web 项目创建和编辑代码文件。

# 在 XAMPP 中创建项目

在 XAMPP 中，你不直接创建项目，而是在 `htdocs` 目录中为项目创建目录。具体操作如下：

**查找 htdocs 目录：** `htdocs` 目录是存放网站文件的位置。默认情况下，该目录位于 XAMPP 安装文件夹中。Windows 上通常位于 `C:\xampp\htdocs`，Mac 上位于 `/Applications/XAMPP/htdocs`。

**为项目创建新目录**：在 `htdocs` 目录中，为项目创建一个新目录。你可以给它起任何喜欢的名称，例如 `ebookphp`。

创建项目目录后，你可以将所有网站文件和文件夹放入其中。这可以包括 HTML、CSS、PHP、JavaScript 文件、图片等。

**通过浏览器访问项目：** 将项目文件放入创建的目录后，打开 Web 浏览器，在地址栏输入以下 URL 即可访问你的网站：`http://localhost/ebookphp`。请务必将 `ebookphp` 替换为你为项目创建的目录名称。

遵循这些步骤，你就可以在 XAMPP 中创建并访问项目。请确保在 XAMPP 中启动 Apache 和 MySQL 服务，以便网站正常运行。

# 你的第一个 PHP 脚本

以下是使用 XAMPP 和 `htdocs` 文件夹中创建的 `ebookphp` 目录创建第一个 PHP 脚本的步骤：

按上述说明启动 XAMPP，并通过点击相应的“启动”按钮启动 Apache。确保它们显示为绿色，表示正在运行。

打开你选择的文本编辑器以编写 PHP 脚本。

在文本编辑器中创建一个新文件，并将其保存到 XAMPP 安装目录下 `htdocs` 文件夹中的 `ebookphp` 目录内。将此文件命名为 `first_script.php`。

编写第一个 PHP 脚本：在 `first_script.php` 文件中编写以下 PHP 代码：

```php
<?php

echo "Hello, world!";

?>
```

编写完 PHP 脚本后，保存文件。

启动你常用的 Web 浏览器（如 Google Chrome、Mozilla Firefox 等）。

在浏览器地址栏输入以下 URL：`http://localhost/ebookphp/premier_script.php` 并按“回车”。

你应该会在浏览器中看到显示“Hello, world!”，表明你的第一个 PHP 脚本已成功执行。

![Image](images/image-8.png)

恭喜！你刚刚使用 XAMPP 创建并执行了第一个 PHP 脚本。这个简单的例子标志着你使用 PHP 进行 Web 开发的精彩旅程的开始。

# 错误显示

正如你所知，犯错，尤其是语法错误，非常常见，我可以向你保证，世界上没有不犯错的开发人器。因此，显示这些错误的提示非常有用。

事实上，取决于服务器的配置，错误可能完全不显示！许多初学者在浏览器中运行 PHP 页面时发现什么也看不到，感到困惑。没有错误消息，只有一片空白，例如。当代码中存在错误而 PHP 服务器未配置为显示错误时，就会发生这种情况。

要解决此问题，只需对 XAMPP 的 `php.ini` 文件进行一些更改。

要找到该文件的位置，只需将下面的代码添加到之前创建的 `first_script.php` 文件中（或项目中的任何其他文件）。

```php
<?php

phpinfo();

?>
```

