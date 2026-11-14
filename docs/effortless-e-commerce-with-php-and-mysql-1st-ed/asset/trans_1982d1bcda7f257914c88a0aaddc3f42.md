

![](img/4f47e47c67bd619ac73250f11c9fc7ce_189_0.png)

Figure 7-5

作为一种安全技术，防止人们浏览此目录的内容，在 products 文件夹中放置一个空白的 index.html 文件。这样，Web 服务器就不会向好奇的访问者提供文件夹的文件列表。

The views directory will store files that represent individual snippets of HTML. These will be used to display elements such as:

views 目录将存储表示单个 HTML 片段的文件。这些文件将用于显示诸如以下的元素：

- The contents of the home page
- The shopping cart
- The wish list
- A listing of categories
- A listing of products

- 主页的内容
- 购物车
- 心愿单
- 类别列表
- 产品列表

The views directory is part of the MVC breakdown that the site uses. Next, you’ll see how to protect this and the other sensitive directories from prying eyes.

views 目录是网站使用的 MVC 架构的一部分。接下来，你将看到如何保护此目录和其他敏感目录，防止被窥探。

## Customizing the Server Behavior

## 自定义服务器行为

For this site, you need to customize how your server runs in four ways. Your ability to perform any of these alterations will depend upon your hosting situation, although most hosts will allow at least two of the four alterations. The specific steps involved will depend upon your hosting situation and the Web server application (such as, Apache, IIS, and so on) involved. Here, I’ll provide instructions for Apache, the most common Web server.

对于本网站，你需要以四种方式自定义服务器的运行方式。你能否执行这些更改中的任何一项将取决于你的托管情况，尽管大多数主机会允许至少两项更改。具体涉及的步骤将取决于你的托管情况以及所涉及的 Web 服务器应用程序（例如 Apache、IIS 等）。在这里，我将为最常见的 Web 服务器 Apache 提供说明。

> **note**
> Make sure you know what Web server application is being used on your server!

> **注意**
> 确保你知道你的服务器上正在使用哪种 Web 服务器应用程序！

## APPLYING PASSWORD PROTECTION

## 应用密码保护

The administration directory needs to be password protected so that only authenticated users can access its contents. If you want to get your hands dirty, you can accomplish this by connecting to your server via a command-line interface and executing the proper commands (search online for what those would be). Or, most likely, your Web host provides a way to password protect a directory through the site’s control panel (Figure 7.6).

管理目录需要受到密码保护，以便只有经过身份验证的用户才能访问其内容。如果你想亲自动手，可以通过命令行界面连接到服务器并执行相应命令来完成此操作（在线搜索这些命令是什么）。或者，更有可能的是，你的 Web 主机提供了一种通过网站控制面板对目录进行密码保护的方法（图 7.6）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_189_1.png)

Figure 7.6

图 7.6

> **tip**
> As always, use obscure and secure usernames, passwords, and directory names for administrative folders.

> **提示**
> 与往常一样，为管理文件夹使用难以辨认且安全的用户名、密码和目录名。

The control panel should take you to a form where you can indicate what directory to protect, as well as what message should be provided to someone attempting to access that directory (Figure 7.7). This message will appear in the Web browser's login prompt (Figure 7.8). Depending upon your control panel, you might use another form to establish the username and password required to access the protected directory (Figure 7.9).

控制面板应会带你进入一个表单，你可以在其中指明要保护哪个目录，以及尝试访问该目录的人应看到什么消息（图 7.7）。此消息将出现在 Web 浏览器的登录提示中（图 7.8）。根据你的控制面板，你可能会使用另一个表单来设置访问受保护目录所需的用户名和密码（图 7.9）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_190_0.png)

![](img/4f47e47c67bd619ac73250f11c9fc7ce_190_1.png)

![](img/4f47e47c67bd619ac73250f11c9fc7ce_190_2.png)

## PROTECTING OTHER DIRECTORIES

## 保护其他目录

Beyond password protection, there are other ways you can keep a folder safe from unwanted visitors. The process of password protecting a directory creates (or modifies) an .htaccess file, which alters how the Apache Web server treats that directory and its contents (other Web servers use other approaches). This file, literally named .htaccess and placed in the directory you want to affect, has a specific syntax for achieving different effects.

除了密码保护之外，还有其他方法可以防止不想要的访问者访问文件夹。对目录进行密码保护的过程会创建（或修改）一个 .htaccess 文件，该文件会更改 Apache Web 服务器处理该目录及其内容的方式（其他 Web 服务器采用其他方法）。这个名为 .htaccess 并放置在你想要影响的目录中的文件，具有实现不同效果的特定语法。

