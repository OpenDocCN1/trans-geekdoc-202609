

## PEAR 插件

symfony 插件部分列出的插件可以打包为 PEAR 包，并通过官方 symfony 插件 PEAR 频道提供：plugins.symfony-project.org。要安装此类插件，请使用带有插件名称的 plugin:install 任务，如清单 17-9 所示。

### 清单 17-9 - 从官方 symfony 插件 PEAR 频道安装插件

```
$ cd myproject
$ php symfony plugin:install pluginName
```

或者，您可以下载插件并从磁盘安装。在这种情况下，使用包存档的路径，如清单 17-10 所示。

### 清单 17-10 - 从下载的 PEAR 包安装插件

```
$ cd myproject
$ php symfony plugin:install /home/path/to/downloads/pluginName.tgz
```

有些插件托管在外部 PEAR 频道上。使用 plugin:install 任务安装它们，不要忘记注册频道并提及频道名称，如清单 17-11 所示。

### 清单 17-11 - 从 PEAR 频道安装插件

```
$ cd myproject
$ php symfony plugin:add-channel channel.symfony.pear.example.com
$ php symfony plugin:install --channel=channel.symfony.pear.example.com
pluginName
```

这三种安装类型都使用 PEAR 包，因此术语“PEAR 插件”将不加区分地用于指代从 symfony 插件 PEAR 频道、外部 PEAR 频道或下载的 PEAR 包安装的插件。

plugin:install 任务还接受一些选项，如清单 17-12 所示。

### 清单 17-12 - 带选项安装插件

```
$ php symfony plugin:install --stability=beta pluginName
$ php symfony plugin:install --release=1.0.3 pluginName
$ php symfony plugin:install --install-deps pluginName
```

> 与所有 symfony 任务一样，您可以通过运行 php symfony help plugin:install 来获取 plugin:install 选项和参数的完整说明。

## 存档插件

有些插件以简单的文件存档形式提供。要安装这些插件，只需将存档解压到项目的 plugins/ 目录中即可。如果插件包含 web/ 子目录，不要忘记运行 plugin:publish-assets 命令，在主 web/ 文件夹下创建相应的符号链接，如清单 17-13 所示。最后，不要忘记清除缓存。

### 清单 17-13 - 从存档安装插件

```
$ cd plugins
$ tar -zxpf myPlugin.tgz
$ cd ..
$ php symfony plugin:publish-assets
$ php symfony cc
```

## 从版本控制仓库安装插件

插件有时有自己的源代码仓库用于版本控制。您可以在 plugins/ 目录中进行简单的检出来安装它们，但如果您的项目本身也在版本控制下，这可能会出现问题。

或者，您可以将插件声明为外部依赖项，以便每次更新项目源代码时也会更新插件源代码。例如，Subversion 将外部依赖项存储在 svn:externals 属性中。因此，您可以编辑此属性并在随后更新源代码来添加插件，如清单 17-14 所示。

### 清单 17-14 - 从源代码版本仓库安装插件

```
$ cd myproject
$ svn propedit svn:externals plugins
pluginName  http://svn.example.com/pluginName/trunk
$ svn up
$ php symfony plugin:publish-assets
$ php symfony cc
```

> 如果插件包含 web/ 目录，则必须运行 symfony plugin:publish-assets 命令，以在项目主 web/ 文件夹下生成相应的符号链接。

## 激活插件模块

有些插件包含整个模块。插件模块与经典模块的唯一区别在于，插件模块不会出现在 myproject/apps/frontend/modules/ 目录中（以便于升级）。它们还需要在 settings.yml 文件中激活，如清单 17-15 所示。

### 清单 17-15 - 激活插件模块，在 frontend/config/settings.yml 中

```
all:
  .settings:
    enabled_modules: [default, sfMyPluginModule]
```

这是为了避免插件模块被错误地提供给不需要它的应用程序，从而可能导致安全漏洞。考虑一个提供前端和后端模块的插件。您只需要在前端应用程序中启用前端模块，仅在后端应用程序中启用后端模块。这就是插件模块默认不被激活的原因。

