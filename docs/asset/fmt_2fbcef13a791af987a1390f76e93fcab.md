
```php
// config/autoload/global.php

use CleanPhp\Invoicer\Domain\Entity\Customer;
use CleanPhp\Invoicer\Persistence\Zend\DataTable\CustomerTable;
use CleanPhp\Invoicer\Persistence\Zend\TableGateway\TableGatewayFactory;
use Zend\Stdlib\Hydrator\ClassMethods;

return [
  'service_manager' => [
    'factories' => [
      'CustomerTable' => function($sm) {
        $factory = new TableGatewayFactory();
        $hydrator = new ClassMethods();
        
        return new CustomerTable(
          $factory->createGateway(
            $sm->get('Zend\Db\Adapter\Adapter'),
            $hydrator,
            new Customer(),
            'customers'
          ),
          $hydrator
        );
      },
    ]
  ]
];
```

我们使用`TableGatewayFactory`创建`TableGateway`实例并提供给`CustomerTable`。我们还传递了`ClassMethods`填充化器实例，以及`Customer`对象和`customers`表名。

现在我们已经配置好并准备好运行`Z Framework`，同时数据库也已设置并配置完毕，我们可以开始实际使用它了。

让我们从客户管理开始。我们已经定义了一个路由，但当我们导航到该路由时，将会收到来自`ZF2`的一个悲伤的错误消息：

> 发生 404 错误未找到页面。请求的控制器无法映射到现有控制器类。

> 控制器: ApplicationControllerCustomers（解析为无效的控制器类或别名: ApplicationControllerCustomers）无可用异常

这是很合理的，因为我们定义了一个指向`Customers`控制器的路由，但并没有花精力创建那个控制器。所以，让我们创建它吧。

## 客户管理

让我们开始构建我们的`CustomersController::indexAction()`，它将显示所有客户的网格。

