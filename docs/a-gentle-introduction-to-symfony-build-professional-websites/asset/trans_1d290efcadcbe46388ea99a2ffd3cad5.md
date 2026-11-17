

_day:
 contextual: true
 enabled: true

位于应用程序 templates/ 目录中的全局组件可以被缓存，前提是你在应用程序的 cache.yml 中声明它们的缓存设置。

## 缓存模板片段

动作缓存仅适用于一部分动作。对于其他动作——即那些在模板中更新数据或显示与会话相关的信息的动作——仍然有缓存改进的空间，只是方式不同。Symfony 提供了第三种缓存类型，专门用于模板片段，并直接在模板中启用。在此模式下，动作始终会被执行，模板被分为已执行的片段和缓存中的片段，如图 12-3 所示。

图 12-3 - 缓存模板片段

![](img/0f886a7f4cbcc3939be96e985ca35ff4_204_0.png)

## 片段缓存

例如，你可能有一个用户列表，显示最后访问用户的链接，而这些信息是动态的。cache() 辅助函数定义了模板中需要缓存的部分。有关语法的详细信息，请参见清单 12-5。

清单 12-5 - 使用 cache() 辅助函数，位于 frontend/modules/user/templates/listSuccess.php

```
<!- - Code executed each time - ->
<?php echo link_to('last accessed user', 'user/
show?id='.$last_accessed_user_id) ?>

<!- - Cached code - ->
<?php if (!cache('users')): ?>
<?php foreach ($users as $user): ?>
<?php echo $user->getName() ?>
<?php endforeach; ?>
<?php cache_save() ?>
<?php endif; ?>
```

其工作原理如下：

- 如果找到了名为 ‘users’ 的片段的缓存版本，则用它来替换 `<?php if (!cache($unique_fragment_name)): ?>` 和 `<?php endif; ?>` 行之间的代码。
- 否则，这些行之间的代码会被处理并保存到缓存中，并使用唯一片段名称进行标识。

不包含在这些行之间的代码始终会被处理，且不会被缓存。

> 该动作（示例中的 list）不得启用缓存，因为这会绕过整个模板执行并忽略片段缓存声明。

使用模板片段缓存带来的速度提升不如动作缓存显著，因为动作始终会被执行，模板仅被部分处理，布局始终用于装饰。

你可以在同一模板中声明更多片段；但是，需要为每个片段提供唯一名称，以便 symfony 缓存系统之后能够找到它们。

与动作和组件一样，缓存的片段可以将秒数作为缓存生命周期，作为对 cache() 辅助函数调用的第二个参数。

清单 12-13 <?php if (!cache('users', 43200)): ?>

如果未向辅助函数提供参数，则使用默认缓存生存期（86400 秒，即一天）。

> 使动作可缓存的另一种方法是，将导致其变化的变量插入动作的路由模式中。例如，如果主页显示已连接用户的名称，则除非 URL 包含用户昵称，否则无法缓存。另一个例子是面向国际化的应用程序：如果要对具有多个翻译的页面启用缓存，语言代码必须以某种方式包含在 URL 模式中。此技巧会增加缓存中的页面数量，但对于加速高度交互的应用程序非常有帮助。

## 动态配置缓存

cache.yml 文件是定义缓存设置的一种方式，但它不变的缺点在于缺乏灵活性。然而，与 symfony 的常规做法一样，你可以使用纯 PHP 而不是 YAML，这样就可以动态配置缓存。

为什么要动态更改缓存设置？一个很好的例子是：某个页面对已认证用户和匿名用户显示的内容不同，但 URL 保持不变。假设有一个文章/show 页面，带有文章评分系统。匿名用户禁用评分功能。对这些用户而言，评分链接会触发登录表单的显示。该页面版本可以被缓存。另一方面，对于已认证用户，点击评分链接会发出 POST 请求并创建新评分。此时，必须为该页面禁用缓存，以便 symfony 动态构建它。