> 默认模块是默认启用的唯一模块。它其实不是插件模块，因为它位于框架中，在 sfConfig::get('sf_symfony_lib_dir')/controller/default/。这是提供祝贺页面以及 404 和凭据所需错误的默认错误页面的模块。如果您不想使用 symfony 默认页面，只需从 enabled_modules 设置中删除此模块即可。

## 列出已安装的插件

只需查看项目的 plugins/ 目录就能知道安装了哪些插件，而 plugin:list 任务会告诉您更多：每个已安装插件的版本号和频道名称（参见清单 17-16）。

### 清单 17-16 - 列出已安装的插件

```
$ cd myproject
$ php symfony plugin:list

Installed plugins:
sfPrototypePlugin 1.0.0-stable # plugins.symfony-project.com
(symfony)
sfSuperCachePlugin 1.0.0-stable # plugins.symfony-project.com
(symfony)
sfThumbnail 1.1.0-stable # plugins.symfony-project.com
(symfony)
```

## 升级和卸载插件

要卸载 PEAR 插件，请从项目根目录调用 plugin:uninstall 任务，如清单 17-17 所示。如果插件的安装频道不同于默认 symfony 频道，则必须在插件名称前加上其安装频道（使用 plugin:list 任务来确定此频道）。

### 清单 17-17 - 卸载插件

```
$ cd myproject
$ php symfony plugin:uninstall sfSuperCachePlugin
$ php symfony cc
```

要卸载存档插件或 SVN 插件，请手动从项目 plugins/ 和 web/ 目录中删除插件文件，并清除缓存。

要升级插件，可以使用 plugin:upgrade 任务（适用于 PEAR 插件）或执行 svn update（如果您从版本控制仓库获取了插件）。存档插件不容易升级。

## 插件结构

插件使用 PHP 语言编写。如果您能理解应用程序的组织方式，就能理解插件的结构。

## 插件文件结构

插件目录大致与项目目录的组织方式相似。插件文件必须放在正确的目录中，以便在需要时能被 symfony 自动加载。请查看清单 17-18 中的插件文件结构说明。

### 清单 17-18 - 插件的文件结构

```
pluginName/
config/
routing.yml // Routing config file
app.yml // Plugin default settings
*schema.yml // Data schema
*schema.xml
config.php // Specific plug-in configuration
data/
generator/
sfPropelAdmin
*/ // Administration generator themes
template/
skeleton/
fixtures/
*.yml // Fixtures files
lib/
  *.php        // Classes
  helper/
  *.php        // Helpers
  model/
  *.php        // Model classes
  task/
  *Task.class.php   // CLI tasks
  modules/
  */           // Modules
    actions/
    actions.class.php
    config/
    module.yml
    view.yml
    security.yml
    templates/
    *.php
  web/
  *           // Assets
```

## 插件功能

插件可以包含很多内容。它们的内容会在运行时以及通过命令行调用任务时，被您的应用程序自动考虑。但是，为了让插件正常工作，您必须遵守一些约定：

- 数据库架构由 propel- 任务检测。当您在项目中调用 propel:build --classes 或 doctrine:build --classes 时，您会重建项目模型和所有插件模型。请注意，Propel 插件架构必须始终带有 plugins.pluginName.lib.model 形式的 package 属性，如清单 17-19 所示。如果您使用 Doctrine，任务将自动在插件目录中生成类。

### 清单 17-19 - 插件中 Propel 架构声明示例，在 myPlugin/config/schema.yml 中

```
propel:
  _attributes:  { package: plugins.myPlugin.lib.model }
  my_plugin_foobar:
    _attributes:    { phpName: myPluginFoobar }
    id:
    name:         { type: varchar, size: 255, index: unique }
    ...
```

- 插件配置应包含在插件配置类（PluginNameConfiguration.class.php）中。此文件在应用程序和项目配置之后执行，因此 symfony 此时已引导完成。您可以使用此文件，例如，通过事件监听器和行为扩展现有类。

- 位于插件 data/fixtures/ 目录中的固件文件由 propel:data-load 或 doctrine:data-load 任务处理。

- 自定义类就像您放在项目 lib/ 文件夹中的类一样自动加载。

- 当您在模板中调用 use_helper() 时，助手会自动被找到。它们必须位于插件的某个 lib/ 目录的 helper/ 子目录中。