| ![generic\_inbar](img/leanpub_frown-o.png) || 我花费了大量时间试图弄如何在 Zend Framework 中对控制器进行单元测试。我打算直说：这是不可能的。根据操作的不同，你需要引导或模拟（mock）四个到四十四种不同的服务、插件等。Zend 提供了一个关于测试其控制器的[很好的教程](http://framework.zend.com/manual/2.0/en/user-guide/unit-testing.html)。他们称其为单元测试，但只有当他们指的是整个 ZF2 生态系统作为一个单元时，这才是真的。因此，我将忽略这些控制器的测试。如果是在现实生活中，我会硬着头皮编写集成测试（这也很重要）。但为了这本书，那太不值得精力了。 |

| --- | --- |

让我们开始编写我们的`indexAction()`：

```php
// modules/Application/src/Application/Controller/CustomersController.php

namespace Application\Controller;

use CleanPhp\Invoicer\Domain\Repository\CustomerRepositoryInterface;
use Zend\Mvc\Controller\AbstractActionController;

class CustomersController extends AbstractActionController {
  public $customerRepository;

  public function __construct(
    CustomerRepositoryInterface $customers
  ) {
    $this->customerRepository = $customers;
  }

  public function indexAction() {
    return [
      'customers' => $this->customerRepository->getAll()
    ];
  }
}
```

我们有一个新的`CustomersController`类，带有一个`indexAction()`方法。注入了一个`CustomerRepositoryInterface`实例，稍后由该操作用来调用`getAll()`方法。我们将该方法的结果在一个数组中返回，键名为`customers`。

现在我们需要适当的视图来表示`indexAction()`，我们应该能在屏幕上看到我们的数据。让我们把视图文件放进去：

```php
<!-- module/Application/views/application/customers/index.phtml -->

<div class="page-header clearfix">
  <h2 class="pull-left">Customers</h2>
  <a href="/customers/new" class="btn btn-success pull-right">
    Create Customer</a>
</div>

<table class="table">
  <thead>
    <tr>
      <th>#</th>
      <th>Name</th>
      <th>Email</th>
    </tr>
 </head>
 <?php foreach ($this->customers as $customer): ?>
    <tr>
      <td>
        <a href="/customers/edit/<?= $customer->getId() ?>">
          <?= $customer->getId() ?></a>
      </td>
      <td><?= $customer->getName() ?></td>
      <td><?= $customer->getEmail() ?></td>
    </tr>
  <?php endforeach; ?>
</table>
```

最后，我们需要配置 ZF2 让它知道`CustomersController`就是我们在路由中引用的`Customers`控制器。即使我们在路由中调用它为`CustomersController`，ZF2 仍然不知道我们在说什么，因为这里的字符串仅仅是控制器服务定位器内部的键。

在模块配置文件的`controllers`部分，我们将为我们的新控制器添加一个条目：

```php
// module/Application/config/module.config.php

return [
  // ...
  'controllers' => [
    'invokables' => [
      'Application\Controller\Index' =>
        'Application\Controller\IndexController'
    ],
    'factories' => [
      'Application\Controller\Customers' => function ($sm) {
        return new \Application\Controller\CustomersController(
          $sm->getServiceLocator()->get('CustomerTable')
        );
      },
    ],
  ],
  // ...
];
```

与主`IndexController`不同，这个`CustomersController`条目将作为工厂注册到 ZF，这样它就不仅仅是直接实例化，而是允许我们嵌入关于其如何实例化的逻辑，从而允许我们注入正确的依赖项。我们使用上一章中定义的`CustomerTable`条目来获取我们的客户数据表，它实现了`CustomerRepositoryInterface`并满足了`CustomersController`构造函数上的类型提示。

所以现在，如果我们在亲爱的浏览器中导航到`/customers`，我们应该能看到从 sqlite 数据库中渲染的所有客户在屏幕上。成功了！

| ![generic\_inbar](img/leanpub_git.png) || 这将是你将代码提交到版本控制的好地方。如果你只是在阅读，但想看到代码运行的效果，可以查看。

| --- | --- |

## 创建客户

在我们的 HTML 中，我们有一个创建客户的按钮，引导用户进入`/new`。让我们开始构建我们的操作操作。

### newAction()

让我们开始构建`newAction()`以及对应的视图文件：

```php
// modules/Application/src/Application/Controller/CustomersController.php

namespace Application\Controller;

use CleanPhp\Invoicer\Domain\Repository\CustomerRepositoryInterface;
use Zend\Mvc\Controller\AbstractActionController;

class CustomersController extends AbstractActionController {
  // ...

  public function newAction() {

  }
}
```

这个简单的控制器操作就是我们最初需要的。让我们构建我们的视图：

```php
<!-- module/Application/views/application/customers/new.phtml -->

<div class="page-header clearfix">
  <h2>New Customer</h2>
</div>

<form role="form" action="" method="post">
  <div class="form-group">
    <label for="name">Name:</label>
    <input type="text" class="form-control" name="name" id="name"
      placeholder="Enter Name">
  </div>
  <div class="form-group">
    <label for="email">Email:</label>
    <input type="text" class="form-control" name="email" id="email"
      placeholder="Enter Email">
  </div>
  <button type="submit" class="btn btn-primary">Save</button>
</form>
```

接下来，我们需要更新我们的路由来处理`/customers/new`：

```php
// module/Application/config/module.config.php

return [
  'router' => [
    'routes' => [
      // ...
      'customers' => [
        // ...
        'may_terminate' => true,
        'child_routes' => [
          'create' => [
            'type' => 'Segment',
            'options' => [
              'route' => '/new',
              'defaults' => [
                'action' => 'new',
              ],
            ]
          ],
        ]
      ],
      // ...
    ],
  ],
  // ...
];
```

这个简单的子路由将结合父路由的`/customers`和子路由的`/new`，从而产生我们的`/customers/new`路由，这将指向`CustomersController`的`newAction()`。

## CustomerInputFilter

我们将使用 Zend 的`InputFilter`来验证和清理我们的输入。你可以在[他们的文档中阅读更多关于 Zend Input Filters 的信息](http://framework.zend.com/manual/current/en/modules/zend.input-filter.intro.html)，但本质上，它们提供了一组用于验证和清理输入数据的类。

我们将`InputFilters`放入`src/`目录，因为当我们决定切换掉 Zend Framework 时，将希望使用它们。否则，我们不得不为验证输入数据构建一套全新的解决方案，虽然这也可以行，但如果不需要同时做那件事的话未免会更好。

我们将从编写一个规格说明（spec）开始，描述我们想要的行为。首先，我们需要一个即将创建的新的`CustomerInputFilter`实例来进行测试：

```php
// specs/input-filter/customer.spec.php

use CleanPhp\Invoicer\Service\InputFilter\CustomerInputFilter;

describe('InputFilter\Customer', function () {
  beforeEach(function () {
      $this->inputFilter = new CustomerInputFilter();
  });

  describe('->isValid()', function () {
    // ...
  });
});
```

我们将关注测试`isValid()`方法，Zend 通过该方法来判断`InputFilter`的数据是否有效。我们还将使用`setData()`方法为`InputFilter`提供一些测试数据。

让我们从测试客户名称的有效性开始：

```php
it('should require a name', function () {
  $isValid = $this->inputFilter->isValid();

  $error = [
    'isEmpty' => 'Value is required and can\'t be empty'
  ];

  $messages = $this->inputFilter
    ->getMessages()['name'];

  expect($isValid)->to->equal(false);
  expect($messages)->to->equal($error);
});
```

最后，我们将测试电子邮件地址的有效性。在这里，我们并不特别担心 ZF2 在我们提供无效数据时返回的精确消息，只要我们收到了某种错误数组而不是`null`即可：
