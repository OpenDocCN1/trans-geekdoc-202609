
```php
// peridot.php

use Evenement\EventEmitterInterface;
use Peridot\Plugin\Watcher\WatcherPlugin;

return function(EventEmitterInterface $emitter) {
  $watcher = new WatcherPlugin($emitter);
  $watcher->track(__DIR__ . '/src');
};
```

现在我们可以使用 `--watch` 标志连续运行测试了！

```bash
./vendor/bin/peridot specs/ --watch
```

## 发票服务

此应用程序中领域逻辑中最大的部分是发票流程。我们将每月收集所有未开票的订单，并为它们生成发票。我们的目标是独立于任何框架、库或其他外部服务来完成这一。这样，我们可以确保核心应用程序与自身以外的任何内容完全解耦，并且它可以轻松地到到任何框架中执行其功能。

该服务将使用 `OrderRepositoryInterface` 来收集需要开票的订单，然后使用我们的 `InvoiceFactory` 为这些订单创建发票。让我们再次从编写测试来定义这些行为开始：

```php
// specs/domain/service/invoice-factory.spec.php

describe('InvoicingService', function () {
  describe('->generateInvoices()', function () {
    it('应该查询仓库以获取未开票的 Orders');
    it('应该为每个未开票的 Order 返回一个 Invoice');
  });
});
```

这次的情况稍微复杂一点。由于我们还没有编写任何具体的仓库实现，因此无法使用它来执行此测试。与其编写并使用具体的仓库实现，我们打算使用 Prophecy 库来模拟（mock）一个。

幸运的是，Peridot 也带有一个插件，让这些集成变得轻而易举。让我们来安装它：

```bash
composer require --dev peridot-php/peridot-prophecy-plugin
```

然后将其添加到到我们的 `peridot.php` 文件中：

```php
// peridot.php

use Evenement\EventEmitterInterface;
use Peridot\Plugin\Prophecy\ProphecyPlugin;
use Peridot\Plugin\Watcher\WatcherPlugin;

return function(EventEmitterInterface $emitter) {
  $watcher = new WatcherPlugin($emitter);
  $watcher->track(__DIR__ . '/src');

  new ProphecyPlugin($emitter);
};
```

现在，我们可以编写一个 `beforeEach()` 块，它将在每个测试之前执行，为我们构建一个模拟的 `OrderRepositoryInterface`：

```php
// specs/domain/service/invoice-factory.spec.php

describe('InvoicingService', function () {
  describe('->generateInvoices()', function () {
    beforeEach(function () {
      $this->repository = $this->getProphet()->prophesize(
        'CleanPhp\Invoicer\Domain\Repository\OrderRepositoryInterface'
      );
    });
    // ...
  });
});
```

当我们需要时，`$this->repository` 将持有模拟仓库的实例。现在我们可以完成第一个测试了：

```php
it('应该查询仓库以获取未开票的 Orders', function () {
  $this->repository->getUninvoicedOrders()->shouldBeCalled();
  $service = new InvoicingService($this->repository->reveal());
  $service->generateInvoices();
});
```

我们在这里测试的是，当调用 `generateInvoices()` 方法时，我们预期 `InvoicingService` 会调用 `OrderRepositoryInterface` 的 `getUninvoicedOrders()` 方法。

我们还想添加一个 `afterEach()` 块来告诉 Prophecy 检查它所做的断言（例如 `shouldBeCalled()`），否则它将不知道确切何时安全地检查该断言。我们可以在 `afterEach()` 中这样做是为了方便自己，但实际上我们可以将其添加到任何地方：

```php
afterEach(function () {
  $this->getProphet()->check();
});
```

我们的测试当然是失败的，因为代码还没有设置以满足测试的预期，所以让我们定稿 `InvoicingService`：

```php
// src/Domain/Service/InvoicingService.php

namespace CleanPhp\Invoicer\Domain\Service;

use CleanPhp\Invoicer\Domain\Factory\InvoiceFactory;
use CleanPhp\Invoicer\Domain\Repository\OrderRepositoryInterface;

class InvoicingService{
  protected $orderRepository;
  protected $invoiceFactory;

  public function __construct(
    OrderRepositoryInterface $orderRepository,
    InvoiceFactory $invoiceFactory
  ) {
    $this->orderRepository = $orderRepository;
    $this->invoiceFactory = $invoiceFactory;
  }

  public function generateInvoices() {
    $orders = $this->orderRepository->getUninvoicedOrders();

    $invoices = [];

    foreach ($orders as $order) {
      $invoices[] = $this->invoiceFactory->createFromOrder($order);
    }

    return $invoices;
  }
}
```

我们现在在构造函数中接收一个 `InvoiceFactory` 实例，并在遍历 `getUninvoicedOrders()` 的结果时使用它为每个 `Order` 创建 `Invoice`。完成后，我们返回此集合。这与我们在测试中定义的行为完全一致。

我们的测试通过了，我们的服务现在已经完成。

| ![tip](img/leanpub_key.png) || 这里是将你的代码提交到版本控制的好地方。如果你只是在阅读，但想看到代码的运行情况，可以检出标签 02-domain-services： |

```
git clone https://github.com/mrkrstphr/cleanphp-example.git
git checkout 02-domain-services
``` |

| --- | --- |

### 总结

到此，我们应用程序的领域部分结束了。应用的领域模型和领域层是其他一切工作的核心。它们包含了我们的业务逻辑，这部分代码不会因为我们决定使用哪些库或框架，或者我们选择如何持久化数据库而改变。

