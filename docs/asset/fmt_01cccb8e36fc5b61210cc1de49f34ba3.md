
这些具体的`Hello`类应该是可以替换的。如果我们有一个使用它们的客户端类，其行为不会因为相互交换而受到影响：

```php
class Greeter {
  public function sayHello(HelloInterface $hello) {
    echo $hello->getHello() . "!\n";
  }
}

$greeter = new Greeter();
$greeter->sayHello(new EnglishHello());
$greeter->sayHello(new SpanishHello());
$greeter->sayHello(new FrenchHello());
```

虽然输出可能不同（这在示例中是预期的），但行为是一致的。无论我们给接口提供哪一个具体实例，代码输出的仍然是“hello”。

## PHPUnit 中的 LSP

在讨论开/闭原则时，我们已经讨论过一个里氏夫替换原则的例子了。我们定义的作为 PHPUnit `IDataSet` 实例的`ArrayDataSet`类是从 DbUnit 的`DatabaseTestCase`抽象类的`getDataSet()`方法返回的。

```php
class MyTest extends DatabaseTestCase {
  public function getDataSet() {
    return new ArrayDataSet([]);
  }
}
```

PHPUnit `DatabaseTestCase`类期望`getDataSet()`方法返回一个`IDataSet`实例，但并不一定在乎你提供的是什么实现，只要它符合接口即可。

此外，如果我们有时需要依赖一个可以读写的日志记录器，我们可以定义一个`LogManagerInterface`：

```php
interface LogManagerInterface
  extends LogReaderInterface, LogWriterInterface {
}
```

我们的`FileLogger`就可以实现`LogManagerInterface`，并满足任何同时需要读取和写入日志文件的需求。

## 为什么 ISP 关重要？

接口隔离原则（ISP）的目标是提供解耦的代码。所有使用接口实现的客户端代码都耦合于该接口的所有方法，无论它们是否使用了这些方法，并且当该接口内部发生重构时，即使与它们实际使用的实现无关，它们也可能受到缺陷的影响。

## 依赖倒置原则

**依赖倒置原则**（Dependency Inversion Principle）规定：

> 1. 高层模块不应该依赖低层模块。两者都应该依赖于抽象。

并且：

> B. 抽象不应该依赖于细节。细节应该依赖于抽象。

这一原则是《整洁架构》（The Clean Architecture）的核心，我们将在领先章节中详细讨论它是如何适配的。

想象一个控制简单游戏的类。游戏负责接受用户输入并在屏幕上显示结果。这个`GameManager`类是一个高层类，负责管理几个低层组件：

```php
class GameManager {
  protected $input;
  protected $video;

  public function __construct() {
    $this->input = new KeyboardInput();
    $this->video = new ScreenOutput();
  }

  public function run() {
    // accept user input from $this->input
    // draw the game state on $this->video
  }
}
```

这个`GameManager`类强依赖于两个低层类：`KeyboardInput`和`ScreenOutput`。这带来了一个问题：如果我们想更改该类中处理输入或输出的方式（例如切换到摇杆或终端输出，或者完全切换平台），我们无法做到。我们对这两个类有硬性依赖。

如果我们遵循里基夫替换原则（LSP）的一些准则，我们可以轻松设计出一个系统，其中`GameManager`允许输入和输出进行切换，而不影响`GameManager`类的输出：

```php
class GameManager {
  protected $input;
  protected $video;

  public function __construct(
    InputInterface $input,
    OutputInterface $output
  ) {
    $this->input = $input;
    $this->video = $output;
  }

  public function run() {
    // accept user input from $this->input
    // draw the game state on $this->video
  }
}
```

现在我们将这种依赖反转了，使其依赖于`InputInterface`和`OutputInterface`，这些是抽象而非具体实现，现在我们的高层`GameManager`类不再绑定于低层的`KeyboardInput`和`ScreenOutput`类。

我们可以让`KeyboardInput`和`ScreenOutput`类继承这些接口，并添加额外的接口，例如`JoystickInput`和`TerminalOutput`，它们可以在运行时进行切换：

```php
class KeyboardInput implements InputInterface {
  public function getInputEvent() { }
}

class JoystickInput implements InputInterface {
  public function getInputEvent() { }
}

class ScreenOutput implements OutputInterface {
  public function render() { }
}

class TerminalOutput implements OutputInterface {
  public function render() { }
}
```

我们在这里还利用了所谓的依赖注入（Dependency Injection），我们将在下一章讨论它，方便地称之为依赖注入。

如果我们无法修改输入和输出类以符合我们的接口（如果它们可能是系统提供的），那么利用我们之前讨论过的适配器模式（Adapter Pattern）来封装这些现有对象并使其符合我们的接口将会是明智的。

### 为什么 DIP 重要？

