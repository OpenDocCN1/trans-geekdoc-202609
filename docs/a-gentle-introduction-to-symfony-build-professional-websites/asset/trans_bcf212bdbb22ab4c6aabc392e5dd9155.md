

config/
...
www/    # Public area
images/
css/
js/
index.php

在这种情况下，根目录是 symfony/ 目录。因此，index.php 前端控制器只需按如下方式包含 config/ProjectConfiguration.class.php 文件，应用即可工作：

```
Listing 19-9
require_once(dirname(__FILE__).'/../symfony/config/ProjectConfiguration.class.php');
```

此外，使用 setWebDir() 方法将公共区域从通常的 web/ 更改为 www/，如下所示：

```
Listing 19-10
class ProjectConfiguration extends sfProjectConfiguration
{
    public function setup()
    {
        // ...

        $this->setWebDir($this->getRootDir().'/../www');
    }
}
```

## 理解配置处理器

每个配置文件都有一个处理器。配置处理器的工作是管理配置级联，并执行配置文件与可在运行时执行的优化 PHP 代码之间的转换。

## 默认配置处理器

默认处理器配置存储在 sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml 中。该文件根据文件路径将处理器与配置文件关联。清单 19-6 显示了该文件的摘录。

Listing 19-6 - Extract of sfConfig::get('sf_symfony_lib_dir')/config/config/config_handlers.yml

```
Listing 19-11
config/settings.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: sf_

config/app.yml:
class:   sfDefineEnvironmentConfigHandler
param:
  prefix: app_

config/filters.yml:
class:   sfFilterConfigHandler
modules/*/config/module.yml:
 class: sfDefineEnvironmentConfigHandler
 param:
   prefix: mod_
   module: yes
```

对于每个配置文件（`config_handlers.yml` 通过带通配符的文件路径标识每个文件），处理器类在 `class` 键下指定。

由 `sfDefineEnvironmentConfigHandler` 处理的配置文件的设置可以通过 `sfConfig` 类直接在代码中使用，而 `param` 键包含一个前缀值。

您可以添加或修改用于处理每个配置文件的处理器——例如，使用 INI 或 XML 文件而不是 YAML 文件。

> `config_handlers.yml` 文件的配置处理器是 `sfRootConfigHandler`，显然，它不能更改。

如果您需要修改配置的解析方式，请在应用程序的 `config/` 文件夹中创建一个空的 `config_handlers.yml` 文件，并使用您编写的类覆盖 `class` 行。

## 添加您自己的处理器

使用处理器来处理配置文件有两个重要好处：

- 配置文件被转换为可执行的 PHP 代码，并将此代码存储在缓存中。这意味着在生产环境中仅解析一次配置，性能最佳。

- 配置文件可以在不同级别（项目和应用程序）定义，最终参数值将由级联产生。因此，您可以在项目级别定义参数，并针对每个应用程序进行覆盖。

如果您想编写自己的配置处理器，请遵循框架在 `sfConfig::get('sf_symfony_lib_dir')/config/` 目录中使用的结构示例。

假设您的应用程序包含一个 `myMapAPI` 类，它提供与第三方地图 Web 服务的接口。该类需要使用 URL 和用户名进行初始化，如清单 19-7 所示。

## 清单 19-7 - `myMapAPI` 类初始化示例

```
$mapApi = new myMapAPI();
$mapApi->setUrl($url);
$mapApi->setUser($user);
```

您可能希望将这两个参数存储在名为 `map.yml` 的自定义配置文件中，该文件位于应用程序的 `config/` 目录中。此配置文件可能包含以下内容：

```
api:
  url: map.api.example.com
  user: foobar
```

要将这些设置转换为与清单 19-7 等效的代码，您必须构建一个配置处理器。每个配置处理器都必须扩展 `sfConfigHandler` 并提供一个 `execute()` 方法，该方法期望将配置文件路径数组作为参数，并且必须返回要写入缓存文件的数据。YAML 文件的处理器应扩展 sfYamlConfigHandler 类，该类提供用于 YAML 解析的额外便利功能。对于 map.yml 文件，典型的配置处理器可以如清单 19-8 所示编写。

## 清单 19-8 - 自定义配置处理器，位于 frontend/lib/myMapConfigHandler.class.php

```
<?php

class myMapConfigHandler extends sfYamlConfigHandler
{
    public function execute($configFiles)
    {
        // Parse the yaml
        $config = $this->parseYamls($configFiles);

        $data = "<?php\n";
        $data .= "\$mapApi = new myMapAPI();\n";

        if (isset($config['api']['url']))
        {
            $data .= sprintf("\$mapApi->setUrl('%s');\n", $config['api']['url']);
        }

        if (isset($config['api']['user']))
        {
            $data .= sprintf("\$mapApi->setUser('%s');\n", $config['api']['user']);
        }

        return $data;
    }
}
```

symfony 传递给 execute() 方法的 $configFiles 数组将包含在 config/ 文件夹中找到的所有 map.yml 文件的路径。parseYamls() 方法将处理配置级联。

要将此新处理器与 map.yml 文件关联，必须创建一个包含以下内容的 config_handlers.yml 配置文件：

```
Listing 19-15
config/map.yml:
class: myMapConfigHandler
```

> 该类必须是自动加载的（这里就是这样），或者定义在 param 键下的 file 参数中指定路径的文件中。

与许多其他 symfony 配置文件一样，您也可以直接在 PHP 代码中注册配置处理器：

```
Listing 19-16
sfContext::getInstance()->getConfigCache()->registerConfigHandler('config/map.yml', 'myMapConfigHandler', array());
```

当您需要在应用程序中使用基于 map.yml 文件并由 myMapConfigHandler 处理器生成的代码时，请调用以下行：

```
include sfContext::getInstance()->getConfigCache()->checkConfig('config/map.yml');
```

调用 checkConfig() 方法时，symfony 会在配置目录中查找现有的 map.yml 文件，并使用 config_handlers.yml 文件中指定的处理器对它们进行处理，前提是缓存中不存在 map.yml.php 或 map.yml 文件比缓存更新。

如果要在 YAML 配置文件中处理环境，处理器可以扩展 sfDefineEnvironmentConfigHandler 类，而不是 sfYamlConfigHandler。您不应调用 parseYaml() 方法来检索配置，而应调用 getConfiguration() 方法：$config = $this->getConfiguration($configFiles)。

## 使用现有配置处理器

如果您只需要允许用户通过 sfConfig 从代码中检索值，可以使用 sfDefineEnvironmentConfigHandler 配置处理器类。例如，要使 url 和 user 参数分别可用为 sfConfig::get('map_url') 和 sfConfig::get('map_user')，请按如下方式定义处理器：

```
config/map.yml:
class: sfDefineEnvironmentConfigHandler
param:
  prefix: map_
```

注意不要选择已被其他处理器使用的前缀。现有前缀为 sf_、app_ 和 mod_。

## 摘要

配置文件可以大幅修改框架的工作方式。由于 symfony 甚至为其核心功能和文件加载依赖配置，因此它可以适应比标准专用主机多得多的环境。这种极强的可配置性是 symfony 的主要优势之一。尽管它有时会吓到新来者（他们在配置文件中看到许多需要学习的约定），但它允许 symfony 应用程序与非常大量的平台和环境兼容。一旦您掌握了 symfony 的配置，就没有服务器会拒绝运行您的应用程序！

