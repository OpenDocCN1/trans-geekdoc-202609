
在 Windows 上，除非是非标准安装，相关文件是 `C:\Windows\System32\drivers\etc\hosts`。不幸的是，你在尝试编辑此文件时可能会遇到权限问题。我通过以管理员模式打开记事本（在开始菜单中右键单击记事本以获取此选项 ![Image](graphics/circle-f.jpg)），然后在记事本中打开该文件，成功解决了该问题。

![Image](graphics/20_figure_27_f.jpg)

![Image](graphics/circle-f.jpg)你可以以管理员模式打开记事本，以便编辑系统文件。

**2.** 在文件最末尾，添加：

```
127.0.0.1 forums.local
```

这将名称 `forums.local` 与 IP 地址 `127.0.0.1` 关联起来，即同一台计算机。

**3.** 保存文件。

**4.** 在 Web 浏览器中加载 `http://forums.local` ![Image](graphics/circle-g.jpg)。

![Image](graphics/20_figure_28_g.jpg)

![Image](graphics/circle-g.jpg)论坛站点，可通过 URL `http://forums.local` 在本地访问。

---

Tip

重复这两个步骤序列——在 Apache 中创建虚拟主机并将主机添加到 hosts 文件——每当你想要创建一个带有自己关联主机名的新 Web 站点项目时。

---

#### 使用 .htaccess 文件

如前所述，所有 Apache 配置实际上都可以在 `httpd.conf` 文件中完成。事实上，这样做是首选。但配置文件并不总是可供你编辑，因此了解如何使用 `.htaccess` 文件来更改站点功能也很有价值。

`.htaccess` 文件只是一个纯文本文件，名为 `.htaccess`（同样，没有文件扩展名，且开头的句点使其成为隐藏文件）。当放置在 Web 目录中时，`.htaccess` 文件中定义的指令将应用于该目录及其子目录。

使用 `.htaccess` 文件时常见的障碍是，必须授予权限以允许 `.htaccess` 更改服务器行为。根据安装和配置，在最严格的安全级别下，Apache 不允许 `.htaccess` 文件更改 Apache 行为。这在 `httpd.conf` 中通过如下代码实现：

```
<Directory />
  AllowOverride None
</Directory>
```

`Directory` 指令用于在 `httpd.conf` 中修改 Apache 在特定目录中的行为。在上述代码中，根目录（`/`）是目标，这意味着 Apache 根本不允许计算机上任何目录中进行覆盖——更改。因此，在创建 `.htaccess` 文件之前，主配置文件必须设置为允许在适用的 Web 目录（或目录）中进行覆盖。

`AllowOverride` 指令接受一个或多个标志，指示具体可以覆盖什么：

* `AuthConfig`，用于授权和认证
* `FileInfo`，用于执行重定向和 URL 重写
* `Indexes`，用于列出目录内容
* `Limit`，用于限制对目录的访问
* `Options`，用于设置目录行为，例如执行 CGI 脚本或索引文件夹内容的能力
* `All`
* `None`

---

**设置默认目录页面**

通常，Web 浏览器在请求时不指定文件，例如 `www.example.com/` 或 `www.example.com/folder/`。在这种情况下，Apache 必须决定做什么。历史上，如果目录中存在 `index.htm` 或 `index.html` 文件，Apache 会提供该文件。如果不存在索引文件，且服务器允许目录浏览，Apache 将改为显示目录中的文件列表（这不安全，但你无疑以前在网上见过）。

在这种情况下告诉 Apache 该做什么的适用指令是 `DirectoryIndex`。在其后，列出用作文件夹索引的文件，多个选项按优先顺序排列。例如，以下配置将尝试加载 `index.htm`，如果不存在则加载 `index.html`，如果仍不存在则加载 `index.php`：

```
DirectoryIndex index.htm index.html index.php
```

同样，`ErrorDocument` 指令告诉 Apache 发生服务器错误时提供什么文件。其语法是：

```
ErrorDocument error_code /page.html
```

错误代码值来自服务器状态代码，例如 401（未授权）、403（禁止）和 500（内部服务器错误）。对于每个代码，你可以指定应提供的页面。注意，你需要为错误文件提供绝对路径（即以 `/` 开头，这是 Web 根目录）。

---

例如，要允许在 forums 目录（刚创建）中覆盖 `AuthConfig` 和 `FileInfo`，`httpd.conf` 文件应包含：

```
<Directory /path/to/forums>
  AllowOverride AuthConfig FileInfo
</Directory>
```

只要这段代码位于任何 `AllowOverride None` 块之后，`forums` 目录中的 `.htaccess` 文件就能在从该目录（及其子目录）提供文件时对 Apache 的行为进行一些更改。

##### 允许 .htaccess 覆盖

**1.** 在任意文本编辑器或 IDE 中打开 `httpd.conf`。

**2.** 在相关站点的 `VirtualHost` 标签内，添加：

```
<Directory /path/to/directory>
</Directory>
```

`Directory` 标签是自定义 Apache 在特定目录或其子目录中行为的方式。在开始标签中，提供目标目录的绝对路径，例如 `C:\xampp\htdocs\somedir` 或 `/Applications/MAMP/htdocs/somedir`。

**3.** 在 `Directory` 标签内，添加 ![Image](graphics/circle-h.jpg)：

```
AllowOverride All
```

![Image](graphics/20_figure_29_h.jpg)

![Image](graphics/circle-h.jpg)更新后的虚拟主机配置，现在允许在 forums Web 目录中进行覆盖。

这是一个激进的解决方案，但行之有效。在公开可用的实时服务器上，你需要更具体地说明可以覆盖的确切设置，但在你的家用电脑上，这不会有问题。

**4.** 保存配置文件。

**5.** 重启 Apache。

---

Tip

`Directory` 指令不必放在相关站点的 `VirtualHost` 标签内，但放在那里是合理的。

---

---

Tip

如果不允许目录覆盖某项设置，`.htaccess` 文件将被忽略。

---

---

Tip

在 `.htaccess` 文件中完成的任何操作，也可以通过 `httpd.conf` 中的 `Directory` 标签来实现。

---

#### 受保护的目录

`.htaccess` 文件的一个常见用途是保护目录的内容。有两种可能的场景：

* 拒绝所有访问
* 将访问限制为授权用户

虽然最初听起来很奇怪，但在 Web 目录中放置的文件和文件夹应该不可用的情况有很多。例如，你可以创建一个包含敏感 PHP 脚本的 `includes` 目录，或一个用于存储上传文件的 `uploads` 目录。在这两种情况下，目录的内容都不打算供直接访问，而是由其他目录中的 PHP 脚本根据需要引用该内容。要拒绝对某个目录的所有访问，请将 **[脚本 A.3](#app01.html#app01ex03)** 中的代码放在该文件夹中的 `.htaccess` 文件中（注释指示每行的作用）。

同样，这段代码只是防止通过 Web 浏览器直接访问该目录的内容。PHP 脚本仍可使用 `include()`、`require()`、`readfile()` 和其他函数访问该内容。事实上，[第 11 章](#ch11.html#ch11) 中的 `show_image.php` 脚本正是如此：它充当*代理脚本*，显示存储在 Web 文档根目录之外的图像（即在 Web 浏览器中原本不可用）。