通常，为了实现解耦的代码库，应该使依赖只向内流动。频繁变化的事（即高层）应该只依赖于很少变化的事（低层）。而低层永远不应该依赖于频繁变化的事（即高层）。

我们遵循这一哲学是为了让未来更容易发生变化，并让这种变化对现有代码的影响尽可能小。在重构代码时，我们只希望重构后的代码容易出现问题；其他无关。

## 应用 SOLID 原则

SOLID 原则紧密结合，以强制易于扩展、重构和测试的代码，最终会导致缺陷更少，新功能的交付周期更快。

正如我们在本章中继续构建设计模式一样，在我们稍后讨论控制反转（Inversion of Control）和整洁架构时，我们将继续在 SOLID 原则的基础上构建。SOLID 原则是使整洁架构运行的基础原则。

## 依赖注入

面向对象编程中遇到的最糟糕的耦合形式之一是在类内部直接实例化类。发现这种实例的最快方法就是简单查找`new`操作符：

```php
class CustomerController {
  public function viewAction() {
    $repository = new CustomerRepository();
    $customer = $repository->getById(1001);
    return $customer;
  }
}
```

在`CustomerController`中，存在对`CustomerRepository`的依赖。这是一个硬性的、具体的依赖；如果没有`CustomerRepository`，`CustomerController`根本无法工作。

在类内部实例化依赖会引入几个问题：

1. **它使得后期难以进行更改。** 当类管理自己的依赖时，重构变得非常困难。如果我们想更改从数据库检索数据的方法（例如切换底层库或切换到不同的数据库存储），我们必须找到代码中所有声明`CustomerRepository`的实例并进行这些更改。这将是一个乏味且容易出错的过程。

2. **它使得测试变得困难。** 为了为`CustomerController`类编写任何类型的单元测试，我们必须确保不仅`CustomerRepository`对测试可用，而且`CustomerRepository`依赖的所有依赖（例如充满可测试数据的数据库）也必须可用。现在我们正在做全栈测试，而不是简单的单元测试。耦合使得隔离测试组件变得非常困难。

3. **我们对依赖没有控制权。** 在某些情况下，我们可能希望根据各种情况让类依赖在另一个类中使用具有不同的配置。当类在声明和配置其依赖时，开发会变得非常笨拙。

这些可能是非常严重的问题，特别是在较大的应用程序中。它会严重限制开发者未来对应用程序进行微小的更改。

## 控制反转

**控制反转**（Inversion of Control）是将依赖的实例化和配置从依赖类中转移，并交给某些外部手段的过程。有许多“外部手段”，我们将讨论其中两种流行的：*服务定位器模式*（Service Locator Pattern）和*依赖注入*（Dependency Injection）。

### 使用服务定位器

实现控制反转的一种方法是使用服务定位器模式。`Service Locator`（服务定位器）是一个资源注册表，应用程序可以通过它请求依赖而无需直接实例化它们。使用这种模式时，我们的代码简单地从服务定位器注册表中拉取其依赖。

```php
public function viewAction() {
  $repository = $this->serviceLocator->get('CustomerRepository');
  $customer = $repository->getById(1001);
  return $customer;
}
```

现在，该控制器不再直接实例化它自己的依赖，而是从服务定位器中提取依赖对象。根据你所使用的实现或框架，你可能会会有一些代码在服务定位器中注册`CustomerRepository`，以便服务定位器知道要向调用代码返回什么：

```php
$serviceLocator->setFactory('CustomerRepository', function($sl) {
  return new Path\To\CustomerRepository(
    $sl->get('Connection')
  );
});
```

在这个理论上的服务定位器中，一个匿名函数通过键`CustomerRepository`进行了注册，该函数负责构建和配置仓库并将其返回。此外，`CustomerRepository`本身依赖于一个名为`Connection`的东西，我们假设它定义在其他地方。这里的点在于，依赖项也可以有自己的依赖项。当出现这种情况时，在需要时直接实例化它们会变得更加难以应对。

这段代码提供了几处优势：

1. 现在只有一个地方负责实例化`CustomerRepository`，因此任何需要它的代码都将始终获得配置恰当的仓库。如果我们需要更改创建该仓库的*方式*的任何内容，只需要在一个地方进行修改即可。这使得重构代码库变得简单得多。

2. 另一个好处是它让`CustomerController`代码变得更容易测试。在测试上述控制器时，测试代码可以简单地为其提供一个不同的服务定位器实现，该实现包含一个模拟（mocked）仓库，可以控制它返回的数据。

```php
$serviceLocator->setFactory('CustomerRepository', function() {
  return new Path\To\MockCustomerRepository([
    1001 => (new Customer())->setName('ACME Corp')
  ]);
});
```

