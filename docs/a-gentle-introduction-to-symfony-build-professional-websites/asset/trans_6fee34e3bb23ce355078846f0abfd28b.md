

## 创建本地化架构

对于包含本地化数据的每个表，您都应该将表拆分为两部分：一个不包含任何 i18n 列的表，另一个仅包含 i18n 列的表。这两个表通过一对多关系关联。这种设置允许您在需要时添加更多语言，而无需更改模型。让我们考虑一个使用 Product 表的示例。

首先，在 schema.yml 文件中创建表，如清单 13-6 所示。

### 清单 13-6 - 使用 Propel 的 i18n 数据示例架构，在 config/schema.yml 中

```yaml
my_connection:
  my_product:
    _attributes: { phpName: Product, isI18N: true, i18nTable:
      my_product_i18n }
    id:        { type: integer, required: true, primaryKey: true,
                 autoincrement: true }
    price:     { type: float }

  my_product_i18n:
    _attributes: { phpName: ProductI18n }
    id:          { type: integer, required: true, primaryKey: true,
                   foreignTable: my_product, foreignReference: id }
    culture:     { isCulture: true, type: varchar, size: 7, required:
                   true, primaryKey: true }
    name:        { type: varchar, size: 50 }
```

注意第一个表中的 isI18N 和 i18nTable 属性，以及第二个表中的特殊 culture 列。所有这些都是 symfony 特有的 Propel 增强功能。

### 清单 13-7 - 使用 Doctrine 的 i18n 数据示例架构，在 config/doctrine/schema.yml 中

```yaml
Product:
  actAs:
    I18n:
      fields: [name]
  columns:
    price: { type: float }
    name:  { type: string(50) }
```

symfony 的自动化功能可以让编写速度快得多。如果包含国际化数据的表与主表同名，且以 _i18n 作为后缀，并且两个表都通过名为 id 的列关联，那么您可以省略 _i18n 表中的 id 和 culture 列，以及主表中的特定 i18n 属性；symfony 会自动推断它们。这意味着 symfony 将把清单 13-8 中的架构视为与清单 13-6 中的架构相同。

### 清单 13-8 - i18n 数据示例架构，简化版，在 config/schema.yml 中

```yaml
my_connection:
  my_product:
    _attributes: { phpName: Product }
    id:
    price:       float

  my_product_i18n:
    _attributes: { phpName: ProductI18n }
    name:        varchar(50)
```

## 使用生成的 I18n 对象

构建相应的对象模型后（请不要忘记在每次修改 schema.yml 后调用 propel:build --model 任务），您就可以使用带有 i18n 支持的 Product 类，就像只有一个表一样，如清单 13-9 所示。

### 清单 13-9 - 处理 i18n 对象

```php
$product = ProductPeer::retrieveByPk(1);
$product->setName('Nom du produit'); // By default, the culture is the current user culture
$product->save();

echo $product->getName();
=> 'Nom du produit'

$product->setName('Product name', 'en'); // change the value for the 'en' culture
$product->save();

echo $product->getName('en');
=> 'Product name'
```

关于使用 peer 对象进行查询，您可以使用 doSelectWithI18n 方法（而不是通常的 doSelect）将结果限制为具有当前区域设置翻译的对象，如清单 13-10 所示。此外，它将在创建常规对象的同时创建相关的 i18n 对象，从而减少获取完整内容所需的查询次数（有关此方法对性能积极影响的更多信息，请参阅第 18 章）。

### 清单 13-10 - 使用 i18n 条件检索对象

```php
$c = new Criteria();
$c->add(ProductPeer::PRICE, 100, Criteria::LESS_THAN);
$products = ProductPeer::doSelectWithI18n($c, $culture);
// The $culture argument is optional
// The current user culture is used if no culture is given
```

因此，基本上您永远不应该直接处理 i18n 对象，而是在使用常规对象进行查询时，每次都将区域设置传递给模型（或让模型自行推断）。