存在于这两个层之外的所有内容都将利用它们来完成应用程序的目标。

我们现在准备好开始构建应用程序的前端部分了！

# Zend Framework 2 设置

我们将开始使用 Zend Framework 2 构建我们的项目。ZF2 是 Zend Framework 的第二次迭代，是一个模块化的、基于事件的框架，拥有一套丰富的库。至少从示例应用程序来看，它是一个支持各种数据库系统的 MVC 框架。

虽然 ZF2 并不是我首选的框架，但它可能是人们在第一次寻找框架时会遇到的之一，特别是由于一个错误的假设，认为它实际上可能得到了 PHP 本身的认可或关联。这种误解可能源于这样一个事实：目前 PHP 的运行时被称为 Zend Engine，而启动它的两个核心人物 Andi Gutmans 和 Zeev Suraski（Zeev + Andi = Zend）后来成立了一家名为 Zend Technologies 的公司，该公司负责 Zend Framework。

无论如何，Zend Framework 并不与 PHP 直接关联，也不受 PHP 认可。

## 使用 Composer 安装

我们在上一章节中安装了 Composer 来设置自动加载器。现在，我们将使用它来下载并配置 ZF Skeleton 应用程序。由于你不能将 git 仓库克隆到现有的非空目录，我们需要稍微“耍个滑”来让它工作。

我们将在与之前的 `cleanphp/` 目录不同的目录中创建我们的 ZF Skeleton 应用程序：

```
cd /path/to/your/preferred/www
composer create-project \
  --repository-url="http://packages.zendframework.com" \
  -sdev zendframework/skeleton-application \
  cleanphp-skeleton
```

此命令会询问你是否想要“移除现有的 VCS 历史”。当询问出现时，输入“Y”来移除 `.git` 目录。

你现在应该有了一个 ZF2 Skeleton 应用程序的工作副本。进入 `public/` 目录并启动 PHP 的内置 Web 服务器：

```
cd cleanphp-skeleton
php -S localhost:1337 -t public
```

在 浏览器中访问 `http://localhost:1337/`，你就能看到结果了！

### 合并代码库

现在我们有两个独立的项目，所以我们需要将 ZF2 特有的代码移动到我们的 `cleanphp/` 目录。在两个 `cleanphp*` 目录的父目录下执行如下操作：

```
cp -R cleanphp-skeleton/config \
  cleanphp-skeleton/data \
  cleanphp-skeleton/public \
  cleanphp-skeleton/module \
  cleanphp-skeleton/init_autoloader.php \
  cleanphp/
```

我们还想确保在该项目中通过 Composer 安装了 Zend Framework：

```bash
composer require zendframework/zendframework
```

现在我们可以删除 `cleanphp-skeleton/` 目录了：

```
rm -rf cleanphp-skeleton/
```

那操作感觉很不舒服又笨拙，所以让我们开始使用 ZF2 吧！

## 清理骨架

现在是时候让 ZF2 骨架服从我们的意愿了。我们只需要快速做一些外观上的调整，把 ZF2 的品牌去掉。

首先，用以下内容替换 `module/Application/view/layout/layout.phtml`：

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>CleanPhp</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <link href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.css" 
    media="screen" rel="stylesheet" type="text/css">
  <link href="/css/application.css" media="screen" 
    rel="stylesheet" type="text/css">
</head>
<body>
<nav class="navbar navbar-default navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <a class="navbar-brand" href="/">CleanPhp</a>
    </div>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <li>
          <a href="/customers">Customers</a>
        </li>
        <li>
          <a href="/orders">Orders</a>
        </li>
        <li>
          <a href="/invoices">Invoices</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
<div class="container">
  <?= $this->content; ?>
  <hr>
  <footer>
    <p>I'm the footer.</p>
  </footer>
</div>
</body>
</html>
```

在这里，我们抛弃了大量的 ZF2 视图助手和布局，并选择使用 CDN 提供的 Bootstrap 版本。我们可以完全删除 `public/css`、`public/fonts`、`public/img` 和 `public/js` 文件夹。

我们在页头中定义了一些指向未来页面的链接。让我们在 Zend Framework 中为这些页面设置路由：

```php
// module/Application/config/module.config.php

return [
  // ...
  'router' => [
    'routes' => [
      'home' => [
        'type' => 'Zend\Mvc\Router\Http\Literal',
        'options' => [
          'route' => '/',
          'defaults' => [
            'controller' => 'Application\Controller\Index',
            'action' => 'index',
          ],
        ],
      ],
      'customers' => [
        'type' => 'Segment',
        'options' => [
          'route' => '/customers',
          'defaults' => [
            'controller' => 'Application\Controller\Customers',
            'action' => 'index',
          ],
        ],
      ],
      'orders' => [
        'type' => 'Segment',
        'options' => [
          'route' => '/orders',
          'defaults' => [
            'controller' => 'Application\Controller\Orders',
            'action' => 'index',
          ],
        ],
      ],
      'invoices' => [
        'type' => 'Segment',
        'options' => [
          'route' => '/invoices',
          'defaults' => [
            'controller' => 'Application\Controller\Invoices',
            'action' => 'index',
          ],
        ],
      ],
    ],
  ],
  // ...
];
```

现在用通用的内容替换 `module/Application/views/application/index/index.phtml` 文件，而不是 ZF2 的广告：