定义动态缓存设置的正确位置是在 sfCacheFilter 之前执行的过滤器中。事实上，缓存是 symfony 中的一个过滤器，就像安全功能一样。为了仅在用户未经过身份验证时才为 article/show 页面启用缓存，请在应用程序 lib/ 目录中创建一个 conditionalCacheFilter，如清单 12-6 所示。

清单 12-6 - 在 PHP 中配置缓存，位于 frontend/lib/conditionalCacheFilter.class.php

```
class conditionalCacheFilter extends sfFilter
{
public function execute($filterChain)
{
$context = $this->getContext();
if (!$context->getUser()->isAuthenticated())
{
foreach ($this->getParameter('pages') as $page)
{
    $context->getViewCacheManager()->addCache($page['module'],
$page['action'], array('lifetime' => 86400));
    }
}
// Execute next filter
$filterChain->execute();
}
}
```

必须在 filters.yml 文件中注册此过滤器，位置在 sfCacheFilter 之前，如清单 12-7 所示。

## 清单 12-7 - 注册自定义过滤器，位于 frontend/config/filters.yml

```
...
security: ~
conditionalCache:
class: conditionalCacheFilter
param:
  pages:
    - { module: article, action: show }
cache: ~
...
```

清除缓存（以自动加载新的过滤器类），条件缓存即可使用。它将仅为未经过身份验证的用户启用 pages 参数中定义的页面缓存。

sfViewCacheManager 对象的 addCache() 方法需要模块名、动作名，以及一个关联数组，其中包含与在 cache.yml 文件中定义的相同参数。例如，如果要定义 article/show 动作必须与布局一起缓存，且生存期为 3600 秒，请编写以下内容：

```
$context->getViewCacheManager()->addCache('article', 'show', array(
    'withLayout' => true,
    'lifetime'   => 3600,
));
```

## 替代缓存存储

默认情况下，symfony 缓存系统将数据存储在 Web 服务器硬盘的文件中。你可能希望将缓存存储在内存中（例如，通过 memcached）或存储在数据库中（特别是如果要在多个服务器之间共享缓存或加速缓存删除）。你可以轻松更改 symfony 的默认缓存存储系统，因为 symfony 视图缓存管理器使用的缓存类是在 factories.yml 中定义的。
默认视图缓存存储工厂是 sfFileCache 类：

```
view_cache:
 class: sfFileCache
 param:
 automaticCleaningFactor: 0
 cacheDir: %SF_TEMPLATE_CACHE_DIR%
```

你可以使用自己的缓存存储类替换该类，也可以使用 symfony 的替代类之一（包括 sfAPCCache、sfEAcceleratorCache、sfMemcacheCache、sfSQLiteCache 和 sfXCacheCache）。在 param 键下定义的参数会作为关联数组传递给缓存类的构造函数。任何视图缓存存储类都必须实现抽象 sfCache 类中的所有方法。有关此主题的更多信息，请参见第 19 章。

使用两个 memcache 服务器的 memcache 后端配置：view_cache: class: sfMemcacheCache param: servers: server_1: host: 192.168.1.10 server_2: host: 192.168.1.11

## 使用超快缓存

即使是缓存页面也涉及一些 PHP 代码执行。对于这种页面，symfony 仍会加载配置、构建响应等。如果你确实确定某个页面在一段时间内不会更改，可以将生成的 HTML 代码直接放入 web/ 文件夹，从而完全绕过 symfony。这归功于 Apache mod_rewrite 设置，前提是你的路由规则指定了不带后缀或以 .html 结尾的模式。

你可以手动逐页执行此操作，只需一个简单的命令行调用：

```
$ curl http://myapp.example.com/user/list.html > web/user/list.html
```

此后，每次请求 user/list 动作时，Apache 都会找到相应的 list.html 页面并完全绕过 symfony。其代价是你无法再通过 symfony 控制页面缓存（生存期、自动删除等），但速度提升非常显著。

或者，你可以使用 sfSuperCache symfony 插件，它可以自动化该过程并支持生存期和缓存清除。有关插件的更多信息，请参见第 17 章。