## 界面翻译

用户界面需要为 i18n 应用程序进行调整。模板必须能够以多种语言显示标签、消息和导航，但保持相同的表现形式。Symfony 建议您使用默认语言构建模板，并在字典文件中为模板中使用的短语提供翻译。这样，您在修改、添加或删除翻译时就不需要更改模板了。

## 配置翻译

模板默认未翻译，这意味着您需要在所有其他操作之前，先在 settings.yml 文件中激活模板翻译功能，如清单 13-11 所示。

### 清单 13-11 - 激活界面翻译，在 frontend/config/settings.yml 中

```yaml
all:
  .settings:
    i18n: true
```

## 使用翻译辅助函数

假设您想创建一个英语和法语网站，以英语为默认语言。在开始之前。因此，用户界面翻译依赖于字典文件。

字典文件采用 XML 本地化交换文件格式（XLIFF）编写，按照 messages.[语言代码].xml 模式命名，并存储在应用程序的 i18n/ 目录中。

XLIFF 是一种基于 XML 的标准格式。众所周知，您可以使用第三方翻译工具来引用网站中的所有文本并进行翻译。翻译公司知道如何处理此类文件，并通过添加新的 XLIFF 翻译来翻译整个网站。

> 除了 XLIFF 标准外，symfony 还支持几种其他用于字典的翻译后端：gettext、MySQL 和 SQLite。有关配置这些后端的更多信息，请参阅 API 文档。

### 清单 13-14 - 一个 XLIFF 字典，在 frontend/i18n/messages.fr.xml 中

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE xliff PUBLIC "-//XLIFF//DTD XLIFF//EN"
"http://www.oasis-open.org/committees/xliff/documents/xliff.dtd" >
<xliff version="1.0">
<file original="global" source-language="en_US" datatype="plaintext">
    <body>
        <trans-unit id="1">
            <source>Welcome to our website.</source>
            <target>Bienvenue sur notre site web.</target>
        </trans-unit>
        <trans-unit id="2">
            <source>Today's date is </source>
            <target>La date d'aujourd'hui est </target>
        </trans-unit>
    </body>
</file>
</xliff>
```

source-language 属性必须始终包含默认区域设置的完整 ISO 代码。每个翻译都写在带有唯一 id 属性的 trans-unit 标记中。

使用默认用户区域设置（设置为 en_US）时，短语不会被翻译，而会显示 __() 调用的原始参数。清单 13-12 的结果然后类似于清单 13-11。但是，如果区域设置更改为 fr_FR 或 fr_BE，则会改为显示 messages.fr.xml 文件中的翻译，结果类似于清单 13-15。

### 清单 13-15 - 一个已翻译的模板

```php
Bienvenue sur notre site web. La date d'aujourd'hui est
<?php echo format_date(date()) ?>
```

如果需要进行其他翻译，只需在同一目录中添加一个新的 messages.XX.xml 翻译文件即可。

> 由于查找字典文件、解析它们以及为给定字符串找到正确翻译需要一些时间，symfony 使用内部缓存来加快此过程。默认情况下，此缓存使用文件系统。您可以在 factories.yml 中配置 i18n 缓存的工作方式（例如，在多个服务器之间共享缓存）（请参见第 19 章）。

## 管理字典

如果您的 messages.XX.xml 文件过长难以阅读，您可以随时将翻译拆分为按主题命名的几个字典文件。例如，您可以将 messages.fr.xml 文件拆分为应用程序 i18n/ 目录中的以下三个文件：

- navigation.fr.xml
- terms_of_service.fr.xml
- search.fr.xml

请注意，一旦在默认的 messages.XX.xml 文件中找不到翻译，您就必须在每次调用 __() 辅助函数时使用其第三个参数声明要使用的字典。例如，要输出在 navigation.fr.xml 字典中翻译的字符串，请编写以下内容：

```php
<?php echo __('Welcome to our website', null, 'navigation') ?>
```

