

## 第 5 章 配置 Symfony

为了简单易用，Symfony 定义了一些约定，这些约定应能满足标准应用的最常见需求，无需修改。然而，通过一组简单而强大的配置文件，可以自定义框架与您的应用交互的几乎所有方面。使用这些文件，您还可以为应用添加特定参数。

本章将解释配置系统的工作原理：

- Symfony 的配置保存在用 YAML 编写的文件中，不过您始终可以选择其他格式。

- 配置文件位于项目目录结构的项目、应用和模块层级中。

- 您可以定义多组配置设置；在 Symfony 中，一组配置称为一个环境。

- 配置文件中定义的值可从应用的 PHP 代码中获取。

- 此外，Symfony 允许在 YAML 文件中使用 PHP 代码以及其他技巧，以使配置系统更加灵活。

## 配置系统

无论用途如何，大多数 Web 应用都共享一组共同特征。例如，某些部分可能仅限部分用户访问，或者页面可以使用布局进行装饰，或者表单可以在验证失败后填充用户输入。框架定义了模拟这些特征的结构，开发者可以通过更改配置设置进一步调整它们。这种策略节省了大量开发时间，因为许多更改不需要编写一行代码，即使背后有大量代码。它也更高效，因为它确保此类信息可以维护在单个且易于识别的位置。

然而，这种方法有两个严重缺点：

- 开发人员最终会编写无限复杂的 XML 文件。

- 在 PHP 架构中，每个请求的处理时间要长得多。

考虑到这些缺点，Symfony 仅在配置文件最擅长的方面使用它们。事实上，Symfony 配置系统的雄心是：

- 功能强大：几乎所有可以使用配置文件管理的方面都使用配置文件进行管理。

- 简单：许多配置方面在普通应用中不显示，因为它们很少需要更改。

- 易用：配置文件易于读取、修改和由开发者创建。

- 可定制：默认配置语言是 YAML，但也可以是 INI、XML 或开发者偏好的任何格式。

- 快速：配置文件从不由应用处理，而是由配置系统处理，它将它们编译为 PHP 服务器快速处理的代码块。

## YAML 语法和 Symfony 约定

为其配置，Symfony 默认使用 YAML 格式，而非更传统的 INI 或 XML 格式。YAML 通过缩进显示结构，编写速度快。其优势和基本规则已在第 1 章中描述。但是，在编写 YAML 文件时，您需要牢记一些约定。本节介绍几项最突出的约定。要完整阐述该主题，请阅读参考指南书中的专用章节31。

31. http://www.symfony-project.org/reference/1_4/en/02-YAML

首先，切勿在 YAML 文件中使用制表符；请改用空格。YAML 解析器无法理解带有制表符的文件，因此请使用空格缩进您的行（双空格是 Symfony 缩进的惯例），如清单 5-1 所示。

### 清单 5-1 - YAML 文件禁止使用制表符

```
# Never use tabs
all:
	mail:
		webmaster:  webmaster@example.com

# Use blanks instead
all:
  mail:
    webmaster:  webmaster@example.com
```

如果您的参数是以空格开头或结尾的字符串，包含特殊字符（例如“井号”（#）或逗号），或“true、false”等关键字（其中字符串为预期内容），则必须将值用单引号括起来，如清单 5-2 所示。

### 清单 5-2 - 非标准字符串应用单引号括起来

```
error1:  This field is compulsory
error2:  ' This field is compulsory '
error3:  'Don''t leave this field blank'  # Single quotes must be doubled
error4:  'Enter a # symbol to define an extension number'
i18n:    'false' # if we left off the quotes here, a boolean false would be returned
```

您可以使用特殊字符串标头（> 和 |）加上额外缩进来定义多行长字符串以及多行字符串。清单 5-3 演示了此约定。

### 清单 5-3 - 定义长字符串和多行字符串

```
# Folded style, introduced by >
# Each line break is folded to a space
# Makes YAML more readable
accomplishment: >
  Mark set a major league
  home run record in 1998.

# Literal style, introduced by |
# All line breaks count
# Indentation doesn't appear in the resulting string
stats: |
  65 Home Runs
  0.278 Batting Average
```

要将值定义为数组，请将元素括在方括号中或使用带破折号的扩展语法，如清单 5-4 所示。

### 清单 5-4 - YAML 数组语法

```
# Shorthand syntax for arrays
players: [ Mark McGwire, Sammy Sosa, Ken Griffey ]

# Expanded syntax for arrays
players:
  - Mark McGwire
  - Sammy Sosa
  - Ken Griffey
```

要将值定义为关联数组（或哈希），请将元素括在花括号中，并在键:值对的键和值之间始终插入空格，任何列表项之间用逗号分隔。您也可以通过为每个新键添加缩进和回车来使用扩展语法，如清单 5-5 所示。

### 清单 5-5 - YAML 关联数组语法

```
# Incorrect syntax, blanks are missing after the colons and comma
mail: {webmaster:webmaster@example.com,contact:contact@example.com}

# Correct shorthand syntax for associative arrays
mail: { webmaster: webmaster@example.com, contact: contact@example.com }

# Expanded syntax for associative arrays
mail:
  webmaster: webmaster@example.com
  contact: contact@example.com
```

要指定布尔值，可以使用 false 和 true 值，前提是它们不被引号括起来。

### 清单 5-6 - YAML 布尔值语法

```
true_value:  true
false_value: false
```

不要犹豫，添加注释（以井号 # 开头）和额外空格到值中，以使您的 YAML 文件更易读，如清单 5-7 所示。

### 清单 5-7 - YAML 注释语法和值对齐

```
# This is a comment line
mail:
  webmaster:  webmaster@example.com
  contact:   contact@example.com
admin:  admin@example.com  # extra spaces allow nice alignment of values
```

在某些 Symfony 配置文件中，您有时会看到以井号开头（因此被 YAML 解析器忽略）但看起来像通常设置行的行。这是 Symfony 的惯例：继承自 Symfony 核心中其他 YAML 文件的默认配置，会以注释行重复在您的应用程序配置中，供您参考。如果要更改此类参数的值，需要先取消注释该行，如清单 5-8 所示。

### 清单 5-8 - 默认配置以注释形式显示

```
# The cache is off by default
settings:
# cache: false

# If you want to change this setting, uncomment the line first
settings:
  cache: true
```

Symfony 有时会将参数定义分组到类别中。给定类别的所有设置都以缩进形式出现在类别标题下方。通过将长键:值对列表分组到类别中来构建结构，可以提高配置的可读性。类别标题以点 (.) 开头。清单 5-9 显示了类别示例。

### 清单 5-9 - 类别标题看起来像键，但以点开头

```
all:
  .general:
    tax: 19.6

mail:
  webmaster: webmaster@example.com
```

在此示例中，mail 是键，而 general 只是类别标题。一切工作如同类别标题不存在一样，如清单 5-10 所示。tax 参数实际上是 all 键的直接子项。但是，使用类别有助于 Symfony 处理 all 键下的数组。

### 清单 5-10 - 类别标题仅用于可读性，实际被忽略

```
all:
  tax: 19.6

mail:
  webmaster: webmaster@example.com
```

