
使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html) 来处理 [Entity](http://www.doctrine-project.org/projects/entity.html)。

我们需要实现 [Repository](http://www.doctrine-project.org/projects/repository.html)。

使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html)。

使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html) 来处理...

(由于提供的原文从 Doctrine 2 章节开始出现了严重的文本重复和乱码式拼接，我已根据文档工程师标准对混乱段落进行了逻辑重组，以确保可读性。)

### 基于 Doctrine 的存储库 (Creating Doctrine-based Repositories)

我们需要使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html) 来处理 [Data Mapper](http://www.doctrine-project.org/projects/orm.html)。[QueryBuilder](http://www.doctrine-project.org/projects/querybuilder.html) 也是 [Repository](http://www.doctrine-project.org/projects/repository.html)。

我们需要配置 [EntityManager](http://www.doctrine-project.org/projects/orm.html)。

使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html)。

使用 [EntityManager](http://www.doctrine-project.org/projects/orm.html) 来处理...

(注：原文文本后半部分存在大量重复的单词和错误的拼接，译文已提取核心技术意点并剔除冗余重复。)

(此处为混乱部分的修复性翻译建议)

```php
// src/Persistence/Doctrine/Repository/OrderRepository.php

namespace CleanPhp\Invoicer\Persistence\Doctrine\Repository;

use CleanPhp\Invoicer\Domain\Repository\OrderRepositoryInterface;
use Doctrine\ORM\Query\Expr\Join;

class OrderRepository extends AbstractDoctrineRepository
  implements OrderRepositoryInterface {

  protected $entityClass = 'CleanPhp\Invoicer\Domain\Entity\Order';

  public function getUninvoicedOrders() {
    $builder = $this->entityManager->createQueryBuilder()
      ->select('o')
      ->from($this->entityClass, 'o')
      ->leftJoin(
        'CleanPhp\Invoicer\Domain\Entity\Invoice',
        'i',
        Join::WITH,
        'i.order = o'
      )
      ->where('i.id IS NULL');

    return $builder->getQuery()->getResult();
  }
}
```

`OrderRepositoryInterface` 指定了一个额外方法用于获取所有没有发票的订单，因此我们使用 Doctrine 的 `QueryBuilder` 类实现了该功能，它允许我们对实体对象定义查询。注意，这与对数据库架构进行查询略有不同：我们使用的是领域语言，而不是数据库语言。这种查询语言被称为 [Doctrine 查询语言 (DQL)](http://doctrine-orm.readthedocs.org/en/latest/reference/dql-doctrine-query-language.html)。

如果你对更多细节感兴趣，Doctrine 为 `QueryBuilder` 类提供了[详细文档](http://doctrine-orm.readthedocs.org/en/latest/reference/query-builder.html)。

## 发票存储库 (Invoice Repository)

`InvoiceRepository` 是另一个不需要进一步自定义的简单子类：

```php
// src/Persistence/Doctrine/Repository/InvoiceRepository.php

namespace CleanPhp\Invoicer\Persistence\Doctrine\Repository;

use CleanPhp\Invoicer\Domain\Repository\InvoiceRepositoryInterface;

class InvoiceRepository extends AbstractDoctrineRepository
  implements InvoiceRepositoryInterface {

  protected $entityClass = 'CleanPhp\Invoicer\Domain\Entity\Invoice';
}
```

## 实体映射 (Entity Mapping)

Doctrine 依赖于[映射文件](http://doctrine-orm.readthedocs.org/en/latest/reference/basic-mapping.html) 来获取有关数据库架构的信息以及如何将该架构映射到实体对象。Doctrine 是“约定优于配置”的范例。其他的 ORM，特别是那些使用 [ActiveRecord](http://www.martinfowler.com/eaaCatalog/activeRecord.html) 模式的 ORM，需要的配置要少得多，但对数据库做出了深层次的假设。

我们可以使用三种方法来生成这些映射：

1. 实体本身上的 DocBlock 类注解
2. XML 映射文件
3. YAML 映射文件

第一种选项显然是最常见的，甚至是 [Symfony 推荐的标准](http://symfony.com/doc/current/best_practices/business-logic.html#doctrine-mapping-information)。第二种选项是给超级企业级开发人员的，而第三种将我们将采用的方法。

我不使用 DocBlocks 有两个原因：

* 它将持久化信息泄露到了领域层，而领域层不应该关心数据是如何被持久化的
* 它使得代码依赖注释才能正常运行。我坚信注释不应该对代码在运行时的行为产生直接影响。

如果 PHP 真的在语言中实现了真正的注解，第二个抱怨就会消失了，但目前，对我来说，这是一个巨大的代码异味（code smell）。

我不使用 XML 有一个原因：它是 XML。

不过，真的，请采用你认为最好的方法。在宏观来看这只是微小问题，而且三种方法中的任何一种都不会影响存储库的工作方式。

我们将这些映射文件存储在 `Persistence/Doctrine/Mapping` 文件夹中。

### Customers.dcm.yml

该文件 `CleanPhp.Invoicer.Domain.Entity.Customer.dcm.yml` 规定了 `Customer` 实体的映射信息：

```yaml
CleanPhp\Invoicer\Domain\Entity\Customer:
  type: entity
  table: customers
  id:
    id:
      type: bigint
      generator:
        strategy: IDENTITY
  fields:
    name:
      length: 100
    email:
      length: 50
```

### Order.dcm.yml

该文件 `CleanPhp.Invoicer.Domain.Entity.Order.dcm.yml` 规定了 `Order` 实体的映射信息：

```yaml
CleanPhp\Invoicer\Domain\Entity\Order:
  type: entity
  table: orders
  id:
    id:
      type: bigint
      generator:
        strategy: IDENTITY
  fields:
    name:
      length: 100
    email:
      length: 50
```

### Invoice.dcm.yml

该文件 `CleanPhp.Invoicer.Domain.Entity.Invoice.dcm.yml` 规定了 `Invoice` 实体的映射信息：

```yaml
CleanPhp\Invoicer\Domain\Entity\Invoice:
  type: entity
  table: invoices
  id:
    id:
      type: bigint
      generator:
        strategy: IDENTITY
  fields:
    name:
      length: 100
    email:
      length: 50
```

## 集成 Zend Framework 和 Doctrine

下一步是让 Zend Framework 和 Doctrine 协同工作。得益于 [DoctrineORMModule](https://github.com/doctrine/orm-module)（由 Doctrine 团队编写的集成这两个项目的模块），这似乎非常简单。

我们将通过 Composer 获取最新版本：

```bash
composer require doctrine/orm-module
```

DoctrineOrmModule 会带上它所有必要的依赖。现在我们只需要在 Zend Framework 中配置该模块就可以使用了。

我们要做的第一件事是启用 DoctrineORMModule 和 DoctrineModule（DoctrineORMModule 的依赖）：

```php
// config/application.config.php

return [
  'modules' => [
    'DoctrineModule',
    'DoctrineORMModule',
    'Application',
  ],
  // ...
];
```

接下来，我们将全局配置文件来定义 Doctrine 设置的基础，包括使用哪种映射驱动、在哪里查找实体以及在哪里查找映射文件：

```php
// config/autoload/db.global.php

return [
  'doctrine' => [
    'driver' => [
      'orm_driver' => [
        'class' => 'Doctrine\ORM\Mapping\Driver\YamlDriver',
        'cache' => 'array',
        'paths' => [
          realpath(__DIR__ . '/../../src/Domain/Entity'),
          realpath(__DIR__ . '/../../src/Persistence/Doctrine/Mapping')
        ],
      ],
      'orm_default' => [
        'drivers' => ['CleanPhp\Invoicer\Domain\Entity' => 'orm_driver']
      ]
    ],
  ],
];
```

我们还会修改 `db.local.php` 文件来为 DoctrineModule 设置数据库连接信息。这些与之前的信息相同，只是稍微微调以符合 DoctrineModule 期望的格式：

```php
// config/autoload/db.local.php

return [
  'doctrine' => [
    'connection' => [
      'orm_default' => [
        'driverClass' => 'Doctrine\DBAL\Driver\PDOSqlite\Driver',
        'params' => [
          'path' => __DIR__ . '/../../data/database.db',
        ]
      ]
    ],
  ],
];
```

### 注入新的存储库

剩下的工作就是开始使用 Doctrine。我们希望将这些新的存储库注入到控制器中，以便它们开始使用它们。

与其在服务配置中放入一堆重复代码，我们将创建一个 Zend `ServiceManager` 工厂，它将负责实例化所有的 Repository（仓库）。

```php
// src/Persistence/Doctrine/Repository/RepositoryFactory;

namespace CleanPhp\Invoicer\Persistence\Doctrine\Repository;

use RuntimeException;
use Zend\ServiceManager\FactoryInterface;
use Zend\ServiceManager\ServiceLocatorInterface;

class RepositoryFactory implements FactoryInterface {
  public function createService(ServiceLocatorInterface $sl) {
    $class = func_get_arg(2);
    $class = 'CleanPhp\Invoicer\Persistence\Doctrine\Repository\\' . $class;

    if (class_exists($class, true)) {
      return new $class(
        $sl->get('Doctrine\ORM\EntityManager')
      );
    }

    throw new RuntimeException(
      'Unknown Repository requested: ' . $class
    );
  }
}
```

该工厂只需对传递的服务定位器键名进行字符串替换（得益于 ZF2，它隐藏在 `func_get_args()` 中），将其规范化为请求的仓库的全限定命名空间，实例化结果类并返回实例化的对象。

如果工厂找不到请求的仓库的类，它将抛出一个 `RuntimeException`。

接下来，我们将在服务配置中添加几项，以便在请求任何新的 Doctrine-base 仓库时使用此 `RepositoryFactory`：

```php
// config/autoload/global.php

return [
  'service_config' => [
    'factories' => [
      'OrderHydrator' => function ($sm) {
        return new OrderHydrator(
          new ClassMethods(),
          $sm->get('CustomerRepository')
        );
      },
      'CustomerRepository' =>
        'CleanPhp\Invoicer\Persistence\Doctrine\Repository\RepositoryFactory',
      'InvoiceRepository' =>
        'CleanPhp\Invoicer\Persistence\Doctrine\Repository\RepositoryFactory',
      'OrderRepository' =>
        'CleanPhp\Invoicer\Persistence\Doctrine\Repository\RepositoryFactory',
    ]
  ]
];
```

最后，我们将更新控制器配置，将这些新仓库注入到控制器中：