For example, you can use the .htaccess file to make a directory entirely unavailable through the Web browser. The syntax for that is:

例如，你可以使用 .htaccess 文件使目录通过 Web 浏览器完全不可用。语法如下：

```
# Disable indexing:
Options All -Indexes
# Ignores every file:
IndexIgnore *
# Prevent access to any file:
<FilesMatch "^.*$">
Order Allow,Deny
Deny from all
</FilesMatch>
```

As the comments indicate (comments in an .htaccess are preceded by a #), the first command allows every option except for indexing, which is to say the Web browser should not create an index of the directory. The second command says that every file should be ignored by any indexing (this is an extra precaution).

如注释所示（.htaccess 中的注释以 # 开头），第一条命令允许除了索引以外的所有选项，也就是说 Web 浏览器不应创建目录的索引。第二条命令表示任何索引都应忽略每个文件（这是一种额外的预防措施）。

The final block applies a set of rules to a group of files, that group being every file in the directory (^.*$). The Order Allow,Deny command indicates that all allow rules should be checked first, then all deny rules. Then, the Deny from all command says that no one should be allowed access.

最后一个块将一组规则应用于一组文件，即目录中的每个文件（^.*$）。Order Allow,Deny 命令表示应先检查所有允许规则，然后再检查所有拒绝规则。接着，Deny from all 命令表示不允许任何人访问。

If you create a file with a name of .htaccess that contains that code and place it in both your includes and views directories, no one will be able to see the contents of those directories, or a specific file therein, through a Web browser (Figure 7.10).

如果你创建一个名为 .htaccess 的文件，包含该代码，并将其放置在 includes 和 views 目录中，那么没有人能够通过 Web 浏览器查看这些目录的内容，或其中的特定文件（图 7.10）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_191_0.png)

Figure 7.10

图 7.10

Most likely, your Web host will not have a control panel tool for editing .htaccess files, but you might be able to create one in any text editor, and then FTP it to the Web server. Or, you could create one on the server via a command-line interface and a command-line text editor like vi or Emacs. Using .htaccess files will only work if the Web server is configured to allow changes on a directory basis. This setting is dictated by the server’s primary configuration file, which is likely outside your influence, unless you’ve got your own server.

很可能，你的 Web 主机没有用于编辑 .htaccess 文件的控制面板工具，但你可能可以在任何文本编辑器中创建一个，然后通过 FTP 将其上传到 Web 服务器。或者，你可以在服务器上通过命令行界面和类似 vi 或 Emacs 的命令行文本编辑器来创建一个。只有在 Web 服务器配置为允许按目录进行更改时，使用 .htaccess 文件才会生效。此设置由服务器的主配置文件决定，该文件可能超出你的影响范围，除非你拥有自己的服务器。

> **tip**
> This section packs a lot of information about .htaccess files and Apache configuration into a small area. Look online to expand your knowledge of these important subjects.

> **提示**
> 本节在较小的篇幅中包含了大量关于 .htaccess 文件和 Apache 配置的信息。请在线搜索以扩展对这些重要主题的了解。

## USING MOD_REWRITE

## 使用 mod_rewrite

The next server alteration, which also requires .htaccess files, is to use Apache’s mod_rewrite feature.

下一项服务器更改也需要 .htaccess 文件，即使用 Apache 的 mod_rewrite 功能。

> **tip**
> If you can’t use mod_rewrite on your server, just skip this section and change every URL in the HTML files accordingly.

> **提示**
> 如果你的服务器无法使用 mod_rewrite，请跳过本节，并相应地更改 HTML 文件中的每个 URL。

As mentioned in Chapter 5, “Managing Site Content,” one way to improve the search-engine rankings of your site is to use descriptive URLs. To accomplish this—to create so-called “pretty” URLs—requires using mod_rewrite, which is Apache’s rewrite module. This tool can transform URLs from one format to another, behind-the-scenes, so that the browser (that is, the user) is unaware of the change.

如第 5 章“管理网站内容”中所述，提高网站搜索引擎排名的一种方法是使用描述性 URL。要做到这一点——即创建所谓的“优雅”URL——需要使用 mod_rewrite，这是 Apache 的重写模块。此工具可以在幕后将 URL 从一种格式转换为另一种格式，因此浏览器（即用户）不会察觉到更改。

For the Coffee site, two public URLs need to be rewritten: shop.php and browse.php. The shop page will list the general coffee and non-coffee product categories. To know which to display, the page needs to receive a type value in the URL. Instead of having URLs like shop.php?type=coffee, let’s use shop/coffee/. To accomplish this, you would create a .htaccess file in the Web root directory that starts off with:

