

要自定义这些页面，只需在项目或应用程序的 config/ 目录中创建 error/error.html.php 和 unavailable.php。Symfony 将使用这些模板，而非其自身的模板。

如需在必要时将请求重定向到 unavailable.php 页面，请在应用程序的 settings.yml 中将 check_lock 设置为 true。此检查默认处于禁用状态，因为它会为每个请求带来极少量的额外开销。

## 可选功能激活

settings.yml 文件中的某些参数控制可启用或禁用的可选框架功能。禁用未使用的功能可略微提升性能，因此请务必在部署应用程序之前查看表 19-1 中列出的设置。

## 表 19-1 - 通过 settings.yml 设置的可选功能

| 参数 | 描述 | 默认值 |
| :--- | :--- | :--- |
| use_database | 启用数据库管理器。如果不使用数据库，请将其设置为 false。 | true |
| i18n | 启用界面翻译（参见第 13 章）。如果是多语言应用程序，请将其设置为 true。 | false |
| logging_enabled | 启用 symfony 事件日志。如果要完全关闭 symfony 日志记录，请将其设置为 false。 | true |
| escaping_strategy | 启用输出转义功能（参见第 7 章）。如果要转义传递给模板的数据，请将其设置为 true。 | true |
| cache | 启用模板缓存（参见第 12 章）。如果某个模块包含 cache.yml 文件，请将其设置为 true。仅在启用时，缓存过滤器（sfCacheFilter）才会生效。 | 开发环境为 false，生产环境为 true |
| web_debug | 启用 Web 调试工具栏以便轻松调试（参见第 16 章）。若要在每个页面上显示工具栏，请将其设置为 true。 | 开发环境为 true，生产环境为 false |
| check_symfony_version | 为每个请求启用 symfony 版本检查。框架升级后，若要自动清除缓存，请将其设置为 true。如果升级后始终清除缓存，请保持设置为 false。 | false |
| check_lock | 启用应用程序锁定系统，由 cache:clear 和 project:disable 任务触发（参见上一节）。若要将所有发往已禁用应用程序的请求重定向到 sfConfig::get('sf_symfony_lib_dir')/exception/data/unavailable.php 页面，请将其设置为 true。 | false |
| compressed | 启用 PHP 响应压缩。若要通过 PHP 压缩处理程序压缩传出 HTML，请将其设置为 true。 | false |

## 功能配置

Symfony 使用 `settings.yml` 中的某些参数来更改内置功能（如表单验证、缓存和第三方模块）的行为。

### 输出转义设置

输出转义设置控制模板中变量的访问方式（参见第 7 章）。`settings.yml` 文件为此功能包含两个设置：

- `escaping_strategy` 设置的值可以为 `true` 或 `false`。
- `escaping_method` 设置可以设置为 `ESC_RAW`、`ESC_SPECIALCHARS`、`ESC_ENTITIES`、`ESC_JS` 或 `ESC_JS_NO_ENTITIES`。

### 路由设置

路由设置（参见第 9 章）定义在 `factories.yml` 的 `routing` 键下。清单 19-1 显示了默认路由配置。

### 清单 19-1 - 路由配置设置，位于 frontend/config/factories.yml

```
routing:
  class: sfPatternRouting
  param:
    load_configuration: true
    suffix:               .
    default_module:       default
    default_action:       index
    variable_prefixes:    [':']
    segment_separators:   ['/', '.']
    variable_regex:       '[\w\d_+]'
    debug:                %SF_DEBUG%
    logging:              %SF_LOGGING_ENABLED%
    cache:
      class: sfFileCache
      param:
        automatic_cleaning_factor: 0
        cache_dir:                 %SF_CONFIG_CACHE_DIR%/routing
        lifetime:                  31556926
        prefix:                    %SF_APP_DIR%
```

- `suffix` 参数设置生成 URL 的默认后缀。默认值为句点 (`.`)，即表示无后缀。例如，将其设置为 `.html` 可使所有生成的 URL 看起来像静态页面。
- 当路由规则未定义 `module` 或 `action` 参数时，将改用 `factories.yml` 中的值：
  - `default_module`: 默认模块请求参数。默认值为 `default` 模块。
  - `default_action`: 默认动作请求参数。默认值为 `index` 动作。
- 默认情况下，路由模式通过冒号 (`:`) 前缀识别命名通配符。但如果您希望采用更符合 PHP 习惯的语法编写规则，可以在 `variable_prefixes` 数组中添加美元符号 (`$`)。这样一来，您就可以编写类似 `'/article/$year/$month/$day/$title'` 的模式，而非 `'/article/:year/:month/:day/:title'`。
- 模式路由将在分隔符之间识别命名通配符。默认分隔符为斜杠和句点，但您可以根据需要在 `segment_separators` 参数中添加更多。例如，如果您添加连字符 (-)，可以编写类似 '/article/:year-:month-:day/:title' 的模式。

- 模式路由在生产模式下使用其自身缓存，以加快外部 URL 与内部 URL 之间的转换。默认情况下，此缓存使用文件系统，但您可以使用任何缓存类，前提是在 cache 参数中声明该类及其设置。有关可用缓存存储类的列表，请参见第 15 章。要在生产环境中禁用路由缓存，请将 debug 参数设置为 true。

