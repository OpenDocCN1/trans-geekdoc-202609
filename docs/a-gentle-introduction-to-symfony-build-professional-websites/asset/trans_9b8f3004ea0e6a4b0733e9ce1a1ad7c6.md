

```
Example internal URI, which never appears to the end user
article/permalink?year=2010&subject=finance&title=activity-breakdown
```

```
Example external URL, which appears to the end user
http://www.example.com/articles/finance/2010/activity-breakdown.html
```

路由系统使用一个特殊的配置文件，称为 routing.yml，你可以在其中定义路由规则。考虑 Listing 9-2 中所示的规则。它定义了一个类似 articles/*/*/* 的模式，并为匹配通配符的内容片段命名。

### Listing 9-2 - 示例路由规则

```
article_by_title:
 url:   articles/:subject/:year/:title.html
 param: { module: article, action: permalink }
```

发送到 symfony 应用程序的每个请求首先由路由系统分析（这很简单，因为每个请求都由单个前端控制器处理）。路由规则会在请求 URL 与路由规则中定义的模式之间查找匹配项。如果找到匹配项，则命名的通配符将成为请求参数，并与 param: 键中定义的参数合并。请参见 Listing 9-3 中的工作原理。

### Listing 9-3 - 路由系统解析传入的请求 URL

```
// The user types (or clicks on) this external URL
http://www.example.com/articles/finance/2010/activity-breakdown.html

// The front controller sees that it matches the article_by_title rule
// The routing system creates the following request parameters
'module' => 'article'
'action' => 'permalink'
'subject' => 'finance'
'year' => '2010'
'title' => 'activity-breakdown'
```

然后将请求传递给 article 模块的 permalink 操作，该操作在请求参数中拥有确定显示哪篇文章所需的所有信息。

但是该机制也必须双向工作。为了让应用程序在其链接中显示外部 URL，你必须为路由系统提供足够的数据来确定应应用哪个规则。你还不能直接使用 <a> 标签编写超链接——这将完全绕过路由——而应使用特殊的辅助函数，如 Listing 9-4 所示。

### Listing 9-4 - 路由系统在模板中格式化传出 URL

```
// The url_for() helper transforms an internal URI into an external URL
<a href="<?php echo url_for('article/permalink?subject=finance&year=2010&title=activity-breakdown') ?>">click here</a>
```

```
// The helper sees that the URI matches the article_by_title rule
// The routing system creates an external URL out of it
=> <a href="http://www.example.com/articles/finance/2010/activity-breakdown.html">click here</a>
```

```
// The link_to() helper directly outputs a hyperlink
// and avoids mixing PHP with HTML
<?php echo link_to(
 'click here',
'article/permalink?subject=finance&year=2010&title=activity-breakdown'
) ?>
```

```
// Internally, link_to() will make a call to url_for() so the result is
the same
=> <a href="http://www.example.com/articles/finance/2010/activity-breakdown.html">click here</a>
```

因此，路由是一种双向机制，只有当你使用 link_to() 辅助函数来格式化所有链接时，它才能正常工作。

## URL 重写

在深入了解路由系统之前，需要澄清一个问题。在上一节给出的示例中，内部 URI 未提及前端控制器（index.php 或 frontend_dev.php）。是前端控制器，而不是应用程序的元素，决定了环境。因此，所有链接都必须与环境无关，前端控制器名称永远不会出现在内部 URI 中。

生成的 URL 示例中也没有脚本名称。这是因为生成的 URL 默认在生产环境中不包含任何脚本名称。settings.yml 文件中的 no_script_name 参数精确控制生成的 URL 中前端控制器名称的出现。如 Listing 9-5 所示，将其设置为 false，则链接辅助函数输出的 URL 将在每个链接中提及前端控制器脚本名称。

### Listing 9-5 - 在 apps/frontend/config/settings.yml 中在 URL 中显示前端控制器名称

```
prod:
 .settings
 no_script_name: false
```

现在，生成的 URL 将如下所示：

```
http://www.example.com/index.php/articles/finance/2010/activity-breakdown.html
```

除了生产环境外，在所有环境中，no_script_name 参数默认设置为 false。因此，例如，当你在开发环境中浏览应用程序时，前端控制器名称始终会出现在 URL 中。

```
http://www.example.com/frontend_dev.php/articles/finance/2010/activity-breakdown.html
```

在生产环境中，no_script_name 设置为 true，因此 URL 仅显示路由信息且更加用户友好。不会出现任何技术信息。

```
http://www.example.com/articles/finance/2010/activity-breakdown.html
```

但是应用程序如何知道调用哪个前端控制器脚本？这就是 URL 重写的用武之地。可以配置 Web 服务器，以便在 URL 中没有脚本时调用给定脚本。