这个`MockCustomerRepository`仅根据客户 ID 返回“存储”的测试数据，因此在测试控制器时，它将返回一个名为 *ACME Corp* 的`Customer`对象。控制器现在与实际仓库分离进行测试，而且测试现在只关心返回了什么，而不关心它是如何检索的。

这段代码相比工厂示例和原始代码的直接实例化仍然改进微乎其微：

1. 它仍然通过服务定位器按需请求自己的依赖项。这比直接实例化依赖要好，因为我们至少可以控制服务定位器内部实际实例化了什么，这应该会让重构和测试变得更容易。

2. 为了进行测试，我们必须经过繁琐的设置过程。

### 使用依赖注入

**依赖注入**（Dependency Injection）是将依赖的实例化和配置从依赖类中转移，并交给某些外部手段的过程。我们将讨论两种依赖注入的方法：

1. **Setter 注入**（Setter Injection） - 使用 setter 方法按需要提供依赖项。

2. **构造函数注入**（Constructor Injection） - 使用构造函数为对象提供依赖项。

`CustomerController`现在被保证有一个准备就绪的`CustomerRepository`实例。控制器可以像以前使用 setter 注入并配合 mock 仓库那样对其进行测试，不同的是它是被提供给构造函数而不是 setter 方法：

```php
$repository = new MockCustomerRepository([
  1001 => (new Customer())->setName('ACME Corp')
]);
$controller = new CustomerController($repository);
$customer = $controller->viewAction();

assertEquals('ACME Corp', $customer->getName());
```

依赖注入有助于实现我们代码库的松耦合，并提供了在孤立状态下测试单个的能力，而无需构建、准备和传递它们各自的依赖项。由于构造函数注入强制对象注入其依赖项，因此在本书的其余部分中，它将优于 setter 注入。

## 何时使用依赖注入

现在我们已经讨论了什么是依赖注入以及它能帮助解决代码中的哪些问题，但花时间思考在什么情况下适用这种技术，在什么情况下不适用是非常重要的。这条界限有些模糊，你和任何人交流，可能都会得到不同的意见。

以下是我认为应该使用依赖注入的地方：

1. **当依赖项被多个组件使用时。** 如果它被很多地方使用，那么将实例化和配置抽象化并注入依赖可能是有意义的，而不是在需要时才这样做。如果不这样做，我们将使重构使用该依赖项的代码变得困难。然而，如果依赖项只被使用一次，那么在重构代码时你只需要去一个地方即可。

2. **依赖项在不同上下文中具有不同的配置。** 如果一个依赖项在使用的不同地方配置不同，那么你绝对想要注入它。同样，这种配置不应该发生在依赖类中。这不仅会让重构变得困难，还可能让测试变得困难。你可能还想投入开发一个真实的工厂，可以在不同场景下创建这些依赖项，以进一步抽象这些依赖项的创建。

3. **当我们需要不同的配置来测试组件时。** 如果测试一个依赖对象需要依赖项以不同的配置来通过测试，你就会想要注入它。没有其他好的方法可以绕过这一点。回想我们 mock `CustomerRepository` 以控制其返回数据的示例。

4. **当被注入的依赖项是第三方库的一部分时。** 如果你正在使用别人的代码，你不应该在依赖它的代码中直接实例化它。这些依赖项绝对应该被注入到你的代码中。对别人代码的使用是我们可能会经常重构的内容。这种场景需要特别注意，我们将在使用适配器进行抽象中通过已经讨论过的适配器模式进行详细讨论。

但确实有一些你可能不想使用依赖注入的场景。

如果依赖项不需要以任何方式进行配置（这意味着不需要调用构造函数参数或 setter 方法来设置），并且它本身没有依赖项，那么在需要它的类内部直接实例化该依赖可能是安全的。当依赖项是应用程序同一层中的组件时尤其如此（我们稍后会讨论软件的各个层级）。

例如，如果我们的框架要求控制器动作返回某种视图或响应对象，那么在动作中直接实例化并返回它是完全合逻辑的。

```php
public function viewAction() {
  $customer = $this->repository->getById(1001);

  return new ViewModel([
    'customer' => $customer
  ]);
}
```

将此`ViewModel`类注入控制器中获得的价值很小。它没有配置，它本身没有依赖项，在测试的情况下，我们可能只是想验证返回了一个`ViewModel`实例，并且其中存储了一个`Customer`实例。

### 使用工厂创建依赖项

如果我们有一个需要配置的依赖项，注入该依赖项本身并不总是有意义。有时注入一个知道如何为我们构建此依赖项的对象可能是更好的主意。当依赖项的配置方式是由类内部的场景控制时，这非常有用。

查看上面的示例：如果我们想根据请求的上下文返回不同类型的响应会怎样？也许默认我们返回 HTML，但根据上下文，也可能返回 JSON 或 XML？

在这种情况下，我们可能想要注入一个知道根据请求上下文构建响应的工厂：