这些仅是 sfPatternRouting 类的设置。您可以为应用程序路由使用另一个类，可以是您自己的类，也可以是 symfony 的路由工厂之一（sfNoRouting 和 sfPathInfoRouting）。使用这两个工厂中的任何一个，所有外部 URL 都类似于 'module/action?key1=param1'。无法进行自定义——但速度很快。区别在于，第一个使用 PHP 的 GET，第二个使用 PATH_INFO。它们主要用于后端界面。

还有一个与路由相关的附加参数，但该参数存储在 settings.yml 中：

- `no_script_name` 参数用于在生成的 URL 中启用前端控制器名称。`no_script_name` 设置在一个项目中只能为单个应用程序启用，除非您将前端控制器存储在不同目录中并更改默认 URL 重写规则。它通常在主应用程序的生产环境中启用，而在其他环境中禁用。

### 表单验证设置

> > 本节中描述的功能自 symfony 1.1 起已弃用，且仅在启用 sfCompat10 插件时才可用。

表单验证设置控制验证辅助函数输出的错误消息的外观（参见第 10 章）。这些错误包含在 <div> 标签中，并使用 validation_error_class 设置作为 class 属性，并使用 validation_error_id_prefix 设置来构建 id 属性。默认值为 form_error 和 error_for_，因此对名为 foobar 的输入调用 form_error() 辅助函数输出的属性将为 class="form_error" id="error_for_foobar"。

两个设置决定每条错误消息前后的字符：validation_error_prefix 和 validation_error_suffix。您可以更改它们以一次性自定义所有错误消息。

### 缓存设置

缓存设置大多在 cache.yml 中定义，除了 settings.yml 中的两个：cache 启用模板缓存机制，etag 启用服务器端的 ETag 处理（参见第 15 章）。您还可以在 factories.yml 中指定所有缓存系统（视图缓存、路由缓存和 i18n 缓存）使用的存储。清单 19-2 显示了默认视图缓存工厂配置。

### 清单 19-2 - 视图缓存配置设置，位于 frontend/config/factories.yml

```
view_cache:
  class: sfFileCache
  param:
    automatic_cleaning_factor: 0
    cache_dir: %SF_TEMPLATE_CACHE_DIR%
    lifetime: 86400
    prefix: %SF_APP_DIR%/template
```

该类可以是 *sfFileCache*、*sfAPCCache*、*sfEAcceleratorCache*、*sfXCacheCache*、*sfMemcacheCache* 和 *sfSQLiteCache* 中的任何一个。也可以是您自己的自定义类，前提是它扩展 *sfCache* 并提供用于设置、检索和删除缓存中键的相同通用方法。工厂参数取决于您选择的类，但存在常量：

- lifetime 定义缓存部分被移除前的秒数
- prefix 是添加到每个缓存键的前缀（在前缀中使用环境，以便根据环境使用不同的缓存）。如果希望两个应用程序共享缓存，请为它们使用相同的前缀。

然后，对于每个特定的工厂，您都必须定义缓存存储的位置。

- 对于 *sfFileCache*，*cache_dir* 参数指定缓存目录的绝对路径
- *sfAPCCache*、*sfEAcceleratorCache* 和 *sfXCacheCache* 不接受任何位置参数，因为它们使用 PHP 原生函数与 APC、EAccelerator 或 XCache 缓存系统进行通信
- 对于 *sfMemcacheCache*，请在 host 参数中输入 Memcached 服务器的主机名，或在 *servers* 参数中输入主机数组
- 对于 *sfSQLiteCache*，应在 *database* 参数中输入 SQLite 数据库文件的绝对路径

有关其他参数，请查看每个缓存类的 API 文档。

视图并非唯一能够使用缓存的组件。路由和 I18N 工厂都提供 *cache* 参数，您可以在其中设置任何缓存工厂，就像视图缓存一样。例如，清单 19-1 显示路由默认使用文件缓存来实现加速策略，但您可以将其更改为任何想要的缓存。

### 日志设置

两个日志设置（参见第 16 章）存储在 *settings.yml* 中：

- *error_reporting* 指定在 PHP 日志中记录哪些事件。默认情况下，对于生产环境，它被设置为 *E_PARSE | E_COMPILE_ERROR | E_ERROR | E_CORE_ERROR | E_USER_ERROR*（因此记录的事件为 *E_PARSE*、*E_COMPILE_ERROR*、*E_ERROR*、*E_CORE_ERROR* 和 *E_USER_ERROR*），对于开发环境，它被设置为 *E_ALL | E_STRICT*。
- *web_debug* 设置激活 Web 调试工具栏。仅在开发和测试环境中将其设置为 *true*。

### 资源路径

*settings.yml* 文件还存储资源路径。如果您想使用与 symfony 捆绑的不同版本的资源，可以更改这些路径设置：

- 管理生成器所需的文件存储在 *admin_web_dir* 中
- Web 调试工具栏所需的文件存储在 *web_debug_web_dir* 中

### 默认辅助函数

为每个模板加载的默认辅助函数在 *standard_helpers* 设置中声明（参见第 7 章）。默认情况下，这些是 Partial 和 Cache 辅助函数组。如果您在应用程序的所有模板中使用某个辅助函数组，则将其名称添加到 *standard_helpers* 设置中，可免去在每个模板中使用 *use_helper()* 声明的麻烦。