在 Apache 中，启用 mod_rewrite 扩展后即可实现此功能。每个 symfony 项目都附带一个 .htaccess 文件，该文件为 web/ 目录的服务器配置添加了 mod_rewrite 设置。该文件的默认内容如 Listing 9-6 所示。

### Listing 9-6 - myproject/web/.htaccess 中 Apache 的默认重写规则

```
<IfModule mod_rewrite.c>
RewriteEngine On

# uncomment the following line, if you are having trouble
# getting no_script_name to work
#RewriteBase /

# we skip all files with .something
#RewriteCond %{REQUEST_URI} \..+$
#RewriteCond %{REQUEST_URI} !\.html$
#RewriteRule .* - [L]

# we check if the .html version is here (caching)
RewriteRule ^$ index.html [QSA]
RewriteRule ^([^.]+)$ $1.html [QSA]
RewriteCond %{REQUEST_FILENAME} !-f

# no, so we redirect to our front web controller
RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>
```

Web 服务器会检查其接收到的 URL 格式。如果 URL 不包含后缀（默认情况下已注释）且没有可用的页面缓存版本（第 12 章介绍缓存），则请求将交给 index.php。

但是，symfony 项目的 web/ 目录在项目的所有应用程序和环境之间共享。这意味着 web 目录中通常不止一个前端控制器。例如，一个同时拥有前端和后端应用程序，以及 dev 和 prod 环境的项目，在 web/ 目录中包含四个前端控制器脚本：

- index.php // 前端，生产环境
- frontend_dev.php // 前端，开发环境
- backend.php // 后端，生产环境
- backend_dev.php // 后端，开发环境

mod_rewrite 设置只能指定一个默认脚本名称。如果你为所有应用程序和环境都将 no_script_name 设置为 true，则所有 URL 都将被解释为针对生产环境中前端应用程序的请求。这就是为什么对于给定项目，只能有一个应用程序和一个环境利用 URL 重写。

> 有一种方法可以拥有多个无脚本名称的应用程序。只需在 Web 根目录中创建子目录，并将前端控制器移入其中。相应地更改 ProjectConfiguration 文件的路径，并为每个应用程序创建所需的 .htaccess URL 重写配置。

## 链接辅助函数

由于路由系统，你应该在模板中使用链接辅助函数，而不是常规的 <a> 标签。不要将其视为麻烦，而应将其视为保持应用程序整洁且易于维护的机会。此外，链接辅助函数提供了一些非常有用的快捷方式，你绝不想错过。

## 超链接、按钮和表单

你已经了解 link_to() 辅助函数。它输出一个符合 XHTML 标准的超链接，并需要两个参数：可单击的元素及其指向的资源的内部 URI。如果你想要的是按钮而不是超链接，请使用 button_to() 辅助函数。表单也有一个辅助函数来管理 action 属性的值。你将在下一章中了解更多关于表单的内容。Listing 9-7 显示了一些链接辅助函数的示例。

### Listing 9-7 - <a>、<input> 和 <form> 标签的链接辅助函数

```
// Hyperlink on a string
<?php echo link_to('my article', 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France">my article</a>
```

```
// Hyperlink on an image
<?php echo link_to(image_tag('read.gif'), 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France"><img src="http://www.symfony-project.org/images/read.gif" /></a>
```

```
// Button tag
<?php echo button_to('my article', 'article/read?title=Finance_in_France') ?>
=> <input value="my article" type="button" onclick="document.location.href='/routed/url/to/Finance_in_France';" />
```

```
// Form tag
<?php echo form_tag('article/read?title=Finance_in_France') ?>
=> <form method="post" action="/routed/url/to/Finance_in_France" />
```

链接辅助函数可以接受内部 URI 以及绝对 URL（以 http:// 开头，并由路由系统跳过）和锚点。请注意，在实际应用程序中，内部 URI 是使用动态参数构建的。Listing 9-8 显示了所有这些情况的示例。

### Listing 9-8 - 链接辅助函数接受的 URL

```
// Internal URI
<?php echo link_to('my article', 'article/read?title=Finance_in_France') ?>
=> <a href="/routed/url/to/Finance_in_France">my article</a>
```

```
// Internal URI with dynamic parameters
<?php echo link_to('my article', 'article/read?title='.$article->getTitle()) ?>
```

```
// Internal URI with anchors
<?php echo link_to('my article', 'article/read?title=Finance_in_France#foo') ?>
=> <a href="/routed/url/to/Finance_in_France#foo">my article</a>
```

```
// Absolute URL
<?php echo link_to('my article', 'http://www.example.com/foobar.html') ?>
=> <a href="http://www.example.com/foobar.html">my article</a>
```