对于 Coffee 网站，需要重写两个公共 URL：shop.php 和 browse.php。商店页面将列出常规咖啡和非咖啡产品类别。为了知道显示哪一项，页面需要在 URL 中接收 type 值。不要使用 shop.php?type=coffee 这样的 URL，让我们使用 shop/coffee/。要做到这一点，你需要在 Web 根目录中创建一个 .htaccess 文件，并以以下内容开头：

```
<IfModule mod_rewrite.c>
RewriteEngine on
</IfModule>
```

These lines say: If the mod_rewrite module exists, turn on the rewrite engine. After turning on the rewrite engine and before the closing IfModule, you define rules. Here is the complete set of rules that will be defined, to be explained later in detail:

这些行表示：如果 mod_rewrite 模块存在，则打开重写引擎。在打开重写引擎之后、在关闭 IfModule 之前，你需要定义规则。以下是将要定义的完整规则集，稍后将详细解释：

```
<IfModule mod_rewrite.c>
RewriteEngine on
# For sales:
RewriteRule ^shop/sales/?$ sales.php
# For the primary categories:
RewriteRule ^shop/([A-Za-z-+]+)/+$ shop.php?type=$1
# For specific products:
RewriteRule ^browse/([A-Za-z-+]+)/([A-Za-z-+]+)/([0-9]+)$ browse.php?type=$1&category=$2&id=$3
# For HTTPS pages:
RewriteCond %{HTTPS} off
RewriteRule ^(checkout\.php|billing\.php|final\.php|admin\/(.*))$
https://%{HTTP_HOST}/$1 [R=301,L]
</IfModule>
```

For the shop.php script, the rule is:

对于 shop.php 脚本，规则是：

```
RewriteRule ^shop/([A-Za-z-+]+)/+$ shop.php?type=$1
```

Regular expressions are in use here, so if you're unfamiliar with them, this may seem like hieroglyphics to you. I'll explain it in pieces...

这里使用了正则表达式，所以如果你不熟悉它们，这对你来说可能像天书一样难懂。我将分段解释...

The middle chunk (between RewriteRule and shop.php?type=$1) identifies the URLs to match. That regular expression matches any URL that has text beginning (the caret ^) with shop followed by a slash. That should be followed by some combination of letters and the plus sign: [A-Za-z-+]+. The square brackets create a class of characters. The specific class matches upper and lowercase letters and the plus sign, which is how spaces are represented in URLs (such as, Kona Coffee in a URL is Kona+Coffee). This class is followed by the plus sign, which is a quantity modifier that matches one or more of whatever the plus sign follows. So shop/Mugs matches ^shop/([A-Za-z-+]+) but just shop does not and neither does shop/123.

中间部分（在 RewriteRule 和 shop.php?type=$1 之间）标识要匹配的 URL。该正则表达式匹配任何以 shop 开头（脱字符 ^）并后跟斜杠的文本的 URL。之后应跟一些字母和加号的组合：[A-Za-z-+]+。方括号创建一类字符。该特定类匹配大写和小写字母以及加号，这是 URL 中空格的表示方式（例如，URL 中的 Kona Coffee 表示为 Kona+Coffee）。该类后跟加号，加号是一个数量修饰符，用于匹配加号后面内容的一个或多个。因此 shop/Mugs 匹配 ^shop/([A-Za-z-+]+)，但 shop 本身不匹配，shop/123 也不匹配。

The class and plus sign quantity modifier is wrapped in parentheses to make a grouping, which will be relevant at the end of the rule. This is followed by an optional slash. This slash is optional because it's followed by the question mark, another quantifier modifier. The question mark says that zero or one of the things it follows is acceptable. At this point, ^shop/([A-Za-z-+]+)/+? matches shop/Mugs or shop/Mugs/.

该类和加号数量修饰符被包裹在括号中以形成一个分组，这在规则的末尾会很重要。之后跟一个可选斜杠。此斜杠是可选的，因为它后面跟着问号，另一个数量修饰符。问号表示其后内容出现零次或一次均可。此时，^shop/([A-Za-z-+]+)/+? 匹配 shop/Mugs 或 shop/Mugs/。

> The rewrite rules apply to the part of the URL after the hostname. In www.example.com/shop/coffee, the matching begins after www.example.com/.

> 重写规则应用于主机名之后的 URL 部分。在 www.example.com/shop/coffee 中，匹配从 www.example.com/ 之后开始。

