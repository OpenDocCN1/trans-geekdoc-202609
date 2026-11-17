

应用程序将子域解释为请求参数（例如 http://php.askeet.com 和 http://life.askeet.com）。如果不设置最后两个参数，symfony 将移除当前主机及所有变化头部的缓存。或者，如果要移除另一个主机的缓存，请按如下方式调用 remove()：

```
$cacheManager->remove('user/show?id=*');
// Remove records for the current host and all users
$cacheManager->remove('user/show?id=*', 'life.askeet.com'); // Remove records for the host life.askeet.com and all users
$cacheManager->remove('user/show?id=*', '*'); // Remove records for every host and all users
```

remove() 方法适用于在 factories.yml 中可定义的所有缓存策略（不仅限于 sfFileCache，还包括 sfAPCCache、sfEAcceleratorCache、sfMemcacheCache、sfSQLiteCache 和 sfXCacheCache）。

## 跨应用清除缓存

跨应用清除缓存可能会出现问题。例如，如果管理员在后台应用程序中修改了用户表的一条记录，则前台应用程序中所有依赖于该用户的操作都需要从缓存中清除。但是，后台应用程序中可用的视图缓存管理器不知道前台应用程序的路由规则（应用程序之间相互隔离）。因此，你不能在后台编写以下代码：

```
$cacheManager = sfContext::getInstance()->getViewCacheManager(); // Retrieves the view cache manager of the backend
$cacheManager->remove('user/show?id=12'); // The pattern is not found, since the template is cached in the frontend
```

解决方案是手动初始化一个 sfCache 对象，使用与前台缓存管理器相同的设置。幸运的是，symfony 中的所有缓存类都提供 removePattern 方法，其服务与视图缓存管理器的 remove 相同。

例如，如果后台应用程序需要清除前台应用程序中 ID 为 12 的用户的 user/show 操作的缓存，可以使用以下代码：

```
$frontend_cache_dir =
sfConfig::get('sf_cache_dir').DIRECTORY_SEPARATOR.'frontend'.
DIRECTORY_SEPARATOR.sfConfig::get('sf_environment').DIRECTORY_SEPARATOR.'template';
$cache = new sfFileCache(array('cache_dir' => $frontend_cache_dir)); // Use the same settings as the ones defined in the frontend factories.yml
$cache->removePattern('user/show?id=12');
```

对于不同的缓存策略，只需更改缓存对象的初始化，但缓存移除过程保持不变：

```
$cache = new sfMemcacheCache(array('prefix' => 'frontend'));
$cache->removePattern('user/show?id=12');
```

## 测试和监控缓存

如果处理不当，HTML 缓存可能会导致显示数据不一致。每次禁用某个元素的缓存时，都应彻底测试并监控执行性能提升，以便进行调整。

### 构建暂存环境

缓存系统在生产环境中容易出现无法在开发环境中检测到的新错误，因为 HTML 缓存在开发环境中默认禁用。如果为某些操作启用了 HTML 缓存，则应添加一个名为 staging 的新环境（本节中如此称呼），其设置与 prod 环境相同（因此启用缓存），但将 web_debug 设置为 true。

要设置它，请编辑应用程序的 settings.yml 文件，并在顶部添加清单 12-12 中所示的行。

清单 12-12 - 暂存环境的设置，位于 frontend/config/settings.yml

```
staging:
  .settings:
    web_debug:    true
    cache:          true
```

此外，通过复制生产环境的前端控制器（可能是 myproject/web/index.php）创建一个新的 frontend_staging.php。编辑它以更改传递给 getApplicationConfiguration() 方法的参数，如下所示：

```
$configuration =
ProjectConfiguration::getApplicationConfiguration('frontend', 'staging',
true);
```

就这样——你有了一个新环境。通过在域名后添加前端控制器名称来使用它：

```
http://myapp.example.com/frontend_staging.php/user/list
```

### 监控性能

第 16 章将探讨网页调试工具栏及其内容。但是，由于此工具栏提供了关于缓存元素的宝贵信息，以下是其缓存功能的简要描述。

当你浏览包含可缓存元素（操作、局部片段、片段等）的页面时，网页调试工具栏（位于窗口右上角）会显示一个忽略缓存按钮（一个绿色的圆形箭头），如图 12-4 所示。此按钮会重新加载页面并强制处理缓存元素。请注意，它不会清除缓存。

调试工具栏右侧的最后一个数字是请求执行的持续时间。如果在页面上启用缓存，第二次加载页面时此数字应该会下降，因为 symfony 使用缓存中的数据而不是重新处理脚本。你可以使用此指标轻松监控缓存改进情况。

图 12-4 - 使用缓存的页面的网页调试工具栏

![](img/0f886a7f4cbcc3939be96e985ca35ff4_213_0.png)

调试工具栏还显示请求处理期间执行的数据库查询数量，以及每个类别的持续时间详情（单击总持续时间以显示详情）。将此数据与总持续时间结合起来监控，将有助于你精确衡量缓存带来的性能改进。

### 基准测试

调试模式会大幅降低应用程序的速度，因为大量信息会被记录并提供给网页调试工具栏。因此，在 `staging` 环境中浏览时显示的处理时间并不能代表生产环境中的表现，因为生产环境中已关闭调试模式。

为了更好地查看每个请求的处理时间，你应该使用基准测试工具，例如 Apache Bench 或 JMeter。这些工具允许进行负载测试，并提供两项重要信息：特定页面的平均加载时间和服务器的最大容量。平均加载时间数据对于监控缓存激活带来的性能改进非常有用。

### 识别缓存部分

启用网页调试工具栏后，页面中的缓存元素会用红色框标识，每个元素左上角都有一个缓存信息框，如图 12-5 所示。如果元素已执行，该框背景为蓝色；如果来自缓存，则背景为黄色。单击缓存信息链接会显示缓存元素的标识符、其生存时间以及自上次修改以来经过的时间。这将帮助你在处理脱离上下文的元素时识别问题，查看元素创建时间以及模板中哪些部分实际可以缓存。

图 12-5 - 页面中缓存元素的标识

![](img/0f886a7f4cbcc3939be96e985ca35ff4_214_0.png)

### HTTP 1.1 和客户端缓存

HTTP 1.1 协议定义了一组头部，通过控制浏览器的缓存系统，这些头部可大大有助于进一步加速应用程序。

万维网联盟（W3C，http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html）的 HTTP 1.1 规范详细描述了这些头部。如果操作启用了缓存，并且使用了 `with_layout` 选项，则可以使用以下部分中描述的一种或多种机制。

即使你网站用户的一些浏览器可能不支持 HTTP 1.1，使用 HTTP 1.1 缓存功能也无风险。接收到不理解的头部的浏览器会直接忽略它们，因此建议你设置 HTTP 1.1 缓存机制。

此外，代理和缓存服务器也能理解 HTTP 1.1 头部。即使用户的浏览器不理解 HTTP 1.1，请求路径中可能存在可以利用它的代理。

### 添加 ETag 头部以避免发送未更改的内容

启用 ETag 功能后，Web 服务器会在响应中添加一个特殊头部，包含响应本身的签名。

